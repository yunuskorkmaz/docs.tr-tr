---
title: Model Oluşturucu nedir ve nasıl çalışır?
description: Makine öğrenimi modelini otomatik olarak eğiteiçin ML.NET model Oluşturucu 'Yu kullanma
ms.date: 01/07/2020
ms.custom: overview
ms.openlocfilehash: ac704b7961a8442a9174cdef5a4cd2a619236a4e
ms.sourcegitcommit: cbdc0f4fd39172b5191a35200c33d5030774463c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777400"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a><span data-ttu-id="bbaf0-103">Model Oluşturucu nedir ve nasıl çalışır?</span><span class="sxs-lookup"><span data-stu-id="bbaf0-103">What is Model Builder and how does it work?</span></span>

<span data-ttu-id="bbaf0-104">ML.NET model Oluşturucu, özel makine öğrenimi modellerini derlemek, eğitme ve dağıtmaya yönelik sezgisel bir grafik Visual Studio uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-104">ML.NET Model Builder is an intuitive graphical Visual Studio extension to build, train, and deploy custom machine learning models.</span></span>

<span data-ttu-id="bbaf0-105">Model Oluşturucu, senaryonuza en uygun olanı bulmanıza yardımcı olmak üzere farklı makine öğrenimi algoritmalarını ve ayarlarını araştırmak için otomatik makine öğrenimi (Otomatikml) kullanır.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-105">Model Builder uses automated machine learning (AutoML) to explore different machine learning algorithms and settings to help you find the one that best suits your scenario.</span></span>

<span data-ttu-id="bbaf0-106">Model Oluşturucuyu kullanmak için Machine Learning uzmanlığına ihtiyacınız yoktur.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-106">You don't need machine learning expertise to use Model Builder.</span></span> <span data-ttu-id="bbaf0-107">Bazı veriler ve çözübir sorun var.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-107">All you need is some data, and a problem to solve.</span></span> <span data-ttu-id="bbaf0-108">Model Oluşturucu, modeli .NET uygulamanıza eklemek için kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-108">Model Builder generates the code to add the model to your .NET application.</span></span>

