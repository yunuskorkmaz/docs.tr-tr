---
title: ML.NET nedir ve nasıl çalışır?
description: ML.NET, .NET uygulamalarına çevrimiçi veya çevrimdışı senaryolarda makine öğrenimi ekleme olanağı sağlar. Bu özellik sayesinde, ML.NET kullanmak üzere bir ağa bağlanmak zorunda kalmadan uygulamanızın kullanabileceği verileri kullanarak otomatik öngörüler yapabilirsiniz. Bu makalede, ML.NET makine öğreniminin temelleri açıklanmaktadır.
ms.date: 11/5/2019
ms.topic: overview
ms.custom: mvc
ms.openlocfilehash: 169250adf81992ad0025e78eb9c8f151107bcf40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185863"
---
# <a name="what-is-mlnet-and-how-does-it-work"></a><span data-ttu-id="1e5c0-105">ML.NET nedir ve nasıl çalışır?</span><span class="sxs-lookup"><span data-stu-id="1e5c0-105">What is ML.NET and how does it work?</span></span>

<span data-ttu-id="1e5c0-106">ML.NET, .NET uygulamalarına çevrimiçi veya çevrimdışı senaryolarda makine öğrenimi ekleme olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-106">ML.NET gives you the ability to add machine learning to .NET applications, in either online or offline scenarios.</span></span> <span data-ttu-id="1e5c0-107">Bu özellik sayesinde, uygulamanızın kullanabileceği verileri kullanarak otomatik öngörüler yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-107">With this capability, you can make automatic predictions using the data available to your application.</span></span> <span data-ttu-id="1e5c0-108">Makine öğrenimi uygulamaları, açıkça programlanması yerine öngörülerde bulunmak için verilerdeki desenlerden yararlanAr.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-108">Machine learning applications make use of patterns in the data to make predictions rather than needing to be explicitly programmed.</span></span>

<span data-ttu-id="1e5c0-109">Merkezi ML.NET bir makine öğrenme **modelidir.**</span><span class="sxs-lookup"><span data-stu-id="1e5c0-109">Central to ML.NET is a machine learning **model**.</span></span> <span data-ttu-id="1e5c0-110">Model, giriş verilerinizi bir tahmine dönüştürmek için gereken adımları belirtir.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-110">The model specifies the steps needed to transform your input data into a prediction.</span></span> <span data-ttu-id="1e5c0-111">ML.NET ile, bir algoritma belirterek özel bir modeli eğitebilir veya önceden eğitilmiş TensorFlow ve ONNX modellerini içe aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-111">With ML.NET, you can train a custom model by specifying an algorithm, or you can import pre-trained TensorFlow and ONNX models.</span></span>

<span data-ttu-id="1e5c0-112">Bir modele sahip olduktan sonra, tahminleri yapmak için uygulamanıza ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-112">Once you have a model, you can add it to your application to make the predictions.</span></span>

<span data-ttu-id="1e5c0-113">ML.NET .NET Core veya Windows kullanarak .NET Framework kullanarak Windows, Linux ve macOS'ta çalışır.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-113">ML.NET runs on Windows, Linux, and macOS using .NET Core, or Windows using .NET Framework.</span></span> <span data-ttu-id="1e5c0-114">64 bit tüm platformlarda desteklenir.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-114">64 bit is supported on all platforms.</span></span> <span data-ttu-id="1e5c0-115">TensorFlow, LightGBM ve ONNX ile ilgili işlevler dışında Windows'da 32 bit desteklenir.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-115">32 bit is supported on Windows, except for TensorFlow, LightGBM, and ONNX-related functionality.</span></span>

<span data-ttu-id="1e5c0-116">ML.NET ile yapabileceğiniz tahmin türüne örnekler:</span><span class="sxs-lookup"><span data-stu-id="1e5c0-116">Examples of the type of predictions that you can make with ML.NET:</span></span>

