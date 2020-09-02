---
title: .NET Core SDK telemetri
description: Analiz için kullanım bilgilerini toplayan, hangi verilerin toplandığı ve devre dışı bırakılacağı .NET Core SDK telemetri özelliklerini bulun.
author: KathleenDollard
ms.date: 08/27/2019
ms.openlocfilehash: 01376cabc4f59f64c59a78dcff061fb6ec11e3c3
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89359239"
---
# <a name="net-core-sdk-telemetry"></a><span data-ttu-id="29263-103">.NET Core SDK telemetri</span><span class="sxs-lookup"><span data-stu-id="29263-103">.NET Core SDK telemetry</span></span>

<span data-ttu-id="29263-104">[.NET Core SDK](index.md) , .NET Core CLI çöktüğünde kullanım verilerini ve özel durum bilgilerini toplayan bir telemetri özelliği içerir.</span><span class="sxs-lookup"><span data-stu-id="29263-104">The [.NET Core SDK](index.md) includes a telemetry feature that collects usage data and exception information when the .NET Core CLI crashes.</span></span> <span data-ttu-id="29263-105">.NET Core CLI .NET Core SDK ile birlikte gelir ve .NET Core uygulamalarınızı oluşturmanızı, test etmeniz ve yayımlamanıza olanak tanıyan fiiller kümesidir.</span><span class="sxs-lookup"><span data-stu-id="29263-105">The .NET Core CLI comes with the .NET Core SDK and is the set of verbs that enable you to build, test, and publish your .NET Core apps.</span></span> <span data-ttu-id="29263-106">.NET ekibinin, araçların iyileştirilmesi için nasıl kullanıldığını anladığından emin olmanız önemlidir.</span><span class="sxs-lookup"><span data-stu-id="29263-106">It's important that the .NET team understands how the tools are used so they can be improved.</span></span> <span data-ttu-id="29263-107">Hatalar hakkında bilgi, takımın sorunları çözmesine ve hataları düzeltmesine yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="29263-107">Information on failures helps the team resolve problems and fix bugs.</span></span>

