---
title: ML.NET nedir ve nasıl çalışır?
description: ML.NET, çevrimiçi veya çevrimdışı senaryolarda .NET uygulamalarına makine öğrenimi ekleme olanağı sunar. Bu özellik sayesinde, ML.NET kullanmak üzere bir ağa bağlı kalmak zorunda kalmadan, uygulamanızın kullanabildiği verileri kullanarak otomatik tahminler yapabilirsiniz. Bu makalede, ML.NET ' de makine öğrenmesinin temelleri açıklanmaktadır.
ms.date: 08/26/2019
ms.topic: overview
ms.custom: mvc
ms.author: nakersha
author: natke
ms.openlocfilehash: af91819c66a2376f446d0f18537d2f6e718b446e
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70104890"
---
# <a name="what-is-mlnet-and-how-does-it-work"></a><span data-ttu-id="7b262-105">ML.NET nedir ve nasıl çalışır?</span><span class="sxs-lookup"><span data-stu-id="7b262-105">What is ML.NET and how does it work?</span></span>

<span data-ttu-id="7b262-106">ML.NET, çevrimiçi veya çevrimdışı senaryolarda .NET uygulamalarına makine öğrenimi ekleme olanağı sunar.</span><span class="sxs-lookup"><span data-stu-id="7b262-106">ML.NET gives you the ability to add machine learning to .NET applications, in either online or offline scenarios.</span></span> <span data-ttu-id="7b262-107">Bu özellik sayesinde, bir ağa bağlı kalmak zorunda kalmadan uygulamanızın kullanabildiği verileri kullanarak otomatik tahminler yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b262-107">With this capability, you can make automatic predictions using the data available to your application without having to be connected to a network.</span></span> <span data-ttu-id="7b262-108">Bu makalede, ML.NET ' de makine öğrenmesinin temelleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7b262-108">This article explains the basics of machine learning in ML.NET.</span></span> 

<span data-ttu-id="7b262-109">ML.NET ile yapabileceğiniz tahmin türlerine örnek olarak şunlar verilebilir:</span><span class="sxs-lookup"><span data-stu-id="7b262-109">Examples of the type of predictions that you can make with ML.NET include:</span></span>

|||
|-|-|
|<span data-ttu-id="7b262-110">Sınıflandırma/kategori oluşturma</span><span class="sxs-lookup"><span data-stu-id="7b262-110">Classification/Categorization</span></span>|<span data-ttu-id="7b262-111">Müşteri geri bildirimini otomatik olarak pozitif ve negatif kategorilere bölün</span><span class="sxs-lookup"><span data-stu-id="7b262-111">Automatically divide customer feedback into positive and negative categories</span></span>|
|<span data-ttu-id="7b262-112">Gerileme/sürekli değerleri tahmin etme</span><span class="sxs-lookup"><span data-stu-id="7b262-112">Regression/Predict continuous values</span></span>|<span data-ttu-id="7b262-113">Boyut ve konuma göre barındırıldığı fiyatlarını tahmin etme</span><span class="sxs-lookup"><span data-stu-id="7b262-113">Predict the price of houses based on size and location</span></span>|
|<span data-ttu-id="7b262-114">Anomali Algılama</span><span class="sxs-lookup"><span data-stu-id="7b262-114">Anomaly Detection</span></span>|<span data-ttu-id="7b262-115">Sahte bankacılık işlemlerini Algıla</span><span class="sxs-lookup"><span data-stu-id="7b262-115">Detect fraudulent banking transactions</span></span> |
|<span data-ttu-id="7b262-116">Öneriler</span><span class="sxs-lookup"><span data-stu-id="7b262-116">Recommendations</span></span>|<span data-ttu-id="7b262-117">Çevrimiçi alışverişçilerin, önceki satın alımlarına göre satın almasını isteyebileceğiniz ürünleri önerin</span><span class="sxs-lookup"><span data-stu-id="7b262-117">Suggest products that online shoppers may want to buy, based on their previous purchases</span></span>|

## <a name="hello-mlnet-world"></a><span data-ttu-id="7b262-118">Merhaba ML.NET dünya</span><span class="sxs-lookup"><span data-stu-id="7b262-118">Hello ML.NET World</span></span>

