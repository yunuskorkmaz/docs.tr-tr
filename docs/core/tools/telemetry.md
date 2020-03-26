---
title: .NET Çekirdek SDK telemetri
description: Analiz için kullanım bilgilerini toplayan .NET Core SDK telemetri özelliklerini, hangi verilerin toplandığını ve nasıl devre dışı kalındığını keşfedin.
author: KathleenDollard
ms.date: 08/27/2019
ms.openlocfilehash: a79b791abc99331ff39f5e281ee0fdc62b258989
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507288"
---
# <a name="net-core-sdk-telemetry"></a><span data-ttu-id="d84b6-103">.NET Çekirdek SDK telemetri</span><span class="sxs-lookup"><span data-stu-id="d84b6-103">.NET Core SDK telemetry</span></span>

<span data-ttu-id="d84b6-104">[.NET Core SDK, .NET Core](index.md) CLI çöktüğinde kullanım verilerini ve özel durum bilgilerini toplayan bir telemetri özelliği içerir.</span><span class="sxs-lookup"><span data-stu-id="d84b6-104">The [.NET Core SDK](index.md) includes a telemetry feature that collects usage data and exception information when the .NET Core CLI crashes.</span></span> <span data-ttu-id="d84b6-105">.NET Core CLI .NET Core SDK ile birlikte gelir ve .NET Core uygulamalarınızı oluşturmanızı, test etmenizi ve yayınlamanızı sağlayan fiiller kümesidir.</span><span class="sxs-lookup"><span data-stu-id="d84b6-105">The .NET Core CLI comes with the .NET Core SDK and is the set of verbs that enable you to build, test, and publish your .NET Core apps.</span></span> <span data-ttu-id="d84b6-106">.NET ekibinin araçların nasıl kullanıldığını anlayıp geliştirilmelerini laması önemlidir.</span><span class="sxs-lookup"><span data-stu-id="d84b6-106">It's important that the .NET team understands how the tools are used so they can be improved.</span></span> <span data-ttu-id="d84b6-107">Hatalar la ilgili bilgiler, takımın sorunları çözmesi ve hataları düzeltmesi yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="d84b6-107">Information on failures helps the team resolve problems and fix bugs.</span></span>

