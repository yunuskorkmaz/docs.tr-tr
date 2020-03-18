---
title: komut-line arabirimi (CLI) aracıML.NET nasıl yüklenir?
description: ML.NET komut satırı arabirimi (CLI) aracını nasıl yükleyip yükseltecek, düşürecek ve kaldırabilirsiniz öğrenin.
ms.date: 12/18/2019
ms.custom: mlnet-tooling
ms.openlocfilehash: 9f678c7117d32bf817139951db7eef2c3d0f5eb2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78848645"
---
# <a name="how-to-install-the-mlnet-command-line-interface-cli-tool"></a><span data-ttu-id="ece21-103">komut-line arabirimi (CLI) aracıML.NET nasıl yüklenir?</span><span class="sxs-lookup"><span data-stu-id="ece21-103">How to install the ML.NET Command-Line Interface (CLI) tool</span></span>

<span data-ttu-id="ece21-104">CLI(komut satırı arabirimi) ML.NET Windows, Mac veya Linux'a nasıl yükleyin.</span><span class="sxs-lookup"><span data-stu-id="ece21-104">Learn how to install the ML.NET CLI (command-line interface) on Windows, Mac, or Linux.</span></span>

<span data-ttu-id="ece21-105">CLI ML.NET, otomatik makine öğrenimi (AutoML) ve eğitim veri seti kullanarak kaliteli ML.NET modeller ve kaynak kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ece21-105">The ML.NET CLI generates good quality ML.NET models and source code using automated machine learning (AutoML) and a training dataset.</span></span>

> [!NOTE]
> <span data-ttu-id="ece21-106">Bu konu, şu anda Önizleme'de olan cli ve ML.NET AutoML'ML.NET anlamına gelir ve malzeme değişebilir.</span><span class="sxs-lookup"><span data-stu-id="ece21-106">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="ece21-107">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="ece21-107">Pre-requisites</span></span>

- [<span data-ttu-id="ece21-108">.NET Çekirdek 2.2 SDK</span><span class="sxs-lookup"><span data-stu-id="ece21-108">.NET Core 2.2 SDK</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)

