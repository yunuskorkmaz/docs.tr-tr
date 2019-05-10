---
title: ML.NET komut satırı arabirimi (CLI) aracı yükleme
description: Genel bakış ve ML.NET komut satırı arabirimi (CLI) aracı yükleme.
ms.date: 04/16/2019
ms.custom: ''
ms.openlocfilehash: 869c443d519557c9d3976676047e63a4a072d2d3
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65066237"
---
# <a name="how-to-install-the-mlnet-command-line-interface-cli-tool"></a><span data-ttu-id="7ce7a-103">ML.NET komut satırı arabirimi (CLI) aracı yükleme</span><span class="sxs-lookup"><span data-stu-id="7ce7a-103">How to install the ML.NET Command-Line Interface (CLI) tool</span></span>

<span data-ttu-id="7ce7a-104">ML.NET CLI (komut satırı arabirimi) kaliteli ML.NET modelleri ve sağladığınız eğitim veri kümeleri üzerinde tabanlı kaynak kodu oluşturmak için bir komut istemi üzerinde (Windows, Mac veya Linux) çalıştırabilirsiniz. bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="7ce7a-104">The ML.NET CLI (command-line interface) is a tool you can run on any command-prompt (Windows, Mac, or Linux) for generating good quality ML.NET models and source code based on training datasets you provide.</span></span>

> [!NOTE]
> <span data-ttu-id="7ce7a-105">ML.NET CLI ve ML.NET AutoML şu anda önizlemede olan bu konuda ifade eder ve malzeme değişiklik gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="7ce7a-105">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="7ce7a-106">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="7ce7a-106">Pre-requisites</span></span>

