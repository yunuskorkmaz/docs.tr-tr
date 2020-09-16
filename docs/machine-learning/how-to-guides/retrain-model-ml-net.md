---
title: Modeli yeniden eğitme
description: ML.NET içinde bir modeli yeniden eğitme hakkında bilgi edinin
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 1c891ad1d5b4c1160ca41c43eff6eea444f7224f
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545005"
---
# <a name="re-train-a-model"></a><span data-ttu-id="a555e-103">Modeli yeniden eğitme</span><span class="sxs-lookup"><span data-stu-id="a555e-103">Re-train a model</span></span>

<span data-ttu-id="a555e-104">ML.NET ' de makine öğrenimi modelini yeniden eğitme hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="a555e-104">Learn how to retrain a machine learning model in ML.NET.</span></span>

<span data-ttu-id="a555e-105">Dünya ve çevresindeki veriler sabit bir hızda değişir.</span><span class="sxs-lookup"><span data-stu-id="a555e-105">The world and the data around it change at a constant pace.</span></span> <span data-ttu-id="a555e-106">Bu nedenle, modellerin de değiştirilmesi ve güncelleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a555e-106">As such, models need to change and update as well.</span></span> <span data-ttu-id="a555e-107">ML.NET, bir başlangıç noktası olarak öğrenilmiş model parametrelerini kullanan yeniden eğitim modellerine, her seferinde sıfırdan başlamak yerine, bir önceki deneyime sürekli olarak derleme yapmak için işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="a555e-107">ML.NET provides functionality for re-training models using learned model parameters as a starting point to continually build on previous experience rather than starting from scratch every time.</span></span>

<span data-ttu-id="a555e-108">Aşağıdaki algoritmalar ML.NET içinde yeniden eğitiliyor:</span><span class="sxs-lookup"><span data-stu-id="a555e-108">The following algorithms are re-trainable in ML.NET:</span></span>

- [<span data-ttu-id="a555e-109">AveragedPerceptronTrainer</span><span class="sxs-lookup"><span data-stu-id="a555e-109">AveragedPerceptronTrainer</span></span>](xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer)
- [<span data-ttu-id="a555e-110">FieldAwareFactorizationMachineTrainer</span><span class="sxs-lookup"><span data-stu-id="a555e-110">FieldAwareFactorizationMachineTrainer</span></span>](xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer)
- [<span data-ttu-id="a555e-111">LbfgsLogisticRegressionBinaryTrainer</span><span class="sxs-lookup"><span data-stu-id="a555e-111">LbfgsLogisticRegressionBinaryTrainer</span></span>](xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer)
- [<span data-ttu-id="a555e-112">Lbfgsmaximumentropybirden çok Lasstrainer</span><span class="sxs-lookup"><span data-stu-id="a555e-112">LbfgsMaximumEntropyMulticlassTrainer</span></span>](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer)
- [<span data-ttu-id="a555e-113">Lbfgspoissongerilesiontrainer</span><span class="sxs-lookup"><span data-stu-id="a555e-113">LbfgsPoissonRegressionTrainer</span></span>](xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer)
- [<span data-ttu-id="a555e-114">Doğrsvmtrainer</span><span class="sxs-lookup"><span data-stu-id="a555e-114">LinearSvmTrainer</span></span>](xref:Microsoft.ML.Trainers.LinearSvmTrainer)
- [<span data-ttu-id="a555e-115">Onlinegradientharfin Ttrainer</span><span class="sxs-lookup"><span data-stu-id="a555e-115">OnlineGradientDescentTrainer</span></span>](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer)
- [<span data-ttu-id="a555e-116">Sgddtu Oytedtrainer</span><span class="sxs-lookup"><span data-stu-id="a555e-116">SgdCalibratedTrainer</span></span>](xref:Microsoft.ML.Trainers.SgdCalibratedTrainer)
- [<span data-ttu-id="a555e-117">Sgdnondtu ırtedtrainer</span><span class="sxs-lookup"><span data-stu-id="a555e-117">SgdNonCalibratedTrainer</span></span>](xref:Microsoft.ML.Trainers.SgdNonCalibratedTrainer)
- [<span data-ttu-id="a555e-118">SymbolicSgdLogisticRegressionBinaryTrainer</span><span class="sxs-lookup"><span data-stu-id="a555e-118">SymbolicSgdLogisticRegressionBinaryTrainer</span></span>](xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer)

