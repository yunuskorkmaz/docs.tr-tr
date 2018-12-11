---
title: ML.NET eğitim modeli için temel kavramlar
description: Bu makalede kapsayan temel kavramları açıklar *model eğitim* ML.NET senaryolarda. Tüm kavramları daha basit bir senaryo için uygun olan *varolan modeli ile tahmini*.
ms.date: 11/06/2018
ms.topic: overview
ms.custom: mvc
ms.openlocfilehash: cff833b45583bc752bb42616820a95ca6c5c6b12
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155440"
---
# <a name="basic-concepts-for-model-training-in-mlnet"></a><span data-ttu-id="9688c-104">ML.NET eğitim modeli için temel kavramlar</span><span class="sxs-lookup"><span data-stu-id="9688c-104">Basic concepts for model training in ML.NET</span></span>

<span data-ttu-id="9688c-105">Bu makalede kapsayan temel kavramları açıklar *model eğitim* ML.NET senaryolarda.</span><span class="sxs-lookup"><span data-stu-id="9688c-105">This article explains the basic concepts covering *model training* scenarios in ML.NET.</span></span> <span data-ttu-id="9688c-106">Tüm kavramları daha basit bir senaryo için uygun olan *varolan modeli ile tahmini*.</span><span class="sxs-lookup"><span data-stu-id="9688c-106">Not all concepts are relevant to the more simple scenario of *prediction with existing model*.</span></span>

## <a name="model-training-concepts"></a><span data-ttu-id="9688c-107">Model eğitimi kavramları</span><span class="sxs-lookup"><span data-stu-id="9688c-107">Model training concepts</span></span>

<span data-ttu-id="9688c-108">Bu belge ML.NET modeli eğitimi ilgili aşağıdaki kavramları kapsar:</span><span class="sxs-lookup"><span data-stu-id="9688c-108">This document covers the following concepts related to model training in ML.NET:</span></span>

