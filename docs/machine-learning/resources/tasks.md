---
title: Makine öğrenimi görevlerini - ML.NET
description: Farklı makine öğrenimi görevlerini ve ML.NET içinde desteklenen ilişkili görevleri keşfedin.
ms.custom: seodec18
ms.date: 04/12/2019
author: natke
ms.openlocfilehash: bfed9cf12f8d539c4327549e5305415ce096e022
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62019110"
---
# <a name="machine-learning-tasks-in-mlnet"></a>ML.NET Machine learning görevleri

Bir machine learning modeli oluştururken ilk verilerinizle elde etmek umarak tanımlamanız gerekir. Bu görev durumunuza öğrenme doğru makine seçmenize olanak sağlar. Aşağıdaki listede, aralarından seçim yapabileceğiniz görevleri öğrenme farklı makine açıklar ve bazı yaygın kullanım örnekleri.

Senaryonuz için hangi görev çalışır karar verdikten sonra modeli eğitmek için en iyi algoritmayı seçin gerekir. Kullanılabilir algoritmalar, her görev için bölümünde listelenir.

## <a name="binary-classification"></a>İkili sınıflandırma

A [denetimli makine öğrenimi](glossary.md#supervised-machine-learning) veri örneği ait olduğu, iki sınıf (Kategoriler) tahmin etmek için kullanılan görev. Bir sınıflandırma algoritmasıdır girişi etiketli örnekler, her etiket bir tamsayı 0 veya 1 olduğu kümesidir. İkili sınıflandırma algoritmasıdır çıktısındaki yeni etiketlenmemiş örnek sınıfı tahmin etmek için kullanabileceğiniz bir sınıflandırıcı ' dir. İkili sınıflandırma senaryolarına örnekler şunlardır:

* [Twitter yorumların anlama yaklaşım](../tutorials/sentiment-analysis.md) "pozitif" veya "negatif" olarak.
* Bir hastanın belirli bir Hastalık olup olmadığını tanılama.
* "Veya istenmeyen posta olarak" e-posta işaretlemek için bir kararı.
* Fotoğraf köpek ve Meyve içerip içermediğini belirleyin.

Daha fazla bilgi için [ikili sınıflandırma](https://en.wikipedia.org/wiki/Binary_classification) wikipedia makalesi.

### <a name="binary-classification-training-algorithms"></a>İkili sınıflandırma eğitim algoritmaları

Aşağıdaki algoritmaları kullanarak bir ikili sınıflandırma modelinde eğitebilirsiniz:

* <xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer>
* <xref:Microsoft.ML.Trainers.LinearSvmTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.PriorTrainer>
* <xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedBinaryTrainer>
* <xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>

## <a name="multiclass-classification"></a>Sınıflı sınıflandırma

A [denetimli makine öğrenimi](glossary.md#supervised-machine-learning) veri örneği sınıfı (kategori) tahmin etmek için kullanılan görev. Bir sınıflandırma algoritmasıdır girişi etiketli örnekleri kümesidir. Her etiketin normal metin olarak başlar. Ardından, anahtarı (sayısal) türüne dönüştürür TermTransform aracılığıyla çalıştırılır. Bir sınıflandırma algoritmasıdır çıktısı, yeni etiketlenmemiş örnek sınıfı tahmin etmek için kullanabileceğiniz bir sınıflandırıcı ' dir. Çok sınıflı sınıflandırma senaryolarına örnekler şunlardır:

* Köpek bir "Siberian Husky", "Altın alıcısı", "şu dar", vb. olarak belirleniyor.
* Film anlama "pozitif", "belirsiz" veya "negatif" incelenir.
* Otel kategorilendirme "Konum", "price", "temizlik", vb. incelenir.

Daha fazla bilgi için [sınıflı sınıflandırma](https://en.wikipedia.org/wiki/Multiclass_classification) wikipedia makalesi.

>[!NOTE]
>Herhangi bir vs tüm yükseltmeleri [ikili sınıflandırma learner](#binary-classification) çok sınıflı veri kümelerinde yapacak. Daha fazla bilgi [Vikipedi] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).

### <a name="multiclass-classification-training-algorithms"></a>Çok sınıflı sınıflandırma eğitim algoritmaları

Aşağıdaki eğitim algoritmalarını kullanarak bir çok sınıflı sınıflandırma modeli eğitmek:

* <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.OneVersusAllTrainer>
* <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer>

## <a name="regression"></a>Regresyon

A [denetimli makine öğrenimi](glossary.md#supervised-machine-learning) ilgili özellikleri kümesinden etiketin değeri tahmin etmek için kullanılan görev. Etiket herhangi bir gerçek değerini olabilir ve sınıflandırma görevleri olduğu gibi değerlerin değil sınırlı ayarlanır. Regresyon algoritmaları modeli etiketi özelliklerinin değerleri olarak nasıl değiştireceğini belirlemek için ilgili özellikleri etikette bağımlılığı çeşitli. Bir regresyon algoritmasıdır girişi bir örnekler etiketlerle bilinen değerler kümesidir. Bir regresyon algoritmasıdır çıktısı her yeni özellik kümesi, giriş etiketi değerini tahmin etmek için kullanabileceğiniz bir işlev ise. Regresyon senaryolarına örnekler şunlardır:

* Ev fiyatları yatak, konum ve boyut sayısı gibi merkezi özniteliklerini temel alarak tahmin etme.
* Geçmiş verileri ve geçerli pazar eğilimlerine göre gelecekteki hisse senedi fiyatlarını tahmin etme.
* Bütçelerini reklam üzerinde temel bir ürün satışları tahmin etme.

### <a name="regression-training-algorithms"></a>Regresyon eğitim algoritmaları

Aşağıdaki algoritmaları kullanarak bir regresyon modeli eğitmek:

* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>
* <xref:Microsoft.ML.Trainers.OlsTrainer>
* <xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>
* <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>

## <a name="clustering"></a>Kümeleme

Bir [Denetimsiz machine learning](glossary.md#unsupervised-machine-learning) benzer özelliklere içeren kümeler halinde veri grubu örnekleri için kullanılan görev. Kümeleme de olmayan mantıksal olarak türettiğiniz DataSet ilişkileri tanımlamak için gözatma veya basit gözlem tarafından kullanılabilir. Giriş ve çıkışları kümeleme algoritması, seçilen metodolojiyi üzerinde bağlıdır. Bir dağıtım, kütle Merkezi, bağlantı veya yoğunluk yaklaşımla alabilir. ML.NET şu anda K-ortalamaları Kümelemesi kullanarak kütle merkezi tabanlı bir yaklaşımı destekler. Kümeleme senaryolarına örnekler şunlardır:

* Otel Konukları alışkanlıkları ve Otel seçeneği özelliklere göre parçalarını anlama.
* Müşteri kesimleri ve demografik bilgilere bağlı hedeflenen reklam kampanyaları oluşturmanıza yardımcı olmak için tanımlayıcı.
* Üretim ölçümleri temel alarak envanteri halinde kategorilere ayrılması.

### <a name="clustering-training-algorithms"></a>Kümeleme eğitim algoritmaları

Aşağıdaki algoritması kullanarak bir kümeleme modeli eğitmek:

* <xref:Microsoft.ML.Trainers.KMeansTrainer>

## <a name="anomaly-detection"></a>Anomali algılama

Bu görevi, asıl bileşen analiz (PCA) kullanarak bir anomali algılama modeli oluşturur. PCA tabanlı Anomali algılama geçerli işlemler gibi bir sınıf eğitim verilerini almak kolay, ancak yeterli örnekleri hedeflenen anomali elde etmek zor olduğu senaryolar modelinde oluşturmanıza yardımcı olur.

İç yapısını gösterir ve veri varyans açıklar machine learning'de PCA kurulan bir teknik keşif veri analizi sık kullanılır. Birden fazla değişken içeren verileri analiz ederek PCA çalışır. Bu değişkenler arasındaki bağıntıları arar ve en iyi sonuçlar farklılıkları yakalar değerlerinin birleşimi belirler. Bu birleşik özellik değerleri, asıl bileşen olarak adlandırılıyordu daha kompakt bir özellik alanı oluşturmak için kullanılır.

Anomali algılama machine learning'de birçok önemli görevleri kapsar:

* Olası sahte işlem tanımlama.
* Ağa yetkisiz erişim oluştu olarak görülebilecek desenler öğrenme.
* Hastalara anormal kümelerini bulma.
* Değer denetimi bir sisteme girdi.

Anomalileri tanımına göre nadir olayları olduğundan, temsili bir örnek model için kullanılacak veri toplamak zor olabilir. Bu kategoride bulunan algoritmaları özellikle imbalanced veri kümelerini kullanarak oluşturma ve eğitim modeli çekirdek sorunları gidermek üzere tasarlanmıştır.

### <a name="anomaly-detection-training-algorithms"></a>Anomali algılama eğitim algoritmaları

Aşağıdaki algoritması kullanarak bir anomali algılama modeli eğitmek:

* <xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>

## <a name="ranking"></a>Derecelendirme

Derecelendirme görev derecelendiricisini etiketli örnekleri bir dizi oluşturur. Bu örnek kümesi ile puanlanmış örnek grupları oluşan bir tetikleyicisi. {0, 1, 2, 3, 4} her örneği için olan derecelendirme etiketleri.  Derecelendiricisini bilinmeyen puanlarının her örneği için yeni derece örneği gruplara eğitildi. ML.NET derecelendirme öğrencileriyle olan [öğrenilen makine derecelendirme](https://en.wikipedia.org/wiki/Learning_to_rank) bağlı.

### <a name="ranking-training-algorithms"></a>Sıralama eğitim algoritmaları

Aşağıdaki algoritmaları ile bir derecelendirme modeli eğitmek:

* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>

## <a name="recommendation"></a>Öneri

Bir öneri görevi önerilen ürünleri veya hizmetleri listesi oluşturmayı etkinleştirir. ML.NET kullanan [matris factorization (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), [işbirliğine dayalı filtreleme](https://en.wikipedia.org/wiki/Collaborative_filtering) geçmiş ürün derecelendirmesi veri Kataloğu'nda varsa önerileri için algoritma. Örneğin, kullanıcılarınız için geçmiş film derecelendirmesi verilere sahip ve sonraki izleyin okunduğunun diğer filmler önermek istediğiniz.

### <a name="recommendation-training-algorithms"></a>Öneri eğitim algoritmaları

Aşağıdaki algoritması ile bir öneri modeli eğitmek:

* <xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>
