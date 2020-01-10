---
title: ML.NET komut satırı arabirimi (CLı) aracını yüklemek
description: ML.NET komut satırı arabirimi (CLı) aracını yükleme, yükseltme, düşürme ve kaldırma hakkında bilgi edinin.
ms.date: 12/18/2019
ms.openlocfilehash: 350122f2d2d2f03484ab6e272b482adf2094495c
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75739972"
---
# <a name="how-to-install-the-mlnet-command-line-interface-cli-tool"></a><span data-ttu-id="e16e7-103">ML.NET komut satırı arabirimi (CLı) aracını yüklemek</span><span class="sxs-lookup"><span data-stu-id="e16e7-103">How to install the ML.NET Command-Line Interface (CLI) tool</span></span>

<span data-ttu-id="e16e7-104">Windows, Mac veya Linux 'a ML.NET CLı (komut satırı arabirimi) yüklemeyi öğrenin.</span><span class="sxs-lookup"><span data-stu-id="e16e7-104">Learn how to install the ML.NET CLI (command-line interface) on Windows, Mac, or Linux.</span></span>

<span data-ttu-id="e16e7-105">ML.NET CLı, otomatik makine öğrenimi (Otomatikml) ve bir eğitim veri kümesini kullanarak iyi kalitede ML.NET modelleri ve kaynak kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e16e7-105">The ML.NET CLI generates good quality ML.NET models and source code using automated machine learning (AutoML) and a training dataset.</span></span>

> [!NOTE]
> <span data-ttu-id="e16e7-106">Bu konu, şu anda önizleme aşamasında olan ML.NET CLı ve ML.NET oto ml 'ye başvurur ve malzemeler değişebilir.</span><span class="sxs-lookup"><span data-stu-id="e16e7-106">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="e16e7-107">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="e16e7-107">Pre-requisites</span></span>

- [<span data-ttu-id="e16e7-108">.NET Core 2,2 SDK</span><span class="sxs-lookup"><span data-stu-id="e16e7-108">.NET Core 2.2 SDK</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)

