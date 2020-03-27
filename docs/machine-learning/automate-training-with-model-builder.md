---
title: Model Oluşturucu nedir ve nasıl çalışır?
description: Otomatik olarak bir makine öğrenme modeli eğitmek için ML.NET Model Builder nasıl kullanılır
ms.date: 03/25/2020
ms.custom: overview, mlnet-tooling
ms.openlocfilehash: 9cf66455109908ebd9fc10e62cf4f067609b57d9
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344782"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a><span data-ttu-id="363e8-103">Model Oluşturucu nedir ve nasıl çalışır?</span><span class="sxs-lookup"><span data-stu-id="363e8-103">What is Model Builder and how does it work?</span></span>

<span data-ttu-id="363e8-104">ML.NET Model Builder, özel makine öğrenme modelleri oluşturmak, eğitmek ve dağıtmak için sezgisel bir grafik Görsel Stüdyo uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="363e8-104">ML.NET Model Builder is an intuitive graphical Visual Studio extension to build, train, and deploy custom machine learning models.</span></span>

<span data-ttu-id="363e8-105">Model Builder, senaryonuza en uygun algoritmayı bulmanıza yardımcı olmak için farklı makine öğrenimi algoritmalarını ve ayarlarını keşfetmek için otomatik makine öğrenimi (AutoML) kullanır.</span><span class="sxs-lookup"><span data-stu-id="363e8-105">Model Builder uses automated machine learning (AutoML) to explore different machine learning algorithms and settings to help you find the one that best suits your scenario.</span></span>

<span data-ttu-id="363e8-106">Model Builder'ı kullanmak için makine öğrenimi uzmanlığına ihtiyacınız yoktur.</span><span class="sxs-lookup"><span data-stu-id="363e8-106">You don't need machine learning expertise to use Model Builder.</span></span> <span data-ttu-id="363e8-107">İhtiyacınız olan tek şey bazı veriler ve çözmeniz gereken bir sorun.</span><span class="sxs-lookup"><span data-stu-id="363e8-107">All you need is some data, and a problem to solve.</span></span> <span data-ttu-id="363e8-108">Model Oluşturucu, modeli .NET uygulamanıza eklemek için kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="363e8-108">Model Builder generates the code to add the model to your .NET application.</span></span>