<span data-ttu-id="7b262-119">Aşağıdaki kod parçacığındaki kod, en basit ML.NET uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7b262-119">The code in the following snippet demonstrates the simplest ML.NET application.</span></span> <span data-ttu-id="7b262-120">Bu örnek, ev boyutunu ve fiyat verilerini kullanarak ev fiyatlarını tahmin etmek için bir doğrusal regresyon modeli oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7b262-120">This example constructs a linear regression model to predict house prices using house size and price data.</span></span> <span data-ttu-id="7b262-121">Gerçek yaşam uygulamalarınızda, verileriniz ve modeliniz çok daha karmaşık olacaktır.</span><span class="sxs-lookup"><span data-stu-id="7b262-121">In your real-life applications, your data and model will be much more complex.</span></span>

 ```csharp
    using System;
    using Microsoft.ML;
    using Microsoft.ML.Data;
    
    class Program
    {
        public class HouseData
        {
            public float Size { get; set; }
            public float Price { get; set; }
        }
    
        public class Prediction
        {
            [ColumnName("Score")]
            public float Price { get; set; }
        }
    
        static void Main(string[] args)
        {
            MLContext mlContext = new MLContext();
    
            // 1. Import or create training data
            HouseData[] houseData = {
                new HouseData() { Size = 1.1F, Price = 1.2F },
                new HouseData() { Size = 1.9F, Price = 2.3F },
                new HouseData() { Size = 2.8F, Price = 3.0F },
                new HouseData() { Size = 3.4F, Price = 3.7F } };
            IDataView trainingData = mlContext.Data.LoadFromEnumerable(houseData);

            // 2. Specify data preparation and model training pipeline
            var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
                .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));
    
            // 3. Train model
            var model = pipeline.Fit(trainingData);
    
            // 4. Make a prediction
            var size = new HouseData() { Size = 2.5F };
            var price = mlContext.Model.CreatePredictionEngine<HouseData, Prediction>(model).Predict(size);

            Console.WriteLine($"Predicted price for size: {size.Size*1000} sq ft= {price.Price*100:C}k");

            // Predicted price for size: 2500 sq ft= $261.98k
        }
    } 
```

## <a name="code-workflow"></a><span data-ttu-id="7b262-122">Kod iş akışı</span><span class="sxs-lookup"><span data-stu-id="7b262-122">Code workflow</span></span>

<span data-ttu-id="7b262-123">Aşağıdaki diyagram, uygulama kodu yapısını, ayrıca model geliştirmenin yinelemeli işlemini temsil eder:</span><span class="sxs-lookup"><span data-stu-id="7b262-123">The following diagram represents the application code structure, as well as the iterative process of model development:</span></span>
- <span data-ttu-id="7b262-124">Bir **ıdataview** nesnesinde eğitim verileri toplama ve yükleme</span><span class="sxs-lookup"><span data-stu-id="7b262-124">Collect and load training data into an **IDataView** object</span></span>
- <span data-ttu-id="7b262-125">Özellikleri ayıklamak ve makine öğrenimi algoritmasını uygulamak için bir işlem hattı belirtin</span><span class="sxs-lookup"><span data-stu-id="7b262-125">Specify a pipeline of operations to extract features and apply a machine learning algorithm</span></span>
- <span data-ttu-id="7b262-126">İşlem hattına **sığdırma ()** yöntemini çağırarak bir modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="7b262-126">Train a model by calling **Fit()** on the pipeline</span></span>
- <span data-ttu-id="7b262-127">Modeli değerlendirin ve geliştirmeyi yineleyin</span><span class="sxs-lookup"><span data-stu-id="7b262-127">Evaluate the model and iterate to improve</span></span>
- <span data-ttu-id="7b262-128">Modeli bir uygulamada kullanılmak üzere ikili biçime Kaydet</span><span class="sxs-lookup"><span data-stu-id="7b262-128">Save the model into binary format, for use in an application</span></span>
- <span data-ttu-id="7b262-129">Modeli bir **ıranseski** nesnesine geri yükleme</span><span class="sxs-lookup"><span data-stu-id="7b262-129">Load the model back into an **ITransformer** object</span></span>
- <span data-ttu-id="7b262-130">**CreatePredictionEngine. tahmin ()** öğesini çağırarak tahminleri yapın</span><span class="sxs-lookup"><span data-stu-id="7b262-130">Make predictions by calling **CreatePredictionEngine.Predict()**</span></span>

![Veri oluşturma, işlem hattı geliştirme, model eğitimi, model değerlendirmesi ve model kullanımı bileşenleri dahil ML.NET uygulama geliştirme akışı](./media/mldotnet-annotated-workflow.png) 

<span data-ttu-id="7b262-132">Bu kavramların biraz daha ayrıntılı bir şekilde bakalım.</span><span class="sxs-lookup"><span data-stu-id="7b262-132">Let's dig a little deeper into those concepts.</span></span>

## <a name="machine-learning-model"></a><span data-ttu-id="7b262-133">Machine Learning modeli</span><span class="sxs-lookup"><span data-stu-id="7b262-133">Machine learning model</span></span>

<span data-ttu-id="7b262-134">ML.NET modeli, tahmin edilen çıkışa ulaşmak üzere giriş verilerinizde gerçekleştirilecek dönüşümleri içeren bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="7b262-134">An ML.NET model is an object that contains transformations to perform on your input data to arrive at the predicted output.</span></span>

### <a name="basic"></a><span data-ttu-id="7b262-135">Temel</span><span class="sxs-lookup"><span data-stu-id="7b262-135">Basic</span></span>

<span data-ttu-id="7b262-136">En temel model, yukarıdaki ev fiyat örneğinde olduğu gibi, bir sürekli miktarın birbiriyle orantılı olduğu iki boyutlu doğrusal regresyon olur.</span><span class="sxs-lookup"><span data-stu-id="7b262-136">The most basic model is two-dimensional linear regression, where one continuous quantity is proportional to another, as in the house price example above.</span></span> 

![Sapma ve ağırlık parametrelerine sahip doğrusal regresyon modeli](./media/linear-regression-model.svg)

