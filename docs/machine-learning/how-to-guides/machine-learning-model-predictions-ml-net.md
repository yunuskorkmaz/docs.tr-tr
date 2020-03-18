---
title: Eğitimli bir modelle tahminlerde bulunun
description: Eğitimli bir modeli kullanarak öngörülerde bulunmayı öğrenin
ms.date: 09/18/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 182350cc5143155133385c6fd77986b271f6db91
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73977039"
---
# <a name="make-predictions-with-a-trained-model"></a><span data-ttu-id="87b7f-103">Eğitimli bir modelle tahminlerde bulunun</span><span class="sxs-lookup"><span data-stu-id="87b7f-103">Make predictions with a trained model</span></span>

<span data-ttu-id="87b7f-104">Öngörülerde bulunmak için eğitilmiş bir modeli nasıl kullanacağınızı öğrenin</span><span class="sxs-lookup"><span data-stu-id="87b7f-104">Learn how to use a trained model to make predictions</span></span>

## <a name="create-data-models"></a><span data-ttu-id="87b7f-105">Veri modelleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="87b7f-105">Create data models</span></span>

### <a name="input-data"></a><span data-ttu-id="87b7f-106">Giriş verileri</span><span class="sxs-lookup"><span data-stu-id="87b7f-106">Input data</span></span>

```csharp
public class HousingData
{
    [LoadColumn(0)]
    public float Size { get; set; }

    [LoadColumn(1, 3)]
    [VectorType(3)]
    public float[] HistoricalPrices { get; set; }

    [LoadColumn(4)]
    [ColumnName("Label")]
    public float CurrentPrice { get; set; }
}
```

### <a name="output-data"></a><span data-ttu-id="87b7f-107">Çıktı verileri</span><span class="sxs-lookup"><span data-stu-id="87b7f-107">Output data</span></span>

<span data-ttu-id="87b7f-108">`Features` Ve `Label` giriş sütun adları gibi, ML.NET bir model tarafından üretilen öngörülen değer sütunları için varsayılan adlara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="87b7f-108">Like the `Features` and `Label` input column names, ML.NET has default names for the predicted value columns produced by a model.</span></span> <span data-ttu-id="87b7f-109">Göreve bağlı olarak ad farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="87b7f-109">Depending on the task the name may differ.</span></span>

<span data-ttu-id="87b7f-110">Bu örnekte kullanılan algoritma doğrusal bir regresyon algoritması olduğundan, çıkış sütununun `Score` varsayılan adı [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) `PredictedPrice` özellikteki öznitelik tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="87b7f-110">Because the algorithm used in this sample is a linear regression algorithm, the default name of the output column is `Score` which is defined by the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute on the `PredictedPrice` property.</span></span>

```csharp
class HousingPrediction
{
    [ColumnName("Score")]
    public float PredictedPrice { get; set; }
}
```

## <a name="set-up-a-prediction-pipeline"></a><span data-ttu-id="87b7f-111">Tahmin ardışık bir dizi ayar</span><span class="sxs-lookup"><span data-stu-id="87b7f-111">Set up a prediction pipeline</span></span>

<span data-ttu-id="87b7f-112">İster tek bir ister toplu tahmin de bulunun, tahmin ardışık alanının uygulamaya yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="87b7f-112">Whether making a single or batch prediction, the prediction pipeline needs to be loaded into the application.</span></span> <span data-ttu-id="87b7f-113">Bu ardışık işlem, hem veri ön işleme dönüşümlerini hem de eğitilmiş modeli içerir.</span><span class="sxs-lookup"><span data-stu-id="87b7f-113">This pipeline contains both the data pre-processing transformations as well as the trained model.</span></span> <span data-ttu-id="87b7f-114">Aşağıdaki kod parçacığı, tahmin ardışık hattını . `model.zip`adlı bir dosyadan yükler.</span><span class="sxs-lookup"><span data-stu-id="87b7f-114">The code snippet below loads the prediction pipeline from a file named `model.zip`.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Load Trained Model
DataViewSchema predictionPipelineSchema;
ITransformer predictionPipeline = mlContext.Model.Load("model.zip", out predictionPipelineSchema);
```

## <a name="single-prediction"></a><span data-ttu-id="87b7f-115">Tek tahmin</span><span class="sxs-lookup"><span data-stu-id="87b7f-115">Single prediction</span></span>

<span data-ttu-id="87b7f-116">Tek bir tahmin yapmak [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) için yüklenen tahmin ardışık hattını kullanarak bir tahmin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="87b7f-116">To make a single prediction, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) using the loaded prediction pipeline.</span></span>

```csharp
// Create PredictionEngines
PredictionEngine<HousingData, HousingPrediction> predictionEngine = mlContext.Model.CreatePredictionEngine<HousingData, HousingPrediction>(predictionPipeline);
```

<span data-ttu-id="87b7f-117">Ardından, [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) yöntemi kullanın ve giriş verilerinizi parametre olarak geçirin.</span><span class="sxs-lookup"><span data-stu-id="87b7f-117">Then, use the [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) method and pass in your input data as a parameter.</span></span> <span data-ttu-id="87b7f-118">[`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) Yöntemi kullanarak giriş bir [`IDataView`](xref:Microsoft.ML.IDataView)olması gerekmez dikkat edin).</span><span class="sxs-lookup"><span data-stu-id="87b7f-118">Notice that using the [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) method does not require the input to be an [`IDataView`](xref:Microsoft.ML.IDataView)).</span></span> <span data-ttu-id="87b7f-119">Bunun nedeni, giriş veri türünden bir nesneye geçebilmeniz için giriş veri türü işlemesini uygun şekilde içselleştiren olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="87b7f-119">This is because it conveniently internalizes the input data type manipulation so you can pass in an object of the input data type.</span></span> <span data-ttu-id="87b7f-120">Ayrıca, `CurrentPrice` yeni veriler kullanarak tahmin etmeye çalıştığınız hedef veya etiket olduğundan, şu anda bunun için bir değer olmadığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="87b7f-120">Additionally, since `CurrentPrice` is the target or label you're trying to predict using new data, it's assumed there is no value for it at the moment.</span></span>

