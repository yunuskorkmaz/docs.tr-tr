---
title: Makine öğrenimi görevleri
description: ML.NET desteklenen farklı makine öğrenimi görevlerini ve ilişkili görevleri keşfedin.
ms.date: 12/23/2019
ms.openlocfilehash: 6cd41065e668375537b9816ef7a208a65e0a523b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399205"
---
# <a name="machine-learning-tasks-in-mlnet"></a>ML.NET makine öğrenimi görevleri

Makine öğrenimi görevi, sorulan soruna veya soruya ve kullanılabilir verilere dayalı olarak yapılan tahmin veya çıkarım türüdür. Örneğin, sınıflandırma görevi kategorilere veri atar ve kümeleme görev grupları verileri benzerliğe göre gruplandırır.

Makine öğrenimi görevleri, açıkça programlanmaktan çok verilerdeki desenlere dayanır.

Bu makalede, ML.NET ve bazı yaygın kullanım durumlarında seçebileceğiniz farklı makine öğrenimi görevleri açıklanmaktadır.

Senaryonuz için hangi görevin işe yaradığına karar verdikten sonra, modelinizi eğitmek için en iyi algoritmayı seçmeniz gerekir. Kullanılabilir algoritmalar her görev için bölümde listelenir.

## <a name="binary-classification"></a>İkili sınıflandırma

