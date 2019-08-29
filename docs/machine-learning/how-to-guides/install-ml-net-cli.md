---
title: ML.NET komut satırı arabirimi (CLı) aracını yüklemek
description: ML.NET komut satırı arabirimi (CLı) aracının genel bakış ve yükleme.
ms.date: 04/16/2019
ms.custom: ''
ms.openlocfilehash: 8b6de466a6cf72b44a16c80fc024671bc4e975e8
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106896"
---
# <a name="how-to-install-the-mlnet-command-line-interface-cli-tool"></a><span data-ttu-id="f83b3-103">ML.NET komut satırı arabirimi (CLı) aracını yüklemek</span><span class="sxs-lookup"><span data-stu-id="f83b3-103">How to install the ML.NET Command-Line Interface (CLI) tool</span></span>

<span data-ttu-id="f83b3-104">ML.NET CLı (komut satırı arabirimi), sağladığınız eğitim veri kümelerine göre iyi kalitede ML.NET modelleri ve kaynak kodu oluşturmak için herhangi bir komut isteminde (Windows, Mac veya Linux) çalıştırabileceğiniz bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="f83b3-104">The ML.NET CLI (command-line interface) is a tool you can run on any command-prompt (Windows, Mac, or Linux) for generating good quality ML.NET models and source code based on training datasets you provide.</span></span>

> [!NOTE]
> <span data-ttu-id="f83b3-105">Bu konu, şu anda önizleme aşamasında olan ML.NET CLı ve ML.NET oto ml 'ye başvurur ve malzemeler değişebilir.</span><span class="sxs-lookup"><span data-stu-id="f83b3-105">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="f83b3-106">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="f83b3-106">Pre-requisites</span></span>

- [<span data-ttu-id="f83b3-107">.NET Core 2,2 SDK</span><span class="sxs-lookup"><span data-stu-id="f83b3-107">.NET Core 2.2 SDK</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)

