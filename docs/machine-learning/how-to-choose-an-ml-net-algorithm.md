---
title: ML.NET algoritması nasıl seçilir?
description: Makine öğrenimi modeliniz için ML.NET algoritması seçme yi öğrenin
ms.topic: overview
ms.date: 06/05/2019
ms.openlocfilehash: 0fed33203c02303e37e47f548e08ec131eeb1c77
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75740001"
---
# <a name="how-to-choose-an-mlnet-algorithm"></a>ML.NET algoritması nasıl seçilir?

Her [ML.NET görev için,](resources/tasks.md)seçim için birden çok eğitim algoritması vardır. Hangisini seçeceğiniz, çözmeye çalıştığınız soruna, verilerinizin özelliklerine ve mevcut bilgi işlem ve depolama kaynaklarına bağlıdır. Bir makine öğrenme modeli nin eğitiminin yinelemeli bir süreç olduğunu unutmayın. En iyi çalışan algoritmayı bulmak için birden çok algoritma denemeniz gerekebilir.

Algoritmalar **özellikleri**üzerinde çalışır. Özellikler, giriş verilerinizden hesaplanan sayısal değerlerdir. Bunlar makine öğrenimi algoritmaları için en uygun girdilerdir. Bir veya daha fazla veri dönüşümlerini kullanarak ham giriş verilerinizi özelliklere [dönüştürürsunuz.](resources/transforms.md) Örneğin, metin verileri sözcük sayımları kümesine ve sözcük birleşimi sayımlarına dönüştürülür. Özellikler, veri dönüşümleri kullanılarak ham bir veri türünden çıkarıldıktan **sonra, bunlara featurized**olarak adlandırılırlar. Örneğin, featurized metin veya featurized görüntü verileri.

## <a name="trainer--algorithm--task"></a>Eğitmen = Algoritma + Görev

Algoritma, bir **model**üretmek için yürüten matematiktir. Farklı algoritmalar farklı özelliklere sahip modeller üretir.

ML.NET ile aynı algoritma farklı görevlere uygulanabilir. Örneğin, Stokhastik Çift Eşgüdümlü Tırmanış İkili Sınıflandırma, Çok Sınıflı Sınıflandırma ve Regresyon için kullanılabilir. Fark, algoritmanın çıktısının görevle eşleşecek şekilde nasıl yorumlanacağıdır.

Her algoritma/görev birleşimi için ML.NET, eğitim algoritmasını yürüten ve yorumlama yapan bir bileşen sağlar. Bu bileşenlere eğitmen denir. Örneğin, <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer> **Regresyon** görevine uygulanan **StochasticDualCoordinatedAscent** algoritmasını kullanır.

## <a name="linear-algorithms"></a>Doğrusal algoritmalar

Doğrusal algoritmalar, giriş verilerinin ve **ağırlık**kümesinin doğrusal bir birleşiminden **gelen puanları** hesaplayan bir model üretir. Ağırlıklar, eğitim sırasında tahmin edilen modelin parametreleridir.

