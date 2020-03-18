---
title: Modeli Azure İşlevleri’ne dağıtma
description: Azure Fonksiyonlarını kullanarak internet üzerinden tahmin için ML.NET duygu analizi makine öğrenme modeline hizmet edin
ms.date: 02/21/2020
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 33afd568bb12b855a3888bec31f2e9bbc3c720da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77628676"
---
# <a name="deploy-a-model-to-azure-functions"></a><span data-ttu-id="b8f9e-103">Modeli Azure İşlevleri’ne dağıtma</span><span class="sxs-lookup"><span data-stu-id="b8f9e-103">Deploy a model to Azure Functions</span></span>

<span data-ttu-id="b8f9e-104">Azure İşlevler sunucusuz bir ortam aracılığıyla HTTP üzerinden öngörüler için önceden eğitilmiş bir ML.NET makine öğrenimi modelini nasıl dağıtılacayacak gerektiğini öğrenin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-104">Learn how to deploy a pre-trained ML.NET machine learning model for predictions over HTTP through an Azure Functions serverless environment.</span></span>

> [!NOTE]
> <span data-ttu-id="b8f9e-105">Bu örnek, hizmetin `PredictionEnginePool` önizleme sürümünü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-105">This sample runs a preview version of the `PredictionEnginePool` service.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b8f9e-106">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="b8f9e-106">Prerequisites</span></span>

