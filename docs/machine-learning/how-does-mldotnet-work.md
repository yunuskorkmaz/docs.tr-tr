---
title: ML.NET nedir ve nasıl çalışır?
description: ML.NET, çevrimiçi veya çevrimdışı senaryolarda .NET uygulamalarına makine öğrenimi ekleme olanağı sunar. Bu özellik sayesinde, ML.NET kullanmak üzere bir ağa bağlı kalmak zorunda kalmadan, uygulamanızın kullanabildiği verileri kullanarak otomatik tahminler yapabilirsiniz. Bu makalede, ML.NET ' de makine öğrenmesinin temelleri açıklanmaktadır.
ms.date: 11/5/2019
ms.topic: overview
ms.custom: mvc
ms.openlocfilehash: d9a218e57756ad8b95248193325e902c1798cc37
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679670"
---
# <a name="what-is-mlnet-and-how-does-it-work"></a><span data-ttu-id="83572-105">ML.NET nedir ve nasıl çalışır?</span><span class="sxs-lookup"><span data-stu-id="83572-105">What is ML.NET and how does it work?</span></span>

<span data-ttu-id="83572-106">ML.NET, çevrimiçi veya çevrimdışı senaryolarda .NET uygulamalarına makine öğrenimi ekleme olanağı sunar.</span><span class="sxs-lookup"><span data-stu-id="83572-106">ML.NET gives you the ability to add machine learning to .NET applications, in either online or offline scenarios.</span></span> <span data-ttu-id="83572-107">Bu özellik sayesinde, uygulamanızın kullanabildiği verileri kullanarak otomatik tahminler yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83572-107">With this capability, you can make automatic predictions using the data available to your application.</span></span> <span data-ttu-id="83572-108">Machine Learning uygulamaları, açık olarak programlanabilir olması yerine tahmine dayalı hale getirmek için verilerdeki desenleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="83572-108">Machine learning applications make use of patterns in the data to make predictions rather than needing to be explicitly programmed.</span></span>

<span data-ttu-id="83572-109">Merkezi ML.NET, bir makine öğrenimi **modelidir**.</span><span class="sxs-lookup"><span data-stu-id="83572-109">Central to ML.NET is a machine learning **model**.</span></span> <span data-ttu-id="83572-110">Model, giriş verilerinizi bir tahmine dönüştürmek için gereken adımları belirtir.</span><span class="sxs-lookup"><span data-stu-id="83572-110">The model specifies the steps needed to transform your input data into a prediction.</span></span> <span data-ttu-id="83572-111">ML.NET ile, bir algoritma belirterek özel bir modeli eğitebilirsiniz veya önceden eğitilen TensorFlow ve ONNX modellerini içeri aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83572-111">With ML.NET, you can train a custom model by specifying an algorithm, or you can import pre-trained TensorFlow and ONNX models.</span></span>

<span data-ttu-id="83572-112">Bir modelinize sahip olduktan sonra, tahmine dayalı hale getirmek için uygulamanızı uygulamanıza ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83572-112">Once you have a model, you can add it to your application to make the predictions.</span></span>

<span data-ttu-id="83572-113">ML.NET, .NET Core veya .NET Framework kullanarak Windows, Linux ve macOS üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="83572-113">ML.NET runs on Windows, Linux, and macOS using .NET Core, or Windows using .NET Framework.</span></span> <span data-ttu-id="83572-114">64 bit tüm platformlarda desteklenir.</span><span class="sxs-lookup"><span data-stu-id="83572-114">64 bit is supported on all platforms.</span></span> <span data-ttu-id="83572-115">32 bit, TensorFlow, LightGBM ve ONNX ile ilgili işlevler dışında Windows 'da desteklenir.</span><span class="sxs-lookup"><span data-stu-id="83572-115">32 bit is supported on Windows, except for TensorFlow, LightGBM, and ONNX-related functionality.</span></span>

<span data-ttu-id="83572-116">ML.NET ile yapabileceğiniz tahmin türlerine örnek olarak şunlar verilebilir:</span><span class="sxs-lookup"><span data-stu-id="83572-116">Examples of the type of predictions that you can make with ML.NET:</span></span>