Doğrusal algoritmalar [doğrusal ayrı kıvanaközellikleri](https://en.wikipedia.org/wiki/Linear_separability)için iyi çalışır.

Doğrusal bir algoritma ile eğitimden önce, özellikler normalleştirilmelidir. Bu, bir özelliğin sonuç üzerinde diğerlerinden daha fazla etkiye sahip olmasını önler.

Genel olarak doğrusal algoritmalar ölçeklenebilir ve hızlı, eğitmek için ucuz, tahmin etmek için ucuz. Bunlar, özelliklerin sayısına ve yaklaşık olarak eğitim veri kümesinin boyutuna göre ölçeklendirilir.

Doğrusal algoritmalar, eğitim verilerinin üzerinden birden çok geçiş yapar. Veri kümeniz belleğe uyuyorsa, eğitmeni eklemeden önce ML.NET ardışık kurulumunuza bir [önbellek denetim noktası](xref:Microsoft.ML.LearningPipelineExtensions.AppendCacheCheckpoint*) eklemek, eğitimin daha hızlı çalışmasını sağlar.

**Lineer Eğitmenler**

|Algoritma|Özellikler|Eğitmenler|
|---------|----------|--------|
|Ortalama perceptron|Metin sınıflandırması için en iyisi|<xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>|
|Stokstik çift eşgüdümlü tırmanış|İyi varsayılan performans için gerekli olmayan tuning|<xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer> <xref:Microsoft.ML.Trainers.SdcaNonCalibratedBinaryTrainer> <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer> <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer> <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>|
|L-BFGS|Özellik sayısı büyükolduğunda kullanın. Lojistik regresyon eğitim istatistikleri üretir, ancak AveragedPerceptronTrainer kadar ölçeklendirmez|<xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer> <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer> <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>|
|Sembolik stokaştik gradyan iniş|En hızlı ve en doğrusal ikili sınıflandırma eğitmeni. İşlemci sayısıyla iyi ölçeklendirin|<xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>|

## <a name="decision-tree-algorithms"></a>Karar ağacı algoritmaları

Karar ağacı algoritmaları bir dizi karar içeren bir model oluşturur: veri değerleri arasında etkili bir akış grafiği.

Bu tür algoritmaları kullanmak için özelliklerin doğrusal olarak ayrılmaz olması gerekmez. Özellik vektöründeki tek tek değerler karar sürecinde bağımsız olarak kullanıldığından, özelliklerin normalleştirilmesi gerekmez.

Karar ağacı algoritmaları genellikle çok doğrudur.

Genelleştirilmiş Katkı Modelleri (GAM) dışında, ağaç modelleri özellik sayısı büyük olduğunda açıklanabilirlik eksikliği olabilir.

Karar ağacı algoritmaları daha fazla kaynak alır ve doğrusal olanlar gibi ölçeklendirmez. Belleğe sığabilen veri kümelerinde iyi performans gösterirler.

Artırılmış karar ağaçları, her ağacın giriş verilerini aldığı ve daha iyi bir skor elde etmek için skoru bir sonraki ağaca aktardığı ve böylece topluluktaki her ağacın bir öncekinde geliştiği küçük ağaçlardan oluşan bir topluluktür.

**Karar ağacı eğitmenleri**

|Algoritma|Özellikler|Eğitmenler|
|---------|----------|--------|
|Hafif degrade artırılmış makine|En hızlı ve en doğru ikili sınıflandırma ağaç eğitmenler. Yüksek derecede tedmümkün|<xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>|
|Hızlı ağaç|Featurized görüntü verileri için kullanın. Dengesiz verilere karşı dayanıklıdır. Yüksek derecede tedmümkün | <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>|
|Hızlı orman|Gürültülü verilerle iyi çalışır|<xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>|
|Jeneralize katkı modeli (GAM)|Ağaç algoritmaları ile iyi performans ama açıklanabilirlik bir öncelik olduğu sorunlar için en iyi|<xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>|

## <a name="matrix-factorization"></a>Matris faktörizasyonu

|Özellikler|Eğitmenler|
|----------|--------|
|Büyük veri kümeleriyle seyrek kategorik veriler için en iyisi|<xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer>|

## <a name="meta-algorithms"></a>Meta algoritmalar

Bu eğitmenler ikili bir eğitmen çok sınıf eğitmen oluşturun. , <xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>, <xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer> <xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer>, <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer>, <xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer>, , , ile kullanın.

|Algoritma|Özellikler|Eğitmenler|
|---------|----------|--------|
|Bir herkese karşı|Bu çok sınıflı sınıflandırıcı, her sınıf için bir ikili sınıflandırıcıyı eğiterek bu sınıfı diğer tüm sınıflardan ayırır. Sınıfların sayısı ile ölçek olarak sınırlıdır|[OneVersusAllTrainer\<İkili SınıflandırmaEğitmen>](xref:Microsoft.ML.Trainers.OneVersusAllTrainer) |
|Çift wise bağlantı|Bu çok sınıflı sınıflandırıcı, her sınıf çiftinde bir ikili sınıflandırma algoritması çalışır. İki sınıfın her bir kombinasyonu eğitilmesi gerektiğinden, sınıf sayısıyla ölçek olarak sınırlıdır.|[PairwiseCouplingTrainer\<İkili SınıflandırmaEğitmen>](xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer)|

## <a name="k-means"></a>K-Anlamı

|Özellikler|Eğitmenler|
|----------|--------|
|Kümeleme için kullanın|<xref:Microsoft.ML.Trainers.KMeansTrainer>|

## <a name="principal-component-analysis"></a>Ana bileşen analizi

|Özellikler|Eğitmenler|
|----------|--------|
|Anomali tespiti için kullanın|<xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>|

## <a name="naive-bayes"></a>Sade Bayes

|Özellikler|Eğitmenler|
|----------|--------|
|Özellikler bağımsız olduğunda ve eğitim veri kümesi küçükolduğunda bu çok sınıflı sınıflandırma eğitmenini kullanın.|<xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>|

## <a name="prior-trainer"></a>Önceki Eğitmen

|Özellikler|Eğitmenler|
|----------|--------|
|Diğer eğitmenlerin performansını temel emzetmek için bu ikili sınıflandırma eğitmenini kullanın. Etkili olmak için, diğer eğitmenlerin ölçümleri önceki eğitmen daha iyi olmalıdır. |<xref:Microsoft.ML.Trainers.PriorTrainer>|