<span data-ttu-id="7b262-138">Model yalnızca: $Price = b + size \* w $.</span><span class="sxs-lookup"><span data-stu-id="7b262-138">The model is simply: $Price = b + Size \* w$.</span></span> <span data-ttu-id="7b262-139">$B $ ve $w $ parametreleri, bir dizi (boyut, Fiyat) çiftleriyle bir satıra göre tahmin edilir.</span><span class="sxs-lookup"><span data-stu-id="7b262-139">The parameters $b$ and $w$ are estimated by fitting a line on a set of (size, price) pairs.</span></span> <span data-ttu-id="7b262-140">Modelin parametrelerini bulmak için kullanılan verilere **eğitim verileri**denir.</span><span class="sxs-lookup"><span data-stu-id="7b262-140">The data used to find the parameters of the model is called **training data**.</span></span> <span data-ttu-id="7b262-141">Machine Learning modelinin girişleri **Özellikler**olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="7b262-141">The inputs of a machine learning model are called **features**.</span></span> <span data-ttu-id="7b262-142">Bu örnekte, $Size $ tek özelliktir.</span><span class="sxs-lookup"><span data-stu-id="7b262-142">In this example, $Size$ is the only feature.</span></span> <span data-ttu-id="7b262-143">Bir makine öğrenimi modelini eğitebilmeniz için kullanılan taban-Truth değerlerine **Etiketler**denir.</span><span class="sxs-lookup"><span data-stu-id="7b262-143">The ground-truth values used to train a machine learning model are called **labels**.</span></span> <span data-ttu-id="7b262-144">Burada eğitim verileri kümesindeki $Price $ değerleri etiketlerdir.</span><span class="sxs-lookup"><span data-stu-id="7b262-144">Here, the $Price$ values in the training data set are the labels.</span></span>

### <a name="more-complex"></a><span data-ttu-id="7b262-145">Daha karmaşık</span><span class="sxs-lookup"><span data-stu-id="7b262-145">More complex</span></span>

<span data-ttu-id="7b262-146">Daha karmaşık bir model, işlem metni açıklamasını kullanarak finansal işlemleri kategoriler halinde sınıflandırır.</span><span class="sxs-lookup"><span data-stu-id="7b262-146">A more complex model classifies financial transactions into categories using the transaction text description.</span></span>

<span data-ttu-id="7b262-147">Her işlem açıklaması, gereksiz sözcük ve karakterleri kaldırarak ve sözcük ve karakter kombinasyonlarını sayarak bir özellik kümesine bölünür.</span><span class="sxs-lookup"><span data-stu-id="7b262-147">Each transaction description is broken down into a set of features by removing redundant words and characters, and counting word and character combinations.</span></span> <span data-ttu-id="7b262-148">Özellik kümesi, eğitim verilerinde kategori kümesini temel alan doğrusal bir modeli eğiteetmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7b262-148">The feature set is used to train a linear model based on the set of categories in the training data.</span></span> <span data-ttu-id="7b262-149">Daha benzer yeni bir açıklama, eğitim kümesindeki diğer bir deyişle, aynı kategoriye daha büyük olasılıkla atanır.</span><span class="sxs-lookup"><span data-stu-id="7b262-149">The more similar a new description is to the ones in the training set, the more likely it will be assigned to the same category.</span></span> 

![Metin sınıflandırması modeli](./media/text-classification-model.svg)

<span data-ttu-id="7b262-151">Hem ev fiyat modeli hem de metin sınıflandırma modeli **Doğrusal** modellerdir.</span><span class="sxs-lookup"><span data-stu-id="7b262-151">Both the house price model and the text classification model are **linear** models.</span></span> <span data-ttu-id="7b262-152">Verilerinizin yapısına ve çözmeyle ilgili soruna bağlı olarak, **karar ağacı** modellerini, **Genelleştirilmiş** ek modellerini ve diğerlerini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b262-152">Depending on the nature of your data and the problem you are solving, you can also use **decision tree** models, **generalized additive** models, and others.</span></span> <span data-ttu-id="7b262-153">[Görevler](./resources/tasks.md)' de modeller hakkında daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b262-153">You can find out more about the models in [Tasks](./resources/tasks.md).</span></span>

## <a name="data-preparation"></a><span data-ttu-id="7b262-154">Veri hazırlama</span><span class="sxs-lookup"><span data-stu-id="7b262-154">Data preparation</span></span>

<span data-ttu-id="7b262-155">Çoğu durumda, kullanılabilir olan veriler makine öğrenimi modelini eğitmek için doğrudan kullanılmaya uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="7b262-155">In most cases, the data that you have available isn't suitable to be used directly to train a machine learning model.</span></span> <span data-ttu-id="7b262-156">Ham verilerin, modelinizin parametrelerini bulmak için kullanılmadan önce hazırlanması veya önceden işlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="7b262-156">The raw data needs to be prepared, or pre-processed before it can be used to find the parameters of your model.</span></span> <span data-ttu-id="7b262-157">Verilerinizin dize değerlerinden sayısal bir gösterimine dönüştürülmesi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="7b262-157">Your data may need to be converted from string values to a numerical representation.</span></span> <span data-ttu-id="7b262-158">Giriş verilerinizde gereksiz bilgilere sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b262-158">You might have redundant information in your input data.</span></span> <span data-ttu-id="7b262-159">Giriş verilerinizin boyutlarını azaltmanız veya genişletmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="7b262-159">You may need to reduce or expand the dimensions of your input data.</span></span> <span data-ttu-id="7b262-160">Verilerinizin normalleştirilmesi veya ölçeklendirilmesi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="7b262-160">Your data might need to be normalized or scaled.</span></span>

