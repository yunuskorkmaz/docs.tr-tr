---
title: Veri dönüştürmeleri
description: ML.NET sürümünde desteklenen özellik Mühendisliği bileşenlerini gezin.
author: natke
ms.author: nakersha
ms.date: 04/02/2019
ms.openlocfilehash: 25da3cceb3c9090661b34254ed240207aaf3b9d7
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929250"
---
# <a name="data-transformations"></a>Veri dönüştürmeleri

Veri dönüştürmeleri şu şekilde kullanılır:

- Model eğitimi için verileri hazırlama
- bir içeri aktarılan modeli TensorFlow veya ONNX biçiminde uygulama
- bir modelden geçtikten sonra işlem sonrası veriler

Bu kılavuzdaki dönüşümler, [ıestimator](xref:Microsoft.ML.IEstimator%601) arabirimini uygulayan sınıflar döndürüyor. Veri dönüştürmeleri birlikte zincirlenebilir. Her bir dönüşüm, bağlantılı başvuru belgelerinde belirtilen belirli tür ve biçimlerin verilerini bekler ve üretir.

Bazı veri dönüştürmeleri, parametrelerini hesaplamak için eğitim verileri gerektirir. Örneğin: <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> transformatör, `Fit()` işlem sırasında eğitim verilerinin ortalama ve varyansını hesaplar ve bu parametreleri `Transform()` işleminde kullanır. 

Diğer veri dönüştürmeleri eğitim verileri gerektirmez. Örneğin: <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale*> dönüştürme işlemi sırasında `Fit()` herhangi bir eğitim `Transform()` verisi görünmeden işlemi gerçekleştirebilir.

## <a name="column-mapping-and-grouping"></a>Sütun eşleme ve gruplama

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A> | Bir veya daha fazla giriş sütununu yeni bir çıktı sütununa birleştirme |
| <xref:Microsoft.ML.TransformExtensionsCatalog.CopyColumns%2A> | Bir veya daha fazla giriş sütununu kopyalama ve yeniden adlandırma |
| <xref:Microsoft.ML.TransformExtensionsCatalog.DropColumns%2A> | Bir veya daha fazla giriş sütununu bırakma |
| <xref:Microsoft.ML.TransformExtensionsCatalog.SelectColumns%2A> | Giriş verilerinden tutulacak bir veya daha fazla sütun seçin |

