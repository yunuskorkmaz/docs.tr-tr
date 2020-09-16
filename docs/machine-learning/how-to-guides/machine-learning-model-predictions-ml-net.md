---
title: Eğitilen bir modelle tahminlere sahip olun
description: Eğitilen bir model kullanarak tahminleri yapmayı öğrenin
ms.date: 09/18/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 2e8263db289bed50e7437b695134458b8c07e0e5
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679579"
---
# <a name="make-predictions-with-a-trained-model"></a><span data-ttu-id="d14ab-103">Eğitilen bir modelle tahminlere sahip olun</span><span class="sxs-lookup"><span data-stu-id="d14ab-103">Make predictions with a trained model</span></span>

<span data-ttu-id="d14ab-104">Öngörüler yapmak için eğitilen bir model kullanmayı öğrenin</span><span class="sxs-lookup"><span data-stu-id="d14ab-104">Learn how to use a trained model to make predictions</span></span>

## <a name="create-data-models"></a><span data-ttu-id="d14ab-105">Veri modelleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="d14ab-105">Create data models</span></span>

### <a name="input-data"></a><span data-ttu-id="d14ab-106">Giriş verileri</span><span class="sxs-lookup"><span data-stu-id="d14ab-106">Input data</span></span>

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

### <a name="output-data"></a><span data-ttu-id="d14ab-107">Çıktı verileri</span><span class="sxs-lookup"><span data-stu-id="d14ab-107">Output data</span></span>

<span data-ttu-id="d14ab-108">`Features`Ve `Label` giriş sütunu adları gibi ml.net, bir model tarafından üretilen tahmin edilen değer sütunlarının varsayılan adlarına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d14ab-108">Like the `Features` and `Label` input column names, ML.NET has default names for the predicted value columns produced by a model.</span></span> <span data-ttu-id="d14ab-109">Göreve bağlı olarak, ad farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="d14ab-109">Depending on the task the name may differ.</span></span>

<span data-ttu-id="d14ab-110">Bu örnekte kullanılan algoritma bir doğrusal regresyon algoritması olduğundan, çıkış sütununun varsayılan adı, `Score` [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) özelliğindeki özniteliği tarafından tanımlanır `PredictedPrice` .</span><span class="sxs-lookup"><span data-stu-id="d14ab-110">Because the algorithm used in this sample is a linear regression algorithm, the default name of the output column is `Score` which is defined by the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute on the `PredictedPrice` property.</span></span>

```csharp
class HousingPrediction
{
    [ColumnName("Score")]
    public float PredictedPrice { get; set; }
}
```

## <a name="set-up-a-prediction-pipeline"></a><span data-ttu-id="d14ab-111">Tahmin işlem hattı ayarlama</span><span class="sxs-lookup"><span data-stu-id="d14ab-111">Set up a prediction pipeline</span></span>

<span data-ttu-id="d14ab-112">Tek veya toplu bir tahmin yapılıp yapılmayacağını belirtir, tahmin işlem hattının uygulamaya yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d14ab-112">Whether making a single or batch prediction, the prediction pipeline needs to be loaded into the application.</span></span> <span data-ttu-id="d14ab-113">Bu işlem hattı hem veri ön işleme dönüştürmelerini hem de eğitilen modeli içerir.</span><span class="sxs-lookup"><span data-stu-id="d14ab-113">This pipeline contains both the data pre-processing transformations as well as the trained model.</span></span> <span data-ttu-id="d14ab-114">Aşağıdaki kod parçacığı, adlı bir dosyadan tahmin işlem hattını yükler `model.zip` .</span><span class="sxs-lookup"><span data-stu-id="d14ab-114">The code snippet below loads the prediction pipeline from a file named `model.zip`.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Load Trained Model
DataViewSchema predictionPipelineSchema;
ITransformer predictionPipeline = mlContext.Model.Load("model.zip", out predictionPipelineSchema);
```

## <a name="single-prediction"></a><span data-ttu-id="d14ab-115">Tek tahmin</span><span class="sxs-lookup"><span data-stu-id="d14ab-115">Single prediction</span></span>

<span data-ttu-id="d14ab-116">Tek bir tahmin yapmak için, yüklenmiş tahmin işlem hattını kullanarak bir oluşturun [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) .</span><span class="sxs-lookup"><span data-stu-id="d14ab-116">To make a single prediction, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) using the loaded prediction pipeline.</span></span>

```csharp
// Create PredictionEngines
PredictionEngine<HousingData, HousingPrediction> predictionEngine = mlContext.Model.CreatePredictionEngine<HousingData, HousingPrediction>(predictionPipeline);
```

<span data-ttu-id="d14ab-117">Ardından, yöntemini kullanın [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict%2A) ve giriş verilerinizi parametre olarak geçirin.</span><span class="sxs-lookup"><span data-stu-id="d14ab-117">Then, use the [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict%2A) method and pass in your input data as a parameter.</span></span> <span data-ttu-id="d14ab-118">[`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict%2A)Yöntemini kullanmanın girişin bir olması gerekmez [`IDataView`](xref:Microsoft.ML.IDataView) ).</span><span class="sxs-lookup"><span data-stu-id="d14ab-118">Notice that using the [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict%2A) method does not require the input to be an [`IDataView`](xref:Microsoft.ML.IDataView)).</span></span> <span data-ttu-id="d14ab-119">Bunun nedeni, girdi veri türünün bir nesnesini geçirebilmeniz için giriş veri türü işlemesini uygun bir şekilde iletmektir.</span><span class="sxs-lookup"><span data-stu-id="d14ab-119">This is because it conveniently internalizes the input data type manipulation so you can pass in an object of the input data type.</span></span> <span data-ttu-id="d14ab-120">Ayrıca, `CurrentPrice` yeni verileri kullanarak tahmin etmeye çalıştığınız hedef veya etiket olduğundan, bu, şu anda bunun için bir değer olmadığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="d14ab-120">Additionally, since `CurrentPrice` is the target or label you're trying to predict using new data, it's assumed there is no value for it at the moment.</span></span>

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

