---
title: Eğitilen bir modelle tahminlere sahip olun
description: Eğitilen bir model kullanarak tahminleri yapmayı öğrenin
ms.date: 09/18/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 33e0cb74342ca3e82ff5f108453d63e022d63d20
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71118021"
---
# <a name="make-predictions-with-a-trained-model"></a><span data-ttu-id="91e31-103">Eğitilen bir modelle tahminlere sahip olun</span><span class="sxs-lookup"><span data-stu-id="91e31-103">Make predictions with a trained model</span></span>

<span data-ttu-id="91e31-104">Öngörüler yapmak için eğitilen bir model kullanmayı öğrenin</span><span class="sxs-lookup"><span data-stu-id="91e31-104">Learn how to use a trained model to make predictions</span></span>

## <a name="create-data-models"></a><span data-ttu-id="91e31-105">Veri modelleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="91e31-105">Create data models</span></span>

### <a name="input-data"></a><span data-ttu-id="91e31-106">Giriş verileri</span><span class="sxs-lookup"><span data-stu-id="91e31-106">Input data</span></span>

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

### <a name="output-data"></a><span data-ttu-id="91e31-107">Çıktı verileri</span><span class="sxs-lookup"><span data-stu-id="91e31-107">Output data</span></span>

<span data-ttu-id="91e31-108">`Features` Ve`Label` giriş sütunu adları gibi ml.net, bir model tarafından üretilen tahmin edilen değer sütunlarının varsayılan adlarına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="91e31-108">Like the `Features` and `Label` input column names, ML.NET has default names for the predicted value columns produced by a model.</span></span> <span data-ttu-id="91e31-109">Göreve bağlı olarak, ad farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="91e31-109">Depending on the task the name may differ.</span></span>

<span data-ttu-id="91e31-110">Bu örnekte kullanılan algoritma bir doğrusal regresyon algoritması olduğundan, çıkış sütununun `Score` varsayılan adı, `PredictedPrice` özelliğindeki [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) özniteliği tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="91e31-110">Because the algorithm used in this sample is a linear regression algorithm, the default name of the output column is `Score` which is defined by the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute on the `PredictedPrice` property.</span></span>

```csharp
class HousingPrediction
{
    [ColumnName("Score")]
    public float PredictedPrice { get; set; }
}
```

## <a name="set-up-a-prediction-pipeline"></a><span data-ttu-id="91e31-111">Tahmin işlem hattı ayarlama</span><span class="sxs-lookup"><span data-stu-id="91e31-111">Set up a prediction pipeline</span></span>

<span data-ttu-id="91e31-112">Tek veya toplu bir tahmin yapılıp yapılmayacağını belirtir, tahmin işlem hattının uygulamaya yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="91e31-112">Whether making a single or batch prediction, the prediction pipeline needs to be loaded into the application.</span></span> <span data-ttu-id="91e31-113">Bu işlem hattı hem veri ön işleme dönüştürmelerini hem de eğitilen modeli içerir.</span><span class="sxs-lookup"><span data-stu-id="91e31-113">This pipeline contains both the data pre-processing transformations as well as the trained model.</span></span> <span data-ttu-id="91e31-114">Aşağıdaki kod parçacığı, adlı `model.zip`bir dosyadan tahmin işlem hattını yükler.</span><span class="sxs-lookup"><span data-stu-id="91e31-114">The code snippet below loads the prediction pipeline from a file named `model.zip`.</span></span>

```csharp
//Create MLContext 
MLContext mlContext = new MLContext();

// Load Trained Model
DataViewSchema predictionPipelineSchema;
ITransformer predictionPipeline = mlContext.Model.Load("model.zip", out predictionPipelineSchema);
```

## <a name="single-prediction"></a><span data-ttu-id="91e31-115">Tek tahmin</span><span class="sxs-lookup"><span data-stu-id="91e31-115">Single prediction</span></span>

<span data-ttu-id="91e31-116">Tek bir tahmin yapmak için, yüklenmiş tahmin [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) işlem hattını kullanarak bir oluşturun.</span><span class="sxs-lookup"><span data-stu-id="91e31-116">To make a single prediction, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) using the loaded prediction pipeline.</span></span>

```csharp
// Create PredictionEngines
PredictionEngine<HousingData, HousingPrediction> predictionEngine = mlContext.Model.CreatePredictionEngine<HousingData, HousingPrediction>(predictionPipeline);
```

