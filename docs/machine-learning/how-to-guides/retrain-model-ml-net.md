---
title: Modeli yeniden eğitme
description: Bilgi ML.NET modelinde nasıl yeniden eğitme
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 1628d0669d8a9e677ff39b5869d3802d89d96410
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67397709"
---
# <a name="re-train-a-model"></a><span data-ttu-id="e7c0f-103">Modeli yeniden eğitme</span><span class="sxs-lookup"><span data-stu-id="e7c0f-103">Re-train a model</span></span>

<span data-ttu-id="e7c0f-104">Bir machine learning modeli ML.NET olarak yeniden eğitme hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="e7c0f-104">Learn how to retrain a machine learning model in ML.NET.</span></span>

<span data-ttu-id="e7c0f-105">Dünya ve verileri çevresinde sabit bir hızda değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e7c0f-105">The world and the data around it change at a constant pace.</span></span> <span data-ttu-id="e7c0f-106">Bu nedenle, modelleri değiştirmek ve güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e7c0f-106">As such, models need to change and update as well.</span></span> <span data-ttu-id="e7c0f-107">ML.NET işlevselliğini kullanarak yeniden eğitim modelleri için sürekli olarak önceki deneyime yerine her zaman sıfırdan oluşturmak için bir başlangıç noktası olarak model parametreleri öğrendiniz sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7c0f-107">ML.NET provides functionality for re-training models using learned model parameters as a starting point to continually build on previous experience rather than starting from scratch every time.</span></span>  

<span data-ttu-id="e7c0f-108">Aşağıdaki algoritmaları ML.NET içinde yeniden trainable şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e7c0f-108">The following algorithms are re-trainable in ML.NET:</span></span>

- [<span data-ttu-id="e7c0f-109">AveragedPerceptronTrainer</span><span class="sxs-lookup"><span data-stu-id="e7c0f-109">AveragedPerceptronTrainer</span></span>](xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer)
- [<span data-ttu-id="e7c0f-110">FieldAwareFactorizationMachineTrainer</span><span class="sxs-lookup"><span data-stu-id="e7c0f-110">FieldAwareFactorizationMachineTrainer</span></span>](xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer)
- [<span data-ttu-id="e7c0f-111">LbfgsLogisticRegressionBinaryTrainer</span><span class="sxs-lookup"><span data-stu-id="e7c0f-111">LbfgsLogisticRegressionBinaryTrainer</span></span>](xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer)
- [<span data-ttu-id="e7c0f-112">LbfgsMaximumEntropyMulticlassTrainer</span><span class="sxs-lookup"><span data-stu-id="e7c0f-112">LbfgsMaximumEntropyMulticlassTrainer</span></span>](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer)
- [<span data-ttu-id="e7c0f-113">LbfgsPoissonRegressionTrainer</span><span class="sxs-lookup"><span data-stu-id="e7c0f-113">LbfgsPoissonRegressionTrainer</span></span>](xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer)
- [<span data-ttu-id="e7c0f-114">LinearSvmTrainer</span><span class="sxs-lookup"><span data-stu-id="e7c0f-114">LinearSvmTrainer</span></span>](xref:Microsoft.ML.Trainers.LinearSvmTrainer)
- [<span data-ttu-id="e7c0f-115">OnlineGradientDescentTrainer</span><span class="sxs-lookup"><span data-stu-id="e7c0f-115">OnlineGradientDescentTrainer</span></span>](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer)
- [<span data-ttu-id="e7c0f-116">SgdCalibratedTrainer</span><span class="sxs-lookup"><span data-stu-id="e7c0f-116">SgdCalibratedTrainer</span></span>](xref:Microsoft.ML.Trainers.SgdCalibratedTrainer)
- [<span data-ttu-id="e7c0f-117">SgdNonCalibratedTrainer</span><span class="sxs-lookup"><span data-stu-id="e7c0f-117">SgdNonCalibratedTrainer</span></span>](xref:Microsoft.ML.Trainers.SgdNonCalibratedTrainer)
- [<span data-ttu-id="e7c0f-118">SymbolicSgdLogisticRegressionBinaryTrainer</span><span class="sxs-lookup"><span data-stu-id="e7c0f-118">SymbolicSgdLogisticRegressionBinaryTrainer</span></span>](xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer)

## <a name="load-pre-trained-model"></a><span data-ttu-id="e7c0f-119">Önceden eğitilmiş model yükle</span><span class="sxs-lookup"><span data-stu-id="e7c0f-119">Load pre-trained model</span></span>