![Model Builder Visual Studio uzantısı kullanıcı arabirimi animasyon](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> <span data-ttu-id="363e8-110">Model Oluşturucu şu anda Önizleme'de.</span><span class="sxs-lookup"><span data-stu-id="363e8-110">Model Builder is currently in Preview.</span></span>

## <a name="scenario"></a><span data-ttu-id="363e8-111">Senaryo</span><span class="sxs-lookup"><span data-stu-id="363e8-111">Scenario</span></span>

<span data-ttu-id="363e8-112">Uygulamanız için bir makine öğrenme modeli oluşturmak için Model Oluşturucu'ya birçok farklı senaryo getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="363e8-112">You can bring many different scenarios to Model Builder, to generate a machine learning model for your application.</span></span>

<span data-ttu-id="363e8-113">Senaryo, verilerinizi kullanarak yapmak istediğiniz tahmin türünün açıklamasıdır.</span><span class="sxs-lookup"><span data-stu-id="363e8-113">A scenario is a description of the type of prediction you want to make using your data.</span></span> <span data-ttu-id="363e8-114">Örnek:</span><span class="sxs-lookup"><span data-stu-id="363e8-114">For example:</span></span>

- <span data-ttu-id="363e8-115">geçmiş satış verilerine dayalı gelecekteki ürün satış hacmini tahmin etme</span><span class="sxs-lookup"><span data-stu-id="363e8-115">predict future product sales volume based on historical sales data</span></span>
- <span data-ttu-id="363e8-116">müşteri yorumlarına göre duyguları olumlu veya olumsuz olarak sınıflandırmak</span><span class="sxs-lookup"><span data-stu-id="363e8-116">classify sentiments as positive or negative based on customer reviews</span></span>
- <span data-ttu-id="363e8-117">bir bankacılık işleminin sahte olup olmadığını algılama</span><span class="sxs-lookup"><span data-stu-id="363e8-117">detect whether a banking transaction is fraudulent</span></span>
- <span data-ttu-id="363e8-118">müşteri geri bildirim sorunlarını şirketinizdeki doğru ekibe yönlendirin</span><span class="sxs-lookup"><span data-stu-id="363e8-118">route customer feedback issues to the correct team in your company</span></span>

### <a name="which-machine-learning-scenario-is-right-for-me"></a><span data-ttu-id="363e8-119">Hangi makine öğrenme senaryosu benim için doğru?</span><span class="sxs-lookup"><span data-stu-id="363e8-119">Which machine learning scenario is right for me?</span></span>

<span data-ttu-id="363e8-120">Model Oluşturucu'da bir senaryo seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="363e8-120">In Model Builder, you need to select a scenario.</span></span> <span data-ttu-id="363e8-121">Senaryonun türü, ne tür bir tahmin oluşturmaya çalıştığınıza bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="363e8-121">The type of scenario depends on what type of prediction you are trying to make.</span></span>

#### <a name="text-classification"></a><span data-ttu-id="363e8-122">Metin sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="363e8-122">Text classification</span></span>

<span data-ttu-id="363e8-123">Sınıflandırma, verileri kategorilere ayırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="363e8-123">Classification is used to categorize data into categories.</span></span>

![Sahtekarlık tespiti, risk azaltma ve uygulama taraması dahil olmak üzere ikili sınıflandırma örneklerini gösteren diyagram](media/binary-classification-examples.png)

![Belge ve ürün sınıflandırması, destek bileti yönlendirmesi ve müşteri sorunu önceliklendirmesi dahil olmak üzere çok sınıflı sınıflandırma örnekleri](media/multiclass-classification-examples.png)

#### <a name="value-prediction"></a><span data-ttu-id="363e8-126">Değer tahmini</span><span class="sxs-lookup"><span data-stu-id="363e8-126">Value prediction</span></span>

<span data-ttu-id="363e8-127">Regresyon sayıları tahmin etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="363e8-127">Regression is used to predict numbers.</span></span>

![Fiyat tahmini, satış tahmini ve tahmine dayalı bakım gibi regresyon örneklerini gösteren diyagram](media/regression-examples.png)

#### <a name="image-classification"></a><span data-ttu-id="363e8-129">Resimleri sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="363e8-129">Image classification</span></span>

<span data-ttu-id="363e8-130">Resim sınıflandırması, farklı kategorilerdeki görüntüleri tanımlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="363e8-130">Image classification can be used to identify images of different categories.</span></span> <span data-ttu-id="363e8-131">Örneğin, arazi veya hayvan veya üretim kusurları farklı türleri.</span><span class="sxs-lookup"><span data-stu-id="363e8-131">For example, different types of terrain or animals or manufacturing defects.</span></span>

<span data-ttu-id="363e8-132">Bir resim setiniz varsa ve görüntüleri farklı kategorilere sınıflandırmak istiyorsanız görüntü sınıflandırma senaryosunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="363e8-132">You can use the image classification scenario if you have a set of images, and you want to classify the images into different categories.</span></span>

#### <a name="recommendation"></a><span data-ttu-id="363e8-133">Öneri</span><span class="sxs-lookup"><span data-stu-id="363e8-133">Recommendation</span></span>

<span data-ttu-id="363e8-134">Öneri senaryosu, beğenmelerinin ve beğenmedikleri öğenin diğer kullanıcılarla ne kadar benzer olduğuna bağlı olarak, belirli bir kullanıcı için önerilen öğelerin listesini öngörür.</span><span class="sxs-lookup"><span data-stu-id="363e8-134">The recommendation scenario predicts a list of suggested items for a particular user, based on how similar their likes and dislikes are to other users'.</span></span>

<span data-ttu-id="363e8-135">Bir kullanıcı kümesiniz ve satın alınacak öğeler, filmler, kitaplar veya TV programları gibi bir dizi "ürün" ve kullanıcının bu ürünlerin "derecelendirmeleri" kümesi varsa, öneri senaryosunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="363e8-135">You can use the recommendation scenario when you have a set of users and a set of "products", such as items to purchase, movies, books, or TV shows, along with a set of users' "ratings" of those products.</span></span>

## <a name="environment"></a><span data-ttu-id="363e8-136">Ortam</span><span class="sxs-lookup"><span data-stu-id="363e8-136">Environment</span></span>

<span data-ttu-id="363e8-137">Makine öğrenimi modelinizi makinenizde veya Azure'daki bulutta yerel olarak eğitebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="363e8-137">You can train your machine learning model locally on your machine or in the cloud on Azure.</span></span>

<span data-ttu-id="363e8-138">Yerel olarak eğitim aldığınızda, bilgisayar kaynaklarınızın (CPU, bellek ve disk) kısıtlamaları içinde çalışırsınız.</span><span class="sxs-lookup"><span data-stu-id="363e8-138">When you train locally, you work within the constraints of your computer resources (CPU, memory, and disk).</span></span> <span data-ttu-id="363e8-139">Bulutta eğitim aldığınızda, kaynaklarınızı senaryonuzun taleplerini karşılamak üzere ölçeklendirebilirsiniz, özellikle de büyük veri kümeleri için.</span><span class="sxs-lookup"><span data-stu-id="363e8-139">When you train in the cloud, you can scale up your resources to meet the demands of your scenario, especially for large datasets.</span></span>

<span data-ttu-id="363e8-140">Yerel eğitim tüm senaryolar için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="363e8-140">Local training is supported for all scenarios.</span></span>

<span data-ttu-id="363e8-141">Azure eğitimi Görüntü Sınıflandırması için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="363e8-141">Azure training is supported for Image Classification.</span></span>

## <a name="data"></a><span data-ttu-id="363e8-142">Veri</span><span class="sxs-lookup"><span data-stu-id="363e8-142">Data</span></span>

<span data-ttu-id="363e8-143">Senaryonuzu seçtikten sonra, Model Oluşturucu sizden bir veri kümesi sağlamanızı ister.</span><span class="sxs-lookup"><span data-stu-id="363e8-143">Once you have chosen your scenario, Model Builder asks you to provide a dataset.</span></span> <span data-ttu-id="363e8-144">Veriler, senaryonuz için en iyi modeli eğitmek, değerlendirmek ve seçmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="363e8-144">The data is used to train, evaluate, and choose the best model for your scenario.</span></span>

![Model Oluşturucu adımlarını gösteren diyagram](media/model-builder-steps.png)

<span data-ttu-id="363e8-146">Model Oluşturucu,.tsv, .csv, .txt biçimlerinde ve SQL veritabanı biçiminde veri kümelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="363e8-146">Model Builder supports datasets in .tsv, .csv, .txt formats, as well as SQL database format.</span></span> <span data-ttu-id="363e8-147">.txt dosyanız varsa, sütunlar ile `,` `;` ayrılmalı veya `/t` dosyanın bir üstbilgi satırı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="363e8-147">If you have a .txt file, columns should be separated with `,`, `;` or `/t` and the file must have a header row.</span></span>

<span data-ttu-id="363e8-148">Veri kümesi resimlerden oluşuyorsa, desteklenen dosya `.jpg` türleri `.png`ve.</span><span class="sxs-lookup"><span data-stu-id="363e8-148">If the dataset is made up of images, the supported file types are `.jpg` and `.png`.</span></span>

<span data-ttu-id="363e8-149">Daha fazla bilgi için [Model Oluşturucu'ya Yük eğitim verilerine](how-to-guides/load-data-model-builder.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="363e8-149">For more information, see [Load training data into Model Builder](how-to-guides/load-data-model-builder.md).</span></span>

### <a name="choose-the-output-to-predict-label"></a><span data-ttu-id="363e8-150">Tahmin etmek için çıktıyı seçin (etiket)</span><span class="sxs-lookup"><span data-stu-id="363e8-150">Choose the output to predict (label)</span></span>

<span data-ttu-id="363e8-151">Veri kümesi, eğitim örnekleri satırları ve özniteliklersütunları tablosudur.</span><span class="sxs-lookup"><span data-stu-id="363e8-151">A dataset is a table of rows of training examples, and columns of attributes.</span></span> <span data-ttu-id="363e8-152">Her satırda:</span><span class="sxs-lookup"><span data-stu-id="363e8-152">Each row has:</span></span>

- <span data-ttu-id="363e8-153">bir **etiket** (tahmin etmek istediğiniz öznitelik)</span><span class="sxs-lookup"><span data-stu-id="363e8-153">a **label** (the attribute that you want to predict)</span></span>
- <span data-ttu-id="363e8-154">**özellikleri** (etiketi tahmin etmek için giriş olarak kullanılan öznitelikler).</span><span class="sxs-lookup"><span data-stu-id="363e8-154">**features** (attributes that are used as inputs to predict the label).</span></span>

<span data-ttu-id="363e8-155">Ev fiyatı tahmin senaryosu için özellikler şu şekilde olabilir:</span><span class="sxs-lookup"><span data-stu-id="363e8-155">For the house-price prediction scenario, the features could be:</span></span>

- <span data-ttu-id="363e8-156">evin kare görüntüleri</span><span class="sxs-lookup"><span data-stu-id="363e8-156">the square footage of the house</span></span>
- <span data-ttu-id="363e8-157">yatak odası ve banyo sayısı</span><span class="sxs-lookup"><span data-stu-id="363e8-157">the number of bedrooms and bathrooms</span></span>
- <span data-ttu-id="363e8-158">posta kodu</span><span class="sxs-lookup"><span data-stu-id="363e8-158">the zip code</span></span>

<span data-ttu-id="363e8-159">Etiket kare görüntüleri, yatak odası ve banyo değerleri ve posta kodu bu satır için tarihsel ev fiyatıdır.</span><span class="sxs-lookup"><span data-stu-id="363e8-159">The label is the historical house price for that row of square footage, bedroom, and bathroom values and zip code.</span></span>

![Boyut odaları posta kodu ve fiyat etiketinden oluşan özelliklere sahip ev fiyat verilerinin satır ve sütunlarını gösteren tablo](media/model-builder-data.png)

### <a name="example-datasets"></a><span data-ttu-id="363e8-161">Örnek veri kümeleri</span><span class="sxs-lookup"><span data-stu-id="363e8-161">Example datasets</span></span>

<span data-ttu-id="363e8-162">Henüz kendi verileriniz yoksa, şu veri kümelerinden birini deneyin:</span><span class="sxs-lookup"><span data-stu-id="363e8-162">If you don't have your own data yet, try out one of these datasets:</span></span>

|<span data-ttu-id="363e8-163">Senaryo</span><span class="sxs-lookup"><span data-stu-id="363e8-163">Scenario</span></span>|<span data-ttu-id="363e8-164">Örnek</span><span class="sxs-lookup"><span data-stu-id="363e8-164">Example</span></span>|<span data-ttu-id="363e8-165">Veri</span><span class="sxs-lookup"><span data-stu-id="363e8-165">Data</span></span>|<span data-ttu-id="363e8-166">Etiketle</span><span class="sxs-lookup"><span data-stu-id="363e8-166">Label</span></span>|<span data-ttu-id="363e8-167">Özellikler</span><span class="sxs-lookup"><span data-stu-id="363e8-167">Features</span></span>|
|-|-|-|-|-|
|<span data-ttu-id="363e8-168">Sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="363e8-168">Classification</span></span>|<span data-ttu-id="363e8-169">Satış anormalliklerini tahmin etme</span><span class="sxs-lookup"><span data-stu-id="363e8-169">Predict sales anomalies</span></span>|[<span data-ttu-id="363e8-170">ürün satış verileri</span><span class="sxs-lookup"><span data-stu-id="363e8-170">product sales data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|<span data-ttu-id="363e8-171">Ürün Satışları</span><span class="sxs-lookup"><span data-stu-id="363e8-171">Product Sales</span></span>|<span data-ttu-id="363e8-172">Ay</span><span class="sxs-lookup"><span data-stu-id="363e8-172">Month</span></span>|
||<span data-ttu-id="363e8-173">Web sitesi yorumlarının duyarlılığını tahmin edin</span><span class="sxs-lookup"><span data-stu-id="363e8-173">Predict sentiment of website comments</span></span>|[<span data-ttu-id="363e8-174">web sitesi yorum verileri</span><span class="sxs-lookup"><span data-stu-id="363e8-174">website comment data</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|<span data-ttu-id="363e8-175">Etiket (0 negatif duygu, 1 pozitif)</span><span class="sxs-lookup"><span data-stu-id="363e8-175">Label (0 when negative sentiment, 1 when positive)</span></span>|<span data-ttu-id="363e8-176">Yorum, Yıl</span><span class="sxs-lookup"><span data-stu-id="363e8-176">Comment, Year</span></span>|
||<span data-ttu-id="363e8-177">Sahte kredi kartı hareketlerini tahmin etme</span><span class="sxs-lookup"><span data-stu-id="363e8-177">Predict fraudulent credit card transactions</span></span>|[<span data-ttu-id="363e8-178">kredi kartı verileri</span><span class="sxs-lookup"><span data-stu-id="363e8-178">credit card data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|<span data-ttu-id="363e8-179">Sınıf (1 sahte, 0 aksi takdirde)</span><span class="sxs-lookup"><span data-stu-id="363e8-179">Class (1 when fraudulent, 0 otherwise)</span></span>|<span data-ttu-id="363e8-180">Tutar, V1-V28 (anonimleştirilmiş özellikler)</span><span class="sxs-lookup"><span data-stu-id="363e8-180">Amount, V1-V28 (anonymized features)</span></span>|
||<span data-ttu-id="363e8-181">GitHub deposundaki sorunun türünü tahmin etme</span><span class="sxs-lookup"><span data-stu-id="363e8-181">Predict the type of issue in a GitHub repository</span></span>|[<span data-ttu-id="363e8-182">GitHub sorun verileri</span><span class="sxs-lookup"><span data-stu-id="363e8-182">GitHub issue data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|<span data-ttu-id="363e8-183">Alan</span><span class="sxs-lookup"><span data-stu-id="363e8-183">Area</span></span>|<span data-ttu-id="363e8-184">Başlık, Açıklama</span><span class="sxs-lookup"><span data-stu-id="363e8-184">Title, Description</span></span>|
|<span data-ttu-id="363e8-185">Değer tahmini</span><span class="sxs-lookup"><span data-stu-id="363e8-185">Value prediction</span></span>|<span data-ttu-id="363e8-186">Taksi ücret fiyatını tahmin edin</span><span class="sxs-lookup"><span data-stu-id="363e8-186">Predict taxi fare price</span></span>|[<span data-ttu-id="363e8-187">taksi ücreti verileri</span><span class="sxs-lookup"><span data-stu-id="363e8-187">taxi fare data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|<span data-ttu-id="363e8-188">Ücret</span><span class="sxs-lookup"><span data-stu-id="363e8-188">Fare</span></span>|<span data-ttu-id="363e8-189">Yolculuk süresi, mesafe</span><span class="sxs-lookup"><span data-stu-id="363e8-189">Trip time, distance</span></span>|
|<span data-ttu-id="363e8-190">Resimleri sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="363e8-190">Image classification</span></span>|<span data-ttu-id="363e8-191">Sorunun kategorisini tahmin etme</span><span class="sxs-lookup"><span data-stu-id="363e8-191">Predict the category of an issue</span></span>|[<span data-ttu-id="363e8-192">çiçek görüntüleri</span><span class="sxs-lookup"><span data-stu-id="363e8-192">flower images</span></span>](http://download.tensorflow.org/example_images/flower_photos.tgz)|<span data-ttu-id="363e8-193">Çiçek türü: papatya, karahindiba, gül, ayçiçeği, lale</span><span class="sxs-lookup"><span data-stu-id="363e8-193">The type of flower: daisy, dandelion, roses, sunflowers, tulips</span></span>|<span data-ttu-id="363e8-194">Görüntü verilerinin kendisi</span><span class="sxs-lookup"><span data-stu-id="363e8-194">The image data itself</span></span>|
|<span data-ttu-id="363e8-195">Öneri</span><span class="sxs-lookup"><span data-stu-id="363e8-195">Recommendation</span></span>|<span data-ttu-id="363e8-196">Birinin beğeneceği filmleri tahmin edin</span><span class="sxs-lookup"><span data-stu-id="363e8-196">Predict movies that someone will like</span></span>|[<span data-ttu-id="363e8-197">film reytingleri</span><span class="sxs-lookup"><span data-stu-id="363e8-197">movie ratings</span></span>](http://files.grouplens.org/datasets/movielens/ml-latest-small.zip)|<span data-ttu-id="363e8-198">Kullanıcılar, Filmler</span><span class="sxs-lookup"><span data-stu-id="363e8-198">Users, Movies</span></span>|<span data-ttu-id="363e8-199">Derecelendirmeler</span><span class="sxs-lookup"><span data-stu-id="363e8-199">Ratings</span></span>|

## <a name="train"></a><span data-ttu-id="363e8-200">Eğitim</span><span class="sxs-lookup"><span data-stu-id="363e8-200">Train</span></span>

<span data-ttu-id="363e8-201">Senaryonuzu, verilerinizi ve etiketinizi seçtikten sonra Model Oluşturucu modeli çalıştırAn modeli çalıştırZ.</span><span class="sxs-lookup"><span data-stu-id="363e8-201">Once you select your scenario, data, and label, Model Builder trains the model.</span></span>

### <a name="what-is-training"></a><span data-ttu-id="363e8-202">Eğitim nedir?</span><span class="sxs-lookup"><span data-stu-id="363e8-202">What is training?</span></span>

<span data-ttu-id="363e8-203">Eğitim, Model Oluşturucu'nun modelinize senaryonuzla ilgili soruları nasıl yanıtlayabildiğini öğrettiği otomatik bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="363e8-203">Training is an automatic process by which Model Builder teaches your model how to answer questions for your scenario.</span></span> <span data-ttu-id="363e8-204">Bir kez eğitildikten sonra, modeliniz daha önce görmediği giriş verileriyle öngörülerde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="363e8-204">Once trained, your model can make predictions with input data that it has not seen before.</span></span> <span data-ttu-id="363e8-205">Örneğin, ev fiyatları tahmin ediyorsanız ve yeni bir ev piyasaya geliyor, onun satış fiyatı tahmin edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="363e8-205">For example, if you are predicting house prices and a new house comes on the market, you can predict its sale price.</span></span>

<span data-ttu-id="363e8-206">Model Oluşturucu otomatik makine öğrenimi (AutoML) kullandığından, eğitim sırasında sizden herhangi bir giriş veya asetama gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="363e8-206">Because Model Builder uses automated machine learning (AutoML), it does not require any input or tuning from you during training.</span></span>

### <a name="how-long-should-i-train-for"></a><span data-ttu-id="363e8-207">Ne kadar süre antrenman yapmalıyım?</span><span class="sxs-lookup"><span data-stu-id="363e8-207">How long should I train for?</span></span>

<span data-ttu-id="363e8-208">Model Oluşturucu, size en iyi performans gösteren modeli bulmak için birden çok modeli keşfetmek için AutoML kullanır.</span><span class="sxs-lookup"><span data-stu-id="363e8-208">Model Builder uses AutoML to explore multiple models to find you the best performing model.</span></span>

<span data-ttu-id="363e8-209">Daha uzun eğitim süreleri, AutoML'nin daha geniş bir ayarı yelpazesine sahip daha fazla modeli keşfetmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="363e8-209">Longer training periods allow AutoML to explore more models with a wider range of settings.</span></span>

<span data-ttu-id="363e8-210">Aşağıdaki tablo, yerel bir makinede örnek veri kümeleri paketi için iyi performans elde etmek için geçen ortalama süreyi özetleyin.</span><span class="sxs-lookup"><span data-stu-id="363e8-210">The table below summarizes the average time taken to get good performance for a suite of example datasets, on a local machine.</span></span>

|<span data-ttu-id="363e8-211">Dataset boyutu</span><span class="sxs-lookup"><span data-stu-id="363e8-211">Dataset size</span></span>|<span data-ttu-id="363e8-212">Eğitim için ortalama süre</span><span class="sxs-lookup"><span data-stu-id="363e8-212">Average time to train</span></span>|
|------------|---------------------|
|<span data-ttu-id="363e8-213">0 - 10 MB</span><span class="sxs-lookup"><span data-stu-id="363e8-213">0 - 10 MB</span></span>|<span data-ttu-id="363e8-214">10 sn</span><span class="sxs-lookup"><span data-stu-id="363e8-214">10 sec</span></span>|
|<span data-ttu-id="363e8-215">10 - 100 MB</span><span class="sxs-lookup"><span data-stu-id="363e8-215">10 - 100 MB</span></span>|<span data-ttu-id="363e8-216">10 dk</span><span class="sxs-lookup"><span data-stu-id="363e8-216">10 min</span></span>|
|<span data-ttu-id="363e8-217">100 - 500 MB</span><span class="sxs-lookup"><span data-stu-id="363e8-217">100 - 500 MB</span></span>|<span data-ttu-id="363e8-218">30 dk</span><span class="sxs-lookup"><span data-stu-id="363e8-218">30 min</span></span>|
|<span data-ttu-id="363e8-219">500 - 1 GB Arası</span><span class="sxs-lookup"><span data-stu-id="363e8-219">500 - 1 GB</span></span>|<span data-ttu-id="363e8-220">60 dk</span><span class="sxs-lookup"><span data-stu-id="363e8-220">60 min</span></span>|
|<span data-ttu-id="363e8-221">1 GB+</span><span class="sxs-lookup"><span data-stu-id="363e8-221">1 GB+</span></span>|<span data-ttu-id="363e8-222">3+ saat</span><span class="sxs-lookup"><span data-stu-id="363e8-222">3+ hours</span></span>|

<span data-ttu-id="363e8-223">Bu sayılar sadece bir rehberdir.</span><span class="sxs-lookup"><span data-stu-id="363e8-223">These numbers are a guide only.</span></span> <span data-ttu-id="363e8-224">Eğitimin tam uzunluğu şuna bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="363e8-224">The exact length of training is dependent on:</span></span>

- <span data-ttu-id="363e8-225">modele giriş olarak kullanılan özellik (sütun) sayısı</span><span class="sxs-lookup"><span data-stu-id="363e8-225">the number of features (columns) being used to as input to the model</span></span>
- <span data-ttu-id="363e8-226">sütun türü</span><span class="sxs-lookup"><span data-stu-id="363e8-226">the type of columns</span></span>
- <span data-ttu-id="363e8-227">ML görev</span><span class="sxs-lookup"><span data-stu-id="363e8-227">the ML task</span></span>
- <span data-ttu-id="363e8-228">eğitim için kullanılan makinenin CPU, disk ve bellek performansı</span><span class="sxs-lookup"><span data-stu-id="363e8-228">the CPU, disk, and memory performance of the machine used for training</span></span>

## <a name="evaluate"></a><span data-ttu-id="363e8-229">Değerlendir</span><span class="sxs-lookup"><span data-stu-id="363e8-229">Evaluate</span></span>

<span data-ttu-id="363e8-230">Değerlendirme, modelinizin ne kadar iyi olduğunu ölçme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="363e8-230">Evaluation is the process of measuring how good your model is.</span></span> <span data-ttu-id="363e8-231">Model Oluşturucu, yeni test verileriyle öngörülerde bulunmak için eğitilmiş modeli kullanır ve ardından tahminlerin ne kadar iyi olduğunu ölçer.</span><span class="sxs-lookup"><span data-stu-id="363e8-231">Model Builder uses the trained model to make predictions with new test data, and then measures how good the predictions are.</span></span>

<span data-ttu-id="363e8-232">Model Oluşturucu, eğitim verilerini bir eğitim kümesine ve test kümesine böler.</span><span class="sxs-lookup"><span data-stu-id="363e8-232">Model Builder splits the training data into a training set and a test set.</span></span> <span data-ttu-id="363e8-233">Eğitim verileri (%80) modelinizi ve test verilerini eğitmek için kullanılır (%20) modelinizi değerlendirmek için geri tutulur.</span><span class="sxs-lookup"><span data-stu-id="363e8-233">The training data (80%) is used to train your model and the test data (20%) is held back to evaluate your model.</span></span>

### <a name="how-do-i-understand-my-model-performance"></a><span data-ttu-id="363e8-234">Model performansımı nasıl anlarım?</span><span class="sxs-lookup"><span data-stu-id="363e8-234">How do I understand my model performance?</span></span>

<span data-ttu-id="363e8-235">Bir senaryo, makine öğrenimi görevine eş ler.</span><span class="sxs-lookup"><span data-stu-id="363e8-235">A scenario maps to a machine learning task.</span></span> <span data-ttu-id="363e8-236">Her ML görevinin kendi değerlendirme ölçütleri kümesi vardır.</span><span class="sxs-lookup"><span data-stu-id="363e8-236">Each ML task has its own set of evaluation metrics.</span></span>

#### <a name="value-prediction"></a><span data-ttu-id="363e8-237">Değer tahmini</span><span class="sxs-lookup"><span data-stu-id="363e8-237">Value prediction</span></span>

<span data-ttu-id="363e8-238">Değer tahmin sorunları için varsayılan metrik RSquared' dir, RSquared değeri 0 ile 1 arasında değişir.</span><span class="sxs-lookup"><span data-stu-id="363e8-238">The default metric for value prediction problems is RSquared, the value of RSquared ranges between 0 and 1.</span></span> <span data-ttu-id="363e8-239">1 mümkün olan en iyi değer dir veya başka bir deyişle rsquared değeri daha yakın 1 modeli daha iyi performans.</span><span class="sxs-lookup"><span data-stu-id="363e8-239">1 is the best possible value or in other words the closer the value of RSquared to 1 the better your model is performing.</span></span>

<span data-ttu-id="363e8-240">Mutlak kayıp, kare-kayıp ve RMS kaybı gibi bildirilen diğer ölçümler, modelinizin nasıl performans gösterdiğini anlamak ve diğer değer tahmin modelleri ile karşılaştırmak için kullanılabilecek ek ölçümlerdir.</span><span class="sxs-lookup"><span data-stu-id="363e8-240">Other metrics reported such as absolute-loss, squared-loss, and RMS loss are additional metrics, which can be used to understand how your model is performing and comparing it against other value prediction models.</span></span>

#### <a name="classification-2-categories"></a><span data-ttu-id="363e8-241">Sınıflandırma (2 kategori)</span><span class="sxs-lookup"><span data-stu-id="363e8-241">Classification (2 categories)</span></span>

<span data-ttu-id="363e8-242">Sınıflandırma sorunları için varsayılan metrik doğruluktır.</span><span class="sxs-lookup"><span data-stu-id="363e8-242">The default metric for classification problems is accuracy.</span></span> <span data-ttu-id="363e8-243">Doğruluk, modelinizin test veri kümesi üzerinde yaptığı doğru tahminlerin oranını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="363e8-243">Accuracy defines the proportion of correct predictions your model is making over the test dataset.</span></span> <span data-ttu-id="363e8-244">%100 veya %1.0'a ne kadar yakınsa o kadar iyi olur.</span><span class="sxs-lookup"><span data-stu-id="363e8-244">The closer to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="363e8-245">AUC (eğrinin altındaki alan) gibi bildirilen diğer ölçümler, modellerin kabul edilememesi için doğru pozitif oranı ve yanlış pozitif oranı ölçen 0,50'den büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="363e8-245">Other metrics reported such as AUC (Area under the curve), which measures the true positive rate vs. the false positive rate should be greater than 0.50 for models to be acceptable.</span></span>

<span data-ttu-id="363e8-246">Hassasve Geri Çağırma arasındaki dengeyi kontrol etmek için F1 puanı gibi ek ölçümler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="363e8-246">Additional metrics like F1 score can be used to control the balance between Precision and Recall.</span></span>

#### <a name="classification-3-categories"></a><span data-ttu-id="363e8-247">Sınıflandırma (3+ kategori)</span><span class="sxs-lookup"><span data-stu-id="363e8-247">Classification (3+ categories)</span></span>

<span data-ttu-id="363e8-248">Çok sınıflı sınıflandırma için varsayılan metrik Mikro Doğruluk'tır.</span><span class="sxs-lookup"><span data-stu-id="363e8-248">The default metric for Multi-class classification is Micro Accuracy.</span></span> <span data-ttu-id="363e8-249">Mikro Doğruluk %100 veya %1.0'a ne kadar yakınsa o kadar iyi olur.</span><span class="sxs-lookup"><span data-stu-id="363e8-249">The closer the Micro Accuracy to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="363e8-250">Çok sınıflı sınıflandırma için bir diğer önemli metrik makro-doğruluk, Mikro-doğruluk benzer 1.0 daha iyi.</span><span class="sxs-lookup"><span data-stu-id="363e8-250">Another important metric for Multi-class classification is Macro-accuracy, similar to Micro-accuracy the closer to 1.0 the better it is.</span></span> <span data-ttu-id="363e8-251">Doğruluk bu iki tür hakkında düşünmek için iyi bir yoldur:</span><span class="sxs-lookup"><span data-stu-id="363e8-251">A good way to think about these two types of accuracy is:</span></span>

- <span data-ttu-id="363e8-252">Mikro doğruluk: Gelen bilet ne sıklıkta doğru takıma sınıflandırılır?</span><span class="sxs-lookup"><span data-stu-id="363e8-252">Micro-accuracy: How often does an incoming ticket get classified to the right team?</span></span>
- <span data-ttu-id="363e8-253">Makro doğruluk: Ortalama bir takım için gelen bilet takım için ne sıklıkta doğrudur?</span><span class="sxs-lookup"><span data-stu-id="363e8-253">Macro-accuracy: For an average team, how often is an incoming ticket correct for their team?</span></span>

### <a name="more-information-on-evaluation-metrics"></a><span data-ttu-id="363e8-254">Değerlendirme ölçümleri hakkında daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="363e8-254">More information on evaluation metrics</span></span>

<span data-ttu-id="363e8-255">Daha fazla bilgi için [model değerlendirme ölçümlerine](resources/metrics.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="363e8-255">For more information, see [model evaluation metrics](resources/metrics.md).</span></span>

## <a name="improve"></a><span data-ttu-id="363e8-256">Geliştirmek</span><span class="sxs-lookup"><span data-stu-id="363e8-256">Improve</span></span>

<span data-ttu-id="363e8-257">Model performans puanınız istediğiniz kadar iyi değilse, şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="363e8-257">If your model performance score is not as good as you want it to be, you can:</span></span>

- <span data-ttu-id="363e8-258">Daha uzun bir süre için tren.</span><span class="sxs-lookup"><span data-stu-id="363e8-258">Train for a longer period of time.</span></span> <span data-ttu-id="363e8-259">Daha fazla zaman ile, daha fazla algoritma ve ayarları ile otomatik makine öğrenme motoru deneyleri.</span><span class="sxs-lookup"><span data-stu-id="363e8-259">With more time, the automated machine learning engine experiments with more algorithms and settings.</span></span>

- <span data-ttu-id="363e8-260">Daha fazla veri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="363e8-260">Add more data.</span></span> <span data-ttu-id="363e8-261">Bazen veri miktarı yüksek kaliteli bir makine öğrenme modeli eğitmek için yeterli değildir.</span><span class="sxs-lookup"><span data-stu-id="363e8-261">Sometimes the amount of data is not sufficient to train a high-quality machine learning model.</span></span>

- <span data-ttu-id="363e8-262">Verilerinizi dengeleyin.</span><span class="sxs-lookup"><span data-stu-id="363e8-262">Balance your data.</span></span> <span data-ttu-id="363e8-263">Sınıflandırma görevleri için, eğitim kümesinin kategoriler arasında dengeli olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="363e8-263">For classification tasks, make sure that the training set is balanced across the categories.</span></span> <span data-ttu-id="363e8-264">Örneğin, 100 eğitim örneği için dört sınıfınız varsa ve iki birinci sınıf (tag1 ve tag2) 90 kayıt için kullanılıyorsa, ancak diğer ikisi (tag3 ve tag4) yalnızca kalan 10 kayıtta kullanılıyorsa, dengeli veri eksikliği modelinizin tag3 veya tag4'u doğru tahmin edin.</span><span class="sxs-lookup"><span data-stu-id="363e8-264">For example, if you have four classes for 100 training examples, and the two first classes (tag1 and tag2) are used for 90 records, but the other two (tag3 and tag4) are only used on the remaining 10 records, the lack of balanced data may cause your model to struggle to correctly predict tag3 or tag4.</span></span>

## <a name="code"></a><span data-ttu-id="363e8-265">Kod</span><span class="sxs-lookup"><span data-stu-id="363e8-265">Code</span></span>

<span data-ttu-id="363e8-266">Değerlendirme aşamasından sonra, Model Oluşturucu bir model dosyası ve uygulamanıza modeli eklemek için kullanabileceğiniz kod çıktır.</span><span class="sxs-lookup"><span data-stu-id="363e8-266">After the evaluation phase, Model Builder outputs a model file, and code that you can use to add the model to your application.</span></span> <span data-ttu-id="363e8-267">ML.NET modelleri zip dosyası olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="363e8-267">ML.NET models are saved as a zip file.</span></span> <span data-ttu-id="363e8-268">Modelinizi yüklemek ve kullanmak için kod çözümünüze yeni bir proje olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="363e8-268">The code to load and use your model is added as a new project in your solution.</span></span> <span data-ttu-id="363e8-269">Model Oluşturucu ayrıca, modelinizi iş başında görmek için çalıştırabileceğiniz örnek bir konsol uygulaması da ekler.</span><span class="sxs-lookup"><span data-stu-id="363e8-269">Model Builder also adds a sample console app that you can run to see your model in action.</span></span>

<span data-ttu-id="363e8-270">Ayrıca, Modeli oluşturmak için kullanılan adımları anlayabilmeniz için Modeli oluşturan kodu Model Oluşturucu çıktır.</span><span class="sxs-lookup"><span data-stu-id="363e8-270">In addition, Model Builder outputs the code that generated the model, so that you can understand the steps used to generate the model.</span></span> <span data-ttu-id="363e8-271">Modelinizi yeni verilerle yeniden eğitmek için model eğitim kodunu da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="363e8-271">You can also use the model training code to retrain your model with new data.</span></span>

## <a name="whats-next"></a><span data-ttu-id="363e8-272">Sırada ne var?</span><span class="sxs-lookup"><span data-stu-id="363e8-272">What's next?</span></span>

<span data-ttu-id="363e8-273">Model Oluşturucu Visual Studio uzantısını [yükleyin](how-to-guides/install-model-builder.md)</span><span class="sxs-lookup"><span data-stu-id="363e8-273">[Install](how-to-guides/install-model-builder.md) the Model Builder Visual Studio extension</span></span>

<span data-ttu-id="363e8-274">[Fiyat tahminini veya herhangi bir gerileme senaryosuni](tutorials/predict-prices-with-model-builder.md) deneyin</span><span class="sxs-lookup"><span data-stu-id="363e8-274">Try [price prediction or any regression scenario](tutorials/predict-prices-with-model-builder.md)</span></span>
