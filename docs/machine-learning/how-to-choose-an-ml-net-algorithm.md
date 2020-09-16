---
title: ML.NET algoritması seçme
description: Machine Learning modeliniz için bir ML.NET algoritması seçme hakkında bilgi edinin
ms.topic: overview
ms.date: 06/05/2019
ms.openlocfilehash: 8af89800485f8f8ac35ee17df10a5e3c039da42d
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679644"
---
# <a name="how-to-choose-an-mlnet-algorithm"></a>ML.NET algoritması seçme

Her [ml.net görevi](resources/tasks.md)için, aralarından seçim yapabileceğiniz birden çok eğitim algoritması vardır. Hangi birini seçeceğiniz, çözmeye çalıştığınız soruna, verilerinizin özelliklerine ve kullanılabilir işlem ve depolama kaynaklarına bağlıdır. Bir makine öğrenimi modeline yönelik eğitim, yinelemeli bir işlem olduğunu unutmamak önemlidir. En iyi şekilde çalışacak olanı bulmak için birden çok algoritma denemeniz gerekebilir.

Algoritmalar **Özellikler**üzerinde çalışır. Özellikler, giriş verilerinizde hesaplanan sayısal değerlerdir. Makine öğrenimi algoritmaları için en iyi girişlerdir. Ham giriş verilerinizi bir veya daha fazla [veri dönüştürme](resources/transforms.md)kullanarak özelliklere dönüştürürler. Örneğin, metin verileri bir sözcük sayısı ve sözcük birleşimi sayısı kümesine dönüştürülür. Özellikler veri dönüştürmeleri kullanılarak ham bir veri türünden ayıklandıktan sonra, bunlar **korkaldırılmış**olarak adlandırılır. Örneğin, korleştirilmiş metin veya daha fazla görüntü verisi.

## <a name="trainer--algorithm--task"></a>Trainer = algoritması + görev

Algoritma, bir **model**oluşturmak için yürütülen matematik. Farklı algoritmalar farklı özelliklerle modeller üretir.

ML.NET ile aynı algoritma farklı görevlere de uygulanabilir. Örneğin, Stochastic Dual ınent, Ikili sınıflandırma, birden çok Lass sınıflandırması ve gerileme için kullanılabilir. Fark, algoritmanın çıktısının görevle eşleşecek şekilde nasıl yorumlanacağına ilişkin farktır.

Her algoritma/görev birleşimi için, ML.NET eğitim algoritmasını yürüten ve yorumu yapan bir bileşen sağlar. Bu bileşenlere, traers adı verilir. Örneğin, <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer> **regresyon** görevine uygulanan **Stochasticdualkoordinatör tedadscent** algoritmasını kullanır.

## <a name="linear-algorithms"></a>Doğrusal algoritmalar

Doğrusal algoritmalar, giriş verilerinin doğrusal bir bileşiminden ve bir **Ağırlık**kümesinden **puanları** hesaplayan bir model üretir. Ağırlıklar eğitim sırasında tahmini model parametreleridir.

