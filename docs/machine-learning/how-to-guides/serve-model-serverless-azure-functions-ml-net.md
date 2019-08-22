---
title: Modeli Azure İşlevleri’ne dağıtma
description: Azure Işlevleri 'ni kullanarak Internet üzerinden tahmin için ML.NET yaklaşım analizi makine öğrenimi modelini sunar
ms.date: 08/20/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 96b62017994da5b7b209c441b3e7fb760cad5201
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666677"
---
# <a name="deploy-a-model-to-azure-functions"></a><span data-ttu-id="563ab-103">Modeli Azure İşlevleri’ne dağıtma</span><span class="sxs-lookup"><span data-stu-id="563ab-103">Deploy a model to Azure Functions</span></span>

<span data-ttu-id="563ab-104">Azure Işlevleri sunucusuz bir ortam aracılığıyla HTTP üzerinden tahmin için önceden eğitilen ML.NET makine öğrenimi modelini dağıtmayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="563ab-104">Learn how to deploy a pre-trained ML.NET machine learning model for predictions over HTTP through an Azure Functions serverless environment.</span></span>

> [!NOTE]
> <span data-ttu-id="563ab-105">`PredictionEnginePool`Hizmet Uzantısı Şu anda önizleme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="563ab-105">`PredictionEnginePool` service extension is currently in preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="563ab-106">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="563ab-106">Prerequisites</span></span>