- <span data-ttu-id="f83b3-108">Seçim [Visual Studio 2017 veya 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="f83b3-108">(Optional) [Visual Studio 2017 or 2019](https://visualstudio.microsoft.com/vs/)</span></span>

<span data-ttu-id="f83b3-109">Oluşturulan C# kod projelerini Visual Studio F5 ya `dotnet run` da (.NET Core CLI) ile çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f83b3-109">You can either run the generated C# code projects with Visual Studio F5 or with `dotnet run` (.NET Core CLI).</span></span>

<span data-ttu-id="f83b3-110">Not: [.NET Core 2,2 SDK 'sını](https://dotnet.microsoft.com/download/dotnet-core/2.2) `dotnet tool` yükledikten sonra komut çalışmıyor, Windows oturumunu kapatıp tekrar oturum açın.</span><span class="sxs-lookup"><span data-stu-id="f83b3-110">Note: If after installing [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) the `dotnet tool` command is not working, sign out from Windows and sign in again.</span></span>

## <a name="install"></a><span data-ttu-id="f83b3-111">Yükleme</span><span class="sxs-lookup"><span data-stu-id="f83b3-111">Install</span></span>

<span data-ttu-id="f83b3-112">ML.NET CLı, diğer DotNet genel aracı gibi yüklenir.</span><span class="sxs-lookup"><span data-stu-id="f83b3-112">The ML.NET CLI is installed like any other dotnet Global Tool.</span></span> <span data-ttu-id="f83b3-113">`dotnet tool install` .NET Core CLI komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="f83b3-113">You use the `dotnet tool install` .NET Core CLI command.</span></span> 

<span data-ttu-id="f83b3-114">Aşağıdaki örnek, ML.NET CLı 'nın varsayılan NuGet akış konumuna nasıl yükleneceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="f83b3-114">The following example shows how to install the ML.NET CLI in the default NuGet feed location:</span></span>

```console
dotnet tool install -g mlnet
```

<span data-ttu-id="f83b3-115">Araç yüklenemezse (yani, varsayılan NuGet akışında yoksa) hata iletileri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f83b3-115">If the tool can't be installed (that is, if it is not available at the default NuGet feed), error messages are displayed.</span></span> <span data-ttu-id="f83b3-116">Beklediğiniz akışların denetlendiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="f83b3-116">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="f83b3-117">Yükleme başarılı olursa, aşağıdaki örneğe benzer şekilde, aracı ve yüklü sürümü çağırmak için kullanılan komutu gösteren bir ileti görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="f83b3-117">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```console
You can invoke the tool using the following command: mlnet
Tool 'mlnet' (version 'X.X.X') was successfully installed.
```

<span data-ttu-id="f83b3-118">Aşağıdaki komutu yazarak yüklemenin başarılı olduğunu doğrulayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f83b3-118">You can confirm the installation was successful by typing the following command:</span></span>

```console
mlnet
```

<span data-ttu-id="f83b3-119">' Auto-eğitme ' komutu gibi mlnet aracının kullanılabilir komutları için yardım görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f83b3-119">You should see the help for available commands for the mlnet tool such as the 'auto-train' command.</span></span>

## <a name="install-a-specific-release-version"></a><span data-ttu-id="f83b3-120">Belirli bir yayın sürümünü yükler</span><span class="sxs-lookup"><span data-stu-id="f83b3-120">Install a specific release version</span></span>

<span data-ttu-id="f83b3-121">Bir yayın öncesi sürüm veya aracın belirli bir sürümünü yüklemeye çalışıyorsanız, [çerçeveyi](../../standard/frameworks.md) aşağıdaki biçimi kullanarak belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f83b3-121">If you're trying to install a pre-release version or a specific version of the tool, you can specify the [framework](../../standard/frameworks.md) using the following format:</span></span>

```console
dotnet tool install -g mlnet --framework <FRAMEWORK>
```

<span data-ttu-id="f83b3-122">Ayrıca, aşağıdaki komutu yazarak paketin düzgün yüklenip yüklenmediğini da denetleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f83b3-122">You can also check if the package is properly installed by typing the following command:</span></span>

```console
dotnet tool list -g
```

## <a name="uninstall-the-cli-package"></a><span data-ttu-id="f83b3-123">CLı paketini kaldırma</span><span class="sxs-lookup"><span data-stu-id="f83b3-123">Uninstall the CLI package</span></span>

<span data-ttu-id="f83b3-124">Paketi yerel makinenizden kaldırmak için aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="f83b3-124">Type the following command to uninstall the package from your local machine:</span></span>

```console
dotnet tool uninstall mlnet -g
```

## <a name="update-the-cli-package"></a><span data-ttu-id="f83b3-125">CLı paketini güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="f83b3-125">Update the CLI package</span></span>

<span data-ttu-id="f83b3-126">Paketi yerel makinenizden güncelleştirmek için aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="f83b3-126">Type the following command to update the package from your local machine:</span></span>

```console
dotnet tool update -g mlnet
```

## <a name="set-up-cli-suggestions-tab-based-auto-completion"></a><span data-ttu-id="f83b3-127">CLı önerilerini ayarlama (sekme tabanlı otomatik tamamlama)</span><span class="sxs-lookup"><span data-stu-id="f83b3-127">Set up CLI suggestions (tab-based auto-completion)</span></span>

<span data-ttu-id="f83b3-128">ML.net CLI tabanlı `System.CommandLine`olduğundan, sekme tamamlama için yerleşik desteğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f83b3-128">Since the ML.NET CLI is based on `System.CommandLine`, it has built-in support for tab completion.</span></span>

<span data-ttu-id="f83b3-129">Aşağıdaki animasyonda sekme otomatik tamamlama 'nın nasıl çalıştığına bir örnek gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="f83b3-129">An example of how tab auto completion works is shown in the following animation:</span></span>

![görüntü](./media/cli-tab-completion.gif)

<span data-ttu-id="f83b3-131">' Sekme tabanlı otomatik tamamlama ' (parametre önerileri) *Windows PowerShell* ve *MacOS/Linux Bash* üzerinde çalışır, ancak *Windows cmd*'de çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="f83b3-131">'Tab-based auto-completion' (parameter suggestions) works on *Windows PowerShell* and *macOS/Linux bash* but it won't work on *Windows CMD*.</span></span>

<span data-ttu-id="f83b3-132">Bu ayarı etkinleştirmek için, geçerli önizleme sürümünde son kullanıcının aşağıda belirtilen her kabuk için birkaç adım olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f83b3-132">To enable it, in the current preview version, the end user has to take a few steps once per shell, outlined below.</span></span> <span data-ttu-id="f83b3-133">Bu işlem tamamlandıktan sonra, ml.net CLI gibi kullanılarak `System.CommandLine` yazılan tüm uygulamalar için tamamlama işlemleri çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="f83b3-133">Once this is done, completions will work for all apps written using `System.CommandLine` such as the ML.NET CLI.</span></span>

<span data-ttu-id="f83b3-134">Tamamlamayı etkinleştirmek istediğiniz makinede iki şey yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f83b3-134">On the machine where you'd like to enable completion, you'll need to do two things.</span></span>

1. <span data-ttu-id="f83b3-135">Aşağıdaki komutu çalıştırarak genel aracı 'nı yüklersiniz: `dotnet-suggest`</span><span class="sxs-lookup"><span data-stu-id="f83b3-135">Install the `dotnet-suggest` global tool by running the following command:</span></span>

    ```console
    dotnet tool install dotnet-suggest -g
    ```

2. <span data-ttu-id="f83b3-136">Kabuk profilinize uygun dolgu betiğini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f83b3-136">Add the appropriate shim script to your shell profile.</span></span> <span data-ttu-id="f83b3-137">Bir kabuk profili dosyası oluşturmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="f83b3-137">You may have to create a shell profile file.</span></span> <span data-ttu-id="f83b3-138">Dolgu betiği, kabuğunuzun `dotnet-suggest` tamamlanma isteklerini, uygun `System.CommandLine`tabanlı uygulamaya temsilci olan bir araca iletir.</span><span class="sxs-lookup"><span data-stu-id="f83b3-138">The shim script will forward completion requests from your shell to the `dotnet-suggest` tool, which delegates to the appropriate `System.CommandLine`-based app.</span></span>

    - <span data-ttu-id="f83b3-139">Bash için [DotNet-öner-Shim. bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) içeriğini ' ye `~/.bash_profile`ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f83b3-139">For bash, add the contents of [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) to `~/.bash_profile`.</span></span>

    - <span data-ttu-id="f83b3-140">PowerShell için, [DotNet-Suggest-Shim. ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) içeriğini PowerShell profilinize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f83b3-140">For PowerShell, add the contents of [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) to your PowerShell profile.</span></span> <span data-ttu-id="f83b3-141">Konsolunda aşağıdaki komutu çalıştırarak, PowerShell profilinize beklenen yolu bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f83b3-141">You can find the expected path to your PowerShell profile by running the following command in your console:</span></span>

    ```console
    echo $profile
    ``` 

<span data-ttu-id="f83b3-142">(Diğer kabuklar için bir [sorun](https://github.com/dotnet/System.CommandLine/issues) [bulun](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) veya açın.)</span><span class="sxs-lookup"><span data-stu-id="f83b3-142">(For other shells, [look for](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) or open an [issue](https://github.com/dotnet/System.CommandLine/issues).)</span></span>

## <a name="installation-directory"></a><span data-ttu-id="f83b3-143">Yükleme dizini</span><span class="sxs-lookup"><span data-stu-id="f83b3-143">Installation directory</span></span>

<span data-ttu-id="f83b3-144">ML.NET CLı varsayılan dizine veya belirli bir konuma yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="f83b3-144">The ML.NET CLI can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="f83b3-145">Varsayılan dizinler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f83b3-145">The default directories are:</span></span>

| <span data-ttu-id="f83b3-146">OS</span><span class="sxs-lookup"><span data-stu-id="f83b3-146">OS</span></span>          | <span data-ttu-id="f83b3-147">Yol</span><span class="sxs-lookup"><span data-stu-id="f83b3-147">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="f83b3-148">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="f83b3-148">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="f83b3-149">Windows</span><span class="sxs-lookup"><span data-stu-id="f83b3-149">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="f83b3-150">Bu konumlar, SDK ilk kez çalıştırıldığında kullanıcının yoluna eklenir, bu nedenle genel araçlar yüklenir, böylece doğrudan çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="f83b3-150">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="f83b3-151">Not: genel araçlar, makineye genel değil, kullanıcıya özeldir.</span><span class="sxs-lookup"><span data-stu-id="f83b3-151">Note: the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="f83b3-152">Kullanıcıya özel olması, makinenin tüm kullanıcıları için kullanılabilir olan küresel bir araç yükleyemeyeceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f83b3-152">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="f83b3-153">Araç yalnızca aracın yüklendiği her kullanıcı profili için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f83b3-153">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="f83b3-154">Genel araçlar, belirli bir dizine de yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="f83b3-154">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="f83b3-155">Belirli bir dizine yüklendiğinde, kullanıcının, yolu belirtilen dizin ile çağırarak veya aracı belirtilen dizin içinden çağırarak, bu dizini da dahil ederek komutun kullanılabilir olduğundan emin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f83b3-155">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="f83b3-156">Bu durumda .NET Core CLI, bu konumu otomatik olarak PATH ortam değişkenine eklemez.</span><span class="sxs-lookup"><span data-stu-id="f83b3-156">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="f83b3-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f83b3-157">See also</span></span>

- [<span data-ttu-id="f83b3-158">' ML.NET CLı aracıyla çalışmaya başlama ' öğreticisi</span><span class="sxs-lookup"><span data-stu-id="f83b3-158">Tutorial on 'Getting Started with ML.NET CLI tool'</span></span>](../tutorials/mlnet-cli.md)
- [<span data-ttu-id="f83b3-159">ML.NET CLı aracı ile modelleri otomatik olarak eğitme</span><span class="sxs-lookup"><span data-stu-id="f83b3-159">How to automatically train models with the ML.NET CLI tool</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="f83b3-160">ML.NET CLı otomatik eğitme komut başvuru kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f83b3-160">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md) 
- [<span data-ttu-id="f83b3-161">ML.NET CLı 'de telemetri</span><span class="sxs-lookup"><span data-stu-id="f83b3-161">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
