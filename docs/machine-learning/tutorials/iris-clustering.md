---
title: Iris çiçek bir kümeleme learner - ML.NET kullanarak küme
description: ML.NET kümeleme senaryosunda kullanmayı öğrenin
author: pkulikov
ms.author: johalex
ms.date: 01/11/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: ab888a2cd9469d5ce0131ba2b17f7c134cf2855c
ms.sourcegitcommit: 81bd16c7435a8c9183d2a7e878a2a5eff7d04584
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2019
ms.locfileid: "54249079"
---
# <a name="tutorial-cluster-iris-flowers-using-a-clustering-learner-with-mlnet"></a><span data-ttu-id="c6c93-103">Öğretici: Küme Iris çiçek kümeleme learner ML.NET ile kullanma</span><span class="sxs-lookup"><span data-stu-id="c6c93-103">Tutorial: Cluster iris flowers using a clustering learner with ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="c6c93-104">Bu konu şu anda Önizleme aşamasında olan ML.NET ifade eder ve malzeme değişiklik gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="c6c93-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="c6c93-105">Daha fazla bilgi için [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="c6c93-105">For more information, see the [ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="c6c93-106">Bu öğretici ML.NET oluşturmak için nasıl kullanılacağını gösterir. bir [kümeleme modelinin yerini](../resources/tasks.md#clustering) için [Iris Çiçeği veri kümesi](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span><span class="sxs-lookup"><span data-stu-id="c6c93-106">This tutorial illustrates how to use ML.NET to build a [clustering model](../resources/tasks.md#clustering) for the [iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span></span>

<span data-ttu-id="c6c93-107">Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="c6c93-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="c6c93-108">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="c6c93-108">Understand the problem</span></span>
> - <span data-ttu-id="c6c93-109">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="c6c93-109">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="c6c93-110">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="c6c93-110">Prepare the data</span></span>
> - <span data-ttu-id="c6c93-111">Yükleme ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="c6c93-111">Load and transform the data</span></span>
> - <span data-ttu-id="c6c93-112">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="c6c93-112">Choose a learning algorithm</span></span>
> - <span data-ttu-id="c6c93-113">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="c6c93-113">Train the model</span></span>
> - <span data-ttu-id="c6c93-114">Kullanım modeli tahminler elde etmek için</span><span class="sxs-lookup"><span data-stu-id="c6c93-114">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c6c93-115">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="c6c93-115">Prerequisites</span></span>

