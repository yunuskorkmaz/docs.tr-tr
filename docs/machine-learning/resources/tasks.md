---
title: Makine öğrenimi görevleri
description: ML.NET desteklenen farklı makine öğrenimi görevlerini ve ilişkili görevleri keşfedin.
ms.date: 12/23/2019
ms.openlocfilehash: 6cd41065e668375537b9816ef7a208a65e0a523b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399205"
---
# <a name="machine-learning-tasks-in-mlnet"></a><span data-ttu-id="66129-103">ML.NET makine öğrenimi görevleri</span><span class="sxs-lookup"><span data-stu-id="66129-103">Machine learning tasks in ML.NET</span></span>

<span data-ttu-id="66129-104">Makine öğrenimi görevi, sorulan soruna veya soruya ve kullanılabilir verilere dayalı olarak yapılan tahmin veya çıkarım türüdür.</span><span class="sxs-lookup"><span data-stu-id="66129-104">A machine learning task is the type of prediction or inference being made, based on the problem or question that is being asked, and the available data.</span></span> <span data-ttu-id="66129-105">Örneğin, sınıflandırma görevi kategorilere veri atar ve kümeleme görev grupları verileri benzerliğe göre gruplandırır.</span><span class="sxs-lookup"><span data-stu-id="66129-105">For example, the classification task assigns data to categories, and the clustering task groups data according to similarity.</span></span>

<span data-ttu-id="66129-106">Makine öğrenimi görevleri, açıkça programlanmaktan çok verilerdeki desenlere dayanır.</span><span class="sxs-lookup"><span data-stu-id="66129-106">Machine learning tasks rely on patterns in the data rather than being explicitly programmed.</span></span>

<span data-ttu-id="66129-107">Bu makalede, ML.NET ve bazı yaygın kullanım durumlarında seçebileceğiniz farklı makine öğrenimi görevleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="66129-107">This article describes the different machine learning tasks that you can choose from in ML.NET and some common use cases.</span></span>

<span data-ttu-id="66129-108">Senaryonuz için hangi görevin işe yaradığına karar verdikten sonra, modelinizi eğitmek için en iyi algoritmayı seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="66129-108">Once you have decided which task works for your scenario, then you need to choose the best algorithm to train your model.</span></span> <span data-ttu-id="66129-109">Kullanılabilir algoritmalar her görev için bölümde listelenir.</span><span class="sxs-lookup"><span data-stu-id="66129-109">The available algorithms are listed in the section for each task.</span></span>

## <a name="binary-classification"></a><span data-ttu-id="66129-110">İkili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="66129-110">Binary classification</span></span>