<span data-ttu-id="91e31-117">Ardından, [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) yöntemini kullanın ve giriş verilerinizi parametre olarak geçirin.</span><span class="sxs-lookup"><span data-stu-id="91e31-117">Then, use the [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) method and pass in your input data as a parameter.</span></span> <span data-ttu-id="91e31-118">[`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) Yöntemini kullanmanın girişin bir [`IDataView`](xref:Microsoft.ML.IDataView)olması gerekmez).</span><span class="sxs-lookup"><span data-stu-id="91e31-118">Notice that using the [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) method does not require the input to be an [`IDataView`](xref:Microsoft.ML.IDataView)).</span></span> <span data-ttu-id="91e31-119">Bunun nedeni, girdi veri türünün bir nesnesini geçirebilmeniz için giriş veri türü işlemesini uygun bir şekilde iletmektir.</span><span class="sxs-lookup"><span data-stu-id="91e31-119">This is because it conveniently internalizes the input data type manipulation so you can pass in an object of the input data type.</span></span> <span data-ttu-id="91e31-120">Ayrıca, `CurrentPrice` yeni verileri kullanarak tahmin etmeye çalıştığınız hedef veya etiket olduğundan, bu, şu anda bunun için bir değer olmadığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="91e31-120">Additionally, since `CurrentPrice` is the target or label you're trying to predict using new data, it's assumed there is no value for it at the moment.</span></span>

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

<span data-ttu-id="91e31-121">Nesnenin özelliğine eriştiğinizde şuna benzer `150079`bir değer almalısınız. `Score` `prediction`</span><span class="sxs-lookup"><span data-stu-id="91e31-121">If you access the `Score` property of the `prediction` object, you should get a value similar to `150079`.</span></span>

## <a name="multiple-predictions"></a><span data-ttu-id="91e31-122">Birden çok tahmin</span><span class="sxs-lookup"><span data-stu-id="91e31-122">Multiple predictions</span></span>

<span data-ttu-id="91e31-123">Aşağıdaki veriler verildiğinde, ' a [`IDataView`](xref:Microsoft.ML.IDataView)yükleyin.</span><span class="sxs-lookup"><span data-stu-id="91e31-123">Given the following data, load it into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="91e31-124">Bu durumda, öğesinin [`IDataView`](xref:Microsoft.ML.IDataView) `inputData`adı.</span><span class="sxs-lookup"><span data-stu-id="91e31-124">In this case, the name of the [`IDataView`](xref:Microsoft.ML.IDataView) is `inputData`.</span></span> <span data-ttu-id="91e31-125">Yeni `CurrentPrice` verileri kullanarak tahmin etmeye çalıştığınız hedef veya etiket olduğundan, bu, şu anda bunun için bir değer olmadığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="91e31-125">Because `CurrentPrice` is the target or label you're trying to predict using new data, it's assumed there is no value for it at the moment.</span></span>

```csharp
// Actual data
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f,175000f,210000f }
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

<span data-ttu-id="91e31-126">Ardından, veri dönüşümlerini [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) uygulamak ve tahmin oluşturmak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="91e31-126">Then, use the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method to apply the data transformations and generate predictions.</span></span>

```csharp
// Predicted Data
IDataView predictions = predictionPipeline.Transform(inputData);
```

<span data-ttu-id="91e31-127">[`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) Yöntemini kullanarak tahmin edilen değerleri inceleyin.</span><span class="sxs-lookup"><span data-stu-id="91e31-127">Inspect the predicted values by using the [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) method.</span></span>

```csharp
// Get Predictions
float[] scoreColumn = predictions.GetColumn<float>("Score").ToArray();
```

<span data-ttu-id="91e31-128">Puan sütunundaki tahmin edilen değerler aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="91e31-128">The predicted values in the score column should look like the following:</span></span>

| <span data-ttu-id="91e31-129">Kümesinin</span><span class="sxs-lookup"><span data-stu-id="91e31-129">Observation</span></span> | <span data-ttu-id="91e31-130">Tahmin</span><span class="sxs-lookup"><span data-stu-id="91e31-130">Prediction</span></span> |
|---|---|
| <span data-ttu-id="91e31-131">1\.</span><span class="sxs-lookup"><span data-stu-id="91e31-131">1</span></span> | <span data-ttu-id="91e31-132">144638,2</span><span class="sxs-lookup"><span data-stu-id="91e31-132">144638.2</span></span> |
| <span data-ttu-id="91e31-133">2</span><span class="sxs-lookup"><span data-stu-id="91e31-133">2</span></span> | <span data-ttu-id="91e31-134">150079,4</span><span class="sxs-lookup"><span data-stu-id="91e31-134">150079.4</span></span> |
| <span data-ttu-id="91e31-135">3</span><span class="sxs-lookup"><span data-stu-id="91e31-135">3</span></span> | <span data-ttu-id="91e31-136">107789,8</span><span class="sxs-lookup"><span data-stu-id="91e31-136">107789.8</span></span> |
