---
title: Veri dönüşümleri
description: ML.NET desteklenen özellik mühendisliği bileşenlerini keşfedin.
ms.date: 04/02/2019
ms.openlocfilehash: ca410b475c556db5ad4c3862fb79755b455d6830
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79398925"
---
# <a name="data-transformations"></a>Veri dönüşümleri

Veri dönüşümleri için kullanılır:

- model eğitimi için veri hazırlama
- içe aktarılan bir modeli TensorFlow veya ONNX biçiminde uygulayın
- bir modelden geçirildikten sonra işlem sonrası veriler

Bu kılavuzdaki dönüşümler [IEstimator](xref:Microsoft.ML.IEstimator%601) arabirimini uygulayan sınıfları döndürer. Veri dönüşümleri birbirine zincirlenebilir. Her dönüşüm, bağlı başvuru belgelerinde belirtilen belirli tür ve biçimlere ait verileri hem bekler hem de üretir.

Bazı veri dönüşümleri parametrelerini hesaplamak için eğitim verileri gerektirir. Örneğin: <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> `Fit()` transformatör, işlem sırasında eğitim verilerinin ortalama ve varyansını hesaplar ve `Transform()` bu parametreleri operasyonda kullanır.

Diğer veri dönüşümleri eğitim verileri gerektirmez. Örneğin: <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale%2A> dönüştürme işlemi, `Transform()` işlem sırasında herhangi bir eğitim `Fit()` verisi görmeden gerçekleştirebilir.

## <a name="column-mapping-and-grouping"></a>Sütun eşleme ve gruplandırma

| Dönüşüm | Tanım |
| --- | --- |
| <xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A> | Bir veya daha fazla giriş sütunu yeni bir çıktı sütununa birleştirme |
| <xref:Microsoft.ML.TransformExtensionsCatalog.CopyColumns%2A> | Bir veya daha fazla giriş sütunu kopyalama ve yeniden adlandırma |
| <xref:Microsoft.ML.TransformExtensionsCatalog.DropColumns%2A> | Bir veya daha fazla giriş sütunu bırak |
| <xref:Microsoft.ML.TransformExtensionsCatalog.SelectColumns%2A> | Giriş verilerinden uzak tutmak için bir veya daha fazla sütun seçin |

## <a name="normalization-and-scaling"></a>Normalleştirme ve ölçekleme

| Dönüşüm | Tanım |
| --- | --- |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> | Ortalamayı (eğitim verilerinin) çıkarın ve varyansa (eğitim verilerinin) bölün |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeLogMeanVariance%2A> | Eğitim verilerinin logaritma dayalı normale |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeLpNorm%2A> | Giriş vektörlerini, p'nin 1, 2 veya sonsuz olduğu [lp-normlarına](https://en.wikipedia.org/wiki/Lp_space#The_p-norm_in_finite_dimensions)göre ölçeklendirin. L2 (Öklid mesafesi) normuna varsayılan |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeGlobalContrast%2A> | Satır verilerinin ortalamasını çıkararak her değeri bir satırda ölçeklendirin ve standart sapma veya l2-norma (satır verilerinin) bölün ve yapılandırılabilir ölçek faktörüyle (varsayılan 2) çarparak bölün |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A> | Giriş değerini bir depo gözü dizine atayın ve 0 ile 1 arasında float değeri oluşturmak için çöp kutusu sayısına bölün. Depo gözü sınırları, eğitim verilerini kutular arasında eşit olarak dağıtmak için hesaplanır |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeSupervisedBinning%2A> | Giriş değerini etiket sütunuyla olan korelasyonuna göre bir depo gözüne atama |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A> | Girdiyi, eğitim verilerindeki minimum ve maksimum değerler arasındaki farka göre ölçeklendirin |

## <a name="conversions-between-data-types"></a>Veri türleri arasındaki dönüşümler

| Dönüşüm | Tanım |
| --- | --- |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.ConvertType%2A> | Giriş sütunu türünü yeni bir türe dönüştürme |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValue%2A> | Verilen eşleme sözlüğüne göre anahtarlara (kategorilere) eşleme değerleri |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A> | Giriş verilerinden eşleme oluşturarak değerleri anahtarlara (kategorilere) eşle |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A> | Anahtarları özgün değerlerine dönüştürme |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToVector%2A> | Tuşları özgün değerlerin vektörlerine dönüştürme |
| <xref:Microsoft.ML.ConversionsCatalog.MapKeyToBinaryVector%2A> | Tuşları özgün değerlerden oluşan ikili vektöre dönüştürme |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A> | Giriş sütunundaki değeri karma |

