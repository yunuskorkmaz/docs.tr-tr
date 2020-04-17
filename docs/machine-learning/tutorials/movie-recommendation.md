---
title: 'Öğretici: Bir film tavsiye oluştur - matris faktörizasyon'
description: Bu öğretici, .NET Core konsol uygulamasında ML.NET ile nasıl bir film tavsiye oluşturabileceğinizi gösterir. Adımlar c# ve Visual Studio 2019'u kullanır.
author: briacht
ms.date: 09/30/2019
ms.custom: mvc, title-hack-0516
ms.topic: tutorial
ms.openlocfilehash: a1d7ef6226580fd3172b5714f9d7358298ba6668
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81608003"
---
# <a name="tutorial-build-a-movie-recommender-using-matrix-factorization-with-mlnet"></a><span data-ttu-id="c7902-104">Öğretici: ML.NET ile matris çarpansama kullanarak bir film tavsiye oluştur</span><span class="sxs-lookup"><span data-stu-id="c7902-104">Tutorial: Build a movie recommender using matrix factorization with ML.NET</span></span>

<span data-ttu-id="c7902-105">Bu öğretici, .NET Core konsol uygulamasında ML.NET ile nasıl bir film tavsiye oluşturabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7902-105">This tutorial shows you how to build a movie recommender with ML.NET in a .NET Core console application.</span></span> <span data-ttu-id="c7902-106">Adımlar c# ve Visual Studio 2019'u kullanır.</span><span class="sxs-lookup"><span data-stu-id="c7902-106">The steps use C# and Visual Studio 2019.</span></span>

<span data-ttu-id="c7902-107">Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="c7902-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="c7902-108">Makine öğrenimi algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="c7902-108">Select a machine learning algorithm</span></span>
> * <span data-ttu-id="c7902-109">Verilerinizi hazırlama ve yükleme</span><span class="sxs-lookup"><span data-stu-id="c7902-109">Prepare and load your data</span></span>
> * <span data-ttu-id="c7902-110">Bir model oluşturma ve eğitme</span><span class="sxs-lookup"><span data-stu-id="c7902-110">Build and train a model</span></span>
> * <span data-ttu-id="c7902-111">Bir modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="c7902-111">Evaluate a model</span></span>
> * <span data-ttu-id="c7902-112">Bir modeli dağıtma ve tüket</span><span class="sxs-lookup"><span data-stu-id="c7902-112">Deploy and consume a model</span></span>

<span data-ttu-id="c7902-113">Bu öğreticinin kaynak kodunu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7902-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repository.</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="c7902-114">Makine öğrenimi iş akışı</span><span class="sxs-lookup"><span data-stu-id="c7902-114">Machine learning workflow</span></span>

<span data-ttu-id="c7902-115">Görevinizi gerçekleştirmek için aşağıdaki adımları ve diğer ML.NET görevleri kullanırsınız:</span><span class="sxs-lookup"><span data-stu-id="c7902-115">You will use the following steps to accomplish your task, as well as any other ML.NET task:</span></span>

