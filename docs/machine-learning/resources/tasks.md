---
title: Makine öğrenimi görevleri
description: ML.NET sürümünde desteklenen farklı makine öğrenimi görevlerini ve ilişkili görevleri keşfedebilirsiniz.
ms.date: 12/23/2019
ms.openlocfilehash: e6e36bd65dbadb8cb7b8edbf9e2e82071c208378
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144454"
---
# <a name="machine-learning-tasks-in-mlnet"></a><span data-ttu-id="e9e36-103">ML.NET 'de makine öğrenimi görevleri</span><span class="sxs-lookup"><span data-stu-id="e9e36-103">Machine learning tasks in ML.NET</span></span>

<span data-ttu-id="e9e36-104">Makine öğrenimi görevi, istenen sorun veya soruya ve kullanılabilir verilere göre yapılan tahmin veya çıkarım türüdür.</span><span class="sxs-lookup"><span data-stu-id="e9e36-104">A machine learning task is the type of prediction or inference being made, based on the problem or question that is being asked, and the available data.</span></span> <span data-ttu-id="e9e36-105">Örneğin, sınıflandırma görevi verileri kategorilere atar ve kümeleme görevi verileri benzerliğe göre gruplandırır.</span><span class="sxs-lookup"><span data-stu-id="e9e36-105">For example, the classification task assigns data to categories, and the clustering task groups data according to similarity.</span></span>

<span data-ttu-id="e9e36-106">Machine Learning görevleri, verileri açıkça programlanabilir değil, verilerdeki desenlere bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e9e36-106">Machine learning tasks rely on patterns in the data rather than being explicitly programmed.</span></span>

<span data-ttu-id="e9e36-107">Bu makalede, ML.NET ve bazı yaygın kullanım durumları arasından seçim yapabileceğiniz farklı makine öğrenimi görevleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e9e36-107">This article describes the different machine learning tasks that you can choose from in ML.NET and some common use cases.</span></span>

<span data-ttu-id="e9e36-108">Senaryolarınız için hangi görevin çalıştığına karar verdikten sonra, modelinize eğitebilmeniz için en iyi algoritmayı seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9e36-108">Once you have decided which task works for your scenario, then you need to choose the best algorithm to train your model.</span></span> <span data-ttu-id="e9e36-109">Kullanılabilir algoritmalar her görevin bölümünde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="e9e36-109">The available algorithms are listed in the section for each task.</span></span>

## <a name="binary-classification"></a><span data-ttu-id="e9e36-110">İkili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="e9e36-110">Binary classification</span></span>

