---
title: .NET core SDK telemetri
description: Analiz, hangi verileri toplanır ve nasıl devre dışı bırakmak için kullanım bilgilerini toplamasına .NET Core SDK telemetri özellikleri keşfedin.
author: richlander
ms.author: mairaw
ms.date: 06/20/2018
ms.openlocfilehash: f60a1eaa7b869676dfbb67529e7878ca9b9ca34a
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36314883"
---
# <a name="net-core-sdk-telemetry"></a><span data-ttu-id="18c10-103">.NET core SDK telemetri</span><span class="sxs-lookup"><span data-stu-id="18c10-103">.NET Core SDK telemetry</span></span>

<span data-ttu-id="18c10-104">[.NET Core SDK](index.md) içeren bir [telemetri özellik](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry) kullanım bilgilerini toplar.</span><span class="sxs-lookup"><span data-stu-id="18c10-104">The [.NET Core SDK](index.md) includes a [telemetry feature](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry) that collects usage information.</span></span> <span data-ttu-id="18c10-105">.NET ekibi geliştirilebilir böylece araçları nasıl kullanıldığını algıladığını önemlidir.</span><span class="sxs-lookup"><span data-stu-id="18c10-105">It's important that the .NET Team understands how the tools are used so they can be improved.</span></span> <span data-ttu-id="18c10-106">Daha fazla bilgi için bkz: [ne biz .NET Core SDK Telemetri öğrendiğinize](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/).</span><span class="sxs-lookup"><span data-stu-id="18c10-106">For more information, see [What we've learned from .NET Core SDK Telemetry](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/).</span></span>

