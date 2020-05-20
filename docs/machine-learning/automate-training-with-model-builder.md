---
title: Model Oluşturucu nedir ve nasıl çalışır?
description: Makine öğrenimi modelini otomatik olarak eğiteiçin ML.NET model Oluşturucu 'Yu kullanma
ms.date: 03/25/2020
ms.custom: overview, mlnet-tooling
ms.openlocfilehash: 4afdbfd1682a30647b09d05d51a5c73c214fe2bd
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616937"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a><span data-ttu-id="ba9a9-103">Model Oluşturucu nedir ve nasıl çalışır?</span><span class="sxs-lookup"><span data-stu-id="ba9a9-103">What is Model Builder and how does it work?</span></span>

<span data-ttu-id="ba9a9-104">ML.NET model Oluşturucu, özel makine öğrenimi modellerini derlemek, eğitme ve dağıtmaya yönelik sezgisel bir grafik Visual Studio uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-104">ML.NET Model Builder is an intuitive graphical Visual Studio extension to build, train, and deploy custom machine learning models.</span></span>

<span data-ttu-id="ba9a9-105">Model Oluşturucu, senaryonuza en uygun olanı bulmanıza yardımcı olmak üzere farklı makine öğrenimi algoritmalarını ve ayarlarını araştırmak için otomatik makine öğrenimi (Otomatikml) kullanır.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-105">Model Builder uses automated machine learning (AutoML) to explore different machine learning algorithms and settings to help you find the one that best suits your scenario.</span></span>

<span data-ttu-id="ba9a9-106">Model Oluşturucuyu kullanmak için Machine Learning uzmanlığına ihtiyacınız yoktur.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-106">You don't need machine learning expertise to use Model Builder.</span></span> <span data-ttu-id="ba9a9-107">Bazı veriler ve çözübir sorun var.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-107">All you need is some data, and a problem to solve.</span></span> <span data-ttu-id="ba9a9-108">Model Oluşturucu, modeli .NET uygulamanıza eklemek için kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-108">Model Builder generates the code to add the model to your .NET application.</span></span>

