---
title: ML.NET algoritması seçme
description: Machine Learning modeliniz için bir ML.NET algoritması seçme hakkında bilgi edinin
ms.topic: overview
ms.date: 03/31/2021
ms.openlocfilehash: c1a35f2b5b2ece2a846469f855e91b49887f0c90
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2021
ms.locfileid: "106122631"
---
# <a name="how-to-choose-an-mlnet-algorithm"></a>ML.NET algoritması seçme

Her [ml.net görevi](resources/tasks.md)için, aralarından seçim yapabileceğiniz birden çok eğitim algoritması vardır. Hangi birini seçeceğiniz, çözmeye çalıştığınız soruna, verilerinizin özelliklerine ve kullanılabilir işlem ve depolama kaynaklarına bağlıdır. Bir makine öğrenimi modeline yönelik eğitim, yinelemeli bir işlem olduğunu unutmamak önemlidir. En iyi şekilde çalışacak olanı bulmak için birden çok algoritma denemeniz gerekebilir.

Algoritmalar **Özellikler** üzerinde çalışır. Özellikler, giriş verilerinizde hesaplanan sayısal değerlerdir. Makine öğrenimi algoritmaları için en iyi girişlerdir. Ham giriş verilerinizi bir veya daha fazla [veri dönüştürme](resources/transforms.md)kullanarak özelliklere dönüştürürler. Örneğin, metin verileri bir sözcük sayısı ve sözcük birleşimi sayısı kümesine dönüştürülür. Özellikler veri dönüştürmeleri kullanılarak ham bir veri türünden ayıklandıktan sonra, bunlar **korkaldırılmış** olarak adlandırılır. Örneğin, korleştirilmiş metin veya daha fazla görüntü verisi.

## <a name="trainer--algorithm--task"></a>Trainer = algoritması + görev

Algoritma, bir **model** oluşturmak için yürütülen matematik. Farklı algoritmalar farklı özelliklerle modeller üretir.

ML.NET ile aynı algoritma farklı görevlere de uygulanabilir. Örneğin, Stochastic çift koordinatı, Ikili sınıflandırma, birden çok Lass sınıflandırması ve gerileme için kullanılabilir. Fark, algoritmanın çıktısının görevle eşleşecek şekilde nasıl yorumlanacağına ilişkin farktır.

Her algoritma/görev birleşimi için, ML.NET eğitim algoritmasını yürüten ve yorumu yapan bir bileşen sağlar. Bu bileşenlere, traers adı verilir. Örneğin, <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer> **regresyon** görevine uygulanan **Stochasticdualkoordinatör tedadscent** algoritmasını kullanır.

## <a name="linear-algorithms"></a>Doğrusal algoritmalar

Doğrusal algoritmalar, giriş verilerinin doğrusal bir bileşiminden ve bir **Ağırlık** kümesinden **puanları** hesaplayan bir model üretir. Ağırlıklar eğitim sırasında tahmini model parametreleridir.