## <a name="load-pre-trained-model"></a><span data-ttu-id="a555e-119">Önceden eğitilen modeli yükle</span><span class="sxs-lookup"><span data-stu-id="a555e-119">Load pre-trained model</span></span>

<span data-ttu-id="a555e-120">İlk olarak, önceden eğitilen modeli uygulamanıza yükleyin.</span><span class="sxs-lookup"><span data-stu-id="a555e-120">First, load the pre-trained model into your application.</span></span> <span data-ttu-id="a555e-121">Eğitim işlem hatlarını ve modellerini yükleme hakkında daha fazla bilgi edinmek için bkz. [eğitilen modeli kaydetme ve yükleme](save-load-machine-learning-models-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="a555e-121">To learn more about loading training pipelines and models, see [Save and load a trained model](save-load-machine-learning-models-ml-net.md).</span></span>

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

## <a name="extract-pre-trained-model-parameters"></a><span data-ttu-id="a555e-122">Önceden eğitilen model parametrelerini Ayıkla</span><span class="sxs-lookup"><span data-stu-id="a555e-122">Extract pre-trained model parameters</span></span>

<span data-ttu-id="a555e-123">Model yüklendikten sonra, [`Model`](xref:Microsoft.ML.Data.PredictionTransformerBase`1.Model*) önceden eğitilen modelin özelliğine erişerek öğrenilen model parametrelerini ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="a555e-123">Once the model is loaded, extract the learned model parameters by accessing the [`Model`](xref:Microsoft.ML.Data.PredictionTransformerBase`1.Model*) property of the pre-trained model.</span></span> <span data-ttu-id="a555e-124">Önceden eğitilen model, [`OnlineGradientDescentTrainer`](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer) Bu çıktıları oluşturan doğrusal regresyon modeli kullanılarak eğitildi [`RegressionPredictionTransformer`](xref:Microsoft.ML.Data.RegressionPredictionTransformer%601) [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) .</span><span class="sxs-lookup"><span data-stu-id="a555e-124">The pre-trained model was trained using the linear regression model [`OnlineGradientDescentTrainer`](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer) which creates a [`RegressionPredictionTransformer`](xref:Microsoft.ML.Data.RegressionPredictionTransformer%601) that outputs [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters).</span></span> <span data-ttu-id="a555e-125">Bu doğrusal regresyon modeli parametreleri, modelin öğrenilen sapma ve ağırlıklarını veya katsayılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="a555e-125">These linear regression model parameters contain the learned bias and weights or coefficients of the model.</span></span> <span data-ttu-id="a555e-126">Bu değerler, yeni yeniden eğitilen model için bir başlangıç noktası olarak kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="a555e-126">These values will be used as a starting point for the new re-trained model.</span></span>

```csharp
// Extract trained model parameters
LinearRegressionModelParameters originalModelParameters =
    ((ISingleFeaturePredictionTransformer<object>)trainedModel).Model as LinearRegressionModelParameters;
```

## <a name="re-train-model"></a><span data-ttu-id="a555e-127">Modeli yeniden eğitme</span><span class="sxs-lookup"><span data-stu-id="a555e-127">Re-train model</span></span>

<span data-ttu-id="a555e-128">Modeli yeniden eğitime işlemi, bir modelin eğitiminden farklı değildir.</span><span class="sxs-lookup"><span data-stu-id="a555e-128">The process for retraining a model is no different than that of training a model.</span></span> <span data-ttu-id="a555e-129">Tek fark, [`Fit`](xref:Microsoft.ML.Trainers.OnlineLinearTrainer`2.Fit*) verilerin yanı sıra özgün öğrenilen model parametrelerini giriş olarak da alır ve bunları yeniden eğitim sürecinde bir başlangıç noktası olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="a555e-129">The only difference is, the [`Fit`](xref:Microsoft.ML.Trainers.OnlineLinearTrainer`2.Fit*) method in addition to the data also takes as input the original learned model parameters and uses them as a starting point in the re-training process.</span></span>

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

## <a name="compare-model-parameters"></a><span data-ttu-id="a555e-130">Model parametrelerini Karşılaştır</span><span class="sxs-lookup"><span data-stu-id="a555e-130">Compare model parameters</span></span>

<span data-ttu-id="a555e-131">Yeniden eğitimin gerçekten gerçekleştiğini nasıl anlarsınız?</span><span class="sxs-lookup"><span data-stu-id="a555e-131">How do you know if re-training actually happened?</span></span> <span data-ttu-id="a555e-132">Bir yol, yeniden eğitilen model parametrelerinin orijinal modelden farklı olup olmadığını karşılaştırmak olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a555e-132">One way would be to compare whether the re-trained model's parameters are different than those of the original model.</span></span> <span data-ttu-id="a555e-133">Aşağıdaki kod örneği, orijinali yeniden eğitilen model ağırlıklarına karşı karşılaştırır ve bunları konsola çıkarır.</span><span class="sxs-lookup"><span data-stu-id="a555e-133">The code sample below compares the original against the re-trained model weights and outputs them to the console.</span></span>

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

<span data-ttu-id="a555e-134">Aşağıdaki tabloda çıktının nasıl görünebileceğini gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a555e-134">The table below shows what the output might look like.</span></span>

|<span data-ttu-id="a555e-135">Özgün</span><span class="sxs-lookup"><span data-stu-id="a555e-135">Original</span></span> | <span data-ttu-id="a555e-136">Eğitilebileceği</span><span class="sxs-lookup"><span data-stu-id="a555e-136">Retrained</span></span> | <span data-ttu-id="a555e-137">Fark</span><span class="sxs-lookup"><span data-stu-id="a555e-137">Difference</span></span> |
|---|---|---|
| <span data-ttu-id="a555e-138">33039,86</span><span class="sxs-lookup"><span data-stu-id="a555e-138">33039.86</span></span> | <span data-ttu-id="a555e-139">56293,76</span><span class="sxs-lookup"><span data-stu-id="a555e-139">56293.76</span></span> | <span data-ttu-id="a555e-140">-23253,9</span><span class="sxs-lookup"><span data-stu-id="a555e-140">-23253.9</span></span> |
| <span data-ttu-id="a555e-141">29099,14</span><span class="sxs-lookup"><span data-stu-id="a555e-141">29099.14</span></span> | <span data-ttu-id="a555e-142">49586,03</span><span class="sxs-lookup"><span data-stu-id="a555e-142">49586.03</span></span> | <span data-ttu-id="a555e-143">-20486,89</span><span class="sxs-lookup"><span data-stu-id="a555e-143">-20486.89</span></span> |
| <span data-ttu-id="a555e-144">28938,38</span><span class="sxs-lookup"><span data-stu-id="a555e-144">28938.38</span></span> | <span data-ttu-id="a555e-145">48609,23</span><span class="sxs-lookup"><span data-stu-id="a555e-145">48609.23</span></span> | <span data-ttu-id="a555e-146">-19670,85</span><span class="sxs-lookup"><span data-stu-id="a555e-146">-19670.85</span></span> |
| <span data-ttu-id="a555e-147">30484,02</span><span class="sxs-lookup"><span data-stu-id="a555e-147">30484.02</span></span> | <span data-ttu-id="a555e-148">53745,43</span><span class="sxs-lookup"><span data-stu-id="a555e-148">53745.43</span></span> | <span data-ttu-id="a555e-149">-23261,41</span><span class="sxs-lookup"><span data-stu-id="a555e-149">-23261.41</span></span> |
