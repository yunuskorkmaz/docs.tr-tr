---
title: Makine öğrenimi görevleri
description: Farklı makine öğrenimi görevlerini ve ML.NET içinde desteklenen ilişkili görevleri keşfedin.
ms.custom: seodec18
ms.date: 04/23/2019
author: natke
ms.openlocfilehash: ed6361fdcbca11c100ee5cae4ca76e152ddfba11
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063537"
---
# <a name="machine-learning-tasks-in-mlnet"></a><span data-ttu-id="6bdd6-103">ML.NET Machine learning görevleri</span><span class="sxs-lookup"><span data-stu-id="6bdd6-103">Machine learning tasks in ML.NET</span></span>

<span data-ttu-id="6bdd6-104">Bir machine learning modeli oluştururken ilk verilerinizle elde etmek umarak tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-104">When building a machine learning model, you first need to define what you are hoping to achieve with your data.</span></span> <span data-ttu-id="6bdd6-105">Bu görev durumunuza öğrenme doğru makine seçmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-105">This allows you to choose the right machine learning task for your situation.</span></span> <span data-ttu-id="6bdd6-106">Aşağıdaki listede, aralarından seçim yapabileceğiniz görevleri öğrenme farklı makine açıklar ve bazı yaygın kullanım örnekleri.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-106">The following list describes the different machine learning tasks that you can choose from and some common use cases.</span></span>

<span data-ttu-id="6bdd6-107">Senaryonuz için hangi görev çalışır karar verdikten sonra modeli eğitmek için en iyi algoritmayı seçin gerekir.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-107">Once you have decided which task works for your scenario, then you need to choose the best algorithm to train your model.</span></span> <span data-ttu-id="6bdd6-108">Kullanılabilir algoritmalar, her görev için bölümünde listelenir.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-108">The available algorithms are listed in the section for each task.</span></span>

## <a name="binary-classification"></a><span data-ttu-id="6bdd6-109">İkili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="6bdd6-109">Binary classification</span></span>