|||
|-|-|
|<span data-ttu-id="83572-117">Sınıflandırma/kategori oluşturma</span><span class="sxs-lookup"><span data-stu-id="83572-117">Classification/Categorization</span></span>|<span data-ttu-id="83572-118">Müşteri geri bildirimini otomatik olarak pozitif ve negatif kategorilere bölün</span><span class="sxs-lookup"><span data-stu-id="83572-118">Automatically divide customer feedback into positive and negative categories</span></span>|
|<span data-ttu-id="83572-119">Gerileme/sürekli değerleri tahmin etme</span><span class="sxs-lookup"><span data-stu-id="83572-119">Regression/Predict continuous values</span></span>|<span data-ttu-id="83572-120">Boyut ve konuma göre barındırıldığı fiyatlarını tahmin etme</span><span class="sxs-lookup"><span data-stu-id="83572-120">Predict the price of houses based on size and location</span></span>|
|<span data-ttu-id="83572-121">Anomali Algılama</span><span class="sxs-lookup"><span data-stu-id="83572-121">Anomaly Detection</span></span>|<span data-ttu-id="83572-122">Sahte bankacılık işlemlerini Algıla</span><span class="sxs-lookup"><span data-stu-id="83572-122">Detect fraudulent banking transactions</span></span> |
|<span data-ttu-id="83572-123">Öneriler</span><span class="sxs-lookup"><span data-stu-id="83572-123">Recommendations</span></span>|<span data-ttu-id="83572-124">Çevrimiçi alışverişçilerin, önceki satın alımlarına göre satın almasını isteyebileceğiniz ürünleri önerin</span><span class="sxs-lookup"><span data-stu-id="83572-124">Suggest products that online shoppers may want to buy, based on their previous purchases</span></span>|
|<span data-ttu-id="83572-125">Zaman serisi/sıralı veriler</span><span class="sxs-lookup"><span data-stu-id="83572-125">Time series/sequential data</span></span>|<span data-ttu-id="83572-126">Hava durumu/ürün satışları tahminini yapın</span><span class="sxs-lookup"><span data-stu-id="83572-126">Forecast the weather/product sales</span></span>|
|<span data-ttu-id="83572-127">Resimleri sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="83572-127">Image classification</span></span>|<span data-ttu-id="83572-128">Tıbbi görüntülerde pathologies kategorilere ayırma</span><span class="sxs-lookup"><span data-stu-id="83572-128">Categorize pathologies in medical images</span></span>|

## <a name="hello-mlnet-world"></a><span data-ttu-id="83572-129">Merhaba ML.NET dünya</span><span class="sxs-lookup"><span data-stu-id="83572-129">Hello ML.NET World</span></span>

<span data-ttu-id="83572-130">Aşağıdaki kod parçacığındaki kod, en basit ML.NET uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="83572-130">The code in the following snippet demonstrates the simplest ML.NET application.</span></span> <span data-ttu-id="83572-131">Bu örnek, ev boyutunu ve fiyat verilerini kullanarak ev fiyatlarını tahmin etmek için bir doğrusal regresyon modeli oluşturur.</span><span class="sxs-lookup"><span data-stu-id="83572-131">This example constructs a linear regression model to predict house prices using house size and price data.</span></span>

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

## <a name="code-workflow"></a><span data-ttu-id="83572-132">Kod iş akışı</span><span class="sxs-lookup"><span data-stu-id="83572-132">Code workflow</span></span>

<span data-ttu-id="83572-133">Aşağıdaki diyagram, uygulama kodu yapısını, ayrıca model geliştirmenin yinelemeli işlemini temsil eder:</span><span class="sxs-lookup"><span data-stu-id="83572-133">The following diagram represents the application code structure, as well as the iterative process of model development:</span></span>

- <span data-ttu-id="83572-134">Bir **ıdataview** nesnesinde eğitim verileri toplama ve yükleme</span><span class="sxs-lookup"><span data-stu-id="83572-134">Collect and load training data into an **IDataView** object</span></span>
- <span data-ttu-id="83572-135">Özellikleri ayıklamak ve makine öğrenimi algoritmasını uygulamak için bir işlem hattı belirtin</span><span class="sxs-lookup"><span data-stu-id="83572-135">Specify a pipeline of operations to extract features and apply a machine learning algorithm</span></span>
- <span data-ttu-id="83572-136">İşlem hattına **sığdırma ()** yöntemini çağırarak bir modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="83572-136">Train a model by calling **Fit()** on the pipeline</span></span>
- <span data-ttu-id="83572-137">Modeli değerlendirin ve geliştirmeyi yineleyin</span><span class="sxs-lookup"><span data-stu-id="83572-137">Evaluate the model and iterate to improve</span></span>
- <span data-ttu-id="83572-138">Modeli bir uygulamada kullanılmak üzere ikili biçime Kaydet</span><span class="sxs-lookup"><span data-stu-id="83572-138">Save the model into binary format, for use in an application</span></span>
- <span data-ttu-id="83572-139">Modeli bir **ıranseski** nesnesine geri yükleme</span><span class="sxs-lookup"><span data-stu-id="83572-139">Load the model back into an **ITransformer** object</span></span>
- <span data-ttu-id="83572-140">**CreatePredictionEngine. tahmin ()** öğesini çağırarak tahminleri yapın</span><span class="sxs-lookup"><span data-stu-id="83572-140">Make predictions by calling **CreatePredictionEngine.Predict()**</span></span>

![Veri oluşturma, işlem hattı geliştirme, model eğitimi, model değerlendirmesi ve model kullanımı bileşenleri dahil ML.NET uygulama geliştirme akışı](./media/mldotnet-annotated-workflow.png)

<span data-ttu-id="83572-142">Bu kavramların biraz daha ayrıntılı bir şekilde bakalım.</span><span class="sxs-lookup"><span data-stu-id="83572-142">Let's dig a little deeper into those concepts.</span></span>

## <a name="machine-learning-model"></a><span data-ttu-id="83572-143">Machine Learning modeli</span><span class="sxs-lookup"><span data-stu-id="83572-143">Machine learning model</span></span>