## <a name="text-transformations"></a>Metin dönüştürmeleri

| Dönüşüm | Tanım |
| --- | --- |
| <xref:Microsoft.ML.TextCatalog.FeaturizeText%2A> | Metin sütununu normalleştirilmiş ngram ve char-gram sayıları bir float diziiçine dönüştürme |
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A> | Bir veya daha fazla metin sütunlarını tek tek sözcüklere bölme |
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoCharactersAsKeys%2A> | Bir veya daha fazla metin sütununun tek tek karakterlere bölünmesi bir dizi konu üzerinde yüzer |
| <xref:Microsoft.ML.TextCatalog.NormalizeText%2A> | Servis talebi değiştirme, akdekritik işaretleri, noktalama işaretlerini ve sayıları kaldırma |
| <xref:Microsoft.ML.TextCatalog.ProduceNgrams%2A> | Metin sütununu ngrams sayılarından oluşan bir torbaya dönüştürme (ardışık sözcük dizileri)|
| <xref:Microsoft.ML.TextCatalog.ProduceWordBags%2A> | Metin sütunu ngrams vektör ükontlarının olduğu bir torbaya dönüştürme |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedNgrams%2A> | Metin sütunu hashed ngram sayıları vektörüne dönüştürme |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedWordBags%2A> | Metin sütunu haşlama ngram sayıları torbasına dönüştürme |
| <xref:Microsoft.ML.TextCatalog.RemoveDefaultStopWords%2A>  | Giriş sütunlarından belirtilen diliçin varsayılan durdurma sözcüklerini kaldırma |
| <xref:Microsoft.ML.TextCatalog.RemoveStopWords%2A> | Giriş sütunlarından belirtilen durdurma sözcüklerini kaldırır |
| <xref:Microsoft.ML.TextCatalog.LatentDirichletAllocation%2A> | Bir belgeyi (yüzenlerin vektörü olarak temsil edilir) bir dizi konu üzerinde yüzen bir vektöre dönüştürme |
| <xref:Microsoft.ML.TextCatalog.ApplyWordEmbedding%2A> | Metin belirteçlerinin vektörlerini önceden eğitilmiş bir model kullanarak cümle vektörlerine dönüştürme |

## <a name="image-transformations"></a>Görüntü dönüşümleri

| Dönüşüm | Tanım |
| --- | --- |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale%2A> | Görüntüyü gri tonlama olarak dönüştürme |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToImage%2A> | Piksel vektörü<xref:Microsoft.ML.Transforms.Image.ImageDataViewType> |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels%2A> | Giriş görüntüsündeki pikselleri sayı vektörüne dönüştürme |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages%2A> | Bir klasördeki görüntüleri belleğe yükleme |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages%2A> | Görüntüleri yeniden boyutlandırma |
| <xref:Microsoft.ML.OnnxCatalog.DnnFeaturizeImage%2A> | Giriş görüntüsünü bir özellik vektörüne dönüştürmek için önceden eğitilmiş bir derin sinir ağı (DNN) modeli uygular |

## <a name="categorical-data-transformations"></a>Kategorik veri dönüşümleri

