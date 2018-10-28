---
title: Veri Dönüşümleri
description: ML.NET içinde desteklenen farklı veri dönüşümleri keşfedin.
ms.date: 10/16/2018
ms.openlocfilehash: 5df4598de6fcd08689d72c378f51d792860ef49c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187747"
---
# <a name="data-transforms"></a>Veri Dönüşümleri

Aşağıdaki tablolarda tüm ML.NET (seçim verileri karşılık gelen tabloya gitmek için tür dönüştürme) desteklenen veri dönüşümleri hakkında bilgiler içerir:

* [Kategorik](#categorical)
* [Combiners ve segregators](#combiners-and-segregators)
* [Özellik Seçimi](#feature-selection)
* [Featurizers](#featurizers)
* [Etiket Ayrıştırma](#label-parsing)
* [Eksik değerleri](#missing-values)
* [Normalleştirme](#normalization)
* [Satır filtreleri](#row-filters)
* [Şema](#schema)
* [Metin işleme ve özellik kazandırma sayesinde](#text-processing-and-featurization)
* [Çeşitli](#miscellaneous)

> [!NOTE]
> ML.NET şu anda Önizleme aşamasındadır. Tüm veri dönüşümleri şu anda desteklenmiyor. Belirli bir dönüştürme için bir istek göndermek için bir sorun açın [dotnet/machinelearning](https://github.com/dotnet/machinelearning/issues) GitHub deposu.

## <a name="categorical"></a>Kategorik

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.CategoricalHashOneHotVectorizer> | Kategorik değişkeni karma tabanlı kodlama ile kodlar. |
| <xref:Microsoft.ML.Legacy.Transforms.CategoricalOneHotVectorizer> | Kategorik değişkeni bir terim sözlük dayalı bir sık erişimli'ı kodlamayla kodlar. |

## <a name="combiners-and-segregators"></a>Combiners ve segregators

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.CombinerByContiguousGroupId> | Grupları bir skaler sütuna bitişik grubu kimliğini temel alan bir vektör değerleri |
| <xref:Microsoft.ML.Legacy.Transforms.FeatureCombiner> | Tüm özellikleri bir özellik sütun halinde birleştirir. |
| <xref:Microsoft.ML.Legacy.Transforms.ManyHeterogeneousModelCombiner> | Tek bir PredictorModel TransformModels ve bir PredictorModel dizisine birleştirir. |
| <xref:Microsoft.ML.Legacy.Transforms.ModelCombiner> | Tek bir model TransformModels dizisine birleştirir. |
| <xref:Microsoft.ML.Legacy.Transforms.Segregator> | Vektör sütunların satır dizileri; grubunu çözer. Kikare dağılımının grubu Dönüştür. |
| <xref:Microsoft.ML.Legacy.Transforms.TwoHeterogeneousModelCombiner> | Bir TransformModel ve bir PredictorModel tek bir PredictorModel birleştirir. |

## <a name="feature-selection"></a>Özellik Seçimi

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.FeatureSelectorByCount> | Varsayılan olmayan değerlerin sayısını bir eşiğe eşitse veya daha büyük olduğu yuvaları seçer. |
| <xref:Microsoft.ML.Legacy.Transforms.FeatureSelectorByMutualInformation> | Etiket sütunu ile karşılıklı bilgilerine göre sıralanmış tüm belirtilen sütunlara top k yuvaları seçer. |

## <a name="featurizers"></a>Featurizers

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.HashConverter> | Sütun değerleri karmaları dönüştürür. Bu dönüşüm, hem sayısal ve metin girişleri, hem tek hem de vektör değerli sütunlar kabul eder. |
| <xref:Microsoft.ML.Legacy.Transforms.TreeLeafFeaturizer> | Bir ağaç topluluğu eğitir veya bir dosyadan yükler ve ardından bir sayısal özellik vektör üç çıktıları eşler: 1. Ağaç topluluğu tek tek ağaç içeren vektör çıkarır. 2. Ağaç topluluğu içinde özellik vektör denk bırakır belirten bir vektör. 3. Ağaç topluluğu içinde özellik vektör denk yolları belirten bir vektör. Bir model dosyası bir eğitmen belirtilirse, vektör model dosyası kullanır. Hiçbiri belirtilmezse, vektör varsayılan FastTree modeli eğitme. Bu, anahtar etiketlerini bunların isteğe bağlı olarak derlenemiyor dizinlerini doğrultusunda bir regresyon modeli eğitimi tarafından işleyebilir. |

## <a name="label-parsing"></a>Etiket Ayrıştırma

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.Dictionarizer> | Dönüştürür (sözcükler, sayılar, vb.) bir sözlükte dizini oluşturmak için değerleri girin. |
| <xref:Microsoft.ML.Legacy.Transforms.LabelColumnKeyBooleanConverter> | Etiket anahtarı ya da bool, sınıflandırma için uygun hale getirmek için (gerekirse) dönüştürür. |
| <xref:Microsoft.ML.Legacy.Transforms.LabelIndicator> | Etiket remapper OVA tarafından kullanılır. |
| <xref:Microsoft.ML.Legacy.Transforms.LabelToFloatConverter> | Regresyon için uygun hale getirmek için kayan nokta etiketi dönüştürür. |
| <xref:Microsoft.ML.Legacy.Transforms.PredictedLabelColumnOriginalValueConverter> | Türü bool olmadığı sürece bir tahmin edilen etiket sütunu, özgün değerlerine dönüştürür. |

## <a name="missing-values"></a>Eksik değerleri

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.MissingValueHandler> | Varsayılan değer ya da (yalnızca metin olmayan sütunları) ortalama/en düşük/en yüksek değeri ile değiştirerek eksik değerleri işleyin. Gösterge sütunu, isteğe bağlı olarak giriş sütun türü sayısal ise birleştirilebilir. |
| <xref:Microsoft.ML.Legacy.Transforms.MissingValueIndicator> | Bir boolean çıktı sütunu giriş sütunu giriş sütunundaki değeri eksik olduğu çıkış değeri true ise, aynı sayıda yuva oluşturun. |
| <xref:Microsoft.ML.Legacy.Transforms.MissingValuesDropper> | NAs vektör sütunları kaldırır. |
| <xref:Microsoft.ML.Legacy.Transforms.MissingValuesRowDropper> | Eksik değerler içeren satırları filtreler. |
| <xref:Microsoft.ML.Legacy.Transforms.MissingValueSubstitutor> | Bir çıkış sütunu aynı türde ve burada eksik değerler varsayılan değer veya en düşük/ortalama/en yüksek değerini (yalnızca metin olmayan sütunları) ile değiştirilir giriş sütun boyutunu oluşturun. |

## <a name="normalization"></a>Normalleştirme

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.BinNormalizer> | Equidensity bölmeler değerler atanır ve bir değer için kendi bin_number eşlendi / number_of_bins. |
| <xref:Microsoft.ML.Legacy.Transforms.ConditionalNormalizer> | Sütunları, yalnızca gerektiğinde Normalleştir. |
| <xref:Microsoft.ML.Legacy.Transforms.GlobalContrastNormalizer> | Giriş değerleri üzerinde bir genel Karşıtlık normalleştirme gerçekleştirir: Y = (s * X - M) / D, s, Ölçek olduğu M ortalama ve D L2 norm ya da standart sapma. | 
| <xref:Microsoft.ML.Legacy.Transforms.LogMeanVarianceNormalizer> | Hesaplanan ortalama ve veri logaritmasını varyansını göre veri normalleştirir. |
| <xref:Microsoft.ML.Legacy.Transforms.LpNormalizer> | Vektör (satırlar) (L2, L1 veya LInf) birim norm ölçeklendirme tarafından ayrı ayrı Normalleştir. Bir vektör X: Y aşağıdaki işlemi gerçekleştirir (X - M) = / D, M Burada, ortalama ve D L2 norm, L1 norm veya LInf norm. |
| <xref:Microsoft.ML.Legacy.Transforms.MeanVarianceNormalizer> | Hesaplanan ortalama ve varyans verilerin göre veri normalleştirir. |
| <xref:Microsoft.ML.Legacy.Transforms.MinMaxNormalizer> | Gözlemlenen minimum ve maksimum değerleri veri verileri normalleştirir. |

## <a name="row-filters"></a>Satır filtreleri

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.RowRangeFilter> | Dataview tek, Double veya anahtarı (bitişik) türünde bir sütun üzerinde filtreler. Belirtilen en düşük/en yüksek aralıktaki değerleri tutar. NaN'ler her zaman filtrelenir. Giriş anahtar türü varsa, yüzde değerlerini sayısı min/maks kabul edilir. |
| <xref:Microsoft.ML.Legacy.Transforms.RowSkipAndTakeFilter> | İsteğe bağlı bir uzaklık konumunda satır kümesini giriş sınırlama sağlar. Veri sayfalama uygulama için kullanılabilir. |
| <xref:Microsoft.ML.Legacy.Transforms.RowSkipFilter> | Alt satır kümesine giriş satır sayısı atlayarak sınırlama sağlar. |
| <xref:Microsoft.ML.Legacy.Transforms.RowTakeFilter> | Alt satır kümesine giriş N ilk satırları yararlanarak sınırlama sağlar. |

## <a name="schema"></a>Şema

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.ColumnConcatenator> | Aynı öğesi türünde iki sütun art arda ekler. |
| <xref:Microsoft.ML.Legacy.Transforms.ColumnCopier> | Veri kümesindeki sütunları çoğaltır.|
| <xref:Microsoft.ML.Legacy.Transforms.ColumnDropper> | Sütunları veri kümesinden bırakır. |
| <xref:Microsoft.ML.Legacy.Transforms.ColumnSelector> | Bir dizi bırakmadan diğer tüm sütunlar seçer. |
| <xref:Microsoft.ML.Legacy.Transforms.ColumnTypeConverter> | Bir sütunun standart dönüştürmeler kullanarak farklı bir türe dönüştürür. |
| <xref:Microsoft.ML.Legacy.Transforms.KeyToTextConverter> | KeyToValueTransform karşılık gelen değerlere KeyValues meta verilerindeki anahtar dizinlerini eşlemek için KeyValues meta verileri kullanır. |
| <xref:Microsoft.ML.Legacy.Transforms.NGramTranslator> | Bir paketi sayısı, anahtarların belirli bir vektör içindeki ngrams (uzunluğu 1-n ardışık değerleri dizisi) üretir. Bunu ngrams sözlüğü oluşturmak ve paketi dizin olarak sözlükte kimliğini kullanarak yapar. | 
| <xref:Microsoft.ML.Legacy.Transforms.OptionalColumnCreator> | Kaynak sütunu seri durumundan çıkarma sonra mevcut değilse, doğru tür ve varsayılan değerleri ile bir sütun oluşturun. |

## <a name="text-processing-and-featurization"></a>Metin işleme ve özellik kazandırma sayesinde

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.CharacterTokenizer> | Simgeleştirici karakter odaklı burada metin bir karakter dizisi olarak değerlendirilir. |
| <xref:Microsoft.ML.Legacy.Transforms.TextFeaturizer> | Koleksiyona sayısal özellik vektör metin belgesi açar Dönüştür. Özellik vektör verilen parçalanmış metin (sözcük ve/veya karakter) ngrams normalleştirilmiş sayısı ' dir. |
| <xref:Microsoft.ML.Legacy.Transforms.TextToKeyConverter> | Dönüştürür (sözcükler, sayılar, vb.) bir sözlükte dizini oluşturmak için değerleri girin. |
| <xref:Microsoft.ML.Legacy.Transforms.WordEmbeddings> | Önceden eğitilmiş bir modeli kullanarak sayısal vektörleri metin belirteçleri vektörleri dönüştürür Dönüştür. Teknik hakkında daha fazla bilgi için bkz. [Word katıştırma](https://en.wikipedia.org/wiki/Word_embedding) Wikipedia sayfasında. |
| <xref:Microsoft.ML.Legacy.Transforms.WordTokenizer> | Bu dönüştürme için giriş metni alır ve çıktıyı bir vektördür orijinal metni (belirteçleri) sözcüklerini içeren metin. Ayırıcı, boşluk olmakla birlikte herhangi bir karakterle (veya birden çok karakter) belirtilebilir. |

## <a name="miscellaneous"></a>Çeşitli

| Dönüştürme | Tanım |
| --- | --- |
| <xref:Microsoft.ML.Legacy.Transforms.ApproximateBootstrapSampler> | Önyükleme örnekleme yaklaşık. |
| <xref:Microsoft.ML.Legacy.Transforms.BinaryPredictionScoreColumnsRenamer> | İkili tahmin için PredictedLabel yeniden adlandırır ve Puanlamak pozitif sınıfının adını içeren sütun.|
| <xref:Microsoft.ML.Legacy.Transforms.DataCache> | Belirtilen önbellek seçeneğini kullanarak önbelleğe alır. |
| <xref:Microsoft.ML.Legacy.Transforms.DatasetScorer> | Bir veri kümesi bir tahmin modeli ile puanlar. |
| <xref:Microsoft.ML.Legacy.Transforms.DatasetTransformScorer> | Bir veri kümesi bir dönüştürme modeliyle puanlar. |
| <xref:Microsoft.ML.Legacy.Transforms.NoOperation> | Hiçbir şey yapılmaz. |
| <xref:Microsoft.ML.Legacy.Transforms.RandomNumberGenerator> | Oluşturulan bir sayı dizisi içeren bir sütun ekler. |
| <xref:Microsoft.ML.Legacy.Transforms.ScoreColumnSelector> | Seçer yalnızca son sütun ve bağımsız değişkenlerde belirtilen sütunlar puan. |
| <xref:Microsoft.ML.Legacy.Transforms.Scorer> | Tahmin modelinin bir dönüştürme modeline kapatır. |
| <xref:Microsoft.ML.Legacy.Transforms.SentimentAnalyzer> | Giriş dizesi puanlamak için bir yaklaşım kullanan modeli kullanır. |
| <xref:Microsoft.ML.Legacy.Transforms.TrainTestDatasetSplitter> | Gruplama eğitme ve test kümesine ayarlar. |