<span data-ttu-id="7b262-161">[Ml.net öğreticileri](./tutorials/index.md) , belirli makine öğrenimi görevleri için kullanılan metin, görüntü, sayısal ve zaman serisi verileri için farklı veri işleme işlem hatları hakkında bilgi öğretin.</span><span class="sxs-lookup"><span data-stu-id="7b262-161">The [ML.NET tutorials](./tutorials/index.md) teach you about different data processing pipelines for text, image, numerical, and time-series data used for specific machine learning tasks.</span></span>

<span data-ttu-id="7b262-162">Verilerinizi [hazırlamak](./how-to-guides/prepare-data-ml-net.md) , veri hazırlığının daha genel olarak nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7b262-162">[How to prepare your data](./how-to-guides/prepare-data-ml-net.md) shows you how to applied data preparation more generally.</span></span>

<span data-ttu-id="7b262-163">Kaynaklar bölümünde tüm [kullanılabilir dönüşümlerinin](./resources/transforms.md) bir özetini bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b262-163">You can find an appendix of all of the [available transformations](./resources/transforms.md) in the resources section.</span></span>

## <a name="model-evaluation"></a><span data-ttu-id="7b262-164">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="7b262-164">Model evaluation</span></span>

<span data-ttu-id="7b262-165">Modelinizi eğittikten sonra, gelecekteki tahminleri ne kadar iyi hale getirmek istediğinizi nasıl anlarsınız?</span><span class="sxs-lookup"><span data-stu-id="7b262-165">Once you have trained your model, how do you know how well it will make future predictions?</span></span> <span data-ttu-id="7b262-166">ML.NET ile modelinizi bazı yeni test verileri için değerlendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b262-166">With ML.NET, you can evaluate your model against some new test data.</span></span> 

<span data-ttu-id="7b262-167">Her makine öğrenimi görevi türü, modelin doğruluğunu ve duyarlığını test veri kümesine karşı değerlendirmek için kullanılan ölçümlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="7b262-167">Each type of machine learning task has metrics used to evaluate the accuracy and precision of the model against the test data set.</span></span>

<span data-ttu-id="7b262-168">Evin fiyat örneğimiz için **regresyon** görevini kullandık.</span><span class="sxs-lookup"><span data-stu-id="7b262-168">For our house price example, we used the **Regression** task.</span></span> <span data-ttu-id="7b262-169">Modeli değerlendirmek için, özgün örneğe aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7b262-169">To evaluate the model, add the following code to the original sample.</span></span>

```csharp
        HouseData[] testHouseData =
        {
            new HouseData() { Size = 1.1F, Price = 0.98F },
            new HouseData() { Size = 1.9F, Price = 2.1F },
            new HouseData() { Size = 2.8F, Price = 2.9F },
            new HouseData() { Size = 3.4F, Price = 3.6F }
        };

        var testHouseDataView = mlContext.Data.LoadFromEnumerable(testHouseData);
        var testPriceDataView = model.Transform(testHouseDataView);
                
        var metrics = mlContext.Regression.Evaluate(testPriceDataView, labelColumnName: "Price");

        Console.WriteLine($"R^2: {metrics.RSquared:0.##}");
        Console.WriteLine($"RMS error: {metrics.RootMeanSquaredError:0.##}");

        // R^2: 0.96
        // RMS error: 0.19
```

<span data-ttu-id="7b262-170">Değerlendirme ölçümleri, hatanın düşük bir şekilde olduğunu ve tahmin edilen çıkış ile test çıkışı arasındaki bağıntıdan yüksek olduğunu söyler.</span><span class="sxs-lookup"><span data-stu-id="7b262-170">The evaluation metrics tell you that the error is low-ish, and that correlation between the predicted output and the test output is high.</span></span> <span data-ttu-id="7b262-171">Bu çok kolay!</span><span class="sxs-lookup"><span data-stu-id="7b262-171">That was easy!</span></span> <span data-ttu-id="7b262-172">Gerçek örneklerde, iyi model ölçümleri elde etmek için daha fazla ayarlama yapılır.</span><span class="sxs-lookup"><span data-stu-id="7b262-172">In real examples, it takes more tuning to achieve good model metrics.</span></span>

## <a name="mlnet-architecture"></a><span data-ttu-id="7b262-173">ML.NET mimarisi</span><span class="sxs-lookup"><span data-stu-id="7b262-173">ML.NET architecture</span></span>

