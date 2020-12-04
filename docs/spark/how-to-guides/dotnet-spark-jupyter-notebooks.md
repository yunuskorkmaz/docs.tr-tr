---
title: Jupyter Notebook'u kullanma
titleSuffix: .NET for Apache Spark
description: Jupyter Notebook, Jupyıter Laboratuvarı veya Visual Studio Code gibi etkileşimli ortamlarda Apache Spark için .NET kullanın (VS Code)
ms.author: luquinta
author: luisquintanilla
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc, how-to
ms.openlocfilehash: cf19b4e4b7a7b9033fb97b2b2736ab0383c11f93
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96598939"
---
# <a name="use-net-for-apache-spark-in-jupyter-notebooks"></a><span data-ttu-id="b3109-103">Jupyıter not defterlerinde Apache Spark için .NET kullanın</span><span class="sxs-lookup"><span data-stu-id="b3109-103">Use .NET for Apache Spark in Jupyter Notebooks</span></span>

<span data-ttu-id="b3109-104">Bu makalede, .net etkileşimli ile Jupyter Notebook ve Visual Studio Code (VS Code) Apache Spark işlerini etkileşimli olarak nasıl çalıştıracağınızı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="b3109-104">In this article, you learn how to run .NET for Apache Spark jobs interactively in Jupyter Notebook and Visual Studio Code (VS Code) with .NET Interactive.</span></span>

## <a name="about-jupyter"></a><span data-ttu-id="b3109-105">Jupyıter hakkında</span><span class="sxs-lookup"><span data-stu-id="b3109-105">About Jupyter</span></span>

