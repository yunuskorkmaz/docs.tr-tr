---
title: .NET SDK telemetrisi
description: Analiz için kullanım bilgilerini toplayan .NET SDK telemetrisi özelliklerini, hangi verilerin toplandığı ve devre dışı bırakılacağını bulun.
author: KathleenDollard
ms.date: 08/27/2019
ms.openlocfilehash: 1a863fe0c713cb49eca2968464d550eae2c9f36a
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873412"
---
# <a name="net-sdk-telemetry"></a><span data-ttu-id="6f53b-103">.NET SDK telemetrisi</span><span class="sxs-lookup"><span data-stu-id="6f53b-103">.NET SDK telemetry</span></span>

<span data-ttu-id="6f53b-104">[.NET SDK](index.md) , .net CLI kilitlenirse kullanım verilerini ve özel durum bilgilerini toplayan bir telemetri özelliği içerir.</span><span class="sxs-lookup"><span data-stu-id="6f53b-104">The [.NET SDK](index.md) includes a telemetry feature that collects usage data and exception information when the .NET CLI crashes.</span></span> <span data-ttu-id="6f53b-105">.Net CLı, .NET SDK ile birlikte gelir ve .NET uygulamalarınızı oluşturmanızı, test etmeniz ve yayımlamanıza olanak tanıyan fiiller kümesidir.</span><span class="sxs-lookup"><span data-stu-id="6f53b-105">The .NET CLI comes with the .NET SDK and is the set of verbs that enable you to build, test, and publish your .NET apps.</span></span> <span data-ttu-id="6f53b-106">.NET ekibinin, araçların iyileştirilmesi için nasıl kullanıldığını anladığından emin olmanız önemlidir.</span><span class="sxs-lookup"><span data-stu-id="6f53b-106">It's important that the .NET team understands how the tools are used so they can be improved.</span></span> <span data-ttu-id="6f53b-107">Hatalar hakkında bilgi, takımın sorunları çözmesine ve hataları düzeltmesine yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="6f53b-107">Information on failures helps the team resolve problems and fix bugs.</span></span>

