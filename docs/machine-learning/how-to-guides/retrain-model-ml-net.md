---
title: Modeli yeniden eğitme
description: ML.NET'da bir modeli nasıl yeniden eğitin
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 735782a4a0877a917b6e1885f009aa49d834170f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73976959"
---
# <a name="re-train-a-model"></a><span data-ttu-id="1f098-103">Modeli yeniden eğitme</span><span class="sxs-lookup"><span data-stu-id="1f098-103">Re-train a model</span></span>

<span data-ttu-id="1f098-104">ML.NET'da bir makine öğrenimi modelini nasıl yeniden eğitin.</span><span class="sxs-lookup"><span data-stu-id="1f098-104">Learn how to retrain a machine learning model in ML.NET.</span></span>

<span data-ttu-id="1f098-105">Dünya ve etrafındaki veriler sabit bir hızla değişir.</span><span class="sxs-lookup"><span data-stu-id="1f098-105">The world and the data around it change at a constant pace.</span></span> <span data-ttu-id="1f098-106">Bu nedenle, modellerin de değişmesi ve güncellendirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="1f098-106">As such, models need to change and update as well.</span></span> <span data-ttu-id="1f098-107">ML.NET, öğrenilen model parametrelerini kullanarak modelleri her seferinde sıfırdan başlamak yerine sürekli olarak önceki deneyimleri temel almak için bir başlangıç noktası olarak yeniden eğitme işlevleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f098-107">ML.NET provides functionality for re-training models using learned model parameters as a starting point to continually build on previous experience rather than starting from scratch every time.</span></span>

<span data-ttu-id="1f098-108">Aşağıdaki algoritmalar ML.NET yeniden eğitilebilir:</span><span class="sxs-lookup"><span data-stu-id="1f098-108">The following algorithms are re-trainable in ML.NET:</span></span>

- [<span data-ttu-id="1f098-109">OrtalamaPerceptronEğitmen</span><span class="sxs-lookup"><span data-stu-id="1f098-109">AveragedPerceptronTrainer</span></span>](xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer)
- [<span data-ttu-id="1f098-110">FieldAwareFactorizationMachineTrainer</span><span class="sxs-lookup"><span data-stu-id="1f098-110">FieldAwareFactorizationMachineTrainer</span></span>](xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer)
- [<span data-ttu-id="1f098-111">LbfgsLojistikRegressionBinaryTrainer</span><span class="sxs-lookup"><span data-stu-id="1f098-111">LbfgsLogisticRegressionBinaryTrainer</span></span>](xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer)
- [<span data-ttu-id="1f098-112">LbfgsMaximumEntropyMulticlassTrainer</span><span class="sxs-lookup"><span data-stu-id="1f098-112">LbfgsMaximumEntropyMulticlassTrainer</span></span>](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer)
- [<span data-ttu-id="1f098-113">LbfgsPoissonRegressionEğitmen</span><span class="sxs-lookup"><span data-stu-id="1f098-113">LbfgsPoissonRegressionTrainer</span></span>](xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer)
- [<span data-ttu-id="1f098-114">LinearSvmTrainer</span><span class="sxs-lookup"><span data-stu-id="1f098-114">LinearSvmTrainer</span></span>](xref:Microsoft.ML.Trainers.LinearSvmTrainer)
- [<span data-ttu-id="1f098-115">OnlineGradientDescentTrainer</span><span class="sxs-lookup"><span data-stu-id="1f098-115">OnlineGradientDescentTrainer</span></span>](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer)
- [<span data-ttu-id="1f098-116">SgdCalibratedTrainer</span><span class="sxs-lookup"><span data-stu-id="1f098-116">SgdCalibratedTrainer</span></span>](xref:Microsoft.ML.Trainers.SgdCalibratedTrainer)
- [<span data-ttu-id="1f098-117">SgdNonCalibratedTrainer</span><span class="sxs-lookup"><span data-stu-id="1f098-117">SgdNonCalibratedTrainer</span></span>](xref:Microsoft.ML.Trainers.SgdNonCalibratedTrainer)
- [<span data-ttu-id="1f098-118">SembolikSgdLojistikRegressionBinaryTrainer</span><span class="sxs-lookup"><span data-stu-id="1f098-118">SymbolicSgdLogisticRegressionBinaryTrainer</span></span>](xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer)

