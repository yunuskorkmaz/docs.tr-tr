---
title: 'Öğretici: TensorFlow modelini kullanarak inceleme duyarlılığını analiz edin'
description: Bu öğretici, web sitesi yorumlarında duyguları sınıflandırmak için önceden eğitilmiş tensorflow modelini nasıl kullanacağınızı gösterir. İkili duygu sınıflandırıcı Visual Studio kullanılarak geliştirilen bir C# konsol uygulamasıdır.
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 688c5b83cef8f21eef8fa24521a85449a9cfbd48
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78241123"
---
# <a name="tutorial-analyze-sentiment-of-movie-reviews-using-a-pre-trained-tensorflow-model-in-mlnet"></a><span data-ttu-id="c0be2-104">Öğretici: ML.NET önceden eğitilmiş TensorFlow modelini kullanarak film incelemelerinin duyarlılığını analiz edin</span><span class="sxs-lookup"><span data-stu-id="c0be2-104">Tutorial: Analyze sentiment of movie reviews using a pre-trained TensorFlow model in ML.NET</span></span>

<span data-ttu-id="c0be2-105">Bu öğretici, web sitesi yorumlarında duyguları sınıflandırmak için önceden eğitilmiş tensorflow modelini nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="c0be2-105">This tutorial shows you how to use a pre-trained TensorFlow model to classify sentiment in website comments.</span></span> <span data-ttu-id="c0be2-106">İkili duygu sınıflandırıcı Visual Studio kullanılarak geliştirilen bir C# konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="c0be2-106">The binary sentiment classifier is a C# console application developed using Visual Studio.</span></span>

<span data-ttu-id="c0be2-107">Bu eğitimde kullanılan TensorFlow modeli IMDB veritabanından film incelemeleri kullanılarak eğitildi.</span><span class="sxs-lookup"><span data-stu-id="c0be2-107">The TensorFlow model used in this tutorial was trained using movie reviews from the IMDB database.</span></span> <span data-ttu-id="c0be2-108">Uygulamayı geliştirmeyi bitirdikten sonra, film inceleme metni ni sağlayabilirsiniz ve uygulama incelemenin olumlu veya olumsuz bir duyarlılığı olup olmadığını size söyleyecektir.</span><span class="sxs-lookup"><span data-stu-id="c0be2-108">Once you have finished developing the application, you will be able to supply movie review text and the application will tell you whether the review has positive or negative sentiment.</span></span>

<span data-ttu-id="c0be2-109">Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c0be2-109">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="c0be2-110">Önceden eğitilmiş tensorFlow modelini yükleyin</span><span class="sxs-lookup"><span data-stu-id="c0be2-110">Load a pre-trained TensorFlow model</span></span>
> * <span data-ttu-id="c0be2-111">Web sitesi yorum metnini modele uygun özelliklere dönüştürme</span><span class="sxs-lookup"><span data-stu-id="c0be2-111">Transform website comment text into features suitable for the model</span></span>
> * <span data-ttu-id="c0be2-112">Tahminde bulunmak için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="c0be2-112">Use the model to make a prediction</span></span>

<span data-ttu-id="c0be2-113">Bu öğreticinin kaynak kodunu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c0be2-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c0be2-114">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="c0be2-114">Prerequisites</span></span>