- <span data-ttu-id="c6c93-116">[Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır.</span><span class="sxs-lookup"><span data-stu-id="c6c93-116">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="c6c93-117">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="c6c93-117">Understand the problem</span></span>

<span data-ttu-id="c6c93-118">Iris çiçek çiçek özelliklere göre farklı gruplardaki kümesini bölme hakkında bu sorun oluşur.</span><span class="sxs-lookup"><span data-stu-id="c6c93-118">This problem is about dividing the set of iris flowers in different groups based on the flower features.</span></span> <span data-ttu-id="c6c93-119">Bu, genişlik ve bir sepal uzunluğu ve bir petal genişliği ve uzunluğu özellikleridir.</span><span class="sxs-lookup"><span data-stu-id="c6c93-119">Those features are the length and width of a sepal and the length and width of a petal.</span></span> <span data-ttu-id="c6c93-120">Bu öğretici için her çiçek türü bilinmiyor varsayılır.</span><span class="sxs-lookup"><span data-stu-id="c6c93-120">For this tutorial, assume that the type of each flower is unknown.</span></span> <span data-ttu-id="c6c93-121">Özellikleri bir veri kümesinden yapısını öğrenin ve bir veri örneği bu yapı nasıl uyduğunu tahmin etmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="c6c93-121">You want to learn the structure of a data set from the features and predict how a data instance fits this structure.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="c6c93-122">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="c6c93-122">Select the appropriate machine learning task</span></span>

<span data-ttu-id="c6c93-123">Her çiçek hangi gruba ait bilinmiyor olarak seçtiğiniz [Denetimsiz machine learning](../resources/glossary.md#unsupervised-machine-learning) görev.</span><span class="sxs-lookup"><span data-stu-id="c6c93-123">As you don't know to which group each flower belongs to, you choose the [unsupervised machine learning](../resources/glossary.md#unsupervised-machine-learning) task.</span></span> <span data-ttu-id="c6c93-124">Bir veri kümesi gruplarında aynı gruptaki öğelerin birbirine daha fazla benzer diğer grupları şekilde bölmek için kullanın. bir [Kümeleme](../resources/tasks.md#clustering) machine learning görev.</span><span class="sxs-lookup"><span data-stu-id="c6c93-124">To divide a data set in groups in such a way that elements in the same group are more similar to each other than to those in other groups, use a [clustering](../resources/tasks.md#clustering) machine learning task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="c6c93-125">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="c6c93-125">Create a console application</span></span>

1. <span data-ttu-id="c6c93-126">Visual Studio 2017'yi açın.</span><span class="sxs-lookup"><span data-stu-id="c6c93-126">Open Visual Studio 2017.</span></span> <span data-ttu-id="c6c93-127">Seçin **dosya** > **yeni** > **proje** menü çubuğundan.</span><span class="sxs-lookup"><span data-stu-id="c6c93-127">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="c6c93-128">İçinde **yeni proje** iletişim kutusunda **Visual C#** düğümünü ve ardından **.NET Core** düğümü.</span><span class="sxs-lookup"><span data-stu-id="c6c93-128">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="c6c93-129">Ardından **konsol uygulaması (.NET Core)** proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="c6c93-129">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="c6c93-130">İçinde **adı** metin kutusuna "IrisFlowerClustering" yazın ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="c6c93-130">In the **Name** text box, type "IrisFlowerClustering" and then select the **OK** button.</span></span>

1. <span data-ttu-id="c6c93-131">Adlı bir dizin oluşturmak *veri* projenizdeki veri kümesi ve model dosyaları depolamak için:</span><span class="sxs-lookup"><span data-stu-id="c6c93-131">Create a directory named *Data* in your project to store the data set and model files:</span></span>

    <span data-ttu-id="c6c93-132">İçinde **Çözüm Gezgini**, projeye sağ tıklayıp seçin **Ekle** > **yeni klasör**.</span><span class="sxs-lookup"><span data-stu-id="c6c93-132">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="c6c93-133">"Veri" yazın ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c6c93-133">Type "Data" and hit Enter.</span></span>

1. <span data-ttu-id="c6c93-134">Yükleme **Microsoft.ML** NuGet paketi:</span><span class="sxs-lookup"><span data-stu-id="c6c93-134">Install the **Microsoft.ML** NuGet package:</span></span>

    <span data-ttu-id="c6c93-135">İçinde **Çözüm Gezgini**, projeye sağ tıklayıp seçin **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="c6c93-135">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="c6c93-136">Paket kaynağı, seçin "nuget.org" seçin **Gözat** sekmesinde, arama **Microsoft.ML**, listesinde o paketi seçin ve seçin **yükleme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="c6c93-136">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="c6c93-137">Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="c6c93-137">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-the-data"></a><span data-ttu-id="c6c93-138">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="c6c93-138">Prepare the data</span></span>

1. <span data-ttu-id="c6c93-139">İndirme [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) veri kümesi ve kaydetmesi *veri* önceki adımda oluşturduğunuz klasör.</span><span class="sxs-lookup"><span data-stu-id="c6c93-139">Download the [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) data set and save it to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="c6c93-140">Iris veri kümesi hakkında daha fazla bilgi için bkz. [Iris Çiçeği veri kümesi](https://en.wikipedia.org/wiki/Iris_flower_data_set) Wikipedia sayfasında ve [Iris veri kümesini](https://archive.ics.uci.edu/ml/datasets/Iris) sayfasında, veri kümesinin kaynağı.</span><span class="sxs-lookup"><span data-stu-id="c6c93-140">For more information about the iris data set, see the [Iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set) Wikipedia page and the [Iris Data Set](https://archive.ics.uci.edu/ml/datasets/Iris) page, which is the source of the data set.</span></span>

1. <span data-ttu-id="c6c93-141">İçinde **Çözüm Gezgini**, sağ *iris.data* seçin ve dosya **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="c6c93-141">In **Solution Explorer**, right-click the *iris.data* file and select **Properties**.</span></span> <span data-ttu-id="c6c93-142">Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.</span><span class="sxs-lookup"><span data-stu-id="c6c93-142">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="c6c93-143">*İris.data* dosyasını temsil eden beş sütunları içerir:</span><span class="sxs-lookup"><span data-stu-id="c6c93-143">The *iris.data* file contains five columns that represent:</span></span>

- <span data-ttu-id="c6c93-144">santimetre sepal uzunluğu</span><span class="sxs-lookup"><span data-stu-id="c6c93-144">sepal length in centimetres</span></span>
- <span data-ttu-id="c6c93-145">santimetre sepal genişliği</span><span class="sxs-lookup"><span data-stu-id="c6c93-145">sepal width in centimetres</span></span>
- <span data-ttu-id="c6c93-146">santimetre Petal uzunluğu</span><span class="sxs-lookup"><span data-stu-id="c6c93-146">petal length in centimetres</span></span>
- <span data-ttu-id="c6c93-147">santimetre Petal genişliği</span><span class="sxs-lookup"><span data-stu-id="c6c93-147">petal width in centimetres</span></span>
- <span data-ttu-id="c6c93-148">Iris çiçek türü</span><span class="sxs-lookup"><span data-stu-id="c6c93-148">type of iris flower</span></span>

<span data-ttu-id="c6c93-149">Kümeleme örnek için bu öğreticinin son sütun yok sayar.</span><span class="sxs-lookup"><span data-stu-id="c6c93-149">For the sake of the clustering example, this tutorial ignores the last column.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="c6c93-150">Veri sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="c6c93-150">Create data classes</span></span>

<span data-ttu-id="c6c93-151">Girdi verilerini ve Öngörüler için sınıflar oluşturun:</span><span class="sxs-lookup"><span data-stu-id="c6c93-151">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="c6c93-152">İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="c6c93-152">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="c6c93-153">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *IrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="c6c93-153">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *IrisData.cs*.</span></span> <span data-ttu-id="c6c93-154">Ardından, **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="c6c93-154">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="c6c93-155">Aşağıdaki `using` yönerge yeni dosya için:</span><span class="sxs-lookup"><span data-stu-id="c6c93-155">Add the following `using` directive to the new file:</span></span>

   [!code-csharp[Add necessary usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#Usings)]

<span data-ttu-id="c6c93-156">Varolan sınıf tanımına kaldırın ve sınıfları tanımlar aşağıdaki kodu ekleyin `IrisData` ve `ClusterPrediction`, *IrisData.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="c6c93-156">Remove the existing class definition and add the following code, which defines the classes `IrisData` and `ClusterPrediction`, to the *IrisData.cs* file:</span></span>

[!code-csharp[Define data classes](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#ClassDefinitions)]

<span data-ttu-id="c6c93-157">`IrisData` giriş verisi sınıfıdır ve veri kümesindeki her bir özellik tanımı yok.</span><span class="sxs-lookup"><span data-stu-id="c6c93-157">`IrisData` is the input data class and has definitions for each feature from the data set.</span></span> <span data-ttu-id="c6c93-158">Kullanım [sütun](xref:Microsoft.ML.Data.ColumnAttribute) veri kümesi dosyasında kaynak sütun dizinlerini belirtmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c6c93-158">Use the [Column](xref:Microsoft.ML.Data.ColumnAttribute) attribute to specify the indices of the source columns in the data set file.</span></span>

<span data-ttu-id="c6c93-159">`ClusterPrediction` Sınıfı temsil eder, uygulanan kümeleme modeli çıktısını bir `IrisData` örneği.</span><span class="sxs-lookup"><span data-stu-id="c6c93-159">The `ClusterPrediction` class represents the output of the clustering model applied to an `IrisData` instance.</span></span> <span data-ttu-id="c6c93-160">Kullanım [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) bağlanacak öznitelik `PredictedClusterId` ve `Distances` alanlarını **PredictedLabel** ve **puanı** sütunları sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="c6c93-160">Use the [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute to bind the `PredictedClusterId` and `Distances` fields to the **PredictedLabel** and **Score** columns respectively.</span></span> <span data-ttu-id="c6c93-161">Kümeleme görev olması durumunda bu sütun şu anlama gelir:</span><span class="sxs-lookup"><span data-stu-id="c6c93-161">In case of the clustering task those columns have the following meaning:</span></span>

- <span data-ttu-id="c6c93-162">**PredictedLabel** sütun tahmin edilen kümenin Kimliğini içerir.</span><span class="sxs-lookup"><span data-stu-id="c6c93-162">**PredictedLabel** column contains the ID of the predicted cluster.</span></span>
- <span data-ttu-id="c6c93-163">**Puan** küme centroids için kare Euclidean uzaklığa sahip bir dizi sütun içerir.</span><span class="sxs-lookup"><span data-stu-id="c6c93-163">**Score** column contains an array with squared Euclidean distances to the cluster centroids.</span></span> <span data-ttu-id="c6c93-164">Dizi uzunluğu küme sayısı eşittir.</span><span class="sxs-lookup"><span data-stu-id="c6c93-164">The array length is equal to the number of clusters.</span></span>

> [!NOTE]
> <span data-ttu-id="c6c93-165">Kullanım `float` giriş ve tahmin verilerini sınıflardaki kayan nokta değerlerini temsil eden tür.</span><span class="sxs-lookup"><span data-stu-id="c6c93-165">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="c6c93-166">Veri ve model tanımlar</span><span class="sxs-lookup"><span data-stu-id="c6c93-166">Define data and model paths</span></span>

<span data-ttu-id="c6c93-167">Geri Git *Program.cs* dosya ve veri kümesi dosyasını ve modeli kaydedin ve dosyaya yolları tutmak için iki alanları ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c6c93-167">Go back to the *Program.cs* file and add two fields to hold the paths to the data set file and to the file to save the model:</span></span>

- <span data-ttu-id="c6c93-168">`_dataPath` modeli eğitmek için kullanılan veri kümesiyle dosyasının yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="c6c93-168">`_dataPath` contains the path to the file with the data set used to train the model.</span></span>
- <span data-ttu-id="c6c93-169">`_modelPath` eğitilen modelin depolandığı dosya yolu içerir.</span><span class="sxs-lookup"><span data-stu-id="c6c93-169">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="c6c93-170">Aşağıdaki kod üzerinde doğru `Main` yöntemi bu yollarını belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="c6c93-170">Add the following code right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Initialize paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Paths)]

<span data-ttu-id="c6c93-171">Derleme, aşağıdaki ekleyin önceki kodun `using` üst kısmındaki yönergeleri *Program.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="c6c93-171">To make the preceding code compile, add the following `using` directives at the top of the *Program.cs* file:</span></span>

[!code-csharp[Add usings for paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a><span data-ttu-id="c6c93-172">ML bağlamı oluşturur</span><span class="sxs-lookup"><span data-stu-id="c6c93-172">Create ML context</span></span>

<span data-ttu-id="c6c93-173">Aşağıdaki ek ekleyin `using` yönergeleri üstüne *Program.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="c6c93-173">Add the following additional `using` directives to the top of the *Program.cs* file:</span></span>

[!code-csharp[Add Microsoft.ML usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#MLUsings)]

<span data-ttu-id="c6c93-174">İçinde `Main` yöntemi Değiştir `Console.WriteLine("Hello World!");` satırı aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="c6c93-174">In the `Main` method, replace the `Console.WriteLine("Hello World!");` line with the following code:</span></span>

[!code-csharp[Create ML context](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateContext)]

<span data-ttu-id="c6c93-175"><xref:Microsoft.ML.MLContext?displayProperty=nameWithType> Sınıf makine öğrenimi ortamını temsil eden ve veri yükleme, model eğitiminin, tahmin ve diğer görevler için günlüğü ve giriş noktaları için mekanizmaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="c6c93-175">The <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> class represents the machine learning environment and provides mechanisms for logging and entry points for data loading, model training, prediction, and other tasks.</span></span> <span data-ttu-id="c6c93-176">Bu kavramsal olarak kullanarak karşılaştırılabilir `DbContext` Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="c6c93-176">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span>

## <a name="setup-data-loading"></a><span data-ttu-id="c6c93-177">Veri yükleme kurulumu</span><span class="sxs-lookup"><span data-stu-id="c6c93-177">Setup data loading</span></span>

<span data-ttu-id="c6c93-178">Aşağıdaki kodu ekleyin `Main` yöntemi veri yükleme şekilde ayarlamak için:</span><span class="sxs-lookup"><span data-stu-id="c6c93-178">Add the following code to the `Main` method to setup the way to load data:</span></span>

[!code-csharp[Create text loader](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#SetupTextLoader)]

<span data-ttu-id="c6c93-179">Sütun adları ve dizinlerini tarafından tanımlanan şema eşleştiğini Not `IrisData` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c6c93-179">Note that the column names and indices match the schema defined by the `IrisData` class.</span></span> <span data-ttu-id="c6c93-180"><xref:Microsoft.ML.Data.DataKind.R4?displayProperty=nameWithType> Değeri belirtir `float` türü.</span><span class="sxs-lookup"><span data-stu-id="c6c93-180">The <xref:Microsoft.ML.Data.DataKind.R4?displayProperty=nameWithType> value specifies the `float` type.</span></span>

<span data-ttu-id="c6c93-181">Kullanım örneği <xref:Microsoft.ML.Data.TextLoader> oluşturmak için örnek bir <xref:Microsoft.ML.Data.IDataView> temsil eden bir eğitim veri kümesi için veri kaynağı örneği:</span><span class="sxs-lookup"><span data-stu-id="c6c93-181">Use instantiated <xref:Microsoft.ML.Data.TextLoader> instance to create an <xref:Microsoft.ML.Data.IDataView> instance, which represents the data source for the training data set:</span></span>

[!code-csharp[Create IDataView](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateDataView)]

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="c6c93-182">Öğrenme işlem hattı oluşturma</span><span class="sxs-lookup"><span data-stu-id="c6c93-182">Create a learning pipeline</span></span>

<span data-ttu-id="c6c93-183">Bu öğreticide, öğrenme işlem hattınızı kümeleme görevin aşağıdaki iki adımdan oluşur:</span><span class="sxs-lookup"><span data-stu-id="c6c93-183">For this tutorial, the learning pipeline of the clustering task comprises two following steps:</span></span>

- <span data-ttu-id="c6c93-184">yüklenen sütunu bir birleştirme **özellikleri** kümeleme Eğitmen tarafından; kullanılan sütun</span><span class="sxs-lookup"><span data-stu-id="c6c93-184">concatenate loaded columns into one **Features** column, which is used by a clustering trainer;</span></span>
- <span data-ttu-id="c6c93-185">kullanan bir <xref:Microsoft.ML.Trainers.KMeans.KMeansPlusPlusTrainer> k kullanarak modeli eğitmek için Eğitmen-anlamına gelir ++ kümeleme algoritması.</span><span class="sxs-lookup"><span data-stu-id="c6c93-185">use a <xref:Microsoft.ML.Trainers.KMeans.KMeansPlusPlusTrainer> trainer to train the model using the k-means++ clustering algorithm.</span></span>

<span data-ttu-id="c6c93-186">Aşağıdaki kodu ekleyin `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="c6c93-186">Add the following code to the `Main` method:</span></span>

[!code-csharp[Create pipeline](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreatePipeline)]

<span data-ttu-id="c6c93-187">Kod üç kümelerinde veri kümesi ayrılmalıdır belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6c93-187">The code specifies that the data set should be split in three clusters.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="c6c93-188">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="c6c93-188">Train the model</span></span>

<span data-ttu-id="c6c93-189">Önceki bölümde eklediğiniz adımlar eğitim için ardışık düzen hazır, ancak hiçbiri yürütüldüğünü.</span><span class="sxs-lookup"><span data-stu-id="c6c93-189">The steps added in the preceding sections prepared the pipeline for training, however, none have been executed.</span></span> <span data-ttu-id="c6c93-190">Aşağıdaki satırı ekleyin `Main` gerçekleştirmek için veri yükleme ve model eğitiminin yöntemi:</span><span class="sxs-lookup"><span data-stu-id="c6c93-190">Add the following line to the `Main` method to perform data loading and model training:</span></span>

[!code-csharp[Train the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#TrainModel)]

### <a name="save-the-model"></a><span data-ttu-id="c6c93-191">Modeli kaydedin</span><span class="sxs-lookup"><span data-stu-id="c6c93-191">Save the model</span></span>

<span data-ttu-id="c6c93-192">Bu noktada, tüm mevcut veya yeni .NET uygulamalarınızı tümleşik bir model var.</span><span class="sxs-lookup"><span data-stu-id="c6c93-192">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="c6c93-193">Modelinizi bir .zip dosyası olarak kaydetmek için aşağıdaki kodu ekleyin. `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="c6c93-193">To save your model to a .zip file, add the following code to the `Main` method:</span></span>

[!code-csharp[Save the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="c6c93-194">Kullanım modeli tahminler elde etmek için</span><span class="sxs-lookup"><span data-stu-id="c6c93-194">Use the model for predictions</span></span>

<span data-ttu-id="c6c93-195">Öngörüler yapma <xref:Microsoft.ML.PredictionEngine%602> giriş türü dönüştürücü ardışık düzeninden örneklerini alır ve çıktı türü örneklerini üretir sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c6c93-195">To make predictions, use the <xref:Microsoft.ML.PredictionEngine%602> class that takes instances of the input type through the transformer pipeline and produces instances of the output type.</span></span> <span data-ttu-id="c6c93-196">Aşağıdaki satırı ekleyin `Main` yöntemi bu sınıfın bir örneğini oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="c6c93-196">Add the following line to the `Main` method to create an instance of that class:</span></span>

[!code-csharp[Create predictor](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Predictor)]

<span data-ttu-id="c6c93-197">Oluşturma `TestIrisData` ev test veri örnekleri sınıfı:</span><span class="sxs-lookup"><span data-stu-id="c6c93-197">Create the `TestIrisData` class to house test data instances:</span></span>

1. <span data-ttu-id="c6c93-198">İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="c6c93-198">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="c6c93-199">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *TestIrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="c6c93-199">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestIrisData.cs*.</span></span> <span data-ttu-id="c6c93-200">Ardından, **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="c6c93-200">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="c6c93-201">Sınıfı gibi aşağıdaki örnekte de statik olarak değiştirin:</span><span class="sxs-lookup"><span data-stu-id="c6c93-201">Modify the class to be static like in the following example:</span></span>

   [!code-csharp[Make class static](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#Static)]

<span data-ttu-id="c6c93-202">Bu öğretici, bu sınıf içinde bir Iris veri örneği tanıtır.</span><span class="sxs-lookup"><span data-stu-id="c6c93-202">This tutorial introduces one iris data instance within this class.</span></span> <span data-ttu-id="c6c93-203">Modelle denemek için diğer senaryolar ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6c93-203">You can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="c6c93-204">Aşağıdaki kodu ekleyin `TestIrisData` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="c6c93-204">Add the following code into the `TestIrisData` class:</span></span>

[!code-csharp[Test data](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#TestData)]

<span data-ttu-id="c6c93-205">Belirtilen öğenin ait olduğu küme öğrenmek için geri dön *Program.cs* dosya ve içine aşağıdaki kodu ekleyin `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="c6c93-205">To find out the cluster to which the specified item belongs to, go back to the *Program.cs* file and add the following code into the `Main` method:</span></span>

[!code-csharp[Predict and output results](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#PredictionExample)]

<span data-ttu-id="c6c93-206">Belirtilen veri örneği ve bu örneğe karesini uzaklıkta küme centroids için hangi küme içerip programı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c6c93-206">Run the program to see which cluster contains the specified data instance and squared distances from that instance to the cluster centroids.</span></span> <span data-ttu-id="c6c93-207">Sonuçlar aşağıdakine benzer olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="c6c93-207">Your results should be similar to the following:</span></span>

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

<span data-ttu-id="c6c93-208">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="c6c93-208">Congratulations!</span></span> <span data-ttu-id="c6c93-209">Bir machine learning modeli için kümeleme ve tahminlerde bulunmak üzere kullanılan Iris artık başarıyla oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="c6c93-209">You've now successfully built a machine learning model for iris clustering and used it to make predictions.</span></span> <span data-ttu-id="c6c93-210">Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub deposu.</span><span class="sxs-lookup"><span data-stu-id="c6c93-210">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c6c93-211">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="c6c93-211">Next steps</span></span>

<span data-ttu-id="c6c93-212">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="c6c93-212">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="c6c93-213">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="c6c93-213">Understand the problem</span></span>
> - <span data-ttu-id="c6c93-214">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="c6c93-214">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="c6c93-215">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="c6c93-215">Prepare the data</span></span>
> - <span data-ttu-id="c6c93-216">Yükleme ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="c6c93-216">Load and transform the data</span></span>
> - <span data-ttu-id="c6c93-217">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="c6c93-217">Choose a learning algorithm</span></span>
> - <span data-ttu-id="c6c93-218">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="c6c93-218">Train the model</span></span>
> - <span data-ttu-id="c6c93-219">Kullanım modeli tahminler elde etmek için</span><span class="sxs-lookup"><span data-stu-id="c6c93-219">Use the model for predictions</span></span>

<span data-ttu-id="c6c93-220">Almaya devam etmek ve diğer örnekleri bulmak için GitHub depomuza denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c6c93-220">Check out our GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="c6c93-221">DotNet/machinelearning GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="c6c93-221">dotnet/machinelearning GitHub repository</span></span>](https://github.com/dotnet/machinelearning/)
