# 👥 PHÂN CHIA CÔNG VIỆC CHO TEAM 2 NGƯỜI

## 📊 TỔNG QUAN PHÂN CHIA

### Nguyên tắc phân chia:
- ✅ **Cân bằng khối lượng công việc**
- ✅ **Có thể làm song song** (parallel work)
- ✅ **Rõ ràng về trách nhiệm** (clear ownership)
- ✅ **Dễ tích hợp** (easy integration)
- ✅ **Phù hợp với thế mạnh** (leverage strengths)

---

## 🎯 PHƯƠNG ÁN PHÂN CHIA ĐỀ XUẤT

### **NGƯỜI 1: Backend & Infrastructure Specialist** 🔧
**Trách nhiệm chính:** Xây dựng hạ tầng, xử lý luồng dữ liệu, đảm bảo hệ thống ổn định

### **NGƯỜI 2: ML & Visualization Specialist** 🤖📊
**Trách nhiệm chính:** Machine Learning, phân tích dữ liệu, Dashboard

---

## 📅 CHI TIẾT PHÂN CHIA THEO GIAI ĐOẠN

### 🔵 GIAI ĐOẠN 1: Infrastructure & Ingestion (Tuần 1)

#### 👤 **NGƯỜI 1: Infrastructure Setup**
**Công việc:**
- ✅ Thiết lập Docker Compose file (`docker-compose.yml`)
- ✅ Cấu hình HDFS (NameNode, DataNode)
- ✅ Cấu hình Spark Cluster (Master, Worker)
- ✅ Cấu hình Kafka và Zookeeper
- ✅ Kiểm tra và troubleshoot các services
- ✅ Tạo Kafka topic `livestream-comments`
- ✅ Viết script kiểm tra services (health check)

**Deliverables:**
- File `docker-compose.yml` hoàn chỉnh
- Tài liệu hướng dẫn setup và troubleshooting
- Script kiểm tra services

**Thời gian ước tính:** 3-4 ngày

---

#### 👤 **NGƯỜI 2: Data Producer & Simulation**
**Công việc:**
- ✅ Viết Producer script (`producer.py`)
- ✅ Thiết kế dataset mẫu (comment pool, topics)
- ✅ Tối ưu tốc độ gửi message (simulate real livestream)
- ✅ Thêm metadata vào comment (timestamp, user_id, topic)
- ✅ Viết script test Producer (verify data format)
- ✅ Tạo file `requirements.txt` cho Producer

**Deliverables:**
- File `producer.py` với comment pool đa dạng
- File `requirements.txt`
- Dataset mẫu (CSV/JSON) nếu cần
- Documentation về data format

**Thời gian ước tính:** 2-3 ngày

**Lưu ý:** Có thể làm song song với Người 1 sau khi Kafka đã setup xong

---

### 🔵 GIAI ĐOẠN 2: Stream Processing & Cleaning (Tuần 2)

#### 👤 **NGƯỜI 1: Spark Streaming Pipeline**
**Công việc:**
- ✅ Viết Spark Streaming code (`spark_streaming.py`)
- ✅ Kết nối Spark với Kafka
- ✅ Implement Preprocessing:
  - `flatMap`: Tách câu thành từ
  - `filter`: Loại bỏ spam, comment ngắn
  - Loại bỏ stop words
- ✅ Xử lý JSON parsing từ Kafka
- ✅ Tối ưu batch interval
- ✅ Viết unit tests cho transformations

**Deliverables:**
- File `spark_streaming.py` với preprocessing đầy đủ
- File `requirements-spark.txt`
- Test cases cho preprocessing logic
- Documentation về data flow

**Thời gian ước tính:** 4-5 ngày

---

#### 👤 **NGƯỜI 2: Data Analysis & Schema Design**
**Công việc:**
- ✅ Thiết kế schema cho comment data
- ✅ Thiết kế schema cho kết quả phân tích
- ✅ Chuẩn bị training dataset cho ML models
- ✅ Viết script `prepare_training_data.py`
- ✅ Feature engineering (tokenization, TF-IDF)
- ✅ Tạo file `requirements-ml.txt`

**Deliverables:**
- Schema definitions (JSON/StructType)
- File `prepare_training_data.py`
- Training dataset (parquet format)
- Preprocessing pipeline model

**Thời gian ước tính:** 3-4 ngày

**Lưu ý:** Có thể làm song song, nhưng cần sync về schema với Người 1

---

### 🔵 GIAI ĐOẠN 3: AI Integration & Window Operations (Tuần 3) ⭐ QUAN TRỌNG

