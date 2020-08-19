---
title: .NET Core araç kullanımı sorunlarını giderme
description: .NET Core araçları ve olası çözümleri çalıştırırken sık karşılaşılan sorunları öğrenin.
author: kdollard
ms.topic: troubleshooting
ms.date: 02/14/2020
ms.openlocfilehash: db88958e1605fef589c5dbcb12065a6318183705
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608318"
---
# <a name="troubleshoot-net-core-tool-usage-issues"></a><span data-ttu-id="4da2a-103">.NET Core araç kullanımı sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="4da2a-103">Troubleshoot .NET Core tool usage issues</span></span>

<span data-ttu-id="4da2a-104">Küresel bir araç veya yerel araç olabilecek bir .NET Core aracını yüklemeye veya çalıştırmaya çalışırken sorunlarla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4da2a-104">You might come across issues when trying to install or run a .NET Core tool, which can be a global tool or a local tool.</span></span> <span data-ttu-id="4da2a-105">Bu makalede, yaygın temel nedenler ve bazı olası çözümler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4da2a-105">This article describes the common root causes and some possible solutions.</span></span>

## <a name="installed-net-core-tool-fails-to-run"></a><span data-ttu-id="4da2a-106">Yüklü .NET Core aracı çalıştırılamıyor</span><span class="sxs-lookup"><span data-stu-id="4da2a-106">Installed .NET Core tool fails to run</span></span>

<span data-ttu-id="4da2a-107">Bir .NET Core aracı çalışamazsa, büyük olasılıkla aşağıdaki sorunlardan biriyle karşılaşdınız:</span><span class="sxs-lookup"><span data-stu-id="4da2a-107">When a .NET Core tool fails to run, most likely you ran into one of the following issues:</span></span>

* <span data-ttu-id="4da2a-108">Aracın yürütülebilir dosyası bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="4da2a-108">The executable file for the tool wasn't found.</span></span>
* <span data-ttu-id="4da2a-109">.NET Core çalışma zamanının doğru sürümü bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="4da2a-109">The correct version of the .NET Core runtime wasn't found.</span></span>

### <a name="executable-file-not-found"></a><span data-ttu-id="4da2a-110">Yürütülebilir dosya bulunamadı</span><span class="sxs-lookup"><span data-stu-id="4da2a-110">Executable file not found</span></span>

<span data-ttu-id="4da2a-111">Yürütülebilir dosya bulunamazsa aşağıdakine benzer bir ileti görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="4da2a-111">If the executable file isn't found, you'll see a message similar to the following:</span></span>

```console
Could not execute because the specified command or file was not found.
Possible reasons for this include:
  * You misspelled a built-in dotnet command.
  * You intended to execute a .NET Core program, but dotnet-xyz does not exist.
  * You intended to run a global tool, but a dotnet-prefixed executable with this name could not be found on the PATH.
```

<span data-ttu-id="4da2a-112">Yürütülebilir dosyanın adı, aracı nasıl çağırabileceğinizi belirler.</span><span class="sxs-lookup"><span data-stu-id="4da2a-112">The name of the executable determines how you invoke the tool.</span></span> <span data-ttu-id="4da2a-113">Aşağıdaki tabloda şu biçim açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="4da2a-113">The following table describes the format:</span></span>

| <span data-ttu-id="4da2a-114">Yürütülebilir dosya adı biçimi</span><span class="sxs-lookup"><span data-stu-id="4da2a-114">Executable name format</span></span>  | <span data-ttu-id="4da2a-115">Çağırma biçimi</span><span class="sxs-lookup"><span data-stu-id="4da2a-115">Invocation format</span></span>   |
|-------------------------|---------------------|
| `dotnet-<toolName>.exe` | `dotnet <toolName>` |
| `<toolName>.exe`        | `<toolName>`        |