- [<span data-ttu-id="7ce7a-107">.NET core SDK'sını 2.2</span><span class="sxs-lookup"><span data-stu-id="7ce7a-107">.NET Core 2.2 SDK</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)

- <span data-ttu-id="7ce7a-108">(İsteğe bağlı) [Visual Studio 2017 veya 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="7ce7a-108">(Optional) [Visual Studio 2017 or 2019](https://visualstudio.microsoft.com/vs/)</span></span>

<span data-ttu-id="7ce7a-109">Çalıştırabilir ya da oluşturulan C# kod projelerini Visual Studio F5 veya ile `dotnet run` (.NET Core CLI).</span><span class="sxs-lookup"><span data-stu-id="7ce7a-109">You can either run the generated C# code projects with Visual Studio F5 or with `dotnet run` (.NET Core CLI).</span></span>

<span data-ttu-id="7ce7a-110">Not: Yükledikten sonra eğer [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) `dotnet tool` çalışmıyor komutu, Windows oturumunuzu kapatıp tekrar açın.</span><span class="sxs-lookup"><span data-stu-id="7ce7a-110">Note: If after installing [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) the `dotnet tool` command is not working, sign out from Windows and sign in again.</span></span>

## <a name="install"></a><span data-ttu-id="7ce7a-111">Yükleme</span><span class="sxs-lookup"><span data-stu-id="7ce7a-111">Install</span></span>

<span data-ttu-id="7ce7a-112">ML.NET CLI herhangi diğer dotnet gibi genel aracı yüklenir.</span><span class="sxs-lookup"><span data-stu-id="7ce7a-112">The ML.NET CLI is installed like any other dotnet Global Tool.</span></span> <span data-ttu-id="7ce7a-113">Kullandığınız `dotnet tool install` .NET Core CLI komutu.</span><span class="sxs-lookup"><span data-stu-id="7ce7a-113">You use the `dotnet tool install` .NET Core CLI command.</span></span> 

<span data-ttu-id="7ce7a-114">Aşağıdaki örnek, NuGet Özet akışı konumu varsayılan olarak ML.NET CLI'yı yükleme gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7ce7a-114">The following example shows how to install the ML.NET CLI in the default NuGet feed location:</span></span>

```console
> dotnet tool install -g mlnet
```

<span data-ttu-id="7ce7a-115">(Diğer bir deyişle, NuGet akışı varsayılan olarak kullanılabilir değilse) araç yüklenemiyor, hata iletileri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7ce7a-115">If the tool can't be installed (that is, if it is not available at the default NuGet feed), error messages are displayed.</span></span> <span data-ttu-id="7ce7a-116">Beklediğiniz akışları denetlendiği denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7ce7a-116">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="7ce7a-117">Yükleme başarılı olursa, aracı ve yüklü sürümü çağırmak için kullanılan komut aşağıdaki örneğe benzer gösteren bir ileti görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="7ce7a-117">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```console
You can invoke the tool using the following command: mlnet
Tool 'mlnet' (version 'X.X.X') was successfully installed.
```

<span data-ttu-id="7ce7a-118">Aşağıdaki komutu yazarak yüklemenin başarılı olduğunu doğrulayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7ce7a-118">You can confirm the installation was successful by typing the following command:</span></span>

```console
> mlnet
```

<span data-ttu-id="7ce7a-119">'Otomatik train' komutu gibi mlnet aracı için kullanılabilir komutlar için Yardım görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7ce7a-119">You should see the help for available commands for the mlnet tool such as the 'auto-train' command.</span></span>

## <a name="install-a-specific-release-version"></a><span data-ttu-id="7ce7a-120">Belirli bir sürümünü yükleyin</span><span class="sxs-lookup"><span data-stu-id="7ce7a-120">Install a specific release version</span></span>

<span data-ttu-id="7ce7a-121">Yayın öncesi bir sürümü ya da aracının belirli bir sürümü yüklemeye çalışıyorsanız, sürüm numarası şu biçimi kullanarak belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7ce7a-121">If you're trying to install a pre-release version or a specific version of the tool, you can specify the version number using the following format:</span></span>

```console
> dotnet tool install -g <package-name> --version <version-number>
```

<span data-ttu-id="7ce7a-122">Aşağıdaki komutu yazarak paketi düzgün şekilde yüklendiğinden de göz atabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7ce7a-122">You can also check if the package is properly installed by typing the following command:</span></span>

```console
> dotnet tool list -g
```

## <a name="uninstall-the-cli-package"></a><span data-ttu-id="7ce7a-123">CLI paketini Kaldır</span><span class="sxs-lookup"><span data-stu-id="7ce7a-123">Uninstall the CLI package</span></span>

<span data-ttu-id="7ce7a-124">Paket yerel makinenizden kaldırmak için aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="7ce7a-124">Type the following command to uninstall the package from your local machine:</span></span>

```console
> dotnet tool uninstall mlnet -g
```

## <a name="update-the-cli-package"></a><span data-ttu-id="7ce7a-125">CLI paketini güncelleştirmek</span><span class="sxs-lookup"><span data-stu-id="7ce7a-125">Update the CLI package</span></span>

<span data-ttu-id="7ce7a-126">Güncelleştirme paketi, yerel makinenizde aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="7ce7a-126">Type the following command to update the package from your local machine:</span></span>

```console
> dotnet tool update -g mlnet
```

## <a name="set-up-cli-suggestions-tab-based-auto-completion"></a><span data-ttu-id="7ce7a-127">CLI önerileri (sekme tabanlı otomatik tamamlama) ayarlama</span><span class="sxs-lookup"><span data-stu-id="7ce7a-127">Set up CLI suggestions (tab-based auto-completion)</span></span>

<span data-ttu-id="7ce7a-128">ML.NET CLI dayalı olduğundan `System.CommandLine`, onu sekme tamamlama için yerleşik destek içerir.</span><span class="sxs-lookup"><span data-stu-id="7ce7a-128">Since the ML.NET CLI is based on `System.CommandLine`, it has built-in support for tab completion.</span></span>

<span data-ttu-id="7ce7a-129">Aşağıdaki animasyonda sekme otomatik tamamlama nasıl çalıştığına ilişkin bir örnek gösterilir:</span><span class="sxs-lookup"><span data-stu-id="7ce7a-129">An example of how tab auto completion works is shown in the following animation:</span></span>

![görüntü](./media/cli-tab-completion.gif)

<span data-ttu-id="7ce7a-131">'Sekmesinde tabanlı Otomatik Tamamlama' (parametre önerileri) çalışır *Windows PowerShell* ve *macOS/Linux bash* ancak işe yaramaz *Windows CMD*.</span><span class="sxs-lookup"><span data-stu-id="7ce7a-131">'Tab-based auto-completion' (parameter suggestions) works on *Windows PowerShell* and *macOS/Linux bash* but it won't work on *Windows CMD*.</span></span>

<span data-ttu-id="7ce7a-132">Geçerli Önizleme sürümünde, etkinleştirmek için son kullanıcı başına bir kez aşağıda özetlenen Kabuk birkaç adım gerekir.</span><span class="sxs-lookup"><span data-stu-id="7ce7a-132">To enable it, in the current preview version, the end user has to take a few steps once per shell, outlined below.</span></span> <span data-ttu-id="7ce7a-133">Bunu yaptıktan sonra tamamlamaları kullanılarak yazılmış tüm uygulamalar için çalışır `System.CommandLine` ML.NET CLI gibi.</span><span class="sxs-lookup"><span data-stu-id="7ce7a-133">Once this is done, completions will work for all apps written using `System.CommandLine` such as the ML.NET CLI.</span></span>

<span data-ttu-id="7ce7a-134">Tamamlama etkinleştirmek için istediğiniz makinede iki işlem gerçekleştirmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="7ce7a-134">On the machine where you'd like to enable completion, you'll need to do two things.</span></span>

1. <span data-ttu-id="7ce7a-135">Yükleme `dotnet-suggest` aşağıdaki komutu çalıştırarak genel aracı:</span><span class="sxs-lookup"><span data-stu-id="7ce7a-135">Install the `dotnet-suggest` global tool by running the following command:</span></span>

    ```console
    > dotnet tool install dotnet-suggest -g
    ```

2. <span data-ttu-id="7ce7a-136">Uygun dolgu komut kabuğu profilinize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7ce7a-136">Add the appropriate shim script to your shell profile.</span></span> <span data-ttu-id="7ce7a-137">Bir kabuk profili dosyası oluşturmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="7ce7a-137">You may have to create a shell profile file.</span></span> <span data-ttu-id="7ce7a-138">Dolgu betik için kabuğundan tamamlama isteği iletir `dotnet-suggest` uygun temsilciler aracı `System.CommandLine`-uygulama tabanlı.</span><span class="sxs-lookup"><span data-stu-id="7ce7a-138">The shim script will forward completion requests from your shell to the `dotnet-suggest` tool, which delegates to the appropriate `System.CommandLine`-based app.</span></span>

    * <span data-ttu-id="7ce7a-139">Bash için içeriğini Ekle [dotnet Öner shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) için `~/.bash_profile`.</span><span class="sxs-lookup"><span data-stu-id="7ce7a-139">For bash, add the contents of [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) to `~/.bash_profile`.</span></span>

    * <span data-ttu-id="7ce7a-140">PowerShell için içeriğini Ekle [dotnet Öner shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) PowerShell profiliniz için.</span><span class="sxs-lookup"><span data-stu-id="7ce7a-140">For PowerShell, add the contents of [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) to your PowerShell profile.</span></span> <span data-ttu-id="7ce7a-141">Konsolunuzda aşağıdaki komutu çalıştırarak PowerShell profiliniz için beklenen yoldan bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7ce7a-141">You can find the expected path to your PowerShell profile by running the following command in your console:</span></span>

    ```console
    > echo $profile
    ``` 

<span data-ttu-id="7ce7a-142">(Diğer Kabukları için [Ara](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) veya açık bir [sorunu](https://github.com/dotnet/System.CommandLine/issues).)</span><span class="sxs-lookup"><span data-stu-id="7ce7a-142">(For other shells, [look for](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) or open an [issue](https://github.com/dotnet/System.CommandLine/issues).)</span></span>

## <a name="installation-directory"></a><span data-ttu-id="7ce7a-143">Yükleme dizini</span><span class="sxs-lookup"><span data-stu-id="7ce7a-143">Installation directory</span></span>

<span data-ttu-id="7ce7a-144">ML.NET CLI, varsayılan dizini veya belirli bir konuma yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="7ce7a-144">The ML.NET CLI can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="7ce7a-145">Varsayılan dizinler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="7ce7a-145">The default directories are:</span></span>

| <span data-ttu-id="7ce7a-146">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="7ce7a-146">OS</span></span>          | <span data-ttu-id="7ce7a-147">Yol</span><span class="sxs-lookup"><span data-stu-id="7ce7a-147">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="7ce7a-148">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="7ce7a-148">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="7ce7a-149">Windows</span><span class="sxs-lookup"><span data-stu-id="7ce7a-149">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="7ce7a-150">SDK'yı ilk kez çalıştırdığınızda, genel araçları yüklü doğrudan çağrılabilir için bu konumları kullanıcının yoluna eklenir.</span><span class="sxs-lookup"><span data-stu-id="7ce7a-150">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="7ce7a-151">Not: Genel araçları kullanıcıya özel, genel makine yok.</span><span class="sxs-lookup"><span data-stu-id="7ce7a-151">Note: the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="7ce7a-152">Kullanıcıya özel olan, makinenin tüm kullanıcıları için kullanılabilir olan bir genel aracı yükleyemezsiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7ce7a-152">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="7ce7a-153">Aracı yalnızca, aracının yüklendiği her kullanıcı profili için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7ce7a-153">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="7ce7a-154">Genel araçları Ayrıca belirli bir dizindeki yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="7ce7a-154">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="7ce7a-155">Belirli bir dizindeki yüklendiğinde, kullanıcı komutu kullanılabilir yolunda belirtilen dizinle komutunu çağırarak bu dizine ekleyerek emin olmanız gerekir veya belirtilen dizin içinde aracından çağırma.</span><span class="sxs-lookup"><span data-stu-id="7ce7a-155">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="7ce7a-156">Bu durumda, .NET Core CLI bu konum otomatik olarak PATH ortam değişkenine eklemez.</span><span class="sxs-lookup"><span data-stu-id="7ce7a-156">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ce7a-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ce7a-157">See also</span></span>

- [<span data-ttu-id="7ce7a-158">'Başlangıç ML.NET CLI aracı ile' öğretici</span><span class="sxs-lookup"><span data-stu-id="7ce7a-158">Tutorial on 'Getting Started with ML.NET CLI tool'</span></span>](../tutorials/mlnet-cli.md)
- [<span data-ttu-id="7ce7a-159">Otomatik olarak ML.NET CLI aracını kullanarak modelleri eğitme</span><span class="sxs-lookup"><span data-stu-id="7ce7a-159">How to automatically train models with the ML.NET CLI tool</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="7ce7a-160">ML.NET CLI otomatik train komut Başvuru Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7ce7a-160">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md) 
- [<span data-ttu-id="7ce7a-161">ML.NET CLI'de telemetri</span><span class="sxs-lookup"><span data-stu-id="7ce7a-161">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
