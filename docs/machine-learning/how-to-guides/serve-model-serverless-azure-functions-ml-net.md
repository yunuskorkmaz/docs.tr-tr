---
title: Modeli Azure İşlevleri’ne dağıtma
description: ML.NET yaklaşım analizi makine öğrenme modelinin tahmin için Azure işlevleri'ni kullanarak internet üzerinden hizmet
ms.date: 06/11/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 7df7a6f9fcc5a4702171e1aac4b6b67e0c343748
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025984"
---
# <a name="deploy-a-model-to-azure-functions"></a><span data-ttu-id="3544c-103">Modeli Azure İşlevleri’ne dağıtma</span><span class="sxs-lookup"><span data-stu-id="3544c-103">Deploy a model to Azure Functions</span></span>

<span data-ttu-id="3544c-104">HTTP üzerinden Azure işlevleri ile sunucusuz ortam öğrenme modeli tahminler elde etmek için önceden eğitilmiş bir ML.NET makine dağıtmayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="3544c-104">Learn how to deploy a pre-trained ML.NET machine learning model for predictions over HTTP through an Azure Functions serverless environment.</span></span>

> [!NOTE]
> <span data-ttu-id="3544c-105">`PredictionEnginePool` Hizmet uzantısı, şu anda Önizleme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="3544c-105">`PredictionEnginePool` service extension is currently in preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3544c-106">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="3544c-106">Prerequisites</span></span>