<span data-ttu-id="83572-144">ML.NET modeli, tahmin edilen çıkışa ulaşmak üzere giriş verilerinizde gerçekleştirilecek dönüşümleri içeren bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="83572-144">An ML.NET model is an object that contains transformations to perform on your input data to arrive at the predicted output.</span></span>

### <a name="basic"></a><span data-ttu-id="83572-145">Temel</span><span class="sxs-lookup"><span data-stu-id="83572-145">Basic</span></span>

<span data-ttu-id="83572-146">En temel model, yukarıdaki ev fiyat örneğinde olduğu gibi, bir sürekli miktarın birbiriyle orantılı olduğu iki boyutlu doğrusal regresyon olur.</span><span class="sxs-lookup"><span data-stu-id="83572-146">The most basic model is two-dimensional linear regression, where one continuous quantity is proportional to another, as in the house price example above.</span></span>

![Sapma ve ağırlık parametrelerine sahip doğrusal regresyon modeli](./media/linear-regression-model.svg)

<span data-ttu-id="83572-148">Model yalnızca: $Price = b + size \* w $.</span><span class="sxs-lookup"><span data-stu-id="83572-148">The model is simply: $Price = b + Size \* w$.</span></span> <span data-ttu-id="83572-149">$B $ ve $w $ parametreleri, bir dizi (boyut, Fiyat) çiftleriyle bir satıra göre tahmin edilir.</span><span class="sxs-lookup"><span data-stu-id="83572-149">The parameters $b$ and $w$ are estimated by fitting a line on a set of (size, price) pairs.</span></span> <span data-ttu-id="83572-150">Modelin parametrelerini bulmak için kullanılan verilere **eğitim verileri**denir.</span><span class="sxs-lookup"><span data-stu-id="83572-150">The data used to find the parameters of the model is called **training data**.</span></span> <span data-ttu-id="83572-151">Machine Learning modelinin girişleri **Özellikler**olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="83572-151">The inputs of a machine learning model are called **features**.</span></span> <span data-ttu-id="83572-152">Bu örnekte, $Size $ tek özelliktir.</span><span class="sxs-lookup"><span data-stu-id="83572-152">In this example, $Size$ is the only feature.</span></span> <span data-ttu-id="83572-153">Bir makine öğrenimi modelini eğitebilmeniz için kullanılan taban-Truth değerlerine **Etiketler**denir.</span><span class="sxs-lookup"><span data-stu-id="83572-153">The ground-truth values used to train a machine learning model are called **labels**.</span></span> <span data-ttu-id="83572-154">Burada eğitim verileri kümesindeki $Price $ değerleri etiketlerdir.</span><span class="sxs-lookup"><span data-stu-id="83572-154">Here, the $Price$ values in the training data set are the labels.</span></span>

### <a name="more-complex"></a><span data-ttu-id="83572-155">Daha karmaşık</span><span class="sxs-lookup"><span data-stu-id="83572-155">More complex</span></span>

<span data-ttu-id="83572-156">Daha karmaşık bir model, işlem metni açıklamasını kullanarak finansal işlemleri kategoriler halinde sınıflandırır.</span><span class="sxs-lookup"><span data-stu-id="83572-156">A more complex model classifies financial transactions into categories using the transaction text description.</span></span>

<span data-ttu-id="83572-157">Her işlem açıklaması, gereksiz sözcük ve karakterleri kaldırarak ve sözcük ve karakter kombinasyonlarını sayarak bir özellik kümesine bölünür.</span><span class="sxs-lookup"><span data-stu-id="83572-157">Each transaction description is broken down into a set of features by removing redundant words and characters, and counting word and character combinations.</span></span> <span data-ttu-id="83572-158">Özellik kümesi, eğitim verilerinde kategori kümesini temel alan doğrusal bir modeli eğiteetmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="83572-158">The feature set is used to train a linear model based on the set of categories in the training data.</span></span> <span data-ttu-id="83572-159">Daha benzer yeni bir açıklama, eğitim kümesindeki diğer bir deyişle, aynı kategoriye daha büyük olasılıkla atanır.</span><span class="sxs-lookup"><span data-stu-id="83572-159">The more similar a new description is to the ones in the training set, the more likely it will be assigned to the same category.</span></span>

![Metin sınıflandırması modeli](./media/text-classification-model.svg)

<span data-ttu-id="83572-161">Hem ev fiyat modeli hem de metin sınıflandırma modeli **Doğrusal** modellerdir.</span><span class="sxs-lookup"><span data-stu-id="83572-161">Both the house price model and the text classification model are **linear** models.</span></span> <span data-ttu-id="83572-162">Verilerinizin yapısına ve çözmeyle ilgili soruna bağlı olarak, **karar ağacı** modellerini, **Genelleştirilmiş** ek modellerini ve diğerlerini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83572-162">Depending on the nature of your data and the problem you are solving, you can also use **decision tree** models, **generalized additive** models, and others.</span></span> <span data-ttu-id="83572-163">[Görevler](./resources/tasks.md)' de modeller hakkında daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83572-163">You can find out more about the models in [Tasks](./resources/tasks.md).</span></span>

