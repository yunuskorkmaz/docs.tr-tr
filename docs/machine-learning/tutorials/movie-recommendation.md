---
title: 'Öğretici: Film oluşturma öneren-matris oluşturma'
description: Bu öğreticide, bir .NET Core konsol uygulamasında ML.NET ile bir film öneren oluşturma yöntemi gösterilmektedir. Adımları ve Visual C# Studio 2019 ' i kullanın.
author: briacht
ms.date: 08/26/2019
ms.custom: mvc, title-hack-0516
ms.topic: tutorial
ms.openlocfilehash: 4f80ebad0a280040e9f3329dc7b647bd53a48fa0
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929490"
---
# <a name="tutorial-build-a-movie-recommender-using-matrix-factorizaton-with-mlnet"></a><span data-ttu-id="463dd-104">Öğretici: ML.NET ile matris factorizaton kullanarak bir film öneren oluşturun</span><span class="sxs-lookup"><span data-stu-id="463dd-104">Tutorial: Build a movie recommender using matrix factorizaton with ML.NET</span></span>

<span data-ttu-id="463dd-105">Bu öğreticide, bir .NET Core konsol uygulamasında ML.NET ile bir film öneren oluşturma yöntemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="463dd-105">This tutorial shows you how to build a movie recommender with ML.NET in a .NET Core console application.</span></span> <span data-ttu-id="463dd-106">Adımları ve Visual C# Studio 2019 ' i kullanın.</span><span class="sxs-lookup"><span data-stu-id="463dd-106">The steps use C# and Visual Studio 2019.</span></span>

<span data-ttu-id="463dd-107">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="463dd-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="463dd-108">Makine öğrenimi algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="463dd-108">Select a machine learning algorithm</span></span>
> * <span data-ttu-id="463dd-109">Verilerinizi hazırlayın ve yükleyin</span><span class="sxs-lookup"><span data-stu-id="463dd-109">Prepare and load your data</span></span>
> * <span data-ttu-id="463dd-110">Model oluşturma ve eğitme</span><span class="sxs-lookup"><span data-stu-id="463dd-110">Build and train a model</span></span>
> * <span data-ttu-id="463dd-111">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="463dd-111">Evaluate a model</span></span>
> * <span data-ttu-id="463dd-112">Bir modeli dağıtma ve kullanma</span><span class="sxs-lookup"><span data-stu-id="463dd-112">Deploy and consume a model</span></span>

<span data-ttu-id="463dd-113">Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="463dd-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repository.</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="463dd-114">Machine Learning iş akışı</span><span class="sxs-lookup"><span data-stu-id="463dd-114">Machine learning workflow</span></span>

<span data-ttu-id="463dd-115">Görevinizi ve diğer ML.NET görevlerini gerçekleştirmek için aşağıdaki adımları kullanacaksınız:</span><span class="sxs-lookup"><span data-stu-id="463dd-115">You will use the following steps to accomplish your task, as well as any other ML.NET task:</span></span>

