---
title: 'Öğretici: Bir film öneren - matris factorization oluşturun'
description: Bu öğreticide bir .NET Core konsol uygulaması içinde bir film öneren ML.NET ile derleme gösterilmektedir. Adımları C# ve Visual Studio 2019.
author: briacht
ms.author: johalex
ms.date: 05/06/2019
ms.custom: mvc, title-hack-0516
ms.topic: tutorial
ms.openlocfilehash: 512c8d663835da77c05fb24926ff85c56afd11ca
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882261"
---
# <a name="tutorial-build-a-movie-recommender-using-matrix-factorizaton-with-mlnet"></a><span data-ttu-id="379c3-104">Öğretici: Matris factorizaton ML.NET ile kullanarak bir film öneren oluşturun</span><span class="sxs-lookup"><span data-stu-id="379c3-104">Tutorial: Build a movie recommender using matrix factorizaton with ML.NET</span></span>

<span data-ttu-id="379c3-105">Bu öğreticide bir .NET Core konsol uygulaması içinde bir film öneren ML.NET ile derleme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="379c3-105">This tutorial shows you how to build a movie recommender with ML.NET in a .NET Core console application.</span></span> <span data-ttu-id="379c3-106">Adımları C# ve Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="379c3-106">The steps use C# and Visual Studio 2019.</span></span>

<span data-ttu-id="379c3-107">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="379c3-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="379c3-108">Bir machine learning algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="379c3-108">Select a machine learning algorithm</span></span>
> * <span data-ttu-id="379c3-109">Verilerinizi yüklemek ve hazırlamak</span><span class="sxs-lookup"><span data-stu-id="379c3-109">Prepare and load your data</span></span>
> * <span data-ttu-id="379c3-110">Yapı ve model eğitme</span><span class="sxs-lookup"><span data-stu-id="379c3-110">Build and train a model</span></span>
> * <span data-ttu-id="379c3-111">Bir modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="379c3-111">Evaluate a model</span></span>
> * <span data-ttu-id="379c3-112">Dağıtma ve bir modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="379c3-112">Deploy and consume a model</span></span>

<span data-ttu-id="379c3-113">Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) depo.</span><span class="sxs-lookup"><span data-stu-id="379c3-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repository.</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="379c3-114">Machine learning iş akışı</span><span class="sxs-lookup"><span data-stu-id="379c3-114">Machine learning workflow</span></span>

<span data-ttu-id="379c3-115">Göreviniz yanı sıra diğer ML.NET görev gerçekleştirmek için aşağıdaki adımları kullanın:</span><span class="sxs-lookup"><span data-stu-id="379c3-115">You will use the following steps to accomplish your task, as well as any other ML.NET task:</span></span>

