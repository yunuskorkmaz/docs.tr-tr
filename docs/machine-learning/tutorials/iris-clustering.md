---
title: Iris çiçek bir kümeleme learner - ML.NET kullanarak küme
description: ML.NET kümeleme senaryosunda kullanmayı öğrenin
author: pkulikov
ms.author: johalex
ms.date: 07/02/2018
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 5bd73c774f60466daaf52215c34e7e17b5f5cc9c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145640"
---
# <a name="tutorial-cluster-iris-flowers-using-a-clustering-learner-with-mlnet"></a><span data-ttu-id="dbbac-103">Öğretici: Küme Iris çiçek kümeleme learner ML.NET ile kullanma</span><span class="sxs-lookup"><span data-stu-id="dbbac-103">Tutorial: Cluster iris flowers using a clustering learner with ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="dbbac-104">Bu konu şu anda Önizleme aşamasında olan ML.NET ifade eder ve malzeme değişiklik gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="dbbac-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="dbbac-105">Daha fazla bilgi için [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="dbbac-105">For more information, see the [ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="dbbac-106">Bu öğretici ML.NET oluşturmak için nasıl kullanılacağını gösterir. bir [kümeleme modelinin yerini](../resources/tasks.md#clustering) için [Iris Çiçeği veri kümesi](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span><span class="sxs-lookup"><span data-stu-id="dbbac-106">This tutorial illustrates how to use ML.NET to build a [clustering model](../resources/tasks.md#clustering) for the [iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span></span>

<span data-ttu-id="dbbac-107">Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="dbbac-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="dbbac-108">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="dbbac-108">Understand the problem</span></span>
> - <span data-ttu-id="dbbac-109">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="dbbac-109">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="dbbac-110">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="dbbac-110">Prepare the data</span></span>
> - <span data-ttu-id="dbbac-111">Yükleme ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="dbbac-111">Load and transform the data</span></span>
> - <span data-ttu-id="dbbac-112">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="dbbac-112">Choose a learning algorithm</span></span>
> - <span data-ttu-id="dbbac-113">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="dbbac-113">Train the model</span></span>
> - <span data-ttu-id="dbbac-114">Kullanım modeli tahminler elde etmek için</span><span class="sxs-lookup"><span data-stu-id="dbbac-114">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dbbac-115">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="dbbac-115">Prerequisites</span></span>