1. [<span data-ttu-id="463dd-116">Verilerinizi yükleme</span><span class="sxs-lookup"><span data-stu-id="463dd-116">Load your data</span></span>](#load-your-data)
2. [<span data-ttu-id="463dd-117">Modelinizi derleyin ve eğitme</span><span class="sxs-lookup"><span data-stu-id="463dd-117">Build and train your model</span></span>](#build-and-train-your-model)
3. [<span data-ttu-id="463dd-118">Modelinizi değerlendirin</span><span class="sxs-lookup"><span data-stu-id="463dd-118">Evaluate your model</span></span>](#evaluate-your-model)
4. [<span data-ttu-id="463dd-119">Modelinizi kullanın</span><span class="sxs-lookup"><span data-stu-id="463dd-119">Use your model</span></span>](#use-your-model)

## <a name="prerequisites"></a><span data-ttu-id="463dd-120">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="463dd-120">Prerequisites</span></span>

* <span data-ttu-id="463dd-121">[Visual Studio 2017 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core platformlar arası geliştirme" iş yükü yüklendi.</span><span class="sxs-lookup"><span data-stu-id="463dd-121">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="463dd-122">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="463dd-122">Select the appropriate machine learning task</span></span>

<span data-ttu-id="463dd-123">Bir film listesi önermek veya ilgili ürünlerin bir listesini önermek gibi öneri sorunlarına yaklaşımak için birkaç yol vardır. Bu durumda, bir kullanıcının belirli bir filmi hangi derecelendirmeye sunduu (1-5) tahmin edecek ve bu filmin tanımlı eşikten yüksek (derecelendirme arttıkça, bir kullanıcının belirli bir filmi beğenme olasılığı yüksektir).</span><span class="sxs-lookup"><span data-stu-id="463dd-123">There are several ways to approach recommendation problems, such as recommending a list of movies or recommending a list of related products, but in this case you will predict what rating (1-5) a user will give to a particular movie and recommend that movie if it's higher than a defined threshold (the higher the rating, the higher the likelihood of a user liking a particular movie).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="463dd-124">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="463dd-124">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="463dd-125">Proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="463dd-125">Create a project</span></span>

1. <span data-ttu-id="463dd-126">Visual Studio 2017'yi açın.</span><span class="sxs-lookup"><span data-stu-id="463dd-126">Open Visual Studio 2017.</span></span> <span data-ttu-id="463dd-127">Menü çubuğundan **Dosya** > **Yeni** > **Proje** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="463dd-127">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="463dd-128">**Yeni proje** iletişim kutusunda,  **C# Visual** düğümünü ve ardından **.NET Core** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="463dd-128">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="463dd-129">Ardından **konsol uygulaması (.NET Core)** proje şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="463dd-129">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="463dd-130">**Ad** metin kutusuna "MovieRecommender" yazın ve **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="463dd-130">In the **Name** text box, type "MovieRecommender" and then select the **OK** button.</span></span>

2. <span data-ttu-id="463dd-131">Veri kümesini depolamak için projenizde *veri* adlı bir dizin oluşturun:</span><span class="sxs-lookup"><span data-stu-id="463dd-131">Create a directory named *Data* in your project to store the data set:</span></span>

    <span data-ttu-id="463dd-132">**Çözüm Gezgini**, projeye sağ tıklayın ve**Yeni klasör** **Ekle** > ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="463dd-132">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="463dd-133">"Data" yazın ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="463dd-133">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="463dd-134">**Microsoft.ml** ve **Microsoft. ml. öneren** NuGet paketlerini yükler:</span><span class="sxs-lookup"><span data-stu-id="463dd-134">Install the **Microsoft.ML** and **Microsoft.ML.Recommender** NuGet Packages:</span></span>

    <span data-ttu-id="463dd-135">**Çözüm Gezgini**, projeye sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="463dd-135">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="463dd-136">Paket kaynağı olarak "nuget.org" öğesini seçin, **Araştır** sekmesini seçin, **Microsoft.ml**için arama yapın, listeden paketi seçin ve sonra da **Install** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="463dd-136">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the package in the list, and select the **Install** button.</span></span> <span data-ttu-id="463dd-137">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="463dd-137">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="463dd-138">**Microsoft. ml. öneren**için bu adımları tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="463dd-138">Repeat these steps for **Microsoft.ML.Recommender**.</span></span>

4. <span data-ttu-id="463dd-139">*Program.cs* dosyanızın en `using` üstüne aşağıdaki deyimleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="463dd-139">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[UsingStatements](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#UsingStatements "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="463dd-140">Verilerinizi indirin</span><span class="sxs-lookup"><span data-stu-id="463dd-140">Download your data</span></span>

1. <span data-ttu-id="463dd-141">İki veri kümesini indirin ve daha önce oluşturduğunuz *veri* klasörüne kaydedin:</span><span class="sxs-lookup"><span data-stu-id="463dd-141">Download the two datasets and save them to the *Data* folder you previously created:</span></span>

   * <span data-ttu-id="463dd-142">[*Recommendation-Ratings-train. csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) ' ye sağ tıklayın ve "bağlantıyı (veya hedefi) farklı kaydet" i seçin.</span><span class="sxs-lookup"><span data-stu-id="463dd-142">Right click on [*recommendation-ratings-train.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) and select "Save Link (or Target) As..."</span></span>
   * <span data-ttu-id="463dd-143">[*Recommendation-Ratings-test. csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) ' ye sağ tıklayın ve "bağlantıyı (veya hedefi) farklı kaydet" i seçin.</span><span class="sxs-lookup"><span data-stu-id="463dd-143">Right click on [*recommendation-ratings-test.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="463dd-144">\*. Csv dosyalarını *veri* klasörüne kaydettiğinizden emin olun veya \*başka bir yere kaydettikten sonra. csv dosyalarını *veri* klasörüne taşıyın.</span><span class="sxs-lookup"><span data-stu-id="463dd-144">Make sure you either save the \*.csv files to the *Data* folder, or after you save it elsewhere, move the \*.csv files to the *Data* folder.</span></span>

2. <span data-ttu-id="463dd-145">Çözüm Gezgini, \*. csv dosyalarının her birine sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="463dd-145">In Solution Explorer, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="463dd-146">**Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="463dd-146">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

   ![VS 'de daha yeniyse kopyala](./media/movie-recommendation/copytoout.gif)

## <a name="load-your-data"></a><span data-ttu-id="463dd-148">Verilerinizi yükleme</span><span class="sxs-lookup"><span data-stu-id="463dd-148">Load your data</span></span>

<span data-ttu-id="463dd-149">ML.NET işlemindeki ilk adım, model eğitimi ve test verilerini hazırlamaktır ve yükler.</span><span class="sxs-lookup"><span data-stu-id="463dd-149">The first step in the ML.NET process is to prepare and load your model training and testing data.</span></span>

<span data-ttu-id="463dd-150">Öneri derecelendirme verileri `Train` , ve `Test` veri kümelerine ayrılır.</span><span class="sxs-lookup"><span data-stu-id="463dd-150">The recommendation ratings data is split into `Train` and `Test` datasets.</span></span> <span data-ttu-id="463dd-151">`Train` Veriler modelinize uyacak şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="463dd-151">The `Train` data is used to fit your model.</span></span> <span data-ttu-id="463dd-152">Veriler `Test` , eğitilen modelinizdeki tahminleri yapmak ve model performansını değerlendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="463dd-152">The `Test` data is used to make predictions with your trained model and evaluate model performance.</span></span> <span data-ttu-id="463dd-153">`Train` Ve`Test` verileri içeren bir 80/20 bölünmesi yaygındır.</span><span class="sxs-lookup"><span data-stu-id="463dd-153">It's common to have an 80/20 split with `Train` and `Test` data.</span></span>

<span data-ttu-id="463dd-154">\*. Csv dosyalarınızda verilerin önizlemesi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="463dd-154">Below is a preview of the data from your \*.csv files:</span></span>

![verilerin önizlemesi](./media/movie-recommendation/csv-dataset-preview.png)

<span data-ttu-id="463dd-156">\*. Csv dosyalarında dört sütun vardır:</span><span class="sxs-lookup"><span data-stu-id="463dd-156">In the \*.csv files, there are four columns:</span></span>

* `userId`
* `movieId`
* `rating`
* `timestamp`

<span data-ttu-id="463dd-157">Machine Learning 'de, bir tahmin yapmak için kullanılan sütunlara [Özellikler](../resources/glossary.md#feature)denir ve döndürülen tahmine sahip olan sütuna [etiket](../resources/glossary.md#label)denir.</span><span class="sxs-lookup"><span data-stu-id="463dd-157">In machine learning, the columns that are used to make a prediction are called [Features](../resources/glossary.md#feature), and the column with the returned prediction is called the [Label](../resources/glossary.md#label).</span></span>

<span data-ttu-id="463dd-158">Film derecelendirmelerini tahmin etmek istiyorsunuz, bu nedenle Derecelendirme sütunu `Label`.</span><span class="sxs-lookup"><span data-stu-id="463dd-158">You want to predict movie ratings, so the rating column is the `Label`.</span></span> <span data-ttu-id="463dd-159">Diğer üç `userId`sütun, `movieId`, ve `timestamp` `Features` , tahmin`Label`etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="463dd-159">The other three columns, `userId`, `movieId`, and `timestamp` are all `Features` used to predict the `Label`.</span></span>

| <span data-ttu-id="463dd-160">Özellikler</span><span class="sxs-lookup"><span data-stu-id="463dd-160">Features</span></span>      | <span data-ttu-id="463dd-161">Etiketle</span><span class="sxs-lookup"><span data-stu-id="463dd-161">Label</span></span>         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |
| `timestamp`     |               |

<span data-ttu-id="463dd-162">' İ `Features` `Label`tahmin etmek için ne kadar kullanıldığına karar verirsiniz.</span><span class="sxs-lookup"><span data-stu-id="463dd-162">It's up to you to decide which `Features` are used to predict the `Label`.</span></span> <span data-ttu-id="463dd-163">En iyi `Features`seçimi seçmenize yardımcı olmak Için [özellik permütasyon önem derecesi](../how-to-guides/determine-global-feature-importance-in-model.md) gibi yöntemleri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="463dd-163">You can also use methods like [Feature Permutation Importance](../how-to-guides/determine-global-feature-importance-in-model.md) to help with selecting the best `Features`.</span></span>

<span data-ttu-id="463dd-164">Bu durumda, zaman damgası bir kullanıcının belirli `timestamp` bir filmi nasıl `Feature` derecelendirmediğini etkilemediği ve bu nedenle daha doğru bir tahmin yapmaya katkıda bulunmamasının gerektiği için sütunu bir olarak kaldırmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="463dd-164">In this case, you should eliminate the `timestamp` column as a `Feature` because the timestamp does not really affect how a user rates a given movie and thus would not contribute to making a more accurate prediction:</span></span>

| <span data-ttu-id="463dd-165">Özellikler</span><span class="sxs-lookup"><span data-stu-id="463dd-165">Features</span></span>      | <span data-ttu-id="463dd-166">Etiketle</span><span class="sxs-lookup"><span data-stu-id="463dd-166">Label</span></span>         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |

<span data-ttu-id="463dd-167">Ardından, giriş sınıfı için veri yapınızı tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="463dd-167">Next you must define your data structure for the input class.</span></span>

<span data-ttu-id="463dd-168">Projenize yeni bir sınıf ekleyin:</span><span class="sxs-lookup"><span data-stu-id="463dd-168">Add a new class to your project:</span></span>

1. <span data-ttu-id="463dd-169">**Çözüm Gezgini**, projeye sağ tıklayın ve ardından **> yeni öğe Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="463dd-169">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="463dd-170">**Yeni öğe Ekle iletişim kutusunda** **sınıf** ' ı seçin ve **ad** alanını *MovieRatingData.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="463dd-170">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *MovieRatingData.cs*.</span></span> <span data-ttu-id="463dd-171">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="463dd-171">Then, select the **Add** button.</span></span>

<span data-ttu-id="463dd-172">*MovieRatingData.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="463dd-172">The *MovieRatingData.cs* file opens in the code editor.</span></span> <span data-ttu-id="463dd-173">Aşağıdaki `using` ifadeyi *MovieRatingData.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="463dd-173">Add the following `using` statement to the top of *MovieRatingData.cs*:</span></span>

```csharp
using Microsoft.ML.Data;
```

<span data-ttu-id="463dd-174">Var olan sınıf tanımını `MovieRating` kaldırarak ve *MovieRatingData.cs*içinde aşağıdaki kodu ekleyerek adlı bir sınıf oluşturun:</span><span class="sxs-lookup"><span data-stu-id="463dd-174">Create a class called `MovieRating` by removing the existing class definition and adding the following code in *MovieRatingData.cs*:</span></span>

[!code-csharp[MovieRatingClass](~/samples/machine-learning/tutorials/MovieRecommendation/MovieRatingData.cs#MovieRatingClass "Add the Movie Rating class")]

<span data-ttu-id="463dd-175">`MovieRating`bir giriş veri sınıfını belirtir.</span><span class="sxs-lookup"><span data-stu-id="463dd-175">`MovieRating` specifies an input data class.</span></span> <span data-ttu-id="463dd-176">[Loadcolumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) özniteliği, veri kümesindeki hangi sütunların (sütun dizinine göre) yükleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="463dd-176">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span> <span data-ttu-id="463dd-177">`userId` Ve `Label` sütunları (modelin tahmin`Label`edilmesine izin verilecek girişler) ve derecelendirme sütunu, tahmin ettiğiniz ' dir (modelin çıktısı). `Features` `movieId`</span><span class="sxs-lookup"><span data-stu-id="463dd-177">The `userId` and `movieId` columns are your `Features` (the inputs you will give the model to predict the `Label`), and the rating column is the `Label` that you will predict (the output of the model).</span></span>

<span data-ttu-id="463dd-178">`MovieRatingPrediction` *MovieRatingData.cs*içindeki `MovieRating` sınıftan sonra aşağıdaki kodu ekleyerek tahmin edilen sonuçları temsil eden başka bir sınıf oluşturun:</span><span class="sxs-lookup"><span data-stu-id="463dd-178">Create another class, `MovieRatingPrediction`, to represent predicted results by adding the following code after the `MovieRating` class in *MovieRatingData.cs*:</span></span>

[!code-csharp[PredictionClass](~/samples/machine-learning/tutorials/MovieRecommendation/MovieRatingData.cs#PredictionClass "Add the Movie Prediction Class")]

<span data-ttu-id="463dd-179">*Program.cs*' de, `Console.WriteLine("Hello World!")` öğesini içinde `Main()`aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="463dd-179">In *Program.cs*, replace the `Console.WriteLine("Hello World!")` with the following code inside `Main()`:</span></span>

[!code-csharp[MLContext](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#MLContext "Add MLContext")]

<span data-ttu-id="463dd-180">[Mlcontext sınıfı](xref:Microsoft.ML.MLContext) tüm ml.NET işlemleri için bir başlangıç noktasıdır ve başlatılıyor `mlContext` , model oluşturma iş akışı nesneleri genelinde paylaşılabilen yeni bir ml.net ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="463dd-180">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="463dd-181">Entity Framework, kavramsal `DBContext` olarak da benzerdir.</span><span class="sxs-lookup"><span data-stu-id="463dd-181">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="463dd-182">Sonra `Main()`, adlı `LoadData()`bir yöntem oluşturun:</span><span class="sxs-lookup"><span data-stu-id="463dd-182">After `Main()`, create a method called `LoadData()`:</span></span>

```csharp
public static (IDataView training, IDataView test) LoadData(MLContext mlContext)
{

}
```

> [!NOTE]
> <span data-ttu-id="463dd-183">Bu yöntem, aşağıdaki adımlarda bir return ifadesini eklemeene kadar bir hata verir.</span><span class="sxs-lookup"><span data-stu-id="463dd-183">This method will give you an error until you add a return statement in the following steps.</span></span>

<span data-ttu-id="463dd-184">Veri yolu değişkenlerinizi başlatın, \*. csv dosyalarından verileri yükleyin ve aşağıdaki kod `LoadData()`satırı olarak aşağıdakini ekleyerek `Train` nesne `Test` olarak `IDataView` ve verileri döndürün:</span><span class="sxs-lookup"><span data-stu-id="463dd-184">Initialize your data path variables, load the data from the \*.csv files, and return the `Train` and `Test` data as `IDataView` objects by adding the following as the next line of code in `LoadData()`:</span></span>

[!code-csharp[LoadData](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#LoadData "Load data from data paths")]

<span data-ttu-id="463dd-185">ML.NET içindeki veriler [ıdataview sınıfı](xref:Microsoft.ML.IDataView)olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="463dd-185">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="463dd-186">`IDataView`, tablo verilerini (sayısal ve metin) tanımlamaya yönelik esnek ve verimli bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="463dd-186">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="463dd-187">Veriler bir metin dosyasından veya gerçek zamanlı olarak (örneğin, SQL veritabanı veya günlük dosyaları) bir `IDataView` nesneye yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="463dd-187">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="463dd-188">[Loadfromtextfile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) , veri şemasını ve dosyadaki okumaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="463dd-188">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="463dd-189">Veri yolu değişkenlerini alır ve döndürür `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="463dd-189">It takes in the data path variables and returns an `IDataView`.</span></span> <span data-ttu-id="463dd-190">Bu durumda, `Test` ve `Train` dosyalarınız için yol sağlar ve hem metin dosyası üst bilgisini hem de (sütun adlarını düzgün bir şekilde kullanabilmesi için) virgül karakter veri ayırıcısını (varsayılan ayırıcı bir sekmedir) belirtin.</span><span class="sxs-lookup"><span data-stu-id="463dd-190">In this case, you provide the path for your `Test` and `Train` files and indicate both the text file header (so it can use the column names properly) and the comma character data separator (the default separator is a tab).</span></span>

<span data-ttu-id="463dd-191">Yöntemi `Main()` `Train` çağırmak veveverilerinidöndürmekiçinyöntemineaşağıdakikoduekleyin:`LoadData()` `Test`</span><span class="sxs-lookup"><span data-stu-id="463dd-191">Add the following code in the `Main()` method to call your `LoadData()` method and return the `Train` and `Test` data:</span></span>

[!code-csharp[LoadDataMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#LoadDataMain "Add LoadData method to Main")]

## <a name="build-and-train-your-model"></a><span data-ttu-id="463dd-192">Modelinizi derleyin ve eğitme</span><span class="sxs-lookup"><span data-stu-id="463dd-192">Build and train your model</span></span>

<span data-ttu-id="463dd-193">ML.NET ' de üç ana kavram vardır: [Veri](../resources/glossary.md#data), [dönüştürücüler](../resources/glossary.md#transformer)ve [estimators](../resources/glossary.md#estimator).</span><span class="sxs-lookup"><span data-stu-id="463dd-193">There are three major concepts in ML.NET: [Data](../resources/glossary.md#data), [Transformers](../resources/glossary.md#transformer), and [Estimators](../resources/glossary.md#estimator).</span></span>

<span data-ttu-id="463dd-194">Machine Learning eğitim algoritmaları, verileri belirli bir biçimde gerektirir.</span><span class="sxs-lookup"><span data-stu-id="463dd-194">Machine learning training algorithms require data in a certain format.</span></span> <span data-ttu-id="463dd-195">`Transformers`tablo verilerini uyumlu bir biçime dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="463dd-195">`Transformers` are used to transform tabular data to a compatible format.</span></span>

![Transformatör resmi](./media/movie-recommendation/transformer.png)

<span data-ttu-id="463dd-197">`Transformers` Oluşturarak`Estimators`ml.NET içinde oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="463dd-197">You create `Transformers` in ML.NET by creating `Estimators`.</span></span> <span data-ttu-id="463dd-198">`Estimators`verileri alın ve döndürün `Transformers`.</span><span class="sxs-lookup"><span data-stu-id="463dd-198">`Estimators` take in data and return `Transformers`.</span></span>

![tahmin aracı resmi](./media/movie-recommendation/estimator.png)

<span data-ttu-id="463dd-200">Modelinize eğitim için kullanacağınız öneri eğitimi algoritması bir `Estimator`örneğidir.</span><span class="sxs-lookup"><span data-stu-id="463dd-200">The recommendation training algorithm you will use for training your model is an example of an `Estimator`.</span></span>

<span data-ttu-id="463dd-201">Aşağıdaki adımlarla `Estimator` bir oluşturun:</span><span class="sxs-lookup"><span data-stu-id="463dd-201">Build an `Estimator` with the following steps:</span></span>

<span data-ttu-id="463dd-202">Aşağıdaki kodu kullanarak yönteminden hemen `LoadData()` sonra yönteminioluşturun:`BuildAndTrainModel()`</span><span class="sxs-lookup"><span data-stu-id="463dd-202">Create the `BuildAndTrainModel()` method, just after the `LoadData()` method, using the following code:</span></span>

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView trainingDataView)
{

}
```

> [!NOTE]
> <span data-ttu-id="463dd-203">Bu yöntem, aşağıdaki adımlarda bir return ifadesini eklemeene kadar bir hata verir.</span><span class="sxs-lookup"><span data-stu-id="463dd-203">This method will give you an error until you add a return statement in the following steps.</span></span>

<span data-ttu-id="463dd-204">Aşağıdaki kodu öğesine `BuildAndTrainModel()`ekleyerek veri dönüşümlerini tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="463dd-204">Define the data transformations by adding the following code to `BuildAndTrainModel()`:</span></span>

[!code-csharp[DataTransformations](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#DataTransformations "Define data transformations")]

<span data-ttu-id="463dd-205">`movieId` [](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) `userId` `Feature` Kullanıcılar ve film başlıklarını gerçek değerlerle değil, her bir sayısal anahtar türü sütununa dönüştürmek için mapvaluetokey () yöntemini kullanırsınız (bir biçim kabul edilir `userId` `movieId` öneri algoritmalarına göre) ve bunları yeni veri kümesi sütunları olarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="463dd-205">Since `userId` and `movieId` represent users and movie titles, not real values, you use the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method to transform each `userId` and each `movieId` into a numeric key type `Feature` column (a format accepted by recommendation algorithms) and add them as new dataset columns:</span></span>

| <span data-ttu-id="463dd-206">UserID</span><span class="sxs-lookup"><span data-stu-id="463dd-206">userId</span></span> | <span data-ttu-id="463dd-207">Movieıd</span><span class="sxs-lookup"><span data-stu-id="463dd-207">movieId</span></span> | <span data-ttu-id="463dd-208">Etiketle</span><span class="sxs-lookup"><span data-stu-id="463dd-208">Label</span></span> | <span data-ttu-id="463dd-209">Userıdencoded</span><span class="sxs-lookup"><span data-stu-id="463dd-209">userIdEncoded</span></span> | <span data-ttu-id="463dd-210">Movieıdencoded</span><span class="sxs-lookup"><span data-stu-id="463dd-210">movieIdEncoded</span></span> |
| ------------- |:-------------:| -----:|-----:|-----:|
| <span data-ttu-id="463dd-211">1\.</span><span class="sxs-lookup"><span data-stu-id="463dd-211">1</span></span> | <span data-ttu-id="463dd-212">1\.</span><span class="sxs-lookup"><span data-stu-id="463dd-212">1</span></span> | <span data-ttu-id="463dd-213">4</span><span class="sxs-lookup"><span data-stu-id="463dd-213">4</span></span> | <span data-ttu-id="463dd-214">userKey1</span><span class="sxs-lookup"><span data-stu-id="463dd-214">userKey1</span></span> | <span data-ttu-id="463dd-215">movieKey1</span><span class="sxs-lookup"><span data-stu-id="463dd-215">movieKey1</span></span> |
| <span data-ttu-id="463dd-216">1\.</span><span class="sxs-lookup"><span data-stu-id="463dd-216">1</span></span> | <span data-ttu-id="463dd-217">3</span><span class="sxs-lookup"><span data-stu-id="463dd-217">3</span></span> | <span data-ttu-id="463dd-218">4</span><span class="sxs-lookup"><span data-stu-id="463dd-218">4</span></span> | <span data-ttu-id="463dd-219">userKey1</span><span class="sxs-lookup"><span data-stu-id="463dd-219">userKey1</span></span> | <span data-ttu-id="463dd-220">movieKey2</span><span class="sxs-lookup"><span data-stu-id="463dd-220">movieKey2</span></span> |
| <span data-ttu-id="463dd-221">1\.</span><span class="sxs-lookup"><span data-stu-id="463dd-221">1</span></span> | <span data-ttu-id="463dd-222">6</span><span class="sxs-lookup"><span data-stu-id="463dd-222">6</span></span> | <span data-ttu-id="463dd-223">4</span><span class="sxs-lookup"><span data-stu-id="463dd-223">4</span></span> | <span data-ttu-id="463dd-224">userKey1</span><span class="sxs-lookup"><span data-stu-id="463dd-224">userKey1</span></span> | <span data-ttu-id="463dd-225">movieKey3</span><span class="sxs-lookup"><span data-stu-id="463dd-225">movieKey3</span></span> |

<span data-ttu-id="463dd-226">Machine Learning algoritmasını seçin ve aşağıdaki kod `BuildAndTrainModel()`satırı olarak aşağıdakini ekleyerek veri dönüştürme tanımlarına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="463dd-226">Choose the machine learning algorithm and append it to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[AddAlgorithm](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#AddAlgorithm "Add the training algorithm with options")]

<span data-ttu-id="463dd-227">[Matrixfactorizationtrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) , öneri eğitim algoritmanız.</span><span class="sxs-lookup"><span data-stu-id="463dd-227">The [MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) is your recommendation training algorithm.</span></span>  <span data-ttu-id="463dd-228">[Matris](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) , kullanıcıların geçmişte ürünleri derecelendirirken, bu öğreticideki veri kümeleri için büyük/küçük bir yaklaşım olan genel bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="463dd-228">[Matrix Factorization](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) is a common approach to recommendation when you have data on how users have rated products in the past, which is the case for the datasets in this tutorial.</span></span> <span data-ttu-id="463dd-229">Farklı verilere sahip olduğunuzda kullanabileceğiniz başka öneri algoritmaları vardır (daha fazla bilgi için aşağıdaki [diğer öneri algoritmaları](#other-recommendation-algorithms) bölümüne bakın).</span><span class="sxs-lookup"><span data-stu-id="463dd-229">There are other recommendation algorithms for when you have different data available (see the [Other recommendation algorithms](#other-recommendation-algorithms) section below to learn more).</span></span>

<span data-ttu-id="463dd-230">Bu durumda `Matrix Factorization` , algoritma "işbirliğine dayalı filtreleme" adlı bir yöntem kullanır. Bu, Kullanıcı 1 ' in belirli bir sorun üzerinde Kullanıcı 2 ' de aynı görüşe sahip olduğunu varsaydığı, 1. Kullanıcı farklı bir sorun hakkında Kullanıcı 2 ' yi aynı şekilde hissetmesinin daha olasıdır.</span><span class="sxs-lookup"><span data-stu-id="463dd-230">In this case, the `Matrix Factorization` algorithm uses a method called "collaborative filtering", which assumes that if User 1 has the same opinion as User 2 on a certain issue, then User 1 is more likely to feel the same way as User 2 about a different issue.</span></span>

<span data-ttu-id="463dd-231">Örneğin, Kullanıcı 1 ve Kullanıcı 2 filmleri benzer şekilde kullanıyorsanız, 1. Kullanıcı 2 ' nin, Kullanıcı 1 ' in izlenen ve yüksek oranda derecelendirdikleri bir filmin keyfini çıkarmak daha yüksektir:</span><span class="sxs-lookup"><span data-stu-id="463dd-231">For instance, if User 1 and User 2 rate movies similarly, then User 2 is more likely to enjoy a movie that User 1 has watched and rated highly:</span></span>

| | `Incredibles 2 (2018)` | `The Avengers (2012)` | `Guardians of the Galaxy (2014)` |
| -------------:|-------------:| -----:|-----:|
| <span data-ttu-id="463dd-232">Kullanıcı 1</span><span class="sxs-lookup"><span data-stu-id="463dd-232">User 1</span></span> | <span data-ttu-id="463dd-233">İzlenen ve beğenilen film</span><span class="sxs-lookup"><span data-stu-id="463dd-233">Watched and liked movie</span></span> | <span data-ttu-id="463dd-234">İzlenen ve beğenilen film</span><span class="sxs-lookup"><span data-stu-id="463dd-234">Watched and liked movie</span></span> | <span data-ttu-id="463dd-235">İzlenen ve beğenilen film</span><span class="sxs-lookup"><span data-stu-id="463dd-235">Watched and liked movie</span></span> |
| <span data-ttu-id="463dd-236">Kullanıcı 2</span><span class="sxs-lookup"><span data-stu-id="463dd-236">User 2</span></span> | <span data-ttu-id="463dd-237">İzlenen ve beğenilen film</span><span class="sxs-lookup"><span data-stu-id="463dd-237">Watched and liked movie</span></span> | <span data-ttu-id="463dd-238">İzlenen ve beğenilen film</span><span class="sxs-lookup"><span data-stu-id="463dd-238">Watched and liked movie</span></span> | <span data-ttu-id="463dd-239">İzleniyor--film öner</span><span class="sxs-lookup"><span data-stu-id="463dd-239">Has not watched -- RECOMMEND movie</span></span> |

<span data-ttu-id="463dd-240">Eğitimci, `Matrix Factorization` aşağıdaki [algoritma hiper parametreleri](#algorithm-hyperparameters) bölümünde hakkında daha fazla bilgi edinmek için çeşitli [seçeneklere](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options)sahiptir.</span><span class="sxs-lookup"><span data-stu-id="463dd-240">The `Matrix Factorization` trainer has several [Options](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), which you can read more about in the [Algorithm hyperparameters](#algorithm-hyperparameters) section below.</span></span>

<span data-ttu-id="463dd-241">Yöntemine bir sonraki kod satırı `Train` olarak aşağıdakileri ekleyerek modeli verilere sığdırın ve eğitilen modeli döndürün: `BuildAndTrainModel()`</span><span class="sxs-lookup"><span data-stu-id="463dd-241">Fit the model to the `Train` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[FitModel](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#FitModel "Call the Fit method and return back the trained model")]

<span data-ttu-id="463dd-242">[Fit ()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) yöntemi, modelinizi belirtilen eğitim veri kümesiyle eğliyor.</span><span class="sxs-lookup"><span data-stu-id="463dd-242">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model with the provided training dataset.</span></span> <span data-ttu-id="463dd-243">Teknik olarak, verileri dönüştürerek `Estimator` ve eğitimi uygulayarak tanımları yürütür ve bir `Transformer`olan eğitilen modeli geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="463dd-243">Technically, it executes the `Estimator` definitions by transforming the data and applying the training, and it returns back the trained model, which is a `Transformer`.</span></span>

<span data-ttu-id="463dd-244">Yönteminizi çağırmak ve eğitilen modeli döndürmek için `Main()` yöntemine bir sonraki kod satırı olarak aşağıdakini ekleyin: `BuildAndTrainModel()`</span><span class="sxs-lookup"><span data-stu-id="463dd-244">Add the following as the next line of code in the `Main()` method to call your `BuildAndTrainModel()` method and return the trained model:</span></span>

[!code-csharp[BuildTrainModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#BuildTrainModelMain "Add BuildAndTrainModel method in Main")]

## <a name="evaluate-your-model"></a><span data-ttu-id="463dd-245">Modelinizi değerlendirin</span><span class="sxs-lookup"><span data-stu-id="463dd-245">Evaluate your model</span></span>

<span data-ttu-id="463dd-246">Modelinizi eğittikten sonra, modelinizin nasıl çalıştığını değerlendirmek için test verilerinizi kullanın.</span><span class="sxs-lookup"><span data-stu-id="463dd-246">Once you have trained your model, use your test data to evaluate how your model is performing.</span></span>

<span data-ttu-id="463dd-247">Aşağıdaki kodu kullanarak yönteminden hemen `BuildAndTrainModel()` sonra yönteminioluşturun:`EvaluateModel()`</span><span class="sxs-lookup"><span data-stu-id="463dd-247">Create the `EvaluateModel()` method, just after the `BuildAndTrainModel()` method, using the following code:</span></span>

```csharp
public static void EvaluateModel(MLContext mlContext, IDataView testDataView, ITransformer model)
{

}
```

<span data-ttu-id="463dd-248">Aşağıdaki kodu öğesine `EvaluateModel()`ekleyerek verileridönüştürün:`Test`</span><span class="sxs-lookup"><span data-stu-id="463dd-248">Transform the `Test` data by adding the following code to `EvaluateModel()`:</span></span>

[!code-csharp[Transform](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#Transform "Transform the test data")]

<span data-ttu-id="463dd-249">[Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemi, test veri kümesinin birden çok sağlanmış giriş satırları için tahminleri yapar.</span><span class="sxs-lookup"><span data-stu-id="463dd-249">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for multiple provided input rows of a test dataset.</span></span>

<span data-ttu-id="463dd-250">`EvaluateModel()` Yöntemine aşağıdaki kod satırı olarak aşağıdakini ekleyerek modeli değerlendirin:</span><span class="sxs-lookup"><span data-stu-id="463dd-250">Evaluate the model by adding the following as the next line of code in the `EvaluateModel()` method:</span></span>

[!code-csharp[Evaluate](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#Evaluate "Evaluate the model using predictions from the test data")]

<span data-ttu-id="463dd-251">Tahmin kümesine sahip olduktan sonra, tahmin edilen değerleri test veri kümesindeki gerçek `Labels` ile karşılaştıran ve modelin nasıl çalıştığı hakkında ölçümler döndüren [değerlendir ()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) yöntemi, modeli değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="463dd-251">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns metrics on how the model is performing.</span></span>

<span data-ttu-id="463dd-252">Aşağıdaki kod `EvaluateModel()` satırını yöntemine ekleyerek değerlendirme ölçümlerinizi konsola yazdırın:</span><span class="sxs-lookup"><span data-stu-id="463dd-252">Print your evaluation metrics to the console by adding the following as the next line of code in the `EvaluateModel()` method:</span></span>

[!code-csharp[PrintMetrics](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PrintMetrics "Print the evaluation metrics")]

<span data-ttu-id="463dd-253">Yönteminizi çağırmak için `Main()` yöntemi içindeki sonraki kod satırı olarak aşağıdakini ekleyin: `EvaluateModel()`</span><span class="sxs-lookup"><span data-stu-id="463dd-253">Add the following as the next line of code in the `Main()` method to call your `EvaluateModel()` method:</span></span>

[!code-csharp[EvaluateModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#EvaluateModelMain "Add EvaluateModel method in Main")]

<span data-ttu-id="463dd-254">Şu ana kadar çıkış aşağıdaki metne benzer görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="463dd-254">The output so far should look similar to the following text:</span></span>

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

<span data-ttu-id="463dd-255">Bu çıktıda 20 yineleme vardır.</span><span class="sxs-lookup"><span data-stu-id="463dd-255">In this output, there are 20 iterations.</span></span> <span data-ttu-id="463dd-256">Her yinelemede, hata ölçüsü azalır ve 0 ' a yaklaştırır.</span><span class="sxs-lookup"><span data-stu-id="463dd-256">In each iteration, the measure of error decreases and converges closer and closer to 0.</span></span>

<span data-ttu-id="463dd-257">`root of mean squared error` (RMS veya rmo), model tahmin edilen değerler ve test veri kümesi gözlenen değerleri arasındaki farkları ölçmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="463dd-257">The `root of mean squared error` (RMS or RMSE) is used to measure the differences between the model predicted values and the test dataset observed values.</span></span> <span data-ttu-id="463dd-258">Teknik olarak, hataların karelerinin ortalamasının karekökünü temel alır.</span><span class="sxs-lookup"><span data-stu-id="463dd-258">Technically it's the square root of the average of the squares of the errors.</span></span> <span data-ttu-id="463dd-259">Bunun ne kadar küçük olması, modelin ne kadar iyi olduğu.</span><span class="sxs-lookup"><span data-stu-id="463dd-259">The lower it is, the better the model is.</span></span>

<span data-ttu-id="463dd-260">`R Squared`verilerin bir modele ne kadar uygun olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="463dd-260">`R Squared` indicates how well data fits a model.</span></span> <span data-ttu-id="463dd-261">0 ile 1 arasında aralıklar.</span><span class="sxs-lookup"><span data-stu-id="463dd-261">Ranges from 0 to 1.</span></span> <span data-ttu-id="463dd-262">0 değeri, verilerin rastgele olması veya başka türlü modele sığamayacak olması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="463dd-262">A value of 0 means that the data is random or otherwise can't be fit to the model.</span></span> <span data-ttu-id="463dd-263">1 değeri, modelin verilerle tam olarak eşleştiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="463dd-263">A value of 1 means that the model exactly matches the data.</span></span> <span data-ttu-id="463dd-264">Puanınızın `R Squared` mümkün olduğunca 1 ' e yakın olmasını istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="463dd-264">You want your `R Squared` score to be as close to 1 as possible.</span></span>

<span data-ttu-id="463dd-265">Başarılı modellerin oluşturulması, yinelemeli bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="463dd-265">Building successful models is an iterative process.</span></span> <span data-ttu-id="463dd-266">Öğretici, hızlı model eğitimi sağlamak için küçük veri kümeleri kullandığından, bu modelin ilk daha düşük kalitesi vardır.</span><span class="sxs-lookup"><span data-stu-id="463dd-266">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="463dd-267">Model kalitede memnun kalmıyorsanız, daha büyük eğitim veri kümeleri sağlayarak veya her algoritma için farklı Hyper-parametreleri ile farklı eğitim algoritmaları seçerek bunu geliştirmeyi deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="463dd-267">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different hyper-parameters for each algorithm.</span></span> <span data-ttu-id="463dd-268">Daha fazla bilgi için aşağıdaki [modelinizi geliştirme](#improve-your-model) bölümünü inceleyin.</span><span class="sxs-lookup"><span data-stu-id="463dd-268">For more information, check out the [Improve your model](#improve-your-model) section below.</span></span>

## <a name="use-your-model"></a><span data-ttu-id="463dd-269">Modelinizi kullanın</span><span class="sxs-lookup"><span data-stu-id="463dd-269">Use your model</span></span>

<span data-ttu-id="463dd-270">Artık yeni verilerde öngörülere sahip olmak için eğitilen modeli kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="463dd-270">Now you can use your trained model to make predictions on new data.</span></span>

<span data-ttu-id="463dd-271">Aşağıdaki kodu kullanarak yönteminden hemen `EvaluateModel()` sonra yönteminioluşturun:`UseModelForSinglePrediction()`</span><span class="sxs-lookup"><span data-stu-id="463dd-271">Create the `UseModelForSinglePrediction()` method, just after the `EvaluateModel()` method, using the following code:</span></span>

```csharp
public static void UseModelForSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="463dd-272">Aşağıdaki kodu öğesine `UseModelForSinglePrediction()`ekleyerek derecelendirmeyi tahmin etmekiçinöğesinikullanın:`PredictionEngine`</span><span class="sxs-lookup"><span data-stu-id="463dd-272">Use the `PredictionEngine` to predict the rating by adding the following code to `UseModelForSinglePrediction()`:</span></span>

[!code-csharp[PredictionEngine](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PredictionEngine "Create Prediction Engine")]

<span data-ttu-id="463dd-273">[PredictionEngine sınıfı](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneğini geçirmenize ve sonra bu tek veri örneğinde tahmin gerçekleştirmenize olanak tanıyan, KULLANıŞLı bir API 'dir.</span><span class="sxs-lookup"><span data-stu-id="463dd-273">The [PredictionEngine class](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass a single instance of data and then perform a prediction on this single instance of data.</span></span>

<span data-ttu-id="463dd-274">Aşağıdaki kod `MovieRating` `testInput` satırlarını yöntemineekleyerek,çağrılanbirörneğioluşturunvebunutahminaltyapısınageçirin:`UseModelForSinglePrediction()`</span><span class="sxs-lookup"><span data-stu-id="463dd-274">Create an instance of `MovieRating` called `testInput` and pass it to the Prediction Engine by adding the following as the next lines of code in the `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[MakeSinglePrediction](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#MakeSinglePrediction "Make a single prediction with the Prediction Engine")]

<span data-ttu-id="463dd-275">PREDICT [()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi, tek bir veri sütunu üzerinde bir tahmin yapar.</span><span class="sxs-lookup"><span data-stu-id="463dd-275">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single column of data.</span></span>

<span data-ttu-id="463dd-276">Daha sonra `Score`, filmi Kullanıcı 6 ' ya movieıd 10 ile önermek isteyip istemediğinizi öğrenmek için veya tahmin edilen derecelendirmeyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="463dd-276">You can then use the `Score`, or the predicted rating, to determine whether you want to recommend the movie with movieId 10 to user 6.</span></span> <span data-ttu-id="463dd-277">Ne kadar yüksekse `Score`, bir kullanıcının belirli bir filmi beğenme olasılığı yüksektir.</span><span class="sxs-lookup"><span data-stu-id="463dd-277">The higher the `Score`, the higher the likelihood of a user liking a particular movie.</span></span> <span data-ttu-id="463dd-278">Bu durumda, > 3,5 ' nin tahmin edilen derecelendirmesine sahip filmler önertiğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="463dd-278">In this case, let’s say that you recommend movies with a predicted rating of > 3.5.</span></span>

<span data-ttu-id="463dd-279">Sonuçları yazdırmak için aşağıdaki kod `UseModelForSinglePrediction()` satırları yöntemine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="463dd-279">To print the results, add the following as the next lines of code in the `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[PrintResults](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PrintResults "Print the recommendation prediction results")]

<span data-ttu-id="463dd-280">Yönteminizi çağırmak için `Main()` yöntemi içindeki sonraki kod satırı olarak aşağıdakini ekleyin: `UseModelForSinglePrediction()`</span><span class="sxs-lookup"><span data-stu-id="463dd-280">Add the following as the next line of code in the `Main()` method to call your `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[UseModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#UseModelMain "Add UseModelForSinglePrediction method in Main")]

<span data-ttu-id="463dd-281">Bu yöntemin çıktısı aşağıdaki metne benzer görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="463dd-281">The output of this method should look similar to the following text:</span></span>

```console
=============== Making a prediction ===============
Movie 10 is recommended for user 6
```

### <a name="save-your-model"></a><span data-ttu-id="463dd-282">Modelinizi kaydetme</span><span class="sxs-lookup"><span data-stu-id="463dd-282">Save your model</span></span>

<span data-ttu-id="463dd-283">Son Kullanıcı uygulamalarında tahmine dayalı hale getirmek üzere modelinizi kullanmak için önce modeli kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="463dd-283">To use your model to make predictions in end-user applications, you must first save the model.</span></span>

<span data-ttu-id="463dd-284">Aşağıdaki kodu kullanarak yönteminden hemen `UseModelForSinglePrediction()` sonra yönteminioluşturun:`SaveModel()`</span><span class="sxs-lookup"><span data-stu-id="463dd-284">Create the `SaveModel()` method, just after the `UseModelForSinglePrediction()` method, using the following code:</span></span>

```csharp
public static void SaveModel(MLContext mlContext, DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

<span data-ttu-id="463dd-285">Aşağıdaki kodu `SaveModel()` yöntemine ekleyerek eğitilen modelinizi kaydedin:</span><span class="sxs-lookup"><span data-stu-id="463dd-285">Save your trained model by adding the following code in the `SaveModel()` method:</span></span>

[!code-csharp[SaveModel](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#SaveModel "Save the model to a zip file")]

<span data-ttu-id="463dd-286">Bu yöntem, eğitilen modelinizi, daha sonra tahmine dayalı hale getirmek için diğer .NET uygulamalarında kullanılabilecek bir. zip dosyasına ("veri" klasöründe) kaydeder.</span><span class="sxs-lookup"><span data-stu-id="463dd-286">This method saves your trained model to a .zip file (in the "Data" folder), which can then be used in other .NET applications to make predictions.</span></span>

<span data-ttu-id="463dd-287">Yönteminizi çağırmak için `Main()` yöntemi içindeki sonraki kod satırı olarak aşağıdakini ekleyin: `SaveModel()`</span><span class="sxs-lookup"><span data-stu-id="463dd-287">Add the following as the next line of code in the `Main()` method to call your `SaveModel()` method:</span></span>

[!code-csharp[SaveModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#SaveModelMain "Create SaveModel method in Main")]

### <a name="use-your-saved-model"></a><span data-ttu-id="463dd-288">Kayıtlı modelinizi kullanın</span><span class="sxs-lookup"><span data-stu-id="463dd-288">Use your saved model</span></span>

<span data-ttu-id="463dd-289">Eğitilen modelinizi kaydettikten sonra modeli farklı ortamlarda kullanabilirsiniz (uygulamalarda eğitilen bir makine öğrenimi modelinin nasıl yapılacağını öğrenmek için bkz. ["nasıl yapılır Kılavuzu"](../how-to-guides/consuming-model-ml-net.md) ).</span><span class="sxs-lookup"><span data-stu-id="463dd-289">Once you have saved your trained model, you can consume the model in different environments (see the ["How-to guide"](../how-to-guides/consuming-model-ml-net.md) to learn how to operationalize a trained machine learning model in apps).</span></span>

## <a name="results"></a><span data-ttu-id="463dd-290">Sonuçlar</span><span class="sxs-lookup"><span data-stu-id="463dd-290">Results</span></span>

<span data-ttu-id="463dd-291">Yukarıdaki adımları tamamladıktan sonra konsol uygulamanızı çalıştırın (CTRL + F5).</span><span class="sxs-lookup"><span data-stu-id="463dd-291">After following the steps above, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="463dd-292">Yukarıdaki tek bir tahmine ait sonuçlarınız aşağıdakine benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="463dd-292">Your results from the single prediction above should be similar to the following.</span></span> <span data-ttu-id="463dd-293">Uyarıları veya işlem iletilerini görebilirsiniz, ancak bu iletiler netme için aşağıdaki sonuçlardan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="463dd-293">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="463dd-294">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="463dd-294">Congratulations!</span></span> <span data-ttu-id="463dd-295">Artık film öneren bir makine öğrenimi modelini başarıyla oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="463dd-295">You've now successfully built a machine learning model for recommending movies.</span></span> <span data-ttu-id="463dd-296">Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="463dd-296">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repository.</span></span>

## <a name="improve-your-model"></a><span data-ttu-id="463dd-297">Modelinizi geliştirme</span><span class="sxs-lookup"><span data-stu-id="463dd-297">Improve your model</span></span>

<span data-ttu-id="463dd-298">Daha doğru öngörülere ulaşmak için modelinizin performansını iyileştirebilmeniz için birkaç yol vardır.</span><span class="sxs-lookup"><span data-stu-id="463dd-298">There are several ways that you can improve the performance of your model so that you can get more accurate predictions.</span></span>

### <a name="data"></a><span data-ttu-id="463dd-299">Veri</span><span class="sxs-lookup"><span data-stu-id="463dd-299">Data</span></span>

<span data-ttu-id="463dd-300">Her Kullanıcı ve film kimliği için yeterli sayıda örnek içeren eğitim verileri eklemek, öneri modelinin kalitesini artırmaya yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="463dd-300">Adding more training data that has enough samples for each user and movie id can help improve the quality of the recommendation model.</span></span>

<span data-ttu-id="463dd-301">[Çapraz doğrulama](../how-to-guides/train-cross-validation-ml-net.md) , verileri rastgele kümeler halinde ayırır (Bu öğreticide yaptığınız gibi veri kümesinden test verilerinin ayıklanmasının yerine) ve bazı gruplardan verileri test verileri olarak eğitme ve gruplardan bazılarını alan bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="463dd-301">[Cross validation](../how-to-guides/train-cross-validation-ml-net.md) is a technique for evaluating models that randomly splits up data into subsets (instead of extracting out test data from the dataset like you did in this tutorial) and takes some of the groups as train data and some of the groups as test data.</span></span> <span data-ttu-id="463dd-302">Bu yöntem, model kalitesi açısından bir eğitme testi ayırma yapmayı gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="463dd-302">This method outperforms making a train-test split in terms of model quality.</span></span>

### <a name="features"></a><span data-ttu-id="463dd-303">Özellikler</span><span class="sxs-lookup"><span data-stu-id="463dd-303">Features</span></span>

<span data-ttu-id="463dd-304">Bu öğreticide, yalnızca veri kümesi tarafından sunulan `Features` üç`user id`( `movie id`,, `rating`ve) kullanın.</span><span class="sxs-lookup"><span data-stu-id="463dd-304">In this tutorial, you only use the three `Features` (`user id`, `movie id`, and `rating`) that are provided by the dataset.</span></span>

<span data-ttu-id="463dd-305">Bu iyi bir başlangıç olsa da, gerçekte veri kümesine dahil edildiklerinde başka öznitelikler veya `Features` (örneğin, Age, cinsiyeti, coğrafi konum vb.) eklemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="463dd-305">While this is a good start, in reality you might want to add other attributes or `Features` (for example, age, gender, geo-location, etc.) if they are included in the dataset.</span></span> <span data-ttu-id="463dd-306">Daha fazla ilgisi `Features` eklemek, öneri modelinizin performansını artırmaya yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="463dd-306">Adding more relevant `Features` can help improve the performance of your recommendation model.</span></span>

<span data-ttu-id="463dd-307">Makinenizin öğrenimi göreviniz için en `Features` uygun olabilecek bir işlem olduğundan emin değilseniz, ml.net 'in en iyi şekilde bulmasını sağlamak için sunduğu özellik katkı hesaplamasını (FCC) ve [özellik](../how-to-guides/determine-global-feature-importance-in-model.md)bilimi önem derecesini de kullanabilirsiniz. `Features`etkili.</span><span class="sxs-lookup"><span data-stu-id="463dd-307">If you are unsure about which `Features` might be the most relevant for your machine learning task, you can also make use of Feature Contribution Calculation (FCC) and [Feature Permutation Importance](../how-to-guides/determine-global-feature-importance-in-model.md), which ML.NET provides to discover the most influential `Features`.</span></span>

### <a name="algorithm-hyperparameters"></a><span data-ttu-id="463dd-308">Algoritma hiper parametreleri</span><span class="sxs-lookup"><span data-stu-id="463dd-308">Algorithm hyperparameters</span></span>

<span data-ttu-id="463dd-309">ML.NET, iyi varsayılan eğitim algoritmaları sağlarken, algoritmanın [hiper parametrelerini](../resources/glossary.md#hyperparameter)değiştirerek performansı daha ayrıntılı bir şekilde ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="463dd-309">While ML.NET provides good default training algorithms, you can further fine-tune performance by changing the algorithm's [hyperparameters](../resources/glossary.md#hyperparameter).</span></span>

<span data-ttu-id="463dd-310">İçin `Matrix Factorization`, numberofıterlationve [yaklaşık](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) olarak, daha [](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) iyi sonuçlar verir.</span><span class="sxs-lookup"><span data-stu-id="463dd-310">For `Matrix Factorization`, you can experiment with hyperparameters such as [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) and [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) to see if that gives you better results.</span></span>

<span data-ttu-id="463dd-311">Örneğin, bu öğreticide algoritma seçenekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="463dd-311">For instance, in this tutorial the algorithm options are:</span></span>

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

### <a name="other-recommendation-algorithms"></a><span data-ttu-id="463dd-312">Diğer öneri algoritmaları</span><span class="sxs-lookup"><span data-stu-id="463dd-312">Other Recommendation Algorithms</span></span>

<span data-ttu-id="463dd-313">Ortak filtreleme ile matris ayırma algoritması, film önerileri gerçekleştirmeye yönelik yalnızca bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="463dd-313">The matrix factorization algorithm with collaborative filtering is only one approach for performing movie recommendations.</span></span> <span data-ttu-id="463dd-314">Çoğu durumda, derecelendirme verileri kullanılabilir olmayabilir ve yalnızca film geçmişi kullanıcılardan bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="463dd-314">In many cases, you may not have the ratings data available and only have movie history available from users.</span></span> <span data-ttu-id="463dd-315">Diğer durumlarda, yalnızca kullanıcının derecelendirme verilerinden daha fazlasına sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="463dd-315">In other cases, you may have more than just the user’s rating data.</span></span>

| <span data-ttu-id="463dd-316">Algoritmalar</span><span class="sxs-lookup"><span data-stu-id="463dd-316">Algorithm</span></span>       | <span data-ttu-id="463dd-317">Senaryo</span><span class="sxs-lookup"><span data-stu-id="463dd-317">Scenario</span></span>           | <span data-ttu-id="463dd-318">Örnek</span><span class="sxs-lookup"><span data-stu-id="463dd-318">Sample</span></span>  |
| ------------- |:-------------:| -----:|
| <span data-ttu-id="463dd-319">Bir sınıf matrisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="463dd-319">One Class Matrix Factorization</span></span> | <span data-ttu-id="463dd-320">Yalnızca Kullanıcı kimliği ve Movieıd olduğunda bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="463dd-320">Use this when you only have userId and movieId.</span></span> <span data-ttu-id="463dd-321">Bu öneri stili, ortak satın alma senaryosuna veya genellikle birlikte satın alınan ürünlere dayalıdır. Bu, müşterilerin kendi satın alma siparişi geçmişine göre bir ürün kümesi önermesini önermeyeceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="463dd-321">This style of recommendation is based upon the co-purchase scenario, or products frequently bought together, which means it will recommend to customers a set of products based upon their own purchase order history.</span></span> | [<span data-ttu-id="463dd-322">> deneyin</span><span class="sxs-lookup"><span data-stu-id="463dd-322">>Try it out</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/MatrixFactorization_ProductRecommendation) |
| <span data-ttu-id="463dd-323">Alan duyarlı bir ayırma makinesi</span><span class="sxs-lookup"><span data-stu-id="463dd-323">Field Aware Factorization Machines</span></span> | <span data-ttu-id="463dd-324">Kullanıcı kimliği, ProductID ve derecelendirmeden daha fazla özelliğe sahip olduğunuzda (ürün açıklaması veya ürün fiyatı gibi) öneri sağlamak için bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="463dd-324">Use this to make recommendations when you have more Features beyond userId, productId, and rating (such as product description or product price).</span></span> <span data-ttu-id="463dd-325">Bu yöntem ayrıca birlikte çalışan bir filtreleme yaklaşımı kullanır.</span><span class="sxs-lookup"><span data-stu-id="463dd-325">This method also uses a collaborative filtering approach.</span></span> | [<span data-ttu-id="463dd-326">> deneyin</span><span class="sxs-lookup"><span data-stu-id="463dd-326">>Try it out</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/Recommendation-MovieRecommender) |

### <a name="new-user-scenario"></a><span data-ttu-id="463dd-327">Yeni Kullanıcı senaryosu</span><span class="sxs-lookup"><span data-stu-id="463dd-327">New user scenario</span></span>

<span data-ttu-id="463dd-328">İşbirliğine dayalı filtrelemede yaygın olarak karşılaşılan bir sorun, yeni bir kullanıcıya, ıntreler eklemek için önceki verileri olmayan yeni bir kullanıcı olduğunda oluşan soğuk başlatma sorunudur.</span><span class="sxs-lookup"><span data-stu-id="463dd-328">One common problem in collaborative filtering is the cold start problem, which is when you have a new user with no previous data to draw inferences from.</span></span> <span data-ttu-id="463dd-329">Bu sorun genellikle yeni kullanıcılardan bir profil oluşturmasını isteyerek ve örneğin, geçmişte gördüğü filmleri derecelendirmek için çözülür.</span><span class="sxs-lookup"><span data-stu-id="463dd-329">This problem is often solved by asking new users to create a profile and, for instance, rate movies they have seen in the past.</span></span> <span data-ttu-id="463dd-330">Bu yöntem kullanıcıya bazı yük koyar, ancak derecelendirme geçmişi olmayan yeni kullanıcılar için bazı veri başlatma verileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="463dd-330">While this method puts some burden on the user, it provides some starting data for new users with no rating history.</span></span>

## <a name="resources"></a><span data-ttu-id="463dd-331">Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="463dd-331">Resources</span></span>

<span data-ttu-id="463dd-332">Bu öğreticide kullanılan veriler [Movielens veri kümesinden](http://files.grouplens.org/datasets/movielens/)türetilir.</span><span class="sxs-lookup"><span data-stu-id="463dd-332">The data used in this tutorial is derived from [MovieLens Dataset](http://files.grouplens.org/datasets/movielens/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="463dd-333">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="463dd-333">Next steps</span></span>

<span data-ttu-id="463dd-334">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="463dd-334">In this tutorial, you learned how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="463dd-335">Makine öğrenimi algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="463dd-335">Select a machine learning algorithm</span></span>
> * <span data-ttu-id="463dd-336">Verilerinizi hazırlayın ve yükleyin</span><span class="sxs-lookup"><span data-stu-id="463dd-336">Prepare and load your data</span></span>
> * <span data-ttu-id="463dd-337">Model oluşturma ve eğitme</span><span class="sxs-lookup"><span data-stu-id="463dd-337">Build and train a model</span></span>
> * <span data-ttu-id="463dd-338">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="463dd-338">Evaluate a model</span></span>
> * <span data-ttu-id="463dd-339">Bir modeli dağıtma ve kullanma</span><span class="sxs-lookup"><span data-stu-id="463dd-339">Deploy and consume a model</span></span>

<span data-ttu-id="463dd-340">Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin</span><span class="sxs-lookup"><span data-stu-id="463dd-340">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="463dd-341">Yaklaşım analizi</span><span class="sxs-lookup"><span data-stu-id="463dd-341">Sentiment Analysis</span></span>](sentiment-analysis.md)
