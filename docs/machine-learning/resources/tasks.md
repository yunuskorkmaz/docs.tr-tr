---
title: Makine öğrenimi görevlerini - ML.NET
description: Farklı makine öğrenimi görevlerini ve ML.NET içinde desteklenen ilişkili görevleri keşfedin.
ms.custom: seodec18
ms.date: 04/12/2019
author: natke
ms.openlocfilehash: bfed9cf12f8d539c4327549e5305415ce096e022
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59613167"
---
# <a name="machine-learning-tasks-in-mlnet"></a><span data-ttu-id="14ab7-103">ML.NET Machine learning görevleri</span><span class="sxs-lookup"><span data-stu-id="14ab7-103">Machine learning tasks in ML.NET</span></span>

<span data-ttu-id="14ab7-104">Bir machine learning modeli oluştururken ilk verilerinizle elde etmek umarak tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="14ab7-104">When building a machine learning model, you first need to define what you are hoping to achieve with your data.</span></span> <span data-ttu-id="14ab7-105">Bu görev durumunuza öğrenme doğru makine seçmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="14ab7-105">This allows you to choose the right machine learning task for your situation.</span></span> <span data-ttu-id="14ab7-106">Aşağıdaki listede, aralarından seçim yapabileceğiniz görevleri öğrenme farklı makine açıklar ve bazı yaygın kullanım örnekleri.</span><span class="sxs-lookup"><span data-stu-id="14ab7-106">The following list describes the different machine learning tasks that you can choose from and some common use cases.</span></span>

<span data-ttu-id="14ab7-107">Senaryonuz için hangi görev çalışır karar verdikten sonra modeli eğitmek için en iyi algoritmayı seçin gerekir.</span><span class="sxs-lookup"><span data-stu-id="14ab7-107">Once you have decided which task works for your scenario, then you need to choose the best algorithm to train your model.</span></span> <span data-ttu-id="14ab7-108">Kullanılabilir algoritmalar, her görev için bölümünde listelenir.</span><span class="sxs-lookup"><span data-stu-id="14ab7-108">The available algorithms are listed in the section for each task.</span></span>

## <a name="binary-classification"></a><span data-ttu-id="14ab7-109">İkili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="14ab7-109">Binary classification</span></span>

