---
title: Bir modeli yeniden eğitme
description: Bilgi ML.NET modelinde nasıl yeniden eğitme
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 552698c02a7846db588822fa68d094dece160ea0
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063558"
---
# <a name="re-train-a-model"></a><span data-ttu-id="fbcc1-103">Bir modeli yeniden eğitme</span><span class="sxs-lookup"><span data-stu-id="fbcc1-103">Re-train a model</span></span>

<span data-ttu-id="fbcc1-104">Bir machine learning modeli ML.NET olarak yeniden eğitme hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="fbcc1-104">Learn how to retrain a machine learning model in ML.NET.</span></span>

<span data-ttu-id="fbcc1-105">Dünya ve verileri çevresinde sabit bir hızda değiştirin.</span><span class="sxs-lookup"><span data-stu-id="fbcc1-105">The world and the data around it change at a constant pace.</span></span> <span data-ttu-id="fbcc1-106">Bu nedenle, modelleri değiştirmek ve güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fbcc1-106">As such, models need to change and update as well.</span></span> <span data-ttu-id="fbcc1-107">ML.NET işlevselliğini kullanarak yeniden eğitim modelleri için sürekli olarak önceki deneyime yerine her zaman sıfırdan oluşturmak için bir başlangıç noktası olarak model parametreleri öğrendiniz sağlar.</span><span class="sxs-lookup"><span data-stu-id="fbcc1-107">ML.NET provides functionality for re-training models using learned model parameters as a starting point to continually build on previous experience rather than starting from scratch every time.</span></span>  

<span data-ttu-id="fbcc1-108">Aşağıdaki algoritmaları ML.NET içinde yeniden trainable şunlardır:</span><span class="sxs-lookup"><span data-stu-id="fbcc1-108">The following algorithms are re-trainable in ML.NET:</span></span>

- [<span data-ttu-id="fbcc1-109">AveragedPerceptronTrainer</span><span class="sxs-lookup"><span data-stu-id="fbcc1-109">AveragedPerceptronTrainer</span></span>](xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer)
- [<span data-ttu-id="fbcc1-110">FieldAwareFactorizationMachineTrainer</span><span class="sxs-lookup"><span data-stu-id="fbcc1-110">FieldAwareFactorizationMachineTrainer</span></span>](xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer)
- [<span data-ttu-id="fbcc1-111">LbfgsLogisticRegressionBinaryTrainer</span><span class="sxs-lookup"><span data-stu-id="fbcc1-111">LbfgsLogisticRegressionBinaryTrainer</span></span>](xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer)
- [<span data-ttu-id="fbcc1-112">LbfgsMaximumEntropyMulticlassTrainer</span><span class="sxs-lookup"><span data-stu-id="fbcc1-112">LbfgsMaximumEntropyMulticlassTrainer</span></span>](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer)
- [<span data-ttu-id="fbcc1-113">LbfgsPoissonRegressionTrainer</span><span class="sxs-lookup"><span data-stu-id="fbcc1-113">LbfgsPoissonRegressionTrainer</span></span>](xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer)
- [<span data-ttu-id="fbcc1-114">LinearSvmTrainer</span><span class="sxs-lookup"><span data-stu-id="fbcc1-114">LinearSvmTrainer</span></span>](xref:Microsoft.ML.Trainers.LinearSvmTrainer)
- [<span data-ttu-id="fbcc1-115">OnlineGradientDescentTrainer</span><span class="sxs-lookup"><span data-stu-id="fbcc1-115">OnlineGradientDescentTrainer</span></span>](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer)
- [<span data-ttu-id="fbcc1-116">SgdCalibratedTrainer</span><span class="sxs-lookup"><span data-stu-id="fbcc1-116">SgdCalibratedTrainer</span></span>](xref:Microsoft.ML.Trainers.SgdCalibratedTrainer)
- [<span data-ttu-id="fbcc1-117">SgdNonCalibratedTrainer</span><span class="sxs-lookup"><span data-stu-id="fbcc1-117">SgdNonCalibratedTrainer</span></span>](xref:Microsoft.ML.Trainers.SgdNonCalibratedTrainer)
- [<span data-ttu-id="fbcc1-118">SymbolicSgdLogisticRegressionBinaryTrainer</span><span class="sxs-lookup"><span data-stu-id="fbcc1-118">SymbolicSgdLogisticRegressionBinaryTrainer</span></span>](xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer)

