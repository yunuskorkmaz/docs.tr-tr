---
title: ML.NET nedir ve nasıl çalışır?
description: ML.NET, çevrimiçi veya çevrimdışı senaryolarda .NET uygulamalarına makine öğrenimi ekleme olanağı sunar. Bu özellik sayesinde, ML.NET kullanmak üzere bir ağa bağlı kalmak zorunda kalmadan, uygulamanızın kullanabildiği verileri kullanarak otomatik tahminler yapabilirsiniz. Bu makalede, ML.NET ' de makine öğrenmesinin temelleri açıklanmaktadır.
ms.date: 11/5/2019
ms.topic: overview
ms.custom: mvc
ms.author: nakersha
author: natke
ms.openlocfilehash: 5d8093c77799a55f4bc13e82c06c856dbb8d85cd
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976734"
---
# <a name="what-is-mlnet-and-how-does-it-work"></a><span data-ttu-id="35ad3-105">ML.NET nedir ve nasıl çalışır?</span><span class="sxs-lookup"><span data-stu-id="35ad3-105">What is ML.NET and how does it work?</span></span>

<span data-ttu-id="35ad3-106">ML.NET, çevrimiçi veya çevrimdışı senaryolarda .NET uygulamalarına makine öğrenimi ekleme olanağı sunar.</span><span class="sxs-lookup"><span data-stu-id="35ad3-106">ML.NET gives you the ability to add machine learning to .NET applications, in either online or offline scenarios.</span></span> <span data-ttu-id="35ad3-107">Bu özellik sayesinde, uygulamanızın kullanabildiği verileri kullanarak otomatik tahminler yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35ad3-107">With this capability, you can make automatic predictions using the data available to your application.</span></span>

<span data-ttu-id="35ad3-108">Merkezi ML.NET, bir makine öğrenimi **modelidir**.</span><span class="sxs-lookup"><span data-stu-id="35ad3-108">Central to ML.NET is a machine learning **model**.</span></span> <span data-ttu-id="35ad3-109">Model, giriş verilerinizi bir tahmine dönüştürmek için gereken adımları belirtir.</span><span class="sxs-lookup"><span data-stu-id="35ad3-109">The model specifies the steps needed to transform your input data into a prediction.</span></span> <span data-ttu-id="35ad3-110">ML.NET ile, bir algoritma belirterek özel bir modeli eğitebilirsiniz veya önceden eğitilen TensorFlow ve ONNX modellerini içeri aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35ad3-110">With ML.NET, you can train a custom model by specifying an algorithm, or you can import pre-trained TensorFlow and ONNX models.</span></span>

<span data-ttu-id="35ad3-111">Bir modelinize sahip olduktan sonra, tahmine dayalı hale getirmek için uygulamanızı uygulamanıza ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35ad3-111">Once you have a model, you can add it to your application to make the predictions.</span></span>

<span data-ttu-id="35ad3-112">ML.NET, .NET Core veya .NET Framework kullanarak Windows, Linux ve macOS üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="35ad3-112">ML.NET runs on Windows, Linux, and macOS using .NET Core, or Windows using .NET Framework.</span></span> <span data-ttu-id="35ad3-113">64 bit tüm platformlarda desteklenir.</span><span class="sxs-lookup"><span data-stu-id="35ad3-113">64 bit is supported on all platforms.</span></span> <span data-ttu-id="35ad3-114">32 bit, TensorFlow, LightGBM ve ONNX ile ilgili işlevler dışında Windows 'da desteklenir.</span><span class="sxs-lookup"><span data-stu-id="35ad3-114">32 bit is supported on Windows, except for TensorFlow, LightGBM, and ONNX related functionality.</span></span>

<span data-ttu-id="35ad3-115">ML.NET ile yapabileceğiniz tahmin türlerine örnek olarak şunlar verilebilir:</span><span class="sxs-lookup"><span data-stu-id="35ad3-115">Examples of the type of predictions that you can make with ML.NET:</span></span>

|||
|-|-|
|<span data-ttu-id="35ad3-116">Sınıflandırma/kategori oluşturma</span><span class="sxs-lookup"><span data-stu-id="35ad3-116">Classification/Categorization</span></span>|<span data-ttu-id="35ad3-117">Müşteri geri bildirimini otomatik olarak pozitif ve negatif kategorilere bölün</span><span class="sxs-lookup"><span data-stu-id="35ad3-117">Automatically divide customer feedback into positive and negative categories</span></span>|
|<span data-ttu-id="35ad3-118">Gerileme/sürekli değerleri tahmin etme</span><span class="sxs-lookup"><span data-stu-id="35ad3-118">Regression/Predict continuous values</span></span>|<span data-ttu-id="35ad3-119">Boyut ve konuma göre barındırıldığı fiyatlarını tahmin etme</span><span class="sxs-lookup"><span data-stu-id="35ad3-119">Predict the price of houses based on size and location</span></span>|
|<span data-ttu-id="35ad3-120">Anomali algılama</span><span class="sxs-lookup"><span data-stu-id="35ad3-120">Anomaly Detection</span></span>|<span data-ttu-id="35ad3-121">Sahte bankacılık işlemlerini Algıla</span><span class="sxs-lookup"><span data-stu-id="35ad3-121">Detect fraudulent banking transactions</span></span> |
|<span data-ttu-id="35ad3-122">Öneri</span><span class="sxs-lookup"><span data-stu-id="35ad3-122">Recommendations</span></span>|<span data-ttu-id="35ad3-123">Çevrimiçi alışverişçilerin, önceki satın alımlarına göre satın almasını isteyebileceğiniz ürünleri önerin</span><span class="sxs-lookup"><span data-stu-id="35ad3-123">Suggest products that online shoppers may want to buy, based on their previous purchases</span></span>|
|<span data-ttu-id="35ad3-124">Zaman serisi/sıralı veriler</span><span class="sxs-lookup"><span data-stu-id="35ad3-124">Time series/sequential data</span></span>|<span data-ttu-id="35ad3-125">Hava durumu/ürün satışları tahminini yapın</span><span class="sxs-lookup"><span data-stu-id="35ad3-125">Forecast the weather/product sales</span></span>|
|<span data-ttu-id="35ad3-126">Görüntü sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="35ad3-126">Image classification</span></span>|<span data-ttu-id="35ad3-127">Tıbbi görüntülerde pathologies kategorilere ayırma</span><span class="sxs-lookup"><span data-stu-id="35ad3-127">Categorize pathologies in medical images</span></span>|