- <span data-ttu-id="e16e7-109">Seçim [Visual Studio 2017 veya 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="e16e7-109">(Optional) [Visual Studio 2017 or 2019](https://visualstudio.microsoft.com/vs/)</span></span>

<span data-ttu-id="e16e7-110">Oluşturulan C# kod projelerini `F5` tuşuna basarak veya `dotnet run` (.NET Core CLI) Ile Visual Studio ile çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e16e7-110">You can run the generated C# code projects with Visual Studio by pressing the `F5` key or with `dotnet run` (.NET Core CLI).</span></span>

<span data-ttu-id="e16e7-111">Not: [.NET Core 2,2 SDK 'yı](https://dotnet.microsoft.com/download/dotnet-core/2.2) yükledikten sonra `dotnet tool` komutu çalışmıyor, Windows oturumunu kapatıp tekrar oturum açın.</span><span class="sxs-lookup"><span data-stu-id="e16e7-111">Note: If after installing [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) the `dotnet tool` command is not working, sign out from Windows and sign in again.</span></span>

## <a name="install"></a><span data-ttu-id="e16e7-112">yükleme</span><span class="sxs-lookup"><span data-stu-id="e16e7-112">Install</span></span>

<span data-ttu-id="e16e7-113">ML.NET CLı, diğer DotNet genel aracı gibi yüklenir.</span><span class="sxs-lookup"><span data-stu-id="e16e7-113">The ML.NET CLI is installed like any other dotnet Global Tool.</span></span> <span data-ttu-id="e16e7-114">`dotnet tool install` .NET Core CLI komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="e16e7-114">You use the `dotnet tool install` .NET Core CLI command.</span></span>

<span data-ttu-id="e16e7-115">Aşağıdaki örnek, ML.NET CLı 'nın varsayılan NuGet akış konumuna nasıl yükleneceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="e16e7-115">The following example shows how to install the ML.NET CLI in the default NuGet feed location:</span></span>

```dotnetcli
dotnet tool install -g mlnet
```

<span data-ttu-id="e16e7-116">Araç yüklenemezse (yani, varsayılan NuGet akışında yoksa) hata iletileri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e16e7-116">If the tool can't be installed (that is, if it is not available at the default NuGet feed), error messages are displayed.</span></span> <span data-ttu-id="e16e7-117">Beklediğiniz akışların denetlendiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="e16e7-117">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="e16e7-118">Yükleme başarılı olursa, aşağıdaki örneğe benzer şekilde, aracı ve yüklü sürümü çağırmak için kullanılan komutu gösteren bir ileti görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="e16e7-118">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```console
You can invoke the tool using the following command: mlnet
Tool 'mlnet' (version 'X.X.X') was successfully installed.
```

<span data-ttu-id="e16e7-119">Aşağıdaki komutu yazarak yüklemenin başarılı olduğunu doğrulayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e16e7-119">You can confirm the installation was successful by typing the following command:</span></span>

```console
mlnet
```

<span data-ttu-id="e16e7-120">' Auto-eğitme ' komutu gibi mlnet aracının kullanılabilir komutları için yardım görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e16e7-120">You should see the help for available commands for the mlnet tool such as the 'auto-train' command.</span></span>

## <a name="install-a-specific-release-version"></a><span data-ttu-id="e16e7-121">Belirli bir yayın sürümünü yükler</span><span class="sxs-lookup"><span data-stu-id="e16e7-121">Install a specific release version</span></span>

<span data-ttu-id="e16e7-122">Bir yayın öncesi sürüm veya aracın belirli bir sürümünü yüklemeye çalışıyorsanız, [çerçeveyi](../../standard/frameworks.md) aşağıdaki biçimi kullanarak belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e16e7-122">If you're trying to install a pre-release version or a specific version of the tool, you can specify the [framework](../../standard/frameworks.md) using the following format:</span></span>

```dotnetcli
dotnet tool install -g mlnet --framework <FRAMEWORK>
```

<span data-ttu-id="e16e7-123">Ayrıca, aşağıdaki komutu yazarak paketin düzgün yüklenip yüklenmediğini da denetleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e16e7-123">You can also check if the package is properly installed by typing the following command:</span></span>

```dotnetcli
dotnet tool list -g
```

## <a name="uninstall-the-cli-package"></a><span data-ttu-id="e16e7-124">CLı paketini kaldırma</span><span class="sxs-lookup"><span data-stu-id="e16e7-124">Uninstall the CLI package</span></span>

<span data-ttu-id="e16e7-125">Paketi yerel makinenizden kaldırmak için aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="e16e7-125">Type the following command to uninstall the package from your local machine:</span></span>

```dotnetcli
dotnet tool uninstall mlnet -g
```

## <a name="update-the-cli-package"></a><span data-ttu-id="e16e7-126">CLı paketini güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="e16e7-126">Update the CLI package</span></span>

<span data-ttu-id="e16e7-127">Paketi yerel makinenizden güncelleştirmek için aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="e16e7-127">Type the following command to update the package from your local machine:</span></span>

```dotnetcli
dotnet tool update -g mlnet
```

## <a name="set-up-cli-suggestions-tab-based-auto-completion"></a><span data-ttu-id="e16e7-128">CLı önerilerini ayarlama (sekme tabanlı otomatik tamamlama)</span><span class="sxs-lookup"><span data-stu-id="e16e7-128">Set up CLI suggestions (tab-based auto-completion)</span></span>

<span data-ttu-id="e16e7-129">ML.NET CLı `System.CommandLine`tabanlı olduğundan, sekme tamamlama için yerleşik desteğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e16e7-129">Since the ML.NET CLI is based on `System.CommandLine`, it has built-in support for tab completion.</span></span>

<span data-ttu-id="e16e7-130">Aşağıdaki animasyonda sekme otomatik tamamlama 'nın nasıl çalıştığına bir örnek gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="e16e7-130">An example of how tab auto completion works is shown in the following animation:</span></span>

![görüntü](./media/cli-tab-completion.gif)

<span data-ttu-id="e16e7-132">' Sekme tabanlı otomatik tamamlama ' (parametre önerileri) *Windows PowerShell* ve *MacOS/Linux Bash* üzerinde çalışır, ancak *Windows cmd*'de çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="e16e7-132">'Tab-based auto-completion' (parameter suggestions) works on *Windows PowerShell* and *macOS/Linux bash* but it won't work on *Windows CMD*.</span></span>

<span data-ttu-id="e16e7-133">Bu ayarı etkinleştirmek için, geçerli önizleme sürümünde son kullanıcının aşağıda belirtilen her kabuk için birkaç adım olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e16e7-133">To enable it, in the current preview version, the end user has to take a few steps once per shell, outlined below.</span></span> <span data-ttu-id="e16e7-134">Bu işlem tamamlandıktan sonra, ML.NET CLı gibi `System.CommandLine` kullanılarak yazılmış tüm uygulamalar için tamamlama işlemleri çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="e16e7-134">Once this is done, completions will work for all apps written using `System.CommandLine` such as the ML.NET CLI.</span></span>

<span data-ttu-id="e16e7-135">Tamamlamayı etkinleştirmek istediğiniz makinede iki şey yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e16e7-135">On the machine where you'd like to enable completion, you'll need to do two things.</span></span>

1. <span data-ttu-id="e16e7-136">Aşağıdaki komutu çalıştırarak `dotnet-suggest` genel aracını yüklersiniz:</span><span class="sxs-lookup"><span data-stu-id="e16e7-136">Install the `dotnet-suggest` global tool by running the following command:</span></span>

    ```dotnetcli
    dotnet tool install dotnet-suggest -g
    ```

2. <span data-ttu-id="e16e7-137">Kabuk profilinize uygun dolgu betiğini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e16e7-137">Add the appropriate shim script to your shell profile.</span></span> <span data-ttu-id="e16e7-138">Bir kabuk profili dosyası oluşturmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="e16e7-138">You may have to create a shell profile file.</span></span> <span data-ttu-id="e16e7-139">Dolgu betiği, kabuğınızdan tamamlama isteklerini, uygun `System.CommandLine`tabanlı uygulamaya temsilci olan `dotnet-suggest` aracına iletmez.</span><span class="sxs-lookup"><span data-stu-id="e16e7-139">The shim script will forward completion requests from your shell to the `dotnet-suggest` tool, which delegates to the appropriate `System.CommandLine`-based app.</span></span>

    - <span data-ttu-id="e16e7-140">Bash için [DotNet-öner-Shim. bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) içeriğini `~/.bash_profile`' ye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e16e7-140">For bash, add the contents of [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) to `~/.bash_profile`.</span></span>

    - <span data-ttu-id="e16e7-141">PowerShell için, [DotNet-Suggest-Shim. ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) içeriğini PowerShell profilinize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e16e7-141">For PowerShell, add the contents of [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) to your PowerShell profile.</span></span> <span data-ttu-id="e16e7-142">Konsolunda aşağıdaki komutu çalıştırarak, PowerShell profilinize beklenen yolu bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e16e7-142">You can find the expected path to your PowerShell profile by running the following command in your console:</span></span>

    ```console
    echo $profile
    ```

<span data-ttu-id="e16e7-143">(Diğer kabuklar için bir [sorun](https://github.com/dotnet/System.CommandLine/issues) [bulun](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) veya açın.)</span><span class="sxs-lookup"><span data-stu-id="e16e7-143">(For other shells, [look for](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) or open an [issue](https://github.com/dotnet/System.CommandLine/issues).)</span></span>

## <a name="installation-directory"></a><span data-ttu-id="e16e7-144">Yükleme dizini</span><span class="sxs-lookup"><span data-stu-id="e16e7-144">Installation directory</span></span>

<span data-ttu-id="e16e7-145">ML.NET CLı varsayılan dizine veya belirli bir konuma yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="e16e7-145">The ML.NET CLI can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="e16e7-146">Varsayılan dizinler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e16e7-146">The default directories are:</span></span>

| <span data-ttu-id="e16e7-147">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="e16e7-147">OS</span></span>          | <span data-ttu-id="e16e7-148">Yol</span><span class="sxs-lookup"><span data-stu-id="e16e7-148">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="e16e7-149">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="e16e7-149">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="e16e7-150">Windows</span><span class="sxs-lookup"><span data-stu-id="e16e7-150">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="e16e7-151">Bu konumlar, SDK ilk kez çalıştırıldığında kullanıcının yoluna eklenir, bu nedenle genel araçlar yüklenir, böylece doğrudan çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="e16e7-151">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="e16e7-152">Not: genel araçlar, makineye genel değil, kullanıcıya özeldir.</span><span class="sxs-lookup"><span data-stu-id="e16e7-152">Note: the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="e16e7-153">Kullanıcıya özel olması, makinenin tüm kullanıcıları için kullanılabilir olan küresel bir araç yükleyemeyeceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e16e7-153">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="e16e7-154">Araç yalnızca aracın yüklendiği her kullanıcı profili için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e16e7-154">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="e16e7-155">Genel araçlar, belirli bir dizine de yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="e16e7-155">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="e16e7-156">Belirli bir dizine yüklendiğinde, kullanıcının, yolu belirtilen dizin ile çağırarak veya aracı belirtilen dizin içinden çağırarak, bu dizini da dahil ederek komutun kullanılabilir olduğundan emin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e16e7-156">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="e16e7-157">Bu durumda .NET Core CLI, bu konumu otomatik olarak PATH ortam değişkenine eklemez.</span><span class="sxs-lookup"><span data-stu-id="e16e7-157">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="e16e7-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e16e7-158">See also</span></span>

- [<span data-ttu-id="e16e7-159">ML.NET CLı genel bakış</span><span class="sxs-lookup"><span data-stu-id="e16e7-159">ML.NET CLI overview</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="e16e7-160">Öğretici: ML.NET CLı ile yaklaşımı çözümleme</span><span class="sxs-lookup"><span data-stu-id="e16e7-160">Tutorial: Analyze sentiment with the ML.NET CLI</span></span>](../tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="e16e7-161">ML.NET CLı otomatik eğitme komut başvuru kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e16e7-161">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="e16e7-162">ML.NET CLı 'de telemetri</span><span class="sxs-lookup"><span data-stu-id="e16e7-162">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