## <a name="load-pre-trained-model"></a><span data-ttu-id="1f098-119">Önceden eğitilmiş modeli yükleyin</span><span class="sxs-lookup"><span data-stu-id="1f098-119">Load pre-trained model</span></span>

<span data-ttu-id="1f098-120">İlk olarak, önceden eğitilmiş modeli uygulamanıza yükleyin.</span><span class="sxs-lookup"><span data-stu-id="1f098-120">First, load the pre-trained model into your application.</span></span> <span data-ttu-id="1f098-121">Eğitim boru hatlarını ve modellerini yükleme hakkında daha fazla bilgi edinmek [için, eğitilen bir modeli kaydet ve yükleyin'](save-load-machine-learning-models-ml-net.md)e bakın.</span><span class="sxs-lookup"><span data-stu-id="1f098-121">To learn more about loading training pipelines and models, see [Save and load a trained model](save-load-machine-learning-models-ml-net.md).</span></span>

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

## <a name="extract-pre-trained-model-parameters"></a><span data-ttu-id="1f098-122">Önceden eğitilmiş model parametrelerini ayıklayın</span><span class="sxs-lookup"><span data-stu-id="1f098-122">Extract pre-trained model parameters</span></span>

<span data-ttu-id="1f098-123">Model yüklendikten sonra, önceden eğitilmiş modelin [`Model`](xref:Microsoft.ML.Data.PredictionTransformerBase`1.Model*) özelliğine erişerek öğrenilen model parametrelerini ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="1f098-123">Once the model is loaded, extract the learned model parameters by accessing the [`Model`](xref:Microsoft.ML.Data.PredictionTransformerBase`1.Model*) property of the pre-trained model.</span></span> <span data-ttu-id="1f098-124">Önceden eğitilmiş model bir [`OnlineGradientDescentTrainer`](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer) [`RegressionPredictionTransformer`](xref:Microsoft.ML.Data.RegressionPredictionTransformer%601) oluşturur doğrusal regresyon modeli kullanılarak [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters)eğitildi.</span><span class="sxs-lookup"><span data-stu-id="1f098-124">The pre-trained model was trained using the linear regression model [`OnlineGradientDescentTrainer`](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer) which creates a[`RegressionPredictionTransformer`](xref:Microsoft.ML.Data.RegressionPredictionTransformer%601) that outputs [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters).</span></span> <span data-ttu-id="1f098-125">Bu doğrusal regresyon modeli parametreleri, modelin öğrenilen önyargıve ağırlıklarını veya katsayıları içerir.</span><span class="sxs-lookup"><span data-stu-id="1f098-125">These linear regression model parameters contain the learned bias and weights or coefficients of the model.</span></span> <span data-ttu-id="1f098-126">Bu değerler, yeni yeniden eğitilmiş model için bir başlangıç noktası olarak kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="1f098-126">These values will be used as a starting point for the new re-trained model.</span></span>

```csharp
// Extract trained model parameters
LinearRegressionModelParameters originalModelParameters =
    ((ISingleFeaturePredictionTransformer<object>)trainedModel).Model as LinearRegressionModelParameters;
```

## <a name="re-train-model"></a><span data-ttu-id="1f098-127">Yeniden eğitim modeli</span><span class="sxs-lookup"><span data-stu-id="1f098-127">Re-train model</span></span>

<span data-ttu-id="1f098-128">Bir modeli yeniden eğitme süreci, bir modeli eğitmekten farklı değildir.</span><span class="sxs-lookup"><span data-stu-id="1f098-128">The process for retraining a model is no different than that of training a model.</span></span> <span data-ttu-id="1f098-129">Tek fark, veri [`Fit`](xref:Microsoft.ML.Trainers.OnlineLinearTrainer`2.Fit*) ek olarak yöntem de giriş orijinal öğrenilen model parametreleri olarak alır ve yeniden eğitim sürecinde bir başlangıç noktası olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="1f098-129">The only difference is, the [`Fit`](xref:Microsoft.ML.Trainers.OnlineLinearTrainer`2.Fit*) method in addition to the data also takes as input the original learned model parameters and uses them as a starting point in the re-training process.</span></span>

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

## <a name="compare-model-parameters"></a><span data-ttu-id="1f098-130">Model parametrelerini karşılaştırın</span><span class="sxs-lookup"><span data-stu-id="1f098-130">Compare model parameters</span></span>

<span data-ttu-id="1f098-131">Yeniden eğitimin gerçekten olup olmadığını nasıl anlarsın?</span><span class="sxs-lookup"><span data-stu-id="1f098-131">How do you know if re-training actually happened?</span></span> <span data-ttu-id="1f098-132">Yeniden eğitilen modelin parametrelerinin orijinal modelden farklı olup olmadığını karşılaştırmanın bir yolu da bu olabilir.</span><span class="sxs-lookup"><span data-stu-id="1f098-132">One way would be to compare whether the re-trained model's parameters are different than those of the original model.</span></span> <span data-ttu-id="1f098-133">Aşağıdaki kod örneği orijinali yeniden eğitilmiş model ağırlıklarıyla karşılaştırır ve bunları konsola çıkar.</span><span class="sxs-lookup"><span data-stu-id="1f098-133">The code sample below compares the original against the re-trained model weights and outputs them to the console.</span></span>

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

<span data-ttu-id="1f098-134">Aşağıdaki tablo, çıktının nasıl görünebileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1f098-134">The table below shows what the output might look like.</span></span>

|<span data-ttu-id="1f098-135">Özgün</span><span class="sxs-lookup"><span data-stu-id="1f098-135">Original</span></span> | <span data-ttu-id="1f098-136">Yeniden eğitildi</span><span class="sxs-lookup"><span data-stu-id="1f098-136">Retrained</span></span> | <span data-ttu-id="1f098-137">Fark</span><span class="sxs-lookup"><span data-stu-id="1f098-137">Difference</span></span> |
|---|---|---|
| <span data-ttu-id="1f098-138">33039.86</span><span class="sxs-lookup"><span data-stu-id="1f098-138">33039.86</span></span> | <span data-ttu-id="1f098-139">56293.76</span><span class="sxs-lookup"><span data-stu-id="1f098-139">56293.76</span></span> | <span data-ttu-id="1f098-140">-23253.9</span><span class="sxs-lookup"><span data-stu-id="1f098-140">-23253.9</span></span> |
| <span data-ttu-id="1f098-141">29099.14</span><span class="sxs-lookup"><span data-stu-id="1f098-141">29099.14</span></span> | <span data-ttu-id="1f098-142">49586.03</span><span class="sxs-lookup"><span data-stu-id="1f098-142">49586.03</span></span> | <span data-ttu-id="1f098-143">-20486.89</span><span class="sxs-lookup"><span data-stu-id="1f098-143">-20486.89</span></span> |
| <span data-ttu-id="1f098-144">28938.38</span><span class="sxs-lookup"><span data-stu-id="1f098-144">28938.38</span></span> | <span data-ttu-id="1f098-145">48609.23</span><span class="sxs-lookup"><span data-stu-id="1f098-145">48609.23</span></span> | <span data-ttu-id="1f098-146">-19670.85</span><span class="sxs-lookup"><span data-stu-id="1f098-146">-19670.85</span></span> |
| <span data-ttu-id="1f098-147">30484.02</span><span class="sxs-lookup"><span data-stu-id="1f098-147">30484.02</span></span> | <span data-ttu-id="1f098-148">53745.43</span><span class="sxs-lookup"><span data-stu-id="1f098-148">53745.43</span></span> | <span data-ttu-id="1f098-149">-23261.41</span><span class="sxs-lookup"><span data-stu-id="1f098-149">-23261.41</span></span> |
