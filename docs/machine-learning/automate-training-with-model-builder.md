---
title: Model Oluşturucu nedir ve nasıl çalışır?
description: Otomatik olarak bir makine öğrenme modeli eğitmek için ML.NET Model Builder nasıl kullanılır
ms.date: 01/07/2020
ms.custom: overview, mlnet-tooling
ms.openlocfilehash: cff4601843ec9ca7201ea7dbdbfbcfa18f50e46e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399226"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a><span data-ttu-id="cc61c-103">Model Oluşturucu nedir ve nasıl çalışır?</span><span class="sxs-lookup"><span data-stu-id="cc61c-103">What is Model Builder and how does it work?</span></span>

<span data-ttu-id="cc61c-104">ML.NET Model Builder, özel makine öğrenme modelleri oluşturmak, eğitmek ve dağıtmak için sezgisel bir grafik Görsel Stüdyo uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="cc61c-104">ML.NET Model Builder is an intuitive graphical Visual Studio extension to build, train, and deploy custom machine learning models.</span></span>

<span data-ttu-id="cc61c-105">Model Builder, senaryonuza en uygun algoritmayı bulmanıza yardımcı olmak için farklı makine öğrenimi algoritmalarını ve ayarlarını keşfetmek için otomatik makine öğrenimi (AutoML) kullanır.</span><span class="sxs-lookup"><span data-stu-id="cc61c-105">Model Builder uses automated machine learning (AutoML) to explore different machine learning algorithms and settings to help you find the one that best suits your scenario.</span></span>

<span data-ttu-id="cc61c-106">Model Builder'ı kullanmak için makine öğrenimi uzmanlığına ihtiyacınız yoktur.</span><span class="sxs-lookup"><span data-stu-id="cc61c-106">You don't need machine learning expertise to use Model Builder.</span></span> <span data-ttu-id="cc61c-107">İhtiyacınız olan tek şey bazı veriler ve çözmeniz gereken bir sorun.</span><span class="sxs-lookup"><span data-stu-id="cc61c-107">All you need is some data, and a problem to solve.</span></span> <span data-ttu-id="cc61c-108">Model Oluşturucu, modeli .NET uygulamanıza eklemek için kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cc61c-108">Model Builder generates the code to add the model to your .NET application.</span></span>