#### 👤 **NGƯỜI 2: Machine Learning Models** (Chủ đạo)
**Công việc:**
- ✅ Train Logistic Regression model với MLlib
- ✅ Train Naive Bayes model với MLlib
- ✅ So sánh 2 models (Accuracy, AUC-ROC)
- ✅ Viết script `train_and_compare_models.py`
- ✅ Tạo báo cáo so sánh models (markdown/PDF)
- ✅ Lưu model tốt nhất
- ✅ Tối ưu hyperparameters nếu có thời gian

**Deliverables:**
- File `train_and_compare_models.py`
- Trained models (saved models)
- Báo cáo so sánh models (`model_comparison_report.md`)
- Model evaluation metrics

**Thời gian ước tính:** 4-5 ngày

---

#### 👤 **NGƯỜI 1: Stream Integration & Window Operations** (Hỗ trợ tích hợp)
**Công việc:**
- ✅ Tích hợp ML model vào Spark Streaming
- ✅ Implement Window Operations:
  - `reduceByKeyAndWindow` cho sentiment trong 30s
  - Tính Top Comments với window
  - Tính Top Keywords với window
- ✅ Implement Top Negative Comments filtering
- ✅ Tối ưu window size và slide interval
- ✅ Xử lý watermark cho late data

**Deliverables:**
- File `spark_streaming_with_ml.py` (tích hợp ML)
- Code cho các window operations
- Documentation về window logic

**Thời gian ước tính:** 3-4 ngày

**Lưu ý:** Cần sync với Người 2 về model format và cách load model

---

### 🔵 GIAI ĐOẠN 4: Fault Tolerance & Storage (Tuần 4)

#### 👤 **NGƯỜI 1: Checkpointing & Storage**
**Công việc:**
- ✅ Cấu hình Checkpointing trên HDFS
- ✅ Implement fault recovery logic
- ✅ Lưu kết quả vào HDFS (Parquet format)
- ✅ Viết script `spark_streaming_checkpoint.py`
- ✅ Test recovery scenario (simulate crash)
- ✅ Tối ưu checkpoint frequency

**Deliverables:**
- File `spark_streaming_checkpoint.py`
- Checkpoint configuration
- Test cases cho fault tolerance
- Documentation về recovery process

**Thời gian ước tính:** 2-3 ngày

---

#### 👤 **NGƯỜI 2: Database Integration**
**Công việc:**
- ✅ Setup MongoDB hoặc MySQL
- ✅ Thiết kế database schema
- ✅ Viết connector lưu kết quả vào DB
- ✅ Viết script `save_to_mongodb.py` hoặc `save_to_mysql.py`
- ✅ Tối ưu batch insert
- ✅ Tạo indexes cho queries nhanh

**Deliverables:**
- Database setup script
- Connector code (`save_to_mongodb.py` hoặc `save_to_mysql.py`)
- Database schema documentation
- Query optimization

**Thời gian ước tính:** 2-3 ngày

---

### 🔵 GIAI ĐOẠN 5: Dashboard Visualization (Tuần 4-5)

#### 👤 **NGƯỜI 2: Dashboard Development** (Chủ đạo)
**Công việc:**
- ✅ Setup Streamlit
- ✅ Thiết kế UI/UX cho Dashboard
- ✅ Implement Sentiment Gauge (Plotly)
- ✅ Implement Top Comments chart
- ✅ Implement Top Keywords visualization
- ✅ Implement Top Negative Comments table
- ✅ Auto-refresh functionality
- ✅ Styling và responsive design

**Deliverables:**
- File `dashboard.py` hoàn chỉnh
- Requirements file cho Dashboard
- Screenshots/Demo video
- User guide

**Thời gian ước tính:** 4-5 ngày

---

#### 👤 **NGƯỜI 1: Data Pipeline Integration** (Hỗ trợ)
**Công việc:**
- ✅ Đảm bảo data flow từ Spark → Database → Dashboard
- ✅ Tối ưu query performance cho Dashboard
- ✅ Viết API endpoints nếu cần (optional)
- ✅ Monitoring và logging
- ✅ Performance testing

**Deliverables:**
- Integration tests
- Performance benchmarks
- Monitoring setup

**Thời gian ước tính:** 2-3 ngày

---

## 📋 TỔNG KẾT PHÂN CHIA

### **NGƯỜI 1: Backend & Infrastructure** 🔧
| Giai đoạn | Công việc chính | Thời gian |
|-----------|----------------|-----------|
| 1 | Docker, Kafka, HDFS, Spark setup | 3-4 ngày |
| 2 | Spark Streaming & Preprocessing | 4-5 ngày |
| 3 | Window Operations & ML Integration | 3-4 ngày |
| 4 | Checkpointing & HDFS Storage | 2-3 ngày |
| 5 | Pipeline Integration & Testing | 2-3 ngày |
| **TỔNG** | | **14-19 ngày** |