## <a name="hello-mlnet-world"></a><span data-ttu-id="35ad3-128">Merhaba ML.NET dünya</span><span class="sxs-lookup"><span data-stu-id="35ad3-128">Hello ML.NET World</span></span>

<span data-ttu-id="35ad3-129">Aşağıdaki kod parçacığındaki kod, en basit ML.NET uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="35ad3-129">The code in the following snippet demonstrates the simplest ML.NET application.</span></span> <span data-ttu-id="35ad3-130">Bu örnek, ev boyutunu ve fiyat verilerini kullanarak ev fiyatlarını tahmin etmek için bir doğrusal regresyon modeli oluşturur.</span><span class="sxs-lookup"><span data-stu-id="35ad3-130">This example constructs a linear regression model to predict house prices using house size and price data.</span></span> 

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

## <a name="code-workflow"></a><span data-ttu-id="35ad3-131">Kod iş akışı</span><span class="sxs-lookup"><span data-stu-id="35ad3-131">Code workflow</span></span>

<span data-ttu-id="35ad3-132">Aşağıdaki diyagram, uygulama kodu yapısını, ayrıca model geliştirmenin yinelemeli işlemini temsil eder:</span><span class="sxs-lookup"><span data-stu-id="35ad3-132">The following diagram represents the application code structure, as well as the iterative process of model development:</span></span>

- <span data-ttu-id="35ad3-133">Bir **ıdataview** nesnesinde eğitim verileri toplama ve yükleme</span><span class="sxs-lookup"><span data-stu-id="35ad3-133">Collect and load training data into an **IDataView** object</span></span>
- <span data-ttu-id="35ad3-134">Özellikleri ayıklamak ve makine öğrenimi algoritmasını uygulamak için bir işlem hattı belirtin</span><span class="sxs-lookup"><span data-stu-id="35ad3-134">Specify a pipeline of operations to extract features and apply a machine learning algorithm</span></span>
- <span data-ttu-id="35ad3-135">İşlem hattına **sığdırma ()** yöntemini çağırarak bir modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="35ad3-135">Train a model by calling **Fit()** on the pipeline</span></span>
- <span data-ttu-id="35ad3-136">Modeli değerlendirin ve geliştirmeyi yineleyin</span><span class="sxs-lookup"><span data-stu-id="35ad3-136">Evaluate the model and iterate to improve</span></span>
- <span data-ttu-id="35ad3-137">Modeli bir uygulamada kullanılmak üzere ikili biçime Kaydet</span><span class="sxs-lookup"><span data-stu-id="35ad3-137">Save the model into binary format, for use in an application</span></span>
- <span data-ttu-id="35ad3-138">Modeli bir **ıranseski** nesnesine geri yükleme</span><span class="sxs-lookup"><span data-stu-id="35ad3-138">Load the model back into an **ITransformer** object</span></span>
- <span data-ttu-id="35ad3-139">**CreatePredictionEngine. tahmin ()** öğesini çağırarak tahminleri yapın</span><span class="sxs-lookup"><span data-stu-id="35ad3-139">Make predictions by calling **CreatePredictionEngine.Predict()**</span></span>

![Veri oluşturma, işlem hattı geliştirme, model eğitimi, model değerlendirmesi ve model kullanımı bileşenleri dahil ML.NET uygulama geliştirme akışı](./media/mldotnet-annotated-workflow.png)

<span data-ttu-id="35ad3-141">Bu kavramların biraz daha ayrıntılı bir şekilde bakalım.</span><span class="sxs-lookup"><span data-stu-id="35ad3-141">Let's dig a little deeper into those concepts.</span></span>

## <a name="machine-learning-model"></a><span data-ttu-id="35ad3-142">Machine Learning modeli</span><span class="sxs-lookup"><span data-stu-id="35ad3-142">Machine learning model</span></span>

<span data-ttu-id="35ad3-143">ML.NET modeli, tahmin edilen çıkışa ulaşmak üzere giriş verilerinizde gerçekleştirilecek dönüşümleri içeren bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="35ad3-143">An ML.NET model is an object that contains transformations to perform on your input data to arrive at the predicted output.</span></span>

