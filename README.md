# yapayzeka
Bu projede, klasik görüntü sınıflandırma yaklaşımlarının dışına çıkarak embedding tabanlı bir balık türü tanıma sistemi geliştirdik. Projede temel motivasyonumuz, görsel olarak birbirine oldukça benzeyen balık türlerini yalnızca etiket bazlı değil, anlamsal ve genellenebilir temsiller üzerinden ayırt edebilmekti.

🎯 Proje Konusu:
Bu çalışma, “etiketi doğru tahmin etmek” yerine görüntüler arasındaki görsel benzerliği öğrenmeyi hedefleyen bir image retrieval problemi olarak ele alındı. Model, aynı türe ait balık görüntülerini embedding uzayında birbirine yaklaştırırken, farklı türleri ise mümkün olduğunca uzaklaştıracak şekilde tasarlandı. Böylece modelin, sınıf ezberlemek yerine temsil (representation) öğrenmesi amaçlandı.

🛠️ 1. Veri Hazırlama ve Ön İşleme Süreci:
Kullanılan veri seti ciddi sınıf dengesizliği içerdiği için accuracy metriğinin yanıltıcı olacağı öngörüldü. Bu nedenle görüntüler normalize edildi, veri artırma (augmentation) yalnızca eğitim setinde uygulandı ve validation/test setlerine veri sızıntısı (data leakage) kesin olarak engellendi. Bu yaklaşım, modelin gerçek dünyadaki performansını daha doğru şekilde ölçmemizi sağladı.

🧩 2. Metric Learning Yaklaşımı (Triplet Loss):
Model, anchor–positive–negative üçlüleri üzerinden Triplet Loss kullanılarak eğitildi. Bu yapı sayesinde aynı türe ait balık görüntüleri embedding uzayında birbirine yaklaşırken, farklı türler net biçimde ayrıldı. Sonuç olarak model, sınıf etiketlerine doğrudan bağımlı kalmadan görsel ilişkileri yakalayabilen bir temsil uzayı oluşturdu.

🤖 3. Modelleme ve Değerlendirme:
Embedding boyutu 128 olarak belirlendi. Bu boyut, ayırt edicilik ve genelleme arasında dengeli bir yapı sundu ve aşırı öğrenme riskini artırmadan stabil sonuçlar verdi. Model performansı sınıflandırma metrikleriyle değil; Top-K Accuracy (CMC), retrieval başarı oranları ve t-SNE görselleştirmeleri ile değerlendirildi. t-SNE çıktıları, aynı türe ait balıkların embedding uzayında anlamlı kümeler oluşturduğunu açıkça gösterdi.

📊 4. İçgörüler:
Analizler sonucunda, yanlış eşleşmelerin büyük kısmının biyolojik ve morfolojik olarak benzer balık türleri arasında gerçekleştiği gözlemlendi. Bu durum, modelin rastgele tahminler yapmadığını; aksine görsel olarak mantıklı, tutarlı ve yorumlanabilir kararlar verdiğini ortaya koydu.