1. [<span data-ttu-id="c7902-116">Verilerinizi yükleyin</span><span class="sxs-lookup"><span data-stu-id="c7902-116">Load your data</span></span>](#load-your-data)
2. [<span data-ttu-id="c7902-117">Modelinizi oluşturun ve eğitin</span><span class="sxs-lookup"><span data-stu-id="c7902-117">Build and train your model</span></span>](#build-and-train-your-model)
3. [<span data-ttu-id="c7902-118">Modelinizi değerlendirme</span><span class="sxs-lookup"><span data-stu-id="c7902-118">Evaluate your model</span></span>](#evaluate-your-model)
4. [<span data-ttu-id="c7902-119">Modelinizi kullanma</span><span class="sxs-lookup"><span data-stu-id="c7902-119">Use your model</span></span>](#use-your-model)

## <a name="prerequisites"></a><span data-ttu-id="c7902-120">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="c7902-120">Prerequisites</span></span>

* <span data-ttu-id="c7902-121">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya sonrası veya Visual Studio 2017 sürümü 15.6 veya daha sonra ".NET Core çapraz platform geliştirme" iş yükü yüklü.</span><span class="sxs-lookup"><span data-stu-id="c7902-121">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="c7902-122">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="c7902-122">Select the appropriate machine learning task</span></span>

<span data-ttu-id="c7902-123">Film listesini önermek veya ilgili ürünlerin bir listesini önermek gibi öneri sorunlarına yaklaşmanın çeşitli yolları vardır, ancak bu durumda bir kullanıcının belirli bir filme hangi derecelendirmeyi (1-5) vereceğini tahmin eder ve tanımlanmış bir eşiğe göre daha yüksekse bu filmi önerirsiniz (derecelendirme ne kadar yüksekse, kullanıcının belirli bir filmi sevme olasılığı da o kadar yüksekolur).</span><span class="sxs-lookup"><span data-stu-id="c7902-123">There are several ways to approach recommendation problems, such as recommending a list of movies or recommending a list of related products, but in this case you will predict what rating (1-5) a user will give to a particular movie and recommend that movie if it's higher than a defined threshold (the higher the rating, the higher the likelihood of a user liking a particular movie).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="c7902-124">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="c7902-124">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="c7902-125">Proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="c7902-125">Create a project</span></span>

1. <span data-ttu-id="c7902-126">Visual Studio 2017'yi açın.</span><span class="sxs-lookup"><span data-stu-id="c7902-126">Open Visual Studio 2017.</span></span> <span data-ttu-id="c7902-127">Menü çubuğundan**Yeni** > **Proje** **Dosyası'nı** > seçin.</span><span class="sxs-lookup"><span data-stu-id="c7902-127">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="c7902-128">Yeni **Proje** iletişim kutusunda, **.NET Core** düğümünü izleyen **Visual C#** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="c7902-128">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="c7902-129">Ardından **Konsol Uygulaması (.NET Core)** proje şablonu'nu seçin.</span><span class="sxs-lookup"><span data-stu-id="c7902-129">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="c7902-130">**Ad** metin kutusunda "MovieRecommender" yazın ve **ardından Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="c7902-130">In the **Name** text box, type "MovieRecommender" and then select the **OK** button.</span></span>

2. <span data-ttu-id="c7902-131">Veri kümesini depolamak için projenizde *Veri* adlı bir dizin oluşturun:</span><span class="sxs-lookup"><span data-stu-id="c7902-131">Create a directory named *Data* in your project to store the data set:</span></span>

    <span data-ttu-id="c7902-132">**Çözüm Gezgini'nde**projeyi sağ tıklatın ve**Yeni Klasör** **Ekle'yi** > seçin.</span><span class="sxs-lookup"><span data-stu-id="c7902-132">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="c7902-133">"Veri" yazın ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c7902-133">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="c7902-134">**Microsoft.ML** ve **Microsoft.ML.Recommender** NuGet Paketlerini yükleyin:</span><span class="sxs-lookup"><span data-stu-id="c7902-134">Install the **Microsoft.ML** and **Microsoft.ML.Recommender** NuGet Packages:</span></span>

    <span data-ttu-id="c7902-135">**Çözüm Gezgini'nde**projeyi sağ tıklatın ve **NuGet Paketlerini Yönet'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="c7902-135">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="c7902-136">Paket kaynağı olarak "nuget.org" seçeneğini belirleyin, **Gözat** sekmesini seçin, **Microsoft.ML**arayın, listedeki paketi seçin ve **Yükle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="c7902-136">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the package in the list, and select the **Install** button.</span></span> <span data-ttu-id="c7902-137">**Değişiklikler Önizleme** iletişim kutusundaki **Tamam** düğmesini seçin ve listelenen paketlerin lisans koşullarını kabul ederseniz Lisans Kabul iletişim kutusundaki **Kabul** **Et** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="c7902-137">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="c7902-138">**Microsoft.ML.Recommender**için bu adımları yineleyin.</span><span class="sxs-lookup"><span data-stu-id="c7902-138">Repeat these steps for **Microsoft.ML.Recommender**.</span></span>

4. <span data-ttu-id="c7902-139">`using` *Program.cs* dosyanızın üst kısmında aşağıdaki ifadeleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c7902-139">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[UsingStatements](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#UsingStatements "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="c7902-140">Verilerinizi indirin</span><span class="sxs-lookup"><span data-stu-id="c7902-140">Download your data</span></span>

1. <span data-ttu-id="c7902-141">İki veri kümesini indirin ve bunları daha önce oluşturduğunuz *Veri* klasörüne kaydedin:</span><span class="sxs-lookup"><span data-stu-id="c7902-141">Download the two datasets and save them to the *Data* folder you previously created:</span></span>

   * <span data-ttu-id="c7902-142">[*Tavsiye-ratings-train.csv'ye*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) sağ tıklayın ve "Bağlantıyı Kaydet (veya Hedef) Olarak..." seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="c7902-142">Right click on [*recommendation-ratings-train.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) and select "Save Link (or Target) As..."</span></span>
   * <span data-ttu-id="c7902-143">[*Öneri-derecelendirme-test.csv'ye*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) sağ tıklayın ve "Bağlantıyı Kaydet (veya Hedef) Olarak..." seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="c7902-143">Right click on [*recommendation-ratings-test.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="c7902-144">.csv dosyalarını \* *Veri* klasörüne kaydettiğinizi veya başka bir yere kaydettikten sonra \*.csv dosyalarını *Veri* klasörüne taşıdığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="c7902-144">Make sure you either save the \*.csv files to the *Data* folder, or after you save it elsewhere, move the \*.csv files to the *Data* folder.</span></span>

2. <span data-ttu-id="c7902-145">Çözüm Gezgini'nde \*,.csv dosyalarının her birini sağ tıklatın ve **Özellikler'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="c7902-145">In Solution Explorer, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="c7902-146">**Gelişmiş**altında, **daha yeniyse**Kopyala'dan **Çıktı Dizini'ne Kopya** değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c7902-146">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

   ![VS'de daha yeniyse kopya seçen bir kullanıcının GIF'i.](./media/movie-recommendation/copy-to-output-if-newer.gif)

## <a name="load-your-data"></a><span data-ttu-id="c7902-148">Verilerinizi yükleyin</span><span class="sxs-lookup"><span data-stu-id="c7902-148">Load your data</span></span>

<span data-ttu-id="c7902-149">ML.NET sürecinin ilk adımı, model eğitim ve test verilerinizi hazırlamak ve yüklemektir.</span><span class="sxs-lookup"><span data-stu-id="c7902-149">The first step in the ML.NET process is to prepare and load your model training and testing data.</span></span>

<span data-ttu-id="c7902-150">Öneri derecelendirme verileri `Train` bölünür `Test` ve veri kümelenir.</span><span class="sxs-lookup"><span data-stu-id="c7902-150">The recommendation ratings data is split into `Train` and `Test` datasets.</span></span> <span data-ttu-id="c7902-151">Veriler `Train` modelinize uymak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c7902-151">The `Train` data is used to fit your model.</span></span> <span data-ttu-id="c7902-152">Veriler, `Test` eğitimli modelinizle öngörülerde bulunmak ve model performansını değerlendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c7902-152">The `Test` data is used to make predictions with your trained model and evaluate model performance.</span></span> <span data-ttu-id="c7902-153">Bir 80/20 ile `Train` bölünmüş ve `Test` veri olması yaygındır.</span><span class="sxs-lookup"><span data-stu-id="c7902-153">It's common to have an 80/20 split with `Train` and `Test` data.</span></span>

<span data-ttu-id="c7902-154">Aşağıda .csv dosyalarınızdaki \*verilerin bir önizlemesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="c7902-154">Below is a preview of the data from your \*.csv files:</span></span>

![CVS veri kümesinin önizlemesinin ekran görüntüsü.](./media/movie-recommendation/csv-file-dataset-preview.png)

<span data-ttu-id="c7902-156">\*.csv dosyalarında dört sütun vardır:</span><span class="sxs-lookup"><span data-stu-id="c7902-156">In the \*.csv files, there are four columns:</span></span>

* `userId`
* `movieId`
* `rating`
* `timestamp`

<span data-ttu-id="c7902-157">Makine öğreniminde, tahmin yapmak için kullanılan sütunlara [Özellikler,](../resources/glossary.md#feature)döndürülen tahmin içeren sütuna [ise Etiket](../resources/glossary.md#label)denir.</span><span class="sxs-lookup"><span data-stu-id="c7902-157">In machine learning, the columns that are used to make a prediction are called [Features](../resources/glossary.md#feature), and the column with the returned prediction is called the [Label](../resources/glossary.md#label).</span></span>

<span data-ttu-id="c7902-158">Film derecelendirmelerini tahmin etmek istiyorsunuz, bu `Label`nedenle derecelendirme sütunu .</span><span class="sxs-lookup"><span data-stu-id="c7902-158">You want to predict movie ratings, so the rating column is the `Label`.</span></span> <span data-ttu-id="c7902-159">Diğer `userId`üç sütun, `movieId`, `timestamp` , `Features` ve tüm `Label`tahmin etmek için kullanılır .</span><span class="sxs-lookup"><span data-stu-id="c7902-159">The other three columns, `userId`, `movieId`, and `timestamp` are all `Features` used to predict the `Label`.</span></span>

| <span data-ttu-id="c7902-160">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c7902-160">Features</span></span>      | <span data-ttu-id="c7902-161">Etiketle</span><span class="sxs-lookup"><span data-stu-id="c7902-161">Label</span></span>         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |
| `timestamp`     |               |

<span data-ttu-id="c7902-162">Hangilerinin tahmin etmek için `Features` kullanılacağına karar `Label`vermek size kalmış.</span><span class="sxs-lookup"><span data-stu-id="c7902-162">It's up to you to decide which `Features` are used to predict the `Label`.</span></span> <span data-ttu-id="c7902-163">Ayrıca en iyi `Features`seçimi ile yardımcı olmak için [permütasyon özelliği önemi](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md) gibi yöntemler kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7902-163">You can also use methods like [permutation feature importance](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md) to help with selecting the best `Features`.</span></span>

<span data-ttu-id="c7902-164">Bu durumda, `timestamp` zaman damgası bir `Feature` kullanıcının belirli bir filmi nasıl oranlarını nitelemeyeceğini gerçekten etkilemediği ve böylece daha doğru bir tahminde bulunmaya katkıda bulunmayacağını zedeyi panlama olarak ortadan kaldırmalısınız:</span><span class="sxs-lookup"><span data-stu-id="c7902-164">In this case, you should eliminate the `timestamp` column as a `Feature` because the timestamp does not really affect how a user rates a given movie and thus would not contribute to making a more accurate prediction:</span></span>

| <span data-ttu-id="c7902-165">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c7902-165">Features</span></span>      | <span data-ttu-id="c7902-166">Etiketle</span><span class="sxs-lookup"><span data-stu-id="c7902-166">Label</span></span>         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |

<span data-ttu-id="c7902-167">Daha sonra giriş sınıfı için veri yapınızı tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7902-167">Next you must define your data structure for the input class.</span></span>

<span data-ttu-id="c7902-168">Projenize yeni bir sınıf ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c7902-168">Add a new class to your project:</span></span>

1. <span data-ttu-id="c7902-169">**Çözüm Gezgini'nde**projeyi sağ tıklatın ve ardından **Yeni Öğe > ekle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="c7902-169">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="c7902-170">Yeni **Öğe Ekle iletişim kutusunda,** **Sınıf'ı** seçin ve **Ad** alanını *MovieRatingData.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c7902-170">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *MovieRatingData.cs*.</span></span> <span data-ttu-id="c7902-171">Ardından **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="c7902-171">Then, select the **Add** button.</span></span>

<span data-ttu-id="c7902-172">kod düzenleyicisinde *MovieRatingData.cs* dosyası açılır.</span><span class="sxs-lookup"><span data-stu-id="c7902-172">The *MovieRatingData.cs* file opens in the code editor.</span></span> <span data-ttu-id="c7902-173">MovieRatingData.cs üstüne `using` aşağıdaki ifadeyi *MovieRatingData.cs*ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c7902-173">Add the following `using` statement to the top of *MovieRatingData.cs*:</span></span>

```csharp
using Microsoft.ML.Data;
```

<span data-ttu-id="c7902-174">Varolan sınıf `MovieRating` tanımını kaldırarak ve *MovieRatingData.cs*aşağıdaki kodu ekleyerek çağrılan bir sınıf oluşturun:</span><span class="sxs-lookup"><span data-stu-id="c7902-174">Create a class called `MovieRating` by removing the existing class definition and adding the following code in *MovieRatingData.cs*:</span></span>

[!code-csharp[MovieRatingClass](~/samples/snippets/machine-learning/MovieRecommendation/csharp/MovieRatingData.cs#MovieRatingClass "Add the Movie Rating class")]

<span data-ttu-id="c7902-175">`MovieRating`bir giriş veri sınıfı belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7902-175">`MovieRating` specifies an input data class.</span></span> <span data-ttu-id="c7902-176">[LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) özniteliği, veri kümesindeki hangi sütunların (sütun dizinine göre) yüklenmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7902-176">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span> <span data-ttu-id="c7902-177">Ve `userId` `movieId` sütunlar `Features` sizin (modeli tahmin etmek için vereceğiniz `Label`girdiler) ve `Label` derecelendirme sütunu tahmin edeceğiniz (modelin çıktısI).</span><span class="sxs-lookup"><span data-stu-id="c7902-177">The `userId` and `movieId` columns are your `Features` (the inputs you will give the model to predict the `Label`), and the rating column is the `Label` that you will predict (the output of the model).</span></span>

<span data-ttu-id="c7902-178">`MovieRatingPrediction` `MovieRating` *MovieRatingData.cs'da*sınıftan sonra aşağıdaki kodu ekleyerek tahmin edilen sonuçları temsil edecek başka bir sınıf oluşturun:</span><span class="sxs-lookup"><span data-stu-id="c7902-178">Create another class, `MovieRatingPrediction`, to represent predicted results by adding the following code after the `MovieRating` class in *MovieRatingData.cs*:</span></span>

[!code-csharp[PredictionClass](~/samples/snippets/machine-learning/MovieRecommendation/csharp/MovieRatingData.cs#PredictionClass "Add the Movie Prediction Class")]

<span data-ttu-id="c7902-179">Program.cs *Program.cs*olarak, `Console.WriteLine("Hello World!")` içinde `Main()`aşağıdaki kodu ile değiştirin:</span><span class="sxs-lookup"><span data-stu-id="c7902-179">In *Program.cs*, replace the `Console.WriteLine("Hello World!")` with the following code inside `Main()`:</span></span>

[!code-csharp[MLContext](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#MLContext "Add MLContext")]

<span data-ttu-id="c7902-180">[MLContext sınıfı](xref:Microsoft.ML.MLContext) tüm ML.NET işlemleri için bir başlangıç `mlContext` noktasıdır ve başlatma, model oluşturma iş akışı nesneleri arasında paylaşılabilen yeni bir ML.NET ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c7902-180">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="c7902-181">Kavramsal olarak Varlık Çerçevesi'ne `DBContext` benzer.</span><span class="sxs-lookup"><span data-stu-id="c7902-181">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="c7902-182">Sonra `Main()`, adlı `LoadData()`bir yöntem oluşturmak:</span><span class="sxs-lookup"><span data-stu-id="c7902-182">After `Main()`, create a method called `LoadData()`:</span></span>

```csharp
public static (IDataView training, IDataView test) LoadData(MLContext mlContext)
{

}
```

> [!NOTE]
> <span data-ttu-id="c7902-183">Bu yöntem, aşağıdaki adımlarda bir iade deyimi ekleyene kadar size bir hata verecektir.</span><span class="sxs-lookup"><span data-stu-id="c7902-183">This method will give you an error until you add a return statement in the following steps.</span></span>

<span data-ttu-id="c7902-184">Veri yolu değişkenlerinizi \*başlatma, .csv dosyalarından gelen verileri `Train` yükleme `Test` ve `IDataView` aşağıdaki kodun bir sonraki satırı olarak `LoadData()`aşağıdakileri ekleyerek ve verileri nesne olarak döndürün:</span><span class="sxs-lookup"><span data-stu-id="c7902-184">Initialize your data path variables, load the data from the \*.csv files, and return the `Train` and `Test` data as `IDataView` objects by adding the following as the next line of code in `LoadData()`:</span></span>

[!code-csharp[LoadData](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#LoadData "Load data from data paths")]

<span data-ttu-id="c7902-185">ML.NET'daki veriler [IDataView sınıfı](xref:Microsoft.ML.IDataView)olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="c7902-185">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="c7902-186">`IDataView`tabular verileri (sayısal ve metin) tanımlamanın esnek ve etkili bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="c7902-186">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="c7902-187">Veriler bir metin dosyasından veya gerçek zamanlı olarak (örneğin, SQL veritabanı `IDataView` veya günlük dosyaları) bir nesneye yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="c7902-187">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="c7902-188">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) veri şemasını tanımlar ve dosyada okur.</span><span class="sxs-lookup"><span data-stu-id="c7902-188">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="c7902-189">Veri yolu değişkenlerini alır ve `IDataView`bir .</span><span class="sxs-lookup"><span data-stu-id="c7902-189">It takes in the data path variables and returns an `IDataView`.</span></span> <span data-ttu-id="c7902-190">Bu durumda, sizin ve `Test` `Train` dosyalarınız için yolu sağlar sınız ve hem metin dosyası üstbilgisini (sütun adlarını düzgün kullanabilsin diye) hem de virgül karakter veri ayırıcısını (varsayılan ayırıcı bir sekmedir) gösterirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7902-190">In this case, you provide the path for your `Test` and `Train` files and indicate both the text file header (so it can use the column names properly) and the comma character data separator (the default separator is a tab).</span></span>

<span data-ttu-id="c7902-191">Yönteminizi `Main()` `LoadData()` çağırmak ve `Train` verileri `Test` döndürmek için yönteme aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c7902-191">Add the following code in the `Main()` method to call your `LoadData()` method and return the `Train` and `Test` data:</span></span>

[!code-csharp[LoadDataMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#LoadDataMain "Add LoadData method to Main")]

## <a name="build-and-train-your-model"></a><span data-ttu-id="c7902-192">Modelinizi oluşturun ve eğitin</span><span class="sxs-lookup"><span data-stu-id="c7902-192">Build and train your model</span></span>

<span data-ttu-id="c7902-193">ML.NET üç ana kavram vardır: [Veri](../resources/glossary.md#data), [Transformatörler](../resources/glossary.md#transformer), ve [Tahminciler](../resources/glossary.md#estimator).</span><span class="sxs-lookup"><span data-stu-id="c7902-193">There are three major concepts in ML.NET: [Data](../resources/glossary.md#data), [Transformers](../resources/glossary.md#transformer), and [Estimators](../resources/glossary.md#estimator).</span></span>

<span data-ttu-id="c7902-194">Makine öğrenimi eğitim algoritmaları belirli bir biçimde veri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c7902-194">Machine learning training algorithms require data in a certain format.</span></span> <span data-ttu-id="c7902-195">`Transformers`tabular verileri uyumlu bir biçime dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c7902-195">`Transformers` are used to transform tabular data to a compatible format.</span></span>

![Transformatör veri akışının diyagramı.](./media/movie-recommendation/data-transformer-transformed.png)

<span data-ttu-id="c7902-197">ML.NET'da `Transformers` oluşturarak `Estimators`oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="c7902-197">You create `Transformers` in ML.NET by creating `Estimators`.</span></span> <span data-ttu-id="c7902-198">`Estimators`veri almak ve `Transformers`geri.</span><span class="sxs-lookup"><span data-stu-id="c7902-198">`Estimators` take in data and return `Transformers`.</span></span>

![Tahminci veri akışının diyagramı.](./media/movie-recommendation/data-estimator-transformer.png)

<span data-ttu-id="c7902-200">Modelinizi eğitmek için kullanacağınız öneri eğitim algoritması `Estimator`bir .</span><span class="sxs-lookup"><span data-stu-id="c7902-200">The recommendation training algorithm you will use for training your model is an example of an `Estimator`.</span></span>

<span data-ttu-id="c7902-201">Aşağıdaki `Estimator` adımları içeren bir yapı oluşturun:</span><span class="sxs-lookup"><span data-stu-id="c7902-201">Build an `Estimator` with the following steps:</span></span>

<span data-ttu-id="c7902-202">Yöntemden `BuildAndTrainModel()` `LoadData()` hemen sonra, aşağıdaki kodu kullanarak yöntemi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="c7902-202">Create the `BuildAndTrainModel()` method, just after the `LoadData()` method, using the following code:</span></span>

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView trainingDataView)
{

}
```

> [!NOTE]
> <span data-ttu-id="c7902-203">Bu yöntem, aşağıdaki adımlarda bir iade deyimi ekleyene kadar size bir hata verecektir.</span><span class="sxs-lookup"><span data-stu-id="c7902-203">This method will give you an error until you add a return statement in the following steps.</span></span>

<span data-ttu-id="c7902-204">Aşağıdaki kodu ekleyerek veri dönüşümlerini `BuildAndTrainModel()`tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="c7902-204">Define the data transformations by adding the following code to `BuildAndTrainModel()`:</span></span>

[!code-csharp[DataTransformations](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#DataTransformations "Define data transformations")]

<span data-ttu-id="c7902-205">Kullanıcıları `userId` `movieId` ve film başlıklarını gerçek değerler değil, temsil ettiği için, her `movieId` `userId` birini sayısal anahtar türü `Feature` sütununa (öneri algoritmaları tarafından kabul edilen bir biçim) dönüştürmek ve bunları yeni veri kümesi sütunları olarak eklemek için [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) yöntemini kullanırsınız:</span><span class="sxs-lookup"><span data-stu-id="c7902-205">Since `userId` and `movieId` represent users and movie titles, not real values, you use the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method to transform each `userId` and each `movieId` into a numeric key type `Feature` column (a format accepted by recommendation algorithms) and add them as new dataset columns:</span></span>

| <span data-ttu-id="c7902-206">userId</span><span class="sxs-lookup"><span data-stu-id="c7902-206">userId</span></span> | <span data-ttu-id="c7902-207">movieId</span><span class="sxs-lookup"><span data-stu-id="c7902-207">movieId</span></span> | <span data-ttu-id="c7902-208">Etiketle</span><span class="sxs-lookup"><span data-stu-id="c7902-208">Label</span></span> | <span data-ttu-id="c7902-209">userIdEncoded</span><span class="sxs-lookup"><span data-stu-id="c7902-209">userIdEncoded</span></span> | <span data-ttu-id="c7902-210">movieIdEncoded</span><span class="sxs-lookup"><span data-stu-id="c7902-210">movieIdEncoded</span></span> |
| ------------- |:-------------:| -----:|-----:|-----:|
| <span data-ttu-id="c7902-211">1</span><span class="sxs-lookup"><span data-stu-id="c7902-211">1</span></span> | <span data-ttu-id="c7902-212">1</span><span class="sxs-lookup"><span data-stu-id="c7902-212">1</span></span> | <span data-ttu-id="c7902-213">4</span><span class="sxs-lookup"><span data-stu-id="c7902-213">4</span></span> | <span data-ttu-id="c7902-214">userKey1</span><span class="sxs-lookup"><span data-stu-id="c7902-214">userKey1</span></span> | <span data-ttu-id="c7902-215">movieKey1</span><span class="sxs-lookup"><span data-stu-id="c7902-215">movieKey1</span></span> |
| <span data-ttu-id="c7902-216">1</span><span class="sxs-lookup"><span data-stu-id="c7902-216">1</span></span> | <span data-ttu-id="c7902-217">3</span><span class="sxs-lookup"><span data-stu-id="c7902-217">3</span></span> | <span data-ttu-id="c7902-218">4</span><span class="sxs-lookup"><span data-stu-id="c7902-218">4</span></span> | <span data-ttu-id="c7902-219">userKey1</span><span class="sxs-lookup"><span data-stu-id="c7902-219">userKey1</span></span> | <span data-ttu-id="c7902-220">movieKey2</span><span class="sxs-lookup"><span data-stu-id="c7902-220">movieKey2</span></span> |
| <span data-ttu-id="c7902-221">1</span><span class="sxs-lookup"><span data-stu-id="c7902-221">1</span></span> | <span data-ttu-id="c7902-222">6</span><span class="sxs-lookup"><span data-stu-id="c7902-222">6</span></span> | <span data-ttu-id="c7902-223">4</span><span class="sxs-lookup"><span data-stu-id="c7902-223">4</span></span> | <span data-ttu-id="c7902-224">userKey1</span><span class="sxs-lookup"><span data-stu-id="c7902-224">userKey1</span></span> | <span data-ttu-id="c7902-225">movieKey3</span><span class="sxs-lookup"><span data-stu-id="c7902-225">movieKey3</span></span> |

<span data-ttu-id="c7902-226">Makine öğrenme algoritmasını seçin ve aşağıdaki kodu aşağıdaki satır olarak ekleyerek veri dönüştürme `BuildAndTrainModel()`tanımlarına eklemek:</span><span class="sxs-lookup"><span data-stu-id="c7902-226">Choose the machine learning algorithm and append it to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[AddAlgorithm](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#AddAlgorithm "Add the training algorithm with options")]

<span data-ttu-id="c7902-227">[MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) tavsiye eğitim algoritmasıdır.</span><span class="sxs-lookup"><span data-stu-id="c7902-227">The [MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) is your recommendation training algorithm.</span></span>  <span data-ttu-id="c7902-228">[Matris Çarpanları,](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) kullanıcıların geçmişte ürünleri nasıl derecelendirdiği hakkında veri ye sahip olduğunuzda, bu öğreticideki veri kümeleri için de geçerli olan yaygın bir öneri yaklaşımıdır.</span><span class="sxs-lookup"><span data-stu-id="c7902-228">[Matrix Factorization](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) is a common approach to recommendation when you have data on how users have rated products in the past, which is the case for the datasets in this tutorial.</span></span> <span data-ttu-id="c7902-229">Farklı verileriniz olduğunda başka öneri algoritmaları da vardır (daha fazla bilgi edinmek için aşağıdaki [Diğer öneri algoritmaları](#other-recommendation-algorithms) bölümüne bakın).</span><span class="sxs-lookup"><span data-stu-id="c7902-229">There are other recommendation algorithms for when you have different data available (see the [Other recommendation algorithms](#other-recommendation-algorithms) section below to learn more).</span></span>

<span data-ttu-id="c7902-230">Bu durumda, `Matrix Factorization` algoritma "işbirlikçi filtreleme" adı verilen bir yöntem kullanır ve kullanıcı 1'in belirli bir konuda Kullanıcı 2 ile aynı görüşe sahip olması durumunda, Kullanıcı 1'in farklı bir sorun hakkında Kullanıcı 2 ile aynı şekilde hissetme olasılığının daha yüksek olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="c7902-230">In this case, the `Matrix Factorization` algorithm uses a method called "collaborative filtering", which assumes that if User 1 has the same opinion as User 2 on a certain issue, then User 1 is more likely to feel the same way as User 2 about a different issue.</span></span>

<span data-ttu-id="c7902-231">Örneğin, Kullanıcı 1 ve Kullanıcı 2 oranı benzer şekilde film varsa, Kullanıcı 2 kullanıcı 1'in izlediği ve yüksek puan verdiği bir filmden daha çok keyif alma olasılığı daha yüksektir:</span><span class="sxs-lookup"><span data-stu-id="c7902-231">For instance, if User 1 and User 2 rate movies similarly, then User 2 is more likely to enjoy a movie that User 1 has watched and rated highly:</span></span>

| | `Incredibles 2 (2018)` | `The Avengers (2012)` | `Guardians of the Galaxy (2014)` |
| -------------:|-------------:| -----:|-----:|
| <span data-ttu-id="c7902-232">Kullanıcı 1</span><span class="sxs-lookup"><span data-stu-id="c7902-232">User 1</span></span> | <span data-ttu-id="c7902-233">İzlenen ve beğenilen film</span><span class="sxs-lookup"><span data-stu-id="c7902-233">Watched and liked movie</span></span> | <span data-ttu-id="c7902-234">İzlenen ve beğenilen film</span><span class="sxs-lookup"><span data-stu-id="c7902-234">Watched and liked movie</span></span> | <span data-ttu-id="c7902-235">İzlenen ve beğenilen film</span><span class="sxs-lookup"><span data-stu-id="c7902-235">Watched and liked movie</span></span> |
| <span data-ttu-id="c7902-236">Kullanıcı 2</span><span class="sxs-lookup"><span data-stu-id="c7902-236">User 2</span></span> | <span data-ttu-id="c7902-237">İzlenen ve beğenilen film</span><span class="sxs-lookup"><span data-stu-id="c7902-237">Watched and liked movie</span></span> | <span data-ttu-id="c7902-238">İzlenen ve beğenilen film</span><span class="sxs-lookup"><span data-stu-id="c7902-238">Watched and liked movie</span></span> | <span data-ttu-id="c7902-239">İzlemedi -- FİlM ÖNER</span><span class="sxs-lookup"><span data-stu-id="c7902-239">Has not watched -- RECOMMEND movie</span></span> |

<span data-ttu-id="c7902-240">Eğitmen, `Matrix Factorization` aşağıdaki [Algoritma hiperparametreleri](#algorithm-hyperparameters) bölümünde hakkında daha fazla bilgi edinebileceğiniz birkaç [seçenek](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options)vardır.</span><span class="sxs-lookup"><span data-stu-id="c7902-240">The `Matrix Factorization` trainer has several [Options](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), which you can read more about in the [Algorithm hyperparameters](#algorithm-hyperparameters) section below.</span></span>

<span data-ttu-id="c7902-241">Modeli `Train` verilere sığdırın ve yöntemde bir sonraki kod satırı olarak `BuildAndTrainModel()` aşağıdakileri ekleyerek eğitilmiş modeli döndürün:</span><span class="sxs-lookup"><span data-stu-id="c7902-241">Fit the model to the `Train` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[FitModel](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#FitModel "Call the Fit method and return back the trained model")]

<span data-ttu-id="c7902-242">[Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) yöntemi, modelinizi sağlanan eğitim veri kümesiyle eğitir.</span><span class="sxs-lookup"><span data-stu-id="c7902-242">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model with the provided training dataset.</span></span> <span data-ttu-id="c7902-243">Teknik olarak, verileri `Estimator` dönüştürerek ve eğitimi uygulayarak tanımları yürütür ve eğitilen `Transformer`modeli geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="c7902-243">Technically, it executes the `Estimator` definitions by transforming the data and applying the training, and it returns back the trained model, which is a `Transformer`.</span></span>

<span data-ttu-id="c7902-244">`Main()` Yöntemde bir sonraki kod satırı olarak aşağıdakileri `BuildAndTrainModel()` ekleyin ve yönteminizi çağırın ve eğitilmiş modeli döndürün:</span><span class="sxs-lookup"><span data-stu-id="c7902-244">Add the following as the next line of code in the `Main()` method to call your `BuildAndTrainModel()` method and return the trained model:</span></span>

[!code-csharp[BuildTrainModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#BuildTrainModelMain "Add BuildAndTrainModel method in Main")]

## <a name="evaluate-your-model"></a><span data-ttu-id="c7902-245">Modelinizi değerlendirme</span><span class="sxs-lookup"><span data-stu-id="c7902-245">Evaluate your model</span></span>

<span data-ttu-id="c7902-246">Modelinizi eğittikten sonra, modelinizin nasıl performans gösterdiğini değerlendirmek için test verilerinizi kullanın.</span><span class="sxs-lookup"><span data-stu-id="c7902-246">Once you have trained your model, use your test data to evaluate how your model is performing.</span></span>

<span data-ttu-id="c7902-247">Yöntemden `EvaluateModel()` `BuildAndTrainModel()` hemen sonra, aşağıdaki kodu kullanarak yöntemi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="c7902-247">Create the `EvaluateModel()` method, just after the `BuildAndTrainModel()` method, using the following code:</span></span>

```csharp
public static void EvaluateModel(MLContext mlContext, IDataView testDataView, ITransformer model)
{

}
```

<span data-ttu-id="c7902-248">Aşağıdaki `Test` kodu ekleyerek verileri dönüştürün: `EvaluateModel()`</span><span class="sxs-lookup"><span data-stu-id="c7902-248">Transform the `Test` data by adding the following code to `EvaluateModel()`:</span></span>

[!code-csharp[Transform](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#Transform "Transform the test data")]

<span data-ttu-id="c7902-249">[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemi, bir test veri kümesinin birden çok sağlanan giriş satırı için öngörüler yapar.</span><span class="sxs-lookup"><span data-stu-id="c7902-249">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for multiple provided input rows of a test dataset.</span></span>

<span data-ttu-id="c7902-250">Yöntemde bir sonraki kod satırı olarak aşağıdakileri `EvaluateModel()` ekleyerek modeli değerlendirin:</span><span class="sxs-lookup"><span data-stu-id="c7902-250">Evaluate the model by adding the following as the next line of code in the `EvaluateModel()` method:</span></span>

[!code-csharp[Evaluate](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#Evaluate "Evaluate the model using predictions from the test data")]

<span data-ttu-id="c7902-251">Tahmin kümesini aldıktan sonra, Tahmin edilen değerleri test veri kümesindeki gerçek `Labels` değerlerle karşılaştıran ve modelin nasıl performans gösterdiğine ilişkin ölçümleri döndüren modeli [değerlendirin.](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A)</span><span class="sxs-lookup"><span data-stu-id="c7902-251">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns metrics on how the model is performing.</span></span>

<span data-ttu-id="c7902-252">Yöntemde bir sonraki kod satırı olarak aşağıdakileri ekleyerek değerlendirme `EvaluateModel()` ölçümlerinizi konsola yazdırın:</span><span class="sxs-lookup"><span data-stu-id="c7902-252">Print your evaluation metrics to the console by adding the following as the next line of code in the `EvaluateModel()` method:</span></span>

[!code-csharp[PrintMetrics](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#PrintMetrics "Print the evaluation metrics")]

<span data-ttu-id="c7902-253">Yöntemde bir sonraki kod `Main()` satırı olarak aşağıdakileri `EvaluateModel()` ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c7902-253">Add the following as the next line of code in the `Main()` method to call your `EvaluateModel()` method:</span></span>

[!code-csharp[EvaluateModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#EvaluateModelMain "Add EvaluateModel method in Main")]

<span data-ttu-id="c7902-254">Çıktı şimdiye kadar aşağıdaki metne benzer görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="c7902-254">The output so far should look similar to the following text:</span></span>

```console
=============== Training the model ===============
iter      tr_rmse          obj
   0       1.5403   3.1262e+05
   1       0.9221   1.6030e+05
   2       0.8687   1.5046e+05
   3       0.8416   1.4584e+05
   4       0.8142   1.4209e+05
   5       0.7849   1.3907e+05
   6       0.7544   1.3594e+05
   7       0.7266   1.3361e+05
   8       0.6987   1.3110e+05
   9       0.6751   1.2948e+05
  10       0.6530   1.2766e+05
  11       0.6350   1.2644e+05
  12       0.6197   1.2541e+05
  13       0.6067   1.2470e+05
  14       0.5953   1.2382e+05
  15       0.5871   1.2342e+05
  16       0.5781   1.2279e+05
  17       0.5713   1.2240e+05
  18       0.5660   1.2230e+05
  19       0.5592   1.2179e+05
=============== Evaluating the model ===============
Rms: 0.994051469730769
RSquared: 0.412556298844873
```

<span data-ttu-id="c7902-255">Bu çıktıda, 20 yineleme vardır.</span><span class="sxs-lookup"><span data-stu-id="c7902-255">In this output, there are 20 iterations.</span></span> <span data-ttu-id="c7902-256">Her yinelemede hata ölçüsü azalır ve 0'a yaklaştıkça yakınlaşır.</span><span class="sxs-lookup"><span data-stu-id="c7902-256">In each iteration, the measure of error decreases and converges closer and closer to 0.</span></span>

<span data-ttu-id="c7902-257">`root of mean squared error` (RMS veya RMSE) model öngörülen değerler ve test veri kümesi gözlenen değerler arasındaki farkları ölçmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c7902-257">The `root of mean squared error` (RMS or RMSE) is used to measure the differences between the model predicted values and the test dataset observed values.</span></span> <span data-ttu-id="c7902-258">Teknik olarak hataların kareortalamasının kare kökü.</span><span class="sxs-lookup"><span data-stu-id="c7902-258">Technically it's the square root of the average of the squares of the errors.</span></span> <span data-ttu-id="c7902-259">Ne kadar düşükse, model o kadar iyi olur.</span><span class="sxs-lookup"><span data-stu-id="c7902-259">The lower it is, the better the model is.</span></span>

<span data-ttu-id="c7902-260">`R Squared`verilerin bir modele ne kadar iyi uyduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7902-260">`R Squared` indicates how well data fits a model.</span></span> <span data-ttu-id="c7902-261">0 ile 1 arasında değişir.</span><span class="sxs-lookup"><span data-stu-id="c7902-261">Ranges from 0 to 1.</span></span> <span data-ttu-id="c7902-262">0 değeri, verilerin rastgele olduğu veya modele başka bir şekilde sığamayacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c7902-262">A value of 0 means that the data is random or otherwise can't be fit to the model.</span></span> <span data-ttu-id="c7902-263">1 değeri, modelin verilerle tam olarak eşleştiğini anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c7902-263">A value of 1 means that the model exactly matches the data.</span></span> <span data-ttu-id="c7902-264">Puanınızın `R Squared` mümkün olduğunca 1'e yakın olmasını istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="c7902-264">You want your `R Squared` score to be as close to 1 as possible.</span></span>

<span data-ttu-id="c7902-265">Başarılı modeller oluşturmak yinelemeli bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="c7902-265">Building successful models is an iterative process.</span></span> <span data-ttu-id="c7902-266">Öğretici hızlı model eğitimi sağlamak için küçük veri kümeleri kullandığından, bu model in ilk düşük kaliteye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c7902-266">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="c7902-267">Model kalitesinden memnun değilseniz, daha büyük eğitim veri kümeleri sağlayarak veya her algoritma için farklı hiper parametrelere sahip farklı eğitim algoritmaları seçerek bunu geliştirmeyi deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7902-267">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different hyper-parameters for each algorithm.</span></span> <span data-ttu-id="c7902-268">Daha fazla bilgi için aşağıdaki [modeli geliştir bölümüne](#improve-your-model) göz atın.</span><span class="sxs-lookup"><span data-stu-id="c7902-268">For more information, check out the [Improve your model](#improve-your-model) section below.</span></span>

## <a name="use-your-model"></a><span data-ttu-id="c7902-269">Modelinizi kullanma</span><span class="sxs-lookup"><span data-stu-id="c7902-269">Use your model</span></span>

<span data-ttu-id="c7902-270">Artık yeni veriler üzerinde öngörülerde bulunmak için eğitilmiş modelinizi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7902-270">Now you can use your trained model to make predictions on new data.</span></span>

<span data-ttu-id="c7902-271">Yöntemden `UseModelForSinglePrediction()` `EvaluateModel()` hemen sonra, aşağıdaki kodu kullanarak yöntemi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="c7902-271">Create the `UseModelForSinglePrediction()` method, just after the `EvaluateModel()` method, using the following code:</span></span>

```csharp
public static void UseModelForSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="c7902-272">Aşağıdaki `PredictionEngine` kodu ekleyerek derecelendirme tahmin etmek `UseModelForSinglePrediction()`için kullanın:</span><span class="sxs-lookup"><span data-stu-id="c7902-272">Use the `PredictionEngine` to predict the rating by adding the following code to `UseModelForSinglePrediction()`:</span></span>

[!code-csharp[PredictionEngine](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#PredictionEngine "Create Prediction Engine")]

<span data-ttu-id="c7902-273">[PredictionEngine,](xref:Microsoft.ML.PredictionEngine%602) tek bir veri örneği üzerinde tahmin gerçekleştirmenize olanak tanıyan kolaylık api'sidir.</span><span class="sxs-lookup"><span data-stu-id="c7902-273">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="c7902-274">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)iş parçacığı güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="c7902-274">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="c7902-275">Tek dişli veya prototip ortamlarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c7902-275">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="c7902-276">Üretim ortamlarında daha iyi performans ve `PredictionEnginePool` iş parçacığı güvenliği [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) için, uygulamanız boyunca kullanılmak üzere bir nesne oluşturan hizmeti kullanın.</span><span class="sxs-lookup"><span data-stu-id="c7902-276">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="c7902-277">ASP.NET Core Web [API'de `PredictionEnginePool` ](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)nasıl kullanılacağı yla ilgili bu kılavuza bakın.</span><span class="sxs-lookup"><span data-stu-id="c7902-277">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

> [!NOTE]
> <span data-ttu-id="c7902-278">`PredictionEnginePool`hizmet uzantısı şu anda önizlemededir.</span><span class="sxs-lookup"><span data-stu-id="c7902-278">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="c7902-279">`MovieRating` Çağrıda bulunan `testInput` bir örnek oluşturun ve yöntemde bir sonraki kod satırları olarak aşağıdakileri ekleyerek Tahmin Motoru'na geçirin: `UseModelForSinglePrediction()`</span><span class="sxs-lookup"><span data-stu-id="c7902-279">Create an instance of `MovieRating` called `testInput` and pass it to the Prediction Engine by adding the following as the next lines of code in the `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[MakeSinglePrediction](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#MakeSinglePrediction "Make a single prediction with the Prediction Engine")]

<span data-ttu-id="c7902-280">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi, tek bir veri sütununda bir tahminde bulunur.</span><span class="sxs-lookup"><span data-stu-id="c7902-280">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single column of data.</span></span>

<span data-ttu-id="c7902-281">Daha sonra movieId 10'dan kullanıcı6'ya film önermek isteyip istemediğinizi belirlemek için `Score`, veya öngörülen derecelendirmeyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7902-281">You can then use the `Score`, or the predicted rating, to determine whether you want to recommend the movie with movieId 10 to user 6.</span></span> <span data-ttu-id="c7902-282">Ne kadar `Score`yüksekse, kullanıcının belirli bir filmi sevme olasılığı da o kadar yüksek.</span><span class="sxs-lookup"><span data-stu-id="c7902-282">The higher the `Score`, the higher the likelihood of a user liking a particular movie.</span></span> <span data-ttu-id="c7902-283">Bu durumda, 3,5 > öngörülen bir dereceye sahip filmleri önerdiğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="c7902-283">In this case, let’s say that you recommend movies with a predicted rating of > 3.5.</span></span>

<span data-ttu-id="c7902-284">Sonuçları yazdırmak için yöntemde `UseModelForSinglePrediction()` sonraki kod satırları olarak aşağıdakileri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c7902-284">To print the results, add the following as the next lines of code in the `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[PrintResults](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#PrintResults "Print the recommendation prediction results")]

<span data-ttu-id="c7902-285">Yöntemde bir sonraki kod `Main()` satırı olarak aşağıdakileri `UseModelForSinglePrediction()` ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c7902-285">Add the following as the next line of code in the `Main()` method to call your `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[UseModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#UseModelMain "Add UseModelForSinglePrediction method in Main")]

<span data-ttu-id="c7902-286">Bu yöntemin çıktısı aşağıdaki metne benzer olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="c7902-286">The output of this method should look similar to the following text:</span></span>

```console
=============== Making a prediction ===============
Movie 10 is recommended for user 6
```

### <a name="save-your-model"></a><span data-ttu-id="c7902-287">Modelinizi kaydedin</span><span class="sxs-lookup"><span data-stu-id="c7902-287">Save your model</span></span>

<span data-ttu-id="c7902-288">Son kullanıcı uygulamalarında öngörülerde bulunmak için modelinizi kullanmak için önce modeli kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7902-288">To use your model to make predictions in end-user applications, you must first save the model.</span></span>

<span data-ttu-id="c7902-289">Yöntemden `SaveModel()` `UseModelForSinglePrediction()` hemen sonra, aşağıdaki kodu kullanarak yöntemi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="c7902-289">Create the `SaveModel()` method, just after the `UseModelForSinglePrediction()` method, using the following code:</span></span>

```csharp
public static void SaveModel(MLContext mlContext, DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

<span data-ttu-id="c7902-290">Yönteme aşağıdaki kodu ekleyerek eğitimli `SaveModel()` modelinizi kaydedin:</span><span class="sxs-lookup"><span data-stu-id="c7902-290">Save your trained model by adding the following code in the `SaveModel()` method:</span></span>

[!code-csharp[SaveModel](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#SaveModel "Save the model to a zip file")]

<span data-ttu-id="c7902-291">Bu yöntem, eğitimli modelinizi bir .zip dosyasına ("Veri" klasöründe) kaydeder ve bu dosya daha sonra diğer .NET uygulamalarında öngörülerde bulunmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c7902-291">This method saves your trained model to a .zip file (in the "Data" folder), which can then be used in other .NET applications to make predictions.</span></span>

<span data-ttu-id="c7902-292">Yöntemde bir sonraki kod `Main()` satırı olarak aşağıdakileri `SaveModel()` ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c7902-292">Add the following as the next line of code in the `Main()` method to call your `SaveModel()` method:</span></span>

[!code-csharp[SaveModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#SaveModelMain "Create SaveModel method in Main")]

### <a name="use-your-saved-model"></a><span data-ttu-id="c7902-293">Kaydettiğiniz modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="c7902-293">Use your saved model</span></span>

<span data-ttu-id="c7902-294">Eğitimli modelinizi kurtardıktan sonra, modeli farklı ortamlarda tüketebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7902-294">Once you have saved your trained model, you can consume the model in different environments.</span></span> <span data-ttu-id="c7902-295">Uygulamalarda eğitimli bir makine öğrenimi modelini nasıl işlevsel hale erdireceklerini öğrenmek için [eğitilmiş modelleri kaydet ve yükleyin.](../how-to-guides/save-load-machine-learning-models-ml-net.md)</span><span class="sxs-lookup"><span data-stu-id="c7902-295">See [Save and load trained models](../how-to-guides/save-load-machine-learning-models-ml-net.md) to learn how to operationalize a trained machine learning model in apps.</span></span>

## <a name="results"></a><span data-ttu-id="c7902-296">Sonuçlar</span><span class="sxs-lookup"><span data-stu-id="c7902-296">Results</span></span>

<span data-ttu-id="c7902-297">Yukarıdaki adımları takip ettikten sonra konsol uygulamanızı (Ctrl + F5) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c7902-297">After following the steps above, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="c7902-298">Yukarıdaki tek tahminden elde edilen sonuçlar aşağıdakilere benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c7902-298">Your results from the single prediction above should be similar to the following.</span></span> <span data-ttu-id="c7902-299">Uyarılar veya iletileri işleme görebilirsiniz, ancak bu iletiler netlik için aşağıdaki sonuçlardan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="c7902-299">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

```console
=============== Training the model ===============
iter      tr_rmse          obj
   0       1.5382   3.1213e+05
   1       0.9223   1.6051e+05
   2       0.8691   1.5050e+05
   3       0.8413   1.4576e+05
   4       0.8145   1.4208e+05
   5       0.7848   1.3895e+05
   6       0.7552   1.3613e+05
   7       0.7259   1.3357e+05
   8       0.6987   1.3121e+05
   9       0.6747   1.2949e+05
  10       0.6533   1.2766e+05
  11       0.6353   1.2636e+05
  12       0.6209   1.2561e+05
  13       0.6072   1.2462e+05
  14       0.5965   1.2394e+05
  15       0.5868   1.2352e+05
  16       0.5782   1.2279e+05
  17       0.5713   1.2227e+05
  18       0.5637   1.2190e+05
  19       0.5604   1.2178e+05
=============== Evaluating the model ===============
Rms: 0.977175077487166
RSquared: 0.43233349213192
=============== Making a prediction ===============
Movie 10 is recommended for user 6
=============== Saving the model to a file ===============
```

<span data-ttu-id="c7902-300">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="c7902-300">Congratulations!</span></span> <span data-ttu-id="c7902-301">Şimdi başarılı film tavsiye için bir makine öğrenme modeli inşa ettik.</span><span class="sxs-lookup"><span data-stu-id="c7902-301">You've now successfully built a machine learning model for recommending movies.</span></span> <span data-ttu-id="c7902-302">Bu öğreticinin kaynak kodunu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7902-302">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repository.</span></span>

## <a name="improve-your-model"></a><span data-ttu-id="c7902-303">Modelinizi geliştirme</span><span class="sxs-lookup"><span data-stu-id="c7902-303">Improve your model</span></span>

<span data-ttu-id="c7902-304">Daha doğru tahminler elde etmek için modelinizin performansını artırmanın birkaç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="c7902-304">There are several ways that you can improve the performance of your model so that you can get more accurate predictions.</span></span>

### <a name="data"></a><span data-ttu-id="c7902-305">Veriler</span><span class="sxs-lookup"><span data-stu-id="c7902-305">Data</span></span>

<span data-ttu-id="c7902-306">Her kullanıcı ve film kimliği için yeterli örnek olan daha fazla eğitim verisi eklemek, öneri modelinin kalitesini artırmaya yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="c7902-306">Adding more training data that has enough samples for each user and movie id can help improve the quality of the recommendation model.</span></span>

<span data-ttu-id="c7902-307">[Çapraz doğrulama,](../how-to-guides/train-machine-learning-model-cross-validation-ml-net.md) verileri rasgele alt kümelere bölen modelleri (bu öğreticide yaptığınız gibi veri kümesinden test verilerini ayıklamak yerine) değerlendirmek için bir tekniktir ve bazı grupları tren verileri olarak, bazı grupları da test verisi olarak alır.</span><span class="sxs-lookup"><span data-stu-id="c7902-307">[Cross validation](../how-to-guides/train-machine-learning-model-cross-validation-ml-net.md) is a technique for evaluating models that randomly splits up data into subsets (instead of extracting out test data from the dataset like you did in this tutorial) and takes some of the groups as train data and some of the groups as test data.</span></span> <span data-ttu-id="c7902-308">Bu yöntem, model kalitesi açısından bir tren testi bölünmüş yapma daha iyi performans gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7902-308">This method outperforms making a train-test split in terms of model quality.</span></span>

### <a name="features"></a><span data-ttu-id="c7902-309">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c7902-309">Features</span></span>

<span data-ttu-id="c7902-310">Bu öğreticide, yalnızca veri `Features` `user id`kümesi `movie id`tarafından `rating`sağlanan üç ( , , ve ) kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="c7902-310">In this tutorial, you only use the three `Features` (`user id`, `movie id`, and `rating`) that are provided by the dataset.</span></span>

<span data-ttu-id="c7902-311">Bu iyi bir başlangıç olsa da, gerçekte başka `Features` öznitelikler eklemek veya veri kümesine dahil edilirse (örneğin, yaş, cinsiyet, coğrafi konum, vb.) eklemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7902-311">While this is a good start, in reality you might want to add other attributes or `Features` (for example, age, gender, geo-location, etc.) if they are included in the dataset.</span></span> <span data-ttu-id="c7902-312">Daha alakalı `Features` eklemek, öneri modelinizin performansını artırmaya yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="c7902-312">Adding more relevant `Features` can help improve the performance of your recommendation model.</span></span>

<span data-ttu-id="c7902-313">Makine öğrenimi göreviniz `Features` için hangisinin en uygun olabileceğinden emin değilseniz, ML.NET en etkili `Features`yi keşfetmenizi sağlayan Özellik Katkısı Hesaplama (FCC) ve [permütasyon özelliğinin önemini](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md)de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7902-313">If you are unsure about which `Features` might be the most relevant for your machine learning task, you can also make use of Feature Contribution Calculation (FCC) and [permutation feature importance](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md), which ML.NET provides to discover the most influential `Features`.</span></span>

### <a name="algorithm-hyperparameters"></a><span data-ttu-id="c7902-314">Algoritma hiperparametreleri</span><span class="sxs-lookup"><span data-stu-id="c7902-314">Algorithm hyperparameters</span></span>

<span data-ttu-id="c7902-315">ML.NET iyi varsayılan eğitim algoritmaları sağlarken, algoritmanın [hiperparametrelerini](../resources/glossary.md#hyperparameter)değiştirerek performansı daha da ince ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7902-315">While ML.NET provides good default training algorithms, you can further fine-tune performance by changing the algorithm's [hyperparameters](../resources/glossary.md#hyperparameter).</span></span>

<span data-ttu-id="c7902-316">Için, `Matrix Factorization`Size daha iyi sonuçlar verir olmadığını görmek için [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) ve [YaklaşıkRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) gibi hiperparametreler i deneme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7902-316">For `Matrix Factorization`, you can experiment with hyperparameters such as [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) and [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) to see if that gives you better results.</span></span>

<span data-ttu-id="c7902-317">Örneğin, bu öğreticide algoritma seçenekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="c7902-317">For instance, in this tutorial the algorithm options are:</span></span>

```csharp
var options = new MatrixFactorizationTrainer.Options
{
    MatrixColumnIndexColumnName = "userIdEncoded",
    MatrixRowIndexColumnName = "movieIdEncoded",
    LabelColumnName = "Label",
    NumberOfIterations = 20,
    ApproximationRank = 100
};
```

### <a name="other-recommendation-algorithms"></a><span data-ttu-id="c7902-318">Diğer Öneri Algoritmaları</span><span class="sxs-lookup"><span data-stu-id="c7902-318">Other Recommendation Algorithms</span></span>

<span data-ttu-id="c7902-319">İşbirlikçi filtreleme ile matris çarpanlara ayırma algoritması film önerileri gerçekleştirmek için yalnızca bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="c7902-319">The matrix factorization algorithm with collaborative filtering is only one approach for performing movie recommendations.</span></span> <span data-ttu-id="c7902-320">Çoğu durumda, derecelendirme verileriniz olmayabilir ve yalnızca kullanıcılardan kullanılabilen film geçmişiniz olabilir.</span><span class="sxs-lookup"><span data-stu-id="c7902-320">In many cases, you may not have the ratings data available and only have movie history available from users.</span></span> <span data-ttu-id="c7902-321">Diğer durumlarda, kullanıcının derecelendirme verilerinden daha fazlanız olabilir.</span><span class="sxs-lookup"><span data-stu-id="c7902-321">In other cases, you may have more than just the user’s rating data.</span></span>

| <span data-ttu-id="c7902-322">Algoritma</span><span class="sxs-lookup"><span data-stu-id="c7902-322">Algorithm</span></span>       | <span data-ttu-id="c7902-323">Senaryo</span><span class="sxs-lookup"><span data-stu-id="c7902-323">Scenario</span></span>           | <span data-ttu-id="c7902-324">Örnek</span><span class="sxs-lookup"><span data-stu-id="c7902-324">Sample</span></span>  |
| ------------- |:-------------:| -----:|
| <span data-ttu-id="c7902-325">Bir Sınıf Matris Çarpanekatizasyonu</span><span class="sxs-lookup"><span data-stu-id="c7902-325">One Class Matrix Factorization</span></span> | <span data-ttu-id="c7902-326">Yalnızca userId ve movieId'invarsa bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="c7902-326">Use this when you only have userId and movieId.</span></span> <span data-ttu-id="c7902-327">Bu öneri stili, ortak satın alma senaryosuna veya sık sık birlikte satın alınan ürünlere dayanır, bu da müşterilere kendi satınalma siparişi geçmişlerine dayalı bir ürün kümesi önereceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c7902-327">This style of recommendation is based upon the co-purchase scenario, or products frequently bought together, which means it will recommend to customers a set of products based upon their own purchase order history.</span></span> | [<span data-ttu-id="c7902-328">>Deneyin</span><span class="sxs-lookup"><span data-stu-id="c7902-328">>Try it out</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/MatrixFactorization_ProductRecommendation) |
| <span data-ttu-id="c7902-329">Alan Farkında Faktoring Makineleri</span><span class="sxs-lookup"><span data-stu-id="c7902-329">Field Aware Factorization Machines</span></span> | <span data-ttu-id="c7902-330">UserId, productId ve derecelendirmenin ötesinde (ürün açıklaması veya ürün fiyatı gibi) daha fazla Özelliğe sahip olduğunuzda önerilerde bulunmak için bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="c7902-330">Use this to make recommendations when you have more Features beyond userId, productId, and rating (such as product description or product price).</span></span> <span data-ttu-id="c7902-331">Bu yöntem, ortak bir filtreleme yaklaşımı da kullanır.</span><span class="sxs-lookup"><span data-stu-id="c7902-331">This method also uses a collaborative filtering approach.</span></span> | [<span data-ttu-id="c7902-332">>Deneyin</span><span class="sxs-lookup"><span data-stu-id="c7902-332">>Try it out</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/Recommendation-MovieRecommender) |

### <a name="new-user-scenario"></a><span data-ttu-id="c7902-333">Yeni kullanıcı senaryosu</span><span class="sxs-lookup"><span data-stu-id="c7902-333">New user scenario</span></span>

<span data-ttu-id="c7902-334">İşbirlikçi filtrelemede sık karşılaşılan bir sorun, çıkarımları çıkarımları yapacak önceki verileri olmayan yeni bir kullanıcıya sahip olduğunuzda soğuk başlangıç sorunudur.</span><span class="sxs-lookup"><span data-stu-id="c7902-334">One common problem in collaborative filtering is the cold start problem, which is when you have a new user with no previous data to draw inferences from.</span></span> <span data-ttu-id="c7902-335">Bu sorun genellikle yeni kullanıcılardan bir profil oluşturmalarını isteyerek ve örneğin geçmişte gördükleri filmleri derecelendirerek çözülür.</span><span class="sxs-lookup"><span data-stu-id="c7902-335">This problem is often solved by asking new users to create a profile and, for instance, rate movies they have seen in the past.</span></span> <span data-ttu-id="c7902-336">Bu yöntem kullanıcıya bazı yükler getirse de, derecelendirme geçmişi olmayan yeni kullanıcılar için bazı başlangıç verileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7902-336">While this method puts some burden on the user, it provides some starting data for new users with no rating history.</span></span>

## <a name="resources"></a><span data-ttu-id="c7902-337">Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="c7902-337">Resources</span></span>

<span data-ttu-id="c7902-338">Bu eğitimde kullanılan veriler [MovieLens Dataset'ten](http://files.grouplens.org/datasets/movielens/)türetilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c7902-338">The data used in this tutorial is derived from [MovieLens Dataset](http://files.grouplens.org/datasets/movielens/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="c7902-339">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="c7902-339">Next steps</span></span>

<span data-ttu-id="c7902-340">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="c7902-340">In this tutorial, you learned how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="c7902-341">Makine öğrenimi algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="c7902-341">Select a machine learning algorithm</span></span>
> * <span data-ttu-id="c7902-342">Verilerinizi hazırlama ve yükleme</span><span class="sxs-lookup"><span data-stu-id="c7902-342">Prepare and load your data</span></span>
> * <span data-ttu-id="c7902-343">Bir model oluşturma ve eğitme</span><span class="sxs-lookup"><span data-stu-id="c7902-343">Build and train a model</span></span>
> * <span data-ttu-id="c7902-344">Bir modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="c7902-344">Evaluate a model</span></span>
> * <span data-ttu-id="c7902-345">Bir modeli dağıtma ve tüket</span><span class="sxs-lookup"><span data-stu-id="c7902-345">Deploy and consume a model</span></span>

<span data-ttu-id="c7902-346">Daha fazla bilgi edinmek için bir sonraki öğreticiye ilerleyin</span><span class="sxs-lookup"><span data-stu-id="c7902-346">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="c7902-347">Duygusallık Analizi</span><span class="sxs-lookup"><span data-stu-id="c7902-347">Sentiment Analysis</span></span>](sentiment-analysis.md)
