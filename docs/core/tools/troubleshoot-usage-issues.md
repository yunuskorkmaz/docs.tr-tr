---
title: Sorun Giderme .NET Core araç kullanım sorunları
description: .NET Core araçlarını ve olası çözümleri çalıştırırken sık karşılaşılan sorunları keşfedin.
author: kdollard
ms.date: 02/14/2020
ms.openlocfilehash: ed6243f802c4d3ce56a742916a1a28676e3cd876
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146456"
---
# <a name="troubleshoot-net-core-tool-usage-issues"></a><span data-ttu-id="727be-103">Sorun Giderme .NET Core araç kullanım sorunları</span><span class="sxs-lookup"><span data-stu-id="727be-103">Troubleshoot .NET Core tool usage issues</span></span>

<span data-ttu-id="727be-104">Genel bir araç veya yerel bir araç olabilecek bir .NET Core aracını yüklemeye veya çalıştırmaya çalışırken sorunlarla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="727be-104">You might come across issues when trying to install or run a .NET Core tool, which can be a global tool or a local tool.</span></span> <span data-ttu-id="727be-105">Bu makalede, ortak kök nedenleri ve bazı olası çözümler açıklanır.</span><span class="sxs-lookup"><span data-stu-id="727be-105">This article describes the common root causes and some possible solutions.</span></span>

## <a name="installed-net-core-tool-fails-to-run"></a><span data-ttu-id="727be-106">Yüklü .NET Core aracı çalışmaz</span><span class="sxs-lookup"><span data-stu-id="727be-106">Installed .NET Core tool fails to run</span></span>

<span data-ttu-id="727be-107">Bir .NET Core aracı çalışmadığında, büyük olasılıkla aşağıdaki sorunlardan biriyle karşılaştınız:</span><span class="sxs-lookup"><span data-stu-id="727be-107">When a .NET Core tool fails to run, most likely you ran into one of the following issues:</span></span>

* <span data-ttu-id="727be-108">Araç için çalıştırılabilir dosya bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="727be-108">The executable file for the tool wasn't found.</span></span>
* <span data-ttu-id="727be-109">.NET Core çalışma zamanının doğru sürümü bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="727be-109">The correct version of the .NET Core runtime wasn't found.</span></span>

### <a name="executable-file-not-found"></a><span data-ttu-id="727be-110">Çalıştırılabilir dosya bulunamadı</span><span class="sxs-lookup"><span data-stu-id="727be-110">Executable file not found</span></span>

<span data-ttu-id="727be-111">Çalıştırılabilir dosya bulunamazsa, aşağıdakilere benzer bir ileti görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="727be-111">If the executable file isn't found, you'll see a message similar to the following:</span></span>

```console
Could not execute because the specified command or file was not found.
Possible reasons for this include:
  * You misspelled a built-in dotnet command.
  * You intended to execute a .NET Core program, but dotnet-xyz does not exist.
  * You intended to run a global tool, but a dotnet-prefixed executable with this name could not be found on the PATH.
```

<span data-ttu-id="727be-112">Yürütülebilir adı aracı nasıl çağırdığınızı belirler.</span><span class="sxs-lookup"><span data-stu-id="727be-112">The name of the executable determines how you invoke the tool.</span></span> <span data-ttu-id="727be-113">Aşağıdaki tabloda biçim açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="727be-113">The following table describes the format:</span></span>

| <span data-ttu-id="727be-114">Çalıştırılabilir ad biçimi</span><span class="sxs-lookup"><span data-stu-id="727be-114">Executable name format</span></span>  | <span data-ttu-id="727be-115">Çağırma biçimi</span><span class="sxs-lookup"><span data-stu-id="727be-115">Invocation format</span></span>   |
|-------------------------|---------------------|
| `dotnet-<toolName>.exe` | `dotnet <toolName>` |
| `<toolName>.exe`        | `<toolName>`        |

