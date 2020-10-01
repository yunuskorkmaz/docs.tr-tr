---
title: Modeli Azure İşlevleri’ne dağıtma
description: Azure Işlevleri 'ni kullanarak Internet üzerinden tahmin için ML.NET yaklaşım analizi makine öğrenimi modelini sunar
ms.date: 02/21/2020
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 74a7a5b941596ba9fffc62ef87a01763937d88c0
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608783"
---
# <a name="deploy-a-model-to-azure-functions"></a><span data-ttu-id="871d2-103">Modeli Azure İşlevleri’ne dağıtma</span><span class="sxs-lookup"><span data-stu-id="871d2-103">Deploy a model to Azure Functions</span></span>

<span data-ttu-id="871d2-104">Azure Işlevleri sunucusuz bir ortam aracılığıyla HTTP üzerinden tahmin için önceden eğitilen ML.NET makine öğrenimi modelini dağıtmayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="871d2-104">Learn how to deploy a pre-trained ML.NET machine learning model for predictions over HTTP through an Azure Functions serverless environment.</span></span>

> [!NOTE]
> <span data-ttu-id="871d2-105">Bu örnek, hizmetin bir önizleme sürümünü çalıştırır `PredictionEnginePool` .</span><span class="sxs-lookup"><span data-stu-id="871d2-105">This sample runs a preview version of the `PredictionEnginePool` service.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="871d2-106">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="871d2-106">Prerequisites</span></span>