- <span data-ttu-id="3544c-107">[Visual Studio 2017 15.6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) "Azure geliştirme yüklü" ve ".NET Core çoklu platform geliştirme" iş yükü.</span><span class="sxs-lookup"><span data-stu-id="3544c-107">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload and "Azure development" installed.</span></span>
- <span data-ttu-id="3544c-108">NuGet paketi sürüm 1.0.28+ Microsoft.NET.Sdk.Functions.</span><span class="sxs-lookup"><span data-stu-id="3544c-108">Microsoft.NET.Sdk.Functions NuGet Package version 1.0.28+.</span></span>
- [<span data-ttu-id="3544c-109">Azure işlevleri araçları</span><span class="sxs-lookup"><span data-stu-id="3544c-109">Azure Functions Tools</span></span>](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- <span data-ttu-id="3544c-110">PowerShell</span><span class="sxs-lookup"><span data-stu-id="3544c-110">Powershell</span></span>
- <span data-ttu-id="3544c-111">Önceden eğitilmiş model.</span><span class="sxs-lookup"><span data-stu-id="3544c-111">Pre-trained model.</span></span> <span data-ttu-id="3544c-112">Kullanım [ML.NET yaklaşım analizi Öğreticisi](../tutorials/sentiment-analysis.md) kendi modelinizi oluşturun veya bunu indirmek üzere [önceden eğitilmiş yaklaşım analizi, machine learning modeli](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span><span class="sxs-lookup"><span data-stu-id="3544c-112">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-azure-functions-project"></a><span data-ttu-id="3544c-113">Azure işlevleri projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="3544c-113">Create Azure Functions project</span></span>

1. <span data-ttu-id="3544c-114">Visual Studio 2017'yi açın.</span><span class="sxs-lookup"><span data-stu-id="3544c-114">Open Visual Studio 2017.</span></span> <span data-ttu-id="3544c-115">Seçin **dosya** > **yeni** > **proje** menü çubuğundan.</span><span class="sxs-lookup"><span data-stu-id="3544c-115">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="3544c-116">İçinde **yeni proje** iletişim kutusunda **Visual C#**  düğümünü ve ardından **bulut** düğümü.</span><span class="sxs-lookup"><span data-stu-id="3544c-116">In the **New Project** dialog, select the **Visual C#** node followed by the **Cloud** node.</span></span> <span data-ttu-id="3544c-117">Ardından **Azure işlevleri** proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="3544c-117">Then select the **Azure Functions** project template.</span></span> <span data-ttu-id="3544c-118">İçinde **adı** metin kutusuna "SentimentAnalysisFunctionsApp" yazın ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="3544c-118">In the **Name** text box, type "SentimentAnalysisFunctionsApp" and then select the **OK** button.</span></span>
1. <span data-ttu-id="3544c-119">İçinde **yeni proje** iletişim kutusunda, proje seçeneklerinde Yukarıdaki açılan listeyi açın ve seçin **Azure işlevler v2 (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="3544c-119">In the **New Project** dialog, open the dropdown above the project options and select **Azure Functions v2 (.NET Core)**.</span></span> <span data-ttu-id="3544c-120">Ardından, **Http tetikleyicisi** proje ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="3544c-120">Then, select the **Http trigger** project and then select the **OK** button.</span></span>
1. <span data-ttu-id="3544c-121">Adlı bir dizin oluşturmak *MLModels* modelinizi kaydetmek için projenizde:</span><span class="sxs-lookup"><span data-stu-id="3544c-121">Create a directory named *MLModels* in your project to save your model:</span></span>

    <span data-ttu-id="3544c-122">İçinde **Çözüm Gezgini**, projenize sağ tıklayıp **Ekle** > **yeni klasör**.</span><span class="sxs-lookup"><span data-stu-id="3544c-122">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="3544c-123">"MLModels" yazın ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="3544c-123">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="3544c-124">Yükleme **Microsoft.ML NuGet paketini**:</span><span class="sxs-lookup"><span data-stu-id="3544c-124">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="3544c-125">Çözüm Gezgini'nde seçin ve proje üzerinde sağ **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="3544c-125">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="3544c-126">Paket kaynağı olarak "nuget.org" seçin, Gözat sekmesini seçin, arama **Microsoft.ML**, bu paket listesinde seçip **yükleme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="3544c-126">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="3544c-127">Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="3544c-127">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="3544c-128">Yükleme **Microsoft.Azure.Functions.Extensions NuGet paketini**:</span><span class="sxs-lookup"><span data-stu-id="3544c-128">Install the **Microsoft.Azure.Functions.Extensions NuGet Package**:</span></span>

    <span data-ttu-id="3544c-129">Çözüm Gezgini'nde seçin ve proje üzerinde sağ **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="3544c-129">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="3544c-130">Paket kaynağı olarak "nuget.org" seçin, Gözat sekmesini seçin, arama **Microsoft.Azure.Functions.Extensions**, bu paket listesinde seçip **yükleme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="3544c-130">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Azure.Functions.Extensions**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="3544c-131">Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="3544c-131">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="3544c-132">Yükleme **Microsoft.Extensions.ML NuGet paketini**:</span><span class="sxs-lookup"><span data-stu-id="3544c-132">Install the **Microsoft.Extensions.ML NuGet Package**:</span></span>

    <span data-ttu-id="3544c-133">Çözüm Gezgini'nde seçin ve proje üzerinde sağ **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="3544c-133">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="3544c-134">Paket kaynağı olarak "nuget.org" seçin, Gözat sekmesini seçin, arama **Microsoft.Extensions.ML**, bu paket listesinde seçip **yükleme** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="3544c-134">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="3544c-135">Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="3544c-135">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="3544c-136">Güncelleştirme **Microsoft.NET.Sdk.Functions NuGet paketini** 1.0.28 sürümü için:</span><span class="sxs-lookup"><span data-stu-id="3544c-136">Update the **Microsoft.NET.Sdk.Functions NuGet Package** to version 1.0.28:</span></span>

    <span data-ttu-id="3544c-137">Çözüm Gezgini'nde seçin ve proje üzerinde sağ **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="3544c-137">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="3544c-138">Paket kaynağı olarak "nuget.org" seçin, yüklü sekmesini seçin, arama **Microsoft.NET.Sdk.Functions**, bu paket listesinde, select 1.0.28 veya sonraki sürümü açılır listeden seçip **güncelleştirme**  düğmesi.</span><span class="sxs-lookup"><span data-stu-id="3544c-138">Choose "nuget.org" as the Package source, select the Installed tab, search for **Microsoft.NET.Sdk.Functions**, select that package in the list, select 1.0.28 or later from the Version dropdown, and select the **Update** button.</span></span> <span data-ttu-id="3544c-139">Seçin **Tamam** düğmesini **Değişiklikleri Önizle** iletişim ve ardından **kabul ediyorum** düğmesini **lisans kabulü** iletişim varsa, listelenen paketlerin lisans koşullarını kabul etmiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="3544c-139">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="add-pre-trained-model-to-project"></a><span data-ttu-id="3544c-140">Önceden eğitilmiş model projeye Ekle</span><span class="sxs-lookup"><span data-stu-id="3544c-140">Add pre-trained model to project</span></span>

1. <span data-ttu-id="3544c-141">Önceden oluşturulmuş modelinizi kopyalama *MLModels* klasör.</span><span class="sxs-lookup"><span data-stu-id="3544c-141">Copy your pre-built model to the *MLModels* folder.</span></span>
1. <span data-ttu-id="3544c-142">Çözüm Gezgini'nde, önceden oluşturulmuş model dosyasını sağ tıklatın ve seçin **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="3544c-142">In Solution Explorer, right-click your pre-built model file and select **Properties**.</span></span> <span data-ttu-id="3544c-143">Altında **Gelişmiş**, değiştirin **çıkış dizinine Kopyala** için **yeniyse Kopyala**.</span><span class="sxs-lookup"><span data-stu-id="3544c-143">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

## <a name="create-azure-function-to-analyze-sentiment"></a><span data-ttu-id="3544c-144">Yaklaşımı analiz etmek için Azure işlevi oluşturma</span><span class="sxs-lookup"><span data-stu-id="3544c-144">Create Azure Function to analyze sentiment</span></span>

<span data-ttu-id="3544c-145">Yaklaşım tahmin etmek için bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3544c-145">Create a class to predict sentiment.</span></span> <span data-ttu-id="3544c-146">Yeni bir sınıf, projenize ekleyin:</span><span class="sxs-lookup"><span data-stu-id="3544c-146">Add a new class to your project:</span></span>

1. <span data-ttu-id="3544c-147">İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="3544c-147">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="3544c-148">İçinde **Yeni Öğe Ekle** iletişim kutusunda **Azure işlevi** değiştirip **adı** alanı *AnalyzeSentiment.cs*.</span><span class="sxs-lookup"><span data-stu-id="3544c-148">In the **Add New Item** dialog box, select **Azure Function** and change the **Name** field to *AnalyzeSentiment.cs*.</span></span> <span data-ttu-id="3544c-149">Ardından, **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="3544c-149">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="3544c-150">İçinde **yeni Azure işlevi** iletişim kutusunda **Http tetikleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="3544c-150">In the **New Azure Function** dialog box, select **Http Trigger**.</span></span> <span data-ttu-id="3544c-151">Ardından, **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="3544c-151">Then, select the **OK** button.</span></span>

    <span data-ttu-id="3544c-152">*AnalyzeSentiment.cs* dosyası Kod Düzenleyicisi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="3544c-152">The *AnalyzeSentiment.cs* file opens in the code editor.</span></span> <span data-ttu-id="3544c-153">Aşağıdaki `using` üstüne deyimi *AnalyzeSentiment.cs*:</span><span class="sxs-lookup"><span data-stu-id="3544c-153">Add the following `using` statement to the top of *AnalyzeSentiment.cs*:</span></span>

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

    <span data-ttu-id="3544c-154">Varsayılan olarak, `AnalyzeSentiment` sınıfı `static`.</span><span class="sxs-lookup"><span data-stu-id="3544c-154">By default, the `AnalyzeSentiment` class is `static`.</span></span> <span data-ttu-id="3544c-155">Kaldırdığınızdan emin olun `static` sınıf tanımından anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="3544c-155">Make sure to remove the `static` keyword from the class definition.</span></span>

    ```csharp
    public class AnalyzeSentiment
    {
    
    }
    ```

## <a name="create-data-models"></a><span data-ttu-id="3544c-156">Veri modelleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="3544c-156">Create data models</span></span>

<span data-ttu-id="3544c-157">Girdi verilerini ve tahminler elde etmek için bazı sınıflar oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3544c-157">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="3544c-158">Yeni bir sınıf, projenize ekleyin:</span><span class="sxs-lookup"><span data-stu-id="3544c-158">Add a new class to your project:</span></span>

1. <span data-ttu-id="3544c-159">Adlı bir dizin oluşturmak *DataModels* projenizde veri Modellerinizi kaydetmek için: Çözüm Gezgini'nde seçin ve proje üzerinde sağ **Ekle > Yeni klasör**.</span><span class="sxs-lookup"><span data-stu-id="3544c-159">Create a directory named *DataModels* in your project to save your data models: In Solution Explorer, right-click on your project and select **Add > New Folder**.</span></span> <span data-ttu-id="3544c-160">"DataModels" yazın ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="3544c-160">Type "DataModels" and hit Enter.</span></span>
2. <span data-ttu-id="3544c-161">Çözüm Gezgini'nde sağ *DataModels* dizin ve ardından **Ekle > Yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="3544c-161">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
3. <span data-ttu-id="3544c-162">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="3544c-162">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="3544c-163">Ardından, **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="3544c-163">Then, select the **Add** button.</span></span> 

    <span data-ttu-id="3544c-164">*SentimentData.cs* dosyası Kod Düzenleyicisi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="3544c-164">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="3544c-165">Aşağıdaki using deyimini üstüne *SentimentData.cs*:</span><span class="sxs-lookup"><span data-stu-id="3544c-165">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="3544c-166">Varolan sınıf tanımına kaldırmak ve aşağıdaki kodu ekleyin *SentimentData.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="3544c-166">Remove the existing class definition and add the following code to the *SentimentData.cs* file:</span></span>
    
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

4. <span data-ttu-id="3544c-167">Çözüm Gezgini'nde sağ *DataModels* dizin ve ardından **Ekle > Yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="3544c-167">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="3544c-168">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="3544c-168">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="3544c-169">Ardından, **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="3544c-169">Then, select the **Add** button.</span></span> <span data-ttu-id="3544c-170">*SentimentPrediction.cs* dosyası Kod Düzenleyicisi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="3544c-170">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="3544c-171">Aşağıdaki using deyimini üstüne *SentimentPrediction.cs*:</span><span class="sxs-lookup"><span data-stu-id="3544c-171">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="3544c-172">Varolan sınıf tanımına kaldırmak ve aşağıdaki kodu ekleyin *SentimentPrediction.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="3544c-172">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    <span data-ttu-id="3544c-173">`SentimentPrediction` devralınan `SentimentData` özgün verilere erişim sağlayan `SentimentText` özelliğinin yanı sıra model tarafından oluşturulan çıktı.</span><span class="sxs-lookup"><span data-stu-id="3544c-173">`SentimentPrediction` inherits from `SentimentData` which provides access to the original data in the `SentimentText` property as well as the output generated by the model.</span></span>

## <a name="register-predictionenginepool-service"></a><span data-ttu-id="3544c-174">PredictionEnginePool hizmeti kaydedin</span><span class="sxs-lookup"><span data-stu-id="3544c-174">Register PredictionEnginePool service</span></span>

<span data-ttu-id="3544c-175">Tek bir tahminde bulunmak için kullanmak [ `PredictionEngine` ](xref:Microsoft.ML.PredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="3544c-175">To make a single prediction, use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="3544c-176">Kullanmak için [ `PredictionEngine` ](xref:Microsoft.ML.PredictionEngine%602) gerektiğinde uygulamanızı oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3544c-176">In order to use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) in your application you must create it when it's needed.</span></span> <span data-ttu-id="3544c-177">Bu durumda, dikkate alınması gereken bir en iyi bağımlılık ekleme yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="3544c-177">In that case, a best practice to consider is dependency injection.</span></span>

<span data-ttu-id="3544c-178">Hakkında bilgi edinmek istiyorsanız aşağıdaki bağlantıda daha fazla bilgi sağlar. [bağımlılık ekleme](https://en.wikipedia.org/wiki/Dependency_injection).</span><span class="sxs-lookup"><span data-stu-id="3544c-178">The following link provides more information if you want to learn about [dependency injection](https://en.wikipedia.org/wiki/Dependency_injection).</span></span>

1. <span data-ttu-id="3544c-179">İçinde **Çözüm Gezgini**projeye sağ tıklayın ve ardından **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="3544c-179">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="3544c-180">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sınıfı** değiştirip **adı** alanı *Startup.cs*.</span><span class="sxs-lookup"><span data-stu-id="3544c-180">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *Startup.cs*.</span></span> <span data-ttu-id="3544c-181">Ardından, **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="3544c-181">Then, select the **Add** button.</span></span> 

    <span data-ttu-id="3544c-182">*Startup.cs* dosyası Kod Düzenleyicisi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="3544c-182">The *Startup.cs* file opens in the code editor.</span></span> <span data-ttu-id="3544c-183">Aşağıdaki using deyimini üstüne *Startup.cs*:</span><span class="sxs-lookup"><span data-stu-id="3544c-183">Add the following using statement to the top of *Startup.cs*:</span></span>

    ```csharp
    using Microsoft.Azure.WebJobs;
    using Microsoft.Azure.WebJobs.Hosting;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisFunctionsApp;
    using SentimentAnalysisFunctionsApp.DataModels;
    ```

    <span data-ttu-id="3544c-184">Kullanarak aşağıdaki var olan kod kaldırma deyimleri ve aşağıdaki kodu ekleyin *Startup.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="3544c-184">Remove the existing code below the using statements and add the following code to the *Startup.cs* file:</span></span>

    ```csharp
    [assembly: WebJobsStartup(typeof(Startup))]
    namespace SentimentAnalysisFunctionsApp
    {
        class Startup : IWebJobsStartup
        {
            public void Configure(IWebJobsBuilder builder)
            {
                builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
                    .FromFile("MLModels/sentiment_model.zip");
            }
        }
    }
    ```

<span data-ttu-id="3544c-185">Yüksek düzeyde, bu kod nesneleri ve otomatik yerine el ile yapmanıza gerek kalmadan uygulama tarafından istendiğinde hizmetlerini başlatır.</span><span class="sxs-lookup"><span data-stu-id="3544c-185">At a high level, this code initializes the objects and services automatically when requested by the application instead of having to manually do it.</span></span>

> [!WARNING]
> <span data-ttu-id="3544c-186">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) iş parçacığı açısından güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="3544c-186">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="3544c-187">Performansı artırmak ve iş parçacığı güvenliği için kullanmak `PredictionEnginePool` oluşturan hizmeti bir [ `ObjectPool` ](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) , `PredictionEngine` nesneleri uygulama kullanımı.</span><span class="sxs-lookup"><span data-stu-id="3544c-187">For improved performance and thread safety, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of `PredictionEngine` objects for application use.</span></span> 

## <a name="load-the-model-into-the-function"></a><span data-ttu-id="3544c-188">İşleve model yüklenemiyor</span><span class="sxs-lookup"><span data-stu-id="3544c-188">Load the model into the function</span></span>

<span data-ttu-id="3544c-189">Aşağıdaki kodu ekleyin *AnalyzeSentiment* sınıfı:</span><span class="sxs-lookup"><span data-stu-id="3544c-189">Insert the following code inside the *AnalyzeSentiment* class:</span></span>

```csharp
private readonly PredictionEnginePool<SentimentData, SentimentPrediction> _predictionEnginePool;

// AnalyzeSentiment class constructor
public AnalyzeSentiment(PredictionEnginePool<SentimentData, SentimentPrediction> predictionEnginePool)
{
    _predictionEnginePool = predictionEnginePool;
}
```

<span data-ttu-id="3544c-190">Bu kod atar `PredictionEnginePool` bağımlılık ekleme erişmenizi işlevin oluşturucusuna geçirerek.</span><span class="sxs-lookup"><span data-stu-id="3544c-190">This code assigns the `PredictionEnginePool` by passing it to the function's constructor which you get via dependency injection.</span></span>

## <a name="use-the-model-to-make-predictions"></a><span data-ttu-id="3544c-191">Tahminler elde etmeye modelini kullanın</span><span class="sxs-lookup"><span data-stu-id="3544c-191">Use the model to make predictions</span></span>

<span data-ttu-id="3544c-192">Mevcut uygulanması yerine *çalıştırmak* yönteminde *AnalyzeSentiment* sınıfı aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="3544c-192">Replace the existing implementation of *Run* method in *AnalyzeSentiment* class with the following code:</span></span>

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

<span data-ttu-id="3544c-193">Zaman `Run` yöntemini yürütür, HTTP isteği gelen verileri seri durumdan ve için girdi olarak kullanılan `PredictionEnginePool`.</span><span class="sxs-lookup"><span data-stu-id="3544c-193">When the `Run` method executes, the incoming data from the HTTP request is deserialized and used as input for the `PredictionEnginePool`.</span></span> <span data-ttu-id="3544c-194">`Predict` Yöntemi tahmin oluşturmak ve bir sonuç kullanıcıya sonra çağrılır.</span><span class="sxs-lookup"><span data-stu-id="3544c-194">The `Predict` method is then called to generate a prediction and return the result to the user.</span></span> 

## <a name="test-locally"></a><span data-ttu-id="3544c-195">Yerel olarak test etme</span><span class="sxs-lookup"><span data-stu-id="3544c-195">Test locally</span></span>

<span data-ttu-id="3544c-196">Her şeyi ayarlanır, bu uygulamayı test etmek için zaman değil:</span><span class="sxs-lookup"><span data-stu-id="3544c-196">Now that everything is set up, it's time to test the application:</span></span>

1. <span data-ttu-id="3544c-197">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="3544c-197">Run the application</span></span>
1. <span data-ttu-id="3544c-198">PowerShell'i açın ve kodu girin bağlantı noktası, bağlantı noktası olduğu istemine uygulamanız çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="3544c-198">Open PowerShell and enter the code into the prompt where PORT is the port your application is running on.</span></span> <span data-ttu-id="3544c-199">Genellikle 7071 bağlantı noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="3544c-199">Typically the port is 7071.</span></span>

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="3544c-200">Başarılı olursa çıktı aşağıdaki metne benzer görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="3544c-200">If successful, the output should look similar to the text below:</span></span>
    
    ```powershell
    Negative
    ```

<span data-ttu-id="3544c-201">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="3544c-201">Congratulations!</span></span> <span data-ttu-id="3544c-202">Ayrıca, bir Azure işlevi kullanarak internet üzerinden tahminlerde bulunmak üzere modelinizi başarıyla hizmet vermektedir.</span><span class="sxs-lookup"><span data-stu-id="3544c-202">You have successfully served your model to make predictions over the internet using an Azure Function.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3544c-203">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="3544c-203">Next Steps</span></span>

- [<span data-ttu-id="3544c-204">Azure’a dağıtma</span><span class="sxs-lookup"><span data-stu-id="3544c-204">Deploy to Azure</span></span>](/azure/azure-functions/functions-develop-vs#publish-to-azure)
