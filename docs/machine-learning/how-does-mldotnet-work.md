---
title: ML.NET nedir ve nasıl çalışır?
description: ML.NET machine Learning'i .NET uygulamalarına ekleme olanağı sunar. Bu özellik sayesinde, uygulamanızın kullanabileceği verileri kullanarak otomatik tahmin yapabilirsiniz. Bu makalede, makine öğrenimi ML.NET temelleri açıklanır.
ms.date: 04/10/2019
ms.topic: overview
ms.custom: mvc
ms.author: nakersha
author: natke
ms.openlocfilehash: 054fa0e1d9d8cc0d7c32efd4a9e8c81b91cb1335
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65960433"
---
# <a name="what-is-mlnet-and-how-does-it-work"></a><span data-ttu-id="d8f15-105">ML.NET nedir ve nasıl çalışır?</span><span class="sxs-lookup"><span data-stu-id="d8f15-105">What is ML.NET and how does it work?</span></span>

<span data-ttu-id="d8f15-106">ML.NET machine Learning'i .NET uygulamalarına ekleme olanağı sunar.</span><span class="sxs-lookup"><span data-stu-id="d8f15-106">ML.NET gives you the ability to add machine learning to .NET applications.</span></span> <span data-ttu-id="d8f15-107">Bu özellik sayesinde, uygulamanızın kullanabileceği verileri kullanarak otomatik tahmin yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8f15-107">With this capability, you can make automatic predictions using the data available to your application.</span></span> <span data-ttu-id="d8f15-108">Bu makalede, makine öğrenimi ML.NET temelleri açıklanır.</span><span class="sxs-lookup"><span data-stu-id="d8f15-108">This article explains the basics of machine learning in ML.NET.</span></span> 

<span data-ttu-id="d8f15-109">ML.NET ile yapabileceğiniz Öngörüler türü örnekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d8f15-109">Examples of the type of predictions that you can make with ML.NET include:</span></span>

|||
|-|-|
|<span data-ttu-id="d8f15-110">Sınıflandırma/kategorilere ayırma</span><span class="sxs-lookup"><span data-stu-id="d8f15-110">Classification/Categorization</span></span>|<span data-ttu-id="d8f15-111">Müşteri geri bildirimi pozitif ve negatif kategoriler halinde otomatik olarak Böl</span><span class="sxs-lookup"><span data-stu-id="d8f15-111">Automatically divide customer feedback into positive and negative categories</span></span>|
|<span data-ttu-id="d8f15-112">Regresyon/Predıct sürekli değerleri</span><span class="sxs-lookup"><span data-stu-id="d8f15-112">Regression/Predict continuous values</span></span>|<span data-ttu-id="d8f15-113">Görev açısından kritik uygulamaları boyutu ve konuma bağlı fiyatını tahmin edin</span><span class="sxs-lookup"><span data-stu-id="d8f15-113">Predict the price of houses based on size and location</span></span>|
|<span data-ttu-id="d8f15-114">Anomali Algılama</span><span class="sxs-lookup"><span data-stu-id="d8f15-114">Anomaly Detection</span></span>|<span data-ttu-id="d8f15-115">Sahte bankacılık işlemleri algılayın</span><span class="sxs-lookup"><span data-stu-id="d8f15-115">Detect fraudulent banking transactions</span></span> |
|<span data-ttu-id="d8f15-116">Öneriler</span><span class="sxs-lookup"><span data-stu-id="d8f15-116">Recommendations</span></span>|<span data-ttu-id="d8f15-117">Önceki aldıklarını temel satın almak için çevrimiçi bir adamın isteyebileceğiniz ürünler önerin</span><span class="sxs-lookup"><span data-stu-id="d8f15-117">Suggest products that online shoppers may want to buy, based on their previous purchases</span></span>|

## <a name="hello-mlnet-world"></a><span data-ttu-id="d8f15-118">ML.NET World Hello</span><span class="sxs-lookup"><span data-stu-id="d8f15-118">Hello ML.NET World</span></span>