- <span data-ttu-id="871d2-107">".NET Core platformlar arası geliştirme" ve "Azure geliştirme" iş yükleri yüklü olan [Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya üzeri ya da visual Studio 2017 sürüm 15,6 veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="871d2-107">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" and "Azure development" workloads installed.</span></span>
- [<span data-ttu-id="871d2-108">Azure Işlevleri araçları</span><span class="sxs-lookup"><span data-stu-id="871d2-108">Azure Functions Tools</span></span>](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- <span data-ttu-id="871d2-109">PowerShell</span><span class="sxs-lookup"><span data-stu-id="871d2-109">PowerShell</span></span>
- <span data-ttu-id="871d2-110">Önceden eğitilen model.</span><span class="sxs-lookup"><span data-stu-id="871d2-110">Pre-trained model.</span></span> <span data-ttu-id="871d2-111">Kendi modelinizi derlemek için [ML.NET yaklaşım Analizi öğreticisini](../tutorials/sentiment-analysis.md) kullanın veya bu [önceden eğitilen yaklaşım Analizi Machine Learning modelini](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip) indirin</span><span class="sxs-lookup"><span data-stu-id="871d2-111">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="azure-functions-sample-overview"></a><span data-ttu-id="871d2-112">Azure Işlevleri örneğine genel bakış</span><span class="sxs-lookup"><span data-stu-id="871d2-112">Azure Functions sample overview</span></span>

<span data-ttu-id="871d2-113">Bu örnek, metnin yaklaşımını pozitif veya negatif olarak kategorilere ayırmak için önceden eğitilen bir ikili sınıflandırma modeli kullanan bir **C# http tetikleyici Azure işlevleri uygulamasıdır** .</span><span class="sxs-lookup"><span data-stu-id="871d2-113">This sample is a **C# HTTP Trigger Azure Functions application** that uses a pretrained binary classification model to categorize the sentiment of text as positive or negative.</span></span> <span data-ttu-id="871d2-114">Azure Işlevleri, bulutta yönetilen sunucusuz bir ortamda küçük kod parçalarını daha kolay bir şekilde çalıştırmanın kolay bir yolunu sunar.</span><span class="sxs-lookup"><span data-stu-id="871d2-114">Azure Functions provides an easy way to run small pieces of code at scale on a managed serverless environment in the cloud.</span></span> <span data-ttu-id="871d2-115">Bu örneğin kodu, GitHub 'daki [DotNet/machinöğrenim-örnekleri](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction) deposunda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="871d2-115">The code for this sample can be found on the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction) repository on GitHub.</span></span>

## <a name="create-azure-functions-project"></a><span data-ttu-id="871d2-116">Azure Işlevleri projesi oluştur</span><span class="sxs-lookup"><span data-stu-id="871d2-116">Create Azure Functions project</span></span>

1. <span data-ttu-id="871d2-117">Visual Studio 2017'yi açın.</span><span class="sxs-lookup"><span data-stu-id="871d2-117">Open Visual Studio 2017.</span></span> <span data-ttu-id="871d2-118">Menü çubuğundan **Dosya**  >  **Yeni**  >  **Proje** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="871d2-118">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="871d2-119">**Yeni proje** iletişim kutusunda, **Visual C#** düğümünü ve ardından **bulut** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="871d2-119">In the **New Project** dialog, select the **Visual C#** node followed by the **Cloud** node.</span></span> <span data-ttu-id="871d2-120">Ardından **Azure işlevleri** proje şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="871d2-120">Then select the **Azure Functions** project template.</span></span> <span data-ttu-id="871d2-121">**Ad** metin kutusuna "SentimentAnalysisFunctionsApp" yazın ve **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="871d2-121">In the **Name** text box, type "SentimentAnalysisFunctionsApp" and then select the **OK** button.</span></span>
1. <span data-ttu-id="871d2-122">**Yeni proje** iletişim kutusunda, proje seçeneklerinin üzerindeki açılan menüyü açın ve **Azure işlevleri v2 (.NET Core)** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="871d2-122">In the **New Project** dialog, open the dropdown above the project options and select **Azure Functions v2 (.NET Core)**.</span></span> <span data-ttu-id="871d2-123">Ardından, **http tetikleyicisi** projesini seçin ve **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="871d2-123">Then, select the **Http trigger** project and then select the **OK** button.</span></span>
1. <span data-ttu-id="871d2-124">Modelinize kaydetmek için projenizde *Mlmodeller* adlı bir dizin oluşturun:</span><span class="sxs-lookup"><span data-stu-id="871d2-124">Create a directory named *MLModels* in your project to save your model:</span></span>

    <span data-ttu-id="871d2-125">**Çözüm Gezgini**, projenize sağ tıklayın ve **Add**  >  **Yeni klasör**Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="871d2-125">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="871d2-126">"Mlmodeller" yazın ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="871d2-126">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="871d2-127">**Microsoft.ml NuGet paketi** sürüm **1.3.1**'nı yükler:</span><span class="sxs-lookup"><span data-stu-id="871d2-127">Install the **Microsoft.ML NuGet Package** version **1.3.1**:</span></span>

    <span data-ttu-id="871d2-128">Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="871d2-128">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="871d2-129">Paket kaynağı olarak "nuget.org" öğesini seçin, araştır sekmesini seçin, **Microsoft.ml**için arama yapın, listeden bu paketi seçin ve sonra da **Install** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="871d2-129">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="871d2-130">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="871d2-130">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="871d2-131">**Microsoft. Azure. Functions. Extensions NuGet paketini**yükler:</span><span class="sxs-lookup"><span data-stu-id="871d2-131">Install the **Microsoft.Azure.Functions.Extensions NuGet Package**:</span></span>

    <span data-ttu-id="871d2-132">Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="871d2-132">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="871d2-133">Paket kaynağı olarak "nuget.org" öğesini seçin, gözden geçirme sekmesini seçin, **Microsoft. Azure. Functions. Extensions**araması yapın, listeden bu paketi seçin ve sonra da **Install** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="871d2-133">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Azure.Functions.Extensions**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="871d2-134">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="871d2-134">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="871d2-135">**Microsoft.Extensions.ml NuGet paketi** sürüm **0.15.1**'nı yükler:</span><span class="sxs-lookup"><span data-stu-id="871d2-135">Install the **Microsoft.Extensions.ML NuGet Package** version **0.15.1**:</span></span>

    <span data-ttu-id="871d2-136">Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="871d2-136">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="871d2-137">Paket kaynağı olarak "nuget.org" öğesini seçin, araştır sekmesini seçin, **Microsoft.Extensions.ml**için arama yapın, listeden bu paketi seçin ve sonra da **Install** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="871d2-137">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="871d2-138">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="871d2-138">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="871d2-139">**Microsoft. net. SDK. Functions NuGet paketi** sürüm **1.0.31**'yi yükler:</span><span class="sxs-lookup"><span data-stu-id="871d2-139">Install the **Microsoft.NET.Sdk.Functions NuGet Package** version **1.0.31**:</span></span>

    <span data-ttu-id="871d2-140">Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="871d2-140">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="871d2-141">Paket kaynağı olarak "nuget.org" öğesini seçin, yüklü sekmesini seçin, **Microsoft. net. SDK. Functions**araması yapın, listeden bu paketi seçin, sürüm açılan menüsünden **1.0.31** ' yi seçin ve **Güncelleştir** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="871d2-141">Choose "nuget.org" as the Package source, select the Installed tab, search for **Microsoft.NET.Sdk.Functions**, select that package in the list, select **1.0.31** from the Version dropdown, and select the **Update** button.</span></span> <span data-ttu-id="871d2-142">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="871d2-142">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="add-pre-trained-model-to-project"></a><span data-ttu-id="871d2-143">Projeye önceden eğitilen Model Ekle</span><span class="sxs-lookup"><span data-stu-id="871d2-143">Add pre-trained model to project</span></span>

1. <span data-ttu-id="871d2-144">Önceden oluşturulmuş modelinizi *Mlmodeller* klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="871d2-144">Copy your pre-built model to the *MLModels* folder.</span></span>
1. <span data-ttu-id="871d2-145">Çözüm Gezgini, önceden oluşturulmuş model dosyanıza sağ tıklayıp **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="871d2-145">In Solution Explorer, right-click your pre-built model file and select **Properties**.</span></span> <span data-ttu-id="871d2-146">**Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="871d2-146">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

## <a name="create-azure-function-to-analyze-sentiment"></a><span data-ttu-id="871d2-147">Yaklaşımı çözümlemek için Azure Işlevi oluşturma</span><span class="sxs-lookup"><span data-stu-id="871d2-147">Create Azure Function to analyze sentiment</span></span>

<span data-ttu-id="871d2-148">Yaklaşımı tahmin etmek için bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="871d2-148">Create a class to predict sentiment.</span></span> <span data-ttu-id="871d2-149">Projenize yeni bir sınıf ekleyin:</span><span class="sxs-lookup"><span data-stu-id="871d2-149">Add a new class to your project:</span></span>

1. <span data-ttu-id="871d2-150">**Çözüm Gezgini**, projeye sağ tıklayın ve ardından **Add**  >  **Yeni öğe**Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="871d2-150">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="871d2-151">**Yeni öğe Ekle** Iletişim kutusunda **Azure işlevi** ' ni seçin ve **ad** alanını *AnalyzeSentiment.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="871d2-151">In the **Add New Item** dialog box, select **Azure Function** and change the **Name** field to *AnalyzeSentiment.cs*.</span></span> <span data-ttu-id="871d2-152">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="871d2-152">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="871d2-153">**Yeni Azure işlevi** Iletişim kutusunda **http tetikleyicisi**' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="871d2-153">In the **New Azure Function** dialog box, select **Http Trigger**.</span></span> <span data-ttu-id="871d2-154">Ardından **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="871d2-154">Then, select the **OK** button.</span></span>

    <span data-ttu-id="871d2-155">*AnalyzeSentiment.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="871d2-155">The *AnalyzeSentiment.cs* file opens in the code editor.</span></span> <span data-ttu-id="871d2-156">Aşağıdaki `using` ifadeyi *AnalyzeSentiment.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="871d2-156">Add the following `using` statement to the top of *AnalyzeSentiment.cs*:</span></span>

    [!code-csharp [AnalyzeUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L1-L11)]

    <span data-ttu-id="871d2-157">Varsayılan olarak, `AnalyzeSentiment` sınıfı `static` .</span><span class="sxs-lookup"><span data-stu-id="871d2-157">By default, the `AnalyzeSentiment` class is `static`.</span></span> <span data-ttu-id="871d2-158">`static`Anahtar sözcüğünü sınıf tanımından kaldırdığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="871d2-158">Make sure to remove the `static` keyword from the class definition.</span></span>

    ```csharp
    public class AnalyzeSentiment
    {

    }
    ```

## <a name="create-data-models"></a><span data-ttu-id="871d2-159">Veri modelleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="871d2-159">Create data models</span></span>

<span data-ttu-id="871d2-160">Giriş verileriniz ve tahminlerinizi için bazı sınıflar oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="871d2-160">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="871d2-161">Projenize yeni bir sınıf ekleyin:</span><span class="sxs-lookup"><span data-stu-id="871d2-161">Add a new class to your project:</span></span>

1. <span data-ttu-id="871d2-162">Projenizde veri modellerinizi kaydetmek için *datamodeller* adlı bir dizin oluşturun: Çözüm Gezgini, projenize sağ tıklayın ve **> yeni klasör ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="871d2-162">Create a directory named *DataModels* in your project to save your data models: In Solution Explorer, right-click on your project and select **Add > New Folder**.</span></span> <span data-ttu-id="871d2-163">"Datamodeller" yazın ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="871d2-163">Type "DataModels" and hit Enter.</span></span>
2. <span data-ttu-id="871d2-164">Çözüm Gezgini, *veri modelleri* dizinine sağ tıklayın ve sonra **> yeni öğe Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="871d2-164">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
3. <span data-ttu-id="871d2-165">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *SentimentData.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="871d2-165">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="871d2-166">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="871d2-166">Then, select the **Add** button.</span></span>

    <span data-ttu-id="871d2-167">*SentimentData.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="871d2-167">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="871d2-168">Aşağıdaki using ifadesini *SentimentData.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="871d2-168">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp [SentimentDataUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L1)]

    <span data-ttu-id="871d2-169">Mevcut sınıf tanımını kaldırın ve aşağıdaki kodu *SentimentData.cs* dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="871d2-169">Remove the existing class definition and add the following code to the *SentimentData.cs* file:</span></span>

    [!code-csharp [SentimentData](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L5-L13)]

4. <span data-ttu-id="871d2-170">Çözüm Gezgini, *veri modelleri* dizinine sağ tıklayın ve sonra **> yeni öğe Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="871d2-170">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="871d2-171">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *SentimentPrediction.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="871d2-171">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="871d2-172">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="871d2-172">Then, select the **Add** button.</span></span> <span data-ttu-id="871d2-173">*SentimentPrediction.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="871d2-173">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="871d2-174">Aşağıdaki using ifadesini *SentimentPrediction.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="871d2-174">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    [!code-csharp [SentimentPredictionUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L1)]

    <span data-ttu-id="871d2-175">Mevcut sınıf tanımını kaldırın ve aşağıdaki kodu *SentimentPrediction.cs* dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="871d2-175">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

    [!code-csharp [SentimentPrediction](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L5-L14)]

    <span data-ttu-id="871d2-176">`SentimentPrediction``SentimentData`, özelliğindeki özgün verilere ve `SentimentText` model tarafından oluşturulan çıktıya erişim sağlayan öğesinden devralır.</span><span class="sxs-lookup"><span data-stu-id="871d2-176">`SentimentPrediction` inherits from `SentimentData` which provides access to the original data in the `SentimentText` property as well as the output generated by the model.</span></span>

## <a name="register-predictionenginepool-service"></a><span data-ttu-id="871d2-177">PredictionEnginePool hizmetini Kaydet</span><span class="sxs-lookup"><span data-stu-id="871d2-177">Register PredictionEnginePool service</span></span>

<span data-ttu-id="871d2-178">Tek bir tahmin yapmak için, oluşturmanız gerekir [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) .</span><span class="sxs-lookup"><span data-stu-id="871d2-178">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="871d2-179">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) , iş parçacığı açısından güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="871d2-179">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="871d2-180">Ayrıca, uygulamanızın içinde gerek duyduğu her yerde bir örneği oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="871d2-180">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="871d2-181">Uygulamanız büyüdükçe, bu işlem yönetilebilir hale gelebilir.</span><span class="sxs-lookup"><span data-stu-id="871d2-181">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="871d2-182">Daha iyi performans ve iş parçacığı güvenliği için, `PredictionEnginePool` [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) uygulamanız genelinde kullanılacak nesneleri oluşturan bağımlılık ekleme ve hizmetin bir birleşimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="871d2-182">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

