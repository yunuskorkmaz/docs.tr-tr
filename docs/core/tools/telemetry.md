---
title: .NET Core SDK telemetri
description: Analiz için kullanım bilgilerini toplayan, hangi verilerin toplandığı ve devre dışı bırakılacağı .NET Core SDK telemetri özelliklerini bulun.
author: KathleenDollard
ms.date: 08/27/2019
ms.openlocfilehash: 9d5d7ff09ade89712f2fbbe35224851bb1c28b4c
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156692"
---
# <a name="net-core-sdk-telemetry"></a><span data-ttu-id="c93a5-103">.NET Core SDK telemetri</span><span class="sxs-lookup"><span data-stu-id="c93a5-103">.NET Core SDK telemetry</span></span>

<span data-ttu-id="c93a5-104">[.NET Core SDK](index.md) , .NET Core CLI çöktüğünde kullanım verilerini ve özel durum bilgilerini toplayan bir telemetri özelliği içerir.</span><span class="sxs-lookup"><span data-stu-id="c93a5-104">The [.NET Core SDK](index.md) includes a telemetry feature that collects usage data and exception information when the .NET Core CLI crashes.</span></span> <span data-ttu-id="c93a5-105">.NET Core CLI .NET Core SDK ile birlikte gelir ve .NET Core uygulamalarınızı oluşturmanızı, test etmeniz ve yayımlamanıza olanak tanıyan fiiller kümesidir.</span><span class="sxs-lookup"><span data-stu-id="c93a5-105">The .NET Core CLI comes with the .NET Core SDK and is the set of verbs that enable you to build, test, and publish your .NET Core apps.</span></span> <span data-ttu-id="c93a5-106">.NET ekibinin, araçların iyileştirilmesi için nasıl kullanıldığını anladığından emin olmanız önemlidir.</span><span class="sxs-lookup"><span data-stu-id="c93a5-106">It's important that the .NET team understands how the tools are used so they can be improved.</span></span> <span data-ttu-id="c93a5-107">Hatalar hakkında bilgi, takımın sorunları çözmesine ve hataları düzeltmesine yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="c93a5-107">Information on failures helps the team resolve problems and fix bugs.</span></span>

