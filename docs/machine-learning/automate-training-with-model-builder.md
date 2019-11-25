---
title: Model Oluşturucu nedir ve nasıl çalışır?
description: Makine öğrenimi modelini otomatik olarak eğiteiçin ML.NET model Oluşturucu 'Yu kullanma
author: natke
ms.date: 08/07/2019
ms.custom: overview
ms.openlocfilehash: 77fe56dba3532617ad9fb0c89bfaac7c8e031ce7
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971518"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a><span data-ttu-id="0c387-103">Model Oluşturucu nedir ve nasıl çalışır?</span><span class="sxs-lookup"><span data-stu-id="0c387-103">What is Model Builder and how does it work?</span></span>

<span data-ttu-id="0c387-104">ML.NET model Oluşturucu, özel makine öğrenimi modellerini derlemek, eğitme ve dağıtmaya yönelik sezgisel bir grafik Visual Studio uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="0c387-104">ML.NET Model Builder is an intuitive graphical Visual Studio extension to build, train, and deploy custom machine learning models.</span></span>

<span data-ttu-id="0c387-105">Model Oluşturucu, senaryonuza en uygun olanı bulmanıza yardımcı olmak üzere farklı makine öğrenimi algoritmalarını ve ayarlarını araştırmak için otomatik makine öğrenimi (Otomatikml) kullanır.</span><span class="sxs-lookup"><span data-stu-id="0c387-105">Model Builder uses automated machine learning (AutoML) to explore different machine learning algorithms and settings to help you find the one that best suits your scenario.</span></span>

<span data-ttu-id="0c387-106">Model Oluşturucuyu kullanmak için Machine Learning uzmanlığına ihtiyacınız yoktur.</span><span class="sxs-lookup"><span data-stu-id="0c387-106">You don't need machine learning expertise to use Model Builder.</span></span> <span data-ttu-id="0c387-107">Bazı veriler ve çözübir sorun var.</span><span class="sxs-lookup"><span data-stu-id="0c387-107">All you need is some data, and a problem to solve.</span></span> <span data-ttu-id="0c387-108">Model Oluşturucu, modeli .NET uygulamanıza eklemek için kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0c387-108">Model Builder generates the code to add the model to your .NET application.</span></span>