## <a name="data-preparation"></a><span data-ttu-id="83572-164">Veri hazırlama</span><span class="sxs-lookup"><span data-stu-id="83572-164">Data preparation</span></span>

<span data-ttu-id="83572-165">Çoğu durumda, kullanılabilir olan veriler makine öğrenimi modelini eğitmek için doğrudan kullanılmaya uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="83572-165">In most cases, the data that you have available isn't suitable to be used directly to train a machine learning model.</span></span> <span data-ttu-id="83572-166">Kuruluşunuzun parametrelerini bulmak için kullanılmadan önce ham verilerin hazırlanması veya önceden işlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="83572-166">The raw data needs to be prepared, or pre-processed, before it can be used to find the parameters of your model.</span></span> <span data-ttu-id="83572-167">Verilerinizin dize değerlerinden sayısal bir gösterimine dönüştürülmesi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="83572-167">Your data may need to be converted from string values to a numerical representation.</span></span> <span data-ttu-id="83572-168">Giriş verilerinizde gereksiz bilgilere sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83572-168">You might have redundant information in your input data.</span></span> <span data-ttu-id="83572-169">Giriş verilerinizin boyutlarını azaltmanız veya genişletmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="83572-169">You may need to reduce or expand the dimensions of your input data.</span></span> <span data-ttu-id="83572-170">Verilerinizin normalleştirilmesi veya ölçeklendirilmesi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="83572-170">Your data might need to be normalized or scaled.</span></span>

<span data-ttu-id="83572-171">[Ml.net öğreticileri](./tutorials/index.md) , belirli makine öğrenimi görevleri için kullanılan metin, görüntü, sayısal ve zaman serisi verileri için farklı veri işleme işlem hatları hakkında bilgi öğretin.</span><span class="sxs-lookup"><span data-stu-id="83572-171">The [ML.NET tutorials](./tutorials/index.md) teach you about different data processing pipelines for text, image, numerical, and time-series data used for specific machine learning tasks.</span></span>

<span data-ttu-id="83572-172">Verilerinizi [hazırlamak](./how-to-guides/prepare-data-ml-net.md) , veri hazırlığını daha genel olarak nasıl uygulayacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="83572-172">[How to prepare your data](./how-to-guides/prepare-data-ml-net.md) shows you how to apply data preparation more generally.</span></span>

<span data-ttu-id="83572-173">Kaynaklar bölümünde tüm [kullanılabilir dönüşümlerinin](./resources/transforms.md) bir özetini bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83572-173">You can find an appendix of all of the [available transformations](./resources/transforms.md) in the resources section.</span></span>

## <a name="model-evaluation"></a><span data-ttu-id="83572-174">Model değerlendirmesi</span><span class="sxs-lookup"><span data-stu-id="83572-174">Model evaluation</span></span>

<span data-ttu-id="83572-175">Modelinizi eğittikten sonra, gelecekteki tahminleri ne kadar iyi hale getirmek istediğinizi nasıl anlarsınız?</span><span class="sxs-lookup"><span data-stu-id="83572-175">Once you have trained your model, how do you know how well it will make future predictions?</span></span> <span data-ttu-id="83572-176">ML.NET ile modelinizi bazı yeni test verileri için değerlendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83572-176">With ML.NET, you can evaluate your model against some new test data.</span></span>

<span data-ttu-id="83572-177">Her makine öğrenimi görevi türü, modelin doğruluğunu ve duyarlığını test veri kümesine karşı değerlendirmek için kullanılan ölçümlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="83572-177">Each type of machine learning task has metrics used to evaluate the accuracy and precision of the model against the test data set.</span></span>

<span data-ttu-id="83572-178">Evin fiyat örneğimiz için **regresyon** görevini kullandık.</span><span class="sxs-lookup"><span data-stu-id="83572-178">For our house price example, we used the **Regression** task.</span></span> <span data-ttu-id="83572-179">Modeli değerlendirmek için, özgün örneğe aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="83572-179">To evaluate the model, add the following code to the original sample.</span></span>

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

<span data-ttu-id="83572-180">Değerlendirme ölçümleri, hatanın düşük bir şekilde olduğunu ve tahmin edilen çıkış ile test çıkışı arasındaki bağıntıdan yüksek olduğunu söyler.</span><span class="sxs-lookup"><span data-stu-id="83572-180">The evaluation metrics tell you that the error is low-ish, and that correlation between the predicted output and the test output is high.</span></span> <span data-ttu-id="83572-181">Ne kadar kolay oldu!</span><span class="sxs-lookup"><span data-stu-id="83572-181">That was easy!</span></span> <span data-ttu-id="83572-182">Gerçek örneklerde, iyi model ölçümleri elde etmek için daha fazla ayarlama yapılır.</span><span class="sxs-lookup"><span data-stu-id="83572-182">In real examples, it takes more tuning to achieve good model metrics.</span></span>

## <a name="mlnet-architecture"></a><span data-ttu-id="83572-183">ML.NET mimarisi</span><span class="sxs-lookup"><span data-stu-id="83572-183">ML.NET architecture</span></span>