* <span data-ttu-id="4da2a-116">Genel araçlar</span><span class="sxs-lookup"><span data-stu-id="4da2a-116">Global tools</span></span>

  <span data-ttu-id="4da2a-117">Genel araçlar varsayılan dizine veya belirli bir konuma yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="4da2a-117">Global tools can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="4da2a-118">Varsayılan dizinler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="4da2a-118">The default directories are:</span></span>

  | <span data-ttu-id="4da2a-119">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="4da2a-119">OS</span></span>          | <span data-ttu-id="4da2a-120">Yol</span><span class="sxs-lookup"><span data-stu-id="4da2a-120">Path</span></span>                          |
  |-------------|-------------------------------|
  | <span data-ttu-id="4da2a-121">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="4da2a-121">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
  | <span data-ttu-id="4da2a-122">Windows</span><span class="sxs-lookup"><span data-stu-id="4da2a-122">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

  <span data-ttu-id="4da2a-123">Küresel bir araç çalıştırmaya çalışıyorsanız, `PATH` makinenizde ortam değişkeninin genel aracı yüklediğiniz yolu içerdiğini ve yürütülebilir dosyanın o yolda olduğunu kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="4da2a-123">If you're trying to run a global tool, check that the `PATH` environment variable on your machine contains the path where you installed the global tool and that the executable is in that path.</span></span>

  <span data-ttu-id="4da2a-124">.NET Core CLI, ilk kullanımındaki yol ortam değişkenine varsayılan konumu eklemeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="4da2a-124">The .NET Core CLI tries to add the default location to the PATH environment variable on its first usage.</span></span> <span data-ttu-id="4da2a-125">Ancak, konumun yola otomatik olarak eklenmeyebilir bazı senaryolar vardır:</span><span class="sxs-lookup"><span data-stu-id="4da2a-125">However, there are some scenarios where the location might not be added to PATH automatically:</span></span>

  * <span data-ttu-id="4da2a-126">Linux kullanıyorsanız ve *. tar. gz* dosyalarını kullanarak .NET Core SDK yüklediyseniz ve apt-get veya rpm değil.</span><span class="sxs-lookup"><span data-stu-id="4da2a-126">If you're using Linux and you've installed the .NET Core SDK using *.tar.gz* files and not apt-get or rpm.</span></span>
  * <span data-ttu-id="4da2a-127">MacOS 10,15 "Catalina" veya sonraki sürümlerini kullanıyorsanız.</span><span class="sxs-lookup"><span data-stu-id="4da2a-127">If you're using macOS 10.15 "Catalina" or later versions.</span></span>
  * <span data-ttu-id="4da2a-128">MacOS 10,14 "Mojave" veya önceki sürümlerini kullanıyorsanız ve. *pkg*değil. *tar. gz* dosyalarını kullanarak .NET Core SDK yüklediyseniz.</span><span class="sxs-lookup"><span data-stu-id="4da2a-128">If you're using macOS 10.14 "Mojave" or earlier versions, and you've installed the .NET Core SDK using *.tar.gz* files and not *.pkg*.</span></span>
  * <span data-ttu-id="4da2a-129">.NET Core 3,0 SDK 'sını yüklediyseniz ve `DOTNET_ADD_GLOBAL_TOOLS_TO_PATH` ortam değişkenini olarak ayarladıysanız `false` .</span><span class="sxs-lookup"><span data-stu-id="4da2a-129">If you've installed the .NET Core 3.0 SDK and you've set the `DOTNET_ADD_GLOBAL_TOOLS_TO_PATH` environment variable to `false`.</span></span>
  * <span data-ttu-id="4da2a-130">.NET Core 2,2 SDK veya önceki sürümlerini yüklediyseniz ve `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` ortam değişkenini olarak ayarladıysanız `true` .</span><span class="sxs-lookup"><span data-stu-id="4da2a-130">If you've installed .NET Core 2.2 SDK or earlier versions, and you've set the `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` environment variable to `true`.</span></span>

  <span data-ttu-id="4da2a-131">Bu senaryolarda veya `--tool-path` seçeneğini belirlediyseniz, `PATH` makinenizde ortam değişkeni, genel aracı yüklediğiniz yolu otomatik olarak içermez.</span><span class="sxs-lookup"><span data-stu-id="4da2a-131">In these scenarios or if you specified the `--tool-path` option, the `PATH` environment variable on your machine doesn't automatically contain the path where you installed the global tool.</span></span> <span data-ttu-id="4da2a-132">Bu durumda, `$HOME/.dotnet/tools` `PATH` kabuğunuzun ortam değişkenlerini güncelleştirmek için sağladığı yöntemi kullanarak araç konumunu (örneğin,) ortam değişkenine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4da2a-132">In that case, append the tool location (for example, `$HOME/.dotnet/tools`) to the `PATH` environment variable by using whatever method your shell provides for updating environment variables.</span></span> <span data-ttu-id="4da2a-133">Daha fazla bilgi için bkz. [.NET Core araçları](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="4da2a-133">For more information, see [.NET Core tools](global-tools.md).</span></span>