<span data-ttu-id="7b262-174">Bu bölümde, ML.NET mimari desenlerine gideceğiz.</span><span class="sxs-lookup"><span data-stu-id="7b262-174">In this section, we go through the architectural patterns of ML.NET.</span></span> <span data-ttu-id="7b262-175">Deneyimli bir .NET geliştiricisiyseniz, bu desenlerden bazıları size tanıdık gelecektir ve bazıları daha az tanıdık olacaktır.</span><span class="sxs-lookup"><span data-stu-id="7b262-175">If you are an experienced .NET developer, some of these patterns will be familiar to you, and some will be less familiar.</span></span> <span data-ttu-id="7b262-176">Sıkı bir şekilde tutun.</span><span class="sxs-lookup"><span data-stu-id="7b262-176">Hold tight, while we dive in!</span></span>

<span data-ttu-id="7b262-177">Bir ml.NET uygulaması bir <xref:Microsoft.ML.MLContext> nesneyle başlar.</span><span class="sxs-lookup"><span data-stu-id="7b262-177">An ML.NET application starts with an <xref:Microsoft.ML.MLContext> object.</span></span> <span data-ttu-id="7b262-178">Bu tekil nesne **kataloglar**içerir.</span><span class="sxs-lookup"><span data-stu-id="7b262-178">This singleton object contains **catalogs**.</span></span> <span data-ttu-id="7b262-179">Katalog, veri yükleme ve kaydetme, dönüşümler, tracılar ve model işlemi bileşenlerine yönelik bir fabrikadır.</span><span class="sxs-lookup"><span data-stu-id="7b262-179">A catalog is a factory for data loading and saving, transforms, trainers, and model operation components.</span></span> <span data-ttu-id="7b262-180">Her Katalog nesnesi farklı bileşen türlerini oluşturma yöntemlerine sahiptir:</span><span class="sxs-lookup"><span data-stu-id="7b262-180">Each catalog object has methods to create the different types of components:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="7b262-181">Veri yükleme ve kaydetme</span><span class="sxs-lookup"><span data-stu-id="7b262-181">Data loading and saving</span></span>||<xref:Microsoft.ML.DataOperationsCatalog>||
|<span data-ttu-id="7b262-182">Veri hazırlama</span><span class="sxs-lookup"><span data-stu-id="7b262-182">Data preparation</span></span>||<xref:Microsoft.ML.TransformsCatalog>||
|<span data-ttu-id="7b262-183">Eğitim algoritmaları</span><span class="sxs-lookup"><span data-stu-id="7b262-183">Training algorithms</span></span>|<span data-ttu-id="7b262-184">İkili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="7b262-184">Binary classification</span></span>|<xref:Microsoft.ML.BinaryClassificationCatalog>||
||<span data-ttu-id="7b262-185">Birden çok Lass sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="7b262-185">Multiclass classification</span></span>|<xref:Microsoft.ML.MulticlassClassificationCatalog>||
||<span data-ttu-id="7b262-186">Anomali algılama</span><span class="sxs-lookup"><span data-stu-id="7b262-186">Anomaly detection</span></span>|<xref:Microsoft.ML.AnomalyDetectionCatalog>||
||<span data-ttu-id="7b262-187">Lenmesi</span><span class="sxs-lookup"><span data-stu-id="7b262-187">Clustering</span></span>|<xref:Microsoft.ML.ClusteringCatalog>||
||<span data-ttu-id="7b262-188">Tahmin etme</span><span class="sxs-lookup"><span data-stu-id="7b262-188">Forecasting</span></span>|<xref:Microsoft.ML.ForecastingCatalog>||
||<span data-ttu-id="7b262-189">Sıralamasına</span><span class="sxs-lookup"><span data-stu-id="7b262-189">Ranking</span></span>|<xref:Microsoft.ML.RankingCatalog>||
||<span data-ttu-id="7b262-190">Regresyon</span><span class="sxs-lookup"><span data-stu-id="7b262-190">Regression</span></span>|<xref:Microsoft.ML.RegressionCatalog>||
||<span data-ttu-id="7b262-191">Öneri</span><span class="sxs-lookup"><span data-stu-id="7b262-191">Recommendation</span></span>|<xref:Microsoft.ML.RecommendationCatalog>|<span data-ttu-id="7b262-192">`Microsoft.ML.Recommender` NuGet paketini ekleme</span><span class="sxs-lookup"><span data-stu-id="7b262-192">add the `Microsoft.ML.Recommender` NuGet package</span></span>|
||<span data-ttu-id="7b262-193">Zaman serisi</span><span class="sxs-lookup"><span data-stu-id="7b262-193">TimeSeries</span></span>|<xref:Microsoft.ML.TimeSeriesCatalog>|<span data-ttu-id="7b262-194">`Microsoft.ML.TimeSeries` NuGet paketini ekleme</span><span class="sxs-lookup"><span data-stu-id="7b262-194">add the `Microsoft.ML.TimeSeries` NuGet package</span></span>|
|<span data-ttu-id="7b262-195">Model kullanımı</span><span class="sxs-lookup"><span data-stu-id="7b262-195">Model usage</span></span> ||<xref:Microsoft.ML.ModelOperationsCatalog>||

<span data-ttu-id="7b262-196">Yukarıdaki kategorilerin her birinde oluşturma yöntemlerine gidebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b262-196">You can navigate to the creation methods in each of the above categories.</span></span> <span data-ttu-id="7b262-197">Visual Studio 'yu kullanarak kataloglar IntelliSense aracılığıyla gösterilir.</span><span class="sxs-lookup"><span data-stu-id="7b262-197">Using Visual Studio, the catalogs show up via IntelliSense.</span></span>

   ![Gerileme Eğitiminleri için IntelliSense](./media/catalog-intellisense.png)

