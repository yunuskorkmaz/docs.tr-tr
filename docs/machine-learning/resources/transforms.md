---
title: Veri Dönüşümleri | ML.NET
description: ML.NET içinde desteklenen özellik Mühendisliği bileşenleri keşfedin.
author: natke
ms.author: nakersha
ms.date: 04/02/2019
ms.openlocfilehash: 506abcc826059f4d252378b1bde0b852949a42e1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62019145"
---
# <a name="data-transformations"></a><span data-ttu-id="a1044-103">Veri Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="a1044-103">Data transformations</span></span>

<span data-ttu-id="a1044-104">Veri Dönüşümleri, model yönetimi için veri hazırlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a1044-104">Data transformations are used to prepare data for model training.</span></span> <span data-ttu-id="a1044-105">Bu kılavuzun dönüştürmeleri uygulayan sınıf döndüren [IEstimator](xref:Microsoft.ML.IEstimator`1) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="a1044-105">The transformations in this guide return classes that implement the [IEstimator](xref:Microsoft.ML.IEstimator`1) interface.</span></span> <span data-ttu-id="a1044-106">Veri Dönüşümleri birbirine zincirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="a1044-106">Data transformations can be chained together.</span></span> <span data-ttu-id="a1044-107">Her dönüştürme hem bekliyor ve belirli türlerin ve bağlantılı başvuru belgelerinde belirtilen biçimden veri üretir.</span><span class="sxs-lookup"><span data-stu-id="a1044-107">Each transformation both expects and produces data of specific types and formats, which are specified in the linked reference documentation.</span></span>

<span data-ttu-id="a1044-108">Bazı veri dönüşümleri kendi parametrelerini hesaplamak için eğitim verilerini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a1044-108">Some data transformations require training data to calculate their parameters.</span></span> <span data-ttu-id="a1044-109">Örneğin: <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> transformer, ortalama ve eğitim verilerini sırasında varyansını hesaplar `Fit()` işlemi, bu parametreleri kullanır `Transform()` işlemi.</span><span class="sxs-lookup"><span data-stu-id="a1044-109">For example: the <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> transformer calculates the mean and variance of the training data during the `Fit()` operation, and uses those parameters in the `Transform()` operation.</span></span> 

<span data-ttu-id="a1044-110">Eğitim verileri diğer veri dönüşümleri gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="a1044-110">Other data transformations don't require training data.</span></span> <span data-ttu-id="a1044-111">Örneğin: <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale*> dönüşümü gerçekleştirebilirsiniz `Transform()` işlemi sırasında herhangi bir eğitim veri görülen kalmadan `Fit()` işlemi.</span><span class="sxs-lookup"><span data-stu-id="a1044-111">For example: the <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale*> transformation can perform the `Transform()` operation without having seen any training data during the `Fit()` operation.</span></span>

## <a name="column-mapping-and-grouping"></a><span data-ttu-id="a1044-112">Sütun eşleme ve gruplandırma</span><span class="sxs-lookup"><span data-stu-id="a1044-112">Column mapping and grouping</span></span>

| <span data-ttu-id="a1044-113">Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="a1044-113">Transform</span></span> | <span data-ttu-id="a1044-114">Tanım</span><span class="sxs-lookup"><span data-stu-id="a1044-114">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A> | <span data-ttu-id="a1044-115">Yeni bir çıktı sütunda bir veya daha fazla giriş sütunları birleştirin</span><span class="sxs-lookup"><span data-stu-id="a1044-115">Concatenate one or more input columns into a new output column</span></span> |
| <xref:Microsoft.ML.TransformExtensionsCatalog.CopyColumns%2A> | <span data-ttu-id="a1044-116">Kopyalayın ve bir veya daha fazla giriş sütunları yeniden adlandırma</span><span class="sxs-lookup"><span data-stu-id="a1044-116">Copy and rename one or more input columns</span></span> |
| <xref:Microsoft.ML.TransformExtensionsCatalog.DropColumns%2A> | <span data-ttu-id="a1044-117">Bir veya daha fazla giriş sütunları kaldırın</span><span class="sxs-lookup"><span data-stu-id="a1044-117">Drop one or more input columns</span></span> |
| <xref:Microsoft.ML.TransformExtensionsCatalog.SelectColumns%2A> | <span data-ttu-id="a1044-118">Giriş verileri tutmak için bir veya daha fazla sütun seçin</span><span class="sxs-lookup"><span data-stu-id="a1044-118">Select one or more columns to keep from the input data</span></span> |

