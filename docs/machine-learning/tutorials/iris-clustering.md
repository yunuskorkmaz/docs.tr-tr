---
title: 'Öğretici: Iris çiçekleri kategorilere ayır-k-bir kümeleme'
description: Kümeleme senaryosunda ML.NET kullanmayı öğrenin
author: pkulikov
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 8ee8b177dc9cc89c4f54956b8c0a274b1d093ece
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/13/2020
ms.locfileid: "86282092"
---
# <a name="tutorial-categorize-iris-flowers-using-k-means-clustering-with-mlnet"></a><span data-ttu-id="f0bad-103">Öğretici: Iris çiçekler 'i k-ML.NET Kümelemesi kullanarak kategorilere ayırın</span><span class="sxs-lookup"><span data-stu-id="f0bad-103">Tutorial: Categorize iris flowers using k-means clustering with ML.NET</span></span>

<span data-ttu-id="f0bad-104">Bu öğreticide, [Iris çiçek veri kümesi](https://en.wikipedia.org/wiki/Iris_flower_data_set)için bir [kümeleme modeli](../resources/tasks.md#clustering) oluşturmak üzere ml.net 'in nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f0bad-104">This tutorial illustrates how to use ML.NET to build a [clustering model](../resources/tasks.md#clustering) for the [iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span></span>

<span data-ttu-id="f0bad-105">Bu öğreticide aşağıdakilerin nasıl yapılacağını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="f0bad-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="f0bad-106">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="f0bad-106">Understand the problem</span></span>
> - <span data-ttu-id="f0bad-107">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="f0bad-107">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="f0bad-108">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="f0bad-108">Prepare the data</span></span>
> - <span data-ttu-id="f0bad-109">Verileri yükleme ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="f0bad-109">Load and transform the data</span></span>
> - <span data-ttu-id="f0bad-110">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="f0bad-110">Choose a learning algorithm</span></span>
> - <span data-ttu-id="f0bad-111">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="f0bad-111">Train the model</span></span>
> - <span data-ttu-id="f0bad-112">Tahmin için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="f0bad-112">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f0bad-113">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="f0bad-113">Prerequisites</span></span>

- <span data-ttu-id="f0bad-114">[Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya üzeri ya da visual Studio 2017 sürüm 15,6 veya üzeri, ".NET Core platformlar arası geliştirme" iş yükü yüklendi.</span><span class="sxs-lookup"><span data-stu-id="f0bad-114">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="f0bad-115">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="f0bad-115">Understand the problem</span></span>

<span data-ttu-id="f0bad-116">Bu sorun, bir Iris çiçekler kümesini, çiçek özelliklerine göre farklı gruplarda bölmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f0bad-116">This problem is about dividing the set of iris flowers in different groups based on the flower features.</span></span> <span data-ttu-id="f0bad-117">Bu özellikler, bir sepal 'ın uzunluğu ve genişliği ve Petal 'ın uzunluğu ve genişliği.</span><span class="sxs-lookup"><span data-stu-id="f0bad-117">Those features are the length and width of a sepal and the length and width of a petal.</span></span> <span data-ttu-id="f0bad-118">Bu öğretici için, her çiçek türünün bilinmediğini varsayın.</span><span class="sxs-lookup"><span data-stu-id="f0bad-118">For this tutorial, assume that the type of each flower is unknown.</span></span> <span data-ttu-id="f0bad-119">Özelliklerden bir veri kümesinin yapısını öğrenmek ve bir veri örneğinin bu yapıya nasıl uyduğunu tahmin etmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="f0bad-119">You want to learn the structure of a data set from the features and predict how a data instance fits this structure.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="f0bad-120">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="f0bad-120">Select the appropriate machine learning task</span></span>

<span data-ttu-id="f0bad-121">Her bir çiçek 'nin hangi gruba ait olduğunu bilmiyorsanız, denetimli [makine öğrenimi](../resources/glossary.md#unsupervised-machine-learning) görevini seçersiniz.</span><span class="sxs-lookup"><span data-stu-id="f0bad-121">As you don't know to which group each flower belongs to, you choose the [unsupervised machine learning](../resources/glossary.md#unsupervised-machine-learning) task.</span></span> <span data-ttu-id="f0bad-122">Gruplardaki bir veri kümesini, aynı gruptaki öğelerin diğer gruplardaki diğer gruplardan birbirlerine benzer şekilde bölmek için, bir [kümeleme](../resources/tasks.md#clustering) Machine Learning görevi kullanın.</span><span class="sxs-lookup"><span data-stu-id="f0bad-122">To divide a data set in groups in such a way that elements in the same group are more similar to each other than to those in other groups, use a [clustering](../resources/tasks.md#clustering) machine learning task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="f0bad-123">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="f0bad-123">Create a console application</span></span>

1. <span data-ttu-id="f0bad-124">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="f0bad-124">Open Visual Studio.</span></span> <span data-ttu-id="f0bad-125">Menü çubuğundan **Dosya**  >  **Yeni**  >  **Proje** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="f0bad-125">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="f0bad-126">**Yeni proje** iletişim kutusunda, **Visual C#** düğümünü ve ardından **.NET Core** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="f0bad-126">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="f0bad-127">Ardından **konsol uygulaması (.NET Core)** proje şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="f0bad-127">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="f0bad-128">**Ad** metin kutusuna "ırisflowerkümeleme" yazın ve **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="f0bad-128">In the **Name** text box, type "IrisFlowerClustering" and then select the **OK** button.</span></span>

1. <span data-ttu-id="f0bad-129">Veri kümesi ve model dosyalarını depolamak için projenizde *veri* adlı bir dizin oluşturun:</span><span class="sxs-lookup"><span data-stu-id="f0bad-129">Create a directory named *Data* in your project to store the data set and model files:</span></span>

    <span data-ttu-id="f0bad-130">**Çözüm Gezgini**, projeye sağ tıklayın ve **Add**  >  **Yeni klasör**Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="f0bad-130">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="f0bad-131">"Data" yazın ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="f0bad-131">Type "Data" and hit Enter.</span></span>

1. <span data-ttu-id="f0bad-132">**Microsoft.ml** NuGet paketini yükler:</span><span class="sxs-lookup"><span data-stu-id="f0bad-132">Install the **Microsoft.ML** NuGet package:</span></span>

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    <span data-ttu-id="f0bad-133">**Çözüm Gezgini**, projeye sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="f0bad-133">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="f0bad-134">Paket kaynağı olarak "nuget.org" öğesini seçin, **Gözden** geçirme sekmesini seçin, **Microsoft.ml** araması yapın ve **yüklemeyi** seçin.</span><span class="sxs-lookup"><span data-stu-id="f0bad-134">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML** and select the **Install** button.</span></span> <span data-ttu-id="f0bad-135">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="f0bad-135">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-the-data"></a><span data-ttu-id="f0bad-136">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="f0bad-136">Prepare the data</span></span>

1. <span data-ttu-id="f0bad-137">[Iris. Data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) veri kümesini indirin ve önceki adımda oluşturduğunuz *veri* klasörüne kaydedin.</span><span class="sxs-lookup"><span data-stu-id="f0bad-137">Download the [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) data set and save it to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="f0bad-138">Iris veri kümesi hakkında daha fazla bilgi için, veri kümesinin kaynağı olan [Iris çiçek veri kümesi](https://en.wikipedia.org/wiki/Iris_flower_data_set) vikipi sayfasında ve [Iris veri kümesi](http://archive.ics.uci.edu/ml/datasets/Iris) sayfasına bakın.</span><span class="sxs-lookup"><span data-stu-id="f0bad-138">For more information about the iris data set, see the [Iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set) Wikipedia page and the [Iris Data Set](http://archive.ics.uci.edu/ml/datasets/Iris) page, which is the source of the data set.</span></span>

1. <span data-ttu-id="f0bad-139">**Çözüm Gezgini**, *Iris. Data* dosyasına sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="f0bad-139">In **Solution Explorer**, right-click the *iris.data* file and select **Properties**.</span></span> <span data-ttu-id="f0bad-140">**Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f0bad-140">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="f0bad-141">*Iris. Data* dosyası, şunları temsil eden beş sütun içerir:</span><span class="sxs-lookup"><span data-stu-id="f0bad-141">The *iris.data* file contains five columns that represent:</span></span>

- <span data-ttu-id="f0bad-142">santimetre cinsinden sepal uzunluğu</span><span class="sxs-lookup"><span data-stu-id="f0bad-142">sepal length in centimeters</span></span>
- <span data-ttu-id="f0bad-143">santimetre cinsinden sepal genişliği</span><span class="sxs-lookup"><span data-stu-id="f0bad-143">sepal width in centimeters</span></span>
- <span data-ttu-id="f0bad-144">santimetre cinsinden Petal uzunluğu</span><span class="sxs-lookup"><span data-stu-id="f0bad-144">petal length in centimeters</span></span>
- <span data-ttu-id="f0bad-145">Genişlik cinsinden Petal genişliği</span><span class="sxs-lookup"><span data-stu-id="f0bad-145">petal width in centimeters</span></span>
- <span data-ttu-id="f0bad-146">Iris çiçek türü</span><span class="sxs-lookup"><span data-stu-id="f0bad-146">type of iris flower</span></span>

<span data-ttu-id="f0bad-147">Kümeleme örneği için bu öğretici son sütunu yoksayar.</span><span class="sxs-lookup"><span data-stu-id="f0bad-147">For the sake of the clustering example, this tutorial ignores the last column.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="f0bad-148">Veri sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="f0bad-148">Create data classes</span></span>

<span data-ttu-id="f0bad-149">Giriş verileri ve tahminleri için sınıflar oluşturun:</span><span class="sxs-lookup"><span data-stu-id="f0bad-149">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="f0bad-150">**Çözüm Gezgini**, projeye sağ tıklayın ve ardından **Add**  >  **Yeni öğe**Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="f0bad-150">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="f0bad-151">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *IrisData.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f0bad-151">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *IrisData.cs*.</span></span> <span data-ttu-id="f0bad-152">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="f0bad-152">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="f0bad-153">Aşağıdaki `using` yönergeyi yeni dosyaya ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f0bad-153">Add the following `using` directive to the new file:</span></span>

   [!code-csharp[Add necessary usings](./snippets/iris-clustering/csharp/IrisData.cs#Usings)]

<span data-ttu-id="f0bad-154">Mevcut sınıf tanımını kaldırın ve sınıfları `IrisData` ve `ClusterPrediction` *IrisData.cs* dosyasını tanımlayan aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f0bad-154">Remove the existing class definition and add the following code, which defines the classes `IrisData` and `ClusterPrediction`, to the *IrisData.cs* file:</span></span>

[!code-csharp[Define data classes](./snippets/iris-clustering/csharp/IrisData.cs#ClassDefinitions)]

<span data-ttu-id="f0bad-155">`IrisData`, giriş veri sınıfıdır ve veri kümesindeki her bir özellik için tanımlar içerir.</span><span class="sxs-lookup"><span data-stu-id="f0bad-155">`IrisData` is the input data class and has definitions for each feature from the data set.</span></span> <span data-ttu-id="f0bad-156">Veri kümesi dosyasındaki kaynak sütunlarının dizinlerini belirtmek için [Loadcolumn](xref:Microsoft.ML.Data.LoadColumnAttribute) özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f0bad-156">Use the [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute to specify the indices of the source columns in the data set file.</span></span>

<span data-ttu-id="f0bad-157">`ClusterPrediction`Sınıfı, bir örneğe uygulanan kümeleme modelinin çıkışını temsil eder `IrisData` .</span><span class="sxs-lookup"><span data-stu-id="f0bad-157">The `ClusterPrediction` class represents the output of the clustering model applied to an `IrisData` instance.</span></span> <span data-ttu-id="f0bad-158">Ve alanlarını tahmine Tedlabel öğesine bağlamak için [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) özniteliğini kullanın `PredictedClusterId` `Distances` ve **PredictedLabel** sütunları sırasıyla **puan** yapın.</span><span class="sxs-lookup"><span data-stu-id="f0bad-158">Use the [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute to bind the `PredictedClusterId` and `Distances` fields to the **PredictedLabel** and **Score** columns respectively.</span></span> <span data-ttu-id="f0bad-159">Kümeleme görevi söz konusu sütunlarda aşağıdaki anlamı vardır:</span><span class="sxs-lookup"><span data-stu-id="f0bad-159">In case of the clustering task those columns have the following meaning:</span></span>

- <span data-ttu-id="f0bad-160">**Predictedlabel** sütunu, tahmin EDILEN kümenin kimliğini içerir.</span><span class="sxs-lookup"><span data-stu-id="f0bad-160">**PredictedLabel** column contains the ID of the predicted cluster.</span></span>
- <span data-ttu-id="f0bad-161">**Puan** sütunu, kare Içinde Euclidea uzaklıkları küme centroıd 'leri için olan bir dizi içeriyor.</span><span class="sxs-lookup"><span data-stu-id="f0bad-161">**Score** column contains an array with squared Euclidean distances to the cluster centroids.</span></span> <span data-ttu-id="f0bad-162">Dizi uzunluğu, küme sayısına eşittir.</span><span class="sxs-lookup"><span data-stu-id="f0bad-162">The array length is equal to the number of clusters.</span></span>

> [!NOTE]
> <span data-ttu-id="f0bad-163">`float`Giriş ve tahmin veri sınıflarında kayan nokta değerlerini göstermek için türünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="f0bad-163">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="f0bad-164">Veri ve model yollarını tanımlama</span><span class="sxs-lookup"><span data-stu-id="f0bad-164">Define data and model paths</span></span>

<span data-ttu-id="f0bad-165">*Program.cs* dosyasına dönün ve veri kümesi dosyasına ve modelin kaydedileceği dosyanın yollarını barındıracak iki alan ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f0bad-165">Go back to the *Program.cs* file and add two fields to hold the paths to the data set file and to the file to save the model:</span></span>

- <span data-ttu-id="f0bad-166">`_dataPath`modeli eğitmek için kullanılan veri kümesiyle dosyanın yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="f0bad-166">`_dataPath` contains the path to the file with the data set used to train the model.</span></span>
- <span data-ttu-id="f0bad-167">`_modelPath`eğitilen modelin depolandığı dosyanın yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="f0bad-167">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="f0bad-168">Aşağıdaki kodu, `Main` Bu yolları belirtmek için yöntemine hemen ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f0bad-168">Add the following code right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Initialize paths](./snippets/iris-clustering/csharp/Program.cs#Paths)]

<span data-ttu-id="f0bad-169">Önceki kodu derlemek için, `using` *program.cs* dosyasının en üstüne aşağıdaki yönergeleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f0bad-169">To make the preceding code compile, add the following `using` directives at the top of the *Program.cs* file:</span></span>

[!code-csharp[Add usings for paths](./snippets/iris-clustering/csharp/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a><span data-ttu-id="f0bad-170">ML bağlamı oluştur</span><span class="sxs-lookup"><span data-stu-id="f0bad-170">Create ML context</span></span>

<span data-ttu-id="f0bad-171">`using` *Program.cs* dosyasının en üstüne aşağıdaki ek yönergeleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f0bad-171">Add the following additional `using` directives to the top of the *Program.cs* file:</span></span>

[!code-csharp[Add Microsoft.ML usings](./snippets/iris-clustering/csharp/Program.cs#MLUsings)]

<span data-ttu-id="f0bad-172">`Main`Yönteminde `Console.WriteLine("Hello World!");` satırını aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="f0bad-172">In the `Main` method, replace the `Console.WriteLine("Hello World!");` line with the following code:</span></span>

[!code-csharp[Create ML context](./snippets/iris-clustering/csharp/Program.cs#CreateContext)]

<span data-ttu-id="f0bad-173"><xref:Microsoft.ML.MLContext?displayProperty=nameWithType>Sınıfı, Machine Learning ortamını temsil eder ve veri yükleme, model eğitimi, tahmin ve diğer görevler için günlüğe kaydetme ve giriş noktaları için mekanizmalar sağlar.</span><span class="sxs-lookup"><span data-stu-id="f0bad-173">The <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> class represents the machine learning environment and provides mechanisms for logging and entry points for data loading, model training, prediction, and other tasks.</span></span> <span data-ttu-id="f0bad-174">Bu, kavramsal olarak `DbContext` Entity Framework ' de kullanılmasına benzer.</span><span class="sxs-lookup"><span data-stu-id="f0bad-174">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span>

## <a name="set-up-data-loading"></a><span data-ttu-id="f0bad-175">Veri yüklemeyi ayarlama</span><span class="sxs-lookup"><span data-stu-id="f0bad-175">Set up data loading</span></span>

<span data-ttu-id="f0bad-176">Aşağıdaki kodu `Main` yöntemine ekleyerek verileri yükleme yolunu ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="f0bad-176">Add the following code to the `Main` method to set up the way to load data:</span></span>

[!code-csharp[Create text loader](./snippets/iris-clustering/csharp/Program.cs#CreateDataView)]

<span data-ttu-id="f0bad-177">Genel [ `MLContext.Data.LoadFromTextFile` genişletme yöntemi](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) , veri kümesi şemasını belirtilen `IrisData` tür ve döndürmektedir <xref:Microsoft.ML.IDataView> . Bu, dönüştürücüler için giriş olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f0bad-177">The generic [`MLContext.Data.LoadFromTextFile` extension method](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) infers the data set schema from the provided `IrisData` type and returns <xref:Microsoft.ML.IDataView> which can be used as input for transformers.</span></span>

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="f0bad-178">Öğrenme işlem hattı oluşturma</span><span class="sxs-lookup"><span data-stu-id="f0bad-178">Create a learning pipeline</span></span>

<span data-ttu-id="f0bad-179">Bu öğreticide, kümeleme görevinin öğrenme işlem hattı aşağıdaki iki adımdan oluşur:</span><span class="sxs-lookup"><span data-stu-id="f0bad-179">For this tutorial, the learning pipeline of the clustering task comprises two following steps:</span></span>

- <span data-ttu-id="f0bad-180">yüklenen sütunları bir kümeleme işlemi tarafından kullanılan tek bir **Özellikler** sütununa birleştirme;</span><span class="sxs-lookup"><span data-stu-id="f0bad-180">concatenate loaded columns into one **Features** column, which is used by a clustering trainer;</span></span>
- <span data-ttu-id="f0bad-181"><xref:Microsoft.ML.Trainers.KMeansTrainer>k-ortalamalar + + kümeleme algoritmasını kullanarak modeli eğitme için bir seyahat kullanın.</span><span class="sxs-lookup"><span data-stu-id="f0bad-181">use a <xref:Microsoft.ML.Trainers.KMeansTrainer> trainer to train the model using the k-means++ clustering algorithm.</span></span>

<span data-ttu-id="f0bad-182">`Main` yöntemine aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f0bad-182">Add the following code to the `Main` method:</span></span>

[!code-csharp[Create pipeline](./snippets/iris-clustering/csharp/Program.cs#CreatePipeline)]

<span data-ttu-id="f0bad-183">Kod, veri kümesinin üç kümede bölünmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f0bad-183">The code specifies that the data set should be split in three clusters.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="f0bad-184">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="f0bad-184">Train the model</span></span>

<span data-ttu-id="f0bad-185">Önceki bölümlerde eklenen adımlar, eğitim için işlem hattını hazırlandı, ancak hiçbiri yürütülmedi.</span><span class="sxs-lookup"><span data-stu-id="f0bad-185">The steps added in the preceding sections prepared the pipeline for training, however, none have been executed.</span></span> <span data-ttu-id="f0bad-186">`Main`Veri yükleme ve model eğitimi gerçekleştirmek için aşağıdaki satırı yöntemine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f0bad-186">Add the following line to the `Main` method to perform data loading and model training:</span></span>

[!code-csharp[Train the model](./snippets/iris-clustering/csharp/Program.cs#TrainModel)]

### <a name="save-the-model"></a><span data-ttu-id="f0bad-187">Modeli kaydetme</span><span class="sxs-lookup"><span data-stu-id="f0bad-187">Save the model</span></span>

<span data-ttu-id="f0bad-188">Bu noktada, mevcut veya yeni .NET uygulamalarından tümleştirilebilen bir modeliniz vardır.</span><span class="sxs-lookup"><span data-stu-id="f0bad-188">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="f0bad-189">Modelinizi bir. zip dosyasına kaydetmek için aşağıdaki kodu `Main` yöntemine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f0bad-189">To save your model to a .zip file, add the following code to the `Main` method:</span></span>

[!code-csharp[Save the model](./snippets/iris-clustering/csharp/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="f0bad-190">Tahmin için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="f0bad-190">Use the model for predictions</span></span>

<span data-ttu-id="f0bad-191">Tahmine dayalı hale getirmek için, <xref:Microsoft.ML.PredictionEngine%602> transformatör işlem hattı aracılığıyla giriş türünün örneklerini alan sınıfı kullanın ve çıkış türünün örneklerini üretir.</span><span class="sxs-lookup"><span data-stu-id="f0bad-191">To make predictions, use the <xref:Microsoft.ML.PredictionEngine%602> class that takes instances of the input type through the transformer pipeline and produces instances of the output type.</span></span> <span data-ttu-id="f0bad-192">Aşağıdaki satırı, `Main` Bu sınıfın bir örneğini oluşturmak için yöntemine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f0bad-192">Add the following line to the `Main` method to create an instance of that class:</span></span>

[!code-csharp[Create predictor](./snippets/iris-clustering/csharp/Program.cs#Predictor)]

<span data-ttu-id="f0bad-193">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneğinde tahmin gerçekleştirmenize olanak tanıyan, KULLANıŞLı bir API 'dir.</span><span class="sxs-lookup"><span data-stu-id="f0bad-193">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="f0bad-194">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602), iş parçacığı açısından güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="f0bad-194">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="f0bad-195">Tek iş parçacıklı veya prototip ortamlarında kullanılması kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="f0bad-195">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="f0bad-196">Üretim ortamlarında geliştirilmiş performans ve iş parçacığı güvenliği için, `PredictionEnginePool` [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) uygulamanız genelinde kullanılacak nesneleri oluşturan hizmetini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f0bad-196">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="f0bad-197">[ `PredictionEnginePool` ASP.NET Core Web API 'sinde kullanma](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)hakkında bu kılavuza bakın.</span><span class="sxs-lookup"><span data-stu-id="f0bad-197">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

> [!NOTE]
> <span data-ttu-id="f0bad-198">`PredictionEnginePool`Hizmet Uzantısı Şu anda önizleme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="f0bad-198">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="f0bad-199">`TestIrisData`Test veri örneklerini barındırmak için sınıf oluşturun:</span><span class="sxs-lookup"><span data-stu-id="f0bad-199">Create the `TestIrisData` class to house test data instances:</span></span>

1. <span data-ttu-id="f0bad-200">**Çözüm Gezgini**, projeye sağ tıklayın ve ardından **Add**  >  **Yeni öğe**Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="f0bad-200">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="f0bad-201">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *TestIrisData.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f0bad-201">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestIrisData.cs*.</span></span> <span data-ttu-id="f0bad-202">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="f0bad-202">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="f0bad-203">Aşağıdaki örnekte olduğu gibi, sınıfı statik olacak şekilde değiştirin:</span><span class="sxs-lookup"><span data-stu-id="f0bad-203">Modify the class to be static like in the following example:</span></span>

   [!code-csharp[Make class static](./snippets/iris-clustering/csharp/TestIrisData.cs#Static)]

<span data-ttu-id="f0bad-204">Bu öğretici, bu sınıf içindeki bir Iris veri örneğini tanıtır.</span><span class="sxs-lookup"><span data-stu-id="f0bad-204">This tutorial introduces one iris data instance within this class.</span></span> <span data-ttu-id="f0bad-205">Modelle denemeler yapmak için başka senaryolar da ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0bad-205">You can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="f0bad-206">Sınıfına aşağıdaki kodu ekleyin `TestIrisData` :</span><span class="sxs-lookup"><span data-stu-id="f0bad-206">Add the following code into the `TestIrisData` class:</span></span>

[!code-csharp[Test data](./snippets/iris-clustering/csharp/TestIrisData.cs#TestData)]

<span data-ttu-id="f0bad-207">Belirtilen öğenin ait olduğu kümeyi bulmak için, *program.cs* dosyasına dönün ve aşağıdaki kodu `Main` yöntemine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f0bad-207">To find out the cluster to which the specified item belongs to, go back to the *Program.cs* file and add the following code into the `Main` method:</span></span>

[!code-csharp[Predict and output results](./snippets/iris-clustering/csharp/Program.cs#PredictionExample)]

<span data-ttu-id="f0bad-208">Hangi kümenin belirtilen veri örneğini içerdiğini ve bu örnekten gelen kare uzaklıkları küme centroıd 'lerini görmek için programı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f0bad-208">Run the program to see which cluster contains the specified data instance and squared distances from that instance to the cluster centroids.</span></span> <span data-ttu-id="f0bad-209">Sonuçlarınız aşağıdakine benzer olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="f0bad-209">Your results should be similar to the following:</span></span>

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

<span data-ttu-id="f0bad-210">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="f0bad-210">Congratulations!</span></span> <span data-ttu-id="f0bad-211">Iris Kümelemesi için bir makine öğrenimi modeli başarıyla oluşturdunuz ve bu uygulamayı tahmine dayalı hale getirmek için kullandınız.</span><span class="sxs-lookup"><span data-stu-id="f0bad-211">You've now successfully built a machine learning model for iris clustering and used it to make predictions.</span></span> <span data-ttu-id="f0bad-212">Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0bad-212">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f0bad-213">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="f0bad-213">Next steps</span></span>

<span data-ttu-id="f0bad-214">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="f0bad-214">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="f0bad-215">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="f0bad-215">Understand the problem</span></span>
> - <span data-ttu-id="f0bad-216">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="f0bad-216">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="f0bad-217">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="f0bad-217">Prepare the data</span></span>
> - <span data-ttu-id="f0bad-218">Verileri yükleme ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="f0bad-218">Load and transform the data</span></span>
> - <span data-ttu-id="f0bad-219">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="f0bad-219">Choose a learning algorithm</span></span>
> - <span data-ttu-id="f0bad-220">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="f0bad-220">Train the model</span></span>
> - <span data-ttu-id="f0bad-221">Tahmin için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="f0bad-221">Use the model for predictions</span></span>

<span data-ttu-id="f0bad-222">Öğrenmeye devam etmek ve daha fazla örnek bulmak için GitHub depomuza göz atın.</span><span class="sxs-lookup"><span data-stu-id="f0bad-222">Check out our GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="f0bad-223">DotNet/machinöğrenim GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="f0bad-223">dotnet/machinelearning GitHub repository</span></span>](https://github.com/dotnet/machinelearning/)
