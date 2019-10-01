---
title: 'Öğretici: önceden eğitilen bir TensorFlow modeli kullanarak film incelemelerinin yaklaşımını çözümleyin'
description: Bu öğreticide, Web sitesi açıklamalarında yaklaşımı sınıflandırmak için önceden eğitilen bir TensorFlow modelinin nasıl kullanılacağı gösterilmektedir. İkili yaklaşım Sınıflandırıcısı, Visual Studio kullanılarak C# geliştirilen bir konsol uygulamasıdır.
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc
ms.author: nakersha
author: natke
ms.openlocfilehash: e25e884769ad62d3d888986b1475000b543b24b1
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700933"
---
# <a name="tutorial-analyze-sentiment-of-movie-reviews-using-a-pre-trained-tensorflow-model-in-mlnet"></a><span data-ttu-id="2642a-104">Öğretici: ML.NET 'de önceden eğitilen bir TensorFlow modeli kullanarak film incelemelerinin yaklaşımını çözümleyin</span><span class="sxs-lookup"><span data-stu-id="2642a-104">Tutorial: Analyze sentiment of movie reviews using a pre-trained TensorFlow model in ML.NET</span></span>

<span data-ttu-id="2642a-105">Bu öğreticide, Web sitesi açıklamalarında yaklaşımı sınıflandırmak için önceden eğitilen bir TensorFlow modelinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2642a-105">This tutorial shows you how to use a pre-trained TensorFlow model to classify sentiment in website comments.</span></span> <span data-ttu-id="2642a-106">İkili yaklaşım Sınıflandırıcısı, Visual Studio kullanılarak C# geliştirilen bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="2642a-106">The binary sentiment classifier is a C# console application developed using Visual Studio.</span></span>

<span data-ttu-id="2642a-107">Bu öğreticide kullanılan TensorFlow modeli, ıMDB veritabanından Film İncelemeleri kullanılarak eğitildi.</span><span class="sxs-lookup"><span data-stu-id="2642a-107">The TensorFlow model used in this tutorial was trained using movie reviews from the IMDB database.</span></span> <span data-ttu-id="2642a-108">Uygulamayı geliştirmeyi bitirdikten sonra, film gözden geçirme metni sağlayabileceksiniz ve uygulama Gözden geçirmedeki pozitif veya negatif bir yaklaşım olup olmadığını söyleyecektir.</span><span class="sxs-lookup"><span data-stu-id="2642a-108">Once you have finished developing the application, you will be able to supply movie review text and the application will tell you whether the review has positive or negative sentiment.</span></span>

<span data-ttu-id="2642a-109">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="2642a-109">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="2642a-110">Önceden eğitilen bir TensorFlow modeli yükleme</span><span class="sxs-lookup"><span data-stu-id="2642a-110">Load a pre-trained TensorFlow model</span></span>
> * <span data-ttu-id="2642a-111">Web sitesi açıklama metnini model için uygun özelliklere Dönüştür</span><span class="sxs-lookup"><span data-stu-id="2642a-111">Transform website comment text into features suitable for the model</span></span>
> * <span data-ttu-id="2642a-112">Tahmin yapmak için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="2642a-112">Use the model to make a prediction</span></span>

<span data-ttu-id="2642a-113">Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2642a-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2642a-114">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="2642a-114">Prerequisites</span></span>