<span data-ttu-id="6f53b-108">Toplanan veriler, [Creative Commons Attribution Lisansı](https://creativecommons.org/licenses/by/4.0/)kapsamında toplu olarak yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="6f53b-108">The collected data is published in aggregate under the [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span></span>

## <a name="scope"></a><span data-ttu-id="6f53b-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="6f53b-109">Scope</span></span>

<span data-ttu-id="6f53b-110">`dotnet` iki işleve sahiptir: uygulamaları çalıştırmak ve CLı komutlarını yürütmek için.</span><span class="sxs-lookup"><span data-stu-id="6f53b-110">`dotnet` has two functions: to run apps, and to execute CLI commands.</span></span> <span data-ttu-id="6f53b-111"> `dotnet` Aşağıdaki biçimde bir uygulamayı başlatmak için kullanılırken telemetri toplanmaz:</span><span class="sxs-lookup"><span data-stu-id="6f53b-111">Telemetry *isn't collected* when using `dotnet` to start an application in the following format:</span></span>

- `dotnet [path-to-app].dll`

<span data-ttu-id="6f53b-112">Telemetri, [.net CLI komutlarının](index.md)herhangi biri kullanılırken *toplanır* , örneğin:</span><span class="sxs-lookup"><span data-stu-id="6f53b-112">Telemetry *is collected* when using any of the [.NET CLI commands](index.md), such as:</span></span>

- `dotnet build`
- `dotnet pack`
- `dotnet run`

## <a name="how-to-opt-out"></a><span data-ttu-id="6f53b-113">Devre dışı bırakma</span><span class="sxs-lookup"><span data-stu-id="6f53b-113">How to opt out</span></span>

<span data-ttu-id="6f53b-114">.NET SDK telemetri özelliği varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="6f53b-114">The .NET SDK telemetry feature is enabled by default.</span></span> <span data-ttu-id="6f53b-115">Telemetri özelliğini devre dışı bırakmak için, `DOTNET_CLI_TELEMETRY_OPTOUT` ortam değişkenini veya olarak ayarlayın `1` `true` .</span><span class="sxs-lookup"><span data-stu-id="6f53b-115">To opt out of the telemetry feature, set the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span>

<span data-ttu-id="6f53b-116">Başarılı bir yükleme gerçekleştiğinde .NET SDK yükleyicisi tarafından tek bir telemetri girişi de gönderilir.</span><span class="sxs-lookup"><span data-stu-id="6f53b-116">A single telemetry entry is also sent by the .NET SDK installer when a successful installation happens.</span></span> <span data-ttu-id="6f53b-117">Devre dışı bırakmak için `DOTNET_CLI_TELEMETRY_OPTOUT` .NET SDK 'yı yüklemeden önce ortam değişkenini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6f53b-117">To opt out, set the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable before you install the .NET SDK.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6f53b-118">Yükleyiciyi başlattıktan sonra devre dışı bırakmak için: yükleyiciyi kapatın, ortam değişkenini ayarlayın ve ardından yükleyiciyi bu değer kümesiyle yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6f53b-118">To opt out after you started the installer: close the installer, set the environment variable, and then run the installer again with that value set.</span></span>

## <a name="disclosure"></a><span data-ttu-id="6f53b-119">Savunmasız</span><span class="sxs-lookup"><span data-stu-id="6f53b-119">Disclosure</span></span>

<span data-ttu-id="6f53b-120">.NET SDK, [.net CLI komutlarından](index.md) birini (örneğin,) ilk kez çalıştırdığınızda aşağıdakine benzer bir metin görüntüler `dotnet build` .</span><span class="sxs-lookup"><span data-stu-id="6f53b-120">The .NET SDK displays text similar to the following when you first run one of the [.NET CLI commands](index.md) (for example, `dotnet build`).</span></span> <span data-ttu-id="6f53b-121">Metin, çalıştırmakta olduğunuz SDK sürümüne bağlı olarak biraz farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="6f53b-121">Text may vary slightly depending on the version of the SDK you're running.</span></span> <span data-ttu-id="6f53b-122">Bu "ilk çalıştırma" deneyimi, Microsoft 'un veri toplamayı nasıl bildisidir.</span><span class="sxs-lookup"><span data-stu-id="6f53b-122">This "first run" experience is how Microsoft notifies you about data collection.</span></span>

```console
Telemetry
---------
The .NET tools collect usage data in order to help us improve your experience. The data is collected by Microsoft and shared with the community. You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry
```

<span data-ttu-id="6f53b-123">Bu iletiyi ve .NET hoş geldiniz iletisini devre dışı bırakmak için `DOTNET_NOLOGO` ortam değişkenini olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="6f53b-123">To disable this message and the .NET welcome message, set the `DOTNET_NOLOGO` environment variable to `true`.</span></span> <span data-ttu-id="6f53b-124">Bu değişkenin telemetri geri çevirme üzerinde hiçbir etkisi olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6f53b-124">Note that this variable has no effect on telemetry opt out.</span></span>

## <a name="data-points"></a><span data-ttu-id="6f53b-125">Veri noktaları</span><span class="sxs-lookup"><span data-stu-id="6f53b-125">Data points</span></span>

<span data-ttu-id="6f53b-126">Telemetri özelliği, Kullanıcı adları veya e-posta adresleri gibi kişisel verileri toplamaz.</span><span class="sxs-lookup"><span data-stu-id="6f53b-126">The telemetry feature doesn't collect personal data, such as usernames or email addresses.</span></span> <span data-ttu-id="6f53b-127">Kodunuzu taramaz ve ad, depo veya yazar gibi proje düzeyi verileri ayıklamaz.</span><span class="sxs-lookup"><span data-stu-id="6f53b-127">It doesn't scan your code and doesn't extract project-level data, such as name, repository, or author.</span></span> <span data-ttu-id="6f53b-128">Veriler, [Azure izleyici](https://azure.microsoft.com/services/monitor/) teknolojisini kullanan Microsoft sunucularına güvenli bir şekilde gönderilir, sınırlı erişim altında tutulur ve güvenli [Azure depolama](https://azure.microsoft.com/services/storage/) sistemlerinden katı güvenlik denetimleri altında yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="6f53b-128">The data is sent securely to Microsoft servers using [Azure Monitor](https://azure.microsoft.com/services/monitor/) technology, held under restricted access, and published under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

<span data-ttu-id="6f53b-129">Gizliliğinizi korumak bizim için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="6f53b-129">Protecting your privacy is important to us.</span></span> <span data-ttu-id="6f53b-130">Telemetrinin hassas verileri toplamasını veya verilerin güvenli veya uygun şekilde işlenmekte olduğunu düşünüyorsanız, [DotNet/SDK](https://github.com/dotnet/sdk/issues) deposunda bir sorun yapın veya araştırma için adresine bir e-posta gönderin [dotnet@microsoft.com](mailto:dotnet@microsoft.com) .</span><span class="sxs-lookup"><span data-stu-id="6f53b-130">If you suspect the telemetry is collecting sensitive data or the data is being insecurely or inappropriately handled, file an issue in the [dotnet/sdk](https://github.com/dotnet/sdk/issues) repository or send an email to [dotnet@microsoft.com](mailto:dotnet@microsoft.com) for investigation.</span></span>

<span data-ttu-id="6f53b-131">Telemetri özelliği aşağıdaki verileri toplar:</span><span class="sxs-lookup"><span data-stu-id="6f53b-131">The telemetry feature collects the following data:</span></span>

| <span data-ttu-id="6f53b-132">SDK sürümleri</span><span class="sxs-lookup"><span data-stu-id="6f53b-132">SDK versions</span></span> | <span data-ttu-id="6f53b-133">Veriler</span><span class="sxs-lookup"><span data-stu-id="6f53b-133">Data</span></span> |
|--------------|------|
| <span data-ttu-id="6f53b-134">Tümü</span><span class="sxs-lookup"><span data-stu-id="6f53b-134">All</span></span>          | <span data-ttu-id="6f53b-135">Çağırma zaman damgası.</span><span class="sxs-lookup"><span data-stu-id="6f53b-135">Timestamp of invocation.</span></span> |
| <span data-ttu-id="6f53b-136">Tümü</span><span class="sxs-lookup"><span data-stu-id="6f53b-136">All</span></span>          | <span data-ttu-id="6f53b-137">Komut çağrıldı (örneğin, "Build"), 2,1 'den başlayarak karma hale getirilmiş.</span><span class="sxs-lookup"><span data-stu-id="6f53b-137">Command invoked (for example, "build"), hashed starting in 2.1.</span></span> |
| <span data-ttu-id="6f53b-138">Tümü</span><span class="sxs-lookup"><span data-stu-id="6f53b-138">All</span></span>          | <span data-ttu-id="6f53b-139">Coğrafi konumu belirlemede kullanılan üç sekizli IP adresi.</span><span class="sxs-lookup"><span data-stu-id="6f53b-139">Three octet IP address used to determine the geographical location.</span></span> |
| <span data-ttu-id="6f53b-140">Tümü</span><span class="sxs-lookup"><span data-stu-id="6f53b-140">All</span></span>          | <span data-ttu-id="6f53b-141">İşletim sistemi ve sürümü.</span><span class="sxs-lookup"><span data-stu-id="6f53b-141">Operating system and version.</span></span> |
| <span data-ttu-id="6f53b-142">Tümü</span><span class="sxs-lookup"><span data-stu-id="6f53b-142">All</span></span>          | <span data-ttu-id="6f53b-143">SDK 'nın üzerinde çalıştığı çalışma zamanı KIMLIĞI (RID).</span><span class="sxs-lookup"><span data-stu-id="6f53b-143">Runtime ID (RID) the SDK is running on.</span></span> |
| <span data-ttu-id="6f53b-144">Tümü</span><span class="sxs-lookup"><span data-stu-id="6f53b-144">All</span></span>          | <span data-ttu-id="6f53b-145">.NET SDK sürümü.</span><span class="sxs-lookup"><span data-stu-id="6f53b-145">.NET SDK version.</span></span> |
| <span data-ttu-id="6f53b-146">Tümü</span><span class="sxs-lookup"><span data-stu-id="6f53b-146">All</span></span>          | <span data-ttu-id="6f53b-147">Telemetri profili: isteğe bağlı bir değer yalnızca açık Kullanıcı kabul etme ve Microsoft 'ta dahili olarak kullanılan bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="6f53b-147">Telemetry profile: an optional value only used with explicit user opt-in and used internally at Microsoft.</span></span> |
| <span data-ttu-id="6f53b-148">>= 2,0</span><span class="sxs-lookup"><span data-stu-id="6f53b-148">>=2.0</span></span>        | <span data-ttu-id="6f53b-149">Komut bağımsız değişkenleri ve seçenekleri: birkaç bağımsız değişken ve seçenek toplanır (rastgele dizeler değil).</span><span class="sxs-lookup"><span data-stu-id="6f53b-149">Command arguments and options: several arguments and options are collected (not arbitrary strings).</span></span> <span data-ttu-id="6f53b-150">[Toplanan seçeneklere](#collected-options)bakın.</span><span class="sxs-lookup"><span data-stu-id="6f53b-150">See [collected options](#collected-options).</span></span> <span data-ttu-id="6f53b-151">2.1.300 sonrasında karma hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="6f53b-151">Hashed after 2.1.300.</span></span> |
| <span data-ttu-id="6f53b-152">>= 2,0</span><span class="sxs-lookup"><span data-stu-id="6f53b-152">>=2.0</span></span>         | <span data-ttu-id="6f53b-153">SDK 'nın bir kapsayıcıda çalışıp çalışmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f53b-153">Whether the SDK is running in a container.</span></span> |
| <span data-ttu-id="6f53b-154">>= 2,0</span><span class="sxs-lookup"><span data-stu-id="6f53b-154">>=2.0</span></span>         | <span data-ttu-id="6f53b-155">`TargetFramework`2,1 ' den başlayarak karma hale getirilmiş hedef çerçeveler (olaydan).</span><span class="sxs-lookup"><span data-stu-id="6f53b-155">Target frameworks (from the `TargetFramework` event), hashed starting in 2.1.</span></span> |
| <span data-ttu-id="6f53b-156">>= 2,0</span><span class="sxs-lookup"><span data-stu-id="6f53b-156">>=2.0</span></span>         | <span data-ttu-id="6f53b-157">Karma medya Access Control (MAC) adresi (SHA256).</span><span class="sxs-lookup"><span data-stu-id="6f53b-157">Hashed Media Access Control (MAC) address (SHA256).</span></span> |
| <span data-ttu-id="6f53b-158">>= 2,0</span><span class="sxs-lookup"><span data-stu-id="6f53b-158">>=2.0</span></span>         | <span data-ttu-id="6f53b-159">Karma hale getirilmiş geçerli çalışma dizini.</span><span class="sxs-lookup"><span data-stu-id="6f53b-159">Hashed current working directory.</span></span> |
| <span data-ttu-id="6f53b-160">>= 2,0</span><span class="sxs-lookup"><span data-stu-id="6f53b-160">>=2.0</span></span>         | <span data-ttu-id="6f53b-161">Karma yükleyici exe dosya adına sahip başarı raporunu yükleme.</span><span class="sxs-lookup"><span data-stu-id="6f53b-161">Install success report, with hashed installer exe filename.</span></span> |
| <span data-ttu-id="6f53b-162">>= 2.1.300</span><span class="sxs-lookup"><span data-stu-id="6f53b-162">>=2.1.300</span></span>     | <span data-ttu-id="6f53b-163">Çekirdek sürümü.</span><span class="sxs-lookup"><span data-stu-id="6f53b-163">Kernel version.</span></span> |
| <span data-ttu-id="6f53b-164">>= 2.1.300</span><span class="sxs-lookup"><span data-stu-id="6f53b-164">>=2.1.300</span></span>     | <span data-ttu-id="6f53b-165">Libc sürümü/sürümü.</span><span class="sxs-lookup"><span data-stu-id="6f53b-165">Libc release/version.</span></span> |
| <span data-ttu-id="6f53b-166">>= 3.0.100</span><span class="sxs-lookup"><span data-stu-id="6f53b-166">>=3.0.100</span></span>     | <span data-ttu-id="6f53b-167">Çıktının yeniden yönlendirilme (true veya false).</span><span class="sxs-lookup"><span data-stu-id="6f53b-167">Whether the output was redirected (true or false).</span></span> |
| <span data-ttu-id="6f53b-168">>= 3.0.100</span><span class="sxs-lookup"><span data-stu-id="6f53b-168">>=3.0.100</span></span>     | <span data-ttu-id="6f53b-169">CLı/SDK kilitlenmesinde, özel durum türü ve yığın izlemesi (yalnızca CLı/SDK kodu, gönderilen yığın izlemesinde bulunur).</span><span class="sxs-lookup"><span data-stu-id="6f53b-169">On a CLI/SDK crash, the exception type and its stack trace (only CLI/SDK code is included in the stack trace sent).</span></span> <span data-ttu-id="6f53b-170">Daha fazla bilgi için bkz. [.net CLI/SDK kilitlenme özel durum telemetrisi toplandı](#net-clisdk-crash-exception-telemetry-collected).</span><span class="sxs-lookup"><span data-stu-id="6f53b-170">For more information, see [.NET CLI/SDK crash exception telemetry collected](#net-clisdk-crash-exception-telemetry-collected).</span></span> |

### <a name="collected-options"></a><span data-ttu-id="6f53b-171">Toplanan seçenekler</span><span class="sxs-lookup"><span data-stu-id="6f53b-171">Collected options</span></span>

<span data-ttu-id="6f53b-172">Bazı komutlar ek veriler gönderir.</span><span class="sxs-lookup"><span data-stu-id="6f53b-172">Certain commands send additional data.</span></span> <span data-ttu-id="6f53b-173">Bir komut alt kümesi ilk bağımsız değişkeni gönderir:</span><span class="sxs-lookup"><span data-stu-id="6f53b-173">A subset of commands sends the first argument:</span></span>

| <span data-ttu-id="6f53b-174">Komut</span><span class="sxs-lookup"><span data-stu-id="6f53b-174">Command</span></span>               | <span data-ttu-id="6f53b-175">Gönderilen ilk bağımsız değişken verileri</span><span class="sxs-lookup"><span data-stu-id="6f53b-175">First argument data sent</span></span>                |
|-----------------------|-----------------------------------------|
| `dotnet help <arg>`   | <span data-ttu-id="6f53b-176">İçin komut yardımı sorgulanırken.</span><span class="sxs-lookup"><span data-stu-id="6f53b-176">The command help is being queried for.</span></span>  |
| `dotnet new <arg>`    | <span data-ttu-id="6f53b-177">Şablon adı (karma).</span><span class="sxs-lookup"><span data-stu-id="6f53b-177">The template name (hashed).</span></span>             |
| `dotnet add <arg>`    | <span data-ttu-id="6f53b-178">Sözcük `package` veya `reference` .</span><span class="sxs-lookup"><span data-stu-id="6f53b-178">The word `package` or `reference`.</span></span>      |
| `dotnet remove <arg>` | <span data-ttu-id="6f53b-179">Sözcük `package` veya `reference` .</span><span class="sxs-lookup"><span data-stu-id="6f53b-179">The word `package` or `reference`.</span></span>      |
| `dotnet list <arg>`   | <span data-ttu-id="6f53b-180">Sözcük `package` veya `reference` .</span><span class="sxs-lookup"><span data-stu-id="6f53b-180">The word `package` or `reference`.</span></span>      |
| `dotnet sln <arg>`    | <span data-ttu-id="6f53b-181">, `add` Veya sözcüğü `list` `remove` .</span><span class="sxs-lookup"><span data-stu-id="6f53b-181">The word `add`, `list`, or `remove`.</span></span>    |
| `dotnet nuget <arg>`  | <span data-ttu-id="6f53b-182">, `delete` Veya sözcüğü `locals` `push` .</span><span class="sxs-lookup"><span data-stu-id="6f53b-182">The word `delete`, `locals`, or `push`.</span></span> |

<span data-ttu-id="6f53b-183">Bir komut alt kümesi, kullanıldıkları takdirde, değerleriyle birlikte, seçili seçenekleri gönderir:</span><span class="sxs-lookup"><span data-stu-id="6f53b-183">A subset of commands sends selected options if they're used, along with their values:</span></span>

| <span data-ttu-id="6f53b-184">Seçenek</span><span class="sxs-lookup"><span data-stu-id="6f53b-184">Option</span></span>                  | <span data-ttu-id="6f53b-185">Komutlar</span><span class="sxs-lookup"><span data-stu-id="6f53b-185">Commands</span></span>                                                                                       |
|-------------------------|------------------------------------------------------------------------------------------------|
| `--verbosity`           | <span data-ttu-id="6f53b-186">Tüm komutlar</span><span class="sxs-lookup"><span data-stu-id="6f53b-186">All commands</span></span>                                                                                   |
| `--language`            | `dotnet new`                                                                                   |
| `--configuration`       | <span data-ttu-id="6f53b-187">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`</span><span class="sxs-lookup"><span data-stu-id="6f53b-187">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`</span></span>                  |
| `--framework`           | <span data-ttu-id="6f53b-188">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`, `dotnet vstest`</span><span class="sxs-lookup"><span data-stu-id="6f53b-188">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`, `dotnet vstest`</span></span> |
| `--runtime`             | <span data-ttu-id="6f53b-189">`dotnet build`,  `dotnet publish`</span><span class="sxs-lookup"><span data-stu-id="6f53b-189">`dotnet build`,  `dotnet publish`</span></span>                                                              |
| `--platform`            | `dotnet vstest`                                                                                |
| `--logger`              | `dotnet vstest`                                                                                |
| `--sdk-package-version` | `dotnet migrate`                                                                               |

<span data-ttu-id="6f53b-190">Ve dışında `--verbosity` `--sdk-package-version` , diğer tüm değerler .NET Core 2.1.100 SDK ile başlayarak karma hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="6f53b-190">Except for `--verbosity` and `--sdk-package-version`, all the other values are hashed starting with .NET Core 2.1.100 SDK.</span></span>

## <a name="net-clisdk-crash-exception-telemetry-collected"></a><span data-ttu-id="6f53b-191">.NET CLı/SDK kilitlenme özel durum telemetrisi toplandı</span><span class="sxs-lookup"><span data-stu-id="6f53b-191">.NET CLI/SDK crash exception telemetry collected</span></span>

<span data-ttu-id="6f53b-192">.NET CLı/SDK kilitlenirse, CLı/SDK kodunun özel durum ve yığın izlemesinin adını toplar.</span><span class="sxs-lookup"><span data-stu-id="6f53b-192">If the .NET CLI/SDK crashes, it collects the name of the exception and stack trace of the CLI/SDK code.</span></span> <span data-ttu-id="6f53b-193">Bu bilgiler, sorunları değerlendirmek ve .NET SDK ve CLı kalitesini geliştirmek için toplanır.</span><span class="sxs-lookup"><span data-stu-id="6f53b-193">This information is collected to assess problems and improve the quality of the .NET SDK and CLI.</span></span> <span data-ttu-id="6f53b-194">Bu makalede Topladığımız veriler hakkında bilgi sağlanır.</span><span class="sxs-lookup"><span data-stu-id="6f53b-194">This article provides information about the data we collect.</span></span> <span data-ttu-id="6f53b-195">Ayrıca, kullanıcıların .NET SDK 'nın kendi sürümünü oluşturmayla ilgili ipuçları, kişisel veya hassas bilgilerin yanlışlıkla açıklanmasını önleyebilir.</span><span class="sxs-lookup"><span data-stu-id="6f53b-195">It also provides tips on how users building their own version of the .NET SDK can avoid inadvertent disclosure of personal or sensitive information.</span></span>

### <a name="types-of-collected-data"></a><span data-ttu-id="6f53b-196">Toplanan veri türleri</span><span class="sxs-lookup"><span data-stu-id="6f53b-196">Types of collected data</span></span>

<span data-ttu-id="6f53b-197">.NET CLı, uygulamanızda özel durumlar değil yalnızca CLı/SDK özel durumları için bilgi toplar.</span><span class="sxs-lookup"><span data-stu-id="6f53b-197">.NET CLI collects information for CLI/SDK exceptions only, not exceptions in your application.</span></span> <span data-ttu-id="6f53b-198">Toplanan veriler, özel durumun ve yığın izlemenin adını içerir.</span><span class="sxs-lookup"><span data-stu-id="6f53b-198">The collected data contains the name of the exception and the stack trace.</span></span> <span data-ttu-id="6f53b-199">Bu yığın izlemesi CLı/SDK kodudur.</span><span class="sxs-lookup"><span data-stu-id="6f53b-199">This stack trace is of CLI/SDK code.</span></span>

<span data-ttu-id="6f53b-200">Aşağıdaki örnek, toplanan veri türünü gösterir:</span><span class="sxs-lookup"><span data-stu-id="6f53b-200">The following example shows the kind of data that is collected:</span></span>

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

### <a name="avoid-inadvertent-disclosure-of-information"></a><span data-ttu-id="6f53b-201">Bilgilerin yanlışlıkla açıklanmasını önleyin</span><span class="sxs-lookup"><span data-stu-id="6f53b-201">Avoid inadvertent disclosure of information</span></span>

<span data-ttu-id="6f53b-202">.NET SDK 'sının kendi kendilerini oluşturdukları bir .NET SDK sürümü çalıştıran herkes, SDK kaynak kodu yolunu kabul etmelidir.</span><span class="sxs-lookup"><span data-stu-id="6f53b-202">.NET contributors and anyone else running a version of the .NET SDK that they built themselves should consider the path to their SDK source code.</span></span> <span data-ttu-id="6f53b-203">Özel hata ayıklama derlemesi olan veya özel derleme sembol dosyalarıyla yapılandırılmış bir .NET SDK kullanırken kilitlenme oluşursa, derleme makinesinden SDK kaynak dosyası yolu, yığın izlemenin bir parçası olarak toplanır ve karma değildir.</span><span class="sxs-lookup"><span data-stu-id="6f53b-203">If a crash occurs while using a .NET SDK that is a custom debug build or configured with custom build symbol files, the SDK source file path from the build machine is collected as part of the stack trace and isn't hashed.</span></span>

<span data-ttu-id="6f53b-204">Bu nedenle, .NET SDK 'nın özel derlemeleri yol adları kişisel veya hassas bilgileri sunan dizinlerde yer içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="6f53b-204">Because of this, custom builds of the .NET SDK shouldn't be located in directories whose path names expose personal or sensitive information.</span></span>

## <a name="see-also"></a><span data-ttu-id="6f53b-205">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f53b-205">See also</span></span>

- [<span data-ttu-id="6f53b-206">.NET CLı telemetri verileri</span><span class="sxs-lookup"><span data-stu-id="6f53b-206">.NET CLI Telemetry Data</span></span>](https://dotnet.microsoft.com/platform/telemetry)
- [<span data-ttu-id="6f53b-207">Telemetri başvuru kaynağı (DotNet/SDK deposu)</span><span class="sxs-lookup"><span data-stu-id="6f53b-207">Telemetry reference source (dotnet/sdk repository)</span></span>](https://github.com/dotnet/sdk/tree/main/src/Cli/dotnet/Telemetry)
