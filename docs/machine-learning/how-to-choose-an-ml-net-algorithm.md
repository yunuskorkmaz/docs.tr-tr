---
title: ML.NET algoritma seçme
description: ML.NET machine learning modeli için algoritma seçme hakkında bilgi edinin
author: natke
ms.topic: overview
ms.date: 04/20/1029
ms.openlocfilehash: d1c637437a7b285f2b66b597d616fcf39248697f
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2019
ms.locfileid: "65557771"
---
# <a name="how-to-choose-an-mlnet-algorithm"></a>ML.NET algoritma seçme

Her [ML.NET görev](resources/tasks.md), aralarından seçim yapabileceğiniz birden fazla eğitim algoritma vardır. Bu sorunu çözmek için özellikleri çalıştığınız hangisini bağlıdır, veri ve işlem ve depolama kaynakları elinizdeki. Makine öğrenme modeli eğitimi bir süreçtir olduğuna dikkat edin önemlidir. En iyi olanı bulmak için birden çok algoritmaları deneyin gerekebilir.

Algoritmalar çalışması üzerinde **özellikleri**. Sayısal giriş verilerinizden hesaplanan değerler özellikleridir. Makine öğrenimi algoritmaları için en iyi girişleri değildirler. Bir veya daha fazla kullanarak özelliklerine ham giriş verilerinizi dönüştürmek [veri dönüşümleri](resources/transforms.md). Örneğin, metin verileri sözcük sayısını ve sözcük birleşimi sayıları kümesine dönüştürülür. Özellikleri kullanarak veri dönüşümleri ham veri türünden ayıklandığını sonra bunlar denir **özellikleri tespit**. Örneğin, özellikleri tespit metin veya görüntü veri özellikleri tespit.

## <a name="trainer--algorithm--task"></a>Eğitmen = algoritması + görevi

Bir algoritmadır üretmek için yürütür matematik bir **model**. Farklı algoritmalar, farklı özelliklere sahip modelleri üretin. 

ML.NET ile aynı algoritmayı farklı görevler için uygulanabilir. Örneğin, ikili Sınıflandırma, veya çoklu sınıflar sınıflandırma ve regresyon Stokastik iniş Eşgüdümlü Ascent kullanılabilir. Nasıl algoritmasının çıktı görevi eşleşecek şekilde yorumlanır içinde farktır. 

Her bir algoritma/görev birleşimi için eğitim algoritması yürütür ve yorumunu yapar bir bileşen ML.NET sağlar. Bu bileşenler Eğitmenler çağrılır. Örneğin, <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer> kullanan **StochasticDualCoordinatedAscent** uygulanan algoritması **regresyon** görev.

## <a name="linear-algorithms"></a>Doğrusal algoritmaları

Doğrusal algoritmaları hesaplayan bir model oluşturmak **puanları** giriş veri kümesi ve doğrusal bileşiminden **ağırlıkları**. Ağırlıkları eğitim sırasında tahmin modelinin parametrelerdir.