![Model Builder Visual Studio uzantısı kullanıcı arabirimi animasyon](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> <span data-ttu-id="cc61c-110">Model Oluşturucu şu anda Önizleme'de.</span><span class="sxs-lookup"><span data-stu-id="cc61c-110">Model Builder is currently in Preview.</span></span>

## <a name="scenarios"></a><span data-ttu-id="cc61c-111">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="cc61c-111">Scenarios</span></span>

<span data-ttu-id="cc61c-112">Uygulamanız için bir makine öğrenme modeli oluşturmak için Model Oluşturucu'ya birçok farklı senaryo getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc61c-112">You can bring many different scenarios to Model Builder, to generate a machine learning model for your application.</span></span>

<span data-ttu-id="cc61c-113">Senaryo, verilerinizi kullanarak yapmak istediğiniz tahmin türünün açıklamasıdır.</span><span class="sxs-lookup"><span data-stu-id="cc61c-113">A scenario is a description of the type of prediction you want to make using your data.</span></span> <span data-ttu-id="cc61c-114">Örnek:</span><span class="sxs-lookup"><span data-stu-id="cc61c-114">For example:</span></span>

- <span data-ttu-id="cc61c-115">geçmiş satış verilerine dayalı gelecekteki ürün satış hacmini tahmin etme</span><span class="sxs-lookup"><span data-stu-id="cc61c-115">predict future product sales volume based on historical sales data</span></span>
- <span data-ttu-id="cc61c-116">müşteri yorumlarına göre duyguları olumlu veya olumsuz olarak sınıflandırmak</span><span class="sxs-lookup"><span data-stu-id="cc61c-116">classify sentiments as positive or negative based on customer reviews</span></span>
- <span data-ttu-id="cc61c-117">bir bankacılık işleminin sahte olup olmadığını algılama</span><span class="sxs-lookup"><span data-stu-id="cc61c-117">detect whether a banking transaction is fraudulent</span></span>
- <span data-ttu-id="cc61c-118">müşteri geri bildirim sorunlarını şirketinizdeki doğru ekibe yönlendirin</span><span class="sxs-lookup"><span data-stu-id="cc61c-118">route customer feedback issues to the correct team in your company</span></span>

### <a name="which-machine-learning-scenario-is-right-for-me"></a><span data-ttu-id="cc61c-119">Hangi makine öğrenme senaryosu benim için doğru?</span><span class="sxs-lookup"><span data-stu-id="cc61c-119">Which machine learning scenario is right for me?</span></span>

<span data-ttu-id="cc61c-120">Model Oluşturucu'da bir senaryo seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc61c-120">In Model Builder, you need to select a scenario.</span></span> <span data-ttu-id="cc61c-121">Senaryonun türü, ne tür bir tahmin oluşturmaya çalıştığınıza bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="cc61c-121">The type of scenario depends on what type of prediction you are trying to make.</span></span>

#### <a name="predict-a-category-when-there-are-only-two-categories"></a><span data-ttu-id="cc61c-122">Bir kategori tahmin edin (yalnızca iki kategori olduğunda)</span><span class="sxs-lookup"><span data-stu-id="cc61c-122">Predict a category (when there are only two categories)</span></span>

<span data-ttu-id="cc61c-123">İkili sınıflandırma, verileri iki kategoriye ayırmak için kullanılır (evet/hayır; pass/fail; true/false; pozitif/negatif).</span><span class="sxs-lookup"><span data-stu-id="cc61c-123">Binary classification is used to categorize data into two categories (yes/no; pass/fail; true/false; positive/negative).</span></span>

![Sahtekarlık tespiti, risk azaltma ve uygulama taraması dahil olmak üzere ikili sınıflandırma örneklerini gösteren diyagram](media/binary-classification-examples.png)

<span data-ttu-id="cc61c-125">Duyarlılık analizi, müşteri geri bildiriminin olumlu veya olumsuz duyarlılığını tahmin etmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cc61c-125">Sentiment analysis can be used to predict positive or negative sentiment of customer feedback.</span></span> <span data-ttu-id="cc61c-126">Bu ikili sınıflandırma makine öğrenme görevi bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="cc61c-126">It is an example of the binary classification machine learning task.</span></span>

<span data-ttu-id="cc61c-127">Senaryonuz iki kategoriye sınıflandırılması gerektiriyorsa, bu şablonu kendi veri kümenizle kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc61c-127">If your scenario requires classification into two categories, you can use this template with your own dataset.</span></span>

#### <a name="predict-a-category-when-there-are-three-or-more-categories"></a><span data-ttu-id="cc61c-128">Bir kategori tahmin edin (üç veya daha fazla kategori olduğunda)</span><span class="sxs-lookup"><span data-stu-id="cc61c-128">Predict a category (when there are three or more categories)</span></span>

<span data-ttu-id="cc61c-129">Çok sınıflı sınıflandırma, verileri üç veya daha fazla sınıfa kategorilere ayırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cc61c-129">Multiclass classification can be used to categorize data into three or more classes.</span></span>

![Belge ve ürün sınıflandırması, destek bileti yönlendirmesi ve müşteri sorunu önceliklendirmesi dahil olmak üzere çok sınıflı sınıflandırma örnekleri](media/multiclass-classification-examples.png)

<span data-ttu-id="cc61c-131">Sorun sınıflandırması, sorun başlığı nı ve açıklamasını kullanarak müşteri geri bildirimlerini (örneğin, GitHub'da) kategorilere ayırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cc61c-131">Issue classification can be used to categorize customer feedback (for example, on GitHub) issues using the issue title and description.</span></span> <span data-ttu-id="cc61c-132">Bu çok sınıflı sınıflandırma makine öğrenme görevi bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="cc61c-132">It is an example of the multi-class classification machine learning task.</span></span>

<span data-ttu-id="cc61c-133">Verileri üç veya daha fazla kategoriye ayırmak istiyorsanız, senaryonuz için sorun sınıflandırma şablonunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc61c-133">You can use the issue classification template for your scenario if you want to categorize data into three or more categories.</span></span>

#### <a name="predict-a-number"></a><span data-ttu-id="cc61c-134">Bir sayı tahmin etme</span><span class="sxs-lookup"><span data-stu-id="cc61c-134">Predict a number</span></span>

<span data-ttu-id="cc61c-135">Regresyon sayıları tahmin etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cc61c-135">Regression is used to predict numbers.</span></span>

![Fiyat tahmini, satış tahmini ve tahmine dayalı bakım gibi regresyon örneklerini gösteren diyagram](media/regression-examples.png)

<span data-ttu-id="cc61c-137">Fiyat tahmini yer, boyut ve evin diğer özelliklerini kullanarak ev fiyatları tahmin etmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cc61c-137">Price prediction can be used to predict house prices using location, size, and other characteristics of the house.</span></span> <span data-ttu-id="cc61c-138">Bu regresyon makine öğrenme görevi bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="cc61c-138">It is an example of the regression machine learning task.</span></span>

<span data-ttu-id="cc61c-139">Kendi veri kümenizle sayısal bir değer tahmin etmek istiyorsanız, senaryonuz için fiyat tahmini şablonunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc61c-139">You can use the price prediction template for your scenario if you want to predict a numerical value with your own dataset.</span></span>

#### <a name="classify-images-into-categories"></a><span data-ttu-id="cc61c-140">Resimleri kategorilere ayırma</span><span class="sxs-lookup"><span data-stu-id="cc61c-140">Classify images into categories</span></span>

<span data-ttu-id="cc61c-141">Bu senaryo, kategorize edilecek giriş verilerinin bir görüntü kümesi olduğu çok sınıflı sınıflandırmanın özel bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="cc61c-141">This scenario is a special case of multiclass classification, where the input data to be categorized is a set of images.</span></span>

<span data-ttu-id="cc61c-142">Resim sınıflandırması, farklı kategorilerdeki görüntüleri tanımlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cc61c-142">Image classification can be used to identify images of different categories.</span></span> <span data-ttu-id="cc61c-143">Örneğin, arazi veya hayvan veya üretim kusurları farklı türleri.</span><span class="sxs-lookup"><span data-stu-id="cc61c-143">For example, different types of terrain or animals or manufacturing defects.</span></span>

<span data-ttu-id="cc61c-144">Bir resim setiniz varsa ve görüntüleri farklı kategorilere sınıflandırmak istiyorsanız, senaryonuz için resim sınıflandırma şablonunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc61c-144">You can use the image classification template for your scenario if you have a set of images, and you want to classify the images into different categories.</span></span>

#### <a name="custom-scenario"></a><span data-ttu-id="cc61c-145">Özel senaryo</span><span class="sxs-lookup"><span data-stu-id="cc61c-145">Custom scenario</span></span>

<span data-ttu-id="cc61c-146">Özel senaryo, senaryonuzu el ile seçmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="cc61c-146">The custom scenario allows you to manually choose your scenario.</span></span>

## <a name="data"></a><span data-ttu-id="cc61c-147">Veriler</span><span class="sxs-lookup"><span data-stu-id="cc61c-147">Data</span></span>

<span data-ttu-id="cc61c-148">Senaryonuzu seçtikten sonra, Model Oluşturucu sizden bir veri kümesi sağlamanızı ister.</span><span class="sxs-lookup"><span data-stu-id="cc61c-148">Once you have chosen your scenario, Model Builder asks you to provide a dataset.</span></span> <span data-ttu-id="cc61c-149">Veriler, senaryonuz için en iyi modeli eğitmek, değerlendirmek ve seçmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cc61c-149">The data is used to train, evaluate, and choose the best model for your scenario.</span></span>

![Model Oluşturucu adımlarını gösteren diyagram](media/model-builder-steps.png)

<span data-ttu-id="cc61c-151">Model Oluşturucu,.tsv, .csv, .txt biçimlerinde ve SQL veritabanı biçiminde veri kümelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="cc61c-151">Model Builder supports datasets in .tsv, .csv, .txt formats, as well as SQL database format.</span></span> <span data-ttu-id="cc61c-152">.txt dosyanız varsa, sütunlar ile `,` `;` ayrılmalı veya `/t` dosyanın bir üstbilgi satırı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cc61c-152">If you have a .txt file, columns should be separated with `,`, `;` or `/t` and the file must have a header row.</span></span>

<span data-ttu-id="cc61c-153">Veri kümesi resimlerden oluşuyorsa, desteklenen dosya `.jpg` türleri `.png`ve.</span><span class="sxs-lookup"><span data-stu-id="cc61c-153">If the dataset is made up of images, the supported file types are `.jpg` and `.png`.</span></span>

<span data-ttu-id="cc61c-154">Daha fazla bilgi için [Model Oluşturucu'ya Yük eğitim verilerine](how-to-guides/load-data-model-builder.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="cc61c-154">For more information, see [Load training data into Model Builder](how-to-guides/load-data-model-builder.md).</span></span>

### <a name="choose-the-output-to-predict-label"></a><span data-ttu-id="cc61c-155">Tahmin etmek için çıktıyı seçin (etiket)</span><span class="sxs-lookup"><span data-stu-id="cc61c-155">Choose the output to predict (label)</span></span>

<span data-ttu-id="cc61c-156">Veri kümesi, eğitim örnekleri satırları ve özniteliklersütunları tablosudur.</span><span class="sxs-lookup"><span data-stu-id="cc61c-156">A dataset is a table of rows of training examples, and columns of attributes.</span></span> <span data-ttu-id="cc61c-157">Her satırda:</span><span class="sxs-lookup"><span data-stu-id="cc61c-157">Each row has:</span></span>

- <span data-ttu-id="cc61c-158">bir **etiket** (tahmin etmek istediğiniz öznitelik)</span><span class="sxs-lookup"><span data-stu-id="cc61c-158">a **label** (the attribute that you want to predict)</span></span>
- <span data-ttu-id="cc61c-159">**özellikleri** (etiketi tahmin etmek için giriş olarak kullanılan öznitelikler).</span><span class="sxs-lookup"><span data-stu-id="cc61c-159">**features** (attributes that are used as inputs to predict the label).</span></span>

<span data-ttu-id="cc61c-160">Ev fiyatı tahmin senaryosu için özellikler şu şekilde olabilir:</span><span class="sxs-lookup"><span data-stu-id="cc61c-160">For the house-price prediction scenario, the features could be:</span></span>

- <span data-ttu-id="cc61c-161">evin kare görüntüleri</span><span class="sxs-lookup"><span data-stu-id="cc61c-161">the square footage of the house</span></span>
- <span data-ttu-id="cc61c-162">yatak odası ve banyo sayısı</span><span class="sxs-lookup"><span data-stu-id="cc61c-162">the number of bedrooms and bathrooms</span></span>
- <span data-ttu-id="cc61c-163">posta kodu</span><span class="sxs-lookup"><span data-stu-id="cc61c-163">the zip code</span></span>

<span data-ttu-id="cc61c-164">Etiket kare görüntüleri, yatak odası ve banyo değerleri ve posta kodu bu satır için tarihsel ev fiyatıdır.</span><span class="sxs-lookup"><span data-stu-id="cc61c-164">The label is the historical house price for that row of square footage, bedroom, and bathroom values and zip code.</span></span>

![Boyut odaları posta kodu ve fiyat etiketinden oluşan özelliklere sahip ev fiyat verilerinin satır ve sütunlarını gösteren tablo](media/model-builder-data.png)

### <a name="example-datasets"></a><span data-ttu-id="cc61c-166">Örnek veri kümeleri</span><span class="sxs-lookup"><span data-stu-id="cc61c-166">Example datasets</span></span>

<span data-ttu-id="cc61c-167">Henüz kendi verileriniz yoksa, şu veri kümelerinden birini deneyin:</span><span class="sxs-lookup"><span data-stu-id="cc61c-167">If you don't have your own data yet, try out one of these datasets:</span></span>

|<span data-ttu-id="cc61c-168">Senaryo</span><span class="sxs-lookup"><span data-stu-id="cc61c-168">Scenario</span></span>|<span data-ttu-id="cc61c-169">ML görev</span><span class="sxs-lookup"><span data-stu-id="cc61c-169">ML task</span></span>|<span data-ttu-id="cc61c-170">Veriler</span><span class="sxs-lookup"><span data-stu-id="cc61c-170">Data</span></span>|<span data-ttu-id="cc61c-171">Etiketle</span><span class="sxs-lookup"><span data-stu-id="cc61c-171">Label</span></span>|<span data-ttu-id="cc61c-172">Özellikler</span><span class="sxs-lookup"><span data-stu-id="cc61c-172">Features</span></span>|
|-|-|-|-|-|
|<span data-ttu-id="cc61c-173">Fiyat tahmini</span><span class="sxs-lookup"><span data-stu-id="cc61c-173">Price prediction</span></span>|<span data-ttu-id="cc61c-174">Regresyon</span><span class="sxs-lookup"><span data-stu-id="cc61c-174">regression</span></span>|[<span data-ttu-id="cc61c-175">taksi ücreti verileri</span><span class="sxs-lookup"><span data-stu-id="cc61c-175">taxi fare data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|<span data-ttu-id="cc61c-176">Ücret</span><span class="sxs-lookup"><span data-stu-id="cc61c-176">Fare</span></span>|<span data-ttu-id="cc61c-177">Yolculuk süresi, mesafe</span><span class="sxs-lookup"><span data-stu-id="cc61c-177">Trip time, distance</span></span>|
|<span data-ttu-id="cc61c-178">Anormallik algılama</span><span class="sxs-lookup"><span data-stu-id="cc61c-178">Anomaly detection</span></span>|<span data-ttu-id="cc61c-179">ikili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="cc61c-179">binary classification</span></span>|[<span data-ttu-id="cc61c-180">ürün satış verileri</span><span class="sxs-lookup"><span data-stu-id="cc61c-180">product sales data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|<span data-ttu-id="cc61c-181">Ürün Satışları</span><span class="sxs-lookup"><span data-stu-id="cc61c-181">Product Sales</span></span>|<span data-ttu-id="cc61c-182">Ay</span><span class="sxs-lookup"><span data-stu-id="cc61c-182">Month</span></span>|
|<span data-ttu-id="cc61c-183">Yaklaşım analizi</span><span class="sxs-lookup"><span data-stu-id="cc61c-183">Sentiment analysis</span></span>|<span data-ttu-id="cc61c-184">ikili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="cc61c-184">binary classification</span></span>|[<span data-ttu-id="cc61c-185">web sitesi yorum verileri</span><span class="sxs-lookup"><span data-stu-id="cc61c-185">website comment data</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|<span data-ttu-id="cc61c-186">Etiket (0 negatif duygu, 1 pozitif)</span><span class="sxs-lookup"><span data-stu-id="cc61c-186">Label (0 when negative sentiment, 1 when positive)</span></span>|<span data-ttu-id="cc61c-187">Yorum, Yıl</span><span class="sxs-lookup"><span data-stu-id="cc61c-187">Comment, Year</span></span>|
|<span data-ttu-id="cc61c-188">Sahtekarlık algılama</span><span class="sxs-lookup"><span data-stu-id="cc61c-188">Fraud detection</span></span>|<span data-ttu-id="cc61c-189">ikili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="cc61c-189">binary classification</span></span>|[<span data-ttu-id="cc61c-190">kredi kartı verileri</span><span class="sxs-lookup"><span data-stu-id="cc61c-190">credit card data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|<span data-ttu-id="cc61c-191">Sınıf (1 sahte, 0 aksi takdirde)</span><span class="sxs-lookup"><span data-stu-id="cc61c-191">Class (1 when fraudulent, 0 otherwise)</span></span>|<span data-ttu-id="cc61c-192">Tutar, V1-V28 (anonimleştirilmiş özellikler)</span><span class="sxs-lookup"><span data-stu-id="cc61c-192">Amount, V1-V28 (anonymized features)</span></span>|
|<span data-ttu-id="cc61c-193">Metin sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="cc61c-193">Text classification</span></span>|<span data-ttu-id="cc61c-194">çok sınıflı sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="cc61c-194">multiclass classification</span></span>|[<span data-ttu-id="cc61c-195">GitHub sorun verileri</span><span class="sxs-lookup"><span data-stu-id="cc61c-195">GitHub issue data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|<span data-ttu-id="cc61c-196">Alan</span><span class="sxs-lookup"><span data-stu-id="cc61c-196">Area</span></span>|<span data-ttu-id="cc61c-197">Başlık, Açıklama</span><span class="sxs-lookup"><span data-stu-id="cc61c-197">Title, Description</span></span>|
|<span data-ttu-id="cc61c-198">Resimleri sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="cc61c-198">Image classification</span></span>|<span data-ttu-id="cc61c-199">çok sınıflı sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="cc61c-199">multiclass classification</span></span>|[<span data-ttu-id="cc61c-200">Çiçek resimleri</span><span class="sxs-lookup"><span data-stu-id="cc61c-200">Flowers images</span></span>](http://download.tensorflow.org/example_images/flower_photos.tgz)|<span data-ttu-id="cc61c-201">Çiçek türü: papatya, karahindiba, gül, ayçiçeği, lale</span><span class="sxs-lookup"><span data-stu-id="cc61c-201">The type of flower: daisy, dandelion, roses, sunflowers, tulips</span></span>|<span data-ttu-id="cc61c-202">Görüntü verilerinin kendisi</span><span class="sxs-lookup"><span data-stu-id="cc61c-202">The image data itself</span></span>|

## <a name="train"></a><span data-ttu-id="cc61c-203">Eğitim</span><span class="sxs-lookup"><span data-stu-id="cc61c-203">Train</span></span>

<span data-ttu-id="cc61c-204">Senaryonuzu, verilerinizi ve etiketinizi seçtikten sonra Model Oluşturucu modeli çalıştırAn modeli çalıştırZ.</span><span class="sxs-lookup"><span data-stu-id="cc61c-204">Once you select your scenario, data, and label, Model Builder trains the model.</span></span>

### <a name="what-is-training"></a><span data-ttu-id="cc61c-205">Eğitim nedir?</span><span class="sxs-lookup"><span data-stu-id="cc61c-205">What is training?</span></span>

<span data-ttu-id="cc61c-206">Eğitim, Model Oluşturucu'nun modelinize senaryonuzla ilgili soruları nasıl yanıtlayabildiğini öğrettiği otomatik bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="cc61c-206">Training is an automatic process by which Model Builder teaches your model how to answer questions for your scenario.</span></span> <span data-ttu-id="cc61c-207">Bir kez eğitildikten sonra, modeliniz daha önce görmediği giriş verileriyle öngörülerde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="cc61c-207">Once trained, your model can make predictions with input data that it has not seen before.</span></span> <span data-ttu-id="cc61c-208">Örneğin, ev fiyatları tahmin ediyorsanız ve yeni bir ev piyasaya geliyor, onun satış fiyatı tahmin edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc61c-208">For example, if you are predicting house prices and a new house comes on the market, you can predict its sale price.</span></span>

<span data-ttu-id="cc61c-209">Model Oluşturucu otomatik makine öğrenimi (AutoML) kullandığından, eğitim sırasında sizden herhangi bir giriş veya asetama gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="cc61c-209">Because Model Builder uses automated machine learning (AutoML), it does not require any input or tuning from you during training.</span></span>

### <a name="how-long-should-i-train-for"></a><span data-ttu-id="cc61c-210">Ne kadar süre antrenman yapmalıyım?</span><span class="sxs-lookup"><span data-stu-id="cc61c-210">How long should I train for?</span></span>

<span data-ttu-id="cc61c-211">Model Oluşturucu, size en iyi performans gösteren modeli bulmak için birden çok modeli keşfetmek için AutoML kullanır.</span><span class="sxs-lookup"><span data-stu-id="cc61c-211">Model Builder uses AutoML to explore multiple models to find you the best performing model.</span></span>

<span data-ttu-id="cc61c-212">Daha uzun eğitim süreleri, AutoML'nin daha geniş bir ayarı yelpazesine sahip daha fazla modeli keşfetmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="cc61c-212">Longer training periods allow AutoML to explore more models with a wider range of settings.</span></span>

<span data-ttu-id="cc61c-213">Aşağıdaki tablo, yerel bir makinede örnek veri kümeleri paketi için iyi performans elde etmek için geçen ortalama süreyi özetleyin.</span><span class="sxs-lookup"><span data-stu-id="cc61c-213">The table below summarizes the average time taken to get good performance for a suite of example datasets, on a local machine.</span></span>

|<span data-ttu-id="cc61c-214">Dataset boyutu</span><span class="sxs-lookup"><span data-stu-id="cc61c-214">Dataset size</span></span>|<span data-ttu-id="cc61c-215">Eğitim için ortalama süre</span><span class="sxs-lookup"><span data-stu-id="cc61c-215">Average time to train</span></span>|
|------------|---------------------|
|<span data-ttu-id="cc61c-216">0 - 10 MB</span><span class="sxs-lookup"><span data-stu-id="cc61c-216">0 - 10 MB</span></span>|<span data-ttu-id="cc61c-217">10 sn</span><span class="sxs-lookup"><span data-stu-id="cc61c-217">10 sec</span></span>|
|<span data-ttu-id="cc61c-218">10 - 100 MB</span><span class="sxs-lookup"><span data-stu-id="cc61c-218">10 - 100 MB</span></span>|<span data-ttu-id="cc61c-219">10 dk</span><span class="sxs-lookup"><span data-stu-id="cc61c-219">10 min</span></span>|
|<span data-ttu-id="cc61c-220">100 - 500 MB</span><span class="sxs-lookup"><span data-stu-id="cc61c-220">100 - 500 MB</span></span>|<span data-ttu-id="cc61c-221">30 dk</span><span class="sxs-lookup"><span data-stu-id="cc61c-221">30 min</span></span>|
|<span data-ttu-id="cc61c-222">500 - 1 GB Arası</span><span class="sxs-lookup"><span data-stu-id="cc61c-222">500 - 1 GB</span></span>|<span data-ttu-id="cc61c-223">60 dk</span><span class="sxs-lookup"><span data-stu-id="cc61c-223">60 min</span></span>|
|<span data-ttu-id="cc61c-224">1 GB+</span><span class="sxs-lookup"><span data-stu-id="cc61c-224">1 GB+</span></span>|<span data-ttu-id="cc61c-225">3+ saat</span><span class="sxs-lookup"><span data-stu-id="cc61c-225">3+ hours</span></span>|

<span data-ttu-id="cc61c-226">Bu sayılar sadece bir rehberdir.</span><span class="sxs-lookup"><span data-stu-id="cc61c-226">These numbers are a guide only.</span></span> <span data-ttu-id="cc61c-227">Eğitimin tam uzunluğu şuna bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="cc61c-227">The exact length of training is dependent on:</span></span>

- <span data-ttu-id="cc61c-228">modele giriş olarak kullanılan özellik (sütun) sayısı</span><span class="sxs-lookup"><span data-stu-id="cc61c-228">the number of features (columns) being used to as input to the model</span></span>
- <span data-ttu-id="cc61c-229">sütun türü</span><span class="sxs-lookup"><span data-stu-id="cc61c-229">the type of columns</span></span>
- <span data-ttu-id="cc61c-230">ML görev</span><span class="sxs-lookup"><span data-stu-id="cc61c-230">the ML task</span></span>
- <span data-ttu-id="cc61c-231">eğitim için kullanılan makinenin CPU, disk ve bellek performansı</span><span class="sxs-lookup"><span data-stu-id="cc61c-231">the CPU, disk and memory performance of the machine used for training</span></span>

## <a name="evaluate"></a><span data-ttu-id="cc61c-232">Değerlendir</span><span class="sxs-lookup"><span data-stu-id="cc61c-232">Evaluate</span></span>

<span data-ttu-id="cc61c-233">Değerlendirme, modelinizin ne kadar iyi olduğunu ölçme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="cc61c-233">Evaluation is the process of measuring how good your model is.</span></span> <span data-ttu-id="cc61c-234">Model Oluşturucu, yeni test verileriyle öngörülerde bulunmak için eğitilmiş modeli kullanır ve ardından tahminlerin ne kadar iyi olduğunu ölçer.</span><span class="sxs-lookup"><span data-stu-id="cc61c-234">Model Builder uses the trained model to make predictions with new test data, and then measures how good the predictions are.</span></span>

<span data-ttu-id="cc61c-235">Model Oluşturucu, eğitim verilerini bir eğitim kümesine ve test kümesine böler.</span><span class="sxs-lookup"><span data-stu-id="cc61c-235">Model Builder splits the training data into a training set and a test set.</span></span> <span data-ttu-id="cc61c-236">Eğitim verileri (%80) modelinizi ve test verilerini eğitmek için kullanılır (%20) modelinizi değerlendirmek için geri tutulur.</span><span class="sxs-lookup"><span data-stu-id="cc61c-236">The training data (80%) is used to train your model and the test data (20%) is held back to evaluate your model.</span></span>

### <a name="how-do-i-understand-my-model-performance"></a><span data-ttu-id="cc61c-237">Model performansımı nasıl anlarım?</span><span class="sxs-lookup"><span data-stu-id="cc61c-237">How do I understand my model performance?</span></span>

<span data-ttu-id="cc61c-238">Bir senaryo, makine öğrenimi görevine eş ler.</span><span class="sxs-lookup"><span data-stu-id="cc61c-238">A scenario maps to a machine learning task.</span></span> <span data-ttu-id="cc61c-239">Her ML görevinin kendi değerlendirme ölçütleri kümesi vardır.</span><span class="sxs-lookup"><span data-stu-id="cc61c-239">Each ML task has its own set of evaluation metrics.</span></span>

#### <a name="regression-for-example-price-prediction"></a><span data-ttu-id="cc61c-240">Regresyon (örneğin, Fiyat Tahmini)</span><span class="sxs-lookup"><span data-stu-id="cc61c-240">Regression (for example, Price Prediction)</span></span>

<span data-ttu-id="cc61c-241">Regresyon sorunları için varsayılan metrik RSquared'dir, RSquared değeri 0 ile 1 arasında değişir.</span><span class="sxs-lookup"><span data-stu-id="cc61c-241">The default metric for regression problems is RSquared, the value of RSquared ranges between 0 and 1.</span></span> <span data-ttu-id="cc61c-242">1 mümkün olan en iyi değer dir veya başka bir deyişle rsquared değeri daha yakın 1 modeli daha iyi performans.</span><span class="sxs-lookup"><span data-stu-id="cc61c-242">1 is the best possible value or in other words the closer the value of RSquared to 1 the better your model is performing.</span></span>

<span data-ttu-id="cc61c-243">Mutlak kayıp, kare-kayıp ve RMS kaybı gibi bildirilen diğer ölçümler, modelinizin nasıl performans gösterdiğini anlamak ve diğer regresyon modelleri ile karşılaştırmak için kullanılabilecek ek ölçümlerdir.</span><span class="sxs-lookup"><span data-stu-id="cc61c-243">Other metrics reported such as absolute-loss, squared-loss, and RMS loss are additional metrics, which can be used to understand how your model is performing and comparing it against other regression models.</span></span>

#### <a name="binary-classification-for-example-sentiment-analysis"></a><span data-ttu-id="cc61c-244">İkili Sınıflandırma (örneğin, Duygu Analizi)</span><span class="sxs-lookup"><span data-stu-id="cc61c-244">Binary Classification (for example, Sentiment Analysis)</span></span>

<span data-ttu-id="cc61c-245">Sınıflandırma sorunları için varsayılan metrik doğruluktır.</span><span class="sxs-lookup"><span data-stu-id="cc61c-245">The default metric for classification problems is accuracy.</span></span> <span data-ttu-id="cc61c-246">Doğruluk, modelinizin test veri kümesi üzerinde yaptığı doğru tahminlerin oranını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cc61c-246">Accuracy defines the proportion of correct predictions your model is making over the test dataset.</span></span> <span data-ttu-id="cc61c-247">%100 veya %1.0'a ne kadar yakınsa o kadar iyi olur.</span><span class="sxs-lookup"><span data-stu-id="cc61c-247">The closer to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="cc61c-248">AUC (eğrinin altındaki alan) gibi bildirilen diğer ölçümler, modellerin kabul edilememesi için doğru pozitif oranı ve yanlış pozitif oranı ölçen 0,50'den büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cc61c-248">Other metrics reported such as AUC (Area under the curve), which measures the true positive rate vs. the false positive rate should be greater than 0.50 for models to be acceptable.</span></span>

<span data-ttu-id="cc61c-249">Hassasve Geri Çağırma arasındaki dengeyi kontrol etmek için F1 puanı gibi ek ölçümler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cc61c-249">Additional metrics like F1 score can be used to control the balance between Precision and Recall.</span></span>

#### <a name="multi-class-classification-for-example-issue-classification-image-classification"></a><span data-ttu-id="cc61c-250">Çok Sınıflı Sınıflandırma (örneğin, Sayı Sınıflandırması, Görüntü Sınıflandırması)</span><span class="sxs-lookup"><span data-stu-id="cc61c-250">Multi-Class Classification (for example, Issue Classification, Image Classification)</span></span>

<span data-ttu-id="cc61c-251">Çok sınıflı sınıflandırma için varsayılan metrik Mikro Doğruluk'tır.</span><span class="sxs-lookup"><span data-stu-id="cc61c-251">The default metric for Multi-class classification is Micro Accuracy.</span></span> <span data-ttu-id="cc61c-252">Mikro Doğruluk %100 veya %1.0'a ne kadar yakınsa o kadar iyi olur.</span><span class="sxs-lookup"><span data-stu-id="cc61c-252">The closer the Micro Accuracy to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="cc61c-253">Çok sınıflı sınıflandırma için bir diğer önemli metrik makro-doğruluk, Mikro-doğruluk benzer 1.0 daha iyi.</span><span class="sxs-lookup"><span data-stu-id="cc61c-253">Another important metric for Multi-class classification is Macro-accuracy, similar to Micro-accuracy the closer to 1.0 the better it is.</span></span> <span data-ttu-id="cc61c-254">Doğruluk bu iki tür hakkında düşünmek için iyi bir yoldur:</span><span class="sxs-lookup"><span data-stu-id="cc61c-254">A good way to think about these two types of accuracy is:</span></span>

- <span data-ttu-id="cc61c-255">Mikro doğruluk: Gelen bilet ne sıklıkta doğru takıma sınıflandırılır?</span><span class="sxs-lookup"><span data-stu-id="cc61c-255">Micro-accuracy: How often does an incoming ticket get classified to the right team?</span></span>
- <span data-ttu-id="cc61c-256">Makro doğruluk: Ortalama bir takım için gelen bilet takım için ne sıklıkta doğrudur?</span><span class="sxs-lookup"><span data-stu-id="cc61c-256">Macro-accuracy: For an average team, how often is an incoming ticket correct for their team?</span></span>

### <a name="more-information-on-evaluation-metrics"></a><span data-ttu-id="cc61c-257">Değerlendirme ölçümleri hakkında daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="cc61c-257">More information on evaluation metrics</span></span>

<span data-ttu-id="cc61c-258">Daha fazla bilgi için [model değerlendirme ölçümlerine](resources/metrics.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="cc61c-258">For more information, see [model evaluation metrics](resources/metrics.md).</span></span>

## <a name="improve"></a><span data-ttu-id="cc61c-259">Geliştirmek</span><span class="sxs-lookup"><span data-stu-id="cc61c-259">Improve</span></span>

<span data-ttu-id="cc61c-260">Model performans puanınız istediğiniz kadar iyi değilse, şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="cc61c-260">If your model performance score is not as good as you want it to be, you can:</span></span>

- <span data-ttu-id="cc61c-261">Daha uzun bir süre için tren.</span><span class="sxs-lookup"><span data-stu-id="cc61c-261">Train for a longer period of time.</span></span> <span data-ttu-id="cc61c-262">Daha fazla zaman ile, daha fazla algoritma ve ayarları denemek için otomatik makine öğrenme motoru.</span><span class="sxs-lookup"><span data-stu-id="cc61c-262">With more time, the automated machine learning engine to try more algorithms and settings.</span></span>

- <span data-ttu-id="cc61c-263">Daha fazla veri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cc61c-263">Add more data.</span></span> <span data-ttu-id="cc61c-264">Bazen veri miktarı yüksek kaliteli bir makine öğrenme modeli eğitmek için yeterli değildir.</span><span class="sxs-lookup"><span data-stu-id="cc61c-264">Sometimes the amount of data is not sufficient to train a high-quality machine learning model.</span></span>

- <span data-ttu-id="cc61c-265">Verilerinizi dengeleyin.</span><span class="sxs-lookup"><span data-stu-id="cc61c-265">Balance your data.</span></span> <span data-ttu-id="cc61c-266">Sınıflandırma görevleri için, eğitim kümesinin kategoriler arasında dengeli olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="cc61c-266">For classification tasks, make sure that the training set is balanced across the categories.</span></span> <span data-ttu-id="cc61c-267">Örneğin, 100 eğitim örneği için dört sınıfınız varsa ve iki birinci sınıf (tag1 ve tag2) 90 kayıt için kullanılıyorsa, ancak diğer ikisi (tag3 ve tag4) yalnızca kalan 10 kayıtta kullanılıyorsa, dengeli veri eksikliği modelinizin tag3 veya tag4'u doğru tahmin edin.</span><span class="sxs-lookup"><span data-stu-id="cc61c-267">For example, if you have four classes for 100 training examples, and the two first classes (tag1 and tag2) are used for 90 records, but the other two (tag3 and tag4) are only used on the remaining 10 records, the lack of balanced data may cause your model to struggle to correctly predict tag3 or tag4.</span></span>

## <a name="code"></a><span data-ttu-id="cc61c-268">Kod</span><span class="sxs-lookup"><span data-stu-id="cc61c-268">Code</span></span>

<span data-ttu-id="cc61c-269">Değerlendirme aşamasından sonra, Model Oluşturucu bir model dosyası ve uygulamanıza modeli eklemek için kullanabileceğiniz kod çıktır.</span><span class="sxs-lookup"><span data-stu-id="cc61c-269">After the evaluation phase, Model Builder outputs a model file, and code that you can use to add the model to your application.</span></span> <span data-ttu-id="cc61c-270">ML.NET modelleri zip dosyası olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="cc61c-270">ML.NET models are saved as a zip file.</span></span> <span data-ttu-id="cc61c-271">Modelinizi yüklemek ve kullanmak için kod çözümünüze yeni bir proje olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="cc61c-271">The code to load and use your model is added as a new project in your solution.</span></span> <span data-ttu-id="cc61c-272">Model Oluşturucu ayrıca, modelinizi iş başında görmek için çalıştırabileceğiniz örnek bir konsol uygulaması da ekler.</span><span class="sxs-lookup"><span data-stu-id="cc61c-272">Model Builder also adds a sample console app that you can run to see your model in action.</span></span>

<span data-ttu-id="cc61c-273">Ayrıca, Modeli oluşturmak için kullanılan adımları anlayabilmeniz için Modeli oluşturan kodu Model Oluşturucu çıktır.</span><span class="sxs-lookup"><span data-stu-id="cc61c-273">In addition, Model Builder outputs the code that generated the model, so that you can understand the steps used to generate the model.</span></span> <span data-ttu-id="cc61c-274">Modelinizi yeni verilerle yeniden eğitmek için model eğitim kodunu da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc61c-274">You can also use the model training code to retrain your model with new data.</span></span>

## <a name="whats-next"></a><span data-ttu-id="cc61c-275">Sırada ne var?</span><span class="sxs-lookup"><span data-stu-id="cc61c-275">What's next?</span></span>

<span data-ttu-id="cc61c-276">Model Oluşturucu Visual Studio uzantısını [yükleyin](how-to-guides/install-model-builder.md)</span><span class="sxs-lookup"><span data-stu-id="cc61c-276">[Install](how-to-guides/install-model-builder.md) the Model Builder Visual Studio extension</span></span>

<span data-ttu-id="cc61c-277">[Fiyat tahminini veya herhangi bir gerileme senaryosuni](tutorials/predict-prices-with-model-builder.md) deneyin</span><span class="sxs-lookup"><span data-stu-id="cc61c-277">Try [price prediction or any regression scenario](tutorials/predict-prices-with-model-builder.md)</span></span>