```csharp
// Input Data
HousingData inputData = new HousingData
{
    Size = 900f,
    HistoricalPrices = new float[] { 155000f, 190000f, 220000f }
};

// Get Prediction
HousingPrediction prediction = predictionEngine.Predict(inputData);
```

<span data-ttu-id="87b7f-121">Nesnenin özelliğine `Score` `prediction` erişiyorsanız, ''ye `150079`benzer bir değer almalısınız.</span><span class="sxs-lookup"><span data-stu-id="87b7f-121">If you access the `Score` property of the `prediction` object, you should get a value similar to `150079`.</span></span>

## <a name="multiple-predictions"></a><span data-ttu-id="87b7f-122">Birden çok tahmin</span><span class="sxs-lookup"><span data-stu-id="87b7f-122">Multiple predictions</span></span>

<span data-ttu-id="87b7f-123">Aşağıdaki veriler göz önüne alındığında, bir [`IDataView`](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="87b7f-123">Given the following data, load it into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="87b7f-124">Bu durumda, adı [`IDataView`](xref:Microsoft.ML.IDataView) . `inputData`</span><span class="sxs-lookup"><span data-stu-id="87b7f-124">In this case, the name of the [`IDataView`](xref:Microsoft.ML.IDataView) is `inputData`.</span></span> <span data-ttu-id="87b7f-125">Yeni `CurrentPrice` veriler kullanarak tahmin etmeye çalıştığınız hedef veya etiket olduğundan, şu anda bunun bir değeri olmadığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="87b7f-125">Because `CurrentPrice` is the target or label you're trying to predict using new data, it's assumed there is no value for it at the moment.</span></span>

```csharp
// Actual data
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f, 175000f, 210000f }
    },
    new HousingData
    {
        Size = 900f,
        HistoricalPrices = new float[] { 155000f, 190000f, 220000f }
    },
    new HousingData
    {
        Size = 550f,
        HistoricalPrices = new float[] { 99000f, 98000f, 130000f }
    }
};
```

<span data-ttu-id="87b7f-126">Ardından, veri [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) dönüşümlerini uygulamak ve öngörüler oluşturmak için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="87b7f-126">Then, use the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method to apply the data transformations and generate predictions.</span></span>

```csharp
// Predicted Data
IDataView predictions = predictionPipeline.Transform(inputData);
```

<span data-ttu-id="87b7f-127">[`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) Yöntemi kullanarak öngörülen değerleri inceleyin.</span><span class="sxs-lookup"><span data-stu-id="87b7f-127">Inspect the predicted values by using the [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) method.</span></span>

```csharp
// Get Predictions
float[] scoreColumn = predictions.GetColumn<float>("Score").ToArray();
```

<span data-ttu-id="87b7f-128">Puan sütununda öngörülen değerler aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="87b7f-128">The predicted values in the score column should look like the following:</span></span>

| <span data-ttu-id="87b7f-129">Gözlem</span><span class="sxs-lookup"><span data-stu-id="87b7f-129">Observation</span></span> | <span data-ttu-id="87b7f-130">Prediction (Tahmin)</span><span class="sxs-lookup"><span data-stu-id="87b7f-130">Prediction</span></span> |
|---|---|
| <span data-ttu-id="87b7f-131">1</span><span class="sxs-lookup"><span data-stu-id="87b7f-131">1</span></span> | <span data-ttu-id="87b7f-132">144638.2</span><span class="sxs-lookup"><span data-stu-id="87b7f-132">144638.2</span></span> |
| <span data-ttu-id="87b7f-133">2</span><span class="sxs-lookup"><span data-stu-id="87b7f-133">2</span></span> | <span data-ttu-id="87b7f-134">150079.4</span><span class="sxs-lookup"><span data-stu-id="87b7f-134">150079.4</span></span> |
| <span data-ttu-id="87b7f-135">3</span><span class="sxs-lookup"><span data-stu-id="87b7f-135">3</span></span> | <span data-ttu-id="87b7f-136">107789.8</span><span class="sxs-lookup"><span data-stu-id="87b7f-136">107789.8</span></span> |