![Model Oluşturucu Visual Studio uzantısı kullanıcı arabirimi animasyonu](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> <span data-ttu-id="bbaf0-110">Model Oluşturucu Şu anda önizleme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-110">Model Builder is currently in Preview.</span></span>

## <a name="scenarios"></a><span data-ttu-id="bbaf0-111">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="bbaf0-111">Scenarios</span></span>

<span data-ttu-id="bbaf0-112">Uygulamanız için bir makine öğrenimi modeli oluşturmak için model Oluşturucu 'ya birçok farklı senaryo getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-112">You can bring many different scenarios to Model Builder, to generate a machine learning model for your application.</span></span>

<span data-ttu-id="bbaf0-113">Senaryo, verilerinizi kullanarak yapmak istediğiniz tahmin türünün bir açıklamasıdır.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-113">A scenario is a description of the type of prediction you want to make using your data.</span></span> <span data-ttu-id="bbaf0-114">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="bbaf0-114">For example:</span></span>

- <span data-ttu-id="bbaf0-115">geçmiş satış verilerine göre gelecek ürün satış hacmini tahmin edin</span><span class="sxs-lookup"><span data-stu-id="bbaf0-115">predict future product sales volume based on historical sales data</span></span>
- <span data-ttu-id="bbaf0-116">müşterilerin gözden geçirmeleri temelinde olumlu veya olumsuz şekilde sınıflandırın</span><span class="sxs-lookup"><span data-stu-id="bbaf0-116">classify sentiments as positive or negative based on customer reviews</span></span>
- <span data-ttu-id="bbaf0-117">Bankacılık işleminin sahte olup olmadığını Algıla</span><span class="sxs-lookup"><span data-stu-id="bbaf0-117">detect whether a banking transaction is fraudulent</span></span>
- <span data-ttu-id="bbaf0-118">Müşteri geri bildirim sorunlarını şirketinizdeki doğru ekibe yönlendirin</span><span class="sxs-lookup"><span data-stu-id="bbaf0-118">route customer feedback issues to the correct team in your company</span></span>

### <a name="which-machine-learning-scenario-is-right-for-me"></a><span data-ttu-id="bbaf0-119">Hangi makine öğrenimi senaryosu bana uygun?</span><span class="sxs-lookup"><span data-stu-id="bbaf0-119">Which machine learning scenario is right for me?</span></span>

<span data-ttu-id="bbaf0-120">Model Oluşturucu 'da bir senaryo seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-120">In Model Builder, you need to select a scenario.</span></span> <span data-ttu-id="bbaf0-121">Senaryonun türü, yapmaya çalıştığınız tahmin türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-121">The type of scenario depends on what type of prediction you are trying to make.</span></span>

#### <a name="predict-a-category-when-there-are-only-two-categories"></a><span data-ttu-id="bbaf0-122">Kategori tahmin etme (yalnızca iki kategori olduğunda)</span><span class="sxs-lookup"><span data-stu-id="bbaf0-122">Predict a category (when there are only two categories)</span></span>

<span data-ttu-id="bbaf0-123">İkili sınıflandırma, verileri iki kategoride kategorilere ayırmak için kullanılır (Evet/Hayır; geçti/başarısız; true/false; pozitif/negatif).</span><span class="sxs-lookup"><span data-stu-id="bbaf0-123">Binary classification is used to categorize data into two categories (yes/no; pass/fail; true/false; positive/negative).</span></span>

![Sahtekarlık algılama, risk azaltma ve uygulama filtreleme dahil olmak üzere ikili sınıflandırma örneklerini gösteren diyagram](media/binary-classification-examples.png)

<span data-ttu-id="bbaf0-125">Yaklaşım analizi, müşteri geri bildirimlerine yönelik olumlu veya olumsuz yaklaşımı tahmin etmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-125">Sentiment analysis can be used to predict positive or negative sentiment of customer feedback.</span></span> <span data-ttu-id="bbaf0-126">Bu, ikili sınıflandırma makinesi öğrenimi görevinin bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-126">It is an example of the binary classification machine learning task.</span></span>

<span data-ttu-id="bbaf0-127">Senaryonuz iki kategoriye sınıflandırma gerektiriyorsa, bu şablonu kendi veri kümeniz ile birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-127">If your scenario requires classification into two categories, you can use this template with your own dataset.</span></span>

#### <a name="predict-a-category-when-there-are-three-or-more-categories"></a><span data-ttu-id="bbaf0-128">Kategori tahmin etme (üç veya daha fazla kategori olduğunda)</span><span class="sxs-lookup"><span data-stu-id="bbaf0-128">Predict a category (when there are three or more categories)</span></span>

<span data-ttu-id="bbaf0-129">Birden çok Lass sınıflandırması, verileri üç veya daha fazla sınıfa kategorize etmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-129">Multiclass classification can be used to categorize data into three or more classes.</span></span>

![Belge ve ürün sınıflandırması, destek bileti yönlendirmesi ve müşteri sorunu önceliklendirmesi dahil birden çok Lass sınıflandırması örnekleri](media/multiclass-classification-examples.png)

<span data-ttu-id="bbaf0-131">Sorun sınıflandırması, sorun başlığı ve açıklaması kullanılarak müşteri geri bildirimini (örneğin, GitHub 'da) kategorilere ayırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-131">Issue classification can be used to categorize customer feedback (for example, on GitHub) issues using the issue title and description.</span></span> <span data-ttu-id="bbaf0-132">Bu, çok sınıflı sınıflandırma makinesi öğrenimi görevinin bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-132">It is an example of the multi-class classification machine learning task.</span></span>

<span data-ttu-id="bbaf0-133">Verileri üç veya daha fazla kategoride sınıflandırmak istiyorsanız senaryonuz için sorun sınıflandırması şablonunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-133">You can use the issue classification template for your scenario if you want to categorize data into three or more categories.</span></span>

#### <a name="predict-a-number"></a><span data-ttu-id="bbaf0-134">Bir sayı tahmin edin</span><span class="sxs-lookup"><span data-stu-id="bbaf0-134">Predict a number</span></span>

<span data-ttu-id="bbaf0-135">Regresyon, sayıları tahmin etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-135">Regression is used to predict numbers.</span></span>

![Fiyat tahmini, satış tahmini ve tahmine dayalı bakım gibi gerileme örneklerini gösteren diyagram](media/regression-examples.png)

<span data-ttu-id="bbaf0-137">Fiyat tahmini, evin konum, boyut ve diğer özelliklerini kullanarak ev fiyatlarını tahmin etmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-137">Price prediction can be used to predict house prices using location, size, and other characteristics of the house.</span></span> <span data-ttu-id="bbaf0-138">Gerileme makine öğrenimi görevi örneğidir.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-138">It is an example of the regression machine learning task.</span></span>

<span data-ttu-id="bbaf0-139">Kendi veri kümeniz ile sayısal bir değer tahmin etmek istiyorsanız senaryonuz için fiyat tahmini şablonunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-139">You can use the price prediction template for your scenario if you want to predict a numerical value with your own dataset.</span></span>

#### <a name="classify-images-into-categories"></a><span data-ttu-id="bbaf0-140">Görüntüleri kategoriler halinde sınıflandır</span><span class="sxs-lookup"><span data-stu-id="bbaf0-140">Classify images into categories</span></span>

<span data-ttu-id="bbaf0-141">Bu senaryo, kategorize edilecek giriş verilerinin bir görüntü kümesi olduğu birden çok Lass sınıflandırmasının özel bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-141">This scenario is a special case of multiclass classification, where the input data to be categorized is a set of images.</span></span>

<span data-ttu-id="bbaf0-142">Görüntü sınıflandırması, farklı kategorilerin görüntülerini belirlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-142">Image classification can be used to identify images of different categories.</span></span> <span data-ttu-id="bbaf0-143">Örneğin, farklı türlerde terur veya hayvanlar veya üretim kusurları vardır.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-143">For example, different types of terrain or animals or manufacturing defects.</span></span>

<span data-ttu-id="bbaf0-144">Bir görüntü kümesine sahipseniz ve görüntüleri farklı kategorilerde sınıflandırmak istiyorsanız senaryonuz için görüntü sınıflandırması şablonunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-144">You can use the image classification template for your scenario if you have a set of images, and you want to classify the images into different categories.</span></span>

#### <a name="custom-scenario"></a><span data-ttu-id="bbaf0-145">Özel senaryo</span><span class="sxs-lookup"><span data-stu-id="bbaf0-145">Custom scenario</span></span>

<span data-ttu-id="bbaf0-146">Özel senaryo, senaryonuzu el ile seçmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-146">The custom scenario allows you to manually choose your scenario.</span></span>

## <a name="data"></a><span data-ttu-id="bbaf0-147">Veri</span><span class="sxs-lookup"><span data-stu-id="bbaf0-147">Data</span></span>

<span data-ttu-id="bbaf0-148">Senaryonuzu seçtikten sonra model Oluşturucu sizden bir veri kümesi sağlamanızı ister.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-148">Once you have chosen your scenario, Model Builder asks you to provide a dataset.</span></span> <span data-ttu-id="bbaf0-149">Veriler, senaryonuza yönelik en iyi modeli eğlendirmek, değerlendirmek ve seçmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-149">The data is used to train, evaluate, and choose the best model for your scenario.</span></span>

![Model Oluşturucu adımlarını gösteren diyagram](media/model-builder-steps.png)

<span data-ttu-id="bbaf0-151">Model Oluşturucu,. tsv,. csv,. txt biçimlerinin yanı sıra SQL veritabanı biçiminde veri kümelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-151">Model Builder supports datasets in .tsv, .csv, .txt formats, as well as SQL database format.</span></span> <span data-ttu-id="bbaf0-152">. Txt dosyanız varsa, sütunların `,`, `;` veya `/t` ile ayrılması ve dosyanın bir başlık satırı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-152">If you have a .txt file, columns should be separated with `,`, `;` or `/t` and the file must have a header row.</span></span>

<span data-ttu-id="bbaf0-153">Veri kümesi görüntülerden birini yapılırsa, desteklenen dosya türleri `.jpg` ve `.png`.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-153">If the dataset is made up of images, the supported file types are `.jpg` and `.png`.</span></span>

<span data-ttu-id="bbaf0-154">Daha fazla bilgi için bkz. [model Oluşturucu 'da eğitim verilerini yükleme](how-to-guides/load-data-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="bbaf0-154">For more information, see [Load training data into Model Builder](how-to-guides/load-data-model-builder.md).</span></span>

### <a name="choose-the-output-to-predict-label"></a><span data-ttu-id="bbaf0-155">Tahmin edilecek çıktıyı seçin (etiket)</span><span class="sxs-lookup"><span data-stu-id="bbaf0-155">Choose the output to predict (label)</span></span>

<span data-ttu-id="bbaf0-156">Veri kümesi, eğitim örneklerinden ve özniteliklerin sütunlarından oluşan bir tablodur.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-156">A dataset is a table of rows of training examples, and columns of attributes.</span></span> <span data-ttu-id="bbaf0-157">Her satır şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="bbaf0-157">Each row has:</span></span>

- <span data-ttu-id="bbaf0-158">bir **etiket** (tahmin etmek istediğiniz öznitelik)</span><span class="sxs-lookup"><span data-stu-id="bbaf0-158">a **label** (the attribute that you want to predict)</span></span>
- <span data-ttu-id="bbaf0-159">**Özellikler** (etiketi tahmin etmek için giriş olarak kullanılan öznitelikler).</span><span class="sxs-lookup"><span data-stu-id="bbaf0-159">**features** (attributes that are used as inputs to predict the label).</span></span>

<span data-ttu-id="bbaf0-160">Ev fiyat tahmini senaryosu için özellikler şu şekilde olabilir:</span><span class="sxs-lookup"><span data-stu-id="bbaf0-160">For the house-price prediction scenario, the features could be:</span></span>

- <span data-ttu-id="bbaf0-161">Evin kare çekimi</span><span class="sxs-lookup"><span data-stu-id="bbaf0-161">the square footage of the house</span></span>
- <span data-ttu-id="bbaf0-162">yatak odaları ve külikler sayısı</span><span class="sxs-lookup"><span data-stu-id="bbaf0-162">the number of bedrooms and bathrooms</span></span>
- <span data-ttu-id="bbaf0-163">posta kodu</span><span class="sxs-lookup"><span data-stu-id="bbaf0-163">the zip code</span></span>

<span data-ttu-id="bbaf0-164">Etiket, bu kare çekimi, yatak odası ve banyo değerleri ve posta kodu satırı için geçmiş bir evin fiyatıdır.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-164">The label is the historical house price for that row of square footage, bedroom, and bathroom values and zip code.</span></span>

![Boyut Odalar ZIP kodu ve fiyat etiketinden oluşan özelliklerle birlikte, ev fiyatı verilerinin satırlarını ve sütunlarını gösteren tablo](media/model-builder-data.png)

### <a name="example-datasets"></a><span data-ttu-id="bbaf0-166">Örnek veri kümeleri</span><span class="sxs-lookup"><span data-stu-id="bbaf0-166">Example datasets</span></span>

<span data-ttu-id="bbaf0-167">Henüz kendi verileriniz yoksa, bu veri kümelerinden birini deneyin:</span><span class="sxs-lookup"><span data-stu-id="bbaf0-167">If you don't have your own data yet, try out one of these datasets:</span></span>

|<span data-ttu-id="bbaf0-168">Senaryo</span><span class="sxs-lookup"><span data-stu-id="bbaf0-168">Scenario</span></span>|<span data-ttu-id="bbaf0-169">ML görevi</span><span class="sxs-lookup"><span data-stu-id="bbaf0-169">ML task</span></span>|<span data-ttu-id="bbaf0-170">Veri</span><span class="sxs-lookup"><span data-stu-id="bbaf0-170">Data</span></span>|<span data-ttu-id="bbaf0-171">Etiketle</span><span class="sxs-lookup"><span data-stu-id="bbaf0-171">Label</span></span>|<span data-ttu-id="bbaf0-172">Özellikler</span><span class="sxs-lookup"><span data-stu-id="bbaf0-172">Features</span></span>|
|-|-|-|-|-|
|<span data-ttu-id="bbaf0-173">Fiyat tahmini</span><span class="sxs-lookup"><span data-stu-id="bbaf0-173">Price prediction</span></span>|<span data-ttu-id="bbaf0-174">regresyon</span><span class="sxs-lookup"><span data-stu-id="bbaf0-174">regression</span></span>|[<span data-ttu-id="bbaf0-175">taxı tarifeli havayolu verileri</span><span class="sxs-lookup"><span data-stu-id="bbaf0-175">taxi fare data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|<span data-ttu-id="bbaf0-176">Tarifeli havayolu</span><span class="sxs-lookup"><span data-stu-id="bbaf0-176">Fare</span></span>|<span data-ttu-id="bbaf0-177">Seyahat süresi, uzaklık</span><span class="sxs-lookup"><span data-stu-id="bbaf0-177">Trip time, distance</span></span>|
|<span data-ttu-id="bbaf0-178">Anomali algılama</span><span class="sxs-lookup"><span data-stu-id="bbaf0-178">Anomaly detection</span></span>|<span data-ttu-id="bbaf0-179">ikili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="bbaf0-179">binary classification</span></span>|[<span data-ttu-id="bbaf0-180">ürün satış verileri</span><span class="sxs-lookup"><span data-stu-id="bbaf0-180">product sales data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|<span data-ttu-id="bbaf0-181">Ürün satışları</span><span class="sxs-lookup"><span data-stu-id="bbaf0-181">Product Sales</span></span>|<span data-ttu-id="bbaf0-182">Ay</span><span class="sxs-lookup"><span data-stu-id="bbaf0-182">Month</span></span>|
|<span data-ttu-id="bbaf0-183">Yaklaşım analizi</span><span class="sxs-lookup"><span data-stu-id="bbaf0-183">Sentiment analysis</span></span>|<span data-ttu-id="bbaf0-184">ikili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="bbaf0-184">binary classification</span></span>|[<span data-ttu-id="bbaf0-185">Web sitesi açıklama verileri</span><span class="sxs-lookup"><span data-stu-id="bbaf0-185">website comment data</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|<span data-ttu-id="bbaf0-186">Etiket (negatif yaklaşım olduğunda 0, pozitif olduğunda 1)</span><span class="sxs-lookup"><span data-stu-id="bbaf0-186">Label (0 when negative sentiment, 1 when positive)</span></span>|<span data-ttu-id="bbaf0-187">Açıklama, yıl</span><span class="sxs-lookup"><span data-stu-id="bbaf0-187">Comment, Year</span></span>|
|<span data-ttu-id="bbaf0-188">Sahtekarlık algılama</span><span class="sxs-lookup"><span data-stu-id="bbaf0-188">Fraud detection</span></span>|<span data-ttu-id="bbaf0-189">ikili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="bbaf0-189">binary classification</span></span>|[<span data-ttu-id="bbaf0-190">kredi kartı verileri</span><span class="sxs-lookup"><span data-stu-id="bbaf0-190">credit card data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|<span data-ttu-id="bbaf0-191">Sınıf (sahte olduğunda 1, aksi durumda 0)</span><span class="sxs-lookup"><span data-stu-id="bbaf0-191">Class (1 when fraudulent, 0 otherwise)</span></span>|<span data-ttu-id="bbaf0-192">Miktar, v1-V28 (anonimleştirilmiş Özellikler)</span><span class="sxs-lookup"><span data-stu-id="bbaf0-192">Amount, V1-V28 (anonymized features)</span></span>|
|<span data-ttu-id="bbaf0-193">Metin sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="bbaf0-193">Text classification</span></span>|<span data-ttu-id="bbaf0-194">birden çok Lass sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="bbaf0-194">multiclass classification</span></span>|[<span data-ttu-id="bbaf0-195">GitHub sorun verileri</span><span class="sxs-lookup"><span data-stu-id="bbaf0-195">GitHub issue data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|<span data-ttu-id="bbaf0-196">Alan</span><span class="sxs-lookup"><span data-stu-id="bbaf0-196">Area</span></span>|<span data-ttu-id="bbaf0-197">Başlık, açıklama</span><span class="sxs-lookup"><span data-stu-id="bbaf0-197">Title, Description</span></span>|
|<span data-ttu-id="bbaf0-198">Görüntü sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="bbaf0-198">Image classification</span></span>|<span data-ttu-id="bbaf0-199">birden çok Lass sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="bbaf0-199">multiclass classification</span></span>|[<span data-ttu-id="bbaf0-200">Çiçekler görüntüleri</span><span class="sxs-lookup"><span data-stu-id="bbaf0-200">Flowers images</span></span>](http://download.tensorflow.org/example_images/flower_photos.tgz)|<span data-ttu-id="bbaf0-201">Çiçek türü: da, Dandelion, Roses, sunçiçekler, TULIP 'ler</span><span class="sxs-lookup"><span data-stu-id="bbaf0-201">The type of flower: daisy, dandelion, roses, sunflowers, tulips</span></span>|<span data-ttu-id="bbaf0-202">Görüntü verilerinin kendisi</span><span class="sxs-lookup"><span data-stu-id="bbaf0-202">The image data itself</span></span>|

## <a name="train"></a><span data-ttu-id="bbaf0-203">Eğitim</span><span class="sxs-lookup"><span data-stu-id="bbaf0-203">Train</span></span>

<span data-ttu-id="bbaf0-204">Senaryonuzu, verilerinizi ve etiketini seçtikten sonra model Oluşturucu modeli izleyin.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-204">Once you select your scenario, data, and label, Model Builder trains the model.</span></span>

### <a name="what-is-training"></a><span data-ttu-id="bbaf0-205">Eğitim nedir?</span><span class="sxs-lookup"><span data-stu-id="bbaf0-205">What is training?</span></span>

<span data-ttu-id="bbaf0-206">Eğitim, model Oluşturucu 'nun, senaryonuza yönelik soruların nasıl yanıtlanarak modelinizi öğretirken otomatik bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-206">Training is an automatic process by which Model Builder teaches your model how to answer questions for your scenario.</span></span> <span data-ttu-id="bbaf0-207">Eğittikten sonra modelinize, daha önce görmemiş olan giriş verileriyle ilgili tahmin yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-207">Once trained, your model can make predictions with input data that it has not seen before.</span></span> <span data-ttu-id="bbaf0-208">Örneğin, ev fiyatlarını tahmin ediyorsanız ve pazara yeni bir ev geliyorsa, satış fiyatını tahmin edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-208">For example, if you are predicting house prices and a new house comes on the market, you can predict its sale price.</span></span>

<span data-ttu-id="bbaf0-209">Model Oluşturucu otomatik makine öğrenimi (Otomatikml) kullandığından, eğitim sırasında sizin için herhangi bir giriş veya ayarlama gerekmez.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-209">Because Model Builder uses automated machine learning (AutoML), it does not require any input or tuning from you during training.</span></span>

### <a name="how-long-should-i-train-for"></a><span data-ttu-id="bbaf0-210">Ne kadar eğitmem gerekir?</span><span class="sxs-lookup"><span data-stu-id="bbaf0-210">How long should I train for?</span></span>

<span data-ttu-id="bbaf0-211">Model Oluşturucu, sizi en iyi şekilde gerçekleştiren modeli bulmak için birden çok modeli araştırmak üzere oto ml kullanır.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-211">Model Builder uses AutoML to explore multiple models to find you the best performing model.</span></span>

<span data-ttu-id="bbaf0-212">Daha uzun eğitim dönemleri, oto ml 'nin daha geniş bir ayar aralığıyla daha fazla modeli keşfetmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-212">Longer training periods allow AutoML to explore more models with a wider range of settings.</span></span>

<span data-ttu-id="bbaf0-213">Aşağıdaki tabloda, yerel bir makinedeki bir örnek veri kümesi paketi için iyi performans sağlamak üzere harcanan ortalama süre özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-213">The table below summarizes the average time taken to get good performance for a suite of example datasets, on a local machine.</span></span>

|<span data-ttu-id="bbaf0-214">Veri kümesi boyutu</span><span class="sxs-lookup"><span data-stu-id="bbaf0-214">Dataset size</span></span>|<span data-ttu-id="bbaf0-215">Ortalama eğitim süresi</span><span class="sxs-lookup"><span data-stu-id="bbaf0-215">Average time to train</span></span>|
|------------|---------------------|
|<span data-ttu-id="bbaf0-216">0-10 MB</span><span class="sxs-lookup"><span data-stu-id="bbaf0-216">0 - 10 MB</span></span>|<span data-ttu-id="bbaf0-217">10 sn</span><span class="sxs-lookup"><span data-stu-id="bbaf0-217">10 sec</span></span>|
|<span data-ttu-id="bbaf0-218">10-100 MB</span><span class="sxs-lookup"><span data-stu-id="bbaf0-218">10 - 100 MB</span></span>|<span data-ttu-id="bbaf0-219">10 dakika</span><span class="sxs-lookup"><span data-stu-id="bbaf0-219">10 min</span></span>|
|<span data-ttu-id="bbaf0-220">100-500 MB</span><span class="sxs-lookup"><span data-stu-id="bbaf0-220">100 - 500 MB</span></span>|<span data-ttu-id="bbaf0-221">30 dakika</span><span class="sxs-lookup"><span data-stu-id="bbaf0-221">30 min</span></span>|
|<span data-ttu-id="bbaf0-222">500-1 GB</span><span class="sxs-lookup"><span data-stu-id="bbaf0-222">500 - 1 GB</span></span>|<span data-ttu-id="bbaf0-223">60 dk</span><span class="sxs-lookup"><span data-stu-id="bbaf0-223">60 min</span></span>|
|<span data-ttu-id="bbaf0-224">1 GB +</span><span class="sxs-lookup"><span data-stu-id="bbaf0-224">1 GB+</span></span>|<span data-ttu-id="bbaf0-225">3 + saat</span><span class="sxs-lookup"><span data-stu-id="bbaf0-225">3+ hours</span></span>|

<span data-ttu-id="bbaf0-226">Bu numaralar yalnızca bir kılavuzdur.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-226">These numbers are a guide only.</span></span> <span data-ttu-id="bbaf0-227">Eğitimin tam uzunluğu şu şekilde bağımlıdır:</span><span class="sxs-lookup"><span data-stu-id="bbaf0-227">The exact length of training is dependent on:</span></span>

- <span data-ttu-id="bbaf0-228">modele girdi olarak kullanılan özellik sayısı (sütun)</span><span class="sxs-lookup"><span data-stu-id="bbaf0-228">the number of features (columns) being used to as input to the model</span></span>
- <span data-ttu-id="bbaf0-229">sütun türü</span><span class="sxs-lookup"><span data-stu-id="bbaf0-229">the type of columns</span></span>
- <span data-ttu-id="bbaf0-230">ML görevi</span><span class="sxs-lookup"><span data-stu-id="bbaf0-230">the ML task</span></span>
- <span data-ttu-id="bbaf0-231">Eğitim için kullanılan makinenin CPU, disk ve bellek performansı</span><span class="sxs-lookup"><span data-stu-id="bbaf0-231">the CPU, disk and memory performance of the machine used for training</span></span>

## <a name="evaluate"></a><span data-ttu-id="bbaf0-232">'i Değerlendirme</span><span class="sxs-lookup"><span data-stu-id="bbaf0-232">Evaluate</span></span>

<span data-ttu-id="bbaf0-233">Değerlendirme, modelinizin ne kadar iyi olduğunu ölçmeye yönelik bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-233">Evaluation is the process of measuring how good your model is.</span></span> <span data-ttu-id="bbaf0-234">Model Oluşturucu, yeni test verileriyle tahmine dayalı hale getirmek için eğitilen modeli kullanır ve daha sonra tahminlerin ne kadar iyi olduğunu ölçer.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-234">Model Builder uses the trained model to make predictions with new test data, and then measures how good the predictions are.</span></span>

<span data-ttu-id="bbaf0-235">Model Oluşturucu eğitim verilerini bir eğitim kümesine ve bir test kümesine böler.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-235">Model Builder splits the training data into a training set and a test set.</span></span> <span data-ttu-id="bbaf0-236">Eğitim verileri (%80) modelinizi ve test verilerini eğiteetmek için kullanılır (%20) , modelinizi değerlendirmek için geri tutulur.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-236">The training data (80%) is used to train your model and the test data (20%) is held back to evaluate your model.</span></span> 

### <a name="how-do-i-understand-my-model-performance"></a><span data-ttu-id="bbaf0-237">Nasıl yaparım? model performansımı anladım mı?</span><span class="sxs-lookup"><span data-stu-id="bbaf0-237">How do I understand my model performance?</span></span>

<span data-ttu-id="bbaf0-238">Bir senaryo bir makine öğrenimi göreviyle eşlenir.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-238">A scenario maps to a machine learning task.</span></span> <span data-ttu-id="bbaf0-239">Her ML görevinin kendi değerlendirme ölçümleri kümesi vardır.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-239">Each ML task has its own set of evaluation metrics.</span></span>

#### <a name="regression-for-example-price-prediction"></a><span data-ttu-id="bbaf0-240">Gerileme (örneğin, fiyat tahmini)</span><span class="sxs-lookup"><span data-stu-id="bbaf0-240">Regression (for example, Price Prediction)</span></span>

<span data-ttu-id="bbaf0-241">Gerileme sorunları için varsayılan ölçüm RKARE, RKARE değeri 0 ile 1 arasında aralıklar olur.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-241">The default metric for regression problems is RSquared, the value of RSquared ranges between 0 and 1.</span></span> <span data-ttu-id="bbaf0-242">1 mümkün olan en iyi değer veya diğer bir deyişle, modelinizin daha iyi bir performans elde etmek için, RKARE değerinin 1 ' e yakın olması.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-242">1 is the best possible value or in other words the closer the value of RSquared to 1 the better your model is performing.</span></span>

<span data-ttu-id="bbaf0-243">Mutlak kayıp, kareli kayıp ve RMS kaybı gibi bildirilen diğer ölçümler, modelinizin nasıl çalıştığını anlamak ve diğer gerileme modelleriyle karşılaştırmak için kullanılabilecek ek ölçümlerdir.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-243">Other metrics reported such as absolute-loss, squared-loss, and RMS loss are additional metrics, which can be used to understand how your model is performing and comparing it against other regression models.</span></span>

#### <a name="binary-classification-for-example-sentiment-analysis"></a><span data-ttu-id="bbaf0-244">İkili Sınıflandırma (örneğin, Yaklaşım Analizi)</span><span class="sxs-lookup"><span data-stu-id="bbaf0-244">Binary Classification (for example, Sentiment Analysis)</span></span>

<span data-ttu-id="bbaf0-245">Sınıflandırma sorunları için varsayılan ölçüm doğruluk ' dir.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-245">The default metric for classification problems is accuracy.</span></span> <span data-ttu-id="bbaf0-246">Doğruluk, modelinizin test veri kümesi üzerinde yapmakta olduğu doğru tahminlerden oranını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-246">Accuracy defines the proportion of correct predictions your model is making over the test dataset.</span></span> <span data-ttu-id="bbaf0-247">%100 veya 1,0 ' e yakın olan daha iyi bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-247">The closer to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="bbaf0-248">Doğru pozitif oranı içeren AUC (eğri kapsamındaki alan) gibi bildirilen diğer ölçümler, modellerin kabul edilebilir olması için 0,50 ' den büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-248">Other metrics reported such as AUC (Area under the curve), which measures the true positive rate vs. the false positive rate should be greater than 0.50 for models to be acceptable.</span></span>

<span data-ttu-id="bbaf0-249">Duyarlılık ve geri çekme arasındaki dengeyi denetlemek için F1 puanı gibi ek ölçümler de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-249">Additional metrics like F1 score can be used to control the balance between Precision and Recall.</span></span>

#### <a name="multi-class-classification-for-example-issue-classification-image-classification"></a><span data-ttu-id="bbaf0-250">Çok sınıf sınıflandırması (örneğin, sorun sınıflandırması, görüntü sınıflandırması)</span><span class="sxs-lookup"><span data-stu-id="bbaf0-250">Multi-Class Classification (for example, Issue Classification, Image Classification)</span></span>

<span data-ttu-id="bbaf0-251">Çoklu Sınıf sınıflandırması için varsayılan ölçüm mikro doğruluk ' dir.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-251">The default metric for Multi-class classification is Micro Accuracy.</span></span> <span data-ttu-id="bbaf0-252">Mikro doğruluk %100 veya 1,0 ' e daha iyi.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-252">The closer the Micro Accuracy to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="bbaf0-253">Çok sınıf sınıflandırma için başka bir önemli ölçüm, daha iyi olan 1,0 ' e yakın olan mikro doğrulukta olduğu gibi, makro doğruluğuna benzer.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-253">Another important metric for Multi-class classification is Macro-accuracy, similar to Micro-accuracy the closer to 1.0 the better it is.</span></span> <span data-ttu-id="bbaf0-254">Bu iki tür doğruluğu düşünmek için iyi bir yoldur:</span><span class="sxs-lookup"><span data-stu-id="bbaf0-254">A good way to think about these two types of accuracy is:</span></span>

- <span data-ttu-id="bbaf0-255">Mikro doğruluk: bir gelen bilet, doğru ekibe ne sıklıkla sınıflandırıldı?</span><span class="sxs-lookup"><span data-stu-id="bbaf0-255">Micro-accuracy: How often does an incoming ticket get classified to the right team?</span></span>
- <span data-ttu-id="bbaf0-256">Makro doğruluğu: ortalama bir ekip Için, takımlarına yönelik gelen bir bilet ne sıklıkta doğru?</span><span class="sxs-lookup"><span data-stu-id="bbaf0-256">Macro-accuracy: For an average team, how often is an incoming ticket correct for their team?</span></span>

### <a name="more-information-on-evaluation-metrics"></a><span data-ttu-id="bbaf0-257">Değerlendirme ölçümleri hakkında daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="bbaf0-257">More information on evaluation metrics</span></span>

<span data-ttu-id="bbaf0-258">Daha fazla bilgi için bkz. [model değerlendirme ölçümleri](resources/metrics.md).</span><span class="sxs-lookup"><span data-stu-id="bbaf0-258">For more information, see [model evaluation metrics](resources/metrics.md).</span></span>

## <a name="improve"></a><span data-ttu-id="bbaf0-259">.NET becerilerinizi</span><span class="sxs-lookup"><span data-stu-id="bbaf0-259">Improve</span></span>

<span data-ttu-id="bbaf0-260">Model performans puanınız istediğiniz kadar iyi değilse şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bbaf0-260">If your model performance score is not as good as you want it to be, you can:</span></span>

- <span data-ttu-id="bbaf0-261">Daha uzun bir süre için eğitme.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-261">Train for a longer period of time.</span></span> <span data-ttu-id="bbaf0-262">Daha fazla zaman, daha fazla algoritma ve ayar denemek için otomatik makine öğrenimi altyapısı.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-262">With more time, the automated machine learning engine to try more algorithms and settings.</span></span>

- <span data-ttu-id="bbaf0-263">Daha fazla veri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-263">Add more data.</span></span> <span data-ttu-id="bbaf0-264">Bazen veri miktarı yüksek kaliteli bir makine öğrenimi modelini eğitmek için yeterli değildir.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-264">Sometimes the amount of data is not sufficient to train a high-quality machine learning model.</span></span>

- <span data-ttu-id="bbaf0-265">Verilerinizi dengeleyin.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-265">Balance your data.</span></span> <span data-ttu-id="bbaf0-266">Sınıflandırma görevleri için, eğitim kümesinin Kategoriler genelinde dengeli olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-266">For classification tasks, make sure that the training set is balanced across the categories.</span></span> <span data-ttu-id="bbaf0-267">Örneğin, 100 eğitim örnekleri için dört sınıfınız varsa ve bu iki sınıf (etiket1 ve etiket2), 90 kayıt için kullanılırsa, ancak diğer iki (etiket3 ve TAG4) yalnızca kalan 10 kayıtta kullanılıyorsa, dengeli verilerin bulunmaması modelinizin eksikliğine zarar verebilir etiket3 veya TAG4 ' i tahmin edin.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-267">For example, if you have four classes for 100 training examples, and the two first classes (tag1 and tag2) are used for 90 records, but the other two (tag3 and tag4) are only used on the remaining 10 records, the lack of balanced data may cause your model to struggle to correctly predict tag3 or tag4.</span></span>

## <a name="code"></a><span data-ttu-id="bbaf0-268">Kod</span><span class="sxs-lookup"><span data-stu-id="bbaf0-268">Code</span></span>

<span data-ttu-id="bbaf0-269">Değerlendirme aşamasından sonra, model Oluşturucu bir model dosyası ve uygulamayı uygulamanıza eklemek için kullanabileceğiniz kodu verir.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-269">After the evaluation phase, Model Builder outputs a model file, and code that you can use to add the model to your application.</span></span> <span data-ttu-id="bbaf0-270">ML.NET modelleri bir ZIP dosyası olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-270">ML.NET models are saved as a zip file.</span></span> <span data-ttu-id="bbaf0-271">Modelinize yüklenecek ve kullanılacak kod, çözümünüze yeni bir proje olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-271">The code to load and use your model is added as a new project in your solution.</span></span> <span data-ttu-id="bbaf0-272">Model Oluşturucu Ayrıca, modelinizi işlem içinde görmek için çalıştırabileceğiniz bir örnek konsol uygulaması da ekler.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-272">Model Builder also adds a sample console app that you can run to see your model in action.</span></span>

<span data-ttu-id="bbaf0-273">Ayrıca model Oluşturucu, modeli oluşturmak için kullanılan adımları anlayabilmeniz için modeli oluşturan kodu çıktı.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-273">In addition, Model Builder outputs the code that generated the model, so that you can understand the steps used to generate the model.</span></span> <span data-ttu-id="bbaf0-274">Modelinize yeni verilerle yeniden eğitebilmeniz için model eğitim kodunu da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bbaf0-274">You can also use the model training code to retrain your model with new data.</span></span>

## <a name="whats-next"></a><span data-ttu-id="bbaf0-275">Sırada ne var?</span><span class="sxs-lookup"><span data-stu-id="bbaf0-275">What's next?</span></span>

<span data-ttu-id="bbaf0-276">Model Oluşturucu Visual Studio uzantısını [yükler](how-to-guides/install-model-builder.md)</span><span class="sxs-lookup"><span data-stu-id="bbaf0-276">[Install](how-to-guides/install-model-builder.md) the Model Builder Visual Studio extension</span></span>

<span data-ttu-id="bbaf0-277">[Fiyat tahmini veya herhangi bir gerileme senaryosu](tutorials/predict-prices-with-model-builder.md) deneyin</span><span class="sxs-lookup"><span data-stu-id="bbaf0-277">Try [price prediction or any regression scenario](tutorials/predict-prices-with-model-builder.md)</span></span>
