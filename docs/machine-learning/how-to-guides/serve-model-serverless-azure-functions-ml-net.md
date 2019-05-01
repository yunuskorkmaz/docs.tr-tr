---
title: Azure işlevleri için ML.NET Model dağıtma
description: ML.NET yaklaşım analizi makine öğrenme modelinin tahmin için Azure işlevleri'ni kullanarak internet üzerinden hizmet
ms.date: 03/08/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 74b75af1963ed2ce23e732608c8f7b8ede8522ee
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63807997"
---
# <a name="how-to-use-mlnet-model-in-azure-functions"></a><span data-ttu-id="52ac4-103">Nasıl yapılır: Azure işlevleri ML.NET modelini kullanın</span><span class="sxs-lookup"><span data-stu-id="52ac4-103">How-To: Use ML.NET Model in Azure Functions</span></span>

<span data-ttu-id="52ac4-104">Bu nasıl yapılır tek tek nasıl Öngörüler gösteren Azure işlevleri gibi sunucusuz bir ortamda Internet üzerinden önceden oluşturulmuş ML.NET makine öğrenme modeli kullanılarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="52ac4-104">This how-to shows how individual predictions can be made using a pre-built ML.NET machine learning model through the internet in a serverless environment such as Azure Functions.</span></span>

> [!NOTE]
> <span data-ttu-id="52ac4-105">Bu konu şu anda Önizleme aşamasında olan ML.NET ifade eder ve malzeme değişiklik gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="52ac4-105">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="52ac4-106">Daha fazla bilgi için ziyaret [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="52ac4-106">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="52ac4-107">Bu nasıl yapılır ve ilgili örnek şu anda kullandığınızdan **ML.NET sürüm 0.10**.</span><span class="sxs-lookup"><span data-stu-id="52ac4-107">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="52ac4-108">Daha fazla bilgi için bkz: adresindeki sürüm notlarını [dotnet/machinelearning github deposunu](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="52ac4-108">For more information, see the release notes at the [dotnet/machinelearning github repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="52ac4-109">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="52ac4-109">Prerequisites</span></span>

- <span data-ttu-id="52ac4-110">[Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) "Azure geliştirme yüklü" ve ".NET Core çoklu platform geliştirme" iş yükü.</span><span class="sxs-lookup"><span data-stu-id="52ac4-110">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload and "Azure development" installed.</span></span>
- [<span data-ttu-id="52ac4-111">Azure işlevleri araçları</span><span class="sxs-lookup"><span data-stu-id="52ac4-111">Azure Functions Tools</span></span>](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- <span data-ttu-id="52ac4-112">PowerShell</span><span class="sxs-lookup"><span data-stu-id="52ac4-112">Powershell</span></span>
- <span data-ttu-id="52ac4-113">Önceden eğitilmiş model.</span><span class="sxs-lookup"><span data-stu-id="52ac4-113">Pre-trained model.</span></span>
  - <span data-ttu-id="52ac4-114">Kullanım [ML.NET yaklaşım analizi Öğreticisi](../tutorials/sentiment-analysis.md) kendi modeli derler.</span><span class="sxs-lookup"><span data-stu-id="52ac4-114">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model.</span></span>
  - <span data-ttu-id="52ac4-115">Bu indirme [önceden eğitilmiş yaklaşım analizi, machine learning modeli](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="52ac4-115">Download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-azure-functions-project"></a><span data-ttu-id="52ac4-116">Azure işlevleri projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="52ac4-116">Create Azure Functions Project</span></span>

1. <span data-ttu-id="52ac4-117">Visual Studio 2017'yi açın.</span><span class="sxs-lookup"><span data-stu-id="52ac4-117">Open Visual Studio 2017.</span></span> <span data-ttu-id="52ac4-118">Seçin **dosya** > **yeni** > **proje** menü çubuğundan.</span><span class="sxs-lookup"><span data-stu-id="52ac4-118">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="52ac4-119">İçinde **yeni proje** iletişim kutusunda **Visual C#**  düğümünü ve ardından **bulut** düğümü.</span><span class="sxs-lookup"><span data-stu-id="52ac4-119">In the **New Project** dialog, select the **Visual C#** node followed by the **Cloud** node.</span></span> <span data-ttu-id="52ac4-120">Ardından **Azure işlevleri** proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="52ac4-120">Then select the **Azure Functions** project template.</span></span> <span data-ttu-id="52ac4-121">İçinde **adı** metin kutusuna "SentimentAnalysisFunctionsApp" yazın ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="52ac4-121">In the **Name** text box, type "SentimentAnalysisFunctionsApp" and then select the **OK** button.</span></span>
1. <span data-ttu-id="52ac4-122">İçinde **yeni proje** iletişim kutusunda, proje seçeneklerinde Yukarıdaki açılan listeyi açın ve seçin **Azure işlevler v2 (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="52ac4-122">In the **New Project** dialog, open the dropdown above the project options and select **Azure Functions v2 (.NET Core)**.</span></span> <span data-ttu-id="52ac4-123">Ardından, **Http tetikleyicisi** proje ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="52ac4-123">Then, select the **Http trigger** project and then select the **OK** button.</span></span>
1. <span data-ttu-id="52ac4-124">Adlı bir dizin oluşturmak *MLModels* modelinizi kaydetmek için projenizde:</span><span class="sxs-lookup"><span data-stu-id="52ac4-124">Create a directory named *MLModels* in your project to save your model:</span></span>

    <span data-ttu-id="52ac4-125">İçinde **Çözüm Gezgini**, projenize sağ tıklayıp **Ekle** > **yeni klasör**.</span><span class="sxs-lookup"><span data-stu-id="52ac4-125">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="52ac4-126">"MLModels" yazın ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="52ac4-126">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="52ac4-127">Yükleme **Microsoft.ML NuGet paketini**:</span><span class="sxs-lookup"><span data-stu-id="52ac4-127">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="52ac4-128">Çözüm Gezgini'nde seçin ve proje üzerinde sağ **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="52ac4-128">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="52ac4-129">Paket kaynağı olarak "nuget.org" seçin, Gözat sekmesini seçin, arama **Microsoft.ML**, bu paket listesinde seçip **yükleme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="52ac4-129">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="52ac4-130">Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="52ac4-130">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="add-pre-built-model-to-project"></a><span data-ttu-id="52ac4-131">Önceden oluşturulmuş Model projeye Ekle</span><span class="sxs-lookup"><span data-stu-id="52ac4-131">Add Pre-built Model To Project</span></span>

1. <span data-ttu-id="52ac4-132">Önceden oluşturulmuş modelinizi kopyalama *MLModels* klasör.</span><span class="sxs-lookup"><span data-stu-id="52ac4-132">Copy your pre-built model to the *MLModels* folder.</span></span>
1. <span data-ttu-id="52ac4-133">Çözüm Gezgini'nde, önceden oluşturulmuş model dosyasını sağ tıklatın ve seçin **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="52ac4-133">In Solution Explorer, right-click your pre-built model file and select **Properties**.</span></span> <span data-ttu-id="52ac4-134">Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.</span><span class="sxs-lookup"><span data-stu-id="52ac4-134">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

## <a name="create-function-to-analyze-sentiment"></a><span data-ttu-id="52ac4-135">Yaklaşımı analiz etmek için işlev oluşturma</span><span class="sxs-lookup"><span data-stu-id="52ac4-135">Create Function to Analyze Sentiment</span></span>

<span data-ttu-id="52ac4-136">Yaklaşım tahmin etmek için bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="52ac4-136">Create a class to predict sentiment.</span></span> <span data-ttu-id="52ac4-137">Yeni bir sınıf, projenize ekleyin:</span><span class="sxs-lookup"><span data-stu-id="52ac4-137">Add a new class to your project:</span></span>

1. <span data-ttu-id="52ac4-138">İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="52ac4-138">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="52ac4-139">İçinde **Yeni Öğe Ekle** iletişim kutusunda **Azure işlevi** değiştirip **adı** alanı *AnalyzeSentiment.cs*.</span><span class="sxs-lookup"><span data-stu-id="52ac4-139">In the **Add New Item** dialog box, select **Azure Function** and change the **Name** field to *AnalyzeSentiment.cs*.</span></span> <span data-ttu-id="52ac4-140">Ardından, **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="52ac4-140">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="52ac4-141">İçinde **yeni Azure işlevi** iletişim kutusunda **Http tetikleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="52ac4-141">In the **New Azure Function** dialog box, select **Http Trigger**.</span></span> <span data-ttu-id="52ac4-142">Ardından, **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="52ac4-142">Then, select the **OK** button.</span></span>

    <span data-ttu-id="52ac4-143">*AnalyzeSentiment.cs* dosyası Kod Düzenleyicisi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="52ac4-143">The *AnalyzeSentiment.cs* file opens in the code editor.</span></span> <span data-ttu-id="52ac4-144">Aşağıdaki `using` üstüne deyimi *GitHubIssueData.cs*:</span><span class="sxs-lookup"><span data-stu-id="52ac4-144">Add the following `using` statement to the top of *GitHubIssueData.cs*:</span></span>

```csharp
using System;
using System.IO;
using System.Threading.Tasks;
using Microsoft.AspNetCore.Mvc;
using Microsoft.Azure.WebJobs;
using Microsoft.Azure.WebJobs.Extensions.Http;
using Microsoft.AspNetCore.Http;
using Microsoft.Extensions.Logging;
using Newtonsoft.Json;
using Microsoft.ML;
using Microsoft.ML.Core.Data;
using Microsoft.ML.Data;
using MLNETServerless.DataModels;
```

### <a name="create-data-models"></a><span data-ttu-id="52ac4-145">Veri modelleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="52ac4-145">Create Data Models</span></span>

<span data-ttu-id="52ac4-146">Girdi verilerini ve tahminler elde etmek için bazı sınıflar oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="52ac4-146">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="52ac4-147">Yeni bir sınıf, projenize ekleyin:</span><span class="sxs-lookup"><span data-stu-id="52ac4-147">Add a new class to your project:</span></span>

1. <span data-ttu-id="52ac4-148">Adlı bir dizin oluşturmak *DataModels* projenizde veri Modellerinizi kaydetmek için: Çözüm Gezgini'nde seçin ve proje üzerinde sağ **Ekle > Yeni klasör**.</span><span class="sxs-lookup"><span data-stu-id="52ac4-148">Create a directory named *DataModels* in your project to save your data models: In Solution Explorer, right-click on your project and select **Add > New Folder**.</span></span> <span data-ttu-id="52ac4-149">"DataModels" yazın ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="52ac4-149">Type "DataModels" and hit Enter.</span></span>
2. <span data-ttu-id="52ac4-150">Çözüm Gezgini'nde sağ *DataModels* dizin ve ardından **Ekle > Yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="52ac4-150">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
3. <span data-ttu-id="52ac4-151">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="52ac4-151">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="52ac4-152">Ardından, **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="52ac4-152">Then, select the **Add** button.</span></span> <span data-ttu-id="52ac4-153">*SentimentData.cs* dosyası Kod Düzenleyicisi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="52ac4-153">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="52ac4-154">Aşağıdaki using deyimini üstüne *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="52ac4-154">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="52ac4-155">Varolan sınıf tanımına kaldırın ve SentimentData.cs dosyaya aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="52ac4-155">Remove the existing class definition and add the following code to the SentimentData.cs file:</span></span>

    ```csharp
    public class SentimentData
    {
        [LoadColumn(0)]
        public bool Label { get; set; }
        [LoadColumn(1)]
        public string Text { get; set; }
    }
    ```

4. <span data-ttu-id="52ac4-156">Çözüm Gezgini'nde sağ *DataModels* dizin ve ardından **Ekle > Yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="52ac4-156">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="52ac4-157">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="52ac4-157">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="52ac4-158">Ardından, **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="52ac4-158">Then, select the **Add** button.</span></span> <span data-ttu-id="52ac4-159">*SentimentPrediction.cs* dosyası Kod Düzenleyicisi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="52ac4-159">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="52ac4-160">Aşağıdaki using deyimini üstüne *SentimentPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="52ac4-160">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="52ac4-161">Varolan sınıf tanımına kaldırmak ve aşağıdaki kodu ekleyin *SentimentPrediction.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="52ac4-161">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

    ```csharp
    public class SentimentPrediction
    {
        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }
    }
    ```

### <a name="add-prediction-logic"></a><span data-ttu-id="52ac4-162">Tahmin mantığı ekleyin</span><span class="sxs-lookup"><span data-stu-id="52ac4-162">Add Prediction Logic</span></span>

<span data-ttu-id="52ac4-163">Mevcut uygulanması yerine *çalıştırmak* yönteminde *AnalyzeSentiment* sınıfı aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="52ac4-163">Replace the existing implementation of *Run* method in *AnalyzeSentiment* class with the following code:</span></span>

```csharp
public static async Task<IActionResult> Run(
    [HttpTrigger(AuthorizationLevel.Function,"post", Route = null)] HttpRequest req,
    ILogger log)
{
    log.LogInformation("C# HTTP trigger function processed a request.");

    //Create Context
    MLContext mlContext = new MLContext();

    //Load Model
    using (var fs = File.OpenRead("MLModels/sentiment_model.zip"))
    {
        model = mlContext.Model.Load(fs);
    }

    //Parse HTTP Request Body
    string requestBody = await new StreamReader(req.Body).ReadToEndAsync();
    SentimentData data = JsonConvert.DeserializeObject<SentimentData>(requestBody);

    //Create Prediction Engine
    PredictionEngine<SentimentData, SentimentPrediction> predictionEngine = model.CreatePredictionEngine<SentimentData, SentimentPrediction>(mlContext);

    //Make Prediction
    SentimentPrediction prediction = predictionEngine.Predict(data);

    //Convert prediction to string
    string isToxic = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";

    //Return Prediction
    return (ActionResult)new OkObjectResult(isToxic);
}
```

## <a name="test-locally"></a><span data-ttu-id="52ac4-164">Yerel olarak test etme</span><span class="sxs-lookup"><span data-stu-id="52ac4-164">Test Locally</span></span>

<span data-ttu-id="52ac4-165">Her şeyi ayarlanır, bu uygulamayı test etmek için zaman değil:</span><span class="sxs-lookup"><span data-stu-id="52ac4-165">Now that everything is set up, it's time to test the application:</span></span>

1. <span data-ttu-id="52ac4-166">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="52ac4-166">Run the application</span></span>
1. <span data-ttu-id="52ac4-167">PowerShell'i açın ve kodu girin bağlantı noktası, bağlantı noktası olduğu istemine uygulamanız çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="52ac4-167">Open PowerShell and enter the code into the prompt where PORT is the port your application is running on.</span></span> <span data-ttu-id="52ac4-168">Genellikle 7071 bağlantı noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="52ac4-168">Typically the port is 7071.</span></span>

```powershell
Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{Text="This is a very rude movie"} | ConvertTo-Json) -ContentType "application/json"
```

<span data-ttu-id="52ac4-169">Başarılı olursa çıktı aşağıdaki metne benzer görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="52ac4-169">If successful, the output should look similar to the text below:</span></span>

```powershell
Toxic
```

<span data-ttu-id="52ac4-170">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="52ac4-170">Congratulations!</span></span> <span data-ttu-id="52ac4-171">Ayrıca, bir Azure işlevi kullanarak internet üzerinden tahminlerde bulunmak üzere modelinizi başarıyla hizmet vermektedir.</span><span class="sxs-lookup"><span data-stu-id="52ac4-171">You have successfully served your model to make predictions over the internet using an Azure Function.</span></span>

## <a name="next-steps"></a><span data-ttu-id="52ac4-172">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="52ac4-172">Next Steps</span></span>

- [<span data-ttu-id="52ac4-173">Azure’a dağıtma</span><span class="sxs-lookup"><span data-stu-id="52ac4-173">Deploy to Azure</span></span>](/azure/azure-functions/functions-develop-vs#publish-to-azure)