<span data-ttu-id="d8f15-119">Aşağıdaki kod parçacığında kod basit ML.NET uygulamayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8f15-119">The code in the following snippet demonstrates the simplest ML.NET application.</span></span> <span data-ttu-id="d8f15-120">Bu örneği kullanarak merkezi boyutu ve fiyat veri merkezi fiyatlarını tahmin etmek için bir doğrusal regresyon modeli oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d8f15-120">This example constructs a linear regression model to predict house prices using house size and price data.</span></span> <span data-ttu-id="d8f15-121">Gerçek zamanlı konuşmaların uygulamalarınızı, verilerinizi ve model çok daha karmaşık olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d8f15-121">In your real-life applications, your data and model will be much more complex.</span></span>

 ```csharp
    using System;
    using System.IO;
    using Microsoft.Data.DataView;
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

## <a name="code-workflow"></a><span data-ttu-id="d8f15-122">İş akışı kodu</span><span class="sxs-lookup"><span data-stu-id="d8f15-122">Code workflow</span></span>

<span data-ttu-id="d8f15-123">Aşağıdaki diyagramda, yinelemeli model geliştirme sürecinin yanı sıra uygulama kod yapısını temsil eder:</span><span class="sxs-lookup"><span data-stu-id="d8f15-123">The following diagram represents the application code structure, as well as the iterative process of model development:</span></span>
- <span data-ttu-id="d8f15-124">Toplama ve yük eğitim verilerini bir **IDataView** nesnesi</span><span class="sxs-lookup"><span data-stu-id="d8f15-124">Collect and load training data into an **IDataView** object</span></span>
- <span data-ttu-id="d8f15-125">İşlem özellikleri ayıklayın ve makine öğrenme algoritmasına uygulamak için bir işlem hattı belirtin</span><span class="sxs-lookup"><span data-stu-id="d8f15-125">Specify a pipeline of operations to extract features and apply a machine learning algorithm</span></span>
- <span data-ttu-id="d8f15-126">Çağırarak bir model eğitip **Fit()** işlem hattında</span><span class="sxs-lookup"><span data-stu-id="d8f15-126">Train a model by calling **Fit()** on the pipeline</span></span>
- <span data-ttu-id="d8f15-127">Modeli değerlendirme ve geliştirmek için yineleme</span><span class="sxs-lookup"><span data-stu-id="d8f15-127">Evaluate the model and iterate to improve</span></span>
- <span data-ttu-id="d8f15-128">Model kullanmak bir uygulamada ikili biçimde kaydedin</span><span class="sxs-lookup"><span data-stu-id="d8f15-128">Save the model into binary format, for use in an application</span></span>
- <span data-ttu-id="d8f15-129">Modeline geri yüklemek bir **ITransformer** nesnesi</span><span class="sxs-lookup"><span data-stu-id="d8f15-129">Load the model back into an **ITransformer** object</span></span>
- <span data-ttu-id="d8f15-130">Çağırarak tahminlerde **CreatePredictionEngine.Predict()**</span><span class="sxs-lookup"><span data-stu-id="d8f15-130">Make predictions by calling **CreatePredictionEngine.Predict()**</span></span>

![ML.NET verisi oluşturma, ardışık düzen geliştirme, model eğitiminin, model değerlendirme ve model kullanımı için bileşenler dahil olmak üzere uygulama geliştirme akışı](./media/mldotnet-annotated-workflow.png) 

<span data-ttu-id="d8f15-132">Biraz söz konusu kavrama biraz daha ayrıntılı açıklayalım.</span><span class="sxs-lookup"><span data-stu-id="d8f15-132">Let's dig a little deeper into those concepts.</span></span>

## <a name="machine-learning-model"></a><span data-ttu-id="d8f15-133">Machine learning modeli</span><span class="sxs-lookup"><span data-stu-id="d8f15-133">Machine learning model</span></span>

<span data-ttu-id="d8f15-134">ML.NET modeli tahmin edilen çıktısına gelmesi giriş verileriniz üzerinde gerçekleştirmek için dönüşümleri içeren bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="d8f15-134">An ML.NET model is an object that contains transformations to perform on your input data to arrive at the predicted output.</span></span>

### <a name="basic"></a><span data-ttu-id="d8f15-135">Temel</span><span class="sxs-lookup"><span data-stu-id="d8f15-135">Basic</span></span>

<span data-ttu-id="d8f15-136">En temel iki boyutlu doğrusal regresyon, sürekli bir miktar yukarıdaki ev fiyat örnekte olduğu gibi başka orantılı olduğu modelidir.</span><span class="sxs-lookup"><span data-stu-id="d8f15-136">The most basic model is two-dimensional linear regression, where one continuous quantity is proportional to another, as in the house price example above.</span></span> 

![Doğrusal regresyon modeli sapması ve Ağırlık parametrelere sahip](./media/linear-regression-model.svg)

<span data-ttu-id="d8f15-138">Yalnızca modelidir: $Price = b + boyutu \* w$.</span><span class="sxs-lookup"><span data-stu-id="d8f15-138">The model is simply: $Price = b + Size \* w$.</span></span> <span data-ttu-id="d8f15-139">Bir dizi üzerinde bir uydurur $w$ ve parametreleri $b$ tahmini (boyut, Fiyat) çiftleri.</span><span class="sxs-lookup"><span data-stu-id="d8f15-139">The parameters $b$ and $w$ are estimated by fitting a line on a set of (size, price) pairs.</span></span> <span data-ttu-id="d8f15-140">Model parametreleri bulmak için kullanılan verileri çağrılır **eğitim verilerini**.</span><span class="sxs-lookup"><span data-stu-id="d8f15-140">The data used to find the parameters of the model is called **training data**.</span></span> <span data-ttu-id="d8f15-141">Makine öğrenme modeli girişleri olarak adlandırılan **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="d8f15-141">The inputs of a machine learning model are called **features**.</span></span> <span data-ttu-id="d8f15-142">Bu örnekte, $Size$ yalnızca özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="d8f15-142">In this example, $Size$ is the only feature.</span></span> <span data-ttu-id="d8f15-143">Machine learning modelini eğitmek için kullanılan taban truth değerler olarak adlandırılan **etiketleri**.</span><span class="sxs-lookup"><span data-stu-id="d8f15-143">The ground-truth values used to train a machine learning model are called **labels**.</span></span> <span data-ttu-id="d8f15-144">Burada, $Price$ eğitim veri kümesi etiketleri değerler.</span><span class="sxs-lookup"><span data-stu-id="d8f15-144">Here, the $Price$ values in the training data set are the labels.</span></span>

### <a name="more-complex"></a><span data-ttu-id="d8f15-145">Daha karmaşık</span><span class="sxs-lookup"><span data-stu-id="d8f15-145">More complex</span></span>

<span data-ttu-id="d8f15-146">Daha karmaşık bir model kullanarak işlem metin açıklama kategoriler halinde Finansal işlemler sınıflandırır.</span><span class="sxs-lookup"><span data-stu-id="d8f15-146">A more complex model classifies financial transactions into categories using the transaction text description.</span></span>

<span data-ttu-id="d8f15-147">Her bir işlem açıklaması bir özellikler kümesi yedekli sözcükler ve karakterleri kaldırarak ve word ve karakter birleşimini sayım ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="d8f15-147">Each transaction description is broken down into a set of features by removing redundant words and characters, and counting word and character combinations.</span></span> <span data-ttu-id="d8f15-148">Özellik kümesini kategorileri eğitim veri kümesi temel olarak doğrusal bir model eğitip için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d8f15-148">The feature set is used to train a linear model based on the set of categories in the training data.</span></span> <span data-ttu-id="d8f15-149">Daha yeni bir açıklama için Eğitim kümesi dışındaki benzer, büyük olasılıkla aynı kategoriye atanır.</span><span class="sxs-lookup"><span data-stu-id="d8f15-149">The more similar a new description is to the ones in the training set, the more likely it will be assigned to the same category.</span></span> 

![Metin sınıflandırma modeli](./media/text-classification-model.svg)

<span data-ttu-id="d8f15-151">Hem merkezi fiyat modeli, hem de metin sınıflandırma modeli **doğrusal** modelleri.</span><span class="sxs-lookup"><span data-stu-id="d8f15-151">Both the house price model and the text classification model are **linear** models.</span></span> <span data-ttu-id="d8f15-152">Verilerinizi ve Çözdüğünüz sorunun doğasına bağlı olarak da kullanabilirsiniz **karar ağacı** modelleri **eklenebilir genelleştirilmiş** modelleri ve diğerleri.</span><span class="sxs-lookup"><span data-stu-id="d8f15-152">Depending on the nature of your data and the problem you are solving, you can also use **decision tree** models, **generalized additive** models, and others.</span></span> <span data-ttu-id="d8f15-153">Modelleri hakkında daha fazla bilgi bulabilirsiniz [görevleri](./resources/tasks.md).</span><span class="sxs-lookup"><span data-stu-id="d8f15-153">You can find out more about the models in [Tasks](./resources/tasks.md).</span></span>

## <a name="data-preparation"></a><span data-ttu-id="d8f15-154">Veri hazırlama</span><span class="sxs-lookup"><span data-stu-id="d8f15-154">Data preparation</span></span>

<span data-ttu-id="d8f15-155">Çoğu durumda veriler kullanılabilir olduğunu doğrudan makine öğrenme modeli eğitmek için kullanılacak uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="d8f15-155">In most cases, the data that you have available isn't suitable to be used directly to train a machine learning model.</span></span> <span data-ttu-id="d8f15-156">Ham verileri hazırlanmış veya modelinizin parametreleri bulmak için kullanılmadan önce ön işlemden gerekir.</span><span class="sxs-lookup"><span data-stu-id="d8f15-156">The raw data needs to be prepared, or pre-processed before it can be used to find the parameters of your model.</span></span> <span data-ttu-id="d8f15-157">Verilerinizi dize değerlerden bir sayısal gösterimine dönüştürülmesi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="d8f15-157">Your data may need to be converted from string values to a numerical representation.</span></span> <span data-ttu-id="d8f15-158">Girdi verilerinizi yedekli bilgiler olabilir.</span><span class="sxs-lookup"><span data-stu-id="d8f15-158">You might have redundant information in your input data.</span></span> <span data-ttu-id="d8f15-159">Azaltın veya girişinizi boyutlarını genişletin gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="d8f15-159">You may need to reduce or expand the dimensions of your input data.</span></span> <span data-ttu-id="d8f15-160">Verilerinizi normalleştirilmiş veya ölçeklendirildiğinde gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="d8f15-160">Your data might need to be normalized or scaled.</span></span>

<span data-ttu-id="d8f15-161">[ML.NET öğreticiler](./tutorials/index.md) görüntü farklı veri işleme komut zincirini metin için ilgili öğretin, belirli bir makine öğrenimi görevlerini için kullanılan sayısal ve zaman serisi verileri.</span><span class="sxs-lookup"><span data-stu-id="d8f15-161">The [ML.NET tutorials](./tutorials/index.md) teach you about different data processing pipelines for text, image, numerical, and time-series data used for specific machine learning tasks.</span></span>

<span data-ttu-id="d8f15-162">[Verilerinizi hazırlama](./how-to-guides/prepare-data-ml-net.md) gösterilmektedir veri hazırlama daha genel olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d8f15-162">[How to prepare your data](./how-to-guides/prepare-data-ml-net.md) shows you how to applied data preparation more generally.</span></span>

<span data-ttu-id="d8f15-163">Tüm ek bulabilirsiniz [kullanılabilir dönüştürmeler](./resources/transforms.md) kaynaklar bölümünde.</span><span class="sxs-lookup"><span data-stu-id="d8f15-163">You can find an appendix of all of the [available transformations](./resources/transforms.md) in the resources section.</span></span>

## <a name="model-evaluation"></a><span data-ttu-id="d8f15-164">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="d8f15-164">Model evaluation</span></span>

<span data-ttu-id="d8f15-165">Nasıl modelinizi eğitim almış sonra ne kadar iyi gelecekteki tahminler yapar biliyor musunuz?</span><span class="sxs-lookup"><span data-stu-id="d8f15-165">Once you have trained your model, how do you know how well it will make future predictions?</span></span> <span data-ttu-id="d8f15-166">ML.NET ile modelinizi yeni bazı test verilerini karşı değerlendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8f15-166">With ML.NET, you can evaluate your model against some new test data.</span></span> 

<span data-ttu-id="d8f15-167">Machine learning görevinin her türü doğruluk ve sınama veri kümesi modelinde duyarlığını değerlendirmek için kullanılan ölçümü mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="d8f15-167">Each type of machine learning task has metrics used to evaluate the accuracy and precision of the model against the test data set.</span></span>

<span data-ttu-id="d8f15-168">Ev fiyat Örneğimiz için kullandığımız **regresyon** görev.</span><span class="sxs-lookup"><span data-stu-id="d8f15-168">For our house price example, we used the **Regression** task.</span></span> <span data-ttu-id="d8f15-169">Modeli değerlendirme için özgün örneğe aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d8f15-169">To evaluate the model, add the following code to the original sample.</span></span>

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

<span data-ttu-id="d8f15-170">Değerlendirme ölçümleri low-ish bir hatadır ve bu bağıntı tahmin edilen çıkış ve test çıkışı arasında yüksek olduğunu bildirin.</span><span class="sxs-lookup"><span data-stu-id="d8f15-170">The evaluation metrics tell you that the error is low-ish, and that correlation between the predicted output and the test output is high.</span></span> <span data-ttu-id="d8f15-171">Bu kadar kolay!</span><span class="sxs-lookup"><span data-stu-id="d8f15-171">That was easy!</span></span> <span data-ttu-id="d8f15-172">Gerçek örneklerde, daha fazla iyi model ölçümleri elde etmek için ayarlama alır.</span><span class="sxs-lookup"><span data-stu-id="d8f15-172">In real examples, it takes more tuning to achieve good model metrics.</span></span>

## <a name="mlnet-architecture"></a><span data-ttu-id="d8f15-173">ML.NET mimarisi</span><span class="sxs-lookup"><span data-stu-id="d8f15-173">ML.NET architecture</span></span>

<span data-ttu-id="d8f15-174">Bu bölümde, biz ML.NET Mimari desenleri gidin.</span><span class="sxs-lookup"><span data-stu-id="d8f15-174">In this section, we go through the architectural patterns of ML.NET.</span></span> <span data-ttu-id="d8f15-175">Deneyimli bir .NET geliştiricisi kullanıyorsanız, bu desenleri bazıları size tanıdık gelecektir ve bazı küçük tanıdık gelecektir.</span><span class="sxs-lookup"><span data-stu-id="d8f15-175">If you are an experienced .NET developer, some of these patterns will be familiar to you, and some will be less familiar.</span></span> <span data-ttu-id="d8f15-176">Biz kolları sıvayın sıkı, basılı!</span><span class="sxs-lookup"><span data-stu-id="d8f15-176">Hold tight, while we dive in!</span></span>

<span data-ttu-id="d8f15-177">ML.NET uygulama ile başlayan bir <xref:Microsoft.ML.MLContext> nesne.</span><span class="sxs-lookup"><span data-stu-id="d8f15-177">An ML.NET application starts with an <xref:Microsoft.ML.MLContext> object.</span></span> <span data-ttu-id="d8f15-178">Bu tekil nesnesini içeren **katalogları**.</span><span class="sxs-lookup"><span data-stu-id="d8f15-178">This singleton object contains **catalogs**.</span></span> <span data-ttu-id="d8f15-179">Veri yükleme ve kaydetme, dönüşümler ve Eğitmenler modeli işlemi bileşenleri için bir üreteci kataloğudur.</span><span class="sxs-lookup"><span data-stu-id="d8f15-179">A catalog is a factory for data loading and saving, transforms, trainers, and model operation components.</span></span> <span data-ttu-id="d8f15-180">Her bir katalog nesnesi bileşenleri farklı türleri oluşturmak için yöntemleri vardır:</span><span class="sxs-lookup"><span data-stu-id="d8f15-180">Each catalog object has methods to create the different types of components:</span></span>

||||
|-|-|-|
|<span data-ttu-id="d8f15-181">Veri yükleme ve kaydetme</span><span class="sxs-lookup"><span data-stu-id="d8f15-181">Data loading and saving</span></span>||<xref:Microsoft.ML.DataOperationsCatalog>|
|<span data-ttu-id="d8f15-182">Veri hazırlama</span><span class="sxs-lookup"><span data-stu-id="d8f15-182">Data preparation</span></span>||<xref:Microsoft.ML.TransformsCatalog>|
|<span data-ttu-id="d8f15-183">Eğitim algoritmaları</span><span class="sxs-lookup"><span data-stu-id="d8f15-183">Training algorithms</span></span>|<span data-ttu-id="d8f15-184">İkili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="d8f15-184">Binary classification</span></span>|<xref:Microsoft.ML.BinaryClassificationCatalog>|
||<span data-ttu-id="d8f15-185">Sınıflı sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="d8f15-185">Multiclass classification</span></span>|<xref:Microsoft.ML.MulticlassClassificationCatalog>|
||<span data-ttu-id="d8f15-186">Anomali algılama</span><span class="sxs-lookup"><span data-stu-id="d8f15-186">Anomaly detection</span></span>|<xref:Microsoft.ML.AnomalyDetectionCatalog>|
||<span data-ttu-id="d8f15-187">Derecelendirme</span><span class="sxs-lookup"><span data-stu-id="d8f15-187">Ranking</span></span>|<xref:Microsoft.ML.RankingCatalog>|
||<span data-ttu-id="d8f15-188">Regresyon</span><span class="sxs-lookup"><span data-stu-id="d8f15-188">Regression</span></span>|<xref:Microsoft.ML.RegressionCatalog>|
||<span data-ttu-id="d8f15-189">Öneri</span><span class="sxs-lookup"><span data-stu-id="d8f15-189">Recommendation</span></span>|<xref:Microsoft.ML.RecommendationCatalog>|
|<span data-ttu-id="d8f15-190">Model kullanımı</span><span class="sxs-lookup"><span data-stu-id="d8f15-190">Model usage</span></span> ||<xref:Microsoft.ML.ModelOperationsCatalog>|

<span data-ttu-id="d8f15-191">Yukarıdaki kategorilerden her biri oluşturma yöntemleri gidebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8f15-191">You can navigate to the creation methods in each of the above categories.</span></span> <span data-ttu-id="d8f15-192">Visual Studio kullanarak, katalogları IntelliSense gösterilir.</span><span class="sxs-lookup"><span data-stu-id="d8f15-192">Using Visual Studio, the catalogs show up via IntelliSense.</span></span>

   ![Regresyon Eğitmenler için IntelliSense](./media/catalog-intellisense.png)

### <a name="build-the-pipeline"></a><span data-ttu-id="d8f15-194">İşlem hattı oluşturma</span><span class="sxs-lookup"><span data-stu-id="d8f15-194">Build the pipeline</span></span>

<span data-ttu-id="d8f15-195">İçinde her kataloğunu genişletme yöntemleri kümesidir.</span><span class="sxs-lookup"><span data-stu-id="d8f15-195">Inside each catalog is a set of extension methods.</span></span> <span data-ttu-id="d8f15-196">Genişletme yöntemleri bir eğitim işlem hattı oluşturmak için nasıl kullanılacağını bakalım.</span><span class="sxs-lookup"><span data-stu-id="d8f15-196">Let's look at how extension methods are used to create a training pipeline.</span></span>

```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
        .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));
