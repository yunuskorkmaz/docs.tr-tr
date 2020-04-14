---
title: 'Öğretici: Iris çiçek kategorize - k-kümeleme anlamına gelir'
description: kümeleme senaryosunda ML.NET nasıl kullanılacağını öğrenin
author: pkulikov
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 03ce1a5f3ef4d4da01f848cac0c520a5a6aaf4bf
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242796"
---
# <a name="tutorial-categorize-iris-flowers-using-k-means-clustering-with-mlnet"></a><span data-ttu-id="7aaf2-103">Öğretici: ML.NET ile k-araçları kümeleme kullanarak iris çiçekler kategorize</span><span class="sxs-lookup"><span data-stu-id="7aaf2-103">Tutorial: Categorize iris flowers using k-means clustering with ML.NET</span></span>

<span data-ttu-id="7aaf2-104">Bu öğretici, [iris çiçek veri kümesi](https://en.wikipedia.org/wiki/Iris_flower_data_set)için bir [kümeleme modeli](../resources/tasks.md#clustering) oluşturmak için ML.NET nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-104">This tutorial illustrates how to use ML.NET to build a [clustering model](../resources/tasks.md#clustering) for the [iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span></span>

<span data-ttu-id="7aaf2-105">Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7aaf2-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="7aaf2-106">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="7aaf2-106">Understand the problem</span></span>
> - <span data-ttu-id="7aaf2-107">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="7aaf2-107">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="7aaf2-108">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="7aaf2-108">Prepare the data</span></span>
> - <span data-ttu-id="7aaf2-109">Verileri yükleme ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="7aaf2-109">Load and transform the data</span></span>
> - <span data-ttu-id="7aaf2-110">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="7aaf2-110">Choose a learning algorithm</span></span>
> - <span data-ttu-id="7aaf2-111">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="7aaf2-111">Train the model</span></span>
> - <span data-ttu-id="7aaf2-112">Öngörüler için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="7aaf2-112">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7aaf2-113">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="7aaf2-113">Prerequisites</span></span>

- <span data-ttu-id="7aaf2-114">[Visual Studio 2017 sürüm 15.6 veya daha sonra](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core çapraz platform geliştirme" iş yükü yüklendi.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-114">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="7aaf2-115">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="7aaf2-115">Understand the problem</span></span>

<span data-ttu-id="7aaf2-116">Bu sorun, çiçek özelliklerine göre farklı gruplarhalinde iris çiçek kümesi bölen ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-116">This problem is about dividing the set of iris flowers in different groups based on the flower features.</span></span> <span data-ttu-id="7aaf2-117">Bu özellikler bir sepal uzunluğu ve genişliği ve bir taç yaprağı uzunluğu ve genişliği vardır.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-117">Those features are the length and width of a sepal and the length and width of a petal.</span></span> <span data-ttu-id="7aaf2-118">Bu öğretici için, her çiçeğin türü bilinmiyor varsayalım.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-118">For this tutorial, assume that the type of each flower is unknown.</span></span> <span data-ttu-id="7aaf2-119">Özelliklerden bir veri kümesinin yapısını öğrenmek ve bir veri örneğinin bu yapıya nasıl uyduğunu tahmin etmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-119">You want to learn the structure of a data set from the features and predict how a data instance fits this structure.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="7aaf2-120">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="7aaf2-120">Select the appropriate machine learning task</span></span>

<span data-ttu-id="7aaf2-121">Her çiçeğin hangi gruba ait olduğunu bilmediğiniz için [denetimsiz makine öğrenimi](../resources/glossary.md#unsupervised-machine-learning) görevini seçersiniz.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-121">As you don't know to which group each flower belongs to, you choose the [unsupervised machine learning](../resources/glossary.md#unsupervised-machine-learning) task.</span></span> <span data-ttu-id="7aaf2-122">Bir veri kümesini, aynı gruptaki öğelerin diğer gruplardakiöğelere göre birbirine daha çok benzer şekilde gruplara bölmek için, bir [kümeleme](../resources/tasks.md#clustering) makinesi öğrenme görevi kullanın.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-122">To divide a data set in groups in such a way that elements in the same group are more similar to each other than to those in other groups, use a [clustering](../resources/tasks.md#clustering) machine learning task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="7aaf2-123">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="7aaf2-123">Create a console application</span></span>

1. <span data-ttu-id="7aaf2-124">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-124">Open Visual Studio.</span></span> <span data-ttu-id="7aaf2-125">Menü çubuğundan**Yeni** > **Proje** **Dosyası'nı** > seçin.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-125">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="7aaf2-126">Yeni **Proje** iletişim kutusunda, **.NET Core** düğümünü izleyen **Visual C#** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-126">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="7aaf2-127">Ardından **Konsol Uygulaması (.NET Core)** proje şablonu'nu seçin.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-127">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="7aaf2-128">**Ad** metin kutusunda "IrisFlowerClustering" yazın ve **ardından Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-128">In the **Name** text box, type "IrisFlowerClustering" and then select the **OK** button.</span></span>

1. <span data-ttu-id="7aaf2-129">Veri kümesini ve model dosyalarını depolamak için projenizde *Veri* adlı bir dizin oluşturun:</span><span class="sxs-lookup"><span data-stu-id="7aaf2-129">Create a directory named *Data* in your project to store the data set and model files:</span></span>

    <span data-ttu-id="7aaf2-130">**Çözüm Gezgini'nde**projeyi sağ tıklatın ve**Yeni Klasör** **Ekle'yi** > seçin.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-130">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="7aaf2-131">"Veri" yazın ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-131">Type "Data" and hit Enter.</span></span>

1. <span data-ttu-id="7aaf2-132">**Microsoft.ML** NuGet paketini yükleyin:</span><span class="sxs-lookup"><span data-stu-id="7aaf2-132">Install the **Microsoft.ML** NuGet package:</span></span>

    <span data-ttu-id="7aaf2-133">**Çözüm Gezgini'nde**projeyi sağ tıklatın ve **NuGet Paketlerini Yönet'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-133">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="7aaf2-134">Paket kaynağı olarak "nuget.org" seçeneğini belirleyin, **Gözat** sekmesini seçin, **Microsoft.ML** arayın ve **Yükle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-134">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML** and select the **Install** button.</span></span> <span data-ttu-id="7aaf2-135">**Değişiklikler Önizleme** iletişim kutusundaki **Tamam** düğmesini seçin ve listelenen paketlerin lisans koşullarını kabul ederseniz Lisans Kabul iletişim kutusundaki **Kabul** **Et** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-135">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-the-data"></a><span data-ttu-id="7aaf2-136">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="7aaf2-136">Prepare the data</span></span>

1. <span data-ttu-id="7aaf2-137">[iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) veri kümesini indirin ve önceki adımda oluşturduğunuz *Veri* klasörüne kaydedin.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-137">Download the [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) data set and save it to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="7aaf2-138">Iris veri kümesi hakkında daha fazla bilgi [için, iris çiçek veri seti](https://en.wikipedia.org/wiki/Iris_flower_data_set) Vikipedi sayfasına ve veri kümesinin kaynağı olan [Iris Veri Seti](http://archive.ics.uci.edu/ml/datasets/Iris) sayfasına bakın.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-138">For more information about the iris data set, see the [Iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set) Wikipedia page and the [Iris Data Set](http://archive.ics.uci.edu/ml/datasets/Iris) page, which is the source of the data set.</span></span>

1. <span data-ttu-id="7aaf2-139">**Çözüm Gezgini'nde** *iris.data* dosyasına sağ tıklayın ve **Özellikler'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-139">In **Solution Explorer**, right-click the *iris.data* file and select **Properties**.</span></span> <span data-ttu-id="7aaf2-140">**Gelişmiş**altında, **daha yeniyse**Kopyala'dan **Çıktı Dizini'ne Kopya** değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-140">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="7aaf2-141">*iris.data* dosyası, aşağıdakileri temsil eden beş sütun içerir:</span><span class="sxs-lookup"><span data-stu-id="7aaf2-141">The *iris.data* file contains five columns that represent:</span></span>

- <span data-ttu-id="7aaf2-142">santimetre sepal uzunluğu</span><span class="sxs-lookup"><span data-stu-id="7aaf2-142">sepal length in centimeters</span></span>
- <span data-ttu-id="7aaf2-143">santimetre sepal genişliği</span><span class="sxs-lookup"><span data-stu-id="7aaf2-143">sepal width in centimeters</span></span>
- <span data-ttu-id="7aaf2-144">santimetre yaprak uzunluğu</span><span class="sxs-lookup"><span data-stu-id="7aaf2-144">petal length in centimeters</span></span>
- <span data-ttu-id="7aaf2-145">santimetre yaprak genişliği</span><span class="sxs-lookup"><span data-stu-id="7aaf2-145">petal width in centimeters</span></span>
- <span data-ttu-id="7aaf2-146">iris çiçek türü</span><span class="sxs-lookup"><span data-stu-id="7aaf2-146">type of iris flower</span></span>

<span data-ttu-id="7aaf2-147">Kümeleme örneğinin hatırına, bu öğretici son sütunu yok sayar.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-147">For the sake of the clustering example, this tutorial ignores the last column.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="7aaf2-148">Veri sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="7aaf2-148">Create data classes</span></span>

<span data-ttu-id="7aaf2-149">Giriş verileri ve öngörüler için sınıflar oluşturun:</span><span class="sxs-lookup"><span data-stu-id="7aaf2-149">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="7aaf2-150">**Çözüm Gezgini'nde,** projeyi sağ tıklatın ve ardından**Yeni Öğe** **Ekle'yi** > seçin.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-150">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="7aaf2-151">Yeni **Öğe Ekle** iletişim kutusunda **Sınıf'ı** seçin ve **Ad** alanını *IrisData.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-151">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *IrisData.cs*.</span></span> <span data-ttu-id="7aaf2-152">Ardından **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-152">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="7aaf2-153">Yeni dosyaya aşağıdaki `using` yönergeyi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7aaf2-153">Add the following `using` directive to the new file:</span></span>

   [!code-csharp[Add necessary usings](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/IrisData.cs#Usings)]

<span data-ttu-id="7aaf2-154">Varolan sınıf tanımını kaldırın ve IrisData.cs dosyasına `IrisData` `ClusterPrediction`sınıfları *IrisData.cs* ve , tanımlayan aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7aaf2-154">Remove the existing class definition and add the following code, which defines the classes `IrisData` and `ClusterPrediction`, to the *IrisData.cs* file:</span></span>

[!code-csharp[Define data classes](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/IrisData.cs#ClassDefinitions)]

<span data-ttu-id="7aaf2-155">`IrisData`giriş veri sınıfıdır ve veri kümesinden her özellik için tanımlar vardır.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-155">`IrisData` is the input data class and has definitions for each feature from the data set.</span></span> <span data-ttu-id="7aaf2-156">Veri kümesi dosyasındaki kaynak sütunların dizinlerini belirtmek için [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-156">Use the [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute to specify the indices of the source columns in the data set file.</span></span>

<span data-ttu-id="7aaf2-157">Sınıf, `ClusterPrediction` bir `IrisData` örne uygulanan kümeleme modelinin çıktısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-157">The `ClusterPrediction` class represents the output of the clustering model applied to an `IrisData` instance.</span></span> <span data-ttu-id="7aaf2-158">Sütun [Adı](xref:Microsoft.ML.Data.ColumnNameAttribute) özniteliğini kullanarak `PredictedClusterId` alanları `Distances` ve alanları **Sırasıyla PredictedLabel** ve **Score** sütunlarına bağlayın.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-158">Use the [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute to bind the `PredictedClusterId` and `Distances` fields to the **PredictedLabel** and **Score** columns respectively.</span></span> <span data-ttu-id="7aaf2-159">Kümeleme görevi söz konusu olduğunda bu sütunlar aşağıdaki anlamlara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="7aaf2-159">In case of the clustering task those columns have the following meaning:</span></span>

- <span data-ttu-id="7aaf2-160">**PredictedLabel** sütunu, tahmin edilen kümenin kimliğini içerir.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-160">**PredictedLabel** column contains the ID of the predicted cluster.</span></span>
- <span data-ttu-id="7aaf2-161">**Puan** sütunu küme centroids kare Öklid mesafeleri olan bir dizi içerir.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-161">**Score** column contains an array with squared Euclidean distances to the cluster centroids.</span></span> <span data-ttu-id="7aaf2-162">Dizi uzunluğu küme sayısına eşittir.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-162">The array length is equal to the number of clusters.</span></span>

> [!NOTE]
> <span data-ttu-id="7aaf2-163">Giriş `float` ve tahmin veri sınıflarında kayan nokta değerlerini temsil etmek için türü kullanın.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-163">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="7aaf2-164">Veri ve model yollarını tanımlama</span><span class="sxs-lookup"><span data-stu-id="7aaf2-164">Define data and model paths</span></span>

<span data-ttu-id="7aaf2-165">*Program.cs* dosyasına geri dön ve veri kümesi dosyasına ve modeli kaydetmek için dosyaya giden yolları tutmak için iki alan ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7aaf2-165">Go back to the *Program.cs* file and add two fields to hold the paths to the data set file and to the file to save the model:</span></span>

- <span data-ttu-id="7aaf2-166">`_dataPath`modeli eğitmek için kullanılan veri kümesi ile dosyaya giden yolu içerir.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-166">`_dataPath` contains the path to the file with the data set used to train the model.</span></span>
- <span data-ttu-id="7aaf2-167">`_modelPath`ilgili modelin depolandığı dosyaya giden yolu içerir.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-167">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="7aaf2-168">Bu yolları belirtmek için `Main` yöntemin hemen üstüne aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7aaf2-168">Add the following code right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Initialize paths](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#Paths)]

<span data-ttu-id="7aaf2-169">Önceki kodu derlemek *için, Program.cs* `using` dosyasının üst kısmında aşağıdaki yönergeleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7aaf2-169">To make the preceding code compile, add the following `using` directives at the top of the *Program.cs* file:</span></span>

[!code-csharp[Add usings for paths](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a><span data-ttu-id="7aaf2-170">ML bağlamı oluşturma</span><span class="sxs-lookup"><span data-stu-id="7aaf2-170">Create ML context</span></span>

<span data-ttu-id="7aaf2-171">Program.cs dosyasının `using` üst bölümüne aşağıdaki *Program.cs* ek yönergeleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7aaf2-171">Add the following additional `using` directives to the top of the *Program.cs* file:</span></span>

[!code-csharp[Add Microsoft.ML usings](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#MLUsings)]

<span data-ttu-id="7aaf2-172">`Main` Yöntemde, satırı `Console.WriteLine("Hello World!");` aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="7aaf2-172">In the `Main` method, replace the `Console.WriteLine("Hello World!");` line with the following code:</span></span>

[!code-csharp[Create ML context](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#CreateContext)]

<span data-ttu-id="7aaf2-173">Sınıf <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> makine öğrenimi ortamını temsil eder ve veri yükleme, model eğitimi, tahmin ve diğer görevler için günlük ve giriş noktaları için mekanizmalar sağlar.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-173">The <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> class represents the machine learning environment and provides mechanisms for logging and entry points for data loading, model training, prediction, and other tasks.</span></span> <span data-ttu-id="7aaf2-174">Bu, kavramsal olarak `DbContext` Varlık Çerçevesi'nde kullanmakla karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-174">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span>

## <a name="set-up-data-loading"></a><span data-ttu-id="7aaf2-175">Veri yüklemeyi ayarlama</span><span class="sxs-lookup"><span data-stu-id="7aaf2-175">Set up data loading</span></span>

<span data-ttu-id="7aaf2-176">Verileri yükleme yöntemini `Main` ayarlamak için yönteme aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7aaf2-176">Add the following code to the `Main` method to set up the way to load data:</span></span>

[!code-csharp[Create text loader](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#CreateDataView)]

<span data-ttu-id="7aaf2-177">Genel [ `MLContext.Data.LoadFromTextFile` uzantı yöntemi,](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) veri kümesi şeasını `IrisData` sağlanan türden <xref:Microsoft.ML.IDataView> çıkarve transformatörler için girdi olarak kullanılabilecek döndürür.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-177">The generic [`MLContext.Data.LoadFromTextFile` extension method](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) infers the data set schema from the provided `IrisData` type and returns <xref:Microsoft.ML.IDataView> which can be used as input for transformers.</span></span>

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="7aaf2-178">Öğrenme ardışık bir yol oluşturma</span><span class="sxs-lookup"><span data-stu-id="7aaf2-178">Create a learning pipeline</span></span>

<span data-ttu-id="7aaf2-179">Bu öğretici için, kümeleme görevinin öğrenme ardışık iki adımı oluşur:</span><span class="sxs-lookup"><span data-stu-id="7aaf2-179">For this tutorial, the learning pipeline of the clustering task comprises two following steps:</span></span>

- <span data-ttu-id="7aaf2-180">yüklenen sütunları kümeleme eğitmeni tarafından kullanılan tek bir **Özellikler** sütununa dönüştürün;</span><span class="sxs-lookup"><span data-stu-id="7aaf2-180">concatenate loaded columns into one **Features** column, which is used by a clustering trainer;</span></span>
- <span data-ttu-id="7aaf2-181">k-means++ kümeleme algoritmasını kullanarak modeli eğitmek için bir <xref:Microsoft.ML.Trainers.KMeansTrainer> eğitmen kullanın.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-181">use a <xref:Microsoft.ML.Trainers.KMeansTrainer> trainer to train the model using the k-means++ clustering algorithm.</span></span>

<span data-ttu-id="7aaf2-182">`Main` yöntemine aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7aaf2-182">Add the following code to the `Main` method:</span></span>

[!code-csharp[Create pipeline](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#CreatePipeline)]

<span data-ttu-id="7aaf2-183">Kod, veri kümesinin üç kümeye bölünmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-183">The code specifies that the data set should be split in three clusters.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="7aaf2-184">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="7aaf2-184">Train the model</span></span>

<span data-ttu-id="7aaf2-185">Önceki bölümlerde eklenen adımlar, boru hattını eğitime hazırladı, ancak hiçbiri yürütülmedi.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-185">The steps added in the preceding sections prepared the pipeline for training, however, none have been executed.</span></span> <span data-ttu-id="7aaf2-186">Veri yükleme ve `Main` model eğitimini gerçekleştirmek için yönteme aşağıdaki satırı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7aaf2-186">Add the following line to the `Main` method to perform data loading and model training:</span></span>

[!code-csharp[Train the model](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#TrainModel)]

### <a name="save-the-model"></a><span data-ttu-id="7aaf2-187">Modeli kaydetme</span><span class="sxs-lookup"><span data-stu-id="7aaf2-187">Save the model</span></span>

<span data-ttu-id="7aaf2-188">Bu noktada, varolan veya yeni .NET uygulamalarınızdan herhangi biri ile entegre edilebilen bir modele sahip siniz.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-188">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="7aaf2-189">Modelinizi bir .zip dosyasına kaydetmek için `Main` yönteme aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7aaf2-189">To save your model to a .zip file, add the following code to the `Main` method:</span></span>

[!code-csharp[Save the model](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="7aaf2-190">Öngörüler için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="7aaf2-190">Use the model for predictions</span></span>

<span data-ttu-id="7aaf2-191">Öngörülerde bulunmak için, <xref:Microsoft.ML.PredictionEngine%602> transformatör ardışık lığından giriş türü örneklerini alan ve çıkış türünün örneklerini üreten sınıfı kullanın.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-191">To make predictions, use the <xref:Microsoft.ML.PredictionEngine%602> class that takes instances of the input type through the transformer pipeline and produces instances of the output type.</span></span> <span data-ttu-id="7aaf2-192">Bu sınıfın bir `Main` örneğini oluşturmak için yönteme aşağıdaki satırı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7aaf2-192">Add the following line to the `Main` method to create an instance of that class:</span></span>

[!code-csharp[Create predictor](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#Predictor)]

<span data-ttu-id="7aaf2-193">[PredictionEngine,](xref:Microsoft.ML.PredictionEngine%602) tek bir veri örneği üzerinde tahmin gerçekleştirmenize olanak tanıyan kolaylık api'sidir.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-193">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="7aaf2-194">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)iş parçacığı güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-194">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="7aaf2-195">Tek dişli veya prototip ortamlarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-195">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="7aaf2-196">Üretim ortamlarında daha iyi performans ve `PredictionEnginePool` iş parçacığı güvenliği [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) için, uygulamanız boyunca kullanılmak üzere bir nesne oluşturan hizmeti kullanın.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-196">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="7aaf2-197">ASP.NET Core Web [API'de `PredictionEnginePool` ](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)nasıl kullanılacağı yla ilgili bu kılavuza bakın.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-197">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

> [!NOTE]
> <span data-ttu-id="7aaf2-198">`PredictionEnginePool`hizmet uzantısı şu anda önizlemededir.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-198">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="7aaf2-199">Test `TestIrisData` veri örneklerini barındıracak sınıf oluşturun:</span><span class="sxs-lookup"><span data-stu-id="7aaf2-199">Create the `TestIrisData` class to house test data instances:</span></span>

1. <span data-ttu-id="7aaf2-200">**Çözüm Gezgini'nde,** projeyi sağ tıklatın ve ardından**Yeni Öğe** **Ekle'yi** > seçin.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-200">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="7aaf2-201">Yeni **Öğe Ekle** iletişim kutusunda **Sınıf'ı** seçin ve **Ad** alanını *TestIrisData.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-201">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestIrisData.cs*.</span></span> <span data-ttu-id="7aaf2-202">Ardından **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-202">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="7aaf2-203">Sınıfı aşağıdaki örnekte olduğu gibi statik olacak şekilde değiştirin:</span><span class="sxs-lookup"><span data-stu-id="7aaf2-203">Modify the class to be static like in the following example:</span></span>

   [!code-csharp[Make class static](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/TestIrisData.cs#Static)]

<span data-ttu-id="7aaf2-204">Bu öğretici, bu sınıf içinde bir iris veri örneği tanıtır.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-204">This tutorial introduces one iris data instance within this class.</span></span> <span data-ttu-id="7aaf2-205">Modelle deneme yapmak için başka senaryolar ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-205">You can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="7aaf2-206">Sınıfa `TestIrisData` aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7aaf2-206">Add the following code into the `TestIrisData` class:</span></span>

[!code-csharp[Test data](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/TestIrisData.cs#TestData)]

<span data-ttu-id="7aaf2-207">Belirtilen öğenin ait olduğu kümeyi bulmak için *Program.cs* dosyasına geri dön ve `Main` yönteme aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7aaf2-207">To find out the cluster to which the specified item belongs to, go back to the *Program.cs* file and add the following code into the `Main` method:</span></span>

[!code-csharp[Predict and output results](~/samples/snippets/machine-learning/IrisFlowerClustering/csharp/Program.cs#PredictionExample)]

<span data-ttu-id="7aaf2-208">Hangi kümenin belirtilen veri örneğini ve bu örnekten küme merkezlerine kare uzaklıklar içerdiğini görmek için programı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-208">Run the program to see which cluster contains the specified data instance and squared distances from that instance to the cluster centroids.</span></span> <span data-ttu-id="7aaf2-209">Sonuçlarınız aşağıdakilere benzer olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="7aaf2-209">Your results should be similar to the following:</span></span>

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

<span data-ttu-id="7aaf2-210">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="7aaf2-210">Congratulations!</span></span> <span data-ttu-id="7aaf2-211">Şimdi başarıyla iris kümeleme için bir makine öğrenme modeli inşa ettik ve tahminler yapmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-211">You've now successfully built a machine learning model for iris clustering and used it to make predictions.</span></span> <span data-ttu-id="7aaf2-212">Bu öğreticinin kaynak kodunu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-212">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="7aaf2-213">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="7aaf2-213">Next steps</span></span>

<span data-ttu-id="7aaf2-214">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="7aaf2-214">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="7aaf2-215">Sorunu anlama</span><span class="sxs-lookup"><span data-stu-id="7aaf2-215">Understand the problem</span></span>
> - <span data-ttu-id="7aaf2-216">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="7aaf2-216">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="7aaf2-217">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="7aaf2-217">Prepare the data</span></span>
> - <span data-ttu-id="7aaf2-218">Verileri yükleme ve dönüştürme</span><span class="sxs-lookup"><span data-stu-id="7aaf2-218">Load and transform the data</span></span>
> - <span data-ttu-id="7aaf2-219">Bir öğrenme algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="7aaf2-219">Choose a learning algorithm</span></span>
> - <span data-ttu-id="7aaf2-220">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="7aaf2-220">Train the model</span></span>
> - <span data-ttu-id="7aaf2-221">Öngörüler için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="7aaf2-221">Use the model for predictions</span></span>

<span data-ttu-id="7aaf2-222">Öğrenmeye devam etmek ve daha fazla örnek bulmak için GitHub depomuza göz atın.</span><span class="sxs-lookup"><span data-stu-id="7aaf2-222">Check out our GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="7aaf2-223">dotnet/machinelearning GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="7aaf2-223">dotnet/machinelearning GitHub repository</span></span>](https://github.com/dotnet/machinelearning/)
