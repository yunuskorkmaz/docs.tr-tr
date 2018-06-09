---
title: Machine Learning sözlüğü
description: Makine öğrenimi terimleri içeren sözlük.
author: jralexander
ms.author: johalex
ms.date: 05/31/2018
ms.topic: conceptual
ms.prod: dotnet-ml
ms.devlang: dotnet
manager: wpickett
ms.openlocfilehash: 332d9e14bea165992f9f00b048286e185269ea79
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2018
ms.locfileid: "35017302"
---
# <a name="machine-learning-glossary"></a><span data-ttu-id="c7d40-103">Machine learning sözlüğü</span><span class="sxs-lookup"><span data-stu-id="c7d40-103">Machine learning glossary</span></span>

<span data-ttu-id="c7d40-104">Aşağıdaki özel Modellerinizi yapı oldukça faydalıdır önemli makine öğrenimi terimleri derlenmesini listesidir.</span><span class="sxs-lookup"><span data-stu-id="c7d40-104">The following list is a compilation of important machine learning terms that are useful as you build your custom models.</span></span>

## <a name="accuracy"></a><span data-ttu-id="c7d40-105">Doğruluk</span><span class="sxs-lookup"><span data-stu-id="c7d40-105">Accuracy</span></span>

<span data-ttu-id="c7d40-106">İçinde [sınıflandırma](#classification), doğruluk, doğru olarak sınıflandırılmış öğeleri bölü sınama kümesi öğelerde toplam sayısı numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="c7d40-106">In [classification](#classification), accuracy is the number of correctly classified items divided by the total number of items in the test set.</span></span> <span data-ttu-id="c7d40-107">0 (en az doğru) aralığından 1 (en doğru).</span><span class="sxs-lookup"><span data-stu-id="c7d40-107">Ranges from 0 (least accurate) to 1 (most accurate).</span></span> <span data-ttu-id="c7d40-108">Doğruluk modelinizi performansını değerlendirme ölçümlerini biridir.</span><span class="sxs-lookup"><span data-stu-id="c7d40-108">Accuracy is one of evaluation metrics of the performance of your model.</span></span> <span data-ttu-id="c7d40-109">İle birlikte düşünün [duyarlık](#precision), [geri çağırma](#recall), ve [F-score](#f-score).</span><span class="sxs-lookup"><span data-stu-id="c7d40-109">Consider it in conjunction with [precision](#precision), [recall](#recall), and [F-score](#f-score).</span></span>

<span data-ttu-id="c7d40-110">İlgili ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.Accuracy?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c7d40-110">Related ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.Accuracy?displayProperty=nameWithType>.</span></span>

## <a name="area-under-the-curve-auc"></a><span data-ttu-id="c7d40-111">Eğriyi (AUC) alanında</span><span class="sxs-lookup"><span data-stu-id="c7d40-111">Area under the curve (AUC)</span></span>

<span data-ttu-id="c7d40-112">İçinde [ikili sınıflandırma](#binary-classification), doğru pozitif sonuç oranı (y) çizer eğri alanında hatalı pozitif sonuç oranı (x ekseni) karşı değeri bir değerlendirme ölçümü.</span><span class="sxs-lookup"><span data-stu-id="c7d40-112">In [binary classification](#binary-classification), an evaluation metric that is the value of the area under the curve that plots the true positives rate (on the y-axis) against the false positives rate (on the x-axis).</span></span> <span data-ttu-id="c7d40-113">0,5 (en kötü) 1 (iyi) aralıkları.</span><span class="sxs-lookup"><span data-stu-id="c7d40-113">Ranges from 0.5 (worst) to 1 (best).</span></span> <span data-ttu-id="c7d40-114">Olarak da bilinen alanı ROC eğrisi, yani, özellik eğri işletim alıcı altında.</span><span class="sxs-lookup"><span data-stu-id="c7d40-114">Also known as the area under the ROC curve, i.e., receiver operating characteristic curve.</span></span> <span data-ttu-id="c7d40-115">Daha fazla bilgi için bkz: [karakteristiğini işletim alıcı](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) makale wikipedia'da.</span><span class="sxs-lookup"><span data-stu-id="c7d40-115">For more information, see the [Receiver operating characteristic](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) article on Wikipedia.</span></span>

<span data-ttu-id="c7d40-116">İlgili ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.Auc?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c7d40-116">Related ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.Auc?displayProperty=nameWithType>.</span></span>

## <a name="binary-classification"></a><span data-ttu-id="c7d40-117">ikili sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="c7d40-117">Binary classification</span></span>

<span data-ttu-id="c7d40-118">A [sınıflandırma](#classification) durumda nerede [etiket](#label) yalnızca bir dışı iki sınıfları.</span><span class="sxs-lookup"><span data-stu-id="c7d40-118">A [classification](#classification) case where the [label](#label) is only one out of two classes.</span></span> <span data-ttu-id="c7d40-119">Daha fazla bilgi için bkz: [ikili sınıflandırma](https://en.wikipedia.org/wiki/Binary_classification) makale wikipedia'da.</span><span class="sxs-lookup"><span data-stu-id="c7d40-119">For more information, see the [Binary classification](https://en.wikipedia.org/wiki/Binary_classification) article on Wikipedia.</span></span>

## <a name="classification"></a><span data-ttu-id="c7d40-120">Sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="c7d40-120">Classification</span></span>

<span data-ttu-id="c7d40-121">Verileri bir kategori tahmin etmek için kullanıldığında, [denetimli makine öğrenme](#supervised-machine-learning) görev sınıflandırma çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c7d40-121">When the data is used to predict a category, [supervised machine learning](#supervised-machine-learning) task is called classification.</span></span> <span data-ttu-id="c7d40-122">[İkili sınıflandırma](#binary-classification) yalnızca iki kategorisi (örneğin, bir görüntü resmini 'Kat' veya 'köpek' sınıflandırma) tahmin etmeye için başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="c7d40-122">[Binary classification](#binary-classification) refers to predicting only two categories (for example, classifying an image as a picture of either a 'cat' or a 'dog').</span></span> <span data-ttu-id="c7d40-123">[Çok sınıflı sınıflandırma](#multiclass-classification) (örneğin, belirli bir köpek bir resim olarak görüntüyü sınıflandırma) birden çok kategori tahmin için başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="c7d40-123">[Multiclass classification](#multiclass-classification) refers to predicting multiple categories (for example, when classifying an image as a picture of a specific breed of dog).</span></span>

## <a name="coefficient-of-determination"></a><span data-ttu-id="c7d40-124">Katsayısı</span><span class="sxs-lookup"><span data-stu-id="c7d40-124">Coefficient of determination</span></span>

<span data-ttu-id="c7d40-125">İçinde [regresyon](#regression), veri modeli ne kadar iyi uyduğunu gösteren bir değerlendirme ölçümü.</span><span class="sxs-lookup"><span data-stu-id="c7d40-125">In [regression](#regression), an evaluation metric that indicates how well data fits a model.</span></span> <span data-ttu-id="c7d40-126">1 aralığı 0'dan.</span><span class="sxs-lookup"><span data-stu-id="c7d40-126">Ranges from 0 to 1.</span></span> <span data-ttu-id="c7d40-127">Veri rastgele veya başka türlü 0 anlamına gelir değerini modele sığamıyorsa.</span><span class="sxs-lookup"><span data-stu-id="c7d40-127">A value of 0 means that the data is random or otherwise cannot be fit to the model.</span></span> <span data-ttu-id="c7d40-128">Bir değer model verileri tam olarak eşleşen 1 anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c7d40-128">A value of 1 means that the model exactly matches the data.</span></span> <span data-ttu-id="c7d40-129">Bu genellikle r adlandırılır<sup>2</sup>, R<sup>2</sup>, veya r karesi alınmış.</span><span class="sxs-lookup"><span data-stu-id="c7d40-129">This is often referred to as r<sup>2</sup>, R<sup>2</sup>, or r-squared.</span></span>

<span data-ttu-id="c7d40-130">İlgili ML.NET API: <xref:Microsoft.ML.Models.RegressionMetrics.RSquared?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c7d40-130">Related ML.NET API: <xref:Microsoft.ML.Models.RegressionMetrics.RSquared?displayProperty=nameWithType>.</span></span>

## <a name="feature"></a><span data-ttu-id="c7d40-131">Özellik</span><span class="sxs-lookup"><span data-stu-id="c7d40-131">Feature</span></span>

<span data-ttu-id="c7d40-132">Ölçülen, olguya genellikle sayısal (double) değeri, ölçülebilir bir özelliği.</span><span class="sxs-lookup"><span data-stu-id="c7d40-132">A measurable property of the phenomenon being measured, typically a numeric (double) value.</span></span> <span data-ttu-id="c7d40-133">Birden çok özellik denir bir **özelliği vektör** ve tipik olarak depolanan `double[]`.</span><span class="sxs-lookup"><span data-stu-id="c7d40-133">Multiple features are referred to as a **Feature vector** and typically stored as `double[]`.</span></span> <span data-ttu-id="c7d40-134">Özellikleri ölçülen olguya önemli özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c7d40-134">Features define the important characteristics of the phenomenon being measured.</span></span> <span data-ttu-id="c7d40-135">Daha fazla bilgi için bkz: [özelliği](https://en.wikipedia.org/wiki/Feature_(machine_learning)) makale wikipedia'da.</span><span class="sxs-lookup"><span data-stu-id="c7d40-135">For more information, see the [Feature](https://en.wikipedia.org/wiki/Feature_(machine_learning)) article on Wikipedia.</span></span>

## <a name="feature-engineering"></a><span data-ttu-id="c7d40-136">Özellik Mühendisliği</span><span class="sxs-lookup"><span data-stu-id="c7d40-136">Feature engineering</span></span>

<span data-ttu-id="c7d40-137">Özellik Mühendisliği işlemidir kümesini tanımlama içeren [özellikleri](#feature) ve başka bir deyişle, özellik vektörlerinin kullanılabilir olguya verilerden üreten yazılım özelliği ayıklama geliştirme.</span><span class="sxs-lookup"><span data-stu-id="c7d40-137">Feature engineering is the process that involves defining a set of [features](#feature) and developing software that produces feature vectors from available phenomenon data, i.e., feature extraction.</span></span> <span data-ttu-id="c7d40-138">Daha fazla bilgi için bkz: [özellik Mühendisliği](https://en.wikipedia.org/wiki/Feature_engineering) makale wikipedia'da.</span><span class="sxs-lookup"><span data-stu-id="c7d40-138">For more information, see the [Feature engineering](https://en.wikipedia.org/wiki/Feature_engineering) article on Wikipedia.</span></span>

## <a name="f-score"></a><span data-ttu-id="c7d40-139">F-score</span><span class="sxs-lookup"><span data-stu-id="c7d40-139">F-score</span></span>

<span data-ttu-id="c7d40-140">İçinde [sınıflandırma](#classification), dengeleyen bir değerlendirme ölçümü [duyarlık](#precision) ve [geri çağırma](#recall).</span><span class="sxs-lookup"><span data-stu-id="c7d40-140">In [classification](#classification), an evaluation metric that balances [precision](#precision) and [recall](#recall).</span></span>

<span data-ttu-id="c7d40-141">İlgili ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.F1Score?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c7d40-141">Related ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.F1Score?displayProperty=nameWithType>.</span></span>

## <a name="hyperparameter"></a><span data-ttu-id="c7d40-142">Hyperparameter</span><span class="sxs-lookup"><span data-stu-id="c7d40-142">Hyperparameter</span></span>

<span data-ttu-id="c7d40-143">Makine öğrenme algoritmasını parametresi.</span><span class="sxs-lookup"><span data-stu-id="c7d40-143">A parameter of a machine learning algorithm.</span></span> <span data-ttu-id="c7d40-144">Örnekler karar orman ya da bir gradyan düşüşü algoritması adım boyutunda öğrenmek için ağaçları sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="c7d40-144">Examples include the number of trees to learn in a decision forest or the step size in a gradient descent algorithm.</span></span> <span data-ttu-id="c7d40-145">Değerleri *Hyperparameters* eğitim modeli önce ayarlanır ve örneğin, tahmin işlevinde parametre bulma işleminin karar ağacı ya da doğrusal regresyon modeli ağırlıkları karşılaştırma işaret yöneten .</span><span class="sxs-lookup"><span data-stu-id="c7d40-145">Values of *Hyperparameters* are set before training the model and govern the process of finding the parameters of the prediction function, for example, the comparison points in a decision tree or the weights in a linear regression model.</span></span> <span data-ttu-id="c7d40-146">Daha fazla bilgi için bkz: [Hyperparameter](https://en.wikipedia.org/wiki/Hyperparameter_(machine_learning)) wikipedia'da makalesi.</span><span class="sxs-lookup"><span data-stu-id="c7d40-146">For more information, see the [Hyperparameter](https://en.wikipedia.org/wiki/Hyperparameter_(machine_learning)) article on Wikipedia.</span></span>

## <a name="label"></a><span data-ttu-id="c7d40-147">Etiketle</span><span class="sxs-lookup"><span data-stu-id="c7d40-147">Label</span></span>

<span data-ttu-id="c7d40-148">Makine öğrenimi modeline tahmin öğesi.</span><span class="sxs-lookup"><span data-stu-id="c7d40-148">The element to be predicted with the machine learning model.</span></span> <span data-ttu-id="c7d40-149">Örneğin, köpek veya gelecekteki bir stok fiyat türü.</span><span class="sxs-lookup"><span data-stu-id="c7d40-149">For example, the breed of dog or a future stock price.</span></span>

## <a name="log-loss"></a><span data-ttu-id="c7d40-150">Günlük kaybı</span><span class="sxs-lookup"><span data-stu-id="c7d40-150">Log loss</span></span>

<span data-ttu-id="c7d40-151">İçinde [sınıflandırma](#classification), bir değerlendirme ölçümü sınıflandırıcı doğruluğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7d40-151">In [classification](#classification), an evaluation metric that characterizes the accuracy of a classifier.</span></span> <span data-ttu-id="c7d40-152">Daha küçük günlük kaybı, daha doğru bir sınıflandırıcı olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="c7d40-152">The smaller log loss is, the more accurate a classifier is.</span></span>

<span data-ttu-id="c7d40-153">İlgili ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.LogLoss?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c7d40-153">Related ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.LogLoss?displayProperty=nameWithType>.</span></span>

## <a name="mean-absolute-error-mae"></a><span data-ttu-id="c7d40-154">Ortalama mutlak hata (MAE)</span><span class="sxs-lookup"><span data-stu-id="c7d40-154">Mean absolute error (MAE)</span></span>

<span data-ttu-id="c7d40-155">İçinde [regresyon](#regression), tüm model hataların ortalaması modeli hata tahmin edilen arasındaki uzaklığı olduğu bir değerlendirme ölçümü [etiket](#label) değeri ve doğru etiket değeri.</span><span class="sxs-lookup"><span data-stu-id="c7d40-155">In [regression](#regression), an evaluation metric that is the average of all the model errors, where model error is the distance between the predicted [label](#label) value and the correct label value.</span></span>

<span data-ttu-id="c7d40-156">İlgili ML.NET API: <xref:Microsoft.ML.Models.RegressionMetrics.L1?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c7d40-156">Related ML.NET API: <xref:Microsoft.ML.Models.RegressionMetrics.L1?displayProperty=nameWithType>.</span></span>

## <a name="model"></a><span data-ttu-id="c7d40-157">Model</span><span class="sxs-lookup"><span data-stu-id="c7d40-157">Model</span></span>

<span data-ttu-id="c7d40-158">Geleneksel olarak, tahmin işlevinde parametreleri.</span><span class="sxs-lookup"><span data-stu-id="c7d40-158">Traditionally, the parameters for the prediction function.</span></span> <span data-ttu-id="c7d40-159">Örneğin, ağırlıkları doğrusal regresyon modeli veya karar ağacında bir bölme noktalarını.</span><span class="sxs-lookup"><span data-stu-id="c7d40-159">For example, the weights in a linear regression model or the split points in a decision tree.</span></span> <span data-ttu-id="c7d40-160">ML.NET içinde bir modeli tahmin etmek gerekli tüm bilgileri içerir. [etiket](#label) bir etki alanı nesnesinin (örneğin, görüntü veya metin).</span><span class="sxs-lookup"><span data-stu-id="c7d40-160">In ML.NET, a model contains all the information necessary to predict the [label](#label) of a domain object (for example, image or text).</span></span> <span data-ttu-id="c7d40-161">Başka bir deyişle, ML.NET modelleri tahmin işlevi için parametre yanı sıra gerekli featurization adımları içerir.</span><span class="sxs-lookup"><span data-stu-id="c7d40-161">This means that ML.NET models include the featurization steps necessary as well as the parameters for the prediction function.</span></span>

## <a name="multiclass-classification"></a><span data-ttu-id="c7d40-162">çok sınıflı sınıflandırma</span><span class="sxs-lookup"><span data-stu-id="c7d40-162">Multiclass classification</span></span>

<span data-ttu-id="c7d40-163">A [sınıflandırma](#classification) durumda nerede [etiket](#label) üç veya daha fazla sınıf dışında biridir.</span><span class="sxs-lookup"><span data-stu-id="c7d40-163">A [classification](#classification) case where the [label](#label) is one out of three or more classes.</span></span> <span data-ttu-id="c7d40-164">Daha fazla bilgi için bkz: [çok sınıflı sınıflandırma](https://en.wikipedia.org/wiki/Multiclass_classification) makale wikipedia'da.</span><span class="sxs-lookup"><span data-stu-id="c7d40-164">For more information, see the [Multiclass classification](https://en.wikipedia.org/wiki/Multiclass_classification) article on Wikipedia.</span></span>

## <a name="n-gram"></a><span data-ttu-id="c7d40-165">N-gram</span><span class="sxs-lookup"><span data-stu-id="c7d40-165">N-gram</span></span>

<span data-ttu-id="c7d40-166">Metin verileri için bir özellik ayıklama şeması: N sözcük herhangi bir dizi kapatır içine bir [özelliği](#feature) değeri.</span><span class="sxs-lookup"><span data-stu-id="c7d40-166">A feature extraction scheme for text data: any sequence of N words turns into a [feature](#feature) value.</span></span>

## <a name="numerical-feature-vector"></a><span data-ttu-id="c7d40-167">Sayısal özellik vektör</span><span class="sxs-lookup"><span data-stu-id="c7d40-167">Numerical feature vector</span></span>

<span data-ttu-id="c7d40-168">A [özelliği](#feature) yalnızca sayısal değerleri içeren vektör.</span><span class="sxs-lookup"><span data-stu-id="c7d40-168">A [feature](#feature) vector consisting only of numerical values.</span></span> <span data-ttu-id="c7d40-169">Bu benzer `double[]`.</span><span class="sxs-lookup"><span data-stu-id="c7d40-169">This is similar to `double[]`.</span></span>

## <a name="pipeline"></a><span data-ttu-id="c7d40-170">Ardışık Düzen</span><span class="sxs-lookup"><span data-stu-id="c7d40-170">Pipeline</span></span>

<span data-ttu-id="c7d40-171">Tüm işlemlerini bir veri kümesi için bir model sığması gerekli.</span><span class="sxs-lookup"><span data-stu-id="c7d40-171">All of the operations needed to fit a model to a data set.</span></span> <span data-ttu-id="c7d40-172">Bir ardışık düzen veri içeri aktarma, dönüştürme, featurization ve adımları öğrenme oluşur.</span><span class="sxs-lookup"><span data-stu-id="c7d40-172">A pipeline consists of data import, transformation, featurization, and learning steps.</span></span> <span data-ttu-id="c7d40-173">Bir işlem hattı eğitildi sonra bir modele etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="c7d40-173">Once a pipeline is trained, it turns into a model.</span></span>

## <a name="precision"></a><span data-ttu-id="c7d40-174">Duyarlık</span><span class="sxs-lookup"><span data-stu-id="c7d40-174">Precision</span></span>

<span data-ttu-id="c7d40-175">İçinde [sınıflandırma](#classification), bir sınıf için duyarlık o sınıfın ait toplam sınıfına ait olarak tahmin öğeleri bölü sayısı gibi doğru şekilde tahmin öğelerin sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="c7d40-175">In [classification](#classification), the precision for a class is the number of items correctly predicted as belonging to that class divided by the total number of items predicted as belonging to the class.</span></span>

<span data-ttu-id="c7d40-176">İlgili ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.NegativePrecision?displayProperty=nameWithType>, <xref:Microsoft.ML.Models.BinaryClassificationMetrics.PositivePrecision?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c7d40-176">Related ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.NegativePrecision?displayProperty=nameWithType>, <xref:Microsoft.ML.Models.BinaryClassificationMetrics.PositivePrecision?displayProperty=nameWithType>.</span></span>

## <a name="recall"></a><span data-ttu-id="c7d40-177">Geri çağırma</span><span class="sxs-lookup"><span data-stu-id="c7d40-177">Recall</span></span>

<span data-ttu-id="c7d40-178">İçinde [sınıflandırma](#classification), bir sınıf için geri çağırma o sınıfın ait toplam gerçekte sınıfına ait öğeleri bölü sayısı gibi doğru şekilde tahmin öğelerin sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="c7d40-178">In [classification](#classification), the recall for a class is the number of items correctly predicted as belonging to that class divided by the total number of items that actually belong to the class.</span></span>

<span data-ttu-id="c7d40-179">İlgili ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.NegativeRecall?displayProperty=nameWithType>, <xref:Microsoft.ML.Models.BinaryClassificationMetrics.PositiveRecall?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c7d40-179">Related ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.NegativeRecall?displayProperty=nameWithType>, <xref:Microsoft.ML.Models.BinaryClassificationMetrics.PositiveRecall?displayProperty=nameWithType>.</span></span>

## <a name="regression"></a><span data-ttu-id="c7d40-180">regresyon</span><span class="sxs-lookup"><span data-stu-id="c7d40-180">Regression</span></span>

<span data-ttu-id="c7d40-181">A [denetimli makine öğrenme](#supervised-machine-learning) çıkış olduğu gerçek bir değer, örneğin, çift görev.</span><span class="sxs-lookup"><span data-stu-id="c7d40-181">A [supervised machine learning](#supervised-machine-learning) task where the output is a real value, for example, double.</span></span> <span data-ttu-id="c7d40-182">Hisse senedi fiyatları tahmin etmeye örnekler.</span><span class="sxs-lookup"><span data-stu-id="c7d40-182">Examples include predicting stock prices.</span></span>

## <a name="relative-absolute-error"></a><span data-ttu-id="c7d40-183">Göreli mutlak hata</span><span class="sxs-lookup"><span data-stu-id="c7d40-183">Relative absolute error</span></span>

<span data-ttu-id="c7d40-184">İçinde [regresyon](#regression), tüm mutlak hataların toplamıdır bir değerlendirme ölçümü bölünmüş doğru arasındaki uzaklıkları toplamına [etiket](#label) değerler ve tüm etiket değerlerini düzeltmek ortalamasını.</span><span class="sxs-lookup"><span data-stu-id="c7d40-184">In [regression](#regression), an evaluation metric that is the sum of all absolute errors divided by the sum of distances between correct [label](#label) values and the average of all correct label values.</span></span>

## <a name="relative-squared-error"></a><span data-ttu-id="c7d40-185">Göreli karesi alınmış hata</span><span class="sxs-lookup"><span data-stu-id="c7d40-185">Relative squared error</span></span>

<span data-ttu-id="c7d40-186">İçinde [regresyon](#regression), tüm toplamı bir değerlendirme ölçümü doğru arasındaki karesi alınmış uzaklıkları toplamını bölü mutlak hataların karesi alınmış [etiket](#label) değerler ve tüm etiket değerlerini düzeltmek ortalamasını.</span><span class="sxs-lookup"><span data-stu-id="c7d40-186">In [regression](#regression), an evaluation metric that is the sum of all squared absolute errors divided by the sum of squared distances between correct [label](#label) values and the average of all correct label values.</span></span>

## <a name="root-of-mean-squared-error-rmse"></a><span data-ttu-id="c7d40-187">Hata (RMSE) kök değerlerin ortalamasının kare</span><span class="sxs-lookup"><span data-stu-id="c7d40-187">Root of mean squared error (RMSE)</span></span>

<span data-ttu-id="c7d40-188">İçinde [regresyon](#regression), hataları kareleri Ortalama kare kökü bir değerlendirme ölçümü.</span><span class="sxs-lookup"><span data-stu-id="c7d40-188">In [regression](#regression), an evaluation metric that is the square root of the average of the squares of the errors.</span></span>

<span data-ttu-id="c7d40-189">İlgili ML.NET API: <xref:Microsoft.ML.Models.RegressionMetrics.Rms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c7d40-189">Related ML.NET API: <xref:Microsoft.ML.Models.RegressionMetrics.Rms?displayProperty=nameWithType>.</span></span>

## <a name="supervised-machine-learning"></a><span data-ttu-id="c7d40-190">Denetimli makine öğrenme</span><span class="sxs-lookup"><span data-stu-id="c7d40-190">Supervised machine learning</span></span>

<span data-ttu-id="c7d40-191">Machine learning istenen modeli henüz-görünmeyen veri etiketi tahmin sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="c7d40-191">A subclass of machine learning in which a desired model predicts the label for yet-unseen data.</span></span> <span data-ttu-id="c7d40-192">Sınıflandırma, regresyon ve yapılandırılmış tahmin örnek verilebilir.</span><span class="sxs-lookup"><span data-stu-id="c7d40-192">Examples include classification, regression, and structured prediction.</span></span> <span data-ttu-id="c7d40-193">Daha fazla bilgi için bkz: [denetimli öğrenme](https://en.wikipedia.org/wiki/Supervised_learning) makale wikipedia'da.</span><span class="sxs-lookup"><span data-stu-id="c7d40-193">For more information, see the  [Supervised learning](https://en.wikipedia.org/wiki/Supervised_learning) article on Wikipedia.</span></span>

## <a name="training"></a><span data-ttu-id="c7d40-194">Eğitim</span><span class="sxs-lookup"><span data-stu-id="c7d40-194">Training</span></span>

<span data-ttu-id="c7d40-195">Tanımlama işlemi bir [modeli](#model) verilen eğitim veri kümesi için.</span><span class="sxs-lookup"><span data-stu-id="c7d40-195">The process of identifying a [model](#model) for a given training data set.</span></span> <span data-ttu-id="c7d40-196">Doğrusal bir model için ağırlıkları bulma anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c7d40-196">For a linear model, this means finding the weights.</span></span> <span data-ttu-id="c7d40-197">Bir ağaç için tanımlayıcı bölme noktalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="c7d40-197">For a tree, it involves the identifying the split points.</span></span>

## <a name="transform"></a><span data-ttu-id="c7d40-198">Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="c7d40-198">Transform</span></span>

<span data-ttu-id="c7d40-199">A [ardışık düzen](#pipeline) verileri dönüştüren bileşeni.</span><span class="sxs-lookup"><span data-stu-id="c7d40-199">A [pipeline](#pipeline) component that transforms data.</span></span> <span data-ttu-id="c7d40-200">Sayıda vektör örneğin metinden.</span><span class="sxs-lookup"><span data-stu-id="c7d40-200">For example, from text to vector of numbers.</span></span>

## <a name="unsupervised-machine-learning"></a><span data-ttu-id="c7d40-201">Denetimsiz makine öğrenme</span><span class="sxs-lookup"><span data-stu-id="c7d40-201">Unsupervised machine learning</span></span>

<span data-ttu-id="c7d40-202">Machine learning istenen model verileri gizli (veya görünmeyen) yapısı bulursa sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="c7d40-202">A subclass of machine learning in which a desired model finds hidden (or latent) structure in data.</span></span> <span data-ttu-id="c7d40-203">Örnekler, kümeleme, konu modelleme ve boyut azaltma içerir.</span><span class="sxs-lookup"><span data-stu-id="c7d40-203">Examples include clustering, topic modeling, and dimensionality reduction.</span></span> <span data-ttu-id="c7d40-204">Daha fazla bilgi için bkz: [Denetimsiz öğrenme](https://en.wikipedia.org/wiki/Unsupervised_learning) makale wikipedia'da.</span><span class="sxs-lookup"><span data-stu-id="c7d40-204">For more information, see the [Unsupervised learning](https://en.wikipedia.org/wiki/Unsupervised_learning) article on Wikipedia.</span></span>