```

<span data-ttu-id="d8f15-197">Kod parçacığında `Concatenate` ve `Sdca` katalogdaki her iki yöntemlerdir.</span><span class="sxs-lookup"><span data-stu-id="d8f15-197">In the snippet, `Concatenate` and `Sdca` are both methods in the catalog.</span></span> <span data-ttu-id="d8f15-198">Oluşturdukları her bir [IEstimator](xref:Microsoft.ML.IEstimator%601) ardışık düzenine eklenen nesne.</span><span class="sxs-lookup"><span data-stu-id="d8f15-198">They each create an [IEstimator](xref:Microsoft.ML.IEstimator%601) object that is appended to the pipeline.</span></span>

<span data-ttu-id="d8f15-199">Bu noktada, nesneleri yalnızca oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="d8f15-199">At this point, the objects are created only.</span></span> <span data-ttu-id="d8f15-200">Hiçbir yürütme gerçekleştirilmedi.</span><span class="sxs-lookup"><span data-stu-id="d8f15-200">No execution has happened.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="d8f15-201">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="d8f15-201">Train the model</span></span>

<span data-ttu-id="d8f15-202">İşlem hattı nesneleri için oluşturduktan sonra modeli eğitmek için verilerin kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d8f15-202">Once the objects in the pipeline have been created, data can be used to train the model.</span></span>

```csharp
    var model = pipeline.Fit(trainingData);