- <span data-ttu-id="ece21-109">(İsteğe bağlı) [Visual Studio 2017 veya 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="ece21-109">(Optional) [Visual Studio 2017 or 2019](https://visualstudio.microsoft.com/vs/)</span></span>

<span data-ttu-id="ece21-110">Oluşturulan C# kod projelerini Visual Studio ile `F5` tuşa `dotnet run` basarak veya (.NET Core CLI) ile çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ece21-110">You can run the generated C# code projects with Visual Studio by pressing the `F5` key or with `dotnet run` (.NET Core CLI).</span></span>

<span data-ttu-id="ece21-111">Not: [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) komutu `dotnet tool` çalışmıyorsa, Windows'tan oturum açın ve yeniden oturum açın.</span><span class="sxs-lookup"><span data-stu-id="ece21-111">Note: If after installing [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) the `dotnet tool` command is not working, sign out from Windows and sign in again.</span></span>

## <a name="install"></a><span data-ttu-id="ece21-112">Yükleme</span><span class="sxs-lookup"><span data-stu-id="ece21-112">Install</span></span>

<span data-ttu-id="ece21-113">cli ML.NET diğer dotnet Global Tool gibi yüklenir.</span><span class="sxs-lookup"><span data-stu-id="ece21-113">The ML.NET CLI is installed like any other dotnet Global Tool.</span></span> <span data-ttu-id="ece21-114">.NET `dotnet tool install` Core CLI komutunu kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="ece21-114">You use the `dotnet tool install` .NET Core CLI command.</span></span>

<span data-ttu-id="ece21-115">Aşağıdaki örnekte, varsayılan NuGet akış konumunda cli ML.NET nasıl yüklenir:</span><span class="sxs-lookup"><span data-stu-id="ece21-115">The following example shows how to install the ML.NET CLI in the default NuGet feed location:</span></span>

```dotnetcli
dotnet tool install -g mlnet
```

<span data-ttu-id="ece21-116">Araç yüklenemezse (diğer bir zamanda varsayılan NuGet akışında kullanılamıyorsa), hata iletileri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ece21-116">If the tool can't be installed (that is, if it is not available at the default NuGet feed), error messages are displayed.</span></span> <span data-ttu-id="ece21-117">Beklediğiniz özet akışlarının kontrol edilebilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ece21-117">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="ece21-118">Yükleme başarılı olursa, aracı aramak için kullanılan komutu ve aşağıdaki örneğe benzer şekilde yüklenen sürümü gösteren bir ileti görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="ece21-118">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```console
You can invoke the tool using the following command: mlnet
Tool 'mlnet' (version 'X.X.X') was successfully installed.
```

<span data-ttu-id="ece21-119">Yüklemenin başarılı olduğunu aşağıdaki komutu yazarak onaylayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ece21-119">You can confirm the installation was successful by typing the following command:</span></span>

```console
mlnet
```

<span data-ttu-id="ece21-120">'Otomatik tren' komutu gibi mlnet aracı için kullanılabilir komutlar için yardım görmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="ece21-120">You should see the help for available commands for the mlnet tool such as the 'auto-train' command.</span></span>

## <a name="install-a-specific-release-version"></a><span data-ttu-id="ece21-121">Belirli bir sürüm sürümünü yükleme</span><span class="sxs-lookup"><span data-stu-id="ece21-121">Install a specific release version</span></span>

<span data-ttu-id="ece21-122">Bir ön sürüm sürümünü veya aracın belirli bir sürümünü yüklemeye çalışıyorsanız, aşağıdaki biçimi kullanarak [çerçeveyi](../../standard/frameworks.md) belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ece21-122">If you're trying to install a pre-release version or a specific version of the tool, you can specify the [framework](../../standard/frameworks.md) using the following format:</span></span>

```dotnetcli
dotnet tool install -g mlnet --framework <FRAMEWORK>
```

<span data-ttu-id="ece21-123">Paketin düzgün yüklenip yüklenmediğinizi aşağıdaki komutu yazarak da kontrol edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ece21-123">You can also check if the package is properly installed by typing the following command:</span></span>

```dotnetcli
dotnet tool list -g
```

## <a name="uninstall-the-cli-package"></a><span data-ttu-id="ece21-124">CLI paketini kaldırın</span><span class="sxs-lookup"><span data-stu-id="ece21-124">Uninstall the CLI package</span></span>

<span data-ttu-id="ece21-125">Paketi yerel makinenizden kaldırmak için aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="ece21-125">Type the following command to uninstall the package from your local machine:</span></span>

```dotnetcli
dotnet tool uninstall mlnet -g
```

## <a name="update-the-cli-package"></a><span data-ttu-id="ece21-126">CLI paketini güncelleştirin</span><span class="sxs-lookup"><span data-stu-id="ece21-126">Update the CLI package</span></span>

<span data-ttu-id="ece21-127">Paketi yerel makinenizden güncelleştirmek için aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="ece21-127">Type the following command to update the package from your local machine:</span></span>

```dotnetcli
dotnet tool update -g mlnet
```

## <a name="set-up-cli-suggestions-tab-based-auto-completion"></a><span data-ttu-id="ece21-128">CLI önerilerini ayarlama (sekme tabanlı otomatik tamamlama)</span><span class="sxs-lookup"><span data-stu-id="ece21-128">Set up CLI suggestions (tab-based auto-completion)</span></span>

<span data-ttu-id="ece21-129">cli ML.NET dayandığı `System.CommandLine`için, sekme tamamlanması için yerleşik desteği vardır.</span><span class="sxs-lookup"><span data-stu-id="ece21-129">Since the ML.NET CLI is based on `System.CommandLine`, it has built-in support for tab completion.</span></span>

<span data-ttu-id="ece21-130">Sekme otomatik tamamlamanın nasıl çalıştığına bir örnek aşağıdaki animasyonda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="ece21-130">An example of how tab auto completion works is shown in the following animation:</span></span>

![image](./media/cli-tab-completion.gif)

<span data-ttu-id="ece21-132">'Sekme tabanlı otomatik tamamlama' (parametre önerileri) *Windows PowerShell* ve *macOS/Linux bash* üzerinde çalışır ancak *Windows CMD*üzerinde çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="ece21-132">'Tab-based auto-completion' (parameter suggestions) works on *Windows PowerShell* and *macOS/Linux bash* but it won't work on *Windows CMD*.</span></span>

<span data-ttu-id="ece21-133">Etkinleştirmek için, geçerli önizleme sürümünde, son kullanıcının kabuk başına bir kez birkaç adım atması gerekir, aşağıda özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="ece21-133">To enable it, in the current preview version, the end user has to take a few steps once per shell, outlined below.</span></span> <span data-ttu-id="ece21-134">Bu işlem tamamlandıktan sonra, cli ML.NET `System.CommandLine` gibi tüm uygulamalar için çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="ece21-134">Once this is done, completions will work for all apps written using `System.CommandLine` such as the ML.NET CLI.</span></span>

<span data-ttu-id="ece21-135">Tamamlanmasını sağlamak istediğiniz makinede iki şey yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ece21-135">On the machine where you'd like to enable completion, you'll need to do two things.</span></span>

1. <span data-ttu-id="ece21-136">Aşağıdaki `dotnet-suggest` komutu çalıştırarak genel aracı yükleyin:</span><span class="sxs-lookup"><span data-stu-id="ece21-136">Install the `dotnet-suggest` global tool by running the following command:</span></span>

    ```dotnetcli
    dotnet tool install dotnet-suggest -g
    ```

2. <span data-ttu-id="ece21-137">Kabuk profilinize uygun şim komut dosyasını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ece21-137">Add the appropriate shim script to your shell profile.</span></span> <span data-ttu-id="ece21-138">Bir kabuk profil dosyası oluşturmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="ece21-138">You may have to create a shell profile file.</span></span> <span data-ttu-id="ece21-139">Şim komut dosyası, tamamlanma isteklerini `dotnet-suggest` kabuğunuzdan uygun `System.CommandLine`tabanlı uygulamaya temsilci olarak sunan araca iletir.</span><span class="sxs-lookup"><span data-stu-id="ece21-139">The shim script will forward completion requests from your shell to the `dotnet-suggest` tool, which delegates to the appropriate `System.CommandLine`-based app.</span></span>

    - <span data-ttu-id="ece21-140">Bash için, `~/.bash_profile` [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) içeriğini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ece21-140">For bash, add the contents of [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) to `~/.bash_profile`.</span></span>

    - <span data-ttu-id="ece21-141">PowerShell için, PowerShell profilinize [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) içeriğini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ece21-141">For PowerShell, add the contents of [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) to your PowerShell profile.</span></span> <span data-ttu-id="ece21-142">Konsolunuzda aşağıdaki komutu çalıştırarak PowerShell profilinize beklenen yolu bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ece21-142">You can find the expected path to your PowerShell profile by running the following command in your console:</span></span>

    ```console
    echo $profile
    ```

<span data-ttu-id="ece21-143">(Diğer kabuklar [için](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) bir [sorun](https://github.com/dotnet/System.CommandLine/issues)arayın veya açın.)</span><span class="sxs-lookup"><span data-stu-id="ece21-143">(For other shells, [look for](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) or open an [issue](https://github.com/dotnet/System.CommandLine/issues).)</span></span>

## <a name="installation-directory"></a><span data-ttu-id="ece21-144">Kurulum dizini</span><span class="sxs-lookup"><span data-stu-id="ece21-144">Installation directory</span></span>

<span data-ttu-id="ece21-145">CLI ML.NET varsayılan dizine veya belirli bir konuma yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="ece21-145">The ML.NET CLI can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="ece21-146">Varsayılan dizinler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ece21-146">The default directories are:</span></span>

| <span data-ttu-id="ece21-147">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="ece21-147">OS</span></span>          | <span data-ttu-id="ece21-148">Yol</span><span class="sxs-lookup"><span data-stu-id="ece21-148">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="ece21-149">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="ece21-149">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="ece21-150">Windows</span><span class="sxs-lookup"><span data-stu-id="ece21-150">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="ece21-151">Bu konumlar, SDK ilk çalıştırıldığında kullanıcının yoluna eklenir, bu nedenle burada yüklenilen Global Araçlar doğrudan çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="ece21-151">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="ece21-152">Not: Genel Araçlar kullanıcıya özeldir, makine geneli değildir.</span><span class="sxs-lookup"><span data-stu-id="ece21-152">Note: the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="ece21-153">Kullanıcıya özel olmak, makinenin tüm kullanıcıları tarafından kullanılabilen bir Global Tool yükleyemeyeceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ece21-153">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="ece21-154">Araç yalnızca aracın yüklendiği her kullanıcı profili için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ece21-154">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="ece21-155">Genel Araçlar belirli bir dizine de yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="ece21-155">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="ece21-156">Belirli bir dizine yüklendiğinde, kullanıcı, bu dizini yola ekleyerek, komutu belirtilen dizini çağırarak veya aracı belirtilen dizinin içinden arayarak komutun kullanılabilir olduğundan emin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ece21-156">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="ece21-157">Bu durumda, .NET Core CLI bu konumu OTOMATIK olarak PATH ortamı değişkenine eklemez.</span><span class="sxs-lookup"><span data-stu-id="ece21-157">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="ece21-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ece21-158">See also</span></span>

- [<span data-ttu-id="ece21-159">ML.NET CLI genel bakış</span><span class="sxs-lookup"><span data-stu-id="ece21-159">ML.NET CLI overview</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="ece21-160">Öğretici: cli ML.NET ile duyguları analiz edin</span><span class="sxs-lookup"><span data-stu-id="ece21-160">Tutorial: Analyze sentiment with the ML.NET CLI</span></span>](../tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="ece21-161">ML.NET CLI otomatik tren komutu başvuru kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ece21-161">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="ece21-162">ML.NET CLI'de telemetri</span><span class="sxs-lookup"><span data-stu-id="ece21-162">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