<span data-ttu-id="83572-184">Bu bölümde, ML.NET mimari desenlerine gideceğiz.</span><span class="sxs-lookup"><span data-stu-id="83572-184">In this section, we go through the architectural patterns of ML.NET.</span></span> <span data-ttu-id="83572-185">Deneyimli bir .NET geliştiricisiyseniz, bu desenlerden bazıları size tanıdık gelecektir ve bazıları daha az tanıdık olacaktır.</span><span class="sxs-lookup"><span data-stu-id="83572-185">If you are an experienced .NET developer, some of these patterns will be familiar to you, and some will be less familiar.</span></span> <span data-ttu-id="83572-186">Sıkı bir şekilde tutun.</span><span class="sxs-lookup"><span data-stu-id="83572-186">Hold tight, while we dive in!</span></span>

<span data-ttu-id="83572-187">Bir ML.NET uygulaması bir nesneyle başlar <xref:Microsoft.ML.MLContext> .</span><span class="sxs-lookup"><span data-stu-id="83572-187">An ML.NET application starts with an <xref:Microsoft.ML.MLContext> object.</span></span> <span data-ttu-id="83572-188">Bu tekil nesne **kataloglar**içerir.</span><span class="sxs-lookup"><span data-stu-id="83572-188">This singleton object contains **catalogs**.</span></span> <span data-ttu-id="83572-189">Katalog, veri yükleme ve kaydetme, dönüşümler, tracılar ve model işlemi bileşenlerine yönelik bir fabrikadır.</span><span class="sxs-lookup"><span data-stu-id="83572-189">A catalog is a factory for data loading and saving, transforms, trainers, and model operation components.</span></span> <span data-ttu-id="83572-190">Her Katalog nesnesi farklı bileşen türlerini oluşturma yöntemlerine sahiptir:</span><span class="sxs-lookup"><span data-stu-id="83572-190">Each catalog object has methods to create the different types of components:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="83572-191">Veri yükleme ve kaydetme</span><span class="sxs-lookup"><span data-stu-id="83572-191">Data loading and saving</span></span>||<xref:Microsoft.ML.DataOperationsCatalog>||
|<span data-ttu-id="83572-192">Veri hazırlama</span><span class="sxs-lookup"><span data-stu-id="83572-192">Data preparation</span></span>||<xref:Microsoft.ML.TransformsCatalog>||
|<span data-ttu-id="83572-193">Eğitim algoritmaları</span><span class="sxs-lookup"><span data-stu-id="83572-193">Training algorithms</span></span>|<span data-ttu-id="83572-194">İkili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="83572-194">Binary classification</span></span>|<xref:Microsoft.ML.BinaryClassificationCatalog>||
||<span data-ttu-id="83572-195">Birden çok Lass sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="83572-195">Multiclass classification</span></span>|<xref:Microsoft.ML.MulticlassClassificationCatalog>||
||<span data-ttu-id="83572-196">Anormallik algılama</span><span class="sxs-lookup"><span data-stu-id="83572-196">Anomaly detection</span></span>|<xref:Microsoft.ML.AnomalyDetectionCatalog>||
||<span data-ttu-id="83572-197">Kümeleme</span><span class="sxs-lookup"><span data-stu-id="83572-197">Clustering</span></span>|<xref:Microsoft.ML.ClusteringCatalog>||
||<span data-ttu-id="83572-198">Tahmin etme</span><span class="sxs-lookup"><span data-stu-id="83572-198">Forecasting</span></span>|<xref:Microsoft.ML.ForecastingCatalog>||
||<span data-ttu-id="83572-199">Sıralamasına</span><span class="sxs-lookup"><span data-stu-id="83572-199">Ranking</span></span>|<xref:Microsoft.ML.RankingCatalog>||
||<span data-ttu-id="83572-200">Regresyon</span><span class="sxs-lookup"><span data-stu-id="83572-200">Regression</span></span>|<xref:Microsoft.ML.RegressionCatalog>||
||<span data-ttu-id="83572-201">Öneri</span><span class="sxs-lookup"><span data-stu-id="83572-201">Recommendation</span></span>|<xref:Microsoft.ML.RecommendationCatalog>|<span data-ttu-id="83572-202">`Microsoft.ML.Recommender`NuGet paketini ekleme</span><span class="sxs-lookup"><span data-stu-id="83572-202">add the `Microsoft.ML.Recommender` NuGet package</span></span>|
||<span data-ttu-id="83572-203">Zaman serisi</span><span class="sxs-lookup"><span data-stu-id="83572-203">TimeSeries</span></span>|<xref:Microsoft.ML.TimeSeriesCatalog>|<span data-ttu-id="83572-204">`Microsoft.ML.TimeSeries`NuGet paketini ekleme</span><span class="sxs-lookup"><span data-stu-id="83572-204">add the `Microsoft.ML.TimeSeries` NuGet package</span></span>|
|<span data-ttu-id="83572-205">Model kullanımı</span><span class="sxs-lookup"><span data-stu-id="83572-205">Model usage</span></span> ||<xref:Microsoft.ML.ModelOperationsCatalog>||

