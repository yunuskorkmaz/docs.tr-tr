---
title: 'Öğretici: Iris çiçekleri kategorilere ayır-k-bir kümeleme'
description: Kümeleme senaryosunda ML.NET kullanmayı öğrenin
author: pkulikov
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 174907adac5741d5cc7d02cb134921debc586061
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78241097"
---
# <a name="tutorial-categorize-iris-flowers-using-k-means-clustering-with-mlnet"></a><span data-ttu-id="5b2d3-103">Öğretici: Iris çiçekler 'i k-ML.NET Kümelemesi kullanarak kategorilere ayırın</span><span class="sxs-lookup"><span data-stu-id="5b2d3-103">Tutorial: Categorize iris flowers using k-means clustering with ML.NET</span></span>

<span data-ttu-id="5b2d3-104">Bu öğreticide, [Iris çiçek veri kümesi](https://en.wikipedia.org/wiki/Iris_flower_data_set)için bir [kümeleme modeli](../resources/tasks.md#clustering) oluşturmak üzere ml.net 'in nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-104">This tutorial illustrates how to use ML.NET to build a [clustering model](../resources/tasks.md#clustering) for the [iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span></span>

<span data-ttu-id="5b2d3-105">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="5b2d3-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="5b2d3-106">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="5b2d3-106">Understand the problem</span></span>
> - <span data-ttu-id="5b2d3-107">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="5b2d3-107">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="5b2d3-108">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="5b2d3-108">Prepare the data</span></span>
> - <span data-ttu-id="5b2d3-109">Verileri yükleme ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="5b2d3-109">Load and transform the data</span></span>
> - <span data-ttu-id="5b2d3-110">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="5b2d3-110">Choose a learning algorithm</span></span>
> - <span data-ttu-id="5b2d3-111">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="5b2d3-111">Train the model</span></span>
> - <span data-ttu-id="5b2d3-112">Tahmin için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="5b2d3-112">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5b2d3-113">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="5b2d3-113">Prerequisites</span></span>

- <span data-ttu-id="5b2d3-114">[Visual Studio 2017 sürüm 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core platformlar arası geliştirme" iş yükü yüklendi.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-114">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="5b2d3-115">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="5b2d3-115">Understand the problem</span></span>

<span data-ttu-id="5b2d3-116">Bu sorun, bir Iris çiçekler kümesini, çiçek özelliklerine göre farklı gruplarda bölmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-116">This problem is about dividing the set of iris flowers in different groups based on the flower features.</span></span> <span data-ttu-id="5b2d3-117">Bu özellikler, bir sepal 'ın uzunluğu ve genişliği ve Petal 'ın uzunluğu ve genişliği.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-117">Those features are the length and width of a sepal and the length and width of a petal.</span></span> <span data-ttu-id="5b2d3-118">Bu öğretici için, her çiçek türünün bilinmediğini varsayın.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-118">For this tutorial, assume that the type of each flower is unknown.</span></span> <span data-ttu-id="5b2d3-119">Özelliklerden bir veri kümesinin yapısını öğrenmek ve bir veri örneğinin bu yapıya nasıl uyduğunu tahmin etmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-119">You want to learn the structure of a data set from the features and predict how a data instance fits this structure.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="5b2d3-120">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="5b2d3-120">Select the appropriate machine learning task</span></span>

<span data-ttu-id="5b2d3-121">Her bir çiçek 'nin hangi gruba ait olduğunu bilmiyorsanız, denetimli [makine öğrenimi](../resources/glossary.md#unsupervised-machine-learning) görevini seçersiniz.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-121">As you don't know to which group each flower belongs to, you choose the [unsupervised machine learning](../resources/glossary.md#unsupervised-machine-learning) task.</span></span> <span data-ttu-id="5b2d3-122">Gruplardaki bir veri kümesini, aynı gruptaki öğelerin diğer gruplardaki diğer gruplardan birbirlerine benzer şekilde bölmek için, bir [kümeleme](../resources/tasks.md#clustering) Machine Learning görevi kullanın.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-122">To divide a data set in groups in such a way that elements in the same group are more similar to each other than to those in other groups, use a [clustering](../resources/tasks.md#clustering) machine learning task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="5b2d3-123">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="5b2d3-123">Create a console application</span></span>

1. <span data-ttu-id="5b2d3-124">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-124">Open Visual Studio.</span></span> <span data-ttu-id="5b2d3-125">Menü çubuğundan **dosya** > **Yeni** > **projesi** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-125">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="5b2d3-126">**Yeni proje** iletişim kutusunda,  **C# Visual** düğümünü ve ardından **.NET Core** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-126">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="5b2d3-127">Ardından **konsol uygulaması (.NET Core)** proje şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-127">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="5b2d3-128">**Ad** metin kutusuna "ırisflowerkümeleme" yazın ve **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-128">In the **Name** text box, type "IrisFlowerClustering" and then select the **OK** button.</span></span>

1. <span data-ttu-id="5b2d3-129">Veri kümesi ve model dosyalarını depolamak için projenizde *veri* adlı bir dizin oluşturun:</span><span class="sxs-lookup"><span data-stu-id="5b2d3-129">Create a directory named *Data* in your project to store the data set and model files:</span></span>

    <span data-ttu-id="5b2d3-130">**Çözüm Gezgini**, projeye sağ tıklayın ve > **Yeni klasör** **Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-130">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="5b2d3-131">"Data" yazın ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-131">Type "Data" and hit Enter.</span></span>

1. <span data-ttu-id="5b2d3-132">**Microsoft.ml** NuGet paketini yükler:</span><span class="sxs-lookup"><span data-stu-id="5b2d3-132">Install the **Microsoft.ML** NuGet package:</span></span>

    <span data-ttu-id="5b2d3-133">**Çözüm Gezgini**, projeye sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-133">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="5b2d3-134">Paket kaynağı olarak "nuget.org" öğesini seçin, **Gözden** geçirme sekmesini seçin, **Microsoft.ml** araması yapın ve **yüklemeyi** seçin.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-134">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML** and select the **Install** button.</span></span> <span data-ttu-id="5b2d3-135">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-135">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-the-data"></a><span data-ttu-id="5b2d3-136">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="5b2d3-136">Prepare the data</span></span>

1. <span data-ttu-id="5b2d3-137">[Iris. Data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) veri kümesini indirin ve önceki adımda oluşturduğunuz *veri* klasörüne kaydedin.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-137">Download the [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) data set and save it to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="5b2d3-138">Iris veri kümesi hakkında daha fazla bilgi için, veri kümesinin kaynağı olan [Iris çiçek veri kümesi](https://en.wikipedia.org/wiki/Iris_flower_data_set) vikipi sayfasında ve [Iris veri kümesi](https://archive.ics.uci.edu/ml/datasets/Iris) sayfasına bakın.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-138">For more information about the iris data set, see the [Iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set) Wikipedia page and the [Iris Data Set](https://archive.ics.uci.edu/ml/datasets/Iris) page, which is the source of the data set.</span></span>

1. <span data-ttu-id="5b2d3-139">**Çözüm Gezgini**, *Iris. Data* dosyasına sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-139">In **Solution Explorer**, right-click the *iris.data* file and select **Properties**.</span></span> <span data-ttu-id="5b2d3-140">**Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-140">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="5b2d3-141">*Iris. Data* dosyası, şunları temsil eden beş sütun içerir:</span><span class="sxs-lookup"><span data-stu-id="5b2d3-141">The *iris.data* file contains five columns that represent:</span></span>

- <span data-ttu-id="5b2d3-142">santimetres cinsinden sepal uzunluğu</span><span class="sxs-lookup"><span data-stu-id="5b2d3-142">sepal length in centimetres</span></span>
- <span data-ttu-id="5b2d3-143">santimetres cinsinden sepal genişliği</span><span class="sxs-lookup"><span data-stu-id="5b2d3-143">sepal width in centimetres</span></span>
- <span data-ttu-id="5b2d3-144">santimetres 'de Petal uzunluğu</span><span class="sxs-lookup"><span data-stu-id="5b2d3-144">petal length in centimetres</span></span>
- <span data-ttu-id="5b2d3-145">santimetres 'de Petal genişliği</span><span class="sxs-lookup"><span data-stu-id="5b2d3-145">petal width in centimetres</span></span>
- <span data-ttu-id="5b2d3-146">Iris çiçek türü</span><span class="sxs-lookup"><span data-stu-id="5b2d3-146">type of iris flower</span></span>

<span data-ttu-id="5b2d3-147">Kümeleme örneği için bu öğretici son sütunu yoksayar.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-147">For the sake of the clustering example, this tutorial ignores the last column.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="5b2d3-148">Veri sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="5b2d3-148">Create data classes</span></span>

<span data-ttu-id="5b2d3-149">Giriş verileri ve tahminleri için sınıflar oluşturun:</span><span class="sxs-lookup"><span data-stu-id="5b2d3-149">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="5b2d3-150">**Çözüm Gezgini**, projeye sağ tıklayın ve ardından > **Yeni öğe** **Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-150">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="5b2d3-151">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *IrisData.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-151">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *IrisData.cs*.</span></span> <span data-ttu-id="5b2d3-152">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-152">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="5b2d3-153">Aşağıdaki `using` yönergesini yeni dosyaya ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5b2d3-153">Add the following `using` directive to the new file:</span></span>

   [!code-csharp[Add necessary usings](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/IrisData.cs#Usings)]

<span data-ttu-id="5b2d3-154">Mevcut sınıf tanımını kaldırın ve *IrisData.cs* dosyasına `IrisData` ve `ClusterPrediction`sınıflarını tanımlayan aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5b2d3-154">Remove the existing class definition and add the following code, which defines the classes `IrisData` and `ClusterPrediction`, to the *IrisData.cs* file:</span></span>

[!code-csharp[Define data classes](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/IrisData.cs#ClassDefinitions)]

<span data-ttu-id="5b2d3-155">`IrisData`, giriş veri sınıfıdır ve veri kümesindeki her bir özellik için tanımlar içerir.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-155">`IrisData` is the input data class and has definitions for each feature from the data set.</span></span> <span data-ttu-id="5b2d3-156">Veri kümesi dosyasındaki kaynak sütunlarının dizinlerini belirtmek için [Loadcolumn](xref:Microsoft.ML.Data.LoadColumnAttribute) özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-156">Use the [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute to specify the indices of the source columns in the data set file.</span></span>

<span data-ttu-id="5b2d3-157">`ClusterPrediction` sınıfı, bir `IrisData` örneğine uygulanan kümeleme modelinin çıkışını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-157">The `ClusterPrediction` class represents the output of the clustering model applied to an `IrisData` instance.</span></span> <span data-ttu-id="5b2d3-158">`PredictedClusterId` ve `Distances` alanlarını tahmine **Tedlabel** öğesine bağlamak için [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) özniteliğini kullanın ve sütunları sırasıyla **puan** yapın.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-158">Use the [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute to bind the `PredictedClusterId` and `Distances` fields to the **PredictedLabel** and **Score** columns respectively.</span></span> <span data-ttu-id="5b2d3-159">Kümeleme görevi söz konusu sütunlarda aşağıdaki anlamı vardır:</span><span class="sxs-lookup"><span data-stu-id="5b2d3-159">In case of the clustering task those columns have the following meaning:</span></span>

- <span data-ttu-id="5b2d3-160">**Predictedlabel** sütunu, tahmin EDILEN kümenin kimliğini içerir.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-160">**PredictedLabel** column contains the ID of the predicted cluster.</span></span>
- <span data-ttu-id="5b2d3-161">**Puan** sütunu, kare Içinde Euclidea uzaklıkları küme centroıd 'leri için olan bir dizi içeriyor.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-161">**Score** column contains an array with squared Euclidean distances to the cluster centroids.</span></span> <span data-ttu-id="5b2d3-162">Dizi uzunluğu, küme sayısına eşittir.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-162">The array length is equal to the number of clusters.</span></span>

> [!NOTE]
> <span data-ttu-id="5b2d3-163">Giriş ve tahmin veri sınıflarında kayan nokta değerlerini göstermek için `float` türünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-163">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="5b2d3-164">Veri ve model yollarını tanımlama</span><span class="sxs-lookup"><span data-stu-id="5b2d3-164">Define data and model paths</span></span>

<span data-ttu-id="5b2d3-165">*Program.cs* dosyasına dönün ve veri kümesi dosyasına ve modelin kaydedileceği dosyanın yollarını barındıracak iki alan ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5b2d3-165">Go back to the *Program.cs* file and add two fields to hold the paths to the data set file and to the file to save the model:</span></span>

- <span data-ttu-id="5b2d3-166">`_dataPath`, modeli eğitmek için kullanılan veri kümesiyle dosyanın yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-166">`_dataPath` contains the path to the file with the data set used to train the model.</span></span>
- <span data-ttu-id="5b2d3-167">`_modelPath`, eğitilen modelin depolandığı dosyanın yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-167">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="5b2d3-168">Aşağıdaki kodu, bu yolları belirtmek için `Main` yönteminin üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5b2d3-168">Add the following code right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Initialize paths](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#Paths)]

<span data-ttu-id="5b2d3-169">Önceki kodu derlemek için, *program.cs* dosyasının en üstüne aşağıdaki `using` yönergelerini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5b2d3-169">To make the preceding code compile, add the following `using` directives at the top of the *Program.cs* file:</span></span>

[!code-csharp[Add usings for paths](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a><span data-ttu-id="5b2d3-170">ML bağlamı oluştur</span><span class="sxs-lookup"><span data-stu-id="5b2d3-170">Create ML context</span></span>

<span data-ttu-id="5b2d3-171">Aşağıdaki ek `using` yönergelerini *program.cs* dosyasının en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5b2d3-171">Add the following additional `using` directives to the top of the *Program.cs* file:</span></span>

[!code-csharp[Add Microsoft.ML usings](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#MLUsings)]

<span data-ttu-id="5b2d3-172">`Main` yönteminde, `Console.WriteLine("Hello World!");` satırını aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="5b2d3-172">In the `Main` method, replace the `Console.WriteLine("Hello World!");` line with the following code:</span></span>

[!code-csharp[Create ML context](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#CreateContext)]

<span data-ttu-id="5b2d3-173"><xref:Microsoft.ML.MLContext?displayProperty=nameWithType> sınıfı, Machine Learning ortamını temsil eder ve veri yükleme, model eğitimi, tahmin ve diğer görevler için günlüğe kaydetme ve giriş noktaları için mekanizmalar sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-173">The <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> class represents the machine learning environment and provides mechanisms for logging and entry points for data loading, model training, prediction, and other tasks.</span></span> <span data-ttu-id="5b2d3-174">Bu, Entity Framework `DbContext` kullanımı kavramsal olarak karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-174">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span>

## <a name="set-up-data-loading"></a><span data-ttu-id="5b2d3-175">Veri yüklemeyi ayarlama</span><span class="sxs-lookup"><span data-stu-id="5b2d3-175">Set up data loading</span></span>

<span data-ttu-id="5b2d3-176">Aşağıdaki kodu `Main` yöntemine ekleyerek verileri yükleme yolunu ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="5b2d3-176">Add the following code to the `Main` method to set up the way to load data:</span></span>

[!code-csharp[Create text loader](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#CreateDataView)]

<span data-ttu-id="5b2d3-177">Genel [`MLContext.Data.LoadFromTextFile` uzantısı yöntemi](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) , belirtilen `IrisData` türünden veri kümesi şemasını kullanır ve dönüştürücüler için giriş olarak kullanılabilecek <xref:Microsoft.ML.IDataView> döndürür.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-177">The generic [`MLContext.Data.LoadFromTextFile` extension method](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) infers the data set schema from the provided `IrisData` type and returns <xref:Microsoft.ML.IDataView> which can be used as input for transformers.</span></span>

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="5b2d3-178">Öğrenme işlem hattı oluşturma</span><span class="sxs-lookup"><span data-stu-id="5b2d3-178">Create a learning pipeline</span></span>

<span data-ttu-id="5b2d3-179">Bu öğreticide, kümeleme görevinin öğrenme işlem hattı aşağıdaki iki adımdan oluşur:</span><span class="sxs-lookup"><span data-stu-id="5b2d3-179">For this tutorial, the learning pipeline of the clustering task comprises two following steps:</span></span>

- <span data-ttu-id="5b2d3-180">yüklenen sütunları bir kümeleme işlemi tarafından kullanılan tek bir **Özellikler** sütununa birleştirme;</span><span class="sxs-lookup"><span data-stu-id="5b2d3-180">concatenate loaded columns into one **Features** column, which is used by a clustering trainer;</span></span>
- <span data-ttu-id="5b2d3-181">k-ortalamalar + + kümeleme algoritmasını kullanarak modeli eğitme için bir <xref:Microsoft.ML.Trainers.KMeansTrainer> eğitmen kullanın.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-181">use a <xref:Microsoft.ML.Trainers.KMeansTrainer> trainer to train the model using the k-means++ clustering algorithm.</span></span>

<span data-ttu-id="5b2d3-182">`Main` yöntemine aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5b2d3-182">Add the following code to the `Main` method:</span></span>

[!code-csharp[Create pipeline](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#CreatePipeline)]

<span data-ttu-id="5b2d3-183">Kod, veri kümesinin üç kümede bölünmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-183">The code specifies that the data set should be split in three clusters.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="5b2d3-184">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="5b2d3-184">Train the model</span></span>

<span data-ttu-id="5b2d3-185">Önceki bölümlerde eklenen adımlar, eğitim için işlem hattını hazırlandı, ancak hiçbiri yürütülmedi.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-185">The steps added in the preceding sections prepared the pipeline for training, however, none have been executed.</span></span> <span data-ttu-id="5b2d3-186">Veri yükleme ve model eğitimi gerçekleştirmek için aşağıdaki satırı `Main` yöntemine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5b2d3-186">Add the following line to the `Main` method to perform data loading and model training:</span></span>

[!code-csharp[Train the model](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#TrainModel)]

### <a name="save-the-model"></a><span data-ttu-id="5b2d3-187">Modeli kaydetme</span><span class="sxs-lookup"><span data-stu-id="5b2d3-187">Save the model</span></span>

<span data-ttu-id="5b2d3-188">Bu noktada, mevcut veya yeni .NET uygulamalarından tümleştirilebilen bir modeliniz vardır.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-188">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="5b2d3-189">Modelinizi bir. zip dosyasına kaydetmek için `Main` yöntemine aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5b2d3-189">To save your model to a .zip file, add the following code to the `Main` method:</span></span>

[!code-csharp[Save the model](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="5b2d3-190">Tahmin için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="5b2d3-190">Use the model for predictions</span></span>

<span data-ttu-id="5b2d3-191">Tahmine dayalı hale getirmek için, transformatör işlem hattı aracılığıyla giriş türünün örneklerini alan <xref:Microsoft.ML.PredictionEngine%602> sınıfını kullanın ve çıkış türünün örneklerini üretir.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-191">To make predictions, use the <xref:Microsoft.ML.PredictionEngine%602> class that takes instances of the input type through the transformer pipeline and produces instances of the output type.</span></span> <span data-ttu-id="5b2d3-192">Aşağıdaki satırı, bu sınıfın bir örneğini oluşturmak için `Main` yöntemine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5b2d3-192">Add the following line to the `Main` method to create an instance of that class:</span></span>

[!code-csharp[Create predictor](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#Predictor)]

<span data-ttu-id="5b2d3-193">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneğinde tahmin gerçekleştirmenize olanak tanıyan, KULLANıŞLı bir API 'dir.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-193">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="5b2d3-194">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) , iş parçacığı açısından güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-194">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="5b2d3-195">Tek iş parçacıklı veya prototip ortamlarında kullanılması kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-195">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="5b2d3-196">Üretim ortamlarında geliştirilmiş performans ve iş parçacığı güvenliği için, uygulamanız genelinde kullanılmak üzere [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) nesnelerinin bir [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) oluşturan `PredictionEnginePool` hizmetini kullanın.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-196">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="5b2d3-197">[ASP.NET Core Web API 'sindeki `PredictionEnginePool` kullanma](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)hakkında bu kılavuza bakın.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-197">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

> [!NOTE]
> <span data-ttu-id="5b2d3-198">`PredictionEnginePool` hizmet uzantısı Şu anda önizleme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-198">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="5b2d3-199">Test verileri örneklerini barındırmak için `TestIrisData` sınıfını oluşturun:</span><span class="sxs-lookup"><span data-stu-id="5b2d3-199">Create the `TestIrisData` class to house test data instances:</span></span>

1. <span data-ttu-id="5b2d3-200">**Çözüm Gezgini**, projeye sağ tıklayın ve ardından > **Yeni öğe** **Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-200">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="5b2d3-201">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *TestIrisData.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-201">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestIrisData.cs*.</span></span> <span data-ttu-id="5b2d3-202">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-202">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="5b2d3-203">Aşağıdaki örnekte olduğu gibi, sınıfı statik olacak şekilde değiştirin:</span><span class="sxs-lookup"><span data-stu-id="5b2d3-203">Modify the class to be static like in the following example:</span></span>

   [!code-csharp[Make class static](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/TestIrisData.cs#Static)]

<span data-ttu-id="5b2d3-204">Bu öğretici, bu sınıf içindeki bir Iris veri örneğini tanıtır.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-204">This tutorial introduces one iris data instance within this class.</span></span> <span data-ttu-id="5b2d3-205">Modelle denemeler yapmak için başka senaryolar da ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-205">You can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="5b2d3-206">`TestIrisData` sınıfına aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5b2d3-206">Add the following code into the `TestIrisData` class:</span></span>

[!code-csharp[Test data](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/TestIrisData.cs#TestData)]

<span data-ttu-id="5b2d3-207">Belirtilen öğenin ait olduğu kümeyi bulmak için, *program.cs* dosyasına dönün ve `Main` yöntemine aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5b2d3-207">To find out the cluster to which the specified item belongs to, go back to the *Program.cs* file and add the following code into the `Main` method:</span></span>

[!code-csharp[Predict and output results](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#PredictionExample)]

<span data-ttu-id="5b2d3-208">Hangi kümenin belirtilen veri örneğini içerdiğini ve bu örnekten gelen kare uzaklıkları küme centroıd 'lerini görmek için programı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-208">Run the program to see which cluster contains the specified data instance and squared distances from that instance to the cluster centroids.</span></span> <span data-ttu-id="5b2d3-209">Sonuçlarınız aşağıdakine benzer olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="5b2d3-209">Your results should be similar to the following:</span></span>

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

<span data-ttu-id="5b2d3-210">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="5b2d3-210">Congratulations!</span></span> <span data-ttu-id="5b2d3-211">Iris Kümelemesi için bir makine öğrenimi modeli başarıyla oluşturdunuz ve bu uygulamayı tahmine dayalı hale getirmek için kullandınız.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-211">You've now successfully built a machine learning model for iris clustering and used it to make predictions.</span></span> <span data-ttu-id="5b2d3-212">Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-212">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="5b2d3-213">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="5b2d3-213">Next steps</span></span>

<span data-ttu-id="5b2d3-214">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="5b2d3-214">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="5b2d3-215">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="5b2d3-215">Understand the problem</span></span>
> - <span data-ttu-id="5b2d3-216">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="5b2d3-216">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="5b2d3-217">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="5b2d3-217">Prepare the data</span></span>
> - <span data-ttu-id="5b2d3-218">Verileri yükleme ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="5b2d3-218">Load and transform the data</span></span>
> - <span data-ttu-id="5b2d3-219">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="5b2d3-219">Choose a learning algorithm</span></span>
> - <span data-ttu-id="5b2d3-220">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="5b2d3-220">Train the model</span></span>
> - <span data-ttu-id="5b2d3-221">Tahmin için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="5b2d3-221">Use the model for predictions</span></span>

<span data-ttu-id="5b2d3-222">Öğrenmeye devam etmek ve daha fazla örnek bulmak için GitHub depomuza göz atın.</span><span class="sxs-lookup"><span data-stu-id="5b2d3-222">Check out our GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="5b2d3-223">DotNet/machinöğrenim GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="5b2d3-223">dotnet/machinelearning GitHub repository</span></span>](https://github.com/dotnet/machinelearning/)