```

<span data-ttu-id="d8f15-203">Çağırma `Fit()` parametreleri modelin tahmin etmek için giriş eğitim verileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="d8f15-203">Calling `Fit()` uses the input training data to estimate the parameters of the model.</span></span> <span data-ttu-id="d8f15-204">Bu, modeli eğitmek olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="d8f15-204">This is known as training the model.</span></span> <span data-ttu-id="d8f15-205">Unutmayın, doğrusal regresyon modelinin Yukarıdaki iki modeli parametre vardı: **sapması** ve **ağırlık**.</span><span class="sxs-lookup"><span data-stu-id="d8f15-205">Remember, the linear regression model above had two model parameters: **bias** and **weight**.</span></span> <span data-ttu-id="d8f15-206">Sonra `Fit()` çağrısı, parametre değerlerini bilinir.</span><span class="sxs-lookup"><span data-stu-id="d8f15-206">After the `Fit()` call, the values of the parameters are known.</span></span> <span data-ttu-id="d8f15-207">Çoğu modelleri bundan çok daha fazla parametre gerekir.</span><span class="sxs-lookup"><span data-stu-id="d8f15-207">Most models will have many more parameters than this.</span></span>

<span data-ttu-id="d8f15-208">Model eğitimi hakkında daha fazla bilgi [nasıl modelinizi eğitin](./how-to-guides/train-machine-learning-model-ml-net.md)</span><span class="sxs-lookup"><span data-stu-id="d8f15-208">You can learn more about model training in [How to train your model](./how-to-guides/train-machine-learning-model-ml-net.md)</span></span>

<span data-ttu-id="d8f15-209">Oluşturulan model nesnesi uygulayan <xref:Microsoft.ML.ITransformer> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d8f15-209">The resulting model object implements the <xref:Microsoft.ML.ITransformer> interface.</span></span> <span data-ttu-id="d8f15-210">Diğer bir deyişle, model öngörülere giriş verilerini dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="d8f15-210">That is, the model transforms input data into predictions.</span></span>

```csharp
   IDataView predictions = model.Transform(inputData);