* <span data-ttu-id="727be-116">Genel araçlar</span><span class="sxs-lookup"><span data-stu-id="727be-116">Global tools</span></span>

  <span data-ttu-id="727be-117">Genel araçlar varsayılan dizine veya belirli bir konuma yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="727be-117">Global tools can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="727be-118">Varsayılan dizinler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="727be-118">The default directories are:</span></span>

  | <span data-ttu-id="727be-119">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="727be-119">OS</span></span>          | <span data-ttu-id="727be-120">Yol</span><span class="sxs-lookup"><span data-stu-id="727be-120">Path</span></span>                          |
  |-------------|-------------------------------|
  | <span data-ttu-id="727be-121">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="727be-121">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
  | <span data-ttu-id="727be-122">Windows</span><span class="sxs-lookup"><span data-stu-id="727be-122">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

  <span data-ttu-id="727be-123">Genel bir araç çalıştırmaya çalışıyorsanız, makinenizdeki ortam değişkeninin `PATH` genel aracı yüklediğiniz yolu içerdiğinden ve yürütülebilir aracın bu yolda olduğundan denetleyin.</span><span class="sxs-lookup"><span data-stu-id="727be-123">If you're trying to run a global tool, check that the `PATH` environment variable on your machine contains the path where you installed the global tool and that the executable is in that path.</span></span>

  <span data-ttu-id="727be-124">.NET Core CLI, ilk kullanımında PATH ortamı değişkenine varsayılan konumu eklemeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="727be-124">The .NET Core CLI tries to add the default location to the PATH environment variable on its first usage.</span></span> <span data-ttu-id="727be-125">Ancak, konumun PATH'e otomatik olarak eklenemeyebildiği bazı senaryolar vardır:</span><span class="sxs-lookup"><span data-stu-id="727be-125">However, there are some scenarios where the location might not be added to PATH automatically:</span></span>

  * <span data-ttu-id="727be-126">Linux kullanıyorsanız ve .NET Core SDK'yı *.tar.gz* dosyalarını kullanarak yüklediyseniz ve apt-get veya rpm değil.</span><span class="sxs-lookup"><span data-stu-id="727be-126">If you're using Linux and you've installed the .NET Core SDK using *.tar.gz* files and not apt-get or rpm.</span></span>
  * <span data-ttu-id="727be-127">macOS 10.15 "Catalina" veya daha sonraki sürümleri kullanıyorsanız.</span><span class="sxs-lookup"><span data-stu-id="727be-127">If you're using macOS 10.15 "Catalina" or later versions.</span></span>
  * <span data-ttu-id="727be-128">macOS 10.14 "Mojave" veya önceki sürümleri kullanıyorsanız ve *.tar.gz* dosyalarını kullanarak .NET Core SDK'yı yüklediyseniz.pkg . *.pkg*</span><span class="sxs-lookup"><span data-stu-id="727be-128">If you're using macOS 10.14 "Mojave" or earlier versions, and you've installed the .NET Core SDK using *.tar.gz* files and not *.pkg*.</span></span>
  * <span data-ttu-id="727be-129">.NET Core 3.0 SDK'yı yüklediyseniz ve ortam `DOTNET_ADD_GLOBAL_TOOLS_TO_PATH` değişkenini '' olarak `false`ayarladıysanız</span><span class="sxs-lookup"><span data-stu-id="727be-129">If you've installed the .NET Core 3.0 SDK and you've set the `DOTNET_ADD_GLOBAL_TOOLS_TO_PATH` environment variable to `false`.</span></span>
  * <span data-ttu-id="727be-130">.NET Core 2.2 SDK veya önceki sürümlerini yüklediyseniz ve `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` ortam `true`değişkenini ' olarak ayarladıysanız.</span><span class="sxs-lookup"><span data-stu-id="727be-130">If you've installed .NET Core 2.2 SDK or earlier versions, and you've set the `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` environment variable to `true`.</span></span>

  <span data-ttu-id="727be-131">Bu senaryolarda veya `--tool-path` seçeneği belirttiyseniz, `PATH` makinenizdeki ortam değişkeni genel aracı yüklediğiniz yolu otomatik olarak içermez.</span><span class="sxs-lookup"><span data-stu-id="727be-131">In these scenarios or if you specified the `--tool-path` option, the `PATH` environment variable on your machine doesn't automatically contain the path where you installed the global tool.</span></span> <span data-ttu-id="727be-132">Bu durumda, shell'inizin çevre değişkenlerini güncelleştirmek için sağladığı yöntemi kullanarak araç konumunu (örneğin, `$HOME/.dotnet/tools`çevre değişkenine) `PATH` ekleyerek ortam değişkenine eklayın.</span><span class="sxs-lookup"><span data-stu-id="727be-132">In that case, append the tool location (for example, `$HOME/.dotnet/tools`) to the `PATH` environment variable by using whatever method your shell provides for updating environment variables.</span></span> <span data-ttu-id="727be-133">Daha fazla bilgi için [bkz.](global-tools.md)</span><span class="sxs-lookup"><span data-stu-id="727be-133">For more information, see [.NET Core tools](global-tools.md).</span></span>