<span data-ttu-id="18c10-107">Anonim ve kullanmak için toplanan biçimde yayınlanan hem Microsoft hem de altında topluluk tarafından toplanan veriler [Creative Commons Attribution lisans](https://creativecommons.org/licenses/by/4.0/).</span><span class="sxs-lookup"><span data-stu-id="18c10-107">The collected data is anonymous and published in an aggregated form for use by both Microsoft and the community under the [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span></span>

## <a name="scope"></a><span data-ttu-id="18c10-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="18c10-108">Scope</span></span>

<span data-ttu-id="18c10-109">`dotnet` Komutu, hem uygulamalar hem de .NET Core CLI başlatmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="18c10-109">The `dotnet` command is used to launch both apps and the .NET Core CLI.</span></span> <span data-ttu-id="18c10-110">`dotnet` Komutu kendisi telemetri toplamak değil.</span><span class="sxs-lookup"><span data-stu-id="18c10-110">The `dotnet` command itself doesn't collect telemetry.</span></span> <span data-ttu-id="18c10-111">.NET Core CLI komutları tarafından çalıştırılan `dotnet` komutu telemetri topla.</span><span class="sxs-lookup"><span data-stu-id="18c10-111">The .NET Core CLI commands run by the `dotnet` command collect the telemetry.</span></span>

<span data-ttu-id="18c10-112">Telemetri *etkinleştirilmemiş* kullanırken `dotnet` kendisine bağlı hiçbir komutuyla komutu:</span><span class="sxs-lookup"><span data-stu-id="18c10-112">Telemetry *isn't enabled* when using the `dotnet` command itself, with no command attached:</span></span>

- `dotnet`
- `dotnet [path-to-app]`

<span data-ttu-id="18c10-113">Telemetri *etkin* kullanırken [.NET Core CLI komutları](index.md), gibi:</span><span class="sxs-lookup"><span data-stu-id="18c10-113">Telemetry *is enabled* when using the [.NET Core CLI commands](index.md), such as:</span></span>

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`

## <a name="how-to-opt-out"></a><span data-ttu-id="18c10-114">Geri çevirmek nasıl</span><span class="sxs-lookup"><span data-stu-id="18c10-114">How to opt out</span></span>

<span data-ttu-id="18c10-115">.NET Core SDK telemetri özellik varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="18c10-115">The .NET Core SDK telemetry feature is enabled by default.</span></span> <span data-ttu-id="18c10-116">Telemetri özellik dışında ayarlayarak opt `DOTNET_CLI_TELEMETRY_OPTOUT` ortam değişkenine `1` veya `true`.</span><span class="sxs-lookup"><span data-stu-id="18c10-116">Opt out of the telemetry feature by setting the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span>

## <a name="data-points"></a><span data-ttu-id="18c10-117">Veri noktaları</span><span class="sxs-lookup"><span data-stu-id="18c10-117">Data points</span></span>

<span data-ttu-id="18c10-118">Bu özellik aşağıdaki verileri toplar:</span><span class="sxs-lookup"><span data-stu-id="18c10-118">The feature collects the following data:</span></span>

- <span data-ttu-id="18c10-119">Zaman damgası çağırma&#8224;</span><span class="sxs-lookup"><span data-stu-id="18c10-119">Timestamp of invocation&#8224;</span></span>
- <span data-ttu-id="18c10-120">(Örneğin "Oluştur") çağrılan komutu&#8224;</span><span class="sxs-lookup"><span data-stu-id="18c10-120">Command invoked (for example, "build")&#8224;</span></span>
- <span data-ttu-id="18c10-121">Coğrafi konumunu belirlemek için kullanılan üç sekizli IP adresi&#8224;</span><span class="sxs-lookup"><span data-stu-id="18c10-121">Three octet IP address used to determine geographical location&#8224;</span></span>
- <span data-ttu-id="18c10-122">`ExitCode` komutu</span><span class="sxs-lookup"><span data-stu-id="18c10-122">`ExitCode` of the command</span></span>
- <span data-ttu-id="18c10-123">Test Çalıştırıcısı (için test projeleri)</span><span class="sxs-lookup"><span data-stu-id="18c10-123">Test runner (for test projects)</span></span>
- <span data-ttu-id="18c10-124">İşletim sistemi ve sürümü&#8224;</span><span class="sxs-lookup"><span data-stu-id="18c10-124">Operating system and version&#8224;</span></span>
- <span data-ttu-id="18c10-125">Çalışma zamanı kimlikleri çalışma zamanları düğümünde mevcut olup olmadığı</span><span class="sxs-lookup"><span data-stu-id="18c10-125">Whether runtime IDs are present in the runtimes node</span></span>
- <span data-ttu-id="18c10-126">.NET core SDK sürümü&#8224;</span><span class="sxs-lookup"><span data-stu-id="18c10-126">.NET Core SDK version&#8224;</span></span>

<span data-ttu-id="18c10-127">&#8224;Bu ölçüm yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="18c10-127">&#8224;This metric is published.</span></span>

<span data-ttu-id="18c10-128">.NET Core SDK 2.0 ile başlayarak, yeni veri noktaları toplanır:</span><span class="sxs-lookup"><span data-stu-id="18c10-128">Starting with .NET Core SDK 2.0, new data points are collected:</span></span>

- <span data-ttu-id="18c10-129">`dotnet` komut bağımsız değişkenleri ve seçenekleri: yalnızca bağımsız değişkenleri ve seçenekleri toplanan (değil rastgele dizeleri) bilinir.</span><span class="sxs-lookup"><span data-stu-id="18c10-129">`dotnet` command arguments and options: only known arguments and options are collected (not arbitrary strings).</span></span>
- <span data-ttu-id="18c10-130">SDK bir kapsayıcıda çalışıp çalışmadığını.</span><span class="sxs-lookup"><span data-stu-id="18c10-130">Whether the SDK is running in a container.</span></span>
- <span data-ttu-id="18c10-131">Bir hedef çerçeve.</span><span class="sxs-lookup"><span data-stu-id="18c10-131">Target frameworks.</span></span>
- <span data-ttu-id="18c10-132">Karma MAC adresi: bir şifreleme açısından (SHA256) anonim ve benzersiz kimliği için bir makine.</span><span class="sxs-lookup"><span data-stu-id="18c10-132">Hashed MAC address: a cryptographically (SHA256) anonymous and unique ID for a machine.</span></span> <span data-ttu-id="18c10-133">Bu ölçüm yayımlanan değil.</span><span class="sxs-lookup"><span data-stu-id="18c10-133">This metric isn't published.</span></span>
- <span data-ttu-id="18c10-134">Karma geçerli çalışma dizini.</span><span class="sxs-lookup"><span data-stu-id="18c10-134">Hashed current working directory.</span></span>

<span data-ttu-id="18c10-135">Özellik kullanıcı adlarını veya e-posta adresleri gibi kişisel verilerini topla değil.</span><span class="sxs-lookup"><span data-stu-id="18c10-135">The feature doesn't collect personal data, such as usernames or email addresses.</span></span> <span data-ttu-id="18c10-136">Kodunuzu taramaz ve adı, depodaki veya yazar gibi hassas proje düzeyi verileri ayıklamak değil.</span><span class="sxs-lookup"><span data-stu-id="18c10-136">It doesn't scan your code and doesn't extract sensitive project-level data, such as name, repo, or author.</span></span> <span data-ttu-id="18c10-137">Veriler güvenli bir şekilde kullanarak Microsoft sunucularına gönderilir [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) altında kısıtlı erişim tutulur ve katı güvenlik denetimleri güvenli altında yayımlanan teknolojisi [Azure Storage](https://azure.microsoft.com/services/storage/) sistemler.</span><span class="sxs-lookup"><span data-stu-id="18c10-137">The data is sent securely to Microsoft servers using [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technology, held under restricted access, and published under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

<span data-ttu-id="18c10-138">.NET ekibi araçları nasıl kullanıldığı ve bunlar da, ne araçlarla oluşturmakta değil çalışırken bilmek ister.</span><span class="sxs-lookup"><span data-stu-id="18c10-138">The .NET team wants to know how the tools are used and if they're working well, not what you're building with the tools.</span></span> <span data-ttu-id="18c10-139">Telemetri hassas verileri ya da topluyor şüpheleniyorsanız verileri güvenli şekilde yüklenmekte olan veya bir sorunu açamayacağı işlenen dosya [dotnet/CLI](https://github.com/dotnet/cli/issues) araştırma için depo.</span><span class="sxs-lookup"><span data-stu-id="18c10-139">If you suspect that the telemetry is collecting sensitive data or that the data is being insecurely or inappropriately handled, file an issue in the [dotnet/cli](https://github.com/dotnet/cli/issues) repository for investigation.</span></span>

## <a name="published-data"></a><span data-ttu-id="18c10-140">Yayımlanan veriler</span><span class="sxs-lookup"><span data-stu-id="18c10-140">Published data</span></span>

<span data-ttu-id="18c10-141">Yayımlanan verileri üç aylık olarak kullanılabilir ve adresinde listelenmiş [.NET Core SDK kullanım verilerini](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md).</span><span class="sxs-lookup"><span data-stu-id="18c10-141">Published data is available quarterly and are listed at [.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md).</span></span> <span data-ttu-id="18c10-142">Bir veri dosyası sütunlarının şunlardır:</span><span class="sxs-lookup"><span data-stu-id="18c10-142">The columns of a data file are:</span></span>

- <span data-ttu-id="18c10-143">Zaman damgası</span><span class="sxs-lookup"><span data-stu-id="18c10-143">Timestamp</span></span>
- <span data-ttu-id="18c10-144">Yineleme&#8224;</span><span class="sxs-lookup"><span data-stu-id="18c10-144">Occurrences&#8224;</span></span>
- <span data-ttu-id="18c10-145">Komut</span><span class="sxs-lookup"><span data-stu-id="18c10-145">Command</span></span>
- <span data-ttu-id="18c10-146">Coğrafi konum&#8225;</span><span class="sxs-lookup"><span data-stu-id="18c10-146">Geography&#8225;</span></span>
- <span data-ttu-id="18c10-147">OSFamily</span><span class="sxs-lookup"><span data-stu-id="18c10-147">OSFamily</span></span>
- <span data-ttu-id="18c10-148">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="18c10-148">RuntimeID</span></span>
- <span data-ttu-id="18c10-149">OSVersion</span><span class="sxs-lookup"><span data-stu-id="18c10-149">OSVersion</span></span>
- <span data-ttu-id="18c10-150">SDKVersion</span><span class="sxs-lookup"><span data-stu-id="18c10-150">SDKVersion</span></span>

<span data-ttu-id="18c10-151">&#8224;*Oluşum* sütunu bu komut, sıranın ölçümleri kullanılmak o gün toplam sayısını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="18c10-151">&#8224;The *Occurrences* column displays the aggregate count of that command's use for that row's metrics that day.</span></span>

<span data-ttu-id="18c10-152">&#8225;Genellikle, *Coğrafya* sütun bir ülke adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="18c10-152">&#8225;Typically, the *Geography* column displays the name of a country.</span></span> <span data-ttu-id="18c10-153">Bazı durumlarda, bu sütun, .NET Core Antarktika veya yanlış konumu verileri kullanarak araştırmacılarının nedeniyle Antarktika kıtada görünür.</span><span class="sxs-lookup"><span data-stu-id="18c10-153">In some cases, the continent of Antarctica appears in this column, either due to researchers using .NET Core in Antarctica or incorrect location data.</span></span>

### <a name="example"></a><span data-ttu-id="18c10-154">Örnek</span><span class="sxs-lookup"><span data-stu-id="18c10-154">Example</span></span>

| <span data-ttu-id="18c10-155">Zaman damgası</span><span class="sxs-lookup"><span data-stu-id="18c10-155">Timestamp</span></span>      | <span data-ttu-id="18c10-156">Yineleme</span><span class="sxs-lookup"><span data-stu-id="18c10-156">Occurrences</span></span> | <span data-ttu-id="18c10-157">Komut</span><span class="sxs-lookup"><span data-stu-id="18c10-157">Command</span></span> | <span data-ttu-id="18c10-158">Coğrafi konum</span><span class="sxs-lookup"><span data-stu-id="18c10-158">Geography</span></span> | <span data-ttu-id="18c10-159">OSFamily</span><span class="sxs-lookup"><span data-stu-id="18c10-159">OSFamily</span></span> | <span data-ttu-id="18c10-160">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="18c10-160">RuntimeID</span></span>     | <span data-ttu-id="18c10-161">OSVersion</span><span class="sxs-lookup"><span data-stu-id="18c10-161">OSVersion</span></span> | <span data-ttu-id="18c10-162">SDKVersion</span><span class="sxs-lookup"><span data-stu-id="18c10-162">SDKVersion</span></span> |
| -------------- | ----------- | ------- | --------- | -------- | ------------- | --------- | ---------- |
| <span data-ttu-id="18c10-163">4/16/2017 0:00</span><span class="sxs-lookup"><span data-stu-id="18c10-163">4/16/2017 0:00</span></span> | <span data-ttu-id="18c10-164">8</span><span class="sxs-lookup"><span data-stu-id="18c10-164">8</span></span>           | <span data-ttu-id="18c10-165">Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="18c10-165">run</span></span>     | <span data-ttu-id="18c10-166">Uganda</span><span class="sxs-lookup"><span data-stu-id="18c10-166">Uganda</span></span>    | <span data-ttu-id="18c10-167">Darwin</span><span class="sxs-lookup"><span data-stu-id="18c10-167">Darwin</span></span>   | <span data-ttu-id="18c10-168">osx.10.12 x64</span><span class="sxs-lookup"><span data-stu-id="18c10-168">osx.10.12-x64</span></span> | <span data-ttu-id="18c10-169">10.12</span><span class="sxs-lookup"><span data-stu-id="18c10-169">10.12</span></span>     | <span data-ttu-id="18c10-170">1.0.1</span><span class="sxs-lookup"><span data-stu-id="18c10-170">1.0.1</span></span>      |

### <a name="datasets"></a><span data-ttu-id="18c10-171">Veri kümeleri</span><span class="sxs-lookup"><span data-stu-id="18c10-171">Datasets</span></span>

[<span data-ttu-id="18c10-172">2016 - S3</span><span class="sxs-lookup"><span data-stu-id="18c10-172">2016 - Q3</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q3.tsv)  
[<span data-ttu-id="18c10-173">2016 - 4</span><span class="sxs-lookup"><span data-stu-id="18c10-173">2016 - Q4</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q4.tsv)  
[<span data-ttu-id="18c10-174">2017 - S1</span><span class="sxs-lookup"><span data-stu-id="18c10-174">2017 - Q1</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q1.tsv)  
[<span data-ttu-id="18c10-175">2017 - S2</span><span class="sxs-lookup"><span data-stu-id="18c10-175">2017 - Q2</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q2.tsv)  
[<span data-ttu-id="18c10-176">2017 - S3</span><span class="sxs-lookup"><span data-stu-id="18c10-176">2017 - Q3</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q3.tsv)  
[<span data-ttu-id="18c10-177">2017 - 4</span><span class="sxs-lookup"><span data-stu-id="18c10-177">2017 - Q4</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q4.tsv)  

<span data-ttu-id="18c10-178">Ek veri kümeleri, standart bir URL biçimi kullanılarak gönderilir.</span><span class="sxs-lookup"><span data-stu-id="18c10-178">Additional datasets are posted using a standard URL format.</span></span> <span data-ttu-id="18c10-179">Değiştir `<YEAR>` değiştirin ve yıl `<QUARTER>` çeyreği ile (kullanmak `1`, `2`, `3`, veya `4`).</span><span class="sxs-lookup"><span data-stu-id="18c10-179">Replace `<YEAR>` with the year and replace `<QUARTER>` with the quarter of the year (use `1`, `2`, `3`, or `4`).</span></span> <span data-ttu-id="18c10-180">Dosyaları sekmeyle ayrılmış değerler (*TSV*) biçimi.</span><span class="sxs-lookup"><span data-stu-id="18c10-180">The files are in tab-separated values (*TSV*) format.</span></span>

`https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-<YEAR>-q<QUARTER>.tsv`

## <a name="license"></a><span data-ttu-id="18c10-181">Lisans</span><span class="sxs-lookup"><span data-stu-id="18c10-181">License</span></span>

<span data-ttu-id="18c10-182">.NET Core Microsoft dağıtılması ile lisanslı [MICROSOFT .NET kitaplığı EULA](https://aka.ms/dotnet-core-eula).</span><span class="sxs-lookup"><span data-stu-id="18c10-182">The Microsoft distribution of .NET Core is licensed with the [MICROSOFT .NET LIBRARY EULA](https://aka.ms/dotnet-core-eula).</span></span> <span data-ttu-id="18c10-183">Bu lisans telemetri (aşağıda gösterilen) etkinleştirmek için "DATA" bölüm içerir.</span><span class="sxs-lookup"><span data-stu-id="18c10-183">This license includes the "DATA" section to enable telemetry (shown below).</span></span>

<span data-ttu-id="18c10-184">[.NET NuGet paketleri](https://www.nuget.org/profiles/dotnetframework) aynı lisans kullanır ancak telemetri etkinleştirmezseniz (bkz [kapsam](#scope)).</span><span class="sxs-lookup"><span data-stu-id="18c10-184">[.NET NuGet packages](https://www.nuget.org/profiles/dotnetframework) use the same license but don't enable telemetry (see [Scope](#scope)).</span></span>

> 2. <span data-ttu-id="18c10-185">VERİLER.</span><span class="sxs-lookup"><span data-stu-id="18c10-185">DATA.</span></span> <span data-ttu-id="18c10-186">Yazılım ve yazılımı kullanımınız hakkında bilgi toplamak ve Microsoft'a göndermek.</span><span class="sxs-lookup"><span data-stu-id="18c10-186">The software may collect information about you and your use of the software, and send that to Microsoft.</span></span> <span data-ttu-id="18c10-187">Microsoft, bu bilgiler, ürünlerimizi ve hizmetlerimizi geliştirmek için kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="18c10-187">Microsoft may use this information to improve our products and services.</span></span> <span data-ttu-id="18c10-188">Veri toplama hakkında daha fazla bilgi ve Yardım belgelerine ve adresindeki Gizlilik Bildirimi'ne kullanma http://go.microsoft.com/fwlink/?LinkId=528096.</span><span class="sxs-lookup"><span data-stu-id="18c10-188">You can learn more about data collection and use in the help documentation and the privacy statement at http://go.microsoft.com/fwlink/?LinkId=528096.</span></span> <span data-ttu-id="18c10-189">Bu uygulamalar için onay yazılımı kullanımınız çalışır.</span><span class="sxs-lookup"><span data-stu-id="18c10-189">Your use of the software operates as your consent to these practices.</span></span>

## <a name="disclosure"></a><span data-ttu-id="18c10-190">Açığa çıkması</span><span class="sxs-lookup"><span data-stu-id="18c10-190">Disclosure</span></span>

<span data-ttu-id="18c10-191">Aşağıdakilerden birini ilk kez çalıştırdığınızda, aşağıdaki metni .NET Core SDK'sı görüntüler [.NET Core CLI komutları](index.md) (örneğin, `dotnet restore`).</span><span class="sxs-lookup"><span data-stu-id="18c10-191">The .NET Core SDK displays the following text when you first run one of the [.NET Core CLI commands](index.md) (for example, `dotnet restore`).</span></span> <span data-ttu-id="18c10-192">Metin, çalıştırmakta olduğunuz SDK'sı sürümüne bağlı olarak biraz değişebilir.</span><span class="sxs-lookup"><span data-stu-id="18c10-192">Text may vary slightly depending on the version of the SDK you're running.</span></span> <span data-ttu-id="18c10-193">Bu "ilk Çalıştır" nasıl Microsoft, verilerin toplanması hakkında bilgilendirir deneyimidir.</span><span class="sxs-lookup"><span data-stu-id="18c10-193">This "first run" experience is how Microsoft notifies you about data collection.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="18c10-194">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="18c10-194">See also</span></span>

[<span data-ttu-id="18c10-195">Ne biz .NET Core SDK Telemetri öğrendiniz</span><span class="sxs-lookup"><span data-stu-id="18c10-195">What we've learned from .NET Core SDK Telemetry</span></span>](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/)  
[<span data-ttu-id="18c10-196">Telemetri başvuru kaynağı (dotnet/CLI deposu)</span><span class="sxs-lookup"><span data-stu-id="18c10-196">Telemetry reference source (dotnet/cli repo)</span></span>](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry)  
[<span data-ttu-id="18c10-197">.NET core SDK kullanım verileri</span><span class="sxs-lookup"><span data-stu-id="18c10-197">.NET Core SDK Usage Data</span></span>](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md)  