<span data-ttu-id="83572-206">Yukarıdaki kategorilerin her birinde oluşturma yöntemlerine gidebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83572-206">You can navigate to the creation methods in each of the above categories.</span></span> <span data-ttu-id="83572-207">Visual Studio 'yu kullanarak kataloglar IntelliSense aracılığıyla gösterilir.</span><span class="sxs-lookup"><span data-stu-id="83572-207">Using Visual Studio, the catalogs show up via IntelliSense.</span></span>

   ![Gerileme Eğitiminleri için IntelliSense](./media/catalog-intellisense.png)

### <a name="build-the-pipeline"></a><span data-ttu-id="83572-209">İşlem hattını oluşturma</span><span class="sxs-lookup"><span data-stu-id="83572-209">Build the pipeline</span></span>

<span data-ttu-id="83572-210">Her kataloğun içinde bir genişletme yöntemleri kümesidir.</span><span class="sxs-lookup"><span data-stu-id="83572-210">Inside each catalog is a set of extension methods.</span></span> <span data-ttu-id="83572-211">Bir eğitim işlem hattı oluşturmak için uzantı yöntemlerinin nasıl kullanıldığına göz atalım.</span><span class="sxs-lookup"><span data-stu-id="83572-211">Let's look at how extension methods are used to create a training pipeline.</span></span>

```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
        .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));
```

<span data-ttu-id="83572-212">Kod parçacığında `Concatenate` ve `Sdca` her iki yöntemde de bulunur.</span><span class="sxs-lookup"><span data-stu-id="83572-212">In the snippet, `Concatenate` and `Sdca` are both methods in the catalog.</span></span> <span data-ttu-id="83572-213">Bunlar, işlem hattının sonuna eklenen bir [ıestimator](xref:Microsoft.ML.IEstimator%601) nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="83572-213">They each create an [IEstimator](xref:Microsoft.ML.IEstimator%601) object that is appended to the pipeline.</span></span>

<span data-ttu-id="83572-214">Bu noktada, nesneler yalnızca oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="83572-214">At this point, the objects are created only.</span></span> <span data-ttu-id="83572-215">Yürütme yapılmadı.</span><span class="sxs-lookup"><span data-stu-id="83572-215">No execution has happened.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="83572-216">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="83572-216">Train the model</span></span>

<span data-ttu-id="83572-217">İşlem hattındaki nesneler oluşturulduktan sonra, modeli eğitebilmeniz için veriler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="83572-217">Once the objects in the pipeline have been created, data can be used to train the model.</span></span>

```csharp
    var model = pipeline.Fit(trainingData);
```

<span data-ttu-id="83572-218">Çağırma, `Fit()` modelin parametrelerini tahmin etmek için giriş eğitim verilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="83572-218">Calling `Fit()` uses the input training data to estimate the parameters of the model.</span></span> <span data-ttu-id="83572-219">Bu, modeli eğitme olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="83572-219">This is known as training the model.</span></span> <span data-ttu-id="83572-220">Yukarıdaki doğrusal regresyon modelinin iki model parametresi olduğunu unutmayın: **sapma** ve **Ağırlık**.</span><span class="sxs-lookup"><span data-stu-id="83572-220">Remember, the linear regression model above had two model parameters: **bias** and **weight**.</span></span> <span data-ttu-id="83572-221">Çağrıdan sonra `Fit()` parametrelerin değerleri bilinmektedir.</span><span class="sxs-lookup"><span data-stu-id="83572-221">After the `Fit()` call, the values of the parameters are known.</span></span> <span data-ttu-id="83572-222">Çoğu modelde bundan çok daha fazla parametre olacaktır.</span><span class="sxs-lookup"><span data-stu-id="83572-222">Most models will have many more parameters than this.</span></span>

<span data-ttu-id="83572-223">[Modelinizi eğitme](./how-to-guides/train-machine-learning-model-ml-net.md)hakkında daha fazla bilgi için model eğitimi hakkında daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83572-223">You can learn more about model training in [How to train your model](./how-to-guides/train-machine-learning-model-ml-net.md).</span></span>

<span data-ttu-id="83572-224">Elde edilen model nesnesi arabirimini uygular <xref:Microsoft.ML.ITransformer> .</span><span class="sxs-lookup"><span data-stu-id="83572-224">The resulting model object implements the <xref:Microsoft.ML.ITransformer> interface.</span></span> <span data-ttu-id="83572-225">Diğer bir deyişle, model giriş verilerini tahmine göre dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="83572-225">That is, the model transforms input data into predictions.</span></span>

```csharp
   IDataView predictions = model.Transform(inputData);
```

### <a name="use-the-model"></a><span data-ttu-id="83572-226">Modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="83572-226">Use the model</span></span>

<span data-ttu-id="83572-227">Giriş verilerini toplu olarak veya bir girişte tek seferde tahmin edilecek şekilde dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83572-227">You can transform input data into predictions in bulk, or one input at a time.</span></span> <span data-ttu-id="83572-228">Ev fiyatı örneğinde, her ikisi de, modeli değerlendirmek amacıyla toplu olarak ve yeni bir tahmin oluşturmak için bir seferde bir kez yaptık.</span><span class="sxs-lookup"><span data-stu-id="83572-228">In the house price example, we did both: in bulk for the purpose of evaluating the model, and one at a time to make a new prediction.</span></span> <span data-ttu-id="83572-229">Tek tahmin yapmaya bakalım.</span><span class="sxs-lookup"><span data-stu-id="83572-229">Let's look at making single predictions.</span></span>