### <a name="basic"></a><span data-ttu-id="35ad3-144">Temel</span><span class="sxs-lookup"><span data-stu-id="35ad3-144">Basic</span></span>

<span data-ttu-id="35ad3-145">En temel model, yukarıdaki ev fiyat örneğinde olduğu gibi, bir sürekli miktarın birbiriyle orantılı olduğu iki boyutlu doğrusal regresyon olur.</span><span class="sxs-lookup"><span data-stu-id="35ad3-145">The most basic model is two-dimensional linear regression, where one continuous quantity is proportional to another, as in the house price example above.</span></span>

![Sapma ve ağırlık parametrelerine sahip doğrusal regresyon modeli](./media/linear-regression-model.svg)

<span data-ttu-id="35ad3-147">Model yalnızca: $Price = b + size \* w $.</span><span class="sxs-lookup"><span data-stu-id="35ad3-147">The model is simply: $Price = b + Size \* w$.</span></span> <span data-ttu-id="35ad3-148">$B $ ve $w $ parametreleri, bir dizi (boyut, Fiyat) çiftleriyle bir satıra göre tahmin edilir.</span><span class="sxs-lookup"><span data-stu-id="35ad3-148">The parameters $b$ and $w$ are estimated by fitting a line on a set of (size, price) pairs.</span></span> <span data-ttu-id="35ad3-149">Modelin parametrelerini bulmak için kullanılan verilere **eğitim verileri**denir.</span><span class="sxs-lookup"><span data-stu-id="35ad3-149">The data used to find the parameters of the model is called **training data**.</span></span> <span data-ttu-id="35ad3-150">Machine Learning modelinin girişleri **Özellikler**olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="35ad3-150">The inputs of a machine learning model are called **features**.</span></span> <span data-ttu-id="35ad3-151">Bu örnekte, $Size $ tek özelliktir.</span><span class="sxs-lookup"><span data-stu-id="35ad3-151">In this example, $Size$ is the only feature.</span></span> <span data-ttu-id="35ad3-152">Bir makine öğrenimi modelini eğitebilmeniz için kullanılan taban-Truth değerlerine **Etiketler**denir.</span><span class="sxs-lookup"><span data-stu-id="35ad3-152">The ground-truth values used to train a machine learning model are called **labels**.</span></span> <span data-ttu-id="35ad3-153">Burada eğitim verileri kümesindeki $Price $ değerleri etiketlerdir.</span><span class="sxs-lookup"><span data-stu-id="35ad3-153">Here, the $Price$ values in the training data set are the labels.</span></span>

### <a name="more-complex"></a><span data-ttu-id="35ad3-154">Daha karmaşık</span><span class="sxs-lookup"><span data-stu-id="35ad3-154">More complex</span></span>

<span data-ttu-id="35ad3-155">Daha karmaşık bir model, işlem metni açıklamasını kullanarak finansal işlemleri kategoriler halinde sınıflandırır.</span><span class="sxs-lookup"><span data-stu-id="35ad3-155">A more complex model classifies financial transactions into categories using the transaction text description.</span></span>

<span data-ttu-id="35ad3-156">Her işlem açıklaması, gereksiz sözcük ve karakterleri kaldırarak ve sözcük ve karakter kombinasyonlarını sayarak bir özellik kümesine bölünür.</span><span class="sxs-lookup"><span data-stu-id="35ad3-156">Each transaction description is broken down into a set of features by removing redundant words and characters, and counting word and character combinations.</span></span> <span data-ttu-id="35ad3-157">Özellik kümesi, eğitim verilerinde kategori kümesini temel alan doğrusal bir modeli eğiteetmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="35ad3-157">The feature set is used to train a linear model based on the set of categories in the training data.</span></span> <span data-ttu-id="35ad3-158">Daha benzer yeni bir açıklama, eğitim kümesindeki diğer bir deyişle, aynı kategoriye daha büyük olasılıkla atanır.</span><span class="sxs-lookup"><span data-stu-id="35ad3-158">The more similar a new description is to the ones in the training set, the more likely it will be assigned to the same category.</span></span>

![Metin sınıflandırması modeli](./media/text-classification-model.svg)

<span data-ttu-id="35ad3-160">Hem ev fiyat modeli hem de metin sınıflandırma modeli **Doğrusal** modellerdir.</span><span class="sxs-lookup"><span data-stu-id="35ad3-160">Both the house price model and the text classification model are **linear** models.</span></span> <span data-ttu-id="35ad3-161">Verilerinizin yapısına ve çözmeyle ilgili soruna bağlı olarak, **karar ağacı** modellerini, **Genelleştirilmiş** ek modellerini ve diğerlerini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35ad3-161">Depending on the nature of your data and the problem you are solving, you can also use **decision tree** models, **generalized additive** models, and others.</span></span> <span data-ttu-id="35ad3-162">[Görevler](./resources/tasks.md)' de modeller hakkında daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35ad3-162">You can find out more about the models in [Tasks](./resources/tasks.md).</span></span>

## <a name="data-preparation"></a><span data-ttu-id="35ad3-163">Veri hazırlama</span><span class="sxs-lookup"><span data-stu-id="35ad3-163">Data preparation</span></span>