<span data-ttu-id="e7c0f-120">İlk olarak, önceden eğitilmiş modelin uygulamanıza yükleyin.</span><span class="sxs-lookup"><span data-stu-id="e7c0f-120">First, load the pre-trained model into your application.</span></span> <span data-ttu-id="e7c0f-121">Yükleme eğitim işlem hatlarını ve modelleri hakkında daha fazla bilgi için bkz ilgili [nasıl yapılır makalesi](./consuming-model-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="e7c0f-121">To learn more about loading training pipelines and models, see the related [how-to article](./consuming-model-ml-net.md).</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define DataViewSchema of data prep pipeline and trained model
DataViewSchema dataPrepPipelineSchema, modelSchema;

// Load data preparation pipeline
ITransformer dataPrepPipeline = mlContext.Model.Load("data_preparation_pipeline.zip", out dataPrepPipelineSchema);

// Load trained model
ITransformer trainedModel = mlContext.Model.Load("ogd_model.zip", out modelSchema);
```

## <a name="extract-pre-trained-model-parameters"></a><span data-ttu-id="e7c0f-122">Önceden eğitilmiş model parametreleri Ayıkla</span><span class="sxs-lookup"><span data-stu-id="e7c0f-122">Extract pre-trained model parameters</span></span>

<span data-ttu-id="e7c0f-123">Modele yüklendiğinde erişerek öğrenilen model parametreleri Ayıkla [ `Model` ](xref:Microsoft.ML.Data.PredictionTransformerBase`1.Model*) önceden eğitilmiş modelin özelliği.</span><span class="sxs-lookup"><span data-stu-id="e7c0f-123">Once the model is loaded, extract the learned model parameters by accessing the [`Model`](xref:Microsoft.ML.Data.PredictionTransformerBase`1.Model*) property of the pre-trained model.</span></span> <span data-ttu-id="e7c0f-124">Önceden eğitilmiş model doğrusal regresyon modeli kullanılarak eğitilmiş [ `OnlineGradientDescentTrainer` ](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer) oluşturan bir[ `RegressionPredictionTransformer` ](xref:Microsoft.ML.Data.RegressionPredictionTransformer%601) , çıkarır [ `LinearRegressionModelParameters` ](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters).</span><span class="sxs-lookup"><span data-stu-id="e7c0f-124">The pre-trained model was trained using the linear regression model [`OnlineGradientDescentTrainer`](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer) which creates a[`RegressionPredictionTransformer`](xref:Microsoft.ML.Data.RegressionPredictionTransformer%601) that outputs [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters).</span></span> <span data-ttu-id="e7c0f-125">Bu doğrusal regresyon modeli parametreleri öğrenilen sapması ve ağırlıklarını veya modelin katsayılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="e7c0f-125">These linear regression model parameters contain the learned bias and weights or coefficients of the model.</span></span> <span data-ttu-id="e7c0f-126">Bu değerler, yeni yeniden eğitim modeli için bir başlangıç noktası olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e7c0f-126">These values will be used as a starting point for the new re-trained model.</span></span>

```csharp
// Extract trained model parameters
LinearRegressionModelParameters originalModelParameters = 
    ((ISingleFeaturePredictionTransformer<object>)trainedModel).Model as LinearRegressionModelParameters;
```

## <a name="re-train-model"></a><span data-ttu-id="e7c0f-127">Modeli yeniden eğitme</span><span class="sxs-lookup"><span data-stu-id="e7c0f-127">Re-train model</span></span>

<span data-ttu-id="e7c0f-128">Bir modeli yeniden eğitme işlemi farklı bir model Eğitimi, değildir.</span><span class="sxs-lookup"><span data-stu-id="e7c0f-128">The process for retraining a model is no different than that of training a model.</span></span> <span data-ttu-id="e7c0f-129">Tek fark, [ `Fit` ](xref:Microsoft.ML.Trainers.OnlineLinearTrainer`2.Fit*) verilerin yanı sıra yöntemi de alır giriş özgün öğrenilen model parametreleri ve yeniden eğitim işlemde olarak başlangıç noktası kullanır.</span><span class="sxs-lookup"><span data-stu-id="e7c0f-129">The only difference is, the [`Fit`](xref:Microsoft.ML.Trainers.OnlineLinearTrainer`2.Fit*) method in addition to the data also takes as input the original learned model parameters and uses them as a starting point in the re-training process.</span></span>  

```csharp
// New Data
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f,175000f,210000f },
        CurrentPrice = 205000f
    },
    new HousingData
    {
        Size = 900f,
        HistoricalPrices = new float[] { 155000f, 190000f, 220000f },
        CurrentPrice = 210000f
    },
    new HousingData
    {
        Size = 550f,
        HistoricalPrices = new float[] { 99000f, 98000f, 130000f },
        CurrentPrice = 180000f
    }
};

//Load New Data
IDataView newData = mlContext.Data.LoadFromEnumerable<HousingData>(housingData);