| Dönüşüm | Tanım |
| --- | --- |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A> | Bir veya daha fazla metin sütunu [tek sıcak](https://en.wikipedia.org/wiki/One-hot) kodlanmış vektörlere dönüştürme |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotHashEncoding%2A> | Bir veya daha fazla metin sütunlarını karma tabanlı tek sıcak kodlanmış vektörlere dönüştürme |

## <a name="time-series-data-transformations"></a>Zaman serisi veri dönüşümleri

| Dönüşüm | Tanım |
| --- | --- |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectAnomalyBySrCnn%2A> | Spektral Rezidüm (SR) algoritmasını kullanarak giriş zaman serisi verilerindeki anormallikleri tespit |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectChangePointBySsa%2A> | Tekil spektrum analizini (SSA) kullanarak zaman serisi verilerindeki değişim noktalarını algılama |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectIidChangePoint%2A> | Uyarlanabilir çekirdek yoğunluğu tahminleri ve martingale skorları kullanarak bağımsız ve aynı şekilde dağıtılmış (IID) zaman serisi verilerindeki değişim noktalarını algılama |
| <xref:Microsoft.ML.TimeSeriesCatalog.ForecastBySsa%2A> | Tekil spektrum analizi (SSA) kullanarak tahmin zaman serisi verileri |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectSpikeBySsa%2A> | Tekil spektrum analizini (SSA) kullanarak zaman serisi verilerindeki ani artışları algılama |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectIidSpike%2A> | Uyarlanabilir çekirdek yoğunluğu tahminleri ve martingale skorları kullanarak bağımsız ve aynı şekilde dağıtılmış (IID) zaman serisi verilerindeki ani artışları tespit etme |

## <a name="missing-values"></a>Eksik değerler

| Dönüşüm | Tanım |
| --- | --- |
| <xref:Microsoft.ML.ExtensionsCatalog.IndicateMissingValues%2A> | Giriş sütunundaki değer eksik olduğunda değeri doğru olan yeni bir boolean çıkış sütunu oluşturma |
| <xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A> | Giriş sütunundaki değer eksikse değeri varsayılan değerolarak ayarlanan yeni bir çıktı sütunu ve aksi takdirde giriş değeri oluşturma |

## <a name="feature-selection"></a>Özellik seçimi

| Dönüşüm | Tanım |
| --- | --- |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnCount%2A> | Varsayılan olmayan değerleri bir eşiğe göre büyük olan özellikleri seçme |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnMutualInformation%2A> | Etiket sütunundaki verilerin en bağımlı olduğu özellikleri seçin |

## <a name="feature-transformations"></a>Özellik dönüşümleri

| Dönüşüm | Tanım |
| --- | --- |
| <xref:Microsoft.ML.KernelExpansionCatalog.ApproximatedKernelMap%2A> | Özelliklerin doğrusal algoritmalara giriş olarak kullanılabileceğini, böylece her giriş vektörü iç ürünlerin çekirdek işlevine yakın olduğu daha düşük boyutlu bir özellik alanına eşle |
| <xref:Microsoft.ML.PcaCatalog.ProjectToPrincipalComponents%2A> | Temel Bileşen Analizi algoritmasını uygulayarak giriş özelliği vektörünün boyutlarını küçültme |

## <a name="explainability-transformations"></a>Açıklanabilirlik dönüşümleri

| Dönüşüm | Tanım |
| --- | --- |
| <xref:Microsoft.ML.ExplainabilityCatalog.CalculateFeatureContribution%2A> | Özellik vektörünün her öğesi için katkı puanlarını hesaplama |

## <a name="calibration-transformations"></a>Kalibrasyon dönüşümleri

| Dönüşüm | Tanım |
| --- | --- |
|<xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Platt%28System.String%2CSystem.String%2CSystem.String%29> | İkili sınıflandırıcı ham skoru, eğitim verileri kullanılarak tahmin edilen parametrelerle lojistik regresyon kullanarak sınıf olasılığına dönüştürür |
| <xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Platt%28System.Double%2CSystem.Double%2CSystem.String%29> | Sabit parametrelerle lojistik regresyon kullanarak ikili sınıflandırıcı ham skoru sınıf olasılığına dönüştürür |
| <xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Naive%2A> | İkili sınıflandırıcı ham skoru, çöp kutularına puan atayarak ve kutular arasındaki dağılıma göre olasılığı hesaplayarak sınıf olasılığına dönüştürür |
| <xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Isotonic%2A> | İkili sınıflandırıcı ham skoru, sınırların konumunun ve depo kutularının boyutunun eğitim verilerini kullanarak tahmin edildiği kutulara puan atayarak sınıf olasılığına dönüştürür  |

## <a name="deep-learning-transformations"></a>Derin öğrenme dönüşümleri

| Dönüşüm | Tanım |
| --- | --- |
| <xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel%2A> | İçe aktarılan BIR ONNX modeliyle giriş verilerini dönüştürme |
| <xref:Microsoft.ML.TensorflowCatalog.LoadTensorFlowModel%2A> | İçe aktarılan TensorFlow modeliyle giriş verilerini dönüştürme |

## <a name="custom-transformations"></a>Özel dönüşümler

| Dönüşüm | Tanım |
| --- | --- |
| <xref:Microsoft.ML.CustomMappingCatalog.CustomMapping%2A> | Kullanıcı tanımlı eşleme yle varolan sütunları yeni sütunlara dönüştürme |