<span data-ttu-id="35ad3-164">Çoğu durumda, kullanılabilir olan veriler makine öğrenimi modelini eğitmek için doğrudan kullanılmaya uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="35ad3-164">In most cases, the data that you have available isn't suitable to be used directly to train a machine learning model.</span></span> <span data-ttu-id="35ad3-165">Ham verilerin, modelinizin parametrelerini bulmak için kullanılmadan önce hazırlanması veya önceden işlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="35ad3-165">The raw data needs to be prepared, or pre-processed before it can be used to find the parameters of your model.</span></span> <span data-ttu-id="35ad3-166">Verilerinizin dize değerlerinden sayısal bir gösterimine dönüştürülmesi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="35ad3-166">Your data may need to be converted from string values to a numerical representation.</span></span> <span data-ttu-id="35ad3-167">Giriş verilerinizde gereksiz bilgilere sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35ad3-167">You might have redundant information in your input data.</span></span> <span data-ttu-id="35ad3-168">Giriş verilerinizin boyutlarını azaltmanız veya genişletmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="35ad3-168">You may need to reduce or expand the dimensions of your input data.</span></span> <span data-ttu-id="35ad3-169">Verilerinizin normalleştirilmesi veya ölçeklendirilmesi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="35ad3-169">Your data might need to be normalized or scaled.</span></span>

<span data-ttu-id="35ad3-170">[Ml.net öğreticileri](./tutorials/index.md) , belirli makine öğrenimi görevleri için kullanılan metin, görüntü, sayısal ve zaman serisi verileri için farklı veri işleme işlem hatları hakkında bilgi öğretin.</span><span class="sxs-lookup"><span data-stu-id="35ad3-170">The [ML.NET tutorials](./tutorials/index.md) teach you about different data processing pipelines for text, image, numerical, and time-series data used for specific machine learning tasks.</span></span>

<span data-ttu-id="35ad3-171">Verilerinizi [hazırlamak](./how-to-guides/prepare-data-ml-net.md) , veri hazırlığının daha genel olarak nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="35ad3-171">[How to prepare your data](./how-to-guides/prepare-data-ml-net.md) shows you how to applied data preparation more generally.</span></span>

<span data-ttu-id="35ad3-172">Kaynaklar bölümünde tüm [kullanılabilir dönüşümlerinin](./resources/transforms.md) bir özetini bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35ad3-172">You can find an appendix of all of the [available transformations](./resources/transforms.md) in the resources section.</span></span>

## <a name="model-evaluation"></a><span data-ttu-id="35ad3-173">Model değerlendirmesi</span><span class="sxs-lookup"><span data-stu-id="35ad3-173">Model evaluation</span></span>

<span data-ttu-id="35ad3-174">Modelinizi eğittikten sonra, gelecekteki tahminleri ne kadar iyi hale getirmek istediğinizi nasıl anlarsınız?</span><span class="sxs-lookup"><span data-stu-id="35ad3-174">Once you have trained your model, how do you know how well it will make future predictions?</span></span> <span data-ttu-id="35ad3-175">ML.NET ile modelinizi bazı yeni test verileri için değerlendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35ad3-175">With ML.NET, you can evaluate your model against some new test data.</span></span>

<span data-ttu-id="35ad3-176">Her makine öğrenimi görevi türü, modelin doğruluğunu ve duyarlığını test veri kümesine karşı değerlendirmek için kullanılan ölçümlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="35ad3-176">Each type of machine learning task has metrics used to evaluate the accuracy and precision of the model against the test data set.</span></span>

<span data-ttu-id="35ad3-177">Evin fiyat örneğimiz için **regresyon** görevini kullandık.</span><span class="sxs-lookup"><span data-stu-id="35ad3-177">For our house price example, we used the **Regression** task.</span></span> <span data-ttu-id="35ad3-178">Modeli değerlendirmek için, özgün örneğe aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="35ad3-178">To evaluate the model, add the following code to the original sample.</span></span>

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

<span data-ttu-id="35ad3-179">Değerlendirme ölçümleri, hatanın düşük bir şekilde olduğunu ve tahmin edilen çıkış ile test çıkışı arasındaki bağıntıdan yüksek olduğunu söyler.</span><span class="sxs-lookup"><span data-stu-id="35ad3-179">The evaluation metrics tell you that the error is low-ish, and that correlation between the predicted output and the test output is high.</span></span> <span data-ttu-id="35ad3-180">Bu çok kolay!</span><span class="sxs-lookup"><span data-stu-id="35ad3-180">That was easy!</span></span> <span data-ttu-id="35ad3-181">Gerçek örneklerde, iyi model ölçümleri elde etmek için daha fazla ayarlama yapılır.</span><span class="sxs-lookup"><span data-stu-id="35ad3-181">In real examples, it takes more tuning to achieve good model metrics.</span></span>

## <a name="mlnet-architecture"></a><span data-ttu-id="35ad3-182">ML.NET mimarisi</span><span class="sxs-lookup"><span data-stu-id="35ad3-182">ML.NET architecture</span></span>