* <span data-ttu-id="727be-134">Yerel araçlar</span><span class="sxs-lookup"><span data-stu-id="727be-134">Local tools</span></span>

  <span data-ttu-id="727be-135">Yerel bir aracı çalıştırmaya çalışıyorsanız, geçerli dizinde veya ana dizinde *dotnet-tools.json* adında bir bildirim dosyası olduğundan doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="727be-135">If you're trying to run a local tool, verify that there's a manifest file called *dotnet-tools.json* in the current directory or any of its parent directories.</span></span> <span data-ttu-id="727be-136">Bu dosya, kök klasör ü yerine proje klasörü hiyerarşisinde herhangi bir yerde *.config* adlı bir klasör altında da yaşayabilir.</span><span class="sxs-lookup"><span data-stu-id="727be-136">This file can also live under a folder named *.config* anywhere in the project folder hierarchy, instead of the root folder.</span></span> <span data-ttu-id="727be-137">*Dotnet-tools.json* varsa açın ve çalıştırmaya çalıştığınız aracı kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="727be-137">If *dotnet-tools.json* exists, open it and check for the tool you're trying to run.</span></span> <span data-ttu-id="727be-138">Dosya için `"isRoot": true`bir giriş içermiyorsa, ek araç bildirimi dosyaları için dosya hiyerarşisini daha da yukarı kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="727be-138">If the file doesn't contain an entry for `"isRoot": true`, then also check further up the file hierarchy for additional tool manifest files.</span></span>

  <span data-ttu-id="727be-139">Belirli bir yol ile yüklenmiş bir .NET Core aracını çalıştırmaya çalışıyorsanız, aracı kullanırken bu yolu eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="727be-139">If you're trying to run a .NET Core tool that was installed with a specified path, you need to include that path when using the tool.</span></span> <span data-ttu-id="727be-140">Bir araç yolu yüklü araç kullanma nın bir örneği:</span><span class="sxs-lookup"><span data-stu-id="727be-140">An example of using a tool-path installed tool is:</span></span>

  ```console
  ..\<toolDirectory>\dotnet-<toolName>
  ```

### <a name="runtime-not-found"></a><span data-ttu-id="727be-141">Çalışma süresi bulunamadı</span><span class="sxs-lookup"><span data-stu-id="727be-141">Runtime not found</span></span>

