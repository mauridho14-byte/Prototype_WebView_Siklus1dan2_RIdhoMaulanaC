📱 Mobile Application Development

Repository ini berisi kumpulan tugas praktikum mata kuliah Pemrograman Mobile (Kelas TIF-A). Repository ini mendokumentasikan dua siklus pengembangan aplikasi mobile dengan metode dan arsitektur yang berbeda: Siklus 1 menggunakan Low-Code Prototyping (MIT App Inventor) dan Siklus 2 menggunakan Cross-Platform Native Framework (React Native dengan Fabric / New Architecture).

Daftar Isi
    
    📱 Mobile Application Development Portfoli
      -👤 Informasi Mahasiswa
      -📑 Daftar Isi
      -📂 Struktur Repository
      -🔹 Siklus 1: WebView Prototype (MIT App Inventor)
            1. Deskripsi Tugas
            2. Spesifikasi & Fitur
            3. Artefak & Output
      -🔹 Siklus 2: React Native WebView (New Architecture / Fabric)
            1. Deskripsi Tugas
            2. Prasyarat System (Prerequisites)
            3. Langkah Pengerjaan & Konfigurasi
                -Langkah 1: Inisialisasi Proyek
                -Langkah 2: Aktivasi Fabric (New Architecture)
                -Langkah 3: Instalasi Library WebView
                -Langkah 4: Struktur Kode Utama (App.jsx)
                -Langkah 5: Running Aplikasi
      -📊 Perbandingan Siklus 1 vs Siklus 2
      -📄 Lisensi & Hak Cipta
  
📂 Struktur Repository.

    ├── siklus-1/                        # Direktori Tugas Siklus 1
    │   ├── RidhoTechNews.zip            # File Source Project MIT App Inventor (.aia / .zip)
    │   ├── RidhoTechNews.apk            # Output File APK Aplikasi
    │   └── screenshots/                 # Tampilan Layar & Bukti Pengerjaan
    │       └── preview.jpg
    │
    ├── siklus-2/                        # Direktori Tugas Siklus 2 (React Native)
    │   ├── android/                     # Konfigurasi Native Android (Fabric enabled)
    │   ├── ios/                         # Konfigurasi Native iOS
    │   ├── App.jsx                      # Source Code Utama Aplikasi
    │   ├── package.json                 # Dependency & Script Proyek
    │   └── README.md                    # Catatan khusus Siklus 2
    │
    └── README.md                        # Berkas Utama Dokumentasi Repository

🔹 Siklus 1: WebView Prototype (MIT App Inventor)

        1. Deskripsi Tugas
           Pada siklus ini, dibuat prototipe aplikasi Android sederhana menggunakan platform MIT App Inventor. Aplikasi bertindak sebagai WebView interaktif yang memuat situs berita teknologi / portal kampus secara langsung di dalam aplikasi mobile.
        2. Spesifikasi & Fitur
           -Platform: MIT App Inventor (appinventor.mit.edu)
           -Komponen Utamanya:
               1.WebViewer: Merender halaman web target secara real-time.
               2.Button (Navigasi): Menyediakan kontrol navigasi interaktif (seperti tombol Refresh atau Home).
               3.Layouting (Vertical/Horizontal Arrangement): Mengatur tata letak antarmuka agar responsif.
           -Fitur Aplikasi:
               1.Auto-load halaman web tujuan saat aplikasi dibuka.
               2.Navigasi manual untuk memperbarui (refresh) atau kembali ke halaman utama.
        3. Artefak & Output
           -RidhoTechNews.zip: Project file mentah untuk diimpor kembali ke MIT App Inventor.
           -RidhoTechNews.apk: Binary file yang siap diinstal pada perangkat Android.

