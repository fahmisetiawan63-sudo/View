# SIMRS Hospital Management System

🏥 **Sistem Informasi Manajemen Rumah Sakit (SIMRS)** - Solusi terintegrasi untuk rumah sakit medium dengan fokus pada manajemen pasien, rekam medis elektronik, billing, farmasi, laboratorium, radiologi, dan inventory.

## 📋 Daftar Isi
- [Fitur Utama](#fitur-utama)
- [Teknologi](#teknologi)
- [Struktur Project](#struktur-project)
- [Instalasi](#instalasi)
- [Penggunaan](#penggunaan)
- [API Documentation](#api-documentation)
- [Development](#development)
- [Kontribusi](#kontribusi)

## ✨ Fitur Utama

### 1. 👥 Manajemen Pasien
- Registrasi pasien baru
- Verifikasi data pasien
- Update informasi pasien
- Search dan filter pasien
- Medical record numbering otomatis
- Asuransi/BPJS verification

### 2. 📋 Electronic Medical Record (EMR/EHR)
- Rekam medis digital lengkap
- Riwayat diagnosa
- Resep digital
- Hasil pemeriksaan
- Catatan perawatan
- Discharge summary
- Multi-user access (dokter, perawat, admin)

### 3. 💊 Manajemen Farmasi
- Inventori obat terintegrasi
- Pembelian obat (PO)
- Penerimaan barang
- Resep digital
- Dispensing obat
- Tracking obat expired
- Stok opname
- Laporan farmasi

### 4. 🔬 Laboratorium
- Permintaan pemeriksaan lab
- Manajemen sampel
- Input hasil lab
- Validasi hasil
- Laporan hasil ke pasien
- Manajemen peralatan lab
- Quality control

### 5. 🩻 Radiologi
- Permintaan pemeriksaan radiologi
- Scheduling radiologi
- Upload hasil imaging
- Radiologist verification
- Report generation
- PACS integration ready
- Archive imaging

### 6. 💰 Billing & Keuangan
- Invoice otomatis
- Manajemen pembayaran
- Verifikasi asuransi
- Laporan revenue
- Piutang pasien tracking
- Rekonsiliasi keuangan

### 7. 📊 Inventory Management
- Manajemen stok umum (non-farmasi)
- Pembelian barang
- Penerimaan barang
- Permintaan internal
- Stock level monitoring
- Supplier management

## 🛠️ Teknologi

### Backend Stack
- **Java 17 LTS** - Programming Language
- **Spring Boot 3.1.5** - Web Framework
- **Spring Data JPA** - ORM
- **Spring Security** - Authentication & Authorization
- **MySQL 8.0+** - Relational Database
- **Flyway** - Database Migration
- **Lombok** - Code Generation
- **Springdoc OpenAPI 2.0.4** - API Documentation (Swagger)
- **Maven 3.9** - Build Tool

### Architecture
- **Layered Architecture**
  - Presentation Layer (Controllers)
  - Business Logic Layer (Services)
  - Data Access Layer (Repositories)
  - Database Layer (MySQL)

- **Design Patterns**
  - Repository Pattern
  - Service Layer Pattern
  - DTO Pattern
  - Exception Handling Pattern

## 📁 Struktur Project

```
SIMRS-Hospital-Management/
│
├── simrs-common/                    # Shared utilities & constants
│   └── src/main/java/com/otten32/common/
│       ├── constant/                # Constants & enums
│       ├── dto/                     # Base DTOs
│       ├── entity/                  # Base entities
│       ├── exception/               # Custom exceptions
│       └── util/                    # Utility classes
│
├── simrs-core/                      # Core business logic
│   └── src/main/java/com/otten32/core/
│       ├── patient/                 # Patient Management
│       ├── medical/                 # Medical Records
│       ├── pharmacy/                # Pharmacy Module
│       ├── laboratory/              # Laboratory Module
│       ├── radiology/               # Radiology Module
│       └── billing/                 # Billing Module
│
├── simrs-api/                       # REST API Server
│   ├── src/main/java/com/otten32/api/
│   │   ├── controller/              # REST Controllers
│   │   ├── config/                  # Configuration classes
│   │   ├── exception/               # Exception handlers
│   │   └── SimrsApiApplication.java
│   ├── src/main/resources/
│   │   ├── application.properties   # Configuration
│   │   └── db/migration/            # Flyway migrations
│   └── pom.xml
│
├── pom.xml                          # Parent POM
├── README.md                        # This file
├── SETUP_COMPLETE.md                # Setup completion summary
├── DEVELOPMENT_GUIDE.md             # Development guidelines
└── .gitignore                       # Git ignore rules
```

## 🚀 Instalasi

### Prerequisites
- Java 17 atau lebih tinggi
- Maven 3.9+
- MySQL 8.0+
- Git

### Step 1: Clone Repository
```bash
git clone https://github.com/fahmisetiawan63-sudo/SIMRS-Hospital-Management.git
cd SIMRS-Hospital-Management
```

### Step 2: Setup Database
```sql
-- Create database
CREATE DATABASE simrs_db CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

### Step 3: Konfigurasi Database
Edit file `simrs-api/src/main/resources/application.properties`:
```properties
spring.datasource.url=jdbc:mysql://localhost:3306/simrs_db?useSSL=false&serverTimezone=UTC
spring.datasource.username=root
spring.datasource.password=your_password
```

### Step 4: Build Project
```bash
mvn clean install
```

### Step 5: Run Application
```bash
cd simrs-api
mvn spring-boot:run
```

Atau run JAR file:
```bash
mvn clean package -DskipTests
java -jar target/simrs-api-1.0.0.jar
```

## 📱 Penggunaan

### Akses Aplikasi
- **API Base URL**: `http://localhost:8080/api/v1`
- **Swagger UI**: `http://localhost:8080/swagger-ui.html`
- **API Documentation**: `http://localhost:8080/api-docs`
- **Health Check**: `http://localhost:8080/actuator/health`

## 📚 API Documentation

### Patient Management Endpoints

| Method | Endpoint | Deskripsi |
|--------|----------|----------|
| POST | `/api/v1/patients` | Register pasien baru |
| GET | `/api/v1/patients/{id}` | Get detail pasien |
| GET | `/api/v1/patients` | Get all patients (paginated) |
| GET | `/api/v1/patients/search` | Search patients |
| GET | `/api/v1/patients/medical-record/{no}` | Get by medical record number |
| GET | `/api/v1/patients/nik/{nik}` | Get by NIK |
| PUT | `/api/v1/patients/{id}` | Update patient |
| PUT | `/api/v1/patients/{id}/deactivate` | Deactivate patient |

## 📊 Project Status

### ✅ Completed
- [x] Project setup & structure
- [x] Database schema
- [x] Common module (utilities, DTOs)
- [x] Patient management module
- [x] Medical records module
- [x] Pharmacy module
- [x] Laboratory module
- [x] Radiology module
- [x] Billing module
- [x] REST API controllers
- [x] Exception handling
- [x] API documentation (Swagger)

### ⏳ In Progress / Coming Soon
- [ ] Authentication & Authorization (JWT)
- [ ] Unit & Integration tests
- [ ] Staff management module
- [ ] Inventory management module
- [ ] Frontend application (React/Angular)
- [ ] CI/CD pipeline (GitHub Actions)
- [ ] Performance optimization
- [ ] Mobile application

## 🤝 Kontribusi

Kontribusi sangat diterima! Silakan:

1. Fork repository
2. Create feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Open Pull Request

## 📝 License

Project ini menggunakan Apache 2.0 License - lihat file LICENSE untuk detail.

## 📞 Support & Contact

- **Repository**: [GitHub](https://github.com/fahmisetiawan63-sudo/SIMRS-Hospital-Management)
- **Issues**: [GitHub Issues](https://github.com/fahmisetiawan63-sudo/SIMRS-Hospital-Management/issues)
- **Email**: support@otten32.com

## 👥 Tim Pengembang

- **Project Lead**: Fahmi Setiawan ([@fahmisetiawan63-sudo](https://github.com/fahmisetiawan63-sudo))
- **Organization**: OTTEN 32

---

**Made with ❤️ by OTTEN 32**

**Last Updated**: September 12, 2026
**Version**: 1.0.0
**Status**: 🟢 Production Ready (Beta)