## <a name="normalization-and-scaling"></a><span data-ttu-id="a1044-119">Normalleştirme ve ölçeklendirme</span><span class="sxs-lookup"><span data-stu-id="a1044-119">Normalization and scaling</span></span>

| <span data-ttu-id="a1044-120">Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="a1044-120">Transform</span></span> | <span data-ttu-id="a1044-121">Tanım</span><span class="sxs-lookup"><span data-stu-id="a1044-121">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> | <span data-ttu-id="a1044-122">Ortalamasını (eğitim verilerini) çıkarın ve varyansını (eğitim verileri) Böl</span><span class="sxs-lookup"><span data-stu-id="a1044-122">Subtract the mean (of the training data) and divide by the variance (of the training data)</span></span> |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeLogMeanVariance%2A> | <span data-ttu-id="a1044-123">Eğitim verileri logaritmasını üzerinde tabanlı normalleştirin</span><span class="sxs-lookup"><span data-stu-id="a1044-123">Normalize based on the logarithm of the training data</span></span> |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeLpNorm%2A> | <span data-ttu-id="a1044-124">Ölçeklendirme giriş vektör tarafından kendi [lp norm](https://en.wikipedia.org/wiki/Lp_space#The_p-norm_in_finite_dimensions), p burada 1, 2 veya sonsuz.</span><span class="sxs-lookup"><span data-stu-id="a1044-124">Scale input vectors by their [lp-norm](https://en.wikipedia.org/wiki/Lp_space#The_p-norm_in_finite_dimensions), where p is 1, 2 or infinity.</span></span> <span data-ttu-id="a1044-125">L2 (Euclidean uzaklık) norm varsayılanlara</span><span class="sxs-lookup"><span data-stu-id="a1044-125">Defaults to the l2 (Euclidean distance) norm</span></span> |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeGlobalContrast%2A> | <span data-ttu-id="a1044-126">L2 norm (satır verilerinin) ya da sıfıra bölünme ya da standart sapma ve satır veri ortalamasını çıkararak her değeri bir satır ölçeklendirin ve yapılandırılabilir bir ölçek faktörü (varsayılan 2) çarpın</span><span class="sxs-lookup"><span data-stu-id="a1044-126">Scale each value in a row by subtracting the mean of the row data and divide by either the standard deviation or l2-norm (of the row data), and multiply by a configurable scale factor (default 2)</span></span> |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A> | <span data-ttu-id="a1044-127">Giriş değeri bin dizinine atayın ve 0 ile 1 arasında kayan nokta değeri üretmek için bölme sayısı bölün.</span><span class="sxs-lookup"><span data-stu-id="a1044-127">Assign the input value to a bin index and divide by the number of bins to produce a float value between 0 and 1.</span></span> <span data-ttu-id="a1044-128">Eğitim verileri depo arasında eşit bir şekilde dağıtmak için depo sınırları hesaplanır</span><span class="sxs-lookup"><span data-stu-id="a1044-128">The bin boundaries are calculated to evenly distribute the training data across bins</span></span> |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeSupervisedBinning%2A> | <span data-ttu-id="a1044-129">Etiket sütunu, bağıntı dayalı bir depo için giriş değeri Ata</span><span class="sxs-lookup"><span data-stu-id="a1044-129">Assign the input value to a bin based on its correlation with label column</span></span> |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A> | <span data-ttu-id="a1044-130">Eğitim verileri, minimum ve maksimum değerler arasındaki farkın tarafından giriş ölçeklendirin</span><span class="sxs-lookup"><span data-stu-id="a1044-130">Scale the input by the difference between the minimum and maximum values in the training data</span></span> |

## <a name="conversions-between-data-types"></a><span data-ttu-id="a1044-131">Veri türleri arasında dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="a1044-131">Conversions between data types</span></span>

| <span data-ttu-id="a1044-132">Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="a1044-132">Transform</span></span> | <span data-ttu-id="a1044-133">Tanım</span><span class="sxs-lookup"><span data-stu-id="a1044-133">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.ConvertType%2A> | <span data-ttu-id="a1044-134">Bir giriş sütun türü için yeni bir tür dönüştürme</span><span class="sxs-lookup"><span data-stu-id="a1044-134">Convert the type of an input column to a new type</span></span> |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValue*> | <span data-ttu-id="a1044-135">Sağlanan sözlük eşleştirmeleri anahtarlardan (Kategoriler) için değerleri eşleyin</span><span class="sxs-lookup"><span data-stu-id="a1044-135">Map values to keys (categories) based on the supplied dictionary of mappings</span></span> |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*> | <span data-ttu-id="a1044-136">Anahtarları (Kategoriler) için değerleri gelen giriş verilerinin eşleme oluşturarak eşleyin</span><span class="sxs-lookup"><span data-stu-id="a1044-136">Map values to keys (categories) by creating the mapping from the input data</span></span> |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue*> | <span data-ttu-id="a1044-137">Anahtarları özgün değerlerine dönüştürme</span><span class="sxs-lookup"><span data-stu-id="a1044-137">Convert keys back to their original values</span></span> |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToVector*> | <span data-ttu-id="a1044-138">Anahtarları özgün değerlerine sahip vektörleri için Geri Dönüştür</span><span class="sxs-lookup"><span data-stu-id="a1044-138">Convert keys back to vectors of original values</span></span> |
| <xref:Microsoft.ML.ConversionsCatalog.MapKeyToBinaryVector*> | <span data-ttu-id="a1044-139">Anahtarlar için özgün değerler geri ikili vektör dönüştürme</span><span class="sxs-lookup"><span data-stu-id="a1044-139">Convert keys back to a binary vector of original values</span></span> |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash*> | <span data-ttu-id="a1044-140">Karma Giriş sütunundaki değeri</span><span class="sxs-lookup"><span data-stu-id="a1044-140">Hash the value in the input column</span></span> |

## <a name="text-transformations"></a><span data-ttu-id="a1044-141">Metin dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="a1044-141">Text transformations</span></span>

| <span data-ttu-id="a1044-142">Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="a1044-142">Transform</span></span> | <span data-ttu-id="a1044-143">Tanım</span><span class="sxs-lookup"><span data-stu-id="a1044-143">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.TextCatalog.FeaturizeText*> | <span data-ttu-id="a1044-144">Bir metin sütunu normalleştirilmiş ngrams char-gram sayısı ve kayan nokta diziye Dönüştür</span><span class="sxs-lookup"><span data-stu-id="a1044-144">Transform a text column into a float array of normalized ngrams and char-grams counts</span></span> | 
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoWords*> | <span data-ttu-id="a1044-145">Bir veya daha fazla metin sütunları tek tek sözcüklere bölme</span><span class="sxs-lookup"><span data-stu-id="a1044-145">Split one or more text columns into individual words</span></span> |
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoCharactersAsKeys*> | <span data-ttu-id="a1044-146">Bir veya daha fazla metin sütunları karakterlerin tek tek float konuları kümesi bölün.</span><span class="sxs-lookup"><span data-stu-id="a1044-146">Split one or more text columns into individual characters floats over a set of topics</span></span> |
| <xref:Microsoft.ML.TextCatalog.NormalizeText*> | <span data-ttu-id="a1044-147">Durumu değiştirmek, aksanlı işaretleri, noktalama işaretleri ve sayılar Kaldır</span><span class="sxs-lookup"><span data-stu-id="a1044-147">Change case, remove diacritical marks, punctuation marks and numbers</span></span> |
| <xref:Microsoft.ML.TextCatalog.ProduceNgrams*> | <span data-ttu-id="a1044-148">Bir paketi ngrams (ardışık bir kelimelerin dizileri) sayısı metin sütunu Dönüştür</span><span class="sxs-lookup"><span data-stu-id="a1044-148">Transform text column into a bag of counts of ngrams (sequences of consecutive words)</span></span>|
| <xref:Microsoft.ML.TextCatalog.ProduceWordBags*> | <span data-ttu-id="a1044-149">Bir paketi ngrams vektör sayısı metin sütunu Dönüştür</span><span class="sxs-lookup"><span data-stu-id="a1044-149">Transform text column into a bag of counts of ngrams vector</span></span> |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedNgrams*> | <span data-ttu-id="a1044-150">Metin sütunu karma ngram sayıları vektörü Dönüştür</span><span class="sxs-lookup"><span data-stu-id="a1044-150">Transform text column into a vector of hashed ngram counts</span></span> |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedWordBags*> | <span data-ttu-id="a1044-151">Bir karma ngram sayıları paketi metin sütunu Dönüştür</span><span class="sxs-lookup"><span data-stu-id="a1044-151">Transform text column into a bag of hashed ngram counts</span></span> |
| <xref:Microsoft.ML.TextCatalog.RemoveDefaultStopWords*>  | <span data-ttu-id="a1044-152">Belirtilen dil için varsayılan durdurma sözcükleri giriş sütunları Kaldır</span><span class="sxs-lookup"><span data-stu-id="a1044-152">Remove default stop words for the specified language from input columns</span></span> |
| <xref:Microsoft.ML.TextCatalog.RemoveStopWords*> | <span data-ttu-id="a1044-153">Kaldırır belirtilen giriş sütunlarından durdurma sözcükleri</span><span class="sxs-lookup"><span data-stu-id="a1044-153">Removes specified stop words from input columns</span></span> |
| <xref:Microsoft.ML.TextCatalog.LatentDirichletAllocation*> | <span data-ttu-id="a1044-154">(Float oluşan bir vektörü temsil edilir) bir belge konuları kümesi vektörü float olarak dönüştürme</span><span class="sxs-lookup"><span data-stu-id="a1044-154">Transform a document (represented as a vector of floats) into a vector of floats over a set of topics</span></span> |
| <xref:Microsoft.ML.TextCatalog.ApplyWordEmbedding*> | <span data-ttu-id="a1044-155">Metin belirteçleri vektörleri önceden eğitilmiş bir modeli kullanarak cümle vektör dönüştürme</span><span class="sxs-lookup"><span data-stu-id="a1044-155">Convert vectors of text tokens into sentence vectors using a pre-trained model</span></span> |

## <a name="image-transformations"></a><span data-ttu-id="a1044-156">Resim dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="a1044-156">Image transformations</span></span>

| <span data-ttu-id="a1044-157">Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="a1044-157">Transform</span></span> | <span data-ttu-id="a1044-158">Tanım</span><span class="sxs-lookup"><span data-stu-id="a1044-158">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale*> | <span data-ttu-id="a1044-159">Görüntüyü gri tonlamaya dönüştürme</span><span class="sxs-lookup"><span data-stu-id="a1044-159">Convert an image to grayscale</span></span> |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToImage*> | <span data-ttu-id="a1044-160">Piksel olarak oluşan bir vektörü Dönüştür <xref:Microsoft.ML.Transforms.Image.ImageDataViewType></span><span class="sxs-lookup"><span data-stu-id="a1044-160">Convert a vector of pixels to <xref:Microsoft.ML.Transforms.Image.ImageDataViewType></span></span> |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*> | <span data-ttu-id="a1044-161">Piksel giriş görüntüden sayıdan oluşan bir vektörü Dönüştür</span><span class="sxs-lookup"><span data-stu-id="a1044-161">Convert pixels from input image into a vector of numbers</span></span> |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*> | <span data-ttu-id="a1044-162">Görüntüleri bir klasörden belleğe yükleyin.</span><span class="sxs-lookup"><span data-stu-id="a1044-162">Load images from a folder into memory</span></span> |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*> | <span data-ttu-id="a1044-163">Görüntüleri yeniden boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="a1044-163">Resize images</span></span> |

## <a name="categorical-data-transformations"></a><span data-ttu-id="a1044-164">Kategorik veri dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="a1044-164">Categorical data transformations</span></span>

| <span data-ttu-id="a1044-165">Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="a1044-165">Transform</span></span> | <span data-ttu-id="a1044-166">Tanım</span><span class="sxs-lookup"><span data-stu-id="a1044-166">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*> | <span data-ttu-id="a1044-167">Bir veya daha fazla metin sütunları Dönüştür [bir seyrek](https://en.wikipedia.org/wiki/One-hot) kodlanmış vektörleri</span><span class="sxs-lookup"><span data-stu-id="a1044-167">Convert one or more text columns into [one-hot](https://en.wikipedia.org/wiki/One-hot) encoded vectors</span></span> |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotHashEncoding*> | <span data-ttu-id="a1044-168">Daha fazla tek metin sütunları karma tabanlı bir seyrek kodlanmış vektörleri dönüştürün</span><span class="sxs-lookup"><span data-stu-id="a1044-168">Convert one more text columns into hash-based one-hot encoded vectors</span></span> |

## <a name="missing-values"></a><span data-ttu-id="a1044-169">Eksik değerleri</span><span class="sxs-lookup"><span data-stu-id="a1044-169">Missing values</span></span>

| <span data-ttu-id="a1044-170">Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="a1044-170">Transform</span></span> | <span data-ttu-id="a1044-171">Tanım</span><span class="sxs-lookup"><span data-stu-id="a1044-171">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.ExtensionsCatalog.IndicateMissingValues*> | <span data-ttu-id="a1044-172">Giriş sütunundaki değeri eksik olduğunda, değer true ise yeni bir Boole çıkış sütun oluşturma</span><span class="sxs-lookup"><span data-stu-id="a1044-172">Create a new boolean output column, the value of which is true when the value in the input column is missing</span></span> |
| <xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*> | <span data-ttu-id="a1044-173">Yeni çıkış değeri, değerin giriş sütunu eksik olması durumunda varsayılan bir değer ve giriş değeri ayarlanır. bir sütun, aksi takdirde oluşturun</span><span class="sxs-lookup"><span data-stu-id="a1044-173">Create a new output column, the value of which is set to a default value if the value is missing from the input column, and the input value otherwise</span></span> |

## <a name="feature-selection"></a><span data-ttu-id="a1044-174">Özellik Seçimi</span><span class="sxs-lookup"><span data-stu-id="a1044-174">Feature selection</span></span>

| <span data-ttu-id="a1044-175">Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="a1044-175">Transform</span></span> | <span data-ttu-id="a1044-176">Tanım</span><span class="sxs-lookup"><span data-stu-id="a1044-176">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnCount*> | <span data-ttu-id="a1044-177">Varsayılan olmayan değerleri eşik değerinden yüksek olan özellikleri seçin</span><span class="sxs-lookup"><span data-stu-id="a1044-177">Select features whose non-default values are greater than a threshold</span></span> |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnMutualInformation*> | <span data-ttu-id="a1044-178">Etiket sütunundaki verileri en bağımlı olduğu özellikleri seçin</span><span class="sxs-lookup"><span data-stu-id="a1044-178">Select the features on which the data in the label column is most dependent</span></span> |

## <a name="custom-transformations"></a><span data-ttu-id="a1044-179">Özel dönüşümler</span><span class="sxs-lookup"><span data-stu-id="a1044-179">Custom transformations</span></span>

| <span data-ttu-id="a1044-180">Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="a1044-180">Transform</span></span> | <span data-ttu-id="a1044-181">Tanım</span><span class="sxs-lookup"><span data-stu-id="a1044-181">Definition</span></span> |
| --- | --- |
| <xref:Microsoft.ML.CustomMappingCatalog.CustomMapping*> | <span data-ttu-id="a1044-182">Kullanıcı tanımlı bir eşleme ile yenilerini üzerine mevcut sütunları Dönüştür</span><span class="sxs-lookup"><span data-stu-id="a1044-182">Transform existing columns onto new ones with a user-defined mapping</span></span> |