<span data-ttu-id="14ab7-110">A [denetimli makine öğrenimi](glossary.md#supervised-machine-learning) veri örneği ait olduğu, iki sınıf (Kategoriler) tahmin etmek için kullanılan görev.</span><span class="sxs-lookup"><span data-stu-id="14ab7-110">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict which of two classes (categories) an instance of data belongs to.</span></span> <span data-ttu-id="14ab7-111">Bir sınıflandırma algoritmasıdır girişi etiketli örnekler, her etiket bir tamsayı 0 veya 1 olduğu kümesidir.</span><span class="sxs-lookup"><span data-stu-id="14ab7-111">The input of a classification algorithm is a set of labeled examples, where each label is an integer of either 0 or 1.</span></span> <span data-ttu-id="14ab7-112">İkili sınıflandırma algoritmasıdır çıktısındaki yeni etiketlenmemiş örnek sınıfı tahmin etmek için kullanabileceğiniz bir sınıflandırıcı ' dir.</span><span class="sxs-lookup"><span data-stu-id="14ab7-112">The output of a binary classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="14ab7-113">İkili sınıflandırma senaryolarına örnekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="14ab7-113">Examples of binary classification scenarios include:</span></span>

* <span data-ttu-id="14ab7-114">[Twitter yorumların anlama yaklaşım](../tutorials/sentiment-analysis.md) "pozitif" veya "negatif" olarak.</span><span class="sxs-lookup"><span data-stu-id="14ab7-114">[Understanding sentiment of Twitter comments](../tutorials/sentiment-analysis.md) as either "positive" or "negative".</span></span>
* <span data-ttu-id="14ab7-115">Bir hastanın belirli bir Hastalık olup olmadığını tanılama.</span><span class="sxs-lookup"><span data-stu-id="14ab7-115">Diagnosing whether a patient has a certain disease or not.</span></span>
* <span data-ttu-id="14ab7-116">"Veya istenmeyen posta olarak" e-posta işaretlemek için bir kararı.</span><span class="sxs-lookup"><span data-stu-id="14ab7-116">Making a decision to mark an email as "spam" or not.</span></span>
* <span data-ttu-id="14ab7-117">Fotoğraf köpek ve Meyve içerip içermediğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="14ab7-117">Determining if a photo contains a dog or fruit.</span></span>

<span data-ttu-id="14ab7-118">Daha fazla bilgi için [ikili sınıflandırma](https://en.wikipedia.org/wiki/Binary_classification) wikipedia makalesi.</span><span class="sxs-lookup"><span data-stu-id="14ab7-118">For more information, see the [Binary classification](https://en.wikipedia.org/wiki/Binary_classification) article on Wikipedia.</span></span>

### <a name="binary-classification-training-algorithms"></a><span data-ttu-id="14ab7-119">İkili sınıflandırma eğitim algoritmaları</span><span class="sxs-lookup"><span data-stu-id="14ab7-119">Binary Classification Training Algorithms</span></span>

<span data-ttu-id="14ab7-120">Aşağıdaki algoritmaları kullanarak bir ikili sınıflandırma modelinde eğitebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="14ab7-120">You can train a binary classification model using the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer>
* <xref:Microsoft.ML.Trainers.LinearSvmTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.PriorTrainer>
* <xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedBinaryTrainer>
* <xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>

## <a name="multiclass-classification"></a><span data-ttu-id="14ab7-121">Sınıflı sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="14ab7-121">Multiclass classification</span></span>

<span data-ttu-id="14ab7-122">A [denetimli makine öğrenimi](glossary.md#supervised-machine-learning) veri örneği sınıfı (kategori) tahmin etmek için kullanılan görev.</span><span class="sxs-lookup"><span data-stu-id="14ab7-122">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the class (category) of an instance of data.</span></span> <span data-ttu-id="14ab7-123">Bir sınıflandırma algoritmasıdır girişi etiketli örnekleri kümesidir.</span><span class="sxs-lookup"><span data-stu-id="14ab7-123">The input of a classification algorithm is a set of labeled examples.</span></span> <span data-ttu-id="14ab7-124">Her etiketin normal metin olarak başlar.</span><span class="sxs-lookup"><span data-stu-id="14ab7-124">Each label normally starts as text.</span></span> <span data-ttu-id="14ab7-125">Ardından, anahtarı (sayısal) türüne dönüştürür TermTransform aracılığıyla çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="14ab7-125">It is then run through the TermTransform, which converts it to the Key (numeric) type.</span></span> <span data-ttu-id="14ab7-126">Bir sınıflandırma algoritmasıdır çıktısı, yeni etiketlenmemiş örnek sınıfı tahmin etmek için kullanabileceğiniz bir sınıflandırıcı ' dir.</span><span class="sxs-lookup"><span data-stu-id="14ab7-126">The output of a classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="14ab7-127">Çok sınıflı sınıflandırma senaryolarına örnekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="14ab7-127">Examples of multi-class classification scenarios include:</span></span>

* <span data-ttu-id="14ab7-128">Köpek bir "Siberian Husky", "Altın alıcısı", "şu dar", vb. olarak belirleniyor.</span><span class="sxs-lookup"><span data-stu-id="14ab7-128">Determining the breed of a dog as a "Siberian Husky", "Golden Retriever", "Poodle", etc.</span></span>
* <span data-ttu-id="14ab7-129">Film anlama "pozitif", "belirsiz" veya "negatif" incelenir.</span><span class="sxs-lookup"><span data-stu-id="14ab7-129">Understanding movie reviews as "positive", "neutral", or "negative".</span></span>
* <span data-ttu-id="14ab7-130">Otel kategorilendirme "Konum", "price", "temizlik", vb. incelenir.</span><span class="sxs-lookup"><span data-stu-id="14ab7-130">Categorizing hotel reviews as "location", "price", "cleanliness", etc.</span></span>

<span data-ttu-id="14ab7-131">Daha fazla bilgi için [sınıflı sınıflandırma](https://en.wikipedia.org/wiki/Multiclass_classification) wikipedia makalesi.</span><span class="sxs-lookup"><span data-stu-id="14ab7-131">For more information, see the [Multiclass classification](https://en.wikipedia.org/wiki/Multiclass_classification) article on Wikipedia.</span></span>

>[!NOTE]
><span data-ttu-id="14ab7-132">Herhangi bir vs tüm yükseltmeleri [ikili sınıflandırma learner](#binary-classification) çok sınıflı veri kümelerinde yapacak.</span><span class="sxs-lookup"><span data-stu-id="14ab7-132">One vs all upgrades any [binary classification learner](#binary-classification) to act on multiclass datasets.</span></span> <span data-ttu-id="14ab7-133">Daha fazla bilgi [Vikipedi] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span><span class="sxs-lookup"><span data-stu-id="14ab7-133">More information on [Wikipedia] (https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span></span>

### <a name="multiclass-classification-training-algorithms"></a><span data-ttu-id="14ab7-134">Çok sınıflı sınıflandırma eğitim algoritmaları</span><span class="sxs-lookup"><span data-stu-id="14ab7-134">Multiclass Classification training algorithms</span></span>

<span data-ttu-id="14ab7-135">Aşağıdaki eğitim algoritmalarını kullanarak bir çok sınıflı sınıflandırma modeli eğitmek:</span><span class="sxs-lookup"><span data-stu-id="14ab7-135">You can train a multiclass classification model using the following training algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.OneVersusAllTrainer>
* <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer>

## <a name="regression"></a><span data-ttu-id="14ab7-136">Regresyon</span><span class="sxs-lookup"><span data-stu-id="14ab7-136">Regression</span></span>

<span data-ttu-id="14ab7-137">A [denetimli makine öğrenimi](glossary.md#supervised-machine-learning) ilgili özellikleri kümesinden etiketin değeri tahmin etmek için kullanılan görev.</span><span class="sxs-lookup"><span data-stu-id="14ab7-137">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the value of the label from a set of related features.</span></span> <span data-ttu-id="14ab7-138">Etiket herhangi bir gerçek değerini olabilir ve sınıflandırma görevleri olduğu gibi değerlerin değil sınırlı ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="14ab7-138">The label can be of any real value and is not from a finite set of values as in classification tasks.</span></span> <span data-ttu-id="14ab7-139">Regresyon algoritmaları modeli etiketi özelliklerinin değerleri olarak nasıl değiştireceğini belirlemek için ilgili özellikleri etikette bağımlılığı çeşitli.</span><span class="sxs-lookup"><span data-stu-id="14ab7-139">Regression algorithms model the dependency of the label on its related features to determine how the label will change as the values of the features are varied.</span></span> <span data-ttu-id="14ab7-140">Bir regresyon algoritmasıdır girişi bir örnekler etiketlerle bilinen değerler kümesidir.</span><span class="sxs-lookup"><span data-stu-id="14ab7-140">The input of a regression algorithm is a set of examples with labels of known values.</span></span> <span data-ttu-id="14ab7-141">Bir regresyon algoritmasıdır çıktısı her yeni özellik kümesi, giriş etiketi değerini tahmin etmek için kullanabileceğiniz bir işlev ise.</span><span class="sxs-lookup"><span data-stu-id="14ab7-141">The output of a regression algorithm is a function, which you can use to predict the label value for any new set of input features.</span></span> <span data-ttu-id="14ab7-142">Regresyon senaryolarına örnekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="14ab7-142">Examples of regression scenarios include:</span></span>

* <span data-ttu-id="14ab7-143">Ev fiyatları yatak, konum ve boyut sayısı gibi merkezi özniteliklerini temel alarak tahmin etme.</span><span class="sxs-lookup"><span data-stu-id="14ab7-143">Predicting house prices based on house attributes such as number of bedrooms, location, or size.</span></span>
* <span data-ttu-id="14ab7-144">Geçmiş verileri ve geçerli pazar eğilimlerine göre gelecekteki hisse senedi fiyatlarını tahmin etme.</span><span class="sxs-lookup"><span data-stu-id="14ab7-144">Predicting future stock prices based on historical data and current market trends.</span></span>
* <span data-ttu-id="14ab7-145">Bütçelerini reklam üzerinde temel bir ürün satışları tahmin etme.</span><span class="sxs-lookup"><span data-stu-id="14ab7-145">Predicting sales of a product based on advertising budgets.</span></span>

### <a name="regression-training-algorithms"></a><span data-ttu-id="14ab7-146">Regresyon eğitim algoritmaları</span><span class="sxs-lookup"><span data-stu-id="14ab7-146">Regression training algorithms</span></span>

<span data-ttu-id="14ab7-147">Aşağıdaki algoritmaları kullanarak bir regresyon modeli eğitmek:</span><span class="sxs-lookup"><span data-stu-id="14ab7-147">You can train a regression model using the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>
* <xref:Microsoft.ML.Trainers.OlsTrainer>
* <xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>
* <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>

## <a name="clustering"></a><span data-ttu-id="14ab7-148">Kümeleme</span><span class="sxs-lookup"><span data-stu-id="14ab7-148">Clustering</span></span>

<span data-ttu-id="14ab7-149">Bir [Denetimsiz machine learning](glossary.md#unsupervised-machine-learning) benzer özelliklere içeren kümeler halinde veri grubu örnekleri için kullanılan görev.</span><span class="sxs-lookup"><span data-stu-id="14ab7-149">An [unsupervised machine learning](glossary.md#unsupervised-machine-learning) task that is used to group instances of data into clusters that contain similar characteristics.</span></span> <span data-ttu-id="14ab7-150">Kümeleme de olmayan mantıksal olarak türettiğiniz DataSet ilişkileri tanımlamak için gözatma veya basit gözlem tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="14ab7-150">Clustering can also be used to identify relationships in a dataset that you might not logically derive by browsing or simple observation.</span></span> <span data-ttu-id="14ab7-151">Giriş ve çıkışları kümeleme algoritması, seçilen metodolojiyi üzerinde bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="14ab7-151">The inputs and outputs of a clustering algorithm depends on the methodology chosen.</span></span> <span data-ttu-id="14ab7-152">Bir dağıtım, kütle Merkezi, bağlantı veya yoğunluk yaklaşımla alabilir.</span><span class="sxs-lookup"><span data-stu-id="14ab7-152">You can take a distribution, centroid, connectivity, or density-based approach.</span></span> <span data-ttu-id="14ab7-153">ML.NET şu anda K-ortalamaları Kümelemesi kullanarak kütle merkezi tabanlı bir yaklaşımı destekler.</span><span class="sxs-lookup"><span data-stu-id="14ab7-153">ML.NET currently supports a centroid-based approach using K-Means clustering.</span></span> <span data-ttu-id="14ab7-154">Kümeleme senaryolarına örnekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="14ab7-154">Examples of clustering scenarios include:</span></span>

* <span data-ttu-id="14ab7-155">Otel Konukları alışkanlıkları ve Otel seçeneği özelliklere göre parçalarını anlama.</span><span class="sxs-lookup"><span data-stu-id="14ab7-155">Understanding segments of hotel guests based on habits and characteristics of hotel choices.</span></span>
* <span data-ttu-id="14ab7-156">Müşteri kesimleri ve demografik bilgilere bağlı hedeflenen reklam kampanyaları oluşturmanıza yardımcı olmak için tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="14ab7-156">Identifying customer segments and demographics to help build targeted advertising campaigns.</span></span>
* <span data-ttu-id="14ab7-157">Üretim ölçümleri temel alarak envanteri halinde kategorilere ayrılması.</span><span class="sxs-lookup"><span data-stu-id="14ab7-157">Categorizing inventory based on manufacturing metrics.</span></span>

### <a name="clustering-training-algorithms"></a><span data-ttu-id="14ab7-158">Kümeleme eğitim algoritmaları</span><span class="sxs-lookup"><span data-stu-id="14ab7-158">Clustering training algorithms</span></span>

<span data-ttu-id="14ab7-159">Aşağıdaki algoritması kullanarak bir kümeleme modeli eğitmek:</span><span class="sxs-lookup"><span data-stu-id="14ab7-159">You can train a clustering model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.KMeansTrainer>

## <a name="anomaly-detection"></a><span data-ttu-id="14ab7-160">Anomali algılama</span><span class="sxs-lookup"><span data-stu-id="14ab7-160">Anomaly detection</span></span>

<span data-ttu-id="14ab7-161">Bu görevi, asıl bileşen analiz (PCA) kullanarak bir anomali algılama modeli oluşturur.</span><span class="sxs-lookup"><span data-stu-id="14ab7-161">This task creates an anomaly detection model by using Principal Component Analysis (PCA).</span></span> <span data-ttu-id="14ab7-162">PCA tabanlı Anomali algılama geçerli işlemler gibi bir sınıf eğitim verilerini almak kolay, ancak yeterli örnekleri hedeflenen anomali elde etmek zor olduğu senaryolar modelinde oluşturmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="14ab7-162">PCA-Based Anomaly Detection helps you build a model in scenarios where it is easy to obtain training data from one class, such as valid transactions, but difficult to obtain sufficient samples of the targeted anomalies.</span></span>

<span data-ttu-id="14ab7-163">İç yapısını gösterir ve veri varyans açıklar machine learning'de PCA kurulan bir teknik keşif veri analizi sık kullanılır.</span><span class="sxs-lookup"><span data-stu-id="14ab7-163">An established technique in machine learning, PCA is frequently used in exploratory data analysis because it reveals the inner structure of the data and explains the variance in the data.</span></span> <span data-ttu-id="14ab7-164">Birden fazla değişken içeren verileri analiz ederek PCA çalışır.</span><span class="sxs-lookup"><span data-stu-id="14ab7-164">PCA works by analyzing data that contains multiple variables.</span></span> <span data-ttu-id="14ab7-165">Bu değişkenler arasındaki bağıntıları arar ve en iyi sonuçlar farklılıkları yakalar değerlerinin birleşimi belirler.</span><span class="sxs-lookup"><span data-stu-id="14ab7-165">It looks for correlations among the variables and determines the combination of values that best captures differences in outcomes.</span></span> <span data-ttu-id="14ab7-166">Bu birleşik özellik değerleri, asıl bileşen olarak adlandırılıyordu daha kompakt bir özellik alanı oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="14ab7-166">These combined feature values are used to create a more compact feature space called the principal components.</span></span>

<span data-ttu-id="14ab7-167">Anomali algılama machine learning'de birçok önemli görevleri kapsar:</span><span class="sxs-lookup"><span data-stu-id="14ab7-167">Anomaly detection encompasses many important tasks in machine learning:</span></span>

* <span data-ttu-id="14ab7-168">Olası sahte işlem tanımlama.</span><span class="sxs-lookup"><span data-stu-id="14ab7-168">Identifying transactions that are potentially fraudulent.</span></span>
* <span data-ttu-id="14ab7-169">Ağa yetkisiz erişim oluştu olarak görülebilecek desenler öğrenme.</span><span class="sxs-lookup"><span data-stu-id="14ab7-169">Learning patterns that indicate that a network intrusion has occurred.</span></span>
* <span data-ttu-id="14ab7-170">Hastalara anormal kümelerini bulma.</span><span class="sxs-lookup"><span data-stu-id="14ab7-170">Finding abnormal clusters of patients.</span></span>
* <span data-ttu-id="14ab7-171">Değer denetimi bir sisteme girdi.</span><span class="sxs-lookup"><span data-stu-id="14ab7-171">Checking values entered into a system.</span></span>

<span data-ttu-id="14ab7-172">Anomalileri tanımına göre nadir olayları olduğundan, temsili bir örnek model için kullanılacak veri toplamak zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="14ab7-172">Because anomalies are rare events by definition, it can be difficult to collect a representative sample of data to use for modeling.</span></span> <span data-ttu-id="14ab7-173">Bu kategoride bulunan algoritmaları özellikle imbalanced veri kümelerini kullanarak oluşturma ve eğitim modeli çekirdek sorunları gidermek üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="14ab7-173">The algorithms included in this category have been especially designed to address the core challenges of building and training models by using imbalanced data sets.</span></span>

### <a name="anomaly-detection-training-algorithms"></a><span data-ttu-id="14ab7-174">Anomali algılama eğitim algoritmaları</span><span class="sxs-lookup"><span data-stu-id="14ab7-174">Anomaly detection training algorithms</span></span>

<span data-ttu-id="14ab7-175">Aşağıdaki algoritması kullanarak bir anomali algılama modeli eğitmek:</span><span class="sxs-lookup"><span data-stu-id="14ab7-175">You can train an anomaly detection model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>

## <a name="ranking"></a><span data-ttu-id="14ab7-176">Derecelendirme</span><span class="sxs-lookup"><span data-stu-id="14ab7-176">Ranking</span></span>

<span data-ttu-id="14ab7-177">Derecelendirme görev derecelendiricisini etiketli örnekleri bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="14ab7-177">A ranking task constructs a ranker from a set of labeled examples.</span></span> <span data-ttu-id="14ab7-178">Bu örnek kümesi ile puanlanmış örnek grupları oluşan bir tetikleyicisi.</span><span class="sxs-lookup"><span data-stu-id="14ab7-178">This example set consists of instance groups that can be scored with a given criteria.</span></span> <span data-ttu-id="14ab7-179">{0, 1, 2, 3, 4} her örneği için olan derecelendirme etiketleri.</span><span class="sxs-lookup"><span data-stu-id="14ab7-179">The ranking labels are { 0, 1, 2, 3, 4 } for each instance.</span></span>  <span data-ttu-id="14ab7-180">Derecelendiricisini bilinmeyen puanlarının her örneği için yeni derece örneği gruplara eğitildi.</span><span class="sxs-lookup"><span data-stu-id="14ab7-180">The ranker is trained to rank new instance groups with unknown scores for each instance.</span></span> <span data-ttu-id="14ab7-181">ML.NET derecelendirme öğrencileriyle olan [öğrenilen makine derecelendirme](https://en.wikipedia.org/wiki/Learning_to_rank) bağlı.</span><span class="sxs-lookup"><span data-stu-id="14ab7-181">ML.NET ranking learners are [machine learned ranking](https://en.wikipedia.org/wiki/Learning_to_rank) based.</span></span>

### <a name="ranking-training-algorithms"></a><span data-ttu-id="14ab7-182">Sıralama eğitim algoritmaları</span><span class="sxs-lookup"><span data-stu-id="14ab7-182">Ranking training algorithms</span></span>

<span data-ttu-id="14ab7-183">Aşağıdaki algoritmaları ile bir derecelendirme modeli eğitmek:</span><span class="sxs-lookup"><span data-stu-id="14ab7-183">You can train a ranking model with the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>

## <a name="recommendation"></a><span data-ttu-id="14ab7-184">Öneri</span><span class="sxs-lookup"><span data-stu-id="14ab7-184">Recommendation</span></span>

<span data-ttu-id="14ab7-185">Bir öneri görevi önerilen ürünleri veya hizmetleri listesi oluşturmayı etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="14ab7-185">A recommendation task enables producing a list of recommended products or services.</span></span> <span data-ttu-id="14ab7-186">ML.NET kullanan [matris factorization (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), [işbirliğine dayalı filtreleme](https://en.wikipedia.org/wiki/Collaborative_filtering) geçmiş ürün derecelendirmesi veri Kataloğu'nda varsa önerileri için algoritma.</span><span class="sxs-lookup"><span data-stu-id="14ab7-186">ML.NET uses [Matrix factorization (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), a [collaborative filtering](https://en.wikipedia.org/wiki/Collaborative_filtering) algorithm for recommendations when you have historical product rating data in your catalog.</span></span> <span data-ttu-id="14ab7-187">Örneğin, kullanıcılarınız için geçmiş film derecelendirmesi verilere sahip ve sonraki izleyin okunduğunun diğer filmler önermek istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="14ab7-187">For example, you have historical movie rating data for your users and want to recommend  other movies they are likely to watch next.</span></span>

### <a name="recommendation-training-algorithms"></a><span data-ttu-id="14ab7-188">Öneri eğitim algoritmaları</span><span class="sxs-lookup"><span data-stu-id="14ab7-188">Recommendation training algorithms</span></span>

<span data-ttu-id="14ab7-189">Aşağıdaki algoritması ile bir öneri modeli eğitmek:</span><span class="sxs-lookup"><span data-stu-id="14ab7-189">You can train a recommendation model with the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>
