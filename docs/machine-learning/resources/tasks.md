---
title: Makine öğrenimi görevlerini - ML.NET
description: Farklı makine öğrenimi görevlerini ve ML.NET içinde desteklenen ilişkili öğrencileriyle keşfedin.
ms.custom: seodec18
ms.date: 01/14/2019
author: jralexander
ms.openlocfilehash: 32a785a28a02b936ab92f6b3a3c4c5abbbf73315
ms.sourcegitcommit: 75567a3cb437009db55949c6092f4e77ed1a9da4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54307415"
---
# <a name="machine-learning-tasks-in-mlnet"></a>ML.NET Machine learning görevleri

Bir machine learning modeli oluştururken ilk verilerinizle elde etmek umarak tanımlamanız gerekir. Ardından, sizin durumunuz için doğru machine learning görev seçebilirsiniz. Aşağıdaki listede, aralarından seçim yapabileceğiniz görevleri öğrenme farklı makine açıklar ve bazı yaygın kullanım örnekleri.

> [!NOTE]
> ML.NET şu anda Önizleme aşamasındadır. Tüm makine öğrenimi görevlerini şu anda desteklenmiyor. Belirli bir görevi bir isteği göndermek için bir sorun açın [dotnet/machinelearning depo](https://github.com/dotnet/machinelearning/issues).

## <a name="binary-classification"></a>İkili sınıflandırma

A [denetimli makine öğrenimi](glossary.md#supervised-machine-learning) veri örneği ait olduğu, iki sınıf (Kategoriler) tahmin etmek için kullanılan görev. Bir sınıflandırma algoritmasıdır girişi etiketli örnekler, her etiket bir tamsayı 0 veya 1 olduğu kümesidir. İkili sınıflandırma algoritmasıdır çıktısındaki yeni etiketlenmemiş örnek sınıfı tahmin etmek için kullanabileceğiniz bir sınıflandırıcı ' dir. İkili sınıflandırma senaryolarına örnekler şunlardır:

* [Twitter yorumların anlama yaklaşım](../tutorials/sentiment-analysis.md) "pozitif" veya "negatif" olarak.
* Bir hastanın belirli bir Hastalık olup olmadığını tanılama.
* "Veya istenmeyen posta olarak" e-posta işaretlemek için bir kararı.
* Fotoğraf köpek ve Meyve içerip içermediğini belirleyin.

Daha fazla bilgi için [ikili sınıflandırma](https://en.wikipedia.org/wiki/Binary_classification) wikipedia makalesi.

Önerilen öğrencileriyle ikili sınıflandırma:

* AveragedPerceptronTrainer
* StochasticGradientDescentClassificationTrainer
* LightGbmBinaryTrainer
* FastTreeBinaryClassificationTrainer
* SymSgdClassificationTrainer

### <a name="binary-classification-learners"></a>İkili sınıflandırma Öğrencileriyle

Aşağıdaki öğrencileriyle ikili sınıflandırma görevleri için kullanılabilir:

* [AveragedPerceptronTrainer](xref:Microsoft.ML.Trainers.Online.AveragedPerceptronTrainer)
* [BinaryClassificationGamTrainer](xref:Microsoft.ML.Trainers.FastTree.BinaryClassificationGamTrainer)
* [FastForestClassification](xref:Microsoft.ML.Trainers.FastTree.FastForestClassification)
* [FastTreeBinaryClassificationTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer)
* [FieldAwareFactorizationMachineTrainer](xref:Microsoft.ML.FactorizationMachine.FieldAwareFactorizationMachineTrainer)
* [LightGbmBinaryTrainer](xref:Microsoft.ML.LightGBM.LightGbmBinaryTrainer)
* [LinearSvm](xref:Microsoft.ML.Trainers.Online.LinearSvm)
* [PriorTrainer](xref:Microsoft.ML.Trainers.PriorTrainer)
* [RandomTrainer](xref:Microsoft.ML.Trainers.RandomTrainer)
* [StochasticGradientDescentClassificationTrainer](xref:Microsoft.ML.Trainers.StochasticGradientDescentClassificationTrainer)
* [SymSgdClassificationTrainer](xref:Microsoft.ML.Trainers.SymSgd.SymSgdClassificationTrainer)

## <a name="multiclass-classification"></a>Sınıflı sınıflandırma

A [denetimli makine öğrenimi](glossary.md#supervised-machine-learning) veri örneği sınıfı (kategori) tahmin etmek için kullanılan görev. Bir sınıflandırma algoritmasıdır girişi etiketli örnekleri kümesidir. Her etiketin normal metin olarak başlar. Ardından, anahtarı (sayısal) türüne dönüştürür TermTransform aracılığıyla çalıştırılır. Bir sınıflandırma algoritmasıdır çıktısı, yeni etiketlenmemiş örnek sınıfı tahmin etmek için kullanabileceğiniz bir sınıflandırıcı ' dir. Çok sınıflı sınıflandırma senaryolarına örnekler şunlardır:

* Köpek bir "Siberian Husky", "Altın alıcısı", "şu dar", vb. olarak belirleniyor.
* Film anlama "pozitif", "belirsiz" veya "negatif" incelenir.
* Otel kategorilendirme "Konum", "price", "temizlik", vb. incelenir.

Daha fazla bilgi için [sınıflı sınıflandırma](https://en.wikipedia.org/wiki/Multiclass_classification) wikipedia makalesi.

Önerilen öğrencileriyle çok sınıflı için:

* OVA AveragedPerceptronTrainer
* SdcaMultiClassTrainer
* LightGbmMulticlassTrainer
* OVA FastTreeBinaryClassificationTrainer

>[!NOTE]
>OVA ve PKPD yükseltir herhangi [ikili sınıflandırma learner](#binary-classification) çok sınıflı veri kümelerinde yapacak. Daha fazla bilgi [Vikipedi] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).

### <a name="multiclass-classification-learners"></a>Sınıflı sınıflandırma Öğrencileriyle

Aşağıdaki öğrencileriyle sınıflı sınıflandırma görevleri için kullanılabilir:

* [LightGbmMulticlassTrainer](xref:Microsoft.ML.LightGBM.LightGbmMulticlassTrainer)
* [MetaMulticlassTrainer < TTransformer, TModel >](xref:Microsoft.ML.Learners.MetaMulticlassTrainer%602)
* [MultiClassClassificationTrainers](xref:Microsoft.ML.Trainers.MultiClassClassificationTrainers)
* [MultiClassNaiveBayesTrainer](xref:Microsoft.ML.Trainers.MultiClassNaiveBayesTrainer)
* [Ova](xref:Microsoft.ML.Trainers.Ova)
* [Pkpd](xref:Microsoft.ML.Trainers.Pkpd)
* [SdcaMultiClassTrainer](xref:Microsoft.ML.Trainers.SdcaMultiClassTrainer)

## <a name="regression"></a>Regresyon

A [denetimli makine öğrenimi](glossary.md#supervised-machine-learning) ilgili özellikleri kümesinden etiketin değeri tahmin etmek için kullanılan görev. Etiket herhangi bir gerçek değerini olabilir ve sınıflandırma görevleri olduğu gibi değerlerin değil sınırlı ayarlanır. Regresyon algoritmaları modeli etiketi özelliklerinin değerleri olarak nasıl değiştireceğini belirlemek için ilgili özellikleri etikette bağımlılığı çeşitli. Bir regresyon algoritmasıdır girişi bir örnekler etiketlerle bilinen değerler kümesidir. Bir regresyon algoritmasıdır çıktısı her yeni özellik kümesi, giriş etiketi değerini tahmin etmek için kullanabileceğiniz bir işlev ise. Regresyon senaryolarına örnekler şunlardır:

* Ev fiyatları yatak, konum ve boyut sayısı gibi merkezi özniteliklerini temel alarak tahmin etme.
* Geçmiş verileri ve geçerli pazar eğilimlerine göre gelecekteki hisse senedi fiyatlarını tahmin etme.
* Bütçelerini reklam üzerinde temel bir ürün satışları tahmin etme.

Önerilen öğrencileriyle regresyon için:

* FastTreeTweedieTrainer 
* LightGbmRegressorTrainer 
* SdcaRegressionTrainer 
* FastTreeRegressionTrainer

### <a name="regression-learners"></a>Regresyon Öğrencileriyle

Aşağıdaki öğrencileriyle regresyon görevleri için kullanılabilir:

* [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer)
* [FastTreeRegressionFastTreeTrainer](xref:Microsoft.ML.Runtime.FastTreeRegressionFastTreeTrainer)
* [FastTreeTweedieTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer)
* [LightGbmRegressorTrainer](xref:Microsoft.ML.LightGBM.LightGbmRegressorTrainer)
* [LogisticRegression](xref:Microsoft.ML.Learners.LogisticRegression)
* [OlsLinearRegressionTrainer](xref:Microsoft.ML.Trainers.HalLearners.OlsLinearRegressionTrainer)
* [OnlineGradientDescentTrainer](xref:Microsoft.ML.Trainers.Online.OnlineGradientDescentTrainer)
* [PoissonRegression](xref:Microsoft.ML.Trainers.PoissonRegression)
* [RegressionGamTrainer](xref:Microsoft.ML.Trainers.FastTree.RegressionGamTrainer)
* [SdcaRegressionTrainer](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer)
* [FastTree.SingleTrainer](xref:Microsoft.ML.Trainers.FastTree.SingleTrainer)
* [LightGBM.SingleTrainer](xref:Microsoft.ML.LightGBM.SingleTrainer)

## <a name="clustering"></a>Kümeleme

Bir [Denetimsiz machine learning](glossary.md#unsupervised-machine-learning) benzer özelliklere içeren kümeler halinde veri grubu örnekleri için kullanılan görev. Kümeleme de olmayan mantıksal olarak türettiğiniz DataSet ilişkileri tanımlamak için gözatma veya basit gözlem tarafından kullanılabilir. Giriş ve çıkışları kümeleme algoritması, seçilen metodolojiyi üzerinde bağlıdır. Bir dağıtım, kütle Merkezi, bağlantı veya yoğunluk yaklaşımla alabilir. ML.NET şu anda K-ortalamaları Kümelemesi kullanarak kütle merkezi tabanlı bir yaklaşımı destekler. Kümeleme senaryolarına örnekler şunlardır:

* Otel Konukları alışkanlıkları ve Otel seçeneği özelliklere göre parçalarını anlama.
* Müşteri kesimleri ve demografik bilgilere bağlı hedeflenen reklam kampanyaları oluşturmanıza yardımcı olmak için tanımlayıcı.
* Üretim ölçümleri temel alarak envanteri halinde kategorilere ayrılması.

### <a name="clustering-learners"></a>Kümeleme Öğrencileriyle

Aşağıdaki öğrencileriyle görevleri kümeleme için kullanılabilir:

* [KMeansPlusPlusTrainer](xref:Microsoft.ML.Trainers.KMeans.KMeansPlusPlusTrainer)

## <a name="anomaly-detection"></a>Anomali algılama

Bu görevi, asıl bileşen analiz (PCA) kullanarak bir anomali algılama modeli oluşturur. PCA tabanlı Anomali algılama geçerli işlemler gibi bir sınıf eğitim verilerini almak kolay, ancak yeterli örnekleri hedeflenen anomali elde etmek zor olduğu senaryolar modelinde oluşturmanıza yardımcı olur.

İç yapısını gösterir ve veri varyans açıklar machine learning'de PCA kurulan bir teknik keşif veri analizi sık kullanılır. Birden fazla değişken içeren verileri analiz ederek PCA çalışır. Bu değişkenler arasındaki bağıntıları arar ve en iyi sonuçlar farklılıkları yakalar değerlerinin birleşimi belirler. Bu birleşik özellik değerleri, asıl bileşen olarak adlandırılıyordu daha kompakt bir özellik alanı oluşturmak için kullanılır.

Anomali algılama machine learning'de birçok önemli görevleri kapsar:

* Olası sahte işlem tanımlama.
* Ağa yetkisiz erişim oluştu olarak görülebilecek desenler öğrenme.
* Hastalara anormal kümelerini bulma.
* Değer denetimi bir sisteme girdi.

Anomalileri tanımına göre nadir olayları olduğundan, temsili bir örnek model için kullanılacak veri toplamak zor olabilir. Bu kategoride bulunan algoritmaları özellikle imbalanced veri kümelerini kullanarak oluşturma ve eğitim modeli çekirdek sorunları gidermek üzere tasarlanmıştır.

### <a name="anomaly-detection-learners"></a>Anomali algılama öğrencileriyle

Aşağıdaki öğrencileriyle anomali algılama görevler için kullanılabilir:

* [RandomizedPcaTrainer](xref:Microsoft.ML.Trainers.PCA.RandomizedPcaTrainer)

## <a name="ranking"></a>Derecelendirme

Derecelendirme görev derecelendiricisini etiketli örnekleri bir dizi oluşturur. Bu örnek kümesi ile puanlanmış örnek grupları oluşan bir tetikleyicisi. {0, 1, 2, 3, 4} her örneği için olan derecelendirme etiketleri.  Derecelendiricisini bilinmeyen puanlarının her örneği için yeni derece örneği gruplara eğitildi. ML.NET derecelendirme öğrencileriyle olan [öğrenilen makine derecelendirme](https://en.wikipedia.org/wiki/Learning_to_rank) bağlı.

### <a name="ranking-learners"></a>Öğrencileriyle sıralaması

Aşağıdaki öğrencileriyle görevleri sıralaması için kullanılabilir:

* [FastTreeRankingTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer)
* [LightGbmRankingTrainer](xref:Microsoft.ML.LightGBM.LightGbmRankingTrainer)

## <a name="recommendation"></a>Öneri

Bir öneri görevi önerilen ürünleri veya hizmetleri listesi oluşturmayı etkinleştirir. ML.NET kullanan [matris factorization (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), [işbirliğine dayalı filtreleme](https://en.wikipedia.org/wiki/Collaborative_filtering) geçmiş ürün derecelendirmesi veri Kataloğu'nda varsa önerileri için algoritma. Örneğin, kullanıcılarınız için geçmiş film derecelendirmesi verilere sahip ve sonraki izleyin okunduğunun diğer filmler önermek istediğiniz.

### <a name="recommendation-learners"></a>Öneri öğrencileriyle

Aşağıdaki öğrencileriyle öneri görevleri için kullanılabilir:

* [MatrixFactorizationTrainer](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer)
* [MatrixFactorizationPredictionTransformer](xref:Microsoft.ML.Trainers.Recommender.MatrixFactorizationPredictionTransformer)