### <a name="build-the-pipeline"></a><span data-ttu-id="7b262-199">İşlem hattını oluşturma</span><span class="sxs-lookup"><span data-stu-id="7b262-199">Build the pipeline</span></span>

<span data-ttu-id="7b262-200">Her kataloğun içinde bir genişletme yöntemleri kümesidir.</span><span class="sxs-lookup"><span data-stu-id="7b262-200">Inside each catalog is a set of extension methods.</span></span> <span data-ttu-id="7b262-201">Bir eğitim işlem hattı oluşturmak için uzantı yöntemlerinin nasıl kullanıldığına göz atalım.</span><span class="sxs-lookup"><span data-stu-id="7b262-201">Let's look at how extension methods are used to create a training pipeline.</span></span>

```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
        .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));
```

<span data-ttu-id="7b262-202">Kod parçacığında `Concatenate` ve `Sdca` her iki yöntemde de bulunur.</span><span class="sxs-lookup"><span data-stu-id="7b262-202">In the snippet, `Concatenate` and `Sdca` are both methods in the catalog.</span></span> <span data-ttu-id="7b262-203">Bunlar, işlem hattının sonuna eklenen bir [ıestimator](xref:Microsoft.ML.IEstimator%601) nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7b262-203">They each create an [IEstimator](xref:Microsoft.ML.IEstimator%601) object that is appended to the pipeline.</span></span>

<span data-ttu-id="7b262-204">Bu noktada, nesneler yalnızca oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7b262-204">At this point, the objects are created only.</span></span> <span data-ttu-id="7b262-205">Yürütme yapılmadı.</span><span class="sxs-lookup"><span data-stu-id="7b262-205">No execution has happened.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="7b262-206">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="7b262-206">Train the model</span></span>

<span data-ttu-id="7b262-207">İşlem hattındaki nesneler oluşturulduktan sonra, modeli eğitebilmeniz için veriler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7b262-207">Once the objects in the pipeline have been created, data can be used to train the model.</span></span>

```csharp
    var model = pipeline.Fit(trainingData);
```

<span data-ttu-id="7b262-208">Çağırma `Fit()` , modelin parametrelerini tahmin etmek için giriş eğitim verilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7b262-208">Calling `Fit()` uses the input training data to estimate the parameters of the model.</span></span> <span data-ttu-id="7b262-209">Bu, modeli eğitme olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="7b262-209">This is known as training the model.</span></span> <span data-ttu-id="7b262-210">Yukarıdaki doğrusal regresyon modelinin iki model parametresi olduğunu unutmayın: **sapma** ve **Ağırlık**.</span><span class="sxs-lookup"><span data-stu-id="7b262-210">Remember, the linear regression model above had two model parameters: **bias** and **weight**.</span></span> <span data-ttu-id="7b262-211">`Fit()` Çağrıdan sonra parametrelerin değerleri bilinmektedir.</span><span class="sxs-lookup"><span data-stu-id="7b262-211">After the `Fit()` call, the values of the parameters are known.</span></span> <span data-ttu-id="7b262-212">Çoğu modelde bundan çok daha fazla parametre olacaktır.</span><span class="sxs-lookup"><span data-stu-id="7b262-212">Most models will have many more parameters than this.</span></span>

<span data-ttu-id="7b262-213">[Modelinizi eğitme](./how-to-guides/train-machine-learning-model-ml-net.md) hakkında daha fazla bilgi için model eğitimi hakkında daha fazla bilgi edinebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="7b262-213">You can learn more about model training in [How to train your model](./how-to-guides/train-machine-learning-model-ml-net.md)</span></span>

<span data-ttu-id="7b262-214">Elde edilen model nesnesi <xref:Microsoft.ML.ITransformer> arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="7b262-214">The resulting model object implements the <xref:Microsoft.ML.ITransformer> interface.</span></span> <span data-ttu-id="7b262-215">Diğer bir deyişle, model giriş verilerini tahmine göre dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="7b262-215">That is, the model transforms input data into predictions.</span></span>

```csharp
   IDataView predictions = model.Transform(inputData);
```

### <a name="use-the-model"></a><span data-ttu-id="7b262-216">Modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="7b262-216">Use the model</span></span>

<span data-ttu-id="7b262-217">Giriş verilerini toplu olarak veya bir girişte tek seferde tahmin edilecek şekilde dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b262-217">You can transform input data into predictions in bulk, or one input at a time.</span></span> <span data-ttu-id="7b262-218">Ev fiyatı örneğinde, her ikisi de, modeli değerlendirmek amacıyla toplu olarak ve yeni bir tahmin oluşturmak için bir seferde bir kez yaptık.</span><span class="sxs-lookup"><span data-stu-id="7b262-218">In the house price example, we did both: in bulk for the purpose of evaluating the model, and one at a time to make a new prediction.</span></span> <span data-ttu-id="7b262-219">Tek tahmin yapmaya bakalım.</span><span class="sxs-lookup"><span data-stu-id="7b262-219">Let's look at making single predictions.</span></span>

