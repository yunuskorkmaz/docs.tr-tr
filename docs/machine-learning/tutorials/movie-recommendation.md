---
title: 'Öğretici: film oluşturma öneren-matris oluşturma'
description: Bu öğreticide, bir .NET Core konsol uygulamasında ML.NET ile bir film öneren oluşturma yöntemi gösterilmektedir. Adımları ve Visual C# Studio 2019 ' i kullanın.
author: briacht
ms.date: 09/30/2019
ms.custom: mvc, title-hack-0516
ms.topic: tutorial
ms.openlocfilehash: 1db2ad6c078cb6201b2a6a4e2f8572f589cee684
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700960"
---
# <a name="tutorial-build-a-movie-recommender-using-matrix-factorizaton-with-mlnet"></a><span data-ttu-id="7c2be-104">Öğretici: ML.NET ile matris factorizaton kullanarak bir film öneren oluşturma</span><span class="sxs-lookup"><span data-stu-id="7c2be-104">Tutorial: Build a movie recommender using matrix factorizaton with ML.NET</span></span>

<span data-ttu-id="7c2be-105">Bu öğreticide, bir .NET Core konsol uygulamasında ML.NET ile bir film öneren oluşturma yöntemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7c2be-105">This tutorial shows you how to build a movie recommender with ML.NET in a .NET Core console application.</span></span> <span data-ttu-id="7c2be-106">Adımları ve Visual C# Studio 2019 ' i kullanın.</span><span class="sxs-lookup"><span data-stu-id="7c2be-106">The steps use C# and Visual Studio 2019.</span></span>

<span data-ttu-id="7c2be-107">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="7c2be-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="7c2be-108">Makine öğrenimi algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="7c2be-108">Select a machine learning algorithm</span></span>
> * <span data-ttu-id="7c2be-109">Verilerinizi hazırlayın ve yükleyin</span><span class="sxs-lookup"><span data-stu-id="7c2be-109">Prepare and load your data</span></span>
> * <span data-ttu-id="7c2be-110">Model oluşturma ve eğitme</span><span class="sxs-lookup"><span data-stu-id="7c2be-110">Build and train a model</span></span>
> * <span data-ttu-id="7c2be-111">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="7c2be-111">Evaluate a model</span></span>
> * <span data-ttu-id="7c2be-112">Bir modeli dağıtma ve kullanma</span><span class="sxs-lookup"><span data-stu-id="7c2be-112">Deploy and consume a model</span></span>

<span data-ttu-id="7c2be-113">Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c2be-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repository.</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="7c2be-114">Machine Learning iş akışı</span><span class="sxs-lookup"><span data-stu-id="7c2be-114">Machine learning workflow</span></span>

<span data-ttu-id="7c2be-115">Görevinizi ve diğer ML.NET görevlerini gerçekleştirmek için aşağıdaki adımları kullanacaksınız:</span><span class="sxs-lookup"><span data-stu-id="7c2be-115">You will use the following steps to accomplish your task, as well as any other ML.NET task:</span></span>