```

### <a name="use-the-model"></a><span data-ttu-id="d8f15-211">Kullanım modeli</span><span class="sxs-lookup"><span data-stu-id="d8f15-211">Use the model</span></span>

<span data-ttu-id="d8f15-212">Giriş verileri aynı anda Öngörüler toplu ya da bir giriş içine dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8f15-212">You can transform input data into predictions in bulk, or one input at a time.</span></span> <span data-ttu-id="d8f15-213">Ev fiyat örnekte, her ikisi de yaptık: model ve yeni bir tahminde bulunmak için birer tane Değerlendirme amacıyla toplu.</span><span class="sxs-lookup"><span data-stu-id="d8f15-213">In the house price example, we did both: in bulk for the purpose of evaluating the model, and one at a time to make a new prediction.</span></span> <span data-ttu-id="d8f15-214">Tek Öngörüler kolaylaştırmayı bakalım.</span><span class="sxs-lookup"><span data-stu-id="d8f15-214">Let's look at making single predictions.</span></span>

```csharp
    var size = new HouseData() { Size = 2.5F };
    var predEngine = model.CreatePredictionEngine<HouseData, Prediction>(mlContext);
    var price = predEngine.Predict(size);
```
 
<span data-ttu-id="d8f15-215">`CreatePredictionEngine()` Yöntemi, bir giriş ve çıkış sınıfı alır.</span><span class="sxs-lookup"><span data-stu-id="d8f15-215">The `CreatePredictionEngine()` method takes an input class and an output class.</span></span> <span data-ttu-id="d8f15-216">Alan adları ve/veya kod öznitelikleri model eğitim ve tahmin sırasında kullanılan veri sütunlarının adlarını belirleyin.</span><span class="sxs-lookup"><span data-stu-id="d8f15-216">The field names and/or code attributes determine the names of the data columns used during model training and prediction.</span></span> <span data-ttu-id="d8f15-217">Okuyabilirsiniz [tek bir tahminde bulunmak nasıl](./how-to-guides/single-predict-model-ml-net.md) bölümünde yapılır.</span><span class="sxs-lookup"><span data-stu-id="d8f15-217">You can read about  [How to make a single prediction](./how-to-guides/single-predict-model-ml-net.md) in the How-to section.</span></span>

### <a name="data-models-and-schema"></a><span data-ttu-id="d8f15-218">Veri modelleri ve şema</span><span class="sxs-lookup"><span data-stu-id="d8f15-218">Data models and schema</span></span>

<span data-ttu-id="d8f15-219">Bir ML.NET makine öğrenimi işlem hattı özünde olan [DataView](xref:Microsoft.ML.IDataView) nesneleri.</span><span class="sxs-lookup"><span data-stu-id="d8f15-219">At the core of an ML.NET machine learning pipeline are [DataView](xref:Microsoft.ML.IDataView) objects.</span></span>

<span data-ttu-id="d8f15-220">İşlem hattındaki her dönüştürme bir giriş şeması (veri adları, türleri ve boyutları dönüştürme hücredeki girişe göre görmek için beklediği); sahip ve bir çıkış şeması (veri adları, türleri ve sonra dönüştürme dönüştürme üreten boyutları).</span><span class="sxs-lookup"><span data-stu-id="d8f15-220">Each transformation in the pipeline has an input schema (data names, types, and sizes that the transform expects to see on its input); and an output schema (data names, types, and sizes that the transform produces after the transformation).</span></span> 

<span data-ttu-id="d8f15-221">ML.NET, işlem hattındaki bir dönüşüm çıkış şemasından sonraki dönüştürme giriş şemasını eşleşmiyorsa bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d8f15-221">If the output schema from one transform in the pipeline doesn't match the input schema of the next transform, ML.NET will throw an exception.</span></span>

<span data-ttu-id="d8f15-222">Veri Görünümü nesnesi satırları ve sütunları vardır.</span><span class="sxs-lookup"><span data-stu-id="d8f15-222">A data view object has columns and rows.</span></span> <span data-ttu-id="d8f15-223">Her sütun bir ad ve bir tür ve bir süre vardır.</span><span class="sxs-lookup"><span data-stu-id="d8f15-223">Each column has a name and a type and a length.</span></span> <span data-ttu-id="d8f15-224">Örneğin: ev fiyat örnekte giriş sütunlar **boyutu** ve **fiyat**.</span><span class="sxs-lookup"><span data-stu-id="d8f15-224">For example: the input columns in the house price example are **Size** and **Price**.</span></span> <span data-ttu-id="d8f15-225">Bunlar olan hem de yazın ve bunlar skaler miktarlarının yerine olanları vektör.</span><span class="sxs-lookup"><span data-stu-id="d8f15-225">They are both type  and they are scalar quantities rather than vector ones.</span></span>

   ![Ev fiyatı tahmin verileriyle ML.NET veri görünümü örneği](./media/ml-net-dataview.png)

<span data-ttu-id="d8f15-227">Tüm ML.NET algoritmalar bir vektördür bir giriş sütun arayın.</span><span class="sxs-lookup"><span data-stu-id="d8f15-227">All ML.NET algorithms look for an input column that is a vector.</span></span> <span data-ttu-id="d8f15-228">Varsayılan olarak bu vektörü sütun çağrılır **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="d8f15-228">By default this vector column is called **Features**.</span></span> <span data-ttu-id="d8f15-229">Biz birleştirilmiş bu yüzden **boyutu** adlı yeni bir sütun sütununa **özellikleri** ev fiyat örneğimizde.</span><span class="sxs-lookup"><span data-stu-id="d8f15-229">This is why we concatenated the **Size** column into a new column called **Features** in our house price example.</span></span>

 ```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
 ```

<span data-ttu-id="d8f15-230">Tahmin gerçekleştirmemiş olan sonra tüm algoritmaları da yeni bir sütun oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d8f15-230">All algorithms also create new columns after they have performed a prediction.</span></span> <span data-ttu-id="d8f15-231">Bu yeni sütunların sabit adları, makine öğrenme algoritmasına türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d8f15-231">The fixed names of these new columns depend on the type of machine learning algorithm.</span></span> <span data-ttu-id="d8f15-232">Regresyon görev için yeni sütunlar birini çağrılır **puanı**.</span><span class="sxs-lookup"><span data-stu-id="d8f15-232">For the regression task, one of the new columns is called **Score**.</span></span> <span data-ttu-id="d8f15-233">Biz bu ada sahip fiyat verilerimizi öznitelikli nedeni budur.</span><span class="sxs-lookup"><span data-stu-id="d8f15-233">This is why we attributed our price data with this name.</span></span>

```csharp
    public class Prediction
    {
        [ColumnName("Score")]
        public float Price { get; set; }
    }