<span data-ttu-id="29263-108">Toplanan veriler anonimdir ve [Creative Commons Attribution Lisansı](https://creativecommons.org/licenses/by/4.0/)kapsamında toplu olarak yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="29263-108">The collected data is anonymous and published in aggregate under the [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span></span>

## <a name="scope"></a><span data-ttu-id="29263-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="29263-109">Scope</span></span>

<span data-ttu-id="29263-110">`dotnet` iki işleve sahiptir: uygulamaları çalıştırmak ve CLı komutlarını yürütmek için.</span><span class="sxs-lookup"><span data-stu-id="29263-110">`dotnet` has two functions: to run apps, and to execute CLI commands.</span></span> <span data-ttu-id="29263-111">*isn't collected* `dotnet` Aşağıdaki biçimde bir uygulamayı başlatmak için kullanılırken telemetri toplanmaz:</span><span class="sxs-lookup"><span data-stu-id="29263-111">Telemetry *isn't collected* when using `dotnet` to start an application in the following format:</span></span>

- `dotnet [path-to-app].dll`

<span data-ttu-id="29263-112">Telemetri, şöyle [.NET Core CLI komutlardan](index.md)biri kullanılarak *toplanır* :</span><span class="sxs-lookup"><span data-stu-id="29263-112">Telemetry *is collected* when using any of the [.NET Core CLI commands](index.md), such as:</span></span>

- `dotnet build`
- `dotnet pack`
- `dotnet run`

## <a name="how-to-opt-out"></a><span data-ttu-id="29263-113">Devre dışı bırakma</span><span class="sxs-lookup"><span data-stu-id="29263-113">How to opt out</span></span>

<span data-ttu-id="29263-114">.NET Core SDK telemetri özelliği varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="29263-114">The .NET Core SDK telemetry feature is enabled by default.</span></span> <span data-ttu-id="29263-115">Telemetri özelliğini devre dışı bırakmak için, `DOTNET_CLI_TELEMETRY_OPTOUT` ortam değişkenini veya olarak ayarlayın `1` `true` .</span><span class="sxs-lookup"><span data-stu-id="29263-115">To opt out of the telemetry feature, set the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span>

<span data-ttu-id="29263-116">Başarılı bir yükleme gerçekleştiğinde .NET Core SDK yükleyicisi tarafından tek bir telemetri girişi de gönderilir.</span><span class="sxs-lookup"><span data-stu-id="29263-116">A single telemetry entry is also sent by the .NET Core SDK installer when a successful installation happens.</span></span> <span data-ttu-id="29263-117">Devre dışı bırakmak için, `DOTNET_CLI_TELEMETRY_OPTOUT` .NET Core SDK yüklemeden önce ortam değişkenini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="29263-117">To opt out, set the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable before you install the .NET Core SDK.</span></span>

## <a name="disclosure"></a><span data-ttu-id="29263-118">Savunmasız</span><span class="sxs-lookup"><span data-stu-id="29263-118">Disclosure</span></span>

<span data-ttu-id="29263-119">.NET Core SDK, [.NET Core CLI komutlarından](index.md) birini (örneğin,) ilk kez çalıştırdığınızda aşağıdakine benzer metni görüntüler `dotnet build` .</span><span class="sxs-lookup"><span data-stu-id="29263-119">The .NET Core SDK displays text similar to the following when you first run one of the [.NET Core CLI commands](index.md) (for example, `dotnet build`).</span></span> <span data-ttu-id="29263-120">Metin, çalıştırmakta olduğunuz SDK sürümüne bağlı olarak biraz farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="29263-120">Text may vary slightly depending on the version of the SDK you're running.</span></span> <span data-ttu-id="29263-121">Bu "ilk çalıştırma" deneyimi, Microsoft 'un veri toplamayı nasıl bildisidir.</span><span class="sxs-lookup"><span data-stu-id="29263-121">This "first run" experience is how Microsoft notifies you about data collection.</span></span>

```console
Telemetry
---------
The .NET Core tools collect usage data in order to help us improve your experience. The data is anonymous. It is collected by Microsoft and shared with the community. You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET Core CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry
```

<span data-ttu-id="29263-122">Bu iletiyi ve .NET Core hoş geldiniz iletisini devre dışı bırakmak için, `DOTNET_NOLOGO` ortam değişkenini olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="29263-122">To disable this message and the .NET Core welcome message, set the `DOTNET_NOLOGO` environment variable to `true`.</span></span> <span data-ttu-id="29263-123">Bu değişkenin telemetri geri çevirme üzerinde hiçbir etkisi olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="29263-123">Note that this variable has no effect on telemetry opt out.</span></span>

## <a name="data-points"></a><span data-ttu-id="29263-124">Veri noktaları</span><span class="sxs-lookup"><span data-stu-id="29263-124">Data points</span></span>

<span data-ttu-id="29263-125">Telemetri özelliği, Kullanıcı adları veya e-posta adresleri gibi kişisel verileri toplamaz.</span><span class="sxs-lookup"><span data-stu-id="29263-125">The telemetry feature doesn't collect personal data, such as usernames or email addresses.</span></span> <span data-ttu-id="29263-126">Kodunuzu taramaz ve ad, depo veya yazar gibi proje düzeyi verileri ayıklamaz.</span><span class="sxs-lookup"><span data-stu-id="29263-126">It doesn't scan your code and doesn't extract project-level data, such as name, repository, or author.</span></span> <span data-ttu-id="29263-127">Veriler, [Azure izleyici](https://azure.microsoft.com/services/monitor/) teknolojisini kullanan Microsoft sunucularına güvenli bir şekilde gönderilir, sınırlı erişim altında tutulur ve güvenli [Azure depolama](https://azure.microsoft.com/services/storage/) sistemlerinden katı güvenlik denetimleri altında yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="29263-127">The data is sent securely to Microsoft servers using [Azure Monitor](https://azure.microsoft.com/services/monitor/) technology, held under restricted access, and published under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

<span data-ttu-id="29263-128">Gizliliğinizi korumak bizim için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="29263-128">Protecting your privacy is important to us.</span></span> <span data-ttu-id="29263-129">Telemetrinin hassas verileri toplamasını veya verilerin güvenli veya uygun şekilde işlenmekte olduğunu düşünüyorsanız, [DotNet/SDK](https://github.com/dotnet/sdk/issues) deposunda bir sorun yapın veya araştırma için adresine bir e-posta gönderin [dotnet@microsoft.com](mailto:dotnet@microsoft.com) .</span><span class="sxs-lookup"><span data-stu-id="29263-129">If you suspect the telemetry is collecting sensitive data or the data is being insecurely or inappropriately handled, file an issue in the [dotnet/sdk](https://github.com/dotnet/sdk/issues) repository or send an email to [dotnet@microsoft.com](mailto:dotnet@microsoft.com) for investigation.</span></span>

<span data-ttu-id="29263-130">Telemetri özelliği aşağıdaki verileri toplar:</span><span class="sxs-lookup"><span data-stu-id="29263-130">The telemetry feature collects the following data:</span></span>

| <span data-ttu-id="29263-131">SDK sürümleri</span><span class="sxs-lookup"><span data-stu-id="29263-131">SDK versions</span></span> | <span data-ttu-id="29263-132">Veriler</span><span class="sxs-lookup"><span data-stu-id="29263-132">Data</span></span> |
|--------------|------|
| <span data-ttu-id="29263-133">Tümü</span><span class="sxs-lookup"><span data-stu-id="29263-133">All</span></span>          | <span data-ttu-id="29263-134">Çağırma zaman damgası.</span><span class="sxs-lookup"><span data-stu-id="29263-134">Timestamp of invocation.</span></span> |
| <span data-ttu-id="29263-135">Tümü</span><span class="sxs-lookup"><span data-stu-id="29263-135">All</span></span>          | <span data-ttu-id="29263-136">Komut çağrıldı (örneğin, "Build"), 2,1 'den başlayarak karma hale getirilmiş.</span><span class="sxs-lookup"><span data-stu-id="29263-136">Command invoked (for example, "build"), hashed starting in 2.1.</span></span> |
| <span data-ttu-id="29263-137">Tümü</span><span class="sxs-lookup"><span data-stu-id="29263-137">All</span></span>          | <span data-ttu-id="29263-138">Coğrafi konumu belirlemede kullanılan üç sekizli IP adresi.</span><span class="sxs-lookup"><span data-stu-id="29263-138">Three octet IP address used to determine the geographical location.</span></span> |
| <span data-ttu-id="29263-139">Tümü</span><span class="sxs-lookup"><span data-stu-id="29263-139">All</span></span>          | <span data-ttu-id="29263-140">İşletim sistemi ve sürümü.</span><span class="sxs-lookup"><span data-stu-id="29263-140">Operating system and version.</span></span> |
| <span data-ttu-id="29263-141">Tümü</span><span class="sxs-lookup"><span data-stu-id="29263-141">All</span></span>          | <span data-ttu-id="29263-142">SDK 'nın üzerinde çalıştığı çalışma zamanı KIMLIĞI (RID).</span><span class="sxs-lookup"><span data-stu-id="29263-142">Runtime ID (RID) the SDK is running on.</span></span> |
| <span data-ttu-id="29263-143">Tümü</span><span class="sxs-lookup"><span data-stu-id="29263-143">All</span></span>          | <span data-ttu-id="29263-144">.NET Core SDK sürümü.</span><span class="sxs-lookup"><span data-stu-id="29263-144">.NET Core SDK version.</span></span> |
| <span data-ttu-id="29263-145">Tümü</span><span class="sxs-lookup"><span data-stu-id="29263-145">All</span></span>          | <span data-ttu-id="29263-146">Telemetri profili: isteğe bağlı bir değer yalnızca açık Kullanıcı kabul etme ve Microsoft 'ta dahili olarak kullanılan bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="29263-146">Telemetry profile: an optional value only used with explicit user opt-in and used internally at Microsoft.</span></span> |
| <span data-ttu-id="29263-147">>= 2,0</span><span class="sxs-lookup"><span data-stu-id="29263-147">>=2.0</span></span>        | <span data-ttu-id="29263-148">Komut bağımsız değişkenleri ve seçenekleri: birkaç bağımsız değişken ve seçenek toplanır (rastgele dizeler değil).</span><span class="sxs-lookup"><span data-stu-id="29263-148">Command arguments and options: several arguments and options are collected (not arbitrary strings).</span></span> <span data-ttu-id="29263-149">[Toplanan seçeneklere](#collected-options)bakın.</span><span class="sxs-lookup"><span data-stu-id="29263-149">See [collected options](#collected-options).</span></span> <span data-ttu-id="29263-150">2.1.300 sonrasında karma hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="29263-150">Hashed after 2.1.300.</span></span> |
| <span data-ttu-id="29263-151">>= 2,0</span><span class="sxs-lookup"><span data-stu-id="29263-151">>=2.0</span></span>         | <span data-ttu-id="29263-152">SDK 'nın bir kapsayıcıda çalışıp çalışmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="29263-152">Whether the SDK is running in a container.</span></span> |
| <span data-ttu-id="29263-153">>= 2,0</span><span class="sxs-lookup"><span data-stu-id="29263-153">>=2.0</span></span>         | <span data-ttu-id="29263-154">`TargetFramework`2,1 ' den başlayarak karma hale getirilmiş hedef çerçeveler (olaydan).</span><span class="sxs-lookup"><span data-stu-id="29263-154">Target frameworks (from the `TargetFramework` event), hashed starting in 2.1.</span></span> |
| <span data-ttu-id="29263-155">>= 2,0</span><span class="sxs-lookup"><span data-stu-id="29263-155">>=2.0</span></span>         | <span data-ttu-id="29263-156">Karma medya Access Control (MAC) adresi: bir makine için bir şifreleme (SHA256) anonim ve benzersiz KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="29263-156">Hashed Media Access Control (MAC) address: a cryptographically (SHA256) anonymous and unique ID for a machine.</span></span> |
| <span data-ttu-id="29263-157">>= 2,0</span><span class="sxs-lookup"><span data-stu-id="29263-157">>=2.0</span></span>         | <span data-ttu-id="29263-158">Karma hale getirilmiş geçerli çalışma dizini.</span><span class="sxs-lookup"><span data-stu-id="29263-158">Hashed current working directory.</span></span> |
| <span data-ttu-id="29263-159">>= 2,0</span><span class="sxs-lookup"><span data-stu-id="29263-159">>=2.0</span></span>         | <span data-ttu-id="29263-160">Karma yükleyici exe dosya adına sahip başarı raporunu yükleme.</span><span class="sxs-lookup"><span data-stu-id="29263-160">Install success report, with hashed installer exe filename.</span></span> |
| <span data-ttu-id="29263-161">>= 2.1.300</span><span class="sxs-lookup"><span data-stu-id="29263-161">>=2.1.300</span></span>     | <span data-ttu-id="29263-162">Çekirdek sürümü.</span><span class="sxs-lookup"><span data-stu-id="29263-162">Kernel version.</span></span> |
| <span data-ttu-id="29263-163">>= 2.1.300</span><span class="sxs-lookup"><span data-stu-id="29263-163">>=2.1.300</span></span>     | <span data-ttu-id="29263-164">Libc sürümü/sürümü.</span><span class="sxs-lookup"><span data-stu-id="29263-164">Libc release/version.</span></span> |
| <span data-ttu-id="29263-165">>= 3.0.100</span><span class="sxs-lookup"><span data-stu-id="29263-165">>=3.0.100</span></span>     | <span data-ttu-id="29263-166">Çıktının yeniden yönlendirilme (true veya false).</span><span class="sxs-lookup"><span data-stu-id="29263-166">Whether the output was redirected (true or false).</span></span> |
| <span data-ttu-id="29263-167">>= 3.0.100</span><span class="sxs-lookup"><span data-stu-id="29263-167">>=3.0.100</span></span>     | <span data-ttu-id="29263-168">CLı/SDK kilitlenmesinde, özel durum türü ve yığın izlemesi (yalnızca CLı/SDK kodu, gönderilen yığın izlemesinde bulunur).</span><span class="sxs-lookup"><span data-stu-id="29263-168">On a CLI/SDK crash, the exception type and its stack trace (only CLI/SDK code is included in the stack trace sent).</span></span> <span data-ttu-id="29263-169">Daha fazla bilgi için bkz. [.NET Core CLI/SDK kilitlenme özel durum telemetrisi toplandı](#net-core-clisdk-crash-exception-telemetry-collected).</span><span class="sxs-lookup"><span data-stu-id="29263-169">For more information, see [.NET Core CLI/SDK crash exception telemetry collected](#net-core-clisdk-crash-exception-telemetry-collected).</span></span> |

### <a name="collected-options"></a><span data-ttu-id="29263-170">Toplanan seçenekler</span><span class="sxs-lookup"><span data-stu-id="29263-170">Collected options</span></span>

<span data-ttu-id="29263-171">Bazı komutlar ek veriler gönderir.</span><span class="sxs-lookup"><span data-stu-id="29263-171">Certain commands send additional data.</span></span> <span data-ttu-id="29263-172">Bir komut alt kümesi ilk bağımsız değişkeni gönderir:</span><span class="sxs-lookup"><span data-stu-id="29263-172">A subset of commands sends the first argument:</span></span>

| <span data-ttu-id="29263-173">Komut</span><span class="sxs-lookup"><span data-stu-id="29263-173">Command</span></span>               | <span data-ttu-id="29263-174">Gönderilen ilk bağımsız değişken verileri</span><span class="sxs-lookup"><span data-stu-id="29263-174">First argument data sent</span></span>                |
|-----------------------|-----------------------------------------|
| `dotnet help <arg>`   | <span data-ttu-id="29263-175">İçin komut yardımı sorgulanırken.</span><span class="sxs-lookup"><span data-stu-id="29263-175">The command help is being queried for.</span></span>  |
| `dotnet new <arg>`    | <span data-ttu-id="29263-176">Şablon adı (karma).</span><span class="sxs-lookup"><span data-stu-id="29263-176">The template name (hashed).</span></span>             |
| `dotnet add <arg>`    | <span data-ttu-id="29263-177">Sözcük `package` veya `reference` .</span><span class="sxs-lookup"><span data-stu-id="29263-177">The word `package` or `reference`.</span></span>      |
| `dotnet remove <arg>` | <span data-ttu-id="29263-178">Sözcük `package` veya `reference` .</span><span class="sxs-lookup"><span data-stu-id="29263-178">The word `package` or `reference`.</span></span>      |
| `dotnet list <arg>`   | <span data-ttu-id="29263-179">Sözcük `package` veya `reference` .</span><span class="sxs-lookup"><span data-stu-id="29263-179">The word `package` or `reference`.</span></span>      |
| `dotnet sln <arg>`    | <span data-ttu-id="29263-180">, `add` Veya sözcüğü `list` `remove` .</span><span class="sxs-lookup"><span data-stu-id="29263-180">The word `add`, `list`, or `remove`.</span></span>    |
| `dotnet nuget <arg>`  | <span data-ttu-id="29263-181">, `delete` Veya sözcüğü `locals` `push` .</span><span class="sxs-lookup"><span data-stu-id="29263-181">The word `delete`, `locals`, or `push`.</span></span> |

<span data-ttu-id="29263-182">Bir komut alt kümesi, kullanıldıkları takdirde, değerleriyle birlikte, seçili seçenekleri gönderir:</span><span class="sxs-lookup"><span data-stu-id="29263-182">A subset of commands sends selected options if they're used, along with their values:</span></span>

| <span data-ttu-id="29263-183">Seçenek</span><span class="sxs-lookup"><span data-stu-id="29263-183">Option</span></span>                  | <span data-ttu-id="29263-184">Komutlar</span><span class="sxs-lookup"><span data-stu-id="29263-184">Commands</span></span>                                                                                       |
|-------------------------|------------------------------------------------------------------------------------------------|
| `--verbosity`           | <span data-ttu-id="29263-185">Tüm komutlar</span><span class="sxs-lookup"><span data-stu-id="29263-185">All commands</span></span>                                                                                   |
| `--language`            | `dotnet new`                                                                                   |
| `--configuration`       | <span data-ttu-id="29263-186">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`</span><span class="sxs-lookup"><span data-stu-id="29263-186">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`</span></span>                  |
| `--framework`           | <span data-ttu-id="29263-187">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`, `dotnet vstest`</span><span class="sxs-lookup"><span data-stu-id="29263-187">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`, `dotnet vstest`</span></span> |
| `--runtime`             | <span data-ttu-id="29263-188">`dotnet build`,  `dotnet publish`</span><span class="sxs-lookup"><span data-stu-id="29263-188">`dotnet build`,  `dotnet publish`</span></span>                                                              |
| `--platform`            | `dotnet vstest`                                                                                |
| `--logger`              | `dotnet vstest`                                                                                |
| `--sdk-package-version` | `dotnet migrate`                                                                               |

<span data-ttu-id="29263-189">Ve dışında `--verbosity` `--sdk-package-version` , diğer tüm değerler .NET Core 2.1.100 SDK ile başlayarak karma hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="29263-189">Except for `--verbosity` and `--sdk-package-version`, all the other values are hashed starting with .NET Core 2.1.100 SDK.</span></span>

## <a name="net-core-clisdk-crash-exception-telemetry-collected"></a><span data-ttu-id="29263-190">.NET Core CLI/SDK kilitlenme özel durum telemetrisi toplandı</span><span class="sxs-lookup"><span data-stu-id="29263-190">.NET Core CLI/SDK crash exception telemetry collected</span></span>

<span data-ttu-id="29263-191">.NET Core CLI/SDK kilitlenirse, CLı/SDK kodunun özel durum ve yığın izlemesinin adını toplar.</span><span class="sxs-lookup"><span data-stu-id="29263-191">If the .NET Core CLI/SDK crashes, it collects the name of the exception and stack trace of the CLI/SDK code.</span></span> <span data-ttu-id="29263-192">Bu bilgiler, sorunları değerlendirmek ve .NET Core SDK ve CLı kalitesini geliştirmek için toplanır.</span><span class="sxs-lookup"><span data-stu-id="29263-192">This information is collected to assess problems and improve the quality of the .NET Core SDK and CLI.</span></span> <span data-ttu-id="29263-193">Bu makalede Topladığımız veriler hakkında bilgi sağlanır.</span><span class="sxs-lookup"><span data-stu-id="29263-193">This article provides information about the data we collect.</span></span> <span data-ttu-id="29263-194">Ayrıca, kullanıcıların kendi .NET Core SDK kendi sürümünü oluşturma konusunda ipuçları, kişisel veya hassas bilgilerin yanlışlıkla açıklanmasını önleyebilir.</span><span class="sxs-lookup"><span data-stu-id="29263-194">It also provides tips on how users building their own version of the .NET Core SDK can avoid inadvertent disclosure of personal or sensitive information.</span></span>

### <a name="types-of-collected-data"></a><span data-ttu-id="29263-195">Toplanan veri türleri</span><span class="sxs-lookup"><span data-stu-id="29263-195">Types of collected data</span></span>

<span data-ttu-id="29263-196">.NET Core CLI, uygulamanızda özel durumlar değil yalnızca CLı/SDK özel durumları için bilgi toplar.</span><span class="sxs-lookup"><span data-stu-id="29263-196">.NET Core CLI collects information for CLI/SDK exceptions only, not exceptions in your application.</span></span> <span data-ttu-id="29263-197">Toplanan veriler, özel durumun ve yığın izlemenin adını içerir.</span><span class="sxs-lookup"><span data-stu-id="29263-197">The collected data contains the name of the exception and the stack trace.</span></span> <span data-ttu-id="29263-198">Bu yığın izlemesi CLı/SDK kodudur.</span><span class="sxs-lookup"><span data-stu-id="29263-198">This stack trace is of CLI/SDK code.</span></span>

<span data-ttu-id="29263-199">Aşağıdaki örnek, toplanan veri türünü gösterir:</span><span class="sxs-lookup"><span data-stu-id="29263-199">The following example shows the kind of data that is collected:</span></span>

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

### <a name="avoid-inadvertent-disclosure-of-information"></a><span data-ttu-id="29263-200">Bilgilerin yanlışlıkla açıklanmasını önleyin</span><span class="sxs-lookup"><span data-stu-id="29263-200">Avoid inadvertent disclosure of information</span></span>

<span data-ttu-id="29263-201">.NET Core katkıda bulunanlar ve başkalarının oluşturdukları .NET Core SDK bir sürümünü çalıştıran herkes kendi SDK kaynak kodu yolunu dikkate almalıdır.</span><span class="sxs-lookup"><span data-stu-id="29263-201">.NET Core contributors and anyone else running a version of the .NET Core SDK that they built themselves should consider the path to their SDK source code.</span></span> <span data-ttu-id="29263-202">Özel hata ayıklama derlemesi olan veya özel derleme sembol dosyalarıyla yapılandırılmış bir .NET Core SDK kullanırken kilitlenme oluşursa, derleme makinesinden SDK kaynak dosyası yolu, yığın izlemenin bir parçası olarak toplanır ve karma değildir.</span><span class="sxs-lookup"><span data-stu-id="29263-202">If a crash occurs while using a .NET Core SDK that is a custom debug build or configured with custom build symbol files, the SDK source file path from the build machine is collected as part of the stack trace and isn't hashed.</span></span>

<span data-ttu-id="29263-203">Bu nedenle, .NET Core SDK özel derlemeleri yol adları kişisel veya hassas bilgileri sunan dizinlerde yer içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="29263-203">Because of this, custom builds of the .NET Core SDK shouldn't be located in directories whose path names expose personal or sensitive information.</span></span>

## <a name="see-also"></a><span data-ttu-id="29263-204">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29263-204">See also</span></span>

- [<span data-ttu-id="29263-205">Telemetri verileri .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="29263-205">.NET Core CLI Telemetry Data</span></span>](https://dotnet.microsoft.com/platform/telemetry)
- [<span data-ttu-id="29263-206">Telemetri başvuru kaynağı (DotNet/SDK deposu)</span><span class="sxs-lookup"><span data-stu-id="29263-206">Telemetry reference source (dotnet/sdk repository)</span></span>](https://github.com/dotnet/sdk/tree/master/src/Cli/dotnet/Telemetry)
