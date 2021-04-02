---
title: ML.NET algoritması seçme
description: Machine Learning modeliniz için bir ML.NET algoritması seçme hakkında bilgi edinin
ms.topic: overview
ms.date: 03/31/2021
ms.openlocfilehash: c1a35f2b5b2ece2a846469f855e91b49887f0c90
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2021
ms.locfileid: "106122631"
---
# <a name="how-to-choose-an-mlnet-algorithm"></a><span data-ttu-id="7f539-103">ML.NET algoritması seçme</span><span class="sxs-lookup"><span data-stu-id="7f539-103">How to choose an ML.NET algorithm</span></span>

<span data-ttu-id="7f539-104">Her [ml.net görevi](resources/tasks.md)için, aralarından seçim yapabileceğiniz birden çok eğitim algoritması vardır.</span><span class="sxs-lookup"><span data-stu-id="7f539-104">For each [ML.NET task](resources/tasks.md), there are multiple training algorithms to choose from.</span></span> <span data-ttu-id="7f539-105">Hangi birini seçeceğiniz, çözmeye çalıştığınız soruna, verilerinizin özelliklerine ve kullanılabilir işlem ve depolama kaynaklarına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="7f539-105">Which one to choose depends on the problem you are trying to solve, the characteristics of your data, and the compute and storage resources you have available.</span></span> <span data-ttu-id="7f539-106">Bir makine öğrenimi modeline yönelik eğitim, yinelemeli bir işlem olduğunu unutmamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="7f539-106">It is important to note that training a machine learning model is an iterative process.</span></span> <span data-ttu-id="7f539-107">En iyi şekilde çalışacak olanı bulmak için birden çok algoritma denemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="7f539-107">You might need to try multiple algorithms to find the one that works best.</span></span>

<span data-ttu-id="7f539-108">Algoritmalar **Özellikler** üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="7f539-108">Algorithms operate on **features**.</span></span> <span data-ttu-id="7f539-109">Özellikler, giriş verilerinizde hesaplanan sayısal değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="7f539-109">Features are numerical values computed from your input data.</span></span> <span data-ttu-id="7f539-110">Makine öğrenimi algoritmaları için en iyi girişlerdir.</span><span class="sxs-lookup"><span data-stu-id="7f539-110">They are optimal inputs for machine learning algorithms.</span></span> <span data-ttu-id="7f539-111">Ham giriş verilerinizi bir veya daha fazla [veri dönüştürme](resources/transforms.md)kullanarak özelliklere dönüştürürler.</span><span class="sxs-lookup"><span data-stu-id="7f539-111">You transform your raw input data into features using one or more [data transforms](resources/transforms.md).</span></span> <span data-ttu-id="7f539-112">Örneğin, metin verileri bir sözcük sayısı ve sözcük birleşimi sayısı kümesine dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="7f539-112">For example, text data is transformed into a set of word counts and word combination counts.</span></span> <span data-ttu-id="7f539-113">Özellikler veri dönüştürmeleri kullanılarak ham bir veri türünden ayıklandıktan sonra, bunlar **korkaldırılmış** olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="7f539-113">Once the features have been extracted from a raw data type using data transforms, they are referred to as **featurized**.</span></span> <span data-ttu-id="7f539-114">Örneğin, korleştirilmiş metin veya daha fazla görüntü verisi.</span><span class="sxs-lookup"><span data-stu-id="7f539-114">For example, featurized text, or featurized image data.</span></span>

## <a name="trainer--algorithm--task"></a><span data-ttu-id="7f539-115">Trainer = algoritması + görev</span><span class="sxs-lookup"><span data-stu-id="7f539-115">Trainer = Algorithm + Task</span></span>

<span data-ttu-id="7f539-116">Algoritma, bir **model** oluşturmak için yürütülen matematik.</span><span class="sxs-lookup"><span data-stu-id="7f539-116">An algorithm is the math that executes to produce a **model**.</span></span> <span data-ttu-id="7f539-117">Farklı algoritmalar farklı özelliklerle modeller üretir.</span><span class="sxs-lookup"><span data-stu-id="7f539-117">Different algorithms produce models with different characteristics.</span></span>

<span data-ttu-id="7f539-118">ML.NET ile aynı algoritma farklı görevlere de uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="7f539-118">With ML.NET, the same algorithm can be applied to different tasks.</span></span> <span data-ttu-id="7f539-119">Örneğin, Stochastic çift koordinatı, Ikili sınıflandırma, birden çok Lass sınıflandırması ve gerileme için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7f539-119">For example, Stochastic Dual Coordinate Ascent can be used for Binary Classification, Multiclass Classification, and Regression.</span></span> <span data-ttu-id="7f539-120">Fark, algoritmanın çıktısının görevle eşleşecek şekilde nasıl yorumlanacağına ilişkin farktır.</span><span class="sxs-lookup"><span data-stu-id="7f539-120">The difference is in how the output of the algorithm is interpreted to match the task.</span></span>

<span data-ttu-id="7f539-121">Her algoritma/görev birleşimi için, ML.NET eğitim algoritmasını yürüten ve yorumu yapan bir bileşen sağlar.</span><span class="sxs-lookup"><span data-stu-id="7f539-121">For each algorithm/task combination, ML.NET provides a component that executes the training algorithm and makes the interpretation.</span></span> <span data-ttu-id="7f539-122">Bu bileşenlere, traers adı verilir.</span><span class="sxs-lookup"><span data-stu-id="7f539-122">These components are called trainers.</span></span> <span data-ttu-id="7f539-123">Örneğin, <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer> **regresyon** görevine uygulanan **Stochasticdualkoordinatör tedadscent** algoritmasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="7f539-123">For example, the <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer> uses the **StochasticDualCoordinatedAscent** algorithm applied to the **Regression** task.</span></span>