- <span data-ttu-id="b8f9e-107">[Visual Studio 2017 sürümü 15.6 veya daha sonra](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core çapraz platform geliştirme" iş yükü ve "Azure geliştirme" yüklü.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-107">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload and "Azure development" installed.</span></span>
- [<span data-ttu-id="b8f9e-108">Azure İşlevaraçları</span><span class="sxs-lookup"><span data-stu-id="b8f9e-108">Azure Functions Tools</span></span>](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- <span data-ttu-id="b8f9e-109">PowerShell</span><span class="sxs-lookup"><span data-stu-id="b8f9e-109">Powershell</span></span>
- <span data-ttu-id="b8f9e-110">Önceden eğitilmiş bir model.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-110">Pre-trained model.</span></span> <span data-ttu-id="b8f9e-111">Kendi modelinizi oluşturmak veya bu [önceden eğitilmiş duygu analizi makine öğrenme modelini](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip) indirmek için ML.NET Sentiment Analysis [öğreticisini](../tutorials/sentiment-analysis.md) kullanın</span><span class="sxs-lookup"><span data-stu-id="b8f9e-111">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="azure-functions-sample-overview"></a><span data-ttu-id="b8f9e-112">Azure Fonksiyonları örnek genel bakış</span><span class="sxs-lookup"><span data-stu-id="b8f9e-112">Azure Functions sample overview</span></span>

<span data-ttu-id="b8f9e-113">Bu örnek, metnin duyarlılığını olumlu veya negatif olarak kategorilere ayırmak için önceden eğitilmiş bir ikili sınıflandırma modeli kullanan bir **C# HTTP Trigger Azure İşleme uygulamasıdır.**</span><span class="sxs-lookup"><span data-stu-id="b8f9e-113">This sample is a **C# HTTP Trigger Azure Functions application** that uses a pretrained binary classification model to categorize the sentiment of text as positive or negative.</span></span> <span data-ttu-id="b8f9e-114">Azure İşlevler, bulutta yönetilen sunucusuz bir ortamda küçük kod parçalarını ölçekte çalıştırmanın kolay bir yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-114">Azure Functions provides an easy way to run small pieces of code at scale on a managed serverless environment in the cloud.</span></span> <span data-ttu-id="b8f9e-115">Bu örneğin kodu GitHub'daki [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction) deposunda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-115">The code for this sample can be found on the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction) repository on GitHub.</span></span>

## <a name="create-azure-functions-project"></a><span data-ttu-id="b8f9e-116">Azure İşlevleri projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="b8f9e-116">Create Azure Functions project</span></span>

1. <span data-ttu-id="b8f9e-117">Visual Studio 2017'yi açın.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-117">Open Visual Studio 2017.</span></span> <span data-ttu-id="b8f9e-118">Menü çubuğundan**Yeni** > **Proje** **Dosyası'nı** > seçin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-118">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="b8f9e-119">Yeni **Proje** iletişim kutusunda, **Bulut** düğümü tarafından izlenen **Visual C#** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-119">In the **New Project** dialog, select the **Visual C#** node followed by the **Cloud** node.</span></span> <span data-ttu-id="b8f9e-120">Ardından **Azure İşlevleri** proje şablonuna katılın.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-120">Then select the **Azure Functions** project template.</span></span> <span data-ttu-id="b8f9e-121">**Ad** metin kutusuna "SentimentAnalysisFunctionsApp" yazın ve **ardından Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-121">In the **Name** text box, type "SentimentAnalysisFunctionsApp" and then select the **OK** button.</span></span>
1. <span data-ttu-id="b8f9e-122">Yeni **Proje** iletişim kutusunda, proje seçeneklerinin üzerindeki açılır dosyayı açın ve **Azure İşlevleri v2 (.NET Core)** seçeneğini seçin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-122">In the **New Project** dialog, open the dropdown above the project options and select **Azure Functions v2 (.NET Core)**.</span></span> <span data-ttu-id="b8f9e-123">Ardından, **Http tetikleyici** projesini seçin ve ardından **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-123">Then, select the **Http trigger** project and then select the **OK** button.</span></span>
1. <span data-ttu-id="b8f9e-124">Modelinizi kaydetmek için projenizde *MLModels* adlı bir dizin oluşturun:</span><span class="sxs-lookup"><span data-stu-id="b8f9e-124">Create a directory named *MLModels* in your project to save your model:</span></span>

    <span data-ttu-id="b8f9e-125">**Çözüm Gezgini'nde,** projenize sağ tıklayın ve**Yeni Klasör** **Ekle'yi** > seçin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-125">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="b8f9e-126">"MLModels" yazın ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-126">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="b8f9e-127">Microsoft.ML **NuGet Paketi** sürüm **1.3.1**yükleyin:</span><span class="sxs-lookup"><span data-stu-id="b8f9e-127">Install the **Microsoft.ML NuGet Package** version **1.3.1**:</span></span>

    <span data-ttu-id="b8f9e-128">Çözüm Gezgini'nde projenize sağ tıklayın ve **NuGet Paketlerini Yönet'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-128">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="b8f9e-129">Paket kaynağı olarak "nuget.org" seçeneğini belirleyin, Gözat sekmesini seçin, **Microsoft.ML**arayın, listedeki paketi seçin ve **Yükle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-129">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="b8f9e-130">**Değişiklikler Önizleme** iletişim kutusundaki **Tamam** düğmesini seçin ve listelenen paketlerin lisans koşullarını kabul ederseniz Lisans Kabul iletişim kutusundaki **Kabul** **Et** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-130">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="b8f9e-131">**Microsoft.Azure.Functions.Extensions NuGet Paketini Yükleyin:**</span><span class="sxs-lookup"><span data-stu-id="b8f9e-131">Install the **Microsoft.Azure.Functions.Extensions NuGet Package**:</span></span>

    <span data-ttu-id="b8f9e-132">Çözüm Gezgini'nde projenize sağ tıklayın ve **NuGet Paketlerini Yönet'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-132">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="b8f9e-133">Paket kaynağı olarak "nuget.org"yi seçin, Gözat sekmesini seçin, **Microsoft.Azure.Functions.Extensions'ı**arayın, listedeki paketi seçin ve **Yükle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-133">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Azure.Functions.Extensions**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="b8f9e-134">**Değişiklikler Önizleme** iletişim kutusundaki **Tamam** düğmesini seçin ve listelenen paketlerin lisans koşullarını kabul ederseniz Lisans Kabul iletişim kutusundaki **Kabul** **Et** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-134">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="b8f9e-135">Microsoft.Extensions.ML **NuGet Paketi** sürümünü **0.15.1 yükleyin:**</span><span class="sxs-lookup"><span data-stu-id="b8f9e-135">Install the **Microsoft.Extensions.ML NuGet Package** version **0.15.1**:</span></span>

    <span data-ttu-id="b8f9e-136">Çözüm Gezgini'nde projenize sağ tıklayın ve **NuGet Paketlerini Yönet'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-136">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="b8f9e-137">Paket kaynağı olarak "nuget.org" seçeneğini belirleyin, Gözat sekmesini seçin, **Microsoft.Extensions.ML**arayın, listedeki paketi seçin ve **Yükle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-137">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="b8f9e-138">**Değişiklikler Önizleme** iletişim kutusundaki **Tamam** düğmesini seçin ve listelenen paketlerin lisans koşullarını kabul ederseniz Lisans Kabul iletişim kutusundaki **Kabul** **Et** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-138">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="b8f9e-139">**Microsoft.NET.Sdk.Functions NuGet Paketi** sürümünü **1.0.31**yükleyin:</span><span class="sxs-lookup"><span data-stu-id="b8f9e-139">Install the **Microsoft.NET.Sdk.Functions NuGet Package** version **1.0.31**:</span></span>

    <span data-ttu-id="b8f9e-140">Çözüm Gezgini'nde projenize sağ tıklayın ve **NuGet Paketlerini Yönet'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-140">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="b8f9e-141">Paket kaynağı olarak "nuget.org"yi seçin, Yüklü sekmesini seçin, **Microsoft.NET.Sdk.Functions'i**arayın, listedeki paketi seçin, Sürüm açılır listesinden **1.0.31'i** seçin ve **Güncelleştir** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-141">Choose "nuget.org" as the Package source, select the Installed tab, search for **Microsoft.NET.Sdk.Functions**, select that package in the list, select **1.0.31** from the Version dropdown, and select the **Update** button.</span></span> <span data-ttu-id="b8f9e-142">**Değişiklikler Önizleme** iletişim kutusundaki **Tamam** düğmesini seçin ve listelenen paketlerin lisans koşullarını kabul ederseniz Lisans Kabul iletişim kutusundaki **Kabul** **Et** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-142">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="add-pre-trained-model-to-project"></a><span data-ttu-id="b8f9e-143">Projeye önceden eğitilmiş modeli ekleme</span><span class="sxs-lookup"><span data-stu-id="b8f9e-143">Add pre-trained model to project</span></span>

1. <span data-ttu-id="b8f9e-144">Önceden oluşturulmuş modelinizi *MLModels* klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-144">Copy your pre-built model to the *MLModels* folder.</span></span>
1. <span data-ttu-id="b8f9e-145">Çözüm Gezgini'nde, önceden oluşturulmuş model dosyanıza sağ tıklayın ve **Özellikler'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-145">In Solution Explorer, right-click your pre-built model file and select **Properties**.</span></span> <span data-ttu-id="b8f9e-146">**Gelişmiş**altında, **daha yeniyse**Kopyala'dan **Çıktı Dizini'ne Kopya** değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-146">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

## <a name="create-azure-function-to-analyze-sentiment"></a><span data-ttu-id="b8f9e-147">Duyarlılığı analiz etmek için Azure İşlevi oluşturma</span><span class="sxs-lookup"><span data-stu-id="b8f9e-147">Create Azure Function to analyze sentiment</span></span>

<span data-ttu-id="b8f9e-148">Duyguları tahmin etmek için bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-148">Create a class to predict sentiment.</span></span> <span data-ttu-id="b8f9e-149">Projenize yeni bir sınıf ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b8f9e-149">Add a new class to your project:</span></span>

1. <span data-ttu-id="b8f9e-150">**Çözüm Gezgini'nde,** projeyi sağ tıklatın ve ardından**Yeni Öğe** **Ekle'yi** > seçin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-150">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="b8f9e-151">Yeni **Öğe Ekle** iletişim kutusunda **Azure İşlev'i** seçin ve **Ad** alanını *AnalyzeSentiment.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-151">In the **Add New Item** dialog box, select **Azure Function** and change the **Name** field to *AnalyzeSentiment.cs*.</span></span> <span data-ttu-id="b8f9e-152">Ardından **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-152">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="b8f9e-153">Yeni **Azure İşlevi** iletişim kutusunda **Http Tetikle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-153">In the **New Azure Function** dialog box, select **Http Trigger**.</span></span> <span data-ttu-id="b8f9e-154">Ardından **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-154">Then, select the **OK** button.</span></span>

    <span data-ttu-id="b8f9e-155">*AnalyzeSentiment.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-155">The *AnalyzeSentiment.cs* file opens in the code editor.</span></span> <span data-ttu-id="b8f9e-156">AnalyzeSentiment.cs üstüne `using` aşağıdaki ifadeyi *AnalyzeSentiment.cs*ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b8f9e-156">Add the following `using` statement to the top of *AnalyzeSentiment.cs*:</span></span>

    [!code-csharp [AnalyzeUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L1-L11)]

    <span data-ttu-id="b8f9e-157">Varsayılan olarak, `AnalyzeSentiment` sınıf `static`.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-157">By default, the `AnalyzeSentiment` class is `static`.</span></span> <span data-ttu-id="b8f9e-158">Anahtar kelimeyi `static` sınıf tanımından kaldırdıktan emin olun.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-158">Make sure to remove the `static` keyword from the class definition.</span></span>

    ```csharp
    public class AnalyzeSentiment
    {

    }
    ```

## <a name="create-data-models"></a><span data-ttu-id="b8f9e-159">Veri modelleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="b8f9e-159">Create data models</span></span>

<span data-ttu-id="b8f9e-160">Giriş verileriniz ve öngörüleriniz için bazı sınıflar oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-160">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="b8f9e-161">Projenize yeni bir sınıf ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b8f9e-161">Add a new class to your project:</span></span>

1. <span data-ttu-id="b8f9e-162">Veri modellerinizi kaydetmek için projenizde *Veri Modelleri* adlı bir dizin oluşturun: Çözüm Gezgini'nde, projenize sağ tıklayın ve Yeni Klasör **> ekle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-162">Create a directory named *DataModels* in your project to save your data models: In Solution Explorer, right-click on your project and select **Add > New Folder**.</span></span> <span data-ttu-id="b8f9e-163">"Veri Modelleri" yazın ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-163">Type "DataModels" and hit Enter.</span></span>
2. <span data-ttu-id="b8f9e-164">Çözüm Gezgini'nde, *DataModels* dizinini sağ tıklatın ve ardından **Yeni Öğe > ekle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-164">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
3. <span data-ttu-id="b8f9e-165">Yeni **Öğe Ekle** iletişim kutusunda **Sınıf'ı** seçin ve **Ad** alanını *SentimentData.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-165">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="b8f9e-166">Ardından **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-166">Then, select the **Add** button.</span></span>

    <span data-ttu-id="b8f9e-167">*SentimentData.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-167">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="b8f9e-168">*SentimentData.cs*üst kısmında aşağıdaki ifadesini kullanarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b8f9e-168">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp [SentimentDataUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L1)]

    <span data-ttu-id="b8f9e-169">Varolan sınıf tanımını kaldırın ve *SentimentData.cs* dosyasına aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b8f9e-169">Remove the existing class definition and add the following code to the *SentimentData.cs* file:</span></span>

    [!code-csharp [SentimentData](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L5-L13)]

4. <span data-ttu-id="b8f9e-170">Çözüm Gezgini'nde, *DataModels* dizinini sağ tıklatın ve ardından **Yeni Öğe > ekle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-170">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="b8f9e-171">Yeni **Öğe Ekle** iletişim kutusunda **Sınıf'ı** seçin ve **Ad** alanını *SentimentPrediction.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-171">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="b8f9e-172">Ardından **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-172">Then, select the **Add** button.</span></span> <span data-ttu-id="b8f9e-173">kod düzenleyicisinde *SentimentPrediction.cs* dosyası açılır.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-173">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="b8f9e-174">*SentimentPrediction.cs*üstüne aşağıdaki ifadesini kullanarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b8f9e-174">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    [!code-csharp [SentimentPredictionUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L1)]

    <span data-ttu-id="b8f9e-175">Varolan sınıf tanımını kaldırın ve *SentimentPrediction.cs* dosyasına aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b8f9e-175">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

    [!code-csharp [SentimentPrediction](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L5-L14)]

    <span data-ttu-id="b8f9e-176">`SentimentPrediction`özellikteki özgün verilere ve model tarafından oluşturulan çıktıya erişim sağlayan devralır. `SentimentData` `SentimentText`</span><span class="sxs-lookup"><span data-stu-id="b8f9e-176">`SentimentPrediction` inherits from `SentimentData` which provides access to the original data in the `SentimentText` property as well as the output generated by the model.</span></span>

## <a name="register-predictionenginepool-service"></a><span data-ttu-id="b8f9e-177">Kayıt TahminEnginePool hizmeti</span><span class="sxs-lookup"><span data-stu-id="b8f9e-177">Register PredictionEnginePool service</span></span>

<span data-ttu-id="b8f9e-178">Tek bir tahmin yapmak için, [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)bir .</span><span class="sxs-lookup"><span data-stu-id="b8f9e-178">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="b8f9e-179">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)iş parçacığı güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-179">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="b8f9e-180">Ayrıca, uygulamanız içinde gerekli olan her yerde bunun bir örneğini oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-180">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="b8f9e-181">Uygulamanız büyüdükçe, bu işlem yönetilemez hale gelebilir.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-181">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="b8f9e-182">Daha iyi performans ve iş parçacığı güvenliği için, `PredictionEnginePool` uygulamanız boyunca [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) kullanılmak [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) üzere bir nesne oluşturan bağımlılık enjeksiyonu ve hizmetin bir birleşimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-182">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