<span data-ttu-id="871d2-183">Aşağıdaki bağlantı, [bağımlılık ekleme](https://en.wikipedia.org/wiki/Dependency_injection)hakkında daha fazla bilgi edinmek istiyorsanız daha fazla bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="871d2-183">The following link provides more information if you want to learn more about [dependency injection](https://en.wikipedia.org/wiki/Dependency_injection).</span></span>

1. <span data-ttu-id="871d2-184">**Çözüm Gezgini**, projeye sağ tıklayın ve ardından **Add**  >  **Yeni öğe**Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="871d2-184">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="871d2-185">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *Startup.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="871d2-185">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *Startup.cs*.</span></span> <span data-ttu-id="871d2-186">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="871d2-186">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="871d2-187">Aşağıdaki using deyimlerini *Startup.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="871d2-187">Add the following using statements to the top of *Startup.cs*:</span></span>

    [!code-csharp [StartupUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L1-L6)]

1. <span data-ttu-id="871d2-188">Using deyimlerinin altındaki mevcut kodu kaldırın ve aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="871d2-188">Remove the existing code below the using statements and add the following code:</span></span>

    ```csharp
    [assembly: FunctionsStartup(typeof(Startup))]
    namespace SentimentAnalysisFunctionsApp
    {
        public class Startup : FunctionsStartup
        {

        }
    }
    ```

1. <span data-ttu-id="871d2-189">Uygulamanın üzerinde çalıştığı ortamın depolanacağı değişkenleri ve modelin sınıfın içinde bulunduğu dosya yolunu tanımlayın `Startup`</span><span class="sxs-lookup"><span data-stu-id="871d2-189">Define variables to store the environment the app is running in and the file path where the model is located inside the `Startup` class</span></span>

    [!code-csharp [DefineStartupVars](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L13-L14)]

1. <span data-ttu-id="871d2-190">Bunun altında, ve değişkenlerinin değerlerini ayarlamak için bir Oluşturucu oluşturun `_environment` `_modelPath` .</span><span class="sxs-lookup"><span data-stu-id="871d2-190">Below that, create a constructor to set the values of the `_environment` and `_modelPath` variables.</span></span> <span data-ttu-id="871d2-191">Uygulama yerel olarak çalıştığında, varsayılan ortam *geliştirme aşamasındadır*.</span><span class="sxs-lookup"><span data-stu-id="871d2-191">When the application is running locally, the default environment is *Development*.</span></span>

    [!code-csharp [StartupCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L16-L29)]

1. <span data-ttu-id="871d2-192">Ardından, `Configure` hizmeti oluşturucunun altına kaydetmek için adlı yeni bir yöntem ekleyin `PredictionEnginePool` .</span><span class="sxs-lookup"><span data-stu-id="871d2-192">Then, add a new method called `Configure` to register the `PredictionEnginePool` service below the constructor.</span></span>

    [!code-csharp [ConfigureServices](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L31-L35)]

<span data-ttu-id="871d2-193">Yüksek düzeyde, bu kod, uygulama tarafından el ile yapmak yerine, daha sonra kullanmak üzere nesne ve hizmetleri otomatik olarak başlatır.</span><span class="sxs-lookup"><span data-stu-id="871d2-193">At a high level, this code initializes the objects and services automatically for later use when requested by the application instead of having to manually do it.</span></span>

<span data-ttu-id="871d2-194">Makine öğrenimi modelleri statik değildir.</span><span class="sxs-lookup"><span data-stu-id="871d2-194">Machine learning models are not static.</span></span> <span data-ttu-id="871d2-195">Yeni eğitim verileri kullanılabilir hale geldiğinde, model geri çekme ve yeniden dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="871d2-195">As new training data becomes available, the model is retrained and redeployed.</span></span> <span data-ttu-id="871d2-196">Bir modelin en son sürümünü uygulamanıza almanın bir yolu, uygulamanın tamamını yeniden dağıtmaktan biridir.</span><span class="sxs-lookup"><span data-stu-id="871d2-196">One way to get the latest version of the model into your application is to redeploy the entire application.</span></span> <span data-ttu-id="871d2-197">Ancak bu, uygulama kapalı kalma süresini tanıtır.</span><span class="sxs-lookup"><span data-stu-id="871d2-197">However, this introduces application downtime.</span></span> <span data-ttu-id="871d2-198">`PredictionEnginePool`Hizmet, uygulamanızı kapatmak zorunda kalmadan güncelleştirilmiş bir modeli yeniden yüklemek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="871d2-198">The `PredictionEnginePool` service provides a mechanism to reload an updated model without taking your application down.</span></span>

<span data-ttu-id="871d2-199">Parametresini olarak ayarlayın `watchForChanges` `true` ve dosya `PredictionEnginePool` [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) sistemi değişiklik bildirimlerini dinler ve dosyada değişiklik olduğunda olay başlatır.</span><span class="sxs-lookup"><span data-stu-id="871d2-199">Set the `watchForChanges` parameter to `true`, and the `PredictionEnginePool` starts a [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) that listens to the file system change notifications and raises events when there is a change to the file.</span></span> <span data-ttu-id="871d2-200">Bu, `PredictionEnginePool` modelini otomatik olarak yeniden yüklemek ister.</span><span class="sxs-lookup"><span data-stu-id="871d2-200">This prompts the `PredictionEnginePool` to automatically reload the model.</span></span>

<span data-ttu-id="871d2-201">Model parametresi tarafından tanımlanır, `modelName` böylece değişiklik yapıldığında uygulama başına birden fazla model yeniden yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="871d2-201">The model is identified by the `modelName` parameter so that more than one model per application can be reloaded upon change.</span></span>

> [!TIP]
> <span data-ttu-id="871d2-202">Alternatif olarak, `FromUri` Uzaktan depolanan modellerle çalışırken yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="871d2-202">Alternatively, you can use the `FromUri` method when working with models stored remotely.</span></span> <span data-ttu-id="871d2-203">Dosya değişmiş olayları izlemek yerine, `FromUri` uzak konumu değişiklikler için yoklar.</span><span class="sxs-lookup"><span data-stu-id="871d2-203">Rather than watching for file changed events, `FromUri` polls the remote location for changes.</span></span> <span data-ttu-id="871d2-204">Yoklama aralığı varsayılan olarak 5 dakikadır.</span><span class="sxs-lookup"><span data-stu-id="871d2-204">The polling interval defaults to 5 minutes.</span></span> <span data-ttu-id="871d2-205">Uygulama gereksinimlerine bağlı olarak yoklama aralığını artırabilir veya azaltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="871d2-205">You can increase or decrease the polling interval based on your application's requirements.</span></span> <span data-ttu-id="871d2-206">Aşağıdaki kod örneğinde, `PredictionEnginePool` her dakikada BELIRTILEN URI 'de depolanan modeli yoklar.</span><span class="sxs-lookup"><span data-stu-id="871d2-206">In the code sample below, the `PredictionEnginePool` polls the model stored at the specified URI every minute.</span></span>
>
>```csharp
>builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="load-the-model-into-the-function"></a><span data-ttu-id="871d2-207">Modeli işleve yükleme</span><span class="sxs-lookup"><span data-stu-id="871d2-207">Load the model into the function</span></span>

<span data-ttu-id="871d2-208">Aşağıdaki kodu, *çözümleyiciler* sınıfının içine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="871d2-208">Insert the following code inside the *AnalyzeSentiment* class:</span></span>

[!code-csharp [AnalyzeCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L18-L24)]

<span data-ttu-id="871d2-209">Bu kod, `PredictionEnginePool` bağımlılığı ekleme yoluyla aldığınız işlevin oluşturucusuna geçirerek öğesine atar.</span><span class="sxs-lookup"><span data-stu-id="871d2-209">This code assigns the `PredictionEnginePool` by passing it to the function's constructor which you get via dependency injection.</span></span>

## <a name="use-the-model-to-make-predictions"></a><span data-ttu-id="871d2-210">Tahminleri yapmak için modeli kullanın</span><span class="sxs-lookup"><span data-stu-id="871d2-210">Use the model to make predictions</span></span>

<span data-ttu-id="871d2-211">*Çözümleyiciler* sınıfında bulunan *Run* yönteminin mevcut uygulamasını aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="871d2-211">Replace the existing implementation of *Run* method in *AnalyzeSentiment* class with the following code:</span></span>

[!code-csharp [AnalyzeRunMethod](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L26-L45)]

<span data-ttu-id="871d2-212">`Run`Yöntem yürütüldüğünde, http isteğinden gelen veriler seri durumdan çıkarılmış olur ve için giriş olarak kullanılır `PredictionEnginePool` .</span><span class="sxs-lookup"><span data-stu-id="871d2-212">When the `Run` method executes, the incoming data from the HTTP request is deserialized and used as input for the `PredictionEnginePool`.</span></span> <span data-ttu-id="871d2-213">`Predict`Daha sonra yöntemi, sınıfında kayıtlı öğesini kullanarak tahmine dayalı hale getirmek için çağrılır `SentimentAnalysisModel` `Startup` ve başarılı olursa sonuçları kullanıcıya geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="871d2-213">The `Predict` method is then called to make predictions using the `SentimentAnalysisModel` registered in the `Startup` class and returns the results back to the user if successful.</span></span>

## <a name="test-locally"></a><span data-ttu-id="871d2-214">Yerel olarak test etme</span><span class="sxs-lookup"><span data-stu-id="871d2-214">Test locally</span></span>

<span data-ttu-id="871d2-215">Her şey ayarlandığına göre, uygulamayı test etmek zaman alabilir:</span><span class="sxs-lookup"><span data-stu-id="871d2-215">Now that everything is set up, it's time to test the application:</span></span>

1. <span data-ttu-id="871d2-216">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="871d2-216">Run the application</span></span>
1. <span data-ttu-id="871d2-217">PowerShell 'i açın ve kodu, uygulamanızın üzerinde çalıştığı bağlantı noktası olan bağlantı noktasının bulunduğu istemine girin.</span><span class="sxs-lookup"><span data-stu-id="871d2-217">Open PowerShell and enter the code into the prompt where PORT is the port your application is running on.</span></span> <span data-ttu-id="871d2-218">Genellikle bağlantı noktası 7071 ' dir.</span><span class="sxs-lookup"><span data-stu-id="871d2-218">Typically the port is 7071.</span></span>

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="871d2-219">Başarılı olursa, çıkış aşağıdaki metne benzer görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="871d2-219">If successful, the output should look similar to the text below:</span></span>

    ```powershell
    Negative
    ```

<span data-ttu-id="871d2-220">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="871d2-220">Congratulations!</span></span> <span data-ttu-id="871d2-221">Azure Işlevi kullanarak, internet üzerinden tahmine dayalı hale getirmek için modelinizi başarıyla sundu.</span><span class="sxs-lookup"><span data-stu-id="871d2-221">You have successfully served your model to make predictions over the internet using an Azure Function.</span></span>

## <a name="next-steps"></a><span data-ttu-id="871d2-222">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="871d2-222">Next Steps</span></span>

- [<span data-ttu-id="871d2-223">Azure’a dağıtın</span><span class="sxs-lookup"><span data-stu-id="871d2-223">Deploy to Azure</span></span>](/azure/azure-functions/functions-develop-vs#publish-to-azure)
