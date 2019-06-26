---
title: 'Öğretici: Iris çiçek - k-ortalamaları kümeleme kategorilere ayırma'
description: ML.NET kümeleme senaryosunda kullanmayı öğrenin
author: pkulikov
ms.author: johalex
ms.date: 05/16/2019
ms.topic: tutorial
ms.custom: mvc, seodec18, title-hack-0516
ms.openlocfilehash: 965408a180245712ceda2c3c17bdf42755af1c2c
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402447"
---
# <a name="tutorial-categorize-iris-flowers-using-k-means-clustering-with-mlnet"></a><span data-ttu-id="2e913-103">Öğretici: ML.NET ile kümeleme k-ortalamaları kullanarak Iris çiçek kategorilere ayırma</span><span class="sxs-lookup"><span data-stu-id="2e913-103">Tutorial: Categorize iris flowers using k-means clustering with ML.NET</span></span>

<span data-ttu-id="2e913-104">Bu öğretici ML.NET oluşturmak için nasıl kullanılacağını gösterir. bir [kümeleme modelinin yerini](../resources/tasks.md#clustering) için [Iris Çiçeği veri kümesi](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span><span class="sxs-lookup"><span data-stu-id="2e913-104">This tutorial illustrates how to use ML.NET to build a [clustering model](../resources/tasks.md#clustering) for the [iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span></span>

<span data-ttu-id="2e913-105">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="2e913-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="2e913-106">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="2e913-106">Understand the problem</span></span>
> - <span data-ttu-id="2e913-107">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="2e913-107">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="2e913-108">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="2e913-108">Prepare the data</span></span>
> - <span data-ttu-id="2e913-109">Yükleme ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="2e913-109">Load and transform the data</span></span>
> - <span data-ttu-id="2e913-110">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="2e913-110">Choose a learning algorithm</span></span>
> - <span data-ttu-id="2e913-111">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="2e913-111">Train the model</span></span>
> - <span data-ttu-id="2e913-112">Kullanım modeli tahminler elde etmek için</span><span class="sxs-lookup"><span data-stu-id="2e913-112">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2e913-113">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="2e913-113">Prerequisites</span></span>

- <span data-ttu-id="2e913-114">[Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır.</span><span class="sxs-lookup"><span data-stu-id="2e913-114">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="2e913-115">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="2e913-115">Understand the problem</span></span>

<span data-ttu-id="2e913-116">Iris çiçek çiçek özelliklere göre farklı gruplardaki kümesini bölme hakkında bu sorun oluşur.</span><span class="sxs-lookup"><span data-stu-id="2e913-116">This problem is about dividing the set of iris flowers in different groups based on the flower features.</span></span> <span data-ttu-id="2e913-117">Bu, genişlik ve bir sepal uzunluğu ve bir petal genişliği ve uzunluğu özellikleridir.</span><span class="sxs-lookup"><span data-stu-id="2e913-117">Those features are the length and width of a sepal and the length and width of a petal.</span></span> <span data-ttu-id="2e913-118">Bu öğretici için her çiçek türü bilinmiyor varsayılır.</span><span class="sxs-lookup"><span data-stu-id="2e913-118">For this tutorial, assume that the type of each flower is unknown.</span></span> <span data-ttu-id="2e913-119">Özellikleri bir veri kümesinden yapısını öğrenin ve bir veri örneği bu yapı nasıl uyduğunu tahmin etmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="2e913-119">You want to learn the structure of a data set from the features and predict how a data instance fits this structure.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="2e913-120">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="2e913-120">Select the appropriate machine learning task</span></span>

<span data-ttu-id="2e913-121">Her çiçek hangi gruba ait bilinmiyor olarak seçtiğiniz [Denetimsiz machine learning](../resources/glossary.md#unsupervised-machine-learning) görev.</span><span class="sxs-lookup"><span data-stu-id="2e913-121">As you don't know to which group each flower belongs to, you choose the [unsupervised machine learning](../resources/glossary.md#unsupervised-machine-learning) task.</span></span> <span data-ttu-id="2e913-122">Bir veri kümesi gruplarında aynı gruptaki öğelerin birbirine daha fazla benzer diğer grupları şekilde bölmek için kullanın. bir [Kümeleme](../resources/tasks.md#clustering) machine learning görev.</span><span class="sxs-lookup"><span data-stu-id="2e913-122">To divide a data set in groups in such a way that elements in the same group are more similar to each other than to those in other groups, use a [clustering](../resources/tasks.md#clustering) machine learning task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="2e913-123">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="2e913-123">Create a console application</span></span>

1. <span data-ttu-id="2e913-124">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="2e913-124">Open Visual Studio.</span></span> <span data-ttu-id="2e913-125">Seçin **dosya** > **yeni** > **proje** menü çubuğundan.</span><span class="sxs-lookup"><span data-stu-id="2e913-125">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="2e913-126">İçinde **yeni proje** iletişim kutusunda **Visual C#** düğümünü ve ardından **.NET Core** düğümü.</span><span class="sxs-lookup"><span data-stu-id="2e913-126">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="2e913-127">Ardından **konsol uygulaması (.NET Core)** proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="2e913-127">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="2e913-128">İçinde **adı** metin kutusuna "IrisFlowerClustering" yazın ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="2e913-128">In the **Name** text box, type "IrisFlowerClustering" and then select the **OK** button.</span></span>

1. <span data-ttu-id="2e913-129">Adlı bir dizin oluşturmak *veri* projenizdeki veri kümesi ve model dosyaları depolamak için:</span><span class="sxs-lookup"><span data-stu-id="2e913-129">Create a directory named *Data* in your project to store the data set and model files:</span></span>

    <span data-ttu-id="2e913-130">İçinde **Çözüm Gezgini**, projeye sağ tıklayıp seçin **Ekle** > **yeni klasör**.</span><span class="sxs-lookup"><span data-stu-id="2e913-130">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="2e913-131">"Veri" yazın ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="2e913-131">Type "Data" and hit Enter.</span></span>

1. <span data-ttu-id="2e913-132">Yükleme **Microsoft.ML** NuGet paketi:</span><span class="sxs-lookup"><span data-stu-id="2e913-132">Install the **Microsoft.ML** NuGet package:</span></span>

    <span data-ttu-id="2e913-133">İçinde **Çözüm Gezgini**, projeye sağ tıklayıp seçin **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="2e913-133">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="2e913-134">Paket kaynağı, seçin "nuget.org" seçin **Gözat** sekmesinde, arama **Microsoft.ML**seçin **v1.0.0** paketini listede bulun ve seçin  **Yükleme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="2e913-134">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the **v1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="2e913-135">Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="2e913-135">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-the-data"></a><span data-ttu-id="2e913-136">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="2e913-136">Prepare the data</span></span>

1. <span data-ttu-id="2e913-137">İndirme [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) veri kümesi ve kaydetmesi *veri* önceki adımda oluşturduğunuz klasör.</span><span class="sxs-lookup"><span data-stu-id="2e913-137">Download the [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) data set and save it to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="2e913-138">Iris veri kümesi hakkında daha fazla bilgi için bkz. [Iris Çiçeği veri kümesi](https://en.wikipedia.org/wiki/Iris_flower_data_set) Wikipedia sayfasında ve [Iris veri kümesini](https://archive.ics.uci.edu/ml/datasets/Iris) sayfasında, veri kümesinin kaynağı.</span><span class="sxs-lookup"><span data-stu-id="2e913-138">For more information about the iris data set, see the [Iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set) Wikipedia page and the [Iris Data Set](https://archive.ics.uci.edu/ml/datasets/Iris) page, which is the source of the data set.</span></span>

1. <span data-ttu-id="2e913-139">İçinde **Çözüm Gezgini**, sağ *iris.data* seçin ve dosya **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="2e913-139">In **Solution Explorer**, right-click the *iris.data* file and select **Properties**.</span></span> <span data-ttu-id="2e913-140">Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.</span><span class="sxs-lookup"><span data-stu-id="2e913-140">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="2e913-141">*İris.data* dosyasını temsil eden beş sütunları içerir:</span><span class="sxs-lookup"><span data-stu-id="2e913-141">The *iris.data* file contains five columns that represent:</span></span>

- <span data-ttu-id="2e913-142">santimetre sepal uzunluğu</span><span class="sxs-lookup"><span data-stu-id="2e913-142">sepal length in centimetres</span></span>
- <span data-ttu-id="2e913-143">santimetre sepal genişliği</span><span class="sxs-lookup"><span data-stu-id="2e913-143">sepal width in centimetres</span></span>
- <span data-ttu-id="2e913-144">santimetre Petal uzunluğu</span><span class="sxs-lookup"><span data-stu-id="2e913-144">petal length in centimetres</span></span>
- <span data-ttu-id="2e913-145">santimetre Petal genişliği</span><span class="sxs-lookup"><span data-stu-id="2e913-145">petal width in centimetres</span></span>
- <span data-ttu-id="2e913-146">Iris çiçek türü</span><span class="sxs-lookup"><span data-stu-id="2e913-146">type of iris flower</span></span>

<span data-ttu-id="2e913-147">Kümeleme örnek için bu öğreticinin son sütun yok sayar.</span><span class="sxs-lookup"><span data-stu-id="2e913-147">For the sake of the clustering example, this tutorial ignores the last column.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="2e913-148">Veri sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="2e913-148">Create data classes</span></span>

<span data-ttu-id="2e913-149">Girdi verilerini ve Öngörüler için sınıflar oluşturun:</span><span class="sxs-lookup"><span data-stu-id="2e913-149">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="2e913-150">İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="2e913-150">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="2e913-151">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *IrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="2e913-151">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *IrisData.cs*.</span></span> <span data-ttu-id="2e913-152">Ardından, **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="2e913-152">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="2e913-153">Aşağıdaki `using` yönerge yeni dosya için:</span><span class="sxs-lookup"><span data-stu-id="2e913-153">Add the following `using` directive to the new file:</span></span>

   [!code-csharp[Add necessary usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#Usings)]

<span data-ttu-id="2e913-154">Varolan sınıf tanımına kaldırın ve sınıfları tanımlar aşağıdaki kodu ekleyin `IrisData` ve `ClusterPrediction`, *IrisData.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="2e913-154">Remove the existing class definition and add the following code, which defines the classes `IrisData` and `ClusterPrediction`, to the *IrisData.cs* file:</span></span>

[!code-csharp[Define data classes](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#ClassDefinitions)]

<span data-ttu-id="2e913-155">`IrisData` giriş verisi sınıfıdır ve veri kümesindeki her bir özellik tanımı yok.</span><span class="sxs-lookup"><span data-stu-id="2e913-155">`IrisData` is the input data class and has definitions for each feature from the data set.</span></span> <span data-ttu-id="2e913-156">Kullanım [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) veri kümesi dosyasında kaynak sütun dizinlerini belirtmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="2e913-156">Use the [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute to specify the indices of the source columns in the data set file.</span></span>

<span data-ttu-id="2e913-157">`ClusterPrediction` Sınıfı temsil eder, uygulanan kümeleme modeli çıktısını bir `IrisData` örneği.</span><span class="sxs-lookup"><span data-stu-id="2e913-157">The `ClusterPrediction` class represents the output of the clustering model applied to an `IrisData` instance.</span></span> <span data-ttu-id="2e913-158">Kullanım [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) bağlanacak öznitelik `PredictedClusterId` ve `Distances` alanlarını **PredictedLabel** ve **puanı** sütunları sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="2e913-158">Use the [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute to bind the `PredictedClusterId` and `Distances` fields to the **PredictedLabel** and **Score** columns respectively.</span></span> <span data-ttu-id="2e913-159">Kümeleme görev olması durumunda bu sütun şu anlama gelir:</span><span class="sxs-lookup"><span data-stu-id="2e913-159">In case of the clustering task those columns have the following meaning:</span></span>

- <span data-ttu-id="2e913-160">**PredictedLabel** sütun tahmin edilen kümenin Kimliğini içerir.</span><span class="sxs-lookup"><span data-stu-id="2e913-160">**PredictedLabel** column contains the ID of the predicted cluster.</span></span>
- <span data-ttu-id="2e913-161">**Puan** küme centroids için kare Euclidean uzaklığa sahip bir dizi sütun içerir.</span><span class="sxs-lookup"><span data-stu-id="2e913-161">**Score** column contains an array with squared Euclidean distances to the cluster centroids.</span></span> <span data-ttu-id="2e913-162">Dizi uzunluğu küme sayısı eşittir.</span><span class="sxs-lookup"><span data-stu-id="2e913-162">The array length is equal to the number of clusters.</span></span>

> [!NOTE]
> <span data-ttu-id="2e913-163">Kullanım `float` giriş ve tahmin verilerini sınıflardaki kayan nokta değerlerini temsil eden tür.</span><span class="sxs-lookup"><span data-stu-id="2e913-163">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="2e913-164">Veri ve model tanımlar</span><span class="sxs-lookup"><span data-stu-id="2e913-164">Define data and model paths</span></span>

<span data-ttu-id="2e913-165">Geri Git *Program.cs* dosya ve veri kümesi dosyasını ve modeli kaydedin ve dosyaya yolları tutmak için iki alanları ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2e913-165">Go back to the *Program.cs* file and add two fields to hold the paths to the data set file and to the file to save the model:</span></span>

- <span data-ttu-id="2e913-166">`_dataPath` modeli eğitmek için kullanılan veri kümesiyle dosyasının yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="2e913-166">`_dataPath` contains the path to the file with the data set used to train the model.</span></span>
- <span data-ttu-id="2e913-167">`_modelPath` eğitilen modelin depolandığı dosya yolu içerir.</span><span class="sxs-lookup"><span data-stu-id="2e913-167">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="2e913-168">Aşağıdaki kod üzerinde doğru `Main` yöntemi bu yollarını belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="2e913-168">Add the following code right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Initialize paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Paths)]

<span data-ttu-id="2e913-169">Derleme, aşağıdaki ekleyin önceki kodun `using` üst kısmındaki yönergeleri *Program.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="2e913-169">To make the preceding code compile, add the following `using` directives at the top of the *Program.cs* file:</span></span>

[!code-csharp[Add usings for paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a><span data-ttu-id="2e913-170">ML bağlamı oluşturur</span><span class="sxs-lookup"><span data-stu-id="2e913-170">Create ML context</span></span>

<span data-ttu-id="2e913-171">Aşağıdaki ek ekleyin `using` yönergeleri üstüne *Program.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="2e913-171">Add the following additional `using` directives to the top of the *Program.cs* file:</span></span>

[!code-csharp[Add Microsoft.ML usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#MLUsings)]

<span data-ttu-id="2e913-172">İçinde `Main` yöntemi Değiştir `Console.WriteLine("Hello World!");` satırı aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="2e913-172">In the `Main` method, replace the `Console.WriteLine("Hello World!");` line with the following code:</span></span>

[!code-csharp[Create ML context](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateContext)]

<span data-ttu-id="2e913-173"><xref:Microsoft.ML.MLContext?displayProperty=nameWithType> Sınıf makine öğrenimi ortamını temsil eden ve veri yükleme, model eğitiminin, tahmin ve diğer görevler için günlüğü ve giriş noktaları için mekanizmaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="2e913-173">The <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> class represents the machine learning environment and provides mechanisms for logging and entry points for data loading, model training, prediction, and other tasks.</span></span> <span data-ttu-id="2e913-174">Bu kavramsal olarak kullanarak karşılaştırılabilir `DbContext` Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="2e913-174">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span>

## <a name="setup-data-loading"></a><span data-ttu-id="2e913-175">Veri yükleme kurulumu</span><span class="sxs-lookup"><span data-stu-id="2e913-175">Setup data loading</span></span>

<span data-ttu-id="2e913-176">Aşağıdaki kodu ekleyin `Main` yöntemi veri yükleme şekilde ayarlamak için:</span><span class="sxs-lookup"><span data-stu-id="2e913-176">Add the following code to the `Main` method to setup the way to load data:</span></span>

[!code-csharp[Create text loader](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateDataView)]

<span data-ttu-id="2e913-177">Genel [ `MLContext.Data.LoadFromTextFile` genişletme yöntemi](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) sağlanan veri kümesi şema çıkarsar `IrisData` türü ve döndürür <xref:Microsoft.ML.IDataView> kullanılabilen giriş olarak dönüştürücüler için.</span><span class="sxs-lookup"><span data-stu-id="2e913-177">The generic [`MLContext.Data.LoadFromTextFile` extension method](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) infers the data set schema from the provided `IrisData` type and returns <xref:Microsoft.ML.IDataView> which can be used as input for transformers.</span></span>

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="2e913-178">Öğrenme işlem hattı oluşturma</span><span class="sxs-lookup"><span data-stu-id="2e913-178">Create a learning pipeline</span></span>

<span data-ttu-id="2e913-179">Bu öğreticide, öğrenme işlem hattınızı kümeleme görevin aşağıdaki iki adımdan oluşur:</span><span class="sxs-lookup"><span data-stu-id="2e913-179">For this tutorial, the learning pipeline of the clustering task comprises two following steps:</span></span>

- <span data-ttu-id="2e913-180">yüklenen sütunu bir birleştirme **özellikleri** kümeleme Eğitmen tarafından; kullanılan sütun</span><span class="sxs-lookup"><span data-stu-id="2e913-180">concatenate loaded columns into one **Features** column, which is used by a clustering trainer;</span></span>
- <span data-ttu-id="2e913-181">kullanan bir <xref:Microsoft.ML.Trainers.KMeansTrainer> k kullanarak modeli eğitmek için Eğitmen-anlamına gelir ++ kümeleme algoritması.</span><span class="sxs-lookup"><span data-stu-id="2e913-181">use a <xref:Microsoft.ML.Trainers.KMeansTrainer> trainer to train the model using the k-means++ clustering algorithm.</span></span>

<span data-ttu-id="2e913-182">Aşağıdaki kodu ekleyin `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="2e913-182">Add the following code to the `Main` method:</span></span>

[!code-csharp[Create pipeline](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreatePipeline)]

<span data-ttu-id="2e913-183">Kod üç kümelerinde veri kümesi ayrılmalıdır belirtir.</span><span class="sxs-lookup"><span data-stu-id="2e913-183">The code specifies that the data set should be split in three clusters.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="2e913-184">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="2e913-184">Train the model</span></span>

<span data-ttu-id="2e913-185">Önceki bölümde eklediğiniz adımlar eğitim için ardışık düzen hazır, ancak hiçbiri yürütüldüğünü.</span><span class="sxs-lookup"><span data-stu-id="2e913-185">The steps added in the preceding sections prepared the pipeline for training, however, none have been executed.</span></span> <span data-ttu-id="2e913-186">Aşağıdaki satırı ekleyin `Main` gerçekleştirmek için veri yükleme ve model eğitiminin yöntemi:</span><span class="sxs-lookup"><span data-stu-id="2e913-186">Add the following line to the `Main` method to perform data loading and model training:</span></span>

[!code-csharp[Train the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#TrainModel)]

### <a name="save-the-model"></a><span data-ttu-id="2e913-187">Modeli kaydedin</span><span class="sxs-lookup"><span data-stu-id="2e913-187">Save the model</span></span>

<span data-ttu-id="2e913-188">Bu noktada, tüm mevcut veya yeni .NET uygulamalarınızı tümleşik bir model var.</span><span class="sxs-lookup"><span data-stu-id="2e913-188">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="2e913-189">Modelinizi bir .zip dosyası olarak kaydetmek için aşağıdaki kodu ekleyin. `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="2e913-189">To save your model to a .zip file, add the following code to the `Main` method:</span></span>

[!code-csharp[Save the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="2e913-190">Kullanım modeli tahminler elde etmek için</span><span class="sxs-lookup"><span data-stu-id="2e913-190">Use the model for predictions</span></span>

<span data-ttu-id="2e913-191">Öngörüler yapma <xref:Microsoft.ML.PredictionEngine%602> giriş türü dönüştürücü ardışık düzeninden örneklerini alır ve çıktı türü örneklerini üretir sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2e913-191">To make predictions, use the <xref:Microsoft.ML.PredictionEngine%602> class that takes instances of the input type through the transformer pipeline and produces instances of the output type.</span></span> <span data-ttu-id="2e913-192">Aşağıdaki satırı ekleyin `Main` yöntemi bu sınıfın bir örneğini oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="2e913-192">Add the following line to the `Main` method to create an instance of that class:</span></span>

[!code-csharp[Create predictor](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Predictor)]

<span data-ttu-id="2e913-193">Oluşturma `TestIrisData` ev test veri örnekleri sınıfı:</span><span class="sxs-lookup"><span data-stu-id="2e913-193">Create the `TestIrisData` class to house test data instances:</span></span>

1. <span data-ttu-id="2e913-194">İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="2e913-194">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="2e913-195">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *TestIrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="2e913-195">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestIrisData.cs*.</span></span> <span data-ttu-id="2e913-196">Ardından, **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="2e913-196">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="2e913-197">Sınıfı gibi aşağıdaki örnekte de statik olarak değiştirin:</span><span class="sxs-lookup"><span data-stu-id="2e913-197">Modify the class to be static like in the following example:</span></span>

   [!code-csharp[Make class static](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#Static)]

<span data-ttu-id="2e913-198">Bu öğretici, bu sınıf içinde bir Iris veri örneği tanıtır.</span><span class="sxs-lookup"><span data-stu-id="2e913-198">This tutorial introduces one iris data instance within this class.</span></span> <span data-ttu-id="2e913-199">Modelle denemek için diğer senaryolar ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2e913-199">You can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="2e913-200">Aşağıdaki kodu ekleyin `TestIrisData` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="2e913-200">Add the following code into the `TestIrisData` class:</span></span>

[!code-csharp[Test data](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#TestData)]

<span data-ttu-id="2e913-201">Belirtilen öğenin ait olduğu küme öğrenmek için geri dön *Program.cs* dosya ve içine aşağıdaki kodu ekleyin `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="2e913-201">To find out the cluster to which the specified item belongs to, go back to the *Program.cs* file and add the following code into the `Main` method:</span></span>

[!code-csharp[Predict and output results](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#PredictionExample)]

<span data-ttu-id="2e913-202">Belirtilen veri örneği ve bu örneğe karesini uzaklıkta küme centroids için hangi küme içerip programı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2e913-202">Run the program to see which cluster contains the specified data instance and squared distances from that instance to the cluster centroids.</span></span> <span data-ttu-id="2e913-203">Sonuçlar aşağıdakine benzer olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="2e913-203">Your results should be similar to the following:</span></span>

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

<span data-ttu-id="2e913-204">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="2e913-204">Congratulations!</span></span> <span data-ttu-id="2e913-205">Bir machine learning modeli için kümeleme ve tahminlerde bulunmak üzere kullanılan Iris artık başarıyla oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="2e913-205">You've now successfully built a machine learning model for iris clustering and used it to make predictions.</span></span> <span data-ttu-id="2e913-206">Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub deposu.</span><span class="sxs-lookup"><span data-stu-id="2e913-206">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2e913-207">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="2e913-207">Next steps</span></span>

<span data-ttu-id="2e913-208">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="2e913-208">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="2e913-209">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="2e913-209">Understand the problem</span></span>
> - <span data-ttu-id="2e913-210">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="2e913-210">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="2e913-211">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="2e913-211">Prepare the data</span></span>
> - <span data-ttu-id="2e913-212">Yükleme ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="2e913-212">Load and transform the data</span></span>
> - <span data-ttu-id="2e913-213">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="2e913-213">Choose a learning algorithm</span></span>
> - <span data-ttu-id="2e913-214">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="2e913-214">Train the model</span></span>
> - <span data-ttu-id="2e913-215">Kullanım modeli tahminler elde etmek için</span><span class="sxs-lookup"><span data-stu-id="2e913-215">Use the model for predictions</span></span>

<span data-ttu-id="2e913-216">Almaya devam etmek ve diğer örnekleri bulmak için GitHub depomuza denetleyin.</span><span class="sxs-lookup"><span data-stu-id="2e913-216">Check out our GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="2e913-217">DotNet/machinelearning GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="2e913-217">dotnet/machinelearning GitHub repository</span></span>](https://github.com/dotnet/machinelearning/)