<span data-ttu-id="b8f9e-183">Bağımlılık [enjeksiyonu](https://en.wikipedia.org/wiki/Dependency_injection)hakkında daha fazla bilgi edinmek istiyorsanız aşağıdaki bağlantı daha fazla bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-183">The following link provides more information if you want to learn more about [dependency injection](https://en.wikipedia.org/wiki/Dependency_injection).</span></span>

1. <span data-ttu-id="b8f9e-184">**Çözüm Gezgini'nde,** projeyi sağ tıklatın ve ardından**Yeni Öğe** **Ekle'yi** > seçin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-184">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="b8f9e-185">Yeni **Öğe Ekle** iletişim kutusunda **Sınıf'ı** seçin ve **Ad** alanını *Startup.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-185">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *Startup.cs*.</span></span> <span data-ttu-id="b8f9e-186">Ardından **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-186">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="b8f9e-187">*Startup.cs*üst kısmında aşağıdaki ifadeleri kullanarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b8f9e-187">Add the following using statements to the top of *Startup.cs*:</span></span>

    [!code-csharp [StartupUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L1-L6)]

1. <span data-ttu-id="b8f9e-188">Aşağıdaki ifadeleri kullanarak ifadeleri altında varolan kodu kaldırın ve aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b8f9e-188">Remove the existing code below the using statements and add the following code:</span></span>

    ```csharp
    [assembly: FunctionsStartup(typeof(Startup))]
    namespace SentimentAnalysisFunctionsApp
    {
        public class Startup : FunctionsStartup
        {

        }
    }
    ```

1. <span data-ttu-id="b8f9e-189">Uygulamanın çalıştığı ortamı ve modelin sınıfın içinde bulunduğu dosya yolunu depolamak `Startup` için değişkenleri tanımlayın</span><span class="sxs-lookup"><span data-stu-id="b8f9e-189">Define variables to store the environment the app is running in and the file path where the model is located inside the `Startup` class</span></span>

    [!code-csharp [DefineStartupVars](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L13-L14)]

1. <span data-ttu-id="b8f9e-190">Bunun altında, `_environment` ve `_modelPath` değişkenlerin değerlerini ayarlamak için bir oluşturucu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-190">Below that, create a constructor to set the values of the `_environment` and `_modelPath` variables.</span></span> <span data-ttu-id="b8f9e-191">Uygulama yerel olarak çalışırken, varsayılan ortam *Development*Geliştirme'dir.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-191">When the application is running locally, the default environment is *Development*.</span></span>

    [!code-csharp [StartupCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L16-L29)]

1. <span data-ttu-id="b8f9e-192">Ardından, hizmeti oluşturucunun `Configure` `PredictionEnginePool` altına kaydetmek için çağrılan yeni bir yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-192">Then, add a new method called `Configure` to register the `PredictionEnginePool` service below the constructor.</span></span>

    [!code-csharp [ConfigureServices](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L31-L35)]

<span data-ttu-id="b8f9e-193">Yüksek düzeyde, bu kod, uygulama tarafından el ile yapmak zorunda kalmak yerine daha sonra kullanılmak üzere nesneleri ve hizmetleri otomatik olarak başlatir.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-193">At a high level, this code initializes the objects and services automatically for later use when requested by the application instead of having to manually do it.</span></span>

<span data-ttu-id="b8f9e-194">Makine öğrenimi modelleri statik değildir.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-194">Machine learning models are not static.</span></span> <span data-ttu-id="b8f9e-195">Yeni eğitim verileri kullanılabilir hale geldikçe, model yeniden eğitilir ve yeniden dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-195">As new training data becomes available, the model is retrained and redeployed.</span></span> <span data-ttu-id="b8f9e-196">Uygulamanıza modelin en son sürümünü almanın bir yolu, tüm uygulamayı yeniden dağıtmaktır.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-196">One way to get the latest version of the model into your application is to redeploy the entire application.</span></span> <span data-ttu-id="b8f9e-197">Ancak, bu uygulama kapalı kalma süresi tanır.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-197">However, this introduces application downtime.</span></span> <span data-ttu-id="b8f9e-198">Hizmet, `PredictionEnginePool` uygulamanızı kaldırmadan güncelleştirilmiş bir modeli yeniden yüklemek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-198">The `PredictionEnginePool` service provides a mechanism to reload an updated model without taking your application down.</span></span>

<span data-ttu-id="b8f9e-199">Parametreyi `watchForChanges` `true`ve dosya `PredictionEnginePool` sistemi [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) değişiklik bildirimlerini dinleyen ve dosyada bir değişiklik olduğunda olayları yükselten bir başlat' olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-199">Set the `watchForChanges` parameter to `true`, and the `PredictionEnginePool` starts a [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) that listens to the file system change notifications and raises events when there is a change to the file.</span></span> <span data-ttu-id="b8f9e-200">Bu, modeli `PredictionEnginePool` otomatik olarak yeniden yüklemesini ister.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-200">This prompts the `PredictionEnginePool` to automatically reload the model.</span></span>

<span data-ttu-id="b8f9e-201">`modelName` Model, uygulama başına birden fazla modelin değişiklik üzerine yeniden yüklenebilmeleri için parametre ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-201">The model is identified by the `modelName` parameter so that more than one model per application can be reloaded upon change.</span></span>

> [!TIP]
> <span data-ttu-id="b8f9e-202">Alternatif olarak, uzaktan `FromUri` depolanan modeller ile çalışırken yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-202">Alternatively, you can use the `FromUri` method when working with models stored remotely.</span></span> <span data-ttu-id="b8f9e-203">Dosya değiştirilen olayları izlemek `FromUri` yerine, değişiklikler için uzak konumu yoklar.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-203">Rather than watching for file changed events, `FromUri` polls the remote location for changes.</span></span> <span data-ttu-id="b8f9e-204">Yoklama aralığı varsayılan olarak 5 dakikadır.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-204">The polling interval defaults to 5 minutes.</span></span> <span data-ttu-id="b8f9e-205">Uygulamanızın gereksinimlerine bağlı olarak yoklama aralığını artırabilir veya azaltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-205">You can increase or decrease the polling interval based on your application's requirements.</span></span> <span data-ttu-id="b8f9e-206">Aşağıdaki kod örneğinde, `PredictionEnginePool` model her dakika belirtilen URI'de depolanır.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-206">In the code sample below, the `PredictionEnginePool` polls the model stored at the specified URI every minute.</span></span>
>
>```csharp
>builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="load-the-model-into-the-function"></a><span data-ttu-id="b8f9e-207">Modeli işleve yükleyin</span><span class="sxs-lookup"><span data-stu-id="b8f9e-207">Load the model into the function</span></span>

<span data-ttu-id="b8f9e-208">*AnalyzeSentiment* sınıfına aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b8f9e-208">Insert the following code inside the *AnalyzeSentiment* class:</span></span>

[!code-csharp [AnalyzeCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L18-L24)]

<span data-ttu-id="b8f9e-209">Bu kod, `PredictionEnginePool` bağımlılık enjeksiyonu yoluyla elde ettiğiniz işlevin oluşturucuya geçirerek atar.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-209">This code assigns the `PredictionEnginePool` by passing it to the function's constructor which you get via dependency injection.</span></span>

## <a name="use-the-model-to-make-predictions"></a><span data-ttu-id="b8f9e-210">Öngörülerde bulunmak için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="b8f9e-210">Use the model to make predictions</span></span>

<span data-ttu-id="b8f9e-211">*AnalyzeSentiment* sınıfında *Run* yönteminin varolan uygulamasını aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="b8f9e-211">Replace the existing implementation of *Run* method in *AnalyzeSentiment* class with the following code:</span></span>

[!code-csharp [AnalyzeRunMethod](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L26-L45)]

<span data-ttu-id="b8f9e-212">`Run` Yöntem yürütüldüğünde, HTTP isteğinden gelen veriler deserialized ve giriş olarak `PredictionEnginePool`kullanılır .</span><span class="sxs-lookup"><span data-stu-id="b8f9e-212">When the `Run` method executes, the incoming data from the HTTP request is deserialized and used as input for the `PredictionEnginePool`.</span></span> <span data-ttu-id="b8f9e-213">Yöntem `Predict` daha sonra `SentimentAnalysisModel` `Startup` sınıfta kayıtlı kullanarak öngörüler yapmak için çağrılır ve başarılı olursa sonuçları kullanıcıya geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-213">The `Predict` method is then called to make predictions using the `SentimentAnalysisModel` registered in the `Startup` class and returns the results back to the user if successful.</span></span>

## <a name="test-locally"></a><span data-ttu-id="b8f9e-214">Yerel olarak test edin</span><span class="sxs-lookup"><span data-stu-id="b8f9e-214">Test locally</span></span>

<span data-ttu-id="b8f9e-215">Artık her şey ayarlandı, uygulamayı test etme zamanı geldi:</span><span class="sxs-lookup"><span data-stu-id="b8f9e-215">Now that everything is set up, it's time to test the application:</span></span>

1. <span data-ttu-id="b8f9e-216">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="b8f9e-216">Run the application</span></span>
1. <span data-ttu-id="b8f9e-217">PowerShell'i açın ve kodu uygulamanızın çalıştığı port PORT PORT'un bulunduğu komut istemine girin.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-217">Open PowerShell and enter the code into the prompt where PORT is the port your application is running on.</span></span> <span data-ttu-id="b8f9e-218">Genellikle bağlantı noktası 7071'dir.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-218">Typically the port is 7071.</span></span>

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="b8f9e-219">Başarılı olursa, çıktı aşağıdaki metne benzer olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="b8f9e-219">If successful, the output should look similar to the text below:</span></span>

    ```powershell
    Negative
    ```

<span data-ttu-id="b8f9e-220">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="b8f9e-220">Congratulations!</span></span> <span data-ttu-id="b8f9e-221">Azure İşlevi kullanarak internet üzerinden öngörülerde bulunmak için modelinizi başarıyla kullandınız.</span><span class="sxs-lookup"><span data-stu-id="b8f9e-221">You have successfully served your model to make predictions over the internet using an Azure Function.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b8f9e-222">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="b8f9e-222">Next Steps</span></span>

- [<span data-ttu-id="b8f9e-223">Azure'a Dağıt</span><span class="sxs-lookup"><span data-stu-id="b8f9e-223">Deploy to Azure</span></span>](/azure/azure-functions/functions-develop-vs#publish-to-azure)
