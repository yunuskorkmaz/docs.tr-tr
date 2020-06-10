---
title: ML.NET komut satırı arabirimi (CLı) aracını yüklemek
description: ML.NET komut satırı arabirimi (CLı) aracını yükleme, yükseltme, düşürme ve kaldırma hakkında bilgi edinin.
ms.date: 06/08/2020
ms.custom: mlnet-tooling
ms.openlocfilehash: 13203246411deadf3ab13a5eba0d2c8e6e9027c5
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602277"
---
# <a name="how-to-install-the-mlnet-command-line-interface-cli-tool"></a><span data-ttu-id="9830d-103">ML.NET komut satırı arabirimi (CLı) aracını yüklemek</span><span class="sxs-lookup"><span data-stu-id="9830d-103">How to install the ML.NET Command-Line Interface (CLI) tool</span></span>

<span data-ttu-id="9830d-104">Windows, Mac veya Linux 'a ML.NET CLı (komut satırı arabirimi) yüklemeyi öğrenin.</span><span class="sxs-lookup"><span data-stu-id="9830d-104">Learn how to install the ML.NET CLI (command-line interface) on Windows, Mac, or Linux.</span></span>

<span data-ttu-id="9830d-105">ML.NET CLı, otomatik makine öğrenimi (Otomatikml) ve bir eğitim veri kümesini kullanarak iyi kalitede ML.NET modelleri ve kaynak kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9830d-105">The ML.NET CLI generates good quality ML.NET models and source code using automated machine learning (AutoML) and a training dataset.</span></span>

> [!NOTE]
> <span data-ttu-id="9830d-106">Bu konu, şu anda önizleme aşamasında olan ML.NET CLı ve ML.NET oto ml 'ye başvurur ve malzemeler değişebilir.</span><span class="sxs-lookup"><span data-stu-id="9830d-106">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="9830d-107">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="9830d-107">Pre-requisites</span></span>

