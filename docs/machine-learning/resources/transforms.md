---
title: Machine learning veri dönüşümleri - ML.NET
description: ML.NET içinde desteklenen özellik Mühendisliği bileşenleri keşfedin.
author: JRAlexander
ms.custom: seodec18
ms.date: 12/14/2018
ms.openlocfilehash: c311aa59426b716ffcd2c53e890d2e3e380360a7
ms.sourcegitcommit: 81bd16c7435a8c9183d2a7e878a2a5eff7d04584
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2019
ms.locfileid: "54249131"
---
# <a name="machine-learning-data-transforms---mlnet"></a>Machine learning veri dönüşümleri - ML.NET

Aşağıdaki tablolarda tüm ML.NET desteklenen veri dönüşümleri hakkında bilgiler içerir.

> [!NOTE]
> ML.NET şu anda Önizleme aşamasındadır. Tüm veri dönüşümleri şu anda desteklenmiyor. Belirli bir dönüştürme için bir istek göndermek için bir sorun açın [dotnet/machinelearning](https://github.com/dotnet/machinelearning/issues) GitHub deposu.

## <a name="combiners-and-segregators"></a>Combiners ve segregators

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.Transforms.GroupTransform> | Grupları bir skaler sütuna bitişik grubu kimliğini temel alan bir vektör değerleri |
| <xref:Microsoft.ML.Legacy.Transforms.FeatureCombiner> | Tüm özellikleri bir özellik sütun halinde birleştirir. |
| <xref:Microsoft.ML.Legacy.Transforms.ManyHeterogeneousModelCombiner> | Tek bir PredictorModel TransformModels ve bir PredictorModel dizisine birleştirir. |
| <xref:Microsoft.ML.Legacy.Transforms.ModelCombiner> | Tek bir model TransformModels dizisine birleştirir. |
| <xref:Microsoft.ML.Legacy.Transforms.Segregator> | Vektör sütunların satır dizileri; grubunu çözer. Kikare dağılımının grubu Dönüştür. |
| <xref:Microsoft.ML.Legacy.Transforms.TwoHeterogeneousModelCombiner> | Bir TransformModel ve bir PredictorModel tek bir PredictorModel birleştirir. |
| <xref:Microsoft.ML.Transforms.UngroupTransform> | Vektör sütunlara satır, ters grubu dönüşümünün dizileri grupları kaldırın. |

## <a name="conversions"></a>Dönüşümler 

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.Transforms.Conversions.HashingTransformer> | Karmaları tek değerli sütunlar veya sütun vektör. Vektör sütunları için her yuva ayrı olarak karma hale getirir. Metin değerleri veya anahtar değerlerini karma. |
| <xref:Microsoft.ML.Legacy.Transforms.HashConverter> | Sütun değerleri karmaları dönüştürür. Bu dönüşüm, hem sayısal ve metin girişleri, hem tek hem de vektör değerli sütunlar kabul eder. |
| <xref:Microsoft.ML.Transforms.Conversions.HashJoiningTransform> | Birden çok sütun değerleri karmaları dönüştürür. Bu dönüşüm, hem sayısal ve metin girişleri, hem tek hem de vektör değerli sütunlar kabul eder. |
| <xref:Microsoft.ML.Transforms.Conversions.KeyToBinaryVectorMappingTransformer> | Bir anahtarı bir ikili vektör sütununa dönüştürür. |
| <xref:Microsoft.ML.Transforms.Conversions.KeyToValueMappingTransformer > | Karşılık gelen değerlere KeyValues meta verilerindeki anahtar dizinlerini eşlemek için KeyValues meta verileri kullanır. |
| <xref:Microsoft.ML.Transforms.Conversions.KeyToVectorMappingTransformer> | Bir anahtarı bir vektör sütununa dönüştürür. |
| <xref:Microsoft.ML.Transforms.Conversions.TypeConvertingTransformer> | Bu türe dönüştürülüp değişiklikler temel alınan sütun türü sağlandı. |
| <xref:Microsoft.ML.Transforms.Conversions.ValueToKeyMappingTransformer> | Dönüştürür (sözcükler, sayılar, vb.) bir sözlükte dizini oluşturmak için değerleri girin. |


## <a name="deep-learning"></a>Derin öğrenme

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.Transforms.OnnxTransform> | Mevcut bir ONNX model için veri sağlar ve puan döndürür (tahmin). |
| <xref:Microsoft.ML.Transforms.TensorFlowTransform> | İle kullanan TensorFlow modeli Puanlama veya TensorFlow modeli yeniden eğitme. |

## <a name="feature-extraction"></a>Özelliği ayıklama

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.Transforms.Text.CustomStopWordsRemovingTransform> | Kaldırır, tek tek belirteçleri (büyük küçük harf duyarsız karşılaştırma) stopword karşılaştırarak durdurma sözcükleri listesini belirttiniz.| 
| <xref:Microsoft.ML.Runtime.ImageAnalytics.ImageGrayscaleTransform> | Bir veya daha fazla ImageType sütunları alır ve bunları aynı görüntüyü gri tona gösterimi için dönüştürür.|
| <xref:Microsoft.ML.Runtime.ImageAnalytics.ImageLoaderTransform> | Bir veya daha fazla ReadOnlyMemory sütunları alır ve bunları bir ImageType yükler. |
| <xref:Microsoft.ML.Runtime.ImageAnalytics.ImagePixelExtractorTransform> | Bir veya daha fazla ImageType sütunları alır ve bunları bir vektör temsiline dönüştürür.|
| <xref:Microsoft.ML.Runtime.ImageAnalytics.ImageResizerTransform> | Bir veya daha fazla ImageType sütunları alır ve bunları sağlanan yükseklik ve genişlik için yeniden boyutlandırır.|
| <xref:Microsoft.ML.Transforms.Text.LatentDirichletAllocationTransformer> | LightLDA, görünmeyen Dirichlet ayırma durumu resim uyarlamasını uygular.|
| <xref:Microsoft.ML.Transforms.LoadTransform> | Belirtilen model dosyasından özel dönüşümler yükler. Seri hale getirilmiş bir zinciri veya farklı (ancak yine de uyumlu) veri görünümüne önceden eğitilmiş bir dönüştürme uygulamak için 'tek tek seçme' dönüştürmeler sağlar. |
| <xref:Microsoft.ML.Transforms.Text.NgramExtractingTransformer> | Bir paketi sayısı, anahtarların belirli bir vektör içindeki ngrams (uzunluğu 1-n ardışık değerleri dizisi) üretir. Bunu ngrams sözlüğü oluşturmak ve paketi dizin olarak sözlükte kimliğini kullanarak yapar. | 
| <xref:Microsoft.ML.Transforms.Text.NgramExtractorTransform> | Parçalanmış metin (ReadOnlyMemory vektörü) koleksiyonu veya anahtarlarının vektörleri sayısal özellik vektör kapatır. Özellik vektör ngrams (uzunluğu 1-n ardışık belirteçleri - sözcükleri veya anahtarlarının - dizileri) sayısı ' dir. | 
| <xref:Microsoft.ML.Transforms.Text.NgramHashExtractingTransformer> | Koleksiyona karmayı kullanarak sayısal özellik vektör parçalanmış metin (ReadOnlyMemory vektörü) kapatır. | 
| <xref:Microsoft.ML.Transforms.Text.NgramHashingTransformer> | Belirli bir metin ngrams (uzunluğu 1-n ardışık bir kelimelerin dizileri) sayısı, bir paket oluşturur. | 
| <xref:Microsoft.ML.Transforms.Categorical.OneHotEncodingTransformer> | Kategorik değer göstergesi dizi kategorileri sözlüğü verileri temel alan yapı ve dizi dizini olarak sözlükte kimliğini kullanarak dönüştürür. |
| <xref:Microsoft.ML.Transforms.Projections.PcaTransform> | Projeksiyon üzerinde düşük sıra alt özellik vektör hesaplar. |
| <xref:Microsoft.ML.Transforms.Text.SentimentAnalyzingTransformer> | Giriş dizesi puanlamak için bir yaklaşım kullanan modeli kullanır. |
| <xref:Microsoft.ML.Transforms.Text.StopWordsRemovingTransformer> | Dile özgü durdurma sözcükleri (en yaygın kelimeler) listesini stopword için tek tek belirteçleri (büyük küçük harf duyarsız karşılaştırma) karşılaştırarak kaldırır. |
| <xref:Microsoft.ML.Transforms.Categorical.TermLookupTransformer> | Yeni sütun bağımsız değişkenleri ile sağlanan bir harita veri kümesini kullanarak metin değerleri sütunları eşlenir. |
| <xref:Microsoft.ML.Transforms.Text.WordBagBuildingTransformer> | Belirli bir metin ngrams (ardışık bir kelimelerin dizileri) sayısı, bir paket oluşturur. Bunu ngrams sözlüğü oluşturmak ve paketi dizin olarak sözlükte kimliğini kullanarak yapar. |
| <xref:Microsoft.ML.Transforms.Text.WordHashBagProducingTransformer> | Belirli bir metin ngrams (uzunluğu 1-n ardışık bir kelimelerin dizileri) sayısı, bir paket oluşturur. Bunu her ngram karma ve paketi dizin olarak karma değeri kullanarak yapar. |
| <xref:Microsoft.ML.Transforms.Text.WordTokenizingTransformer> | Ayırıcı karakterler kullanarak sözcüklere metin böler. |


## <a name="image-model-featurizers"></a>Görüntü modeli featurizers

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.Transforms.AlexNetExtension> | İle kullanılmak için bir genişletme yöntemi budur <xref:Microsoft.ML.Transforms.DnnImageFeaturizerEstimator> bir pretrained kullanmak için [AlexNet](https://en.wikipedia.org/wiki/AlexNet) modeli. Bu uzantıyı içeren NuGet ikili model dosyası eklemek için de sağlanır. | 
| <xref:Microsoft.ML.Transforms.ResNet18Extension> | İle kullanılmak için bir genişletme yöntemi budur <xref:Microsoft.ML.Transforms.DnnImageFeaturizerEstimator> bir pretrained ResNet18 modelini kullanmak için. Bu uzantıyı içeren NuGet ikili model dosyası eklemek için de sağlanır. |
| <xref:Microsoft.ML.Transforms.ResNet50Extension> | İle kullanılmak için bir genişletme yöntemi budur <xref:Microsoft.ML.Transforms.DnnImageFeaturizerEstimator> pretrained ResNet50model kullanılacak. Bu uzantıyı içeren NuGet ikili model dosyası eklemek için de sağlanır. |
| <xref:Microsoft.ML.Transforms.ResNet101Extension> | İle kullanılmak için bir genişletme yöntemi budur <xref:Microsoft.ML.Transforms.DnnImageFeaturizerEstimator> bir pretrained ResNet101 modelini kullanmak için. Bu uzantıyı içeren NuGet ikili model dosyası eklemek için de sağlanır. |

## <a name="label-parsing"></a>Etiket Ayrıştırma

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.Dictionarizer> | Dönüştürür (sözcükler, sayılar, vb.) bir sözlükte dizini oluşturmak için değerleri girin. |
| <xref:Microsoft.ML.Legacy.Transforms.LabelColumnKeyBooleanConverter> | Etiket anahtarı ya da bool, sınıflandırma için uygun hale getirmek için (gerekirse) dönüştürür. |
| <xref:Microsoft.ML.Transforms.LabelConvertTransform> |  Etiketleri dönüştürür. |
| <xref:Microsoft.ML.Transforms.LabelIndicatorTransform> | Çok sınıflı etiketleri ikili true, False OVA ile kullanmak için öncelikle etiketleri yeniden eşlemesi.|
| <xref:Microsoft.ML.Legacy.Transforms.LabelToFloatConverter> | Regresyon için uygun hale getirmek için kayan nokta etiketi dönüştürür. |
| <xref:Microsoft.ML.Legacy.Transforms.PredictedLabelColumnOriginalValueConverter> | Türü bool olmadığı sürece bir tahmin edilen etiket sütunu, özgün değerlerine dönüştürür. |

## <a name="missing-values"></a>Eksik değerleri

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.Transforms.MissingValueDroppingTransformer> | Sütundaki değerleri eksik bırakır. |
| <xref:Microsoft.ML.Transforms.MissingValueIndicatorTransform> | Bir boolean çıktı sütunu giriş sütunu giriş sütunundaki değeri eksik olduğu çıkış değeri true ise, aynı sayıda yuva oluşturur. |
| <xref:Microsoft.ML.Transforms.MissingValueReplacingTransformer> | Varsayılan değer ya da (yalnızca metin olmayan sütunları) ortalama/en düşük/en yüksek değeri ile değiştirerek eksik değerleri işleyin. |

## <a name="normalization"></a>Normalleştirme

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.Transforms.Projections.LpNormalizingTransformer> | LP-Norm (vektör/row-wise) normalleştirme Dönüştür. |
| <xref:Microsoft.ML.Transforms.Normalizers.MeanVarDblAggregator> | Ortalama ve vektör değerli sütun için varyansı hesaplar. Geçerli ortalama ve M2 izler (değerleri mean squared farkları toplamı), NaN'ler ve sıfır olmayan öğe sayısını sayısı. |
| <xref:Microsoft.ML.Transforms.Normalizers.MeanVarSngAggregator> | Ortalama ve vektör değerli sütun için varyansı hesaplar. Geçerli ortalama ve M2 izler (değerleri mean squared farkları toplamı), NaN'ler ve sıfır olmayan öğe sayısını sayısı. |
| <xref:Microsoft.ML.Transforms.Normalizers.MinMaxDblAggregator> | Min, max, seyrek olmayan değerleri (vCount) sayısı ve ProcessValue() çağrı (trainCount) sayısı için bir vektör değerli sütun izler. |
| <xref:Microsoft.ML.Transforms.Normalizers.MinMaxSngAggregator> | Min, max, seyrek olmayan değerleri (vCount) sayısı ve ProcessValue() çağrı (trainCount) sayısı için bir vektör değerli sütun izler. |
| <xref:Microsoft.ML.Transforms.Normalizers.NormalizeTransform> | Özellik aralıkları standart hale getirir. |
| <xref:Microsoft.ML.Transforms.Normalizers.NormalizingTransformer> |Özellik aralıkları standart hale getirir. |

## <a name="onnx"></a>Onnx

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.Transforms.OnnxTransform> | ONNX standart v1.2 kullanacağınız puanları önceden eğitilmiş ONNX modelleri |

## <a name="preprocessing"></a>Ön işleme
| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.Transforms.BootstrapSamplingTransformer> | Önyükleme örnekleme Poisson örnekleme kullanarak yaklaştırır. |
| <xref:Microsoft.ML.Transforms.Projections.RandomFourierFeaturizingTransformer> | Rastgele Fourier özellik oluşturur. |
| <xref:Microsoft.ML.Transforms.Text.TokenizingByCharactersTransformer> | Simgeleştirici karakter odaklı burada metin bir karakter dizisi olarak değerlendirilir. |
| <xref:Microsoft.ML.Transforms.Projections.VectorWhiteningTransformer> | Ağırlıklar tanımlamaya yardımcı olmak için Simplfies iyileştirme. |

## <a name="row-filters"></a>Satır filtreleri

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.Transforms.RowShufflingTransformer> | Rastgele bir imleç seçeneği belirli sayıda satırı oluşan bir havuz kullanarak gerçekleştirmeyi deneyin.  |
| <xref:Microsoft.ML.Transforms.SkipFilter> | Alt satır kümesine giriş satır sayısı atlayarak sınırlama sağlar. |
| <xref:Microsoft.ML.Transforms.SkipTakeFilter> | İsteğe bağlı bir uzaklık konumunda satır kümesini giriş sınırlama sağlar. Veri sayfalama uygulama için kullanılabilir. İle oluşturulduğunda SkipTakeFilter.SkipArguments gibi davranır `SkipFilter`.
| <xref:Microsoft.ML.Transforms.TakeFilter> | Alt satır kümesine giriş N ilk satırları yararlanarak sınırlama sağlar. |


## <a name="schema"></a>Şema

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.Transforms.ColumnCopyingTransformer> | Veri kümesindeki sütunları çoğaltır.|
| <xref:Microsoft.ML.Transforms.ColumnSelectingTransformer> | Bırakın ya da belirli bir girdiden koruma sütun kümesini seçer. |
| <xref:Microsoft.ML.Transforms.FeatureSelection.SlotsDroppingTransformer> | Yuva sütunları bırakır.|
| <xref:Microsoft.ML.Legacy.Transforms.KeyToTextConverter> | KeyToValueTransform karşılık gelen değerlere KeyValues meta verilerindeki anahtar dizinlerini eşlemek için KeyValues meta verileri kullanır. |
| <xref:Microsoft.ML.Transforms.OptionalColumnTransform> | Belirtilen tür ve varsayılan değerlerle yeni bir sütun oluşturur. |
| <xref:Microsoft.ML.Transforms.RangeFilter> | Dataview tek, Double veya anahtarı (bitişik) türünde bir sütun üzerinde filtreler. Belirtilen en düşük/en yüksek aralıktaki değerleri tutar. NaN'ler her zaman filtrelenir. Giriş anahtar türü varsa, yüzde değerlerini sayısı min/maks kabul edilir. |

## <a name="tensorflow"></a>TensorFlow

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.Transforms.TensorFlowTransform> | Veya puanları kullanan TensorFlow ile model retrains TensorFlow modeli. |

## <a name="text-processing-and-featurization"></a>Metin işleme ve özellik kazandırma sayesinde

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.Transforms.Text.TextNormalizingTransformer> | Metin normalleştirme dönüşüm sağlayan büyük/küçük harf normalleştirme, aksanlı işaretleri, noktalama işaretleri ve/veya sayı kaldırılıyor. Dönüştürme, vektör belirteçleri/metin (ReadOnlyMemory vektörü) yanı sıra metin girişi üzerinde çalışır. |
| <xref:Microsoft.ML.Transforms.Text.TokenizingByCharactersTransformer> | Simgeleştirici karakter odaklı burada metin bir karakter dizisi olarak değerlendirilir. |

## <a name="time-series"></a>Zaman serisi

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.Runtime.TimeSeriesProcessing.ExponentialAverageTransform> | Değerleri ağırlıklı ortalamasını alır: ExpAvg(y_t) = bir * y_t + (1-a) * ExpAvg(y_(t-1)). |
| <xref:Microsoft.ML.Runtime.TimeSeriesProcessing.IidChangePointDetector> | Bir i.i.d. değişiklik noktası algılayıcısı dönüşümün uygular Uyarlamalı çekirdek yoğunluğu tahmini ve martingales göre sırası (rastgele örnek). |
| <xref:Microsoft.ML.Runtime.TimeSeriesProcessing.IidSpikeDetector> | Implements depo algılayıcısı dönüştürmek için bir i.i.d. dizisi üzerinde Uyarlamalı çekirdek yoğunluğu Tahmine dayalı (rastgele örnek). |
| <xref:Microsoft.ML.Runtime.TimeSeriesProcessing.MovingAverageTransform> | Kayan pencere değerleri ağırlıklı ortalamasını sağlar. |
| <xref:Microsoft.ML.Runtime.TimeSeriesProcessing.PercentileThresholdTransform> | Zaman serisi geçerli değeri kayan pencere en yüksek değerleri yüzdebirlik ait olup olmadığını belirler. |
| <xref:Microsoft.ML.Runtime.TimeSeriesProcessing.PValueTransform> | Geçerli değer görgül p-değer kayan pencere diğer değerlere göre hesaplar. |
| <xref:Microsoft.ML.Runtime.TimeSeriesProcessing.SlidingWindowTransform> | Bir kayan pencere üzerinde türünde tek bir zaman serisi çıkarır. |
| <xref:Microsoft.ML.Runtime.TimeSeriesProcessing.SsaChangePointDetector> | Zaman serisi tekil Spektrumun model oluşturma göre değişiklik noktası algılayıcısı dönüşüm uygular. |
| <xref:Microsoft.ML.Runtime.TimeSeriesProcessing.SsaSpikeDetector> | Uygular, zaman serisi tekil Spektrumun model oluşturma depo algılayıcısı dönüştürme temel. |

## <a name="miscellaneous"></a>Çeşitli

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.Transforms.CompositeTransformer> | Bileşik DataTransform oluşturur. |
| <xref:Microsoft.ML.Transforms.CustomMappingTransformer%602> | Sağlanan ek sütunları oluşturur `IDataView`. Satır sayısı değişmez ve giriş verilerinin her satır için uygulama kullanıcının işlevinin sonucu olarak görülebilir.|
| <xref:Microsoft.ML.Transforms.GenerateNumberTransform> | Oluşturulan bir sayı dizisi içeren bir sütun ekler. |
| <xref:Microsoft.ML.Transforms.ProduceIdTransform> | İmlecin Kimliğine sahip bir sütun bir sütun oluşturur. |
| <xref:Microsoft.ML.Transforms.RandomNumberGenerator> | Rastgele bir sayı oluşturur. |
| <xref:Microsoft.ML.Transforms.ScoringTransformer> | Puanları bir önceden eğitilmiş modelden kullanarak işlem hattı, yeni bir modeli oluşturmak için birden çok Tahmine dayalı modeller aracılığıyla bilgileri bir araya getirir. |