<span data-ttu-id="e9e36-111">İki sınıftan (kategori) hangisinin ait olduğunu tahmin etmek için kullanılan [denetimli bir makine öğrenimi](glossary.md#supervised-machine-learning) görevi.</span><span class="sxs-lookup"><span data-stu-id="e9e36-111">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict which of two classes (categories) an instance of data belongs to.</span></span> <span data-ttu-id="e9e36-112">Sınıflandırma algoritmasının girişi, her etiketin 0 veya 1 tamsayısı olduğu etiketli örnekler kümesidir.</span><span class="sxs-lookup"><span data-stu-id="e9e36-112">The input of a classification algorithm is a set of labeled examples, where each label is an integer of either 0 or 1.</span></span> <span data-ttu-id="e9e36-113">İkili sınıflandırma algoritmasının çıktısı, yeni etiketlenmiş olmayan örneklerin sınıfını tahmin etmek için kullanabileceğiniz bir sınıflandırıcıdır.</span><span class="sxs-lookup"><span data-stu-id="e9e36-113">The output of a binary classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="e9e36-114">İkili sınıflandırma senaryolarına örnek olarak şunlar verilebilir:</span><span class="sxs-lookup"><span data-stu-id="e9e36-114">Examples of binary classification scenarios include:</span></span>

* <span data-ttu-id="e9e36-115">[Twitter açıklamalarının](../tutorials/sentiment-analysis.md) yaklaşımını "pozitif" veya "negatif" olarak anlama.</span><span class="sxs-lookup"><span data-stu-id="e9e36-115">[Understanding sentiment of Twitter comments](../tutorials/sentiment-analysis.md) as either "positive" or "negative".</span></span>
* <span data-ttu-id="e9e36-116">Hasta 'in belirli bir sapmasına sahip olup olmadığını tanılama.</span><span class="sxs-lookup"><span data-stu-id="e9e36-116">Diagnosing whether a patient has a certain disease or not.</span></span>
* <span data-ttu-id="e9e36-117">E-postayı "istenmeyen posta" olarak işaretlemek için bir karar verme.</span><span class="sxs-lookup"><span data-stu-id="e9e36-117">Making a decision to mark an email as "spam" or not.</span></span>
* <span data-ttu-id="e9e36-118">Bir fotoğrafın bir köpek ya da meyve gibi belirli bir öğe içerip içermediğini belirleme.</span><span class="sxs-lookup"><span data-stu-id="e9e36-118">Determining if a photo contains a particular item or not, such as a dog or fruit.</span></span>

<span data-ttu-id="e9e36-119">Daha fazla bilgi için Vikipde bulunan [ikili sınıflandırma](https://en.wikipedia.org/wiki/Binary_classification) makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="e9e36-119">For more information, see the [Binary classification](https://en.wikipedia.org/wiki/Binary_classification) article on Wikipedia.</span></span>

### <a name="binary-classification-trainers"></a><span data-ttu-id="e9e36-120">İkili sınıflandırma traiciler</span><span class="sxs-lookup"><span data-stu-id="e9e36-120">Binary classification trainers</span></span>

<span data-ttu-id="e9e36-121">Aşağıdaki algoritmaları kullanarak bir ikili sınıflandırma modeli eğitebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e9e36-121">You can train a binary classification model using the following algorithms:</span></span>

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

### <a name="binary-classification-inputs-and-outputs"></a><span data-ttu-id="e9e36-122">İkili sınıflandırma girişleri ve çıkışları</span><span class="sxs-lookup"><span data-stu-id="e9e36-122">Binary classification inputs and outputs</span></span>

<span data-ttu-id="e9e36-123">İkili sınıflandırmayla en iyi sonuçları elde etmek için eğitim verilerinin dengelenmesi gerekir (yani, pozitif ve negatif eğitim verilerinin eşit sayısı).</span><span class="sxs-lookup"><span data-stu-id="e9e36-123">For best results with binary classification, the training data should be balanced (that is, equal numbers of positive and negative training data).</span></span> <span data-ttu-id="e9e36-124">Eksik değerler, eğitimin önüne alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e9e36-124">Missing values should be handled before training.</span></span>

<span data-ttu-id="e9e36-125">Giriş etiketi sütun verileri olmalıdır <xref:System.Boolean> .</span><span class="sxs-lookup"><span data-stu-id="e9e36-125">The input label column data must be <xref:System.Boolean>.</span></span>
<span data-ttu-id="e9e36-126">Giriş özellikleri sütun verileri sabit boyutlu bir vektör olmalıdır <xref:System.Single> .</span><span class="sxs-lookup"><span data-stu-id="e9e36-126">The input features column data must be a fixed-size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="e9e36-127">Bu traçler aşağıdaki sütunları çıktı:</span><span class="sxs-lookup"><span data-stu-id="e9e36-127">These trainers output the following columns:</span></span>

| <span data-ttu-id="e9e36-128">Çıkış sütunu adı</span><span class="sxs-lookup"><span data-stu-id="e9e36-128">Output Column Name</span></span> | <span data-ttu-id="e9e36-129">Sütun türü</span><span class="sxs-lookup"><span data-stu-id="e9e36-129">Column Type</span></span> | <span data-ttu-id="e9e36-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9e36-130">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="e9e36-131">Model tarafından hesaplanan ham puan</span><span class="sxs-lookup"><span data-stu-id="e9e36-131">The raw score that was calculated by the model</span></span>|
| `PredictedLabel` | <xref:System.Boolean> | <span data-ttu-id="e9e36-132">Puanınızın işaretine göre öngörülen etiket.</span><span class="sxs-lookup"><span data-stu-id="e9e36-132">The predicted label, based on the sign of the score.</span></span> <span data-ttu-id="e9e36-133">Negatif puan ile eşlenir `false` ve bir pozitif puan ile eşlenir `true` .</span><span class="sxs-lookup"><span data-stu-id="e9e36-133">A negative score maps to `false` and a positive score maps to `true`.</span></span>|

## <a name="multiclass-classification"></a><span data-ttu-id="e9e36-134">Birden çok Lass sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="e9e36-134">Multiclass classification</span></span>

<span data-ttu-id="e9e36-135">Bir veri örneğinin sınıfını (kategori) tahmin etmek için kullanılan [denetimli bir makine öğrenimi](glossary.md#supervised-machine-learning) görevi.</span><span class="sxs-lookup"><span data-stu-id="e9e36-135">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the class (category) of an instance of data.</span></span> <span data-ttu-id="e9e36-136">Sınıflandırma algoritmasının girişi, etiketlenmiş bir örnek kümesidir.</span><span class="sxs-lookup"><span data-stu-id="e9e36-136">The input of a classification algorithm is a set of labeled examples.</span></span> <span data-ttu-id="e9e36-137">Her etiket normalde metin olarak başlar.</span><span class="sxs-lookup"><span data-stu-id="e9e36-137">Each label normally starts as text.</span></span> <span data-ttu-id="e9e36-138">Daha sonra TermTransform aracılığıyla çalıştırılır. Bu, anahtar (sayısal) türüne dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="e9e36-138">It is then run through the TermTransform, which converts it to the Key (numeric) type.</span></span> <span data-ttu-id="e9e36-139">Bir sınıflandırma algoritmasının çıktısı, yeni etiketlenmiş olmayan örneklerin sınıfını tahmin etmek için kullanabileceğiniz bir sınıflandırıcıdır.</span><span class="sxs-lookup"><span data-stu-id="e9e36-139">The output of a classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="e9e36-140">Çok sınıflı sınıflandırma senaryolarına örnek olarak şunlar verilebilir:</span><span class="sxs-lookup"><span data-stu-id="e9e36-140">Examples of multi-class classification scenarios include:</span></span>

* <span data-ttu-id="e9e36-141">Bir köpek "Sıberian Husky", "altın Retriever", "Pookıl" vb. olarak belirlenir.</span><span class="sxs-lookup"><span data-stu-id="e9e36-141">Determining the breed of a dog as a "Siberian Husky", "Golden Retriever", "Poodle", etc.</span></span>
* <span data-ttu-id="e9e36-142">Film incelemelerini "pozitif", "nötr" veya "negatif" olarak anlama.</span><span class="sxs-lookup"><span data-stu-id="e9e36-142">Understanding movie reviews as "positive", "neutral", or "negative".</span></span>
* <span data-ttu-id="e9e36-143">Otel incelemelerini "konum", "Price", "cleanliness" vb. olarak kategorilere ayırma.</span><span class="sxs-lookup"><span data-stu-id="e9e36-143">Categorizing hotel reviews as "location", "price", "cleanliness", etc.</span></span>

<span data-ttu-id="e9e36-144">Daha fazla bilgi için Vikipde bulunan [birden çok sınıf sınıflandırması](https://en.wikipedia.org/wiki/Multiclass_classification) makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="e9e36-144">For more information, see the [Multiclass classification](https://en.wikipedia.org/wiki/Multiclass_classification) article on Wikipedia.</span></span>

>[!NOTE]
><span data-ttu-id="e9e36-145">Bunlardan biri, birden çok Lass veri kümesi üzerinde işlem yapmak için herhangi bir [ikili sınıflandırmanın yükseltimidir](#binary-classification) .</span><span class="sxs-lookup"><span data-stu-id="e9e36-145">One vs all upgrades any [binary classification learner](#binary-classification) to act on multiclass datasets.</span></span> <span data-ttu-id="e9e36-146">[Vikipedi](https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest)hakkında daha fazla bilgi.</span><span class="sxs-lookup"><span data-stu-id="e9e36-146">More information on [Wikipedia](https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span></span>

### <a name="multiclass-classification-trainers"></a><span data-ttu-id="e9e36-147">Birden çok Lass sınıflandırma traipleyiciler</span><span class="sxs-lookup"><span data-stu-id="e9e36-147">Multiclass classification trainers</span></span>

<span data-ttu-id="e9e36-148">Aşağıdaki eğitim algoritmalarını kullanarak çok bir Lass sınıflandırma modelini eğitebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e9e36-148">You can train a multiclass classification model using the following training algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.OneVersusAllTrainer>
* <xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer>
* <xref:Microsoft.ML.Vision.ImageClassificationTrainer>

### <a name="multiclass-classification-inputs-and-outputs"></a><span data-ttu-id="e9e36-149">Birden çok Lass sınıflandırma girişleri ve çıkışları</span><span class="sxs-lookup"><span data-stu-id="e9e36-149">Multiclass classification inputs and outputs</span></span>

<span data-ttu-id="e9e36-150">Giriş etiketi sütun verileri, [anahtar](xref:Microsoft.ML.Data.KeyDataViewType) türünde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e9e36-150">The input label column data must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>
<span data-ttu-id="e9e36-151">Özellik sütunu sabit boyutlu bir vektör olmalıdır <xref:System.Single> .</span><span class="sxs-lookup"><span data-stu-id="e9e36-151">The feature column must be a fixed size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="e9e36-152">Bu, aşağıdaki çıkışları verir:</span><span class="sxs-lookup"><span data-stu-id="e9e36-152">This trainer outputs the following:</span></span>

| <span data-ttu-id="e9e36-153">Çıkış adı</span><span class="sxs-lookup"><span data-stu-id="e9e36-153">Output Name</span></span> | <span data-ttu-id="e9e36-154">Tür</span><span class="sxs-lookup"><span data-stu-id="e9e36-154">Type</span></span> | <span data-ttu-id="e9e36-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9e36-155">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="e9e36-156">Vektör<xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="e9e36-156">Vector of <xref:System.Single></span></span> | <span data-ttu-id="e9e36-157">Tüm sınıfların puanları.</span><span class="sxs-lookup"><span data-stu-id="e9e36-157">The scores of all classes.</span></span> <span data-ttu-id="e9e36-158">Daha yüksek değer, ilişkili sınıfa düşecek daha büyük olasılık anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e9e36-158">Higher value means higher probability to fall into the associated class.</span></span> <span data-ttu-id="e9e36-159">İ-th öğesi en büyük değere sahipse, tahmin edilen etiket dizini i olur.</span><span class="sxs-lookup"><span data-stu-id="e9e36-159">If the i-th element has the largest value, the predicted label index would be i.</span></span> <span data-ttu-id="e9e36-160">Sıfır tabanlı dizin olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e9e36-160">Note that i is zero-based index.</span></span> |
| `PredictedLabel` | <span data-ttu-id="e9e36-161">[anahtar](xref:Microsoft.ML.Data.KeyDataViewType) türü</span><span class="sxs-lookup"><span data-stu-id="e9e36-161">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="e9e36-162">Tahmin edilen etiketin dizini.</span><span class="sxs-lookup"><span data-stu-id="e9e36-162">The predicted label's index.</span></span> <span data-ttu-id="e9e36-163">Değeri i ise, gerçek etiket anahtar değerli giriş etiketi türündeki ı-TH kategorisi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e9e36-163">If its value is i, the actual label would be the i-th category in the key-valued input label type.</span></span> |

## <a name="regression"></a><span data-ttu-id="e9e36-164">Regresyon</span><span class="sxs-lookup"><span data-stu-id="e9e36-164">Regression</span></span>

<span data-ttu-id="e9e36-165">Bir ilişkili özellikler kümesinden etiketin değerini tahmin etmek için kullanılan [denetimli bir makine öğrenimi](glossary.md#supervised-machine-learning) görevi.</span><span class="sxs-lookup"><span data-stu-id="e9e36-165">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the value of the label from a set of related features.</span></span> <span data-ttu-id="e9e36-166">Etiket herhangi bir gerçek değer olabilir ve sınıflandırma görevlerinde olduğu gibi sınırlı bir değer kümesinden değildir.</span><span class="sxs-lookup"><span data-stu-id="e9e36-166">The label can be of any real value and is not from a finite set of values as in classification tasks.</span></span> <span data-ttu-id="e9e36-167">Regresyon algoritmaları, özelliğin değerleri farklılaştırılmadıkça etiketin nasıl değiştirileceğini anlamak için ilgili özellikler üzerindeki etiketin bağımlılığını modelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="e9e36-167">Regression algorithms model the dependency of the label on its related features to determine how the label will change as the values of the features are varied.</span></span> <span data-ttu-id="e9e36-168">Regresyon algoritmasının girişi, bilinen değerlerin etiketlerine sahip bir örnek kümesidir.</span><span class="sxs-lookup"><span data-stu-id="e9e36-168">The input of a regression algorithm is a set of examples with labels of known values.</span></span> <span data-ttu-id="e9e36-169">Regresyon algoritmasının çıktısı, herhangi bir yeni giriş özellikleri kümesi için etiket değerini tahmin etmek üzere kullanabileceğiniz bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="e9e36-169">The output of a regression algorithm is a function, which you can use to predict the label value for any new set of input features.</span></span> <span data-ttu-id="e9e36-170">Regresyon senaryolarına örnek olarak şunlar verilebilir:</span><span class="sxs-lookup"><span data-stu-id="e9e36-170">Examples of regression scenarios include:</span></span>

* <span data-ttu-id="e9e36-171">Yatak odası, konum veya boyut gibi ev özniteliklerini temel alan ev fiyatlarını tahmin etme.</span><span class="sxs-lookup"><span data-stu-id="e9e36-171">Predicting house prices based on house attributes such as number of bedrooms, location, or size.</span></span>
* <span data-ttu-id="e9e36-172">Geçmiş verileri ve geçerli pazar eğilimlerini temel alarak gelecekteki stok fiyatlarını tahmin etme.</span><span class="sxs-lookup"><span data-stu-id="e9e36-172">Predicting future stock prices based on historical data and current market trends.</span></span>
* <span data-ttu-id="e9e36-173">Tanıtım bütçeleri temelinde bir ürünün satışlarını tahmin etme.</span><span class="sxs-lookup"><span data-stu-id="e9e36-173">Predicting sales of a product based on advertising budgets.</span></span>

### <a name="regression-trainers"></a><span data-ttu-id="e9e36-174">Gerileme tracılar</span><span class="sxs-lookup"><span data-stu-id="e9e36-174">Regression trainers</span></span>

<span data-ttu-id="e9e36-175">Aşağıdaki algoritmaları kullanarak bir regresyon modeli eğitebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e9e36-175">You can train a regression model using the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>
* <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>
* <xref:Microsoft.ML.Trainers.OlsTrainer>
* <xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>

### <a name="regression-inputs-and-outputs"></a><span data-ttu-id="e9e36-176">Regresyon girişleri ve çıktılar</span><span class="sxs-lookup"><span data-stu-id="e9e36-176">Regression inputs and outputs</span></span>

<span data-ttu-id="e9e36-177">Giriş etiketi sütun verileri olmalıdır <xref:System.Single> .</span><span class="sxs-lookup"><span data-stu-id="e9e36-177">The input label column data must be <xref:System.Single>.</span></span>

<span data-ttu-id="e9e36-178">Bu görev için şu kadar traipler aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e9e36-178">The trainers for this task output the following:</span></span>

| <span data-ttu-id="e9e36-179">Çıkış adı</span><span class="sxs-lookup"><span data-stu-id="e9e36-179">Output Name</span></span> | <span data-ttu-id="e9e36-180">Tür</span><span class="sxs-lookup"><span data-stu-id="e9e36-180">Type</span></span> | <span data-ttu-id="e9e36-181">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9e36-181">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="e9e36-182">Model tarafından tahmin edilen ham puan</span><span class="sxs-lookup"><span data-stu-id="e9e36-182">The raw score that was predicted by the model</span></span> |

## <a name="clustering"></a><span data-ttu-id="e9e36-183">Kümeleme</span><span class="sxs-lookup"><span data-stu-id="e9e36-183">Clustering</span></span>

<span data-ttu-id="e9e36-184">Benzer özellikler içeren kümelere veri örneklerini gruplamak için kullanılan, denetimli bir [makine öğrenimi](glossary.md#unsupervised-machine-learning) görevi.</span><span class="sxs-lookup"><span data-stu-id="e9e36-184">An [unsupervised machine learning](glossary.md#unsupervised-machine-learning) task that is used to group instances of data into clusters that contain similar characteristics.</span></span> <span data-ttu-id="e9e36-185">Kümeleme, göz atma veya basit gözlemlemeye göre mantıksal olarak türeteceğiniz bir veri kümesindeki ilişkileri tanımlamak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e9e36-185">Clustering can also be used to identify relationships in a dataset that you might not logically derive by browsing or simple observation.</span></span> <span data-ttu-id="e9e36-186">Bir kümeleme algoritmasının giriş ve çıkışları, seçilen metodolojiye bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e9e36-186">The inputs and outputs of a clustering algorithm depends on the methodology chosen.</span></span> <span data-ttu-id="e9e36-187">Dağıtım, centroıd, bağlantı veya Yoğunluk tabanlı yaklaşıma sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9e36-187">You can take a distribution, centroid, connectivity, or density-based approach.</span></span> <span data-ttu-id="e9e36-188">ML.NET şu anda K-anlamı Kümelemesi kullanarak centroıd tabanlı bir yaklaşımı desteklemektedir.</span><span class="sxs-lookup"><span data-stu-id="e9e36-188">ML.NET currently supports a centroid-based approach using K-Means clustering.</span></span> <span data-ttu-id="e9e36-189">Kümeleme senaryolarına örnekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e9e36-189">Examples of clustering scenarios include:</span></span>

* <span data-ttu-id="e9e36-190">Otel seçeneklerinin alışkanlıklarını ve özelliklerini temel alarak otel konuklarının segmentlerini anlama.</span><span class="sxs-lookup"><span data-stu-id="e9e36-190">Understanding segments of hotel guests based on habits and characteristics of hotel choices.</span></span>
* <span data-ttu-id="e9e36-191">Hedeflenen reklam kampanyaları oluşturmaya yardımcı olmak için müşteri segmentlerini ve demografik tanımlama.</span><span class="sxs-lookup"><span data-stu-id="e9e36-191">Identifying customer segments and demographics to help build targeted advertising campaigns.</span></span>
* <span data-ttu-id="e9e36-192">Stoku üretim ölçümlerine göre kategorilere ayırma.</span><span class="sxs-lookup"><span data-stu-id="e9e36-192">Categorizing inventory based on manufacturing metrics.</span></span>

### <a name="clustering-trainer"></a><span data-ttu-id="e9e36-193">Kümeleme eğitmen</span><span class="sxs-lookup"><span data-stu-id="e9e36-193">Clustering trainer</span></span>

<span data-ttu-id="e9e36-194">Aşağıdaki algoritmayı kullanarak bir kümeleme modeli eğitebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e9e36-194">You can train a clustering model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.KMeansTrainer>

### <a name="clustering-inputs-and-outputs"></a><span data-ttu-id="e9e36-195">Kümeleme girişleri ve çıkışları</span><span class="sxs-lookup"><span data-stu-id="e9e36-195">Clustering inputs and outputs</span></span>

<span data-ttu-id="e9e36-196">Giriş özellikleri verileri olmalıdır <xref:System.Single> .</span><span class="sxs-lookup"><span data-stu-id="e9e36-196">The input features data must be <xref:System.Single>.</span></span> <span data-ttu-id="e9e36-197">Etiket gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="e9e36-197">No labels are needed.</span></span>

<span data-ttu-id="e9e36-198">Bu, aşağıdaki çıkışları verir:</span><span class="sxs-lookup"><span data-stu-id="e9e36-198">This trainer outputs the following:</span></span>

| <span data-ttu-id="e9e36-199">Çıkış adı</span><span class="sxs-lookup"><span data-stu-id="e9e36-199">Output Name</span></span> | <span data-ttu-id="e9e36-200">Tür</span><span class="sxs-lookup"><span data-stu-id="e9e36-200">Type</span></span> | <span data-ttu-id="e9e36-201">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9e36-201">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="e9e36-202">vektör<xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="e9e36-202">vector of <xref:System.Single></span></span> | <span data-ttu-id="e9e36-203">Verilen veri noktasının tüm kümelerdeki mesafeler ' centriods</span><span class="sxs-lookup"><span data-stu-id="e9e36-203">The distances of the given data point to all clusters' centriods</span></span> |
| `PredictedLabel` | <span data-ttu-id="e9e36-204">[anahtar](xref:Microsoft.ML.Data.KeyDataViewType) türü</span><span class="sxs-lookup"><span data-stu-id="e9e36-204">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="e9e36-205">Model tarafından tahmin edilen en yakın küme dizini.</span><span class="sxs-lookup"><span data-stu-id="e9e36-205">The closest cluster's index predicted by the model.</span></span> |

## <a name="anomaly-detection"></a><span data-ttu-id="e9e36-206">Anormallik algılama</span><span class="sxs-lookup"><span data-stu-id="e9e36-206">Anomaly detection</span></span>

<span data-ttu-id="e9e36-207">Bu görev, sorumlu bileşen analizi (PCA) kullanarak bir anomali algılama modeli oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e9e36-207">This task creates an anomaly detection model by using Principal Component Analysis (PCA).</span></span> <span data-ttu-id="e9e36-208">PCA tabanlı anomali algılama, geçerli işlemler gibi bir sınıftan eğitim verileri elde etmek, ancak hedeflenen bozukluklar için yeterli örnek elde etmek zor olan senaryolarda bir model oluşturmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="e9e36-208">PCA-Based Anomaly Detection helps you build a model in scenarios where it is easy to obtain training data from one class, such as valid transactions, but difficult to obtain sufficient samples of the targeted anomalies.</span></span>

<span data-ttu-id="e9e36-209">Machine Learning 'de sağlanan bir teknik, PCA verilerin iç yapısını açığa çıkardığından ve verilerdeki varyansı bildirdiği için araştırmacı veri analizinde sıklıkla kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e9e36-209">An established technique in machine learning, PCA is frequently used in exploratory data analysis because it reveals the inner structure of the data and explains the variance in the data.</span></span> <span data-ttu-id="e9e36-210">PCA birden çok değişken içeren verileri analiz ederek işe yarar.</span><span class="sxs-lookup"><span data-stu-id="e9e36-210">PCA works by analyzing data that contains multiple variables.</span></span> <span data-ttu-id="e9e36-211">Değişkenler arasında bağıntılar arar ve sonuçların farklarını en iyi şekilde yakalayan değerlerin birleşimini belirler.</span><span class="sxs-lookup"><span data-stu-id="e9e36-211">It looks for correlations among the variables and determines the combination of values that best captures differences in outcomes.</span></span> <span data-ttu-id="e9e36-212">Bu Birleşik özellik değerleri, sorumlu bileşenleri olarak adlandırılan daha kompakt bir özellik alanı oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e9e36-212">These combined feature values are used to create a more compact feature space called the principal components.</span></span>

<span data-ttu-id="e9e36-213">Anomali algılama, Machine Learning 'de birçok önemli görevi kapsar:</span><span class="sxs-lookup"><span data-stu-id="e9e36-213">Anomaly detection encompasses many important tasks in machine learning:</span></span>

* <span data-ttu-id="e9e36-214">Potansiyel olarak sahte olan işlemleri tanımlama.</span><span class="sxs-lookup"><span data-stu-id="e9e36-214">Identifying transactions that are potentially fraudulent.</span></span>
* <span data-ttu-id="e9e36-215">Ağ üzerinden izinsiz giriş gerçekleştiğini gösteren öğrenme desenleri.</span><span class="sxs-lookup"><span data-stu-id="e9e36-215">Learning patterns that indicate that a network intrusion has occurred.</span></span>
* <span data-ttu-id="e9e36-216">Anormal bir hastaların kümelerini bulma.</span><span class="sxs-lookup"><span data-stu-id="e9e36-216">Finding abnormal clusters of patients.</span></span>
* <span data-ttu-id="e9e36-217">Sisteme girilen değerler denetleniyor.</span><span class="sxs-lookup"><span data-stu-id="e9e36-217">Checking values entered into a system.</span></span>

<span data-ttu-id="e9e36-218">Anomali, tanıma göre nadir olaylar olduğundan, modelleme için kullanılacak verilerin temsili bir örneğini toplamak zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="e9e36-218">Because anomalies are rare events by definition, it can be difficult to collect a representative sample of data to use for modeling.</span></span> <span data-ttu-id="e9e36-219">Bu kategoriye dahil edilen algoritmalar, özellikle de imdendengelenmiş veri kümeleri kullanılarak modeller oluşturma ve eğitim konusunda temel zorlukları karşılamak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e9e36-219">The algorithms included in this category have been especially designed to address the core challenges of building and training models by using imbalanced data sets.</span></span>

### <a name="anomaly-detection-trainer"></a><span data-ttu-id="e9e36-220">Anomali algılama</span><span class="sxs-lookup"><span data-stu-id="e9e36-220">Anomaly detection trainer</span></span>

<span data-ttu-id="e9e36-221">Aşağıdaki algoritmayı kullanarak bir anomali algılama modeli eğitebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e9e36-221">You can train an anomaly detection model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>

### <a name="anomaly-detection-inputs-and-outputs"></a><span data-ttu-id="e9e36-222">Anomali algılama girişleri ve çıkışları</span><span class="sxs-lookup"><span data-stu-id="e9e36-222">Anomaly detection inputs and outputs</span></span>

<span data-ttu-id="e9e36-223">Giriş özellikleri sabit boyutlu bir vektör olmalıdır <xref:System.Single> .</span><span class="sxs-lookup"><span data-stu-id="e9e36-223">The input features must be a fixed-sized vector of <xref:System.Single>.</span></span>

<span data-ttu-id="e9e36-224">Bu, aşağıdaki çıkışları verir:</span><span class="sxs-lookup"><span data-stu-id="e9e36-224">This trainer outputs the following:</span></span>

| <span data-ttu-id="e9e36-225">Çıkış adı</span><span class="sxs-lookup"><span data-stu-id="e9e36-225">Output Name</span></span> | <span data-ttu-id="e9e36-226">Tür</span><span class="sxs-lookup"><span data-stu-id="e9e36-226">Type</span></span> | <span data-ttu-id="e9e36-227">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9e36-227">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="e9e36-228">Anomali algılama modeli tarafından hesaplanan negatif olmayan, sınırlandırılmamış puan</span><span class="sxs-lookup"><span data-stu-id="e9e36-228">The non-negative, unbounded score that was calculated by the anomaly detection model</span></span> |
| `PredictedLabel` | <xref:System.Boolean> | <span data-ttu-id="e9e36-229">Girişin bir anomali (PredictedLabel = true) olup olmadığını temsil eden doğru/yanlış değeri (PredictedLabel = false)</span><span class="sxs-lookup"><span data-stu-id="e9e36-229">A true/false value representing whether the input is an anomaly (PredictedLabel=true) or not (PredictedLabel=false)</span></span> |

## <a name="ranking"></a><span data-ttu-id="e9e36-230">Sıralamasına</span><span class="sxs-lookup"><span data-stu-id="e9e36-230">Ranking</span></span>

<span data-ttu-id="e9e36-231">Bir derecelendirme görevi bir etiketli örnekler kümesinden derecelendiricisini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e9e36-231">A ranking task constructs a ranker from a set of labeled examples.</span></span> <span data-ttu-id="e9e36-232">Bu örnek küme, verilen ölçütlerle puanlanbir örnek gruplarından oluşur.</span><span class="sxs-lookup"><span data-stu-id="e9e36-232">This example set consists of instance groups that can be scored with a given criteria.</span></span> <span data-ttu-id="e9e36-233">Sıralama etiketleri her örnek için {0, 1, 2, 3, 4}.</span><span class="sxs-lookup"><span data-stu-id="e9e36-233">The ranking labels are { 0, 1, 2, 3, 4 } for each instance.</span></span>  <span data-ttu-id="e9e36-234">Derecelendiricisini, her örnek için bilinmeyen puanları olan yeni örnek gruplarını derecelendirmek için eğitim sağlar.</span><span class="sxs-lookup"><span data-stu-id="e9e36-234">The ranker is trained to rank new instance groups with unknown scores for each instance.</span></span> <span data-ttu-id="e9e36-235">ML.NET derecelendirmesi öğrenenler, [makine tarafından öğrenilen sıralama](https://en.wikipedia.org/wiki/Learning_to_rank) tabanlıdır.</span><span class="sxs-lookup"><span data-stu-id="e9e36-235">ML.NET ranking learners are [machine learned ranking](https://en.wikipedia.org/wiki/Learning_to_rank) based.</span></span>

### <a name="ranking-training-algorithms"></a><span data-ttu-id="e9e36-236">Derecelendirme eğitimi algoritmaları</span><span class="sxs-lookup"><span data-stu-id="e9e36-236">Ranking training algorithms</span></span>

<span data-ttu-id="e9e36-237">Aşağıdaki algoritmalarla bir derecelendirme modeli eğitebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e9e36-237">You can train a ranking model with the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>

### <a name="ranking-input-and-outputs"></a><span data-ttu-id="e9e36-238">Sıralama girişi ve çıkışları</span><span class="sxs-lookup"><span data-stu-id="e9e36-238">Ranking input and outputs</span></span>

<span data-ttu-id="e9e36-239">Giriş etiketi veri türü, [anahtar](xref:Microsoft.ML.Data.KeyDataViewType) türünde veya olmalıdır <xref:System.Single> .</span><span class="sxs-lookup"><span data-stu-id="e9e36-239">The input label data type must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type or <xref:System.Single>.</span></span> <span data-ttu-id="e9e36-240">Etiketin değeri ilgiyi belirler, burada daha yüksek değerler daha yüksek uygunluğu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e9e36-240">The value of the label determines relevance, where higher values indicate higher relevance.</span></span> <span data-ttu-id="e9e36-241">Etiket bir [anahtar](xref:Microsoft.ML.Data.KeyDataViewType) türü ise, anahtar dizin, en küçük dizin en az ilgili olan ilgi değeridir.</span><span class="sxs-lookup"><span data-stu-id="e9e36-241">If the label is a [key](xref:Microsoft.ML.Data.KeyDataViewType) type, then the key index is the relevance value, where the smallest index is the least relevant.</span></span> <span data-ttu-id="e9e36-242">Etiket bir ise <xref:System.Single> , daha büyük değerler daha yüksek uygunluğu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e9e36-242">If the label is a <xref:System.Single>, larger values indicate higher relevance.</span></span>

<span data-ttu-id="e9e36-243">Özellik verileri sabit boyutlu bir vektör olmalıdır <xref:System.Single> ve giriş satırı grup sütunu [anahtar](xref:Microsoft.ML.Data.KeyDataViewType) türünde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e9e36-243">The feature data must be a fixed size vector of <xref:System.Single> and input row group column must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>

<span data-ttu-id="e9e36-244">Bu, aşağıdaki çıkışları verir:</span><span class="sxs-lookup"><span data-stu-id="e9e36-244">This trainer outputs the following:</span></span>

| <span data-ttu-id="e9e36-245">Çıkış adı</span><span class="sxs-lookup"><span data-stu-id="e9e36-245">Output Name</span></span> | <span data-ttu-id="e9e36-246">Tür</span><span class="sxs-lookup"><span data-stu-id="e9e36-246">Type</span></span> | <span data-ttu-id="e9e36-247">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9e36-247">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="e9e36-248">Tahmin belirlenmesi için model tarafından hesaplanan, sınırlandırılmamış puan</span><span class="sxs-lookup"><span data-stu-id="e9e36-248">The unbounded score that was calculated by the model to determine the prediction</span></span> |

## <a name="recommendation"></a><span data-ttu-id="e9e36-249">Öneri</span><span class="sxs-lookup"><span data-stu-id="e9e36-249">Recommendation</span></span>

<span data-ttu-id="e9e36-250">Öneri görevi, önerilen ürünlerin veya hizmetlerin bir listesini üretmenizi mümkün.</span><span class="sxs-lookup"><span data-stu-id="e9e36-250">A recommendation task enables producing a list of recommended products or services.</span></span> <span data-ttu-id="e9e36-251">ML.NET, kataloğunuzda geçmiş ürün derecelendirme verileri olduğunda öneriler için [birlikte](https://en.wikipedia.org/wiki/Collaborative_filtering) çalışan bir filtreleme algoritması olan [matris factorleştirme (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29)kullanır.</span><span class="sxs-lookup"><span data-stu-id="e9e36-251">ML.NET uses [Matrix factorization (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), a [collaborative filtering](https://en.wikipedia.org/wiki/Collaborative_filtering) algorithm for recommendations when you have historical product rating data in your catalog.</span></span> <span data-ttu-id="e9e36-252">Örneğin, kullanıcılarınız için geçmiş film derecelendirme verileri vardır ve diğer filmleri daha sonra izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9e36-252">For example, you have historical movie rating data for your users and want to recommend  other movies they are likely to watch next.</span></span>

### <a name="recommendation-training-algorithms"></a><span data-ttu-id="e9e36-253">Öneri eğitimi algoritmaları</span><span class="sxs-lookup"><span data-stu-id="e9e36-253">Recommendation training algorithms</span></span>

<span data-ttu-id="e9e36-254">Aşağıdaki algoritmayla bir öneri modeli eğitebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e9e36-254">You can train a recommendation model with the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>

## <a name="forecasting"></a><span data-ttu-id="e9e36-255">Tahmin etme</span><span class="sxs-lookup"><span data-stu-id="e9e36-255">Forecasting</span></span>

<span data-ttu-id="e9e36-256">Tahmin görevi, gelecekteki davranışları hakkında tahminler yapmak için geçen zaman serisi verilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e9e36-256">The forecasting task use past time-series data to make predictions about future behavior.</span></span> <span data-ttu-id="e9e36-257">Tahmin için geçerli olan senaryolar, hava durumu tahmini, dönemsel satış tahminleri ve tahmine dayalı bakım dahil,</span><span class="sxs-lookup"><span data-stu-id="e9e36-257">Scenarios applicable to forecasting include weather forecasting, seasonal sales predictions, and predictive maintenance,</span></span>

### <a name="forecasting-trainers"></a><span data-ttu-id="e9e36-258">Tahmin tahminleri tahmin ediliyor</span><span class="sxs-lookup"><span data-stu-id="e9e36-258">Forecasting trainers</span></span>

<span data-ttu-id="e9e36-259">Aşağıdaki algoritmayla bir tahmin modeli eğitebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e9e36-259">You can train a forecasting model with the following algorithm:</span></span>

<xref:Microsoft.ML.TimeSeriesCatalog.ForecastBySsa*>