```csharp
    var size = new HouseData() { Size = 2.5F };
    var predEngine = mlContext.CreatePredictionEngine<HouseData, Prediction>(model);
    var price = predEngine.Predict(size);
```
 
<span data-ttu-id="7b262-220">`CreatePredictionEngine()` Yöntemi bir giriş sınıfı ve bir çıkış sınıfı alır.</span><span class="sxs-lookup"><span data-stu-id="7b262-220">The `CreatePredictionEngine()` method takes an input class and an output class.</span></span> <span data-ttu-id="7b262-221">Alan adları ve/veya kod öznitelikleri, model eğitimi ve tahmin sırasında kullanılan veri sütunlarının adlarını belirlenir.</span><span class="sxs-lookup"><span data-stu-id="7b262-221">The field names and/or code attributes determine the names of the data columns used during model training and prediction.</span></span> <span data-ttu-id="7b262-222">Nasıl yapılır bölümünde [tek bir tahmin yapma](./how-to-guides/single-predict-model-ml-net.md) hakkında bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b262-222">You can read about  [How to make a single prediction](./how-to-guides/single-predict-model-ml-net.md) in the How-to section.</span></span>

### <a name="data-models-and-schema"></a><span data-ttu-id="7b262-223">Veri modelleri ve şema</span><span class="sxs-lookup"><span data-stu-id="7b262-223">Data models and schema</span></span>

<span data-ttu-id="7b262-224">Bir ML.NET Machine Learning işlem hattının Core 'da [DataView](xref:Microsoft.ML.IDataView) nesneleri bulunur.</span><span class="sxs-lookup"><span data-stu-id="7b262-224">At the core of an ML.NET machine learning pipeline are [DataView](xref:Microsoft.ML.IDataView) objects.</span></span>

