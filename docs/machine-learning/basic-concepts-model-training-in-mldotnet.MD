---
title: ML.NET eğitim modeli için temel kavramlar
description: Bu makalede kapsayan temel kavramları açıklar *model eğitim* ML.NET senaryolarda. Tüm kavramları daha basit bir senaryo için uygun olan *varolan modeli ile tahmini*.
ms.date: 03/05/2019
ms.topic: overview
ms.custom: mvc
ms.openlocfilehash: 78554cfd1dfdb3dba82a325d47245aeb313bb6fe
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675569"
---
# <a name="basic-concepts-for-model-training-in-mlnet"></a><span data-ttu-id="68671-104">ML.NET eğitim modeli için temel kavramlar</span><span class="sxs-lookup"><span data-stu-id="68671-104">Basic concepts for model training in ML.NET</span></span>

<span data-ttu-id="68671-105">Bu makalede kapsayan temel kavramları açıklar *model eğitim* ML.NET senaryolarda.</span><span class="sxs-lookup"><span data-stu-id="68671-105">This article explains the basic concepts covering *model training* scenarios in ML.NET.</span></span> <span data-ttu-id="68671-106">Tüm kavramları daha basit bir senaryo için uygun olan *mevcut bir model ile tahmini*.</span><span class="sxs-lookup"><span data-stu-id="68671-106">Not all concepts are relevant to the more simple scenario of *prediction with an existing model*.</span></span>