<span data-ttu-id="c93a5-108">Toplanan veriler anonimdir ve [Creative Commons Attribution Lisansı](https://creativecommons.org/licenses/by/4.0/)kapsamında toplu olarak yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="c93a5-108">The collected data is anonymous and published in aggregate under the [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span></span>

## <a name="scope"></a><span data-ttu-id="c93a5-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="c93a5-109">Scope</span></span>

<span data-ttu-id="c93a5-110">`dotnet` iki işleve sahiptir: uygulamaları çalıştırmak ve CLı komutlarını yürütmek için.</span><span class="sxs-lookup"><span data-stu-id="c93a5-110">`dotnet` has two functions: to run apps, and to execute CLI commands.</span></span> <span data-ttu-id="c93a5-111">Bir uygulamayı aşağıdaki biçimde başlatmak için `dotnet` kullanılırken telemetri *toplanmaz* :</span><span class="sxs-lookup"><span data-stu-id="c93a5-111">Telemetry *isn't collected* when using `dotnet` to start an application in the following format:</span></span>

- `dotnet [path-to-app].dll`

<span data-ttu-id="c93a5-112">Telemetri, şöyle [.NET Core CLI komutlardan](index.md)biri kullanılarak *toplanır* :</span><span class="sxs-lookup"><span data-stu-id="c93a5-112">Telemetry *is collected* when using any of the [.NET Core CLI commands](index.md), such as:</span></span>

- `dotnet build`
- `dotnet pack`
- `dotnet run`

## <a name="how-to-opt-out"></a><span data-ttu-id="c93a5-113">Devre dışı bırakma</span><span class="sxs-lookup"><span data-stu-id="c93a5-113">How to opt out</span></span>

<span data-ttu-id="c93a5-114">.NET Core SDK telemetri özelliği varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="c93a5-114">The .NET Core SDK telemetry feature is enabled by default.</span></span> <span data-ttu-id="c93a5-115">Telemetri özelliğini devre dışı bırakmak için `DOTNET_CLI_TELEMETRY_OPTOUT` ortam değişkenini `1` veya `true`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c93a5-115">To opt out of the telemetry feature, set the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span>

<span data-ttu-id="c93a5-116">Başarılı bir yükleme gerçekleştiğinde .NET Core SDK yükleyicisi tarafından tek bir telemetri girişi de gönderilir.</span><span class="sxs-lookup"><span data-stu-id="c93a5-116">A single telemetry entry is also sent by the .NET Core SDK installer when a successful installation happens.</span></span> <span data-ttu-id="c93a5-117">Devre dışı bırakmak için, .NET Core SDK yüklemeden önce `DOTNET_CLI_TELEMETRY_OPTOUT` ortam değişkenini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c93a5-117">To opt out, set the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable before you install the .NET Core SDK.</span></span>

## <a name="disclosure"></a><span data-ttu-id="c93a5-118">Savunmasız</span><span class="sxs-lookup"><span data-stu-id="c93a5-118">Disclosure</span></span>

<span data-ttu-id="c93a5-119">.NET Core SDK, [.NET Core CLI komutlarından](index.md) birini ilk kez çalıştırdığınızda (örneğin, `dotnet build`) aşağıdakine benzer metni görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c93a5-119">The .NET Core SDK displays text similar to the following when you first run one of the [.NET Core CLI commands](index.md) (for example, `dotnet build`).</span></span> <span data-ttu-id="c93a5-120">Metin, çalıştırmakta olduğunuz SDK sürümüne bağlı olarak biraz farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="c93a5-120">Text may vary slightly depending on the version of the SDK you're running.</span></span> <span data-ttu-id="c93a5-121">Bu "ilk çalıştırma" deneyimi, Microsoft 'un veri toplamayı nasıl bildisidir.</span><span class="sxs-lookup"><span data-stu-id="c93a5-121">This "first run" experience is how Microsoft notifies you about data collection.</span></span>

```console
Telemetry
---------
The .NET Core tools collect usage data in order to help us improve your experience. The data is anonymous. It is collected by Microsoft and shared with the community. You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET Core CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry
```

## <a name="data-points"></a><span data-ttu-id="c93a5-122">Veri noktaları</span><span class="sxs-lookup"><span data-stu-id="c93a5-122">Data points</span></span>

<span data-ttu-id="c93a5-123">Telemetri özelliği, Kullanıcı adları veya e-posta adresleri gibi kişisel verileri toplamaz.</span><span class="sxs-lookup"><span data-stu-id="c93a5-123">The telemetry feature doesn't collect personal data, such as usernames or email addresses.</span></span> <span data-ttu-id="c93a5-124">Kodunuzu taramaz ve ad, depo veya yazar gibi proje düzeyi verileri ayıklamaz.</span><span class="sxs-lookup"><span data-stu-id="c93a5-124">It doesn't scan your code and doesn't extract project-level data, such as name, repository, or author.</span></span> <span data-ttu-id="c93a5-125">Veriler, [Azure izleyici](https://azure.microsoft.com/services/monitor/) teknolojisini kullanan Microsoft sunucularına güvenli bir şekilde gönderilir, sınırlı erişim altında tutulur ve güvenli [Azure depolama](https://azure.microsoft.com/services/storage/) sistemlerinden katı güvenlik denetimleri altında yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="c93a5-125">The data is sent securely to Microsoft servers using [Azure Monitor](https://azure.microsoft.com/services/monitor/) technology, held under restricted access, and published under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

<span data-ttu-id="c93a5-126">Gizliliğinizi korumak bizim için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="c93a5-126">Protecting your privacy is important to us.</span></span> <span data-ttu-id="c93a5-127">Telemetrinin hassas verileri toplamasını veya verilerin güvenli veya uygun şekilde işlenmekte olduğunu düşünüyorsanız, [DotNet/CLI](https://github.com/dotnet/cli/issues) deposunda bir sorun yapın veya araştırma için [dotnet@microsoft.com](mailto:dotnet@microsoft.com) bir e-posta gönderin.</span><span class="sxs-lookup"><span data-stu-id="c93a5-127">If you suspect the telemetry is collecting sensitive data or the data is being insecurely or inappropriately handled, file an issue in the [dotnet/cli](https://github.com/dotnet/cli/issues) repository or send an email to [dotnet@microsoft.com](mailto:dotnet@microsoft.com) for investigation.</span></span>

<span data-ttu-id="c93a5-128">Telemetri özelliği aşağıdaki verileri toplar:</span><span class="sxs-lookup"><span data-stu-id="c93a5-128">The telemetry feature collects the following data:</span></span>

| <span data-ttu-id="c93a5-129">SDK sürümleri</span><span class="sxs-lookup"><span data-stu-id="c93a5-129">SDK versions</span></span> | <span data-ttu-id="c93a5-130">Veriler</span><span class="sxs-lookup"><span data-stu-id="c93a5-130">Data</span></span> |
|--------------|------|
| <span data-ttu-id="c93a5-131">Tümü</span><span class="sxs-lookup"><span data-stu-id="c93a5-131">All</span></span>          | <span data-ttu-id="c93a5-132">Çağırma zaman damgası.</span><span class="sxs-lookup"><span data-stu-id="c93a5-132">Timestamp of invocation.</span></span> |
| <span data-ttu-id="c93a5-133">Tümü</span><span class="sxs-lookup"><span data-stu-id="c93a5-133">All</span></span>          | <span data-ttu-id="c93a5-134">Komut çağrıldı (örneğin, "Build"), 2,1 'den başlayarak karma hale getirilmiş.</span><span class="sxs-lookup"><span data-stu-id="c93a5-134">Command invoked (for example, "build"), hashed starting in 2.1.</span></span> |
| <span data-ttu-id="c93a5-135">Tümü</span><span class="sxs-lookup"><span data-stu-id="c93a5-135">All</span></span>          | <span data-ttu-id="c93a5-136">Coğrafi konumu belirlemede kullanılan üç sekizli IP adresi.</span><span class="sxs-lookup"><span data-stu-id="c93a5-136">Three octet IP address used to determine the geographical location.</span></span> |
| <span data-ttu-id="c93a5-137">Tümü</span><span class="sxs-lookup"><span data-stu-id="c93a5-137">All</span></span>          | <span data-ttu-id="c93a5-138">İşletim sistemi ve sürümü.</span><span class="sxs-lookup"><span data-stu-id="c93a5-138">Operating system and version.</span></span> |
| <span data-ttu-id="c93a5-139">Tümü</span><span class="sxs-lookup"><span data-stu-id="c93a5-139">All</span></span>          | <span data-ttu-id="c93a5-140">SDK 'nın üzerinde çalıştığı çalışma zamanı KIMLIĞI (RID).</span><span class="sxs-lookup"><span data-stu-id="c93a5-140">Runtime ID (RID) the SDK is running on.</span></span> |
| <span data-ttu-id="c93a5-141">Tümü</span><span class="sxs-lookup"><span data-stu-id="c93a5-141">All</span></span>          | <span data-ttu-id="c93a5-142">.NET Core SDK sürümü.</span><span class="sxs-lookup"><span data-stu-id="c93a5-142">.NET Core SDK version.</span></span> |
| <span data-ttu-id="c93a5-143">Tümü</span><span class="sxs-lookup"><span data-stu-id="c93a5-143">All</span></span>          | <span data-ttu-id="c93a5-144">Telemetri profili: isteğe bağlı bir değer yalnızca açık Kullanıcı kabul etme ve Microsoft 'ta dahili olarak kullanılan bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="c93a5-144">Telemetry profile: an optional value only used with explicit user opt-in and used internally at Microsoft.</span></span> |
| <span data-ttu-id="c93a5-145">> = 2.0</span><span class="sxs-lookup"><span data-stu-id="c93a5-145">>=2.0</span></span>        | <span data-ttu-id="c93a5-146">Komut bağımsız değişkenleri ve seçenekleri: birkaç bağımsız değişken ve seçenek toplanır (rastgele dizeler değil).</span><span class="sxs-lookup"><span data-stu-id="c93a5-146">Command arguments and options: several arguments and options are collected (not arbitrary strings).</span></span> <span data-ttu-id="c93a5-147">[Toplanan seçeneklere](#collected-options)bakın.</span><span class="sxs-lookup"><span data-stu-id="c93a5-147">See [collected options](#collected-options).</span></span> <span data-ttu-id="c93a5-148">2\.1.300 sonrasında karma hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="c93a5-148">Hashed after 2.1.300.</span></span> |
| <span data-ttu-id="c93a5-149">> = 2.0</span><span class="sxs-lookup"><span data-stu-id="c93a5-149">>=2.0</span></span>         | <span data-ttu-id="c93a5-150">SDK 'nın bir kapsayıcıda çalışıp çalışmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c93a5-150">Whether the SDK is running in a container.</span></span> |
| <span data-ttu-id="c93a5-151">> = 2.0</span><span class="sxs-lookup"><span data-stu-id="c93a5-151">>=2.0</span></span>         | <span data-ttu-id="c93a5-152">2,1 ' den başlayarak karma hale getirilmiş hedef çerçeveler (`TargetFramework` olayından).</span><span class="sxs-lookup"><span data-stu-id="c93a5-152">Target frameworks (from the `TargetFramework` event), hashed starting in 2.1.</span></span> |
| <span data-ttu-id="c93a5-153">> = 2.0</span><span class="sxs-lookup"><span data-stu-id="c93a5-153">>=2.0</span></span>         | <span data-ttu-id="c93a5-154">Karma medya Access Control (MAC) adresi: bir makine için bir şifreleme (SHA256) anonim ve benzersiz KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="c93a5-154">Hashed Media Access Control (MAC) address: a cryptographically (SHA256) anonymous and unique ID for a machine.</span></span> |
| <span data-ttu-id="c93a5-155">> = 2.0</span><span class="sxs-lookup"><span data-stu-id="c93a5-155">>=2.0</span></span>         | <span data-ttu-id="c93a5-156">Karma hale getirilmiş geçerli çalışma dizini.</span><span class="sxs-lookup"><span data-stu-id="c93a5-156">Hashed current working directory.</span></span> |
| <span data-ttu-id="c93a5-157">> = 2.0</span><span class="sxs-lookup"><span data-stu-id="c93a5-157">>=2.0</span></span>         | <span data-ttu-id="c93a5-158">Karma yükleyici exe dosya adına sahip başarı raporunu yükleme.</span><span class="sxs-lookup"><span data-stu-id="c93a5-158">Install success report, with hashed installer exe filename.</span></span> |
| <span data-ttu-id="c93a5-159">> = 2.1.300</span><span class="sxs-lookup"><span data-stu-id="c93a5-159">>=2.1.300</span></span>     | <span data-ttu-id="c93a5-160">Çekirdek sürümü.</span><span class="sxs-lookup"><span data-stu-id="c93a5-160">Kernel version.</span></span> |
| <span data-ttu-id="c93a5-161">> = 2.1.300</span><span class="sxs-lookup"><span data-stu-id="c93a5-161">>=2.1.300</span></span>     | <span data-ttu-id="c93a5-162">Libc sürümü/sürümü.</span><span class="sxs-lookup"><span data-stu-id="c93a5-162">Libc release/version.</span></span> |
| <span data-ttu-id="c93a5-163">> = 3.0.100</span><span class="sxs-lookup"><span data-stu-id="c93a5-163">>=3.0.100</span></span>     | <span data-ttu-id="c93a5-164">Çıktının yeniden yönlendirilme (true veya false).</span><span class="sxs-lookup"><span data-stu-id="c93a5-164">Whether the output was redirected (true or false).</span></span> |
| <span data-ttu-id="c93a5-165">> = 3.0.100</span><span class="sxs-lookup"><span data-stu-id="c93a5-165">>=3.0.100</span></span>     | <span data-ttu-id="c93a5-166">CLı/SDK kilitlenmesinde, özel durum türü ve yığın izlemesi (yalnızca CLı/SDK kodu, gönderilen yığın izlemesinde bulunur).</span><span class="sxs-lookup"><span data-stu-id="c93a5-166">On a CLI/SDK crash, the exception type and its stack trace (only CLI/SDK code is included in the stack trace sent).</span></span> <span data-ttu-id="c93a5-167">Daha fazla bilgi için bkz. [.NET Core CLI/SDK kilitlenme özel durum telemetrisi toplandı](#net-core-clisdk-crash-exception-telemetry-collected).</span><span class="sxs-lookup"><span data-stu-id="c93a5-167">For more information, see [.NET Core CLI/SDK crash exception telemetry collected](#net-core-clisdk-crash-exception-telemetry-collected).</span></span> |

### <a name="collected-options"></a><span data-ttu-id="c93a5-168">Toplanan seçenekler</span><span class="sxs-lookup"><span data-stu-id="c93a5-168">Collected options</span></span>

<span data-ttu-id="c93a5-169">Bazı komutlar ek veriler gönderir.</span><span class="sxs-lookup"><span data-stu-id="c93a5-169">Certain commands send additional data.</span></span> <span data-ttu-id="c93a5-170">Bir komut alt kümesi ilk bağımsız değişkeni gönderir:</span><span class="sxs-lookup"><span data-stu-id="c93a5-170">A subset of commands sends the first argument:</span></span>

| <span data-ttu-id="c93a5-171">Komut</span><span class="sxs-lookup"><span data-stu-id="c93a5-171">Command</span></span>               | <span data-ttu-id="c93a5-172">Gönderilen ilk bağımsız değişken verileri</span><span class="sxs-lookup"><span data-stu-id="c93a5-172">First argument data sent</span></span>                |
|-----------------------|-----------------------------------------|
| `dotnet help <arg>`   | <span data-ttu-id="c93a5-173">İçin komut yardımı sorgulanırken.</span><span class="sxs-lookup"><span data-stu-id="c93a5-173">The command help is being queried for.</span></span>  |
| `dotnet new <arg>`    | <span data-ttu-id="c93a5-174">Şablon adı (karma).</span><span class="sxs-lookup"><span data-stu-id="c93a5-174">The template name (hashed).</span></span>             |
| `dotnet add <arg>`    | <span data-ttu-id="c93a5-175">`package` veya `reference`sözcük.</span><span class="sxs-lookup"><span data-stu-id="c93a5-175">The word `package` or `reference`.</span></span>      |
| `dotnet remove <arg>` | <span data-ttu-id="c93a5-176">`package` veya `reference`sözcük.</span><span class="sxs-lookup"><span data-stu-id="c93a5-176">The word `package` or `reference`.</span></span>      |
| `dotnet list <arg>`   | <span data-ttu-id="c93a5-177">`package` veya `reference`sözcük.</span><span class="sxs-lookup"><span data-stu-id="c93a5-177">The word `package` or `reference`.</span></span>      |
| `dotnet sln <arg>`    | <span data-ttu-id="c93a5-178">`add`, `list`veya `remove`sözcük.</span><span class="sxs-lookup"><span data-stu-id="c93a5-178">The word `add`, `list`, or `remove`.</span></span>    |
| `dotnet nuget <arg>`  | <span data-ttu-id="c93a5-179">`delete`, `locals`veya `push`sözcük.</span><span class="sxs-lookup"><span data-stu-id="c93a5-179">The word `delete`, `locals`, or `push`.</span></span> |

<span data-ttu-id="c93a5-180">Bir komut alt kümesi, kullanıldıkları takdirde, değerleriyle birlikte, seçili seçenekleri gönderir:</span><span class="sxs-lookup"><span data-stu-id="c93a5-180">A subset of commands sends selected options if they're used, along with their values:</span></span>

| <span data-ttu-id="c93a5-181">Seçenek</span><span class="sxs-lookup"><span data-stu-id="c93a5-181">Option</span></span>                  | <span data-ttu-id="c93a5-182">Komutlar</span><span class="sxs-lookup"><span data-stu-id="c93a5-182">Commands</span></span>                                                                                       |
|-------------------------|------------------------------------------------------------------------------------------------|
| `--verbosity`           | <span data-ttu-id="c93a5-183">Tüm komutlar</span><span class="sxs-lookup"><span data-stu-id="c93a5-183">All commands</span></span>                                                                                   |
| `--language`            | `dotnet new`                                                                                   |
| `--configuration`       | <span data-ttu-id="c93a5-184">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`</span><span class="sxs-lookup"><span data-stu-id="c93a5-184">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`</span></span>                  |
| `--framework`           | <span data-ttu-id="c93a5-185">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`, `dotnet vstest`</span><span class="sxs-lookup"><span data-stu-id="c93a5-185">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`, `dotnet vstest`</span></span> |
| `--runtime`             | <span data-ttu-id="c93a5-186">`dotnet build`, `dotnet publish`</span><span class="sxs-lookup"><span data-stu-id="c93a5-186">`dotnet build`,  `dotnet publish`</span></span>                                                              |
| `--platform`            | `dotnet vstest`                                                                                |
| `--logger`              | `dotnet vstest`                                                                                |
| `--sdk-package-version` | `dotnet migrate`                                                                               |

<span data-ttu-id="c93a5-187">`--verbosity` ve `--sdk-package-version`dışında, diğer tüm değerler .NET Core 2.1.100 SDK ile başlayarak karma hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="c93a5-187">Except for `--verbosity` and `--sdk-package-version`, all the other values are hashed starting with .NET Core 2.1.100 SDK.</span></span>

## <a name="net-core-clisdk-crash-exception-telemetry-collected"></a><span data-ttu-id="c93a5-188">.NET Core CLI/SDK kilitlenme özel durum telemetrisi toplandı</span><span class="sxs-lookup"><span data-stu-id="c93a5-188">.NET Core CLI/SDK crash exception telemetry collected</span></span>

<span data-ttu-id="c93a5-189">.NET Core CLI/SDK kilitlenirse, CLı/SDK kodunun özel durum ve yığın izlemesinin adını toplar.</span><span class="sxs-lookup"><span data-stu-id="c93a5-189">If the .NET Core CLI/SDK crashes, it collects the name of the exception and stack trace of the CLI/SDK code.</span></span> <span data-ttu-id="c93a5-190">Bu bilgiler, sorunları değerlendirmek ve .NET Core SDK ve CLı kalitesini geliştirmek için toplanır.</span><span class="sxs-lookup"><span data-stu-id="c93a5-190">This information is collected to assess problems and improve the quality of the .NET Core SDK and CLI.</span></span> <span data-ttu-id="c93a5-191">Bu makalede Topladığımız veriler hakkında bilgi sağlanır.</span><span class="sxs-lookup"><span data-stu-id="c93a5-191">This article provides information about the data we collect.</span></span> <span data-ttu-id="c93a5-192">Ayrıca, kullanıcıların kendi .NET Core SDK kendi sürümünü oluşturma konusunda ipuçları, kişisel veya hassas bilgilerin yanlışlıkla açıklanmasını önleyebilir.</span><span class="sxs-lookup"><span data-stu-id="c93a5-192">It also provides tips on how users building their own version of the .NET Core SDK can avoid inadvertent disclosure of personal or sensitive information.</span></span>

### <a name="types-of-collected-data"></a><span data-ttu-id="c93a5-193">Toplanan veri türleri</span><span class="sxs-lookup"><span data-stu-id="c93a5-193">Types of collected data</span></span>

<span data-ttu-id="c93a5-194">.NET Core CLI, uygulamanızda özel durumlar değil yalnızca CLı/SDK özel durumları için bilgi toplar.</span><span class="sxs-lookup"><span data-stu-id="c93a5-194">.NET Core CLI collects information for CLI/SDK exceptions only, not exceptions in your application.</span></span> <span data-ttu-id="c93a5-195">Toplanan veriler, özel durumun ve yığın izlemenin adını içerir.</span><span class="sxs-lookup"><span data-stu-id="c93a5-195">The collected data contains the name of the exception and the stack trace.</span></span> <span data-ttu-id="c93a5-196">Bu yığın izlemesi CLı/SDK kodudur.</span><span class="sxs-lookup"><span data-stu-id="c93a5-196">This stack trace is of CLI/SDK code.</span></span>

<span data-ttu-id="c93a5-197">Aşağıdaki örnek, toplanan veri türünü gösterir:</span><span class="sxs-lookup"><span data-stu-id="c93a5-197">The following example shows the kind of data that is collected:</span></span>

```console
System.IO.IOException
at System.ConsolePal.WindowsConsoleStream.Write(Byte[] buffer, Int32 offset, Int32 count)
at System.IO.StreamWriter.Flush(Boolean flushStream, Boolean flushEncoder)
at System.IO.StreamWriter.Write(Char[] buffer)
at System.IO.TextWriter.WriteLine()
at System.IO.TextWriter.SyncTextWriter.WriteLine()
at Microsoft.DotNet.Cli.Utils.Reporter.WriteLine()
at Microsoft.DotNet.Tools.Run.RunCommand.EnsureProjectIsBuilt()
at Microsoft.DotNet.Tools.Run.RunCommand.Execute()
at Microsoft.DotNet.Tools.Run.RunCommand.Run(String[] args)
at Microsoft.DotNet.Cli.Program.ProcessArgs(String[] args, ITelemetry telemetryClient)
at Microsoft.DotNet.Cli.Program.Main(String[] args)
```

### <a name="avoid-inadvertent-disclosure-of-information"></a><span data-ttu-id="c93a5-198">Bilgilerin yanlışlıkla açıklanmasını önleyin</span><span class="sxs-lookup"><span data-stu-id="c93a5-198">Avoid inadvertent disclosure of information</span></span>

<span data-ttu-id="c93a5-199">.NET Core katkıda bulunanlar ve başkalarının oluşturdukları .NET Core SDK bir sürümünü çalıştıran herkes kendi SDK kaynak kodu yolunu dikkate almalıdır.</span><span class="sxs-lookup"><span data-stu-id="c93a5-199">.NET Core contributors and anyone else running a version of the .NET Core SDK that they built themselves should consider the path to their SDK source code.</span></span> <span data-ttu-id="c93a5-200">Özel hata ayıklama derlemesi olan veya özel derleme sembol dosyalarıyla yapılandırılmış bir .NET Core SDK kullanırken kilitlenme oluşursa, derleme makinesinden SDK kaynak dosyası yolu, yığın izlemenin bir parçası olarak toplanır ve karma değildir.</span><span class="sxs-lookup"><span data-stu-id="c93a5-200">If a crash occurs while using a .NET Core SDK that is a custom debug build or configured with custom build symbol files, the SDK source file path from the build machine is collected as part of the stack trace and isn't hashed.</span></span>

<span data-ttu-id="c93a5-201">Bu nedenle, .NET Core SDK özel derlemeleri yol adları kişisel veya hassas bilgileri sunan dizinlerde yer içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="c93a5-201">Because of this, custom builds of the .NET Core SDK shouldn't be located in directories whose path names expose personal or sensitive information.</span></span>

## <a name="see-also"></a><span data-ttu-id="c93a5-202">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c93a5-202">See also</span></span>

- [<span data-ttu-id="c93a5-203">.NET Core CLI telemetri-2019 S2 verileri</span><span class="sxs-lookup"><span data-stu-id="c93a5-203">.NET Core CLI Telemetry - 2019 Q2 Data</span></span>](https://dotnet.microsoft.com/platform/telemetry/dotnet-core-cli-2019q2)
- [<span data-ttu-id="c93a5-204">Telemetri başvuru kaynağı (DotNet/CLI deposu)</span><span class="sxs-lookup"><span data-stu-id="c93a5-204">Telemetry reference source (dotnet/cli repository)</span></span>](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry)