1. [<span data-ttu-id="7c2be-116">Verilerinizi yükleme</span><span class="sxs-lookup"><span data-stu-id="7c2be-116">Load your data</span></span>](#load-your-data)
2. [<span data-ttu-id="7c2be-117">Modelinizi derleyin ve eğitme</span><span class="sxs-lookup"><span data-stu-id="7c2be-117">Build and train your model</span></span>](#build-and-train-your-model)
3. [<span data-ttu-id="7c2be-118">Modelinizi değerlendirin</span><span class="sxs-lookup"><span data-stu-id="7c2be-118">Evaluate your model</span></span>](#evaluate-your-model)
4. [<span data-ttu-id="7c2be-119">Modelinizi kullanın</span><span class="sxs-lookup"><span data-stu-id="7c2be-119">Use your model</span></span>](#use-your-model)

## <a name="prerequisites"></a><span data-ttu-id="7c2be-120">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="7c2be-120">Prerequisites</span></span>

* <span data-ttu-id="7c2be-121">[Visual Studio 2017 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core platformlar arası geliştirme" iş yükü yüklendi.</span><span class="sxs-lookup"><span data-stu-id="7c2be-121">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="7c2be-122">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="7c2be-122">Select the appropriate machine learning task</span></span>

<span data-ttu-id="7c2be-123">Bir film listesi önermek veya ilgili ürünlerin bir listesini önermek gibi öneri sorunlarına yaklaşımak için birkaç yol vardır. Bu durumda, bir kullanıcının belirli bir filmi hangi derecelendirmeye sunduu (1-5) tahmin edecek ve bu filmin tanımlı eşikten yüksek (derecelendirme arttıkça, bir kullanıcının belirli bir filmi beğenme olasılığı yüksektir).</span><span class="sxs-lookup"><span data-stu-id="7c2be-123">There are several ways to approach recommendation problems, such as recommending a list of movies or recommending a list of related products, but in this case you will predict what rating (1-5) a user will give to a particular movie and recommend that movie if it's higher than a defined threshold (the higher the rating, the higher the likelihood of a user liking a particular movie).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="7c2be-124">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="7c2be-124">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="7c2be-125">Proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="7c2be-125">Create a project</span></span>

1. <span data-ttu-id="7c2be-126">Visual Studio 2017 ' i açın.</span><span class="sxs-lookup"><span data-stu-id="7c2be-126">Open Visual Studio 2017.</span></span> <span data-ttu-id="7c2be-127">Menü çubuğundan **dosya** > **Yeni** > **Proje** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="7c2be-127">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="7c2be-128">**Yeni proje** iletişim kutusunda,  **C# Visual** düğümünü ve ardından **.NET Core** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="7c2be-128">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="7c2be-129">Ardından **konsol uygulaması (.NET Core)** proje şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="7c2be-129">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="7c2be-130">**Ad** metin kutusuna "MovieRecommender" yazın ve **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="7c2be-130">In the **Name** text box, type "MovieRecommender" and then select the **OK** button.</span></span>

2. <span data-ttu-id="7c2be-131">Veri kümesini depolamak için projenizde *veri* adlı bir dizin oluşturun:</span><span class="sxs-lookup"><span data-stu-id="7c2be-131">Create a directory named *Data* in your project to store the data set:</span></span>

    <span data-ttu-id="7c2be-132">**Çözüm Gezgini**, projeye sağ tıklayın ve ardından  > **Yeni klasör** **Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="7c2be-132">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="7c2be-133">"Data" yazın ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7c2be-133">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="7c2be-134">**Microsoft.ml** ve **Microsoft. ml. öneren** NuGet paketlerini yükler:</span><span class="sxs-lookup"><span data-stu-id="7c2be-134">Install the **Microsoft.ML** and **Microsoft.ML.Recommender** NuGet Packages:</span></span>

    <span data-ttu-id="7c2be-135">**Çözüm Gezgini**, projeye sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="7c2be-135">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="7c2be-136">Paket kaynağı olarak "nuget.org" öğesini seçin, **Araştır** sekmesini seçin, **Microsoft.ml**için arama yapın, listeden paketi seçin ve sonra da **Install** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="7c2be-136">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the package in the list, and select the **Install** button.</span></span> <span data-ttu-id="7c2be-137">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="7c2be-137">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="7c2be-138">**Microsoft. ml. öneren**için bu adımları tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="7c2be-138">Repeat these steps for **Microsoft.ML.Recommender**.</span></span>

4. <span data-ttu-id="7c2be-139">Aşağıdaki `using` deyimlerini *program.cs* dosyanızın üst kısmına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7c2be-139">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[UsingStatements](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#UsingStatements "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="7c2be-140">Verilerinizi indirin</span><span class="sxs-lookup"><span data-stu-id="7c2be-140">Download your data</span></span>

1. <span data-ttu-id="7c2be-141">İki veri kümesini indirin ve daha önce oluşturduğunuz *veri* klasörüne kaydedin:</span><span class="sxs-lookup"><span data-stu-id="7c2be-141">Download the two datasets and save them to the *Data* folder you previously created:</span></span>

   * <span data-ttu-id="7c2be-142">[*Recommendation-Ratings-train. csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) ' ye sağ tıklayın ve "bağlantıyı (veya hedefi) farklı kaydet" i seçin.</span><span class="sxs-lookup"><span data-stu-id="7c2be-142">Right click on [*recommendation-ratings-train.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) and select "Save Link (or Target) As..."</span></span>
   * <span data-ttu-id="7c2be-143">[*Recommendation-Ratings-test. csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) ' ye sağ tıklayın ve "bağlantıyı (veya hedefi) farklı kaydet" i seçin.</span><span class="sxs-lookup"><span data-stu-id="7c2be-143">Right click on [*recommendation-ratings-test.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="7c2be-144">@No__t -0. csv dosyalarını *veri* klasörüne kaydettiğinizden ya da başka bir yere kaydettikten sonra, @no__t -2. csv dosyalarını *veri* klasörüne taşıyın.</span><span class="sxs-lookup"><span data-stu-id="7c2be-144">Make sure you either save the \*.csv files to the *Data* folder, or after you save it elsewhere, move the \*.csv files to the *Data* folder.</span></span>

2. <span data-ttu-id="7c2be-145">Çözüm Gezgini, @no__t -0. csv dosyalarının her birine sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="7c2be-145">In Solution Explorer, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="7c2be-146">**Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7c2be-146">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

   ![VS 'de daha yeniyse kopyala](./media/movie-recommendation/copytoout.gif)

## <a name="load-your-data"></a><span data-ttu-id="7c2be-148">Verilerinizi yükleme</span><span class="sxs-lookup"><span data-stu-id="7c2be-148">Load your data</span></span>

<span data-ttu-id="7c2be-149">ML.NET işlemindeki ilk adım, model eğitimi ve test verilerini hazırlamaktır ve yükler.</span><span class="sxs-lookup"><span data-stu-id="7c2be-149">The first step in the ML.NET process is to prepare and load your model training and testing data.</span></span>

<span data-ttu-id="7c2be-150">Öneri derecelendirme verileri `Train` ve `Test` veri kümelerine bölünür.</span><span class="sxs-lookup"><span data-stu-id="7c2be-150">The recommendation ratings data is split into `Train` and `Test` datasets.</span></span> <span data-ttu-id="7c2be-151">@No__t-0 verisi modelinize uyacak şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7c2be-151">The `Train` data is used to fit your model.</span></span> <span data-ttu-id="7c2be-152">@No__t-0 verisi, eğitilen modelinizdeki tahminleri yapmak ve model performansını değerlendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7c2be-152">The `Test` data is used to make predictions with your trained model and evaluate model performance.</span></span> <span data-ttu-id="7c2be-153">@No__t-0 ve `Test` verileri ile 80/20 bölüneceği için yaygındır.</span><span class="sxs-lookup"><span data-stu-id="7c2be-153">It's common to have an 80/20 split with `Train` and `Test` data.</span></span>

<span data-ttu-id="7c2be-154">Aşağıda @no__t -0. csv dosyalarınızda verilerin önizlemesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="7c2be-154">Below is a preview of the data from your \*.csv files:</span></span>

![verilerin önizlemesi](./media/movie-recommendation/csv-dataset-preview.png)

<span data-ttu-id="7c2be-156">@No__t -0. csv dosyalarında dört sütun vardır:</span><span class="sxs-lookup"><span data-stu-id="7c2be-156">In the \*.csv files, there are four columns:</span></span>

* `userId`
* `movieId`
* `rating`
* `timestamp`

<span data-ttu-id="7c2be-157">Machine Learning 'de, bir tahmin yapmak için kullanılan sütunlara [Özellikler](../resources/glossary.md#feature)denir ve döndürülen tahmine sahip olan sütuna [etiket](../resources/glossary.md#label)denir.</span><span class="sxs-lookup"><span data-stu-id="7c2be-157">In machine learning, the columns that are used to make a prediction are called [Features](../resources/glossary.md#feature), and the column with the returned prediction is called the [Label](../resources/glossary.md#label).</span></span>

<span data-ttu-id="7c2be-158">Film derecelendirmelerini tahmin etmek istiyorsunuz, bu nedenle Derecelendirme sütunu `Label` olur.</span><span class="sxs-lookup"><span data-stu-id="7c2be-158">You want to predict movie ratings, so the rating column is the `Label`.</span></span> <span data-ttu-id="7c2be-159">@No__t-0, `movieId` ve `timestamp` diğer üç sütun, `Label` ' ü tahmin etmek için kullanılan `Features` ' ü kullanır.</span><span class="sxs-lookup"><span data-stu-id="7c2be-159">The other three columns, `userId`, `movieId`, and `timestamp` are all `Features` used to predict the `Label`.</span></span>

| <span data-ttu-id="7c2be-160">Özellikler</span><span class="sxs-lookup"><span data-stu-id="7c2be-160">Features</span></span>      | <span data-ttu-id="7c2be-161">Etiketle</span><span class="sxs-lookup"><span data-stu-id="7c2be-161">Label</span></span>         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |
| `timestamp`     |               |

<span data-ttu-id="7c2be-162">@No__t-1 ' i tahmin etmek için kullanılacak `Features` ' a karar verirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c2be-162">It's up to you to decide which `Features` are used to predict the `Label`.</span></span> <span data-ttu-id="7c2be-163">Ayrıca, `Features` ' i seçmeye yardımcı olması için [özellik permütasyon önem derecesi](../how-to-guides/determine-global-feature-importance-in-model.md) gibi yöntemleri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c2be-163">You can also use methods like [Feature Permutation Importance](../how-to-guides/determine-global-feature-importance-in-model.md) to help with selecting the best `Features`.</span></span>

<span data-ttu-id="7c2be-164">Bu durumda, zaman damgası bir kullanıcının belirli bir filmi nasıl fiyatlandırdığı ve bu nedenle daha doğru bir tahmin yapma konusunda katkıda bulunmamasının gerektiği için `timestamp` sütununu `Feature` olarak ortadan kaldırmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="7c2be-164">In this case, you should eliminate the `timestamp` column as a `Feature` because the timestamp does not really affect how a user rates a given movie and thus would not contribute to making a more accurate prediction:</span></span>

| <span data-ttu-id="7c2be-165">Özellikler</span><span class="sxs-lookup"><span data-stu-id="7c2be-165">Features</span></span>      | <span data-ttu-id="7c2be-166">Etiketle</span><span class="sxs-lookup"><span data-stu-id="7c2be-166">Label</span></span>         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |

<span data-ttu-id="7c2be-167">Ardından, giriş sınıfı için veri yapınızı tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7c2be-167">Next you must define your data structure for the input class.</span></span>

<span data-ttu-id="7c2be-168">Projenize yeni bir sınıf ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7c2be-168">Add a new class to your project:</span></span>

1. <span data-ttu-id="7c2be-169">**Çözüm Gezgini**, projeye sağ tıklayın ve ardından **> yeni öğe Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="7c2be-169">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="7c2be-170">**Yeni öğe Ekle iletişim kutusunda** **sınıf** ' ı seçin ve **ad** alanını *MovieRatingData.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7c2be-170">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *MovieRatingData.cs*.</span></span> <span data-ttu-id="7c2be-171">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="7c2be-171">Then, select the **Add** button.</span></span>

<span data-ttu-id="7c2be-172">*MovieRatingData.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="7c2be-172">The *MovieRatingData.cs* file opens in the code editor.</span></span> <span data-ttu-id="7c2be-173">Aşağıdaki `using` ifadesini *MovieRatingData.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7c2be-173">Add the following `using` statement to the top of *MovieRatingData.cs*:</span></span>

```csharp
using Microsoft.ML.Data;
```

<span data-ttu-id="7c2be-174">Mevcut sınıf tanımını kaldırarak `MovieRating` adlı bir sınıf oluşturun ve aşağıdaki kodu *MovieRatingData.cs*içine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7c2be-174">Create a class called `MovieRating` by removing the existing class definition and adding the following code in *MovieRatingData.cs*:</span></span>

[!code-csharp[MovieRatingClass](~/samples/machine-learning/tutorials/MovieRecommendation/MovieRatingData.cs#MovieRatingClass "Add the Movie Rating class")]

<span data-ttu-id="7c2be-175">`MovieRating` bir giriş veri sınıfını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7c2be-175">`MovieRating` specifies an input data class.</span></span> <span data-ttu-id="7c2be-176">[Loadcolumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) özniteliği, veri kümesindeki hangi sütunların (sütun dizinine göre) yükleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7c2be-176">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span> <span data-ttu-id="7c2be-177">@No__t-0 ve `movieId` sütunları `Features` ' dir (modele `Label` ' ü tahmin etmek için izin verdiğiniz girişler) ve derecelendirme sütunu, tahmin ettiğiniz `Label` ' ü (modelin çıktısı) sağlar.</span><span class="sxs-lookup"><span data-stu-id="7c2be-177">The `userId` and `movieId` columns are your `Features` (the inputs you will give the model to predict the `Label`), and the rating column is the `Label` that you will predict (the output of the model).</span></span>

<span data-ttu-id="7c2be-178">*MovieRatingData.cs*içindeki `MovieRating` sınıfından sonra aşağıdaki kodu ekleyerek tahmin edilen sonuçları göstermek için `MovieRatingPrediction` olan başka bir sınıf oluşturun:</span><span class="sxs-lookup"><span data-stu-id="7c2be-178">Create another class, `MovieRatingPrediction`, to represent predicted results by adding the following code after the `MovieRating` class in *MovieRatingData.cs*:</span></span>

[!code-csharp[PredictionClass](~/samples/machine-learning/tutorials/MovieRecommendation/MovieRatingData.cs#PredictionClass "Add the Movie Prediction Class")]

<span data-ttu-id="7c2be-179">*Program.cs*' de `Console.WriteLine("Hello World!")` ' i `Main()` içindeki aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="7c2be-179">In *Program.cs*, replace the `Console.WriteLine("Hello World!")` with the following code inside `Main()`:</span></span>

[!code-csharp[MLContext](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#MLContext "Add MLContext")]

<span data-ttu-id="7c2be-180">[Mlcontext sınıfı](xref:Microsoft.ML.MLContext) tüm ml.NET işlemleri için bir başlangıç noktasıdır ve @no__t başlatılıyor-1, model oluşturma iş akışı nesneleri genelinde paylaşılabilen yeni bir ml.net ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7c2be-180">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="7c2be-181">Bu, kavramsal olarak, Entity Framework `DBContext` ' a benzer.</span><span class="sxs-lookup"><span data-stu-id="7c2be-181">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="7c2be-182">@No__t-0 ' dan sonra, `LoadData()` adlı bir yöntem oluşturun:</span><span class="sxs-lookup"><span data-stu-id="7c2be-182">After `Main()`, create a method called `LoadData()`:</span></span>

```csharp
public static (IDataView training, IDataView test) LoadData(MLContext mlContext)
{

}
```

> [!NOTE]
> <span data-ttu-id="7c2be-183">Bu yöntem, aşağıdaki adımlarda bir return ifadesini eklemeene kadar bir hata verir.</span><span class="sxs-lookup"><span data-stu-id="7c2be-183">This method will give you an error until you add a return statement in the following steps.</span></span>

<span data-ttu-id="7c2be-184">Veri yolu değişkenlerinizi başlatın, @no__t -0. csv dosyalarından verileri yükleyin ve `LoadData()` ' te sonraki kod satırı olarak aşağıdakini ekleyerek @no__t 3 nesne olarak `Train` ve `Test` verileri döndürün:</span><span class="sxs-lookup"><span data-stu-id="7c2be-184">Initialize your data path variables, load the data from the \*.csv files, and return the `Train` and `Test` data as `IDataView` objects by adding the following as the next line of code in `LoadData()`:</span></span>

[!code-csharp[LoadData](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#LoadData "Load data from data paths")]

<span data-ttu-id="7c2be-185">ML.NET içindeki veriler [ıdataview sınıfı](xref:Microsoft.ML.IDataView)olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="7c2be-185">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="7c2be-186">`IDataView`, tablo verilerini (sayısal ve metin) tanımlamaya yönelik esnek ve verimli bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="7c2be-186">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="7c2be-187">Veriler bir metin dosyasından veya gerçek zamanlı olarak (örneğin, SQL veritabanı veya günlük dosyaları) `IDataView` nesnesine yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="7c2be-187">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="7c2be-188">[Loadfromtextfile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) , veri şemasını ve dosyadaki okumaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7c2be-188">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="7c2be-189">Veri yolu değişkenlerini alır ve `IDataView` döndürür.</span><span class="sxs-lookup"><span data-stu-id="7c2be-189">It takes in the data path variables and returns an `IDataView`.</span></span> <span data-ttu-id="7c2be-190">Bu durumda, `Test` ve `Train` dosyalarınız için yol sağlar ve hem metin dosyası üst bilgisini hem de (sütun adlarını düzgün bir şekilde kullanabilmesi için) virgül karakter veri ayırıcısını (varsayılan ayırıcı bir sekmedir) belirtin.</span><span class="sxs-lookup"><span data-stu-id="7c2be-190">In this case, you provide the path for your `Test` and `Train` files and indicate both the text file header (so it can use the column names properly) and the comma character data separator (the default separator is a tab).</span></span>

<span data-ttu-id="7c2be-191">@No__t-1 yönteminizi çağırmak için `Main()` yöntemine aşağıdaki kodu ekleyin ve `Train` ve `Test` verilerini geri döndürün:</span><span class="sxs-lookup"><span data-stu-id="7c2be-191">Add the following code in the `Main()` method to call your `LoadData()` method and return the `Train` and `Test` data:</span></span>

[!code-csharp[LoadDataMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#LoadDataMain "Add LoadData method to Main")]

## <a name="build-and-train-your-model"></a><span data-ttu-id="7c2be-192">Modelinizi derleyin ve eğitme</span><span class="sxs-lookup"><span data-stu-id="7c2be-192">Build and train your model</span></span>

<span data-ttu-id="7c2be-193">ML.NET: [Data](../resources/glossary.md#data), [dönüştürücüler](../resources/glossary.md#transformer)ve [estimators](../resources/glossary.md#estimator)'da üç önemli kavram vardır.</span><span class="sxs-lookup"><span data-stu-id="7c2be-193">There are three major concepts in ML.NET: [Data](../resources/glossary.md#data), [Transformers](../resources/glossary.md#transformer), and [Estimators](../resources/glossary.md#estimator).</span></span>

<span data-ttu-id="7c2be-194">Machine Learning eğitim algoritmaları, verileri belirli bir biçimde gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7c2be-194">Machine learning training algorithms require data in a certain format.</span></span> <span data-ttu-id="7c2be-195">`Transformers`, tablo verilerini uyumlu bir biçime dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7c2be-195">`Transformers` are used to transform tabular data to a compatible format.</span></span>

![Transformatör resmi](./media/movie-recommendation/transformer.png)

<span data-ttu-id="7c2be-197">@No__t-1 oluşturarak, ML.NET içinde `Transformers` oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7c2be-197">You create `Transformers` in ML.NET by creating `Estimators`.</span></span> <span data-ttu-id="7c2be-198">`Estimators` verileri alın ve `Transformers` döndürün.</span><span class="sxs-lookup"><span data-stu-id="7c2be-198">`Estimators` take in data and return `Transformers`.</span></span>

![tahmin aracı resmi](./media/movie-recommendation/estimator.png)

<span data-ttu-id="7c2be-200">Modelinize eğitim için kullanacağınız öneri eğitimi algoritması, `Estimator` ' a bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="7c2be-200">The recommendation training algorithm you will use for training your model is an example of an `Estimator`.</span></span>

<span data-ttu-id="7c2be-201">Aşağıdaki adımlarla bir `Estimator` oluşturun:</span><span class="sxs-lookup"><span data-stu-id="7c2be-201">Build an `Estimator` with the following steps:</span></span>

<span data-ttu-id="7c2be-202">Aşağıdaki kodu kullanarak, `LoadData()` yönteminden hemen sonra `BuildAndTrainModel()` yöntemini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="7c2be-202">Create the `BuildAndTrainModel()` method, just after the `LoadData()` method, using the following code:</span></span>

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView trainingDataView)
{

}
```

> [!NOTE]
> <span data-ttu-id="7c2be-203">Bu yöntem, aşağıdaki adımlarda bir return ifadesini eklemeene kadar bir hata verir.</span><span class="sxs-lookup"><span data-stu-id="7c2be-203">This method will give you an error until you add a return statement in the following steps.</span></span>

<span data-ttu-id="7c2be-204">@No__t-0 ' a aşağıdaki kodu ekleyerek veri dönüşümlerini tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="7c2be-204">Define the data transformations by adding the following code to `BuildAndTrainModel()`:</span></span>

[!code-csharp[DataTransformations](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#DataTransformations "Define data transformations")]

<span data-ttu-id="7c2be-205">@No__t-0 ve `movieId`, gerçek değerleri değil kullanıcıları ve film başlıklarını temsil ettiğinden, her bir `userId` ' ü ve her `movieId` ' ü bir sayısal anahtar türü `Feature` sütununa (öneri algoritmalarının tarafından kabul edilen bir biçim) dönüştürmek için [Mapvaluetokey ()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) yöntemini kullanırsınız ve bunları yeni veri kümesi sütunları olarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7c2be-205">Since `userId` and `movieId` represent users and movie titles, not real values, you use the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method to transform each `userId` and each `movieId` into a numeric key type `Feature` column (a format accepted by recommendation algorithms) and add them as new dataset columns:</span></span>

| <span data-ttu-id="7c2be-206">UserID</span><span class="sxs-lookup"><span data-stu-id="7c2be-206">userId</span></span> | <span data-ttu-id="7c2be-207">Movieıd</span><span class="sxs-lookup"><span data-stu-id="7c2be-207">movieId</span></span> | <span data-ttu-id="7c2be-208">Etiketle</span><span class="sxs-lookup"><span data-stu-id="7c2be-208">Label</span></span> | <span data-ttu-id="7c2be-209">Userıdencoded</span><span class="sxs-lookup"><span data-stu-id="7c2be-209">userIdEncoded</span></span> | <span data-ttu-id="7c2be-210">Movieıdencoded</span><span class="sxs-lookup"><span data-stu-id="7c2be-210">movieIdEncoded</span></span> |
| ------------- |:-------------:| -----:|-----:|-----:|
| <span data-ttu-id="7c2be-211">1\.</span><span class="sxs-lookup"><span data-stu-id="7c2be-211">1</span></span> | <span data-ttu-id="7c2be-212">1\.</span><span class="sxs-lookup"><span data-stu-id="7c2be-212">1</span></span> | <span data-ttu-id="7c2be-213">4</span><span class="sxs-lookup"><span data-stu-id="7c2be-213">4</span></span> | <span data-ttu-id="7c2be-214">userKey1</span><span class="sxs-lookup"><span data-stu-id="7c2be-214">userKey1</span></span> | <span data-ttu-id="7c2be-215">movieKey1</span><span class="sxs-lookup"><span data-stu-id="7c2be-215">movieKey1</span></span> |
| <span data-ttu-id="7c2be-216">1\.</span><span class="sxs-lookup"><span data-stu-id="7c2be-216">1</span></span> | <span data-ttu-id="7c2be-217">3</span><span class="sxs-lookup"><span data-stu-id="7c2be-217">3</span></span> | <span data-ttu-id="7c2be-218">4</span><span class="sxs-lookup"><span data-stu-id="7c2be-218">4</span></span> | <span data-ttu-id="7c2be-219">userKey1</span><span class="sxs-lookup"><span data-stu-id="7c2be-219">userKey1</span></span> | <span data-ttu-id="7c2be-220">movieKey2</span><span class="sxs-lookup"><span data-stu-id="7c2be-220">movieKey2</span></span> |
| <span data-ttu-id="7c2be-221">1\.</span><span class="sxs-lookup"><span data-stu-id="7c2be-221">1</span></span> | <span data-ttu-id="7c2be-222">6</span><span class="sxs-lookup"><span data-stu-id="7c2be-222">6</span></span> | <span data-ttu-id="7c2be-223">4</span><span class="sxs-lookup"><span data-stu-id="7c2be-223">4</span></span> | <span data-ttu-id="7c2be-224">userKey1</span><span class="sxs-lookup"><span data-stu-id="7c2be-224">userKey1</span></span> | <span data-ttu-id="7c2be-225">movieKey3</span><span class="sxs-lookup"><span data-stu-id="7c2be-225">movieKey3</span></span> |

<span data-ttu-id="7c2be-226">Machine Learning algoritmasını seçin ve `BuildAndTrainModel()` ' a bir sonraki kod satırı olarak aşağıdakini ekleyerek veri dönüştürme tanımlarına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7c2be-226">Choose the machine learning algorithm and append it to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[AddAlgorithm](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#AddAlgorithm "Add the training algorithm with options")]

<span data-ttu-id="7c2be-227">[Matrixfactorizationtrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) , öneri eğitim algoritmanız.</span><span class="sxs-lookup"><span data-stu-id="7c2be-227">The [MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) is your recommendation training algorithm.</span></span>  <span data-ttu-id="7c2be-228">[Matris](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) , kullanıcıların geçmişte ürünleri derecelendirirken, bu öğreticideki veri kümeleri için büyük/küçük bir yaklaşım olan genel bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="7c2be-228">[Matrix Factorization](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) is a common approach to recommendation when you have data on how users have rated products in the past, which is the case for the datasets in this tutorial.</span></span> <span data-ttu-id="7c2be-229">Farklı verilere sahip olduğunuzda kullanabileceğiniz başka öneri algoritmaları vardır (daha fazla bilgi için aşağıdaki [diğer öneri algoritmaları](#other-recommendation-algorithms) bölümüne bakın).</span><span class="sxs-lookup"><span data-stu-id="7c2be-229">There are other recommendation algorithms for when you have different data available (see the [Other recommendation algorithms](#other-recommendation-algorithms) section below to learn more).</span></span>

<span data-ttu-id="7c2be-230">Bu durumda, `Matrix Factorization` algoritması "işbirliğine dayalı filtreleme" adlı bir yöntem kullanır. Bu, Kullanıcı 1 ' in belirli bir sorun üzerinde Kullanıcı 2 ' de aynı görüşe sahip olduğunu varsaymışsa, 1. Kullanıcı farklı bir sorun hakkında Kullanıcı 2 ' ye benzer şekilde daha olasıdır.</span><span class="sxs-lookup"><span data-stu-id="7c2be-230">In this case, the `Matrix Factorization` algorithm uses a method called "collaborative filtering", which assumes that if User 1 has the same opinion as User 2 on a certain issue, then User 1 is more likely to feel the same way as User 2 about a different issue.</span></span>

<span data-ttu-id="7c2be-231">Örneğin, Kullanıcı 1 ve Kullanıcı 2 filmleri benzer şekilde kullanıyorsanız, 1. Kullanıcı 2 ' nin, Kullanıcı 1 ' in izlenen ve yüksek oranda derecelendirdikleri bir filmin keyfini çıkarmak daha yüksektir:</span><span class="sxs-lookup"><span data-stu-id="7c2be-231">For instance, if User 1 and User 2 rate movies similarly, then User 2 is more likely to enjoy a movie that User 1 has watched and rated highly:</span></span>

| | `Incredibles 2 (2018)` | `The Avengers (2012)` | `Guardians of the Galaxy (2014)` |
| -------------:|-------------:| -----:|-----:|
| <span data-ttu-id="7c2be-232">Kullanıcı 1</span><span class="sxs-lookup"><span data-stu-id="7c2be-232">User 1</span></span> | <span data-ttu-id="7c2be-233">İzlenen ve beğenilen film</span><span class="sxs-lookup"><span data-stu-id="7c2be-233">Watched and liked movie</span></span> | <span data-ttu-id="7c2be-234">İzlenen ve beğenilen film</span><span class="sxs-lookup"><span data-stu-id="7c2be-234">Watched and liked movie</span></span> | <span data-ttu-id="7c2be-235">İzlenen ve beğenilen film</span><span class="sxs-lookup"><span data-stu-id="7c2be-235">Watched and liked movie</span></span> |
| <span data-ttu-id="7c2be-236">Kullanıcı 2</span><span class="sxs-lookup"><span data-stu-id="7c2be-236">User 2</span></span> | <span data-ttu-id="7c2be-237">İzlenen ve beğenilen film</span><span class="sxs-lookup"><span data-stu-id="7c2be-237">Watched and liked movie</span></span> | <span data-ttu-id="7c2be-238">İzlenen ve beğenilen film</span><span class="sxs-lookup"><span data-stu-id="7c2be-238">Watched and liked movie</span></span> | <span data-ttu-id="7c2be-239">İzleniyor--film öner</span><span class="sxs-lookup"><span data-stu-id="7c2be-239">Has not watched -- RECOMMEND movie</span></span> |

<span data-ttu-id="7c2be-240">@No__t-0 eğitmen, aşağıdaki [algoritma hiper parametreleri](#algorithm-hyperparameters) bölümünde hakkında daha fazla bilgi edinmek için çeşitli [seçeneklere](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options)sahiptir.</span><span class="sxs-lookup"><span data-stu-id="7c2be-240">The `Matrix Factorization` trainer has several [Options](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), which you can read more about in the [Algorithm hyperparameters](#algorithm-hyperparameters) section below.</span></span>

<span data-ttu-id="7c2be-241">Modeli `Train` verilerine sığdırın ve `BuildAndTrainModel()` yöntemine sonraki kod satırı olarak aşağıdakileri ekleyerek eğitilen modeli döndürün:</span><span class="sxs-lookup"><span data-stu-id="7c2be-241">Fit the model to the `Train` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[FitModel](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#FitModel "Call the Fit method and return back the trained model")]

<span data-ttu-id="7c2be-242">[Fit ()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) yöntemi, modelinizi belirtilen eğitim veri kümesiyle eğliyor.</span><span class="sxs-lookup"><span data-stu-id="7c2be-242">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model with the provided training dataset.</span></span> <span data-ttu-id="7c2be-243">Teknik olarak, verileri dönüştürerek ve eğitimi uygulayarak `Estimator` tanımlarını yürütür ve bir `Transformer` olan eğitilen modeli geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="7c2be-243">Technically, it executes the `Estimator` definitions by transforming the data and applying the training, and it returns back the trained model, which is a `Transformer`.</span></span>

<span data-ttu-id="7c2be-244">@No__t-1 yönteminizi çağırmak ve eğitilen modeli döndürmek için `Main()` yöntemine sonraki kod satırı olarak aşağıdakini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7c2be-244">Add the following as the next line of code in the `Main()` method to call your `BuildAndTrainModel()` method and return the trained model:</span></span>

[!code-csharp[BuildTrainModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#BuildTrainModelMain "Add BuildAndTrainModel method in Main")]

## <a name="evaluate-your-model"></a><span data-ttu-id="7c2be-245">Modelinizi değerlendirin</span><span class="sxs-lookup"><span data-stu-id="7c2be-245">Evaluate your model</span></span>

<span data-ttu-id="7c2be-246">Modelinizi eğittikten sonra, modelinizin nasıl çalıştığını değerlendirmek için test verilerinizi kullanın.</span><span class="sxs-lookup"><span data-stu-id="7c2be-246">Once you have trained your model, use your test data to evaluate how your model is performing.</span></span>

<span data-ttu-id="7c2be-247">Aşağıdaki kodu kullanarak, `BuildAndTrainModel()` yönteminden hemen sonra `EvaluateModel()` yöntemini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="7c2be-247">Create the `EvaluateModel()` method, just after the `BuildAndTrainModel()` method, using the following code:</span></span>

```csharp
public static void EvaluateModel(MLContext mlContext, IDataView testDataView, ITransformer model)
{

}
```

<span data-ttu-id="7c2be-248">Aşağıdaki kodu `EvaluateModel()` ' e ekleyerek `Test` verisini dönüştürün:</span><span class="sxs-lookup"><span data-stu-id="7c2be-248">Transform the `Test` data by adding the following code to `EvaluateModel()`:</span></span>

[!code-csharp[Transform](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#Transform "Transform the test data")]

<span data-ttu-id="7c2be-249">[Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemi, test veri kümesinin birden çok sağlanmış giriş satırları için tahminleri yapar.</span><span class="sxs-lookup"><span data-stu-id="7c2be-249">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for multiple provided input rows of a test dataset.</span></span>

<span data-ttu-id="7c2be-250">@No__t-0 yöntemine sonraki kod satırı olarak aşağıdakileri ekleyerek modeli değerlendirin:</span><span class="sxs-lookup"><span data-stu-id="7c2be-250">Evaluate the model by adding the following as the next line of code in the `EvaluateModel()` method:</span></span>

[!code-csharp[Evaluate](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#Evaluate "Evaluate the model using predictions from the test data")]

<span data-ttu-id="7c2be-251">Tahmin kümesine sahip olduktan sonra, değerlendirir [()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) yöntemi, tahmin edilen değerleri test veri kümesindeki gerçek `Labels` ile karşılaştıran ve modelin nasıl çalıştığı ile ilgili ölçümleri döndüren modeli.</span><span class="sxs-lookup"><span data-stu-id="7c2be-251">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns metrics on how the model is performing.</span></span>

<span data-ttu-id="7c2be-252">Aşağıdaki kod satırı olarak `EvaluateModel()` yöntemine ekleyerek değerlendirme ölçümlerini konsola yazdırın:</span><span class="sxs-lookup"><span data-stu-id="7c2be-252">Print your evaluation metrics to the console by adding the following as the next line of code in the `EvaluateModel()` method:</span></span>

[!code-csharp[PrintMetrics](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PrintMetrics "Print the evaluation metrics")]

<span data-ttu-id="7c2be-253">@No__t-1 yönteminizi çağırmak için `Main()` yöntemine sonraki kod satırı olarak aşağıdakini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7c2be-253">Add the following as the next line of code in the `Main()` method to call your `EvaluateModel()` method:</span></span>

[!code-csharp[EvaluateModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#EvaluateModelMain "Add EvaluateModel method in Main")]

<span data-ttu-id="7c2be-254">Şu ana kadar çıkış aşağıdaki metne benzer görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="7c2be-254">The output so far should look similar to the following text:</span></span>

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

<span data-ttu-id="7c2be-255">Bu çıktıda 20 yineleme vardır.</span><span class="sxs-lookup"><span data-stu-id="7c2be-255">In this output, there are 20 iterations.</span></span> <span data-ttu-id="7c2be-256">Her yinelemede, hata ölçüsü azalır ve 0 ' a yaklaştırır.</span><span class="sxs-lookup"><span data-stu-id="7c2be-256">In each iteration, the measure of error decreases and converges closer and closer to 0.</span></span>

<span data-ttu-id="7c2be-257">@No__t-0 (RMS veya rmo), model tahmin edilen değerler ve test veri kümesi gözlenen değerleri arasındaki farkları ölçmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7c2be-257">The `root of mean squared error` (RMS or RMSE) is used to measure the differences between the model predicted values and the test dataset observed values.</span></span> <span data-ttu-id="7c2be-258">Teknik olarak, hataların karelerinin ortalamasının karekökünü temel alır.</span><span class="sxs-lookup"><span data-stu-id="7c2be-258">Technically it's the square root of the average of the squares of the errors.</span></span> <span data-ttu-id="7c2be-259">Bunun ne kadar küçük olması, modelin ne kadar iyi olduğu.</span><span class="sxs-lookup"><span data-stu-id="7c2be-259">The lower it is, the better the model is.</span></span>

<span data-ttu-id="7c2be-260">`R Squared`, verilerin modele ne kadar iyi uyduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="7c2be-260">`R Squared` indicates how well data fits a model.</span></span> <span data-ttu-id="7c2be-261">0 ile 1 arasında aralıklar.</span><span class="sxs-lookup"><span data-stu-id="7c2be-261">Ranges from 0 to 1.</span></span> <span data-ttu-id="7c2be-262">0 değeri, verilerin rastgele olması veya başka türlü modele sığamayacak olması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7c2be-262">A value of 0 means that the data is random or otherwise can't be fit to the model.</span></span> <span data-ttu-id="7c2be-263">1 değeri, modelin verilerle tam olarak eşleştiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7c2be-263">A value of 1 means that the model exactly matches the data.</span></span> <span data-ttu-id="7c2be-264">@No__t-0 puanınızın mümkün olduğunca 1 ' e yakın olmasını istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="7c2be-264">You want your `R Squared` score to be as close to 1 as possible.</span></span>

<span data-ttu-id="7c2be-265">Başarılı modellerin oluşturulması, yinelemeli bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="7c2be-265">Building successful models is an iterative process.</span></span> <span data-ttu-id="7c2be-266">Öğretici, hızlı model eğitimi sağlamak için küçük veri kümeleri kullandığından, bu modelin ilk daha düşük kalitesi vardır.</span><span class="sxs-lookup"><span data-stu-id="7c2be-266">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="7c2be-267">Model kalitede memnun kalmıyorsanız, daha büyük eğitim veri kümeleri sağlayarak veya her algoritma için farklı Hyper-parametreleri ile farklı eğitim algoritmaları seçerek bunu geliştirmeyi deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c2be-267">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different hyper-parameters for each algorithm.</span></span> <span data-ttu-id="7c2be-268">Daha fazla bilgi için aşağıdaki [modelinizi geliştirme](#improve-your-model) bölümünü inceleyin.</span><span class="sxs-lookup"><span data-stu-id="7c2be-268">For more information, check out the [Improve your model](#improve-your-model) section below.</span></span>

## <a name="use-your-model"></a><span data-ttu-id="7c2be-269">Modelinizi kullanın</span><span class="sxs-lookup"><span data-stu-id="7c2be-269">Use your model</span></span>

<span data-ttu-id="7c2be-270">Artık yeni verilerde öngörülere sahip olmak için eğitilen modeli kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c2be-270">Now you can use your trained model to make predictions on new data.</span></span>

<span data-ttu-id="7c2be-271">Aşağıdaki kodu kullanarak, `EvaluateModel()` yönteminden hemen sonra `UseModelForSinglePrediction()` yöntemini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="7c2be-271">Create the `UseModelForSinglePrediction()` method, just after the `EvaluateModel()` method, using the following code:</span></span>

```csharp
public static void UseModelForSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="7c2be-272">Aşağıdaki kodu `UseModelForSinglePrediction()` ' e ekleyerek derecelendirmeyi tahmin etmek için `PredictionEngine` kullanın:</span><span class="sxs-lookup"><span data-stu-id="7c2be-272">Use the `PredictionEngine` to predict the rating by adding the following code to `UseModelForSinglePrediction()`:</span></span>

[!code-csharp[PredictionEngine](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PredictionEngine "Create Prediction Engine")]

<span data-ttu-id="7c2be-273">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneğinde tahmin gerçekleştirmenize olanak tanıyan, KULLANıŞLı bir API 'dir.</span><span class="sxs-lookup"><span data-stu-id="7c2be-273">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="7c2be-274">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) , iş parçacığı açısından güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="7c2be-274">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="7c2be-275">Tek iş parçacıklı veya prototip ortamlarında kullanılması kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="7c2be-275">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="7c2be-276">Üretim ortamlarında geliştirilmiş performans ve iş parçacığı güvenliği için, uygulamanızda kullanılmak üzere [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) nesnesi oluşturan `PredictionEnginePool` hizmetini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7c2be-276">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="7c2be-277">[ASP.NET Core Web API 'sinde `PredictionEnginePool` ' i nasıl kullanacağınızı](https://docs.microsoft.com/en-us/dotnet/machine-learning/how-to-guides/serve-model-web-api-ml-net#register-predictionenginepool-for-use-in-the-application) öğrenmek için bu kılavuza bakın</span><span class="sxs-lookup"><span data-stu-id="7c2be-277">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](https://docs.microsoft.com/en-us/dotnet/machine-learning/how-to-guides/serve-model-web-api-ml-net#register-predictionenginepool-for-use-in-the-application)</span></span>

> [!NOTE]
> <span data-ttu-id="7c2be-278">`PredictionEnginePool` hizmet uzantısı Şu anda önizleme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="7c2be-278">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="7c2be-279">@No__t-1 adlı @no__t bir örnek oluşturun ve aşağıdaki kod satırları `UseModelForSinglePrediction()` yöntemine ekleyerek bunu tahmin altyapısına geçirin:</span><span class="sxs-lookup"><span data-stu-id="7c2be-279">Create an instance of `MovieRating` called `testInput` and pass it to the Prediction Engine by adding the following as the next lines of code in the `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[MakeSinglePrediction](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#MakeSinglePrediction "Make a single prediction with the Prediction Engine")]

<span data-ttu-id="7c2be-280">PREDICT [()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi, tek bir veri sütunu üzerinde bir tahmin yapar.</span><span class="sxs-lookup"><span data-stu-id="7c2be-280">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single column of data.</span></span>

<span data-ttu-id="7c2be-281">Ardından, filmi Kullanıcı 6 ' ya Movieıd 10 ile önermek isteyip istemediğinizi öğrenmek için `Score` veya tahmin edilen derecelendirmeyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c2be-281">You can then use the `Score`, or the predicted rating, to determine whether you want to recommend the movie with movieId 10 to user 6.</span></span> <span data-ttu-id="7c2be-282">@No__t-0 arttıkça, bir kullanıcının belirli bir filmi beğenme olasılığı yüksektir.</span><span class="sxs-lookup"><span data-stu-id="7c2be-282">The higher the `Score`, the higher the likelihood of a user liking a particular movie.</span></span> <span data-ttu-id="7c2be-283">Bu durumda, > 3,5 ' nin tahmin edilen derecelendirmesine sahip filmler önertiğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="7c2be-283">In this case, let’s say that you recommend movies with a predicted rating of > 3.5.</span></span>

<span data-ttu-id="7c2be-284">Sonuçları yazdırmak için, `UseModelForSinglePrediction()` yöntemine sonraki kod satırları olarak aşağıdakini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7c2be-284">To print the results, add the following as the next lines of code in the `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[PrintResults](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PrintResults "Print the recommendation prediction results")]

<span data-ttu-id="7c2be-285">@No__t-1 yönteminizi çağırmak için `Main()` yöntemine sonraki kod satırı olarak aşağıdakini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7c2be-285">Add the following as the next line of code in the `Main()` method to call your `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[UseModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#UseModelMain "Add UseModelForSinglePrediction method in Main")]

<span data-ttu-id="7c2be-286">Bu yöntemin çıktısı aşağıdaki metne benzer görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="7c2be-286">The output of this method should look similar to the following text:</span></span>

```console
=============== Making a prediction ===============
Movie 10 is recommended for user 6
```

### <a name="save-your-model"></a><span data-ttu-id="7c2be-287">Modelinizi kaydetme</span><span class="sxs-lookup"><span data-stu-id="7c2be-287">Save your model</span></span>

<span data-ttu-id="7c2be-288">Son Kullanıcı uygulamalarında tahmine dayalı hale getirmek üzere modelinizi kullanmak için önce modeli kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7c2be-288">To use your model to make predictions in end-user applications, you must first save the model.</span></span>

<span data-ttu-id="7c2be-289">Aşağıdaki kodu kullanarak, `UseModelForSinglePrediction()` yönteminden hemen sonra `SaveModel()` yöntemini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="7c2be-289">Create the `SaveModel()` method, just after the `UseModelForSinglePrediction()` method, using the following code:</span></span>

```csharp
public static void SaveModel(MLContext mlContext, DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

<span data-ttu-id="7c2be-290">@No__t-0 yöntemine aşağıdaki kodu ekleyerek eğitilen modelinizi kaydedin:</span><span class="sxs-lookup"><span data-stu-id="7c2be-290">Save your trained model by adding the following code in the `SaveModel()` method:</span></span>

[!code-csharp[SaveModel](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#SaveModel "Save the model to a zip file")]

<span data-ttu-id="7c2be-291">Bu yöntem, eğitilen modelinizi, daha sonra tahmine dayalı hale getirmek için diğer .NET uygulamalarında kullanılabilecek bir. zip dosyasına ("veri" klasöründe) kaydeder.</span><span class="sxs-lookup"><span data-stu-id="7c2be-291">This method saves your trained model to a .zip file (in the "Data" folder), which can then be used in other .NET applications to make predictions.</span></span>

<span data-ttu-id="7c2be-292">@No__t-1 yönteminizi çağırmak için `Main()` yöntemine sonraki kod satırı olarak aşağıdakini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7c2be-292">Add the following as the next line of code in the `Main()` method to call your `SaveModel()` method:</span></span>

[!code-csharp[SaveModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#SaveModelMain "Create SaveModel method in Main")]

### <a name="use-your-saved-model"></a><span data-ttu-id="7c2be-293">Kayıtlı modelinizi kullanın</span><span class="sxs-lookup"><span data-stu-id="7c2be-293">Use your saved model</span></span>

<span data-ttu-id="7c2be-294">Eğitilen modelinizi kaydettikten sonra modeli farklı ortamlarda kullanabilirsiniz (uygulamalarda eğitilen bir makine öğrenimi modelinin nasıl yapılacağını öğrenmek için bkz. ["nasıl yapılır Kılavuzu"](../how-to-guides/consuming-model-ml-net.md) ).</span><span class="sxs-lookup"><span data-stu-id="7c2be-294">Once you have saved your trained model, you can consume the model in different environments (see the ["How-to guide"](../how-to-guides/consuming-model-ml-net.md) to learn how to operationalize a trained machine learning model in apps).</span></span>

## <a name="results"></a><span data-ttu-id="7c2be-295">Sonuçlar</span><span class="sxs-lookup"><span data-stu-id="7c2be-295">Results</span></span>

<span data-ttu-id="7c2be-296">Yukarıdaki adımları tamamladıktan sonra konsol uygulamanızı çalıştırın (CTRL + F5).</span><span class="sxs-lookup"><span data-stu-id="7c2be-296">After following the steps above, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="7c2be-297">Yukarıdaki tek bir tahmine ait sonuçlarınız aşağıdakine benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7c2be-297">Your results from the single prediction above should be similar to the following.</span></span> <span data-ttu-id="7c2be-298">Uyarıları veya işlem iletilerini görebilirsiniz, ancak bu iletiler netme için aşağıdaki sonuçlardan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="7c2be-298">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="7c2be-299">Mühendisi!</span><span class="sxs-lookup"><span data-stu-id="7c2be-299">Congratulations!</span></span> <span data-ttu-id="7c2be-300">Artık film öneren bir makine öğrenimi modelini başarıyla oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="7c2be-300">You've now successfully built a machine learning model for recommending movies.</span></span> <span data-ttu-id="7c2be-301">Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c2be-301">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repository.</span></span>

## <a name="improve-your-model"></a><span data-ttu-id="7c2be-302">Modelinizi geliştirme</span><span class="sxs-lookup"><span data-stu-id="7c2be-302">Improve your model</span></span>

<span data-ttu-id="7c2be-303">Daha doğru öngörülere ulaşmak için modelinizin performansını iyileştirebilmeniz için birkaç yol vardır.</span><span class="sxs-lookup"><span data-stu-id="7c2be-303">There are several ways that you can improve the performance of your model so that you can get more accurate predictions.</span></span>

### <a name="data"></a><span data-ttu-id="7c2be-304">Veri</span><span class="sxs-lookup"><span data-stu-id="7c2be-304">Data</span></span>

<span data-ttu-id="7c2be-305">Her Kullanıcı ve film kimliği için yeterli sayıda örnek içeren eğitim verileri eklemek, öneri modelinin kalitesini artırmaya yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="7c2be-305">Adding more training data that has enough samples for each user and movie id can help improve the quality of the recommendation model.</span></span>

<span data-ttu-id="7c2be-306">[Çapraz doğrulama](../how-to-guides/train-cross-validation-ml-net.md) , verileri rastgele kümeler halinde ayırır (Bu öğreticide yaptığınız gibi veri kümesinden test verilerinin ayıklanmasının yerine) ve bazı gruplardan verileri test verileri olarak eğitme ve gruplardan bazılarını alan bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="7c2be-306">[Cross validation](../how-to-guides/train-cross-validation-ml-net.md) is a technique for evaluating models that randomly splits up data into subsets (instead of extracting out test data from the dataset like you did in this tutorial) and takes some of the groups as train data and some of the groups as test data.</span></span> <span data-ttu-id="7c2be-307">Bu yöntem, model kalitesi açısından bir eğitme testi ayırma yapmayı gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="7c2be-307">This method outperforms making a train-test split in terms of model quality.</span></span>

### <a name="features"></a><span data-ttu-id="7c2be-308">Özellikler</span><span class="sxs-lookup"><span data-stu-id="7c2be-308">Features</span></span>

<span data-ttu-id="7c2be-309">Bu öğreticide, yalnızca veri kümesi tarafından sunulan üç @no__t (`user id`, `movie id` ve `rating`) kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="7c2be-309">In this tutorial, you only use the three `Features` (`user id`, `movie id`, and `rating`) that are provided by the dataset.</span></span>

<span data-ttu-id="7c2be-310">Bu iyi bir başlangıç olsa da, gerçekte veri kümesine dahil ediliyorlarsa diğer öznitelikleri veya `Features` (örneğin, Age, cinsiyet, coğrafi konum vb.) eklemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c2be-310">While this is a good start, in reality you might want to add other attributes or `Features` (for example, age, gender, geo-location, etc.) if they are included in the dataset.</span></span> <span data-ttu-id="7c2be-311">Daha fazla ilgili @no__t eklemek, öneri modelinizin performansını artırmaya yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="7c2be-311">Adding more relevant `Features` can help improve the performance of your recommendation model.</span></span>

<span data-ttu-id="7c2be-312">Machine Learning göreviniz için en uygun olan `Features` ' ı bilmiyorsanız, özellik katkı hesaplaması (FCC) ve [özellik permütasyon önem](../how-to-guides/determine-global-feature-importance-in-model.md)derecesini de kullanabilirsiniz. bu, ml.net 'in en etkili olduğunu keşfetmesini sağlar `Features`.</span><span class="sxs-lookup"><span data-stu-id="7c2be-312">If you are unsure about which `Features` might be the most relevant for your machine learning task, you can also make use of Feature Contribution Calculation (FCC) and [Feature Permutation Importance](../how-to-guides/determine-global-feature-importance-in-model.md), which ML.NET provides to discover the most influential `Features`.</span></span>

### <a name="algorithm-hyperparameters"></a><span data-ttu-id="7c2be-313">Algoritma hiper parametreleri</span><span class="sxs-lookup"><span data-stu-id="7c2be-313">Algorithm hyperparameters</span></span>

<span data-ttu-id="7c2be-314">ML.NET, iyi varsayılan eğitim algoritmaları sağlarken, algoritmanın [hiper parametrelerini](../resources/glossary.md#hyperparameter)değiştirerek performansı daha ayrıntılı bir şekilde ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c2be-314">While ML.NET provides good default training algorithms, you can further fine-tune performance by changing the algorithm's [hyperparameters](../resources/glossary.md#hyperparameter).</span></span>

<span data-ttu-id="7c2be-315">@No__t-0 için, [Numberofiterasyonların](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) ve [yaklaşık](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) olarak daha iyi sonuçlar verir.</span><span class="sxs-lookup"><span data-stu-id="7c2be-315">For `Matrix Factorization`, you can experiment with hyperparameters such as [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) and [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) to see if that gives you better results.</span></span>

<span data-ttu-id="7c2be-316">Örneğin, bu öğreticide algoritma seçenekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="7c2be-316">For instance, in this tutorial the algorithm options are:</span></span>

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

### <a name="other-recommendation-algorithms"></a><span data-ttu-id="7c2be-317">Diğer öneri algoritmaları</span><span class="sxs-lookup"><span data-stu-id="7c2be-317">Other Recommendation Algorithms</span></span>

<span data-ttu-id="7c2be-318">Ortak filtreleme ile matris ayırma algoritması, film önerileri gerçekleştirmeye yönelik yalnızca bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="7c2be-318">The matrix factorization algorithm with collaborative filtering is only one approach for performing movie recommendations.</span></span> <span data-ttu-id="7c2be-319">Çoğu durumda, derecelendirme verileri kullanılabilir olmayabilir ve yalnızca film geçmişi kullanıcılardan bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="7c2be-319">In many cases, you may not have the ratings data available and only have movie history available from users.</span></span> <span data-ttu-id="7c2be-320">Diğer durumlarda, yalnızca kullanıcının derecelendirme verilerinden daha fazlasına sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c2be-320">In other cases, you may have more than just the user’s rating data.</span></span>

| <span data-ttu-id="7c2be-321">Algoritmalar</span><span class="sxs-lookup"><span data-stu-id="7c2be-321">Algorithm</span></span>       | <span data-ttu-id="7c2be-322">Senaryo</span><span class="sxs-lookup"><span data-stu-id="7c2be-322">Scenario</span></span>           | <span data-ttu-id="7c2be-323">Örnek</span><span class="sxs-lookup"><span data-stu-id="7c2be-323">Sample</span></span>  |
| ------------- |:-------------:| -----:|
| <span data-ttu-id="7c2be-324">Bir sınıf matrisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="7c2be-324">One Class Matrix Factorization</span></span> | <span data-ttu-id="7c2be-325">Yalnızca Kullanıcı kimliği ve Movieıd olduğunda bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="7c2be-325">Use this when you only have userId and movieId.</span></span> <span data-ttu-id="7c2be-326">Bu öneri stili, ortak satın alma senaryosuna veya genellikle birlikte satın alınan ürünlere dayalıdır. Bu, müşterilerin kendi satın alma siparişi geçmişine göre bir ürün kümesi önermesini önermeyeceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7c2be-326">This style of recommendation is based upon the co-purchase scenario, or products frequently bought together, which means it will recommend to customers a set of products based upon their own purchase order history.</span></span> | [<span data-ttu-id="7c2be-327">> deneyin</span><span class="sxs-lookup"><span data-stu-id="7c2be-327">>Try it out</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/MatrixFactorization_ProductRecommendation) |
| <span data-ttu-id="7c2be-328">Alan duyarlı bir ayırma makinesi</span><span class="sxs-lookup"><span data-stu-id="7c2be-328">Field Aware Factorization Machines</span></span> | <span data-ttu-id="7c2be-329">Kullanıcı kimliği, ProductID ve derecelendirmeden daha fazla özelliğe sahip olduğunuzda (ürün açıklaması veya ürün fiyatı gibi) öneri sağlamak için bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="7c2be-329">Use this to make recommendations when you have more Features beyond userId, productId, and rating (such as product description or product price).</span></span> <span data-ttu-id="7c2be-330">Bu yöntem ayrıca birlikte çalışan bir filtreleme yaklaşımı kullanır.</span><span class="sxs-lookup"><span data-stu-id="7c2be-330">This method also uses a collaborative filtering approach.</span></span> | [<span data-ttu-id="7c2be-331">> deneyin</span><span class="sxs-lookup"><span data-stu-id="7c2be-331">>Try it out</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/Recommendation-MovieRecommender) |

### <a name="new-user-scenario"></a><span data-ttu-id="7c2be-332">Yeni Kullanıcı senaryosu</span><span class="sxs-lookup"><span data-stu-id="7c2be-332">New user scenario</span></span>

<span data-ttu-id="7c2be-333">İşbirliğine dayalı filtrelemede yaygın olarak karşılaşılan bir sorun, yeni bir kullanıcıya, ıntreler eklemek için önceki verileri olmayan yeni bir kullanıcı olduğunda oluşan soğuk başlatma sorunudur.</span><span class="sxs-lookup"><span data-stu-id="7c2be-333">One common problem in collaborative filtering is the cold start problem, which is when you have a new user with no previous data to draw inferences from.</span></span> <span data-ttu-id="7c2be-334">Bu sorun genellikle yeni kullanıcılardan bir profil oluşturmasını isteyerek ve örneğin, geçmişte gördüğü filmleri derecelendirmek için çözülür.</span><span class="sxs-lookup"><span data-stu-id="7c2be-334">This problem is often solved by asking new users to create a profile and, for instance, rate movies they have seen in the past.</span></span> <span data-ttu-id="7c2be-335">Bu yöntem kullanıcıya bazı yük koyar, ancak derecelendirme geçmişi olmayan yeni kullanıcılar için bazı veri başlatma verileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="7c2be-335">While this method puts some burden on the user, it provides some starting data for new users with no rating history.</span></span>

## <a name="resources"></a><span data-ttu-id="7c2be-336">Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="7c2be-336">Resources</span></span>

<span data-ttu-id="7c2be-337">Bu öğreticide kullanılan veriler [Movielens veri kümesinden](http://files.grouplens.org/datasets/movielens/)türetilir.</span><span class="sxs-lookup"><span data-stu-id="7c2be-337">The data used in this tutorial is derived from [MovieLens Dataset](http://files.grouplens.org/datasets/movielens/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="7c2be-338">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="7c2be-338">Next steps</span></span>

<span data-ttu-id="7c2be-339">Bu öğreticide, nasıl yapılacağını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="7c2be-339">In this tutorial, you learned how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="7c2be-340">Makine öğrenimi algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="7c2be-340">Select a machine learning algorithm</span></span>
> * <span data-ttu-id="7c2be-341">Verilerinizi hazırlayın ve yükleyin</span><span class="sxs-lookup"><span data-stu-id="7c2be-341">Prepare and load your data</span></span>
> * <span data-ttu-id="7c2be-342">Model oluşturma ve eğitme</span><span class="sxs-lookup"><span data-stu-id="7c2be-342">Build and train a model</span></span>
> * <span data-ttu-id="7c2be-343">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="7c2be-343">Evaluate a model</span></span>
> * <span data-ttu-id="7c2be-344">Bir modeli dağıtma ve kullanma</span><span class="sxs-lookup"><span data-stu-id="7c2be-344">Deploy and consume a model</span></span>

<span data-ttu-id="7c2be-345">Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin</span><span class="sxs-lookup"><span data-stu-id="7c2be-345">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="7c2be-346">Yaklaşım Analizi</span><span class="sxs-lookup"><span data-stu-id="7c2be-346">Sentiment Analysis</span></span>](sentiment-analysis.md)