Doğrusal algoritmalar, daha [önce ayrılabilir](https://en.wikipedia.org/wiki/Linear_separability)özellikler için iyi çalışır.

Doğrusal algoritmayla eğitiminden önce Özellikler normalleştirilmelidir. Bu, bir özelliğin sonuç üzerinde diğerlerinden daha fazla etki almasını engeller.

Genel olarak, doğrusal algoritmalar ölçeklenebilir, hızlı, ucuz ve yüksek EAP 'yi tahmin etmek için tasarlanmıştır. Bunlar, özellik sayısına ve yaklaşık olarak eğitim verileri kümesinin boyutuna göre ölçeklendirebilir.

Doğrusal algoritmalar eğitim verileri üzerinde birden çok geçiş yapar. Veri kümeniz belleğe sığıyorsa, öngörüyi eklemeden önce ML.NET işlem hattınızla bir [önbellek kontrol noktası](xref:Microsoft.ML.LearningPipelineExtensions.AppendCacheCheckpoint%2A) eklemek, eğitimin daha hızlı çalışmasını sağlar.

### <a name="averaged-perceptron"></a>Ortalama Perceptron

Metin sınıflandırması için idealdir.

|Eğitmen|Görev|ONNX dışarı aktarılabilir|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>|İkili sınıflandırma|Yes|

### <a name="stochastic-dual-coordinated-ascent"></a>Stochastik çift Eşgüdümlü yoksı

Daha iyi varsayılan performans için ayarlama gerekmez.

|Eğitmen|Görev|ONNX dışarı aktarılabilir|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer>|İkili sınıflandırma|Yes|
|<xref:Microsoft.ML.Trainers.SdcaNonCalibratedBinaryTrainer>|İkili sınıflandırma|Yes|
|<xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>|Birden çok Lass sınıflandırması|Yes|
|<xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>|Birden çok Lass sınıflandırması|Yes|
|<xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>|Regresyon|Yes|

### <a name="l-bfgs"></a>L-BFGS

Özellik sayısı büyük olduğunda kullanın. Lojistik regresyon eğitimi istatistikleri üretir, ancak AveragedPerceptronTrainer ile birlikte ölçeklendirmez.

|Eğitmen|Görev|ONNX dışarı aktarılabilir|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer>|İkili sınıflandırma|Yes|
|<xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer>|Birden çok Lass sınıflandırması|Yes|
|<xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>|Regresyon|Yes|

### <a name="symbolic-stochastic-gradient-descent"></a>Sembolik Stokastik gradyan

En hızlı ve en doğru doğrusal ikili sınıflandırma Trainer. İşlemci sayısıyla birlikte ölçekler.

|Eğitmen|Görev|ONNX dışarı aktarılabilir|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>|İkili sınıflandırma|Yes|

### <a name="online-gradient-descent"></a>Çevrimiçi gradyan

Standart (Batch olmayan) stochastik degradesini, bir kayıp işlevleri ile ve zaman içinde görülen vektörin ortalamasını kullanarak ağırlık vektörünü güncelleştirme seçeneği uygular.

|Eğitmen|Görev|ONNX dışarı aktarılabilir|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer>|Regresyon|Yes|

## <a name="decision-tree-algorithms"></a>Karar ağacı algoritmaları

Karar ağacı algoritmaları, bir dizi kararı içeren bir model oluşturur: veri değerleriyle etkin bir akış grafiği.

Özelliklerin bu tür bir algoritma kullanması için doğrusal olarak ayrılabilir olması gerekmez. Özellik Vektördeki tekil değerler karar sürecinde bağımsız olarak kullanıldığından, ve özelliklerinin normalleştirilmesine gerek yoktur.

Karar ağacı algoritmaları genellikle çok doğru.

Genelleştirilmiş ek modeller (GAMs) dışında, özellik sayısı büyük olduğunda ağaç modellerinin explainability eksik olabilir.

Karar ağacı algoritmaları daha fazla kaynak alır ve doğrusal olanları da ölçeklendirmez. Bunlar, belleğe sığan veri kümelerinde iyi bir şekilde gerçekleştirilir.

Artırılmış karar ağaçları, her bir ağacın giriş verilerini puanlarını ve daha iyi bir puan üretmek için puanı bir sonraki ağaca geçirir ve bu şekilde, her bir ağacın bir öncekini geliştirdiği her bir ağaçta daha fazla gelişmesine neden olan küçük ağaçların bir alt kümesini oluşturur.

### <a name="light-gradient-boosted-machine"></a>Hafif gradyan tarafından artırılmış makine

İkili sınıflandırma ağacı izleyenilerinin en hızlı ve en doğru. Yüksek düzeyde tunable.

|Eğitmen|Görev|ONNX dışarı aktarılabilir|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer>|İkili sınıflandırma|Yes|
|<xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>|Birden çok Lass sınıflandırması|Yes|
|<xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>|Regresyon|Yes|
|<xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>|Sıralamasına|No|

### <a name="fast-tree"></a>Hızlı ağaç

Korleştirilmiş görüntü verileri için kullanın. Dengesiz verilere dayanıklı. Yüksek düzeyde tunable.

|Eğitmen|Görev|ONNX dışarı aktarılabilir|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer>|İkili sınıflandırma|Yes|
|<xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>|Regresyon|Yes|
|<xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>|Regresyon|Yes|
|<xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>|Sıralamasına|No|

### <a name="fast-forest"></a>Hızlı orman

Gürültülü verilerle iyi sonuç verir.

|Eğitmen|Görev|ONNX dışarı aktarılabilir|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer>|İkili sınıflandırma|Yes|
|<xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>|Regresyon|Yes|

### <a name="generalized-additive-model-gam"></a>Genelleştirilmiş eklenebilir model (GAM)

Ağaç algoritmalarıyla iyi sonuç veren, ancak explainability bir öncelik olduğu sorunlar için idealdir.

|Eğitmen|Görev|ONNX dışarı aktarılabilir|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer>|İkili sınıflandırma|No|
|<xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>|Regresyon|No|

## <a name="matrix-factorization"></a>Matris ayırma

### <a name="matrix-factorization"></a>Matris ayırma

Önerideki [birlikte çalışan filtrelemesi](https://en.wikipedia.org/wiki/Collaborative_filtering) için kullanılır.

|Eğitmen|Görev|ONNX dışarı aktarılabilir|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>|Öneri|No|

### <a name="field-aware-factorization-machine"></a>Alan duyarlı Faks makinesi

 Büyük veri kümeleriyle seyrek kategorik veriler için idealdir.

|Eğitmen|Görev|ONNX dışarı aktarılabilir|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer>|İkili sınıflandırma|No|

## <a name="meta-algorithms"></a>Meta algoritmalar

Bu traçler, ikili bir eğitimci tarafından çok sınıflı bir değer oluşturur. ,,,,,, İle kullanın <xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer> <xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer> <xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer> .

### <a name="one-versus-all"></a>Tek ve tüm

Bu çok sınıf Sınıflandırıcısı her sınıf için bir ikili sınıflandırıcının yanı da bu sınıfı diğer tüm sınıflardan ayırt eder. Sınıflandırılacak sınıf sayısına göre ölçeğe göre sınırlandırılmıştır.

|Eğitmen|Görev|ONNX dışarı aktarılabilir|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.OneVersusAllTrainer>|Birden çok Lass sınıflandırması|Yes|

### <a name="pairwise-coupling"></a>İkili eşlenme

Bu çok sınıf Sınıflandırıcısı, her sınıf çiftinde ikili bir sınıflandırma algoritması oluşturur. , İki sınıfın birleşiminin eğitililmesi gerektiği için sınıfların sayısına göre ölçeklendirilmesine sınırlıdır.

|Eğitmen|Görev|ONNX dışarı aktarılabilir|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer>|Birden çok Lass sınıflandırması|No|

## <a name="k-means"></a>K-anlamı

Kümeleme için kullanılır.

|Eğitmen|Görev|ONNX dışarı aktarılabilir|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.KMeansTrainer>|Kümeleme|Yes|

## <a name="principal-component-analysis"></a>Sorumlu bileşen analizi

Anomali algılama için kullanılır.

|Eğitmen|Görev|ONNX dışarı aktarılabilir|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>|Anormallik algılama|No|

## <a name="naive-bayes"></a>Sade Bayes

Özellikler bağımsız olduğunda ve eğitim veri kümesi küçük olduğunda bu çok sınıflı sınıflandırma algoritmasını kullanın.

|Eğitmen|Görev|ONNX dışarı aktarılabilir|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>|Birden çok Lass sınıflandırması|Yes|

## <a name="prior-trainer"></a>Önceki seyahat

Diğer eğitiçilerin performansını temel almak için bu ikili sınıflandırma algoritmasını kullanın. Etkili olması için, diğer traçilerin ölçümleri önceki eğitime göre daha iyi olmalıdır.

|Eğitmen|Görev|ONNX dışarı aktarılabilir|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.PriorTrainer>|İkili sınıflandırma|Yes|

## <a name="support-vector-machines"></a>Vektör makinelerini destekleme

Destek vektör makineleri (SVMs), doğrusal ve doğrusal olmayan sınıflandırma görevlerinde kullanılabilecek, denetimli bir öğrenme modellerinin son derece popüler ve iyi arandığı bir sınıftır.

Son araştırma, bu modelleri daha büyük eğitim kümelerine verimli bir şekilde ölçeklendirmek için iyileştirmek için yöntemlere odaklanmıştır.

### <a name="linear-svm"></a>Doğrusal SVM

Boole olarak etiketlenen veriler üzerinde eğitilen doğrusal bir ikili sınıflandırma modeli kullanarak bir hedefi tahmin eder. Stokastik gradyan adımları ve İzdüşüm adımları arasında alternatifler.

|Eğitmen|Görev|ONNX dışarı aktarılabilir|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.LinearSvmTrainer>|İkili sınıflandırma|Yes|

### <a name="local-deep-svm"></a>Yerel derin SVM

Doğrusal olmayan bir ikili sınıflandırma modeli kullanarak bir hedefi tahmin eder. Tahmin süresi maliyetini azaltır; tahmin maliyeti, daha erken bir şekilde, sınıflandırma doğruluğunun toleransı kaybı ile değil, eğitim kümesinin boyutuyla logaritarak büyüyerek artar.

|Eğitmen|Görev|ONNX dışarı aktarılabilir|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.LdSvmTrainer>|İkili sınıflandırma|Yes|

## <a name="ordinary-least-squares"></a>Normal en az kareler

Normal en az kareler (IR), doğrusal Regresyondaki en yaygın olarak kullanılan tekniklerin biridir.

Normal en az kareler, hatayı gerçek değerden tahmin edilen satıra kadar olan uzaklık karenin toplamı olarak hesaplayan kayıp işlevini ifade eder ve kare içinde hatayı en aza indirerek modele uyar. Bu yöntem, girişler ve bağımlı değişken arasında güçlü doğrusal bir ilişki olduğunu varsayar.

|Eğitmen|Görev|ONNX dışarı aktarılabilir|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.OlsTrainer>|Regresyon|Yes|