<span data-ttu-id="7b262-225">İşlem hattındaki her dönüşümde bir giriş şeması (veri adları, türler ve boyutlar, dönüştürmenin girişte görmeyi beklediği boyutlar) vardır; ve bir çıkış şeması (veri adları, türler ve dönüşümün dönüşümden sonra ürettiği boyutlar).</span><span class="sxs-lookup"><span data-stu-id="7b262-225">Each transformation in the pipeline has an input schema (data names, types, and sizes that the transform expects to see on its input); and an output schema (data names, types, and sizes that the transform produces after the transformation).</span></span> <span data-ttu-id="7b262-226">Aşağıdaki belge, [ıdataview arabiriminin ve tür sisteminin](https://xadupre.github.io/machinelearningext/mlnetdocs/idataviewtypesystem.html)ayrıntılı bir açıklamasını sunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7b262-226">The following document provides an in-depth explanation of the [IDataView interface and its type system](https://xadupre.github.io/machinelearningext/mlnetdocs/idataviewtypesystem.html).</span></span>

<span data-ttu-id="7b262-227">İşlem hattındaki bir dönüşümden çıkış şeması, sonraki dönüşümün giriş şemasıyla eşleşmiyorsa, ML.NET bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7b262-227">If the output schema from one transform in the pipeline doesn't match the input schema of the next transform, ML.NET will throw an exception.</span></span>

<span data-ttu-id="7b262-228">Veri görünümü nesnesinin sütunları ve satırları vardır.</span><span class="sxs-lookup"><span data-stu-id="7b262-228">A data view object has columns and rows.</span></span> <span data-ttu-id="7b262-229">Her sütunun bir adı ve bir türü ve uzunluğu vardır.</span><span class="sxs-lookup"><span data-stu-id="7b262-229">Each column has a name and a type and a length.</span></span> <span data-ttu-id="7b262-230">Örneğin: ev fiyatı örnekteki giriş sütunları **Boyut** ve **fiyattır**.</span><span class="sxs-lookup"><span data-stu-id="7b262-230">For example: the input columns in the house price example are **Size** and **Price**.</span></span> <span data-ttu-id="7b262-231">Bunlar her ikisi de aynıdır ve vektörler yerine skaler miktarlardır.</span><span class="sxs-lookup"><span data-stu-id="7b262-231">They are both type  and they are scalar quantities rather than vector ones.</span></span>

   ![ML.NET veri görünümü örneği, ev fiyatı tahmin verileri](./media/ml-net-dataview.png)

<span data-ttu-id="7b262-233">Tüm ML.NET algoritmaları vektör olan bir giriş sütununu arar.</span><span class="sxs-lookup"><span data-stu-id="7b262-233">All ML.NET algorithms look for an input column that is a vector.</span></span> <span data-ttu-id="7b262-234">Varsayılan olarak bu vektör sütununa **Özellikler**denir.</span><span class="sxs-lookup"><span data-stu-id="7b262-234">By default this vector column is called **Features**.</span></span> <span data-ttu-id="7b262-235">Bu nedenle, **Boyut** sütununu, evin fiyat örneğimizde **Özellikler** adlı yeni bir sütuna bitiştirtik.</span><span class="sxs-lookup"><span data-stu-id="7b262-235">This is why we concatenated the **Size** column into a new column called **Features** in our house price example.</span></span>

 ```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
 ```

<span data-ttu-id="7b262-236">Tüm algoritmalar Ayrıca bir tahmin gerçekleştirildikten sonra yeni sütunlar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7b262-236">All algorithms also create new columns after they have performed a prediction.</span></span> <span data-ttu-id="7b262-237">Bu yeni sütunların sabit adları makine öğrenimi algoritmasının türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="7b262-237">The fixed names of these new columns depend on the type of machine learning algorithm.</span></span> <span data-ttu-id="7b262-238">Regresyon görevi için, yeni sütunlardan birine **puan**denir.</span><span class="sxs-lookup"><span data-stu-id="7b262-238">For the regression task, one of the new columns is called **Score**.</span></span> <span data-ttu-id="7b262-239">Bu nedenle fiyat verilerimizi bu adla ekledik.</span><span class="sxs-lookup"><span data-stu-id="7b262-239">This is why we attributed our price data with this name.</span></span>

```csharp
    public class Prediction
    {
        [ColumnName("Score")]
        public float Price { get; set; }
    }
```    

<span data-ttu-id="7b262-240">[Machine Learning görevler](resources/tasks.md) kılavuzunda, farklı makine öğrenimi görevlerinin çıkış sütunları hakkında daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b262-240">You can find out more about output columns of different machine learning tasks in the [Machine Learning Tasks](resources/tasks.md) guide.</span></span>

<span data-ttu-id="7b262-241">DataView nesnelerinin önemli bir özelliği, **geç**değerlendirilmesinden kaynaklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7b262-241">An important property of DataView objects is that they are evaluated **lazily**.</span></span> <span data-ttu-id="7b262-242">Veri görünümleri yalnızca model eğitimi ve değerlendirmesi sırasında yüklenir ve üzerinde çalıştırılır ve veri tahmini yapılır.</span><span class="sxs-lookup"><span data-stu-id="7b262-242">Data views are only loaded and operated on during model training and evaluation, and data prediction.</span></span> <span data-ttu-id="7b262-243">ML.NET uygulamanızı yazarken ve test ederken, [Önizleme](xref:Microsoft.ML.DebuggerExtensions.Preview*) yöntemini çağırarak herhangi bir veri görünümü nesnesine bir göz atma işlemleri yapmak Için Visual Studio hata ayıklayıcısını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b262-243">While you are writing and testing your ML.NET application, you can use the Visual Studio debugger to take a peek at any data view object by calling the [Preview](xref:Microsoft.ML.DebuggerExtensions.Preview*) method.</span></span>

```csharp
    var debug = testPriceDataView.Preview();
```

<span data-ttu-id="7b262-244">`debug` Değişkeni hata ayıklayıcıda izleyebilir ve içeriğini inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b262-244">You can watch the `debug` variable in the debugger and examine its contents.</span></span> <span data-ttu-id="7b262-245">Performansı önemli ölçüde düşürür, üretim kodunda önizleme yöntemini kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="7b262-245">Do not use the Preview method in production code, as it significantly degrades performance.</span></span>

### <a name="model-deployment"></a><span data-ttu-id="7b262-246">Model dağıtımı</span><span class="sxs-lookup"><span data-stu-id="7b262-246">Model Deployment</span></span>

<span data-ttu-id="7b262-247">Gerçek yaşam uygulamalarında, model eğitimi ve değerlendirme kodunuz tahmininizden ayrı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="7b262-247">In real-life applications, your model training and evaluation code will be separate from your prediction.</span></span> <span data-ttu-id="7b262-248">Aslında, bu iki etkinlik genellikle ayrı takımlar tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="7b262-248">In fact, these two activities are often performed by separate teams.</span></span> <span data-ttu-id="7b262-249">Model geliştirme ekibiniz, modeli tahmin uygulamasında kullanım için kaydedebilir.</span><span class="sxs-lookup"><span data-stu-id="7b262-249">Your model development team can save the model for use in the prediction application.</span></span>

```csharp   
   mlContext.Model.Save(model, trainingData.Schema,"model.zip");
```

## <a name="where-to-now"></a><span data-ttu-id="7b262-250">Şimdi nereden?</span><span class="sxs-lookup"><span data-stu-id="7b262-250">Where to now?</span></span>

<span data-ttu-id="7b262-251">[Öğreticilerde](./tutorials/index.md)daha gerçekçi veri kümeleriyle farklı makine öğrenimi görevleri kullanarak nasıl uygulama oluşturacağınızı öğrenebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b262-251">You can learn how to build applications using different machine learning tasks with more realistic data sets in the [tutorials](./tutorials/index.md).</span></span>

<span data-ttu-id="7b262-252">Ya da [nasıl yapılır kılavuzlarında](./how-to-guides/index.md)daha ayrıntılı bilgi edinmek için belirli konular hakkında bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b262-252">Or you can learn about specific topics in more depth in the [How To Guides](./how-to-guides/index.md).</span></span>

<span data-ttu-id="7b262-253">Süper KEDE kullanıyorsanız, [API başvuru belgelerine](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet)doğrudan gidebilirsiniz!</span><span class="sxs-lookup"><span data-stu-id="7b262-253">And if you're super keen, you can dive straight into the [API Reference documentation](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet)!</span></span>
