---
title: ML.NET eğitim modeli için temel kavramlar
description: Bu makalede kapsayan temel kavramları açıklar *model eğitim* ML.NET senaryolarda. Tüm kavramları daha basit bir senaryo için uygun olan *varolan modeli ile tahmini*.
ms.date: 03/05/2019
ms.topic: overview
ms.custom: mvc
ms.openlocfilehash: d29f6b901b0296f4d9a75b470a84dc087fb50e5d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59973843"
---
# <a name="basic-concepts-for-model-training-in-mlnet"></a>ML.NET eğitim modeli için temel kavramlar

Bu makalede kapsayan temel kavramları açıklar *model eğitim* ML.NET senaryolarda. Tüm kavramları daha basit bir senaryo için uygun olan *mevcut bir model ile tahmini*.

Bu makale ve ilgili örnek şu anda kullandığınız **ML.NET sürüm 0.10**. Daha fazla bilgi için bkz: adresindeki sürüm notlarını [dotnet/machinelearning GitHub deposunu](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).

## <a name="model-training-concepts"></a>Model eğitimi kavramları

Bu belge ML.NET modeli eğitimi ilgili aşağıdaki kavramları kapsar:

- [*Veri* ](#data) olarak temsil edilen bir `IDataView` arabirimi.
  - ML.NET verileri bir SQL görünümüne benzer: Bu bir gevşek Değerlendirilmiş, sabit, cursorable, heterojen, şema veri kümesi olur. 
  - Mükemmel bir belge veri arabirimi hakkında [IDataView tasarım ilkeleri](https://github.com/dotnet/machinelearning/blob/master/docs/code/IDataViewDesignPrinciples.md).
- [*Transformer* ](#transformer) olarak temsil edilen `ITransformer` arabirimi.
  - Bir veri alan bir bileşendir, bazı üzerinde çalışır ve dönüştürülen verilere yeni döndürür.
  - Örneğin, bir makine öğrenme modelinin özellikleri alır ve Öngörüler döndüren bir dönüştürücü düşünebilirsiniz.
  - Başka bir örnek metin simgeleştirici tek metin sütununu alır ve bir vektör sütun ayıklanan metinleri dışında kelimeler ile çıkarır.
- [*Veri okuyucusu* ](#data-reader) olarak temsil edilen bir `IDataReader<T>` arabirimi.
  - Veri okuyucu verileri oluşturmak için ML.NET bileşendir. Örneğini alır `T` ve bu verileri döndürür. 
  - Örneğin, bir *TextLoader* olduğu bir `IDataReader<IMultiStreamSource>`. Bu kaynak alır ve veri üretir. 
- [*Tahmin* ](#estimator) olarak temsil edilen bir `IEstimator<T>` arabirimi.
  - Bu verilerden öğrenen bir nesnedir. Öğrenme sonucu bir *transformer*.
  - Bir machine learning, düşündüğünüz *algoritması* veri öğrenir ve bir machine learning üreten bir tahmin aracı olarak *model*.
- [*Tahmin işlevi* ](#prediction-function) olarak temsil edilen bir `PredictionEngine<TSrc, TDst>` sınıfı.
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

Bir veri alan bir bileşendir, bazı üzerinde çalışır ve dönüştürülen verilere yeni döndürür.

ML.NET içinde çoğu dönüştürücüler birinde çalışan eğilimindedir *giriş sütununu* zamanda ve üretim *çıktı sütunu*. Örneğin, bir `new HashTransformer("bar", "foo")` sütun "foo" değerlerini alır, bunları karma hale getirir ve bunları "çubuğu" sütununa yerleştirir. 

Giriş ve çıkış sütun adlarının aynı olduğunu yaygındır. Bu durumda, eski sütunu yenisiyle değiştirilir. Örneğin, bir `new HashTransformer("foo")` "foo" bunları geri koyar sütun "foo" değerlerini alır ve bunları karma hale getirir. 

Herhangi bir dönüştürücü, yeni bir veri görünümü zaman üretir `Transform` çağrılır. Veri görünümleri sabittir unutmayın.

Veri gevşek değerlendirilir, başka bir önemli konu, çünkü *dönüştürücüler yavaş çok*. Aslında, sonra çağırın

```csharp
var newData = transformer.Transform(oldData)
```

gerçek bir hesaplama gerçekleşir. Yalnızca bir imleci aldığınızda `newData` ve başlangıç değeri kullanan `newData` çağırma `transformer` dönüştürme mantığını (ve hatta daha sonra yalnızca olur `transformer` söz konusu istenen sütunlar oluşturmak için gereklidir).

### <a name="transformer-chains"></a>Transformer zincirleri

Bir kullanışlı bir özellik olan *dönüştürücüler, sıralı bir uygulama olarak başka bir dönüştürücü oluşturabileceğinizi*:

```csharp
var fullTransformer = transformer1.Append(transformer2).Append(transformer3);
```

Bu özellik ML.NET yaygın olarak kullanılır: genellikle eğitim ML.NET modeli için tüm intents ve purposes, olan dönüştürücüler, zinciri olan bir *transformer*.

## <a name="data-reader"></a>Veri okuyucusu

Veri okuyucu 'verileri oluşturmak için ' bir ML.NET bileşendir: örneğini alır `T` ve bu verileri döndürür.

Dikkat edilecek bir ilgi çekici bir veri Okuyucu için mevcut bir veri okuyucu bir dönüştürücü ekleyerek oluşturabilirsiniz özelliğidir. Bu şekilde dönüştürme davranış marketinden bir okuyucu olabilir:

```csharp
var newReader = reader.Append(transformer1).Append(transformer2)
```

Veri gevşek değerlendirilir, başka bir benzerliği dönüştürücüler, olduğu *okuyucular yavaş*: yok (veya en az) gerçek 'okuma' olmuyor çağırdığınızda `reader.Read()`: yalnızca bir imleç elde edilen verileri ne zaman istenen yok Okuyucu çalışmaya başlayın.

## <a name="estimator"></a>Tahmin aracı

*Estimator* verilerden öğrenir bir nesnedir. Öğrenme sonucu bir *transformer*.

ML.NET içinde farklı estimators zincir learning işlem hatlarını oluşturmak için bu özelliği kullanın:

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

Estimators önemli bir özellik olan *estimators eager, olmayan yavaş*: yapılan her çağrı `Fit` olası zaman alıcı bir işlem olan meydana gelmesine öğrenme neden oluyor.

## <a name="prediction-function"></a>Tahmin işlevi

Tahmin işlevi bir satır için bir dönüştürücü uygulayan bir bileşen olarak görülebilir.

Model aldıktan sonra (bir *transformer* aracılığıyla ya da eğitim `Fit()`, veya bir yere gelen yüklü), normal çağrıları kullanarak tahminlerde bulunmayı kullanabilirsiniz `model.Transform(data)`. Ancak, gerçek zamanlı konuşmaların senaryoda bu modeli kullandığınızda, genellikle şirket tahmin etmek için birçok örneği yok. Bunun yerine, bir örnek aynı anda sahip ve zamanında bunlar üzerinde hemen tahminlerde gerekir.

Elbette, bunu batch tahmin azaltabilirsiniz:

- Veri Görünümü ile tam olarak bir satır oluşturun.
- Çağrı `model.Transform(data)` tahmin edilen veriler bir görünüm elde edin.
- Sonuçta elde edilen veriler üzerinde bir imleç alın.
- İlk (ve tek) satır almak için İmleç bir adım ilerleyin.
- Tahmin edilen değerler dışına ayıklayın.

Önceki algoritması kullanılarak uygulanabilir [şema kavramayı](https://github.com/dotnet/machinelearning/blob/master/docs/code/SchemaComprehension.md), iki kullanıcı tanımlı nesneler ile `InputExample` ve `OutputPrediction` şu şekilde:

```csharp
var inputData = mlContext.Data.ReadFromEnumerable(new InputExample[] { example });
var outputData = model.Transform(inputData);
var output = mlContext.CreateEnumerable<OutputPrediction>(outputData,reuseRowObject:false).First();
```

Ancak bu yavaşlatan bir yöntemdir ve performans maliyetleri doğurur. Bunun yerine, tahmin işlev nesnesi aynı iş, ancak daha hızlı ve daha kolay, bir genişletme yöntemi aracılığıyla gerçekleştirir `CreatePredictionEngine`:

```csharp
var predictionEngine = model.CreatePredictionEngine<InputExample,OutputPrediction>(mlContext);
var prediction = predictionEngine.Predict(example);
```

Tahmin işlevi *değil a / iş parçacığı açısından güvenli*. Öngörüler aynı anda birden çok iş parçacığı ile gerçekleştirmek istiyorsanız, iş parçacığı başına bir tahmin işlevi olması gerekir.