Doğrusal algoritmalar, daha [önce ayrılabilir](https://en.wikipedia.org/wiki/Linear_separability)özellikler için iyi çalışır.

Doğrusal algoritmayla eğitiminden önce Özellikler normalleştirilmelidir. Bu, bir özelliğin sonuç üzerinde daha fazla etkisi olmasına engel olur.

Genel doğrusal algoritmalarda ölçeklenebilir ve hızlı, ucuz, eğitime, tek EAP ise tahmin edilecek. Bunlar, özellik sayısına ve yaklaşık olarak eğitim verileri kümesinin boyutuna göre ölçeklendirebilir.

Doğrusal algoritmalar eğitim verileri üzerinde birden çok geçiş yapar. Veri kümeniz belleğe sığıyorsa ve sonra da ML.NET işlem hattınızı eklemeden önce bir [önbellek kontrol noktası](xref:Microsoft.ML.LearningPipelineExtensions.AppendCacheCheckpoint%2A) ekleyerek eğitimin daha hızlı çalışmasını sağlayabilirsiniz.

**Doğrusal Traıners**

|Algoritma|Özellikler|Eğitmenler|
|---------|----------|--------|
|Ortalama Perceptron|Metin sınıflandırması için en iyisi|<xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>|
|Stochastik çift Eşgüdümlü yoksı|Daha iyi varsayılan performans için ayarlama gerekmiyor|<xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer> <xref:Microsoft.ML.Trainers.SdcaNonCalibratedBinaryTrainer> <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer> <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer> <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>|
|L-BFGS|Özellik sayısı büyük olduğunda kullanın. Lojistik regresyon eğitimi istatistikleri üretir, ancak ölçeklendirmez ve AveragedPerceptronTrainer|<xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer> <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer> <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>|
|Sembolik Stokastik gradyan|En hızlı ve en doğru doğrusal ikili sınıflandırma Trainer. İşlemci sayısıyla iyi ölçeklendirir|<xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>|

## <a name="decision-tree-algorithms"></a>Karar ağacı algoritmaları

Karar ağacı algoritmaları, bir dizi kararı içeren bir model oluşturur: veri değerleriyle etkin bir akış grafiği.

Özelliklerin bu tür bir algoritma kullanması için doğrusal olarak ayrılabilir olması gerekmez. Özellik Vektördeki tekil değerler karar sürecinde bağımsız olarak kullanıldığından, ve özelliklerinin normalleştirilmesine gerek yoktur.

Karar ağacı algoritmaları genellikle çok doğru.

Genelleştirilmiş ek modeller (GAMs) dışında, özellik sayısı büyük olduğunda ağaç modellerinin explainability eksik olabilir.

Karar ağacı algoritmaları daha fazla kaynak alır ve doğrusal olanları da ölçeklendirmez. Bunlar, belleğe sığan veri kümelerinde iyi bir şekilde gerçekleştirilir.

Artırılmış karar ağaçları, her bir ağacın giriş verilerini puanlarını ve daha iyi bir puan üretmek için puanı bir sonraki ağaca geçirir ve bu şekilde, her bir ağacın bir öncekini geliştirdiği her bir ağaçta daha fazla gelişmesine neden olan küçük ağaçların bir alt kümesini oluşturur.

**Karar ağacı tracılar**

|Algoritma|Özellikler|Eğitmenler|
|---------|----------|--------|
|Hafif gradyan tarafından artırılmış makine|İkili sınıflandırma ağacı izleyenilerinin en hızlı ve en doğru. Yüksek düzeyde ayarlanabilir|<xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>|
|Hızlı ağaç|Korleştirilmiş görüntü verileri için kullanın. Dengesiz verilere dayanıklı. Yüksek düzeyde ayarlanabilir | <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>|
|Hızlı orman|Gürültülü verilerle iyi çalışma|<xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>|
|Genelleştirilmiş eklenebilir model (GAM)|Ağaç algoritmalarıyla iyi bir şekilde gerçekleştiren, ancak explainability bir öncelik olduğu sorunlar için idealdir|<xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>|

## <a name="matrix-factorization"></a>Matris ayırma

|Özellikler|Eğitmenler|
|----------|--------|
|Büyük veri kümeleriyle seyrek kategorik veriler için en iyisi|<xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer>|

## <a name="meta-algorithms"></a>Meta algoritmalar

Bu traçler, ikili bir eğitimci tarafından çok sınıf bir adım oluşturur. ,,,,,, İle kullanın <xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer> <xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer> <xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer> .

|Algoritma|Özellikler|Eğitmenler|
|---------|----------|--------|
|Tek ve tüm|Bu çok sınıf Sınıflandırıcısı her sınıf için bir ikili sınıflandırıcının yanı da bu sınıfı diğer tüm sınıflardan ayırt eder. Sınıflandırılacak sınıf sayısına göre ölçeğe göre sınırlandırılmıştır|[OneVersusAllTrainer\<BinaryClassificationTrainer>](xref:Microsoft.ML.Trainers.OneVersusAllTrainer) |
|İkili eşlenme|Bu çok sınıf Sınıflandırıcısı, her sınıf çiftinde ikili bir sınıflandırma algoritması oluşturur. , İki sınıfın birleşiminin eğitililmesi gerektiği için sınıfların sayısına göre ölçeklendirilmesine sınırlıdır.|[PairwiseCouplingTrainer\<BinaryClassificationTrainer>](xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer)|

## <a name="k-means"></a>K-anlamı

|Özellikler|Eğitmenler|
|----------|--------|
|Kümeleme için kullanın|<xref:Microsoft.ML.Trainers.KMeansTrainer>|

## <a name="principal-component-analysis"></a>Sorumlu bileşen analizi

|Özellikler|Eğitmenler|
|----------|--------|
|Anomali algılama için kullanma|<xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>|

## <a name="naive-bayes"></a>Sade Bayes

|Özellikler|Eğitmenler|
|----------|--------|
|Özellikler bağımsız olduğunda ve eğitim veri kümesi küçük olduğunda bu çok sınıflı sınıflandırma eğitmen kullanın.|<xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>|

## <a name="prior-trainer"></a>Önceki seyahat

|Özellikler|Eğitmenler|
|----------|--------|
|Diğer eğitimci performansını temel alarak bu ikili sınıflandırma eğitmen ' i kullanın. Etkili olması için, diğer traçilerin ölçümleri önceki eğitime göre daha iyi olmalıdır. |<xref:Microsoft.ML.Trainers.PriorTrainer>|