<span data-ttu-id="727be-142">.NET Core araçları [çerçeveye bağımlı uygulamalardır,](../deploying/index.md#publish-runtime-dependent)bu da makinenize yüklenen bir .NET Core çalışma süresine güvendikleri anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="727be-142">.NET Core tools are [framework-dependent applications](../deploying/index.md#publish-runtime-dependent), which means they rely on a .NET Core runtime installed on your machine.</span></span> <span data-ttu-id="727be-143">Beklenen çalışma süresi bulunamazsa, aşağıdakiler gibi normal .NET Core runtime roll-forward kurallarına uyarlar:</span><span class="sxs-lookup"><span data-stu-id="727be-143">If the expected runtime isn't found, they follow normal .NET Core runtime roll-forward rules such as:</span></span>

* <span data-ttu-id="727be-144">Bir uygulama, belirtilen ana ve küçük sürümün en yüksek yama sürümüne doğru ilerler.</span><span class="sxs-lookup"><span data-stu-id="727be-144">An application rolls forward to the highest patch release of the specified major and minor version.</span></span>
* <span data-ttu-id="727be-145">Eşleşen bir büyük ve küçük sürüm numarasıyla eşleşen çalışma zamanı yoksa, bir sonraki yüksek küçük sürüm kullanılır.</span><span class="sxs-lookup"><span data-stu-id="727be-145">If there's no matching runtime with a matching major and minor version number, the next higher minor version is used.</span></span>
* <span data-ttu-id="727be-146">Roll forward, çalışma zamanının önizleme sürümleri veya önizleme sürümleri ve sürüm sürümleri arasında gerçekleşmez.</span><span class="sxs-lookup"><span data-stu-id="727be-146">Roll forward doesn't occur between preview versions of the runtime or between preview versions and release versions.</span></span> <span data-ttu-id="727be-147">Bu nedenle, önizleme sürümleri kullanılarak oluşturulan .NET Core araçlarının yazar tarafından yeniden oluşturulup yeniden yayımlanmalıdır ve yeniden yüklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="727be-147">So, .NET Core tools created using preview versions must be rebuilt and republished by the author and reinstalled.</span></span>

<span data-ttu-id="727be-148">Roll-forward varsayılan olarak iki yaygın senaryoda oluşmaz:</span><span class="sxs-lookup"><span data-stu-id="727be-148">Roll-forward won't occur by default in two common scenarios:</span></span>

* <span data-ttu-id="727be-149">Yalnızca çalışma zamanının daha düşük sürümleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="727be-149">Only lower versions of the runtime are available.</span></span> <span data-ttu-id="727be-150">Roll-forward yalnızca çalışma zamanının sonraki sürümlerini seçer.</span><span class="sxs-lookup"><span data-stu-id="727be-150">Roll-forward only selects later versions of the runtime.</span></span>
* <span data-ttu-id="727be-151">Yalnızca çalışma zamanının daha yüksek ana sürümleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="727be-151">Only higher major versions of the runtime are available.</span></span> <span data-ttu-id="727be-152">Roll-forward ana sürüm sınırlarını geçmez.</span><span class="sxs-lookup"><span data-stu-id="727be-152">Roll-forward doesn't cross major version boundaries.</span></span>

<span data-ttu-id="727be-153">Bir uygulama uygun bir çalışma zamanı bulamazsa, çalışmaz ve bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="727be-153">If an application can't find an appropriate runtime, it fails to run and reports an error.</span></span>

<span data-ttu-id="727be-154">Aşağıdaki komutlardan birini kullanarak makinenize hangi .NET Core çalışma saatlerinin takıldığı öğrenebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="727be-154">You can find out which .NET Core runtimes are installed on your machine using one of the following commands:</span></span>

```dotnetcli
dotnet --list-runtimes
dotnet --info
```

<span data-ttu-id="727be-155">Aracın şu anda yüklediğiniz çalışma zamanı sürümünü desteklemesi gerektiğini düşünüyorsanız, araç yazarına başvurabilir ve sürüm numarasını veya çoklu hedefi güncelleştirip güncelleştiremediklerini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="727be-155">If you think the tool should support the runtime version you currently have installed, you can contact the tool author and see if they can update the version number or multi-target.</span></span> <span data-ttu-id="727be-156">Araç paketlerini güncelleştirilmiş bir sürüm numarasıyla NuGet'e yeniden derleyip yeniden yayımladıktan sonra kopyanızı güncelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="727be-156">Once they've recompiled and republished their tool package to NuGet with an updated version number, you can update your copy.</span></span> <span data-ttu-id="727be-157">Bu gerçekleşmese de, sizin için en hızlı çözüm, çalıştırmaya çalıştığınız araçla çalışacak çalışma zamanının bir sürümünü yüklemektir.</span><span class="sxs-lookup"><span data-stu-id="727be-157">While that doesn't happen, the quickest solution for you is to install a version of the runtime that would work with the tool you're trying to run.</span></span> <span data-ttu-id="727be-158">Belirli bir .NET Core çalışma zamanı sürümünü indirmek için [.NET Core indirme sayfasını](https://dotnet.microsoft.com/download/dotnet-core)ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="727be-158">To download a specific .NET Core runtime version, visit the [.NET Core download page](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="727be-159">.NET Core SDK'yı varsayılan olmayan bir konuma yüklerseniz, ortam `DOTNET_ROOT` değişkenini `dotnet` yürütülebilir içeren dizine ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="727be-159">If you install the .NET Core SDK to a non-default location, you need to set the environment variable `DOTNET_ROOT` to the directory that contains the `dotnet` executable.</span></span>

## <a name="net-core-tool-installation-fails"></a><span data-ttu-id="727be-160">.NET Core araç kurulumu başarısız oldu</span><span class="sxs-lookup"><span data-stu-id="727be-160">.NET Core tool installation fails</span></span>

<span data-ttu-id="727be-161">.NET Core global veya yerel bir aracın yüklenmesinin başarısız olmasının birkaç nedeni vardır.</span><span class="sxs-lookup"><span data-stu-id="727be-161">There are a number of reasons the installation of a .NET Core global or local tool may fail.</span></span> <span data-ttu-id="727be-162">Araç yüklemesi başarısız olduğunda, aşağıdakine benzer bir ileti görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="727be-162">When the tool installation fails, you'll see a message similar to the following one:</span></span>

```console
Tool '{0}' failed to install. This failure may have been caused by:

* You are attempting to install a preview release and did not use the --version option to specify the version.
* A package by this name was found, but it was not a .NET Core tool.
* The required NuGet feed cannot be accessed, perhaps because of an Internet connection problem.
* You mistyped the name of the tool.

For more reasons, including package naming enforcement, visit https://aka.ms/failure-installing-tool
```

<span data-ttu-id="727be-163">Bu hataları tanılamaya yardımcı olmak için, NuGet iletileri önceki iletiyle birlikte doğrudan kullanıcıya gösterilir.</span><span class="sxs-lookup"><span data-stu-id="727be-163">To help diagnose these failures, NuGet messages are shown directly to the user, along with the previous message.</span></span> <span data-ttu-id="727be-164">NuGet iletisi sorunu belirlemenize yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="727be-164">The NuGet message may help you identify the problem.</span></span>

### <a name="package-naming-enforcement"></a><span data-ttu-id="727be-165">Paket adlandırma zorlama</span><span class="sxs-lookup"><span data-stu-id="727be-165">Package naming enforcement</span></span>

<span data-ttu-id="727be-166">Microsoft, araçlar için Paket Kimliği kılavuzunu değiştirerek, bir dizi araçta öngörülen adla birlikte bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="727be-166">Microsoft has changed its guidance on the Package ID for tools, resulting in a number of tools not being found with the predicted name.</span></span> <span data-ttu-id="727be-167">Yeni kılavuz, tüm Microsoft araçlarının "Microsoft" ile önceden belirlenmiş olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="727be-167">The new guidance is that all Microsoft tools be prefixed with "Microsoft."</span></span> <span data-ttu-id="727be-168">Bu önek ayrılmıştır ve yalnızca Microsoft yetkili sertifikasıyla imzalanmış paketler için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="727be-168">This prefix is reserved and can only be used for packages signed with a Microsoft authorized certificate.</span></span>

<span data-ttu-id="727be-169">Geçiş sırasında, bazı Microsoft araçları paket kimliğinin eski biçimine sahip olurken, diğerleri yeni forma sahip olur:</span><span class="sxs-lookup"><span data-stu-id="727be-169">During the transition, some Microsoft tools will have the old form of the package ID, while others will have the new form:</span></span>

```dotnetcli
dotnet tool install -g Microsoft.<toolName>
dotnet tool install -g <toolName>
```

<span data-ttu-id="727be-170">Paket kimlikleri güncelleştirildikçe, en son güncelleştirmeleri almak için yeni paket kimliğine değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="727be-170">As package IDs are updated, you'll need to change to the new package ID to get the latest updates.</span></span> <span data-ttu-id="727be-171">Basitleştirilmiş araç adı taşıyan paketler amortismana sokulacaktır.</span><span class="sxs-lookup"><span data-stu-id="727be-171">Packages with the simplified tool name will be deprecated.</span></span>

### <a name="preview-releases"></a><span data-ttu-id="727be-172">Önizleme bültenleri</span><span class="sxs-lookup"><span data-stu-id="727be-172">Preview releases</span></span>

* <span data-ttu-id="727be-173">Bir önizleme sürümü yüklemeye çalışıyorsunuz ve sürümü `--version` belirtme seçeneğini kullanmadınız.</span><span class="sxs-lookup"><span data-stu-id="727be-173">You're attempting to install a preview release and didn't use the `--version` option to specify the version.</span></span>

<span data-ttu-id="727be-174">.NET Core araçları önizlemede olduklarını belirtmek için adın bir bölümüyle belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="727be-174">.NET Core tools that are in preview must be specified with a portion of the name to indicate that they are in preview.</span></span> <span data-ttu-id="727be-175">Önizlemenin tamamını eklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="727be-175">You don't need to include the entire preview.</span></span> <span data-ttu-id="727be-176">Sürüm numaralarının beklenen biçimde olduğunu varsayarsak, aşağıdaki örnek gibi bir şey kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="727be-176">Assuming the version numbers are in the expected format, you can use something like the following example:</span></span>

```dotnetcli
dotnet tool install -g --version 1.1.0-pre <toolName>
```

### <a name="package-isnt-a-net-core-tool"></a><span data-ttu-id="727be-177">Paket bir .NET Core aracı değildir</span><span class="sxs-lookup"><span data-stu-id="727be-177">Package isn't a .NET Core tool</span></span>

* <span data-ttu-id="727be-178">Bu ada göre bir NuGet paketi bulundu, ancak bir .NET Core aracı değildi.</span><span class="sxs-lookup"><span data-stu-id="727be-178">A NuGet package by this name was found, but it wasn't a .NET Core tool.</span></span>

<span data-ttu-id="727be-179">Bir .NET Core aracı değil de normal bir NuGet paketi yüklemeye çalışırsanız, aşağıdakilere benzer bir hata görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="727be-179">If you try to install a NuGet package that is a regular NuGet package and not a .NET Core tool, you'll see an error similar to the following:</span></span>

> <span data-ttu-id="727be-180">NU1212: Geçersiz proje paketi `<ToolName>`kombinasyonu.</span><span class="sxs-lookup"><span data-stu-id="727be-180">NU1212: Invalid project-package combination for `<ToolName>`.</span></span> <span data-ttu-id="727be-181">DotnetToolReference proje stili yalnızca DotnetTool türüne ait referanslar içerebilir.</span><span class="sxs-lookup"><span data-stu-id="727be-181">DotnetToolReference project style can only contain references of the DotnetTool type.</span></span>

### <a name="nuget-feed-cant-be-accessed"></a><span data-ttu-id="727be-182">NuGet akışına erişilenemiyor</span><span class="sxs-lookup"><span data-stu-id="727be-182">NuGet feed can't be accessed</span></span>

* <span data-ttu-id="727be-183">Gerekli NuGet akışına, internet bağlantısı sorunu nedeniyle erişilememektedir.</span><span class="sxs-lookup"><span data-stu-id="727be-183">The required NuGet feed can't be accessed, perhaps because of an Internet connection problem.</span></span>

<span data-ttu-id="727be-184">Araç yükleme, araç paketini içeren NuGet akışına erişim gerektirir.</span><span class="sxs-lookup"><span data-stu-id="727be-184">Tool installation requires access to the NuGet feed that contains the tool package.</span></span> <span data-ttu-id="727be-185">Özet akışı kullanılamıyorsa başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="727be-185">It fails if the feed isn't available.</span></span> <span data-ttu-id="727be-186">Akışlarını `nuget.config`değiştirebilir, belirli `nuget.config` bir dosya yı isteyebilir veya `--add-source` anahtarla ek akışlar belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="727be-186">You can alter feeds with `nuget.config`, request a specific `nuget.config` file, or specify additional feeds with the `--add-source` switch.</span></span> <span data-ttu-id="727be-187">Varsayılan olarak, NuGet bağlanamayan tüm akışlar için bir hata atar.</span><span class="sxs-lookup"><span data-stu-id="727be-187">By default, NuGet throws an error for any feed that can't connect.</span></span> <span data-ttu-id="727be-188">Bayrak `--ignore-failed-sources` bu erişilemez kaynakları atlayabilir.</span><span class="sxs-lookup"><span data-stu-id="727be-188">The flag `--ignore-failed-sources` can skip these non-reachable sources.</span></span>

### <a name="package-id-incorrect"></a><span data-ttu-id="727be-189">Paket kimliği yanlış</span><span class="sxs-lookup"><span data-stu-id="727be-189">Package ID incorrect</span></span>

* <span data-ttu-id="727be-190">Aracın adını yanlış yazdınız.</span><span class="sxs-lookup"><span data-stu-id="727be-190">You mistyped the name of the tool.</span></span>

<span data-ttu-id="727be-191">Hatanın yaygın bir nedeni, araç adının doğru olmamasıdır.</span><span class="sxs-lookup"><span data-stu-id="727be-191">A common reason for failure is that the tool name isn't correct.</span></span> <span data-ttu-id="727be-192">Bu, yanlış yazım nedeniyle veya araç taşındığı veya küçümdelenmiş olması nedeniyle olabilir.</span><span class="sxs-lookup"><span data-stu-id="727be-192">This can happen because of mistyping, or because the tool has moved or been deprecated.</span></span> <span data-ttu-id="727be-193">NuGet.org araçlar için, adı doğru olduğundan emin olmak için bir yolu NuGet.org aracı aramak ve yükleme komutunu kopyalamaktır.</span><span class="sxs-lookup"><span data-stu-id="727be-193">For tools on NuGet.org, one way to ensure you have the name correct is to search for the tool at NuGet.org and copy the installation command.</span></span>

## <a name="see-also"></a><span data-ttu-id="727be-194">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="727be-194">See also</span></span>

* [<span data-ttu-id="727be-195">.NET Çekirdek araçları</span><span class="sxs-lookup"><span data-stu-id="727be-195">.NET Core tools</span></span>](global-tools.md)