![Model Oluşturucu Visual Studio uzantısı kullanıcı arabirimi animasyonu](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> <span data-ttu-id="ba9a9-110">Model Oluşturucu Şu anda önizleme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-110">Model Builder is currently in Preview.</span></span>

## <a name="scenario"></a><span data-ttu-id="ba9a9-111">Senaryo</span><span class="sxs-lookup"><span data-stu-id="ba9a9-111">Scenario</span></span>

<span data-ttu-id="ba9a9-112">Uygulamanız için bir makine öğrenimi modeli oluşturmak için model Oluşturucu 'ya birçok farklı senaryo getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-112">You can bring many different scenarios to Model Builder, to generate a machine learning model for your application.</span></span>

<span data-ttu-id="ba9a9-113">Senaryo, verilerinizi kullanarak yapmak istediğiniz tahmin türünün bir açıklamasıdır.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-113">A scenario is a description of the type of prediction you want to make using your data.</span></span> <span data-ttu-id="ba9a9-114">Örnek:</span><span class="sxs-lookup"><span data-stu-id="ba9a9-114">For example:</span></span>

- <span data-ttu-id="ba9a9-115">geçmiş satış verilerine göre gelecek ürün satış hacmini tahmin edin</span><span class="sxs-lookup"><span data-stu-id="ba9a9-115">predict future product sales volume based on historical sales data</span></span>
- <span data-ttu-id="ba9a9-116">müşterilerin gözden geçirmeleri temelinde olumlu veya olumsuz şekilde sınıflandırın</span><span class="sxs-lookup"><span data-stu-id="ba9a9-116">classify sentiments as positive or negative based on customer reviews</span></span>
- <span data-ttu-id="ba9a9-117">Bankacılık işleminin sahte olup olmadığını Algıla</span><span class="sxs-lookup"><span data-stu-id="ba9a9-117">detect whether a banking transaction is fraudulent</span></span>
- <span data-ttu-id="ba9a9-118">Müşteri geri bildirim sorunlarını şirketinizdeki doğru ekibe yönlendirin</span><span class="sxs-lookup"><span data-stu-id="ba9a9-118">route customer feedback issues to the correct team in your company</span></span>

### <a name="which-machine-learning-scenario-is-right-for-me"></a><span data-ttu-id="ba9a9-119">Hangi makine öğrenimi senaryosu bana uygun?</span><span class="sxs-lookup"><span data-stu-id="ba9a9-119">Which machine learning scenario is right for me?</span></span>

<span data-ttu-id="ba9a9-120">Model Oluşturucu 'da bir senaryo seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-120">In Model Builder, you need to select a scenario.</span></span> <span data-ttu-id="ba9a9-121">Senaryonun türü, yapmaya çalıştığınız tahmin türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-121">The type of scenario depends on what type of prediction you are trying to make.</span></span>

#### <a name="text-classification"></a><span data-ttu-id="ba9a9-122">Metin sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="ba9a9-122">Text classification</span></span>

<span data-ttu-id="ba9a9-123">Sınıflandırma, verileri kategorilere ayırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-123">Classification is used to categorize data into categories.</span></span>

![Sahtekarlık algılama, risk azaltma ve uygulama filtreleme dahil olmak üzere ikili sınıflandırma örneklerini gösteren diyagram](media/binary-classification-examples.png)

![Belge ve ürün sınıflandırması, destek bileti yönlendirmesi ve müşteri sorunu önceliklendirmesi dahil birden çok Lass sınıflandırması örnekleri](media/multiclass-classification-examples.png)

#### <a name="value-prediction"></a><span data-ttu-id="ba9a9-126">Değer tahmini</span><span class="sxs-lookup"><span data-stu-id="ba9a9-126">Value prediction</span></span>

<span data-ttu-id="ba9a9-127">Regresyon, sayıları tahmin etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-127">Regression is used to predict numbers.</span></span>

![Fiyat tahmini, satış tahmini ve tahmine dayalı bakım gibi gerileme örneklerini gösteren diyagram](media/regression-examples.png)

#### <a name="image-classification"></a><span data-ttu-id="ba9a9-129">Resimleri sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="ba9a9-129">Image classification</span></span>

<span data-ttu-id="ba9a9-130">Görüntü sınıflandırması, farklı kategorilerin görüntülerini belirlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-130">Image classification can be used to identify images of different categories.</span></span> <span data-ttu-id="ba9a9-131">Örneğin, farklı türlerde terur veya hayvanlar veya üretim kusurları vardır.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-131">For example, different types of terrain or animals or manufacturing defects.</span></span>

<span data-ttu-id="ba9a9-132">Bir görüntü kümesine sahipseniz ve görüntüleri farklı kategorilerde sınıflandırmak istiyorsanız resim sınıflandırması senaryosunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-132">You can use the image classification scenario if you have a set of images, and you want to classify the images into different categories.</span></span>

#### <a name="recommendation"></a><span data-ttu-id="ba9a9-133">Öneri</span><span class="sxs-lookup"><span data-stu-id="ba9a9-133">Recommendation</span></span>

<span data-ttu-id="ba9a9-134">Öneri senaryosu, belirli bir kullanıcı için önerilen öğelerin bir listesini, beğenilmesi ve benzemelerine bağlı olarak diğer kullanıcılara da tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-134">The recommendation scenario predicts a list of suggested items for a particular user, based on how similar their likes and dislikes are to other users'.</span></span>

<span data-ttu-id="ba9a9-135">Kullanıcı kümesi ve satın alma, Filmler, kitaplar veya TV programları gibi bir dizi kullanıcıya ve bu ürünlerin bir Kullanıcı ' "derecelendirmesine" sahip olduğunuzda öneri senaryosunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-135">You can use the recommendation scenario when you have a set of users and a set of "products", such as items to purchase, movies, books, or TV shows, along with a set of users' "ratings" of those products.</span></span>

## <a name="environment"></a><span data-ttu-id="ba9a9-136">Ortam</span><span class="sxs-lookup"><span data-stu-id="ba9a9-136">Environment</span></span>

<span data-ttu-id="ba9a9-137">Makine öğrenimi modelinizi makinenizde yerel olarak veya Azure 'da bulutta eğitebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-137">You can train your machine learning model locally on your machine or in the cloud on Azure.</span></span>

<span data-ttu-id="ba9a9-138">Yerel olarak eğitedığınızda, bilgisayar kaynaklarınızın (CPU, bellek ve disk) kısıtlamaları dahilinde çalışırsınız.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-138">When you train locally, you work within the constraints of your computer resources (CPU, memory, and disk).</span></span> <span data-ttu-id="ba9a9-139">Bulutta eğiyorsanız, özellikle büyük veri kümelerinde, senaryolarınızın taleplerini karşılamak için kaynaklarınızı ölçeklendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-139">When you train in the cloud, you can scale up your resources to meet the demands of your scenario, especially for large datasets.</span></span>

<span data-ttu-id="ba9a9-140">Yerel Eğitim tüm senaryolar için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-140">Local training is supported for all scenarios.</span></span>

<span data-ttu-id="ba9a9-141">Azure eğitimi, görüntü sınıflandırması için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-141">Azure training is supported for Image Classification.</span></span>

## <a name="data"></a><span data-ttu-id="ba9a9-142">Veriler</span><span class="sxs-lookup"><span data-stu-id="ba9a9-142">Data</span></span>

<span data-ttu-id="ba9a9-143">Senaryonuzu seçtikten sonra model Oluşturucu sizden bir veri kümesi sağlamanızı ister.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-143">Once you have chosen your scenario, Model Builder asks you to provide a dataset.</span></span> <span data-ttu-id="ba9a9-144">Veriler, senaryonuza yönelik en iyi modeli eğlendirmek, değerlendirmek ve seçmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-144">The data is used to train, evaluate, and choose the best model for your scenario.</span></span>

![Model Oluşturucu adımlarını gösteren diyagram](media/model-builder-steps.png)

<span data-ttu-id="ba9a9-146">Model Oluşturucu,. tsv,. csv,. txt biçimlerinin yanı sıra SQL veritabanı biçiminde veri kümelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-146">Model Builder supports datasets in .tsv, .csv, .txt formats, as well as SQL database format.</span></span> <span data-ttu-id="ba9a9-147">Bir. txt dosyanız varsa, sütunlar veya ile ayrılmalıdır `,` , `;` `/t` dosyanın bir başlık satırı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-147">If you have a .txt file, columns should be separated with `,`, `;` or `/t` and the file must have a header row.</span></span>

<span data-ttu-id="ba9a9-148">Veri kümesi görüntülerden birini yapılırsa, desteklenen dosya türleri `.jpg` ve olur `.png` .</span><span class="sxs-lookup"><span data-stu-id="ba9a9-148">If the dataset is made up of images, the supported file types are `.jpg` and `.png`.</span></span>

<span data-ttu-id="ba9a9-149">Daha fazla bilgi için bkz. [model Oluşturucu 'da eğitim verilerini yükleme](how-to-guides/load-data-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="ba9a9-149">For more information, see [Load training data into Model Builder](how-to-guides/load-data-model-builder.md).</span></span>

### <a name="choose-the-output-to-predict-label"></a><span data-ttu-id="ba9a9-150">Tahmin edilecek çıktıyı seçin (etiket)</span><span class="sxs-lookup"><span data-stu-id="ba9a9-150">Choose the output to predict (label)</span></span>

<span data-ttu-id="ba9a9-151">Veri kümesi, eğitim örneklerinden ve özniteliklerin sütunlarından oluşan bir tablodur.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-151">A dataset is a table of rows of training examples, and columns of attributes.</span></span> <span data-ttu-id="ba9a9-152">Her satır şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="ba9a9-152">Each row has:</span></span>

- <span data-ttu-id="ba9a9-153">bir **etiket** (tahmin etmek istediğiniz öznitelik)</span><span class="sxs-lookup"><span data-stu-id="ba9a9-153">a **label** (the attribute that you want to predict)</span></span>
- <span data-ttu-id="ba9a9-154">**Özellikler** (etiketi tahmin etmek için giriş olarak kullanılan öznitelikler).</span><span class="sxs-lookup"><span data-stu-id="ba9a9-154">**features** (attributes that are used as inputs to predict the label).</span></span>

<span data-ttu-id="ba9a9-155">Ev fiyat tahmini senaryosu için özellikler şu şekilde olabilir:</span><span class="sxs-lookup"><span data-stu-id="ba9a9-155">For the house-price prediction scenario, the features could be:</span></span>

- <span data-ttu-id="ba9a9-156">Evin kare çekimi</span><span class="sxs-lookup"><span data-stu-id="ba9a9-156">the square footage of the house</span></span>
- <span data-ttu-id="ba9a9-157">yatak odaları ve külikler sayısı</span><span class="sxs-lookup"><span data-stu-id="ba9a9-157">the number of bedrooms and bathrooms</span></span>
- <span data-ttu-id="ba9a9-158">posta kodu</span><span class="sxs-lookup"><span data-stu-id="ba9a9-158">the zip code</span></span>

<span data-ttu-id="ba9a9-159">Etiket, bu kare çekimi, yatak odası ve banyo değerleri ve posta kodu satırı için geçmiş bir evin fiyatıdır.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-159">The label is the historical house price for that row of square footage, bedroom, and bathroom values and zip code.</span></span>

![Boyut Odalar ZIP kodu ve fiyat etiketinden oluşan özelliklerle birlikte, ev fiyatı verilerinin satırlarını ve sütunlarını gösteren tablo](media/model-builder-data.png)

### <a name="example-datasets"></a><span data-ttu-id="ba9a9-161">Örnek veri kümeleri</span><span class="sxs-lookup"><span data-stu-id="ba9a9-161">Example datasets</span></span>

<span data-ttu-id="ba9a9-162">Henüz kendi verileriniz yoksa, bu veri kümelerinden birini deneyin:</span><span class="sxs-lookup"><span data-stu-id="ba9a9-162">If you don't have your own data yet, try out one of these datasets:</span></span>

|<span data-ttu-id="ba9a9-163">Senaryo</span><span class="sxs-lookup"><span data-stu-id="ba9a9-163">Scenario</span></span>|<span data-ttu-id="ba9a9-164">Örnek</span><span class="sxs-lookup"><span data-stu-id="ba9a9-164">Example</span></span>|<span data-ttu-id="ba9a9-165">Veriler</span><span class="sxs-lookup"><span data-stu-id="ba9a9-165">Data</span></span>|<span data-ttu-id="ba9a9-166">Etiketle</span><span class="sxs-lookup"><span data-stu-id="ba9a9-166">Label</span></span>|<span data-ttu-id="ba9a9-167">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ba9a9-167">Features</span></span>|
|-|-|-|-|-|
|<span data-ttu-id="ba9a9-168">Sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="ba9a9-168">Classification</span></span>|<span data-ttu-id="ba9a9-169">Satış anormalilerini tahmin edin</span><span class="sxs-lookup"><span data-stu-id="ba9a9-169">Predict sales anomalies</span></span>|[<span data-ttu-id="ba9a9-170">ürün satış verileri</span><span class="sxs-lookup"><span data-stu-id="ba9a9-170">product sales data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|<span data-ttu-id="ba9a9-171">Ürün satışları</span><span class="sxs-lookup"><span data-stu-id="ba9a9-171">Product Sales</span></span>|<span data-ttu-id="ba9a9-172">Ay</span><span class="sxs-lookup"><span data-stu-id="ba9a9-172">Month</span></span>|
||<span data-ttu-id="ba9a9-173">Web sitesi açıklamalarının yaklaşımını tahmin etme</span><span class="sxs-lookup"><span data-stu-id="ba9a9-173">Predict sentiment of website comments</span></span>|[<span data-ttu-id="ba9a9-174">Web sitesi açıklama verileri</span><span class="sxs-lookup"><span data-stu-id="ba9a9-174">website comment data</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|<span data-ttu-id="ba9a9-175">Etiket (negatif yaklaşım olduğunda 0, pozitif olduğunda 1)</span><span class="sxs-lookup"><span data-stu-id="ba9a9-175">Label (0 when negative sentiment, 1 when positive)</span></span>|<span data-ttu-id="ba9a9-176">Açıklama, yıl</span><span class="sxs-lookup"><span data-stu-id="ba9a9-176">Comment, Year</span></span>|
||<span data-ttu-id="ba9a9-177">Sahte kredi kartı işlemlerini tahmin etme</span><span class="sxs-lookup"><span data-stu-id="ba9a9-177">Predict fraudulent credit card transactions</span></span>|[<span data-ttu-id="ba9a9-178">kredi kartı verileri</span><span class="sxs-lookup"><span data-stu-id="ba9a9-178">credit card data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|<span data-ttu-id="ba9a9-179">Sınıf (sahte olduğunda 1, aksi durumda 0)</span><span class="sxs-lookup"><span data-stu-id="ba9a9-179">Class (1 when fraudulent, 0 otherwise)</span></span>|<span data-ttu-id="ba9a9-180">Miktar, v1-V28 (anonimleştirilmiş Özellikler)</span><span class="sxs-lookup"><span data-stu-id="ba9a9-180">Amount, V1-V28 (anonymized features)</span></span>|
||<span data-ttu-id="ba9a9-181">GitHub deposundaki sorun türünü tahmin etme</span><span class="sxs-lookup"><span data-stu-id="ba9a9-181">Predict the type of issue in a GitHub repository</span></span>|[<span data-ttu-id="ba9a9-182">GitHub sorun verileri</span><span class="sxs-lookup"><span data-stu-id="ba9a9-182">GitHub issue data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|<span data-ttu-id="ba9a9-183">Alan</span><span class="sxs-lookup"><span data-stu-id="ba9a9-183">Area</span></span>|<span data-ttu-id="ba9a9-184">Başlık, açıklama</span><span class="sxs-lookup"><span data-stu-id="ba9a9-184">Title, Description</span></span>|
|<span data-ttu-id="ba9a9-185">Değer tahmini</span><span class="sxs-lookup"><span data-stu-id="ba9a9-185">Value prediction</span></span>|<span data-ttu-id="ba9a9-186">Taxı tarifeli havayolu fiyatını tahmin etme</span><span class="sxs-lookup"><span data-stu-id="ba9a9-186">Predict taxi fare price</span></span>|[<span data-ttu-id="ba9a9-187">taxı tarifeli havayolu verileri</span><span class="sxs-lookup"><span data-stu-id="ba9a9-187">taxi fare data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|<span data-ttu-id="ba9a9-188">Tarifeli havayolu</span><span class="sxs-lookup"><span data-stu-id="ba9a9-188">Fare</span></span>|<span data-ttu-id="ba9a9-189">Seyahat süresi, uzaklık</span><span class="sxs-lookup"><span data-stu-id="ba9a9-189">Trip time, distance</span></span>|
|<span data-ttu-id="ba9a9-190">Resimleri sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="ba9a9-190">Image classification</span></span>|<span data-ttu-id="ba9a9-191">Çiçek kategorisini tahmin etme</span><span class="sxs-lookup"><span data-stu-id="ba9a9-191">Predict the category of a flower</span></span> |[<span data-ttu-id="ba9a9-192">çiçek görüntüleri</span><span class="sxs-lookup"><span data-stu-id="ba9a9-192">flower images</span></span>](http://download.tensorflow.org/example_images/flower_photos.tgz)|<span data-ttu-id="ba9a9-193">Çiçek türü: da, Dandelion, Roses, sunçiçekler, TULIP 'ler</span><span class="sxs-lookup"><span data-stu-id="ba9a9-193">The type of flower: daisy, dandelion, roses, sunflowers, tulips</span></span>|<span data-ttu-id="ba9a9-194">Görüntü verilerinin kendisi</span><span class="sxs-lookup"><span data-stu-id="ba9a9-194">The image data itself</span></span>|
|<span data-ttu-id="ba9a9-195">Öneri</span><span class="sxs-lookup"><span data-stu-id="ba9a9-195">Recommendation</span></span>|<span data-ttu-id="ba9a9-196">Birisinin beğenolacağı filmleri tahmin edin</span><span class="sxs-lookup"><span data-stu-id="ba9a9-196">Predict movies that someone will like</span></span>|[<span data-ttu-id="ba9a9-197">Film derecelendirmeleri</span><span class="sxs-lookup"><span data-stu-id="ba9a9-197">movie ratings</span></span>](http://files.grouplens.org/datasets/movielens/ml-latest-small.zip)|<span data-ttu-id="ba9a9-198">Kullanıcılar, Filmler</span><span class="sxs-lookup"><span data-stu-id="ba9a9-198">Users, Movies</span></span>|<span data-ttu-id="ba9a9-199">Derecelendirmeler</span><span class="sxs-lookup"><span data-stu-id="ba9a9-199">Ratings</span></span>|

## <a name="train"></a><span data-ttu-id="ba9a9-200">Eğitim</span><span class="sxs-lookup"><span data-stu-id="ba9a9-200">Train</span></span>

<span data-ttu-id="ba9a9-201">Senaryonuzu, verilerinizi ve etiketini seçtikten sonra model Oluşturucu modeli izleyin.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-201">Once you select your scenario, data, and label, Model Builder trains the model.</span></span>

### <a name="what-is-training"></a><span data-ttu-id="ba9a9-202">Eğitim nedir?</span><span class="sxs-lookup"><span data-stu-id="ba9a9-202">What is training?</span></span>

<span data-ttu-id="ba9a9-203">Eğitim, model Oluşturucu 'nun, senaryonuza yönelik soruların nasıl yanıtlanarak modelinizi öğretirken otomatik bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-203">Training is an automatic process by which Model Builder teaches your model how to answer questions for your scenario.</span></span> <span data-ttu-id="ba9a9-204">Eğittikten sonra modelinize, daha önce görmemiş olan giriş verileriyle ilgili tahmin yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-204">Once trained, your model can make predictions with input data that it has not seen before.</span></span> <span data-ttu-id="ba9a9-205">Örneğin, ev fiyatlarını tahmin ediyorsanız ve pazara yeni bir ev geliyorsa, satış fiyatını tahmin edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-205">For example, if you are predicting house prices and a new house comes on the market, you can predict its sale price.</span></span>

<span data-ttu-id="ba9a9-206">Model Oluşturucu otomatik makine öğrenimi (Otomatikml) kullandığından, eğitim sırasında sizin için herhangi bir giriş veya ayarlama gerekmez.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-206">Because Model Builder uses automated machine learning (AutoML), it does not require any input or tuning from you during training.</span></span>

### <a name="how-long-should-i-train-for"></a><span data-ttu-id="ba9a9-207">Ne kadar eğitmem gerekir?</span><span class="sxs-lookup"><span data-stu-id="ba9a9-207">How long should I train for?</span></span>

<span data-ttu-id="ba9a9-208">Model Oluşturucu, sizi en iyi şekilde gerçekleştiren modeli bulmak için birden çok modeli araştırmak üzere oto ml kullanır.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-208">Model Builder uses AutoML to explore multiple models to find you the best performing model.</span></span>

<span data-ttu-id="ba9a9-209">Daha uzun eğitim dönemleri, oto ml 'nin daha geniş bir ayar aralığıyla daha fazla modeli keşfetmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-209">Longer training periods allow AutoML to explore more models with a wider range of settings.</span></span>

<span data-ttu-id="ba9a9-210">Aşağıdaki tabloda, yerel bir makinedeki bir örnek veri kümesi paketi için iyi performans sağlamak üzere harcanan ortalama süre özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-210">The table below summarizes the average time taken to get good performance for a suite of example datasets, on a local machine.</span></span>

|<span data-ttu-id="ba9a9-211">Veri kümesi boyutu</span><span class="sxs-lookup"><span data-stu-id="ba9a9-211">Dataset size</span></span>|<span data-ttu-id="ba9a9-212">Ortalama eğitim süresi</span><span class="sxs-lookup"><span data-stu-id="ba9a9-212">Average time to train</span></span>|
|------------|---------------------|
|<span data-ttu-id="ba9a9-213">0-10 MB</span><span class="sxs-lookup"><span data-stu-id="ba9a9-213">0 - 10 MB</span></span>|<span data-ttu-id="ba9a9-214">10 sn</span><span class="sxs-lookup"><span data-stu-id="ba9a9-214">10 sec</span></span>|
|<span data-ttu-id="ba9a9-215">10-100 MB</span><span class="sxs-lookup"><span data-stu-id="ba9a9-215">10 - 100 MB</span></span>|<span data-ttu-id="ba9a9-216">10 dakika</span><span class="sxs-lookup"><span data-stu-id="ba9a9-216">10 min</span></span>|
|<span data-ttu-id="ba9a9-217">100-500 MB</span><span class="sxs-lookup"><span data-stu-id="ba9a9-217">100 - 500 MB</span></span>|<span data-ttu-id="ba9a9-218">30 dakika</span><span class="sxs-lookup"><span data-stu-id="ba9a9-218">30 min</span></span>|
|<span data-ttu-id="ba9a9-219">500-1 GB</span><span class="sxs-lookup"><span data-stu-id="ba9a9-219">500 - 1 GB</span></span>|<span data-ttu-id="ba9a9-220">60 dk</span><span class="sxs-lookup"><span data-stu-id="ba9a9-220">60 min</span></span>|
|<span data-ttu-id="ba9a9-221">1 GB +</span><span class="sxs-lookup"><span data-stu-id="ba9a9-221">1 GB+</span></span>|<span data-ttu-id="ba9a9-222">3 + saat</span><span class="sxs-lookup"><span data-stu-id="ba9a9-222">3+ hours</span></span>|

<span data-ttu-id="ba9a9-223">Bu numaralar yalnızca bir kılavuzdur.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-223">These numbers are a guide only.</span></span> <span data-ttu-id="ba9a9-224">Eğitimin tam uzunluğu şu şekilde bağımlıdır:</span><span class="sxs-lookup"><span data-stu-id="ba9a9-224">The exact length of training is dependent on:</span></span>

- <span data-ttu-id="ba9a9-225">modele girdi olarak kullanılan özellik sayısı (sütun)</span><span class="sxs-lookup"><span data-stu-id="ba9a9-225">the number of features (columns) being used to as input to the model</span></span>
- <span data-ttu-id="ba9a9-226">sütun türü</span><span class="sxs-lookup"><span data-stu-id="ba9a9-226">the type of columns</span></span>
- <span data-ttu-id="ba9a9-227">ML görevi</span><span class="sxs-lookup"><span data-stu-id="ba9a9-227">the ML task</span></span>
- <span data-ttu-id="ba9a9-228">Eğitim için kullanılan makinenin CPU, disk ve bellek performansı</span><span class="sxs-lookup"><span data-stu-id="ba9a9-228">the CPU, disk, and memory performance of the machine used for training</span></span>

## <a name="evaluate"></a><span data-ttu-id="ba9a9-229">Değerlendir</span><span class="sxs-lookup"><span data-stu-id="ba9a9-229">Evaluate</span></span>

<span data-ttu-id="ba9a9-230">Değerlendirme, modelinizin ne kadar iyi olduğunu ölçmeye yönelik bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-230">Evaluation is the process of measuring how good your model is.</span></span> <span data-ttu-id="ba9a9-231">Model Oluşturucu, yeni test verileriyle tahmine dayalı hale getirmek için eğitilen modeli kullanır ve daha sonra tahminlerin ne kadar iyi olduğunu ölçer.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-231">Model Builder uses the trained model to make predictions with new test data, and then measures how good the predictions are.</span></span>

<span data-ttu-id="ba9a9-232">Model Oluşturucu eğitim verilerini bir eğitim kümesine ve bir test kümesine böler.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-232">Model Builder splits the training data into a training set and a test set.</span></span> <span data-ttu-id="ba9a9-233">Eğitim verileri (%80) modelinizi ve test verilerini eğiteetmek için kullanılır (%20) , modelinizi değerlendirmek için geri tutulur.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-233">The training data (80%) is used to train your model and the test data (20%) is held back to evaluate your model.</span></span>

### <a name="how-do-i-understand-my-model-performance"></a><span data-ttu-id="ba9a9-234">Nasıl yaparım? model performansımı anladım mı?</span><span class="sxs-lookup"><span data-stu-id="ba9a9-234">How do I understand my model performance?</span></span>

<span data-ttu-id="ba9a9-235">Bir senaryo bir makine öğrenimi göreviyle eşlenir.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-235">A scenario maps to a machine learning task.</span></span> <span data-ttu-id="ba9a9-236">Her ML görevinin kendi değerlendirme ölçümleri kümesi vardır.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-236">Each ML task has its own set of evaluation metrics.</span></span>

#### <a name="value-prediction"></a><span data-ttu-id="ba9a9-237">Değer tahmini</span><span class="sxs-lookup"><span data-stu-id="ba9a9-237">Value prediction</span></span>

<span data-ttu-id="ba9a9-238">Değer tahmini sorunları için varsayılan ölçüm RKARE, RKARE değeri 0 ile 1 arasında aralıklar olur.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-238">The default metric for value prediction problems is RSquared, the value of RSquared ranges between 0 and 1.</span></span> <span data-ttu-id="ba9a9-239">1 mümkün olan en iyi değer veya diğer bir deyişle, modelinizin daha iyi bir performans elde etmek için, RKARE değerinin 1 ' e yakın olması.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-239">1 is the best possible value or in other words the closer the value of RSquared to 1 the better your model is performing.</span></span>

<span data-ttu-id="ba9a9-240">Mutlak kayıp, kareli kayıp ve RMS kaybı gibi bildirilen diğer ölçümler, modelinizin nasıl çalıştığını anlamak ve diğer değer tahmini modelleriyle karşılaştırmak için kullanılabilecek ek ölçümlerdir.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-240">Other metrics reported such as absolute-loss, squared-loss, and RMS loss are additional metrics, which can be used to understand how your model is performing and comparing it against other value prediction models.</span></span>

#### <a name="classification-2-categories"></a><span data-ttu-id="ba9a9-241">Sınıflandırma (2 kategori)</span><span class="sxs-lookup"><span data-stu-id="ba9a9-241">Classification (2 categories)</span></span>

<span data-ttu-id="ba9a9-242">Sınıflandırma sorunları için varsayılan ölçüm doğruluk ' dir.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-242">The default metric for classification problems is accuracy.</span></span> <span data-ttu-id="ba9a9-243">Doğruluk, modelinizin test veri kümesi üzerinde yapmakta olduğu doğru tahminlerden oranını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-243">Accuracy defines the proportion of correct predictions your model is making over the test dataset.</span></span> <span data-ttu-id="ba9a9-244">%100 veya 1,0 ' e yakın olan daha iyi bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-244">The closer to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="ba9a9-245">Doğru pozitif oranı içeren AUC (eğri kapsamındaki alan) gibi bildirilen diğer ölçümler, modellerin kabul edilebilir olması için 0,50 ' den büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-245">Other metrics reported such as AUC (Area under the curve), which measures the true positive rate vs. the false positive rate should be greater than 0.50 for models to be acceptable.</span></span>

<span data-ttu-id="ba9a9-246">Duyarlılık ve geri çekme arasındaki dengeyi denetlemek için F1 puanı gibi ek ölçümler de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-246">Additional metrics like F1 score can be used to control the balance between Precision and Recall.</span></span>

#### <a name="classification-3-categories"></a><span data-ttu-id="ba9a9-247">Sınıflandırma (3 + kategori)</span><span class="sxs-lookup"><span data-stu-id="ba9a9-247">Classification (3+ categories)</span></span>

<span data-ttu-id="ba9a9-248">Çoklu Sınıf sınıflandırması için varsayılan ölçüm mikro doğruluk ' dir.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-248">The default metric for Multi-class classification is Micro Accuracy.</span></span> <span data-ttu-id="ba9a9-249">Mikro doğruluk %100 veya 1,0 ' e daha iyi.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-249">The closer the Micro Accuracy to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="ba9a9-250">Çok sınıf sınıflandırma için başka bir önemli ölçüm, daha iyi olan 1,0 ' e yakın olan mikro doğrulukta olduğu gibi, makro doğruluğuna benzer.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-250">Another important metric for Multi-class classification is Macro-accuracy, similar to Micro-accuracy the closer to 1.0 the better it is.</span></span> <span data-ttu-id="ba9a9-251">Bu iki tür doğruluğu düşünmek için iyi bir yoldur:</span><span class="sxs-lookup"><span data-stu-id="ba9a9-251">A good way to think about these two types of accuracy is:</span></span>

- <span data-ttu-id="ba9a9-252">Mikro doğruluk: bir gelen bilet, doğru ekibe ne sıklıkla sınıflandırıldı?</span><span class="sxs-lookup"><span data-stu-id="ba9a9-252">Micro-accuracy: How often does an incoming ticket get classified to the right team?</span></span>
- <span data-ttu-id="ba9a9-253">Makro doğruluğu: ortalama bir ekip Için, takımlarına yönelik gelen bir bilet ne sıklıkta doğru?</span><span class="sxs-lookup"><span data-stu-id="ba9a9-253">Macro-accuracy: For an average team, how often is an incoming ticket correct for their team?</span></span>

### <a name="more-information-on-evaluation-metrics"></a><span data-ttu-id="ba9a9-254">Değerlendirme ölçümleri hakkında daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="ba9a9-254">More information on evaluation metrics</span></span>

<span data-ttu-id="ba9a9-255">Daha fazla bilgi için bkz. [model değerlendirme ölçümleri](resources/metrics.md).</span><span class="sxs-lookup"><span data-stu-id="ba9a9-255">For more information, see [model evaluation metrics](resources/metrics.md).</span></span>

## <a name="improve"></a><span data-ttu-id="ba9a9-256">Enizi</span><span class="sxs-lookup"><span data-stu-id="ba9a9-256">Improve</span></span>

<span data-ttu-id="ba9a9-257">Model performans puanınız istediğiniz kadar iyi değilse şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ba9a9-257">If your model performance score is not as good as you want it to be, you can:</span></span>

- <span data-ttu-id="ba9a9-258">Daha uzun bir süre için eğitme.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-258">Train for a longer period of time.</span></span> <span data-ttu-id="ba9a9-259">Daha fazla zaman, otomatik makine öğrenme altyapısı, daha fazla algoritmalarla ve ayarlarla denemeleri.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-259">With more time, the automated machine learning engine experiments with more algorithms and settings.</span></span>

- <span data-ttu-id="ba9a9-260">Daha fazla veri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-260">Add more data.</span></span> <span data-ttu-id="ba9a9-261">Bazen veri miktarı yüksek kaliteli bir makine öğrenimi modelini eğitmek için yeterli değildir.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-261">Sometimes the amount of data is not sufficient to train a high-quality machine learning model.</span></span>

- <span data-ttu-id="ba9a9-262">Verilerinizi dengeleyin.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-262">Balance your data.</span></span> <span data-ttu-id="ba9a9-263">Sınıflandırma görevleri için, eğitim kümesinin Kategoriler genelinde dengeli olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-263">For classification tasks, make sure that the training set is balanced across the categories.</span></span> <span data-ttu-id="ba9a9-264">Örneğin, 100 eğitim örnekleri için dört sınıfınız varsa ve bu iki sınıf (etiket1 ve etiket2), 90 kayıt için kullanılırsa, ancak diğer iki (etiket3 ve TAG4) yalnızca kalan 10 kayıtta kullanılıyorsa, dengeli verilerin olmaması modelinizin, etiket3 veya TAG4 doğru tahmin etmeye yönelik olarak, modelinize neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-264">For example, if you have four classes for 100 training examples, and the two first classes (tag1 and tag2) are used for 90 records, but the other two (tag3 and tag4) are only used on the remaining 10 records, the lack of balanced data may cause your model to struggle to correctly predict tag3 or tag4.</span></span>

## <a name="code"></a><span data-ttu-id="ba9a9-265">Kod</span><span class="sxs-lookup"><span data-stu-id="ba9a9-265">Code</span></span>

<span data-ttu-id="ba9a9-266">Değerlendirme aşamasından sonra, model Oluşturucu bir model dosyası ve uygulamayı uygulamanıza eklemek için kullanabileceğiniz kodu verir.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-266">After the evaluation phase, Model Builder outputs a model file, and code that you can use to add the model to your application.</span></span> <span data-ttu-id="ba9a9-267">ML.NET modelleri bir ZIP dosyası olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-267">ML.NET models are saved as a zip file.</span></span> <span data-ttu-id="ba9a9-268">Modelinize yüklenecek ve kullanılacak kod, çözümünüze yeni bir proje olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-268">The code to load and use your model is added as a new project in your solution.</span></span> <span data-ttu-id="ba9a9-269">Model Oluşturucu Ayrıca, modelinizi işlem içinde görmek için çalıştırabileceğiniz bir örnek konsol uygulaması da ekler.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-269">Model Builder also adds a sample console app that you can run to see your model in action.</span></span>

<span data-ttu-id="ba9a9-270">Ayrıca model Oluşturucu, modeli oluşturmak için kullanılan adımları anlayabilmeniz için modeli oluşturan kodu çıktı.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-270">In addition, Model Builder outputs the code that generated the model, so that you can understand the steps used to generate the model.</span></span> <span data-ttu-id="ba9a9-271">Modelinize yeni verilerle yeniden eğitebilmeniz için model eğitim kodunu da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba9a9-271">You can also use the model training code to retrain your model with new data.</span></span>

## <a name="whats-next"></a><span data-ttu-id="ba9a9-272">Sırada ne var?</span><span class="sxs-lookup"><span data-stu-id="ba9a9-272">What's next?</span></span>

<span data-ttu-id="ba9a9-273">Model Oluşturucu Visual Studio uzantısını [yükler](how-to-guides/install-model-builder.md)</span><span class="sxs-lookup"><span data-stu-id="ba9a9-273">[Install](how-to-guides/install-model-builder.md) the Model Builder Visual Studio extension</span></span>

<span data-ttu-id="ba9a9-274">[Fiyat tahmini veya herhangi bir gerileme senaryosu](tutorials/predict-prices-with-model-builder.md) deneyin</span><span class="sxs-lookup"><span data-stu-id="ba9a9-274">Try [price prediction or any regression scenario](tutorials/predict-prices-with-model-builder.md)</span></span>