<span data-ttu-id="35ad3-183">Bu bölümde, ML.NET mimari desenlerine gideceğiz.</span><span class="sxs-lookup"><span data-stu-id="35ad3-183">In this section, we go through the architectural patterns of ML.NET.</span></span> <span data-ttu-id="35ad3-184">Deneyimli bir .NET geliştiricisiyseniz, bu desenlerden bazıları size tanıdık gelecektir ve bazıları daha az tanıdık olacaktır.</span><span class="sxs-lookup"><span data-stu-id="35ad3-184">If you are an experienced .NET developer, some of these patterns will be familiar to you, and some will be less familiar.</span></span> <span data-ttu-id="35ad3-185">Sıkı bir şekilde tutun.</span><span class="sxs-lookup"><span data-stu-id="35ad3-185">Hold tight, while we dive in!</span></span>

<span data-ttu-id="35ad3-186">Bir ML.NET uygulaması <xref:Microsoft.ML.MLContext> nesnesiyle başlar.</span><span class="sxs-lookup"><span data-stu-id="35ad3-186">An ML.NET application starts with an <xref:Microsoft.ML.MLContext> object.</span></span> <span data-ttu-id="35ad3-187">Bu tekil nesne **kataloglar**içerir.</span><span class="sxs-lookup"><span data-stu-id="35ad3-187">This singleton object contains **catalogs**.</span></span> <span data-ttu-id="35ad3-188">Katalog, veri yükleme ve kaydetme, dönüşümler, tracılar ve model işlemi bileşenlerine yönelik bir fabrikadır.</span><span class="sxs-lookup"><span data-stu-id="35ad3-188">A catalog is a factory for data loading and saving, transforms, trainers, and model operation components.</span></span> <span data-ttu-id="35ad3-189">Her Katalog nesnesi farklı bileşen türlerini oluşturma yöntemlerine sahiptir:</span><span class="sxs-lookup"><span data-stu-id="35ad3-189">Each catalog object has methods to create the different types of components:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="35ad3-190">Veri yükleme ve kaydetme</span><span class="sxs-lookup"><span data-stu-id="35ad3-190">Data loading and saving</span></span>||<xref:Microsoft.ML.DataOperationsCatalog>||
|<span data-ttu-id="35ad3-191">Veri hazırlama</span><span class="sxs-lookup"><span data-stu-id="35ad3-191">Data preparation</span></span>||<xref:Microsoft.ML.TransformsCatalog>||
|<span data-ttu-id="35ad3-192">Eğitim algoritmaları</span><span class="sxs-lookup"><span data-stu-id="35ad3-192">Training algorithms</span></span>|<span data-ttu-id="35ad3-193">ikili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="35ad3-193">Binary classification</span></span>|<xref:Microsoft.ML.BinaryClassificationCatalog>||
||<span data-ttu-id="35ad3-194">birden çok Lass sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="35ad3-194">Multiclass classification</span></span>|<xref:Microsoft.ML.MulticlassClassificationCatalog>||
||<span data-ttu-id="35ad3-195">Anomali algılama</span><span class="sxs-lookup"><span data-stu-id="35ad3-195">Anomaly detection</span></span>|<xref:Microsoft.ML.AnomalyDetectionCatalog>||
||<span data-ttu-id="35ad3-196">Lenmesi</span><span class="sxs-lookup"><span data-stu-id="35ad3-196">Clustering</span></span>|<xref:Microsoft.ML.ClusteringCatalog>||
||<span data-ttu-id="35ad3-197">Tahminine</span><span class="sxs-lookup"><span data-stu-id="35ad3-197">Forecasting</span></span>|<xref:Microsoft.ML.ForecastingCatalog>||
||<span data-ttu-id="35ad3-198">Sıralamasına</span><span class="sxs-lookup"><span data-stu-id="35ad3-198">Ranking</span></span>|<xref:Microsoft.ML.RankingCatalog>||
||<span data-ttu-id="35ad3-199">regresyon</span><span class="sxs-lookup"><span data-stu-id="35ad3-199">Regression</span></span>|<xref:Microsoft.ML.RegressionCatalog>||
||<span data-ttu-id="35ad3-200">Öneri</span><span class="sxs-lookup"><span data-stu-id="35ad3-200">Recommendation</span></span>|<xref:Microsoft.ML.RecommendationCatalog>|<span data-ttu-id="35ad3-201">`Microsoft.ML.Recommender` NuGet paketini ekleyin</span><span class="sxs-lookup"><span data-stu-id="35ad3-201">add the `Microsoft.ML.Recommender` NuGet package</span></span>|
||<span data-ttu-id="35ad3-202">Zaman serisi</span><span class="sxs-lookup"><span data-stu-id="35ad3-202">TimeSeries</span></span>|<xref:Microsoft.ML.TimeSeriesCatalog>|<span data-ttu-id="35ad3-203">`Microsoft.ML.TimeSeries` NuGet paketini ekleyin</span><span class="sxs-lookup"><span data-stu-id="35ad3-203">add the `Microsoft.ML.TimeSeries` NuGet package</span></span>|
|<span data-ttu-id="35ad3-204">Model kullanımı</span><span class="sxs-lookup"><span data-stu-id="35ad3-204">Model usage</span></span> ||<xref:Microsoft.ML.ModelOperationsCatalog>||