* <span data-ttu-id="4da2a-134">Yerel Araçlar</span><span class="sxs-lookup"><span data-stu-id="4da2a-134">Local tools</span></span>

  <span data-ttu-id="4da2a-135">Yerel bir araç çalıştırmaya çalışıyorsanız, geçerli dizinde veya onun üst dizinlerinde *dotnet-tools.js* adlı bir bildirim dosyası olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="4da2a-135">If you're trying to run a local tool, verify that there's a manifest file called *dotnet-tools.json* in the current directory or any of its parent directories.</span></span> <span data-ttu-id="4da2a-136">Bu dosya Ayrıca, kök klasör yerine proje klasörü hiyerarşisinde *. config* adlı bir klasör altında da bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="4da2a-136">This file can also live under a folder named *.config* anywhere in the project folder hierarchy, instead of the root folder.</span></span> <span data-ttu-id="4da2a-137">*dotnet-tools.js* varsa, açın ve çalıştırmaya çalıştığınız aracı denetleyin.</span><span class="sxs-lookup"><span data-stu-id="4da2a-137">If *dotnet-tools.json* exists, open it and check for the tool you're trying to run.</span></span> <span data-ttu-id="4da2a-138">Dosya için bir giriş içermiyorsa `"isRoot": true` , ek araç bildirim dosyaları için de dosya hiyerarşisini daha da denetleyin.</span><span class="sxs-lookup"><span data-stu-id="4da2a-138">If the file doesn't contain an entry for `"isRoot": true`, then also check further up the file hierarchy for additional tool manifest files.</span></span>

  <span data-ttu-id="4da2a-139">Belirtilen bir yol ile yüklenmiş bir .NET Core aracını çalıştırmaya çalışıyorsanız, aracı kullanırken bu yolu eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4da2a-139">If you're trying to run a .NET Core tool that was installed with a specified path, you need to include that path when using the tool.</span></span> <span data-ttu-id="4da2a-140">Araç yolu yüklü aracının kullanılmasına bir örnek:</span><span class="sxs-lookup"><span data-stu-id="4da2a-140">An example of using a tool-path installed tool is:</span></span>

  ```console
  ..\<toolDirectory>\dotnet-<toolName>
  ```

### <a name="runtime-not-found"></a><span data-ttu-id="4da2a-141">Çalışma zamanı bulunamadı</span><span class="sxs-lookup"><span data-stu-id="4da2a-141">Runtime not found</span></span>