Doğrusal algoritmaları çalışmak iyi olan özellikler için [doğrusal olarak ayrılabilir](https://en.wikipedia.org/wiki/Linear_separability).

Doğrusal bir algoritmayla eğitim önce özellikleri normalleştirilmeli. Bu sonucu üzerinde diğerlerinden daha fazla etkisi olan bir özellik engeller.

Genel doğrusal algoritmalarının ölçeklenebilir ve hızlı, ucuz eğitmek, tahmin etmek ucuz. Bunlar, bir dizi özellik ve eğitim veri kümesi boyutu yaklaşık göre ölçeklendirin.

Doğrusal algoritmaları eğitim verilerini birden çok geçiş yapın. Veri kümeniz belleğe uyuyorsa, ardından ekleyerek bir [önbellek kontrol noktası](xref:Microsoft.ML.LearningPipelineExtensions.AppendCacheCheckpoint*) eklemeden denetlemediğinden Eğitmeni ML.NET ardışık düzeninize, eğitim daha hızlı çalışmasını sağlamak.

**Doğrusal Eğitmenler**

|Algoritması|Özellikler|Eğitmenler|
|---------|----------|--------|
|Ortalama perceptron|Metin sınıflandırma için en iyi|<xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>|
|Stokastik iniş Eşgüdümlü ascent|Varsayılan iyi performans için gereken otomatik ayarlama|<xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer> <xref:Microsoft.ML.Trainers.SdcaNonCalibratedBinaryTrainer> <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer> <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer> <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>|
|L-BFGS|Birçok özellik büyük olduğunda kullanın. Lojistik regresyon eğitim İstatistikler oluşturur, ancak yanı sıra AveragedPerceptronTrainer ölçeklendirilemez|<xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer> <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer> <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>|
|Sembolik stokastik aşama|Hızlı ve en doğru doğrusal ikili sınıflandırma trainer. İşlemci sayısı ile iyi ölçeklendirilir|<xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>|

## <a name="decision-tree-algorithms"></a>Karar ağacı algoritmalarını

Karar ağacı algoritmalarını içeren bir dizi kararları modeli oluşturma: veri değerleri arasında etkili bir şekilde bir akış çizelgesi.

Özellikler, bu tür bir algoritma kullanan doğrusal olarak ayrılabilir olması gerekmez. Ve tek tek özellik vektör değerleri birbirinden bağımsız olarak karar alma sürecini kullanıldığından özellikleri normalleştirilmesine, gerek yoktur.

Karar ağacı algoritmalarını genellikle çok doğru.

Genelleştirilmiş eklenebilir modelleri dışında (GAMs), birçok özellik büyük olduğunda ağaç modelleri explainability eksik.

Daha fazla kaynak karar ağacı algoritmalarını alın ve değil ölçeği hem de doğrusal olanları yaparsınız. Bunlar da belleğe sığması veri kümeleri üzerinde gerçekleştirin.

Burada her topluluğu ağacında bir önceki artırır burada ağaçlarının her girdi verilerini puanlar ve puan daha iyi bir puan üretmek için İleri ağacı üzerine geçirir küçük ağaçları ve benzeri bir topluluğu artırmalı karar ağacı var.

**Karar ağacı Eğitmenler**

|Algoritması|Özellikler|Eğitmenler|
|---------|----------|--------|
|Işık gradyanı artırmalı makine|Hızlı ve en doğru ikili sınıflandırma ağaç eğitmenler. Yüksek oranda ayarlanabilir|<xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>|
|Hızlı ağacı|Özellikleri tespit görüntü verileri için kullanın. Dayanıklı dengesiz veri. Yüksek oranda ayarlanabilir | <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>|
|Hızlı orman|Gürültülü veri ile de çalışır|<xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer><xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>|
|Genelleştirilmiş eklenebilir modeli (GAM)|En iyi ağacı algoritmalarını ile ancak explainability öncelikli olduğu gerçekleştirmek sorunları|<xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer><xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>|

## <a name="matrix-factorization"></a>Matris factorization

|Özellikler|Eğitmenler|
|----------|--------|
|Büyük veri kümeleriyle seyrek kategorik veriler için en iyi|<xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer>|

## <a name="meta-algorithms"></a>Meta algoritmaları

Aşağıdaki eğitmenler, bir çok sınıflı trainer ikili bir eğitmen oluşturun. İle kullanma <xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>, <xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer>, <xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>, <xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer>, <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer>, <xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer>, <xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer>.

|Algoritması|Özellikler|Eğitmenler|
|---------|----------|--------|
|Bir tüm karşılaştırması|Bu çok sınıflı sınıflandırıcı Bu sınıf diğer tüm sınıflarından ayırt eden her sınıf için bir ikili dosya sınıflandırıcı eğitir. Ölçek kümesinde sınıfları kategorilere ayırmak için sayısıyla sınırlıdır|[OneVersusAllTrainer\<BinaryClassificationTrainer >](xref:Microsoft.ML.Trainers.OneVersusAllTrainer) |
|İkili eşlenmesiyle|Bu çok sınıflı sınıflandırıcı sınıflarının her çifti üzerinde bir ikili bir sınıflandırma algoritmasıdır eğitir. Her iki sınıf birleşimi eğitim gibi ölçek sınıfları sayısıyla sınırlıdır.|[PairwiseCouplingTrainer\<BinaryClassificationTrainer >](xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer)|

## <a name="k-means"></a>K-ortalamaları

|Özellikler|Eğitmenler|
|----------|--------|
|Kümeleme kullanın|<xref:Microsoft.ML.Trainers.KMeansTrainer>|

## <a name="principal-component-analysis"></a>Asıl bileşende analizi

|Özellikler|Eğitmenler|
|----------|--------|
|Anomali algılama için kullanın|<xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>|

## <a name="naive-bayes"></a>Naive Bayes

|Özellikler|Eğitmenler|
|----------|--------|
|Bu çok sınıflı sınıflandırma trainer özellikleri bağımsızdır ve eğitim veri kümesi küçük olduğunda kullanın.|<xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>|

## <a name="prior-trainer"></a>Önceki Eğitmen

|Özellikler|Eğitmenler|
|----------|--------|
|Bu ikili sınıflandırma trainer diğer Eğitmenler performansının taban çizgisi için kullanın. Etkili olması için diğer Eğitmenler ölçümlerini önceki Eğitmeni daha iyi olmalıdır. |<xref:Microsoft.ML.Trainers.PriorTrainer>|