- <span data-ttu-id="9688c-109">[*Veri* ](#data) olarak temsil edilen bir `IDataView` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="9688c-109">[*Data*](#data) represented as an `IDataView` interface.</span></span>
  - <span data-ttu-id="9688c-110">ML.NET verileri bir SQL görünümüne benzer: Bu bir gevşek Değerlendirilmiş, sabit, cursorable, heterojen, şema veri kümesi olur.</span><span class="sxs-lookup"><span data-stu-id="9688c-110">In ML.NET, data is similar to a SQL view: It's a lazily evaluated, immutable, cursorable, heterogenous, schematized dataset.</span></span> 
  - <span data-ttu-id="9688c-111">Mükemmel bir belge veri arabirimi hakkında [IDataView tasarım ilkeleri](https://github.com/dotnet/machinelearning/blob/master/docs/code/IDataViewDesignPrinciples.md).</span><span class="sxs-lookup"><span data-stu-id="9688c-111">An excellent document about the data interface is [IDataView Design Principles](https://github.com/dotnet/machinelearning/blob/master/docs/code/IDataViewDesignPrinciples.md).</span></span>
- <span data-ttu-id="9688c-112">[*Transformer* ](#transformer) olarak temsil edilen `ITransformer` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="9688c-112">[*Transformer*](#transformer) represented as `ITransformer` interface.</span></span>
  - <span data-ttu-id="9688c-113">Bir veri alan bir bileşendir, bazı üzerinde çalışır ve dönüştürülen verilere yeni döndürür.</span><span class="sxs-lookup"><span data-stu-id="9688c-113">A transformer is a component that takes data, does some work on it, and returns new transformed data.</span></span>
  - <span data-ttu-id="9688c-114">Örneğin, bir makine öğrenme modelinin özellikleri alır ve Öngörüler döndüren bir dönüştürücü düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9688c-114">For example, you can think of a machine learning model as a transformer that takes features and returns predictions.</span></span>
  - <span data-ttu-id="9688c-115">Başka bir örnek metin simgeleştirici tek metin sütununu alır ve bir vektör sütun ayıklanan metinleri dışında kelimeler ile çıktı.</span><span class="sxs-lookup"><span data-stu-id="9688c-115">Another example, text tokenizer takes a single text column and output a vector column with individual words extracted out of the texts.</span></span>
- <span data-ttu-id="9688c-116">[*Veri okuyucusu* ](#data-reader) olarak temsil edilen bir `IDataReader<T>` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="9688c-116">[*Data reader*](#data-reader) represented as an `IDataReader<T>` interface.</span></span>
  - <span data-ttu-id="9688c-117">Veri okuyucu verileri oluşturmak için ML.NET bileşendir.</span><span class="sxs-lookup"><span data-stu-id="9688c-117">The data reader is ML.NET component to create data.</span></span> <span data-ttu-id="9688c-118">Örneğini alır `T` ve bu verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="9688c-118">It takes an instance of `T` and returns data out of it.</span></span> 
  - <span data-ttu-id="9688c-119">Örneğin, bir *TextLoader* olduğu bir `IDataReader<FileSource>`.</span><span class="sxs-lookup"><span data-stu-id="9688c-119">For example, a *TextLoader* is an `IDataReader<FileSource>`.</span></span> <span data-ttu-id="9688c-120">Bu dosya kaynak alır ve veri üretir.</span><span class="sxs-lookup"><span data-stu-id="9688c-120">It takes the file source and produces data.</span></span> 
- <span data-ttu-id="9688c-121">[*Tahmin* ](#estimator) olarak temsil edilen bir `IEstimator<T>` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="9688c-121">[*Estimator*](#estimator) represented as an `IEstimator<T>` interface.</span></span>
  - <span data-ttu-id="9688c-122">Bu verilerden öğrenen bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="9688c-122">This is an object that learns from data.</span></span> <span data-ttu-id="9688c-123">Öğrenme sonucu bir *transformer*.</span><span class="sxs-lookup"><span data-stu-id="9688c-123">The result of the learning is a *transformer*.</span></span>
  - <span data-ttu-id="9688c-124">Bir machine learning, düşündüğünüz *algoritması* veri öğrenir ve bir machine learning üreten bir tahmin aracı olarak *model*.</span><span class="sxs-lookup"><span data-stu-id="9688c-124">You can think of a machine learning *algorithm* as an estimator that learns on data and produces a machine learning *model*.</span></span>
- <span data-ttu-id="9688c-125">[*Tahmin işlevi* ](#prediction-function) olarak temsil edilen bir `PredictionFunction<TSrc, TDst>` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9688c-125">[*Prediction function*](#prediction-function) represented as a `PredictionFunction<TSrc, TDst>` class.</span></span>
  - <span data-ttu-id="9688c-126">Tahmin işlevi uygulayan bir bir satır için gibi tahmin zaman makine olarak görülebilir.</span><span class="sxs-lookup"><span data-stu-id="9688c-126">The prediction function can be seen as a machine that applies a transformer to one row, such as at prediction time.</span></span>

## <a name="data"></a><span data-ttu-id="9688c-127">Veri</span><span class="sxs-lookup"><span data-stu-id="9688c-127">Data</span></span>

<span data-ttu-id="9688c-128">ML.NET verileri bir SQL görünümüne benzer: Bu bir gevşek, değerlendirilir cursorable, heterojen, şema veri kümesi.</span><span class="sxs-lookup"><span data-stu-id="9688c-128">In ML.NET, data is similar to a SQL view: It's a lazily evaluated, cursorable, heterogenous, schematized dataset.</span></span>

- <span data-ttu-id="9688c-129">Sahip *şema* (örneği bir `ISchema` arabirimi), veri görünümü'nün sütunları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="9688c-129">It has *Schema* (an instance of an `ISchema` interface) that contains the information about the data view's columns.</span></span>
  - <span data-ttu-id="9688c-130">Her sütunun bir *adı*, *türü*ve isteğe bağlı bir dizi *meta verileri* ilişkili.</span><span class="sxs-lookup"><span data-stu-id="9688c-130">Each column has a *Name*, a *Type*, and an arbitrary set of *metadata* associated with it.</span></span>
  - <span data-ttu-id="9688c-131">Sütunun *meta verileri* vektör sütun ve benzeri yuvası adları gibi bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="9688c-131">The column's *metadata* contains information like slot names of a vector column and the like.</span></span> <span data-ttu-id="9688c-132">Başka bir satır meta temsil *veri* her sütun için benzersiz.</span><span class="sxs-lookup"><span data-stu-id="9688c-132">The metadata itself is represented as another one-row *data* that is unique to each column.</span></span>
  - <span data-ttu-id="9688c-133">Bir veri görünümü kaynağıdır *imleçler*.</span><span class="sxs-lookup"><span data-stu-id="9688c-133">The data view is a source of *cursors*.</span></span> <span data-ttu-id="9688c-134">SQL imleçlerin dikkate alın: Bir imleç kullanılabilir verileri bir kerede bir satır veri gezinir ve bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="9688c-134">Think SQL cursors: A cursor is an object that iterates through the data, one row at a time, and presents the available data.</span></span>
  - <span data-ttu-id="9688c-135">Doğal olarak, veri gibi çok sayıda etkin imleçler gerektiği şekilde sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9688c-135">Naturally, data can have as many active cursors over it as needed.</span></span> <span data-ttu-id="9688c-136">İmleçler veriyle sabit olduğundan, tamamen bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="9688c-136">Since data itself is immutable, cursors are truly independent.</span></span>
  - <span data-ttu-id="9688c-137">İmleçler, genellikle yalnızca bir sütun alt kümesi erişebilirsiniz: Verimlilik için yalnızca imleci tarafından gerekli olan sütunların değerlerini ML.NET hesaplar.</span><span class="sxs-lookup"><span data-stu-id="9688c-137">Cursors typically access only a subset of columns: For efficiency, ML.NET computes only the values of columns that are needed by the cursor.</span></span>

## <a name="transformer"></a><span data-ttu-id="9688c-138">Transformer</span><span class="sxs-lookup"><span data-stu-id="9688c-138">Transformer</span></span>

<span data-ttu-id="9688c-139">Bir dönüştürücü veri alan bir bileşendir, bazı üzerinde çalışmak ve yeni dönüştürülmüş verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="9688c-139">A transformer is a component that takes data, does some work on it, and return new transformed data.</span></span>

<span data-ttu-id="9688c-140">ML.NET içinde çoğu dönüştürücüler birinde çalışan eğilimindedir *giriş sütununu* zamanda ve üretim *çıktı sütunu*.</span><span class="sxs-lookup"><span data-stu-id="9688c-140">Most transformers in ML.NET tend to operate on one *input column* at a time, and produce the *output column*.</span></span> <span data-ttu-id="9688c-141">Örneğin, bir `new HashTransformer("foo", "bar")` değerleri alır "foo" sütununda, bunları karma ve bunları "çubuğu" sütuna yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9688c-141">For example, a `new HashTransformer("foo", "bar")` takes the values from column "foo", hash them, and put them into column "bar".</span></span> 

<span data-ttu-id="9688c-142">Giriş ve çıkış sütun adlarının aynı olduğunu yaygındır.</span><span class="sxs-lookup"><span data-stu-id="9688c-142">It's also common that the input and output column names are the same.</span></span> <span data-ttu-id="9688c-143">Bu durumda, eski sütunu yenisiyle değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="9688c-143">In this case, the old column is replaced with the new one.</span></span> <span data-ttu-id="9688c-144">Örneğin, bir `new HashTransformer("foo")` sütun "foo", "foo" bunları geri karma bunları ve put değerleri alır.</span><span class="sxs-lookup"><span data-stu-id="9688c-144">For example, a `new HashTransformer("foo")` takes the values from column "foo", hash them, and put them back into "foo".</span></span> 

<span data-ttu-id="9688c-145">Tüm transformer, doğal olarak, yeni bir veri görünümü zaman üretir `Transform` çağrılır.</span><span class="sxs-lookup"><span data-stu-id="9688c-145">Any transformer, of course, produces a new data view when `Transform` is called.</span></span> <span data-ttu-id="9688c-146">Veri görünümleri sabittir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9688c-146">Remember, data views are immutable.</span></span>

<span data-ttu-id="9688c-147">Veri gevşek değerlendirilir, başka bir önemli konu, çünkü *dönüştürücüler yavaş çok*.</span><span class="sxs-lookup"><span data-stu-id="9688c-147">Another important consideration is that, because data is lazily evaluated, *transformers are lazy too*.</span></span> <span data-ttu-id="9688c-148">Aslında, sonra çağırın</span><span class="sxs-lookup"><span data-stu-id="9688c-148">Essentially, after you call</span></span>

```csharp
var newData = transformer.Transform(oldData)
```

<span data-ttu-id="9688c-149">gerçek bir hesaplama gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="9688c-149">no actual computation happens.</span></span> <span data-ttu-id="9688c-150">Yalnızca bir imleci aldığınızda `newData` ve başlangıç değeri kullanan `newData` çağırma `transformer` dönüştürme mantığını (ve hatta tek olması durumunda `transformer` söz konusu istenen sütunlar oluşturmak için gereklidir).</span><span class="sxs-lookup"><span data-stu-id="9688c-150">Only after you get a cursor from `newData` and start consuming the value does `newData` invoke the `transformer` transformation logic (and even that only if `transformer` in question is needed to produce the requested columns).</span></span>

### <a name="transformer-chains"></a><span data-ttu-id="9688c-151">Transformer zincirleri</span><span class="sxs-lookup"><span data-stu-id="9688c-151">Transformer chains</span></span>

<span data-ttu-id="9688c-152">Bir kullanışlı bir özellik olan *dönüştürücüler, sıralı bir uygulama olarak başka bir dönüştürücü tümcecik*:</span><span class="sxs-lookup"><span data-stu-id="9688c-152">A useful property of a transformer is that *you can phrase a sequential application of transformers as yet another transformer*:</span></span>

```csharp
var fullTransformer = transformer1.Append(transformer2).Append(transformer3);
```

<span data-ttu-id="9688c-153">Bu özellik ML.NET yaygın olarak kullanılır: genellikle eğitim ML.NET modeli için tüm intents ve purposes, olan dönüştürücüler, zinciri olan bir *transformer*.</span><span class="sxs-lookup"><span data-stu-id="9688c-153">This property is commonly used in ML.NET: typically, the trained ML.NET model is a chain of transformers, which is, for all intents and purposes, a *transformer*.</span></span> 

## <a name="data-reader"></a><span data-ttu-id="9688c-154">Veri okuyucusu</span><span class="sxs-lookup"><span data-stu-id="9688c-154">Data reader</span></span>

<span data-ttu-id="9688c-155">Veri okuyucu 'verileri oluşturmak için ' ML.NET bileşendir: örneğini alır `T` ve bu verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="9688c-155">The data reader is ML.NET component to 'create' data: it takes an instance of `T` and returns data out of it.</span></span>

<span data-ttu-id="9688c-156">Dikkat edilecek bir ilgi çekici bir veri Okuyucu için mevcut bir veri okuyucu bir dönüştürücü ekleyerek oluşturabilirsiniz özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="9688c-156">An interesting property to note is that you can create a data reader by attaching a transformer to an existing data reader.</span></span> <span data-ttu-id="9688c-157">Bu şekilde dönüştürme davranış marketinden bir okuyucu olabilir:</span><span class="sxs-lookup"><span data-stu-id="9688c-157">This way you can have a reader with transformation behavior baked in:</span></span>

```c#
var newReader = reader.Append(transformer1).Append(transformer2)
```

<span data-ttu-id="9688c-158">Veri gevşek değerlendirilir, başka bir benzerliği dönüştürücüler, olduğu *okuyucular yavaş*: yok (veya en az) gerçek 'okuma' olmuyor çağırdığınızda `dataReader.Read()`: yalnızca bir imleç elde edilen verileri ne zaman istenen yok Okuyucu çalışmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="9688c-158">Another similarity to transformers is that, since data is lazily evaluated, *readers are lazy*: no (or minimal) actual 'reading' happens when you call `dataReader.Read()`: only when a cursor is requested on the resulting data does the reader begin to work.</span></span>

## <a name="estimator"></a><span data-ttu-id="9688c-159">Tahmin aracı</span><span class="sxs-lookup"><span data-stu-id="9688c-159">Estimator</span></span>

<span data-ttu-id="9688c-160">*Estimator* verilerden öğrenir bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="9688c-160">The *estimator* is an object that learns from data.</span></span> <span data-ttu-id="9688c-161">Öğrenme sonucu bir *transformer*.</span><span class="sxs-lookup"><span data-stu-id="9688c-161">The result of the learning is a *transformer*.</span></span>

<span data-ttu-id="9688c-162">ML.NET içinde farklı estimators zincir learning işlem hatlarını oluşturmak için bu özelliği kullanın:</span><span class="sxs-lookup"><span data-stu-id="9688c-162">In ML.NET, use this property to create learning pipelines that chain together different estimators:</span></span>

```csharp
MLContext mlContext = new MLContext(seed: 0);

var pipeline = new CopyColumnsEstimator(mlContext, "FareAmount", "Label")
.Append(mlContextml.Transforms.Categorical.OneHotEncoding(mlContext, "VendorId"))
.Append(mlContextml.Transforms.Categorical.OneHotEncoding(mlContext, "RateCode"))
.Append(mlContextml.Transforms.Categorical.OneHotEncoding(mlContext, "PaymentType"))
.Append(new ColumnConcatenatingEstimator(mlContext, "Features", "VendorId", "RateCode", "PassengerCount", "TripTime", "TripDistance", "PaymentType"))
.Append(mlContext.Regression.Trainers.FastTree("Label", "Features"));

var model = pipeline.Fit(dataView);
```

<span data-ttu-id="9688c-163">Estimators önemli bir özellik olan *estimators eager, olmayan yavaş*: yapılan her çağrı `Fit` olası zaman alıcı bir işlem olan meydana gelmesine öğrenme neden oluyor.</span><span class="sxs-lookup"><span data-stu-id="9688c-163">One important property of estimators is that *estimators are eager, not lazy*: every call to `Fit` is causing learning to happen, which is potentially a time-consuming operation.</span></span>

## <a name="prediction-function"></a><span data-ttu-id="9688c-164">Tahmin işlevi</span><span class="sxs-lookup"><span data-stu-id="9688c-164">Prediction function</span></span>

<span data-ttu-id="9688c-165">Tahmin işlevi bir satır için bir dönüştürücü geçerli makine olarak görülebilir.</span><span class="sxs-lookup"><span data-stu-id="9688c-165">The prediction function can be seen as a machine that applies a transformer to one row.</span></span>

<span data-ttu-id="9688c-166">Model aldıktan sonra (bir *transformer* aracılığıyla ya da eğitim `Fit()`, veya bir yere gelen yüklü), normal çağrıları kullanarak tahminlerde bulunmayı kullanabilirsiniz `model.Transform(data)`.</span><span class="sxs-lookup"><span data-stu-id="9688c-166">Once you get the model (a *transformer* either trained via `Fit()`, or loaded from somewhere), you can use it to make predictions using the normal calls to `model.Transform(data)`.</span></span> <span data-ttu-id="9688c-167">Ancak, gerçek zamanlı konuşmaların senaryoda bu modeli kullandığınızda, genellikle şirket tahmin etmek için birçok örneği yok.</span><span class="sxs-lookup"><span data-stu-id="9688c-167">However, when you use this model in a real-life scenario, you often don't have many examples to predict on.</span></span> <span data-ttu-id="9688c-168">Bunun yerine, bir örnek aynı anda sahip ve zamanında bunlar üzerinde hemen tahminlerde gerekir.</span><span class="sxs-lookup"><span data-stu-id="9688c-168">Instead, you have one example at a time, and you need to make timely predictions on them immediately.</span></span>

<span data-ttu-id="9688c-169">Elbette, bunu batch tahmin azaltabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9688c-169">Of course, you can reduce this to the batch prediction:</span></span>

- <span data-ttu-id="9688c-170">Veri Görünümü ile tam olarak bir satır oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9688c-170">Create a data view with exactly one row.</span></span>
- <span data-ttu-id="9688c-171">Çağrı `model.Transform(data)` tahmin edilen veriler bir görünüm elde edin.</span><span class="sxs-lookup"><span data-stu-id="9688c-171">Call `model.Transform(data)` to get the predicted data view.</span></span>
- <span data-ttu-id="9688c-172">Sonuçta elde edilen veriler üzerinde bir imleç alın.</span><span class="sxs-lookup"><span data-stu-id="9688c-172">Get a cursor over the resulting data.</span></span>
- <span data-ttu-id="9688c-173">İlk (ve tek) satır almak için İmleç bir adım ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="9688c-173">Advance the cursor one step to get to the first (and only) row.</span></span>
- <span data-ttu-id="9688c-174">Tahmin edilen değerler dışına ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="9688c-174">Extract the predicted values out of it.</span></span>

<span data-ttu-id="9688c-175">Önceki algoritması kullanılarak uygulanabilir [şema kavramayı](https://github.com/dotnet/machinelearning/blob/master/docs/code/SchemaComprehension.md), iki kullanıcı tanımlı nesneler ile `InputExample` ve `OutputPrediction` şu şekilde:</span><span class="sxs-lookup"><span data-stu-id="9688c-175">The preceding algorithm can be implemented using the [schema comprehension](https://github.com/dotnet/machinelearning/blob/master/docs/code/SchemaComprehension.md), with two user-defined objects `InputExample` and `OutputPrediction` as follows:</span></span>

```c#
var inputData = env.CreateDataView(new InputExample[] { example });
var outputData = model.Transform(inputData);
var output = outputData.AsDynamic.AsEnumerable<OutputPrediction>(env, reuseRowObject: false).Single();
```

<span data-ttu-id="9688c-176">Ancak bu yavaşlatan bir yöntemdir ve performans maliyetleri doğurur.</span><span class="sxs-lookup"><span data-stu-id="9688c-176">But this is cumbersome and incurs performance costs.</span></span> <span data-ttu-id="9688c-177">Bunun yerine, tahmin işlev nesnesi aynı iş, ancak daha hızlı ve daha kolay, bir genişletme yöntemi aracılığıyla gerçekleştirir `MakePredictionFunction`:</span><span class="sxs-lookup"><span data-stu-id="9688c-177">Instead, a prediction function object performs the same work, but faster and more convenient, via an extension method `MakePredictionFunction`:</span></span>

```c#
var predictionFunc = model.MakePredictionFunction<InputExample, OutputPrediction>(env);
var output = predictionFunc.Predict(example);
```

<span data-ttu-id="9688c-178">Tahmin işlevi *değil a / iş parçacığı açısından güvenli*.</span><span class="sxs-lookup"><span data-stu-id="9688c-178">The prediction function is *not re-entrant / thread-safe*.</span></span> <span data-ttu-id="9688c-179">Öngörüler aynı anda birden çok iş parçacığı ile gerçekleştirmek istiyorsanız, iş parçacığı başına bir tahmin işlevi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9688c-179">If you want to conduct predictions simultaneously with multiple threads, you need to have a prediction function per thread.</span></span>