- [<span data-ttu-id="9830d-108">.NET Core 3,1 SDK</span><span class="sxs-lookup"><span data-stu-id="9830d-108">.NET Core 3.1 SDK</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

- <span data-ttu-id="9830d-109">Seçim [Visual Studio 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="9830d-109">(Optional) [Visual Studio 2019](https://visualstudio.microsoft.com/vs/)</span></span>

<span data-ttu-id="9830d-110">Oluşturulan C# kod projelerini Visual Studio ile veya tuşuna basarak `F5` `dotnet run` (.NET Core CLI) çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9830d-110">You can run the generated C# code projects with Visual Studio by pressing the `F5` key or with `dotnet run` (.NET Core CLI).</span></span>

<span data-ttu-id="9830d-111">Not: .NET Core SDK yükledikten sonra `dotnet tool` komut çalışmaz, Windows oturumunu kapatın ve yeniden oturum açın.</span><span class="sxs-lookup"><span data-stu-id="9830d-111">Note: If after installing .NET Core SDK the `dotnet tool` command is not working, sign out from Windows and sign in again.</span></span>

## <a name="install"></a><span data-ttu-id="9830d-112">Yükleme</span><span class="sxs-lookup"><span data-stu-id="9830d-112">Install</span></span>

<span data-ttu-id="9830d-113">ML.NET CLı, diğer DotNet genel aracı gibi yüklenir.</span><span class="sxs-lookup"><span data-stu-id="9830d-113">The ML.NET CLI is installed like any other dotnet Global Tool.</span></span> <span data-ttu-id="9830d-114">`dotnet tool install`.NET Core CLI komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="9830d-114">You use the `dotnet tool install` .NET Core CLI command.</span></span>

<span data-ttu-id="9830d-115">Aşağıdaki örnek, ML.NET CLı 'nın varsayılan NuGet akış konumuna nasıl yükleneceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="9830d-115">The following example shows how to install the ML.NET CLI in the default NuGet feed location:</span></span>

```dotnetcli
dotnet tool install -g mlnet
```

<span data-ttu-id="9830d-116">Araç yüklenemezse (yani, varsayılan NuGet akışında yoksa) hata iletileri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9830d-116">If the tool can't be installed (that is, if it is not available at the default NuGet feed), error messages are displayed.</span></span> <span data-ttu-id="9830d-117">Beklediğiniz akışların denetlendiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="9830d-117">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="9830d-118">Yükleme başarılı olursa, aşağıdaki örneğe benzer şekilde, aracı ve yüklü sürümü çağırmak için kullanılan komutu gösteren bir ileti görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="9830d-118">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```console
You can invoke the tool using the following command: mlnet
Tool 'mlnet' (version 'X.X.X') was successfully installed.
```

<span data-ttu-id="9830d-119">Aşağıdaki komutu yazarak yüklemenin başarılı olduğunu doğrulayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9830d-119">You can confirm the installation was successful by typing the following command:</span></span>

```console
mlnet
```

<span data-ttu-id="9830d-120">' Sınıflandırma ' komutu gibi mlnet aracının kullanılabilir komutları için yardım görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9830d-120">You should see the help for available commands for the mlnet tool such as the 'classification' command.</span></span>

## <a name="install-a-specific-release-version"></a><span data-ttu-id="9830d-121">Belirli bir yayın sürümünü yükler</span><span class="sxs-lookup"><span data-stu-id="9830d-121">Install a specific release version</span></span>

<span data-ttu-id="9830d-122">Bir yayın öncesi sürüm veya aracın belirli bir sürümünü yüklemeye çalışıyorsanız, [çerçeveyi](../../standard/frameworks.md) aşağıdaki biçimi kullanarak belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9830d-122">If you're trying to install a pre-release version or a specific version of the tool, you can specify the [framework](../../standard/frameworks.md) using the following format:</span></span>

```dotnetcli
dotnet tool install -g mlnet --framework <FRAMEWORK>
```

<span data-ttu-id="9830d-123">Ayrıca, aşağıdaki komutu yazarak paketin düzgün yüklenip yüklenmediğini da denetleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9830d-123">You can also check if the package is properly installed by typing the following command:</span></span>

```dotnetcli
dotnet tool list -g
```

## <a name="uninstall-the-cli-package"></a><span data-ttu-id="9830d-124">CLı paketini kaldırma</span><span class="sxs-lookup"><span data-stu-id="9830d-124">Uninstall the CLI package</span></span>

<span data-ttu-id="9830d-125">Paketi yerel makinenizden kaldırmak için aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="9830d-125">Type the following command to uninstall the package from your local machine:</span></span>

```dotnetcli
dotnet tool uninstall mlnet -g
```

## <a name="update-the-cli-package"></a><span data-ttu-id="9830d-126">CLı paketini güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="9830d-126">Update the CLI package</span></span>

<span data-ttu-id="9830d-127">Paketi yerel makinenizden güncelleştirmek için aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="9830d-127">Type the following command to update the package from your local machine:</span></span>

```dotnetcli
dotnet tool update -g mlnet
```

## <a name="set-up-cli-suggestions-tab-based-auto-completion"></a><span data-ttu-id="9830d-128">CLı önerilerini ayarlama (sekme tabanlı otomatik tamamlama)</span><span class="sxs-lookup"><span data-stu-id="9830d-128">Set up CLI suggestions (tab-based auto-completion)</span></span>

<span data-ttu-id="9830d-129">ML.NET CLı tabanlı olduğundan `System.CommandLine` , sekme tamamlama için yerleşik desteğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9830d-129">Since the ML.NET CLI is based on `System.CommandLine`, it has built-in support for tab completion.</span></span>

<span data-ttu-id="9830d-130">Aşağıdaki animasyonda sekme otomatik tamamlama 'nın nasıl çalıştığına bir örnek gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="9830d-130">An example of how tab auto completion works is shown in the following animation:</span></span>

![image](./media/cli-tab-completion.gif)

<span data-ttu-id="9830d-132">' Sekme tabanlı otomatik tamamlama ' (parametre önerileri) *Windows PowerShell* ve *MacOS/Linux Bash* üzerinde çalışır, ancak *Windows cmd*'de çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="9830d-132">'Tab-based auto-completion' (parameter suggestions) works on *Windows PowerShell* and *macOS/Linux bash* but it won't work on *Windows CMD*.</span></span>

<span data-ttu-id="9830d-133">Bu ayarı etkinleştirmek için, geçerli önizleme sürümünde son kullanıcının aşağıda belirtilen her kabuk için birkaç adım olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9830d-133">To enable it, in the current preview version, the end user has to take a few steps once per shell, outlined below.</span></span> <span data-ttu-id="9830d-134">Bu işlem tamamlandıktan sonra, ML.NET CLı gibi kullanılarak yazılan tüm uygulamalar için tamamlama işlemleri çalışacaktır `System.CommandLine` .</span><span class="sxs-lookup"><span data-stu-id="9830d-134">Once this is done, completions will work for all apps written using `System.CommandLine` such as the ML.NET CLI.</span></span>

<span data-ttu-id="9830d-135">Tamamlamayı etkinleştirmek istediğiniz makinede iki şey yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9830d-135">On the machine where you'd like to enable completion, you'll need to do two things.</span></span>

1. <span data-ttu-id="9830d-136">`dotnet-suggest`Aşağıdaki komutu çalıştırarak genel aracı 'nı yüklersiniz:</span><span class="sxs-lookup"><span data-stu-id="9830d-136">Install the `dotnet-suggest` global tool by running the following command:</span></span>

    ```dotnetcli
    dotnet tool install dotnet-suggest -g
    ```

2. <span data-ttu-id="9830d-137">Kabuk profilinize uygun dolgu betiğini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9830d-137">Add the appropriate shim script to your shell profile.</span></span> <span data-ttu-id="9830d-138">Bir kabuk profili dosyası oluşturmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="9830d-138">You may have to create a shell profile file.</span></span> <span data-ttu-id="9830d-139">Dolgu betiği, kabuğunuzun tamamlanma isteklerini `dotnet-suggest` , uygun tabanlı uygulamaya temsilci olan bir araca iletir `System.CommandLine` .</span><span class="sxs-lookup"><span data-stu-id="9830d-139">The shim script will forward completion requests from your shell to the `dotnet-suggest` tool, which delegates to the appropriate `System.CommandLine`-based app.</span></span>

    - <span data-ttu-id="9830d-140">Bash için [DotNet-öner-Shim. bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) içeriğini ' ye ekleyin `~/.bash_profile` .</span><span class="sxs-lookup"><span data-stu-id="9830d-140">For bash, add the contents of [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) to `~/.bash_profile`.</span></span>

    - <span data-ttu-id="9830d-141">PowerShell için, [DotNet-Suggest-Shim. ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) içeriğini PowerShell profilinize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9830d-141">For PowerShell, add the contents of [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) to your PowerShell profile.</span></span> <span data-ttu-id="9830d-142">Konsolunda aşağıdaki komutu çalıştırarak, PowerShell profilinize beklenen yolu bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9830d-142">You can find the expected path to your PowerShell profile by running the following command in your console:</span></span>

    ```console
    echo $profile
    ```

<span data-ttu-id="9830d-143">(Diğer kabuklar için bir [sorun](https://github.com/dotnet/System.CommandLine/issues) [bulun](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) veya açın.)</span><span class="sxs-lookup"><span data-stu-id="9830d-143">(For other shells, [look for](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) or open an [issue](https://github.com/dotnet/System.CommandLine/issues).)</span></span>

## <a name="installation-directory"></a><span data-ttu-id="9830d-144">Yükleme dizini</span><span class="sxs-lookup"><span data-stu-id="9830d-144">Installation directory</span></span>

<span data-ttu-id="9830d-145">ML.NET CLı varsayılan dizine veya belirli bir konuma yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="9830d-145">The ML.NET CLI can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="9830d-146">Varsayılan dizinler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="9830d-146">The default directories are:</span></span>

| <span data-ttu-id="9830d-147">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="9830d-147">OS</span></span>          | <span data-ttu-id="9830d-148">Yol</span><span class="sxs-lookup"><span data-stu-id="9830d-148">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="9830d-149">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="9830d-149">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="9830d-150">Windows</span><span class="sxs-lookup"><span data-stu-id="9830d-150">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="9830d-151">Bu konumlar, SDK ilk kez çalıştırıldığında kullanıcının yoluna eklenir, bu nedenle genel araçlar yüklenir, böylece doğrudan çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="9830d-151">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="9830d-152">Not: genel araçlar, makineye genel değil, kullanıcıya özeldir.</span><span class="sxs-lookup"><span data-stu-id="9830d-152">Note: the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="9830d-153">Kullanıcıya özel olması, makinenin tüm kullanıcıları için kullanılabilir olan küresel bir araç yükleyemeyeceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9830d-153">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="9830d-154">Araç yalnızca aracın yüklendiği her kullanıcı profili için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9830d-154">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="9830d-155">Genel araçlar, belirli bir dizine de yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="9830d-155">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="9830d-156">Belirli bir dizine yüklendiğinde, kullanıcının, yolu belirtilen dizin ile çağırarak veya aracı belirtilen dizin içinden çağırarak, bu dizini da dahil ederek komutun kullanılabilir olduğundan emin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9830d-156">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="9830d-157">Bu durumda .NET Core CLI, bu konumu otomatik olarak PATH ortam değişkenine eklemez.</span><span class="sxs-lookup"><span data-stu-id="9830d-157">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="9830d-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9830d-158">See also</span></span>

- [<span data-ttu-id="9830d-159">ML.NET CLı genel bakış</span><span class="sxs-lookup"><span data-stu-id="9830d-159">ML.NET CLI overview</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="9830d-160">Öğretici: ML.NET CLı ile yaklaşımı çözümleme</span><span class="sxs-lookup"><span data-stu-id="9830d-160">Tutorial: Analyze sentiment with the ML.NET CLI</span></span>](../tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="9830d-161">ML.NET CLı otomatik eğitme komut başvuru kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9830d-161">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="9830d-162">ML.NET CLı 'de telemetri</span><span class="sxs-lookup"><span data-stu-id="9830d-162">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