1. [<span data-ttu-id="379c3-116">Veri yükleme</span><span class="sxs-lookup"><span data-stu-id="379c3-116">Load your data</span></span>](#load-your-data)
2. [<span data-ttu-id="379c3-117">Derleme ve modelinizi eğitin</span><span class="sxs-lookup"><span data-stu-id="379c3-117">Build and train your model</span></span>](#build-and-train-your-model)
3. [<span data-ttu-id="379c3-118">Modelinizi değerlendir</span><span class="sxs-lookup"><span data-stu-id="379c3-118">Evaluate your model</span></span>](#evaluate-your-model)
4. [<span data-ttu-id="379c3-119">Modelinizi kullanın</span><span class="sxs-lookup"><span data-stu-id="379c3-119">Use your model</span></span>](#use-your-model)

## <a name="prerequisites"></a><span data-ttu-id="379c3-120">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="379c3-120">Prerequisites</span></span>

* <span data-ttu-id="379c3-121">[Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır.</span><span class="sxs-lookup"><span data-stu-id="379c3-121">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="379c3-122">Uygun makine öğrenimi görevini seçin</span><span class="sxs-lookup"><span data-stu-id="379c3-122">Select the appropriate machine learning task</span></span>

<span data-ttu-id="379c3-123">Öneri sorunları, filmler listesini önerme veya ilgili ürünler listesi öneren gibi yaklaşan çeşitli yolları vardır, ancak derecelendirme hangi (1-5) bir kullanıcı belirli bir filmi verin ve da ise, film önerir. Bu durumda tahmin tanımlı bir eşiğin (yüksek derecelendirme, bir kullanıcı belirli bir filmi özelleştirebilir olma olasılığı daha) daha yüksek.</span><span class="sxs-lookup"><span data-stu-id="379c3-123">There are several ways to approach recommendation problems, such as recommending a list of movies or recommending a list of related products, but in this case you will predict what rating (1-5) a user will give to a particular movie and recommend that movie if it's higher than a defined threshold (the higher the rating, the higher the likelihood of a user liking a particular movie).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="379c3-124">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="379c3-124">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="379c3-125">Proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="379c3-125">Create a project</span></span>

1. <span data-ttu-id="379c3-126">Visual Studio 2017'yi açın.</span><span class="sxs-lookup"><span data-stu-id="379c3-126">Open Visual Studio 2017.</span></span> <span data-ttu-id="379c3-127">Seçin **dosya** > **yeni** > **proje** menü çubuğundan.</span><span class="sxs-lookup"><span data-stu-id="379c3-127">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="379c3-128">İçinde **yeni proje** iletişim kutusunda **Visual C#** düğümünü ve ardından **.NET Core** düğümü.</span><span class="sxs-lookup"><span data-stu-id="379c3-128">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="379c3-129">Ardından **konsol uygulaması (.NET Core)** proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="379c3-129">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="379c3-130">İçinde **adı** metin kutusuna "MovieRecommender" yazın ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="379c3-130">In the **Name** text box, type "MovieRecommender" and then select the **OK** button.</span></span>

2. <span data-ttu-id="379c3-131">Adlı bir dizin oluşturmak *veri* projenizdeki veri kümesi depolamak için:</span><span class="sxs-lookup"><span data-stu-id="379c3-131">Create a directory named *Data* in your project to store the data set:</span></span>

    <span data-ttu-id="379c3-132">İçinde **Çözüm Gezgini**, projeye sağ tıklayıp seçin **Ekle** > **yeni klasör**.</span><span class="sxs-lookup"><span data-stu-id="379c3-132">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="379c3-133">"Veri" yazın ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="379c3-133">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="379c3-134">Yükleme **Microsoft.ML** ve **Microsoft.ML.Recommender** NuGet paketleri:</span><span class="sxs-lookup"><span data-stu-id="379c3-134">Install the **Microsoft.ML** and **Microsoft.ML.Recommender** NuGet Packages:</span></span>

    <span data-ttu-id="379c3-135">İçinde **Çözüm Gezgini**, projeye sağ tıklayıp seçin **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="379c3-135">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="379c3-136">Paket kaynağı, seçin "nuget.org" seçin **Gözat** sekmesinde, arama **Microsoft.ML**seçin **1.0.0** paketini listede bulun ve seçin  **Yükleme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="379c3-136">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the **1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="379c3-137">Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="379c3-137">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="379c3-138">Bu adımı yineleyin **Microsoft.ML.Recommender v0.12.0**.</span><span class="sxs-lookup"><span data-stu-id="379c3-138">Repeat these steps for **Microsoft.ML.Recommender v0.12.0**.</span></span>

4. <span data-ttu-id="379c3-139">Aşağıdaki `using` en üstündeki deyimleri, *Program.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="379c3-139">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[UsingStatements](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#UsingStatements "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="379c3-140">Verilerinizi indirin</span><span class="sxs-lookup"><span data-stu-id="379c3-140">Download your data</span></span>

1. <span data-ttu-id="379c3-141">İki veri kümesi indirmek ve bunları kaydetmek *veri* daha önce oluşturduğunuz klasör:</span><span class="sxs-lookup"><span data-stu-id="379c3-141">Download the two datasets and save them to the *Data* folder you previously created:</span></span>

   * <span data-ttu-id="379c3-142">Sağ tıklayın [ *öneri derecelendirmeleri train.csv* ](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) seçip "bağlantısına (veya hedef) olarak kaydedin. …"</span><span class="sxs-lookup"><span data-stu-id="379c3-142">Right click on [*recommendation-ratings-train.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) and select "Save Link (or Target) As..."</span></span>
   * <span data-ttu-id="379c3-143">Sağ tıklayın [ *öneri derecelendirmeleri test.csv* ](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) seçip "bağlantısına (veya hedef) olarak kaydedin. …"</span><span class="sxs-lookup"><span data-stu-id="379c3-143">Right click on [*recommendation-ratings-test.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="379c3-144">Ya da kaydettiğinizden emin olun \*.csv dosyalarını *veri* klasöründe veya başka bir yerde kaydettikten sonra taşıma \*.csv dosyalarını *veri* klasör.</span><span class="sxs-lookup"><span data-stu-id="379c3-144">Make sure you either save the \*.csv files to the *Data* folder, or after you save it elsewhere, move the \*.csv files to the *Data* folder.</span></span>

2. <span data-ttu-id="379c3-145">Her bir Çözüm Gezgini'nde sağ \*.csv dosyalarını ve select **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="379c3-145">In Solution Explorer, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="379c3-146">Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.</span><span class="sxs-lookup"><span data-stu-id="379c3-146">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

   ![vs'de yeniyse Kopyala](./media/movie-recommendation/copytoout.gif)

## <a name="load-your-data"></a><span data-ttu-id="379c3-148">Veri yükleme</span><span class="sxs-lookup"><span data-stu-id="379c3-148">Load your data</span></span>

<span data-ttu-id="379c3-149">ML.NET sürecinde ilk adım, hazırlama ve model eğitiminin ve test verilerinin yük sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="379c3-149">The first step in the ML.NET process is to prepare and load your model training and testing data.</span></span>

<span data-ttu-id="379c3-150">Öneri derecelendirmeleri verileri bölün `Train` ve `Test` veri kümeleri.</span><span class="sxs-lookup"><span data-stu-id="379c3-150">The recommendation ratings data is split into `Train` and `Test` datasets.</span></span> <span data-ttu-id="379c3-151">`Train` Veri modelinizi sığdırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="379c3-151">The `Train` data is used to fit your model.</span></span> <span data-ttu-id="379c3-152">`Test` Veri modeliniz eğitilen tahminlerde bulunabilir ve model performansını değerlendirme için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="379c3-152">The `Test` data is used to make predictions with your trained model and evaluate model performance.</span></span> <span data-ttu-id="379c3-153">Bölme bir 80/20 çok yaygındır `Train` ve `Test` veri.</span><span class="sxs-lookup"><span data-stu-id="379c3-153">It's common to have an 80/20 split with `Train` and `Test` data.</span></span>

<span data-ttu-id="379c3-154">Aşağıda verilerden önizlemesidir, \*.csv dosyaları:</span><span class="sxs-lookup"><span data-stu-id="379c3-154">Below is a preview of the data from your \*.csv files:</span></span>

![Veri önizlemesi](./media/movie-recommendation/csv-dataset-preview.png)

<span data-ttu-id="379c3-156">İçinde \*.csv dosyalarını dört sütun vardır:</span><span class="sxs-lookup"><span data-stu-id="379c3-156">In the \*.csv files, there are four columns:</span></span>

* `userId`
* `movieId`
* `rating`
* `timestamp`

<span data-ttu-id="379c3-157">Machine learning'de bir tahminde bulunmak için kullanılan sütun olarak adlandırılan [özellikleri](../resources/glossary.md#feature), ve döndürülen tahmin sütunla çağrılır [etiket](../resources/glossary.md#label).</span><span class="sxs-lookup"><span data-stu-id="379c3-157">In machine learning, the columns that are used to make a prediction are called [Features](../resources/glossary.md#feature), and the column with the returned prediction is called the [Label](../resources/glossary.md#label).</span></span>

<span data-ttu-id="379c3-158">Film derecelendirme Derecelendirme sütunu, bu nedenle tahmin etmek istediğiniz `Label`.</span><span class="sxs-lookup"><span data-stu-id="379c3-158">You want to predict movie ratings, so the rating column is the `Label`.</span></span> <span data-ttu-id="379c3-159">Diğer üç sütun `userId`, `movieId`, ve `timestamp` tümü `Features` tahmin etmek için kullanılan `Label`.</span><span class="sxs-lookup"><span data-stu-id="379c3-159">The other three columns, `userId`, `movieId`, and `timestamp` are all `Features` used to predict the `Label`.</span></span>

| <span data-ttu-id="379c3-160">Özellikler</span><span class="sxs-lookup"><span data-stu-id="379c3-160">Features</span></span>      | <span data-ttu-id="379c3-161">Etiketle</span><span class="sxs-lookup"><span data-stu-id="379c3-161">Label</span></span>         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |
| `timestamp`     |               |

<span data-ttu-id="379c3-162">Hangi karar vermek için size kalmıştır `Features` tahmin etmek için kullanılan `Label`.</span><span class="sxs-lookup"><span data-stu-id="379c3-162">It's up to you to decide which `Features` are used to predict the `Label`.</span></span> <span data-ttu-id="379c3-163">Gibi yöntemleri de kullanabilirsiniz [özellik permütasyon önem](../how-to-guides/determine-global-feature-importance-in-model.md) en iyi seçme ile yardımcı olmak için `Features`.</span><span class="sxs-lookup"><span data-stu-id="379c3-163">You can also use methods like [Feature Permutation Importance](../how-to-guides/determine-global-feature-importance-in-model.md) to help with selecting the best `Features`.</span></span>

<span data-ttu-id="379c3-164">Bu durumda, ortadan `timestamp` sütun olarak bir `Feature` zaman damgası gerçekten ne bir kullanıcı belirli bir filmi derecelendirir etkilemez ve böylece daha doğru bir tahmin yapmaya katkıda değil çünkü:</span><span class="sxs-lookup"><span data-stu-id="379c3-164">In this case, you should eliminate the `timestamp` column as a `Feature` because the timestamp does not really affect how a user rates a given movie and thus would not contribute to making a more accurate prediction:</span></span>

| <span data-ttu-id="379c3-165">Özellikler</span><span class="sxs-lookup"><span data-stu-id="379c3-165">Features</span></span>      | <span data-ttu-id="379c3-166">Etiketle</span><span class="sxs-lookup"><span data-stu-id="379c3-166">Label</span></span>         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |

<span data-ttu-id="379c3-167">Sonraki giriş sınıfı için data yapınız tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="379c3-167">Next you must define your data structure for the input class.</span></span>

<span data-ttu-id="379c3-168">Yeni bir sınıf, projenize ekleyin:</span><span class="sxs-lookup"><span data-stu-id="379c3-168">Add a new class to your project:</span></span>

1. <span data-ttu-id="379c3-169">İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle > Yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="379c3-169">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="379c3-170">İçinde **Yeni Öğe Ekle iletişim kutusu**seçin **sınıfı** değiştirip **adı** alanı *MovieRatingData.cs*.</span><span class="sxs-lookup"><span data-stu-id="379c3-170">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *MovieRatingData.cs*.</span></span> <span data-ttu-id="379c3-171">Ardından, **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="379c3-171">Then, select the **Add** button.</span></span>

<span data-ttu-id="379c3-172">*MovieRatingData.cs* dosyası Kod Düzenleyicisi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="379c3-172">The *MovieRatingData.cs* file opens in the code editor.</span></span> <span data-ttu-id="379c3-173">Aşağıdaki `using` üstüne deyimi *MovieRatingData.cs*:</span><span class="sxs-lookup"><span data-stu-id="379c3-173">Add the following `using` statement to the top of *MovieRatingData.cs*:</span></span>

```csharp
using Microsoft.ML.Data;
```

<span data-ttu-id="379c3-174">Adlı bir sınıf oluşturmak `MovieRating` varolan sınıf tanımına kaldırma ve aşağıdaki kodu ekleyerek *MovieRatingData.cs*:</span><span class="sxs-lookup"><span data-stu-id="379c3-174">Create a class called `MovieRating` by removing the existing class definition and adding the following code in *MovieRatingData.cs*:</span></span>

[!code-csharp[MovieRatingClass](~/samples/machine-learning/tutorials/MovieRecommendation/MovieRatingData.cs#MovieRatingClass "Add the Movie Rating class")]

<span data-ttu-id="379c3-175">`MovieRating` bir giriş veri sınıfı belirtir.</span><span class="sxs-lookup"><span data-stu-id="379c3-175">`MovieRating` specifies an input data class.</span></span> <span data-ttu-id="379c3-176">[LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) özniteliği (sütun dizini tarafından) veri kümesindeki sütunları yüklenmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="379c3-176">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span> <span data-ttu-id="379c3-177">`userId` Ve `movieId` sütunlar, `Features` (girişleri tahmin modelini sunacak `Label`), ve Derecelendirme sütunu `Label` (modelin çıkış) tahmin.</span><span class="sxs-lookup"><span data-stu-id="379c3-177">The `userId` and `movieId` columns are your `Features` (the inputs you will give the model to predict the `Label`), and the rating column is the `Label` that you will predict (the output of the model).</span></span>

<span data-ttu-id="379c3-178">Başka bir sınıf oluşturun `MovieRatingPrediction`, sonra aşağıdaki kodu ekleyerek tahmin edilen sonuçları göstermek için `MovieRating` sınıfını *MovieRatingData.cs*:</span><span class="sxs-lookup"><span data-stu-id="379c3-178">Create another class, `MovieRatingPrediction`, to represent predicted results by adding the following code after the `MovieRating` class in *MovieRatingData.cs*:</span></span>

[!code-csharp[PredictionClass](~/samples/machine-learning/tutorials/MovieRecommendation/MovieRatingData.cs#PredictionClass "Add the Movie Prediction Class")]

<span data-ttu-id="379c3-179">İçinde *Program.cs*, değiştirin `Console.WriteLine("Hello World!")` içinde aşağıdaki kodla `Main()`:</span><span class="sxs-lookup"><span data-stu-id="379c3-179">In *Program.cs*, replace the `Console.WriteLine("Hello World!")` with the following code inside `Main()`:</span></span>

[!code-csharp[MLContext](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#MLContext "Add MLContext")]

<span data-ttu-id="379c3-180">[MLContext sınıfı](xref:Microsoft.ML.MLContext) bir tüm ML.NET işlemleri için başlangıç noktası ve başlatma `mlContext` modeli oluşturma iş akışı nesneleri arasında paylaşılabilir bir yeni ML.NET ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="379c3-180">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="379c3-181">Bu, kavramsal olarak, benzer `DBContext` Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="379c3-181">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="379c3-182">Sonra `Main()`, adında bir yöntem oluşturun `LoadData()`:</span><span class="sxs-lookup"><span data-stu-id="379c3-182">After `Main()`, create a method called `LoadData()`:</span></span>

```csharp
public static (IDataView training, IDataView test) LoadData(MLContext mlContext)
{

}
```

> [!NOTE]
> <span data-ttu-id="379c3-183">Aşağıdaki adımlarda bir dönüş ifadesi eklenene kadar bu yöntem bir hata verir.</span><span class="sxs-lookup"><span data-stu-id="379c3-183">This method will give you an error until you add a return statement in the following steps.</span></span>

<span data-ttu-id="379c3-184">Veri yolu değişkenlerinizi başlatmak, verilerden yük \*.csv dosyalarını ve dönüş `Train` ve `Test` verileri olarak `IDataView` sonraki kod satırı olarak aşağıdakileri ekleyerek nesneleri `LoadData()`:</span><span class="sxs-lookup"><span data-stu-id="379c3-184">Initialize your data path variables, load the data from the \*.csv files, and return the `Train` and `Test` data as `IDataView` objects by adding the following as the next line of code in `LoadData()`:</span></span>

[!code-csharp[LoadData](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#LoadData "Load data from data paths")]

<span data-ttu-id="379c3-185">ML.NET verilerinde olarak temsil edilir bir [IDataView sınıfı](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="379c3-185">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="379c3-186">`IDataView` Sekmeli veriler (sayısal ve metin) açıklayan bir esnek ve verimli yoludur.</span><span class="sxs-lookup"><span data-stu-id="379c3-186">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="379c3-187">Veri yüklenebilir bir metin dosyasından veya gerçek zamanlı olarak (örneğin, SQL veritabanı veya günlük dosyaları) için bir `IDataView` nesne.</span><span class="sxs-lookup"><span data-stu-id="379c3-187">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="379c3-188">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) veri şemasını tanımlar ve dosyayı okur.</span><span class="sxs-lookup"><span data-stu-id="379c3-188">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="379c3-189">Veri yolu değişkenlerinde alır ve döndürür bir `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="379c3-189">It takes in the data path variables and returns an `IDataView`.</span></span> <span data-ttu-id="379c3-190">Bu durumda, yolu sağlamak, `Test` ve `Train` dosyaları ve hem (sütun adları düzgün kullanabilmesi için) metin dosya üstbilgisi hem de (varsayılan ayırıcısı olan bir sekme) virgülle karakter veri ayırıcısı gösterir.</span><span class="sxs-lookup"><span data-stu-id="379c3-190">In this case, you provide the path for your `Test` and `Train` files and indicate both the text file header (so it can use the column names properly) and the comma character data separator (the default separator is a tab).</span></span>

<span data-ttu-id="379c3-191">Sonraki iki kod satırlarını olarak aşağıdakileri ekleyin `Main()` çağrılacak yöntem, `LoadData()` yöntemi ve dönüş `Train` ve `Test` veri:</span><span class="sxs-lookup"><span data-stu-id="379c3-191">Add the following as the next two lines of code in the `Main()` method to call your `LoadData()` method and return the `Train` and `Test` data:</span></span>

[!code-csharp[LoadDataMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#LoadDataMain "Add LoadData method to Main")]

## <a name="build-and-train-your-model"></a><span data-ttu-id="379c3-192">Derleme ve modelinizi eğitin</span><span class="sxs-lookup"><span data-stu-id="379c3-192">Build and train your model</span></span>

<span data-ttu-id="379c3-193">ML.NET içinde üç ana kavramı vardır: [Veri](../resources/glossary.md#data), [dönüştürücüler](../resources/glossary.md#transformer), ve [Estimators](../resources/glossary.md#estimator).</span><span class="sxs-lookup"><span data-stu-id="379c3-193">There are three major concepts in ML.NET: [Data](../resources/glossary.md#data), [Transformers](../resources/glossary.md#transformer), and [Estimators](../resources/glossary.md#estimator).</span></span>

<span data-ttu-id="379c3-194">Makine öğrenimi eğitim algoritmalar, verileri belirli bir biçimde gerektirir.</span><span class="sxs-lookup"><span data-stu-id="379c3-194">Machine learning training algorithms require data in a certain format.</span></span> <span data-ttu-id="379c3-195">`Transformers` tablosal veri uyumlu bir biçime dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="379c3-195">`Transformers` are used to transform tabular data to a compatible format.</span></span>

![Transformer görüntüsü](./media/movie-recommendation/transformer.png)

<span data-ttu-id="379c3-197">Oluşturduğunuz `Transformers` oluşturarak ML.NET içinde `Estimators`.</span><span class="sxs-lookup"><span data-stu-id="379c3-197">You create `Transformers` in ML.NET by creating `Estimators`.</span></span> <span data-ttu-id="379c3-198">`Estimators` veri ve dönüş ele `Transformers`.</span><span class="sxs-lookup"><span data-stu-id="379c3-198">`Estimators` take in data and return `Transformers`.</span></span>

![Tahmin görüntüsü](./media/movie-recommendation/estimator.png)

<span data-ttu-id="379c3-200">Örneğidir, modeli eğitmek için kullanacağınız öneri eğitim algoritması bir `Estimator`.</span><span class="sxs-lookup"><span data-stu-id="379c3-200">The recommendation training algorithm you will use for training your model is an example of an `Estimator`.</span></span>

<span data-ttu-id="379c3-201">Derleme bir `Estimator` aşağıdaki adımları:</span><span class="sxs-lookup"><span data-stu-id="379c3-201">Build an `Estimator` with the following steps:</span></span>

<span data-ttu-id="379c3-202">Oluşturma `BuildAndTrainModel()` yöntemi hemen sonrasına `LoadData()` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="379c3-202">Create the `BuildAndTrainModel()` method, just after the `LoadData()` method, using the following code:</span></span>

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView trainingDataView)
{

}
```

> [!NOTE]
> <span data-ttu-id="379c3-203">Aşağıdaki adımlarda bir dönüş ifadesi eklenene kadar bu yöntem bir hata verir.</span><span class="sxs-lookup"><span data-stu-id="379c3-203">This method will give you an error until you add a return statement in the following steps.</span></span>

<span data-ttu-id="379c3-204">Aşağıdaki kodu ekleyerek veri dönüşümlerini tanımlamak `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="379c3-204">Define the data transformations by adding the following code to `BuildAndTrainModel()`:</span></span>

[!code-csharp[DataTransformations](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#DataTransformations "Define data transformations")]

<span data-ttu-id="379c3-205">Bu yana `userId` ve `movieId` temsil kullanıcılar ve başlık, değil gerçek değerler kullandığınız [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) her dönüştürmek için yöntemi `userId` ve her `movieId` sayısal anahtar türü `Feature`sütun (öneri algoritmalarda kabul biçimi) ve bunları yeni dataset sütunları ekleyin:</span><span class="sxs-lookup"><span data-stu-id="379c3-205">Since `userId` and `movieId` represent users and movie titles, not real values, you use the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method to transform each `userId` and each `movieId` into a numeric key type `Feature` column (a format accepted by recommendation algorithms) and add them as new dataset columns:</span></span>

| <span data-ttu-id="379c3-206">userId</span><span class="sxs-lookup"><span data-stu-id="379c3-206">userId</span></span> | <span data-ttu-id="379c3-207">movieId</span><span class="sxs-lookup"><span data-stu-id="379c3-207">movieId</span></span> | <span data-ttu-id="379c3-208">Etiketle</span><span class="sxs-lookup"><span data-stu-id="379c3-208">Label</span></span> | <span data-ttu-id="379c3-209">userIdEncoded</span><span class="sxs-lookup"><span data-stu-id="379c3-209">userIdEncoded</span></span> | <span data-ttu-id="379c3-210">movieIdEncoded</span><span class="sxs-lookup"><span data-stu-id="379c3-210">movieIdEncoded</span></span> |
| ------------- |:-------------:| -----:|-----:|-----:|
| <span data-ttu-id="379c3-211">1.</span><span class="sxs-lookup"><span data-stu-id="379c3-211">1</span></span> | <span data-ttu-id="379c3-212">1.</span><span class="sxs-lookup"><span data-stu-id="379c3-212">1</span></span> | <span data-ttu-id="379c3-213">4</span><span class="sxs-lookup"><span data-stu-id="379c3-213">4</span></span> | <span data-ttu-id="379c3-214">userKey1</span><span class="sxs-lookup"><span data-stu-id="379c3-214">userKey1</span></span> | <span data-ttu-id="379c3-215">movieKey1</span><span class="sxs-lookup"><span data-stu-id="379c3-215">movieKey1</span></span> |
| <span data-ttu-id="379c3-216">1.</span><span class="sxs-lookup"><span data-stu-id="379c3-216">1</span></span> | <span data-ttu-id="379c3-217">3</span><span class="sxs-lookup"><span data-stu-id="379c3-217">3</span></span> | <span data-ttu-id="379c3-218">4</span><span class="sxs-lookup"><span data-stu-id="379c3-218">4</span></span> | <span data-ttu-id="379c3-219">userKey1</span><span class="sxs-lookup"><span data-stu-id="379c3-219">userKey1</span></span> | <span data-ttu-id="379c3-220">movieKey2</span><span class="sxs-lookup"><span data-stu-id="379c3-220">movieKey2</span></span> |
| <span data-ttu-id="379c3-221">1.</span><span class="sxs-lookup"><span data-stu-id="379c3-221">1</span></span> | <span data-ttu-id="379c3-222">6</span><span class="sxs-lookup"><span data-stu-id="379c3-222">6</span></span> | <span data-ttu-id="379c3-223">4</span><span class="sxs-lookup"><span data-stu-id="379c3-223">4</span></span> | <span data-ttu-id="379c3-224">userKey1</span><span class="sxs-lookup"><span data-stu-id="379c3-224">userKey1</span></span> | <span data-ttu-id="379c3-225">movieKey3</span><span class="sxs-lookup"><span data-stu-id="379c3-225">movieKey3</span></span> |

<span data-ttu-id="379c3-226">Makine öğrenme algoritmasını seçin ve sonraki kod satırı olarak aşağıdakileri ekleyerek veri dönüştürme tanımlarını ekleme `BuildAndTrainModel()`:</span><span class="sxs-lookup"><span data-stu-id="379c3-226">Choose the machine learning algorithm and append it to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[AddAlgorithm](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#AddAlgorithm "Add the training algorithm with options")]

<span data-ttu-id="379c3-227">[MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) öneri eğitim algoritmasıdır.</span><span class="sxs-lookup"><span data-stu-id="379c3-227">The [MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) is your recommendation training algorithm.</span></span>  <span data-ttu-id="379c3-228">[Matris Factorization](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) kullanıcıların geçmişte veri kümeleri için Bu öğreticide olduğu ürünleri nasıl değerlendirmiş şirket verileriniz öneri için yaygın bir yaklaşım gerekir.</span><span class="sxs-lookup"><span data-stu-id="379c3-228">[Matrix Factorization](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) is a common approach to recommendation when you have data on how users have rated products in the past, which is the case for the datasets in this tutorial.</span></span> <span data-ttu-id="379c3-229">Farklı veri kullanılabilir olduğunda için diğer öneri algoritmalar vardır (bkz [diğer öneri algoritmalar](#other-recommendation-algorithms) daha fazla bilgi için aşağıdaki bölümü).</span><span class="sxs-lookup"><span data-stu-id="379c3-229">There are other recommendation algorithms for when you have different data available (see the [Other recommendation algorithms](#other-recommendation-algorithms) section below to learn more).</span></span>

<span data-ttu-id="379c3-230">Bu durumda, `Matrix Factorization` daha sonra kullanıcı 1. büyük olasılıkla aynı biçimde kullanıcı 2 farklı bir sorunla ilgili olarak algoritması kullanıcı 1 kullanıcı 2 belirli bir sorunla ilgili olarak aynı fikrim varsa, olduğunu varsayar, "işbirliğine dayalı filtreleme" adlı bir yöntem kullanır.</span><span class="sxs-lookup"><span data-stu-id="379c3-230">In this case, the `Matrix Factorization` algorithm uses a method called "collaborative filtering", which assumes that if User 1 has the same opinion as User 2 on a certain issue, then User 1 is more likely to feel the same way as User 2 about a different issue.</span></span>

<span data-ttu-id="379c3-231">Kullanıcı 1, kullanıcı 2 filmler benzer şekilde oranı, örneğin, ardından kullanıcı 2 kullanıcı 1 olan ve izlenen yüksek dereceli bir filmi keyfini çıkarın daha kolaydır:</span><span class="sxs-lookup"><span data-stu-id="379c3-231">For instance, if User 1 and User 2 rate movies similarly, then User 2 is more likely to enjoy a movie that User 1 has watched and rated highly:</span></span>

| | `Incredibles 2 (2018)` | `The Avengers (2012)` | `Guardians of the Galaxy (2014)` |
| -------------:|-------------:| -----:|-----:|
| <span data-ttu-id="379c3-232">Kullanıcı 1</span><span class="sxs-lookup"><span data-stu-id="379c3-232">User 1</span></span> | <span data-ttu-id="379c3-233">İzlenen ve bağlanan film</span><span class="sxs-lookup"><span data-stu-id="379c3-233">Watched and liked movie</span></span> | <span data-ttu-id="379c3-234">İzlenen ve bağlanan film</span><span class="sxs-lookup"><span data-stu-id="379c3-234">Watched and liked movie</span></span> | <span data-ttu-id="379c3-235">İzlenen ve bağlanan film</span><span class="sxs-lookup"><span data-stu-id="379c3-235">Watched and liked movie</span></span> |
| <span data-ttu-id="379c3-236">Kullanıcı 2</span><span class="sxs-lookup"><span data-stu-id="379c3-236">User 2</span></span> | <span data-ttu-id="379c3-237">İzlenen ve bağlanan film</span><span class="sxs-lookup"><span data-stu-id="379c3-237">Watched and liked movie</span></span> | <span data-ttu-id="379c3-238">İzlenen ve bağlanan film</span><span class="sxs-lookup"><span data-stu-id="379c3-238">Watched and liked movie</span></span> | <span data-ttu-id="379c3-239">Olmayan izlenen--ÖNERİ film</span><span class="sxs-lookup"><span data-stu-id="379c3-239">Has not watched -- RECOMMEND movie</span></span> |

<span data-ttu-id="379c3-240">`Matrix Factorization` Trainer sahip birkaç [seçenekleri](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), daha fazla ilgili bilgi de edinebilirsiniz hangi [algoritması hiperparametreleri](#algorithm-hyperparameters) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="379c3-240">The `Matrix Factorization` trainer has several [Options](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), which you can read more about in the [Algorithm hyperparameters](#algorithm-hyperparameters) section below.</span></span>

<span data-ttu-id="379c3-241">Modele uygun `Train` veri ve sonraki kod satırı olarak aşağıdakileri ekleyerek eğitilen model dönüş `BuildAndTrainModel()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="379c3-241">Fit the model to the `Train` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[FitModel](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#FitModel "Call the Fit method and return back the trained model")]

<span data-ttu-id="379c3-242">[Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) yöntemine sağlanan bir eğitim veri kümesi modelinizi eğitir.</span><span class="sxs-lookup"><span data-stu-id="379c3-242">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model with the provided training dataset.</span></span> <span data-ttu-id="379c3-243">Teknik olarak yürütür `Estimator` verileri dönüştürme ve eğitim ve uygulama tanımlarını döndürür geri olan eğitilen model bir `Transformer`.</span><span class="sxs-lookup"><span data-stu-id="379c3-243">Technically, it executes the `Estimator` definitions by transforming the data and applying the training, and it returns back the trained model, which is a `Transformer`.</span></span>

<span data-ttu-id="379c3-244">Sonraki kod satırı olarak ekleyin `Main()` çağrılacak yöntem, `BuildAndTrainModel()` yöntemi ve dönüş eğitim modeli:</span><span class="sxs-lookup"><span data-stu-id="379c3-244">Add the following as the next line of code in the `Main()` method to call your `BuildAndTrainModel()` method and return the trained model:</span></span>

[!code-csharp[BuildTrainModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#BuildTrainModelMain "Add BuildAndTrainModel method in Main")]

## <a name="evaluate-your-model"></a><span data-ttu-id="379c3-245">Modelinizi değerlendir</span><span class="sxs-lookup"><span data-stu-id="379c3-245">Evaluate your model</span></span>

<span data-ttu-id="379c3-246">Modelinizi eğitim almış sonra modelinizi performansını değerlendirmek için test verilerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="379c3-246">Once you have trained your model, use your test data to evaluate how your model is performing.</span></span>

<span data-ttu-id="379c3-247">Oluşturma `EvaluateModel()` yöntemi hemen sonrasına `BuildAndTrainModel()` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="379c3-247">Create the `EvaluateModel()` method, just after the `BuildAndTrainModel()` method, using the following code:</span></span>

```csharp
public static void EvaluateModel(MLContext mlContext, IDataView testDataView, ITransformer model)
{

}
```

<span data-ttu-id="379c3-248">Dönüştürme `Test` aşağıdakileri ekleyerek veri kod için `EvaluateModel()`: [!code-csharp[Transform](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#Transform "Transform the test data")]</span><span class="sxs-lookup"><span data-stu-id="379c3-248">Transform the `Test` data by adding the following code to `EvaluateModel()`: [!code-csharp[Transform](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#Transform "Transform the test data")]</span></span>

<span data-ttu-id="379c3-249">[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemi, birden çok test veri kümesini girdi satırları sağlanan için Öngörüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="379c3-249">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for multiple provided input rows of a test dataset.</span></span>

<span data-ttu-id="379c3-250">Sonraki kod satırı olarak aşağıdakileri ekleyerek modeli değerlendirme `EvaluateModel()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="379c3-250">Evaluate the model by adding the following as the next line of code in the `EvaluateModel()` method:</span></span>

[!code-csharp[Evaluate](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#Evaluate "Evaluate the model using predictions from the test data")]

<span data-ttu-id="379c3-251">Ayarlanırsa, tahmin sonra [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) yöntemi değerlendirir gerçek tahmin edilen değerlerle karşılaştırır modeli `Labels` modelin nasıl performans gösterdiğini üzerinde test veri kümesini ve döndürür ölçümleri de.</span><span class="sxs-lookup"><span data-stu-id="379c3-251">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns metrics on how the model is performing.</span></span>

<span data-ttu-id="379c3-252">Sonraki kod satırı olarak aşağıdakileri ekleyerek değerlendirme ölçümlerinizi konsola yazdırma `EvaluateModel()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="379c3-252">Print your evaluation metrics to the console by adding the following as the next line of code in the `EvaluateModel()` method:</span></span>

[!code-csharp[PrintMetrics](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PrintMetrics "Print the evaluation metrics")]

<span data-ttu-id="379c3-253">Sonraki kod satırı olarak ekleyin `Main()` çağrılacak yöntem, `EvaluateModel()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="379c3-253">Add the following as the next line of code in the `Main()` method to call your `EvaluateModel()` method:</span></span>

[!code-csharp[EvaluateModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#EvaluateModelMain "Add EvaluateModel method in Main")]

<span data-ttu-id="379c3-254">Şu ana kadar çıktı aşağıdaki metne benzer görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="379c3-254">The output so far should look similar to the following text:</span></span>

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

<span data-ttu-id="379c3-255">Bu çıkış, 20 yinelemeler vardır.</span><span class="sxs-lookup"><span data-stu-id="379c3-255">In this output, there are 20 iterations.</span></span> <span data-ttu-id="379c3-256">Her yinelemede hata ölçü azaltır ve daha yakın ve 0 yakın uygun sonuç verir.</span><span class="sxs-lookup"><span data-stu-id="379c3-256">In each iteration, the measure of error decreases and converges closer and closer to 0.</span></span>

<span data-ttu-id="379c3-257">`root of mean squared error` (RMS veya RMSE) tahmin modeli arasındaki farklılıklar ölçmek için kullanılan değerleri ve test veri kümesini gözlenen değerler.</span><span class="sxs-lookup"><span data-stu-id="379c3-257">The `root of mean squared error` (RMS or RMSE) is used to measure the differences between the model predicted values and the test dataset observed values.</span></span> <span data-ttu-id="379c3-258">Teknik olarak hataları kareler Ortalama kare kökünü olduğu.</span><span class="sxs-lookup"><span data-stu-id="379c3-258">Technically it's the square root of the average of the squares of the errors.</span></span> <span data-ttu-id="379c3-259">Daha düşük olan, daha iyi modelidir.</span><span class="sxs-lookup"><span data-stu-id="379c3-259">The lower it is, the better the model is.</span></span>

<span data-ttu-id="379c3-260">`R Squared` veri modeli ne kadar iyi uyduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="379c3-260">`R Squared` indicates how well data fits a model.</span></span> <span data-ttu-id="379c3-261">1 Aralık 0.</span><span class="sxs-lookup"><span data-stu-id="379c3-261">Ranges from 0 to 1.</span></span> <span data-ttu-id="379c3-262">Değeri 0 anlamına gelir veri rastgele veya başka türlü modele sığamıyorsa.</span><span class="sxs-lookup"><span data-stu-id="379c3-262">A value of 0 means that the data is random or otherwise can't be fit to the model.</span></span> <span data-ttu-id="379c3-263">Değeri model verileri tam olarak eşleşen 1 anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="379c3-263">A value of 1 means that the model exactly matches the data.</span></span> <span data-ttu-id="379c3-264">İstediğiniz, `R Squared` 1 olarak mümkün olduğunca yakın olmasını puanı.</span><span class="sxs-lookup"><span data-stu-id="379c3-264">You want your `R Squared` score to be as close to 1 as possible.</span></span>

<span data-ttu-id="379c3-265">Başarılı modeller oluşturma yinelemeli bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="379c3-265">Building successful models is an iterative process.</span></span> <span data-ttu-id="379c3-266">Bu model düşük ilk kalite hızlı modeli eğitimi sağlamak için öğretici kullanan küçük veri kümeleri sahiptir.</span><span class="sxs-lookup"><span data-stu-id="379c3-266">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="379c3-267">Model kalitesi memnun değilseniz daha büyük bir eğitim veri kümeleri sağlama veya farklı hyper-parametreleriyle her bir algoritmanın için farklı eğitim algoritmalarıyla seçerek geliştirmek deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="379c3-267">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different hyper-parameters for each algorithm.</span></span> <span data-ttu-id="379c3-268">Daha fazla bilgi için kullanıma [modelinizin geliştirilmesine](#improve-your-model) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="379c3-268">For more information, check out the [Improve your model](#improve-your-model) section below.</span></span>

## <a name="use-your-model"></a><span data-ttu-id="379c3-269">Modelinizi kullanın</span><span class="sxs-lookup"><span data-stu-id="379c3-269">Use your model</span></span>

<span data-ttu-id="379c3-270">Artık, eğitilen model üzerinde yeni veri tahmininde bulunmak amacıyla kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="379c3-270">Now you can use your trained model to make predictions on new data.</span></span>

<span data-ttu-id="379c3-271">Oluşturma `UseModelForSinglePrediction()` yöntemi hemen sonrasına `EvaluateModel()` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="379c3-271">Create the `UseModelForSinglePrediction()` method, just after the `EvaluateModel()` method, using the following code:</span></span>

```csharp
public static void UseModelForSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="379c3-272">Kullanım `PredictionEngine` derecelendirme aşağıdaki kodu ekleyerek tahmin etmek için `UseModelForSinglePrediction()`:</span><span class="sxs-lookup"><span data-stu-id="379c3-272">Use the `PredictionEngine` to predict the rating by adding the following code to `UseModelForSinglePrediction()`:</span></span>

[!code-csharp[PredictionEngine](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PredictionEngine "Create Prediction Engine")]

<span data-ttu-id="379c3-273">[PredictionEngine sınıfı](xref:Microsoft.ML.PredictionEngine%602) verileri tek bir örneğini geçirin ve ardından bu tek veri örneğinde bir tahmin gerçekleştirin izin veren bir kolaylık API.</span><span class="sxs-lookup"><span data-stu-id="379c3-273">The [PredictionEngine class](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass a single instance of data and then perform a prediction on this single instance of data.</span></span>

<span data-ttu-id="379c3-274">Bir örneğini oluşturmak `MovieRating` adlı `testInput` ve aşağıdaki kodda bir sonraki satırı olarak ekleyerek tahmin Altyapısı'na geçme `UseModelForSinglePrediction()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="379c3-274">Create an instance of `MovieRating` called `testInput` and pass it to the Prediction Engine by adding the following as the next lines of code in the `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[MakeSinglePrediction](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#MakeSinglePrediction "Make a single prediction with the Prediction Engine")]

<span data-ttu-id="379c3-275">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi, tek bir veri sütununu tahmin sağlar.</span><span class="sxs-lookup"><span data-stu-id="379c3-275">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single column of data.</span></span>

<span data-ttu-id="379c3-276">Ardından `Score`, ya da kullanıcı 6 movieId 10 film önerilir isteyip istemediğinizi belirlemek için tahmin edilen derecelendirmesi.</span><span class="sxs-lookup"><span data-stu-id="379c3-276">You can then use the `Score`, or the predicted rating, to determine whether you want to recommend the movie with movieId 10 to user 6.</span></span> <span data-ttu-id="379c3-277">En yüksek `Score`, daha yüksek bir kullanıcı olasılığını belirli bir filmi özelleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="379c3-277">The higher the `Score`, the higher the likelihood of a user liking a particular movie.</span></span> <span data-ttu-id="379c3-278">Bu durumda, tahmin edilen bir derecelendirme > 3.5 filmlerle önerilir varsayalım.</span><span class="sxs-lookup"><span data-stu-id="379c3-278">In this case, let’s say that you recommend movies with a predicted rating of > 3.5.</span></span>

<span data-ttu-id="379c3-279">Sonuçları yazdırmak için sonraki kod satırlarını olarak aşağıdakileri ekleyin `UseModelForSinglePrediction()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="379c3-279">To print the results, add the following as the next lines of code in the `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[PrintResults](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PrintResults "Print the recommendation prediction results")]

<span data-ttu-id="379c3-280">Sonraki kod satırı olarak ekleyin `Main()` çağrılacak yöntem, `UseModelForSinglePrediction()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="379c3-280">Add the following as the next line of code in the `Main()` method to call your `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[UseModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#UseModelMain "Add UseModelForSinglePrediction method in Main")]

<span data-ttu-id="379c3-281">Bu yöntem, çıktı aşağıdaki metne benzer görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="379c3-281">The output of this method should look similar to the following text:</span></span>

```console
=============== Making a prediction ===============
Movie 10 is recommended for user 6
```

### <a name="save-your-model"></a><span data-ttu-id="379c3-282">Modelinizi Kaydet</span><span class="sxs-lookup"><span data-stu-id="379c3-282">Save your model</span></span>

<span data-ttu-id="379c3-283">Son kullanıcı uygulamaları tahminlerde bulunmak üzere modelinizi kullanmak için önce model kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="379c3-283">To use your model to make predictions in end-user applications, you must first save the model.</span></span>

<span data-ttu-id="379c3-284">Oluşturma `SaveModel()` yöntemi hemen sonrasına `UseModelForSinglePrediction()` yöntemi, aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="379c3-284">Create the `SaveModel()` method, just after the `UseModelForSinglePrediction()` method, using the following code:</span></span>

```csharp
public static void SaveModel(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="379c3-285">Aşağıdaki kodu ekleyerek, eğitilen modeli kaydedin `SaveModel()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="379c3-285">Save your trained model by adding the following code in the `SaveModel()` method:</span></span>

[!code-csharp[SaveModel](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#SaveModel "Save the model to a zip file")]

<span data-ttu-id="379c3-286">Bu yöntem, eğitilen model sonra diğer .NET uygulamalarında tahminlerde bulunmak için kullanılabilecek bir .zip dosyası olarak ("Veri" klasöründe farklı olarak) kaydeder.</span><span class="sxs-lookup"><span data-stu-id="379c3-286">This method saves your trained model to a .zip file (in the "Data" folder), which can then be used in other .NET applications to make predictions.</span></span>

<span data-ttu-id="379c3-287">Sonraki kod satırı olarak ekleyin `Main()` çağrılacak yöntem, `SaveModel()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="379c3-287">Add the following as the next line of code in the `Main()` method to call your `SaveModel()` method:</span></span>

[!code-csharp[SaveModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#SaveModelMain "Create SaveModel method in Main")]

### <a name="use-your-saved-model"></a><span data-ttu-id="379c3-288">Kaydedilen modelinizi kullanın</span><span class="sxs-lookup"><span data-stu-id="379c3-288">Use your saved model</span></span>

<span data-ttu-id="379c3-289">Eğitilen model kaydedildikten sonra farklı ortamlarda modeli raporlarını kullanabilirsiniz (bkz ["Nasıl yapılır kılavuzunda"](../how-to-guides/consuming-model-ml-net.md) uygulamalarında eğitilen machine learning modeli kullanıma hazır hale getirme hakkında bilgi edinmek için).</span><span class="sxs-lookup"><span data-stu-id="379c3-289">Once you have saved your trained model, you can consume the model in different environments (see the ["How-to guide"](../how-to-guides/consuming-model-ml-net.md) to learn how to operationalize a trained machine learning model in apps).</span></span>

## <a name="results"></a><span data-ttu-id="379c3-290">Sonuçlar</span><span class="sxs-lookup"><span data-stu-id="379c3-290">Results</span></span>

<span data-ttu-id="379c3-291">Yukarıdaki adımları tamamladıktan sonra Konsol uygulamanızı (Ctrl + F5) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="379c3-291">After following the steps above, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="379c3-292">Yukarıdaki tek tahmin sonuçlarınızdan aşağıdakine benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="379c3-292">Your results from the single prediction above should be similar to the following.</span></span> <span data-ttu-id="379c3-293">Uyarı veya işlem iletileri görebilirsiniz, ancak bu iletiler anlaşılması için aşağıdaki sonuçları kaldırılmış olan.</span><span class="sxs-lookup"><span data-stu-id="379c3-293">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="379c3-294">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="379c3-294">Congratulations!</span></span> <span data-ttu-id="379c3-295">Bir machine learning modeli filmler önermek için artık başarıyla oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="379c3-295">You've now successfully built a machine learning model for recommending movies.</span></span> <span data-ttu-id="379c3-296">Bu öğreticide kaynak kodunu bulabilirsiniz [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) depo.</span><span class="sxs-lookup"><span data-stu-id="379c3-296">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repository.</span></span>

## <a name="improve-your-model"></a><span data-ttu-id="379c3-297">Modelinizi geliştirin</span><span class="sxs-lookup"><span data-stu-id="379c3-297">Improve your model</span></span>

<span data-ttu-id="379c3-298">Daha doğru tahminler alabilmesi modelinizi performansını artırmak birkaç yol vardır.</span><span class="sxs-lookup"><span data-stu-id="379c3-298">There are several ways that you can improve the performance of your model so that you can get more accurate predictions.</span></span>

### <a name="data"></a><span data-ttu-id="379c3-299">Veri</span><span class="sxs-lookup"><span data-stu-id="379c3-299">Data</span></span>

<span data-ttu-id="379c3-300">Her kullanıcı ve film kimliği için yeterli örnekleri içeren daha fazla eğitim veri ekleme, öneri model kalitesini artırmaya yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="379c3-300">Adding more training data that has enough samples for each user and movie id can help improve the quality of the recommendation model.</span></span>

<span data-ttu-id="379c3-301">[Çapraz doğrulama](../how-to-guides/train-cross-validation-ml-net.md) değerlendirme modelleri, rastgele verilerin (Bu öğreticide yaptığınız gibi yerine test veri kümesindeki verileri dışarı ayıklanıyor) alt kümelerini böler ve bazı grupların test verileri ve bazı grupları eğitin alır bir tekniktir veriler.</span><span class="sxs-lookup"><span data-stu-id="379c3-301">[Cross validation](../how-to-guides/train-cross-validation-ml-net.md) is a technique for evaluating models that randomly splits up data into subsets (instead of extracting out test data from the dataset like you did in this tutorial) and takes some of the groups as train data and some of the groups as test data.</span></span> <span data-ttu-id="379c3-302">Bu yöntem, model kalitesi açısından bölme train-test yaparak daha iyi.</span><span class="sxs-lookup"><span data-stu-id="379c3-302">This method outperforms making a train-test split in terms of model quality.</span></span>

### <a name="features"></a><span data-ttu-id="379c3-303">Özellikler</span><span class="sxs-lookup"><span data-stu-id="379c3-303">Features</span></span>

<span data-ttu-id="379c3-304">Bu öğreticide, yalnızca üç kullandığınız `Features` (`user id`, `movie id`, ve `rating`) veri kümesi tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="379c3-304">In this tutorial, you only use the three `Features` (`user id`, `movie id`, and `rating`) that are provided by the dataset.</span></span>

<span data-ttu-id="379c3-305">Bu çok iyi bir başlangıç olsa da, gerçekte, diğer öznitelikleri eklemek isteyebilirsiniz veya `Features` (örneğin, yaş, cinsiyet, coğrafi konum, vb.) kümesinde içeriyorsa.</span><span class="sxs-lookup"><span data-stu-id="379c3-305">While this is a good start, in reality you might want to add other attributes or `Features` (for example, age, gender, geo-location, etc.) if they are included in the dataset.</span></span> <span data-ttu-id="379c3-306">Daha fazla ilgili ekleme `Features` öneri modelinizin performansını artırmaya yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="379c3-306">Adding more relevant `Features` can help improve the performance of your recommendation model.</span></span>

<span data-ttu-id="379c3-307">Konusunda emin değilseniz `Features` machine learning göreviniz için en uygun olabilir, özellik katkı hesaplama (FCC) birini kullanmak de yapabilirsiniz ve [özellik permütasyon önem](../how-to-guides/determine-global-feature-importance-in-model.md), hangi ML.NET sağlar en etkili Bul `Features`.</span><span class="sxs-lookup"><span data-stu-id="379c3-307">If you are unsure about which `Features` might be the most relevant for your machine learning task, you can also make use of Feature Contribution Calculation (FCC) and [Feature Permutation Importance](../how-to-guides/determine-global-feature-importance-in-model.md), which ML.NET provides to discover the most influential `Features`.</span></span>

### <a name="algorithm-hyperparameters"></a><span data-ttu-id="379c3-308">Algoritma hiperparametreleri</span><span class="sxs-lookup"><span data-stu-id="379c3-308">Algorithm hyperparameters</span></span>

<span data-ttu-id="379c3-309">ML.NET eğitim algoritmaları iyi varsayılan sağlasa da, daha fazla performans algoritması'nın değiştirerek ince ayar yapabilirsiniz [hiperparametreleri](../resources/glossary.md#hyperparameter).</span><span class="sxs-lookup"><span data-stu-id="379c3-309">While ML.NET provides good default training algorithms, you can further fine-tune performance by changing the algorithm's [hyperparameters](../resources/glossary.md#hyperparameter).</span></span>

<span data-ttu-id="379c3-310">İçin `Matrix Factorization`, gibi hiperparametreleri ile denemeler [Numberofıterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) ve [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) , size daha iyi sonuç verdiğini olmadığını görmek için.</span><span class="sxs-lookup"><span data-stu-id="379c3-310">For `Matrix Factorization`, you can experiment with hyperparameters such as [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) and [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) to see if that gives you better results.</span></span>

<span data-ttu-id="379c3-311">Örneğin, bu öğreticide algoritması Seçenekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="379c3-311">For instance, in this tutorial the algorithm options are:</span></span>

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

### <a name="other-recommendation-algorithms"></a><span data-ttu-id="379c3-312">Diğer öneri algoritmalar</span><span class="sxs-lookup"><span data-stu-id="379c3-312">Other Recommendation Algorithms</span></span>

<span data-ttu-id="379c3-313">Matris factorization algoritma işbirliğine dayalı filtreleme ile film önerileri gerçekleştirmek için yalnızca bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="379c3-313">The matrix factorization algorithm with collaborative filtering is only one approach for performing movie recommendations.</span></span> <span data-ttu-id="379c3-314">Çoğu durumda, değil kullanılabilir derecelendirmeleri verilere sahip ve kullanıcıların film geçmiş yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="379c3-314">In many cases, you may not have the ratings data available and only have movie history available from users.</span></span> <span data-ttu-id="379c3-315">Diğer durumlarda, daha fazlasını kullanıcının derecelendirme veri olabilir.</span><span class="sxs-lookup"><span data-stu-id="379c3-315">In other cases, you may have more than just the user’s rating data.</span></span>

| <span data-ttu-id="379c3-316">Algoritması</span><span class="sxs-lookup"><span data-stu-id="379c3-316">Algorithm</span></span>       | <span data-ttu-id="379c3-317">Senaryo</span><span class="sxs-lookup"><span data-stu-id="379c3-317">Scenario</span></span>           | <span data-ttu-id="379c3-318">Örnek</span><span class="sxs-lookup"><span data-stu-id="379c3-318">Sample</span></span>  |
| ------------- |:-------------:| -----:|
| <span data-ttu-id="379c3-319">Bir sınıf matris Factorization</span><span class="sxs-lookup"><span data-stu-id="379c3-319">One Class Matrix Factorization</span></span> | <span data-ttu-id="379c3-320">Kullanıcı kimliği ve movieId yalnızca varsa bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="379c3-320">Use this when you only have userId and movieId.</span></span> <span data-ttu-id="379c3-321">Ortak satın alma senaryosu bu stil önerileri temel alır ve ürünleri sık birlikte müşterilere ürün kendi satın alma siparişi geçmişi dayalı bir kümesi dtu'lara anlamına satın.</span><span class="sxs-lookup"><span data-stu-id="379c3-321">This style of recommendation is based upon the co-purchase scenario, or products frequently bought together, which means it will recommend to customers a set of products based upon their own purchase order history.</span></span> | [<span data-ttu-id="379c3-322">> deneyin</span><span class="sxs-lookup"><span data-stu-id="379c3-322">>Try it out</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/MatrixFactorization_ProductRecommendation) |
| <span data-ttu-id="379c3-323">Alan kullanan Factorization makineler</span><span class="sxs-lookup"><span data-stu-id="379c3-323">Field Aware Factorization Machines</span></span> | <span data-ttu-id="379c3-324">Daha fazla özellik UserID, ProductID ve derecelendirme (örneğin, ürün açıklaması veya ürün fiyatı) dışında olduğunda önerilerde için bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="379c3-324">Use this to make recommendations when you have more Features beyond userId, productId, and rating (such as product description or product price).</span></span> <span data-ttu-id="379c3-325">Bu yöntem, işbirliğine dayalı bir filtre yaklaşım da kullanır.</span><span class="sxs-lookup"><span data-stu-id="379c3-325">This method also uses a collaborative filtering approach.</span></span> | [<span data-ttu-id="379c3-326">> deneyin</span><span class="sxs-lookup"><span data-stu-id="379c3-326">>Try it out</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/Recommendation-MovieRecommender) |

### <a name="new-user-scenario"></a><span data-ttu-id="379c3-327">Yeni kullanıcı senaryosu</span><span class="sxs-lookup"><span data-stu-id="379c3-327">New user scenario</span></span>

<span data-ttu-id="379c3-328">Ortak filtreleme bir yaygın sorun çıkarımı gelen çizmek için önceki veri içermeyen yeni bir kullanıcı varsa, hazırlıksız başlatma sorunudur.</span><span class="sxs-lookup"><span data-stu-id="379c3-328">One common problem in collaborative filtering is the cold start problem, which is when you have a new user with no previous data to draw inferences from.</span></span> <span data-ttu-id="379c3-329">Bu sorun genellikle bir profil oluşturmak için yeni kullanıcılar isteyerek çözülür ve örneği için oranı filmler, geçmişte gördünüz.</span><span class="sxs-lookup"><span data-stu-id="379c3-329">This problem is often solved by asking new users to create a profile and, for instance, rate movies they have seen in the past.</span></span> <span data-ttu-id="379c3-330">Bu yöntem, kullanıcı bazı yük koyar, ancak hiçbir derecelendirme geçmişi ile yeni kullanıcılar için bazı başlangıç verileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="379c3-330">While this method puts some burden on the user, it provides some starting data for new users with no rating history.</span></span>

## <a name="resources"></a><span data-ttu-id="379c3-331">Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="379c3-331">Resources</span></span>

<span data-ttu-id="379c3-332">Bu öğreticide kullanılan veri türetilir [MovieLens Dataset](http://files.grouplens.org/datasets/movielens/).</span><span class="sxs-lookup"><span data-stu-id="379c3-332">The data used in this tutorial is derived from [MovieLens Dataset](http://files.grouplens.org/datasets/movielens/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="379c3-333">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="379c3-333">Next steps</span></span>

<span data-ttu-id="379c3-334">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="379c3-334">In this tutorial, you learned how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="379c3-335">Bir machine learning algoritması seçin</span><span class="sxs-lookup"><span data-stu-id="379c3-335">Select a machine learning algorithm</span></span>
> * <span data-ttu-id="379c3-336">Verilerinizi yüklemek ve hazırlamak</span><span class="sxs-lookup"><span data-stu-id="379c3-336">Prepare and load your data</span></span>
> * <span data-ttu-id="379c3-337">Yapı ve model eğitme</span><span class="sxs-lookup"><span data-stu-id="379c3-337">Build and train a model</span></span>
> * <span data-ttu-id="379c3-338">Bir modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="379c3-338">Evaluate a model</span></span>
> * <span data-ttu-id="379c3-339">Dağıtma ve bir modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="379c3-339">Deploy and consume a model</span></span>

<span data-ttu-id="379c3-340">Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="379c3-340">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="379c3-341">Yaklaşım analizi</span><span class="sxs-lookup"><span data-stu-id="379c3-341">Sentiment Analysis</span></span>](sentiment-analysis.md)