|||
|-|-|
|<span data-ttu-id="1e5c0-117">Sınıflandırma/Kategorizasyon</span><span class="sxs-lookup"><span data-stu-id="1e5c0-117">Classification/Categorization</span></span>|<span data-ttu-id="1e5c0-118">Müşteri geri bildirimlerini otomatik olarak pozitif ve negatif kategorilere ayırın</span><span class="sxs-lookup"><span data-stu-id="1e5c0-118">Automatically divide customer feedback into positive and negative categories</span></span>|
|<span data-ttu-id="1e5c0-119">Regresyon/Sürekli değerleri tahmin etme</span><span class="sxs-lookup"><span data-stu-id="1e5c0-119">Regression/Predict continuous values</span></span>|<span data-ttu-id="1e5c0-120">Büyüklük ve konuma göre evlerin fiyatını tahmin edin</span><span class="sxs-lookup"><span data-stu-id="1e5c0-120">Predict the price of houses based on size and location</span></span>|
|<span data-ttu-id="1e5c0-121">Anomali Algılama</span><span class="sxs-lookup"><span data-stu-id="1e5c0-121">Anomaly Detection</span></span>|<span data-ttu-id="1e5c0-122">Sahte bankacılık işlemlerini algılama</span><span class="sxs-lookup"><span data-stu-id="1e5c0-122">Detect fraudulent banking transactions</span></span> |
|<span data-ttu-id="1e5c0-123">Öneriler</span><span class="sxs-lookup"><span data-stu-id="1e5c0-123">Recommendations</span></span>|<span data-ttu-id="1e5c0-124">Çevrimiçi alışverişyapanların önceki satın alma işlemlerini temel alan satın almak isteyebileceği ürünler önerme</span><span class="sxs-lookup"><span data-stu-id="1e5c0-124">Suggest products that online shoppers may want to buy, based on their previous purchases</span></span>|
|<span data-ttu-id="1e5c0-125">Zaman serisi/sıralı veriler</span><span class="sxs-lookup"><span data-stu-id="1e5c0-125">Time series/sequential data</span></span>|<span data-ttu-id="1e5c0-126">Hava durumu/ürün satışlarını tahmin edin</span><span class="sxs-lookup"><span data-stu-id="1e5c0-126">Forecast the weather/product sales</span></span>|
|<span data-ttu-id="1e5c0-127">Resimleri sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="1e5c0-127">Image classification</span></span>|<span data-ttu-id="1e5c0-128">Tıbbi görüntülerdeki patolojileri kategorilere ayırın</span><span class="sxs-lookup"><span data-stu-id="1e5c0-128">Categorize pathologies in medical images</span></span>|

## <a name="hello-mlnet-world"></a><span data-ttu-id="1e5c0-129">Merhaba ML.NET Dünya</span><span class="sxs-lookup"><span data-stu-id="1e5c0-129">Hello ML.NET World</span></span>

<span data-ttu-id="1e5c0-130">Aşağıdaki snippet kodu en basit ML.NET uygulama gösterir.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-130">The code in the following snippet demonstrates the simplest ML.NET application.</span></span> <span data-ttu-id="1e5c0-131">Bu örnek, ev büyüklüğü ve fiyat verilerini kullanarak ev fiyatlarını tahmin etmek için doğrusal bir regresyon modeli oluşturuyor.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-131">This example constructs a linear regression model to predict house prices using house size and price data.</span></span>

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

## <a name="code-workflow"></a><span data-ttu-id="1e5c0-132">Kod iş akışı</span><span class="sxs-lookup"><span data-stu-id="1e5c0-132">Code workflow</span></span>

<span data-ttu-id="1e5c0-133">Aşağıdaki diyagram, uygulama kodu yapısını ve model geliştirme işlemini temsil eder:</span><span class="sxs-lookup"><span data-stu-id="1e5c0-133">The following diagram represents the application code structure, as well as the iterative process of model development:</span></span>

- <span data-ttu-id="1e5c0-134">Eğitim verilerini bir **IDataView** nesnesine toplama ve yükleme</span><span class="sxs-lookup"><span data-stu-id="1e5c0-134">Collect and load training data into an **IDataView** object</span></span>
- <span data-ttu-id="1e5c0-135">Özellikleri ayıklamak ve makine öğrenimi algoritması uygulamak için bir işlem ardışık hattı belirtin</span><span class="sxs-lookup"><span data-stu-id="1e5c0-135">Specify a pipeline of operations to extract features and apply a machine learning algorithm</span></span>
- <span data-ttu-id="1e5c0-136">Boru hattında **Fit()** numaralı telefonu arayarak bir model eğitin</span><span class="sxs-lookup"><span data-stu-id="1e5c0-136">Train a model by calling **Fit()** on the pipeline</span></span>
- <span data-ttu-id="1e5c0-137">Modeli değerlendirin ve geliştirmek için yineleyin</span><span class="sxs-lookup"><span data-stu-id="1e5c0-137">Evaluate the model and iterate to improve</span></span>
- <span data-ttu-id="1e5c0-138">Bir uygulamada kullanılmak üzere modeli ikili biçime kaydetme</span><span class="sxs-lookup"><span data-stu-id="1e5c0-138">Save the model into binary format, for use in an application</span></span>
- <span data-ttu-id="1e5c0-139">Modeli bir **ITransformer** nesnesine geri yükleme</span><span class="sxs-lookup"><span data-stu-id="1e5c0-139">Load the model back into an **ITransformer** object</span></span>
- <span data-ttu-id="1e5c0-140">**CreatePredictionEngine.Predict()** numaralı telefonu arayarak öngörülerde bulunun</span><span class="sxs-lookup"><span data-stu-id="1e5c0-140">Make predictions by calling **CreatePredictionEngine.Predict()**</span></span>

