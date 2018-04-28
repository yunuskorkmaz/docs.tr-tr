---
title: .NET core CLI araçlarını telemetri
description: Analiz, hangi verileri toplanır ve nasıl devre dışı bırakmak için kullanım bilgilerini toplamasına .NET Core araçları telemetri özellikleri keşfedin.
author: richlander
ms.author: mairaw
ms.date: 08/04/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: b3da69a7fc8de095b3845428af742870e7e737ad
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="net-core-cli-tools-telemetry"></a><span data-ttu-id="c6738-103">.NET core CLI araçlarını telemetri</span><span class="sxs-lookup"><span data-stu-id="c6738-103">.NET Core CLI Tools telemetry</span></span>

<span data-ttu-id="c6738-104">[.NET Core SDK](index.md) içeren bir [telemetri özellik](https://github.com/dotnet/cli/pull/2145) kullanım bilgilerini toplar.</span><span class="sxs-lookup"><span data-stu-id="c6738-104">The [.NET Core SDK](index.md) includes a [telemetry feature](https://github.com/dotnet/cli/pull/2145) that collects usage information.</span></span> <span data-ttu-id="c6738-105">.NET ekibi, böylece biz artırabilir araçları nasıl kullanıldığını algıladığını önemlidir.</span><span class="sxs-lookup"><span data-stu-id="c6738-105">It's important that the .NET Team understands how the tools are used so that we can improve them.</span></span> <span data-ttu-id="c6738-106">Daha fazla bilgi için bkz: [ne biz .NET Core SDK Telemetri öğrendiğinize](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/).</span><span class="sxs-lookup"><span data-stu-id="c6738-106">For more information, see [What we've learned from .NET Core SDK Telemetry](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/).</span></span>

<span data-ttu-id="c6738-107">Anonim ve kullanmak için toplanan biçimde yayınlanan hem Microsoft hem de altında topluluk tarafından toplanan veriler [Creative Commons Attribution lisans](https://creativecommons.org/licenses/by/4.0/).</span><span class="sxs-lookup"><span data-stu-id="c6738-107">The collected data is anonymous and published in an aggregated form for use by both Microsoft and the community under the [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span></span> 

## <a name="scope"></a><span data-ttu-id="c6738-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="c6738-108">Scope</span></span>

<span data-ttu-id="c6738-109">`dotnet` Komutu, hem uygulamalar hem de .NET Core CLI başlatmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c6738-109">The `dotnet` command is used to launch both apps and the .NET Core CLI.</span></span> <span data-ttu-id="c6738-110">`dotnet` Komutu kendisi telemetri toplamak değil.</span><span class="sxs-lookup"><span data-stu-id="c6738-110">The `dotnet` command itself doesn't collect telemetry.</span></span> <span data-ttu-id="c6738-111">.NET Core CLI komutları tarafından çalıştırılan `dotnet` komutu telemetri topla.</span><span class="sxs-lookup"><span data-stu-id="c6738-111">The .NET Core CLI commands run by the `dotnet` command collect the telemetry.</span></span>

<span data-ttu-id="c6738-112">Telemetri *etkinleştirilmemiş* kullanırken `dotnet` kendisine bağlı hiçbir komutuyla komutu:</span><span class="sxs-lookup"><span data-stu-id="c6738-112">Telemetry *isn't enabled* when using the `dotnet` command itself, with no command attached:</span></span>

- `dotnet`
- `dotnet [path-to-app]`

<span data-ttu-id="c6738-113">Telemetri *etkin* kullanırken [.NET Core CLI komutları](index.md), gibi:</span><span class="sxs-lookup"><span data-stu-id="c6738-113">Telemetry *is enabled* when using the [.NET Core CLI commands](index.md), such as:</span></span>

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`


## <a name="behavior"></a><span data-ttu-id="c6738-114">Davranış</span><span class="sxs-lookup"><span data-stu-id="c6738-114">Behavior</span></span>

<span data-ttu-id="c6738-115">.NET Core CLI araçlarını telemetri özellik varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="c6738-115">The .NET Core CLI Tools telemetry feature is enabled by default.</span></span> <span data-ttu-id="c6738-116">Üyelikten çıkmak ayarlayarak telemetri özelliğinin `DOTNET_CLI_TELEMETRY_OPTOUT` ortam değişkenine `1` veya `true`.</span><span class="sxs-lookup"><span data-stu-id="c6738-116">Opt-out of the telemetry feature by setting the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span>

## <a name="data-points"></a><span data-ttu-id="c6738-117">Veri noktaları</span><span class="sxs-lookup"><span data-stu-id="c6738-117">Data points</span></span>

<span data-ttu-id="c6738-118">Bu özellik aşağıdaki verileri toplar:</span><span class="sxs-lookup"><span data-stu-id="c6738-118">The feature collects the following data:</span></span>

- <span data-ttu-id="c6738-119">Zaman damgası çağırma&#8224;</span><span class="sxs-lookup"><span data-stu-id="c6738-119">Timestamp of invocation&#8224;</span></span>
- <span data-ttu-id="c6738-120">(Örneğin "Oluştur") çağrılan komutu&#8224;</span><span class="sxs-lookup"><span data-stu-id="c6738-120">Command invoked (for example, "build")&#8224;</span></span>
- <span data-ttu-id="c6738-121">Coğrafi konumunu belirlemek için kullanılan üç sekizli IP adresi&#8224;</span><span class="sxs-lookup"><span data-stu-id="c6738-121">Three octet IP address used to determine geographical location&#8224;</span></span>
- <span data-ttu-id="c6738-122">`ExitCode` komutu</span><span class="sxs-lookup"><span data-stu-id="c6738-122">`ExitCode` of the command</span></span>
- <span data-ttu-id="c6738-123">Test Çalıştırıcısı (için test projeleri)</span><span class="sxs-lookup"><span data-stu-id="c6738-123">Test runner (for test projects)</span></span>
- <span data-ttu-id="c6738-124">İşletim sistemi ve sürümü&#8224;</span><span class="sxs-lookup"><span data-stu-id="c6738-124">Operating system and version&#8224;</span></span>
- <span data-ttu-id="c6738-125">Çalışma zamanı kimlikleri çalışma zamanları düğümünde mevcut olup olmadığı</span><span class="sxs-lookup"><span data-stu-id="c6738-125">Whether runtime IDs are present in the runtimes node</span></span>
- <span data-ttu-id="c6738-126">.NET core SDK sürümü&#8224;</span><span class="sxs-lookup"><span data-stu-id="c6738-126">.NET Core SDK version&#8224;</span></span>

<span data-ttu-id="c6738-127">&#8224;Bu ölçüm yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="c6738-127">&#8224;This metric is published.</span></span>

<span data-ttu-id="c6738-128">.NET Core SDK 2.0 ile başlayarak, yeni veri noktaları toplanır:</span><span class="sxs-lookup"><span data-stu-id="c6738-128">Starting with .NET Core SDK 2.0, new data points are collected:</span></span>

- <span data-ttu-id="c6738-129">`dotnet` komut bağımsız değişkenleri ve seçenekleri: yalnızca bağımsız değişkenleri ve seçenekleri toplanan (değil rastgele dizeleri) bilinir.</span><span class="sxs-lookup"><span data-stu-id="c6738-129">`dotnet` command arguments and options: only known arguments and options are collected (not arbitrary strings).</span></span>
- <span data-ttu-id="c6738-130">SDK bir kapsayıcıda çalışıp çalışmadığını.</span><span class="sxs-lookup"><span data-stu-id="c6738-130">Whether the SDK is running in a container.</span></span>
- <span data-ttu-id="c6738-131">Bir hedef çerçeve.</span><span class="sxs-lookup"><span data-stu-id="c6738-131">Target frameworks.</span></span>
- <span data-ttu-id="c6738-132">Karma MAC adresi: bir şifreleme açısından (SHA256) anonim ve benzersiz kimliği için bir makine.</span><span class="sxs-lookup"><span data-stu-id="c6738-132">Hashed MAC address: a cryptographically (SHA256) anonymous and unique ID for a machine.</span></span> <span data-ttu-id="c6738-133">Bu ölçüm yayımlanmaz.</span><span class="sxs-lookup"><span data-stu-id="c6738-133">This metric is not published.</span></span>
- <span data-ttu-id="c6738-134">Karma geçerli çalışma dizini.</span><span class="sxs-lookup"><span data-stu-id="c6738-134">Hashed current working directory.</span></span>

<span data-ttu-id="c6738-135">Özellik kullanıcı adlarını veya e-posta adresleri gibi kişisel verilerini topla değil.</span><span class="sxs-lookup"><span data-stu-id="c6738-135">The feature doesn't collect personal data, such as usernames or email addresses.</span></span> <span data-ttu-id="c6738-136">Kodunuzu taramaz ve adı, depodaki veya yazar gibi hassas proje düzeyi verileri ayıklamak değil.</span><span class="sxs-lookup"><span data-stu-id="c6738-136">It doesn't scan your code and doesn't extract sensitive project-level data, such as name, repo, or author.</span></span> <span data-ttu-id="c6738-137">Veriler güvenli bir şekilde kullanarak Microsoft sunucularına gönderilir [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) altında kısıtlı erişim tutulur ve katı güvenlik denetimleri güvenli altında yayımlanan teknolojisi [Azure Storage](https://azure.microsoft.com/services/storage/) sistemler.</span><span class="sxs-lookup"><span data-stu-id="c6738-137">The data is sent securely to Microsoft servers using [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technology, held under restricted access, and published under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

<span data-ttu-id="c6738-138">Araçlar nasıl kullanıldığı ve bunlar da, ne araçlarla oluşturmakta değil çalışırken bilmek isteriz.</span><span class="sxs-lookup"><span data-stu-id="c6738-138">We want to know how the tools are used and if they're working well, not what you're building with the tools.</span></span> <span data-ttu-id="c6738-139">Telemetri hassas verileri veya güvenli şekilde çalışıyoruz toplama veya açamayacağı veri işleme şüpheleniyorsanız [bir sorun dotnet/CLI depodaki sorunları dosya](https://github.com/dotnet/cli/issues) araştırma için.</span><span class="sxs-lookup"><span data-stu-id="c6738-139">If you suspect that the telemetry is collecting sensitive data or that we're insecurely or inappropriately handling data, [file an issue in the dotnet/cli repo issues](https://github.com/dotnet/cli/issues) for investigation.</span></span>

## <a name="published-data"></a><span data-ttu-id="c6738-140">Yayımlanan veriler</span><span class="sxs-lookup"><span data-stu-id="c6738-140">Published data</span></span>

<span data-ttu-id="c6738-141">Yayımlanan verileri üç aylık olarak kullanılabilir ve adresinde listelenmiş [.NET Core SDK kullanım verilerini](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md).</span><span class="sxs-lookup"><span data-stu-id="c6738-141">Published data is available quarterly and are listed at [.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md).</span></span> <span data-ttu-id="c6738-142">Bir veri dosyası sütunlarının şunlardır:</span><span class="sxs-lookup"><span data-stu-id="c6738-142">The columns of a data file are:</span></span>
- <span data-ttu-id="c6738-143">zaman damgası</span><span class="sxs-lookup"><span data-stu-id="c6738-143">Timestamp</span></span>
- <span data-ttu-id="c6738-144">Yineleme&#8224;</span><span class="sxs-lookup"><span data-stu-id="c6738-144">Occurrences&#8224;</span></span>
- <span data-ttu-id="c6738-145">Komut</span><span class="sxs-lookup"><span data-stu-id="c6738-145">Command</span></span>
- <span data-ttu-id="c6738-146">Coğrafi konum&#8225;</span><span class="sxs-lookup"><span data-stu-id="c6738-146">Geography&#8225;</span></span>
- <span data-ttu-id="c6738-147">OSFamily</span><span class="sxs-lookup"><span data-stu-id="c6738-147">OSFamily</span></span>
- <span data-ttu-id="c6738-148">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="c6738-148">RuntimeID</span></span>
- <span data-ttu-id="c6738-149">OSVersion</span><span class="sxs-lookup"><span data-stu-id="c6738-149">OSVersion</span></span>
- <span data-ttu-id="c6738-150">SDKVersion</span><span class="sxs-lookup"><span data-stu-id="c6738-150">SDKVersion</span></span>

<span data-ttu-id="c6738-151">&#8224;*Oluşum* sütunu bu komut, sıranın ölçümleri kullanılmak o gün toplam sayısını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c6738-151">&#8224;The *Occurrences* column displays the aggregate count of that command's use for that row's metrics that day.</span></span> 

<span data-ttu-id="c6738-152">&#8225;Genellikle, *Coğrafya* sütun bir ülke adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c6738-152">&#8225;Typically, the *Geography* column displays the name of a country.</span></span> <span data-ttu-id="c6738-153">Bazı durumlarda, bu sütun, .NET Core Antarktika veya yanlış konumu verileri kullanarak araştırmacılarının nedeniyle Antarktika kıtada görünür.</span><span class="sxs-lookup"><span data-stu-id="c6738-153">In some cases, the continent of Antarctica appears in this column, either due to researchers using .NET Core in Antarctica or incorrect location data.</span></span>

### <a name="example"></a><span data-ttu-id="c6738-154">Örnek</span><span class="sxs-lookup"><span data-stu-id="c6738-154">Example</span></span>

| <span data-ttu-id="c6738-155">zaman damgası</span><span class="sxs-lookup"><span data-stu-id="c6738-155">Timestamp</span></span>      | <span data-ttu-id="c6738-156">Yineleme</span><span class="sxs-lookup"><span data-stu-id="c6738-156">Occurrences</span></span> | <span data-ttu-id="c6738-157">Komut</span><span class="sxs-lookup"><span data-stu-id="c6738-157">Command</span></span> | <span data-ttu-id="c6738-158">coğrafi konum</span><span class="sxs-lookup"><span data-stu-id="c6738-158">Geography</span></span> | <span data-ttu-id="c6738-159">OSFamily</span><span class="sxs-lookup"><span data-stu-id="c6738-159">OSFamily</span></span> | <span data-ttu-id="c6738-160">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="c6738-160">RuntimeID</span></span>     | <span data-ttu-id="c6738-161">OSVersion</span><span class="sxs-lookup"><span data-stu-id="c6738-161">OSVersion</span></span> | <span data-ttu-id="c6738-162">SDKVersion</span><span class="sxs-lookup"><span data-stu-id="c6738-162">SDKVersion</span></span> |
| -------------- | ----------- | ------- | --------- | -------- | ------------- | --------- | ---------- |
| <span data-ttu-id="c6738-163">4/16/2017 0:00</span><span class="sxs-lookup"><span data-stu-id="c6738-163">4/16/2017 0:00</span></span> | <span data-ttu-id="c6738-164">8</span><span class="sxs-lookup"><span data-stu-id="c6738-164">8</span></span>           | <span data-ttu-id="c6738-165">çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c6738-165">run</span></span>     | <span data-ttu-id="c6738-166">Uganda</span><span class="sxs-lookup"><span data-stu-id="c6738-166">Uganda</span></span>    | <span data-ttu-id="c6738-167">Darwin</span><span class="sxs-lookup"><span data-stu-id="c6738-167">Darwin</span></span>   | <span data-ttu-id="c6738-168">osx.10.12 x64</span><span class="sxs-lookup"><span data-stu-id="c6738-168">osx.10.12-x64</span></span> | <span data-ttu-id="c6738-169">10.12</span><span class="sxs-lookup"><span data-stu-id="c6738-169">10.12</span></span>     | <span data-ttu-id="c6738-170">1.0.1</span><span class="sxs-lookup"><span data-stu-id="c6738-170">1.0.1</span></span>      |

### <a name="datasets"></a><span data-ttu-id="c6738-171">Veri kümeleri</span><span class="sxs-lookup"><span data-stu-id="c6738-171">Datasets</span></span>

[<span data-ttu-id="c6738-172">2016 - S3</span><span class="sxs-lookup"><span data-stu-id="c6738-172">2016 - Q3</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q3.tsv)  
[<span data-ttu-id="c6738-173">2016 - 4</span><span class="sxs-lookup"><span data-stu-id="c6738-173">2016 - Q4</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q4.tsv)  
[<span data-ttu-id="c6738-174">2017 - S1</span><span class="sxs-lookup"><span data-stu-id="c6738-174">2017 - Q1</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q1.tsv)  
[<span data-ttu-id="c6738-175">2017 - S2</span><span class="sxs-lookup"><span data-stu-id="c6738-175">2017 - Q2</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q2.tsv)

<span data-ttu-id="c6738-176">Ek veri kümeleri, standart bir URL biçimi kullanılarak gönderilir.</span><span class="sxs-lookup"><span data-stu-id="c6738-176">Additional datasets are posted using a standard URL format.</span></span> <span data-ttu-id="c6738-177">Değiştir `<YEAR>` değiştirin ve yıl `<QUARTER>` çeyreği ile (kullanmak `1`, `2`, `3`, veya `4`).</span><span class="sxs-lookup"><span data-stu-id="c6738-177">Replace `<YEAR>` with the year and replace `<QUARTER>` with the quarter of the year (use `1`, `2`, `3`, or `4`).</span></span> <span data-ttu-id="c6738-178">Dosyaları sekmeyle ayrılmış değerler (*TSV*) biçimi.</span><span class="sxs-lookup"><span data-stu-id="c6738-178">The files are in tab-separated values (*TSV*) format.</span></span> 

```
https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-<YEAR>-q<QUARTER>.tsv
```

## <a name="license"></a><span data-ttu-id="c6738-179">Lisans</span><span class="sxs-lookup"><span data-stu-id="c6738-179">License</span></span>

<span data-ttu-id="c6738-180">.NET Core Microsoft dağıtılması ile lisanslı [MICROSOFT .NET kitaplığı EULA](https://aka.ms/dotnet-core-eula).</span><span class="sxs-lookup"><span data-stu-id="c6738-180">The Microsoft distribution of .NET Core is licensed with the [MICROSOFT .NET LIBRARY EULA](https://aka.ms/dotnet-core-eula).</span></span> <span data-ttu-id="c6738-181">Bu lisans telemetri (aşağıda gösterilen) etkinleştirmek için "DATA" bölüm içerir.</span><span class="sxs-lookup"><span data-stu-id="c6738-181">This license includes the "DATA" section to enable telemetry (shown below).</span></span>

<span data-ttu-id="c6738-182">[.NET NuGet paketleri](https://www.nuget.org/profiles/dotnetframework) aynı lisans kullanır ancak telemetri etkinleştirmezseniz (bkz [kapsam](#scope)).</span><span class="sxs-lookup"><span data-stu-id="c6738-182">[.NET NuGet packages](https://www.nuget.org/profiles/dotnetframework) use the same license but don't enable telemetry (see [Scope](#scope)).</span></span>

> 2. <span data-ttu-id="c6738-183">VERİLER.</span><span class="sxs-lookup"><span data-stu-id="c6738-183">DATA.</span></span> <span data-ttu-id="c6738-184">Yazılım ve yazılımı kullanımınız hakkında bilgi toplamak ve Microsoft'a göndermek.</span><span class="sxs-lookup"><span data-stu-id="c6738-184">The software may collect information about you and your use of the software, and send that to Microsoft.</span></span> <span data-ttu-id="c6738-185">Microsoft, bu bilgiler, ürünlerimizi ve hizmetlerimizi geliştirmek için kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="c6738-185">Microsoft may use this information to improve our products and services.</span></span> <span data-ttu-id="c6738-186">Veri toplama hakkında daha fazla bilgi ve Yardım belgelerine ve adresindeki Gizlilik Bildirimi'ne kullanma http://go.microsoft.com/fwlink/?LinkId=528096.</span><span class="sxs-lookup"><span data-stu-id="c6738-186">You can learn more about data collection and use in the help documentation and the privacy statement at http://go.microsoft.com/fwlink/?LinkId=528096.</span></span> <span data-ttu-id="c6738-187">Bu uygulamalar için onay yazılımı kullanımınız çalışır.</span><span class="sxs-lookup"><span data-stu-id="c6738-187">Your use of the software operates as your consent to these practices.</span></span>

## <a name="disclosure"></a><span data-ttu-id="c6738-188">Açığa çıkması</span><span class="sxs-lookup"><span data-stu-id="c6738-188">Disclosure</span></span>

<span data-ttu-id="c6738-189">.NET Core CLI araçlarını komutlarından birini ilk kez çalıştırdığınızda, aşağıdaki metni görüntüle (örneğin, `dotnet restore`).</span><span class="sxs-lookup"><span data-stu-id="c6738-189">The .NET Core CLI Tools display the following text when you first run one of the commands (for example, `dotnet restore`).</span></span> <span data-ttu-id="c6738-190">Metin, çalıştırmakta olduğunuz SDK'sı sürümüne bağlı olarak biraz değişebilir.</span><span class="sxs-lookup"><span data-stu-id="c6738-190">Text may vary slightly depending on the version of the SDK you're running.</span></span> <span data-ttu-id="c6738-191">Bu "ilk Çalıştır" nasıl Microsoft, verilerin toplanması hakkında bilgilendirir deneyimidir.</span><span class="sxs-lookup"><span data-stu-id="c6738-191">This "first run" experience is how Microsoft notifies you about data collection.</span></span>

```console
Welcome to .NET Core!
---------------------
Learn more about .NET Core @ https://aka.ms/dotnet-docs. Use dotnet --help to see available commands or go to https://aka.ms/dotnet-cli-docs.
 
Telemetry
--------------
The .NET Core tools collect usage data in order to improve your experience. The data is anonymous and does not include command-line arguments. The data is collected by Microsoft and shared with the community.
You can opt out of telemetry by setting a DOTNET_CLI_TELEMETRY_OPTOUT environment variable to 1 using your favorite shell.
You can read more about .NET Core tools telemetry @ https://aka.ms/dotnet-cli-telemetry.
```

## <a name="see-also"></a><span data-ttu-id="c6738-192">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6738-192">See also</span></span>

[<span data-ttu-id="c6738-193">Ne biz .NET Core SDK Telemetri öğrendiniz</span><span class="sxs-lookup"><span data-stu-id="c6738-193">What we've learned from .NET Core SDK Telemetry</span></span>](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/)  
<span data-ttu-id="c6738-194">[Telemetri başvuru kaynağı (dotnet/CLI depodaki; release/2.0.0 dalı)](https://github.com/dotnet/cli/tree/release/2.0.0/src/dotnet/Telemetry) </span><span class="sxs-lookup"><span data-stu-id="c6738-194">[Telemetry reference source (dotnet/cli repo; release/2.0.0 branch)](https://github.com/dotnet/cli/tree/release/2.0.0/src/dotnet/Telemetry) </span></span>  
[<span data-ttu-id="c6738-195">.NET core SDK kullanım verileri</span><span class="sxs-lookup"><span data-stu-id="c6738-195">.NET Core SDK Usage Data</span></span>](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md)
