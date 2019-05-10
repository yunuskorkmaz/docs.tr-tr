---
title: Veri Dönüşümleri
description: ML.NET içinde desteklenen özellik Mühendisliği bileşenleri keşfedin.
author: natke
ms.author: nakersha
ms.date: 04/02/2019
ms.openlocfilehash: d3261f88a8e52c71f8ddf4d3d5c90b2e2b22b620
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64636544"
---
# <a name="data-transformations"></a>Veri Dönüşümleri

Veri Dönüşümleri, model yönetimi için veri hazırlamak için kullanılır. Bu kılavuzun dönüştürmeleri uygulayan sınıf döndüren [IEstimator](xref:Microsoft.ML.IEstimator`1) arabirimi. Veri Dönüşümleri birbirine zincirlenebilir. Her dönüştürme hem bekliyor ve belirli türlerin ve bağlantılı başvuru belgelerinde belirtilen biçimden veri üretir.

Bazı veri dönüşümleri kendi parametrelerini hesaplamak için eğitim verilerini gerektirir. Örneğin: <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> transformer, ortalama ve eğitim verilerini sırasında varyansını hesaplar `Fit()` işlemi, bu parametreleri kullanır `Transform()` işlemi. 

Eğitim verileri diğer veri dönüşümleri gerektirmez. Örneğin: <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale*> dönüşümü gerçekleştirebilirsiniz `Transform()` işlemi sırasında herhangi bir eğitim veri görülen kalmadan `Fit()` işlemi.

## <a name="column-mapping-and-grouping"></a>Sütun eşleme ve gruplandırma

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A> | Yeni bir çıktı sütunda bir veya daha fazla giriş sütunları birleştirin |
| <xref:Microsoft.ML.TransformExtensionsCatalog.CopyColumns%2A> | Kopyalayın ve bir veya daha fazla giriş sütunları yeniden adlandırma |
| <xref:Microsoft.ML.TransformExtensionsCatalog.DropColumns%2A> | Bir veya daha fazla giriş sütunları kaldırın |
| <xref:Microsoft.ML.TransformExtensionsCatalog.SelectColumns%2A> | Giriş verileri tutmak için bir veya daha fazla sütun seçin |

## <a name="normalization-and-scaling"></a>Normalleştirme ve ölçeklendirme

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> | Ortalamasını (eğitim verilerini) çıkarın ve varyansını (eğitim verileri) Böl |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeLogMeanVariance%2A> | Eğitim verileri logaritmasını üzerinde tabanlı normalleştirin |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeLpNorm%2A> | Ölçeklendirme giriş vektör tarafından kendi [lp norm](https://en.wikipedia.org/wiki/Lp_space#The_p-norm_in_finite_dimensions), p burada 1, 2 veya sonsuz. L2 (Euclidean uzaklık) norm varsayılanlara |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeGlobalContrast%2A> | L2 norm (satır verilerinin) ya da sıfıra bölünme ya da standart sapma ve satır veri ortalamasını çıkararak her değeri bir satır ölçeklendirin ve yapılandırılabilir bir ölçek faktörü (varsayılan 2) çarpın |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A> | Giriş değeri bin dizinine atayın ve 0 ile 1 arasında kayan nokta değeri üretmek için bölme sayısı bölün. Eğitim verileri depo arasında eşit bir şekilde dağıtmak için depo sınırları hesaplanır |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeSupervisedBinning%2A> | Etiket sütunu, bağıntı dayalı bir depo için giriş değeri Ata |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A> | Eğitim verileri, minimum ve maksimum değerler arasındaki farkın tarafından giriş ölçeklendirin |

## <a name="conversions-between-data-types"></a>Veri türleri arasında dönüştürmeler

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.ConvertType%2A> | Bir giriş sütun türü için yeni bir tür dönüştürme |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValue*> | Sağlanan sözlük eşleştirmeleri anahtarlardan (Kategoriler) için değerleri eşleyin |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*> | Anahtarları (Kategoriler) için değerleri gelen giriş verilerinin eşleme oluşturarak eşleyin |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue*> | Anahtarları özgün değerlerine dönüştürme |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToVector*> | Anahtarları özgün değerlerine sahip vektörleri için Geri Dönüştür |
| <xref:Microsoft.ML.ConversionsCatalog.MapKeyToBinaryVector*> | Anahtarlar için özgün değerler geri ikili vektör dönüştürme |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash*> | Karma Giriş sütunundaki değeri |

## <a name="text-transformations"></a>Metin dönüştürmeleri

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.TextCatalog.FeaturizeText*> | Bir metin sütunu normalleştirilmiş ngrams char-gram sayısı ve kayan nokta diziye Dönüştür | 
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoWords*> | Bir veya daha fazla metin sütunları tek tek sözcüklere bölme |
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoCharactersAsKeys*> | Bir veya daha fazla metin sütunları karakterlerin tek tek float konuları kümesi bölün. |
| <xref:Microsoft.ML.TextCatalog.NormalizeText*> | Durumu değiştirmek, aksanlı işaretleri, noktalama işaretleri ve sayılar Kaldır |
| <xref:Microsoft.ML.TextCatalog.ProduceNgrams*> | Bir paketi ngrams (ardışık bir kelimelerin dizileri) sayısı metin sütunu Dönüştür|
| <xref:Microsoft.ML.TextCatalog.ProduceWordBags*> | Bir paketi ngrams vektör sayısı metin sütunu Dönüştür |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedNgrams*> | Metin sütunu karma ngram sayıları vektörü Dönüştür |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedWordBags*> | Bir karma ngram sayıları paketi metin sütunu Dönüştür |
| <xref:Microsoft.ML.TextCatalog.RemoveDefaultStopWords*>  | Belirtilen dil için varsayılan durdurma sözcükleri giriş sütunları Kaldır |
| <xref:Microsoft.ML.TextCatalog.RemoveStopWords*> | Kaldırır belirtilen giriş sütunlarından durdurma sözcükleri |
| <xref:Microsoft.ML.TextCatalog.LatentDirichletAllocation*> | (Float oluşan bir vektörü temsil edilir) bir belge konuları kümesi vektörü float olarak dönüştürme |
| <xref:Microsoft.ML.TextCatalog.ApplyWordEmbedding*> | Metin belirteçleri vektörleri önceden eğitilmiş bir modeli kullanarak cümle vektör dönüştürme |

## <a name="image-transformations"></a>Resim dönüşümleri

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale*> | Görüntüyü gri tonlamaya dönüştürme |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToImage*> | Piksel olarak oluşan bir vektörü Dönüştür <xref:Microsoft.ML.Transforms.Image.ImageDataViewType> |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*> | Piksel giriş görüntüden sayıdan oluşan bir vektörü Dönüştür |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*> | Görüntüleri bir klasörden belleğe yükleyin. |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*> | Görüntüleri yeniden boyutlandırma |

## <a name="categorical-data-transformations"></a>Kategorik veri dönüşümleri

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*> | Bir veya daha fazla metin sütunları Dönüştür [bir seyrek](https://en.wikipedia.org/wiki/One-hot) kodlanmış vektörleri |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotHashEncoding*> | Daha fazla tek metin sütunları karma tabanlı bir seyrek kodlanmış vektörleri dönüştürün |

## <a name="missing-values"></a>Eksik değerleri

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.ExtensionsCatalog.IndicateMissingValues*> | Giriş sütunundaki değeri eksik olduğunda, değer true ise yeni bir Boole çıkış sütun oluşturma |
| <xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*> | Yeni çıkış değeri, değerin giriş sütunu eksik olması durumunda varsayılan bir değer ve giriş değeri ayarlanır. bir sütun, aksi takdirde oluşturun |

## <a name="feature-selection"></a>Özellik Seçimi

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnCount*> | Varsayılan olmayan değerleri eşik değerinden yüksek olan özellikleri seçin |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnMutualInformation*> | Etiket sütunundaki verileri en bağımlı olduğu özellikleri seçin |

## <a name="custom-transformations"></a>Özel dönüşümler

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.CustomMappingCatalog.CustomMapping*> | Kullanıcı tanımlı bir eşleme ile yenilerini üzerine mevcut sütunları Dönüştür |