* <span data-ttu-id="2642a-115">[Visual Studio 2017 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ".NET Core platformlar arası geliştirme" iş yükü yüklendi.</span><span class="sxs-lookup"><span data-stu-id="2642a-115">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="setup"></a><span data-ttu-id="2642a-116">Kurulum</span><span class="sxs-lookup"><span data-stu-id="2642a-116">Setup</span></span>

### <a name="create-the-application"></a><span data-ttu-id="2642a-117">Uygulamayı oluşturma</span><span class="sxs-lookup"><span data-stu-id="2642a-117">Create the application</span></span>

1. <span data-ttu-id="2642a-118">"TextClassificationTF" adlı bir **.NET Core konsol uygulaması** oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2642a-118">Create a **.NET Core Console Application** called "TextClassificationTF".</span></span>

2. <span data-ttu-id="2642a-119">Veri kümesi dosyalarınızı kaydetmek için projenizde *veri* adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2642a-119">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="2642a-120">**Microsoft.ml NuGet paketini**yükler:</span><span class="sxs-lookup"><span data-stu-id="2642a-120">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="2642a-121">Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="2642a-121">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="2642a-122">Paket kaynağı olarak "nuget.org" öğesini seçin ve sonra da **tarayıcı** sekmesini seçin. **Microsoft.ml**için arama yapın, istediğiniz paketi seçin ve sonra da **Install** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="2642a-122">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="2642a-123">Kabul etmiş ile yüklemeye, seçtiğiniz paketin lisans koşullarına devam edin.</span><span class="sxs-lookup"><span data-stu-id="2642a-123">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span> <span data-ttu-id="2642a-124">**Microsoft. ml. TensorFlow**için bu adımları tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="2642a-124">Repeat these steps for **Microsoft.ML.TensorFlow**.</span></span>

### <a name="add-the-tensorflow-model-to-the-project"></a><span data-ttu-id="2642a-125">TensorFlow modelini projeye ekleme</span><span class="sxs-lookup"><span data-stu-id="2642a-125">Add the TensorFlow model to the project</span></span>

> [!NOTE]
> <span data-ttu-id="2642a-126">Bu öğreticinin modeli [DotNet/machinöğrenim-TestData](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) GitHub deposundan.</span><span class="sxs-lookup"><span data-stu-id="2642a-126">The model for this tutorial is from the [dotnet/machinelearning-testdata](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) GitHub repo.</span></span> <span data-ttu-id="2642a-127">Model, TensorFlow SavedModel biçimindedir.</span><span class="sxs-lookup"><span data-stu-id="2642a-127">The model is in TensorFlow SavedModel format.</span></span>

1. <span data-ttu-id="2642a-128">[Sentiment_model ZIP dosyasını](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true)indirin ve sıkıştırmayı açın.</span><span class="sxs-lookup"><span data-stu-id="2642a-128">Download the [sentiment_model zip file](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true), and unzip.</span></span>

    <span data-ttu-id="2642a-129">ZIP dosyası şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="2642a-129">The zip file contains:</span></span>

    * <span data-ttu-id="2642a-130">`saved_model.pb`: TensorFlow modelinin kendisi.</span><span class="sxs-lookup"><span data-stu-id="2642a-130">`saved_model.pb`: the TensorFlow model itself.</span></span> <span data-ttu-id="2642a-131">Model, bir ıMDB İnceleme dizesindeki metni temsil eden özelliklerin sabit bir uzunluğunu (boyut 600) tamsayı dizisini alır ve 1 ' e kadar olan iki olasılıkların çıkışını verir: giriş incelemesinin pozitif yaklaşım olduğu ve giriş incelemesinin sahip olduğu olasılık negatif yaklaşım.</span><span class="sxs-lookup"><span data-stu-id="2642a-131">The model takes a fixed length (size 600) integer array of features representing the text in an IMDB review string, and outputs two probabilities which sum to 1: the probability that the input review has positive sentiment, and the probability that the input review has negative sentiment.</span></span>
    * <span data-ttu-id="2642a-132">`imdb_word_index.csv`: tek sözcüklerden bir tamsayı değere eşleme.</span><span class="sxs-lookup"><span data-stu-id="2642a-132">`imdb_word_index.csv`: a mapping from individual words to an integer value.</span></span> <span data-ttu-id="2642a-133">Eşleme, TensorFlow modelinin giriş özelliklerini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2642a-133">The mapping is used to generate the input features for the TensorFlow model.</span></span>

2. <span data-ttu-id="2642a-134">En içteki `sentiment_model` dizininin içeriğini *TextClassificationTF* projenizin `sentiment_model` dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="2642a-134">Copy the contents of the innermost `sentiment_model` directory into your *TextClassificationTF* project `sentiment_model` directory.</span></span> <span data-ttu-id="2642a-135">Bu dizin, aşağıdaki görüntüde gösterildiği gibi, bu öğretici için gereken modeli ve ek destek dosyalarını içerir:</span><span class="sxs-lookup"><span data-stu-id="2642a-135">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![sentiment_model Dizin içeriği](./media/text-classification-tf/sentiment-model-files.png)

3. <span data-ttu-id="2642a-137">Çözüm Gezgini, `sentiment_model` Dizin ve alt dizinindeki dosyaların her birine sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="2642a-137">In Solution Explorer, right-click each of the files in the `sentiment_model` directory and subdirectory and select **Properties**.</span></span> <span data-ttu-id="2642a-138">**Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="2642a-138">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="add-using-statements-and-global-variables"></a><span data-ttu-id="2642a-139">Using deyimleri ve genel değişkenler ekleme</span><span class="sxs-lookup"><span data-stu-id="2642a-139">Add using statements and global variables</span></span>

1. <span data-ttu-id="2642a-140">*Program.cs* dosyasının en üstüne aşağıdaki ek `using` deyimlerini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2642a-140">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TextClassificationTF/Program.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="2642a-141">Kaydedilen model dosyası yolunu ve özellik vektörü uzunluğunu tutmak için `Main` yönteminin üzerinde doğrudan iki genel değişken oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2642a-141">Create two global variables right above the `Main` method to hold the saved model file path, and the feature vector length.</span></span>

   [!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TextClassificationTF/Program.cs#DeclareGlobalVariables "Declare global variables")]

    * <span data-ttu-id="2642a-142">`_modelPath`, eğitilen modelin dosya yoludur.</span><span class="sxs-lookup"><span data-stu-id="2642a-142">`_modelPath` is the file path of the trained model.</span></span>
    * <span data-ttu-id="2642a-143">`FeatureLength`, modelin beklediği tamsayı özelliği dizisinin uzunluğudur.</span><span class="sxs-lookup"><span data-stu-id="2642a-143">`FeatureLength` is the length of the integer feature array that the model is expecting.</span></span>

### <a name="model-the-data"></a><span data-ttu-id="2642a-144">Verileri modelleyin</span><span class="sxs-lookup"><span data-stu-id="2642a-144">Model the data</span></span>

<span data-ttu-id="2642a-145">Film İncelemeleri, ücretsiz form metinlerdir.</span><span class="sxs-lookup"><span data-stu-id="2642a-145">Movie reviews are free form text.</span></span> <span data-ttu-id="2642a-146">Uygulamanız, metni bir dizi farklı aşamada model tarafından beklenen giriş biçimine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="2642a-146">Your application converts the text into the input format expected by the model in a number of discrete stages.</span></span>

<span data-ttu-id="2642a-147">Birincisi, metni ayrı sözcüklere bölmek ve her bir sözcüğü bir tamsayı kodlamasıyla eşlemek için belirtilen eşleme dosyasını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="2642a-147">The first is to split the text into separate words and use the provided mapping file to map each word onto an integer encoding.</span></span> <span data-ttu-id="2642a-148">Bu dönüştürmenin sonucu, tümcedeki sözcüklerin sayısına karşılık gelen uzunluğa sahip bir değişken uzunluklu tamsayı dizisidir.</span><span class="sxs-lookup"><span data-stu-id="2642a-148">The result of this transformation is a variable length integer array with a length corresponding to the number of words in the sentence.</span></span>

|<span data-ttu-id="2642a-149">Özellik</span><span class="sxs-lookup"><span data-stu-id="2642a-149">Property</span></span>| <span data-ttu-id="2642a-150">Değer</span><span class="sxs-lookup"><span data-stu-id="2642a-150">Value</span></span>|<span data-ttu-id="2642a-151">Tür</span><span class="sxs-lookup"><span data-stu-id="2642a-151">Type</span></span>|
|-------------|-----------------------|------|
|<span data-ttu-id="2642a-152">Belgemetinmetni</span><span class="sxs-lookup"><span data-stu-id="2642a-152">ReviewText</span></span>|<span data-ttu-id="2642a-153">Bu film gerçekten iyi</span><span class="sxs-lookup"><span data-stu-id="2642a-153">this film is really good</span></span>|<span data-ttu-id="2642a-154">dize</span><span class="sxs-lookup"><span data-stu-id="2642a-154">string</span></span>|
|<span data-ttu-id="2642a-155">VariableLengthFeatures</span><span class="sxs-lookup"><span data-stu-id="2642a-155">VariableLengthFeatures</span></span>|<span data-ttu-id="2642a-156">14, 22, 9, 66, 78,...</span><span class="sxs-lookup"><span data-stu-id="2642a-156">14,22,9,66,78,...</span></span> |<span data-ttu-id="2642a-157">int []</span><span class="sxs-lookup"><span data-stu-id="2642a-157">int[]</span></span>|

<span data-ttu-id="2642a-158">Değişken uzunluğu özellik dizisi daha sonra sabit 600 uzunluğuna yeniden boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="2642a-158">The variable length feature array is then resized to a fixed length of 600.</span></span> <span data-ttu-id="2642a-159">Bu, TensorFlow modelinin beklediği uzunluktadır.</span><span class="sxs-lookup"><span data-stu-id="2642a-159">This is the length that the TensorFlow model expects.</span></span>

|<span data-ttu-id="2642a-160">Özellik</span><span class="sxs-lookup"><span data-stu-id="2642a-160">Property</span></span>| <span data-ttu-id="2642a-161">Değer</span><span class="sxs-lookup"><span data-stu-id="2642a-161">Value</span></span>|<span data-ttu-id="2642a-162">Tür</span><span class="sxs-lookup"><span data-stu-id="2642a-162">Type</span></span>|
|-------------|-----------------------|------|
|<span data-ttu-id="2642a-163">Belgemetinmetni</span><span class="sxs-lookup"><span data-stu-id="2642a-163">ReviewText</span></span>|<span data-ttu-id="2642a-164">Bu film gerçekten iyi</span><span class="sxs-lookup"><span data-stu-id="2642a-164">this film is really good</span></span>|<span data-ttu-id="2642a-165">dize</span><span class="sxs-lookup"><span data-stu-id="2642a-165">string</span></span>|
|<span data-ttu-id="2642a-166">VariableLengthFeatures</span><span class="sxs-lookup"><span data-stu-id="2642a-166">VariableLengthFeatures</span></span>|<span data-ttu-id="2642a-167">14, 22, 9, 66, 78,...</span><span class="sxs-lookup"><span data-stu-id="2642a-167">14,22,9,66,78,...</span></span> |<span data-ttu-id="2642a-168">int []</span><span class="sxs-lookup"><span data-stu-id="2642a-168">int[]</span></span>|
|<span data-ttu-id="2642a-169">Özellikler</span><span class="sxs-lookup"><span data-stu-id="2642a-169">Features</span></span>|<span data-ttu-id="2642a-170">14, 22, 9, 66, 78,...</span><span class="sxs-lookup"><span data-stu-id="2642a-170">14,22,9,66,78,...</span></span> |<span data-ttu-id="2642a-171">Tamsayı [600]</span><span class="sxs-lookup"><span data-stu-id="2642a-171">int[600]</span></span>|

1. <span data-ttu-id="2642a-172">@No__t-0 yönteminden sonra giriş verileriniz için bir sınıf oluşturun:</span><span class="sxs-lookup"><span data-stu-id="2642a-172">Create a class for your input data, after the `Main` method:</span></span>

    [!code-csharp[MovieReviewClass](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#MovieReviewClass "Declare movie review type")]

    <span data-ttu-id="2642a-173">@No__t-0 olan giriş veri sınıfında kullanıcı açıklamaları için bir `string` (`ReviewText`) vardır.</span><span class="sxs-lookup"><span data-stu-id="2642a-173">The input data class, `MovieReview`, has a `string` for user comments (`ReviewText`).</span></span>

1. <span data-ttu-id="2642a-174">@No__t-0 yönteminden sonra değişken uzunluklu özellikler için bir sınıf oluşturun:</span><span class="sxs-lookup"><span data-stu-id="2642a-174">Create a class for the variable length features, after the `Main` method:</span></span>

    [!code-csharp[VariableLengthFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#VariableLengthFeatures "Declare variable length features type")]

    <span data-ttu-id="2642a-175">@No__t-0 özelliğinin vektör olarak belirlemek için bir [Vectortype](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="2642a-175">The `VariableLengthFeatures` property has a [VectorType](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) attribute to designate it as a vector.</span></span>  <span data-ttu-id="2642a-176">Tüm vektör öğeleri aynı türde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2642a-176">All of the vector elements must be the same type.</span></span> <span data-ttu-id="2642a-177">Çok sayıda sütun içeren veri kümelerinde, birden fazla sütunu tek bir vektör olarak yüklemek, veri dönüştürmeleri uyguladığınızda veri geçişlerinin sayısını azaltır.</span><span class="sxs-lookup"><span data-stu-id="2642a-177">In data sets with a large number of columns, loading multiple columns as a single vector reduces the number of data passes when you apply data transformations.</span></span>

    <span data-ttu-id="2642a-178">Bu sınıf `ResizeFeatures` eyleminde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2642a-178">This class is used in the `ResizeFeatures` action.</span></span> <span data-ttu-id="2642a-179">Özelliklerinin adları (Bu durumda yalnızca bir tane), DataView içindeki hangi sütunların özel eşleme eylemine _giriş_ olarak kullanılabileceğini göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2642a-179">The names of its properties (in this case only one) are used to indicate which columns in the DataView can be used as the _input_ to the custom mapping action.</span></span>

1. <span data-ttu-id="2642a-180">@No__t-0 yönteminden sonra sabit uzunluklu özellikler için bir sınıf oluşturun:</span><span class="sxs-lookup"><span data-stu-id="2642a-180">Create a class for the fixed length features, after the `Main` method:</span></span>

    [!code-csharp[FixedLengthFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#FixedLengthFeatures)]

    <span data-ttu-id="2642a-181">Bu sınıf `ResizeFeatures` eyleminde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2642a-181">This class is used in the `ResizeFeatures` action.</span></span> <span data-ttu-id="2642a-182">Özelliklerinin adları (Bu durumda yalnızca bir tane), DataView içindeki hangi sütunların özel eşleme eyleminin _çıktısı_ olarak kullanılabileceğini göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2642a-182">The names of its properties (in this case only one) are used to indicate which columns in the DataView can be used as the _output_ of the custom mapping action.</span></span>

    <span data-ttu-id="2642a-183">@No__t-0 özelliğinin adının TensorFlow modeliyle belirlendiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2642a-183">Note that the name of the property `Features` is determined by the TensorFlow model.</span></span> <span data-ttu-id="2642a-184">Bu özellik adını değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="2642a-184">You cannot change this property name.</span></span>

1. <span data-ttu-id="2642a-185">@No__t-0 yönteminden sonra tahmin için bir sınıf oluşturun:</span><span class="sxs-lookup"><span data-stu-id="2642a-185">Create a class for the prediction after the `Main` method:</span></span>

    [!code-csharp[Prediction](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#Prediction "Declare prediction class")]

    <span data-ttu-id="2642a-186">`MovieReviewSentimentPrediction`, model eğitiminden sonra kullanılan tahmin sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="2642a-186">`MovieReviewSentimentPrediction` is the prediction class used after the model training.</span></span> <span data-ttu-id="2642a-187">`MovieReviewSentimentPrediction` tek bir `float` dizisine (`Prediction`) ve `VectorType` özniteliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2642a-187">`MovieReviewSentimentPrediction` has a single `float` array (`Prediction`) and a `VectorType` attribute.</span></span>

### <a name="create-the-mlcontext-lookup-dictionary-and-action-to-resize-features"></a><span data-ttu-id="2642a-188">Özellikleri yeniden boyutlandırmak için MLContext, arama sözlüğü ve eylemi oluşturma</span><span class="sxs-lookup"><span data-stu-id="2642a-188">Create the MLContext, lookup dictionary, and action to resize features</span></span>

<span data-ttu-id="2642a-189">[Mlcontext sınıfı](xref:Microsoft.ML.MLContext) tüm ml.NET işlemleri için bir başlangıç noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="2642a-189">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="2642a-190">@No__t başlatılıyor-0, model oluşturma iş akışı nesneleri genelinde paylaşılabilen yeni bir ML.NET ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2642a-190">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="2642a-191">Bu, kavramsal olarak, Entity Framework `DBContext` ' a benzer.</span><span class="sxs-lookup"><span data-stu-id="2642a-191">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

1. <span data-ttu-id="2642a-192">@No__t-1 yöntemindeki `Console.WriteLine("Hello World!")` satırını, mlContext değişkenini bildirmek ve başlatmak için aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="2642a-192">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

   [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateMLContext "Create the ML Context")]

1. <span data-ttu-id="2642a-193">Aşağıdaki tabloda görüldüğü gibi, bir dosyadan eşleme verilerini yüklemek için [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) metodunu kullanarak sözcükleri tamsayı olarak kodlamak için bir sözlük oluşturun:</span><span class="sxs-lookup"><span data-stu-id="2642a-193">Create a dictionary to encode words as integers by using the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method to load mapping data from a file, as seen in the following table:</span></span>

    |<span data-ttu-id="2642a-194">Word</span><span class="sxs-lookup"><span data-stu-id="2642a-194">Word</span></span>     |<span data-ttu-id="2642a-195">Dizin</span><span class="sxs-lookup"><span data-stu-id="2642a-195">Index</span></span>    |
    |---------|---------|
    |<span data-ttu-id="2642a-196">öğre</span><span class="sxs-lookup"><span data-stu-id="2642a-196">kids</span></span>     |  <span data-ttu-id="2642a-197">362</span><span class="sxs-lookup"><span data-stu-id="2642a-197">362</span></span>    |
    |<span data-ttu-id="2642a-198">istiyorum</span><span class="sxs-lookup"><span data-stu-id="2642a-198">want</span></span>     |  <span data-ttu-id="2642a-199">181</span><span class="sxs-lookup"><span data-stu-id="2642a-199">181</span></span>    |
    |<span data-ttu-id="2642a-200">yanlış</span><span class="sxs-lookup"><span data-stu-id="2642a-200">wrong</span></span>    |  <span data-ttu-id="2642a-201">355</span><span class="sxs-lookup"><span data-stu-id="2642a-201">355</span></span>    |
    |<span data-ttu-id="2642a-202">efektler</span><span class="sxs-lookup"><span data-stu-id="2642a-202">effects</span></span>  |  <span data-ttu-id="2642a-203">302</span><span class="sxs-lookup"><span data-stu-id="2642a-203">302</span></span>    |
    |<span data-ttu-id="2642a-204">rahatsızlık</span><span class="sxs-lookup"><span data-stu-id="2642a-204">feeling</span></span>  |  <span data-ttu-id="2642a-205">547</span><span class="sxs-lookup"><span data-stu-id="2642a-205">547</span></span>    |

    <span data-ttu-id="2642a-206">Arama eşlemesini oluşturmak için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2642a-206">Add the code below to create the lookup map:</span></span>

    [!code-csharp[CreateLookupMap](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateLookupMap)]

1. <span data-ttu-id="2642a-207">Değişken uzunluklu kelime tamsayı dizisinin bir sonraki kod satırı ile sabit boyutlu bir tamsayı dizisine yeniden boyutlandırılması için bir `Action` ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2642a-207">Add an `Action` to resize the variable length word integer array to an integer array of fixed size, with the next lines of code:</span></span>

   [!code-csharp[ResizeFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#ResizeFeatures)]

## <a name="load-the-pre-trained-tensorflow-model"></a><span data-ttu-id="2642a-208">Önceden eğitilen TensorFlow modelini yükleme</span><span class="sxs-lookup"><span data-stu-id="2642a-208">Load the pre-trained TensorFlow model</span></span>

1. <span data-ttu-id="2642a-209">TensorFlow modelini yüklemek için kod ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2642a-209">Add code to load the TensorFlow model:</span></span>

    [!code-csharp[LoadTensorFlowModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#LoadTensorFlowModel)]

    <span data-ttu-id="2642a-210">Model yüklendikten sonra, giriş ve çıkış şemasını ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2642a-210">Once the model is loaded, you can extract its input and output schema.</span></span> <span data-ttu-id="2642a-211">Şemalar yalnızca ilgi ve öğrenme için görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="2642a-211">The schemas are displayed for interest and learning only.</span></span> <span data-ttu-id="2642a-212">Son uygulamanın çalışması için bu koda ihtiyacınız yoktur:</span><span class="sxs-lookup"><span data-stu-id="2642a-212">You do not need this code for the final application to function:</span></span>

    [!code-csharp[GetModelSchema](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#GetModelSchema)]

    <span data-ttu-id="2642a-213">Giriş şeması, tamsayı kodlamalı sözcüklerin sabit uzunluklu dizisidir.</span><span class="sxs-lookup"><span data-stu-id="2642a-213">The input schema is the fixed-length array of integer encoded words.</span></span> <span data-ttu-id="2642a-214">Çıktı şeması, bir gözden geçirme yaklaşımını negatif mi yoksa pozitif mi olduğunu gösteren bir dizi olasılıkların dizisidir.</span><span class="sxs-lookup"><span data-stu-id="2642a-214">The output schema is a float array of probabilities indicating whether a review's sentiment is negative, or positive .</span></span> <span data-ttu-id="2642a-215">Bu değerler, pozitif olma olasılığı olarak 1 ' e kadar toplamdır.</span><span class="sxs-lookup"><span data-stu-id="2642a-215">These values sum to 1, as the probability of being positive is the complement of the probability of the sentiment being negative.</span></span>

## <a name="create-the-mlnet-pipeline"></a><span data-ttu-id="2642a-216">ML.NET işlem hattını oluşturma</span><span class="sxs-lookup"><span data-stu-id="2642a-216">Create the ML.NET pipeline</span></span>

1. <span data-ttu-id="2642a-217">Bir sonraki kod satırı olarak sözcükleri sözcüklere eklemek için, işlem hattını oluşturun ve giriş metnini [Tokenizeıntowords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) dönüşümünü kullanarak sözcüklere bölün:</span><span class="sxs-lookup"><span data-stu-id="2642a-217">Create the pipeline and split the input text into words using [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transform to break the text into words as the next line of code:</span></span>

   [!code-csharp[TokenizeIntoWords](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#TokenizeIntoWords)]

   <span data-ttu-id="2642a-218">[Tokenizeıntowords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) dönüşümü, metni/dizeyi sözcüklere ayrıştırmak için boşluk kullanır.</span><span class="sxs-lookup"><span data-stu-id="2642a-218">The [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transform uses spaces to parse the text/string into words.</span></span> <span data-ttu-id="2642a-219">Yeni bir sütun oluşturur ve her giriş dizesini Kullanıcı tanımlı ayırıcıya göre alt dizelerin vektörüne böler.</span><span class="sxs-lookup"><span data-stu-id="2642a-219">It creates a new column and splits each input string to a vector of substrings based on the user-defined separator.</span></span>

1. <span data-ttu-id="2642a-220">Yukarıda bildirdiğiniz arama tablosunu kullanarak kelimeleri tamsayı kodlamasıyla eşleyin:</span><span class="sxs-lookup"><span data-stu-id="2642a-220">Map the words onto their integer encoding using the lookup table that you declared above:</span></span>

    [!code-csharp[MapValue](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#MapValue)]

1. <span data-ttu-id="2642a-221">Değişken uzunluğu tamsayı kodlamalarını modelin gerektirdiği sabit uzunluğa göre yeniden boyutlandırın:</span><span class="sxs-lookup"><span data-stu-id="2642a-221">Resize the variable length integer encodings to the fixed-length one required by the model:</span></span>

    [!code-csharp[CustomMapping](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CustomMapping)]

1. <span data-ttu-id="2642a-222">Girişi yüklenen TensorFlow modeliyle sınıflandırın:</span><span class="sxs-lookup"><span data-stu-id="2642a-222">Classify the input with the loaded TensorFlow model:</span></span>

    [!code-csharp[ScoreTensorFlowModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#ScoreTensorFlowModel)]

    <span data-ttu-id="2642a-223">TensorFlow model çıkışı `Prediction/Softmax` olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="2642a-223">The TensorFlow model output is called `Prediction/Softmax`.</span></span> <span data-ttu-id="2642a-224">@No__t-0 adının TensorFlow modeliyle belirlendiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2642a-224">Note that the name `Prediction/Softmax` is determined by the TensorFlow model.</span></span> <span data-ttu-id="2642a-225">Bu adı değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="2642a-225">You cannot change this name.</span></span>

1. <span data-ttu-id="2642a-226">Çıkış tahmini için yeni bir sütun oluşturun:</span><span class="sxs-lookup"><span data-stu-id="2642a-226">Create a new column for the output prediction:</span></span>

    [!code-csharp[SnippetCopyColumns](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#SnippetCopyColumns)]

    <span data-ttu-id="2642a-227">@No__t-0 sütununu bir C# sınıfta özellik olarak kullanılabilecek bir adla birine kopyalamanız gerekir: `Prediction`.</span><span class="sxs-lookup"><span data-stu-id="2642a-227">You need to copy the `Prediction/Softmax` column into one with a name that can be used as a property in a C# class: `Prediction`.</span></span> <span data-ttu-id="2642a-228">C# Özellik adında `/` karakterine izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="2642a-228">The `/` character is not allowed in a C# property name.</span></span>

## <a name="create-the-mlnet-model-from-the-pipeline"></a><span data-ttu-id="2642a-229">İşlem hattından ML.NET modeli oluşturma</span><span class="sxs-lookup"><span data-stu-id="2642a-229">Create the ML.NET model from the pipeline</span></span>

1. <span data-ttu-id="2642a-230">Ardışık düzen aracılığıyla model oluşturmak için kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2642a-230">Add the code to create the model from the pipeline:</span></span>

    [!code-csharp[SnippetCreateModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#SnippetCreateModel)]

    <span data-ttu-id="2642a-231">@No__t-0 yöntemini çağırarak, işlem hattındaki tahmini zincirinden bir ml.net modeli oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2642a-231">An ML.NET model is created from the chain of estimators in the pipeline by calling the `Fit` method.</span></span> <span data-ttu-id="2642a-232">Bu durumda, TensorFlow modeli önceden eğitilen için, modeli oluşturmak üzere herhangi bir veri vermedik.</span><span class="sxs-lookup"><span data-stu-id="2642a-232">In this case, we are not fitting any data to create the model, as the TensorFlow model has already been previously trained.</span></span> <span data-ttu-id="2642a-233">@No__t-0 yönteminin gereksinimlerini karşılamak için boş bir veri görünümü nesnesi sağlıyoruz.</span><span class="sxs-lookup"><span data-stu-id="2642a-233">We supply an empty data view object to satisfy the requirements of the `Fit` method.</span></span>

## <a name="use-the-model-to-make-a-prediction"></a><span data-ttu-id="2642a-234">Tahmin yapmak için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="2642a-234">Use the model to make a prediction</span></span>

1. <span data-ttu-id="2642a-235">@No__t-1 yönteminin altına `PredictSentiment` yöntemini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2642a-235">Add the `PredictSentiment` method below the `Main` method:</span></span>

    ```csharp
    public static void PredictSentiment(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. <span data-ttu-id="2642a-236">@No__t-1 yönteminde ilk satır olarak `PredictionEngine` oluşturmak için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2642a-236">Add the following code to create the `PredictionEngine` as the first line in the `PredictSentiment()` method:</span></span>

    [!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreatePredictionEngine)]

    <span data-ttu-id="2642a-237">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneğinde tahmin gerçekleştirmenize olanak tanıyan, KULLANıŞLı bir API 'dir.</span><span class="sxs-lookup"><span data-stu-id="2642a-237">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="2642a-238">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) , iş parçacığı açısından güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="2642a-238">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="2642a-239">Tek iş parçacıklı veya prototip ortamlarında kullanılması kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="2642a-239">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="2642a-240">Üretim ortamlarında geliştirilmiş performans ve iş parçacığı güvenliği için, uygulamanızda kullanılmak üzere [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) nesnesi oluşturan `PredictionEnginePool` hizmetini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2642a-240">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="2642a-241">[ASP.NET Core Web API 'sinde `PredictionEnginePool` ' i nasıl kullanacağınızı](https://docs.microsoft.com/en-us/dotnet/machine-learning/how-to-guides/serve-model-web-api-ml-net#register-predictionenginepool-for-use-in-the-application) öğrenmek için bu kılavuza bakın</span><span class="sxs-lookup"><span data-stu-id="2642a-241">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](https://docs.microsoft.com/en-us/dotnet/machine-learning/how-to-guides/serve-model-web-api-ml-net#register-predictionenginepool-for-use-in-the-application)</span></span>

    > [!NOTE]
    > <span data-ttu-id="2642a-242">`PredictionEnginePool` hizmet uzantısı Şu anda önizleme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="2642a-242">`PredictionEnginePool` service extension is currently in preview.</span></span>

1. <span data-ttu-id="2642a-243">@No__t-1 ' in bir örneğini oluşturarak eğitilen modelin tahminini `Predict()` yönteminde test etmek için bir açıklama ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2642a-243">Add a comment to test the trained model's prediction in the `Predict()` method by creating an instance of `MovieReview`:</span></span>

    [!code-csharp[CreateTestData](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateTestData)]

1. <span data-ttu-id="2642a-244">@No__t-1 yöntemine sonraki kod satırlarını ekleyerek test açıklama verilerini `Prediction Engine` ' a geçirin:</span><span class="sxs-lookup"><span data-stu-id="2642a-244">Pass the test comment data to the `Prediction Engine` by adding the next lines of code in the `PredictSentiment()` method:</span></span>

    [!code-csharp[Predict](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#Predict)]

1. <span data-ttu-id="2642a-245">[Tahmin ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi, tek bir veri satırı üzerinde bir tahmin yapar:</span><span class="sxs-lookup"><span data-stu-id="2642a-245">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data:</span></span>

    |<span data-ttu-id="2642a-246">Özellik</span><span class="sxs-lookup"><span data-stu-id="2642a-246">Property</span></span>| <span data-ttu-id="2642a-247">Değer</span><span class="sxs-lookup"><span data-stu-id="2642a-247">Value</span></span>|<span data-ttu-id="2642a-248">Tür</span><span class="sxs-lookup"><span data-stu-id="2642a-248">Type</span></span>|
    |-------------|-----------------------|------|
    |<span data-ttu-id="2642a-249">hızlı</span><span class="sxs-lookup"><span data-stu-id="2642a-249">Prediction</span></span>|<span data-ttu-id="2642a-250">[0,5459937, 0,454006255]</span><span class="sxs-lookup"><span data-stu-id="2642a-250">[0.5459937, 0.454006255]</span></span>|<span data-ttu-id="2642a-251">float []</span><span class="sxs-lookup"><span data-stu-id="2642a-251">float[]</span></span>|

1. <span data-ttu-id="2642a-252">Aşağıdaki kodu kullanarak yaklaşım tahminini görüntüleyin:</span><span class="sxs-lookup"><span data-stu-id="2642a-252">Display sentiment prediction using the following code:</span></span>

    [!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#DisplayPredictions)]

1. <span data-ttu-id="2642a-253">@No__t-1 yönteminin sonundaki `PredictSentiment` ' a bir çağrı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2642a-253">Add a call to `PredictSentiment` at the end of the `Main` method:</span></span>

    [!code-csharp[CallPredictSentiment](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CallPredictSentiment)]

## <a name="results"></a><span data-ttu-id="2642a-254">Sonuçlar</span><span class="sxs-lookup"><span data-stu-id="2642a-254">Results</span></span>

<span data-ttu-id="2642a-255">Uygulamanızı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2642a-255">Build and run your application.</span></span>

<span data-ttu-id="2642a-256">Sonuçlarınız aşağıdakine benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2642a-256">Your results should be similar to the following.</span></span> <span data-ttu-id="2642a-257">İşlem sırasında iletiler görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="2642a-257">During processing, messages are displayed.</span></span> <span data-ttu-id="2642a-258">Uyarıları görebilir veya iletileri işleme alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2642a-258">You may see warnings, or processing messages.</span></span> <span data-ttu-id="2642a-259">Bu iletiler, açıklık açısından aşağıdaki sonuçlardan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="2642a-259">These messages have been removed from the following results for clarity.</span></span>

```console
Number of classes: 2
Is sentiment/review positive ? Yes
```

<span data-ttu-id="2642a-260">Mühendisi!</span><span class="sxs-lookup"><span data-stu-id="2642a-260">Congratulations!</span></span> <span data-ttu-id="2642a-261">ML.NET ' de önceden eğitilen bir `TensorFlow` modelini yeniden çalıştırarak, ileti yaklaşımını sınıflandırma ve tahmin etme için bir makine öğrenimi modelini başarıyla oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="2642a-261">You've now successfully built a machine learning model for classifying and predicting messages sentiment by reusing a pre-trained `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="2642a-262">Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2642a-262">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) repository.</span></span>

<span data-ttu-id="2642a-263">Bu öğreticide, nasıl yapılacağını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="2642a-263">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="2642a-264">Önceden eğitilen bir TensorFlow modeli yükleme</span><span class="sxs-lookup"><span data-stu-id="2642a-264">Load a pre-trained TensorFlow model</span></span>
> * <span data-ttu-id="2642a-265">Web sitesi açıklama metnini model için uygun özelliklere Dönüştür</span><span class="sxs-lookup"><span data-stu-id="2642a-265">Transform website comment text into features suitable for the model</span></span>
> * <span data-ttu-id="2642a-266">Tahmin yapmak için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="2642a-266">Use the model to make a prediction</span></span>
