---
title: Makine öğrenimi görevleri
description: ML.NET sürümünde desteklenen farklı makine öğrenimi görevlerini ve ilişkili görevleri keşfedebilirsiniz.
ms.custom: seodec18
ms.date: 04/23/2019
author: natke
ms.openlocfilehash: bcd967c11156ca9b837631560e78722b13fc7ae0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630055"
---
# <a name="machine-learning-tasks-in-mlnet"></a><span data-ttu-id="f594a-103">ML.NET 'de makine öğrenimi görevleri</span><span class="sxs-lookup"><span data-stu-id="f594a-103">Machine learning tasks in ML.NET</span></span>

<span data-ttu-id="f594a-104">Bir makine öğrenimi modeli oluştururken, öncelikle verilerinize ulaşmak için ne kadar atlama yapabileceğinizi tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f594a-104">When building a machine learning model, you first need to define what you are hoping to achieve with your data.</span></span> <span data-ttu-id="f594a-105">Bu, durumunuz için doğru makine öğrenimi görevini seçmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f594a-105">This allows you to choose the right machine learning task for your situation.</span></span> <span data-ttu-id="f594a-106">Aşağıdaki listede, aralarından seçim yapabileceğiniz farklı makine öğrenimi görevleri ve bazı yaygın kullanım durumları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f594a-106">The following list describes the different machine learning tasks that you can choose from and some common use cases.</span></span>

<span data-ttu-id="f594a-107">Senaryolarınız için hangi görevin çalıştığına karar verdikten sonra, modelinize eğitebilmeniz için en iyi algoritmayı seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f594a-107">Once you have decided which task works for your scenario, then you need to choose the best algorithm to train your model.</span></span> <span data-ttu-id="f594a-108">Kullanılabilir algoritmalar her görevin bölümünde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="f594a-108">The available algorithms are listed in the section for each task.</span></span>

## <a name="binary-classification"></a><span data-ttu-id="f594a-109">İkili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="f594a-109">Binary classification</span></span>