### **NGƯỜI 2: ML & Visualization** 🤖📊
| Giai đoạn | Công việc chính | Thời gian |
|-----------|----------------|-----------|
| 1 | Producer Script & Data Simulation | 2-3 ngày |
| 2 | Training Data Preparation | 3-4 ngày |
| 3 | ML Models Training & Comparison | 4-5 ngày |
| 4 | Database Integration | 2-3 ngày |
| 5 | Dashboard Development | 4-5 ngày |
| **TỔNG** | | **15-20 ngày** |

---

## 🤝 CÁCH LÀM VIỆC NHÓM HIỆU QUẢ

### 1. **Communication & Sync**
- ✅ **Daily standup** (10 phút mỗi ngày): Báo cáo tiến độ, blockers
- ✅ **Sync điểm** sau mỗi giai đoạn: Review code, test integration
- ✅ **Git workflow**: Sử dụng branches, code review
- ✅ **Shared documentation**: Google Docs/Notion để track progress

### 2. **Git Repository Structure**
```
Big_data/
├── infrastructure/          # Người 1
│   ├── docker-compose.yml
│   ├── scripts/
│   └── docs/
├── streaming/              # Người 1
│   ├── spark_streaming.py
│   └── preprocessing/
├── ml/                     # Người 2
│   ├── train_models.py
│   ├── models/
│   └── data/
├── producer/               # Người 2
│   ├── producer.py
│   └── data/
├── storage/                # Cả 2
│   ├── mongodb_connector.py
│   └── checkpoint_config.py
└── dashboard/              # Người 2
    ├── dashboard.py
    └── requirements.txt
```

### 3. **Integration Points** (Cần sync)
- ✅ **Schema định nghĩa**: Comment format, Result format
- ✅ **Model format**: Cách load/save ML models
- ✅ **Database schema**: Table/Collection structure
- ✅ **API contracts**: Nếu có API giữa các components

### 4. **Testing Strategy**
- ✅ **Unit tests**: Mỗi người viết test cho phần của mình
- ✅ **Integration tests**: Test chung sau mỗi giai đoạn
- ✅ **End-to-end test**: Test toàn bộ pipeline trước khi demo

---

## ⚠️ LƯU Ý QUAN TRỌNG

### Dependencies (Thứ tự làm việc):
1. **Giai đoạn 1**: Người 1 setup infrastructure TRƯỚC → Người 2 mới test Producer được
2. **Giai đoạn 2**: Có thể làm song song nhưng cần sync về schema
3. **Giai đoạn 3**: Người 2 train model TRƯỚC → Người 1 mới tích hợp được
4. **Giai đoạn 4**: Có thể làm song song
5. **Giai đoạn 5**: Người 2 làm Dashboard, Người 1 hỗ trợ integration

### Risk Management:
- ⚠️ **Nếu một người bị delay**: Người kia có thể hỗ trợ phần có thể làm song song
- ⚠️ **Nếu có blocker**: Cả 2 cùng troubleshoot
- ⚠️ **Code review**: Luôn review code của nhau trước khi merge

---

## 📝 CHECKLIST THEO GIAI ĐOẠN

### ✅ Giai đoạn 1 - Hoàn thành khi:
- [ ] Docker cluster chạy ổn định
- [ ] Kafka topic đã tạo và Producer gửi được data
- [ ] Cả 2 đều test được trên cùng môi trường

### ✅ Giai đoạn 2 - Hoàn thành khi:
- [ ] Spark Streaming đọc được data từ Kafka
- [ ] Preprocessing chạy đúng
- [ ] Schema đã được đồng bộ giữa 2 người

### ✅ Giai đoạn 3 - Hoàn thành khi:
- [ ] 2 models đã được train và so sánh
- [ ] Model tốt nhất đã được tích hợp vào stream
- [ ] Window operations tính đúng các metrics

### ✅ Giai đoạn 4 - Hoàn thành khi:
- [ ] Checkpointing hoạt động, có thể recover
- [ ] Data được lưu vào database
- [ ] Cả 2 đều verify được data trong DB

### ✅ Giai đoạn 5 - Hoàn thành khi:
- [ ] Dashboard hiển thị đúng dữ liệu realtime
- [ ] Tất cả charts/metrics đều hoạt động
- [ ] End-to-end test thành công

---

## 🎯 KẾT LUẬN

Với cách phân chia này:
- ✅ **Cân bằng công việc**: Mỗi người ~15-20 ngày
- ✅ **Rõ ràng trách nhiệm**: Mỗi người có ownership rõ ràng
- ✅ **Có thể làm song song**: Nhiều phần không phụ thuộc nhau
- ✅ **Dễ tích hợp**: Có điểm sync rõ ràng
- ✅ **Phù hợp thế mạnh**: Người 1 (Backend), Người 2 (ML/Visualization)

**Chúc team làm việc hiệu quả! 🚀**