<span data-ttu-id="35ad3-205">Yukarıdaki kategorilerin her birinde oluşturma yöntemlerine gidebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35ad3-205">You can navigate to the creation methods in each of the above categories.</span></span> <span data-ttu-id="35ad3-206">Visual Studio 'yu kullanarak kataloglar IntelliSense aracılığıyla gösterilir.</span><span class="sxs-lookup"><span data-stu-id="35ad3-206">Using Visual Studio, the catalogs show up via IntelliSense.</span></span>

   ![Gerileme Eğitiminleri için IntelliSense](./media/catalog-intellisense.png)

### <a name="build-the-pipeline"></a><span data-ttu-id="35ad3-208">İşlem hattını oluşturma</span><span class="sxs-lookup"><span data-stu-id="35ad3-208">Build the pipeline</span></span>

<span data-ttu-id="35ad3-209">Her kataloğun içinde bir genişletme yöntemleri kümesidir.</span><span class="sxs-lookup"><span data-stu-id="35ad3-209">Inside each catalog is a set of extension methods.</span></span> <span data-ttu-id="35ad3-210">Bir eğitim işlem hattı oluşturmak için uzantı yöntemlerinin nasıl kullanıldığına göz atalım.</span><span class="sxs-lookup"><span data-stu-id="35ad3-210">Let's look at how extension methods are used to create a training pipeline.</span></span>

```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
        .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));
```

<span data-ttu-id="35ad3-211">Kod parçacığında, `Concatenate` ve `Sdca` her ikisi de katalogdaki yöntemlerdir.</span><span class="sxs-lookup"><span data-stu-id="35ad3-211">In the snippet, `Concatenate` and `Sdca` are both methods in the catalog.</span></span> <span data-ttu-id="35ad3-212">Bunlar, işlem hattının sonuna eklenen bir [ıestimator](xref:Microsoft.ML.IEstimator%601) nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="35ad3-212">They each create an [IEstimator](xref:Microsoft.ML.IEstimator%601) object that is appended to the pipeline.</span></span>

<span data-ttu-id="35ad3-213">Bu noktada, nesneler yalnızca oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="35ad3-213">At this point, the objects are created only.</span></span> <span data-ttu-id="35ad3-214">Yürütme yapılmadı.</span><span class="sxs-lookup"><span data-stu-id="35ad3-214">No execution has happened.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="35ad3-215">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="35ad3-215">Train the model</span></span>

<span data-ttu-id="35ad3-216">İşlem hattındaki nesneler oluşturulduktan sonra, modeli eğitebilmeniz için veriler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="35ad3-216">Once the objects in the pipeline have been created, data can be used to train the model.</span></span>

```csharp
    var model = pipeline.Fit(trainingData);
```

<span data-ttu-id="35ad3-217">`Fit()` çağırmak, modelin parametrelerini tahmin etmek için giriş eğitim verilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="35ad3-217">Calling `Fit()` uses the input training data to estimate the parameters of the model.</span></span> <span data-ttu-id="35ad3-218">Bu, modeli eğitme olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="35ad3-218">This is known as training the model.</span></span> <span data-ttu-id="35ad3-219">Yukarıdaki doğrusal regresyon modelinin iki model parametresi olduğunu unutmayın: **sapma** ve **Ağırlık**.</span><span class="sxs-lookup"><span data-stu-id="35ad3-219">Remember, the linear regression model above had two model parameters: **bias** and **weight**.</span></span> <span data-ttu-id="35ad3-220">`Fit()` çağrısından sonra parametrelerin değerleri bilinmektedir.</span><span class="sxs-lookup"><span data-stu-id="35ad3-220">After the `Fit()` call, the values of the parameters are known.</span></span> <span data-ttu-id="35ad3-221">Çoğu modelde bundan çok daha fazla parametre olacaktır.</span><span class="sxs-lookup"><span data-stu-id="35ad3-221">Most models will have many more parameters than this.</span></span>

<span data-ttu-id="35ad3-222">[Modelinizi eğitme](./how-to-guides/train-machine-learning-model-ml-net.md) hakkında daha fazla bilgi için model eğitimi hakkında daha fazla bilgi edinebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="35ad3-222">You can learn more about model training in [How to train your model](./how-to-guides/train-machine-learning-model-ml-net.md)</span></span>

<span data-ttu-id="35ad3-223">Elde edilen model nesnesi <xref:Microsoft.ML.ITransformer> arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="35ad3-223">The resulting model object implements the <xref:Microsoft.ML.ITransformer> interface.</span></span> <span data-ttu-id="35ad3-224">Diğer bir deyişle, model giriş verilerini tahmine göre dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="35ad3-224">That is, the model transforms input data into predictions.</span></span>

```csharp
   IDataView predictions = model.Transform(inputData);
```

### <a name="use-the-model"></a><span data-ttu-id="35ad3-225">Modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="35ad3-225">Use the model</span></span>

<span data-ttu-id="35ad3-226">Giriş verilerini toplu olarak veya bir girişte tek seferde tahmin edilecek şekilde dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35ad3-226">You can transform input data into predictions in bulk, or one input at a time.</span></span> <span data-ttu-id="35ad3-227">Ev fiyatı örneğinde, her ikisi de, modeli değerlendirmek amacıyla toplu olarak ve yeni bir tahmin oluşturmak için bir seferde bir kez yaptık.</span><span class="sxs-lookup"><span data-stu-id="35ad3-227">In the house price example, we did both: in bulk for the purpose of evaluating the model, and one at a time to make a new prediction.</span></span> <span data-ttu-id="35ad3-228">Tek tahmin yapmaya bakalım.</span><span class="sxs-lookup"><span data-stu-id="35ad3-228">Let's look at making single predictions.</span></span>