```    

<span data-ttu-id="d8f15-234">Çıkış sütunları farklı makine öğrenimi görevleri hakkında daha fazla bilgi bulabilirsiniz [makine öğrenimi görevlerini](resources/tasks.md) Kılavuzu.</span><span class="sxs-lookup"><span data-stu-id="d8f15-234">You can find out more about output columns of different machine learning tasks in the [Machine Learning Tasks](resources/tasks.md) guide.</span></span>

<span data-ttu-id="d8f15-235">DataView önemli bir özelliği nesnelerindeki değerlendirilme **gevşek**.</span><span class="sxs-lookup"><span data-stu-id="d8f15-235">An important property of DataView objects is that they are evaluated **lazily**.</span></span> <span data-ttu-id="d8f15-236">Veri görünümleri yalnızca yüklenir ve üzerinde model eğitim ve değerlendirme ve veri tahmin sırasında işletilir.</span><span class="sxs-lookup"><span data-stu-id="d8f15-236">Data views are only loaded and operated on during model training and evaluation, and data prediction.</span></span> <span data-ttu-id="d8f15-237">Yazma ve ML.NET uygulamanızı test ederken, Visual Studio hata ayıklayıcısını çağırarak herhangi bir veri görünümü nesne göz atalım için kullanabileceğiniz [Önizleme](xref:Microsoft.ML.DebuggerExtensions.Preview*) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d8f15-237">While you are writing and testing your ML.NET application, you can use the Visual Studio debugger to take a peek at any data view object by calling the [Preview](xref:Microsoft.ML.DebuggerExtensions.Preview*) method.</span></span>

```csharp
    var debug = testPriceDataView.Preview();