## <a name="linear-algorithms"></a><span data-ttu-id="7f539-124">Doğrusal algoritmalar</span><span class="sxs-lookup"><span data-stu-id="7f539-124">Linear algorithms</span></span>

<span data-ttu-id="7f539-125">Doğrusal algoritmalar, giriş verilerinin doğrusal bir bileşiminden ve bir **Ağırlık** kümesinden **puanları** hesaplayan bir model üretir.</span><span class="sxs-lookup"><span data-stu-id="7f539-125">Linear algorithms produce a model that calculates **scores** from a linear combination of the input data and a set of **weights**.</span></span> <span data-ttu-id="7f539-126">Ağırlıklar eğitim sırasında tahmini model parametreleridir.</span><span class="sxs-lookup"><span data-stu-id="7f539-126">The weights are parameters of the model estimated during training.</span></span>

<span data-ttu-id="7f539-127">Doğrusal algoritmalar, daha [önce ayrılabilir](https://en.wikipedia.org/wiki/Linear_separability)özellikler için iyi çalışır.</span><span class="sxs-lookup"><span data-stu-id="7f539-127">Linear algorithms work well for features that are [linearly separable](https://en.wikipedia.org/wiki/Linear_separability).</span></span>

<span data-ttu-id="7f539-128">Doğrusal algoritmayla eğitiminden önce Özellikler normalleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="7f539-128">Before training with a linear algorithm, the features should be normalized.</span></span> <span data-ttu-id="7f539-129">Bu, bir özelliğin sonuç üzerinde diğerlerinden daha fazla etki almasını engeller.</span><span class="sxs-lookup"><span data-stu-id="7f539-129">This prevents one feature from having more influence over the result than others.</span></span>

<span data-ttu-id="7f539-130">Genel olarak, doğrusal algoritmalar ölçeklenebilir, hızlı, ucuz ve yüksek EAP 'yi tahmin etmek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="7f539-130">In general, linear algorithms are scalable, fast, cheap to train, and cheap to predict.</span></span> <span data-ttu-id="7f539-131">Bunlar, özellik sayısına ve yaklaşık olarak eğitim verileri kümesinin boyutuna göre ölçeklendirebilir.</span><span class="sxs-lookup"><span data-stu-id="7f539-131">They scale by the number of features and approximately by the size of the training data set.</span></span>

<span data-ttu-id="7f539-132">Doğrusal algoritmalar eğitim verileri üzerinde birden çok geçiş yapar.</span><span class="sxs-lookup"><span data-stu-id="7f539-132">Linear algorithms make multiple passes over the training data.</span></span> <span data-ttu-id="7f539-133">Veri kümeniz belleğe sığıyorsa, öngörüyi eklemeden önce ML.NET işlem hattınızla bir [önbellek kontrol noktası](xref:Microsoft.ML.LearningPipelineExtensions.AppendCacheCheckpoint%2A) eklemek, eğitimin daha hızlı çalışmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="7f539-133">If your dataset fits into memory, then adding a [cache checkpoint](xref:Microsoft.ML.LearningPipelineExtensions.AppendCacheCheckpoint%2A) to your ML.NET pipeline before appending the trainer will make the training run faster.</span></span>

### <a name="averaged-perceptron"></a><span data-ttu-id="7f539-134">Ortalama Perceptron</span><span class="sxs-lookup"><span data-stu-id="7f539-134">Averaged perceptron</span></span>

<span data-ttu-id="7f539-135">Metin sınıflandırması için idealdir.</span><span class="sxs-lookup"><span data-stu-id="7f539-135">Best for text classification.</span></span>

|<span data-ttu-id="7f539-136">Eğitmen</span><span class="sxs-lookup"><span data-stu-id="7f539-136">Trainer</span></span>|<span data-ttu-id="7f539-137">Görev</span><span class="sxs-lookup"><span data-stu-id="7f539-137">Task</span></span>|<span data-ttu-id="7f539-138">ONNX dışarı aktarılabilir</span><span class="sxs-lookup"><span data-stu-id="7f539-138">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>|<span data-ttu-id="7f539-139">İkili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="7f539-139">Binary classification</span></span>|<span data-ttu-id="7f539-140">Yes</span><span class="sxs-lookup"><span data-stu-id="7f539-140">Yes</span></span>|

### <a name="stochastic-dual-coordinated-ascent"></a><span data-ttu-id="7f539-141">Stochastik çift Eşgüdümlü yoksı</span><span class="sxs-lookup"><span data-stu-id="7f539-141">Stochastic dual coordinated ascent</span></span>

<span data-ttu-id="7f539-142">Daha iyi varsayılan performans için ayarlama gerekmez.</span><span class="sxs-lookup"><span data-stu-id="7f539-142">Tuning not needed for good default performance.</span></span>

|<span data-ttu-id="7f539-143">Eğitmen</span><span class="sxs-lookup"><span data-stu-id="7f539-143">Trainer</span></span>|<span data-ttu-id="7f539-144">Görev</span><span class="sxs-lookup"><span data-stu-id="7f539-144">Task</span></span>|<span data-ttu-id="7f539-145">ONNX dışarı aktarılabilir</span><span class="sxs-lookup"><span data-stu-id="7f539-145">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer>|<span data-ttu-id="7f539-146">İkili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="7f539-146">Binary classification</span></span>|<span data-ttu-id="7f539-147">Yes</span><span class="sxs-lookup"><span data-stu-id="7f539-147">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.SdcaNonCalibratedBinaryTrainer>|<span data-ttu-id="7f539-148">İkili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="7f539-148">Binary classification</span></span>|<span data-ttu-id="7f539-149">Yes</span><span class="sxs-lookup"><span data-stu-id="7f539-149">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>|<span data-ttu-id="7f539-150">Birden çok Lass sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="7f539-150">Multiclass classification</span></span>|<span data-ttu-id="7f539-151">Yes</span><span class="sxs-lookup"><span data-stu-id="7f539-151">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>|<span data-ttu-id="7f539-152">Birden çok Lass sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="7f539-152">Multiclass classification</span></span>|<span data-ttu-id="7f539-153">Yes</span><span class="sxs-lookup"><span data-stu-id="7f539-153">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>|<span data-ttu-id="7f539-154">Regresyon</span><span class="sxs-lookup"><span data-stu-id="7f539-154">Regression</span></span>|<span data-ttu-id="7f539-155">Yes</span><span class="sxs-lookup"><span data-stu-id="7f539-155">Yes</span></span>|

### <a name="l-bfgs"></a><span data-ttu-id="7f539-156">L-BFGS</span><span class="sxs-lookup"><span data-stu-id="7f539-156">L-BFGS</span></span>

<span data-ttu-id="7f539-157">Özellik sayısı büyük olduğunda kullanın.</span><span class="sxs-lookup"><span data-stu-id="7f539-157">Use when number of features is large.</span></span> <span data-ttu-id="7f539-158">Lojistik regresyon eğitimi istatistikleri üretir, ancak AveragedPerceptronTrainer ile birlikte ölçeklendirmez.</span><span class="sxs-lookup"><span data-stu-id="7f539-158">Produces logistic regression training statistics, but doesn't scale as well as the AveragedPerceptronTrainer.</span></span>

|<span data-ttu-id="7f539-159">Eğitmen</span><span class="sxs-lookup"><span data-stu-id="7f539-159">Trainer</span></span>|<span data-ttu-id="7f539-160">Görev</span><span class="sxs-lookup"><span data-stu-id="7f539-160">Task</span></span>|<span data-ttu-id="7f539-161">ONNX dışarı aktarılabilir</span><span class="sxs-lookup"><span data-stu-id="7f539-161">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer>|<span data-ttu-id="7f539-162">İkili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="7f539-162">Binary classification</span></span>|<span data-ttu-id="7f539-163">Yes</span><span class="sxs-lookup"><span data-stu-id="7f539-163">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer>|<span data-ttu-id="7f539-164">Birden çok Lass sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="7f539-164">Multiclass classification</span></span>|<span data-ttu-id="7f539-165">Yes</span><span class="sxs-lookup"><span data-stu-id="7f539-165">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>|<span data-ttu-id="7f539-166">Regresyon</span><span class="sxs-lookup"><span data-stu-id="7f539-166">Regression</span></span>|<span data-ttu-id="7f539-167">Yes</span><span class="sxs-lookup"><span data-stu-id="7f539-167">Yes</span></span>|

### <a name="symbolic-stochastic-gradient-descent"></a><span data-ttu-id="7f539-168">Sembolik Stokastik gradyan</span><span class="sxs-lookup"><span data-stu-id="7f539-168">Symbolic stochastic gradient descent</span></span>

<span data-ttu-id="7f539-169">En hızlı ve en doğru doğrusal ikili sınıflandırma Trainer.</span><span class="sxs-lookup"><span data-stu-id="7f539-169">Fastest and most accurate linear binary classification trainer.</span></span> <span data-ttu-id="7f539-170">İşlemci sayısıyla birlikte ölçekler.</span><span class="sxs-lookup"><span data-stu-id="7f539-170">Scales well with number of processors.</span></span>

|<span data-ttu-id="7f539-171">Eğitmen</span><span class="sxs-lookup"><span data-stu-id="7f539-171">Trainer</span></span>|<span data-ttu-id="7f539-172">Görev</span><span class="sxs-lookup"><span data-stu-id="7f539-172">Task</span></span>|<span data-ttu-id="7f539-173">ONNX dışarı aktarılabilir</span><span class="sxs-lookup"><span data-stu-id="7f539-173">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>|<span data-ttu-id="7f539-174">İkili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="7f539-174">Binary classification</span></span>|<span data-ttu-id="7f539-175">Yes</span><span class="sxs-lookup"><span data-stu-id="7f539-175">Yes</span></span>|

### <a name="online-gradient-descent"></a><span data-ttu-id="7f539-176">Çevrimiçi gradyan</span><span class="sxs-lookup"><span data-stu-id="7f539-176">Online gradient descent</span></span>

<span data-ttu-id="7f539-177">Standart (Batch olmayan) stochastik degradesini, bir kayıp işlevleri ile ve zaman içinde görülen vektörin ortalamasını kullanarak ağırlık vektörünü güncelleştirme seçeneği uygular.</span><span class="sxs-lookup"><span data-stu-id="7f539-177">Implements the standard (non-batch) stochastic gradient descent, with a choice of loss functions, and an option to update the weight vector using the average of the vectors seen over time.</span></span>

|<span data-ttu-id="7f539-178">Eğitmen</span><span class="sxs-lookup"><span data-stu-id="7f539-178">Trainer</span></span>|<span data-ttu-id="7f539-179">Görev</span><span class="sxs-lookup"><span data-stu-id="7f539-179">Task</span></span>|<span data-ttu-id="7f539-180">ONNX dışarı aktarılabilir</span><span class="sxs-lookup"><span data-stu-id="7f539-180">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer>|<span data-ttu-id="7f539-181">Regresyon</span><span class="sxs-lookup"><span data-stu-id="7f539-181">Regression</span></span>|<span data-ttu-id="7f539-182">Yes</span><span class="sxs-lookup"><span data-stu-id="7f539-182">Yes</span></span>|

## <a name="decision-tree-algorithms"></a><span data-ttu-id="7f539-183">Karar ağacı algoritmaları</span><span class="sxs-lookup"><span data-stu-id="7f539-183">Decision tree algorithms</span></span>

<span data-ttu-id="7f539-184">Karar ağacı algoritmaları, bir dizi kararı içeren bir model oluşturur: veri değerleriyle etkin bir akış grafiği.</span><span class="sxs-lookup"><span data-stu-id="7f539-184">Decision tree algorithms create a model that contains a series of decisions: effectively a flow chart through the data values.</span></span>

<span data-ttu-id="7f539-185">Özelliklerin bu tür bir algoritma kullanması için doğrusal olarak ayrılabilir olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="7f539-185">Features do not need to be linearly separable to use this type of algorithm.</span></span> <span data-ttu-id="7f539-186">Özellik Vektördeki tekil değerler karar sürecinde bağımsız olarak kullanıldığından, ve özelliklerinin normalleştirilmesine gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="7f539-186">And features do not need to be normalized, because the individual values in the feature vector are used independently in the decision process.</span></span>

<span data-ttu-id="7f539-187">Karar ağacı algoritmaları genellikle çok doğru.</span><span class="sxs-lookup"><span data-stu-id="7f539-187">Decision tree algorithms are generally very accurate.</span></span>

<span data-ttu-id="7f539-188">Genelleştirilmiş ek modeller (GAMs) dışında, özellik sayısı büyük olduğunda ağaç modellerinin explainability eksik olabilir.</span><span class="sxs-lookup"><span data-stu-id="7f539-188">Except for Generalized Additive Models (GAMs), tree models can lack explainability when the number of features is large.</span></span>

<span data-ttu-id="7f539-189">Karar ağacı algoritmaları daha fazla kaynak alır ve doğrusal olanları da ölçeklendirmez.</span><span class="sxs-lookup"><span data-stu-id="7f539-189">Decision tree algorithms take more resources and do not scale as well as linear ones do.</span></span> <span data-ttu-id="7f539-190">Bunlar, belleğe sığan veri kümelerinde iyi bir şekilde gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="7f539-190">They do perform well on datasets that can fit into memory.</span></span>

<span data-ttu-id="7f539-191">Artırılmış karar ağaçları, her bir ağacın giriş verilerini puanlarını ve daha iyi bir puan üretmek için puanı bir sonraki ağaca geçirir ve bu şekilde, her bir ağacın bir öncekini geliştirdiği her bir ağaçta daha fazla gelişmesine neden olan küçük ağaçların bir alt kümesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7f539-191">Boosted decision trees are an ensemble of small trees where each tree scores the input data and passes the score onto the next tree to produce a better score, and so on, where each tree in the ensemble improves on the previous.</span></span>

### <a name="light-gradient-boosted-machine"></a><span data-ttu-id="7f539-192">Hafif gradyan tarafından artırılmış makine</span><span class="sxs-lookup"><span data-stu-id="7f539-192">Light gradient boosted machine</span></span>

<span data-ttu-id="7f539-193">İkili sınıflandırma ağacı izleyenilerinin en hızlı ve en doğru.</span><span class="sxs-lookup"><span data-stu-id="7f539-193">Fastest and most accurate of the binary classification tree trainers.</span></span> <span data-ttu-id="7f539-194">Yüksek düzeyde tunable.</span><span class="sxs-lookup"><span data-stu-id="7f539-194">Highly tunable.</span></span>

|<span data-ttu-id="7f539-195">Eğitmen</span><span class="sxs-lookup"><span data-stu-id="7f539-195">Trainer</span></span>|<span data-ttu-id="7f539-196">Görev</span><span class="sxs-lookup"><span data-stu-id="7f539-196">Task</span></span>|<span data-ttu-id="7f539-197">ONNX dışarı aktarılabilir</span><span class="sxs-lookup"><span data-stu-id="7f539-197">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer>|<span data-ttu-id="7f539-198">İkili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="7f539-198">Binary classification</span></span>|<span data-ttu-id="7f539-199">Yes</span><span class="sxs-lookup"><span data-stu-id="7f539-199">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>|<span data-ttu-id="7f539-200">Birden çok Lass sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="7f539-200">Multiclass classification</span></span>|<span data-ttu-id="7f539-201">Yes</span><span class="sxs-lookup"><span data-stu-id="7f539-201">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>|<span data-ttu-id="7f539-202">Regresyon</span><span class="sxs-lookup"><span data-stu-id="7f539-202">Regression</span></span>|<span data-ttu-id="7f539-203">Yes</span><span class="sxs-lookup"><span data-stu-id="7f539-203">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>|<span data-ttu-id="7f539-204">Sıralamasına</span><span class="sxs-lookup"><span data-stu-id="7f539-204">Ranking</span></span>|<span data-ttu-id="7f539-205">No</span><span class="sxs-lookup"><span data-stu-id="7f539-205">No</span></span>|

### <a name="fast-tree"></a><span data-ttu-id="7f539-206">Hızlı ağaç</span><span class="sxs-lookup"><span data-stu-id="7f539-206">Fast tree</span></span>

<span data-ttu-id="7f539-207">Korleştirilmiş görüntü verileri için kullanın.</span><span class="sxs-lookup"><span data-stu-id="7f539-207">Use for featurized image data.</span></span> <span data-ttu-id="7f539-208">Dengesiz verilere dayanıklı.</span><span class="sxs-lookup"><span data-stu-id="7f539-208">Resilient to unbalanced data.</span></span> <span data-ttu-id="7f539-209">Yüksek düzeyde tunable.</span><span class="sxs-lookup"><span data-stu-id="7f539-209">Highly tunable.</span></span>

|<span data-ttu-id="7f539-210">Eğitmen</span><span class="sxs-lookup"><span data-stu-id="7f539-210">Trainer</span></span>|<span data-ttu-id="7f539-211">Görev</span><span class="sxs-lookup"><span data-stu-id="7f539-211">Task</span></span>|<span data-ttu-id="7f539-212">ONNX dışarı aktarılabilir</span><span class="sxs-lookup"><span data-stu-id="7f539-212">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer>|<span data-ttu-id="7f539-213">İkili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="7f539-213">Binary classification</span></span>|<span data-ttu-id="7f539-214">Yes</span><span class="sxs-lookup"><span data-stu-id="7f539-214">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>|<span data-ttu-id="7f539-215">Regresyon</span><span class="sxs-lookup"><span data-stu-id="7f539-215">Regression</span></span>|<span data-ttu-id="7f539-216">Yes</span><span class="sxs-lookup"><span data-stu-id="7f539-216">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>|<span data-ttu-id="7f539-217">Regresyon</span><span class="sxs-lookup"><span data-stu-id="7f539-217">Regression</span></span>|<span data-ttu-id="7f539-218">Yes</span><span class="sxs-lookup"><span data-stu-id="7f539-218">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>|<span data-ttu-id="7f539-219">Sıralamasına</span><span class="sxs-lookup"><span data-stu-id="7f539-219">Ranking</span></span>|<span data-ttu-id="7f539-220">No</span><span class="sxs-lookup"><span data-stu-id="7f539-220">No</span></span>|

### <a name="fast-forest"></a><span data-ttu-id="7f539-221">Hızlı orman</span><span class="sxs-lookup"><span data-stu-id="7f539-221">Fast forest</span></span>

<span data-ttu-id="7f539-222">Gürültülü verilerle iyi sonuç verir.</span><span class="sxs-lookup"><span data-stu-id="7f539-222">Works well with noisy data.</span></span>

|<span data-ttu-id="7f539-223">Eğitmen</span><span class="sxs-lookup"><span data-stu-id="7f539-223">Trainer</span></span>|<span data-ttu-id="7f539-224">Görev</span><span class="sxs-lookup"><span data-stu-id="7f539-224">Task</span></span>|<span data-ttu-id="7f539-225">ONNX dışarı aktarılabilir</span><span class="sxs-lookup"><span data-stu-id="7f539-225">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer>|<span data-ttu-id="7f539-226">İkili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="7f539-226">Binary classification</span></span>|<span data-ttu-id="7f539-227">Yes</span><span class="sxs-lookup"><span data-stu-id="7f539-227">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>|<span data-ttu-id="7f539-228">Regresyon</span><span class="sxs-lookup"><span data-stu-id="7f539-228">Regression</span></span>|<span data-ttu-id="7f539-229">Yes</span><span class="sxs-lookup"><span data-stu-id="7f539-229">Yes</span></span>|

### <a name="generalized-additive-model-gam"></a><span data-ttu-id="7f539-230">Genelleştirilmiş eklenebilir model (GAM)</span><span class="sxs-lookup"><span data-stu-id="7f539-230">Generalized additive model (GAM)</span></span>

<span data-ttu-id="7f539-231">Ağaç algoritmalarıyla iyi sonuç veren, ancak explainability bir öncelik olduğu sorunlar için idealdir.</span><span class="sxs-lookup"><span data-stu-id="7f539-231">Best for problems that perform well with tree algorithms but where explainability is a priority.</span></span>

|<span data-ttu-id="7f539-232">Eğitmen</span><span class="sxs-lookup"><span data-stu-id="7f539-232">Trainer</span></span>|<span data-ttu-id="7f539-233">Görev</span><span class="sxs-lookup"><span data-stu-id="7f539-233">Task</span></span>|<span data-ttu-id="7f539-234">ONNX dışarı aktarılabilir</span><span class="sxs-lookup"><span data-stu-id="7f539-234">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer>|<span data-ttu-id="7f539-235">İkili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="7f539-235">Binary classification</span></span>|<span data-ttu-id="7f539-236">No</span><span class="sxs-lookup"><span data-stu-id="7f539-236">No</span></span>|
|<xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>|<span data-ttu-id="7f539-237">Regresyon</span><span class="sxs-lookup"><span data-stu-id="7f539-237">Regression</span></span>|<span data-ttu-id="7f539-238">No</span><span class="sxs-lookup"><span data-stu-id="7f539-238">No</span></span>|

## <a name="matrix-factorization"></a><span data-ttu-id="7f539-239">Matris ayırma</span><span class="sxs-lookup"><span data-stu-id="7f539-239">Matrix factorization</span></span>

### <a name="matrix-factorization"></a><span data-ttu-id="7f539-240">Matris ayırma</span><span class="sxs-lookup"><span data-stu-id="7f539-240">Matrix Factorization</span></span>

<span data-ttu-id="7f539-241">Önerideki [birlikte çalışan filtrelemesi](https://en.wikipedia.org/wiki/Collaborative_filtering) için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7f539-241">Used for [collaborative filtering](https://en.wikipedia.org/wiki/Collaborative_filtering) in recommendation.</span></span>

|<span data-ttu-id="7f539-242">Eğitmen</span><span class="sxs-lookup"><span data-stu-id="7f539-242">Trainer</span></span>|<span data-ttu-id="7f539-243">Görev</span><span class="sxs-lookup"><span data-stu-id="7f539-243">Task</span></span>|<span data-ttu-id="7f539-244">ONNX dışarı aktarılabilir</span><span class="sxs-lookup"><span data-stu-id="7f539-244">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>|<span data-ttu-id="7f539-245">Öneri</span><span class="sxs-lookup"><span data-stu-id="7f539-245">Recommendation</span></span>|<span data-ttu-id="7f539-246">No</span><span class="sxs-lookup"><span data-stu-id="7f539-246">No</span></span>|

### <a name="field-aware-factorization-machine"></a><span data-ttu-id="7f539-247">Alan duyarlı Faks makinesi</span><span class="sxs-lookup"><span data-stu-id="7f539-247">Field Aware Factorization Machine</span></span>

 <span data-ttu-id="7f539-248">Büyük veri kümeleriyle seyrek kategorik veriler için idealdir.</span><span class="sxs-lookup"><span data-stu-id="7f539-248">Best for sparse categorical data, with large datasets.</span></span>

|<span data-ttu-id="7f539-249">Eğitmen</span><span class="sxs-lookup"><span data-stu-id="7f539-249">Trainer</span></span>|<span data-ttu-id="7f539-250">Görev</span><span class="sxs-lookup"><span data-stu-id="7f539-250">Task</span></span>|<span data-ttu-id="7f539-251">ONNX dışarı aktarılabilir</span><span class="sxs-lookup"><span data-stu-id="7f539-251">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer>|<span data-ttu-id="7f539-252">İkili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="7f539-252">Binary classification</span></span>|<span data-ttu-id="7f539-253">No</span><span class="sxs-lookup"><span data-stu-id="7f539-253">No</span></span>|

## <a name="meta-algorithms"></a><span data-ttu-id="7f539-254">Meta algoritmalar</span><span class="sxs-lookup"><span data-stu-id="7f539-254">Meta algorithms</span></span>

<span data-ttu-id="7f539-255">Bu traçler, ikili bir eğitimci tarafından çok sınıflı bir değer oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7f539-255">These trainers create a multiclass trainer from a binary trainer.</span></span> <span data-ttu-id="7f539-256">,,,,,, İle kullanın <xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer> <xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer> <xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer> .</span><span class="sxs-lookup"><span data-stu-id="7f539-256">Use with <xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>, <xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer>, <xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>, <xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer>, <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer>, <xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer>, <xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer>.</span></span>

### <a name="one-versus-all"></a><span data-ttu-id="7f539-257">Tek ve tüm</span><span class="sxs-lookup"><span data-stu-id="7f539-257">One versus all</span></span>

<span data-ttu-id="7f539-258">Bu çok sınıf Sınıflandırıcısı her sınıf için bir ikili sınıflandırıcının yanı da bu sınıfı diğer tüm sınıflardan ayırt eder.</span><span class="sxs-lookup"><span data-stu-id="7f539-258">This multiclass classifier trains one binary classifier for each class, which distinguishes that class from all other classes.</span></span> <span data-ttu-id="7f539-259">Sınıflandırılacak sınıf sayısına göre ölçeğe göre sınırlandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="7f539-259">Is limited in scale by the number of classes to categorize.</span></span>

|<span data-ttu-id="7f539-260">Eğitmen</span><span class="sxs-lookup"><span data-stu-id="7f539-260">Trainer</span></span>|<span data-ttu-id="7f539-261">Görev</span><span class="sxs-lookup"><span data-stu-id="7f539-261">Task</span></span>|<span data-ttu-id="7f539-262">ONNX dışarı aktarılabilir</span><span class="sxs-lookup"><span data-stu-id="7f539-262">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.OneVersusAllTrainer>|<span data-ttu-id="7f539-263">Birden çok Lass sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="7f539-263">Multiclass classification</span></span>|<span data-ttu-id="7f539-264">Yes</span><span class="sxs-lookup"><span data-stu-id="7f539-264">Yes</span></span>|

### <a name="pairwise-coupling"></a><span data-ttu-id="7f539-265">İkili eşlenme</span><span class="sxs-lookup"><span data-stu-id="7f539-265">Pairwise coupling</span></span>

<span data-ttu-id="7f539-266">Bu çok sınıf Sınıflandırıcısı, her sınıf çiftinde ikili bir sınıflandırma algoritması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7f539-266">This multiclass classifier trains a binary classification algorithm on each pair of classes.</span></span> <span data-ttu-id="7f539-267">, İki sınıfın birleşiminin eğitililmesi gerektiği için sınıfların sayısına göre ölçeklendirilmesine sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="7f539-267">Is limited in scale by the number of classes, as each combination of two classes must be trained.</span></span>

|<span data-ttu-id="7f539-268">Eğitmen</span><span class="sxs-lookup"><span data-stu-id="7f539-268">Trainer</span></span>|<span data-ttu-id="7f539-269">Görev</span><span class="sxs-lookup"><span data-stu-id="7f539-269">Task</span></span>|<span data-ttu-id="7f539-270">ONNX dışarı aktarılabilir</span><span class="sxs-lookup"><span data-stu-id="7f539-270">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer>|<span data-ttu-id="7f539-271">Birden çok Lass sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="7f539-271">Multiclass classification</span></span>|<span data-ttu-id="7f539-272">No</span><span class="sxs-lookup"><span data-stu-id="7f539-272">No</span></span>|

## <a name="k-means"></a><span data-ttu-id="7f539-273">K-anlamı</span><span class="sxs-lookup"><span data-stu-id="7f539-273">K-Means</span></span>

<span data-ttu-id="7f539-274">Kümeleme için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7f539-274">Used for clustering.</span></span>

|<span data-ttu-id="7f539-275">Eğitmen</span><span class="sxs-lookup"><span data-stu-id="7f539-275">Trainer</span></span>|<span data-ttu-id="7f539-276">Görev</span><span class="sxs-lookup"><span data-stu-id="7f539-276">Task</span></span>|<span data-ttu-id="7f539-277">ONNX dışarı aktarılabilir</span><span class="sxs-lookup"><span data-stu-id="7f539-277">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.KMeansTrainer>|<span data-ttu-id="7f539-278">Kümeleme</span><span class="sxs-lookup"><span data-stu-id="7f539-278">Clustering</span></span>|<span data-ttu-id="7f539-279">Yes</span><span class="sxs-lookup"><span data-stu-id="7f539-279">Yes</span></span>|

## <a name="principal-component-analysis"></a><span data-ttu-id="7f539-280">Sorumlu bileşen analizi</span><span class="sxs-lookup"><span data-stu-id="7f539-280">Principal component analysis</span></span>

<span data-ttu-id="7f539-281">Anomali algılama için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7f539-281">Used for anomaly detection.</span></span>

|<span data-ttu-id="7f539-282">Eğitmen</span><span class="sxs-lookup"><span data-stu-id="7f539-282">Trainer</span></span>|<span data-ttu-id="7f539-283">Görev</span><span class="sxs-lookup"><span data-stu-id="7f539-283">Task</span></span>|<span data-ttu-id="7f539-284">ONNX dışarı aktarılabilir</span><span class="sxs-lookup"><span data-stu-id="7f539-284">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>|<span data-ttu-id="7f539-285">Anormallik algılama</span><span class="sxs-lookup"><span data-stu-id="7f539-285">Anomaly detection</span></span>|<span data-ttu-id="7f539-286">No</span><span class="sxs-lookup"><span data-stu-id="7f539-286">No</span></span>|

## <a name="naive-bayes"></a><span data-ttu-id="7f539-287">Sade Bayes</span><span class="sxs-lookup"><span data-stu-id="7f539-287">Naive Bayes</span></span>

<span data-ttu-id="7f539-288">Özellikler bağımsız olduğunda ve eğitim veri kümesi küçük olduğunda bu çok sınıflı sınıflandırma algoritmasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="7f539-288">Use this multi-class classification algorithm when the features are independent, and the training dataset is small.</span></span>

|<span data-ttu-id="7f539-289">Eğitmen</span><span class="sxs-lookup"><span data-stu-id="7f539-289">Trainer</span></span>|<span data-ttu-id="7f539-290">Görev</span><span class="sxs-lookup"><span data-stu-id="7f539-290">Task</span></span>|<span data-ttu-id="7f539-291">ONNX dışarı aktarılabilir</span><span class="sxs-lookup"><span data-stu-id="7f539-291">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>|<span data-ttu-id="7f539-292">Birden çok Lass sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="7f539-292">Multiclass classification</span></span>|<span data-ttu-id="7f539-293">Yes</span><span class="sxs-lookup"><span data-stu-id="7f539-293">Yes</span></span>|

## <a name="prior-trainer"></a><span data-ttu-id="7f539-294">Önceki seyahat</span><span class="sxs-lookup"><span data-stu-id="7f539-294">Prior Trainer</span></span>

<span data-ttu-id="7f539-295">Diğer eğitiçilerin performansını temel almak için bu ikili sınıflandırma algoritmasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="7f539-295">Use this binary classification algorithm to baseline the performance of other trainers.</span></span> <span data-ttu-id="7f539-296">Etkili olması için, diğer traçilerin ölçümleri önceki eğitime göre daha iyi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7f539-296">To be effective, the metrics of the other trainers should be better than the prior trainer.</span></span>

|<span data-ttu-id="7f539-297">Eğitmen</span><span class="sxs-lookup"><span data-stu-id="7f539-297">Trainer</span></span>|<span data-ttu-id="7f539-298">Görev</span><span class="sxs-lookup"><span data-stu-id="7f539-298">Task</span></span>|<span data-ttu-id="7f539-299">ONNX dışarı aktarılabilir</span><span class="sxs-lookup"><span data-stu-id="7f539-299">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.PriorTrainer>|<span data-ttu-id="7f539-300">İkili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="7f539-300">Binary classification</span></span>|<span data-ttu-id="7f539-301">Yes</span><span class="sxs-lookup"><span data-stu-id="7f539-301">Yes</span></span>|

## <a name="support-vector-machines"></a><span data-ttu-id="7f539-302">Vektör makinelerini destekleme</span><span class="sxs-lookup"><span data-stu-id="7f539-302">Support vector machines</span></span>

<span data-ttu-id="7f539-303">Destek vektör makineleri (SVMs), doğrusal ve doğrusal olmayan sınıflandırma görevlerinde kullanılabilecek, denetimli bir öğrenme modellerinin son derece popüler ve iyi arandığı bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="7f539-303">Support vector machines (SVMs) are an extremely popular and well-researched class of supervised learning models, which can be used in linear and non-linear classification tasks.</span></span>

<span data-ttu-id="7f539-304">Son araştırma, bu modelleri daha büyük eğitim kümelerine verimli bir şekilde ölçeklendirmek için iyileştirmek için yöntemlere odaklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="7f539-304">Recent research has focused on ways to optimize these models to efficiently scale to larger training sets.</span></span>

### <a name="linear-svm"></a><span data-ttu-id="7f539-305">Doğrusal SVM</span><span class="sxs-lookup"><span data-stu-id="7f539-305">Linear SVM</span></span>

<span data-ttu-id="7f539-306">Boole olarak etiketlenen veriler üzerinde eğitilen doğrusal bir ikili sınıflandırma modeli kullanarak bir hedefi tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="7f539-306">Predicts a target using a linear binary classification model trained over boolean labeled data.</span></span> <span data-ttu-id="7f539-307">Stokastik gradyan adımları ve İzdüşüm adımları arasında alternatifler.</span><span class="sxs-lookup"><span data-stu-id="7f539-307">Alternates between stochastic gradient descent steps and projection steps.</span></span>

|<span data-ttu-id="7f539-308">Eğitmen</span><span class="sxs-lookup"><span data-stu-id="7f539-308">Trainer</span></span>|<span data-ttu-id="7f539-309">Görev</span><span class="sxs-lookup"><span data-stu-id="7f539-309">Task</span></span>|<span data-ttu-id="7f539-310">ONNX dışarı aktarılabilir</span><span class="sxs-lookup"><span data-stu-id="7f539-310">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.LinearSvmTrainer>|<span data-ttu-id="7f539-311">İkili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="7f539-311">Binary classification</span></span>|<span data-ttu-id="7f539-312">Yes</span><span class="sxs-lookup"><span data-stu-id="7f539-312">Yes</span></span>|

### <a name="local-deep-svm"></a><span data-ttu-id="7f539-313">Yerel derin SVM</span><span class="sxs-lookup"><span data-stu-id="7f539-313">Local Deep SVM</span></span>

<span data-ttu-id="7f539-314">Doğrusal olmayan bir ikili sınıflandırma modeli kullanarak bir hedefi tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="7f539-314">Predicts a target using a non-linear binary classification model.</span></span> <span data-ttu-id="7f539-315">Tahmin süresi maliyetini azaltır; tahmin maliyeti, daha erken bir şekilde, sınıflandırma doğruluğunun toleransı kaybı ile değil, eğitim kümesinin boyutuyla logaritarak büyüyerek artar.</span><span class="sxs-lookup"><span data-stu-id="7f539-315">Reduces the prediction time cost; the prediction cost grows logarithmically with the size of the training set, rather than linearly, with a tolerable loss in classification accuracy.</span></span>

|<span data-ttu-id="7f539-316">Eğitmen</span><span class="sxs-lookup"><span data-stu-id="7f539-316">Trainer</span></span>|<span data-ttu-id="7f539-317">Görev</span><span class="sxs-lookup"><span data-stu-id="7f539-317">Task</span></span>|<span data-ttu-id="7f539-318">ONNX dışarı aktarılabilir</span><span class="sxs-lookup"><span data-stu-id="7f539-318">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.LdSvmTrainer>|<span data-ttu-id="7f539-319">İkili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="7f539-319">Binary classification</span></span>|<span data-ttu-id="7f539-320">Yes</span><span class="sxs-lookup"><span data-stu-id="7f539-320">Yes</span></span>|

## <a name="ordinary-least-squares"></a><span data-ttu-id="7f539-321">Normal en az kareler</span><span class="sxs-lookup"><span data-stu-id="7f539-321">Ordinary least squares</span></span>

<span data-ttu-id="7f539-322">Normal en az kareler (IR), doğrusal Regresyondaki en yaygın olarak kullanılan tekniklerin biridir.</span><span class="sxs-lookup"><span data-stu-id="7f539-322">Ordinary least squares (OLS) is one of the most commonly used techniques in linear regression.</span></span>

<span data-ttu-id="7f539-323">Normal en az kareler, hatayı gerçek değerden tahmin edilen satıra kadar olan uzaklık karenin toplamı olarak hesaplayan kayıp işlevini ifade eder ve kare içinde hatayı en aza indirerek modele uyar.</span><span class="sxs-lookup"><span data-stu-id="7f539-323">Ordinary least squares refers to the loss function, which computes error as the sum of the square of distance from the actual value to the predicted line, and fits the model by minimizing the squared error.</span></span> <span data-ttu-id="7f539-324">Bu yöntem, girişler ve bağımlı değişken arasında güçlü doğrusal bir ilişki olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="7f539-324">This method assumes a strong linear relationship between the inputs and the dependent variable.</span></span>

|<span data-ttu-id="7f539-325">Eğitmen</span><span class="sxs-lookup"><span data-stu-id="7f539-325">Trainer</span></span>|<span data-ttu-id="7f539-326">Görev</span><span class="sxs-lookup"><span data-stu-id="7f539-326">Task</span></span>|<span data-ttu-id="7f539-327">ONNX dışarı aktarılabilir</span><span class="sxs-lookup"><span data-stu-id="7f539-327">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.OlsTrainer>|<span data-ttu-id="7f539-328">Regresyon</span><span class="sxs-lookup"><span data-stu-id="7f539-328">Regression</span></span>|<span data-ttu-id="7f539-329">Yes</span><span class="sxs-lookup"><span data-stu-id="7f539-329">Yes</span></span>|