<span data-ttu-id="d14ab-121">`Score`Nesnenin özelliğine eriştiğinizde `prediction` Şuna benzer bir değer almalısınız `150079` .</span><span class="sxs-lookup"><span data-stu-id="d14ab-121">If you access the `Score` property of the `prediction` object, you should get a value similar to `150079`.</span></span>

## <a name="multiple-predictions"></a><span data-ttu-id="d14ab-122">Birden çok tahmin</span><span class="sxs-lookup"><span data-stu-id="d14ab-122">Multiple predictions</span></span>

<span data-ttu-id="d14ab-123">Aşağıdaki veriler verildiğinde, ' a yükleyin [`IDataView`](xref:Microsoft.ML.IDataView) .</span><span class="sxs-lookup"><span data-stu-id="d14ab-123">Given the following data, load it into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="d14ab-124">Bu durumda, öğesinin adı [`IDataView`](xref:Microsoft.ML.IDataView) `inputData` .</span><span class="sxs-lookup"><span data-stu-id="d14ab-124">In this case, the name of the [`IDataView`](xref:Microsoft.ML.IDataView) is `inputData`.</span></span> <span data-ttu-id="d14ab-125">`CurrentPrice`Yeni verileri kullanarak tahmin etmeye çalıştığınız hedef veya etiket olduğundan, bu, şu anda bunun için bir değer olmadığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="d14ab-125">Because `CurrentPrice` is the target or label you're trying to predict using new data, it's assumed there is no value for it at the moment.</span></span>

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

<span data-ttu-id="d14ab-126">Ardından, [`Transform`](xref:Microsoft.ML.ITransformer.Transform%2A) veri dönüşümlerini uygulamak ve tahmin oluşturmak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d14ab-126">Then, use the [`Transform`](xref:Microsoft.ML.ITransformer.Transform%2A) method to apply the data transformations and generate predictions.</span></span>

```csharp
// Predicted Data
IDataView predictions = predictionPipeline.Transform(inputData);
```

<span data-ttu-id="d14ab-127">Yöntemini kullanarak tahmin edilen değerleri inceleyin [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn%2A) .</span><span class="sxs-lookup"><span data-stu-id="d14ab-127">Inspect the predicted values by using the [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn%2A) method.</span></span>

```csharp
// Get Predictions
float[] scoreColumn = predictions.GetColumn<float>("Score").ToArray();
```

<span data-ttu-id="d14ab-128">Puan sütunundaki tahmin edilen değerler aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="d14ab-128">The predicted values in the score column should look like the following:</span></span>

| <span data-ttu-id="d14ab-129">Kümesinin</span><span class="sxs-lookup"><span data-stu-id="d14ab-129">Observation</span></span> | <span data-ttu-id="d14ab-130">Tahmin</span><span class="sxs-lookup"><span data-stu-id="d14ab-130">Prediction</span></span> |
|---|---|
| <span data-ttu-id="d14ab-131">1</span><span class="sxs-lookup"><span data-stu-id="d14ab-131">1</span></span> | <span data-ttu-id="d14ab-132">144638,2</span><span class="sxs-lookup"><span data-stu-id="d14ab-132">144638.2</span></span> |
| <span data-ttu-id="d14ab-133">2</span><span class="sxs-lookup"><span data-stu-id="d14ab-133">2</span></span> | <span data-ttu-id="d14ab-134">150079,4</span><span class="sxs-lookup"><span data-stu-id="d14ab-134">150079.4</span></span> |
| <span data-ttu-id="d14ab-135">3</span><span class="sxs-lookup"><span data-stu-id="d14ab-135">3</span></span> | <span data-ttu-id="d14ab-136">107789,8</span><span class="sxs-lookup"><span data-stu-id="d14ab-136">107789.8</span></span> |