![veri üretimi, boru hattı geliştirme, model eğitimi, model değerlendirmesi ve model kullanımı için bileşenler de dahil olmak üzere ML.NET uygulama geliştirme akışı](./media/mldotnet-annotated-workflow.png)

<span data-ttu-id="1e5c0-142">Bu kavramları biraz daha derinlemesine araştıralım.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-142">Let's dig a little deeper into those concepts.</span></span>

## <a name="machine-learning-model"></a><span data-ttu-id="1e5c0-143">Makine öğrenimi modeli</span><span class="sxs-lookup"><span data-stu-id="1e5c0-143">Machine learning model</span></span>

<span data-ttu-id="1e5c0-144">ML.NET modeli, tahmin edilen çıktıya ulaşmak için giriş verilerinizde gerçekleştirmek için dönüşümler içeren bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-144">An ML.NET model is an object that contains transformations to perform on your input data to arrive at the predicted output.</span></span>

### <a name="basic"></a><span data-ttu-id="1e5c0-145">Temel</span><span class="sxs-lookup"><span data-stu-id="1e5c0-145">Basic</span></span>

<span data-ttu-id="1e5c0-146">En temel model iki boyutlu doğrusal regresyon, bir sürekli miktar başka bir orantılı olduğu, yukarıdaki ev fiyat örneği gibi.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-146">The most basic model is two-dimensional linear regression, where one continuous quantity is proportional to another, as in the house price example above.</span></span>

![Yanlı ve ağırlık parametrelerli Lineer Regresyon Modeli](./media/linear-regression-model.svg)

<span data-ttu-id="1e5c0-148">Model basitçe: $Price = b + Boyut \* w$.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-148">The model is simply: $Price = b + Size \* w$.</span></span> <span data-ttu-id="1e5c0-149">$b$ ve $w$ parametreleri, bir dizi (boyut, fiyat) çifte bir satır takılarak tahmin edilir.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-149">The parameters $b$ and $w$ are estimated by fitting a line on a set of (size, price) pairs.</span></span> <span data-ttu-id="1e5c0-150">Modelin parametrelerini bulmak için kullanılan **verilere eğitim verileri**denir.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-150">The data used to find the parameters of the model is called **training data**.</span></span> <span data-ttu-id="1e5c0-151">Bir makine öğrenme modelinin girdileri **özellikleri**denir.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-151">The inputs of a machine learning model are called **features**.</span></span> <span data-ttu-id="1e5c0-152">Bu örnekte, $Size$ tek özelliktir.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-152">In this example, $Size$ is the only feature.</span></span> <span data-ttu-id="1e5c0-153">Bir makine öğrenme modelini eğitmek için kullanılan zemin-gerçeğdeğerlerine **etiketler**denir.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-153">The ground-truth values used to train a machine learning model are called **labels**.</span></span> <span data-ttu-id="1e5c0-154">Burada, eğitim veri kümesindeki $Price$ değerleri etiketlerdir.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-154">Here, the $Price$ values in the training data set are the labels.</span></span>

### <a name="more-complex"></a><span data-ttu-id="1e5c0-155">Daha karmaşık</span><span class="sxs-lookup"><span data-stu-id="1e5c0-155">More complex</span></span>

<span data-ttu-id="1e5c0-156">Daha karmaşık bir model, hareket metni açıklamasını kullanarak mali hareketleri kategorilere ayırır.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-156">A more complex model classifies financial transactions into categories using the transaction text description.</span></span>

<span data-ttu-id="1e5c0-157">Her işlem açıklaması, gereksiz sözcükleri ve karakterleri kaldırarak ve sözcük ve karakter birleşimlerini sayarak bir dizi özelliğe ayrılır.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-157">Each transaction description is broken down into a set of features by removing redundant words and characters, and counting word and character combinations.</span></span> <span data-ttu-id="1e5c0-158">Özellik kümesi, eğitim verilerindeki kategoriler kümesine dayalı doğrusal bir model eğitmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-158">The feature set is used to train a linear model based on the set of categories in the training data.</span></span> <span data-ttu-id="1e5c0-159">Yeni bir açıklama, eğitim kümesindekilere ne kadar benzerse, aynı kategoriye atanmanın olasılığı da o kadar yüksek tir.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-159">The more similar a new description is to the ones in the training set, the more likely it will be assigned to the same category.</span></span>

![Metin Sınıflandırma Modeli](./media/text-classification-model.svg)