```csharp
    var size = new HouseData() { Size = 2.5F };
    var predEngine = mlContext.CreatePredictionEngine<HouseData, Prediction>(model);
    var price = predEngine.Predict(size);
```

<span data-ttu-id="35ad3-229">`CreatePredictionEngine()` yöntemi bir giriş sınıfı ve bir çıkış sınıfı alır.</span><span class="sxs-lookup"><span data-stu-id="35ad3-229">The `CreatePredictionEngine()` method takes an input class and an output class.</span></span> <span data-ttu-id="35ad3-230">Alan adları ve/veya kod öznitelikleri, model eğitimi ve tahmin sırasında kullanılan veri sütunlarının adlarını belirlenir.</span><span class="sxs-lookup"><span data-stu-id="35ad3-230">The field names and/or code attributes determine the names of the data columns used during model training and prediction.</span></span> <span data-ttu-id="35ad3-231">Nasıl yapılır bölümünde [tek bir tahmin yapma](./how-to-guides/single-predict-model-ml-net.md) hakkında bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35ad3-231">You can read about  [How to make a single prediction](./how-to-guides/single-predict-model-ml-net.md) in the How-to section.</span></span>

### <a name="data-models-and-schema"></a><span data-ttu-id="35ad3-232">Veri modelleri ve şema</span><span class="sxs-lookup"><span data-stu-id="35ad3-232">Data models and schema</span></span>

<span data-ttu-id="35ad3-233">Bir ML.NET Machine Learning işlem hattının Core 'da [DataView](xref:Microsoft.ML.IDataView) nesneleri bulunur.</span><span class="sxs-lookup"><span data-stu-id="35ad3-233">At the core of an ML.NET machine learning pipeline are [DataView](xref:Microsoft.ML.IDataView) objects.</span></span>