<span data-ttu-id="b3109-106">[Jupyıter](https://jupyter.org/) , kullanıcıların uygulamaları etkileşimli olarak prototip ve geliştirmesini sağlayan bir yol sağlayan açık kaynaklı, platformlar arası bir bilgi işlem ortamıdır.</span><span class="sxs-lookup"><span data-stu-id="b3109-106">[Jupyter](https://jupyter.org/) is an open-source, cross-platform computing environment that provides a way for users to prototype and develop applications interactively.</span></span> <span data-ttu-id="b3109-107">Jupyter Notebook, Jupyıter Laboratuvarı ve VS Code gibi çok çeşitli arabirimler aracılığıyla Jupyıter ile etkileşim kurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3109-107">You can interact with Jupyter through a wide variety of interfaces such as Jupyter Notebook, Jupyter Lab, and VS Code.</span></span>

<span data-ttu-id="b3109-108">.NET Core küresel aracı olan .net, .net [etkileşimli](https://github.com/dotnet/interactive)bağlamında, Jupyter Notebook gibi etkileşimli bilgi işlem ortamlarında .NET kodu (C#/f #) yazmak için bir çekirdek sağlar.</span><span class="sxs-lookup"><span data-stu-id="b3109-108">In the context of .NET, [.NET Interactive](https://github.com/dotnet/interactive), a .NET Core global tool, provides a kernel for writing .NET code (C#/F#) in interactive computing environments such as Jupyter Notebook.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b3109-109">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="b3109-109">Prerequisites</span></span>

- [<span data-ttu-id="b3109-110">.NET Core 3,1 SDK</span><span class="sxs-lookup"><span data-stu-id="b3109-110">.NET Core 3.1 SDK</span></span>](../../core/install/index.yml)
- [<span data-ttu-id="b3109-111">Apache Spark</span><span class="sxs-lookup"><span data-stu-id="b3109-111">Apache Spark</span></span>](https://spark.apache.org/downloads.html)
- [<span data-ttu-id="b3109-112">Apache Spark .NET Worker</span><span class="sxs-lookup"><span data-stu-id="b3109-112">Apache Spark .NET Worker</span></span>](https://github.com/dotnet/spark/releases)

<span data-ttu-id="b3109-113">Apache Spark ortamınızı .NET için ayarlama hakkında daha fazla bilgi için bkz. Başlangıç [öğreticisi](../tutorials/get-started.md) .</span><span class="sxs-lookup"><span data-stu-id="b3109-113">See the [getting started tutorial](../tutorials/get-started.md) for more information on setting up your .NET for Apache Spark environment.</span></span>

## <a name="prepare-environment"></a><span data-ttu-id="b3109-114">Ortamı hazırlama</span><span class="sxs-lookup"><span data-stu-id="b3109-114">Prepare environment</span></span>

<span data-ttu-id="b3109-115">Jupi Not defterleri ile çalışmak için iki şey olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b3109-115">To work with Jupyter Notebooks, you'll need two things.</span></span>

1. <span data-ttu-id="b3109-116">[.Net etkileşimli küresel .NET aracını](https://github.com/dotnet/interactive/blob/main/docs/NotebooksLocalExperience.md) yükler</span><span class="sxs-lookup"><span data-stu-id="b3109-116">Install the [.NET Interactive global .NET tool](https://github.com/dotnet/interactive/blob/main/docs/NotebooksLocalExperience.md)</span></span>
1. <span data-ttu-id="b3109-117">`Microsoft.Spark`NuGet paketini indirin.</span><span class="sxs-lookup"><span data-stu-id="b3109-117">Download the `Microsoft.Spark` NuGet package.</span></span>
    1. <span data-ttu-id="b3109-118">[Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet paketi sayfasına gidin.</span><span class="sxs-lookup"><span data-stu-id="b3109-118">Navigate to the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet package page.</span></span>

        > [!IMPORTANT]
        > <span data-ttu-id="b3109-119">Varsayılan olarak, paketin en son sürümü indirilir.</span><span class="sxs-lookup"><span data-stu-id="b3109-119">By default, the latest version of the package is downloaded.</span></span> <span data-ttu-id="b3109-120">**İndirdiğinizden emin olun Apache Spark .NET çalışanınız ile aynı.**</span><span class="sxs-lookup"><span data-stu-id="b3109-120">**Make sure that the version you download is the same as your Apache Spark .NET Worker.**</span></span>

    1. <span data-ttu-id="b3109-121">**Bilgi** bölmesinde, paketin en son sürümünü indirmek Için **paketi indir** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="b3109-121">In the **Info** pane, select **Download package** to download the latest version of the package.</span></span> <span data-ttu-id="b3109-122">Paketin adı  *Microsoft. Spark ile benzerdir. [ Paket-sürümü]. nupkg*.</span><span class="sxs-lookup"><span data-stu-id="b3109-122">The name of the package is similar to  *microsoft.spark.[PACKAGE-VERSION].nupkg*.</span></span>
    1. <span data-ttu-id="b3109-123">İndirilen paketi sıkıştırmayı açın.</span><span class="sxs-lookup"><span data-stu-id="b3109-123">Unzip the downloaded package.</span></span> <span data-ttu-id="b3109-124">Sıkıştırılmış olmayan dizin, *jar dosyaları dışındaki* adlı bir alt dizin içermelidir.</span><span class="sxs-lookup"><span data-stu-id="b3109-124">The unzipped directory should contain a subdirectory called *jars*.</span></span> <span data-ttu-id="b3109-125">Daha sonraki bir zamanda kullanıldığından yola göz atın.</span><span class="sxs-lookup"><span data-stu-id="b3109-125">Take note of the path since it's used at a later time.</span></span>

## <a name="start-net-for-apache-spark"></a><span data-ttu-id="b3109-126">Apache Spark için .NET 'i başlatın</span><span class="sxs-lookup"><span data-stu-id="b3109-126">Start .NET for Apache Spark</span></span>

<span data-ttu-id="b3109-127">Hata ayıklama modunda Apache Spark için .NET 'i başlatmak üzere aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b3109-127">Run the following command to start .NET for Apache Spark in debug mode.</span></span> <span data-ttu-id="b3109-128">Bu `spark-submit` komut bir işlem başlatır ve bir [mini oturum](xref:Microsoft.Spark.Sql.SparkSession)bağlantısı bekler.</span><span class="sxs-lookup"><span data-stu-id="b3109-128">This `spark-submit` command starts a process and waits for connections from a [SparkSession](xref:Microsoft.Spark.Sql.SparkSession).</span></span> <span data-ttu-id="b3109-129">`microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar`Kullandığınız Apache Spark ilgili .NET sürümü için yolunu sağladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="b3109-129">Make sure to provide the path to the `microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar` for the respective version of .NET for Apache Spark you're using.</span></span>

<span data-ttu-id="b3109-130">**Ubuntu**</span><span class="sxs-lookup"><span data-stu-id="b3109-130">**Ubuntu**</span></span>

```bash
spark-submit \
    --class org.apache.spark.deploy.dotnet.DotnetRunner \
    --master local \
    <path-to-microsoft-spark-jar> \
    debug
```

<span data-ttu-id="b3109-131">**Windows**</span><span class="sxs-lookup"><span data-stu-id="b3109-131">**Windows**</span></span>

```cmd
spark-submit ^
    --class org.apache.spark.deploy.dotnet.DotnetRunner ^
    --master local ^
    <path-to-microsoft-spark-jar> ^
    debug
```

## <a name="create-a-notebook"></a><span data-ttu-id="b3109-132">Not defteri oluşturma</span><span class="sxs-lookup"><span data-stu-id="b3109-132">Create a notebook</span></span>

<span data-ttu-id="b3109-133">Jupyıter ile etkileşim kurmak için farklı arabirimler kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3109-133">You can use different interfaces to interact with Jupyter.</span></span> <span data-ttu-id="b3109-134">Tarayıcı tabanlı bir arabirim için Jupyıter not defterlerini veya Jupyıter Laboratuvarı kullanın.</span><span class="sxs-lookup"><span data-stu-id="b3109-134">For a browser-based interface, use Jupyter Notebooks or Jupyter Lab.</span></span> <span data-ttu-id="b3109-135">Yerel bir düzenleyici deneyimi için VS Code kullanın.</span><span class="sxs-lookup"><span data-stu-id="b3109-135">For a local editor experience, use VS Code.</span></span>

### <a name="jupyter-notebooks--jupyter-lab"></a><span data-ttu-id="b3109-136">Jupi Notebook & Jupyıter Laboratuvarı</span><span class="sxs-lookup"><span data-stu-id="b3109-136">Jupyter Notebooks & Jupyter Lab</span></span>

1. <span data-ttu-id="b3109-137">Başka bir komut isteminde, aşağıdaki komutlardan birini kullanarak Jupyter Notebook veya Jupyter Laboratuvarı başlatın:</span><span class="sxs-lookup"><span data-stu-id="b3109-137">In another command prompt, start Jupyter Notebook or Jupyter Lab using one of the commands below:</span></span>

    <span data-ttu-id="b3109-138">**Jupyter Notebook**</span><span class="sxs-lookup"><span data-stu-id="b3109-138">**Jupyter Notebook**</span></span>

    ```bash
    jupyter notebook
    ```

    <span data-ttu-id="b3109-139">**Jupyıter Laboratuvarı**</span><span class="sxs-lookup"><span data-stu-id="b3109-139">**Jupyter Lab**</span></span>

    ```bash
    jupyter lab
    ```

    <span data-ttu-id="b3109-140">Bu komutlar Jupyter Notebook veya Jupyıter laboratuvar arabirimiyle bir tarayıcı penceresi başlatır.</span><span class="sxs-lookup"><span data-stu-id="b3109-140">These commands launch a browser window with the Jupyter Notebook or Jupyter Lab interface.</span></span>

1. <span data-ttu-id="b3109-141">Tarayıcıda yeni bir not defteri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b3109-141">In the browser, create a new notebook.</span></span>

    <span data-ttu-id="b3109-142">**Jupyter Notebook**</span><span class="sxs-lookup"><span data-stu-id="b3109-142">**Jupyter Notebook**</span></span>

    <span data-ttu-id="b3109-143">**Yeni > .net (C#)** veya **Yeni > .NET seçin (F #)**</span><span class="sxs-lookup"><span data-stu-id="b3109-143">Select **New > .NET (C#)** or **New > .NET (F#)**</span></span>

    <span data-ttu-id="b3109-144">**Jupyıter Laboratuvarı**</span><span class="sxs-lookup"><span data-stu-id="b3109-144">**Jupyter Lab**</span></span>

    <span data-ttu-id="b3109-145">Başlatıcı penceresinde **.net (C#)** veya **.NET seçin (F #)**</span><span class="sxs-lookup"><span data-stu-id="b3109-145">In the Launcher window, select **.NET (C#)** or **.NET (F#)**</span></span>

### <a name="visual-studio-code-preview"></a><span data-ttu-id="b3109-146">Visual Studio Code (Önizleme)</span><span class="sxs-lookup"><span data-stu-id="b3109-146">Visual Studio Code (preview)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b3109-147">Jupyter not defterlerini VS Code kullanmak için şunu yüklemelisiniz:</span><span class="sxs-lookup"><span data-stu-id="b3109-147">To use Jupyter Notebooks in VS Code, you have to install:</span></span>
>
>- [<span data-ttu-id="b3109-148">VS Code Insiders</span><span class="sxs-lookup"><span data-stu-id="b3109-148">VS Code Insiders</span></span>](https://code.visualstudio.com/insiders/)
>- [<span data-ttu-id="b3109-149">.NET etkileşimli not defterleri uzantısı</span><span class="sxs-lookup"><span data-stu-id="b3109-149">.NET Interactive Notebooks extension</span></span>](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.dotnet-interactive-vscode)

1. <span data-ttu-id="b3109-150">VS Code’u açın.</span><span class="sxs-lookup"><span data-stu-id="b3109-150">Open VS Code.</span></span>
1. <span data-ttu-id="b3109-151">Komut paleti **görünümünü > komut paleti**' ni açın.</span><span class="sxs-lookup"><span data-stu-id="b3109-151">Open the command palette **View > Command Palette**.</span></span>

    <span data-ttu-id="b3109-152">Komut paleti göründüğünde, yeni bir .NET etkileşimli not defteri oluşturmak için aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="b3109-152">When the command palette appears, enter the following command to create a new .NET Interactive notebook:</span></span>

    ```text
    >.NET Interactive: Create new blank notebook
    ```

    <span data-ttu-id="b3109-153">Alternatif olarak, var olan bir .NET etkileşimli not defterini *. ipynb* uzantısıyla açmak istiyorsanız aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="b3109-153">Alternatively, if you want to open an existing .NET Interactive notebook with the *.ipynb* extension, use the following command:</span></span>

    ```text
    >.NET Interactive: Open notebook
    ```

## <a name="initialize-a-spark-session"></a><span data-ttu-id="b3109-154">Spark oturumu başlatma</span><span class="sxs-lookup"><span data-stu-id="b3109-154">Initialize a Spark Session</span></span>

1. <span data-ttu-id="b3109-155">Not Defteri açıldığında, `Microsoft.Spark` NuGet paketini yükler.</span><span class="sxs-lookup"><span data-stu-id="b3109-155">When the notebook opens, install the `Microsoft.Spark` NuGet package.</span></span> <span data-ttu-id="b3109-156">Yüklediğiniz sürümün .NET Worker ile aynı olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="b3109-156">Make sure the version you install is the same as the .NET Worker.</span></span>

    ```text
    #r "nuget:Microsoft.Spark, 0.12.1"
    ```

1. <span data-ttu-id="b3109-157">Aşağıdaki using ifadesini not defterine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b3109-157">Add the following using statement to the notebook.</span></span>

    ```csharp
    using Microsoft.Spark.Sql;
    ```

1. <span data-ttu-id="b3109-158">[Mini oturum oturumunuzu](xref:Microsoft.Spark.Sql.SparkSession)başlatın.</span><span class="sxs-lookup"><span data-stu-id="b3109-158">Initialize your [SparkSession](xref:Microsoft.Spark.Sql.SparkSession).</span></span>

    ```csharp
    var sparkSession =
    SparkSession
        .Builder()
        .AppName("dotnet-interactive-spark")
        .GetOrCreate();
    ```

<span data-ttu-id="b3109-159">Not defteri aşağıdaki görüntüde gösterilene benzer görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="b3109-159">The notebook should look similar to the one in the following image.</span></span> <span data-ttu-id="b3109-160">Bu örnek VS Code kullanır, ancak Jupyter Notebook ve Jupyıter Laboratuvarı aynı şekilde görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="b3109-160">This example uses VS Code, but Jupyter Notebook and Jupyter Lab should look about the same.</span></span>

> [!div class="mx-imgBorder"]
<span data-ttu-id="b3109-161">![Apache Spark Jupyter Notebook için .NET VS Code](media/dotnet-spark-jupyter-notebooks/jupyter-notebooks-dotnet-spark-vscode.png)</span><span class="sxs-lookup"><span data-stu-id="b3109-161">![.NET for Apache Spark Jupyter Notebook VS Code](media/dotnet-spark-jupyter-notebooks/jupyter-notebooks-dotnet-spark-vscode.png)</span></span>

## <a name="next-steps"></a><span data-ttu-id="b3109-162">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="b3109-162">Next Steps</span></span>

- [<span data-ttu-id="b3109-163">Apache Spark için .NET ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="b3109-163">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
- [<span data-ttu-id="b3109-164">Apache Spark ve ML.NET için .NET kullanarak yaklaşımı tahmin edin</span><span class="sxs-lookup"><span data-stu-id="b3109-164">Predict sentiment using .NET for Apache Spark and ML.NET</span></span>](../tutorials/ml-sentiment-analysis.md)
- <span data-ttu-id="b3109-165">.NET etkileşimli hakkında daha fazla bilgi için bkz. [.net etkileşimli belgeleri](https://github.com/dotnet/interactive/blob/main/docs/README.md).</span><span class="sxs-lookup"><span data-stu-id="b3109-165">For more information on .NET Interactive, see the [.NET Interactive documentation](https://github.com/dotnet/interactive/blob/main/docs/README.md).</span></span>