🔹 Siklus 2: React Native WebView (New Architecture / Fabric)

      1. Deskripsi Tugas
         Siklus 2 meningkatkan kompleksitas pengembangan ke tingkat hybrid/native development menggunakan React Native. Fokus utama siklus ini adalah mengaktifkan Fabric (New Architecture) untuk performa rendering yang lebih cepat, sinkron, dan efisien, serta mengintegrasikan library react-native-webview.
      2. Prasyarat System (Prerequisites)
         -Node.js versi >= 18
         -JDK (Java Development Kit) 17
         -Android Studio & Android SDK (dengan konfigurasi ANDROID_HOME)
         -React Native CLI (npx react-native)
      3. Langkah Pengerjaan & Konfigurasi
         Langkah 1: Inisialisasi Proyek
            npx react-native init TugasWebViewFabric 
            cd TugasWebViewFabric
         Langkah 2: Aktivasi Fabric (New Architecture)
           -Android: Buka file android/gradle.properties, lalu pastikan flag berikut aktif:
             newArchEnabled=true
           -iOS: Jalankan Pod install dengan flag New Architecture aktif:
             cd ios && RCT_NEW_ARCH_ENABLED=1 bundle exec pod install && cd ..
        Langkah 3: Instalasi Library WebView
            npm install react-native-webview
            # Atau jika menggunakan Yarn:
            yarn add react-native-webview
        Langkah 4: Struktur Kode Utama (App.jsx)
           Kode aplikasi dibuat menggunakan arsitektur komponen React Native modern:
             import React from 'react';
             import { StyleSheet, View, Text, SafeAreaView, StatusBar } from 'react-native';
             import { WebView } from 'react-native-webview';
          
        const App = () => {
          return (
            <SafeAreaView style={styles.container}>
                   <StatusBar barStyle="dark-content" backgroundColor="#4A90E2" />
      
              {/* Header Aplikasi */}
              <View style={styles.header}>
                <Text style={styles.headerText}>Portal Kampus - Fabric WebView</Text>
              </View>

              {/* Komponen WebView Fabric */}
              <View style={styles.webViewContainer}>
                <WebView
                  source={{ uri: 'https://example.com' }}
                  style={styles.flexOne}
                  javaScriptEnabled={true}
                  startInLoadingState={true}
                />
             </View>
          </SafeAreaView>
        );
      };

     const styles = StyleSheet.create({
      container: {
        flex: 1,
        backgroundColor: '#F5FCFF',
      },
      header: {
        height: 55,
        backgroundColor: '#4A90E2',
        justifyContent: 'center',
        alignItems: 'center',
        elevation: 4,
      },
      headerText: {
        color: '#FFFFFF',
        fontSize: 18,
        fontWeight: 'bold',
      },
      webViewContainer: {
        flex: 1,
      },
      flexOne: {
        flex: 1,
      },
    });

    export default App;

Langkah 5: Running Aplikasi
  
  Untuk menjalankan aplikasi pada Emulator Android atau Perangkat Fisik:
  npx react-native run-android
  
📊 Perbandingan Siklus 1 vs Siklus 2

    Parameter      Siklus 1 (MIT App Inventor)    Siklus 2 (React Native Fabric)
    Pendekatan     Visual/Block Programming       Code-based Framework (JavaScript/JSX)
                   (Low-Code)               
   
    Arsitektur     Standard Web Component         New Architecture (Fabric Engine)
    Rendering 
    
    Fleksibilitas  Terbatas pada blok UI         Sangat tinggi (Custom Component & Styling)
                   yang tersedia           
    
    Performa       Standar                       Tinggi (Synchronous UI rendering)
    
    Target Build   Android (.apk)                Multiplatform (Android & iOS)



Hasil Siklus 1

<img width="720" height="1600" alt="Hasil1" src="https://github.com/user-attachments/assets/64cd4168-5efb-443b-a836-1998767a95e2" />
<img width="720" height="1600" alt="Hasil2" src="https://github.com/user-attachments/assets/cc659d3c-c4f9-4206-99b3-396d1a5606da" />



Hasil Siklus 2

<img width="1566" height="1191" alt="WhatsApp Image 2026-10-15 at 16 19 32" src="https://github.com/user-attachments/assets/c21afac9-7ff2-40b4-b557-3b6a5864b538" />