![Model Oluşturucu Visual Studio uzantısı kullanıcı arabirimi animasyonu](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> <span data-ttu-id="0c387-110">Model Oluşturucu Şu anda önizleme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="0c387-110">Model Builder is currently in Preview.</span></span>

## <a name="scenarios"></a><span data-ttu-id="0c387-111">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="0c387-111">Scenarios</span></span>

<span data-ttu-id="0c387-112">Uygulamanız için bir makine öğrenimi modeli oluşturmak için model Oluşturucu 'ya birçok farklı senaryo getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0c387-112">You can bring many different scenarios to Model Builder, to generate a machine learning model for your application.</span></span>

<span data-ttu-id="0c387-113">Senaryo, verilerinizi kullanarak yapmak istediğiniz tahmin türünün bir açıklamasıdır.</span><span class="sxs-lookup"><span data-stu-id="0c387-113">A scenario is a description of the type of prediction you want to make using your data.</span></span> <span data-ttu-id="0c387-114">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="0c387-114">For example:</span></span>

- <span data-ttu-id="0c387-115">geçmiş satış verilerine göre gelecek ürün satış hacmini tahmin edin</span><span class="sxs-lookup"><span data-stu-id="0c387-115">predict future product sales volume based on historical sales data</span></span>
- <span data-ttu-id="0c387-116">müşterilerin gözden geçirmeleri temelinde olumlu veya olumsuz şekilde sınıflandırın</span><span class="sxs-lookup"><span data-stu-id="0c387-116">classify sentiments as positive or negative based on customer reviews</span></span>
- <span data-ttu-id="0c387-117">Bankacılık işleminin sahte olup olmadığını Algıla</span><span class="sxs-lookup"><span data-stu-id="0c387-117">detect whether a banking transaction is fraudulent</span></span>
- <span data-ttu-id="0c387-118">Müşteri geri bildirim sorunlarını şirketinizdeki doğru ekibe yönlendirin</span><span class="sxs-lookup"><span data-stu-id="0c387-118">route customer feedback issues to the correct team in your company</span></span>

## <a name="choose-a-model-type"></a><span data-ttu-id="0c387-119">Model türü seçin</span><span class="sxs-lookup"><span data-stu-id="0c387-119">Choose a model type</span></span>

<span data-ttu-id="0c387-120">Model Oluşturucu 'da, bir makine öğrenimi model türü seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0c387-120">In Model Builder, you need to select a machine learning model type.</span></span> <span data-ttu-id="0c387-121">Modelin türü, yapmaya çalıştığınız tahmine göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="0c387-121">The type of model depends on what sort of prediction you are trying to make.</span></span>

<span data-ttu-id="0c387-122">Bir sayıyı tahmin eden senaryolar için makine öğrenimi model türü `regression`olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="0c387-122">For scenarios that predict a number, the machine learning model type is called `regression`.</span></span>

<span data-ttu-id="0c387-123">Bir kategoriyi tahmin eden senaryolar için model türü `classification`.</span><span class="sxs-lookup"><span data-stu-id="0c387-123">For scenarios that predict a category, the model type is `classification`.</span></span> <span data-ttu-id="0c387-124">İki tür sınıflandırma vardır:</span><span class="sxs-lookup"><span data-stu-id="0c387-124">There are two types of classification:</span></span>

- <span data-ttu-id="0c387-125">yalnızca 2 kategorinin bulunduğu yer: `binary classification`.</span><span class="sxs-lookup"><span data-stu-id="0c387-125">where there are only 2 categories: `binary classification`.</span></span>
- <span data-ttu-id="0c387-126">üç veya daha fazla kategorinin bulunduğu yer: `multiclass classification`.</span><span class="sxs-lookup"><span data-stu-id="0c387-126">where there are three or more categories: `multiclass classification`.</span></span>

### <a name="which-model-type-is-right-for-me"></a><span data-ttu-id="0c387-127">Benim için hangi model türü uygun?</span><span class="sxs-lookup"><span data-stu-id="0c387-127">Which model type is right for me?</span></span>

#### <a name="predict-a-category-when-there-are-only-two-categories"></a><span data-ttu-id="0c387-128">Kategori tahmin etme (yalnızca iki kategori olduğunda)</span><span class="sxs-lookup"><span data-stu-id="0c387-128">Predict a category (when there are only two categories)</span></span>

<span data-ttu-id="0c387-129">İkili sınıflandırma, verileri iki kategoride kategorilere ayırmak için kullanılır (Evet/Hayır; geçti/başarısız; true/false; pozitif/negatif).</span><span class="sxs-lookup"><span data-stu-id="0c387-129">Binary classification is used to categorize data into two categories (yes/no; pass/fail; true/false; positive/negative).</span></span>

![Sahtekarlık algılama, risk azaltma ve uygulama filtreleme dahil olmak üzere ikili sınıflandırma örneklerini gösteren diyagram](media/binary-classification-examples.png)

<span data-ttu-id="0c387-131">Yaklaşım analizi, müşteri geri bildirimlerine yönelik olumlu veya olumsuz yaklaşımı tahmin etmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0c387-131">Sentiment analysis can be used to predict positive or negative sentiment of customer feedback.</span></span> <span data-ttu-id="0c387-132">İkili sınıflandırma modeli türüne bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="0c387-132">It is an example of a binary classification model type.</span></span>

<span data-ttu-id="0c387-133">Senaryonuz iki kategoriye sınıflandırma gerektiriyorsa, bu şablonu kendi veri kümeniz ile birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0c387-133">If your scenario requires classification into two categories, you can use this template with your own dataset.</span></span>

#### <a name="predict-a-category-when-there-are-three-or-more-categories"></a><span data-ttu-id="0c387-134">Kategori tahmin etme (üç veya daha fazla kategori olduğunda)</span><span class="sxs-lookup"><span data-stu-id="0c387-134">Predict a category (when there are three or more categories)</span></span>

<span data-ttu-id="0c387-135">Birden çok Lass sınıflandırması, verileri üç veya daha fazla sınıfa kategorize etmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0c387-135">Multiclass classification can be used to categorize data into three or more classes.</span></span>

![Belge ve ürün sınıflandırması, destek bileti yönlendirmesi ve müşteri sorunu önceliklendirmesi dahil birden çok Lass sınıflandırması örnekleri](media/multiclass-classification-examples.png)

<span data-ttu-id="0c387-137">Sorun sınıflandırması, sorun başlığı ve açıklaması kullanılarak müşteri geri bildirimini (örneğin, GitHub 'da) kategorilere ayırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0c387-137">Issue classification can be used to categorize customer feedback (for example, on GitHub) issues using the issue title and description.</span></span> <span data-ttu-id="0c387-138">Bu, çok sınıflı sınıflandırma modeli türüne bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="0c387-138">It is an example of the multi-class classification model type.</span></span>

<span data-ttu-id="0c387-139">Verileri üç veya daha fazla kategoride sınıflandırmak istiyorsanız senaryonuz için sorun sınıflandırması şablonunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0c387-139">You can use the issue classification template for your scenario if you want to categorize data into three or more categories.</span></span>

#### <a name="predict-a-number"></a><span data-ttu-id="0c387-140">Bir sayı tahmin edin</span><span class="sxs-lookup"><span data-stu-id="0c387-140">Predict a number</span></span>

<span data-ttu-id="0c387-141">Regresyon, sayıları tahmin etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0c387-141">Regression is used to predict numbers.</span></span>

![Fiyat tahmini, satış tahmini ve tahmine dayalı bakım gibi gerileme örneklerini gösteren diyagram](media/regression-examples.png)

<span data-ttu-id="0c387-143">Fiyat tahmini, evin konum, boyut ve diğer özelliklerini kullanarak ev fiyatlarını tahmin etmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0c387-143">Price prediction can be used to predict house prices using location, size, and other characteristics of the house.</span></span> <span data-ttu-id="0c387-144">Regresyon modeli türüne bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="0c387-144">It is an example of a regression model type.</span></span>

<span data-ttu-id="0c387-145">Kendi veri kümeniz ile sayısal bir değer tahmin etmek istiyorsanız senaryonuz için fiyat tahmini şablonunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0c387-145">You can use the price prediction template for your scenario if you want to predict a numerical value with your own dataset.</span></span>

#### <a name="custom-scenario-choose-your-model-type"></a><span data-ttu-id="0c387-146">Özel senaryo (model türünü seçin)</span><span class="sxs-lookup"><span data-stu-id="0c387-146">Custom scenario (choose your model type)</span></span>

<span data-ttu-id="0c387-147">Özel senaryo, model türünü el ile seçmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="0c387-147">The custom scenario allows you to manually choose your model type.</span></span>

## <a name="data"></a><span data-ttu-id="0c387-148">Veri</span><span class="sxs-lookup"><span data-stu-id="0c387-148">Data</span></span>

<span data-ttu-id="0c387-149">Model türünü seçtikten sonra model Oluşturucu sizden bir veri kümesi sağlamanızı ister.</span><span class="sxs-lookup"><span data-stu-id="0c387-149">Once you have chosen your model type, Model Builder asks you to provide a dataset.</span></span> <span data-ttu-id="0c387-150">Veriler, senaryonuza yönelik en iyi modeli eğlendirmek, değerlendirmek ve seçmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0c387-150">The data is used to train, evaluate, and choose the best model for your scenario.</span></span>

![Model Oluşturucu adımlarını gösteren diyagram](media/model-builder-steps.png)

### <a name="choose-the-output-to-predict-label"></a><span data-ttu-id="0c387-152">Tahmin edilecek çıktıyı seçin (etiket)</span><span class="sxs-lookup"><span data-stu-id="0c387-152">Choose the output to predict (label)</span></span>

<span data-ttu-id="0c387-153">Veri kümesi, eğitim örneklerinden ve özniteliklerin sütunlarından oluşan bir tablodur.</span><span class="sxs-lookup"><span data-stu-id="0c387-153">A dataset is a table of rows of training examples, and columns of attributes.</span></span> <span data-ttu-id="0c387-154">Her satır şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="0c387-154">Each row has:</span></span>

- <span data-ttu-id="0c387-155">bir **etiket** (tahmin etmek istediğiniz öznitelik)</span><span class="sxs-lookup"><span data-stu-id="0c387-155">a **label** (the attribute that you want to predict)</span></span>
- <span data-ttu-id="0c387-156">**Özellikler** (etiketi tahmin etmek için giriş olarak kullanılan öznitelikler).</span><span class="sxs-lookup"><span data-stu-id="0c387-156">**features** (attributes that are used as inputs to predict the label).</span></span>

<span data-ttu-id="0c387-157">Ev fiyat tahmini senaryosu için özellikler şu şekilde olabilir:</span><span class="sxs-lookup"><span data-stu-id="0c387-157">For the house-price prediction scenario, the features could be:</span></span>

- <span data-ttu-id="0c387-158">Evin kare çekimi</span><span class="sxs-lookup"><span data-stu-id="0c387-158">the square footage of the house</span></span>
- <span data-ttu-id="0c387-159">yatak odaları ve külikler sayısı</span><span class="sxs-lookup"><span data-stu-id="0c387-159">the number of bedrooms and bathrooms</span></span>
- <span data-ttu-id="0c387-160">posta kodu</span><span class="sxs-lookup"><span data-stu-id="0c387-160">the zip code</span></span>

<span data-ttu-id="0c387-161">Etiket, bu kare çekimi, yatak odası ve banyo değerleri ve posta kodu satırı için geçmiş bir evin fiyatıdır.</span><span class="sxs-lookup"><span data-stu-id="0c387-161">The label is the historical house price for that row of square footage, bedroom, and bathroom values and zip code.</span></span>

![Boyut Odalar ZIP kodu ve fiyat etiketinden oluşan özelliklerle birlikte, ev fiyatı verilerinin satırlarını ve sütunlarını gösteren tablo](media/model-builder-data.png)

### <a name="example-datasets"></a><span data-ttu-id="0c387-163">Örnek veri kümeleri</span><span class="sxs-lookup"><span data-stu-id="0c387-163">Example datasets</span></span>

<span data-ttu-id="0c387-164">Henüz kendi verileriniz yoksa, bu veri kümelerinden birini deneyin:</span><span class="sxs-lookup"><span data-stu-id="0c387-164">If you don't have your own data yet, try out one of these datasets:</span></span>

|<span data-ttu-id="0c387-165">Senaryo</span><span class="sxs-lookup"><span data-stu-id="0c387-165">Scenario</span></span>|<span data-ttu-id="0c387-166">Model türü</span><span class="sxs-lookup"><span data-stu-id="0c387-166">Model Type</span></span>|<span data-ttu-id="0c387-167">Veri</span><span class="sxs-lookup"><span data-stu-id="0c387-167">Data</span></span>|<span data-ttu-id="0c387-168">Etiketle</span><span class="sxs-lookup"><span data-stu-id="0c387-168">Label</span></span>|<span data-ttu-id="0c387-169">Özellikler</span><span class="sxs-lookup"><span data-stu-id="0c387-169">Features</span></span>|
|-|-|-|-|-|
|<span data-ttu-id="0c387-170">Fiyat tahmini</span><span class="sxs-lookup"><span data-stu-id="0c387-170">Price prediction</span></span>|<span data-ttu-id="0c387-171">regresyon</span><span class="sxs-lookup"><span data-stu-id="0c387-171">regression</span></span>|[<span data-ttu-id="0c387-172">taxı tarifeli havayolu verileri</span><span class="sxs-lookup"><span data-stu-id="0c387-172">taxi fare data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|<span data-ttu-id="0c387-173">Tarifeli havayolu</span><span class="sxs-lookup"><span data-stu-id="0c387-173">Fare</span></span>|<span data-ttu-id="0c387-174">Seyahat süresi, uzaklık</span><span class="sxs-lookup"><span data-stu-id="0c387-174">Trip time, distance</span></span>|
|<span data-ttu-id="0c387-175">Anomali algılama</span><span class="sxs-lookup"><span data-stu-id="0c387-175">Anomaly detection</span></span>|<span data-ttu-id="0c387-176">ikili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="0c387-176">binary classification</span></span>|[<span data-ttu-id="0c387-177">ürün satış verileri</span><span class="sxs-lookup"><span data-stu-id="0c387-177">product sales data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|<span data-ttu-id="0c387-178">Ürün satışları</span><span class="sxs-lookup"><span data-stu-id="0c387-178">Product Sales</span></span>|<span data-ttu-id="0c387-179">Başından</span><span class="sxs-lookup"><span data-stu-id="0c387-179">Month</span></span>|
|<span data-ttu-id="0c387-180">Yaklaşım Analizi</span><span class="sxs-lookup"><span data-stu-id="0c387-180">Sentiment analysis</span></span>|<span data-ttu-id="0c387-181">ikili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="0c387-181">binary classification</span></span>|[<span data-ttu-id="0c387-182">Web sitesi açıklama verileri</span><span class="sxs-lookup"><span data-stu-id="0c387-182">website comment data</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|<span data-ttu-id="0c387-183">Etiket (negatif yaklaşım olduğunda 0, pozitif olduğunda 1)</span><span class="sxs-lookup"><span data-stu-id="0c387-183">Label (0 when negative sentiment, 1 when positive)</span></span>|<span data-ttu-id="0c387-184">Açıklama, yıl</span><span class="sxs-lookup"><span data-stu-id="0c387-184">Comment, Year</span></span>|
|<span data-ttu-id="0c387-185">Sahtekarlık algılama</span><span class="sxs-lookup"><span data-stu-id="0c387-185">Fraud detection</span></span>|<span data-ttu-id="0c387-186">ikili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="0c387-186">binary classification</span></span>|[<span data-ttu-id="0c387-187">kredi kartı verileri</span><span class="sxs-lookup"><span data-stu-id="0c387-187">credit card data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|<span data-ttu-id="0c387-188">Sınıf (sahte olduğunda 1, aksi durumda 0)</span><span class="sxs-lookup"><span data-stu-id="0c387-188">Class (1 when fraudulent, 0 otherwise)</span></span>|<span data-ttu-id="0c387-189">Miktar, v1-V28 (anonimleştirilmiş Özellikler)</span><span class="sxs-lookup"><span data-stu-id="0c387-189">Amount, V1-V28 (anonymized features)</span></span>|
|<span data-ttu-id="0c387-190">Metin sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="0c387-190">Text classification</span></span>|<span data-ttu-id="0c387-191">birden çok Lass sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="0c387-191">multiclass classification</span></span>|[<span data-ttu-id="0c387-192">GitHub sorun verileri</span><span class="sxs-lookup"><span data-stu-id="0c387-192">GitHub issue data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|<span data-ttu-id="0c387-193">Alan</span><span class="sxs-lookup"><span data-stu-id="0c387-193">Area</span></span>|<span data-ttu-id="0c387-194">Başlık, açıklama</span><span class="sxs-lookup"><span data-stu-id="0c387-194">Title, Description</span></span>|

## <a name="train"></a><span data-ttu-id="0c387-195">eğit</span><span class="sxs-lookup"><span data-stu-id="0c387-195">Train</span></span>

<span data-ttu-id="0c387-196">Senaryonuzu, verilerinizi ve etiketini seçtikten sonra model Oluşturucu modeli izleyin.</span><span class="sxs-lookup"><span data-stu-id="0c387-196">Once you select your scenario, data, and label, Model Builder trains the model.</span></span>

### <a name="what-is-training"></a><span data-ttu-id="0c387-197">Eğitim nedir?</span><span class="sxs-lookup"><span data-stu-id="0c387-197">What is training?</span></span>

<span data-ttu-id="0c387-198">Eğitim, model Oluşturucu 'nun, senaryonuza yönelik soruların nasıl yanıtlanarak modelinizi öğretirken otomatik bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="0c387-198">Training is an automatic process by which Model Builder teaches your model how to answer questions for your scenario.</span></span> <span data-ttu-id="0c387-199">Eğittikten sonra modelinize, daha önce görmemiş olan giriş verileriyle ilgili tahmin yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="0c387-199">Once trained, your model can make predictions with input data that it has not seen before.</span></span> <span data-ttu-id="0c387-200">Örneğin, ev fiyatlarını tahmin ediyorsanız ve pazara yeni bir ev geliyorsa, satış fiyatını tahmin edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0c387-200">For example, if you are predicting house prices and a new house comes on the market, you can predict its sale price.</span></span>

<span data-ttu-id="0c387-201">Model Oluşturucu otomatik makine öğrenimi (Otomatikml) kullandığından, eğitim sırasında sizin için herhangi bir giriş veya ayarlama gerekmez.</span><span class="sxs-lookup"><span data-stu-id="0c387-201">Because Model Builder uses automated machine learning (AutoML), it does not require any input or tuning from you during training.</span></span>

## <a name="evaluate"></a><span data-ttu-id="0c387-202">Değerlendirmesini</span><span class="sxs-lookup"><span data-stu-id="0c387-202">Evaluate</span></span>

<span data-ttu-id="0c387-203">Değerlendirme, eğitilen modeli kullanarak yeni test verileriyle tahminleri yapabilir ve daha sonra tahmine göre ne kadar iyi olduğunu ölçmeye yönelik bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="0c387-203">Evaluation is the process of using the trained model to make predictions with new test data, and then measuring how good the predictions are.</span></span>

<span data-ttu-id="0c387-204">Model Oluşturucu eğitim verilerini bir eğitim kümesine ve bir test kümesine böler.</span><span class="sxs-lookup"><span data-stu-id="0c387-204">Model Builder splits the training data into a training set and a test set.</span></span> <span data-ttu-id="0c387-205">Eğitim verileri (%80) modelinizi ve test verilerini eğiteetmek için kullanılır (%20) , modelinizi değerlendirmek için geri tutulur.</span><span class="sxs-lookup"><span data-stu-id="0c387-205">The training data (80%) is used to train your model and the test data (20%) is held back to evaluate your model.</span></span> <span data-ttu-id="0c387-206">Model Oluşturucu, modelin ne kadar iyi olduğunu ölçmek için ölçümleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="0c387-206">Model Builder uses metrics to measure how good the model is.</span></span> <span data-ttu-id="0c387-207">Kullanılan belirli ölçümler modelin türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0c387-207">The specific metrics used are dependent on the type of model.</span></span> <span data-ttu-id="0c387-208">Daha fazla bilgi için bkz. [model değerlendirme ölçümleri](resources/metrics.md).</span><span class="sxs-lookup"><span data-stu-id="0c387-208">For more information, see [model evaluation metrics](resources/metrics.md).</span></span>

## <a name="improve"></a><span data-ttu-id="0c387-209">Enizi</span><span class="sxs-lookup"><span data-stu-id="0c387-209">Improve</span></span>

<span data-ttu-id="0c387-210">Model performans puanınız istediğiniz kadar iyi değilse şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0c387-210">If your model performance score is not as good as you want it to be, you can:</span></span>

- <span data-ttu-id="0c387-211">Daha uzun bir süre için eğitme.</span><span class="sxs-lookup"><span data-stu-id="0c387-211">Train for a longer period of time.</span></span> <span data-ttu-id="0c387-212">Daha fazla zaman, daha fazla algoritma ve ayar denemek için otomatik makine öğrenimi altyapısı.</span><span class="sxs-lookup"><span data-stu-id="0c387-212">With more time, the automated machine learning engine to try more algorithms and settings.</span></span>

- <span data-ttu-id="0c387-213">Daha fazla veri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0c387-213">Add more data.</span></span> <span data-ttu-id="0c387-214">Bazen veri miktarı yüksek kaliteli bir makine öğrenimi modelini eğitmek için yeterli değildir.</span><span class="sxs-lookup"><span data-stu-id="0c387-214">Sometimes the amount of data is not sufficient to train a high-quality machine learning model.</span></span>

- <span data-ttu-id="0c387-215">Verilerinizi dengeleyin.</span><span class="sxs-lookup"><span data-stu-id="0c387-215">Balance your data.</span></span> <span data-ttu-id="0c387-216">Sınıflandırma görevleri için, eğitim kümesinin Kategoriler genelinde dengeli olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="0c387-216">For classification tasks, make sure that the training set is balanced across the categories.</span></span> <span data-ttu-id="0c387-217">Örneğin, 100 eğitim örnekleri için dört sınıfınız varsa ve bu iki sınıf (etiket1 ve etiket2), 90 kayıt için kullanılırsa, ancak diğer iki (etiket3 ve TAG4) yalnızca kalan 10 kayıtta kullanılıyorsa, dengeli verilerin bulunmaması modelinizin eksikliğine zarar verebilir etiket3 veya TAG4 ' i tahmin edin.</span><span class="sxs-lookup"><span data-stu-id="0c387-217">For example, if you have four classes for 100 training examples, and the two first classes (tag1 and tag2) are used for 90 records, but the other two (tag3 and tag4) are only used on the remaining 10 records, the lack of balanced data may cause your model to struggle to correctly predict tag3 or tag4.</span></span>

## <a name="code"></a><span data-ttu-id="0c387-218">Kod</span><span class="sxs-lookup"><span data-stu-id="0c387-218">Code</span></span>

<span data-ttu-id="0c387-219">Değerlendirme aşamasından sonra, model Oluşturucu bir model dosyası ve uygulamayı uygulamanıza eklemek için kullanabileceğiniz kodu verir.</span><span class="sxs-lookup"><span data-stu-id="0c387-219">After the evaluation phase, Model Builder outputs a model file, and code that you can use to add the model to your application.</span></span> <span data-ttu-id="0c387-220">ML.NET modelleri bir ZIP dosyası olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="0c387-220">ML.NET models are saved as a zip file.</span></span> <span data-ttu-id="0c387-221">Modelinize yüklenecek ve kullanılacak kod, çözümünüze yeni bir proje olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="0c387-221">The code to load and use your model is added as a new project in your solution.</span></span> <span data-ttu-id="0c387-222">Model Oluşturucu Ayrıca, modelinizi işlem içinde görmek için çalıştırabileceğiniz bir örnek konsol uygulaması da ekler.</span><span class="sxs-lookup"><span data-stu-id="0c387-222">Model Builder also adds a sample console app that you can run to see your model in action.</span></span>

<span data-ttu-id="0c387-223">Ayrıca model Oluşturucu, modeli oluşturmak için kullanılan adımları anlayabilmeniz için modeli oluşturan kodu çıktı.</span><span class="sxs-lookup"><span data-stu-id="0c387-223">In addition, Model Builder outputs the code that generated the model, so that you can understand the steps used to generate the model.</span></span> <span data-ttu-id="0c387-224">Modelinize yeni verilerle yeniden eğitebilmeniz için model eğitim kodunu da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0c387-224">You can also use the model training code to retrain your model with new data.</span></span>

## <a name="whats-next"></a><span data-ttu-id="0c387-225">Sırada ne var?</span><span class="sxs-lookup"><span data-stu-id="0c387-225">What's next?</span></span>

<span data-ttu-id="0c387-226">Model Oluşturucu Visual Studio uzantısını [yükler](how-to-guides/install-model-builder.md)</span><span class="sxs-lookup"><span data-stu-id="0c387-226">[Install](how-to-guides/install-model-builder.md) the Model Builder Visual Studio extension</span></span>

<span data-ttu-id="0c387-227">[Fiyat tahmini veya herhangi bir gerileme senaryosu](tutorials/predict-prices-with-model-builder.md) deneyin</span><span class="sxs-lookup"><span data-stu-id="0c387-227">Try [price prediction or any regression scenario](tutorials/predict-prices-with-model-builder.md)</span></span>