## <a name="load-pre-trained-model"></a><span data-ttu-id="fbcc1-119">Önceden eğitilmiş model yükle</span><span class="sxs-lookup"><span data-stu-id="fbcc1-119">Load pre-trained model</span></span>

<span data-ttu-id="fbcc1-120">İlk olarak, önceden eğitilmiş modelin uygulamanıza yükleyin.</span><span class="sxs-lookup"><span data-stu-id="fbcc1-120">First, load the pre-trained model into your application.</span></span> <span data-ttu-id="fbcc1-121">Yükleme eğitim işlem hatlarını ve modelleri hakkında daha fazla bilgi için bkz ilgili [nasıl yapılır makalesi](./consuming-model-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="fbcc1-121">To learn more about loading training pipelines and models, see the related [how-to article](./consuming-model-ml-net.md).</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define DataViewSchema of data prep pipeline and trained model
DataViewSchema dataPrepPipelineSchema, modelSchema;

// Load data prepration pipeline
ITransformer dataPrepPipeline = mlContext.Model.Load("data_preparation_pipeline.zip", out dataPrepPipelineSchema);

// Load trained model
ITransformer trainedModel = mlContext.Model.Load("ogd_model.zip", out modelSchema);
```

## <a name="extract-pre-trained-model-parameters"></a><span data-ttu-id="fbcc1-122">Önceden eğitilmiş model parametreleri Ayıkla</span><span class="sxs-lookup"><span data-stu-id="fbcc1-122">Extract pre-trained model parameters</span></span>

<span data-ttu-id="fbcc1-123">Modele yüklendiğinde erişerek öğrenilen model parametreleri Ayıkla [ `Model` ](xref:Microsoft.ML.Data.PredictionTransformerBase`1.Model*) önceden eğitilmiş modelin özelliği.</span><span class="sxs-lookup"><span data-stu-id="fbcc1-123">Once the model is loaded, extract the learned model parameters by accessing the [`Model`](xref:Microsoft.ML.Data.PredictionTransformerBase`1.Model*) property of the pre-trained model.</span></span> <span data-ttu-id="fbcc1-124">Önceden eğitilmiş model doğrusal regresyon modeli kullanılarak eğitilmiş [ `OnlineGradientDescentTrainer` ](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer) oluşturan bir[ `RegressionPredictionTransformer` ](xref:Microsoft.ML.Data.RegressionPredictionTransformer`1) , çıkarır [ `LinearRegressionModelParameters` ](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters).</span><span class="sxs-lookup"><span data-stu-id="fbcc1-124">The pre-trained model was trained using the linear regression model [`OnlineGradientDescentTrainer`](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer) which creates a[`RegressionPredictionTransformer`](xref:Microsoft.ML.Data.RegressionPredictionTransformer`1) that outputs [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters).</span></span> <span data-ttu-id="fbcc1-125">Bu doğrusal regresyon modeli parametreleri öğrenilen sapması ve ağırlıklarını veya modelin katsayılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="fbcc1-125">These linear regression model parameters contain the learned bias and weights or coefficients of the model.</span></span> <span data-ttu-id="fbcc1-126">Bu değerler, yeni yeniden eğitim modeli için bir başlangıç noktası olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fbcc1-126">These values will be used as a starting point for the new re-trained model.</span></span>

```csharp
// Extract trained model parameters
LinearRegressionModelParameters originalModelParameters = 
    ((ISingleFeaturePredictionTransformer<object>)trainedModel).Model as LinearRegressionModelParameters;
```

## <a name="re-train-model"></a><span data-ttu-id="fbcc1-127">Modeli yeniden eğitme</span><span class="sxs-lookup"><span data-stu-id="fbcc1-127">Re-train model</span></span>

<span data-ttu-id="fbcc1-128">Bir modeli yeniden eğitme işlemi farklı bir model Eğitimi, değildir.</span><span class="sxs-lookup"><span data-stu-id="fbcc1-128">The process for retraining a model is no different than that of training a model.</span></span> <span data-ttu-id="fbcc1-129">Tek fark, [ `Fit` ](xref:Microsoft.ML.Trainers.OnlineLinearTrainer`2.Fit*) verilerin yanı sıra yöntemi de alır giriş özgün öğrenilen model parametreleri ve yeniden eğitim işlemde olarak başlangıç noktası kullanır.</span><span class="sxs-lookup"><span data-stu-id="fbcc1-129">The only difference is, the [`Fit`](xref:Microsoft.ML.Trainers.OnlineLinearTrainer`2.Fit*) method in addition to the data also takes as input the original learned model parameters and uses them as a starting point in the re-training process.</span></span>  

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

## <a name="compare-model-parameters"></a><span data-ttu-id="fbcc1-130">Model parametreleri karşılaştırın</span><span class="sxs-lookup"><span data-stu-id="fbcc1-130">Compare model parameters</span></span>

<span data-ttu-id="fbcc1-131">Eğitim yeniden gerçekten oldu, nasıl bilebilirsiniz?</span><span class="sxs-lookup"><span data-stu-id="fbcc1-131">How do you know if re-training actually happened?</span></span> <span data-ttu-id="fbcc1-132">Bir yolu, yeniden eğitilen modelin parametreleri özgün modeli farklı olup olmadığını Karşılaştırılacak olacaktır.</span><span class="sxs-lookup"><span data-stu-id="fbcc1-132">One way would be to compare whether the re-trained model's parameters are different than those of the original model.</span></span> <span data-ttu-id="fbcc1-133">Aşağıdaki kod örneği, orijinal yeniden eğitilen model ağırlıkları karşı karşılaştırır ve bunları konsola çıkarır.</span><span class="sxs-lookup"><span data-stu-id="fbcc1-133">The code sample below compares the original against the re-trained model weights and outputs them to the console.</span></span>

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

<span data-ttu-id="fbcc1-134">Aşağıdaki tabloda, çıktı aşağıdaki gibi görünmelidir gösterir.</span><span class="sxs-lookup"><span data-stu-id="fbcc1-134">The table below shows what the output might look like.</span></span> 

|<span data-ttu-id="fbcc1-135">Özgün</span><span class="sxs-lookup"><span data-stu-id="fbcc1-135">Original</span></span> | <span data-ttu-id="fbcc1-136">Retrained</span><span class="sxs-lookup"><span data-stu-id="fbcc1-136">Retrained</span></span> | <span data-ttu-id="fbcc1-137">Fark</span><span class="sxs-lookup"><span data-stu-id="fbcc1-137">Difference</span></span> |
|---|---|---|
| <span data-ttu-id="fbcc1-138">33039.86</span><span class="sxs-lookup"><span data-stu-id="fbcc1-138">33039.86</span></span> | <span data-ttu-id="fbcc1-139">56293.76</span><span class="sxs-lookup"><span data-stu-id="fbcc1-139">56293.76</span></span> | <span data-ttu-id="fbcc1-140">-23253.9</span><span class="sxs-lookup"><span data-stu-id="fbcc1-140">-23253.9</span></span> |
| <span data-ttu-id="fbcc1-141">29099.14</span><span class="sxs-lookup"><span data-stu-id="fbcc1-141">29099.14</span></span> | <span data-ttu-id="fbcc1-142">49586.03</span><span class="sxs-lookup"><span data-stu-id="fbcc1-142">49586.03</span></span> | <span data-ttu-id="fbcc1-143">-20486.89</span><span class="sxs-lookup"><span data-stu-id="fbcc1-143">-20486.89</span></span> |
| <span data-ttu-id="fbcc1-144">28938.38</span><span class="sxs-lookup"><span data-stu-id="fbcc1-144">28938.38</span></span> | <span data-ttu-id="fbcc1-145">48609.23</span><span class="sxs-lookup"><span data-stu-id="fbcc1-145">48609.23</span></span> | <span data-ttu-id="fbcc1-146">-19670.85</span><span class="sxs-lookup"><span data-stu-id="fbcc1-146">-19670.85</span></span> |
| <span data-ttu-id="fbcc1-147">30484.02</span><span class="sxs-lookup"><span data-stu-id="fbcc1-147">30484.02</span></span> | <span data-ttu-id="fbcc1-148">53745.43</span><span class="sxs-lookup"><span data-stu-id="fbcc1-148">53745.43</span></span> | <span data-ttu-id="fbcc1-149">-23261.41</span><span class="sxs-lookup"><span data-stu-id="fbcc1-149">-23261.41</span></span> |