<span data-ttu-id="f594a-110">İki sınıftan (kategori) hangisinin ait olduğunu tahmin etmek için kullanılan [denetimli bir makine öğrenimi](glossary.md#supervised-machine-learning) görevi.</span><span class="sxs-lookup"><span data-stu-id="f594a-110">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict which of two classes (categories) an instance of data belongs to.</span></span> <span data-ttu-id="f594a-111">Sınıflandırma algoritmasının girişi, her etiketin 0 veya 1 tamsayısı olduğu etiketli örnekler kümesidir.</span><span class="sxs-lookup"><span data-stu-id="f594a-111">The input of a classification algorithm is a set of labeled examples, where each label is an integer of either 0 or 1.</span></span> <span data-ttu-id="f594a-112">İkili sınıflandırma algoritmasının çıktısı, yeni etiketlenmiş olmayan örneklerin sınıfını tahmin etmek için kullanabileceğiniz bir sınıflandırıcıdır.</span><span class="sxs-lookup"><span data-stu-id="f594a-112">The output of a binary classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="f594a-113">İkili sınıflandırma senaryolarına örnek olarak şunlar verilebilir:</span><span class="sxs-lookup"><span data-stu-id="f594a-113">Examples of binary classification scenarios include:</span></span>

* <span data-ttu-id="f594a-114">[Twitter açıklamalarının](../tutorials/sentiment-analysis.md) yaklaşımını "pozitif" veya "negatif" olarak anlama.</span><span class="sxs-lookup"><span data-stu-id="f594a-114">[Understanding sentiment of Twitter comments](../tutorials/sentiment-analysis.md) as either "positive" or "negative".</span></span>
* <span data-ttu-id="f594a-115">Hasta 'in belirli bir sapmasına sahip olup olmadığını tanılama.</span><span class="sxs-lookup"><span data-stu-id="f594a-115">Diagnosing whether a patient has a certain disease or not.</span></span>
* <span data-ttu-id="f594a-116">E-postayı "istenmeyen posta" olarak işaretlemek için bir karar verme.</span><span class="sxs-lookup"><span data-stu-id="f594a-116">Making a decision to mark an email as "spam" or not.</span></span>
* <span data-ttu-id="f594a-117">Fotoğrafın bir köpek mi yoksa meyve mi içerdiğini belirleme.</span><span class="sxs-lookup"><span data-stu-id="f594a-117">Determining if a photo contains a dog or fruit.</span></span>

<span data-ttu-id="f594a-118">Daha fazla bilgi için Vikipde bulunan [ikili sınıflandırma](https://en.wikipedia.org/wiki/Binary_classification) makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="f594a-118">For more information, see the [Binary classification](https://en.wikipedia.org/wiki/Binary_classification) article on Wikipedia.</span></span>

### <a name="binary-classification-trainers"></a><span data-ttu-id="f594a-119">İkili sınıflandırma traiciler</span><span class="sxs-lookup"><span data-stu-id="f594a-119">Binary classification trainers</span></span>

<span data-ttu-id="f594a-120">Aşağıdaki algoritmaları kullanarak bir ikili sınıflandırma modeli eğitebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f594a-120">You can train a binary classification model using the following algorithms:</span></span>

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

### <a name="binary-classification-inputs-and-outputs"></a><span data-ttu-id="f594a-121">İkili sınıflandırma girişleri ve çıkışları</span><span class="sxs-lookup"><span data-stu-id="f594a-121">Binary classification inputs and outputs</span></span>

<span data-ttu-id="f594a-122">İkili sınıflandırmayla en iyi sonuçları elde etmek için eğitim verilerinin dengelenmesi gerekir (yani, pozitif ve negatif eğitim verilerinin eşit sayısı).</span><span class="sxs-lookup"><span data-stu-id="f594a-122">For best results with binary classification, the training data should be balanced (that is, equal numbers of positive and negative training data).</span></span> <span data-ttu-id="f594a-123">Eksik değerler, eğitimin önüne alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f594a-123">Missing values should be handled before training.</span></span>

<span data-ttu-id="f594a-124">Giriş etiketi sütun verileri <xref:System.Boolean>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f594a-124">The input label column data must be <xref:System.Boolean>.</span></span>
<span data-ttu-id="f594a-125">Giriş özellikleri sütun verileri sabit boyutlu bir vektör <xref:System.Single>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f594a-125">The input features column data must be a fixed-size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="f594a-126">Bu traipler aşağıdaki sütunları çıktı:</span><span class="sxs-lookup"><span data-stu-id="f594a-126">These trainers outputs the following columns:</span></span>

| <span data-ttu-id="f594a-127">Çıkış sütunu adı</span><span class="sxs-lookup"><span data-stu-id="f594a-127">Output Column Name</span></span> | <span data-ttu-id="f594a-128">Sütun türü</span><span class="sxs-lookup"><span data-stu-id="f594a-128">Column Type</span></span> | <span data-ttu-id="f594a-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f594a-129">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="f594a-130">Model tarafından hesaplanan ham puan</span><span class="sxs-lookup"><span data-stu-id="f594a-130">The raw score that was calculated by the model</span></span>|
| `PredictedLabel` | <xref:System.Boolean> | <span data-ttu-id="f594a-131">Puanınızın işaretine göre öngörülen etiket.</span><span class="sxs-lookup"><span data-stu-id="f594a-131">The predicted label, based on the sign of the score.</span></span> <span data-ttu-id="f594a-132">Negatif puan ile eşlenir `false` ve bir pozitif puan ile `true`eşlenir.</span><span class="sxs-lookup"><span data-stu-id="f594a-132">A negative score maps to `false` and a positive score maps to `true`.</span></span>|

## <a name="multiclass-classification"></a><span data-ttu-id="f594a-133">Birden çok Lass sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="f594a-133">Multiclass classification</span></span>

<span data-ttu-id="f594a-134">Bir veri örneğinin sınıfını (kategori) tahmin etmek için kullanılan [denetimli bir makine öğrenimi](glossary.md#supervised-machine-learning) görevi.</span><span class="sxs-lookup"><span data-stu-id="f594a-134">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the class (category) of an instance of data.</span></span> <span data-ttu-id="f594a-135">Sınıflandırma algoritmasının girişi, etiketlenmiş bir örnek kümesidir.</span><span class="sxs-lookup"><span data-stu-id="f594a-135">The input of a classification algorithm is a set of labeled examples.</span></span> <span data-ttu-id="f594a-136">Her etiket normalde metin olarak başlar.</span><span class="sxs-lookup"><span data-stu-id="f594a-136">Each label normally starts as text.</span></span> <span data-ttu-id="f594a-137">Daha sonra TermTransform aracılığıyla çalıştırılır. Bu, anahtar (sayısal) türüne dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="f594a-137">It is then run through the TermTransform, which converts it to the Key (numeric) type.</span></span> <span data-ttu-id="f594a-138">Bir sınıflandırma algoritmasının çıktısı, yeni etiketlenmiş olmayan örneklerin sınıfını tahmin etmek için kullanabileceğiniz bir sınıflandırıcıdır.</span><span class="sxs-lookup"><span data-stu-id="f594a-138">The output of a classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="f594a-139">Çok sınıflı sınıflandırma senaryolarına örnek olarak şunlar verilebilir:</span><span class="sxs-lookup"><span data-stu-id="f594a-139">Examples of multi-class classification scenarios include:</span></span>

* <span data-ttu-id="f594a-140">Bir köpek "Sıberian Husky", "altın Retriever", "Pookıl" vb. olarak belirlenir.</span><span class="sxs-lookup"><span data-stu-id="f594a-140">Determining the breed of a dog as a "Siberian Husky", "Golden Retriever", "Poodle", etc.</span></span>
* <span data-ttu-id="f594a-141">Film incelemelerini "pozitif", "nötr" veya "negatif" olarak anlama.</span><span class="sxs-lookup"><span data-stu-id="f594a-141">Understanding movie reviews as "positive", "neutral", or "negative".</span></span>
* <span data-ttu-id="f594a-142">Otel incelemelerini "konum", "Price", "cleanliness" vb. olarak kategorilere ayırma.</span><span class="sxs-lookup"><span data-stu-id="f594a-142">Categorizing hotel reviews as "location", "price", "cleanliness", etc.</span></span>

<span data-ttu-id="f594a-143">Daha fazla bilgi için Vikipde bulunan [birden çok sınıf sınıflandırması](https://en.wikipedia.org/wiki/Multiclass_classification) makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="f594a-143">For more information, see the [Multiclass classification](https://en.wikipedia.org/wiki/Multiclass_classification) article on Wikipedia.</span></span>

>[!NOTE]
><span data-ttu-id="f594a-144">Bunlardan biri, birden çok Lass veri kümesi üzerinde işlem yapmak için herhangi bir [ikili sınıflandırmanın yükseltimidir](#binary-classification) .</span><span class="sxs-lookup"><span data-stu-id="f594a-144">One vs all upgrades any [binary classification learner](#binary-classification) to act on multiclass datasets.</span></span> <span data-ttu-id="f594a-145">[Vikipedi] hakkında daha https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest) fazla bilgi (.</span><span class="sxs-lookup"><span data-stu-id="f594a-145">More information on [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span></span>

### <a name="multiclass-classification-trainers"></a><span data-ttu-id="f594a-146">Birden çok Lass sınıflandırma traipleyiciler</span><span class="sxs-lookup"><span data-stu-id="f594a-146">Multiclass classification trainers</span></span>

<span data-ttu-id="f594a-147">Aşağıdaki eğitim algoritmalarını kullanarak çok bir Lass sınıflandırma modelini eğitebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f594a-147">You can train a multiclass classification model using the following training algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer> 
* <xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer> 
* <xref:Microsoft.ML.Trainers.OneVersusAllTrainer>
* <xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer> 

### <a name="multiclass-classification-inputs-and-outputs"></a><span data-ttu-id="f594a-148">Birden çok Lass sınıflandırma girişleri ve çıkışları</span><span class="sxs-lookup"><span data-stu-id="f594a-148">Multiclass classification inputs and outputs</span></span>

<span data-ttu-id="f594a-149">Giriş etiketi sütun verileri, [anahtar](xref:Microsoft.ML.Data.KeyDataViewType) türünde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f594a-149">The input label column data must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>
<span data-ttu-id="f594a-150">Özellik sütunu sabit boyutlu bir vektör <xref:System.Single>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f594a-150">The feature column must be a fixed size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="f594a-151">Bu, aşağıdaki çıkışları verir:</span><span class="sxs-lookup"><span data-stu-id="f594a-151">This trainer outputs the following:</span></span>

| <span data-ttu-id="f594a-152">Çıkış adı</span><span class="sxs-lookup"><span data-stu-id="f594a-152">Output Name</span></span> | <span data-ttu-id="f594a-153">Tür</span><span class="sxs-lookup"><span data-stu-id="f594a-153">Type</span></span> | <span data-ttu-id="f594a-154">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f594a-154">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="f594a-155">Vektör<xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="f594a-155">Vector of <xref:System.Single></span></span> | <span data-ttu-id="f594a-156">Tüm sınıfların puanları.</span><span class="sxs-lookup"><span data-stu-id="f594a-156">The scores of all classes.</span></span> <span data-ttu-id="f594a-157">Daha yüksek değer, ilişkili sınıfa düşecek daha büyük olasılık anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f594a-157">Higher value means higher probability to fall into the associated class.</span></span> <span data-ttu-id="f594a-158">İ-th öğesi en büyük değere sahipse, tahmin edilen etiket dizini i olur.</span><span class="sxs-lookup"><span data-stu-id="f594a-158">If the i-th element has the largest value, the predicted label index would be i.</span></span> <span data-ttu-id="f594a-159">Sıfır tabanlı dizin olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f594a-159">Note that i is zero-based index.</span></span> |
| `PredictedLabel` | <span data-ttu-id="f594a-160">[anahtar](xref:Microsoft.ML.Data.KeyDataViewType) türü</span><span class="sxs-lookup"><span data-stu-id="f594a-160">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="f594a-161">Tahmin edilen etiketin dizini.</span><span class="sxs-lookup"><span data-stu-id="f594a-161">The predicted label's index.</span></span> <span data-ttu-id="f594a-162">Değeri i ise, gerçek etiket anahtar değerli giriş etiketi türündeki ı-TH kategorisi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="f594a-162">If its value is i, the actual label would be the i-th category in the key-valued input label type.</span></span> |

## <a name="regression"></a><span data-ttu-id="f594a-163">Regresyon</span><span class="sxs-lookup"><span data-stu-id="f594a-163">Regression</span></span>

<span data-ttu-id="f594a-164">Bir ilişkili özellikler kümesinden etiketin değerini tahmin etmek için kullanılan [denetimli bir makine öğrenimi](glossary.md#supervised-machine-learning) görevi.</span><span class="sxs-lookup"><span data-stu-id="f594a-164">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the value of the label from a set of related features.</span></span> <span data-ttu-id="f594a-165">Etiket herhangi bir gerçek değer olabilir ve sınıflandırma görevlerinde olduğu gibi sınırlı bir değer kümesinden değildir.</span><span class="sxs-lookup"><span data-stu-id="f594a-165">The label can be of any real value and is not from a finite set of values as in classification tasks.</span></span> <span data-ttu-id="f594a-166">Regresyon algoritmaları, özelliğin değerleri farklılaştırılmadıkça etiketin nasıl değiştirileceğini anlamak için ilgili özellikler üzerindeki etiketin bağımlılığını modelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="f594a-166">Regression algorithms model the dependency of the label on its related features to determine how the label will change as the values of the features are varied.</span></span> <span data-ttu-id="f594a-167">Regresyon algoritmasının girişi, bilinen değerlerin etiketlerine sahip bir örnek kümesidir.</span><span class="sxs-lookup"><span data-stu-id="f594a-167">The input of a regression algorithm is a set of examples with labels of known values.</span></span> <span data-ttu-id="f594a-168">Regresyon algoritmasının çıktısı, herhangi bir yeni giriş özellikleri kümesi için etiket değerini tahmin etmek üzere kullanabileceğiniz bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="f594a-168">The output of a regression algorithm is a function, which you can use to predict the label value for any new set of input features.</span></span> <span data-ttu-id="f594a-169">Regresyon senaryolarına örnek olarak şunlar verilebilir:</span><span class="sxs-lookup"><span data-stu-id="f594a-169">Examples of regression scenarios include:</span></span>

* <span data-ttu-id="f594a-170">Yatak odası, konum veya boyut gibi ev özniteliklerini temel alan ev fiyatlarını tahmin etme.</span><span class="sxs-lookup"><span data-stu-id="f594a-170">Predicting house prices based on house attributes such as number of bedrooms, location, or size.</span></span>
* <span data-ttu-id="f594a-171">Geçmiş verileri ve geçerli pazar eğilimlerini temel alarak gelecekteki stok fiyatlarını tahmin etme.</span><span class="sxs-lookup"><span data-stu-id="f594a-171">Predicting future stock prices based on historical data and current market trends.</span></span>
* <span data-ttu-id="f594a-172">Tanıtım bütçeleri temelinde bir ürünün satışlarını tahmin etme.</span><span class="sxs-lookup"><span data-stu-id="f594a-172">Predicting sales of a product based on advertising budgets.</span></span>

### <a name="regression-trainers"></a><span data-ttu-id="f594a-173">Gerileme tracılar</span><span class="sxs-lookup"><span data-stu-id="f594a-173">Regression trainers</span></span>

<span data-ttu-id="f594a-174">Aşağıdaki algoritmaları kullanarak bir regresyon modeli eğitebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f594a-174">You can train a regression model using the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>
* <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>
* <xref:Microsoft.ML.Trainers.OlsTrainer>
* <xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer> 
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>

### <a name="regression-inputs-and-outputs"></a><span data-ttu-id="f594a-175">Regresyon girişleri ve çıktılar</span><span class="sxs-lookup"><span data-stu-id="f594a-175">Regression inputs and outputs</span></span>

<span data-ttu-id="f594a-176">Giriş etiketi sütun verileri <xref:System.Single>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f594a-176">The input label column data must be <xref:System.Single>.</span></span>

<span data-ttu-id="f594a-177">Bu görev için şu kadar traipler aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f594a-177">The trainers for this task output the following:</span></span>

| <span data-ttu-id="f594a-178">Çıkış adı</span><span class="sxs-lookup"><span data-stu-id="f594a-178">Output Name</span></span> | <span data-ttu-id="f594a-179">Tür</span><span class="sxs-lookup"><span data-stu-id="f594a-179">Type</span></span> | <span data-ttu-id="f594a-180">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f594a-180">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="f594a-181">Model tarafından tahmin edilen ham puan</span><span class="sxs-lookup"><span data-stu-id="f594a-181">The raw score that was predicted by the model</span></span> |

## <a name="clustering"></a><span data-ttu-id="f594a-182">Lenmesi</span><span class="sxs-lookup"><span data-stu-id="f594a-182">Clustering</span></span>

<span data-ttu-id="f594a-183">Benzer özellikler içeren kümelere veri örneklerini gruplamak için kullanılan, denetimli bir [makine öğrenimi](glossary.md#unsupervised-machine-learning) görevi.</span><span class="sxs-lookup"><span data-stu-id="f594a-183">An [unsupervised machine learning](glossary.md#unsupervised-machine-learning) task that is used to group instances of data into clusters that contain similar characteristics.</span></span> <span data-ttu-id="f594a-184">Kümeleme, göz atma veya basit gözlemlemeye göre mantıksal olarak türeteceğiniz bir veri kümesindeki ilişkileri tanımlamak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f594a-184">Clustering can also be used to identify relationships in a dataset that you might not logically derive by browsing or simple observation.</span></span> <span data-ttu-id="f594a-185">Bir kümeleme algoritmasının giriş ve çıkışları, seçilen metodolojiye bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="f594a-185">The inputs and outputs of a clustering algorithm depends on the methodology chosen.</span></span> <span data-ttu-id="f594a-186">Dağıtım, centroıd, bağlantı veya Yoğunluk tabanlı yaklaşıma sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f594a-186">You can take a distribution, centroid, connectivity, or density-based approach.</span></span> <span data-ttu-id="f594a-187">ML.NET şu anda K-anlamı Kümelemesi kullanarak centroıd tabanlı bir yaklaşımı desteklemektedir.</span><span class="sxs-lookup"><span data-stu-id="f594a-187">ML.NET currently supports a centroid-based approach using K-Means clustering.</span></span> <span data-ttu-id="f594a-188">Kümeleme senaryolarına örnekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f594a-188">Examples of clustering scenarios include:</span></span>

* <span data-ttu-id="f594a-189">Otel seçeneklerinin alışkanlıklarını ve özelliklerini temel alarak otel konuklarının segmentlerini anlama.</span><span class="sxs-lookup"><span data-stu-id="f594a-189">Understanding segments of hotel guests based on habits and characteristics of hotel choices.</span></span>
* <span data-ttu-id="f594a-190">Hedeflenen reklam kampanyaları oluşturmaya yardımcı olmak için müşteri segmentlerini ve demografik tanımlama.</span><span class="sxs-lookup"><span data-stu-id="f594a-190">Identifying customer segments and demographics to help build targeted advertising campaigns.</span></span>
* <span data-ttu-id="f594a-191">Stoku üretim ölçümlerine göre kategorilere ayırma.</span><span class="sxs-lookup"><span data-stu-id="f594a-191">Categorizing inventory based on manufacturing metrics.</span></span>

### <a name="clustering-trainer"></a><span data-ttu-id="f594a-192">Kümeleme eğitmen</span><span class="sxs-lookup"><span data-stu-id="f594a-192">Clustering trainer</span></span>

<span data-ttu-id="f594a-193">Aşağıdaki algoritmayı kullanarak bir kümeleme modeli eğitebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f594a-193">You can train a clustering model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.KMeansTrainer> 

### <a name="clustering-inputs-and-outputs"></a><span data-ttu-id="f594a-194">Kümeleme girişleri ve çıkışları</span><span class="sxs-lookup"><span data-stu-id="f594a-194">Clustering inputs and outputs</span></span>

<span data-ttu-id="f594a-195">Giriş özellikleri verileri olmalıdır <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="f594a-195">The input features data must be <xref:System.Single>.</span></span> <span data-ttu-id="f594a-196">Etiket gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="f594a-196">No labels are needed.</span></span>

<span data-ttu-id="f594a-197">Bu, aşağıdaki çıkışları verir:</span><span class="sxs-lookup"><span data-stu-id="f594a-197">This trainer outputs the following:</span></span>

| <span data-ttu-id="f594a-198">Çıkış adı</span><span class="sxs-lookup"><span data-stu-id="f594a-198">Output Name</span></span> | <span data-ttu-id="f594a-199">Tür</span><span class="sxs-lookup"><span data-stu-id="f594a-199">Type</span></span> | <span data-ttu-id="f594a-200">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f594a-200">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="f594a-201">vektör<xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="f594a-201">vector of <xref:System.Single></span></span> | <span data-ttu-id="f594a-202">Verilen veri noktasının tüm kümelerdeki mesafeler ' centriods</span><span class="sxs-lookup"><span data-stu-id="f594a-202">The distances of the given data point to all clusters' centriods</span></span> |
| `PredictedLabel` | <span data-ttu-id="f594a-203">[anahtar](xref:Microsoft.ML.Data.KeyDataViewType) türü</span><span class="sxs-lookup"><span data-stu-id="f594a-203">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="f594a-204">Model tarafından tahmin edilen en yakın küme dizini.</span><span class="sxs-lookup"><span data-stu-id="f594a-204">The closest cluster's index predicted by the model.</span></span> |

## <a name="anomaly-detection"></a><span data-ttu-id="f594a-205">Anomali algılama</span><span class="sxs-lookup"><span data-stu-id="f594a-205">Anomaly detection</span></span>

<span data-ttu-id="f594a-206">Bu görev, sorumlu bileşen analizi (PCA) kullanarak bir anomali algılama modeli oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f594a-206">This task creates an anomaly detection model by using Principal Component Analysis (PCA).</span></span> <span data-ttu-id="f594a-207">PCA tabanlı anomali algılama, geçerli işlemler gibi bir sınıftan eğitim verileri elde etmek, ancak hedeflenen bozukluklar için yeterli örnek elde etmek zor olan senaryolarda bir model oluşturmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="f594a-207">PCA-Based Anomaly Detection helps you build a model in scenarios where it is easy to obtain training data from one class, such as valid transactions, but difficult to obtain sufficient samples of the targeted anomalies.</span></span>

<span data-ttu-id="f594a-208">Machine Learning 'de sağlanan bir teknik, PCA verilerin iç yapısını açığa çıkardığından ve verilerdeki varyansı bildirdiği için araştırmacı veri analizinde sıklıkla kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f594a-208">An established technique in machine learning, PCA is frequently used in exploratory data analysis because it reveals the inner structure of the data and explains the variance in the data.</span></span> <span data-ttu-id="f594a-209">PCA birden çok değişken içeren verileri analiz ederek işe yarar.</span><span class="sxs-lookup"><span data-stu-id="f594a-209">PCA works by analyzing data that contains multiple variables.</span></span> <span data-ttu-id="f594a-210">Değişkenler arasında bağıntılar arar ve sonuçların farklarını en iyi şekilde yakalayan değerlerin birleşimini belirler.</span><span class="sxs-lookup"><span data-stu-id="f594a-210">It looks for correlations among the variables and determines the combination of values that best captures differences in outcomes.</span></span> <span data-ttu-id="f594a-211">Bu Birleşik özellik değerleri, sorumlu bileşenleri olarak adlandırılan daha kompakt bir özellik alanı oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f594a-211">These combined feature values are used to create a more compact feature space called the principal components.</span></span>

<span data-ttu-id="f594a-212">Anomali algılama, Machine Learning 'de birçok önemli görevi kapsar:</span><span class="sxs-lookup"><span data-stu-id="f594a-212">Anomaly detection encompasses many important tasks in machine learning:</span></span>

* <span data-ttu-id="f594a-213">Potansiyel olarak sahte olan işlemleri tanımlama.</span><span class="sxs-lookup"><span data-stu-id="f594a-213">Identifying transactions that are potentially fraudulent.</span></span>
* <span data-ttu-id="f594a-214">Ağ üzerinden izinsiz giriş gerçekleştiğini gösteren öğrenme desenleri.</span><span class="sxs-lookup"><span data-stu-id="f594a-214">Learning patterns that indicate that a network intrusion has occurred.</span></span>
* <span data-ttu-id="f594a-215">Anormal bir hastaların kümelerini bulma.</span><span class="sxs-lookup"><span data-stu-id="f594a-215">Finding abnormal clusters of patients.</span></span>
* <span data-ttu-id="f594a-216">Sisteme girilen değerler denetleniyor.</span><span class="sxs-lookup"><span data-stu-id="f594a-216">Checking values entered into a system.</span></span>

<span data-ttu-id="f594a-217">Anomali, tanıma göre nadir olaylar olduğundan, modelleme için kullanılacak verilerin temsili bir örneğini toplamak zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="f594a-217">Because anomalies are rare events by definition, it can be difficult to collect a representative sample of data to use for modeling.</span></span> <span data-ttu-id="f594a-218">Bu kategoriye dahil edilen algoritmalar, özellikle de imdendengelenmiş veri kümeleri kullanılarak modeller oluşturma ve eğitim konusunda temel zorlukları karşılamak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f594a-218">The algorithms included in this category have been especially designed to address the core challenges of building and training models by using imbalanced data sets.</span></span>

### <a name="anomaly-detection-trainer"></a><span data-ttu-id="f594a-219">Anomali algılama</span><span class="sxs-lookup"><span data-stu-id="f594a-219">Anomaly detection trainer</span></span>

<span data-ttu-id="f594a-220">Aşağıdaki algoritmayı kullanarak bir anomali algılama modeli eğitebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f594a-220">You can train an anomaly detection model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>

### <a name="anomaly-detection-inputs-and-outputs"></a><span data-ttu-id="f594a-221">Anomali algılama girişleri ve çıkışları</span><span class="sxs-lookup"><span data-stu-id="f594a-221">Anomaly detection inputs and outputs</span></span>

<span data-ttu-id="f594a-222">Giriş özellikleri sabit boyutlu bir vektör <xref:System.Single>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f594a-222">The input features must be a fixed-sized vector of <xref:System.Single>.</span></span>

<span data-ttu-id="f594a-223">Bu, aşağıdaki çıkışları verir:</span><span class="sxs-lookup"><span data-stu-id="f594a-223">This trainer outputs the following:</span></span>

| <span data-ttu-id="f594a-224">Çıkış adı</span><span class="sxs-lookup"><span data-stu-id="f594a-224">Output Name</span></span> | <span data-ttu-id="f594a-225">Tür</span><span class="sxs-lookup"><span data-stu-id="f594a-225">Type</span></span> | <span data-ttu-id="f594a-226">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f594a-226">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="f594a-227">Anomali algılama modeli tarafından hesaplanan negatif olmayan, sınırlandırılmamış puan</span><span class="sxs-lookup"><span data-stu-id="f594a-227">The non-negative, unbounded score that was calculated by the anomaly detection model</span></span> |

## <a name="ranking"></a><span data-ttu-id="f594a-228">Sıralamasına</span><span class="sxs-lookup"><span data-stu-id="f594a-228">Ranking</span></span>

<span data-ttu-id="f594a-229">Bir derecelendirme görevi bir etiketli örnekler kümesinden derecelendiricisini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f594a-229">A ranking task constructs a ranker from a set of labeled examples.</span></span> <span data-ttu-id="f594a-230">Bu örnek küme, verilen ölçütlerle puanlanbir örnek gruplarından oluşur.</span><span class="sxs-lookup"><span data-stu-id="f594a-230">This example set consists of instance groups that can be scored with a given criteria.</span></span> <span data-ttu-id="f594a-231">Sıralama etiketleri her örnek için {0, 1, 2, 3, 4}.</span><span class="sxs-lookup"><span data-stu-id="f594a-231">The ranking labels are { 0, 1, 2, 3, 4 } for each instance.</span></span>  <span data-ttu-id="f594a-232">Derecelendiricisini, her örnek için bilinmeyen puanları olan yeni örnek gruplarını derecelendirmek için eğitim sağlar.</span><span class="sxs-lookup"><span data-stu-id="f594a-232">The ranker is trained to rank new instance groups with unknown scores for each instance.</span></span> <span data-ttu-id="f594a-233">ML.NET derecelendirmesi öğrenenler, [makine tarafından öğrenilen sıralama](https://en.wikipedia.org/wiki/Learning_to_rank) tabanlıdır.</span><span class="sxs-lookup"><span data-stu-id="f594a-233">ML.NET ranking learners are [machine learned ranking](https://en.wikipedia.org/wiki/Learning_to_rank) based.</span></span>

### <a name="ranking-training-algorithms"></a><span data-ttu-id="f594a-234">Derecelendirme eğitimi algoritmaları</span><span class="sxs-lookup"><span data-stu-id="f594a-234">Ranking training algorithms</span></span>

<span data-ttu-id="f594a-235">Aşağıdaki algoritmalarla bir derecelendirme modeli eğitebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f594a-235">You can train a ranking model with the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer> 

### <a name="ranking-input-and-outputs"></a><span data-ttu-id="f594a-236">Sıralama girişi ve çıkışları</span><span class="sxs-lookup"><span data-stu-id="f594a-236">Ranking input and outputs</span></span>

<span data-ttu-id="f594a-237">Giriş etiketi veri türü, [anahtar](xref:Microsoft.ML.Data.KeyDataViewType) türünde veya <xref:System.Single>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f594a-237">The input label data type must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type or <xref:System.Single>.</span></span> <span data-ttu-id="f594a-238">Etiketin değeri ilgiyi belirler, burada daha yüksek değerler daha yüksek uygunluğu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f594a-238">The value of the label determines relevance, where higher values indicate higher relevance.</span></span> <span data-ttu-id="f594a-239">Etiket bir [anahtar](xref:Microsoft.ML.Data.KeyDataViewType) türü ise, anahtar dizin, en küçük dizin en az ilgili olan ilgi değeridir.</span><span class="sxs-lookup"><span data-stu-id="f594a-239">If the label is a [key](xref:Microsoft.ML.Data.KeyDataViewType) type, then the key index is the relevance value, where the smallest index is the least relevant.</span></span> <span data-ttu-id="f594a-240">Etiket bir <xref:System.Single>ise, daha büyük değerler daha yüksek uygunluğu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f594a-240">If the label is a <xref:System.Single>, larger values indicate higher relevance.</span></span>

<span data-ttu-id="f594a-241">Özellik verileri sabit boyutlu bir vektör <xref:System.Single> olmalıdır ve giriş satırı grup sütunu [anahtar](xref:Microsoft.ML.Data.KeyDataViewType) türünde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f594a-241">The feature data must be a fixed size vector of <xref:System.Single> and input row group column must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>

<span data-ttu-id="f594a-242">Bu, aşağıdaki çıkışları verir:</span><span class="sxs-lookup"><span data-stu-id="f594a-242">This trainer outputs the following:</span></span>

| <span data-ttu-id="f594a-243">Çıkış adı</span><span class="sxs-lookup"><span data-stu-id="f594a-243">Output Name</span></span> | <span data-ttu-id="f594a-244">Tür</span><span class="sxs-lookup"><span data-stu-id="f594a-244">Type</span></span> | <span data-ttu-id="f594a-245">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f594a-245">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="f594a-246">Tahmin belirlenmesi için model tarafından hesaplanan, sınırlandırılmamış puan</span><span class="sxs-lookup"><span data-stu-id="f594a-246">The unbounded score that was calculated by the model to determine the prediction</span></span> |

## <a name="recommendation"></a><span data-ttu-id="f594a-247">Öneri</span><span class="sxs-lookup"><span data-stu-id="f594a-247">Recommendation</span></span>

<span data-ttu-id="f594a-248">Öneri görevi, önerilen ürünlerin veya hizmetlerin bir listesini üretmenizi mümkün.</span><span class="sxs-lookup"><span data-stu-id="f594a-248">A recommendation task enables producing a list of recommended products or services.</span></span> <span data-ttu-id="f594a-249">ML.NET, kataloğunuzda geçmiş ürün derecelendirme verileri olduğunda öneriler için [birlikte](https://en.wikipedia.org/wiki/Collaborative_filtering) çalışan bir filtreleme algoritması olan [matris factorleştirme (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29)kullanır.</span><span class="sxs-lookup"><span data-stu-id="f594a-249">ML.NET uses [Matrix factorization (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), a [collaborative filtering](https://en.wikipedia.org/wiki/Collaborative_filtering) algorithm for recommendations when you have historical product rating data in your catalog.</span></span> <span data-ttu-id="f594a-250">Örneğin, kullanıcılarınız için geçmiş film derecelendirme verileri vardır ve diğer filmleri daha sonra izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f594a-250">For example, you have historical movie rating data for your users and want to recommend  other movies they are likely to watch next.</span></span>

### <a name="recommendation-training-algorithms"></a><span data-ttu-id="f594a-251">Öneri eğitimi algoritmaları</span><span class="sxs-lookup"><span data-stu-id="f594a-251">Recommendation training algorithms</span></span>

<span data-ttu-id="f594a-252">Aşağıdaki algoritmayla bir öneri modeli eğitebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f594a-252">You can train a recommendation model with the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>