- <span data-ttu-id="dbbac-116">[Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır.</span><span class="sxs-lookup"><span data-stu-id="dbbac-116">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="dbbac-117">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="dbbac-117">Understand the problem</span></span>

<span data-ttu-id="dbbac-118">Iris çiçek çiçek özelliklere göre farklı gruplardaki kümesini bölme hakkında bu sorun oluşur.</span><span class="sxs-lookup"><span data-stu-id="dbbac-118">This problem is about dividing the set of iris flowers in different groups based on the flower features.</span></span> <span data-ttu-id="dbbac-119">Bu, genişlik ve bir sepal uzunluğu ve bir petal genişliği ve uzunluğu özellikleridir.</span><span class="sxs-lookup"><span data-stu-id="dbbac-119">Those features are the length and width of a sepal and the length and width of a petal.</span></span> <span data-ttu-id="dbbac-120">Bu öğretici için her çiçek türü bilinmiyor varsayılır.</span><span class="sxs-lookup"><span data-stu-id="dbbac-120">For this tutorial, assume that the type of each flower is unknown.</span></span> <span data-ttu-id="dbbac-121">Özellikleri bir veri kümesinden yapısını öğrenin ve bir veri örneği bu yapı nasıl uyduğunu tahmin etmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="dbbac-121">You want to learn the structure of a data set from the features and predict how a data instance fits this structure.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="dbbac-122">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="dbbac-122">Select the appropriate machine learning task</span></span>

<span data-ttu-id="dbbac-123">Her çiçek hangi gruba ait bilinmiyor olarak seçtiğiniz [Denetimsiz machine learning](../resources/glossary.md#unsupervised-machine-learning) görev.</span><span class="sxs-lookup"><span data-stu-id="dbbac-123">As you don't know to which group each flower belongs to, you choose the [unsupervised machine learning](../resources/glossary.md#unsupervised-machine-learning) task.</span></span> <span data-ttu-id="dbbac-124">Bir veri kümesi gruplarında aynı gruptaki öğelerin birbirine daha fazla benzer diğer grupları şekilde bölmek için kullanın. bir [Kümeleme](../resources/tasks.md#clustering) machine learning görev.</span><span class="sxs-lookup"><span data-stu-id="dbbac-124">To divide a data set in groups in such a way that elements in the same group are more similar to each other than to those in other groups, use a [clustering](../resources/tasks.md#clustering) machine learning task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="dbbac-125">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="dbbac-125">Create a console application</span></span>

1. <span data-ttu-id="dbbac-126">Visual Studio 2017'yi açın.</span><span class="sxs-lookup"><span data-stu-id="dbbac-126">Open Visual Studio 2017.</span></span> <span data-ttu-id="dbbac-127">Seçin **dosya** > **yeni** > **proje** menü çubuğundan.</span><span class="sxs-lookup"><span data-stu-id="dbbac-127">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="dbbac-128">İçinde **yeni proje** iletişim kutusunda **Visual C#** düğümünü ve ardından **.NET Core** düğümü.</span><span class="sxs-lookup"><span data-stu-id="dbbac-128">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="dbbac-129">Ardından **konsol uygulaması (.NET Core)** proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="dbbac-129">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="dbbac-130">İçinde **adı** metin kutusuna "IrisClustering" yazın ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="dbbac-130">In the **Name** text box, type "IrisClustering" and then select the **OK** button.</span></span>

1. <span data-ttu-id="dbbac-131">Adlı bir dizin oluşturmak *veri* projenizdeki veri kümesi ve model dosyaları depolamak için:</span><span class="sxs-lookup"><span data-stu-id="dbbac-131">Create a directory named *Data* in your project to store the data set and model files:</span></span>

    <span data-ttu-id="dbbac-132">İçinde **Çözüm Gezgini**, projeye sağ tıklayıp seçin **Ekle** > **yeni klasör**.</span><span class="sxs-lookup"><span data-stu-id="dbbac-132">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="dbbac-133">"Veri" yazın ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="dbbac-133">Type "Data" and hit Enter.</span></span>

1. <span data-ttu-id="dbbac-134">Yükleme **Microsoft.ML** NuGet paketi:</span><span class="sxs-lookup"><span data-stu-id="dbbac-134">Install the **Microsoft.ML** NuGet package:</span></span>

    <span data-ttu-id="dbbac-135">İçinde **Çözüm Gezgini**, projeye sağ tıklayıp seçin **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="dbbac-135">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="dbbac-136">Paket kaynağı, seçin "nuget.org" seçin **Gözat** sekmesinde, arama **Microsoft.ML**, listesinde o paketi seçin ve seçin **yükleme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="dbbac-136">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="dbbac-137">Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="dbbac-137">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-the-data"></a><span data-ttu-id="dbbac-138">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="dbbac-138">Prepare the data</span></span>

1. <span data-ttu-id="dbbac-139">İndirme [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) veri kümesi ve kaydetmesi *veri* önceki adımda oluşturduğunuz klasör.</span><span class="sxs-lookup"><span data-stu-id="dbbac-139">Download the [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) data set and save it to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="dbbac-140">Iris veri kümesi hakkında daha fazla bilgi için bkz. [Iris Çiçeği veri kümesi](https://en.wikipedia.org/wiki/Iris_flower_data_set) Wikipedia sayfasında ve [Iris veri kümesini](http://archive.ics.uci.edu/ml/datasets/Iris) sayfasında, veri kümesinin kaynağı.</span><span class="sxs-lookup"><span data-stu-id="dbbac-140">For more information about the iris data set, see the [Iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set) Wikipedia page and the [Iris Data Set](http://archive.ics.uci.edu/ml/datasets/Iris) page, which is the source of the data set.</span></span>

1. <span data-ttu-id="dbbac-141">İçinde **Çözüm Gezgini**, sağ *iris.data* seçin ve dosya **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="dbbac-141">In **Solution Explorer**, right-click the *iris.data* file and select **Properties**.</span></span> <span data-ttu-id="dbbac-142">Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.</span><span class="sxs-lookup"><span data-stu-id="dbbac-142">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="dbbac-143">*İris.data* dosyasını temsil eden beş sütunları içerir:</span><span class="sxs-lookup"><span data-stu-id="dbbac-143">The *iris.data* file contains five columns that represent:</span></span>

- <span data-ttu-id="dbbac-144">santimetre sepal uzunluğu</span><span class="sxs-lookup"><span data-stu-id="dbbac-144">sepal length in centimetres</span></span>
- <span data-ttu-id="dbbac-145">santimetre sepal genişliği</span><span class="sxs-lookup"><span data-stu-id="dbbac-145">sepal width in centimetres</span></span>
- <span data-ttu-id="dbbac-146">santimetre Petal uzunluğu</span><span class="sxs-lookup"><span data-stu-id="dbbac-146">petal length in centimetres</span></span>
- <span data-ttu-id="dbbac-147">santimetre Petal genişliği</span><span class="sxs-lookup"><span data-stu-id="dbbac-147">petal width in centimetres</span></span>
- <span data-ttu-id="dbbac-148">Iris çiçek türü</span><span class="sxs-lookup"><span data-stu-id="dbbac-148">type of iris flower</span></span>

<span data-ttu-id="dbbac-149">Kümeleme örnek için bu öğreticinin son sütun yok sayar.</span><span class="sxs-lookup"><span data-stu-id="dbbac-149">For the sake of the clustering example, this tutorial ignores the last column.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="dbbac-150">Veri sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="dbbac-150">Create data classes</span></span>

<span data-ttu-id="dbbac-151">Girdi verilerini ve Öngörüler için sınıflar oluşturun:</span><span class="sxs-lookup"><span data-stu-id="dbbac-151">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="dbbac-152">İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="dbbac-152">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="dbbac-153">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *IrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="dbbac-153">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *IrisData.cs*.</span></span> <span data-ttu-id="dbbac-154">Ardından, **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="dbbac-154">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="dbbac-155">Aşağıdaki `using` yönerge yeni dosya için:</span><span class="sxs-lookup"><span data-stu-id="dbbac-155">Add the following `using` directive to the new file:</span></span>

   [!code-csharp[Add necessary usings](../../../samples/machine-learning/tutorials/IrisClustering/IrisData.cs#1)]

<span data-ttu-id="dbbac-156">Varolan sınıf tanımına kaldırın ve sınıfları tanımlar aşağıdaki kodu ekleyin `IrisData` ve `ClusterPrediction`, *IrisData.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="dbbac-156">Remove the existing class definition and add the following code, which defines the classes `IrisData` and `ClusterPrediction`, to the *IrisData.cs* file:</span></span>

[!code-csharp[Define data classes](../../../samples/machine-learning/tutorials/IrisClustering/IrisData.cs#2)]

<span data-ttu-id="dbbac-157">`IrisData` giriş verisi sınıfıdır ve veri kümesindeki her bir özellik tanımı yok.</span><span class="sxs-lookup"><span data-stu-id="dbbac-157">`IrisData` is the input data class and has definitions for each feature from the data set.</span></span> <span data-ttu-id="dbbac-158">Kullanım [sütun](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) veri kümesi dosyasında kaynak sütun dizinlerini belirtmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="dbbac-158">Use the [Column](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) attribute to specify the indices of the source columns in the data set file.</span></span>

<span data-ttu-id="dbbac-159">`ClusterPrediction` Sınıfı temsil eder, uygulanan kümeleme modeli çıktısını bir `IrisData` örneği.</span><span class="sxs-lookup"><span data-stu-id="dbbac-159">The `ClusterPrediction` class represents the output of the clustering model applied to an `IrisData` instance.</span></span> <span data-ttu-id="dbbac-160">Kullanım [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) bağlanacak öznitelik `PredictedClusterId` ve `Distances` alanlarını **PredictedLabel** ve **puanı** sütunları sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="dbbac-160">Use the [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) attribute to bind the `PredictedClusterId` and `Distances` fields to the **PredictedLabel** and **Score** columns respectively.</span></span> <span data-ttu-id="dbbac-161">Kümeleme görev olması durumunda bu sütun şu anlama gelir:</span><span class="sxs-lookup"><span data-stu-id="dbbac-161">In case of the clustering task those columns have the following meaning:</span></span>

- <span data-ttu-id="dbbac-162">**PredictedLabel** sütun tahmin edilen kümenin Kimliğini içerir.</span><span class="sxs-lookup"><span data-stu-id="dbbac-162">**PredictedLabel** column contains the ID of the predicted cluster.</span></span>
- <span data-ttu-id="dbbac-163">**Puan** küme centroids için kare Euclidean uzaklığa sahip bir dizi sütun içerir.</span><span class="sxs-lookup"><span data-stu-id="dbbac-163">**Score** column contains an array with squared Euclidean distances to the cluster centroids.</span></span> <span data-ttu-id="dbbac-164">Dizi uzunluğu küme sayısı eşittir.</span><span class="sxs-lookup"><span data-stu-id="dbbac-164">The array length is equal to the number of clusters.</span></span>

> [!NOTE]
> <span data-ttu-id="dbbac-165">Kullanım `float` giriş ve tahmin verilerini sınıflardaki kayan nokta değerlerini temsil eden tür.</span><span class="sxs-lookup"><span data-stu-id="dbbac-165">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="dbbac-166">Veri ve model tanımlar</span><span class="sxs-lookup"><span data-stu-id="dbbac-166">Define data and model paths</span></span>

<span data-ttu-id="dbbac-167">Geri Git *Program.cs* dosya ve veri kümesi dosyasını ve modeli kaydedin ve dosyaya yolları tutmak için iki alanları ekleyin:</span><span class="sxs-lookup"><span data-stu-id="dbbac-167">Go back to the *Program.cs* file and add two fields to hold the paths to the data set file and to the file to save the model:</span></span>

- <span data-ttu-id="dbbac-168">`_dataPath` modeli eğitmek için kullanılan veri kümesiyle dosyasının yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="dbbac-168">`_dataPath` contains the path to the file with the data set used to train the model.</span></span>
- <span data-ttu-id="dbbac-169">`_modelPath` eğitilen modelin depolandığı dosya yolu içerir.</span><span class="sxs-lookup"><span data-stu-id="dbbac-169">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="dbbac-170">Aşağıdaki kod üzerinde doğru `Main` yöntemi bu yollarını belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="dbbac-170">Add the following code right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Initialize paths](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#1)]

<span data-ttu-id="dbbac-171">Derleme, aşağıdaki ekleyin önceki kodun `using` üst kısmındaki yönergeleri *Program.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="dbbac-171">To make the preceding code compile, add the following `using` directives at the top of the *Program.cs* file:</span></span>

[!code-csharp[Add usings for paths](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#2)]

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="dbbac-172">Öğrenme işlem hattı oluşturma</span><span class="sxs-lookup"><span data-stu-id="dbbac-172">Create a learning pipeline</span></span>

<span data-ttu-id="dbbac-173">Aşağıdaki ek ekleyin `using` yönergeleri üstüne *Program.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="dbbac-173">Add the following additional `using` directives to the top of the *Program.cs* file:</span></span>

[!code-csharp[Add Microsoft.ML usings](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#3)]

<span data-ttu-id="dbbac-174">İçinde `Main` yöntemi Değiştir `Console.WriteLine("Hello World!")` aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="dbbac-174">In the `Main` method, replace the `Console.WriteLine("Hello World!")` with the following code:</span></span>

[!code-csharp[Call the Train method](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#4)]

<span data-ttu-id="dbbac-175">`Train` Yöntemi modeli eğitir.</span><span class="sxs-lookup"><span data-stu-id="dbbac-175">The `Train` method trains the model.</span></span> <span data-ttu-id="dbbac-176">Bu yöntem oluşturma hemen altına `Main` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="dbbac-176">Create that method just below the `Main` method, using the following code:</span></span>

```csharp
private static PredictionModel<IrisData, ClusterPrediction> Train()
{

}
```

<span data-ttu-id="dbbac-177">Öğrenme işlem hattınızı tüm veri ve algoritmaları modeli eğitmek gerekli yükler.</span><span class="sxs-lookup"><span data-stu-id="dbbac-177">The learning pipeline loads all of the data and algorithms necessary to train the model.</span></span> <span data-ttu-id="dbbac-178">Aşağıdaki kodu ekleyin `Train` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="dbbac-178">Add the following code into the `Train` method:</span></span>

[!code-csharp[Initialize pipeline](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#5)]

## <a name="load-and-transform-data"></a><span data-ttu-id="dbbac-179">Veri yükleme ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="dbbac-179">Load and transform data</span></span>

<span data-ttu-id="dbbac-180">İlk adımı gerçekleştirmek için eğitim veri kümesine yüklenmesidir.</span><span class="sxs-lookup"><span data-stu-id="dbbac-180">The first step to perform is to load the training data set.</span></span> <span data-ttu-id="dbbac-181">Bu örnekte, tarafından tanımlanan bir yol ile metin dosyasında eğitim veri kümesi depolanır `_dataPath` alan.</span><span class="sxs-lookup"><span data-stu-id="dbbac-181">In our case, the training data set is stored in the text file with a path defined by the `_dataPath` field.</span></span> <span data-ttu-id="dbbac-182">Bir dosyadaki sütunları virgülle ayrılmış (",").</span><span class="sxs-lookup"><span data-stu-id="dbbac-182">Columns in the file are separated by the comma (",").</span></span> <span data-ttu-id="dbbac-183">Aşağıdaki kodu ekleyin `Train` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="dbbac-183">Add the following code into the `Train` method:</span></span>

[!code-csharp[Add step to load data](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#6)]

<span data-ttu-id="dbbac-184">Tüm özellik sütunlar birleştirmek için sonraki adımdır **özellikleri** sütun kullanarak <xref:Microsoft.ML.Legacy.Transforms.ColumnConcatenator> dönüştürme sınıfı.</span><span class="sxs-lookup"><span data-stu-id="dbbac-184">The next step is to combine all of the feature columns into the **Features** column using the <xref:Microsoft.ML.Legacy.Transforms.ColumnConcatenator> transformation class.</span></span> <span data-ttu-id="dbbac-185">Varsayılan olarak, bir öğrenme algoritması yalnızca özelliklerinden işler **özellikleri** sütun.</span><span class="sxs-lookup"><span data-stu-id="dbbac-185">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="dbbac-186">Aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="dbbac-186">Add the following code:</span></span>

[!code-csharp[Add step to concatenate columns](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#7)]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="dbbac-187">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="dbbac-187">Choose a learning algorithm</span></span>

<span data-ttu-id="dbbac-188">Veri ardışık düzenine eklemek ve giriş doğru biçime dönüştürme sonra bir öğrenme algoritması seçin (**learner**).</span><span class="sxs-lookup"><span data-stu-id="dbbac-188">After adding the data to the pipeline and transforming it into the correct input format, you select a learning algorithm (**learner**).</span></span> <span data-ttu-id="dbbac-189">Learner modeli eğitir.</span><span class="sxs-lookup"><span data-stu-id="dbbac-189">The learner trains the model.</span></span> <span data-ttu-id="dbbac-190">ML.NET sağlayan bir <xref:Microsoft.ML.Legacy.Trainers.KMeansPlusPlusClusterer> uygulayan learner [k-ortalamaları algoritması](https://en.wikipedia.org/wiki/K-means_clustering) ilk küme centroids seçmeye yönelik geliştirilmiş bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="dbbac-190">ML.NET provides a <xref:Microsoft.ML.Legacy.Trainers.KMeansPlusPlusClusterer> learner that implements [k-means algorithm](https://en.wikipedia.org/wiki/K-means_clustering) with an improved method for choosing the initial cluster centroids.</span></span>

<span data-ttu-id="dbbac-191">Aşağıdaki kodu ekleyin `Train` önceki adımda eklenen koddan veri işleme yöntemi:</span><span class="sxs-lookup"><span data-stu-id="dbbac-191">Add the following code into the `Train` method following the data processing code added in the previous step:</span></span>

[!code-csharp[Add a learner step](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#8)]

<span data-ttu-id="dbbac-192">Kullanım <xref:Microsoft.ML.Legacy.Trainers.KMeansPlusPlusClusterer.K?displayProperty=nameWithType> özellik kümeleri sayısını belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="dbbac-192">Use the <xref:Microsoft.ML.Legacy.Trainers.KMeansPlusPlusClusterer.K?displayProperty=nameWithType> property to specify number of clusters.</span></span> <span data-ttu-id="dbbac-193">Yukarıdaki kod, veri kümesi üç kümelerinde ayrılmalıdır belirtir.</span><span class="sxs-lookup"><span data-stu-id="dbbac-193">The code above specifies that the data set should be split in three clusters.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="dbbac-194">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="dbbac-194">Train the model</span></span>

<span data-ttu-id="dbbac-195">Önceki bölümde eklediğiniz adımlar eğitim için ardışık düzen hazır, ancak hiçbiri yürütüldüğünü.</span><span class="sxs-lookup"><span data-stu-id="dbbac-195">The steps added in the preceding sections prepared the pipeline for training, however, none have been executed.</span></span> <span data-ttu-id="dbbac-196">`pipeline.Train<TInput, TOutput>` Yöntemi üreten bir örneğini alan modeli `TInput` türü ve örneği çıkaran `TOutput` türü.</span><span class="sxs-lookup"><span data-stu-id="dbbac-196">The `pipeline.Train<TInput, TOutput>` method produces the model that takes in an instance of the `TInput` type and outputs an instance of the `TOutput` type.</span></span> <span data-ttu-id="dbbac-197">Aşağıdaki kodu ekleyin `Train` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="dbbac-197">Add the following code into the `Train` method:</span></span>

[!code-csharp[Train the model and return](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#9)]

### <a name="save-the-model"></a><span data-ttu-id="dbbac-198">Modeli kaydedin</span><span class="sxs-lookup"><span data-stu-id="dbbac-198">Save the model</span></span>

<span data-ttu-id="dbbac-199">Bu noktada, tüm mevcut veya yeni .NET uygulamalarınızı tümleşik bir model var.</span><span class="sxs-lookup"><span data-stu-id="dbbac-199">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="dbbac-200">Modelinizi bir .zip dosyası olarak kaydetmek için aşağıdaki kodu ekleyin. `Main` çağrının altına yöntemi `Train` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="dbbac-200">To save your model to a .zip file, add the following code to the `Main` method below the call to the `Train` method:</span></span>

[!code-csharp[Save the model](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#10)]

<span data-ttu-id="dbbac-201">Kullanarak `await` içinde `Main` yöntemi anlamına gelir `Main` yöntemi olmalıdır `async` değiştiricisi ve dönüş bir `Task`:</span><span class="sxs-lookup"><span data-stu-id="dbbac-201">Using `await` in the `Main` method means the `Main` method must have the `async` modifier and return a `Task`:</span></span>

[!code-csharp[Make the Main method async](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#11)]

<span data-ttu-id="dbbac-202">Ayrıca aşağıdakileri eklemeniz gerekir `using` en üstündeki yönerge *Program.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="dbbac-202">You also need to add the following `using` directive at the top of the *Program.cs* file:</span></span>

[!code-csharp[Add System.Threading.Tasks using](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#12)]

<span data-ttu-id="dbbac-203">Çünkü `async Main` yöntemi, C# 7.1 eklenen özelliğidir ve C# 7.0 projesi varsayılan dil sürümü değil, C# 7.1 veya üzeri dil sürümünü değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="dbbac-203">Because the `async Main` method is the feature added in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span> <span data-ttu-id="dbbac-204">Bunu yapmak için'nde proje düğümüne sağ **Çözüm Gezgini** seçip **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="dbbac-204">To do that, right-click the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="dbbac-205">Seçin **derleme** sekmenize **Gelişmiş** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="dbbac-205">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="dbbac-206">Açılır menüden seçin **C# 7.1** (veya üzeri bir sürüm).</span><span class="sxs-lookup"><span data-stu-id="dbbac-206">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="dbbac-207">**Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="dbbac-207">Select the **OK** button.</span></span>

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="dbbac-208">Kullanım modeli tahminler elde etmek için</span><span class="sxs-lookup"><span data-stu-id="dbbac-208">Use the model for predictions</span></span>

<span data-ttu-id="dbbac-209">Oluşturma `TestIrisData` ev test veri örnekleri sınıfı:</span><span class="sxs-lookup"><span data-stu-id="dbbac-209">Create the `TestIrisData` class to house test data instances:</span></span>

1. <span data-ttu-id="dbbac-210">İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="dbbac-210">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="dbbac-211">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *TestIrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="dbbac-211">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestIrisData.cs*.</span></span> <span data-ttu-id="dbbac-212">Ardından, **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="dbbac-212">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="dbbac-213">Sınıfı gibi aşağıdaki örnekte de statik olarak değiştirin:</span><span class="sxs-lookup"><span data-stu-id="dbbac-213">Modify the class to be static like in the following example:</span></span>

   [!code-csharp[Make class static](../../../samples/machine-learning/tutorials/IrisClustering/TestIrisData.cs#1)]

<span data-ttu-id="dbbac-214">Bu öğretici, bu sınıf içinde bir Iris veri örneği tanıtır.</span><span class="sxs-lookup"><span data-stu-id="dbbac-214">This tutorial introduces one iris data instance within this class.</span></span> <span data-ttu-id="dbbac-215">Modelle denemek için diğer senaryolar ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dbbac-215">You can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="dbbac-216">Aşağıdaki kodu ekleyin `TestIrisData` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="dbbac-216">Add the following code into the `TestIrisData` class:</span></span>

[!code-csharp[Test data](../../../samples/machine-learning/tutorials/IrisClustering/TestIrisData.cs#2)]

<span data-ttu-id="dbbac-217">Belirtilen öğenin ait olduğu küme öğrenmek için geri dön *Program.cs* dosya ve içine aşağıdaki kodu ekleyin `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="dbbac-217">To find out the cluster to which the specified item belongs to, go back to the *Program.cs* file and add the following code into the `Main` method:</span></span>

[!code-csharp[Predict and output results](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#13)]

<span data-ttu-id="dbbac-218">Belirtilen veri örneği ve bu örneğe karesini uzaklıkta küme centroids için hangi küme içerip programı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="dbbac-218">Run the program to see which cluster contains the specified data instance and squared distances from that instance to the cluster centroids.</span></span> <span data-ttu-id="dbbac-219">Sonuçlar aşağıdakine benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dbbac-219">Your results should be similar to the following.</span></span> <span data-ttu-id="dbbac-220">İşlem hattı işlerken bir uyarı veya iletilerini işleme görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="dbbac-220">As the pipeline processes, it might display warnings or processing messages.</span></span> <span data-ttu-id="dbbac-221">Bunlar aşağıdaki çıktıya anlaşılması için kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="dbbac-221">These have been removed from the following output for clarity.</span></span>

```text
Cluster: 2
Distances: 0.4192338 0.0008847713 0.9660053
```

<span data-ttu-id="dbbac-222">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="dbbac-222">Congratulations!</span></span> <span data-ttu-id="dbbac-223">Bir machine learning modeli için kümeleme ve tahminlerde bulunmak üzere kullanılan Iris artık başarıyla oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="dbbac-223">You've now successfully built a machine learning model for iris clustering and used it to make predictions.</span></span> <span data-ttu-id="dbbac-224">Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisClustering) GitHub deposu.</span><span class="sxs-lookup"><span data-stu-id="dbbac-224">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisClustering) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="dbbac-225">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="dbbac-225">Next steps</span></span>

<span data-ttu-id="dbbac-226">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="dbbac-226">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="dbbac-227">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="dbbac-227">Understand the problem</span></span>
> - <span data-ttu-id="dbbac-228">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="dbbac-228">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="dbbac-229">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="dbbac-229">Prepare the data</span></span>
> - <span data-ttu-id="dbbac-230">Yükleme ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="dbbac-230">Load and transform the data</span></span>
> - <span data-ttu-id="dbbac-231">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="dbbac-231">Choose a learning algorithm</span></span>
> - <span data-ttu-id="dbbac-232">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="dbbac-232">Train the model</span></span>
> - <span data-ttu-id="dbbac-233">Kullanım modeli tahminler elde etmek için</span><span class="sxs-lookup"><span data-stu-id="dbbac-233">Use the model for predictions</span></span>

<span data-ttu-id="dbbac-234">Almaya devam etmek ve diğer örnekleri bulmak için GitHub depomuza denetleyin.</span><span class="sxs-lookup"><span data-stu-id="dbbac-234">Check out our GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="dbbac-235">DotNet/machinelearning GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="dbbac-235">dotnet/machinelearning GitHub repository</span></span>](https://github.com/dotnet/machinelearning/)