```

<span data-ttu-id="d8f15-238">İzleyebilir `debug` hata ayıklayıcı değişken ve içeriğini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="d8f15-238">You can watch the `debug` variable in the debugger and examine its contents.</span></span> <span data-ttu-id="d8f15-239">Önemli ölçüde performansı düşürür gibi üretim kodunda Önizleme yöntemi kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="d8f15-239">Do not use the Preview method in production code, as it significantly degrades performance.</span></span>

### <a name="model-deployment"></a><span data-ttu-id="d8f15-240">Model dağıtımı</span><span class="sxs-lookup"><span data-stu-id="d8f15-240">Model Deployment</span></span>

<span data-ttu-id="d8f15-241">Gerçek zamanlı konuşmaların uygulamalarda, model eğitimi ve değerlendirmesi kodunuzu tahmininizde ayrı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d8f15-241">In real-life applications, your model training and evaluation code will be separate from your prediction.</span></span> <span data-ttu-id="d8f15-242">Aslında, bu iki etkinliği genellikle ayrı takımlar tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d8f15-242">In fact, these two activities are often performed by separate teams.</span></span> <span data-ttu-id="d8f15-243">Model Geliştirme ekibiniz, tahmin uygulama modelini kullanmak için kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8f15-243">Your model development team can save the model for use in the prediction application.</span></span>

```csharp   
   mlContext.Model.Save(model, trainingData.Schema,"model.zip");