// Preprocess Data
IDataView transformedNewData = dataPrepPipeline.Transform(newData);

// Retrain model
RegressionPredictionTransformer<LinearRegressionModelParameters> retrainedModel = 
    mlContext.Regression.Trainers.OnlineGradientDescent()
        .Fit(transformedNewData, originalModelParameters);
```

## <a name="compare-model-parameters"></a><span data-ttu-id="e7c0f-130">Model parametreleri karşılaştırın</span><span class="sxs-lookup"><span data-stu-id="e7c0f-130">Compare model parameters</span></span>

<span data-ttu-id="e7c0f-131">Eğitim yeniden gerçekten oldu, nasıl bilebilirsiniz?</span><span class="sxs-lookup"><span data-stu-id="e7c0f-131">How do you know if re-training actually happened?</span></span> <span data-ttu-id="e7c0f-132">Bir yolu, yeniden eğitilen modelin parametreleri özgün modeli farklı olup olmadığını Karşılaştırılacak olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e7c0f-132">One way would be to compare whether the re-trained model's parameters are different than those of the original model.</span></span> <span data-ttu-id="e7c0f-133">Aşağıdaki kod örneği, orijinal yeniden eğitilen model ağırlıkları karşı karşılaştırır ve bunları konsola çıkarır.</span><span class="sxs-lookup"><span data-stu-id="e7c0f-133">The code sample below compares the original against the re-trained model weights and outputs them to the console.</span></span>

```csharp
// Extract Model Parameters of re-trained model
LinearRegressionModelParameters retrainedModelParameters = retrainedModel.Model as LinearRegressionModelParameters;

// Inspect Change in Weights
var weightDiffs = 
    originalModelParameters.Weights.Zip(
        retrainedModelParameters.Weights, (original, retrained) => original - retrained).ToArray();

Console.WriteLine("Original | Retrained | Difference");
for(int i=0;i < weightDiffs.Count();i++)
{
    Console.WriteLine($"{originalModelParameters.Weights[i]} | {retrainedModelParameters.Weights[i]} | {weightDiffs[i]}");
}
```

<span data-ttu-id="e7c0f-134">Aşağıdaki tabloda, çıktı aşağıdaki gibi görünmelidir gösterir.</span><span class="sxs-lookup"><span data-stu-id="e7c0f-134">The table below shows what the output might look like.</span></span> 

|<span data-ttu-id="e7c0f-135">Özgün</span><span class="sxs-lookup"><span data-stu-id="e7c0f-135">Original</span></span> | <span data-ttu-id="e7c0f-136">Retrained</span><span class="sxs-lookup"><span data-stu-id="e7c0f-136">Retrained</span></span> | <span data-ttu-id="e7c0f-137">Fark</span><span class="sxs-lookup"><span data-stu-id="e7c0f-137">Difference</span></span> |
|---|---|---|
| <span data-ttu-id="e7c0f-138">33039.86</span><span class="sxs-lookup"><span data-stu-id="e7c0f-138">33039.86</span></span> | <span data-ttu-id="e7c0f-139">56293.76</span><span class="sxs-lookup"><span data-stu-id="e7c0f-139">56293.76</span></span> | <span data-ttu-id="e7c0f-140">-23253.9</span><span class="sxs-lookup"><span data-stu-id="e7c0f-140">-23253.9</span></span> |
| <span data-ttu-id="e7c0f-141">29099.14</span><span class="sxs-lookup"><span data-stu-id="e7c0f-141">29099.14</span></span> | <span data-ttu-id="e7c0f-142">49586.03</span><span class="sxs-lookup"><span data-stu-id="e7c0f-142">49586.03</span></span> | <span data-ttu-id="e7c0f-143">-20486.89</span><span class="sxs-lookup"><span data-stu-id="e7c0f-143">-20486.89</span></span> |
| <span data-ttu-id="e7c0f-144">28938.38</span><span class="sxs-lookup"><span data-stu-id="e7c0f-144">28938.38</span></span> | <span data-ttu-id="e7c0f-145">48609.23</span><span class="sxs-lookup"><span data-stu-id="e7c0f-145">48609.23</span></span> | <span data-ttu-id="e7c0f-146">-19670.85</span><span class="sxs-lookup"><span data-stu-id="e7c0f-146">-19670.85</span></span> |
| <span data-ttu-id="e7c0f-147">30484.02</span><span class="sxs-lookup"><span data-stu-id="e7c0f-147">30484.02</span></span> | <span data-ttu-id="e7c0f-148">53745.43</span><span class="sxs-lookup"><span data-stu-id="e7c0f-148">53745.43</span></span> | <span data-ttu-id="e7c0f-149">-23261.41</span><span class="sxs-lookup"><span data-stu-id="e7c0f-149">-23261.41</span></span> |