<span data-ttu-id="35ad3-234">İşlem hattındaki her dönüşümde bir giriş şeması (veri adları, türler ve boyutlar, dönüştürmenin girişte görmeyi beklediği boyutlar) vardır; ve bir çıkış şeması (veri adları, türler ve dönüşümün dönüşümden sonra ürettiği boyutlar).</span><span class="sxs-lookup"><span data-stu-id="35ad3-234">Each transformation in the pipeline has an input schema (data names, types, and sizes that the transform expects to see on its input); and an output schema (data names, types, and sizes that the transform produces after the transformation).</span></span> <span data-ttu-id="35ad3-235">Aşağıdaki belge, [ıdataview arabiriminin ve tür sisteminin](https://xadupre.github.io/machinelearningext/mlnetdocs/idataviewtypesystem.html)ayrıntılı bir açıklamasını sunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="35ad3-235">The following document provides an in-depth explanation of the [IDataView interface and its type system](https://xadupre.github.io/machinelearningext/mlnetdocs/idataviewtypesystem.html).</span></span>

<span data-ttu-id="35ad3-236">İşlem hattındaki bir dönüşümden çıkış şeması, sonraki dönüşümün giriş şemasıyla eşleşmiyorsa, ML.NET bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="35ad3-236">If the output schema from one transform in the pipeline doesn't match the input schema of the next transform, ML.NET will throw an exception.</span></span>

<span data-ttu-id="35ad3-237">Veri görünümü nesnesinin sütunları ve satırları vardır.</span><span class="sxs-lookup"><span data-stu-id="35ad3-237">A data view object has columns and rows.</span></span> <span data-ttu-id="35ad3-238">Her sütunun bir adı ve bir türü ve uzunluğu vardır.</span><span class="sxs-lookup"><span data-stu-id="35ad3-238">Each column has a name and a type and a length.</span></span> <span data-ttu-id="35ad3-239">Örneğin: ev fiyatı örnekteki giriş sütunları **Boyut** ve **fiyattır**.</span><span class="sxs-lookup"><span data-stu-id="35ad3-239">For example: the input columns in the house price example are **Size** and **Price**.</span></span> <span data-ttu-id="35ad3-240">Bunlar her ikisi de aynıdır ve vektörler yerine skaler miktarlardır.</span><span class="sxs-lookup"><span data-stu-id="35ad3-240">They are both type  and they are scalar quantities rather than vector ones.</span></span>

   ![ML.NET veri görünümü örneği, ev fiyatı tahmin verileri](./media/ml-net-dataview.png)

<span data-ttu-id="35ad3-242">Tüm ML.NET algoritmaları vektör olan bir giriş sütununu arar.</span><span class="sxs-lookup"><span data-stu-id="35ad3-242">All ML.NET algorithms look for an input column that is a vector.</span></span> <span data-ttu-id="35ad3-243">Varsayılan olarak bu vektör sütununa **Özellikler**denir.</span><span class="sxs-lookup"><span data-stu-id="35ad3-243">By default this vector column is called **Features**.</span></span> <span data-ttu-id="35ad3-244">Bu nedenle, **Boyut** sütununu, evin fiyat örneğimizde **Özellikler** adlı yeni bir sütuna bitiştirtik.</span><span class="sxs-lookup"><span data-stu-id="35ad3-244">This is why we concatenated the **Size** column into a new column called **Features** in our house price example.</span></span>

 ```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
 ```

<span data-ttu-id="35ad3-245">Tüm algoritmalar Ayrıca bir tahmin gerçekleştirildikten sonra yeni sütunlar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="35ad3-245">All algorithms also create new columns after they have performed a prediction.</span></span> <span data-ttu-id="35ad3-246">Bu yeni sütunların sabit adları makine öğrenimi algoritmasının türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="35ad3-246">The fixed names of these new columns depend on the type of machine learning algorithm.</span></span> <span data-ttu-id="35ad3-247">Regresyon görevi için, yeni sütunlardan birine **puan**denir.</span><span class="sxs-lookup"><span data-stu-id="35ad3-247">For the regression task, one of the new columns is called **Score**.</span></span> <span data-ttu-id="35ad3-248">Bu nedenle fiyat verilerimizi bu adla ekledik.</span><span class="sxs-lookup"><span data-stu-id="35ad3-248">This is why we attributed our price data with this name.</span></span>

```csharp
    public class Prediction
    {
        [ColumnName("Score")]
        public float Price { get; set; }
    }
```

<span data-ttu-id="35ad3-249">[Machine Learning görevler](resources/tasks.md) kılavuzunda, farklı makine öğrenimi görevlerinin çıkış sütunları hakkında daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35ad3-249">You can find out more about output columns of different machine learning tasks in the [Machine Learning Tasks](resources/tasks.md) guide.</span></span>

<span data-ttu-id="35ad3-250">DataView nesnelerinin önemli bir özelliği, **geç**değerlendirilmesinden kaynaklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="35ad3-250">An important property of DataView objects is that they are evaluated **lazily**.</span></span> <span data-ttu-id="35ad3-251">Veri görünümleri yalnızca model eğitimi ve değerlendirmesi sırasında yüklenir ve üzerinde çalıştırılır ve veri tahmini yapılır.</span><span class="sxs-lookup"><span data-stu-id="35ad3-251">Data views are only loaded and operated on during model training and evaluation, and data prediction.</span></span> <span data-ttu-id="35ad3-252">ML.NET uygulamanızı yazarken ve test ederken, [Önizleme](xref:Microsoft.ML.DebuggerExtensions.Preview*) yöntemini çağırarak herhangi bir veri görünümü nesnesine bir göz atma işlemleri yapmak Için Visual Studio hata ayıklayıcısını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35ad3-252">While you are writing and testing your ML.NET application, you can use the Visual Studio debugger to take a peek at any data view object by calling the [Preview](xref:Microsoft.ML.DebuggerExtensions.Preview*) method.</span></span>

```csharp
    var debug = testPriceDataView.Preview();
```

<span data-ttu-id="35ad3-253">Hata ayıklayıcıda `debug` değişkenini izleyebilir ve içeriğini inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35ad3-253">You can watch the `debug` variable in the debugger and examine its contents.</span></span> <span data-ttu-id="35ad3-254">Performansı önemli ölçüde düşürür, üretim kodunda önizleme yöntemini kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="35ad3-254">Do not use the Preview method in production code, as it significantly degrades performance.</span></span>

### <a name="model-deployment"></a><span data-ttu-id="35ad3-255">Model dağıtımı</span><span class="sxs-lookup"><span data-stu-id="35ad3-255">Model Deployment</span></span>

<span data-ttu-id="35ad3-256">Gerçek yaşam uygulamalarında, model eğitimi ve değerlendirme kodunuz tahmininizden ayrı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="35ad3-256">In real-life applications, your model training and evaluation code will be separate from your prediction.</span></span> <span data-ttu-id="35ad3-257">Aslında, bu iki etkinlik genellikle ayrı takımlar tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="35ad3-257">In fact, these two activities are often performed by separate teams.</span></span> <span data-ttu-id="35ad3-258">Model geliştirme ekibiniz, modeli tahmin uygulamasında kullanım için kaydedebilir.</span><span class="sxs-lookup"><span data-stu-id="35ad3-258">Your model development team can save the model for use in the prediction application.</span></span>

```csharp
   mlContext.Model.Save(model, trainingData.Schema,"model.zip");
```

## <a name="next-steps"></a><span data-ttu-id="35ad3-259">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="35ad3-259">Next steps</span></span>

* <span data-ttu-id="35ad3-260">[Öğreticilerde](./tutorials/index.md)daha gerçekçi veri kümeleriyle farklı makine öğrenimi görevleri kullanarak uygulama oluşturmayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="35ad3-260">Learn how to build applications using different machine learning tasks with more realistic data sets in the [tutorials](./tutorials/index.md).</span></span>

* <span data-ttu-id="35ad3-261">Belirli konular hakkında daha ayrıntılı bilgi edinmek Için bkz. [nasıl yapılır kılavuzlarında](./how-to-guides/index.md).</span><span class="sxs-lookup"><span data-stu-id="35ad3-261">Learn about specific topics in more depth in the [How To Guides](./how-to-guides/index.md).</span></span>

* <span data-ttu-id="35ad3-262">Süper kez kullanıyorsanız, [API başvuru belgelerine](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet)doğrudan gidebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35ad3-262">If you're super keen, you can dive straight into the [API Reference documentation](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet).</span></span>