<span data-ttu-id="d84b6-108">Toplanan veriler anonimdir ve [Creative Commons Atıf Lisansı](https://creativecommons.org/licenses/by/4.0/)altında toplu olarak yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="d84b6-108">The collected data is anonymous and published in aggregate under the [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span></span>

## <a name="scope"></a><span data-ttu-id="d84b6-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="d84b6-109">Scope</span></span>

<span data-ttu-id="d84b6-110">`dotnet`uygulamaları çalıştırmak ve CLI komutlarını yürütmek için iki işlevi vardır.</span><span class="sxs-lookup"><span data-stu-id="d84b6-110">`dotnet` has two functions: to run apps, and to execute CLI commands.</span></span> <span data-ttu-id="d84b6-111">Bir uygulamayı aşağıdaki biçimde başlatmak `dotnet` için kullanırken telemetri *toplanmaz:*</span><span class="sxs-lookup"><span data-stu-id="d84b6-111">Telemetry *isn't collected* when using `dotnet` to start an application in the following format:</span></span>

- `dotnet [path-to-app].dll`

<span data-ttu-id="d84b6-112">Telemetri,.NET [Core CLI komutlarından](index.md)herhangi biri (örneğin) kullanılarak *toplanır:*</span><span class="sxs-lookup"><span data-stu-id="d84b6-112">Telemetry *is collected* when using any of the [.NET Core CLI commands](index.md), such as:</span></span>

- `dotnet build`
- `dotnet pack`
- `dotnet run`

## <a name="how-to-opt-out"></a><span data-ttu-id="d84b6-113">Nasıl devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="d84b6-113">How to opt out</span></span>

<span data-ttu-id="d84b6-114">.NET Core SDK telemetri özelliği varsayılan olarak etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d84b6-114">The .NET Core SDK telemetry feature is enabled by default.</span></span> <span data-ttu-id="d84b6-115">Telemetri özelliğini devre dışı bırakmak `DOTNET_CLI_TELEMETRY_OPTOUT` için `1` ortam `true`değişkenini veya '</span><span class="sxs-lookup"><span data-stu-id="d84b6-115">To opt out of the telemetry feature, set the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span>

<span data-ttu-id="d84b6-116">Başarılı bir yükleme gerçekleştiğinde .NET Core SDK yükleyicisi tarafından da tek bir telemetri girişi gönderilir.</span><span class="sxs-lookup"><span data-stu-id="d84b6-116">A single telemetry entry is also sent by the .NET Core SDK installer when a successful installation happens.</span></span> <span data-ttu-id="d84b6-117">Devre dışı bırakmak `DOTNET_CLI_TELEMETRY_OPTOUT` için ,.NET Core SDK'yı yüklemeden önce ortam değişkenini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d84b6-117">To opt out, set the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable before you install the .NET Core SDK.</span></span>

## <a name="disclosure"></a><span data-ttu-id="d84b6-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d84b6-118">Disclosure</span></span>

<span data-ttu-id="d84b6-119">.NET Core SDK, [.NET Core CLI komutlarından](index.md) birini ilk çalıştırdığınızda (örneğin, `dotnet build`aşağıdakilere benzer bir metin görüntüler).</span><span class="sxs-lookup"><span data-stu-id="d84b6-119">The .NET Core SDK displays text similar to the following when you first run one of the [.NET Core CLI commands](index.md) (for example, `dotnet build`).</span></span> <span data-ttu-id="d84b6-120">Metin, çalıştırdığınız SDK sürümüne bağlı olarak biraz değişiklik gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="d84b6-120">Text may vary slightly depending on the version of the SDK you're running.</span></span> <span data-ttu-id="d84b6-121">Bu "ilk çalıştırma" deneyimi, Microsoft'un veri toplama hakkında sizi nasıl bilgi edindiğini ortaya attırdığıdır.</span><span class="sxs-lookup"><span data-stu-id="d84b6-121">This "first run" experience is how Microsoft notifies you about data collection.</span></span>

```console
Telemetry
---------
The .NET Core tools collect usage data in order to help us improve your experience. The data is anonymous. It is collected by Microsoft and shared with the community. You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET Core CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry
```

<span data-ttu-id="d84b6-122">Bu iletiyi ve .NET Core karşılama iletisini devre dışı kılabilir, ortam değişkenini `DOTNET_NOLOGO` `true`.</span><span class="sxs-lookup"><span data-stu-id="d84b6-122">To disable this message and the .NET Core welcome message, set the `DOTNET_NOLOGO` environment variable to `true`.</span></span> <span data-ttu-id="d84b6-123">Bu değişkenin telemetri devre dışı bırakma üzerinde hiçbir etkisi olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d84b6-123">Note that this variable has no effect on telemetry opt out.</span></span>

## <a name="data-points"></a><span data-ttu-id="d84b6-124">Veri noktaları</span><span class="sxs-lookup"><span data-stu-id="d84b6-124">Data points</span></span>

<span data-ttu-id="d84b6-125">Telemetri özelliği, kullanıcı adları veya e-posta adresleri gibi kişisel verileri toplamaz.</span><span class="sxs-lookup"><span data-stu-id="d84b6-125">The telemetry feature doesn't collect personal data, such as usernames or email addresses.</span></span> <span data-ttu-id="d84b6-126">Kodunuzu tarayıp ad, depo veya yazar gibi proje düzeyinde veri ayıklamaz.</span><span class="sxs-lookup"><span data-stu-id="d84b6-126">It doesn't scan your code and doesn't extract project-level data, such as name, repository, or author.</span></span> <span data-ttu-id="d84b6-127">Veriler, [Azure Monitor](https://azure.microsoft.com/services/monitor/) teknolojisini kullanarak Microsoft sunucularına güvenli bir şekilde gönderilir, sınırlı erişim altında tutulur ve güvenli [Azure Depolama](https://azure.microsoft.com/services/storage/) sistemlerinden gelen sıkı güvenlik denetimleri altında yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="d84b6-127">The data is sent securely to Microsoft servers using [Azure Monitor](https://azure.microsoft.com/services/monitor/) technology, held under restricted access, and published under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

<span data-ttu-id="d84b6-128">Gizliliğinizi korumak bizim için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="d84b6-128">Protecting your privacy is important to us.</span></span> <span data-ttu-id="d84b6-129">Telemetrinin hassas verileri topladığından veya verilerin güvensiz veya uygunsuz şekilde işlendiğinden şüpheleniyorsanız, [dotnet/cli](https://github.com/dotnet/cli/issues) deposunda bir sorun [dotnet@microsoft.com](mailto:dotnet@microsoft.com) dosyala veya soruşturma için bir e-posta gönderin.</span><span class="sxs-lookup"><span data-stu-id="d84b6-129">If you suspect the telemetry is collecting sensitive data or the data is being insecurely or inappropriately handled, file an issue in the [dotnet/cli](https://github.com/dotnet/cli/issues) repository or send an email to [dotnet@microsoft.com](mailto:dotnet@microsoft.com) for investigation.</span></span>

<span data-ttu-id="d84b6-130">Telemetri özelliği aşağıdaki verileri toplar:</span><span class="sxs-lookup"><span data-stu-id="d84b6-130">The telemetry feature collects the following data:</span></span>

| <span data-ttu-id="d84b6-131">SDK sürümleri</span><span class="sxs-lookup"><span data-stu-id="d84b6-131">SDK versions</span></span> | <span data-ttu-id="d84b6-132">Veri</span><span class="sxs-lookup"><span data-stu-id="d84b6-132">Data</span></span> |
|--------------|------|
| <span data-ttu-id="d84b6-133">Tümü</span><span class="sxs-lookup"><span data-stu-id="d84b6-133">All</span></span>          | <span data-ttu-id="d84b6-134">Çağırma zaman damgası.</span><span class="sxs-lookup"><span data-stu-id="d84b6-134">Timestamp of invocation.</span></span> |
| <span data-ttu-id="d84b6-135">Tümü</span><span class="sxs-lookup"><span data-stu-id="d84b6-135">All</span></span>          | <span data-ttu-id="d84b6-136">Komut çağrıldı (örneğin, "inşa"), 2.1'den başlayarak haşiye.</span><span class="sxs-lookup"><span data-stu-id="d84b6-136">Command invoked (for example, "build"), hashed starting in 2.1.</span></span> |
| <span data-ttu-id="d84b6-137">Tümü</span><span class="sxs-lookup"><span data-stu-id="d84b6-137">All</span></span>          | <span data-ttu-id="d84b6-138">Coğrafi konumu belirlemek için kullanılan üç sekizli IP adresi.</span><span class="sxs-lookup"><span data-stu-id="d84b6-138">Three octet IP address used to determine the geographical location.</span></span> |
| <span data-ttu-id="d84b6-139">Tümü</span><span class="sxs-lookup"><span data-stu-id="d84b6-139">All</span></span>          | <span data-ttu-id="d84b6-140">İşletim sistemi ve sürüm.</span><span class="sxs-lookup"><span data-stu-id="d84b6-140">Operating system and version.</span></span> |
| <span data-ttu-id="d84b6-141">Tümü</span><span class="sxs-lookup"><span data-stu-id="d84b6-141">All</span></span>          | <span data-ttu-id="d84b6-142">Çalışma Zamanı Kimliği (RID) SDK üzerinde çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="d84b6-142">Runtime ID (RID) the SDK is running on.</span></span> |
| <span data-ttu-id="d84b6-143">Tümü</span><span class="sxs-lookup"><span data-stu-id="d84b6-143">All</span></span>          | <span data-ttu-id="d84b6-144">.NET Çekirdek SDK versiyonu.</span><span class="sxs-lookup"><span data-stu-id="d84b6-144">.NET Core SDK version.</span></span> |
| <span data-ttu-id="d84b6-145">Tümü</span><span class="sxs-lookup"><span data-stu-id="d84b6-145">All</span></span>          | <span data-ttu-id="d84b6-146">Telemetri profili: yalnızca açık kullanıcı tercihi ile kullanılan ve Microsoft'ta dahili olarak kullanılan isteğe bağlı bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="d84b6-146">Telemetry profile: an optional value only used with explicit user opt-in and used internally at Microsoft.</span></span> |
| <span data-ttu-id="d84b6-147">>=2.0</span><span class="sxs-lookup"><span data-stu-id="d84b6-147">>=2.0</span></span>        | <span data-ttu-id="d84b6-148">Komut bağımsız değişkenleri ve seçenekleri: çeşitli bağımsız değişkenler ve seçenekler toplanır (rasgele dizeleri değil).</span><span class="sxs-lookup"><span data-stu-id="d84b6-148">Command arguments and options: several arguments and options are collected (not arbitrary strings).</span></span> <span data-ttu-id="d84b6-149">[Toplanan seçeneklere](#collected-options)bakın.</span><span class="sxs-lookup"><span data-stu-id="d84b6-149">See [collected options](#collected-options).</span></span> <span data-ttu-id="d84b6-150">2.1.300'den sonra hashed.</span><span class="sxs-lookup"><span data-stu-id="d84b6-150">Hashed after 2.1.300.</span></span> |
| <span data-ttu-id="d84b6-151">>=2.0</span><span class="sxs-lookup"><span data-stu-id="d84b6-151">>=2.0</span></span>         | <span data-ttu-id="d84b6-152">SDK'nın bir kapta çalışıp çalışmadığı.</span><span class="sxs-lookup"><span data-stu-id="d84b6-152">Whether the SDK is running in a container.</span></span> |
| <span data-ttu-id="d84b6-153">>=2.0</span><span class="sxs-lookup"><span data-stu-id="d84b6-153">>=2.0</span></span>         | <span data-ttu-id="d84b6-154">Hedef çerçeveler `TargetFramework` (olaydan), 2.1'den başlayan bir hadde.</span><span class="sxs-lookup"><span data-stu-id="d84b6-154">Target frameworks (from the `TargetFramework` event), hashed starting in 2.1.</span></span> |
| <span data-ttu-id="d84b6-155">>=2.0</span><span class="sxs-lookup"><span data-stu-id="d84b6-155">>=2.0</span></span>         | <span data-ttu-id="d84b6-156">Karma Medya Erişim Kontrolü (MAC) adresi: bir makine için şifreleme (SHA256) anonim ve benzersiz bir kimlik.</span><span class="sxs-lookup"><span data-stu-id="d84b6-156">Hashed Media Access Control (MAC) address: a cryptographically (SHA256) anonymous and unique ID for a machine.</span></span> |
| <span data-ttu-id="d84b6-157">>=2.0</span><span class="sxs-lookup"><span data-stu-id="d84b6-157">>=2.0</span></span>         | <span data-ttu-id="d84b6-158">Hashed geçerli çalışma dizini.</span><span class="sxs-lookup"><span data-stu-id="d84b6-158">Hashed current working directory.</span></span> |
| <span data-ttu-id="d84b6-159">>=2.0</span><span class="sxs-lookup"><span data-stu-id="d84b6-159">>=2.0</span></span>         | <span data-ttu-id="d84b6-160">Hashed installer exe dosya adı ile başarı raporu yükleyin.</span><span class="sxs-lookup"><span data-stu-id="d84b6-160">Install success report, with hashed installer exe filename.</span></span> |
| <span data-ttu-id="d84b6-161">>=2.1.300</span><span class="sxs-lookup"><span data-stu-id="d84b6-161">>=2.1.300</span></span>     | <span data-ttu-id="d84b6-162">Çekirdek versiyonu.</span><span class="sxs-lookup"><span data-stu-id="d84b6-162">Kernel version.</span></span> |
| <span data-ttu-id="d84b6-163">>=2.1.300</span><span class="sxs-lookup"><span data-stu-id="d84b6-163">>=2.1.300</span></span>     | <span data-ttu-id="d84b6-164">Libc sürümü/sürümü.</span><span class="sxs-lookup"><span data-stu-id="d84b6-164">Libc release/version.</span></span> |
| <span data-ttu-id="d84b6-165">>=3.0.100</span><span class="sxs-lookup"><span data-stu-id="d84b6-165">>=3.0.100</span></span>     | <span data-ttu-id="d84b6-166">Çıktının yönlendirilip yönlendirilmediği (doğru veya yanlış).</span><span class="sxs-lookup"><span data-stu-id="d84b6-166">Whether the output was redirected (true or false).</span></span> |
| <span data-ttu-id="d84b6-167">>=3.0.100</span><span class="sxs-lookup"><span data-stu-id="d84b6-167">>=3.0.100</span></span>     | <span data-ttu-id="d84b6-168">CLI/SDK kilitlenmesinde, özel durum türü ve yığın izi (gönderilen yığın izlemesine yalnızca CLI/SDK kodu dahildir).</span><span class="sxs-lookup"><span data-stu-id="d84b6-168">On a CLI/SDK crash, the exception type and its stack trace (only CLI/SDK code is included in the stack trace sent).</span></span> <span data-ttu-id="d84b6-169">Daha fazla bilgi için [bkz.](#net-core-clisdk-crash-exception-telemetry-collected)</span><span class="sxs-lookup"><span data-stu-id="d84b6-169">For more information, see [.NET Core CLI/SDK crash exception telemetry collected](#net-core-clisdk-crash-exception-telemetry-collected).</span></span> |

### <a name="collected-options"></a><span data-ttu-id="d84b6-170">Toplanan seçenekler</span><span class="sxs-lookup"><span data-stu-id="d84b6-170">Collected options</span></span>

<span data-ttu-id="d84b6-171">Bazı komutlar ek veri gönderir.</span><span class="sxs-lookup"><span data-stu-id="d84b6-171">Certain commands send additional data.</span></span> <span data-ttu-id="d84b6-172">Komutların bir alt kümesi ilk bağımsız değişkeni gönderir:</span><span class="sxs-lookup"><span data-stu-id="d84b6-172">A subset of commands sends the first argument:</span></span>

| <span data-ttu-id="d84b6-173">Komut</span><span class="sxs-lookup"><span data-stu-id="d84b6-173">Command</span></span>               | <span data-ttu-id="d84b6-174">Gönderilen ilk bağımsız değişken verileri</span><span class="sxs-lookup"><span data-stu-id="d84b6-174">First argument data sent</span></span>                |
|-----------------------|-----------------------------------------|
| `dotnet help <arg>`   | <span data-ttu-id="d84b6-175">Komut yardımı için sorgulanıyor.</span><span class="sxs-lookup"><span data-stu-id="d84b6-175">The command help is being queried for.</span></span>  |
| `dotnet new <arg>`    | <span data-ttu-id="d84b6-176">Şablon adı (hashed).</span><span class="sxs-lookup"><span data-stu-id="d84b6-176">The template name (hashed).</span></span>             |
| `dotnet add <arg>`    | <span data-ttu-id="d84b6-177">Kelime `package` ya `reference`da .</span><span class="sxs-lookup"><span data-stu-id="d84b6-177">The word `package` or `reference`.</span></span>      |
| `dotnet remove <arg>` | <span data-ttu-id="d84b6-178">Kelime `package` ya `reference`da .</span><span class="sxs-lookup"><span data-stu-id="d84b6-178">The word `package` or `reference`.</span></span>      |
| `dotnet list <arg>`   | <span data-ttu-id="d84b6-179">Kelime `package` ya `reference`da .</span><span class="sxs-lookup"><span data-stu-id="d84b6-179">The word `package` or `reference`.</span></span>      |
| `dotnet sln <arg>`    | <span data-ttu-id="d84b6-180">Kelime `add`, `list`, `remove`veya .</span><span class="sxs-lookup"><span data-stu-id="d84b6-180">The word `add`, `list`, or `remove`.</span></span>    |
| `dotnet nuget <arg>`  | <span data-ttu-id="d84b6-181">Kelime `delete`, `locals`, `push`veya .</span><span class="sxs-lookup"><span data-stu-id="d84b6-181">The word `delete`, `locals`, or `push`.</span></span> |

<span data-ttu-id="d84b6-182">Komutların bir alt kümesi, değerleriyle birlikte kullanılırsa seçili seçenekleri gönderir:</span><span class="sxs-lookup"><span data-stu-id="d84b6-182">A subset of commands sends selected options if they're used, along with their values:</span></span>

| <span data-ttu-id="d84b6-183">Seçenek</span><span class="sxs-lookup"><span data-stu-id="d84b6-183">Option</span></span>                  | <span data-ttu-id="d84b6-184">Komutlar</span><span class="sxs-lookup"><span data-stu-id="d84b6-184">Commands</span></span>                                                                                       |
|-------------------------|------------------------------------------------------------------------------------------------|
| `--verbosity`           | <span data-ttu-id="d84b6-185">Tüm komutlar</span><span class="sxs-lookup"><span data-stu-id="d84b6-185">All commands</span></span>                                                                                   |
| `--language`            | `dotnet new`                                                                                   |
| `--configuration`       | <span data-ttu-id="d84b6-186">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`</span><span class="sxs-lookup"><span data-stu-id="d84b6-186">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`</span></span>                  |
| `--framework`           | <span data-ttu-id="d84b6-187">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`, `dotnet vstest`</span><span class="sxs-lookup"><span data-stu-id="d84b6-187">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`, `dotnet vstest`</span></span> |
| `--runtime`             | <span data-ttu-id="d84b6-188">`dotnet build`,  `dotnet publish`</span><span class="sxs-lookup"><span data-stu-id="d84b6-188">`dotnet build`,  `dotnet publish`</span></span>                                                              |
| `--platform`            | `dotnet vstest`                                                                                |
| `--logger`              | `dotnet vstest`                                                                                |
| `--sdk-package-version` | `dotnet migrate`                                                                               |

<span data-ttu-id="d84b6-189">`--verbosity` .NET Core 2.1.100 SDK ile başlayan diğer tüm değerler karnedir. `--sdk-package-version`</span><span class="sxs-lookup"><span data-stu-id="d84b6-189">Except for `--verbosity` and `--sdk-package-version`, all the other values are hashed starting with .NET Core 2.1.100 SDK.</span></span>

## <a name="net-core-clisdk-crash-exception-telemetry-collected"></a><span data-ttu-id="d84b6-190">.NET Core CLI/SDK çarpışma istisnatelemetri toplanan</span><span class="sxs-lookup"><span data-stu-id="d84b6-190">.NET Core CLI/SDK crash exception telemetry collected</span></span>

<span data-ttu-id="d84b6-191">.NET Core CLI/SDK çökerse, özel durum adını toplar ve CLI/SDK kodunun yığın izini toplar.</span><span class="sxs-lookup"><span data-stu-id="d84b6-191">If the .NET Core CLI/SDK crashes, it collects the name of the exception and stack trace of the CLI/SDK code.</span></span> <span data-ttu-id="d84b6-192">Bu bilgiler, sorunları değerlendirmek ve .NET Core SDK ve CLI kalitesini artırmak için toplanır.</span><span class="sxs-lookup"><span data-stu-id="d84b6-192">This information is collected to assess problems and improve the quality of the .NET Core SDK and CLI.</span></span> <span data-ttu-id="d84b6-193">Bu makalede, topladığımız veriler hakkında bilgi verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d84b6-193">This article provides information about the data we collect.</span></span> <span data-ttu-id="d84b6-194">Ayrıca, .NET Core SDK'nın kendi sürümünü oluşturan kullanıcıların kişisel veya hassas bilgilerin yanlışlıkla açıklanmasını nasıl önleyebildiği hakkında ipuçları da sağlar.</span><span class="sxs-lookup"><span data-stu-id="d84b6-194">It also provides tips on how users building their own version of the .NET Core SDK can avoid inadvertent disclosure of personal or sensitive information.</span></span>

### <a name="types-of-collected-data"></a><span data-ttu-id="d84b6-195">Toplanan veri türleri</span><span class="sxs-lookup"><span data-stu-id="d84b6-195">Types of collected data</span></span>

<span data-ttu-id="d84b6-196">.NET Core CLI, uygulamanızdaki istisnalar için değil, yalnızca CLI/SDK istisnaları için bilgi toplar.</span><span class="sxs-lookup"><span data-stu-id="d84b6-196">.NET Core CLI collects information for CLI/SDK exceptions only, not exceptions in your application.</span></span> <span data-ttu-id="d84b6-197">Toplanan veriler özel durum ve yığın izleme adını içerir.</span><span class="sxs-lookup"><span data-stu-id="d84b6-197">The collected data contains the name of the exception and the stack trace.</span></span> <span data-ttu-id="d84b6-198">Bu yığın izi CLI/SDK koduna ait.</span><span class="sxs-lookup"><span data-stu-id="d84b6-198">This stack trace is of CLI/SDK code.</span></span>

<span data-ttu-id="d84b6-199">Aşağıdaki örnek, toplanan veri türünü gösterir:</span><span class="sxs-lookup"><span data-stu-id="d84b6-199">The following example shows the kind of data that is collected:</span></span>

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

### <a name="avoid-inadvertent-disclosure-of-information"></a><span data-ttu-id="d84b6-200">Bilgilerin yanlışlıkla ifşa edilmesinden kaçının</span><span class="sxs-lookup"><span data-stu-id="d84b6-200">Avoid inadvertent disclosure of information</span></span>

<span data-ttu-id="d84b6-201">.NET Core katılımcıları ve .NET Core SDK'nın kendi kurdukları bir sürümünü çalıştıran herkes, SDK kaynak kodlarına giden yolu göz önünde bulundurmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d84b6-201">.NET Core contributors and anyone else running a version of the .NET Core SDK that they built themselves should consider the path to their SDK source code.</span></span> <span data-ttu-id="d84b6-202">Özel hata ayıklama yapılı veya özel yapı simgesi dosyalarıyla yapılandırılan bir .NET Core SDK kullanırken bir kilitlenme oluşursa, yapı makinesinden Gelen SDK kaynak dosya yolu yığın izlemenin bir parçası olarak toplanır ve haşlanmadı.</span><span class="sxs-lookup"><span data-stu-id="d84b6-202">If a crash occurs while using a .NET Core SDK that is a custom debug build or configured with custom build symbol files, the SDK source file path from the build machine is collected as part of the stack trace and isn't hashed.</span></span>

<span data-ttu-id="d84b6-203">Bu nedenle, .NET Core SDK'nın özel yapılarının, yol adları kişisel veya hassas bilgileri açığa çıkaran dizinlerde bulunmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d84b6-203">Because of this, custom builds of the .NET Core SDK shouldn't be located in directories whose path names expose personal or sensitive information.</span></span>

## <a name="see-also"></a><span data-ttu-id="d84b6-204">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d84b6-204">See also</span></span>

- [<span data-ttu-id="d84b6-205">.NET Core CLI Telemetri - 2019 S2 Verileri</span><span class="sxs-lookup"><span data-stu-id="d84b6-205">.NET Core CLI Telemetry - 2019 Q2 Data</span></span>](https://dotnet.microsoft.com/platform/telemetry/dotnet-core-cli-2019q2)
- [<span data-ttu-id="d84b6-206">Telemetri referans kaynağı (dotnet/cli deposu)</span><span class="sxs-lookup"><span data-stu-id="d84b6-206">Telemetry reference source (dotnet/cli repository)</span></span>](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry)