<span data-ttu-id="68671-107">Bu makale ve ilgili örnek şu anda kullandığınız **ML.NET sürüm 0.10**.</span><span class="sxs-lookup"><span data-stu-id="68671-107">This article and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="68671-108">Daha fazla bilgi için bkz: adresindeki sürüm notlarını [dotnet/machinelearning GitHub deposunu](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="68671-108">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

## <a name="model-training-concepts"></a><span data-ttu-id="68671-109">Model eğitimi kavramları</span><span class="sxs-lookup"><span data-stu-id="68671-109">Model training concepts</span></span>

<span data-ttu-id="68671-110">Bu belge ML.NET modeli eğitimi ilgili aşağıdaki kavramları kapsar:</span><span class="sxs-lookup"><span data-stu-id="68671-110">This document covers the following concepts related to model training in ML.NET:</span></span>

- <span data-ttu-id="68671-111">[*Veri* ](#data) olarak temsil edilen bir `IDataView` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="68671-111">[*Data*](#data) represented as an `IDataView` interface.</span></span>
  - <span data-ttu-id="68671-112">ML.NET verileri bir SQL görünümüne benzer: Bu bir gevşek Değerlendirilmiş, sabit, cursorable, heterojen, şema veri kümesi olur.</span><span class="sxs-lookup"><span data-stu-id="68671-112">In ML.NET, data is similar to a SQL view: It's a lazily evaluated, immutable, cursorable, heterogenous, schematized dataset.</span></span> 
  - <span data-ttu-id="68671-113">Mükemmel bir belge veri arabirimi hakkında [IDataView tasarım ilkeleri](https://github.com/dotnet/machinelearning/blob/master/docs/code/IDataViewDesignPrinciples.md).</span><span class="sxs-lookup"><span data-stu-id="68671-113">An excellent document about the data interface is [IDataView Design Principles](https://github.com/dotnet/machinelearning/blob/master/docs/code/IDataViewDesignPrinciples.md).</span></span>
- <span data-ttu-id="68671-114">[*Transformer* ](#transformer) olarak temsil edilen `ITransformer` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="68671-114">[*Transformer*](#transformer) represented as `ITransformer` interface.</span></span>
  - <span data-ttu-id="68671-115">Bir veri alan bir bileşendir, bazı üzerinde çalışır ve dönüştürülen verilere yeni döndürür.</span><span class="sxs-lookup"><span data-stu-id="68671-115">A transformer is a component that takes data, does some work on it, and returns new transformed data.</span></span>
  - <span data-ttu-id="68671-116">Örneğin, bir makine öğrenme modelinin özellikleri alır ve Öngörüler döndüren bir dönüştürücü düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68671-116">For example, you can think of a machine learning model as a transformer that takes features and returns predictions.</span></span>
  - <span data-ttu-id="68671-117">Başka bir örnek metin simgeleştirici tek metin sütununu alır ve bir vektör sütun ayıklanan metinleri dışında kelimeler ile çıkarır.</span><span class="sxs-lookup"><span data-stu-id="68671-117">Another example, text tokenizer takes a single text column and outputs a vector column with individual words extracted out of the texts.</span></span>
- <span data-ttu-id="68671-118">[*Veri okuyucusu* ](#data-reader) olarak temsil edilen bir `IDataReader<T>` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="68671-118">[*Data reader*](#data-reader) represented as an `IDataReader<T>` interface.</span></span>
  - <span data-ttu-id="68671-119">Veri okuyucu verileri oluşturmak için ML.NET bileşendir.</span><span class="sxs-lookup"><span data-stu-id="68671-119">The data reader is ML.NET component to create data.</span></span> <span data-ttu-id="68671-120">Örneğini alır `T` ve bu verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="68671-120">It takes an instance of `T` and returns data out of it.</span></span> 
  - <span data-ttu-id="68671-121">Örneğin, bir *TextLoader* olduğu bir `IDataReader<IMultiStreamSource>`.</span><span class="sxs-lookup"><span data-stu-id="68671-121">For example, a *TextLoader* is an `IDataReader<IMultiStreamSource>`.</span></span> <span data-ttu-id="68671-122">Bu kaynak alır ve veri üretir.</span><span class="sxs-lookup"><span data-stu-id="68671-122">It takes the source and produces data.</span></span> 
- <span data-ttu-id="68671-123">[*Tahmin* ](#estimator) olarak temsil edilen bir `IEstimator<T>` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="68671-123">[*Estimator*](#estimator) represented as an `IEstimator<T>` interface.</span></span>
  - <span data-ttu-id="68671-124">Bu verilerden öğrenen bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="68671-124">This is an object that learns from data.</span></span> <span data-ttu-id="68671-125">Öğrenme sonucu bir *transformer*.</span><span class="sxs-lookup"><span data-stu-id="68671-125">The result of the learning is a *transformer*.</span></span>
  - <span data-ttu-id="68671-126">Bir machine learning, düşündüğünüz *algoritması* veri öğrenir ve bir machine learning üreten bir tahmin aracı olarak *model*.</span><span class="sxs-lookup"><span data-stu-id="68671-126">You can think of a machine learning *algorithm* as an estimator that learns on data and produces a machine learning *model*.</span></span>
- <span data-ttu-id="68671-127">[*Tahmin işlevi* ](#prediction-function) olarak temsil edilen bir `PredictionEngine<TSrc, TDst>` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="68671-127">[*Prediction function*](#prediction-function) represented as a `PredictionEngine<TSrc, TDst>` class.</span></span>
  - <span data-ttu-id="68671-128">Tahmin işlevi uygulayan bir bir satır için gibi tahmin zaman makine olarak görülebilir.</span><span class="sxs-lookup"><span data-stu-id="68671-128">The prediction function can be seen as a machine that applies a transformer to one row, such as at prediction time.</span></span>

## <a name="data"></a><span data-ttu-id="68671-129">Veri</span><span class="sxs-lookup"><span data-stu-id="68671-129">Data</span></span>

<span data-ttu-id="68671-130">ML.NET verileri bir SQL görünümüne benzer: Bu bir gevşek, değerlendirilir cursorable, heterojen, şema veri kümesi.</span><span class="sxs-lookup"><span data-stu-id="68671-130">In ML.NET, data is similar to a SQL view: It's a lazily evaluated, cursorable, heterogenous, schematized dataset.</span></span>

- <span data-ttu-id="68671-131">Sahip *şema* (örneği bir `ISchema` arabirimi), veri görünümü'nün sütunları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="68671-131">It has *Schema* (an instance of an `ISchema` interface) that contains the information about the data view's columns.</span></span>
  - <span data-ttu-id="68671-132">Her sütunun bir *adı*, *türü*ve isteğe bağlı bir dizi *meta verileri* ilişkili.</span><span class="sxs-lookup"><span data-stu-id="68671-132">Each column has a *Name*, a *Type*, and an arbitrary set of *metadata* associated with it.</span></span>
  - <span data-ttu-id="68671-133">Sütunun *meta verileri* vektör sütun ve benzeri yuvası adları gibi bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="68671-133">The column's *metadata* contains information like slot names of a vector column and the like.</span></span> <span data-ttu-id="68671-134">Başka bir satır meta temsil *veri* her sütun için benzersiz.</span><span class="sxs-lookup"><span data-stu-id="68671-134">The metadata itself is represented as another one-row *data* that is unique to each column.</span></span>
  - <span data-ttu-id="68671-135">Bir veri görünümü kaynağıdır *imleçler*.</span><span class="sxs-lookup"><span data-stu-id="68671-135">The data view is a source of *cursors*.</span></span> <span data-ttu-id="68671-136">SQL imleçlerin dikkate alın: Bir imleç kullanılabilir verileri bir kerede bir satır veri gezinir ve bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="68671-136">Think SQL cursors: A cursor is an object that iterates through the data, one row at a time, and presents the available data.</span></span>
  - <span data-ttu-id="68671-137">Doğal olarak, veri gibi çok sayıda etkin imleçler gerektiği şekilde sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68671-137">Naturally, data can have as many active cursors over it as needed.</span></span> <span data-ttu-id="68671-138">İmleçler veriyle sabit olduğundan, tamamen bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="68671-138">Since data itself is immutable, cursors are truly independent.</span></span>
  - <span data-ttu-id="68671-139">İmleçler, genellikle yalnızca bir sütun alt kümesi erişebilirsiniz: Verimlilik için yalnızca imleci tarafından gerekli olan sütunların değerlerini ML.NET hesaplar.</span><span class="sxs-lookup"><span data-stu-id="68671-139">Cursors typically access only a subset of columns: For efficiency, ML.NET computes only the values of columns that are needed by the cursor.</span></span>

## <a name="transformer"></a><span data-ttu-id="68671-140">Transformer</span><span class="sxs-lookup"><span data-stu-id="68671-140">Transformer</span></span>

<span data-ttu-id="68671-141">Bir veri alan bir bileşendir, bazı üzerinde çalışır ve dönüştürülen verilere yeni döndürür.</span><span class="sxs-lookup"><span data-stu-id="68671-141">A transformer is a component that takes data, does some work on it, and returns new transformed data.</span></span>

<span data-ttu-id="68671-142">ML.NET içinde çoğu dönüştürücüler birinde çalışan eğilimindedir *giriş sütununu* zamanda ve üretim *çıktı sütunu*.</span><span class="sxs-lookup"><span data-stu-id="68671-142">Most transformers in ML.NET tend to operate on one *input column* at a time, and produce the *output column*.</span></span> <span data-ttu-id="68671-143">Örneğin, bir `new HashTransformer("bar", "foo")` sütun "foo" değerlerini alır, bunları karma hale getirir ve bunları "çubuğu" sütununa yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="68671-143">For example, a `new HashTransformer("bar", "foo")` takes the values from column "foo", hashes them, and puts them into column "bar".</span></span> 

<span data-ttu-id="68671-144">Giriş ve çıkış sütun adlarının aynı olduğunu yaygındır.</span><span class="sxs-lookup"><span data-stu-id="68671-144">It's also common that the input and output column names are the same.</span></span> <span data-ttu-id="68671-145">Bu durumda, eski sütunu yenisiyle değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="68671-145">In this case, the old column is replaced with the new one.</span></span> <span data-ttu-id="68671-146">Örneğin, bir `new HashTransformer("foo")` "foo" bunları geri koyar sütun "foo" değerlerini alır ve bunları karma hale getirir.</span><span class="sxs-lookup"><span data-stu-id="68671-146">For example, a `new HashTransformer("foo")` takes the values from column "foo", hashes them, and puts them back into "foo".</span></span> 

<span data-ttu-id="68671-147">Herhangi bir dönüştürücü, yeni bir veri görünümü zaman üretir `Transform` çağrılır.</span><span class="sxs-lookup"><span data-stu-id="68671-147">Any transformer, produces a new data view when `Transform` is called.</span></span> <span data-ttu-id="68671-148">Veri görünümleri sabittir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="68671-148">Remember, data views are immutable.</span></span>

<span data-ttu-id="68671-149">Veri gevşek değerlendirilir, başka bir önemli konu, çünkü *dönüştürücüler yavaş çok*.</span><span class="sxs-lookup"><span data-stu-id="68671-149">Another important consideration is that, because data is lazily evaluated, *transformers are lazy too*.</span></span> <span data-ttu-id="68671-150">Aslında, sonra çağırın</span><span class="sxs-lookup"><span data-stu-id="68671-150">Essentially, after you call</span></span>

```csharp
var newData = transformer.Transform(oldData)
```

<span data-ttu-id="68671-151">gerçek bir hesaplama gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="68671-151">no actual computation happens.</span></span> <span data-ttu-id="68671-152">Yalnızca bir imleci aldığınızda `newData` ve başlangıç değeri kullanan `newData` çağırma `transformer` dönüştürme mantığını (ve hatta daha sonra yalnızca olur `transformer` söz konusu istenen sütunlar oluşturmak için gereklidir).</span><span class="sxs-lookup"><span data-stu-id="68671-152">Only after you get a cursor from `newData` and start consuming the value does `newData` invoke the `transformer` transformation logic (and even then, it only happens if the `transformer` in question is needed to produce the requested columns).</span></span>

### <a name="transformer-chains"></a><span data-ttu-id="68671-153">Transformer zincirleri</span><span class="sxs-lookup"><span data-stu-id="68671-153">Transformer chains</span></span>

<span data-ttu-id="68671-154">Bir kullanışlı bir özellik olan *dönüştürücüler, sıralı bir uygulama olarak başka bir dönüştürücü oluşturabileceğinizi*:</span><span class="sxs-lookup"><span data-stu-id="68671-154">A useful property of a transformer is that *you can build a sequential application of transformers as yet another transformer*:</span></span>

```csharp
var fullTransformer = transformer1.Append(transformer2).Append(transformer3);
```

<span data-ttu-id="68671-155">Bu özellik ML.NET yaygın olarak kullanılır: genellikle eğitim ML.NET modeli için tüm intents ve purposes, olan dönüştürücüler, zinciri olan bir *transformer*.</span><span class="sxs-lookup"><span data-stu-id="68671-155">This property is commonly used in ML.NET: typically, the trained ML.NET model is a chain of transformers, which is, for all intents and purposes, a *transformer*.</span></span>

## <a name="data-reader"></a><span data-ttu-id="68671-156">Veri okuyucusu</span><span class="sxs-lookup"><span data-stu-id="68671-156">Data reader</span></span>

<span data-ttu-id="68671-157">Veri okuyucu 'verileri oluşturmak için ' bir ML.NET bileşendir: örneğini alır `T` ve bu verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="68671-157">The data reader is an ML.NET component to 'create' data: it takes an instance of `T` and returns data out of it.</span></span>

<span data-ttu-id="68671-158">Dikkat edilecek bir ilgi çekici bir veri Okuyucu için mevcut bir veri okuyucu bir dönüştürücü ekleyerek oluşturabilirsiniz özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="68671-158">An interesting property to note is that you can create a data reader by attaching a transformer to an existing data reader.</span></span> <span data-ttu-id="68671-159">Bu şekilde dönüştürme davranış marketinden bir okuyucu olabilir:</span><span class="sxs-lookup"><span data-stu-id="68671-159">This way you can have a reader with transformation behavior baked in:</span></span>

```csharp
var newReader = reader.Append(transformer1).Append(transformer2)
```

<span data-ttu-id="68671-160">Veri gevşek değerlendirilir, başka bir benzerliği dönüştürücüler, olduğu *okuyucular yavaş*: yok (veya en az) gerçek 'okuma' olmuyor çağırdığınızda `reader.Read()`: yalnızca bir imleç elde edilen verileri ne zaman istenen yok Okuyucu çalışmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="68671-160">Another similarity to transformers is that, since data is lazily evaluated, *readers are lazy*: no (or minimal) actual 'reading' happens when you call `reader.Read()`: only when a cursor is requested on the resulting data does the reader begin to work.</span></span>

## <a name="estimator"></a><span data-ttu-id="68671-161">Tahmin aracı</span><span class="sxs-lookup"><span data-stu-id="68671-161">Estimator</span></span>

<span data-ttu-id="68671-162">*Estimator* verilerden öğrenir bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="68671-162">The *estimator* is an object that learns from data.</span></span> <span data-ttu-id="68671-163">Öğrenme sonucu bir *transformer*.</span><span class="sxs-lookup"><span data-stu-id="68671-163">The result of the learning is a *transformer*.</span></span>

<span data-ttu-id="68671-164">ML.NET içinde farklı estimators zincir learning işlem hatlarını oluşturmak için bu özelliği kullanın:</span><span class="sxs-lookup"><span data-stu-id="68671-164">In ML.NET, use this property to create learning pipelines that chain together different estimators:</span></span>

```csharp
MLContext mlContext = new MLContext(seed: 0);

var pipeline = mlContext.Transforms.CopyColumns("Label","FareAmount")
    .Append(mlContext.Transforms.Categorical.OneHotEncoding("VendorId"))
    .Append(mlContext.Transforms.Categorical.OneHotEncoding("RateCode"))
    .Append(mlContext.Transforms.Categorical.OneHotEncoding("PaymentType"))
    .Append(mlContext.Transforms.Concatenate("Features","VendorId","RateCode","PassengerCount","TripTime","TripDistance","PaymentType"))
    .Append(mlContext.Regression.Trainers.FastTree("Label","Features"));

var model = pipeline.Fit(dataView);
```

<span data-ttu-id="68671-165">Estimators önemli bir özellik olan *estimators eager, olmayan yavaş*: yapılan her çağrı `Fit` olası zaman alıcı bir işlem olan meydana gelmesine öğrenme neden oluyor.</span><span class="sxs-lookup"><span data-stu-id="68671-165">One important property of estimators is that *estimators are eager, not lazy*: every call to `Fit` is causing learning to happen, which is potentially a time-consuming operation.</span></span>

## <a name="prediction-function"></a><span data-ttu-id="68671-166">Tahmin işlevi</span><span class="sxs-lookup"><span data-stu-id="68671-166">Prediction function</span></span>

<span data-ttu-id="68671-167">Tahmin işlevi bir satır için bir dönüştürücü uygulayan bir bileşen olarak görülebilir.</span><span class="sxs-lookup"><span data-stu-id="68671-167">The prediction function can be seen as a component that applies a transformer to one row.</span></span>

<span data-ttu-id="68671-168">Model aldıktan sonra (bir *transformer* aracılığıyla ya da eğitim `Fit()`, veya bir yere gelen yüklü), normal çağrıları kullanarak tahminlerde bulunmayı kullanabilirsiniz `model.Transform(data)`.</span><span class="sxs-lookup"><span data-stu-id="68671-168">Once you get the model (a *transformer* either trained via `Fit()`, or loaded from somewhere), you can use it to make predictions using the normal calls to `model.Transform(data)`.</span></span> <span data-ttu-id="68671-169">Ancak, gerçek zamanlı konuşmaların senaryoda bu modeli kullandığınızda, genellikle şirket tahmin etmek için birçok örneği yok.</span><span class="sxs-lookup"><span data-stu-id="68671-169">However, when you use this model in a real-life scenario, you often don't have many examples to predict on.</span></span> <span data-ttu-id="68671-170">Bunun yerine, bir örnek aynı anda sahip ve zamanında bunlar üzerinde hemen tahminlerde gerekir.</span><span class="sxs-lookup"><span data-stu-id="68671-170">Instead, you have one example at a time, and you need to make timely predictions on them immediately.</span></span>

<span data-ttu-id="68671-171">Elbette, bunu batch tahmin azaltabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="68671-171">Of course, you can reduce this to the batch prediction:</span></span>

- <span data-ttu-id="68671-172">Veri Görünümü ile tam olarak bir satır oluşturun.</span><span class="sxs-lookup"><span data-stu-id="68671-172">Create a data view with exactly one row.</span></span>
- <span data-ttu-id="68671-173">Çağrı `model.Transform(data)` tahmin edilen veriler bir görünüm elde edin.</span><span class="sxs-lookup"><span data-stu-id="68671-173">Call `model.Transform(data)` to get the predicted data view.</span></span>
- <span data-ttu-id="68671-174">Sonuçta elde edilen veriler üzerinde bir imleç alın.</span><span class="sxs-lookup"><span data-stu-id="68671-174">Get a cursor over the resulting data.</span></span>
- <span data-ttu-id="68671-175">İlk (ve tek) satır almak için İmleç bir adım ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="68671-175">Advance the cursor one step to get to the first (and only) row.</span></span>
- <span data-ttu-id="68671-176">Tahmin edilen değerler dışına ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="68671-176">Extract the predicted values out of it.</span></span>

<span data-ttu-id="68671-177">Önceki algoritması kullanılarak uygulanabilir [şema kavramayı](https://github.com/dotnet/machinelearning/blob/master/docs/code/SchemaComprehension.md), iki kullanıcı tanımlı nesneler ile `InputExample` ve `OutputPrediction` şu şekilde:</span><span class="sxs-lookup"><span data-stu-id="68671-177">The preceding algorithm can be implemented using the [schema comprehension](https://github.com/dotnet/machinelearning/blob/master/docs/code/SchemaComprehension.md), with two user-defined objects `InputExample` and `OutputPrediction` as follows:</span></span>

```csharp
var inputData = mlContext.Data.ReadFromEnumerable(new InputExample[] { example });
var outputData = model.Transform(inputData);
var output = mlContext.CreateEnumerable<OutputPrediction>(outputData,reuseRowObject:false).First();
```

<span data-ttu-id="68671-178">Ancak bu yavaşlatan bir yöntemdir ve performans maliyetleri doğurur.</span><span class="sxs-lookup"><span data-stu-id="68671-178">But this is cumbersome and incurs performance costs.</span></span> <span data-ttu-id="68671-179">Bunun yerine, tahmin işlev nesnesi aynı iş, ancak daha hızlı ve daha kolay, bir genişletme yöntemi aracılığıyla gerçekleştirir `CreatePredictionEngine`:</span><span class="sxs-lookup"><span data-stu-id="68671-179">Instead, a prediction function object performs the same work, but faster and more convenient, via an extension method `CreatePredictionEngine`:</span></span>

```csharp
var predictionEngine = model.CreatePredictionEngine<InputExample,OutputPrediction>(mlContext);
var prediction = predictionEngine.Predict(example);
```

<span data-ttu-id="68671-180">Tahmin işlevi *değil a / iş parçacığı açısından güvenli*.</span><span class="sxs-lookup"><span data-stu-id="68671-180">The prediction function is *not re-entrant / thread-safe*.</span></span> <span data-ttu-id="68671-181">Öngörüler aynı anda birden çok iş parçacığı ile gerçekleştirmek istiyorsanız, iş parçacığı başına bir tahmin işlevi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="68671-181">If you want to conduct predictions simultaneously with multiple threads, you need to have a prediction function per thread.</span></span>