- <span data-ttu-id="563ab-107">".NET Core platformlar arası geliştirme" iş yükü ve "Azure geliştirme" yüklü olan [Visual Studio 2017 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) .</span><span class="sxs-lookup"><span data-stu-id="563ab-107">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload and "Azure development" installed.</span></span>
- <span data-ttu-id="563ab-108">Microsoft. NET. SDK. Functions NuGet paketi sürüm 1.0.28 +.</span><span class="sxs-lookup"><span data-stu-id="563ab-108">Microsoft.NET.Sdk.Functions NuGet Package version 1.0.28+.</span></span>
- [<span data-ttu-id="563ab-109">Azure Işlevleri araçları</span><span class="sxs-lookup"><span data-stu-id="563ab-109">Azure Functions Tools</span></span>](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- <span data-ttu-id="563ab-110">PowerShell</span><span class="sxs-lookup"><span data-stu-id="563ab-110">Powershell</span></span>
- <span data-ttu-id="563ab-111">Önceden eğitilen model.</span><span class="sxs-lookup"><span data-stu-id="563ab-111">Pre-trained model.</span></span> <span data-ttu-id="563ab-112">Kendi modelinizi derlemek için [ML.NET yaklaşım Analizi öğreticisini](../tutorials/sentiment-analysis.md) kullanın veya bu [önceden eğitilen yaklaşım Analizi Machine Learning modelini](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip) indirin</span><span class="sxs-lookup"><span data-stu-id="563ab-112">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-azure-functions-project"></a><span data-ttu-id="563ab-113">Azure Işlevleri projesi oluştur</span><span class="sxs-lookup"><span data-stu-id="563ab-113">Create Azure Functions project</span></span>

1. <span data-ttu-id="563ab-114">Visual Studio 2017'yi açın.</span><span class="sxs-lookup"><span data-stu-id="563ab-114">Open Visual Studio 2017.</span></span> <span data-ttu-id="563ab-115">Menü çubuğundan **Dosya** > **Yeni** > **Proje** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="563ab-115">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="563ab-116">**Yeni proje** iletişim kutusunda, **Visual C#**  düğümünü ve ardından **bulut** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="563ab-116">In the **New Project** dialog, select the **Visual C#** node followed by the **Cloud** node.</span></span> <span data-ttu-id="563ab-117">Ardından **Azure işlevleri** proje şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="563ab-117">Then select the **Azure Functions** project template.</span></span> <span data-ttu-id="563ab-118">**Ad** metin kutusuna "SentimentAnalysisFunctionsApp" yazın ve **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="563ab-118">In the **Name** text box, type "SentimentAnalysisFunctionsApp" and then select the **OK** button.</span></span>
1. <span data-ttu-id="563ab-119">**Yeni proje** iletişim kutusunda, proje seçeneklerinin üzerindeki açılan menüyü açın ve **Azure işlevleri v2 (.NET Core)** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="563ab-119">In the **New Project** dialog, open the dropdown above the project options and select **Azure Functions v2 (.NET Core)**.</span></span> <span data-ttu-id="563ab-120">Ardından, **http tetikleyicisi** projesini seçin ve **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="563ab-120">Then, select the **Http trigger** project and then select the **OK** button.</span></span>
1. <span data-ttu-id="563ab-121">Modelinize kaydetmek için projenizde *Mlmodeller* adlı bir dizin oluşturun:</span><span class="sxs-lookup"><span data-stu-id="563ab-121">Create a directory named *MLModels* in your project to save your model:</span></span>

    <span data-ttu-id="563ab-122">**Çözüm Gezgini**, projenize sağ tıklayın ve**Yeni klasör** **Ekle** > ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="563ab-122">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="563ab-123">"Mlmodeller" yazın ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="563ab-123">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="563ab-124">**Microsoft.ml NuGet paketini**yükler:</span><span class="sxs-lookup"><span data-stu-id="563ab-124">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="563ab-125">Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="563ab-125">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="563ab-126">Paket kaynağı olarak "nuget.org" öğesini seçin, araştır sekmesini seçin, **Microsoft.ml**için arama yapın, listeden bu paketi seçin ve sonra da **Install** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="563ab-126">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="563ab-127">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="563ab-127">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="563ab-128">**Microsoft. Azure. Functions. Extensions NuGet paketini**yükler:</span><span class="sxs-lookup"><span data-stu-id="563ab-128">Install the **Microsoft.Azure.Functions.Extensions NuGet Package**:</span></span>

    <span data-ttu-id="563ab-129">Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="563ab-129">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="563ab-130">Paket kaynağı olarak "nuget.org" öğesini seçin, gözden geçirme sekmesini seçin, **Microsoft. Azure. Functions. Extensions**araması yapın, listeden bu paketi seçin ve sonra da **Install** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="563ab-130">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Azure.Functions.Extensions**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="563ab-131">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="563ab-131">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="563ab-132">**Microsoft.Extensions.ml NuGet paketini**yükler:</span><span class="sxs-lookup"><span data-stu-id="563ab-132">Install the **Microsoft.Extensions.ML NuGet Package**:</span></span>

    <span data-ttu-id="563ab-133">Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="563ab-133">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="563ab-134">Paket kaynağı olarak "nuget.org" öğesini seçin, araştır sekmesini seçin, **Microsoft.Extensions.ml**için arama yapın, listeden bu paketi seçin ve sonra da **Install** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="563ab-134">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="563ab-135">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="563ab-135">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="563ab-136">**Microsoft. net. SDK. Functions NuGet paketini** 1.0.28 + sürümüne güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="563ab-136">Update the **Microsoft.NET.Sdk.Functions NuGet Package** to version 1.0.28+:</span></span>

    <span data-ttu-id="563ab-137">Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="563ab-137">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="563ab-138">Paket kaynağı olarak "nuget.org" öğesini seçin, yüklü sekmesini seçin, **Microsoft. net. SDK. Functions**araması yapın, listeden bu paketi seçin, sürüm açılan menüsünde 1.0.28 veya üzeri ' i seçin ve **Güncelleştir** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="563ab-138">Choose "nuget.org" as the Package source, select the Installed tab, search for **Microsoft.NET.Sdk.Functions**, select that package in the list, select 1.0.28 or later from the Version dropdown, and select the **Update** button.</span></span> <span data-ttu-id="563ab-139">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="563ab-139">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="add-pre-trained-model-to-project"></a><span data-ttu-id="563ab-140">Projeye önceden eğitilen Model Ekle</span><span class="sxs-lookup"><span data-stu-id="563ab-140">Add pre-trained model to project</span></span>

1. <span data-ttu-id="563ab-141">Önceden oluşturulmuş modelinizi *Mlmodeller* klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="563ab-141">Copy your pre-built model to the *MLModels* folder.</span></span>
1. <span data-ttu-id="563ab-142">Çözüm Gezgini, önceden oluşturulmuş model dosyanıza sağ tıklayıp **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="563ab-142">In Solution Explorer, right-click your pre-built model file and select **Properties**.</span></span> <span data-ttu-id="563ab-143">**Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="563ab-143">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

## <a name="create-azure-function-to-analyze-sentiment"></a><span data-ttu-id="563ab-144">Yaklaşımı çözümlemek için Azure Işlevi oluşturma</span><span class="sxs-lookup"><span data-stu-id="563ab-144">Create Azure Function to analyze sentiment</span></span>

<span data-ttu-id="563ab-145">Yaklaşımı tahmin etmek için bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="563ab-145">Create a class to predict sentiment.</span></span> <span data-ttu-id="563ab-146">Projenize yeni bir sınıf ekleyin:</span><span class="sxs-lookup"><span data-stu-id="563ab-146">Add a new class to your project:</span></span>

1. <span data-ttu-id="563ab-147">**Çözüm Gezgini**, projeye sağ tıklayın ve ardından**Yeni öğe** **Ekle** > ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="563ab-147">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="563ab-148">**Yeni öğe Ekle** Iletişim kutusunda **Azure işlevi** ' ni seçin ve **ad** alanını *AnalyzeSentiment.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="563ab-148">In the **Add New Item** dialog box, select **Azure Function** and change the **Name** field to *AnalyzeSentiment.cs*.</span></span> <span data-ttu-id="563ab-149">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="563ab-149">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="563ab-150">**Yeni Azure işlevi** Iletişim kutusunda **http tetikleyicisi**' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="563ab-150">In the **New Azure Function** dialog box, select **Http Trigger**.</span></span> <span data-ttu-id="563ab-151">Ardından **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="563ab-151">Then, select the **OK** button.</span></span>

    <span data-ttu-id="563ab-152">*AnalyzeSentiment.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="563ab-152">The *AnalyzeSentiment.cs* file opens in the code editor.</span></span> <span data-ttu-id="563ab-153">Aşağıdaki `using` ifadeyi *AnalyzeSentiment.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="563ab-153">Add the following `using` statement to the top of *AnalyzeSentiment.cs*:</span></span>

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
    using Microsoft.Extensions.ML;
    using SentimentAnalysisFunctionsApp.DataModels;
    ```

    <span data-ttu-id="563ab-154">Varsayılan olarak, `AnalyzeSentiment` `static`sınıfı.</span><span class="sxs-lookup"><span data-stu-id="563ab-154">By default, the `AnalyzeSentiment` class is `static`.</span></span> <span data-ttu-id="563ab-155">`static` Anahtar sözcüğünü sınıf tanımından kaldırdığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="563ab-155">Make sure to remove the `static` keyword from the class definition.</span></span>

    ```csharp
    public class AnalyzeSentiment
    {
    
    }
    ```

## <a name="create-data-models"></a><span data-ttu-id="563ab-156">Veri modelleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="563ab-156">Create data models</span></span>

<span data-ttu-id="563ab-157">Giriş verileriniz ve tahminlerinizi için bazı sınıflar oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="563ab-157">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="563ab-158">Projenize yeni bir sınıf ekleyin:</span><span class="sxs-lookup"><span data-stu-id="563ab-158">Add a new class to your project:</span></span>

1. <span data-ttu-id="563ab-159">Veri modellerinizi kaydetmek için projenizde *Datamodeller* adlı bir dizin oluşturun: Çözüm Gezgini, projenize sağ tıklayın ve **> yeni klasör ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="563ab-159">Create a directory named *DataModels* in your project to save your data models: In Solution Explorer, right-click on your project and select **Add > New Folder**.</span></span> <span data-ttu-id="563ab-160">"Datamodeller" yazın ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="563ab-160">Type "DataModels" and hit Enter.</span></span>
2. <span data-ttu-id="563ab-161">Çözüm Gezgini, *veri modelleri* dizinine sağ tıklayın ve sonra **> yeni öğe Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="563ab-161">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
3. <span data-ttu-id="563ab-162">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *SentimentData.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="563ab-162">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="563ab-163">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="563ab-163">Then, select the **Add** button.</span></span> 

    <span data-ttu-id="563ab-164">*SentimentData.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="563ab-164">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="563ab-165">Aşağıdaki using ifadesini *SentimentData.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="563ab-165">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="563ab-166">Mevcut sınıf tanımını kaldırın ve aşağıdaki kodu *SentimentData.cs* dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="563ab-166">Remove the existing class definition and add the following code to the *SentimentData.cs* file:</span></span>
    
    ```csharp
    public class SentimentData
    {
        [LoadColumn(0)]
        public string SentimentText;

        [LoadColumn(1)]
        [ColumnName("Label")]
        public bool Sentiment;
    }
    ```

4. <span data-ttu-id="563ab-167">Çözüm Gezgini, *veri modelleri* dizinine sağ tıklayın ve sonra **> yeni öğe Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="563ab-167">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="563ab-168">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *SentimentPrediction.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="563ab-168">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="563ab-169">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="563ab-169">Then, select the **Add** button.</span></span> <span data-ttu-id="563ab-170">*SentimentPrediction.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="563ab-170">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="563ab-171">Aşağıdaki using ifadesini *SentimentPrediction.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="563ab-171">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="563ab-172">Mevcut sınıf tanımını kaldırın ve aşağıdaki kodu *SentimentPrediction.cs* dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="563ab-172">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    <span data-ttu-id="563ab-173">`SentimentPrediction``SentimentData` ,`SentimentText` özelliğindeki özgün verilere ve model tarafından oluşturulan çıktıya erişim sağlayan öğesinden devralır.</span><span class="sxs-lookup"><span data-stu-id="563ab-173">`SentimentPrediction` inherits from `SentimentData` which provides access to the original data in the `SentimentText` property as well as the output generated by the model.</span></span>

## <a name="register-predictionenginepool-service"></a><span data-ttu-id="563ab-174">PredictionEnginePool hizmetini Kaydet</span><span class="sxs-lookup"><span data-stu-id="563ab-174">Register PredictionEnginePool service</span></span>

<span data-ttu-id="563ab-175">Tek bir tahmin yapmak için kullanın [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="563ab-175">To make a single prediction, use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="563ab-176">Uygulamanızda kullanabilmeniz [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) için, gerektiğinde oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="563ab-176">In order to use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) in your application you must create it when it's needed.</span></span> <span data-ttu-id="563ab-177">Bu durumda, dikkate alınması gereken en iyi yöntem bağımlılık ekleme yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="563ab-177">In that case, a best practice to consider is dependency injection.</span></span>

<span data-ttu-id="563ab-178">Aşağıdaki bağlantı, [bağımlılık ekleme](https://en.wikipedia.org/wiki/Dependency_injection)hakkında bilgi edinmek istiyorsanız daha fazla bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="563ab-178">The following link provides more information if you want to learn about [dependency injection](https://en.wikipedia.org/wiki/Dependency_injection).</span></span>

1. <span data-ttu-id="563ab-179">**Çözüm Gezgini**, projeye sağ tıklayın ve ardından**Yeni öğe** **Ekle** > ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="563ab-179">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="563ab-180">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *Startup.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="563ab-180">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *Startup.cs*.</span></span> <span data-ttu-id="563ab-181">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="563ab-181">Then, select the **Add** button.</span></span> 

    <span data-ttu-id="563ab-182">*Startup.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="563ab-182">The *Startup.cs* file opens in the code editor.</span></span> <span data-ttu-id="563ab-183">Aşağıdaki using ifadesini *Startup.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="563ab-183">Add the following using statement to the top of *Startup.cs*:</span></span>

    ```csharp
    using Microsoft.Azure.Functions.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisFunctionsApp;
    using SentimentAnalysisFunctionsApp.DataModels;
    ```

    <span data-ttu-id="563ab-184">Using deyimlerinin altındaki mevcut kodu kaldırın ve *Startup.cs* dosyasına aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="563ab-184">Remove the existing code below the using statements and add the following code to the *Startup.cs* file:</span></span>

    ```csharp
    [assembly: FunctionsStartup(typeof(Startup))]
    namespace SentimentAnalysisFunctionsApp
    {
        public class Startup : FunctionsStartup
        {
            public override void Configure(IFunctionsHostBuilder builder)
            {
                builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
                    .FromFile("MLModels/sentiment_model.zip");
            }
        }
    }
    ```

<span data-ttu-id="563ab-185">Yüksek düzeyde bu kod, uygulama tarafından el ile yapmak yerine nesneleri ve hizmetleri otomatik olarak başlatır.</span><span class="sxs-lookup"><span data-stu-id="563ab-185">At a high level, this code initializes the objects and services automatically when requested by the application instead of having to manually do it.</span></span>

> [!WARNING]
> <span data-ttu-id="563ab-186">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602), iş parçacığı açısından güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="563ab-186">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="563ab-187">Gelişmiş performans ve iş parçacığı güvenliği için, uygulama `PredictionEnginePool` kullanımı için `PredictionEngine` bir [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) nesne oluşturan hizmetini kullanın.</span><span class="sxs-lookup"><span data-stu-id="563ab-187">For improved performance and thread safety, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of `PredictionEngine` objects for application use.</span></span> 

## <a name="load-the-model-into-the-function"></a><span data-ttu-id="563ab-188">Modeli işleve yükleme</span><span class="sxs-lookup"><span data-stu-id="563ab-188">Load the model into the function</span></span>

<span data-ttu-id="563ab-189">Aşağıdaki kodu, *çözümleyiciler* sınıfının içine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="563ab-189">Insert the following code inside the *AnalyzeSentiment* class:</span></span>

```csharp
private readonly PredictionEnginePool<SentimentData, SentimentPrediction> _predictionEnginePool;

// AnalyzeSentiment class constructor
public AnalyzeSentiment(PredictionEnginePool<SentimentData, SentimentPrediction> predictionEnginePool)
{
    _predictionEnginePool = predictionEnginePool;
}
```

<span data-ttu-id="563ab-190">Bu kod, `PredictionEnginePool` bağımlılığı ekleme yoluyla aldığınız işlevin oluşturucusuna geçirerek öğesine atar.</span><span class="sxs-lookup"><span data-stu-id="563ab-190">This code assigns the `PredictionEnginePool` by passing it to the function's constructor which you get via dependency injection.</span></span>

## <a name="use-the-model-to-make-predictions"></a><span data-ttu-id="563ab-191">Tahminleri yapmak için modeli kullanın</span><span class="sxs-lookup"><span data-stu-id="563ab-191">Use the model to make predictions</span></span>

<span data-ttu-id="563ab-192">*Çözümleyiciler* sınıfında bulunan *Run* yönteminin mevcut uygulamasını aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="563ab-192">Replace the existing implementation of *Run* method in *AnalyzeSentiment* class with the following code:</span></span>

```csharp
[FunctionName("AnalyzeSentiment")]
public async Task<IActionResult> Run(
[HttpTrigger(AuthorizationLevel.Function, "post", Route = null)] HttpRequest req,
ILogger log)
{
    log.LogInformation("C# HTTP trigger function processed a request.");

    //Parse HTTP Request Body
    string requestBody = await new StreamReader(req.Body).ReadToEndAsync();
    SentimentData data = JsonConvert.DeserializeObject<SentimentData>(requestBody);
    
    //Make Prediction
    SentimentPrediction prediction = _predictionEnginePool.Predict(data);

    //Convert prediction to string
    string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

    //Return Prediction
    return (ActionResult)new OkObjectResult(sentiment);
}
```

<span data-ttu-id="563ab-193">Yöntem yürütüldüğünde, http isteğinden gelen veriler seri durumdan çıkarılmış olur ve `PredictionEnginePool`için giriş olarak kullanılır. `Run`</span><span class="sxs-lookup"><span data-stu-id="563ab-193">When the `Run` method executes, the incoming data from the HTTP request is deserialized and used as input for the `PredictionEnginePool`.</span></span> <span data-ttu-id="563ab-194">Daha `Predict` sonra yöntemi bir tahmin oluşturmak ve sonucu kullanıcıya döndürmek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="563ab-194">The `Predict` method is then called to generate a prediction and return the result to the user.</span></span> 

## <a name="test-locally"></a><span data-ttu-id="563ab-195">Yerel olarak test etme</span><span class="sxs-lookup"><span data-stu-id="563ab-195">Test locally</span></span>

<span data-ttu-id="563ab-196">Her şey ayarlandığına göre, uygulamayı test etmek zaman alabilir:</span><span class="sxs-lookup"><span data-stu-id="563ab-196">Now that everything is set up, it's time to test the application:</span></span>

1. <span data-ttu-id="563ab-197">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="563ab-197">Run the application</span></span>
1. <span data-ttu-id="563ab-198">PowerShell 'i açın ve kodu, uygulamanızın üzerinde çalıştığı bağlantı noktası olan bağlantı noktasının bulunduğu istemine girin.</span><span class="sxs-lookup"><span data-stu-id="563ab-198">Open PowerShell and enter the code into the prompt where PORT is the port your application is running on.</span></span> <span data-ttu-id="563ab-199">Genellikle bağlantı noktası 7071 ' dir.</span><span class="sxs-lookup"><span data-stu-id="563ab-199">Typically the port is 7071.</span></span>

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="563ab-200">Başarılı olursa, çıkış aşağıdaki metne benzer görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="563ab-200">If successful, the output should look similar to the text below:</span></span>
    
    ```powershell
    Negative
    ```

<span data-ttu-id="563ab-201">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="563ab-201">Congratulations!</span></span> <span data-ttu-id="563ab-202">Azure Işlevi kullanarak, internet üzerinden tahmine dayalı hale getirmek için modelinizi başarıyla sundu.</span><span class="sxs-lookup"><span data-stu-id="563ab-202">You have successfully served your model to make predictions over the internet using an Azure Function.</span></span>

## <a name="next-steps"></a><span data-ttu-id="563ab-203">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="563ab-203">Next Steps</span></span>

- [<span data-ttu-id="563ab-204">Azure’a dağıtma</span><span class="sxs-lookup"><span data-stu-id="563ab-204">Deploy to Azure</span></span>](/azure/azure-functions/functions-develop-vs#publish-to-azure)