```

## <a name="where-to-now"></a><span data-ttu-id="d8f15-244">Şimdi nereye?</span><span class="sxs-lookup"><span data-stu-id="d8f15-244">Where to now?</span></span>

<span data-ttu-id="d8f15-245">Daha gerçekçi veri kümelerinde farklı makine öğrenimi görevlerini kullanarak uygulamaları nasıl oluşturabileceğinizi öğrenebilirsiniz [öğreticiler](./tutorials/index.md).</span><span class="sxs-lookup"><span data-stu-id="d8f15-245">You can learn how to build applications using different machine learning tasks with more realistic data sets in the [tutorials](./tutorials/index.md).</span></span>

<span data-ttu-id="d8f15-246">Veya belirli konuları bölümünde daha ayrıntılı olarak hakkında bilgi edinebilirsiniz [nasıl yapılır kılavuzları](./how-to-guides/index.md).</span><span class="sxs-lookup"><span data-stu-id="d8f15-246">Or you can learn about specific topics in more depth in the [How To Guides](./how-to-guides/index.md).</span></span>

<span data-ttu-id="d8f15-247">Ve Süper içeriğimizi, düz içine başlayabilirsiniz [API başvuru belgeleri](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet)!</span><span class="sxs-lookup"><span data-stu-id="d8f15-247">And if you're super keen, you can dive straight into the [API Reference documentation](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet)!</span></span>