```csharp
    var size = new HouseData() { Size = 2.5F };
    var predEngine = mlContext.CreatePredictionEngine<HouseData, Prediction>(model);
    var price = predEngine.Predict(size);
```

<span data-ttu-id="83572-230">`CreatePredictionEngine()`Yöntemi bir giriş sınıfı ve bir çıkış sınıfı alır.</span><span class="sxs-lookup"><span data-stu-id="83572-230">The `CreatePredictionEngine()` method takes an input class and an output class.</span></span> <span data-ttu-id="83572-231">Alan adları ve/veya kod öznitelikleri, model eğitimi ve tahmin sırasında kullanılan veri sütunlarının adlarını belirlenir.</span><span class="sxs-lookup"><span data-stu-id="83572-231">The field names and/or code attributes determine the names of the data columns used during model training and prediction.</span></span> <span data-ttu-id="83572-232">Daha fazla bilgi için bkz. [eğitilen bir modelle Öngörüler yapma](how-to-guides/machine-learning-model-predictions-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="83572-232">For more information, see [Make predictions with a trained model](how-to-guides/machine-learning-model-predictions-ml-net.md).</span></span>

### <a name="data-models-and-schema"></a><span data-ttu-id="83572-233">Veri modelleri ve şema</span><span class="sxs-lookup"><span data-stu-id="83572-233">Data models and schema</span></span>

<span data-ttu-id="83572-234">Bir ML.NET Machine Learning işlem hattının Core 'da [DataView](xref:Microsoft.ML.IDataView) nesneleri bulunur.</span><span class="sxs-lookup"><span data-stu-id="83572-234">At the core of an ML.NET machine learning pipeline are [DataView](xref:Microsoft.ML.IDataView) objects.</span></span>

<span data-ttu-id="83572-235">İşlem hattındaki her dönüşümde bir giriş şeması (veri adları, türler ve boyutlar, dönüştürmenin girişte görmeyi beklediği boyutlar) vardır; ve bir çıkış şeması (veri adları, türler ve dönüşümün dönüşümden sonra ürettiği boyutlar).</span><span class="sxs-lookup"><span data-stu-id="83572-235">Each transformation in the pipeline has an input schema (data names, types, and sizes that the transform expects to see on its input); and an output schema (data names, types, and sizes that the transform produces after the transformation).</span></span> <span data-ttu-id="83572-236">Aşağıdaki belge, [ıdataview arabiriminin ve tür sisteminin](https://xadupre.github.io/machinelearningext/mlnetdocs/idataviewtypesystem.html)ayrıntılı bir açıklamasını sunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="83572-236">The following document provides an in-depth explanation of the [IDataView interface and its type system](https://xadupre.github.io/machinelearningext/mlnetdocs/idataviewtypesystem.html).</span></span>

<span data-ttu-id="83572-237">İşlem hattındaki bir dönüşümden çıkış şeması, sonraki dönüşümün giriş şemasıyla eşleşmiyorsa, ML.NET bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="83572-237">If the output schema from one transform in the pipeline doesn't match the input schema of the next transform, ML.NET will throw an exception.</span></span>

<span data-ttu-id="83572-238">Veri görünümü nesnesinin sütunları ve satırları vardır.</span><span class="sxs-lookup"><span data-stu-id="83572-238">A data view object has columns and rows.</span></span> <span data-ttu-id="83572-239">Her sütunun bir adı ve bir türü ve uzunluğu vardır.</span><span class="sxs-lookup"><span data-stu-id="83572-239">Each column has a name and a type and a length.</span></span> <span data-ttu-id="83572-240">Örneğin, ev fiyatı örnekteki giriş sütunları **Boyut** ve **fiyattır**.</span><span class="sxs-lookup"><span data-stu-id="83572-240">For example, the input columns in the house price example are **Size** and **Price**.</span></span> <span data-ttu-id="83572-241">Bunlar her ikisi de aynıdır ve vektörler yerine skaler miktarlardır.</span><span class="sxs-lookup"><span data-stu-id="83572-241">They are both type and they are scalar quantities rather than vector ones.</span></span>

   ![ML.NET veri görünümü örneği, ev fiyatı tahmin verileri](./media/ml-net-dataview.png)

<span data-ttu-id="83572-243">Tüm ML.NET algoritmaları vektör olan bir giriş sütununu arar.</span><span class="sxs-lookup"><span data-stu-id="83572-243">All ML.NET algorithms look for an input column that is a vector.</span></span> <span data-ttu-id="83572-244">Varsayılan olarak bu vektör sütununa **Özellikler**denir.</span><span class="sxs-lookup"><span data-stu-id="83572-244">By default this vector column is called **Features**.</span></span> <span data-ttu-id="83572-245">Bu nedenle, **Boyut** sütununu, evin fiyat örneğimizde **Özellikler** adlı yeni bir sütuna bitiştirtik.</span><span class="sxs-lookup"><span data-stu-id="83572-245">This is why we concatenated the **Size** column into a new column called **Features** in our house price example.</span></span>

 ```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
 ```

<span data-ttu-id="83572-246">Tüm algoritmalar Ayrıca bir tahmin gerçekleştirildikten sonra yeni sütunlar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="83572-246">All algorithms also create new columns after they have performed a prediction.</span></span> <span data-ttu-id="83572-247">Bu yeni sütunların sabit adları makine öğrenimi algoritmasının türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="83572-247">The fixed names of these new columns depend on the type of machine learning algorithm.</span></span> <span data-ttu-id="83572-248">Regresyon görevi için, yeni sütunlardan birine **puan**denir.</span><span class="sxs-lookup"><span data-stu-id="83572-248">For the regression task, one of the new columns is called **Score**.</span></span> <span data-ttu-id="83572-249">Bu nedenle fiyat verilerimizi bu adla ekledik.</span><span class="sxs-lookup"><span data-stu-id="83572-249">This is why we attributed our price data with this name.</span></span>

```csharp
    public class Prediction
    {
        [ColumnName("Score")]
        public float Price { get; set; }
    }
```

<span data-ttu-id="83572-250">[Machine Learning görevler](resources/tasks.md) kılavuzunda, farklı makine öğrenimi görevlerinin çıkış sütunları hakkında daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83572-250">You can find out more about output columns of different machine learning tasks in the [Machine Learning Tasks](resources/tasks.md) guide.</span></span>

<span data-ttu-id="83572-251">DataView nesnelerinin önemli bir özelliği, **geç**değerlendirilmesinden kaynaklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="83572-251">An important property of DataView objects is that they are evaluated **lazily**.</span></span> <span data-ttu-id="83572-252">Veri görünümleri yalnızca model eğitimi ve değerlendirmesi sırasında yüklenir ve üzerinde çalıştırılır ve veri tahmini yapılır.</span><span class="sxs-lookup"><span data-stu-id="83572-252">Data views are only loaded and operated on during model training and evaluation, and data prediction.</span></span> <span data-ttu-id="83572-253">ML.NET uygulamanızı yazarken ve test ederken, [Önizleme](xref:Microsoft.ML.DebuggerExtensions.Preview%2A) yöntemini çağırarak herhangi bir veri görünümü nesnesine bir göz atma işlemleri yapmak Için Visual Studio hata ayıklayıcısını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83572-253">While you are writing and testing your ML.NET application, you can use the Visual Studio debugger to take a peek at any data view object by calling the [Preview](xref:Microsoft.ML.DebuggerExtensions.Preview%2A) method.</span></span>

```csharp
    var debug = testPriceDataView.Preview();
```

<span data-ttu-id="83572-254">`debug`Değişkeni hata ayıklayıcıda izleyebilir ve içeriğini inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83572-254">You can watch the `debug` variable in the debugger and examine its contents.</span></span> <span data-ttu-id="83572-255">Performansı önemli ölçüde düşürür, üretim kodunda önizleme yöntemini kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="83572-255">Do not use the Preview method in production code, as it significantly degrades performance.</span></span>

### <a name="model-deployment"></a><span data-ttu-id="83572-256">Model dağıtımı</span><span class="sxs-lookup"><span data-stu-id="83572-256">Model Deployment</span></span>

<span data-ttu-id="83572-257">Gerçek yaşam uygulamalarında, model eğitimi ve değerlendirme kodunuz tahmininizden ayrı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="83572-257">In real-life applications, your model training and evaluation code will be separate from your prediction.</span></span> <span data-ttu-id="83572-258">Aslında, bu iki etkinlik genellikle ayrı takımlar tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="83572-258">In fact, these two activities are often performed by separate teams.</span></span> <span data-ttu-id="83572-259">Model geliştirme ekibiniz, modeli tahmin uygulamasında kullanım için kaydedebilir.</span><span class="sxs-lookup"><span data-stu-id="83572-259">Your model development team can save the model for use in the prediction application.</span></span>

```csharp
   mlContext.Model.Save(model, trainingData.Schema,"model.zip");
```

## <a name="next-steps"></a><span data-ttu-id="83572-260">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="83572-260">Next steps</span></span>

* <span data-ttu-id="83572-261">[Öğreticilerde](./tutorials/index.md)daha gerçekçi veri kümeleriyle farklı makine öğrenimi görevleri kullanarak uygulama oluşturmayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="83572-261">Learn how to build applications using different machine learning tasks with more realistic data sets in the [tutorials](./tutorials/index.md).</span></span>

* <span data-ttu-id="83572-262">Belirli konular hakkında daha ayrıntılı bilgi edinmek Için bkz. [nasıl yapılır kılavuzlarında](./how-to-guides/index.md).</span><span class="sxs-lookup"><span data-stu-id="83572-262">Learn about specific topics in more depth in the [How To Guides](./how-to-guides/index.md).</span></span>

* <span data-ttu-id="83572-263">Süper kez kullanıyorsanız, [API başvuru belgelerine](../../api/index.md?view=ml-dotnet)doğrudan gidebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83572-263">If you're super keen, you can dive straight into the [API Reference documentation](../../api/index.md?view=ml-dotnet).</span></span>