<span data-ttu-id="66129-111">İki sınıftan (kategoride) bir veri örneğinin ait olduğunu tahmin etmek için kullanılan [denetlenen makine öğrenimi](glossary.md#supervised-machine-learning) görevi.</span><span class="sxs-lookup"><span data-stu-id="66129-111">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict which of two classes (categories) an instance of data belongs to.</span></span> <span data-ttu-id="66129-112">Sınıflandırma algoritmasının girişi, her etiketin 0 veya 1'lik bir tamsayı olduğu etiketli örnekler kümesidir.</span><span class="sxs-lookup"><span data-stu-id="66129-112">The input of a classification algorithm is a set of labeled examples, where each label is an integer of either 0 or 1.</span></span> <span data-ttu-id="66129-113">İkili sınıflandırma algoritmasının çıktısı, yeni etiketlenmemiş örneklerin sınıfını tahmin etmek için kullanabileceğiniz bir sınıflandırmadır.</span><span class="sxs-lookup"><span data-stu-id="66129-113">The output of a binary classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="66129-114">İkili sınıflandırma senaryolarına örnek olarak şunlar verilebilir:</span><span class="sxs-lookup"><span data-stu-id="66129-114">Examples of binary classification scenarios include:</span></span>

* <span data-ttu-id="66129-115">[Twitter yorumlarının duygularını](../tutorials/sentiment-analysis.md) ya "olumlu" ya da "olumsuz" olarak anlamak.</span><span class="sxs-lookup"><span data-stu-id="66129-115">[Understanding sentiment of Twitter comments](../tutorials/sentiment-analysis.md) as either "positive" or "negative".</span></span>
* <span data-ttu-id="66129-116">Hastanın belirli bir hastalığı olup olmadığını teşhis etmek.</span><span class="sxs-lookup"><span data-stu-id="66129-116">Diagnosing whether a patient has a certain disease or not.</span></span>
* <span data-ttu-id="66129-117">Bir e-postayı "spam" olarak işaretleme kararı almak veya işaretlememek.</span><span class="sxs-lookup"><span data-stu-id="66129-117">Making a decision to mark an email as "spam" or not.</span></span>
* <span data-ttu-id="66129-118">Bir fotoğrafın köpek veya meyve gibi belirli bir öğeyi içerip içermediğini belirleme.</span><span class="sxs-lookup"><span data-stu-id="66129-118">Determining if a photo contains a particular item or not, such as a dog or fruit.</span></span>

<span data-ttu-id="66129-119">Daha fazla bilgi için Vikipedi'deki [İkili sınıflandırma](https://en.wikipedia.org/wiki/Binary_classification) makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="66129-119">For more information, see the [Binary classification](https://en.wikipedia.org/wiki/Binary_classification) article on Wikipedia.</span></span>

### <a name="binary-classification-trainers"></a><span data-ttu-id="66129-120">İkili sınıflandırma eğitmenleri</span><span class="sxs-lookup"><span data-stu-id="66129-120">Binary classification trainers</span></span>

<span data-ttu-id="66129-121">Aşağıdaki algoritmaları kullanarak ikili sınıflandırma modelini eğitebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="66129-121">You can train a binary classification model using the following algorithms:</span></span>

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

### <a name="binary-classification-inputs-and-outputs"></a><span data-ttu-id="66129-122">İkili sınıflandırma giriş ve çıkışları</span><span class="sxs-lookup"><span data-stu-id="66129-122">Binary classification inputs and outputs</span></span>

<span data-ttu-id="66129-123">İkili sınıflandırma ile en iyi sonuçlar için, eğitim verileri dengeli olmalıdır (yani, pozitif ve negatif eğitim verilerinin eşit sayıda).</span><span class="sxs-lookup"><span data-stu-id="66129-123">For best results with binary classification, the training data should be balanced (that is, equal numbers of positive and negative training data).</span></span> <span data-ttu-id="66129-124">Eksik değerler eğitimden önce ele alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="66129-124">Missing values should be handled before training.</span></span>

<span data-ttu-id="66129-125">Giriş etiketi sütun verileri <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="66129-125">The input label column data must be <xref:System.Boolean>.</span></span>
<span data-ttu-id="66129-126">Giriş özellikleri sütun verileri sabit boyutlu bir <xref:System.Single>vektör olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="66129-126">The input features column data must be a fixed-size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="66129-127">Bu eğitmenler aşağıdaki sütunları çıktı:</span><span class="sxs-lookup"><span data-stu-id="66129-127">These trainers output the following columns:</span></span>

| <span data-ttu-id="66129-128">Çıktı Sütun Adı</span><span class="sxs-lookup"><span data-stu-id="66129-128">Output Column Name</span></span> | <span data-ttu-id="66129-129">Sütun Türü</span><span class="sxs-lookup"><span data-stu-id="66129-129">Column Type</span></span> | <span data-ttu-id="66129-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66129-130">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="66129-131">Model tarafından hesaplanan ham puan</span><span class="sxs-lookup"><span data-stu-id="66129-131">The raw score that was calculated by the model</span></span>|
| `PredictedLabel` | <xref:System.Boolean> | <span data-ttu-id="66129-132">Skor işaretine göre öngörülen etiket.</span><span class="sxs-lookup"><span data-stu-id="66129-132">The predicted label, based on the sign of the score.</span></span> <span data-ttu-id="66129-133">Negatif bir puan `false` haritaları ve pozitif `true`bir puan haritaları .</span><span class="sxs-lookup"><span data-stu-id="66129-133">A negative score maps to `false` and a positive score maps to `true`.</span></span>|

## <a name="multiclass-classification"></a><span data-ttu-id="66129-134">Çok sınıflı sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="66129-134">Multiclass classification</span></span>

<span data-ttu-id="66129-135">Bir veri örneğinin sınıfını (kategorisini) tahmin etmek için kullanılan [denetlenen makine öğrenimi](glossary.md#supervised-machine-learning) görevi.</span><span class="sxs-lookup"><span data-stu-id="66129-135">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the class (category) of an instance of data.</span></span> <span data-ttu-id="66129-136">Sınıflandırma algoritmasının girişi, etiketli örnekler kümesidir.</span><span class="sxs-lookup"><span data-stu-id="66129-136">The input of a classification algorithm is a set of labeled examples.</span></span> <span data-ttu-id="66129-137">Her etiket normalde metin olarak başlar.</span><span class="sxs-lookup"><span data-stu-id="66129-137">Each label normally starts as text.</span></span> <span data-ttu-id="66129-138">Daha sonra, Anahtar (sayısal) türüne dönüştüren TermTransform üzerinden çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="66129-138">It is then run through the TermTransform, which converts it to the Key (numeric) type.</span></span> <span data-ttu-id="66129-139">Sınıflandırma algoritmasının çıktısı, yeni etiketlenmemiş örneklerin sınıfını tahmin etmek için kullanabileceğiniz bir sınıflandırma algoritmasıdır.</span><span class="sxs-lookup"><span data-stu-id="66129-139">The output of a classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="66129-140">Çok sınıflı sınıflandırma senaryolarına örnek olarak şunlar verilebilir:</span><span class="sxs-lookup"><span data-stu-id="66129-140">Examples of multi-class classification scenarios include:</span></span>

* <span data-ttu-id="66129-141">Bir "Sibirya Husky", "Golden Retriever", "Kaniş" vb gibi bir köpek cins belirlenmesi</span><span class="sxs-lookup"><span data-stu-id="66129-141">Determining the breed of a dog as a "Siberian Husky", "Golden Retriever", "Poodle", etc.</span></span>
* <span data-ttu-id="66129-142">Film yorumlarını "olumlu", "tarafsız" veya "olumsuz" olarak anlamak.</span><span class="sxs-lookup"><span data-stu-id="66129-142">Understanding movie reviews as "positive", "neutral", or "negative".</span></span>
* <span data-ttu-id="66129-143">Otel yorumlarını "konum", "fiyat", "temizlik" vb. olarak kategorilere ayırmak.</span><span class="sxs-lookup"><span data-stu-id="66129-143">Categorizing hotel reviews as "location", "price", "cleanliness", etc.</span></span>

<span data-ttu-id="66129-144">Daha fazla bilgi için Vikipedi'deki [Çok Sınıflı sınıflandırma](https://en.wikipedia.org/wiki/Multiclass_classification) makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="66129-144">For more information, see the [Multiclass classification](https://en.wikipedia.org/wiki/Multiclass_classification) article on Wikipedia.</span></span>

>[!NOTE]
><span data-ttu-id="66129-145">Bir vs tüm yükseltmeleri herhangi bir [ikili sınıflandırma öğrenen](#binary-classification) çoklu sınıf veri kümeleri üzerinde hareket etmek.</span><span class="sxs-lookup"><span data-stu-id="66129-145">One vs all upgrades any [binary classification learner](#binary-classification) to act on multiclass datasets.</span></span> <span data-ttu-id="66129-146">[Vikipedi] hakkında dahahttps://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest)fazla bilgi ( .</span><span class="sxs-lookup"><span data-stu-id="66129-146">More information on [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span></span>

### <a name="multiclass-classification-trainers"></a><span data-ttu-id="66129-147">Çok sınıflı sınıflandırma eğitmenleri</span><span class="sxs-lookup"><span data-stu-id="66129-147">Multiclass classification trainers</span></span>

<span data-ttu-id="66129-148">Aşağıdaki eğitim algoritmalarını kullanarak çok sınıflı bir sınıflandırma modeli eğitebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="66129-148">You can train a multiclass classification model using the following training algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.OneVersusAllTrainer>
* <xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer>
* <xref:Microsoft.ML.Vision.ImageClassificationTrainer>

### <a name="multiclass-classification-inputs-and-outputs"></a><span data-ttu-id="66129-149">Çok sınıflı sınıflandırma giriş ve çıktıları</span><span class="sxs-lookup"><span data-stu-id="66129-149">Multiclass classification inputs and outputs</span></span>

<span data-ttu-id="66129-150">Giriş etiketi sütun verileri [anahtar](xref:Microsoft.ML.Data.KeyDataViewType) türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="66129-150">The input label column data must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>
<span data-ttu-id="66129-151">Özellik sütunu sabit boyutlu bir <xref:System.Single>vektör olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="66129-151">The feature column must be a fixed size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="66129-152">Bu eğitmen aşağıdaki çıkışları:</span><span class="sxs-lookup"><span data-stu-id="66129-152">This trainer outputs the following:</span></span>

| <span data-ttu-id="66129-153">Çıktı Adı</span><span class="sxs-lookup"><span data-stu-id="66129-153">Output Name</span></span> | <span data-ttu-id="66129-154">Tür</span><span class="sxs-lookup"><span data-stu-id="66129-154">Type</span></span> | <span data-ttu-id="66129-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66129-155">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="66129-156">Vektör<xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="66129-156">Vector of <xref:System.Single></span></span> | <span data-ttu-id="66129-157">Tüm sınıfların puanları.</span><span class="sxs-lookup"><span data-stu-id="66129-157">The scores of all classes.</span></span> <span data-ttu-id="66129-158">Daha yüksek değer, ilişkili sınıfa düşme olasılığının daha yüksek olması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="66129-158">Higher value means higher probability to fall into the associated class.</span></span> <span data-ttu-id="66129-159">i-th öğesi en büyük değere sahipse, öngörülen etiket dizini i olacaktır.</span><span class="sxs-lookup"><span data-stu-id="66129-159">If the i-th element has the largest value, the predicted label index would be i.</span></span> <span data-ttu-id="66129-160">I sıfır tabanlı dizin olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="66129-160">Note that i is zero-based index.</span></span> |
| `PredictedLabel` | <span data-ttu-id="66129-161">[anahtar](xref:Microsoft.ML.Data.KeyDataViewType) türü</span><span class="sxs-lookup"><span data-stu-id="66129-161">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="66129-162">Tahmin edilen etiketin dizini.</span><span class="sxs-lookup"><span data-stu-id="66129-162">The predicted label's index.</span></span> <span data-ttu-id="66129-163">Değeri i ise, gerçek etiket anahtar değerli giriş etiketi türünde i-th kategorisi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="66129-163">If its value is i, the actual label would be the i-th category in the key-valued input label type.</span></span> |

## <a name="regression"></a><span data-ttu-id="66129-164">Regresyon</span><span class="sxs-lookup"><span data-stu-id="66129-164">Regression</span></span>

<span data-ttu-id="66129-165">İlgili özellikler kümesinden etiketin değerini tahmin etmek için kullanılan [denetlenen makine öğrenimi](glossary.md#supervised-machine-learning) görevi.</span><span class="sxs-lookup"><span data-stu-id="66129-165">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the value of the label from a set of related features.</span></span> <span data-ttu-id="66129-166">Etiket herhangi bir gerçek değere sahip olabilir ve sınıflandırma görevlerinde olduğu gibi sonlu bir değer kümesinden değildir.</span><span class="sxs-lookup"><span data-stu-id="66129-166">The label can be of any real value and is not from a finite set of values as in classification tasks.</span></span> <span data-ttu-id="66129-167">Regresyon algoritmaları, özelliklerin değerleri farklı olarak etiketin nasıl değişeceğini belirlemek için etiketin ilgili özellikleriüzerindeki bağımlılığını modeller.</span><span class="sxs-lookup"><span data-stu-id="66129-167">Regression algorithms model the dependency of the label on its related features to determine how the label will change as the values of the features are varied.</span></span> <span data-ttu-id="66129-168">Bir regresyon algoritması girişi bilinen değerlerin etiketleri ile örnekler kümesidir.</span><span class="sxs-lookup"><span data-stu-id="66129-168">The input of a regression algorithm is a set of examples with labels of known values.</span></span> <span data-ttu-id="66129-169">Bir regresyon algoritmasının çıktısı, herhangi bir yeni giriş özellikleri kümesi için etiket değerini tahmin etmek için kullanabileceğiniz bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="66129-169">The output of a regression algorithm is a function, which you can use to predict the label value for any new set of input features.</span></span> <span data-ttu-id="66129-170">Gerileme senaryolarına örnek olarak şunlar verilebilir:</span><span class="sxs-lookup"><span data-stu-id="66129-170">Examples of regression scenarios include:</span></span>

* <span data-ttu-id="66129-171">Yatak odası sayısı, yer veya boyut gibi ev özelliklerine göre ev fiyatları tahmin.</span><span class="sxs-lookup"><span data-stu-id="66129-171">Predicting house prices based on house attributes such as number of bedrooms, location, or size.</span></span>
* <span data-ttu-id="66129-172">Geçmiş verilere ve mevcut piyasa eğilimlerine dayalı olarak gelecekteki hisse senedi fiyatlarını tahmin etmek.</span><span class="sxs-lookup"><span data-stu-id="66129-172">Predicting future stock prices based on historical data and current market trends.</span></span>
* <span data-ttu-id="66129-173">Reklam bütçelerine dayalı bir ürünün satışını tahmin etme.</span><span class="sxs-lookup"><span data-stu-id="66129-173">Predicting sales of a product based on advertising budgets.</span></span>

### <a name="regression-trainers"></a><span data-ttu-id="66129-174">Regresyon eğitmenleri</span><span class="sxs-lookup"><span data-stu-id="66129-174">Regression trainers</span></span>

<span data-ttu-id="66129-175">Aşağıdaki algoritmaları kullanarak bir regresyon modeli eğitebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="66129-175">You can train a regression model using the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>
* <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>
* <xref:Microsoft.ML.Trainers.OlsTrainer>
* <xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>

### <a name="regression-inputs-and-outputs"></a><span data-ttu-id="66129-176">Regresyon giriş ve çıkışları</span><span class="sxs-lookup"><span data-stu-id="66129-176">Regression inputs and outputs</span></span>

<span data-ttu-id="66129-177">Giriş etiketi sütun verileri <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="66129-177">The input label column data must be <xref:System.Single>.</span></span>

<span data-ttu-id="66129-178">Bu görev için eğitmenler aşağıdaki çıktı çıktı:</span><span class="sxs-lookup"><span data-stu-id="66129-178">The trainers for this task output the following:</span></span>

| <span data-ttu-id="66129-179">Çıktı Adı</span><span class="sxs-lookup"><span data-stu-id="66129-179">Output Name</span></span> | <span data-ttu-id="66129-180">Tür</span><span class="sxs-lookup"><span data-stu-id="66129-180">Type</span></span> | <span data-ttu-id="66129-181">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66129-181">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="66129-182">Model tarafından öngörülen ham puan</span><span class="sxs-lookup"><span data-stu-id="66129-182">The raw score that was predicted by the model</span></span> |

## <a name="clustering"></a><span data-ttu-id="66129-183">Kümeleme</span><span class="sxs-lookup"><span data-stu-id="66129-183">Clustering</span></span>

<span data-ttu-id="66129-184">Veri örneklerini benzer özelliklere sahip kümeler halinde gruplandırmak için kullanılan [denetimsiz bir makine öğrenimi](glossary.md#unsupervised-machine-learning) görevi.</span><span class="sxs-lookup"><span data-stu-id="66129-184">An [unsupervised machine learning](glossary.md#unsupervised-machine-learning) task that is used to group instances of data into clusters that contain similar characteristics.</span></span> <span data-ttu-id="66129-185">Kümeleme, bir veri kümesinde, tarama veya basit gözlem le mantıksal olarak elde edilemeyeceğiniz ilişkileri tanımlamak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="66129-185">Clustering can also be used to identify relationships in a dataset that you might not logically derive by browsing or simple observation.</span></span> <span data-ttu-id="66129-186">Kümeleme algoritmasının giriş ve çıkışları seçilen metodolojiye bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="66129-186">The inputs and outputs of a clustering algorithm depends on the methodology chosen.</span></span> <span data-ttu-id="66129-187">Bir dağılım, merkez, bağlantı veya yoğunluk tabanlı bir yaklaşım alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66129-187">You can take a distribution, centroid, connectivity, or density-based approach.</span></span> <span data-ttu-id="66129-188">ML.NET şu anda K-Means kümeleme kullanarak bir santrioit tabanlı bir yaklaşım destekler.</span><span class="sxs-lookup"><span data-stu-id="66129-188">ML.NET currently supports a centroid-based approach using K-Means clustering.</span></span> <span data-ttu-id="66129-189">Kümeleme senaryolarına örnek olarak şunlar verilebilir:</span><span class="sxs-lookup"><span data-stu-id="66129-189">Examples of clustering scenarios include:</span></span>

* <span data-ttu-id="66129-190">Otel konuklarının yaşam ve otel seçeneklerinin özelliklerine göre bölümlerini anlamak.</span><span class="sxs-lookup"><span data-stu-id="66129-190">Understanding segments of hotel guests based on habits and characteristics of hotel choices.</span></span>
* <span data-ttu-id="66129-191">Hedefli reklam kampanyaları oluşturmaya yardımcı olmak için müşteri segmentlerini ve demografik özellikleri belirlemek.</span><span class="sxs-lookup"><span data-stu-id="66129-191">Identifying customer segments and demographics to help build targeted advertising campaigns.</span></span>
* <span data-ttu-id="66129-192">Üretim ölçümlerine göre envanteri kategorilere ayırma.</span><span class="sxs-lookup"><span data-stu-id="66129-192">Categorizing inventory based on manufacturing metrics.</span></span>

### <a name="clustering-trainer"></a><span data-ttu-id="66129-193">Kümeleme eğitmeni</span><span class="sxs-lookup"><span data-stu-id="66129-193">Clustering trainer</span></span>

<span data-ttu-id="66129-194">Aşağıdaki algoritmayı kullanarak bir kümeleme modelini eğitebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="66129-194">You can train a clustering model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.KMeansTrainer>

### <a name="clustering-inputs-and-outputs"></a><span data-ttu-id="66129-195">Girdi ve çıktıları kümeleme</span><span class="sxs-lookup"><span data-stu-id="66129-195">Clustering inputs and outputs</span></span>

<span data-ttu-id="66129-196">Giriş özellikleri verileri . <xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="66129-196">The input features data must be <xref:System.Single>.</span></span> <span data-ttu-id="66129-197">Etiket gerekmez.</span><span class="sxs-lookup"><span data-stu-id="66129-197">No labels are needed.</span></span>

<span data-ttu-id="66129-198">Bu eğitmen aşağıdaki çıkışları:</span><span class="sxs-lookup"><span data-stu-id="66129-198">This trainer outputs the following:</span></span>

| <span data-ttu-id="66129-199">Çıktı Adı</span><span class="sxs-lookup"><span data-stu-id="66129-199">Output Name</span></span> | <span data-ttu-id="66129-200">Tür</span><span class="sxs-lookup"><span data-stu-id="66129-200">Type</span></span> | <span data-ttu-id="66129-201">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66129-201">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="66129-202">vektörü<xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="66129-202">vector of <xref:System.Single></span></span> | <span data-ttu-id="66129-203">Verilen verilerin tüm kümelerin merkezlerine olan uzaklıkları</span><span class="sxs-lookup"><span data-stu-id="66129-203">The distances of the given data point to all clusters' centriods</span></span> |
| `PredictedLabel` | <span data-ttu-id="66129-204">[anahtar](xref:Microsoft.ML.Data.KeyDataViewType) türü</span><span class="sxs-lookup"><span data-stu-id="66129-204">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="66129-205">Model tarafından öngörülen en yakın kümenin dizin.</span><span class="sxs-lookup"><span data-stu-id="66129-205">The closest cluster's index predicted by the model.</span></span> |

## <a name="anomaly-detection"></a><span data-ttu-id="66129-206">Anormallik algılama</span><span class="sxs-lookup"><span data-stu-id="66129-206">Anomaly detection</span></span>

<span data-ttu-id="66129-207">Bu görev, Temel Bileşen Analizi (PCA) kullanarak bir anomali algılama modeli oluşturur.</span><span class="sxs-lookup"><span data-stu-id="66129-207">This task creates an anomaly detection model by using Principal Component Analysis (PCA).</span></span> <span data-ttu-id="66129-208">PCA Tabanlı Anomali Algılama, geçerli işlemler gibi bir sınıftan eğitim verilerini almanın kolay olduğu, ancak hedeflenen anomalilerden yeterli örnek almanın zor olduğu senaryolarda bir model oluşturmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="66129-208">PCA-Based Anomaly Detection helps you build a model in scenarios where it is easy to obtain training data from one class, such as valid transactions, but difficult to obtain sufficient samples of the targeted anomalies.</span></span>

<span data-ttu-id="66129-209">Makine öğreniminde yerleşik bir teknik olan PCA, verilerin iç yapısını ortaya çıkardığı ve verilerdeki varyansı açıkladığı için araştırmacı veri analizinde sıklıkla kullanılır.</span><span class="sxs-lookup"><span data-stu-id="66129-209">An established technique in machine learning, PCA is frequently used in exploratory data analysis because it reveals the inner structure of the data and explains the variance in the data.</span></span> <span data-ttu-id="66129-210">PCA, birden çok değişken içeren verileri analiz ederek çalışır.</span><span class="sxs-lookup"><span data-stu-id="66129-210">PCA works by analyzing data that contains multiple variables.</span></span> <span data-ttu-id="66129-211">Değişkenler arasındaki bağıntıları arar ve sonuçlardaki farklılıkları en iyi yakalayan değerlerin birleşimini belirler.</span><span class="sxs-lookup"><span data-stu-id="66129-211">It looks for correlations among the variables and determines the combination of values that best captures differences in outcomes.</span></span> <span data-ttu-id="66129-212">Bu birleştirilmiş özellik değerleri, ana bileşenler adı verilen daha kompakt bir özellik alanı oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="66129-212">These combined feature values are used to create a more compact feature space called the principal components.</span></span>

<span data-ttu-id="66129-213">Anomali tespiti makine öğreniminde birçok önemli görevi kapsar:</span><span class="sxs-lookup"><span data-stu-id="66129-213">Anomaly detection encompasses many important tasks in machine learning:</span></span>

* <span data-ttu-id="66129-214">Sahte olabilecek hareketleri tanımlama.</span><span class="sxs-lookup"><span data-stu-id="66129-214">Identifying transactions that are potentially fraudulent.</span></span>
* <span data-ttu-id="66129-215">Ağ izinsiz girişinin gerçekleştiğini gösteren öğrenme kalıpları.</span><span class="sxs-lookup"><span data-stu-id="66129-215">Learning patterns that indicate that a network intrusion has occurred.</span></span>
* <span data-ttu-id="66129-216">Anormal hasta kümeleri bulmak.</span><span class="sxs-lookup"><span data-stu-id="66129-216">Finding abnormal clusters of patients.</span></span>
* <span data-ttu-id="66129-217">Sisteme girilen değerleri denetleme.</span><span class="sxs-lookup"><span data-stu-id="66129-217">Checking values entered into a system.</span></span>

<span data-ttu-id="66129-218">Anomaliler tanım olarak nadir olaylar olduğundan, modelleme için kullanılacak temsili bir veri örneği toplamak zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="66129-218">Because anomalies are rare events by definition, it can be difficult to collect a representative sample of data to use for modeling.</span></span> <span data-ttu-id="66129-219">Bu kategoride yer alan algoritmalar özellikle dengesiz veri kümeleri kullanarak oluşturma ve eğitim modellerinin temel zorluklarını ele almak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="66129-219">The algorithms included in this category have been especially designed to address the core challenges of building and training models by using imbalanced data sets.</span></span>

### <a name="anomaly-detection-trainer"></a><span data-ttu-id="66129-220">Anomali tespit eğitmeni</span><span class="sxs-lookup"><span data-stu-id="66129-220">Anomaly detection trainer</span></span>

<span data-ttu-id="66129-221">Aşağıdaki algoritmayı kullanarak bir anomali algılama modeli eğitebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="66129-221">You can train an anomaly detection model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>

### <a name="anomaly-detection-inputs-and-outputs"></a><span data-ttu-id="66129-222">Anomali algılama giriş ve çıkışları</span><span class="sxs-lookup"><span data-stu-id="66129-222">Anomaly detection inputs and outputs</span></span>

<span data-ttu-id="66129-223">Giriş özellikleri sabit boyutlu bir vektör <xref:System.Single>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="66129-223">The input features must be a fixed-sized vector of <xref:System.Single>.</span></span>

<span data-ttu-id="66129-224">Bu eğitmen aşağıdaki çıkışları:</span><span class="sxs-lookup"><span data-stu-id="66129-224">This trainer outputs the following:</span></span>

| <span data-ttu-id="66129-225">Çıktı Adı</span><span class="sxs-lookup"><span data-stu-id="66129-225">Output Name</span></span> | <span data-ttu-id="66129-226">Tür</span><span class="sxs-lookup"><span data-stu-id="66129-226">Type</span></span> | <span data-ttu-id="66129-227">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66129-227">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="66129-228">Anomali algılama modeli ile hesaplanan negatif olmayan, sınırsız skor</span><span class="sxs-lookup"><span data-stu-id="66129-228">The non-negative, unbounded score that was calculated by the anomaly detection model</span></span> |
| `PredictedLabel` | <xref:System.Boolean> | <span data-ttu-id="66129-229">Girişin bir anormallik olup olmadığını gösteren gerçek/yanlış değer (PredictedLabel=true) (PredictedLabel=false)</span><span class="sxs-lookup"><span data-stu-id="66129-229">A true/false value representing whether the input is an anomaly (PredictedLabel=true) or not (PredictedLabel=false)</span></span> |

## <a name="ranking"></a><span data-ttu-id="66129-230">Sıralama</span><span class="sxs-lookup"><span data-stu-id="66129-230">Ranking</span></span>

<span data-ttu-id="66129-231">Sıralama görevi, etiketli örnekler kümesinden bir sıralama oluşturucusu belirler.</span><span class="sxs-lookup"><span data-stu-id="66129-231">A ranking task constructs a ranker from a set of labeled examples.</span></span> <span data-ttu-id="66129-232">Bu örnek kümesi, belirli bir ölçütle puanlanabilecek örnek gruplarından oluşur.</span><span class="sxs-lookup"><span data-stu-id="66129-232">This example set consists of instance groups that can be scored with a given criteria.</span></span> <span data-ttu-id="66129-233">Sıralama etiketleri her örnek için { 0, 1, 2, 3, 4 } 'dir.</span><span class="sxs-lookup"><span data-stu-id="66129-233">The ranking labels are { 0, 1, 2, 3, 4 } for each instance.</span></span>  <span data-ttu-id="66129-234">Ranker, her örnek için bilinmeyen puanları olan yeni örnek gruplarını sıralamak üzere eğitilir.</span><span class="sxs-lookup"><span data-stu-id="66129-234">The ranker is trained to rank new instance groups with unknown scores for each instance.</span></span> <span data-ttu-id="66129-235">ML.NET sıralama öğrenenler [makine tabanlı sıralama öğrendim.](https://en.wikipedia.org/wiki/Learning_to_rank)</span><span class="sxs-lookup"><span data-stu-id="66129-235">ML.NET ranking learners are [machine learned ranking](https://en.wikipedia.org/wiki/Learning_to_rank) based.</span></span>

### <a name="ranking-training-algorithms"></a><span data-ttu-id="66129-236">Sıralama eğitim algoritmaları</span><span class="sxs-lookup"><span data-stu-id="66129-236">Ranking training algorithms</span></span>

<span data-ttu-id="66129-237">Bir sıralama modelini aşağıdaki algoritmalarla eğitebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="66129-237">You can train a ranking model with the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>

### <a name="ranking-input-and-outputs"></a><span data-ttu-id="66129-238">Giriş ve çıktıları sıralama</span><span class="sxs-lookup"><span data-stu-id="66129-238">Ranking input and outputs</span></span>

<span data-ttu-id="66129-239">Giriş etiketi veri türü [anahtar](xref:Microsoft.ML.Data.KeyDataViewType) türü <xref:System.Single>veya .</span><span class="sxs-lookup"><span data-stu-id="66129-239">The input label data type must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type or <xref:System.Single>.</span></span> <span data-ttu-id="66129-240">Etiketin değeri, daha yüksek değerlerin daha yüksek alaka düzeyini gösterdiği alaka düzeyini belirler.</span><span class="sxs-lookup"><span data-stu-id="66129-240">The value of the label determines relevance, where higher values indicate higher relevance.</span></span> <span data-ttu-id="66129-241">Etiket [anahtar](xref:Microsoft.ML.Data.KeyDataViewType) türüyse, anahtar dizin, en küçük dizin en az alakalı olduğu alaka düzeyi değeridir.</span><span class="sxs-lookup"><span data-stu-id="66129-241">If the label is a [key](xref:Microsoft.ML.Data.KeyDataViewType) type, then the key index is the relevance value, where the smallest index is the least relevant.</span></span> <span data-ttu-id="66129-242">Etiket bir <xref:System.Single>ise, daha büyük değerler daha yüksek alaka gösterir.</span><span class="sxs-lookup"><span data-stu-id="66129-242">If the label is a <xref:System.Single>, larger values indicate higher relevance.</span></span>

<span data-ttu-id="66129-243">Özellik verileri sabit boyutlu bir <xref:System.Single> vektör olmalı ve giriş satırı grup sütunu [anahtar](xref:Microsoft.ML.Data.KeyDataViewType) türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="66129-243">The feature data must be a fixed size vector of <xref:System.Single> and input row group column must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>

<span data-ttu-id="66129-244">Bu eğitmen aşağıdaki çıkışları:</span><span class="sxs-lookup"><span data-stu-id="66129-244">This trainer outputs the following:</span></span>

| <span data-ttu-id="66129-245">Çıktı Adı</span><span class="sxs-lookup"><span data-stu-id="66129-245">Output Name</span></span> | <span data-ttu-id="66129-246">Tür</span><span class="sxs-lookup"><span data-stu-id="66129-246">Type</span></span> | <span data-ttu-id="66129-247">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66129-247">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="66129-248">Tahminbelirlemek için model tarafından hesaplanan sınırsız puan</span><span class="sxs-lookup"><span data-stu-id="66129-248">The unbounded score that was calculated by the model to determine the prediction</span></span> |

## <a name="recommendation"></a><span data-ttu-id="66129-249">Öneri</span><span class="sxs-lookup"><span data-stu-id="66129-249">Recommendation</span></span>

<span data-ttu-id="66129-250">Öneri görevi, önerilen ürün veya hizmetlerin bir listesini oluşturmayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="66129-250">A recommendation task enables producing a list of recommended products or services.</span></span> <span data-ttu-id="66129-251">ML.NET, kataloğunuzda geçmiş ürün derecelendirme verileri varsa öneriler için ortak bir [filtreleme algoritması](https://en.wikipedia.org/wiki/Collaborative_filtering) olan [Matris çarpanalizasyonu (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29)kullanır.</span><span class="sxs-lookup"><span data-stu-id="66129-251">ML.NET uses [Matrix factorization (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), a [collaborative filtering](https://en.wikipedia.org/wiki/Collaborative_filtering) algorithm for recommendations when you have historical product rating data in your catalog.</span></span> <span data-ttu-id="66129-252">Örneğin, kullanıcılarınız için geçmiş film derecelendirme verilerine sahipsiniz ve bir sonraki izleme olasılıkları yüksek olan diğer filmleri önermek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="66129-252">For example, you have historical movie rating data for your users and want to recommend  other movies they are likely to watch next.</span></span>

### <a name="recommendation-training-algorithms"></a><span data-ttu-id="66129-253">Öneri eğitim algoritmaları</span><span class="sxs-lookup"><span data-stu-id="66129-253">Recommendation training algorithms</span></span>

<span data-ttu-id="66129-254">Bir öneri modelini aşağıdaki algoritmayla eğitebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="66129-254">You can train a recommendation model with the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>

## <a name="forecasting"></a><span data-ttu-id="66129-255">Tahmin etme</span><span class="sxs-lookup"><span data-stu-id="66129-255">Forecasting</span></span>

<span data-ttu-id="66129-256">Tahmin görevi, gelecekteki davranışlar hakkında öngörülerde bulunmak için geçmiş zaman serileri verilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="66129-256">The forecasting task use past time-series data to make predictions about future behavior.</span></span> <span data-ttu-id="66129-257">Tahmin için geçerli senaryolar arasında hava tahmini, mevsimsel satış tahminleri ve tahmine dayalı bakım,</span><span class="sxs-lookup"><span data-stu-id="66129-257">Scenarios applicable to forecasting include weather forecasting, seasonal sales predictions, and predictive maintenance,</span></span>

### <a name="forecasting-trainers"></a><span data-ttu-id="66129-258">Tahmin eğitmenleri</span><span class="sxs-lookup"><span data-stu-id="66129-258">Forecasting trainers</span></span>

<span data-ttu-id="66129-259">Bir tahmin modelini aşağıdaki algoritmayla eğitebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="66129-259">You can train a forecasting model with the following algorithm:</span></span>

<xref:Microsoft.ML.TimeSeriesCatalog.ForecastBySsa*>