İki sınıftan (kategoride) bir veri örneğinin ait olduğunu tahmin etmek için kullanılan [denetlenen makine öğrenimi](glossary.md#supervised-machine-learning) görevi. Sınıflandırma algoritmasının girişi, her etiketin 0 veya 1'lik bir tamsayı olduğu etiketli örnekler kümesidir. İkili sınıflandırma algoritmasının çıktısı, yeni etiketlenmemiş örneklerin sınıfını tahmin etmek için kullanabileceğiniz bir sınıflandırmadır. İkili sınıflandırma senaryolarına örnek olarak şunlar verilebilir:

* [Twitter yorumlarının duygularını](../tutorials/sentiment-analysis.md) ya "olumlu" ya da "olumsuz" olarak anlamak.
* Hastanın belirli bir hastalığı olup olmadığını teşhis etmek.
* Bir e-postayı "spam" olarak işaretleme kararı almak veya işaretlememek.
* Bir fotoğrafın köpek veya meyve gibi belirli bir öğeyi içerip içermediğini belirleme.

Daha fazla bilgi için Vikipedi'deki [İkili sınıflandırma](https://en.wikipedia.org/wiki/Binary_classification) makalesine bakın.

### <a name="binary-classification-trainers"></a>İkili sınıflandırma eğitmenleri

Aşağıdaki algoritmaları kullanarak ikili sınıflandırma modelini eğitebilirsiniz:

* <xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>
* <xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedBinaryTrainer>
* <xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer>
* <xref:Microsoft.ML.Trainers.PriorTrainer>
* <xref:Microsoft.ML.Trainers.LinearSvmTrainer>

### <a name="binary-classification-inputs-and-outputs"></a>İkili sınıflandırma giriş ve çıkışları

İkili sınıflandırma ile en iyi sonuçlar için, eğitim verileri dengeli olmalıdır (yani, pozitif ve negatif eğitim verilerinin eşit sayıda). Eksik değerler eğitimden önce ele alınmalıdır.

Giriş etiketi sütun verileri <xref:System.Boolean>.
Giriş özellikleri sütun verileri sabit boyutlu bir <xref:System.Single>vektör olmalıdır.

Bu eğitmenler aşağıdaki sütunları çıktı:

| Çıktı Sütun Adı | Sütun Türü | Açıklama|
| -- | -- | -- |
| `Score` | <xref:System.Single> | Model tarafından hesaplanan ham puan|
| `PredictedLabel` | <xref:System.Boolean> | Skor işaretine göre öngörülen etiket. Negatif bir puan `false` haritaları ve pozitif `true`bir puan haritaları .|

## <a name="multiclass-classification"></a>Çok sınıflı sınıflandırma

Bir veri örneğinin sınıfını (kategorisini) tahmin etmek için kullanılan [denetlenen makine öğrenimi](glossary.md#supervised-machine-learning) görevi. Sınıflandırma algoritmasının girişi, etiketli örnekler kümesidir. Her etiket normalde metin olarak başlar. Daha sonra, Anahtar (sayısal) türüne dönüştüren TermTransform üzerinden çalıştırılır. Sınıflandırma algoritmasının çıktısı, yeni etiketlenmemiş örneklerin sınıfını tahmin etmek için kullanabileceğiniz bir sınıflandırma algoritmasıdır. Çok sınıflı sınıflandırma senaryolarına örnek olarak şunlar verilebilir:

* Bir "Sibirya Husky", "Golden Retriever", "Kaniş" vb gibi bir köpek cins belirlenmesi
* Film yorumlarını "olumlu", "tarafsız" veya "olumsuz" olarak anlamak.
* Otel yorumlarını "konum", "fiyat", "temizlik" vb. olarak kategorilere ayırmak.

Daha fazla bilgi için Vikipedi'deki [Çok Sınıflı sınıflandırma](https://en.wikipedia.org/wiki/Multiclass_classification) makalesine bakın.

>[!NOTE]
>Bir vs tüm yükseltmeleri herhangi bir [ikili sınıflandırma öğrenen](#binary-classification) çoklu sınıf veri kümeleri üzerinde hareket etmek. [Vikipedi] hakkında dahahttps://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest)fazla bilgi ( .

### <a name="multiclass-classification-trainers"></a>Çok sınıflı sınıflandırma eğitmenleri

Aşağıdaki eğitim algoritmalarını kullanarak çok sınıflı bir sınıflandırma modeli eğitebilirsiniz:

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.OneVersusAllTrainer>
* <xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer>
* <xref:Microsoft.ML.Vision.ImageClassificationTrainer>

### <a name="multiclass-classification-inputs-and-outputs"></a>Çok sınıflı sınıflandırma giriş ve çıktıları

Giriş etiketi sütun verileri [anahtar](xref:Microsoft.ML.Data.KeyDataViewType) türü olmalıdır.
Özellik sütunu sabit boyutlu bir <xref:System.Single>vektör olmalıdır.

Bu eğitmen aşağıdaki çıkışları:

| Çıktı Adı | Tür | Açıklama|
| -- | -- | -- |
| `Score` | Vektör<xref:System.Single> | Tüm sınıfların puanları. Daha yüksek değer, ilişkili sınıfa düşme olasılığının daha yüksek olması anlamına gelir. i-th öğesi en büyük değere sahipse, öngörülen etiket dizini i olacaktır. I sıfır tabanlı dizin olduğunu unutmayın. |
| `PredictedLabel` | [anahtar](xref:Microsoft.ML.Data.KeyDataViewType) türü | Tahmin edilen etiketin dizini. Değeri i ise, gerçek etiket anahtar değerli giriş etiketi türünde i-th kategorisi olacaktır. |

## <a name="regression"></a>Regresyon

İlgili özellikler kümesinden etiketin değerini tahmin etmek için kullanılan [denetlenen makine öğrenimi](glossary.md#supervised-machine-learning) görevi. Etiket herhangi bir gerçek değere sahip olabilir ve sınıflandırma görevlerinde olduğu gibi sonlu bir değer kümesinden değildir. Regresyon algoritmaları, özelliklerin değerleri farklı olarak etiketin nasıl değişeceğini belirlemek için etiketin ilgili özellikleriüzerindeki bağımlılığını modeller. Bir regresyon algoritması girişi bilinen değerlerin etiketleri ile örnekler kümesidir. Bir regresyon algoritmasının çıktısı, herhangi bir yeni giriş özellikleri kümesi için etiket değerini tahmin etmek için kullanabileceğiniz bir işlevdir. Gerileme senaryolarına örnek olarak şunlar verilebilir:

* Yatak odası sayısı, yer veya boyut gibi ev özelliklerine göre ev fiyatları tahmin.
* Geçmiş verilere ve mevcut piyasa eğilimlerine dayalı olarak gelecekteki hisse senedi fiyatlarını tahmin etmek.
* Reklam bütçelerine dayalı bir ürünün satışını tahmin etme.

### <a name="regression-trainers"></a>Regresyon eğitmenleri

Aşağıdaki algoritmaları kullanarak bir regresyon modeli eğitebilirsiniz:

* <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>
* <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>
* <xref:Microsoft.ML.Trainers.OlsTrainer>
* <xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>

### <a name="regression-inputs-and-outputs"></a>Regresyon giriş ve çıkışları

Giriş etiketi sütun verileri <xref:System.Single>.

Bu görev için eğitmenler aşağıdaki çıktı çıktı:

| Çıktı Adı | Tür | Açıklama|
| -- | -- | -- |
| `Score` | <xref:System.Single> | Model tarafından öngörülen ham puan |

## <a name="clustering"></a>Kümeleme

Veri örneklerini benzer özelliklere sahip kümeler halinde gruplandırmak için kullanılan [denetimsiz bir makine öğrenimi](glossary.md#unsupervised-machine-learning) görevi. Kümeleme, bir veri kümesinde, tarama veya basit gözlem le mantıksal olarak elde edilemeyeceğiniz ilişkileri tanımlamak için de kullanılabilir. Kümeleme algoritmasının giriş ve çıkışları seçilen metodolojiye bağlıdır. Bir dağılım, merkez, bağlantı veya yoğunluk tabanlı bir yaklaşım alabilirsiniz. ML.NET şu anda K-Means kümeleme kullanarak bir santrioit tabanlı bir yaklaşım destekler. Kümeleme senaryolarına örnek olarak şunlar verilebilir:

* Otel konuklarının yaşam ve otel seçeneklerinin özelliklerine göre bölümlerini anlamak.
* Hedefli reklam kampanyaları oluşturmaya yardımcı olmak için müşteri segmentlerini ve demografik özellikleri belirlemek.
* Üretim ölçümlerine göre envanteri kategorilere ayırma.

### <a name="clustering-trainer"></a>Kümeleme eğitmeni

Aşağıdaki algoritmayı kullanarak bir kümeleme modelini eğitebilirsiniz:

* <xref:Microsoft.ML.Trainers.KMeansTrainer>

### <a name="clustering-inputs-and-outputs"></a>Girdi ve çıktıları kümeleme

Giriş özellikleri verileri . <xref:System.Single> Etiket gerekmez.

Bu eğitmen aşağıdaki çıkışları:

| Çıktı Adı | Tür | Açıklama|
| -- | -- | -- |
| `Score` | vektörü<xref:System.Single> | Verilen verilerin tüm kümelerin merkezlerine olan uzaklıkları |
| `PredictedLabel` | [anahtar](xref:Microsoft.ML.Data.KeyDataViewType) türü | Model tarafından öngörülen en yakın kümenin dizin. |

## <a name="anomaly-detection"></a>Anormallik algılama

Bu görev, Temel Bileşen Analizi (PCA) kullanarak bir anomali algılama modeli oluşturur. PCA Tabanlı Anomali Algılama, geçerli işlemler gibi bir sınıftan eğitim verilerini almanın kolay olduğu, ancak hedeflenen anomalilerden yeterli örnek almanın zor olduğu senaryolarda bir model oluşturmanıza yardımcı olur.

Makine öğreniminde yerleşik bir teknik olan PCA, verilerin iç yapısını ortaya çıkardığı ve verilerdeki varyansı açıkladığı için araştırmacı veri analizinde sıklıkla kullanılır. PCA, birden çok değişken içeren verileri analiz ederek çalışır. Değişkenler arasındaki bağıntıları arar ve sonuçlardaki farklılıkları en iyi yakalayan değerlerin birleşimini belirler. Bu birleştirilmiş özellik değerleri, ana bileşenler adı verilen daha kompakt bir özellik alanı oluşturmak için kullanılır.

Anomali tespiti makine öğreniminde birçok önemli görevi kapsar:

* Sahte olabilecek hareketleri tanımlama.
* Ağ izinsiz girişinin gerçekleştiğini gösteren öğrenme kalıpları.
* Anormal hasta kümeleri bulmak.
* Sisteme girilen değerleri denetleme.

Anomaliler tanım olarak nadir olaylar olduğundan, modelleme için kullanılacak temsili bir veri örneği toplamak zor olabilir. Bu kategoride yer alan algoritmalar özellikle dengesiz veri kümeleri kullanarak oluşturma ve eğitim modellerinin temel zorluklarını ele almak üzere tasarlanmıştır.

### <a name="anomaly-detection-trainer"></a>Anomali tespit eğitmeni

Aşağıdaki algoritmayı kullanarak bir anomali algılama modeli eğitebilirsiniz:

* <xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>

### <a name="anomaly-detection-inputs-and-outputs"></a>Anomali algılama giriş ve çıkışları

Giriş özellikleri sabit boyutlu bir vektör <xref:System.Single>olmalıdır.

Bu eğitmen aşağıdaki çıkışları:

| Çıktı Adı | Tür | Açıklama|
| -- | -- | -- |
| `Score` | <xref:System.Single> | Anomali algılama modeli ile hesaplanan negatif olmayan, sınırsız skor |
| `PredictedLabel` | <xref:System.Boolean> | Girişin bir anormallik olup olmadığını gösteren gerçek/yanlış değer (PredictedLabel=true) (PredictedLabel=false) |

## <a name="ranking"></a>Sıralama

Sıralama görevi, etiketli örnekler kümesinden bir sıralama oluşturucusu belirler. Bu örnek kümesi, belirli bir ölçütle puanlanabilecek örnek gruplarından oluşur. Sıralama etiketleri her örnek için { 0, 1, 2, 3, 4 } 'dir.  Ranker, her örnek için bilinmeyen puanları olan yeni örnek gruplarını sıralamak üzere eğitilir. ML.NET sıralama öğrenenler [makine tabanlı sıralama öğrendim.](https://en.wikipedia.org/wiki/Learning_to_rank)

### <a name="ranking-training-algorithms"></a>Sıralama eğitim algoritmaları

Bir sıralama modelini aşağıdaki algoritmalarla eğitebilirsiniz:

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>

### <a name="ranking-input-and-outputs"></a>Giriş ve çıktıları sıralama

Giriş etiketi veri türü [anahtar](xref:Microsoft.ML.Data.KeyDataViewType) türü <xref:System.Single>veya . Etiketin değeri, daha yüksek değerlerin daha yüksek alaka düzeyini gösterdiği alaka düzeyini belirler. Etiket [anahtar](xref:Microsoft.ML.Data.KeyDataViewType) türüyse, anahtar dizin, en küçük dizin en az alakalı olduğu alaka düzeyi değeridir. Etiket bir <xref:System.Single>ise, daha büyük değerler daha yüksek alaka gösterir.

Özellik verileri sabit boyutlu bir <xref:System.Single> vektör olmalı ve giriş satırı grup sütunu [anahtar](xref:Microsoft.ML.Data.KeyDataViewType) türü olmalıdır.

Bu eğitmen aşağıdaki çıkışları:

| Çıktı Adı | Tür | Açıklama|
| -- | -- | -- |
| `Score` | <xref:System.Single> | Tahminbelirlemek için model tarafından hesaplanan sınırsız puan |

## <a name="recommendation"></a>Öneri

Öneri görevi, önerilen ürün veya hizmetlerin bir listesini oluşturmayı sağlar. ML.NET, kataloğunuzda geçmiş ürün derecelendirme verileri varsa öneriler için ortak bir [filtreleme algoritması](https://en.wikipedia.org/wiki/Collaborative_filtering) olan [Matris çarpanalizasyonu (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29)kullanır. Örneğin, kullanıcılarınız için geçmiş film derecelendirme verilerine sahipsiniz ve bir sonraki izleme olasılıkları yüksek olan diğer filmleri önermek istiyorsunuz.

### <a name="recommendation-training-algorithms"></a>Öneri eğitim algoritmaları

Bir öneri modelini aşağıdaki algoritmayla eğitebilirsiniz:

* <xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>

## <a name="forecasting"></a>Tahmin etme

Tahmin görevi, gelecekteki davranışlar hakkında öngörülerde bulunmak için geçmiş zaman serileri verilerini kullanır. Tahmin için geçerli senaryolar arasında hava tahmini, mevsimsel satış tahminleri ve tahmine dayalı bakım,

### <a name="forecasting-trainers"></a>Tahmin eğitmenleri

Bir tahmin modelini aşağıdaki algoritmayla eğitebilirsiniz:

<xref:Microsoft.ML.TimeSeriesCatalog.ForecastBySsa*>