* <span data-ttu-id="c0be2-115">[Visual Studio 2017 sürüm 15.6 veya daha sonra](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ".NET Core çapraz platform geliştirme" iş yükü yüklendi.</span><span class="sxs-lookup"><span data-stu-id="c0be2-115">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="setup"></a><span data-ttu-id="c0be2-116">Kurulum</span><span class="sxs-lookup"><span data-stu-id="c0be2-116">Setup</span></span>

### <a name="create-the-application"></a><span data-ttu-id="c0be2-117">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="c0be2-117">Create the application</span></span>

1. <span data-ttu-id="c0be2-118">"TextClassificationTF" adlı bir **.NET Çekirdek Konsol Uygulaması** oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c0be2-118">Create a **.NET Core Console Application** called "TextClassificationTF".</span></span>

2. <span data-ttu-id="c0be2-119">Veri kümesi dosyalarınızı kaydetmek için projenizde *Veri* adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c0be2-119">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="c0be2-120">Microsoft.ML **NuGet Paketini**Yükleyin:</span><span class="sxs-lookup"><span data-stu-id="c0be2-120">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="c0be2-121">Çözüm Gezgini'nde projenize sağ tıklayın ve **NuGet Paketlerini Yönet'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="c0be2-121">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="c0be2-122">Paket kaynağı olarak "nuget.org" seçeneğini belirleyin ve ardından **Gözat** sekmesini seçin. **Microsoft.ML**ara, istediğiniz paketi seçin ve sonra **Yükle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="c0be2-122">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="c0be2-123">Seçtiğiniz paketin lisans koşullarını kabul ederek yüklemeye devam edin.</span><span class="sxs-lookup"><span data-stu-id="c0be2-123">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span> <span data-ttu-id="c0be2-124">**Microsoft.ML.TensorFlow** ve **SciSharp.TensorFlow.Redist**için bu adımları tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="c0be2-124">Repeat these steps for **Microsoft.ML.TensorFlow** and **SciSharp.TensorFlow.Redist**.</span></span>

### <a name="add-the-tensorflow-model-to-the-project"></a><span data-ttu-id="c0be2-125">Projeye TensorFlow modelini ekleme</span><span class="sxs-lookup"><span data-stu-id="c0be2-125">Add the TensorFlow model to the project</span></span>

> [!NOTE]
> <span data-ttu-id="c0be2-126">Bu öğretici için model [dotnet / machinelearning-testdata](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) GitHub repo olduğunu.</span><span class="sxs-lookup"><span data-stu-id="c0be2-126">The model for this tutorial is from the [dotnet/machinelearning-testdata](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) GitHub repo.</span></span> <span data-ttu-id="c0be2-127">Model TensorFlow SavedModel biçimindedir.</span><span class="sxs-lookup"><span data-stu-id="c0be2-127">The model is in TensorFlow SavedModel format.</span></span>

1. <span data-ttu-id="c0be2-128">zip [sentiment_model dosyasını](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true)indirin ve zip'i açın.</span><span class="sxs-lookup"><span data-stu-id="c0be2-128">Download the [sentiment_model zip file](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true), and unzip.</span></span>

    <span data-ttu-id="c0be2-129">Zip dosyası şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="c0be2-129">The zip file contains:</span></span>

    * <span data-ttu-id="c0be2-130">`saved_model.pb`: TensorFlow modelinin kendisi.</span><span class="sxs-lookup"><span data-stu-id="c0be2-130">`saved_model.pb`: the TensorFlow model itself.</span></span> <span data-ttu-id="c0be2-131">Model, IMDB gözden geçirme dizesinde metni temsil eden sabit bir uzunluk (boyut 600) tamsayı dizisini alır ve 1'e kadar toplamı iki olasılık çıkarır: giriş incelemesinin olumlu bir duyarlılığa sahip olma olasılığı ve girdi incelemesinin sahip olma olasılığı olumsuz duygular.</span><span class="sxs-lookup"><span data-stu-id="c0be2-131">The model takes a fixed length (size 600) integer array of features representing the text in an IMDB review string, and outputs two probabilities which sum to 1: the probability that the input review has positive sentiment, and the probability that the input review has negative sentiment.</span></span>
    * <span data-ttu-id="c0be2-132">`imdb_word_index.csv`: tek tek sözcüklerden tamsayı değerine eşleme.</span><span class="sxs-lookup"><span data-stu-id="c0be2-132">`imdb_word_index.csv`: a mapping from individual words to an integer value.</span></span> <span data-ttu-id="c0be2-133">Eşleme TensorFlow modeli için giriş özellikleri oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c0be2-133">The mapping is used to generate the input features for the TensorFlow model.</span></span>

2. <span data-ttu-id="c0be2-134">En içteki `sentiment_model` dizinin içeriğini *TextClassificationTF* proje `sentiment_model` dizininize kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c0be2-134">Copy the contents of the innermost `sentiment_model` directory into your *TextClassificationTF* project `sentiment_model` directory.</span></span> <span data-ttu-id="c0be2-135">Bu dizin, aşağıdaki resimde gösterildiği gibi, bu öğretici için gerekli modeli ve ek destek dosyalarını içerir:</span><span class="sxs-lookup"><span data-stu-id="c0be2-135">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![sentiment_model dizin içeriği](./media/text-classification-tf/sentiment-model-files.png)

3. <span data-ttu-id="c0be2-137">Çözüm Gezgini'nde, `sentiment_model` dizin ve alt dizindeki dosyaların her birini sağ tıklatın ve **Özellikler'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="c0be2-137">In Solution Explorer, right-click each of the files in the `sentiment_model` directory and subdirectory and select **Properties**.</span></span> <span data-ttu-id="c0be2-138">**Gelişmiş**altında, **daha yeniyse**Kopyala'dan **Çıktı Dizini'ne Kopya** değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c0be2-138">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="add-using-statements-and-global-variables"></a><span data-ttu-id="c0be2-139">Deyimleri ve genel değişkenleri kullanarak ekleme</span><span class="sxs-lookup"><span data-stu-id="c0be2-139">Add using statements and global variables</span></span>

1. <span data-ttu-id="c0be2-140">Aşağıdaki ek `using` deyimleri *Program.cs* dosyasının üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c0be2-140">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

   [!code-csharp[AddUsings](../../../samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="c0be2-141">Kaydedilen model dosya yolunu `Main` ve özellik vektör uzunluğunu tutmak için yöntemin hemen üzerinde iki genel değişken oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c0be2-141">Create two global variables right above the `Main` method to hold the saved model file path, and the feature vector length.</span></span>

   [!code-csharp[DeclareGlobalVariables](../../../samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

    * <span data-ttu-id="c0be2-142">`_modelPath`eğitilmiş modelin dosya yoludur.</span><span class="sxs-lookup"><span data-stu-id="c0be2-142">`_modelPath` is the file path of the trained model.</span></span>
    * <span data-ttu-id="c0be2-143">`FeatureLength`modelin beklediği toplam özellik dizisinin uzunluğudur.</span><span class="sxs-lookup"><span data-stu-id="c0be2-143">`FeatureLength` is the length of the integer feature array that the model is expecting.</span></span>

### <a name="model-the-data"></a><span data-ttu-id="c0be2-144">Verileri modelleme</span><span class="sxs-lookup"><span data-stu-id="c0be2-144">Model the data</span></span>

<span data-ttu-id="c0be2-145">Film eleştirileri ücretsiz form metindir.</span><span class="sxs-lookup"><span data-stu-id="c0be2-145">Movie reviews are free form text.</span></span> <span data-ttu-id="c0be2-146">Uygulamanız, metni, modeltarafından birkaç ayrı aşamada beklenen giriş biçimine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="c0be2-146">Your application converts the text into the input format expected by the model in a number of discrete stages.</span></span>

<span data-ttu-id="c0be2-147">İlki, metni ayrı sözcüklere bölmek ve her sözcüğü bir sonda kodlamasına eşlemek için sağlanan eşleme dosyasını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="c0be2-147">The first is to split the text into separate words and use the provided mapping file to map each word onto an integer encoding.</span></span> <span data-ttu-id="c0be2-148">Bu dönüşümün sonucu, cümledeki sözcük sayısına karşılık gelen uzunlukta bir değişken uzunlukta tamsayı dizisidir.</span><span class="sxs-lookup"><span data-stu-id="c0be2-148">The result of this transformation is a variable length integer array with a length corresponding to the number of words in the sentence.</span></span>

|<span data-ttu-id="c0be2-149">Özellik</span><span class="sxs-lookup"><span data-stu-id="c0be2-149">Property</span></span>| <span data-ttu-id="c0be2-150">Değer</span><span class="sxs-lookup"><span data-stu-id="c0be2-150">Value</span></span>|<span data-ttu-id="c0be2-151">Tür</span><span class="sxs-lookup"><span data-stu-id="c0be2-151">Type</span></span>|
|-------------|-----------------------|------|
|<span data-ttu-id="c0be2-152">İnceleme Metni</span><span class="sxs-lookup"><span data-stu-id="c0be2-152">ReviewText</span></span>|<span data-ttu-id="c0be2-153">bu film gerçekten çok iyi</span><span class="sxs-lookup"><span data-stu-id="c0be2-153">this film is really good</span></span>|<span data-ttu-id="c0be2-154">string</span><span class="sxs-lookup"><span data-stu-id="c0be2-154">string</span></span>|
|<span data-ttu-id="c0be2-155">Değişken UzunlukÖzellikleri</span><span class="sxs-lookup"><span data-stu-id="c0be2-155">VariableLengthFeatures</span></span>|<span data-ttu-id="c0be2-156">14,22,9,66,78,...</span><span class="sxs-lookup"><span data-stu-id="c0be2-156">14,22,9,66,78,...</span></span> |<span data-ttu-id="c0be2-157">int[]</span><span class="sxs-lookup"><span data-stu-id="c0be2-157">int[]</span></span>|

<span data-ttu-id="c0be2-158">Değişken uzunluk özelliği dizisi daha sonra 600 sabit bir uzunluğa yeniden boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="c0be2-158">The variable length feature array is then resized to a fixed length of 600.</span></span> <span data-ttu-id="c0be2-159">Bu, TensorFlow modelinin beklediği uzunluktur.</span><span class="sxs-lookup"><span data-stu-id="c0be2-159">This is the length that the TensorFlow model expects.</span></span>

|<span data-ttu-id="c0be2-160">Özellik</span><span class="sxs-lookup"><span data-stu-id="c0be2-160">Property</span></span>| <span data-ttu-id="c0be2-161">Değer</span><span class="sxs-lookup"><span data-stu-id="c0be2-161">Value</span></span>|<span data-ttu-id="c0be2-162">Tür</span><span class="sxs-lookup"><span data-stu-id="c0be2-162">Type</span></span>|
|-------------|-----------------------|------|
|<span data-ttu-id="c0be2-163">İnceleme Metni</span><span class="sxs-lookup"><span data-stu-id="c0be2-163">ReviewText</span></span>|<span data-ttu-id="c0be2-164">bu film gerçekten çok iyi</span><span class="sxs-lookup"><span data-stu-id="c0be2-164">this film is really good</span></span>|<span data-ttu-id="c0be2-165">string</span><span class="sxs-lookup"><span data-stu-id="c0be2-165">string</span></span>|
|<span data-ttu-id="c0be2-166">Değişken UzunlukÖzellikleri</span><span class="sxs-lookup"><span data-stu-id="c0be2-166">VariableLengthFeatures</span></span>|<span data-ttu-id="c0be2-167">14,22,9,66,78,...</span><span class="sxs-lookup"><span data-stu-id="c0be2-167">14,22,9,66,78,...</span></span> |<span data-ttu-id="c0be2-168">int[]</span><span class="sxs-lookup"><span data-stu-id="c0be2-168">int[]</span></span>|
|<span data-ttu-id="c0be2-169">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c0be2-169">Features</span></span>|<span data-ttu-id="c0be2-170">14,22,9,66,78,...</span><span class="sxs-lookup"><span data-stu-id="c0be2-170">14,22,9,66,78,...</span></span> |<span data-ttu-id="c0be2-171">int[600]</span><span class="sxs-lookup"><span data-stu-id="c0be2-171">int[600]</span></span>|

1. <span data-ttu-id="c0be2-172">Yöntemden `Main` sonra giriş verileriniz için bir sınıf oluşturun:</span><span class="sxs-lookup"><span data-stu-id="c0be2-172">Create a class for your input data, after the `Main` method:</span></span>

    [!code-csharp[MovieReviewClass](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#MovieReviewClass "Declare movie review type")]

    <span data-ttu-id="c0be2-173">Giriş veri sınıfı, `MovieReview`kullanıcı `string` yorumları için`ReviewText`bir var ( ).</span><span class="sxs-lookup"><span data-stu-id="c0be2-173">The input data class, `MovieReview`, has a `string` for user comments (`ReviewText`).</span></span>

1. <span data-ttu-id="c0be2-174">`Main` Yöntemden sonra değişken uzunluk özellikleri için bir sınıf oluşturun:</span><span class="sxs-lookup"><span data-stu-id="c0be2-174">Create a class for the variable length features, after the `Main` method:</span></span>

    [!code-csharp[VariableLengthFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#VariableLengthFeatures "Declare variable length features type")]

    <span data-ttu-id="c0be2-175">Özellik `VariableLengthFeatures` vektör olarak belirlemek için bir [VectorType](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="c0be2-175">The `VariableLengthFeatures` property has a [VectorType](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) attribute to designate it as a vector.</span></span>  <span data-ttu-id="c0be2-176">Tüm vektör elemanları aynı türde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c0be2-176">All of the vector elements must be the same type.</span></span> <span data-ttu-id="c0be2-177">Çok sayıda sütuna sahip veri kümelerinde, birden çok sütunu tek bir vektör olarak yüklemek, veri dönüşümlerini uyguladığınızda veri geçişlerinin sayısını azaltır.</span><span class="sxs-lookup"><span data-stu-id="c0be2-177">In data sets with a large number of columns, loading multiple columns as a single vector reduces the number of data passes when you apply data transformations.</span></span>

    <span data-ttu-id="c0be2-178">Bu sınıf `ResizeFeatures` eylemde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c0be2-178">This class is used in the `ResizeFeatures` action.</span></span> <span data-ttu-id="c0be2-179">Özelliklerinin adları (bu durumda yalnızca bir) DataView'daki hangi sütunların özel eşleme eylemine _giriş_ olarak kullanılabileceğini belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c0be2-179">The names of its properties (in this case only one) are used to indicate which columns in the DataView can be used as the _input_ to the custom mapping action.</span></span>

1. <span data-ttu-id="c0be2-180">`Main` Yöntemden sonra sabit uzunluk özellikleri için bir sınıf oluşturun:</span><span class="sxs-lookup"><span data-stu-id="c0be2-180">Create a class for the fixed length features, after the `Main` method:</span></span>

    [!code-csharp[FixedLengthFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#FixedLengthFeatures)]

    <span data-ttu-id="c0be2-181">Bu sınıf `ResizeFeatures` eylemde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c0be2-181">This class is used in the `ResizeFeatures` action.</span></span> <span data-ttu-id="c0be2-182">Özelliklerinin adları (bu durumda yalnızca bir tane) DataView'daki hangi sütunların özel eşleme eyleminin _çıktısı_ olarak kullanılabileceğini belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c0be2-182">The names of its properties (in this case only one) are used to indicate which columns in the DataView can be used as the _output_ of the custom mapping action.</span></span>

    <span data-ttu-id="c0be2-183">Özelliğin `Features` adının TensorFlow modeli tarafından belirlendiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c0be2-183">Note that the name of the property `Features` is determined by the TensorFlow model.</span></span> <span data-ttu-id="c0be2-184">Bu özellik adını değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="c0be2-184">You cannot change this property name.</span></span>

1. <span data-ttu-id="c0be2-185">`Main` Yöntemden sonra tahmin için bir sınıf oluşturun:</span><span class="sxs-lookup"><span data-stu-id="c0be2-185">Create a class for the prediction after the `Main` method:</span></span>

    [!code-csharp[Prediction](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#Prediction "Declare prediction class")]

    <span data-ttu-id="c0be2-186">`MovieReviewSentimentPrediction`model eğitiminden sonra kullanılan tahmin sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="c0be2-186">`MovieReviewSentimentPrediction` is the prediction class used after the model training.</span></span> <span data-ttu-id="c0be2-187">`MovieReviewSentimentPrediction`tek `float` bir dizi`Prediction`( `VectorType` ) ve bir özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="c0be2-187">`MovieReviewSentimentPrediction` has a single `float` array (`Prediction`) and a `VectorType` attribute.</span></span>

### <a name="create-the-mlcontext-lookup-dictionary-and-action-to-resize-features"></a><span data-ttu-id="c0be2-188">Özellikleri yeniden boyutlandırmak için MLContext, arama sözlüğü ve eylem oluşturun</span><span class="sxs-lookup"><span data-stu-id="c0be2-188">Create the MLContext, lookup dictionary, and action to resize features</span></span>

<span data-ttu-id="c0be2-189">[MLContext sınıfı](xref:Microsoft.ML.MLContext) tüm ML.NET işlemleri için bir başlangıç noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="c0be2-189">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="c0be2-190">İlk `mlContext` başlatma, model oluşturma iş akışı nesneleri arasında paylaşılabilen yeni bir ML.NET ortamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c0be2-190">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="c0be2-191">Kavramsal olarak Varlık Çerçevesi'ne `DBContext` benzer.</span><span class="sxs-lookup"><span data-stu-id="c0be2-191">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

1. <span data-ttu-id="c0be2-192">MlContext `Console.WriteLine("Hello World!")` değişkenini `Main` bildirmek ve başlatmak için yöntemdeki satırı aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="c0be2-192">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

   [!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateMLContext "Create the ML Context")]

1. <span data-ttu-id="c0be2-193">Aşağıdaki tabloda görüldüğü gibi, bir dosyadan [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) eşleme verilerini yüklemek için yöntemi kullanarak sözcükleri tamsayı olarak kodlamak için bir sözlük oluşturun:</span><span class="sxs-lookup"><span data-stu-id="c0be2-193">Create a dictionary to encode words as integers by using the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method to load mapping data from a file, as seen in the following table:</span></span>

    |<span data-ttu-id="c0be2-194">Word</span><span class="sxs-lookup"><span data-stu-id="c0be2-194">Word</span></span>     |<span data-ttu-id="c0be2-195">Dizin oluşturma</span><span class="sxs-lookup"><span data-stu-id="c0be2-195">Index</span></span>    |
    |---------|---------|
    |<span data-ttu-id="c0be2-196">Çocuklar</span><span class="sxs-lookup"><span data-stu-id="c0be2-196">kids</span></span>     |  <span data-ttu-id="c0be2-197">362</span><span class="sxs-lookup"><span data-stu-id="c0be2-197">362</span></span>    |
    |<span data-ttu-id="c0be2-198">Istiyor</span><span class="sxs-lookup"><span data-stu-id="c0be2-198">want</span></span>     |  <span data-ttu-id="c0be2-199">181</span><span class="sxs-lookup"><span data-stu-id="c0be2-199">181</span></span>    |
    |<span data-ttu-id="c0be2-200">Yanlış</span><span class="sxs-lookup"><span data-stu-id="c0be2-200">wrong</span></span>    |  <span data-ttu-id="c0be2-201">355</span><span class="sxs-lookup"><span data-stu-id="c0be2-201">355</span></span>    |
    |<span data-ttu-id="c0be2-202">effects</span><span class="sxs-lookup"><span data-stu-id="c0be2-202">effects</span></span>  |  <span data-ttu-id="c0be2-203">302</span><span class="sxs-lookup"><span data-stu-id="c0be2-203">302</span></span>    |
    |<span data-ttu-id="c0be2-204">Duygu</span><span class="sxs-lookup"><span data-stu-id="c0be2-204">feeling</span></span>  |  <span data-ttu-id="c0be2-205">547</span><span class="sxs-lookup"><span data-stu-id="c0be2-205">547</span></span>    |

    <span data-ttu-id="c0be2-206">Arama eşlemi oluşturmak için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c0be2-206">Add the code below to create the lookup map:</span></span>

    [!code-csharp[CreateLookupMap](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateLookupMap)]

1. <span data-ttu-id="c0be2-207">Bir `Action` sonraki kod satırları ile sabit boyutlu bir toplam dizi değişken uzunlukta sözcük ortasayı dizisini yeniden boyutlandırmak için bir ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c0be2-207">Add an `Action` to resize the variable length word integer array to an integer array of fixed size, with the next lines of code:</span></span>

   [!code-csharp[ResizeFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#ResizeFeatures)]

## <a name="load-the-pre-trained-tensorflow-model"></a><span data-ttu-id="c0be2-208">Önceden eğitilmiş TensorFlow modelini yükleyin</span><span class="sxs-lookup"><span data-stu-id="c0be2-208">Load the pre-trained TensorFlow model</span></span>

1. <span data-ttu-id="c0be2-209">TensorFlow modelini yüklemek için kod ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c0be2-209">Add code to load the TensorFlow model:</span></span>

    [!code-csharp[LoadTensorFlowModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#LoadTensorFlowModel)]

    <span data-ttu-id="c0be2-210">Model yüklendikten sonra, giriş ve çıkış şema ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c0be2-210">Once the model is loaded, you can extract its input and output schema.</span></span> <span data-ttu-id="c0be2-211">Şemalar sadece ilgi ve öğrenme için görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c0be2-211">The schemas are displayed for interest and learning only.</span></span> <span data-ttu-id="c0be2-212">Son uygulamanın çalışması için bu koda ihtiyacınız yoktur:</span><span class="sxs-lookup"><span data-stu-id="c0be2-212">You do not need this code for the final application to function:</span></span>

    [!code-csharp[GetModelSchema](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#GetModelSchema)]

    <span data-ttu-id="c0be2-213">Giriş şeması, tamsayı kodlanmış sözcüklerin sabit uzunluktaki dizisidir.</span><span class="sxs-lookup"><span data-stu-id="c0be2-213">The input schema is the fixed-length array of integer encoded words.</span></span> <span data-ttu-id="c0be2-214">Çıktı şeması, bir incelemenin duyarlılığının olumsuz mu yoksa olumlu mu olduğunu gösteren bir sürüolasılık dizisidir.</span><span class="sxs-lookup"><span data-stu-id="c0be2-214">The output schema is a float array of probabilities indicating whether a review's sentiment is negative, or positive .</span></span> <span data-ttu-id="c0be2-215">Bu değerler 1'e kadar toplam, pozitif olma olasılığı, duyarlılığın negatif olma olasılığının tamamlayıcısı olduğu için.</span><span class="sxs-lookup"><span data-stu-id="c0be2-215">These values sum to 1, as the probability of being positive is the complement of the probability of the sentiment being negative.</span></span>

## <a name="create-the-mlnet-pipeline"></a><span data-ttu-id="c0be2-216">ML.NET ardışık oluşturma</span><span class="sxs-lookup"><span data-stu-id="c0be2-216">Create the ML.NET pipeline</span></span>

1. <span data-ttu-id="c0be2-217">Satır kuralını oluşturun ve bir sonraki kod satırı olarak metni sözcüklere bölmek için [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) dönüştürmeyi kullanarak giriş metnini sözcüklere bölün:</span><span class="sxs-lookup"><span data-stu-id="c0be2-217">Create the pipeline and split the input text into words using [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transform to break the text into words as the next line of code:</span></span>

   [!code-csharp[TokenizeIntoWords](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#TokenizeIntoWords)]

   <span data-ttu-id="c0be2-218">[TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) dönüştürme, metin/dizeyi sözcüklere ayrıştırmak için boşlukları kullanır.</span><span class="sxs-lookup"><span data-stu-id="c0be2-218">The [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transform uses spaces to parse the text/string into words.</span></span> <span data-ttu-id="c0be2-219">Yeni bir sütun oluşturur ve her giriş dizesini kullanıcı tanımlı ayırıcıya dayalı bir alt dizeleri vektörüne böler.</span><span class="sxs-lookup"><span data-stu-id="c0be2-219">It creates a new column and splits each input string to a vector of substrings based on the user-defined separator.</span></span>

1. <span data-ttu-id="c0be2-220">Yukarıda beyan ettiğiniz arama tablosunu kullanarak sözcükleri, kendi enstabazı kodlamalarına eşle:</span><span class="sxs-lookup"><span data-stu-id="c0be2-220">Map the words onto their integer encoding using the lookup table that you declared above:</span></span>

    [!code-csharp[MapValue](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#MapValue)]

1. <span data-ttu-id="c0be2-221">Değişken uzunluk lı ortalık kodlayıcı kodlamalarını modelin gerektirdiği sabit uzunlukta olana yeniden boyutlandırın:</span><span class="sxs-lookup"><span data-stu-id="c0be2-221">Resize the variable length integer encodings to the fixed-length one required by the model:</span></span>

    [!code-csharp[CustomMapping](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CustomMapping)]

1. <span data-ttu-id="c0be2-222">Yüklenen TensorFlow modeliyle girişi sınıflandırın:</span><span class="sxs-lookup"><span data-stu-id="c0be2-222">Classify the input with the loaded TensorFlow model:</span></span>

    [!code-csharp[ScoreTensorFlowModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#ScoreTensorFlowModel)]

    <span data-ttu-id="c0be2-223">TensorFlow modeli çıktısı `Prediction/Softmax`denir.</span><span class="sxs-lookup"><span data-stu-id="c0be2-223">The TensorFlow model output is called `Prediction/Softmax`.</span></span> <span data-ttu-id="c0be2-224">Adın `Prediction/Softmax` TensorFlow modeli tarafından belirlendiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c0be2-224">Note that the name `Prediction/Softmax` is determined by the TensorFlow model.</span></span> <span data-ttu-id="c0be2-225">Bu adı değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="c0be2-225">You cannot change this name.</span></span>

1. <span data-ttu-id="c0be2-226">Çıktı tahmini için yeni bir sütun oluşturun:</span><span class="sxs-lookup"><span data-stu-id="c0be2-226">Create a new column for the output prediction:</span></span>

    [!code-csharp[SnippetCopyColumns](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#SnippetCopyColumns)]

    <span data-ttu-id="c0be2-227">Sütunu `Prediction/Softmax` C# sınıfında özellik olarak kullanılabilecek bir adla kopyalamanız gerekir: `Prediction`.</span><span class="sxs-lookup"><span data-stu-id="c0be2-227">You need to copy the `Prediction/Softmax` column into one with a name that can be used as a property in a C# class: `Prediction`.</span></span> <span data-ttu-id="c0be2-228">`/` C# özellik adında karaktere izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="c0be2-228">The `/` character is not allowed in a C# property name.</span></span>

## <a name="create-the-mlnet-model-from-the-pipeline"></a><span data-ttu-id="c0be2-229">Boru hattından ML.NET modeli oluşturma</span><span class="sxs-lookup"><span data-stu-id="c0be2-229">Create the ML.NET model from the pipeline</span></span>

1. <span data-ttu-id="c0be2-230">Modeli ardışık kaynaktan oluşturmak için kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c0be2-230">Add the code to create the model from the pipeline:</span></span>

    [!code-csharp[SnippetCreateModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#SnippetCreateModel)]

    <span data-ttu-id="c0be2-231">ML.NET modeli, `Fit` yöntem çağırılarak ardışık ardışık alan tahminciler zincirinden oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c0be2-231">An ML.NET model is created from the chain of estimators in the pipeline by calling the `Fit` method.</span></span> <span data-ttu-id="c0be2-232">Bu durumda, TensorFlow modeli daha önce eğitilmiş olduğundan, modeli oluşturmak için herhangi bir veri sığdırmiyoruz.</span><span class="sxs-lookup"><span data-stu-id="c0be2-232">In this case, we are not fitting any data to create the model, as the TensorFlow model has already been previously trained.</span></span> <span data-ttu-id="c0be2-233">Yöntemin gereksinimlerini karşılamak için boş bir `Fit` veri görünümü nesnesi sağlıyoruz.</span><span class="sxs-lookup"><span data-stu-id="c0be2-233">We supply an empty data view object to satisfy the requirements of the `Fit` method.</span></span>

## <a name="use-the-model-to-make-a-prediction"></a><span data-ttu-id="c0be2-234">Tahminde bulunmak için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="c0be2-234">Use the model to make a prediction</span></span>

1. <span data-ttu-id="c0be2-235">`PredictSentiment` Yöntemi aşağıdaki yöntemin `Main` altına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c0be2-235">Add the `PredictSentiment` method below the `Main` method:</span></span>

    ```csharp
    public static void PredictSentiment(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. <span data-ttu-id="c0be2-236">Yöntemde ilk satır `PredictionEngine` olarak oluşturmak için aşağıdaki kodu ekleyin: `PredictSentiment()`</span><span class="sxs-lookup"><span data-stu-id="c0be2-236">Add the following code to create the `PredictionEngine` as the first line in the `PredictSentiment()` method:</span></span>

    [!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreatePredictionEngine)]

    <span data-ttu-id="c0be2-237">[PredictionEngine,](xref:Microsoft.ML.PredictionEngine%602) tek bir veri örneği üzerinde tahmin gerçekleştirmenize olanak tanıyan kolaylık api'sidir.</span><span class="sxs-lookup"><span data-stu-id="c0be2-237">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="c0be2-238">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)iş parçacığı güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="c0be2-238">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="c0be2-239">Tek dişli veya prototip ortamlarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c0be2-239">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="c0be2-240">Üretim ortamlarında daha iyi performans ve `PredictionEnginePool` iş parçacığı güvenliği [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) için, uygulamanız boyunca kullanılmak üzere bir nesne oluşturan hizmeti kullanın.</span><span class="sxs-lookup"><span data-stu-id="c0be2-240">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="c0be2-241">ASP.NET Core Web [API'de `PredictionEnginePool` ](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)nasıl kullanılacağı yla ilgili bu kılavuza bakın.</span><span class="sxs-lookup"><span data-stu-id="c0be2-241">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

    > [!NOTE]
    > <span data-ttu-id="c0be2-242">`PredictionEnginePool`hizmet uzantısı şu anda önizlemededir.</span><span class="sxs-lookup"><span data-stu-id="c0be2-242">`PredictionEnginePool` service extension is currently in preview.</span></span>

1. <span data-ttu-id="c0be2-243">Bir örnek oluşturarak `Predict()` yöntemde eğitimli modelin tahminsına test `MovieReview`etmek için bir açıklama ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c0be2-243">Add a comment to test the trained model's prediction in the `Predict()` method by creating an instance of `MovieReview`:</span></span>

    [!code-csharp[CreateTestData](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateTestData)]

1. <span data-ttu-id="c0be2-244">Yöntemde sonraki kod `Prediction Engine` satırlarını ekleyerek test yorum `PredictSentiment()` verilerini geçirin:</span><span class="sxs-lookup"><span data-stu-id="c0be2-244">Pass the test comment data to the `Prediction Engine` by adding the next lines of code in the `PredictSentiment()` method:</span></span>

    [!code-csharp[Predict](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#Predict)]

1. <span data-ttu-id="c0be2-245">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi, tek bir veri satırı üzerinde bir tahminyapar:</span><span class="sxs-lookup"><span data-stu-id="c0be2-245">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data:</span></span>

    |<span data-ttu-id="c0be2-246">Özellik</span><span class="sxs-lookup"><span data-stu-id="c0be2-246">Property</span></span>| <span data-ttu-id="c0be2-247">Değer</span><span class="sxs-lookup"><span data-stu-id="c0be2-247">Value</span></span>|<span data-ttu-id="c0be2-248">Tür</span><span class="sxs-lookup"><span data-stu-id="c0be2-248">Type</span></span>|
    |-------------|-----------------------|------|
    |<span data-ttu-id="c0be2-249">Prediction (Tahmin)</span><span class="sxs-lookup"><span data-stu-id="c0be2-249">Prediction</span></span>|<span data-ttu-id="c0be2-250">[0.5459937, 0.454006255]</span><span class="sxs-lookup"><span data-stu-id="c0be2-250">[0.5459937, 0.454006255]</span></span>|<span data-ttu-id="c0be2-251">float[]</span><span class="sxs-lookup"><span data-stu-id="c0be2-251">float[]</span></span>|

1. <span data-ttu-id="c0be2-252">Aşağıdaki kodu kullanarak duyarlılık tahminini görüntüleyin:</span><span class="sxs-lookup"><span data-stu-id="c0be2-252">Display sentiment prediction using the following code:</span></span>

    [!code-csharp[DisplayPredictions](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#DisplayPredictions)]

1. <span data-ttu-id="c0be2-253">Yöntemin sonunda `PredictSentiment` bir çağrı ekleyin: `Main`</span><span class="sxs-lookup"><span data-stu-id="c0be2-253">Add a call to `PredictSentiment` at the end of the `Main` method:</span></span>

    [!code-csharp[CallPredictSentiment](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CallPredictSentiment)]

## <a name="results"></a><span data-ttu-id="c0be2-254">Sonuçlar</span><span class="sxs-lookup"><span data-stu-id="c0be2-254">Results</span></span>

<span data-ttu-id="c0be2-255">Uygulamanızı oluşturun ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c0be2-255">Build and run your application.</span></span>

<span data-ttu-id="c0be2-256">Sonuçlarınız aşağıdakilere benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c0be2-256">Your results should be similar to the following.</span></span> <span data-ttu-id="c0be2-257">İşlem sırasında iletiler görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c0be2-257">During processing, messages are displayed.</span></span> <span data-ttu-id="c0be2-258">Uyarılar veya iletileri işleme görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c0be2-258">You may see warnings, or processing messages.</span></span> <span data-ttu-id="c0be2-259">Bu iletiler netlik için aşağıdaki sonuçlardan kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="c0be2-259">These messages have been removed from the following results for clarity.</span></span>

```console
Number of classes: 2
Is sentiment/review positive ? Yes
```

<span data-ttu-id="c0be2-260">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="c0be2-260">Congratulations!</span></span> <span data-ttu-id="c0be2-261">Şimdi, ML.NET önceden eğitilmiş bir modeli yeniden kullanarak iletilerin duyarlılığını sınıflandırmak ve `TensorFlow` tahmin etmek için başarılı bir şekilde bir makine öğrenme modeli oluşturmuşsunuz.</span><span class="sxs-lookup"><span data-stu-id="c0be2-261">You've now successfully built a machine learning model for classifying and predicting messages sentiment by reusing a pre-trained `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="c0be2-262">Bu öğreticinin kaynak kodunu [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c0be2-262">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) repository.</span></span>

<span data-ttu-id="c0be2-263">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="c0be2-263">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="c0be2-264">Önceden eğitilmiş tensorFlow modelini yükleyin</span><span class="sxs-lookup"><span data-stu-id="c0be2-264">Load a pre-trained TensorFlow model</span></span>
> * <span data-ttu-id="c0be2-265">Web sitesi yorum metnini modele uygun özelliklere dönüştürme</span><span class="sxs-lookup"><span data-stu-id="c0be2-265">Transform website comment text into features suitable for the model</span></span>
> * <span data-ttu-id="c0be2-266">Tahminde bulunmak için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="c0be2-266">Use the model to make a prediction</span></span>