<span data-ttu-id="4da2a-142">.NET Core araçları, [çerçeveye bağlı uygulamalardır](../deploying/index.md#publish-framework-dependent)ve bu, makinenizde yüklü bir .NET Core çalışma zamanına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="4da2a-142">.NET Core tools are [framework-dependent applications](../deploying/index.md#publish-framework-dependent), which means they rely on a .NET Core runtime installed on your machine.</span></span> <span data-ttu-id="4da2a-143">Beklenen çalışma zamanı bulunmazsa, normal .NET Core çalışma zamanı alma-iletme kurallarını izler:</span><span class="sxs-lookup"><span data-stu-id="4da2a-143">If the expected runtime isn't found, they follow normal .NET Core runtime roll-forward rules such as:</span></span>

* <span data-ttu-id="4da2a-144">Bir uygulama, belirtilen birincil ve ikincil sürümün en yüksek düzeltme eki sürümüne ileri kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="4da2a-144">An application rolls forward to the highest patch release of the specified major and minor version.</span></span>
* <span data-ttu-id="4da2a-145">Eşleşen bir ana ve alt sürüm numarasına sahip eşleşen bir çalışma zamanı yoksa, sonraki en düşük sürüm kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4da2a-145">If there's no matching runtime with a matching major and minor version number, the next higher minor version is used.</span></span>
* <span data-ttu-id="4da2a-146">Çalışma zamanının veya önizleme sürümleri ile sürüm sürümlerinin önizleme sürümleri arasında ileri alma gerçekleşmez.</span><span class="sxs-lookup"><span data-stu-id="4da2a-146">Roll forward doesn't occur between preview versions of the runtime or between preview versions and release versions.</span></span> <span data-ttu-id="4da2a-147">Bu nedenle, önizleme sürümleri kullanılarak oluşturulan .NET Core araçlarının, yazar tarafından yeniden oluşturulması ve yeniden yayımlanması ve yeniden yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="4da2a-147">So, .NET Core tools created using preview versions must be rebuilt and republished by the author and reinstalled.</span></span>

<span data-ttu-id="4da2a-148">Geri alma iki yaygın senaryoda varsayılan olarak gerçekleşmez:</span><span class="sxs-lookup"><span data-stu-id="4da2a-148">Roll-forward won't occur by default in two common scenarios:</span></span>

* <span data-ttu-id="4da2a-149">Çalışma zamanının yalnızca alt sürümleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4da2a-149">Only lower versions of the runtime are available.</span></span> <span data-ttu-id="4da2a-150">İlet geri alma yalnızca çalışma zamanının sonraki sürümlerini seçer.</span><span class="sxs-lookup"><span data-stu-id="4da2a-150">Roll-forward only selects later versions of the runtime.</span></span>
* <span data-ttu-id="4da2a-151">Çalışma zamanının yalnızca daha yüksek ana sürümleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4da2a-151">Only higher major versions of the runtime are available.</span></span> <span data-ttu-id="4da2a-152">İlet, büyük sürüm sınırları değildir.</span><span class="sxs-lookup"><span data-stu-id="4da2a-152">Roll-forward doesn't cross major version boundaries.</span></span>

<span data-ttu-id="4da2a-153">Bir uygulama uygun bir çalışma zamanı bulamazsa, çalışmaz ve bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="4da2a-153">If an application can't find an appropriate runtime, it fails to run and reports an error.</span></span>

<span data-ttu-id="4da2a-154">Aşağıdaki komutlardan birini kullanarak makinenizde hangi .NET Core çalışma zamanlarının yüklü olduğunu öğrenebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4da2a-154">You can find out which .NET Core runtimes are installed on your machine using one of the following commands:</span></span>

```dotnetcli
dotnet --list-runtimes
dotnet --info
```

<span data-ttu-id="4da2a-155">Aracın şu anda yüklü olan çalışma zamanı sürümünü desteklemesi gerektiğini düşünüyorsanız, araç yazarıyla iletişim kurun ve sürüm numarasını veya çoklu hedefi güncelleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="4da2a-155">If you think the tool should support the runtime version you currently have installed, you can contact the tool author and see if they can update the version number or multi-target.</span></span> <span data-ttu-id="4da2a-156">Araç paketlerini yeniden derlendikten ve güncelleştirilmiş bir sürüm numarasıyla NuGet 'e yeniden yayınladıktan sonra, kopyanızı güncelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4da2a-156">Once they've recompiled and republished their tool package to NuGet with an updated version number, you can update your copy.</span></span> <span data-ttu-id="4da2a-157">Gerçekleşmediğinden, sizin için en hızlı çözüm, çalıştırmaya çalıştığınız araçla çalışacak çalışma zamanının bir sürümünü yüklemektir.</span><span class="sxs-lookup"><span data-stu-id="4da2a-157">While that doesn't happen, the quickest solution for you is to install a version of the runtime that would work with the tool you're trying to run.</span></span> <span data-ttu-id="4da2a-158">Belirli bir .NET Core çalışma zamanı sürümünü indirmek için [.NET Core indirme sayfasını](https://dotnet.microsoft.com/download/dotnet-core)ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="4da2a-158">To download a specific .NET Core runtime version, visit the [.NET Core download page](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="4da2a-159">.NET Core SDK varsayılan olmayan bir konuma yüklerseniz, ortam değişkenini `DOTNET_ROOT` yürütülebilir dosyayı içeren dizine ayarlamanız gerekir `dotnet` .</span><span class="sxs-lookup"><span data-stu-id="4da2a-159">If you install the .NET Core SDK to a non-default location, you need to set the environment variable `DOTNET_ROOT` to the directory that contains the `dotnet` executable.</span></span>

## <a name="net-core-tool-installation-fails"></a><span data-ttu-id="4da2a-160">.NET Core aracı yüklemesi başarısız oluyor</span><span class="sxs-lookup"><span data-stu-id="4da2a-160">.NET Core tool installation fails</span></span>

<span data-ttu-id="4da2a-161">.NET Core küresel veya yerel bir araç yüklemesinin başarısız olması birkaç nedenden kaynaklanabilir.</span><span class="sxs-lookup"><span data-stu-id="4da2a-161">There are a number of reasons the installation of a .NET Core global or local tool may fail.</span></span> <span data-ttu-id="4da2a-162">Araç yüklemesi başarısız olduğunda aşağıdakine benzer bir ileti görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="4da2a-162">When the tool installation fails, you'll see a message similar to the following one:</span></span>

```console
Tool '{0}' failed to install. This failure may have been caused by:

* You are attempting to install a preview release and did not use the --version option to specify the version.
* A package by this name was found, but it was not a .NET Core tool.
* The required NuGet feed cannot be accessed, perhaps because of an Internet connection problem.
* You mistyped the name of the tool.

For more reasons, including package naming enforcement, visit https://aka.ms/failure-installing-tool
```

<span data-ttu-id="4da2a-163">Bu hataların tanılanmasına yardımcı olmak için, NuGet iletileri önceki iletiyle birlikte doğrudan kullanıcıya gösterilir.</span><span class="sxs-lookup"><span data-stu-id="4da2a-163">To help diagnose these failures, NuGet messages are shown directly to the user, along with the previous message.</span></span> <span data-ttu-id="4da2a-164">NuGet iletisi sorunu belirlemenize yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="4da2a-164">The NuGet message may help you identify the problem.</span></span>

### <a name="package-naming-enforcement"></a><span data-ttu-id="4da2a-165">Paket adlandırma zorlaması</span><span class="sxs-lookup"><span data-stu-id="4da2a-165">Package naming enforcement</span></span>

<span data-ttu-id="4da2a-166">Microsoft, araçların paket KIMLIĞI üzerinde rehberlik değiştirdi, bu da tahmin edilen ada sahip bir dizi araç bulunamamıştır.</span><span class="sxs-lookup"><span data-stu-id="4da2a-166">Microsoft has changed its guidance on the Package ID for tools, resulting in a number of tools not being found with the predicted name.</span></span> <span data-ttu-id="4da2a-167">Yeni kılavuzluk, tüm Microsoft araçlarının ön eki olan "Microsoft"</span><span class="sxs-lookup"><span data-stu-id="4da2a-167">The new guidance is that all Microsoft tools be prefixed with "Microsoft."</span></span> <span data-ttu-id="4da2a-168">Bu ön ek ayrılmıştır ve yalnızca Microsoft yetkili sertifikasıyla imzalanmış paketler için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4da2a-168">This prefix is reserved and can only be used for packages signed with a Microsoft authorized certificate.</span></span>

<span data-ttu-id="4da2a-169">Geçiş sırasında bazı Microsoft araçları paket KIMLIĞI eski biçiminde olacaktır, diğerleri ise yeni biçime sahip olur:</span><span class="sxs-lookup"><span data-stu-id="4da2a-169">During the transition, some Microsoft tools will have the old form of the package ID, while others will have the new form:</span></span>

```dotnetcli
dotnet tool install -g Microsoft.<toolName>
dotnet tool install -g <toolName>
```

<span data-ttu-id="4da2a-170">Paket kimlikleri güncelleştirildiğinden, en son güncelleştirmeleri almak için yeni paket KIMLIĞINE geçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4da2a-170">As package IDs are updated, you'll need to change to the new package ID to get the latest updates.</span></span> <span data-ttu-id="4da2a-171">Basitleştirilmiş araç adına sahip paketler kullanım dışı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="4da2a-171">Packages with the simplified tool name will be deprecated.</span></span>

### <a name="preview-releases"></a><span data-ttu-id="4da2a-172">Önizleme yayınları</span><span class="sxs-lookup"><span data-stu-id="4da2a-172">Preview releases</span></span>

* <span data-ttu-id="4da2a-173">Bir önizleme sürümü yüklemeye çalışıyorsunuz ve `--version` sürümü belirlemek için bu seçeneği kullanmadınız.</span><span class="sxs-lookup"><span data-stu-id="4da2a-173">You're attempting to install a preview release and didn't use the `--version` option to specify the version.</span></span>

<span data-ttu-id="4da2a-174">Önizlemedeki .NET Core araçları, önizlemede olduğunu göstermek için adının bir bölümüyle birlikte belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="4da2a-174">.NET Core tools that are in preview must be specified with a portion of the name to indicate that they are in preview.</span></span> <span data-ttu-id="4da2a-175">Tüm önizlemeyi eklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="4da2a-175">You don't need to include the entire preview.</span></span> <span data-ttu-id="4da2a-176">Sürüm numaralarının beklenen biçimde olduğu varsayılarak, aşağıdaki örneğe benzer bir şey kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4da2a-176">Assuming the version numbers are in the expected format, you can use something like the following example:</span></span>

```dotnetcli
dotnet tool install -g --version 1.1.0-pre <toolName>
```

### <a name="package-isnt-a-net-core-tool"></a><span data-ttu-id="4da2a-177">Paket bir .NET Core aracı değil</span><span class="sxs-lookup"><span data-stu-id="4da2a-177">Package isn't a .NET Core tool</span></span>

* <span data-ttu-id="4da2a-178">Bu ada sahip bir NuGet paketi bulundu, ancak bir .NET Core aracı değildi.</span><span class="sxs-lookup"><span data-stu-id="4da2a-178">A NuGet package by this name was found, but it wasn't a .NET Core tool.</span></span>

<span data-ttu-id="4da2a-179">.NET Core aracı olmayan düzenli bir NuGet paketi olan bir NuGet paketini yüklemeye çalışırsanız, aşağıdakine benzer bir hata görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="4da2a-179">If you try to install a NuGet package that is a regular NuGet package and not a .NET Core tool, you'll see an error similar to the following:</span></span>

> <span data-ttu-id="4da2a-180">NU1212: için geçersiz proje-Package birleşimi `<ToolName>` .</span><span class="sxs-lookup"><span data-stu-id="4da2a-180">NU1212: Invalid project-package combination for `<ToolName>`.</span></span> <span data-ttu-id="4da2a-181">DotnetToolReference proje stili yalnızca DotnetTool türündeki başvuruları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="4da2a-181">DotnetToolReference project style can only contain references of the DotnetTool type.</span></span>

### <a name="nuget-feed-cant-be-accessed"></a><span data-ttu-id="4da2a-182">NuGet akışına erişilemiyor</span><span class="sxs-lookup"><span data-stu-id="4da2a-182">NuGet feed can't be accessed</span></span>

* <span data-ttu-id="4da2a-183">Olası bir Internet bağlantısı sorunu nedeniyle, gerekli NuGet akışına erişilemiyor.</span><span class="sxs-lookup"><span data-stu-id="4da2a-183">The required NuGet feed can't be accessed, perhaps because of an Internet connection problem.</span></span>

<span data-ttu-id="4da2a-184">Araç yüklemesi için araç paketini içeren NuGet akışına erişim gerekir.</span><span class="sxs-lookup"><span data-stu-id="4da2a-184">Tool installation requires access to the NuGet feed that contains the tool package.</span></span> <span data-ttu-id="4da2a-185">Akış kullanılamıyorsa başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="4da2a-185">It fails if the feed isn't available.</span></span> <span data-ttu-id="4da2a-186">Akışları ile değiştirebilir `nuget.config` , belirli bir `nuget.config` dosya isteyebilir veya anahtarla ek akışlar belirtebilirsiniz `--add-source` .</span><span class="sxs-lookup"><span data-stu-id="4da2a-186">You can alter feeds with `nuget.config`, request a specific `nuget.config` file, or specify additional feeds with the `--add-source` switch.</span></span> <span data-ttu-id="4da2a-187">NuGet, varsayılan olarak, bağlanamaan herhangi bir akış için bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4da2a-187">By default, NuGet throws an error for any feed that can't connect.</span></span> <span data-ttu-id="4da2a-188">Bayrak, `--ignore-failed-sources` Bu ulaşılabilir olmayan kaynakları atlayabilir.</span><span class="sxs-lookup"><span data-stu-id="4da2a-188">The flag `--ignore-failed-sources` can skip these non-reachable sources.</span></span>

### <a name="package-id-incorrect"></a><span data-ttu-id="4da2a-189">Paket KIMLIĞI yanlış</span><span class="sxs-lookup"><span data-stu-id="4da2a-189">Package ID incorrect</span></span>

* <span data-ttu-id="4da2a-190">Aracın adını yanlış yazmış olursunuz.</span><span class="sxs-lookup"><span data-stu-id="4da2a-190">You mistyped the name of the tool.</span></span>

<span data-ttu-id="4da2a-191">Hatanın yaygın bir nedeni, araç adının doğru olmaması.</span><span class="sxs-lookup"><span data-stu-id="4da2a-191">A common reason for failure is that the tool name isn't correct.</span></span> <span data-ttu-id="4da2a-192">Bu, yanlış yazma veya araç taşınmış ya da kullanım dışı olduğu için oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="4da2a-192">This can happen because of mistyping, or because the tool has moved or been deprecated.</span></span> <span data-ttu-id="4da2a-193">NuGet.org üzerinde Araçlar için, adın doğru olduğundan emin olmanın bir yolu, NuGet.org adresinde aracı aramak ve yükleme komutunu kopyalamaktır.</span><span class="sxs-lookup"><span data-stu-id="4da2a-193">For tools on NuGet.org, one way to ensure you have the name correct is to search for the tool at NuGet.org and copy the installation command.</span></span>

## <a name="see-also"></a><span data-ttu-id="4da2a-194">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4da2a-194">See also</span></span>

* [<span data-ttu-id="4da2a-195">.NET Core araçları</span><span class="sxs-lookup"><span data-stu-id="4da2a-195">.NET Core tools</span></span>](global-tools.md)
