---
title: Makine öğrenimi görevleri
description: ML.NET sürümünde desteklenen farklı makine öğrenimi görevlerini ve ilişkili görevleri keşfedebilirsiniz.
ms.custom: seodec18
ms.date: 04/23/2019
author: natke
ms.openlocfilehash: bcd967c11156ca9b837631560e78722b13fc7ae0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630055"
---
# <a name="machine-learning-tasks-in-mlnet"></a>ML.NET 'de makine öğrenimi görevleri

Bir makine öğrenimi modeli oluştururken, öncelikle verilerinize ulaşmak için ne kadar atlama yapabileceğinizi tanımlamanız gerekir. Bu, durumunuz için doğru makine öğrenimi görevini seçmenizi sağlar. Aşağıdaki listede, aralarından seçim yapabileceğiniz farklı makine öğrenimi görevleri ve bazı yaygın kullanım durumları açıklanmaktadır.

Senaryolarınız için hangi görevin çalıştığına karar verdikten sonra, modelinize eğitebilmeniz için en iyi algoritmayı seçmeniz gerekir. Kullanılabilir algoritmalar her görevin bölümünde listelenmiştir.

## <a name="binary-classification"></a>İkili sınıflandırma

İki sınıftan (kategori) hangisinin ait olduğunu tahmin etmek için kullanılan [denetimli bir makine öğrenimi](glossary.md#supervised-machine-learning) görevi. Sınıflandırma algoritmasının girişi, her etiketin 0 veya 1 tamsayısı olduğu etiketli örnekler kümesidir. İkili sınıflandırma algoritmasının çıktısı, yeni etiketlenmiş olmayan örneklerin sınıfını tahmin etmek için kullanabileceğiniz bir sınıflandırıcıdır. İkili sınıflandırma senaryolarına örnek olarak şunlar verilebilir:

* [Twitter açıklamalarının](../tutorials/sentiment-analysis.md) yaklaşımını "pozitif" veya "negatif" olarak anlama.
* Hasta 'in belirli bir sapmasına sahip olup olmadığını tanılama.
* E-postayı "istenmeyen posta" olarak işaretlemek için bir karar verme.
* Fotoğrafın bir köpek mi yoksa meyve mi içerdiğini belirleme.

Daha fazla bilgi için Vikipde bulunan [ikili sınıflandırma](https://en.wikipedia.org/wiki/Binary_classification) makalesine bakın.

### <a name="binary-classification-trainers"></a>İkili sınıflandırma traiciler

Aşağıdaki algoritmaları kullanarak bir ikili sınıflandırma modeli eğitebilirsiniz:

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

### <a name="binary-classification-inputs-and-outputs"></a>İkili sınıflandırma girişleri ve çıkışları

İkili sınıflandırmayla en iyi sonuçları elde etmek için eğitim verilerinin dengelenmesi gerekir (yani, pozitif ve negatif eğitim verilerinin eşit sayısı). Eksik değerler, eğitimin önüne alınmalıdır.

Giriş etiketi sütun verileri <xref:System.Boolean>olmalıdır.
Giriş özellikleri sütun verileri sabit boyutlu bir vektör <xref:System.Single>olmalıdır.

Bu traipler aşağıdaki sütunları çıktı:

| Çıkış sütunu adı | Sütun türü | Açıklama|
| -- | -- | -- |
| `Score` | <xref:System.Single> | Model tarafından hesaplanan ham puan|
| `PredictedLabel` | <xref:System.Boolean> | Puanınızın işaretine göre öngörülen etiket. Negatif puan ile eşlenir `false` ve bir pozitif puan ile `true`eşlenir.|

## <a name="multiclass-classification"></a>Birden çok Lass sınıflandırması

Bir veri örneğinin sınıfını (kategori) tahmin etmek için kullanılan [denetimli bir makine öğrenimi](glossary.md#supervised-machine-learning) görevi. Sınıflandırma algoritmasının girişi, etiketlenmiş bir örnek kümesidir. Her etiket normalde metin olarak başlar. Daha sonra TermTransform aracılığıyla çalıştırılır. Bu, anahtar (sayısal) türüne dönüştürür. Bir sınıflandırma algoritmasının çıktısı, yeni etiketlenmiş olmayan örneklerin sınıfını tahmin etmek için kullanabileceğiniz bir sınıflandırıcıdır. Çok sınıflı sınıflandırma senaryolarına örnek olarak şunlar verilebilir:

* Bir köpek "Sıberian Husky", "altın Retriever", "Pookıl" vb. olarak belirlenir.
* Film incelemelerini "pozitif", "nötr" veya "negatif" olarak anlama.
* Otel incelemelerini "konum", "Price", "cleanliness" vb. olarak kategorilere ayırma.

Daha fazla bilgi için Vikipde bulunan [birden çok sınıf sınıflandırması](https://en.wikipedia.org/wiki/Multiclass_classification) makalesine bakın.

>[!NOTE]
>Bunlardan biri, birden çok Lass veri kümesi üzerinde işlem yapmak için herhangi bir [ikili sınıflandırmanın yükseltimidir](#binary-classification) . [Vikipedi] hakkında daha https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest) fazla bilgi (.

### <a name="multiclass-classification-trainers"></a>Birden çok Lass sınıflandırma traipleyiciler

Aşağıdaki eğitim algoritmalarını kullanarak çok bir Lass sınıflandırma modelini eğitebilirsiniz:

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer> 
* <xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer> 
* <xref:Microsoft.ML.Trainers.OneVersusAllTrainer>
* <xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer> 

### <a name="multiclass-classification-inputs-and-outputs"></a>Birden çok Lass sınıflandırma girişleri ve çıkışları

Giriş etiketi sütun verileri, [anahtar](xref:Microsoft.ML.Data.KeyDataViewType) türünde olmalıdır.
Özellik sütunu sabit boyutlu bir vektör <xref:System.Single>olmalıdır.

Bu, aşağıdaki çıkışları verir:

| Çıkış adı | Tür | Açıklama|
| -- | -- | -- |
| `Score` | Vektör<xref:System.Single> | Tüm sınıfların puanları. Daha yüksek değer, ilişkili sınıfa düşecek daha büyük olasılık anlamına gelir. İ-th öğesi en büyük değere sahipse, tahmin edilen etiket dizini i olur. Sıfır tabanlı dizin olduğunu unutmayın. |
| `PredictedLabel` | [anahtar](xref:Microsoft.ML.Data.KeyDataViewType) türü | Tahmin edilen etiketin dizini. Değeri i ise, gerçek etiket anahtar değerli giriş etiketi türündeki ı-TH kategorisi olacaktır. |

## <a name="regression"></a>Regresyon

Bir ilişkili özellikler kümesinden etiketin değerini tahmin etmek için kullanılan [denetimli bir makine öğrenimi](glossary.md#supervised-machine-learning) görevi. Etiket herhangi bir gerçek değer olabilir ve sınıflandırma görevlerinde olduğu gibi sınırlı bir değer kümesinden değildir. Regresyon algoritmaları, özelliğin değerleri farklılaştırılmadıkça etiketin nasıl değiştirileceğini anlamak için ilgili özellikler üzerindeki etiketin bağımlılığını modelleyebilir. Regresyon algoritmasının girişi, bilinen değerlerin etiketlerine sahip bir örnek kümesidir. Regresyon algoritmasının çıktısı, herhangi bir yeni giriş özellikleri kümesi için etiket değerini tahmin etmek üzere kullanabileceğiniz bir işlevdir. Regresyon senaryolarına örnek olarak şunlar verilebilir:

* Yatak odası, konum veya boyut gibi ev özniteliklerini temel alan ev fiyatlarını tahmin etme.
* Geçmiş verileri ve geçerli pazar eğilimlerini temel alarak gelecekteki stok fiyatlarını tahmin etme.
* Tanıtım bütçeleri temelinde bir ürünün satışlarını tahmin etme.

### <a name="regression-trainers"></a>Gerileme tracılar

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

### <a name="regression-inputs-and-outputs"></a>Regresyon girişleri ve çıktılar

Giriş etiketi sütun verileri <xref:System.Single>olmalıdır.

Bu görev için şu kadar traipler aşağıda verilmiştir:

| Çıkış adı | Tür | Açıklama|
| -- | -- | -- |
| `Score` | <xref:System.Single> | Model tarafından tahmin edilen ham puan |

## <a name="clustering"></a>Lenmesi

Benzer özellikler içeren kümelere veri örneklerini gruplamak için kullanılan, denetimli bir [makine öğrenimi](glossary.md#unsupervised-machine-learning) görevi. Kümeleme, göz atma veya basit gözlemlemeye göre mantıksal olarak türeteceğiniz bir veri kümesindeki ilişkileri tanımlamak için de kullanılabilir. Bir kümeleme algoritmasının giriş ve çıkışları, seçilen metodolojiye bağlıdır. Dağıtım, centroıd, bağlantı veya Yoğunluk tabanlı yaklaşıma sahip olabilirsiniz. ML.NET şu anda K-anlamı Kümelemesi kullanarak centroıd tabanlı bir yaklaşımı desteklemektedir. Kümeleme senaryolarına örnekler şunlardır:

* Otel seçeneklerinin alışkanlıklarını ve özelliklerini temel alarak otel konuklarının segmentlerini anlama.
* Hedeflenen reklam kampanyaları oluşturmaya yardımcı olmak için müşteri segmentlerini ve demografik tanımlama.
* Stoku üretim ölçümlerine göre kategorilere ayırma.

### <a name="clustering-trainer"></a>Kümeleme eğitmen

Aşağıdaki algoritmayı kullanarak bir kümeleme modeli eğitebilirsiniz:

* <xref:Microsoft.ML.Trainers.KMeansTrainer> 

### <a name="clustering-inputs-and-outputs"></a>Kümeleme girişleri ve çıkışları

Giriş özellikleri verileri olmalıdır <xref:System.Single>. Etiket gerekli değildir.

Bu, aşağıdaki çıkışları verir:

| Çıkış adı | Tür | Açıklama|
| -- | -- | -- |
| `Score` | vektör<xref:System.Single> | Verilen veri noktasının tüm kümelerdeki mesafeler ' centriods |
| `PredictedLabel` | [anahtar](xref:Microsoft.ML.Data.KeyDataViewType) türü | Model tarafından tahmin edilen en yakın küme dizini. |

## <a name="anomaly-detection"></a>Anomali algılama

Bu görev, sorumlu bileşen analizi (PCA) kullanarak bir anomali algılama modeli oluşturur. PCA tabanlı anomali algılama, geçerli işlemler gibi bir sınıftan eğitim verileri elde etmek, ancak hedeflenen bozukluklar için yeterli örnek elde etmek zor olan senaryolarda bir model oluşturmanıza yardımcı olur.

Machine Learning 'de sağlanan bir teknik, PCA verilerin iç yapısını açığa çıkardığından ve verilerdeki varyansı bildirdiği için araştırmacı veri analizinde sıklıkla kullanılır. PCA birden çok değişken içeren verileri analiz ederek işe yarar. Değişkenler arasında bağıntılar arar ve sonuçların farklarını en iyi şekilde yakalayan değerlerin birleşimini belirler. Bu Birleşik özellik değerleri, sorumlu bileşenleri olarak adlandırılan daha kompakt bir özellik alanı oluşturmak için kullanılır.

Anomali algılama, Machine Learning 'de birçok önemli görevi kapsar:

* Potansiyel olarak sahte olan işlemleri tanımlama.
* Ağ üzerinden izinsiz giriş gerçekleştiğini gösteren öğrenme desenleri.
* Anormal bir hastaların kümelerini bulma.
* Sisteme girilen değerler denetleniyor.

Anomali, tanıma göre nadir olaylar olduğundan, modelleme için kullanılacak verilerin temsili bir örneğini toplamak zor olabilir. Bu kategoriye dahil edilen algoritmalar, özellikle de imdendengelenmiş veri kümeleri kullanılarak modeller oluşturma ve eğitim konusunda temel zorlukları karşılamak üzere tasarlanmıştır.

### <a name="anomaly-detection-trainer"></a>Anomali algılama

Aşağıdaki algoritmayı kullanarak bir anomali algılama modeli eğitebilirsiniz:

* <xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>

### <a name="anomaly-detection-inputs-and-outputs"></a>Anomali algılama girişleri ve çıkışları

Giriş özellikleri sabit boyutlu bir vektör <xref:System.Single>olmalıdır.

Bu, aşağıdaki çıkışları verir:

| Çıkış adı | Tür | Açıklama|
| -- | -- | -- |
| `Score` | <xref:System.Single> | Anomali algılama modeli tarafından hesaplanan negatif olmayan, sınırlandırılmamış puan |

## <a name="ranking"></a>Sıralamasına

Bir derecelendirme görevi bir etiketli örnekler kümesinden derecelendiricisini oluşturur. Bu örnek küme, verilen ölçütlerle puanlanbir örnek gruplarından oluşur. Sıralama etiketleri her örnek için {0, 1, 2, 3, 4}.  Derecelendiricisini, her örnek için bilinmeyen puanları olan yeni örnek gruplarını derecelendirmek için eğitim sağlar. ML.NET derecelendirmesi öğrenenler, [makine tarafından öğrenilen sıralama](https://en.wikipedia.org/wiki/Learning_to_rank) tabanlıdır.

### <a name="ranking-training-algorithms"></a>Derecelendirme eğitimi algoritmaları

Aşağıdaki algoritmalarla bir derecelendirme modeli eğitebilirsiniz:

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer> 

### <a name="ranking-input-and-outputs"></a>Sıralama girişi ve çıkışları

Giriş etiketi veri türü, [anahtar](xref:Microsoft.ML.Data.KeyDataViewType) türünde veya <xref:System.Single>olmalıdır. Etiketin değeri ilgiyi belirler, burada daha yüksek değerler daha yüksek uygunluğu gösterir. Etiket bir [anahtar](xref:Microsoft.ML.Data.KeyDataViewType) türü ise, anahtar dizin, en küçük dizin en az ilgili olan ilgi değeridir. Etiket bir <xref:System.Single>ise, daha büyük değerler daha yüksek uygunluğu gösterir.

Özellik verileri sabit boyutlu bir vektör <xref:System.Single> olmalıdır ve giriş satırı grup sütunu [anahtar](xref:Microsoft.ML.Data.KeyDataViewType) türünde olmalıdır.

Bu, aşağıdaki çıkışları verir:

| Çıkış adı | Tür | Açıklama|
| -- | -- | -- |
| `Score` | <xref:System.Single> | Tahmin belirlenmesi için model tarafından hesaplanan, sınırlandırılmamış puan |

## <a name="recommendation"></a>Öneri

Öneri görevi, önerilen ürünlerin veya hizmetlerin bir listesini üretmenizi mümkün. ML.NET, kataloğunuzda geçmiş ürün derecelendirme verileri olduğunda öneriler için [birlikte](https://en.wikipedia.org/wiki/Collaborative_filtering) çalışan bir filtreleme algoritması olan [matris factorleştirme (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29)kullanır. Örneğin, kullanıcılarınız için geçmiş film derecelendirme verileri vardır ve diğer filmleri daha sonra izlemek isteyebilirsiniz.

### <a name="recommendation-training-algorithms"></a>Öneri eğitimi algoritmaları

Aşağıdaki algoritmayla bir öneri modeli eğitebilirsiniz:

* <xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>