<span data-ttu-id="6bdd6-110">A [denetimli makine öğrenimi](glossary.md#supervised-machine-learning) veri örneği ait olduğu, iki sınıf (Kategoriler) tahmin etmek için kullanılan görev.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-110">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict which of two classes (categories) an instance of data belongs to.</span></span> <span data-ttu-id="6bdd6-111">Bir sınıflandırma algoritmasıdır girişi etiketli örnekler, her etiket bir tamsayı 0 veya 1 olduğu kümesidir.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-111">The input of a classification algorithm is a set of labeled examples, where each label is an integer of either 0 or 1.</span></span> <span data-ttu-id="6bdd6-112">İkili sınıflandırma algoritmasıdır çıktısındaki yeni etiketlenmemiş örnek sınıfı tahmin etmek için kullanabileceğiniz bir sınıflandırıcı ' dir.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-112">The output of a binary classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="6bdd6-113">İkili sınıflandırma senaryolarına örnekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="6bdd6-113">Examples of binary classification scenarios include:</span></span>

* <span data-ttu-id="6bdd6-114">[Twitter yorumların anlama yaklaşım](../tutorials/sentiment-analysis.md) "pozitif" veya "negatif" olarak.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-114">[Understanding sentiment of Twitter comments](../tutorials/sentiment-analysis.md) as either "positive" or "negative".</span></span>
* <span data-ttu-id="6bdd6-115">Bir hastanın belirli bir Hastalık olup olmadığını tanılama.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-115">Diagnosing whether a patient has a certain disease or not.</span></span>
* <span data-ttu-id="6bdd6-116">"Veya istenmeyen posta olarak" e-posta işaretlemek için bir kararı.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-116">Making a decision to mark an email as "spam" or not.</span></span>
* <span data-ttu-id="6bdd6-117">Fotoğraf köpek ve Meyve içerip içermediğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-117">Determining if a photo contains a dog or fruit.</span></span>

<span data-ttu-id="6bdd6-118">Daha fazla bilgi için [ikili sınıflandırma](https://en.wikipedia.org/wiki/Binary_classification) wikipedia makalesi.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-118">For more information, see the [Binary classification](https://en.wikipedia.org/wiki/Binary_classification) article on Wikipedia.</span></span>

### <a name="binary-classification-trainers"></a><span data-ttu-id="6bdd6-119">İkili sınıflandırma Eğitmenler</span><span class="sxs-lookup"><span data-stu-id="6bdd6-119">Binary classification trainers</span></span>

<span data-ttu-id="6bdd6-120">Aşağıdaki algoritmaları kullanarak bir ikili sınıflandırma modelinde eğitebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6bdd6-120">You can train a binary classification model using the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>
* <xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedBinaryTrainer> 
* <xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer> 
* <xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer> 
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer> 
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer> 
* <xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer> 
* <xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer> 
* <xref:Microsoft.ML.Trainers.PriorTrainer> 
* <xref:Microsoft.ML.Trainers.LinearSvmTrainer>

### <a name="binary-classification-inputs-and-outputs"></a><span data-ttu-id="6bdd6-121">İkili sınıflandırma girişler ve çıkışlar</span><span class="sxs-lookup"><span data-stu-id="6bdd6-121">Binary classification inputs and outputs</span></span>

<span data-ttu-id="6bdd6-122">İkili sınıflandırma ile en iyi sonuçlar için eğitim verileri (yani eşit sayıda pozitif ve negatif eğitim verilerini) dengelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-122">For best results with binary classification, the training data should be balanced (i.e. equal numbers of positive and negative training data).</span></span> <span data-ttu-id="6bdd6-123">Eksik ve değerleri eğitim önce yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-123">Missing and values should be handled before training.</span></span>

<span data-ttu-id="6bdd6-124">Sütun verileri giriş etiket olmalıdır <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-124">The input label column data must be <xref:System.Boolean>.</span></span>
<span data-ttu-id="6bdd6-125">Giriş özellikleri sütun verileri bir sabit boyutlu vektör olmalıdır <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-125">The input features column data must be a fixed-size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="6bdd6-126">Bu Eğitmenler çıkarır aşağıdaki sütunlar:</span><span class="sxs-lookup"><span data-stu-id="6bdd6-126">These trainers outputs the following columns:</span></span>

| <span data-ttu-id="6bdd6-127">Çıkış sütununun adı</span><span class="sxs-lookup"><span data-stu-id="6bdd6-127">Output Column Name</span></span> | <span data-ttu-id="6bdd6-128">Sütun türü</span><span class="sxs-lookup"><span data-stu-id="6bdd6-128">Column Type</span></span> | <span data-ttu-id="6bdd6-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6bdd6-129">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="6bdd6-130">Model tarafından hesaplanan ham puan</span><span class="sxs-lookup"><span data-stu-id="6bdd6-130">The raw score that was calculated by the model</span></span>|
| `PredictedLabel` | <xref:System.Boolean> | <span data-ttu-id="6bdd6-131">Puan oturum açma göre tahmin edilen etiketi.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-131">The predicted label, based on the sign of the score.</span></span> <span data-ttu-id="6bdd6-132">Negatif bir puan eşlendiği `false` ve pozitif bir puan eşlendiği `true`.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-132">A negative score maps to `false` and a positive score maps to `true`.</span></span>|

## <a name="multiclass-classification"></a><span data-ttu-id="6bdd6-133">Sınıflı sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="6bdd6-133">Multiclass classification</span></span>

<span data-ttu-id="6bdd6-134">A [denetimli makine öğrenimi](glossary.md#supervised-machine-learning) veri örneği sınıfı (kategori) tahmin etmek için kullanılan görev.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-134">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the class (category) of an instance of data.</span></span> <span data-ttu-id="6bdd6-135">Bir sınıflandırma algoritmasıdır girişi etiketli örnekleri kümesidir.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-135">The input of a classification algorithm is a set of labeled examples.</span></span> <span data-ttu-id="6bdd6-136">Her etiketin normal metin olarak başlar.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-136">Each label normally starts as text.</span></span> <span data-ttu-id="6bdd6-137">Ardından, anahtarı (sayısal) türüne dönüştürür TermTransform aracılığıyla çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-137">It is then run through the TermTransform, which converts it to the Key (numeric) type.</span></span> <span data-ttu-id="6bdd6-138">Bir sınıflandırma algoritmasıdır çıktısı, yeni etiketlenmemiş örnek sınıfı tahmin etmek için kullanabileceğiniz bir sınıflandırıcı ' dir.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-138">The output of a classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="6bdd6-139">Çok sınıflı sınıflandırma senaryolarına örnekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="6bdd6-139">Examples of multi-class classification scenarios include:</span></span>

* <span data-ttu-id="6bdd6-140">Köpek bir "Siberian Husky", "Altın alıcısı", "şu dar", vb. olarak belirleniyor.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-140">Determining the breed of a dog as a "Siberian Husky", "Golden Retriever", "Poodle", etc.</span></span>
* <span data-ttu-id="6bdd6-141">Film anlama "pozitif", "belirsiz" veya "negatif" incelenir.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-141">Understanding movie reviews as "positive", "neutral", or "negative".</span></span>
* <span data-ttu-id="6bdd6-142">Otel kategorilendirme "Konum", "price", "temizlik", vb. incelenir.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-142">Categorizing hotel reviews as "location", "price", "cleanliness", etc.</span></span>

<span data-ttu-id="6bdd6-143">Daha fazla bilgi için [sınıflı sınıflandırma](https://en.wikipedia.org/wiki/Multiclass_classification) wikipedia makalesi.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-143">For more information, see the [Multiclass classification](https://en.wikipedia.org/wiki/Multiclass_classification) article on Wikipedia.</span></span>

>[!NOTE]
><span data-ttu-id="6bdd6-144">Herhangi bir vs tüm yükseltmeleri [ikili sınıflandırma learner](#binary-classification) çok sınıflı veri kümelerinde yapacak.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-144">One vs all upgrades any [binary classification learner](#binary-classification) to act on multiclass datasets.</span></span> <span data-ttu-id="6bdd6-145">Daha fazla bilgi [Vikipedi] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span><span class="sxs-lookup"><span data-stu-id="6bdd6-145">More information on [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span></span>

### <a name="multiclass-classification-trainers"></a><span data-ttu-id="6bdd6-146">Sınıflı sınıflandırma Eğitmenler</span><span class="sxs-lookup"><span data-stu-id="6bdd6-146">Multiclass classification trainers</span></span>

<span data-ttu-id="6bdd6-147">Aşağıdaki eğitim algoritmalarını kullanarak bir çok sınıflı sınıflandırma modeli eğitmek:</span><span class="sxs-lookup"><span data-stu-id="6bdd6-147">You can train a multiclass classification model using the following training algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer> 
* <xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer> 
* <xref:Microsoft.ML.Trainers.OneVersusAllTrainer>
* <xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer> 

### <a name="multiclass-classification-inputs-and-outputs"></a><span data-ttu-id="6bdd6-148">Sınıflı sınıflandırma girişler ve çıkışlar</span><span class="sxs-lookup"><span data-stu-id="6bdd6-148">Multiclass classification inputs and outputs</span></span>

<span data-ttu-id="6bdd6-149">Sütun verileri giriş etiket olmalıdır [anahtar](xref:Microsoft.ML.Data.KeyDataViewType) türü.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-149">The input label column data must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>
<span data-ttu-id="6bdd6-150">Sabit boyutlu vektörü özellik sütunu olmalıdır <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-150">The feature column must be a fixed size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="6bdd6-151">Bu eğitmen aşağıdaki verir:</span><span class="sxs-lookup"><span data-stu-id="6bdd6-151">This trainer outputs the following:</span></span>

| <span data-ttu-id="6bdd6-152">Çıkış adı</span><span class="sxs-lookup"><span data-stu-id="6bdd6-152">Output Name</span></span> | <span data-ttu-id="6bdd6-153">Tür</span><span class="sxs-lookup"><span data-stu-id="6bdd6-153">Type</span></span> | <span data-ttu-id="6bdd6-154">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6bdd6-154">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="6bdd6-155">Vektörü <xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="6bdd6-155">Vector of <xref:System.Single></span></span> | <span data-ttu-id="6bdd6-156">Tüm sınıflar puanları.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-156">The scores of all classes.</span></span> <span data-ttu-id="6bdd6-157">Daha yüksek değere ilişkili sınıfına denk için daha yüksek olasılık anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-157">Higher value means higher probability to fall into the associated class.</span></span> <span data-ttu-id="6bdd6-158">İ öğedeki en büyük değeri varsa, tahmin edilen etiket dizini i olacaktır.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-158">If the i-th element has the largest value, the predicted label index would be i.</span></span> <span data-ttu-id="6bdd6-159">Sıfır tabanlı dizin i olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-159">Note that i is zero-based index.</span></span> |
| `PredictedLabel` | <span data-ttu-id="6bdd6-160">[anahtar](xref:Microsoft.ML.Data.KeyDataViewType) türü</span><span class="sxs-lookup"><span data-stu-id="6bdd6-160">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="6bdd6-161">Tahmin edilen etiketin dizini.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-161">The predicted label's index.</span></span> <span data-ttu-id="6bdd6-162">Varsa değerini i, gerçek etiket anahtarı değerli giriş etiket türü i. kategorisinde olacaktır.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-162">If its value is i, the actual label would be the i-th category in the key-valued input label type.</span></span> |

## <a name="regression"></a><span data-ttu-id="6bdd6-163">Regresyon</span><span class="sxs-lookup"><span data-stu-id="6bdd6-163">Regression</span></span>

<span data-ttu-id="6bdd6-164">A [denetimli makine öğrenimi](glossary.md#supervised-machine-learning) ilgili özellikleri kümesinden etiketin değeri tahmin etmek için kullanılan görev.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-164">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the value of the label from a set of related features.</span></span> <span data-ttu-id="6bdd6-165">Etiket herhangi bir gerçek değerini olabilir ve sınıflandırma görevleri olduğu gibi değerlerin değil sınırlı ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-165">The label can be of any real value and is not from a finite set of values as in classification tasks.</span></span> <span data-ttu-id="6bdd6-166">Regresyon algoritmaları modeli etiketi özelliklerinin değerleri olarak nasıl değiştireceğini belirlemek için ilgili özellikleri etikette bağımlılığı çeşitli.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-166">Regression algorithms model the dependency of the label on its related features to determine how the label will change as the values of the features are varied.</span></span> <span data-ttu-id="6bdd6-167">Bir regresyon algoritmasıdır girişi bir örnekler etiketlerle bilinen değerler kümesidir.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-167">The input of a regression algorithm is a set of examples with labels of known values.</span></span> <span data-ttu-id="6bdd6-168">Bir regresyon algoritmasıdır çıktısı her yeni özellik kümesi, giriş etiketi değerini tahmin etmek için kullanabileceğiniz bir işlev ise.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-168">The output of a regression algorithm is a function, which you can use to predict the label value for any new set of input features.</span></span> <span data-ttu-id="6bdd6-169">Regresyon senaryolarına örnekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="6bdd6-169">Examples of regression scenarios include:</span></span>

* <span data-ttu-id="6bdd6-170">Ev fiyatları yatak, konum ve boyut sayısı gibi merkezi özniteliklerini temel alarak tahmin etme.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-170">Predicting house prices based on house attributes such as number of bedrooms, location, or size.</span></span>
* <span data-ttu-id="6bdd6-171">Geçmiş verileri ve geçerli pazar eğilimlerine göre gelecekteki hisse senedi fiyatlarını tahmin etme.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-171">Predicting future stock prices based on historical data and current market trends.</span></span>
* <span data-ttu-id="6bdd6-172">Bütçelerini reklam üzerinde temel bir ürün satışları tahmin etme.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-172">Predicting sales of a product based on advertising budgets.</span></span>

### <a name="regression-trainers"></a><span data-ttu-id="6bdd6-173">Regresyon Eğitmenler</span><span class="sxs-lookup"><span data-stu-id="6bdd6-173">Regression trainers</span></span>

<span data-ttu-id="6bdd6-174">Aşağıdaki algoritmaları kullanarak bir regresyon modeli eğitmek:</span><span class="sxs-lookup"><span data-stu-id="6bdd6-174">You can train a regression model using the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>
* <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>
* <xref:Microsoft.ML.Trainers.OlsTrainer>
* <xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer> 
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>

### <a name="regression-inputs-and-outputs"></a><span data-ttu-id="6bdd6-175">Regresyon girişler ve çıkışlar</span><span class="sxs-lookup"><span data-stu-id="6bdd6-175">Regression inputs and outputs</span></span>

<span data-ttu-id="6bdd6-176">Sütun verileri giriş etiket olmalıdır <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-176">The input label column data must be <xref:System.Single>.</span></span>

<span data-ttu-id="6bdd6-177">Bu görev için Eğitmenler aşağıdaki çıkışı:</span><span class="sxs-lookup"><span data-stu-id="6bdd6-177">The trainers for this task output the following:</span></span>

| <span data-ttu-id="6bdd6-178">Çıkış adı</span><span class="sxs-lookup"><span data-stu-id="6bdd6-178">Output Name</span></span> | <span data-ttu-id="6bdd6-179">Tür</span><span class="sxs-lookup"><span data-stu-id="6bdd6-179">Type</span></span> | <span data-ttu-id="6bdd6-180">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6bdd6-180">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="6bdd6-181">Model tarafından tahmin ham puan</span><span class="sxs-lookup"><span data-stu-id="6bdd6-181">The raw score that was predicted by the model</span></span> |

## <a name="clustering"></a><span data-ttu-id="6bdd6-182">Kümeleme</span><span class="sxs-lookup"><span data-stu-id="6bdd6-182">Clustering</span></span>

<span data-ttu-id="6bdd6-183">Bir [Denetimsiz machine learning](glossary.md#unsupervised-machine-learning) benzer özelliklere içeren kümeler halinde veri grubu örnekleri için kullanılan görev.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-183">An [unsupervised machine learning](glossary.md#unsupervised-machine-learning) task that is used to group instances of data into clusters that contain similar characteristics.</span></span> <span data-ttu-id="6bdd6-184">Kümeleme de olmayan mantıksal olarak türettiğiniz DataSet ilişkileri tanımlamak için gözatma veya basit gözlem tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-184">Clustering can also be used to identify relationships in a dataset that you might not logically derive by browsing or simple observation.</span></span> <span data-ttu-id="6bdd6-185">Giriş ve çıkışları kümeleme algoritması, seçilen metodolojiyi üzerinde bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-185">The inputs and outputs of a clustering algorithm depends on the methodology chosen.</span></span> <span data-ttu-id="6bdd6-186">Bir dağıtım, kütle Merkezi, bağlantı veya yoğunluk yaklaşımla alabilir.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-186">You can take a distribution, centroid, connectivity, or density-based approach.</span></span> <span data-ttu-id="6bdd6-187">ML.NET şu anda K-ortalamaları Kümelemesi kullanarak kütle merkezi tabanlı bir yaklaşımı destekler.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-187">ML.NET currently supports a centroid-based approach using K-Means clustering.</span></span> <span data-ttu-id="6bdd6-188">Kümeleme senaryolarına örnekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="6bdd6-188">Examples of clustering scenarios include:</span></span>

* <span data-ttu-id="6bdd6-189">Otel Konukları alışkanlıkları ve Otel seçeneği özelliklere göre parçalarını anlama.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-189">Understanding segments of hotel guests based on habits and characteristics of hotel choices.</span></span>
* <span data-ttu-id="6bdd6-190">Müşteri kesimleri ve demografik bilgilere bağlı hedeflenen reklam kampanyaları oluşturmanıza yardımcı olmak için tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-190">Identifying customer segments and demographics to help build targeted advertising campaigns.</span></span>
* <span data-ttu-id="6bdd6-191">Üretim ölçümleri temel alarak envanteri halinde kategorilere ayrılması.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-191">Categorizing inventory based on manufacturing metrics.</span></span>

### <a name="clustering-trainer"></a><span data-ttu-id="6bdd6-192">Eğitmen kümeleme</span><span class="sxs-lookup"><span data-stu-id="6bdd6-192">Clustering trainer</span></span>

<span data-ttu-id="6bdd6-193">Aşağıdaki algoritması kullanarak bir kümeleme modeli eğitmek:</span><span class="sxs-lookup"><span data-stu-id="6bdd6-193">You can train a clustering model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.KMeansTrainer> 

### <a name="clustering-inputs-and-outputs"></a><span data-ttu-id="6bdd6-194">Giriş ve çıkışları kümeleme</span><span class="sxs-lookup"><span data-stu-id="6bdd6-194">Clustering inputs and outputs</span></span>

<span data-ttu-id="6bdd6-195">Giriş özellikleri veri olmalıdır <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-195">The input features data must be <xref:System.Single>.</span></span> <span data-ttu-id="6bdd6-196">Hiçbir etiket gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-196">No labels are needed.</span></span>

<span data-ttu-id="6bdd6-197">Bu eğitmen aşağıdaki verir:</span><span class="sxs-lookup"><span data-stu-id="6bdd6-197">This trainer outputs the following:</span></span>

| <span data-ttu-id="6bdd6-198">Çıkış adı</span><span class="sxs-lookup"><span data-stu-id="6bdd6-198">Output Name</span></span> | <span data-ttu-id="6bdd6-199">Tür</span><span class="sxs-lookup"><span data-stu-id="6bdd6-199">Type</span></span> | <span data-ttu-id="6bdd6-200">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6bdd6-200">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="6bdd6-201">vektörü <xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="6bdd6-201">vector of <xref:System.Single></span></span> | <span data-ttu-id="6bdd6-202">Tüm kümeler centriods için belirli bir veri noktasının uzaklıkları</span><span class="sxs-lookup"><span data-stu-id="6bdd6-202">The distances of the given data point to all clusters' centriods</span></span> |
| `PredictedLabel` | <span data-ttu-id="6bdd6-203">[anahtar](xref:Microsoft.ML.Data.KeyDataViewType) türü</span><span class="sxs-lookup"><span data-stu-id="6bdd6-203">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="6bdd6-204">Model tarafından tahmin edilen en yakın kümenin dizini.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-204">The closest cluster's index predicted by the model.</span></span> |

## <a name="anomaly-detection"></a><span data-ttu-id="6bdd6-205">Anomali algılama</span><span class="sxs-lookup"><span data-stu-id="6bdd6-205">Anomaly detection</span></span>

<span data-ttu-id="6bdd6-206">Bu görevi, asıl bileşen analiz (PCA) kullanarak bir anomali algılama modeli oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-206">This task creates an anomaly detection model by using Principal Component Analysis (PCA).</span></span> <span data-ttu-id="6bdd6-207">PCA tabanlı Anomali algılama geçerli işlemler gibi bir sınıf eğitim verilerini almak kolay, ancak yeterli örnekleri hedeflenen anomali elde etmek zor olduğu senaryolar modelinde oluşturmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-207">PCA-Based Anomaly Detection helps you build a model in scenarios where it is easy to obtain training data from one class, such as valid transactions, but difficult to obtain sufficient samples of the targeted anomalies.</span></span>

<span data-ttu-id="6bdd6-208">İç yapısını gösterir ve veri varyans açıklar machine learning'de PCA kurulan bir teknik keşif veri analizi sık kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-208">An established technique in machine learning, PCA is frequently used in exploratory data analysis because it reveals the inner structure of the data and explains the variance in the data.</span></span> <span data-ttu-id="6bdd6-209">Birden fazla değişken içeren verileri analiz ederek PCA çalışır.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-209">PCA works by analyzing data that contains multiple variables.</span></span> <span data-ttu-id="6bdd6-210">Bu değişkenler arasındaki bağıntıları arar ve en iyi sonuçlar farklılıkları yakalar değerlerinin birleşimi belirler.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-210">It looks for correlations among the variables and determines the combination of values that best captures differences in outcomes.</span></span> <span data-ttu-id="6bdd6-211">Bu birleşik özellik değerleri, asıl bileşen olarak adlandırılıyordu daha kompakt bir özellik alanı oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-211">These combined feature values are used to create a more compact feature space called the principal components.</span></span>

<span data-ttu-id="6bdd6-212">Anomali algılama machine learning'de birçok önemli görevleri kapsar:</span><span class="sxs-lookup"><span data-stu-id="6bdd6-212">Anomaly detection encompasses many important tasks in machine learning:</span></span>

* <span data-ttu-id="6bdd6-213">Olası sahte işlem tanımlama.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-213">Identifying transactions that are potentially fraudulent.</span></span>
* <span data-ttu-id="6bdd6-214">Ağa yetkisiz erişim oluştu olarak görülebilecek desenler öğrenme.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-214">Learning patterns that indicate that a network intrusion has occurred.</span></span>
* <span data-ttu-id="6bdd6-215">Hastalara anormal kümelerini bulma.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-215">Finding abnormal clusters of patients.</span></span>
* <span data-ttu-id="6bdd6-216">Değer denetimi bir sisteme girdi.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-216">Checking values entered into a system.</span></span>

<span data-ttu-id="6bdd6-217">Anomalileri tanımına göre nadir olayları olduğundan, temsili bir örnek model için kullanılacak veri toplamak zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-217">Because anomalies are rare events by definition, it can be difficult to collect a representative sample of data to use for modeling.</span></span> <span data-ttu-id="6bdd6-218">Bu kategoride bulunan algoritmaları özellikle imbalanced veri kümelerini kullanarak oluşturma ve eğitim modeli çekirdek sorunları gidermek üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-218">The algorithms included in this category have been especially designed to address the core challenges of building and training models by using imbalanced data sets.</span></span>

### <a name="anomaly-detection-trainer"></a><span data-ttu-id="6bdd6-219">Anomali algılama Eğitmen</span><span class="sxs-lookup"><span data-stu-id="6bdd6-219">Anomaly detection trainer</span></span>

<span data-ttu-id="6bdd6-220">Aşağıdaki algoritması kullanarak bir anomali algılama modeli eğitmek:</span><span class="sxs-lookup"><span data-stu-id="6bdd6-220">You can train an anomaly detection model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>

### <a name="anomaly-detection-inputs-and-outputs"></a><span data-ttu-id="6bdd6-221">Anomali algılama giriş ve çıkışları</span><span class="sxs-lookup"><span data-stu-id="6bdd6-221">Anomaly detection inputs and outputs</span></span>

<span data-ttu-id="6bdd6-222">Giriş özellikleri sabit boyutlu bir vektör olmalıdır <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-222">The input features must be a fixed-sized vector of <xref:System.Single>.</span></span>

<span data-ttu-id="6bdd6-223">Bu eğitmen aşağıdaki verir:</span><span class="sxs-lookup"><span data-stu-id="6bdd6-223">This trainer outputs the following:</span></span>

| <span data-ttu-id="6bdd6-224">Çıkış adı</span><span class="sxs-lookup"><span data-stu-id="6bdd6-224">Output Name</span></span> | <span data-ttu-id="6bdd6-225">Tür</span><span class="sxs-lookup"><span data-stu-id="6bdd6-225">Type</span></span> | <span data-ttu-id="6bdd6-226">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6bdd6-226">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="6bdd6-227">Anomali algılama modeli tarafından hesaplanan negatif olmayan, sınırsız puanı</span><span class="sxs-lookup"><span data-stu-id="6bdd6-227">The non-negative, unbounded score that was calculated by the anomaly detection model</span></span> |

## <a name="ranking"></a><span data-ttu-id="6bdd6-228">Derecelendirme</span><span class="sxs-lookup"><span data-stu-id="6bdd6-228">Ranking</span></span>

<span data-ttu-id="6bdd6-229">Derecelendirme görev derecelendiricisini etiketli örnekleri bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-229">A ranking task constructs a ranker from a set of labeled examples.</span></span> <span data-ttu-id="6bdd6-230">Bu örnek kümesi ile puanlanmış örnek grupları oluşan bir tetikleyicisi.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-230">This example set consists of instance groups that can be scored with a given criteria.</span></span> <span data-ttu-id="6bdd6-231">{0, 1, 2, 3, 4} her örneği için olan derecelendirme etiketleri.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-231">The ranking labels are { 0, 1, 2, 3, 4 } for each instance.</span></span>  <span data-ttu-id="6bdd6-232">Derecelendiricisini bilinmeyen puanlarının her örneği için yeni derece örneği gruplara eğitildi.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-232">The ranker is trained to rank new instance groups with unknown scores for each instance.</span></span> <span data-ttu-id="6bdd6-233">ML.NET derecelendirme öğrencileriyle olan [öğrenilen makine derecelendirme](https://en.wikipedia.org/wiki/Learning_to_rank) bağlı.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-233">ML.NET ranking learners are [machine learned ranking](https://en.wikipedia.org/wiki/Learning_to_rank) based.</span></span>

### <a name="ranking-training-algorithms"></a><span data-ttu-id="6bdd6-234">Sıralama eğitim algoritmaları</span><span class="sxs-lookup"><span data-stu-id="6bdd6-234">Ranking training algorithms</span></span>

<span data-ttu-id="6bdd6-235">Aşağıdaki algoritmaları ile bir derecelendirme modeli eğitmek:</span><span class="sxs-lookup"><span data-stu-id="6bdd6-235">You can train a ranking model with the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer> 

### <a name="ranking-input-and-outputs"></a><span data-ttu-id="6bdd6-236">Sıralama giriş ve çıkışları</span><span class="sxs-lookup"><span data-stu-id="6bdd6-236">Ranking input and outputs</span></span>

<span data-ttu-id="6bdd6-237">Giriş etiketi veri türü olmalıdır [anahtarı](xref:Microsoft.ML.Data.KeyDataViewType) türü veya <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-237">The input label data type must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type or <xref:System.Single>.</span></span> <span data-ttu-id="6bdd6-238">Etiketin değeri, ilgi düzeyi yüksek değerler daha yüksek bir ilgi yeri belirtmek, belirler.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-238">The value of the label determines relevance, where higher values indicate higher relevance.</span></span> <span data-ttu-id="6bdd6-239">Etiket ise bir [anahtar](xref:Microsoft.ML.Data.KeyDataViewType) küçük dizini az ilgili olduğu anahtar dizini ilgi düzeyi değeri ise yazın.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-239">If the label is a [key](xref:Microsoft.ML.Data.KeyDataViewType) type, then the key index is the relevance value, where the smallest index is the least relevant.</span></span> <span data-ttu-id="6bdd6-240">Etiket ise bir <xref:System.Single>, daha yüksek bir ilgi düzeyi daha büyük değerler belirtin.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-240">If the label is a <xref:System.Single>, larger values indicate higher relevance.</span></span>

<span data-ttu-id="6bdd6-241">Özellik verileri bir sabit boyutlu vektör olmalıdır <xref:System.Single> ve Grup sütunu giriş satır olmalıdır [anahtar](xref:Microsoft.ML.Data.KeyDataViewType) türü.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-241">The feature data must be a fixed size vector of <xref:System.Single> and input row group column must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>

<span data-ttu-id="6bdd6-242">Bu eğitmen aşağıdaki verir:</span><span class="sxs-lookup"><span data-stu-id="6bdd6-242">This trainer outputs the following:</span></span>

| <span data-ttu-id="6bdd6-243">Çıkış adı</span><span class="sxs-lookup"><span data-stu-id="6bdd6-243">Output Name</span></span> | <span data-ttu-id="6bdd6-244">Tür</span><span class="sxs-lookup"><span data-stu-id="6bdd6-244">Type</span></span> | <span data-ttu-id="6bdd6-245">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6bdd6-245">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="6bdd6-246">Tahmin belirlemek için model tarafından hesaplanan sınırsız puanı</span><span class="sxs-lookup"><span data-stu-id="6bdd6-246">The unbounded score that was calculated by the model to determine the prediction</span></span> |

## <a name="recommendation"></a><span data-ttu-id="6bdd6-247">Öneri</span><span class="sxs-lookup"><span data-stu-id="6bdd6-247">Recommendation</span></span>

<span data-ttu-id="6bdd6-248">Bir öneri görevi önerilen ürünleri veya hizmetleri listesi oluşturmayı etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-248">A recommendation task enables producing a list of recommended products or services.</span></span> <span data-ttu-id="6bdd6-249">ML.NET kullanan [matris factorization (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), [işbirliğine dayalı filtreleme](https://en.wikipedia.org/wiki/Collaborative_filtering) geçmiş ürün derecelendirmesi veri Kataloğu'nda varsa önerileri için algoritma.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-249">ML.NET uses [Matrix factorization (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), a [collaborative filtering](https://en.wikipedia.org/wiki/Collaborative_filtering) algorithm for recommendations when you have historical product rating data in your catalog.</span></span> <span data-ttu-id="6bdd6-250">Örneğin, kullanıcılarınız için geçmiş film derecelendirmesi verilere sahip ve sonraki izleyin okunduğunun diğer filmler önermek istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="6bdd6-250">For example, you have historical movie rating data for your users and want to recommend  other movies they are likely to watch next.</span></span>

### <a name="recommendation-training-algorithms"></a><span data-ttu-id="6bdd6-251">Öneri eğitim algoritmaları</span><span class="sxs-lookup"><span data-stu-id="6bdd6-251">Recommendation training algorithms</span></span>

<span data-ttu-id="6bdd6-252">Aşağıdaki algoritması ile bir öneri modeli eğitmek:</span><span class="sxs-lookup"><span data-stu-id="6bdd6-252">You can train a recommendation model with the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>