## <a name="normalization-and-scaling"></a>Normalleştirme ve ölçekleme

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> | Ortalama (eğitim verileri) çıkarın ve varyansı (eğitim verileri) göre bölün |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeLogMeanVariance%2A> | Eğitim verilerinin logaritmasını temel alarak normalleştirin |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeLpNorm%2A> | Giriş vektörlerini [LP-norm](https://en.wikipedia.org/wiki/Lp_space#The_p-norm_in_finite_dimensions)olarak ölçeklendirin, p 1, 2 veya Infinity. Varsayılan değer L2 (Euclidea Distance) norm |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeGlobalContrast%2A> | Satır verilerinin ortalama değerini çıkararak bir satırdaki her değeri ölçeklendirin ve standart sapma veya L2-norm (satır verilerinin) ile bölün ve yapılandırılabilir bir ölçek faktörü (varsayılan 2) ile çarpın |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A> | Giriş değerini bir bin dizinine atayın ve 0 ile 1 arasında bir float değeri üretmek için bölme sayısına göre bölün. Bölme sınırları, eğitim verilerini depo gözleri arasında eşit olarak dağıtmak için hesaplanır |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeSupervisedBinning%2A> | Etiket sütunuyla bağıntı temelinde bir sepete giriş değeri ata |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A> | Eğitim verilerinde minimum ve maksimum değerler arasındaki farka göre girişi ölçeklendirin |

## <a name="conversions-between-data-types"></a>Veri türleri arasındaki dönüşümler

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.ConvertType%2A> | Giriş sütununun türünü yeni bir türe Dönüştür |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValue*> | Değerleri, eşlemelerin sağlanan sözlüğüne göre anahtarlar (kategoriler) ile eşleyin |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*> | Giriş verilerinden eşleme oluşturarak değerleri anahtarlar (kategoriler) ile eşleyin |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue*> | Anahtarları özgün değerlerine geri Dönüştür |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToVector*> | Anahtarları özgün değerlerin vektörlerine geri Dönüştür |
| <xref:Microsoft.ML.ConversionsCatalog.MapKeyToBinaryVector*> | Anahtarları özgün değerlerin ikili vektörüne geri Dönüştür |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash*> | Giriş sütunundaki değeri karma olarak |

## <a name="text-transformations"></a>Metin dönüşümleri

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.TextCatalog.FeaturizeText*> | Metin sütununu normalleştirilmiş Ngram ve karakter-gram sayıları float dizisine Dönüştür | 
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoWords*> | Bir veya daha fazla metin sütununu tekil sözcüklere Böl |
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoCharactersAsKeys*> | Bir veya daha fazla metin sütununu bir konu kümesi üzerinde ayrı karakterlere böler |
| <xref:Microsoft.ML.TextCatalog.NormalizeText*> | Durumu değiştir, aksanlı işaretleri, noktalama işaretlerini ve sayıları kaldır |
| <xref:Microsoft.ML.TextCatalog.ProduceNgrams*> | Metin sütununu Ngram sayısı (ardışık sözcüklerin dizileri) için bir paket olarak Dönüştür|
| <xref:Microsoft.ML.TextCatalog.ProduceWordBags*> | Metin sütununu Ngram vektörü sayısı için bir paket olarak Dönüştür |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedNgrams*> | Metin sütununu karma Ngram sayımlarının vektörüne Dönüştür |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedWordBags*> | Metin sütununu karma Ngram sayımlarının bir torba Dönüştür |
| <xref:Microsoft.ML.TextCatalog.RemoveDefaultStopWords*>  | Giriş sütunlarından belirtilen dilin varsayılan durdurma sözcüklerini kaldır |
| <xref:Microsoft.ML.TextCatalog.RemoveStopWords*> | Giriş sütunlarından belirtilen durdurma sözcüklerini kaldırır |
| <xref:Microsoft.ML.TextCatalog.LatentDirichletAllocation*> | Bir belge (float vektörü olarak gösterilir), bir konu kümesi üzerinde kayan bir vektöre dönüştürme |
| <xref:Microsoft.ML.TextCatalog.ApplyWordEmbedding*> | Önceden eğitilen bir model kullanarak metin belirteçlerinin vektörlerini tümce vektörlerine dönüştürme |

## <a name="image-transformations"></a>Görüntü dönüşümleri

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale*> | Bir görüntüyü gri tonlamaya Dönüştür |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToImage*> | Piksel vektörünü Dönüştür<xref:Microsoft.ML.Transforms.Image.ImageDataViewType> |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*> | Giriş görüntüsünden pikselleri sayı vektörüne Dönüştür |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*> | Bir klasörden belleğe görüntü yükleme |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*> | Görüntüleri yeniden boyutlandırma |
| <xref:Microsoft.ML.OnnxCatalog.DnnFeaturizeImage*> | Bir giriş görüntüsünü Özellik vektörüne dönüştürmek için önceden eğitilen derin sinir ağı (DNN) modeli uygular |

## <a name="categorical-data-transformations"></a>Kategorik veri dönüştürmeleri

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*> | Bir veya daha fazla metin sütununu [tek yönlü](https://en.wikipedia.org/wiki/One-hot) kodlanmış vektöre dönüştürme |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotHashEncoding*> | Bir veya daha fazla metin sütununu karma tabanlı tek başına kodlanmış vektöre dönüştürme |

## <a name="time-series-data-transformations"></a>Zaman serisi veri dönüştürmeleri

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectAnomalyBySrCnn*> | Spectral artımı (SR) algoritmasını kullanarak giriş zamanı serisi verilerinde bozukluklar algılayın |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectChangePointBySsa*> | Tekil spekme Analizi (SSA) kullanarak zaman serisi verilerinde değişiklik noktalarını Algıla |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectIidChangePoint*> | Uyarlamalı Çekirdek yoğunluğu tahminleri ve Martingale puanlarını kullanarak bağımsız ve özdeş dağıtılmış (IID) zaman serisi verilerinde değişiklik noktalarını Algıla |
| <xref:Microsoft.ML.TimeSeriesCatalog.ForecastBySsa*> | Tekil spekme Analizi (SSA) kullanarak zaman serisi verilerini tahmin etme |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectSpikeBySsa*> | Tekil spekme Analizi (SSA) kullanarak zaman serisi verilerinde ani artışları Algıla |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectIidSpike*> | Uyarlamalı Çekirdek yoğunluğu tahminleri ve Martingale puanlarını kullanarak bağımsız ve özdeş dağıtılmış (IID) zaman serisi verilerinde artışlar Algıla |

## <a name="missing-values"></a>Eksik değerler

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.ExtensionsCatalog.IndicateMissingValues*> | Yeni bir Boole çıkış sütunu oluşturun, giriş sütunundaki değer eksik olduğunda true değerine sahip olur |
| <xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*> | Değer giriş sütununda eksikse, varsayılan değer olarak ayarlanan değeri, aksi takdirde giriş sütununda olmayan yeni bir çıkış sütunu oluşturun |

## <a name="feature-selection"></a>Özellik seçimi

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnCount*> | Varsayılan olmayan değerleri eşikten büyük olan özellikleri seçin |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnMutualInformation*> | Etiket sütunundaki verilerin en bağlı olduğu özellikleri seçin |

## <a name="feature-transformations"></a>Özellik dönüşümleri

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.KernelExpansionCatalog.ApproximatedKernelMap*> | Her giriş vektörünü, iç ürünlerin bir çekirdek işlevini yaklaşık bir şekilde tahmin ettiği, bu sayede özelliklerin doğrusal algoritmalara giriş olarak kullanılabilmesi için, daha düşük boyutlu bir özellik alanı üzerine eşleyin |
| <xref:Microsoft.ML.PcaCatalog.ProjectToPrincipalComponents*> | Asıl bileşen çözümleme algoritmasını uygulayarak giriş özelliği vektörünün boyutlarını azaltma |

## <a name="explainability-transformations"></a>Explainability dönüşümler

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.ExplainabilityCatalog.CalculateFeatureContribution*> | Bir özellik vektörünün her bir öğesi için katkı puanlarını hesaplama |

## <a name="calibration-transformations"></a>Ayarlama dönüşümleri

| Dönüştürme | Tanım |
| --- | --- |
|<xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Platt%28System.String%2CSystem.String%2CSystem.String%29> | Eğitim verilerini kullanarak tahmini parametrelerle Lojistik gerileme kullanarak bir ikili sınıflandırıcının ham Puanını bir sınıf olasılığa dönüştürür |
| <xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Platt%28System.Double%2CSystem.Double%2CSystem.String%29> | Sabit parametrelerle Lojistik gerileme kullanarak bir ikili sınıflandırıcının ham Puanını bir sınıf olasılığa dönüştürür |
| <xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Naive*> | Bir ikili sınıflandırıcının ham Puanını, depo gözlerine puan atayarak bir sınıf olasılığa dönüştürür ve bu da depo gözleri arasındaki dağıtıma göre olasılığı hesaplıyor |
| <xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Isotonic*> | Bir ikili sınıflandırıcının ham Puanını, sınırların konumunun ve depo gözlerinin boyutunun eğitim verileri aracılığıyla tahmin edildiği yerlere puan atayarak bir sınıf olasılığa dönüştürür  |

## <a name="deep-learning-transformations"></a>Derin öğrenme dönüşümleri

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel*> | Giriş verilerini içeri aktarılan bir ONNX modeliyle Dönüştür |
| <xref:Microsoft.ML.TensorflowCatalog.LoadTensorFlowModel*> | Giriş verilerini içeri aktarılan bir TensorFlow modeliyle Dönüştür |

## <a name="custom-transformations"></a>Özel dönüştürmeler

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.CustomMappingCatalog.CustomMapping*> | Varolan sütunları Kullanıcı tanımlı eşleme ile yeni olanlarla Dönüştür |