<span data-ttu-id="1e5c0-161">Hem ev fiyat modeli hem de metin sınıflandırma modeli **doğrusal** modellerdir.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-161">Both the house price model and the text classification model are **linear** models.</span></span> <span data-ttu-id="1e5c0-162">Verilerinizin yapısına ve çözdüğünüz soruna bağlı olarak, **karar ağacı** modellerini, **genelleştirilmiş katkı maddesi modellerini** ve diğerlerini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-162">Depending on the nature of your data and the problem you are solving, you can also use **decision tree** models, **generalized additive** models, and others.</span></span> <span data-ttu-id="1e5c0-163">[Görevler'deki](./resources/tasks.md)modeller hakkında daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-163">You can find out more about the models in [Tasks](./resources/tasks.md).</span></span>

## <a name="data-preparation"></a><span data-ttu-id="1e5c0-164">Veri hazırlama</span><span class="sxs-lookup"><span data-stu-id="1e5c0-164">Data preparation</span></span>

<span data-ttu-id="1e5c0-165">Çoğu durumda, mevcut veriler doğrudan bir makine öğrenme modeli eğitmek için kullanılmak üzere uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-165">In most cases, the data that you have available isn't suitable to be used directly to train a machine learning model.</span></span> <span data-ttu-id="1e5c0-166">Modelinizin parametrelerini bulmak için kullanılabilmesi için ham verilerin hazırlanması veya önceden işlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-166">The raw data needs to be prepared, or pre-processed, before it can be used to find the parameters of your model.</span></span> <span data-ttu-id="1e5c0-167">Verilerinizin dize değerlerinden sayısal gösterime dönüştürülmesi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-167">Your data may need to be converted from string values to a numerical representation.</span></span> <span data-ttu-id="1e5c0-168">Giriş verilerinizde gereksiz bilgiler olabilir.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-168">You might have redundant information in your input data.</span></span> <span data-ttu-id="1e5c0-169">Giriş verilerinizin boyutlarını azaltmanız veya genişletmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-169">You may need to reduce or expand the dimensions of your input data.</span></span> <span data-ttu-id="1e5c0-170">Verilerinizin normalleştirilmesi veya ölçeklendirilmesi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-170">Your data might need to be normalized or scaled.</span></span>

<span data-ttu-id="1e5c0-171">[ML.NET öğreticiler,](./tutorials/index.md) belirli makine öğrenimi görevleri için kullanılan metin, resim, sayısal ve zaman serisi verileri için farklı veri işleme ardışık lıkları hakkında bilgi verir.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-171">The [ML.NET tutorials](./tutorials/index.md) teach you about different data processing pipelines for text, image, numerical, and time-series data used for specific machine learning tasks.</span></span>

<span data-ttu-id="1e5c0-172">[Verilerinizin nasıl hazırlanacağı,](./how-to-guides/prepare-data-ml-net.md) veri hazırlamayı nasıl daha genel olarak uygulayacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-172">[How to prepare your data](./how-to-guides/prepare-data-ml-net.md) shows you how to apply data preparation more generally.</span></span>

<span data-ttu-id="1e5c0-173">Kaynaklar bölümünde mevcut tüm [dönüşümlerin](./resources/transforms.md) bir ekini bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-173">You can find an appendix of all of the [available transformations](./resources/transforms.md) in the resources section.</span></span>

## <a name="model-evaluation"></a><span data-ttu-id="1e5c0-174">Model değerlendirmesi</span><span class="sxs-lookup"><span data-stu-id="1e5c0-174">Model evaluation</span></span>

<span data-ttu-id="1e5c0-175">Modelinizi eğittikten sonra, bunun gelecekteki tahminleri ne kadar iyi yapacağını nasıl biliyorsunuz?</span><span class="sxs-lookup"><span data-stu-id="1e5c0-175">Once you have trained your model, how do you know how well it will make future predictions?</span></span> <span data-ttu-id="1e5c0-176">ML.NET ile, modelinizi bazı yeni test verilerine göre değerlendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-176">With ML.NET, you can evaluate your model against some new test data.</span></span>

<span data-ttu-id="1e5c0-177">Her tür makine öğrenimi görevi, test veri kümesine karşı modelin doğruluğunu ve hassasiyetini değerlendirmek için kullanılan ölçümlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-177">Each type of machine learning task has metrics used to evaluate the accuracy and precision of the model against the test data set.</span></span>

<span data-ttu-id="1e5c0-178">Bizim ev fiyat örneği için, biz **Regresyon** görevi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-178">For our house price example, we used the **Regression** task.</span></span> <span data-ttu-id="1e5c0-179">Modeli değerlendirmek için özgün örneğe aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-179">To evaluate the model, add the following code to the original sample.</span></span>

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

<span data-ttu-id="1e5c0-180">Değerlendirme ölçümleri, hatanın düşük olduğunu ve öngörülen çıktı ile test çıktısı arasındaki korelasyonun yüksek olduğunu söyler.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-180">The evaluation metrics tell you that the error is low-ish, and that correlation between the predicted output and the test output is high.</span></span> <span data-ttu-id="1e5c0-181">Çok kolaydı!</span><span class="sxs-lookup"><span data-stu-id="1e5c0-181">That was easy!</span></span> <span data-ttu-id="1e5c0-182">Gerçek örneklerde, iyi model ölçümleri elde etmek için daha fazla atokalma alır.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-182">In real examples, it takes more tuning to achieve good model metrics.</span></span>

## <a name="mlnet-architecture"></a><span data-ttu-id="1e5c0-183">ML.NET mimarisi</span><span class="sxs-lookup"><span data-stu-id="1e5c0-183">ML.NET architecture</span></span>

<span data-ttu-id="1e5c0-184">Bu bölümde ML.NET mimari desenleri üzerinden geçeceğiz.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-184">In this section, we go through the architectural patterns of ML.NET.</span></span> <span data-ttu-id="1e5c0-185">Deneyimli bir .NET geliştiricisiyseniz, bu desenlerden bazıları size tanıdık gelecektir ve bazıları daha az tanıdık olacaktır.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-185">If you are an experienced .NET developer, some of these patterns will be familiar to you, and some will be less familiar.</span></span> <span data-ttu-id="1e5c0-186">Biz dalırken sıkıca tutun!</span><span class="sxs-lookup"><span data-stu-id="1e5c0-186">Hold tight, while we dive in!</span></span>

<span data-ttu-id="1e5c0-187">ML.NET uygulaması bir <xref:Microsoft.ML.MLContext> nesneyle başlar.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-187">An ML.NET application starts with an <xref:Microsoft.ML.MLContext> object.</span></span> <span data-ttu-id="1e5c0-188">Bu singleton nesne **katalogları**içerir.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-188">This singleton object contains **catalogs**.</span></span> <span data-ttu-id="1e5c0-189">Katalog, veri yükleme ve kaydetme, dönüşümler, eğitmenler ve model işletim bileşenleri için bir fabrikadır.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-189">A catalog is a factory for data loading and saving, transforms, trainers, and model operation components.</span></span> <span data-ttu-id="1e5c0-190">Her katalog nesnesinin farklı bileşen türlerini oluşturmak için yöntemleri vardır:</span><span class="sxs-lookup"><span data-stu-id="1e5c0-190">Each catalog object has methods to create the different types of components:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="1e5c0-191">Veri yükleme ve kaydetme</span><span class="sxs-lookup"><span data-stu-id="1e5c0-191">Data loading and saving</span></span>||<xref:Microsoft.ML.DataOperationsCatalog>||
|<span data-ttu-id="1e5c0-192">Veri hazırlama</span><span class="sxs-lookup"><span data-stu-id="1e5c0-192">Data preparation</span></span>||<xref:Microsoft.ML.TransformsCatalog>||
|<span data-ttu-id="1e5c0-193">Eğitim algoritmaları</span><span class="sxs-lookup"><span data-stu-id="1e5c0-193">Training algorithms</span></span>|<span data-ttu-id="1e5c0-194">İkili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="1e5c0-194">Binary classification</span></span>|<xref:Microsoft.ML.BinaryClassificationCatalog>||
||<span data-ttu-id="1e5c0-195">Çok sınıflı sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="1e5c0-195">Multiclass classification</span></span>|<xref:Microsoft.ML.MulticlassClassificationCatalog>||
||<span data-ttu-id="1e5c0-196">Anormallik algılama</span><span class="sxs-lookup"><span data-stu-id="1e5c0-196">Anomaly detection</span></span>|<xref:Microsoft.ML.AnomalyDetectionCatalog>||
||<span data-ttu-id="1e5c0-197">Kümeleme</span><span class="sxs-lookup"><span data-stu-id="1e5c0-197">Clustering</span></span>|<xref:Microsoft.ML.ClusteringCatalog>||
||<span data-ttu-id="1e5c0-198">Tahmin etme</span><span class="sxs-lookup"><span data-stu-id="1e5c0-198">Forecasting</span></span>|<xref:Microsoft.ML.ForecastingCatalog>||
||<span data-ttu-id="1e5c0-199">Sıralama</span><span class="sxs-lookup"><span data-stu-id="1e5c0-199">Ranking</span></span>|<xref:Microsoft.ML.RankingCatalog>||
||<span data-ttu-id="1e5c0-200">Regresyon</span><span class="sxs-lookup"><span data-stu-id="1e5c0-200">Regression</span></span>|<xref:Microsoft.ML.RegressionCatalog>||
||<span data-ttu-id="1e5c0-201">Öneri</span><span class="sxs-lookup"><span data-stu-id="1e5c0-201">Recommendation</span></span>|<xref:Microsoft.ML.RecommendationCatalog>|<span data-ttu-id="1e5c0-202">NuGet `Microsoft.ML.Recommender` paketini ekleyin</span><span class="sxs-lookup"><span data-stu-id="1e5c0-202">add the `Microsoft.ML.Recommender` NuGet package</span></span>|
||<span data-ttu-id="1e5c0-203">Zaman Serisi</span><span class="sxs-lookup"><span data-stu-id="1e5c0-203">TimeSeries</span></span>|<xref:Microsoft.ML.TimeSeriesCatalog>|<span data-ttu-id="1e5c0-204">NuGet `Microsoft.ML.TimeSeries` paketini ekleyin</span><span class="sxs-lookup"><span data-stu-id="1e5c0-204">add the `Microsoft.ML.TimeSeries` NuGet package</span></span>|
|<span data-ttu-id="1e5c0-205">Model kullanımı</span><span class="sxs-lookup"><span data-stu-id="1e5c0-205">Model usage</span></span> ||<xref:Microsoft.ML.ModelOperationsCatalog>||

<span data-ttu-id="1e5c0-206">Yukarıdaki kategorilerin her birinde oluşturma yöntemlerine gidebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-206">You can navigate to the creation methods in each of the above categories.</span></span> <span data-ttu-id="1e5c0-207">Visual Studio'yu kullanarak kataloglar IntelliSense üzerinden ortaya çıkar.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-207">Using Visual Studio, the catalogs show up via IntelliSense.</span></span>

   ![Regresyon Eğitmenler için Intellisense](./media/catalog-intellisense.png)

### <a name="build-the-pipeline"></a><span data-ttu-id="1e5c0-209">Boru hattını oluşturun</span><span class="sxs-lookup"><span data-stu-id="1e5c0-209">Build the pipeline</span></span>

<span data-ttu-id="1e5c0-210">Her kataloğun içinde bir dizi uzatma yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-210">Inside each catalog is a set of extension methods.</span></span> <span data-ttu-id="1e5c0-211">Bir eğitim boru hattı oluşturmak için uzantı yöntemlerinin nasıl kullanıldığına bakalım.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-211">Let's look at how extension methods are used to create a training pipeline.</span></span>

```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
        .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));
```

<span data-ttu-id="1e5c0-212">Snippet ve `Concatenate` `Sdca` katalogda her iki yöntem vardır.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-212">In the snippet, `Concatenate` and `Sdca` are both methods in the catalog.</span></span> <span data-ttu-id="1e5c0-213">Her biri, ardışık almaya eklenen bir [IEstimator](xref:Microsoft.ML.IEstimator%601) nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-213">They each create an [IEstimator](xref:Microsoft.ML.IEstimator%601) object that is appended to the pipeline.</span></span>

<span data-ttu-id="1e5c0-214">Bu noktada, nesneler yalnızca oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-214">At this point, the objects are created only.</span></span> <span data-ttu-id="1e5c0-215">İdam gerçekleşmemiş.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-215">No execution has happened.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="1e5c0-216">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="1e5c0-216">Train the model</span></span>

<span data-ttu-id="1e5c0-217">Ardışık ardışık ardışık nesneler oluşturulduktan sonra, verileri modeli eğitmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-217">Once the objects in the pipeline have been created, data can be used to train the model.</span></span>

```csharp
    var model = pipeline.Fit(trainingData);
```

<span data-ttu-id="1e5c0-218">Arama, `Fit()` modelin parametrelerini tahmin etmek için giriş eğitim verilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-218">Calling `Fit()` uses the input training data to estimate the parameters of the model.</span></span> <span data-ttu-id="1e5c0-219">Bu modeli eğitim olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-219">This is known as training the model.</span></span> <span data-ttu-id="1e5c0-220">Unutmayın, yukarıdaki doğrusal regresyon modeliiki model parametreleri vardı: **önyargı** ve **ağırlık**.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-220">Remember, the linear regression model above had two model parameters: **bias** and **weight**.</span></span> <span data-ttu-id="1e5c0-221">`Fit()` Aramadan sonra parametrelerin değerleri bilinir.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-221">After the `Fit()` call, the values of the parameters are known.</span></span> <span data-ttu-id="1e5c0-222">Çoğu model bundan çok daha fazla parametreye sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-222">Most models will have many more parameters than this.</span></span>

<span data-ttu-id="1e5c0-223">[Modelinizi nasıl eğitebileceğiniz](./how-to-guides/train-machine-learning-model-ml-net.md)konusunda model eğitimi hakkında daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-223">You can learn more about model training in [How to train your model](./how-to-guides/train-machine-learning-model-ml-net.md).</span></span>

<span data-ttu-id="1e5c0-224">Ortaya çıkan model nesnesi <xref:Microsoft.ML.ITransformer> arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-224">The resulting model object implements the <xref:Microsoft.ML.ITransformer> interface.</span></span> <span data-ttu-id="1e5c0-225">Diğer bir deyişle, model giriş verilerini öngörülere dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-225">That is, the model transforms input data into predictions.</span></span>

```csharp
   IDataView predictions = model.Transform(inputData);
```

### <a name="use-the-model"></a><span data-ttu-id="1e5c0-226">Modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="1e5c0-226">Use the model</span></span>

<span data-ttu-id="1e5c0-227">Giriş verilerini toplu olarak tahminlere veya aynı anda bir girişe dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-227">You can transform input data into predictions in bulk, or one input at a time.</span></span> <span data-ttu-id="1e5c0-228">Ev fiyat örneğinde, biz her ikisini de yaptı: model değerlendirmek amacıyla toplu olarak, ve birseferde yeni bir tahmin yapmak için.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-228">In the house price example, we did both: in bulk for the purpose of evaluating the model, and one at a time to make a new prediction.</span></span> <span data-ttu-id="1e5c0-229">Tek tahminlerde bulunalım.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-229">Let's look at making single predictions.</span></span>

```csharp
    var size = new HouseData() { Size = 2.5F };
    var predEngine = mlContext.CreatePredictionEngine<HouseData, Prediction>(model);
    var price = predEngine.Predict(size);
```

<span data-ttu-id="1e5c0-230">Yöntem `CreatePredictionEngine()` bir giriş sınıfı ve bir çıktı sınıfı alır.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-230">The `CreatePredictionEngine()` method takes an input class and an output class.</span></span> <span data-ttu-id="1e5c0-231">Alan adları ve/veya kod öznitelikleri, model eğitimi ve tahmini sırasında kullanılan veri sütunlarının adlarını belirler.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-231">The field names and/or code attributes determine the names of the data columns used during model training and prediction.</span></span> <span data-ttu-id="1e5c0-232">Nasıl Yapılır bölümünde [tek bir tahmin nasıl yapılır](./how-to-guides/single-predict-model-ml-net.md) hakkında bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-232">You can read about  [How to make a single prediction](./how-to-guides/single-predict-model-ml-net.md) in the How-to section.</span></span>

### <a name="data-models-and-schema"></a><span data-ttu-id="1e5c0-233">Veri modelleri ve şema</span><span class="sxs-lookup"><span data-stu-id="1e5c0-233">Data models and schema</span></span>

<span data-ttu-id="1e5c0-234">Bir ML.NET makine öğrenme boru hattının özünde [DataView](xref:Microsoft.ML.IDataView) nesneleri vardır.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-234">At the core of an ML.NET machine learning pipeline are [DataView](xref:Microsoft.ML.IDataView) objects.</span></span>

<span data-ttu-id="1e5c0-235">Ardışık ardışık yoldaki her dönüşümün bir girdi şeması vardır (dönüşümün girdisinde görmeyi beklediği veri adları, türleri ve boyutları); ve bir çıktı şeması (dönüşümün dönüşümden sonra ürettiği veri adları, türleri ve boyutları).</span><span class="sxs-lookup"><span data-stu-id="1e5c0-235">Each transformation in the pipeline has an input schema (data names, types, and sizes that the transform expects to see on its input); and an output schema (data names, types, and sizes that the transform produces after the transformation).</span></span> <span data-ttu-id="1e5c0-236">Aşağıdaki [belge, IDataView arabiriminin ve tür sisteminin](https://xadupre.github.io/machinelearningext/mlnetdocs/idataviewtypesystem.html)ayrıntılı bir açıklamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-236">The following document provides an in-depth explanation of the [IDataView interface and its type system](https://xadupre.github.io/machinelearningext/mlnetdocs/idataviewtypesystem.html).</span></span>

<span data-ttu-id="1e5c0-237">Ardışık ardışık bir dönüşümden çıkış şeması bir sonraki dönüşümün giriş şemasıyla eşleşmiyorsa, ML.NET bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-237">If the output schema from one transform in the pipeline doesn't match the input schema of the next transform, ML.NET will throw an exception.</span></span>

<span data-ttu-id="1e5c0-238">Veri görünümü nesnesi sütunları ve satırları vardır.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-238">A data view object has columns and rows.</span></span> <span data-ttu-id="1e5c0-239">Her sütunun bir adı, bir türü ve uzunluğu vardır.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-239">Each column has a name and a type and a length.</span></span> <span data-ttu-id="1e5c0-240">Örneğin, ev fiyat örneğindeki giriş sütunları **Boyut** ve **Fiyat'dır.**</span><span class="sxs-lookup"><span data-stu-id="1e5c0-240">For example, the input columns in the house price example are **Size** and **Price**.</span></span> <span data-ttu-id="1e5c0-241">Her ikisi de tür ve vektör olanlar yerine skaler miktarları vardır.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-241">They are both type and they are scalar quantities rather than vector ones.</span></span>

   ![ev fiyat tahmini verileri ile ML.NET Veri Görünümü örneği](./media/ml-net-dataview.png)

<span data-ttu-id="1e5c0-243">Tüm ML.NET algoritmaları bir vektör olan bir giriş sütunu arar.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-243">All ML.NET algorithms look for an input column that is a vector.</span></span> <span data-ttu-id="1e5c0-244">Varsayılan olarak bu vektör sütunu **Özellikler**olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-244">By default this vector column is called **Features**.</span></span> <span data-ttu-id="1e5c0-245">Bu nedenle **Size** sütununu ev fiyat örneğimizde **Özellikler** adlı yeni bir sütuna dönüştürdük.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-245">This is why we concatenated the **Size** column into a new column called **Features** in our house price example.</span></span>

 ```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
 ```

<span data-ttu-id="1e5c0-246">Tüm algoritmalar, bir tahmin gerçekleştirdikten sonra da yeni sütunlar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-246">All algorithms also create new columns after they have performed a prediction.</span></span> <span data-ttu-id="1e5c0-247">Bu yeni sütunların sabit adları makine öğrenimi algoritmasının türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-247">The fixed names of these new columns depend on the type of machine learning algorithm.</span></span> <span data-ttu-id="1e5c0-248">Regresyon görevi için, yeni sütunlardan biri **Puan**olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-248">For the regression task, one of the new columns is called **Score**.</span></span> <span data-ttu-id="1e5c0-249">Bu nedenle fiyat verilerimizi bu adla ilişkilendirdik.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-249">This is why we attributed our price data with this name.</span></span>

```csharp
    public class Prediction
    {
        [ColumnName("Score")]
        public float Price { get; set; }
    }
```

<span data-ttu-id="1e5c0-250">[Makine Öğrenimi Görevleri](resources/tasks.md) kılavuzunda farklı makine öğrenimi görevlerinin çıktı sütunları hakkında daha fazla bilgi bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-250">You can find out more about output columns of different machine learning tasks in the [Machine Learning Tasks](resources/tasks.md) guide.</span></span>

<span data-ttu-id="1e5c0-251">DataView nesnelerinin önemli bir özelliği, **onların tembel olarak**değerlendirilmiş olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-251">An important property of DataView objects is that they are evaluated **lazily**.</span></span> <span data-ttu-id="1e5c0-252">Veri görünümleri yalnızca model eğitimi ve değerlendirmesi ve veri tahmini sırasında yüklenir ve çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-252">Data views are only loaded and operated on during model training and evaluation, and data prediction.</span></span> <span data-ttu-id="1e5c0-253">ML.NET uygulamanızı yazarken ve test ederken, [Önizleme](xref:Microsoft.ML.DebuggerExtensions.Preview*) yöntemini arayarak herhangi bir veri görünümü nesnesine göz atmak için Visual Studio hata ayıklama sını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-253">While you are writing and testing your ML.NET application, you can use the Visual Studio debugger to take a peek at any data view object by calling the [Preview](xref:Microsoft.ML.DebuggerExtensions.Preview*) method.</span></span>

```csharp
    var debug = testPriceDataView.Preview();
```

<span data-ttu-id="1e5c0-254">Hata ayıklamadaki değişkeni `debug` izleyebilir ve içeriğini inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-254">You can watch the `debug` variable in the debugger and examine its contents.</span></span> <span data-ttu-id="1e5c0-255">Performansı önemli ölçüde düşürdüğünüz için üretim kodunda Önizleme yöntemini kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-255">Do not use the Preview method in production code, as it significantly degrades performance.</span></span>

### <a name="model-deployment"></a><span data-ttu-id="1e5c0-256">Model Dağıtımı</span><span class="sxs-lookup"><span data-stu-id="1e5c0-256">Model Deployment</span></span>

<span data-ttu-id="1e5c0-257">Gerçek hayattaki uygulamalarda, model eğitim ve değerlendirme kodunuz tahmininizden ayrı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-257">In real-life applications, your model training and evaluation code will be separate from your prediction.</span></span> <span data-ttu-id="1e5c0-258">Aslında, bu iki etkinlik genellikle ayrı takımlar tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-258">In fact, these two activities are often performed by separate teams.</span></span> <span data-ttu-id="1e5c0-259">Model geliştirme ekibiniz modeli tahmin uygulamasında kullanılmak üzere kaydedebilir.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-259">Your model development team can save the model for use in the prediction application.</span></span>

```csharp
   mlContext.Model.Save(model, trainingData.Schema,"model.zip");
```

## <a name="next-steps"></a><span data-ttu-id="1e5c0-260">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="1e5c0-260">Next steps</span></span>

* <span data-ttu-id="1e5c0-261">Öğreticilerde daha gerçekçi veri [kümeleri](./tutorials/index.md)ile farklı makine öğrenimi görevleri kullanarak uygulamaları oluşturmak için nasıl öğrenin.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-261">Learn how to build applications using different machine learning tasks with more realistic data sets in the [tutorials](./tutorials/index.md).</span></span>

* <span data-ttu-id="1e5c0-262">[Nasıl Kılavuzlar](./how-to-guides/index.md)için daha derinlemesine belirli konular hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-262">Learn about specific topics in more depth in the [How To Guides](./how-to-guides/index.md).</span></span>

* <span data-ttu-id="1e5c0-263">Eğer süper hevesli iseniz, doğrudan [API Başvuru belgeleri](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet)içine dalış yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e5c0-263">If you're super keen, you can dive straight into the [API Reference documentation](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet).</span></span>
