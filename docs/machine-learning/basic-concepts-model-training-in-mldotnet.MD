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
# <a name="basic-concepts-for-model-training-in-mlnet"></a>ML.NET eğitim modeli için temel kavramlar

Bu makalede kapsayan temel kavramları açıklar *model eğitim* ML.NET senaryolarda. Tüm kavramları daha basit bir senaryo için uygun olan *varolan modeli ile tahmini*.

## <a name="model-training-concepts"></a>Model eğitimi kavramları

Bu belge ML.NET modeli eğitimi ilgili aşağıdaki kavramları kapsar:

- [*Veri* ](#data) olarak temsil edilen bir `IDataView` arabirimi.
  - ML.NET verileri bir SQL görünümüne benzer: Bu bir gevşek Değerlendirilmiş, sabit, cursorable, heterojen, şema veri kümesi olur. 
  - Mükemmel bir belge veri arabirimi hakkında [IDataView tasarım ilkeleri](https://github.com/dotnet/machinelearning/blob/master/docs/code/IDataViewDesignPrinciples.md).
- [*Transformer* ](#transformer) olarak temsil edilen `ITransformer` arabirimi.
  - Bir veri alan bir bileşendir, bazı üzerinde çalışır ve dönüştürülen verilere yeni döndürür.
  - Örneğin, bir makine öğrenme modelinin özellikleri alır ve Öngörüler döndüren bir dönüştürücü düşünebilirsiniz.
  - Başka bir örnek metin simgeleştirici tek metin sütununu alır ve bir vektör sütun ayıklanan metinleri dışında kelimeler ile çıktı.
- [*Veri okuyucusu* ](#data-reader) olarak temsil edilen bir `IDataReader<T>` arabirimi.
  - Veri okuyucu verileri oluşturmak için ML.NET bileşendir. Örneğini alır `T` ve bu verileri döndürür. 
  - Örneğin, bir *TextLoader* olduğu bir `IDataReader<FileSource>`. Bu dosya kaynak alır ve veri üretir. 
- [*Tahmin* ](#estimator) olarak temsil edilen bir `IEstimator<T>` arabirimi.
  - Bu verilerden öğrenen bir nesnedir. Öğrenme sonucu bir *transformer*.
  - Bir machine learning, düşündüğünüz *algoritması* veri öğrenir ve bir machine learning üreten bir tahmin aracı olarak *model*.
- [*Tahmin işlevi* ](#prediction-function) olarak temsil edilen bir `PredictionFunction<TSrc, TDst>` sınıfı.
  - Tahmin işlevi uygulayan bir bir satır için gibi tahmin zaman makine olarak görülebilir.

## <a name="data"></a>Veri

ML.NET verileri bir SQL görünümüne benzer: Bu bir gevşek, değerlendirilir cursorable, heterojen, şema veri kümesi.

- Sahip *şema* (örneği bir `ISchema` arabirimi), veri görünümü'nün sütunları hakkında bilgi içerir.
  - Her sütunun bir *adı*, *türü*ve isteğe bağlı bir dizi *meta verileri* ilişkili.
  - Sütunun *meta verileri* vektör sütun ve benzeri yuvası adları gibi bilgileri içerir. Başka bir satır meta temsil *veri* her sütun için benzersiz.
  - Bir veri görünümü kaynağıdır *imleçler*. SQL imleçlerin dikkate alın: Bir imleç kullanılabilir verileri bir kerede bir satır veri gezinir ve bir nesnedir.
  - Doğal olarak, veri gibi çok sayıda etkin imleçler gerektiği şekilde sağlayabilirsiniz. İmleçler veriyle sabit olduğundan, tamamen bağımsızdır.
  - İmleçler, genellikle yalnızca bir sütun alt kümesi erişebilirsiniz: Verimlilik için yalnızca imleci tarafından gerekli olan sütunların değerlerini ML.NET hesaplar.

## <a name="transformer"></a>Transformer

Bir dönüştürücü veri alan bir bileşendir, bazı üzerinde çalışmak ve yeni dönüştürülmüş verileri döndürür.

ML.NET içinde çoğu dönüştürücüler birinde çalışan eğilimindedir *giriş sütununu* zamanda ve üretim *çıktı sütunu*. Örneğin, bir `new HashTransformer("foo", "bar")` değerleri alır "foo" sütununda, bunları karma ve bunları "çubuğu" sütuna yerleştirebilirsiniz. 

Giriş ve çıkış sütun adlarının aynı olduğunu yaygındır. Bu durumda, eski sütunu yenisiyle değiştirilir. Örneğin, bir `new HashTransformer("foo")` sütun "foo", "foo" bunları geri karma bunları ve put değerleri alır. 

Tüm transformer, doğal olarak, yeni bir veri görünümü zaman üretir `Transform` çağrılır. Veri görünümleri sabittir unutmayın.

Veri gevşek değerlendirilir, başka bir önemli konu, çünkü *dönüştürücüler yavaş çok*. Aslında, sonra çağırın

```csharp
var newData = transformer.Transform(oldData)
```

gerçek bir hesaplama gerçekleşir. Yalnızca bir imleci aldığınızda `newData` ve başlangıç değeri kullanan `newData` çağırma `transformer` dönüştürme mantığını (ve hatta tek olması durumunda `transformer` söz konusu istenen sütunlar oluşturmak için gereklidir).

### <a name="transformer-chains"></a>Transformer zincirleri

Bir kullanışlı bir özellik olan *dönüştürücüler, sıralı bir uygulama olarak başka bir dönüştürücü tümcecik*:

```csharp
var fullTransformer = transformer1.Append(transformer2).Append(transformer3);
```

Bu özellik ML.NET yaygın olarak kullanılır: genellikle eğitim ML.NET modeli için tüm intents ve purposes, olan dönüştürücüler, zinciri olan bir *transformer*. 

## <a name="data-reader"></a>Veri okuyucusu

Veri okuyucu 'verileri oluşturmak için ' ML.NET bileşendir: örneğini alır `T` ve bu verileri döndürür.

Dikkat edilecek bir ilgi çekici bir veri Okuyucu için mevcut bir veri okuyucu bir dönüştürücü ekleyerek oluşturabilirsiniz özelliğidir. Bu şekilde dönüştürme davranış marketinden bir okuyucu olabilir:

```c#
var newReader = reader.Append(transformer1).Append(transformer2)
```

Veri gevşek değerlendirilir, başka bir benzerliği dönüştürücüler, olduğu *okuyucular yavaş*: yok (veya en az) gerçek 'okuma' olmuyor çağırdığınızda `dataReader.Read()`: yalnızca bir imleç elde edilen verileri ne zaman istenen yok Okuyucu çalışmaya başlayın.

## <a name="estimator"></a>Tahmin aracı

*Estimator* verilerden öğrenir bir nesnedir. Öğrenme sonucu bir *transformer*.

ML.NET içinde farklı estimators zincir learning işlem hatlarını oluşturmak için bu özelliği kullanın:

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

Estimators önemli bir özellik olan *estimators eager, olmayan yavaş*: yapılan her çağrı `Fit` olası zaman alıcı bir işlem olan meydana gelmesine öğrenme neden oluyor.

## <a name="prediction-function"></a>Tahmin işlevi

Tahmin işlevi bir satır için bir dönüştürücü geçerli makine olarak görülebilir.

Model aldıktan sonra (bir *transformer* aracılığıyla ya da eğitim `Fit()`, veya bir yere gelen yüklü), normal çağrıları kullanarak tahminlerde bulunmayı kullanabilirsiniz `model.Transform(data)`. Ancak, gerçek zamanlı konuşmaların senaryoda bu modeli kullandığınızda, genellikle şirket tahmin etmek için birçok örneği yok. Bunun yerine, bir örnek aynı anda sahip ve zamanında bunlar üzerinde hemen tahminlerde gerekir.

Elbette, bunu batch tahmin azaltabilirsiniz:

- Veri Görünümü ile tam olarak bir satır oluşturun.
- Çağrı `model.Transform(data)` tahmin edilen veriler bir görünüm elde edin.
- Sonuçta elde edilen veriler üzerinde bir imleç alın.
- İlk (ve tek) satır almak için İmleç bir adım ilerleyin.
- Tahmin edilen değerler dışına ayıklayın.

Önceki algoritması kullanılarak uygulanabilir [şema kavramayı](https://github.com/dotnet/machinelearning/blob/master/docs/code/SchemaComprehension.md), iki kullanıcı tanımlı nesneler ile `InputExample` ve `OutputPrediction` şu şekilde:

```c#
var inputData = env.CreateDataView(new InputExample[] { example });
var outputData = model.Transform(inputData);
var output = outputData.AsDynamic.AsEnumerable<OutputPrediction>(env, reuseRowObject: false).Single();
```

Ancak bu yavaşlatan bir yöntemdir ve performans maliyetleri doğurur. Bunun yerine, tahmin işlev nesnesi aynı iş, ancak daha hızlı ve daha kolay, bir genişletme yöntemi aracılığıyla gerçekleştirir `MakePredictionFunction`:

```c#
var predictionFunc = model.MakePredictionFunction<InputExample, OutputPrediction>(env);
var output = predictionFunc.Predict(example);
```

Tahmin işlevi *değil a / iş parçacığı açısından güvenli*. Öngörüler aynı anda birden çok iş parçacığı ile gerçekleştirmek istiyorsanız, iş parçacığı başına bir tahmin işlevi olması gerekir.
