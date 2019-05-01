---
title: .NET core SDK'sı telemetri
description: Analiz, hangi verileri toplanır ve nasıl devre dışı bırakmak için kullanım bilgileri toplamasına .NET Core SDK'sı telemetri özellikleri keşfedin.
author: richlander
ms.date: 06/20/2018
ms.custom: seodec18
ms.openlocfilehash: 2ef6ade36092ff5a17b0cc420dc4859409d459ce
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63773845"
---
# <a name="net-core-sdk-telemetry"></a><span data-ttu-id="4c17d-103">.NET core SDK'sı telemetri</span><span class="sxs-lookup"><span data-stu-id="4c17d-103">.NET Core SDK telemetry</span></span>

<span data-ttu-id="4c17d-104">[.NET Core SDK'sı](index.md) içeren bir [telemetri özellik](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry) , kullanım bilgilerini toplar.</span><span class="sxs-lookup"><span data-stu-id="4c17d-104">The [.NET Core SDK](index.md) includes a [telemetry feature](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry) that collects usage information.</span></span> <span data-ttu-id="4c17d-105">.NET ekibi geliştirilebilir bu nedenle araçları nasıl kullanıldığını anladığını önemlidir.</span><span class="sxs-lookup"><span data-stu-id="4c17d-105">It's important that the .NET Team understands how the tools are used so they can be improved.</span></span> <span data-ttu-id="4c17d-106">Daha fazla bilgi için [.NET Core SDK'sı Telemetri öğrendiklerimizi](https://devblogs.microsoft.com/dotnet/what-weve-learned-from-net-core-sdk-telemetry/).</span><span class="sxs-lookup"><span data-stu-id="4c17d-106">For more information, see [What we've learned from .NET Core SDK Telemetry](https://devblogs.microsoft.com/dotnet/what-weve-learned-from-net-core-sdk-telemetry/).</span></span>

<span data-ttu-id="4c17d-107">Anonim ve yayınlanan hem Microsoft hem de altında topluluk tarafından kullanım için toplu bir biçimde toplanan verileri [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span><span class="sxs-lookup"><span data-stu-id="4c17d-107">The collected data is anonymous and published in an aggregated form for use by both Microsoft and the community under the [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span></span>

## <a name="scope"></a><span data-ttu-id="4c17d-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="4c17d-108">Scope</span></span>

<span data-ttu-id="4c17d-109">`dotnet` Komutu, hem uygulama hem de .NET Core CLI başlatmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4c17d-109">The `dotnet` command is used to launch both apps and the .NET Core CLI.</span></span> <span data-ttu-id="4c17d-110">`dotnet` Komutun kendisindeki telemetri toplamak değil.</span><span class="sxs-lookup"><span data-stu-id="4c17d-110">The `dotnet` command itself doesn't collect telemetry.</span></span> <span data-ttu-id="4c17d-111">.NET Core CLI komutları tarafından çalıştırılan `dotnet` komut telemetri toplar.</span><span class="sxs-lookup"><span data-stu-id="4c17d-111">The .NET Core CLI commands run by the `dotnet` command collect the telemetry.</span></span>

<span data-ttu-id="4c17d-112">Telemetri *etkin değilse* kullanırken `dotnet` kendisine bağlı bir komut ile komutu:</span><span class="sxs-lookup"><span data-stu-id="4c17d-112">Telemetry *isn't enabled* when using the `dotnet` command itself, with no command attached:</span></span>

- `dotnet`
- `dotnet [path-to-app]`

<span data-ttu-id="4c17d-113">Telemetri *etkin* kullanırken [.NET Core CLI komutları](index.md), örneğin:</span><span class="sxs-lookup"><span data-stu-id="4c17d-113">Telemetry *is enabled* when using the [.NET Core CLI commands](index.md), such as:</span></span>

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`

## <a name="how-to-opt-out"></a><span data-ttu-id="4c17d-114">İptal etme</span><span class="sxs-lookup"><span data-stu-id="4c17d-114">How to opt out</span></span>

<span data-ttu-id="4c17d-115">.NET Core SDK'sı telemetri özellik varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="4c17d-115">The .NET Core SDK telemetry feature is enabled by default.</span></span> <span data-ttu-id="4c17d-116">Ayarlayarak telemetri özelliği iyileştirilmiş `DOTNET_CLI_TELEMETRY_OPTOUT` ortam değişkenine `1` veya `true`.</span><span class="sxs-lookup"><span data-stu-id="4c17d-116">Opt out of the telemetry feature by setting the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span>

## <a name="data-points"></a><span data-ttu-id="4c17d-117">Veri noktaları</span><span class="sxs-lookup"><span data-stu-id="4c17d-117">Data points</span></span>

<span data-ttu-id="4c17d-118">Bu özellik aşağıdaki verileri toplar:</span><span class="sxs-lookup"><span data-stu-id="4c17d-118">The feature collects the following data:</span></span>

- <span data-ttu-id="4c17d-119">Zaman damgası çağırma&#8224;</span><span class="sxs-lookup"><span data-stu-id="4c17d-119">Timestamp of invocation&#8224;</span></span>
- <span data-ttu-id="4c17d-120">Komutu (örneğin "derleme") çağrılır&#8224;</span><span class="sxs-lookup"><span data-stu-id="4c17d-120">Command invoked (for example, "build")&#8224;</span></span>
- <span data-ttu-id="4c17d-121">Coğrafi konumunu belirlemek için kullanılan üç sekizli IP adresi&#8224;</span><span class="sxs-lookup"><span data-stu-id="4c17d-121">Three octet IP address used to determine geographical location&#8224;</span></span>
- <span data-ttu-id="4c17d-122">`ExitCode` komutu</span><span class="sxs-lookup"><span data-stu-id="4c17d-122">`ExitCode` of the command</span></span>
- <span data-ttu-id="4c17d-123">Test Çalıştırıcısı (için test projeleri)</span><span class="sxs-lookup"><span data-stu-id="4c17d-123">Test runner (for test projects)</span></span>
- <span data-ttu-id="4c17d-124">İşletim sistemi ve sürümü&#8224;</span><span class="sxs-lookup"><span data-stu-id="4c17d-124">Operating system and version&#8224;</span></span>
- <span data-ttu-id="4c17d-125">Çalışma zamanı kimlikleri çalışma zamanları düğümünde mevcut olup olmadığı</span><span class="sxs-lookup"><span data-stu-id="4c17d-125">Whether runtime IDs are present in the runtimes node</span></span>
- <span data-ttu-id="4c17d-126">.NET core SDK sürümü&#8224;</span><span class="sxs-lookup"><span data-stu-id="4c17d-126">.NET Core SDK version&#8224;</span></span>

<span data-ttu-id="4c17d-127">&#8224;Bu ölçüm yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="4c17d-127">&#8224;This metric is published.</span></span>

<span data-ttu-id="4c17d-128">.NET Core 2.0 SDK'sı ile başlayarak, yeni veri noktaları toplanır:</span><span class="sxs-lookup"><span data-stu-id="4c17d-128">Starting with .NET Core 2.0 SDK, new data points are collected:</span></span>

- <span data-ttu-id="4c17d-129">`dotnet` komut bağımsız değişkenleri ve seçenekleri: yalnızca bağımsız değişkenleri ve seçenekleri toplanan (değil rasgele dizeleri) bilinir.</span><span class="sxs-lookup"><span data-stu-id="4c17d-129">`dotnet` command arguments and options: only known arguments and options are collected (not arbitrary strings).</span></span>
- <span data-ttu-id="4c17d-130">SDK'sı bir kapsayıcıda kullanılıp kullanılmadığını.</span><span class="sxs-lookup"><span data-stu-id="4c17d-130">Whether the SDK is running in a container.</span></span>
- <span data-ttu-id="4c17d-131">Hedef çerçeve.</span><span class="sxs-lookup"><span data-stu-id="4c17d-131">Target frameworks.</span></span>
- <span data-ttu-id="4c17d-132">Karma MAC adresi: bir şifreleme açısından (SHA256) anonim ve benzersiz bir kimliği için bir makine.</span><span class="sxs-lookup"><span data-stu-id="4c17d-132">Hashed MAC address: a cryptographically (SHA256) anonymous and unique ID for a machine.</span></span> <span data-ttu-id="4c17d-133">Bu ölçüm yayımlanan değil.</span><span class="sxs-lookup"><span data-stu-id="4c17d-133">This metric isn't published.</span></span>
- <span data-ttu-id="4c17d-134">Karma geçerli çalışma dizini.</span><span class="sxs-lookup"><span data-stu-id="4c17d-134">Hashed current working directory.</span></span>

<span data-ttu-id="4c17d-135">Bu özellik, kullanıcı adları veya e-posta adresleri gibi kişisel verileri toplamaz.</span><span class="sxs-lookup"><span data-stu-id="4c17d-135">The feature doesn't collect personal data, such as usernames or email addresses.</span></span> <span data-ttu-id="4c17d-136">Bu, kodunuzu taramaz ve adı, depo veya yazar gibi hassas proje düzeyi verileri ayıklamak değil.</span><span class="sxs-lookup"><span data-stu-id="4c17d-136">It doesn't scan your code and doesn't extract sensitive project-level data, such as name, repo, or author.</span></span> <span data-ttu-id="4c17d-137">Veriler güvenli bir şekilde kullanarak Microsoft sunucularına gönderilir [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) kısıtlı erişim'in altında tutulması ve katı güvenlik denetimleri güvenli altında yayımlanan teknoloji [Azuredepolama](https://azure.microsoft.com/services/storage/) sistemler.</span><span class="sxs-lookup"><span data-stu-id="4c17d-137">The data is sent securely to Microsoft servers using [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technology, held under restricted access, and published under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

<span data-ttu-id="4c17d-138">.NET ekibi araçları nasıl kullanıldığını ve bunlar da ne araçlarla hedeflediğiniz platformun değil çalışıyorsanız bilmek istemektedir.</span><span class="sxs-lookup"><span data-stu-id="4c17d-138">The .NET team wants to know how the tools are used and if they're working well, not what you're building with the tools.</span></span> <span data-ttu-id="4c17d-139">Telemetri hassas veriler ya da toplama şüpheleniyorsanız veri endpoınt yapılıyor veya uygunsuz bir şekilde ele, sorunu bildirin [dotnet/CLI](https://github.com/dotnet/cli/issues) araştırma için depo.</span><span class="sxs-lookup"><span data-stu-id="4c17d-139">If you suspect that the telemetry is collecting sensitive data or that the data is being insecurely or inappropriately handled, file an issue in the [dotnet/cli](https://github.com/dotnet/cli/issues) repository for investigation.</span></span>

## <a name="published-data"></a><span data-ttu-id="4c17d-140">Yayımlanan veriler</span><span class="sxs-lookup"><span data-stu-id="4c17d-140">Published data</span></span>

<span data-ttu-id="4c17d-141">Yayımlanan veriler üç aylık olarak kullanılabilir ve listelenen [.NET Core SDK'sı kullanım verilerini](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md).</span><span class="sxs-lookup"><span data-stu-id="4c17d-141">Published data is available quarterly and are listed at [.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md).</span></span> <span data-ttu-id="4c17d-142">Bir veri dosyasının sütunları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="4c17d-142">The columns of a data file are:</span></span>

- <span data-ttu-id="4c17d-143">Zaman damgası</span><span class="sxs-lookup"><span data-stu-id="4c17d-143">Timestamp</span></span>
- <span data-ttu-id="4c17d-144">Örnekleri&#8224;</span><span class="sxs-lookup"><span data-stu-id="4c17d-144">Occurrences&#8224;</span></span>
- <span data-ttu-id="4c17d-145">Komut</span><span class="sxs-lookup"><span data-stu-id="4c17d-145">Command</span></span>
- <span data-ttu-id="4c17d-146">Coğrafi konum&#8225;</span><span class="sxs-lookup"><span data-stu-id="4c17d-146">Geography&#8225;</span></span>
- <span data-ttu-id="4c17d-147">OSFamily</span><span class="sxs-lookup"><span data-stu-id="4c17d-147">OSFamily</span></span>
- <span data-ttu-id="4c17d-148">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="4c17d-148">RuntimeID</span></span>
- <span data-ttu-id="4c17d-149">OSVersion</span><span class="sxs-lookup"><span data-stu-id="4c17d-149">OSVersion</span></span>
- <span data-ttu-id="4c17d-150">SDKVersion</span><span class="sxs-lookup"><span data-stu-id="4c17d-150">SDKVersion</span></span>

<span data-ttu-id="4c17d-151">&#8224;*Oluşum* sütunu bu komutun kullanın, sıranın ölçümler için o gün toplam sayısını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4c17d-151">&#8224;The *Occurrences* column displays the aggregate count of that command's use for that row's metrics that day.</span></span>

<span data-ttu-id="4c17d-152">&#8225;Genellikle, *Coğrafya* sütun ülke adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4c17d-152">&#8225;Typically, the *Geography* column displays the name of a country.</span></span> <span data-ttu-id="4c17d-153">Bazı durumlarda, bu sütunda, .NET Core Antarktika ya da yanlış konum verileri kullanarak Araştırmacıları nedeniyle Antarktika, kıta görünür.</span><span class="sxs-lookup"><span data-stu-id="4c17d-153">In some cases, the continent of Antarctica appears in this column, either due to researchers using .NET Core in Antarctica or incorrect location data.</span></span>

### <a name="example"></a><span data-ttu-id="4c17d-154">Örnek</span><span class="sxs-lookup"><span data-stu-id="4c17d-154">Example</span></span>

| <span data-ttu-id="4c17d-155">Zaman damgası</span><span class="sxs-lookup"><span data-stu-id="4c17d-155">Timestamp</span></span>      | <span data-ttu-id="4c17d-156">Örnekleri</span><span class="sxs-lookup"><span data-stu-id="4c17d-156">Occurrences</span></span> | <span data-ttu-id="4c17d-157">Komut</span><span class="sxs-lookup"><span data-stu-id="4c17d-157">Command</span></span> | <span data-ttu-id="4c17d-158">Geography</span><span class="sxs-lookup"><span data-stu-id="4c17d-158">Geography</span></span> | <span data-ttu-id="4c17d-159">OSFamily</span><span class="sxs-lookup"><span data-stu-id="4c17d-159">OSFamily</span></span> | <span data-ttu-id="4c17d-160">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="4c17d-160">RuntimeID</span></span>     | <span data-ttu-id="4c17d-161">OSVersion</span><span class="sxs-lookup"><span data-stu-id="4c17d-161">OSVersion</span></span> | <span data-ttu-id="4c17d-162">SDKVersion</span><span class="sxs-lookup"><span data-stu-id="4c17d-162">SDKVersion</span></span> |
| -------------- | ----------- | ------- | --------- | -------- | ------------- | --------- | ---------- |
| <span data-ttu-id="4c17d-163">4/16/2017 0:00</span><span class="sxs-lookup"><span data-stu-id="4c17d-163">4/16/2017 0:00</span></span> | <span data-ttu-id="4c17d-164">8</span><span class="sxs-lookup"><span data-stu-id="4c17d-164">8</span></span>           | <span data-ttu-id="4c17d-165">Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="4c17d-165">run</span></span>     | <span data-ttu-id="4c17d-166">Uganda</span><span class="sxs-lookup"><span data-stu-id="4c17d-166">Uganda</span></span>    | <span data-ttu-id="4c17d-167">Darwin</span><span class="sxs-lookup"><span data-stu-id="4c17d-167">Darwin</span></span>   | <span data-ttu-id="4c17d-168">osx.10.12 x64</span><span class="sxs-lookup"><span data-stu-id="4c17d-168">osx.10.12-x64</span></span> | <span data-ttu-id="4c17d-169">10.12</span><span class="sxs-lookup"><span data-stu-id="4c17d-169">10.12</span></span>     | <span data-ttu-id="4c17d-170">1.0.1</span><span class="sxs-lookup"><span data-stu-id="4c17d-170">1.0.1</span></span>      |

### <a name="datasets"></a><span data-ttu-id="4c17d-171">Veri kümeleri</span><span class="sxs-lookup"><span data-stu-id="4c17d-171">Datasets</span></span>

- [<span data-ttu-id="4c17d-172">2016 - S3</span><span class="sxs-lookup"><span data-stu-id="4c17d-172">2016 - Q3</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q3.tsv)
- [<span data-ttu-id="4c17d-173">2016 - 4</span><span class="sxs-lookup"><span data-stu-id="4c17d-173">2016 - Q4</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q4.tsv)
- [<span data-ttu-id="4c17d-174">2017 - S1</span><span class="sxs-lookup"><span data-stu-id="4c17d-174">2017 - Q1</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q1.tsv)
- [<span data-ttu-id="4c17d-175">2017 - S2</span><span class="sxs-lookup"><span data-stu-id="4c17d-175">2017 - Q2</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q2.tsv)
- [<span data-ttu-id="4c17d-176">2017 - S3</span><span class="sxs-lookup"><span data-stu-id="4c17d-176">2017 - Q3</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q3.tsv)
- [<span data-ttu-id="4c17d-177">2017 - 4</span><span class="sxs-lookup"><span data-stu-id="4c17d-177">2017 - Q4</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q4.tsv)

<span data-ttu-id="4c17d-178">Ek veri kümeleri, standart bir URL biçimi kullanılarak gönderilir.</span><span class="sxs-lookup"><span data-stu-id="4c17d-178">Additional datasets are posted using a standard URL format.</span></span> <span data-ttu-id="4c17d-179">Değiştirin `<YEAR>` yıl ve Değiştir `<QUARTER>` yılın çeyreği ile (kullanın `1`, `2`, `3`, veya `4`).</span><span class="sxs-lookup"><span data-stu-id="4c17d-179">Replace `<YEAR>` with the year and replace `<QUARTER>` with the quarter of the year (use `1`, `2`, `3`, or `4`).</span></span> <span data-ttu-id="4c17d-180">Dosyaları sekmeyle ayrılmış değerler (*TSV*) biçimi.</span><span class="sxs-lookup"><span data-stu-id="4c17d-180">The files are in tab-separated values (*TSV*) format.</span></span>

`https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-<YEAR>-q<QUARTER>.tsv`

## <a name="license"></a><span data-ttu-id="4c17d-181">Lisans</span><span class="sxs-lookup"><span data-stu-id="4c17d-181">License</span></span>

<span data-ttu-id="4c17d-182">Microsoft Dağıtım .NET Core ile lisanslanan [Microsoft Yazılımı Lisans koşulları: Mirosoft .NET kitaplığı](https://aka.ms/dotnet-core-eula).</span><span class="sxs-lookup"><span data-stu-id="4c17d-182">The Microsoft distribution of .NET Core is licensed with the [Microsoft Software License Terms: Mirosoft .NET Library](https://aka.ms/dotnet-core-eula).</span></span> <span data-ttu-id="4c17d-183">Veri toplama ve işleme hakkında daha fazla bilgi için "Veri" başlıklı bölüme bakın.</span><span class="sxs-lookup"><span data-stu-id="4c17d-183">For details on data collection and processing, see the section entitled "Data."</span></span>

<span data-ttu-id="4c17d-184">[.NET NuGet paketleri](https://www.nuget.org/profiles/dotnetframework) aynı lisans kullanın, ancak telemetri etkinleştirme (bkz [kapsam](#scope)).</span><span class="sxs-lookup"><span data-stu-id="4c17d-184">[.NET NuGet packages](https://www.nuget.org/profiles/dotnetframework) use the same license but don't enable telemetry (see [Scope](#scope)).</span></span>

## <a name="disclosure"></a><span data-ttu-id="4c17d-185">Açığa çıkması</span><span class="sxs-lookup"><span data-stu-id="4c17d-185">Disclosure</span></span>

<span data-ttu-id="4c17d-186">İlk birini çalıştırdığınızda, .NET Core SDK'sı aşağıdaki metni görüntüler [.NET Core CLI komutları](index.md) (örneğin, `dotnet restore`).</span><span class="sxs-lookup"><span data-stu-id="4c17d-186">The .NET Core SDK displays the following text when you first run one of the [.NET Core CLI commands](index.md) (for example, `dotnet restore`).</span></span> <span data-ttu-id="4c17d-187">Metin, çalıştırmakta olduğunuz SDK'sı sürümüne bağlı olarak biraz değişebilir.</span><span class="sxs-lookup"><span data-stu-id="4c17d-187">Text may vary slightly depending on the version of the SDK you're running.</span></span> <span data-ttu-id="4c17d-188">Nasıl Microsoft, veri toplama hakkında size bildirir, bu "İlk Çalıştırma" deneyimi sunar.</span><span class="sxs-lookup"><span data-stu-id="4c17d-188">This "first run" experience is how Microsoft notifies you about data collection.</span></span>

```console
Welcome to .NET Core!
---------------------
Learn more about .NET Core: https://aka.ms/dotnet-docs
Use 'dotnet --help' to see available commands or visit: https://aka.ms/dotnet-cli-docs

Telemetry
---------
The .NET Core tools collect usage data in order to help us improve your experience.
The data is anonymous and doesn't include command-line arguments.
The data is collected by Microsoft and shared with the community.
You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET Core CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry
```

## <a name="see-also"></a><span data-ttu-id="4c17d-189">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c17d-189">See also</span></span>

- [<span data-ttu-id="4c17d-190">.NET Core SDK'sı Telemetri öğrendiklerimizi</span><span class="sxs-lookup"><span data-stu-id="4c17d-190">What we've learned from .NET Core SDK Telemetry</span></span>](https://devblogs.microsoft.com/dotnet/what-weve-learned-from-net-core-sdk-telemetry/)
- [<span data-ttu-id="4c17d-191">Telemetri başvuru kaynağı (dotnet/CLI depo)</span><span class="sxs-lookup"><span data-stu-id="4c17d-191">Telemetry reference source (dotnet/cli repo)</span></span>](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry)
- [<span data-ttu-id="4c17d-192">.NET core SDK'sı kullanım verileri</span><span class="sxs-lookup"><span data-stu-id="4c17d-192">.NET Core SDK Usage Data</span></span>](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md)
