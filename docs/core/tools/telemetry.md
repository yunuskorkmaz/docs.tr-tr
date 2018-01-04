---
title: ".NET core CLI araçlarını telemetri"
description: "Analiz, hangi verileri toplanır ve nasıl devre dışı bırakmak için kullanım bilgilerini toplamasına .NET Core araçları telemetri özellikleri keşfedin."
keywords: .NET, .NET core telemetri
author: richlander
ms.author: mairaw
ms.date: 08/04/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 480df976-7568-4df4-9d26-9911357b5a31
ms.workload: dotnetcore
ms.openlocfilehash: 66ad63f0b2a2f62f34f0784b236d242f1d92066a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="net-core-cli-tools-telemetry"></a><span data-ttu-id="c736f-104">.NET core CLI araçlarını telemetri</span><span class="sxs-lookup"><span data-stu-id="c736f-104">.NET Core CLI Tools telemetry</span></span>

<span data-ttu-id="c736f-105">[.NET Core SDK](index.md) içeren bir [telemetri özellik](https://github.com/dotnet/cli/pull/2145) kullanım bilgilerini toplar.</span><span class="sxs-lookup"><span data-stu-id="c736f-105">The [.NET Core SDK](index.md) includes a [telemetry feature](https://github.com/dotnet/cli/pull/2145) that collects usage information.</span></span> <span data-ttu-id="c736f-106">.NET ekibi, böylece biz artırabilir araçları nasıl kullanıldığını algıladığını önemlidir.</span><span class="sxs-lookup"><span data-stu-id="c736f-106">It's important that the .NET Team understands how the tools are used so that we can improve them.</span></span> <span data-ttu-id="c736f-107">Daha fazla bilgi için bkz: [ne biz .NET Core SDK Telemetri öğrendiğinize](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/).</span><span class="sxs-lookup"><span data-stu-id="c736f-107">For more information, see [What we've learned from .NET Core SDK Telemetry](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/).</span></span>

<span data-ttu-id="c736f-108">Anonim ve kullanmak için toplanan biçimde yayınlanan hem Microsoft hem de altında topluluk tarafından toplanan veriler [Creative Commons Attribution lisans](https://creativecommons.org/licenses/by/4.0/).</span><span class="sxs-lookup"><span data-stu-id="c736f-108">The collected data is anonymous and published in an aggregated form for use by both Microsoft and the community under the [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span></span> 

## <a name="scope"></a><span data-ttu-id="c736f-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="c736f-109">Scope</span></span>

<span data-ttu-id="c736f-110">`dotnet` Komutu, hem uygulamalar hem de .NET Core CLI başlatmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c736f-110">The `dotnet` command is used to launch both apps and the .NET Core CLI.</span></span> <span data-ttu-id="c736f-111">`dotnet` Komutu kendisi telemetri toplamak değil.</span><span class="sxs-lookup"><span data-stu-id="c736f-111">The `dotnet` command itself doesn't collect telemetry.</span></span> <span data-ttu-id="c736f-112">.NET Core CLI komutları tarafından çalıştırılan `dotnet` komutu telemetri topla.</span><span class="sxs-lookup"><span data-stu-id="c736f-112">The .NET Core CLI commands run by the `dotnet` command collect the telemetry.</span></span>

<span data-ttu-id="c736f-113">Telemetri *etkinleştirilmemiş* kullanırken `dotnet` kendisine bağlı hiçbir komutuyla komutu:</span><span class="sxs-lookup"><span data-stu-id="c736f-113">Telemetry *isn't enabled* when using the `dotnet` command itself, with no command attached:</span></span>

- `dotnet`
- `dotnet [path-to-app]`

<span data-ttu-id="c736f-114">Telemetri *etkin* kullanırken [.NET Core CLI komutları](index.md), gibi:</span><span class="sxs-lookup"><span data-stu-id="c736f-114">Telemetry *is enabled* when using the [.NET Core CLI commands](index.md), such as:</span></span>

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`


## <a name="behavior"></a><span data-ttu-id="c736f-115">Davranış</span><span class="sxs-lookup"><span data-stu-id="c736f-115">Behavior</span></span>

<span data-ttu-id="c736f-116">.NET Core CLI araçlarını telemetri özellik varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="c736f-116">The .NET Core CLI Tools telemetry feature is enabled by default.</span></span> <span data-ttu-id="c736f-117">Üyelikten çıkmak ayarlayarak telemetri özelliğinin `DOTNET_CLI_TELEMETRY_OPTOUT` ortam değişkenine `1` veya `true`.</span><span class="sxs-lookup"><span data-stu-id="c736f-117">Opt-out of the telemetry feature by setting the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span>

## <a name="data-points"></a><span data-ttu-id="c736f-118">Veri noktaları</span><span class="sxs-lookup"><span data-stu-id="c736f-118">Data points</span></span>

<span data-ttu-id="c736f-119">Bu özellik aşağıdaki verileri toplar:</span><span class="sxs-lookup"><span data-stu-id="c736f-119">The feature collects the following data:</span></span>

- <span data-ttu-id="c736f-120">Zaman damgası çağırma &#8224;</span><span class="sxs-lookup"><span data-stu-id="c736f-120">Timestamp of invocation&#8224;</span></span>
- <span data-ttu-id="c736f-121">(Örneğin "Oluştur") çağrılan komut &#8224;</span><span class="sxs-lookup"><span data-stu-id="c736f-121">Command invoked (for example, "build")&#8224;</span></span>
- <span data-ttu-id="c736f-122">Coğrafi konum &#8224;belirlemek için kullanılan üç sekizli IP adresini;</span><span class="sxs-lookup"><span data-stu-id="c736f-122">Three octet IP address used to determine geographical location&#8224;</span></span>
- <span data-ttu-id="c736f-123">`ExitCode`komutu</span><span class="sxs-lookup"><span data-stu-id="c736f-123">`ExitCode` of the command</span></span>
- <span data-ttu-id="c736f-124">Test Çalıştırıcısı (için test projeleri)</span><span class="sxs-lookup"><span data-stu-id="c736f-124">Test runner (for test projects)</span></span>
- <span data-ttu-id="c736f-125">İşletim sistemi ve sürümü &#8224;</span><span class="sxs-lookup"><span data-stu-id="c736f-125">Operating system and version&#8224;</span></span>
- <span data-ttu-id="c736f-126">Çalışma zamanı kimlikleri çalışma zamanları düğümünde mevcut olup olmadığı</span><span class="sxs-lookup"><span data-stu-id="c736f-126">Whether runtime IDs are present in the runtimes node</span></span>
- <span data-ttu-id="c736f-127">.NET core SDK sürüm &#8224;</span><span class="sxs-lookup"><span data-stu-id="c736f-127">.NET Core SDK version&#8224;</span></span>

<span data-ttu-id="c736f-128">&#8224; Bu ölçüm yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="c736f-128">&#8224;This metric is published.</span></span>

<span data-ttu-id="c736f-129">.NET Core SDK 2.0 ile başlayarak, yeni veri noktaları toplanır:</span><span class="sxs-lookup"><span data-stu-id="c736f-129">Starting with .NET Core SDK 2.0, new data points are collected:</span></span>

- <span data-ttu-id="c736f-130">`dotnet`komut bağımsız değişkenleri ve seçenekleri: yalnızca bağımsız değişkenleri ve seçenekleri toplanan (değil rastgele dizeleri) bilinir.</span><span class="sxs-lookup"><span data-stu-id="c736f-130">`dotnet` command arguments and options: only known arguments and options are collected (not arbitrary strings).</span></span>
- <span data-ttu-id="c736f-131">SDK bir kapsayıcıda çalışıp çalışmadığını.</span><span class="sxs-lookup"><span data-stu-id="c736f-131">Whether the SDK is running in a container.</span></span>
- <span data-ttu-id="c736f-132">Bir hedef çerçeve.</span><span class="sxs-lookup"><span data-stu-id="c736f-132">Target frameworks.</span></span>
- <span data-ttu-id="c736f-133">Karma MAC adresi: bir şifreleme açısından (SHA256) anonim ve benzersiz kimliği için bir makine.</span><span class="sxs-lookup"><span data-stu-id="c736f-133">Hashed MAC address: a cryptographically (SHA256) anonymous and unique ID for a machine.</span></span> <span data-ttu-id="c736f-134">Bu ölçüm yayımlanmaz.</span><span class="sxs-lookup"><span data-stu-id="c736f-134">This metric is not published.</span></span>
- <span data-ttu-id="c736f-135">Karma geçerli çalışma dizini.</span><span class="sxs-lookup"><span data-stu-id="c736f-135">Hashed current working directory.</span></span>

<span data-ttu-id="c736f-136">Özellik kullanıcı adlarını veya e-posta adresleri gibi kişisel verilerini topla değil.</span><span class="sxs-lookup"><span data-stu-id="c736f-136">The feature doesn't collect personal data, such as usernames or email addresses.</span></span> <span data-ttu-id="c736f-137">Kodunuzu taramaz ve adı, depodaki veya yazar gibi hassas proje düzeyi verileri ayıklamak değil.</span><span class="sxs-lookup"><span data-stu-id="c736f-137">It doesn't scan your code and doesn't extract sensitive project-level data, such as name, repo, or author.</span></span> <span data-ttu-id="c736f-138">Veriler güvenli bir şekilde kullanarak Microsoft sunucularına gönderilir [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) altında kısıtlı erişim tutulur ve katı güvenlik denetimleri güvenli altında yayımlanan teknolojisi [Azure Storage](https://azure.microsoft.com/services/storage/) sistemler.</span><span class="sxs-lookup"><span data-stu-id="c736f-138">The data is sent securely to Microsoft servers using [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technology, held under restricted access, and published under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

<span data-ttu-id="c736f-139">Araçlar nasıl kullanıldığı ve bunlar da, ne araçlarla oluşturmakta değil çalışırken bilmek isteriz.</span><span class="sxs-lookup"><span data-stu-id="c736f-139">We want to know how the tools are used and if they're working well, not what you're building with the tools.</span></span> <span data-ttu-id="c736f-140">Telemetri hassas verileri veya güvenli şekilde çalışıyoruz toplama veya açamayacağı veri işleme şüpheleniyorsanız [bir sorun dotnet/CLI depodaki sorunları dosya](https://github.com/dotnet/cli/issues) araştırma için.</span><span class="sxs-lookup"><span data-stu-id="c736f-140">If you suspect that the telemetry is collecting sensitive data or that we're insecurely or inappropriately handling data, [file an issue in the dotnet/cli repo issues](https://github.com/dotnet/cli/issues) for investigation.</span></span>

## <a name="published-data"></a><span data-ttu-id="c736f-141">Yayımlanan veriler</span><span class="sxs-lookup"><span data-stu-id="c736f-141">Published data</span></span>

<span data-ttu-id="c736f-142">Yayımlanan verileri üç aylık olarak kullanılabilir ve adresinde listelenmiş [.NET Core SDK kullanım verilerini](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md).</span><span class="sxs-lookup"><span data-stu-id="c736f-142">Published data is available quarterly and are listed at [.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md).</span></span> <span data-ttu-id="c736f-143">Bir veri dosyası sütunlarının şunlardır:</span><span class="sxs-lookup"><span data-stu-id="c736f-143">The columns of a data file are:</span></span>
- <span data-ttu-id="c736f-144">zaman damgası</span><span class="sxs-lookup"><span data-stu-id="c736f-144">Timestamp</span></span>
- <span data-ttu-id="c736f-145">Yineleme &#8224;</span><span class="sxs-lookup"><span data-stu-id="c736f-145">Occurrences&#8224;</span></span>
- <span data-ttu-id="c736f-146">Komut</span><span class="sxs-lookup"><span data-stu-id="c736f-146">Command</span></span>
- <span data-ttu-id="c736f-147">Coğrafya &#8225;</span><span class="sxs-lookup"><span data-stu-id="c736f-147">Geography&#8225;</span></span>
- <span data-ttu-id="c736f-148">OSFamily</span><span class="sxs-lookup"><span data-stu-id="c736f-148">OSFamily</span></span>
- <span data-ttu-id="c736f-149">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="c736f-149">RuntimeID</span></span>
- <span data-ttu-id="c736f-150">OSVersion</span><span class="sxs-lookup"><span data-stu-id="c736f-150">OSVersion</span></span>
- <span data-ttu-id="c736f-151">SDKVersion</span><span class="sxs-lookup"><span data-stu-id="c736f-151">SDKVersion</span></span>

<span data-ttu-id="c736f-152">&#8224; *Oluşum* sütunu bu komut, sıranın ölçümleri kullanılmak o gün toplam sayısını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c736f-152">&#8224;The *Occurrences* column displays the aggregate count of that command's use for that row's metrics that day.</span></span> 

<span data-ttu-id="c736f-153">&#8225; Genellikle, *Coğrafya* sütun bir ülke adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c736f-153">&#8225;Typically, the *Geography* column displays the name of a country.</span></span> <span data-ttu-id="c736f-154">Bazı durumlarda, bu sütun, .NET Core Antarktika veya yanlış konumu verileri kullanarak araştırmacılarının nedeniyle Antarktika kıtada görünür.</span><span class="sxs-lookup"><span data-stu-id="c736f-154">In some cases, the continent of Antarctica appears in this column, either due to researchers using .NET Core in Antarctica or incorrect location data.</span></span>

### <a name="example"></a><span data-ttu-id="c736f-155">Örnek</span><span class="sxs-lookup"><span data-stu-id="c736f-155">Example</span></span>

| <span data-ttu-id="c736f-156">zaman damgası</span><span class="sxs-lookup"><span data-stu-id="c736f-156">Timestamp</span></span>      | <span data-ttu-id="c736f-157">Yineleme</span><span class="sxs-lookup"><span data-stu-id="c736f-157">Occurrences</span></span> | <span data-ttu-id="c736f-158">Komut</span><span class="sxs-lookup"><span data-stu-id="c736f-158">Command</span></span> | <span data-ttu-id="c736f-159">coğrafi konum</span><span class="sxs-lookup"><span data-stu-id="c736f-159">Geography</span></span> | <span data-ttu-id="c736f-160">OSFamily</span><span class="sxs-lookup"><span data-stu-id="c736f-160">OSFamily</span></span> | <span data-ttu-id="c736f-161">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="c736f-161">RuntimeID</span></span>     | <span data-ttu-id="c736f-162">OSVersion</span><span class="sxs-lookup"><span data-stu-id="c736f-162">OSVersion</span></span> | <span data-ttu-id="c736f-163">SDKVersion</span><span class="sxs-lookup"><span data-stu-id="c736f-163">SDKVersion</span></span> |
| -------------- | ----------- | ------- | --------- | -------- | ------------- | --------- | ---------- |
| <span data-ttu-id="c736f-164">4/16/2017 0:00</span><span class="sxs-lookup"><span data-stu-id="c736f-164">4/16/2017 0:00</span></span> | <span data-ttu-id="c736f-165">8</span><span class="sxs-lookup"><span data-stu-id="c736f-165">8</span></span>           | <span data-ttu-id="c736f-166">çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c736f-166">run</span></span>     | <span data-ttu-id="c736f-167">Uganda</span><span class="sxs-lookup"><span data-stu-id="c736f-167">Uganda</span></span>    | <span data-ttu-id="c736f-168">Darwin</span><span class="sxs-lookup"><span data-stu-id="c736f-168">Darwin</span></span>   | <span data-ttu-id="c736f-169">osx.10.12 x64</span><span class="sxs-lookup"><span data-stu-id="c736f-169">osx.10.12-x64</span></span> | <span data-ttu-id="c736f-170">10.12</span><span class="sxs-lookup"><span data-stu-id="c736f-170">10.12</span></span>     | <span data-ttu-id="c736f-171">1.0.1</span><span class="sxs-lookup"><span data-stu-id="c736f-171">1.0.1</span></span>      |

### <a name="datasets"></a><span data-ttu-id="c736f-172">Veri kümeleri</span><span class="sxs-lookup"><span data-stu-id="c736f-172">Datasets</span></span>

[<span data-ttu-id="c736f-173">2016 - S3</span><span class="sxs-lookup"><span data-stu-id="c736f-173">2016 - Q3</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q3.tsv)  
[<span data-ttu-id="c736f-174">2016 - 4</span><span class="sxs-lookup"><span data-stu-id="c736f-174">2016 - Q4</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q4.tsv)  
[<span data-ttu-id="c736f-175">2017 - S1</span><span class="sxs-lookup"><span data-stu-id="c736f-175">2017 - Q1</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q1.tsv)  
[<span data-ttu-id="c736f-176">2017 - S2</span><span class="sxs-lookup"><span data-stu-id="c736f-176">2017 - Q2</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q2.tsv)

<span data-ttu-id="c736f-177">Ek veri kümeleri, standart bir URL biçimi kullanılarak gönderilir.</span><span class="sxs-lookup"><span data-stu-id="c736f-177">Additional datasets are posted using a standard URL format.</span></span> <span data-ttu-id="c736f-178">Değiştir `<YEAR>` değiştirin ve yıl `<QUARTER>` çeyreği ile (kullanmak `1`, `2`, `3`, veya `4`).</span><span class="sxs-lookup"><span data-stu-id="c736f-178">Replace `<YEAR>` with the year and replace `<QUARTER>` with the quarter of the year (use `1`, `2`, `3`, or `4`).</span></span> <span data-ttu-id="c736f-179">Dosyaları sekmeyle ayrılmış değerler (*TSV*) biçimi.</span><span class="sxs-lookup"><span data-stu-id="c736f-179">The files are in tab-separated values (*TSV*) format.</span></span> 

```
https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-<YEAR>-q<QUARTER>.tsv
```

## <a name="license"></a><span data-ttu-id="c736f-180">Lisans</span><span class="sxs-lookup"><span data-stu-id="c736f-180">License</span></span>

<span data-ttu-id="c736f-181">.NET Core Microsoft dağıtılması ile lisanslı [MICROSOFT .NET kitaplığı EULA](https://aka.ms/dotnet-core-eula).</span><span class="sxs-lookup"><span data-stu-id="c736f-181">The Microsoft distribution of .NET Core is licensed with the [MICROSOFT .NET LIBRARY EULA](https://aka.ms/dotnet-core-eula).</span></span> <span data-ttu-id="c736f-182">Bu lisans telemetri (aşağıda gösterilen) etkinleştirmek için "DATA" bölüm içerir.</span><span class="sxs-lookup"><span data-stu-id="c736f-182">This license includes the "DATA" section to enable telemetry (shown below).</span></span>

<span data-ttu-id="c736f-183">[.NET NuGet paketleri](https://www.nuget.org/profiles/dotnetframework) aynı lisans kullanır ancak telemetri etkinleştirmezseniz (bkz [kapsam](#scope)).</span><span class="sxs-lookup"><span data-stu-id="c736f-183">[.NET NuGet packages](https://www.nuget.org/profiles/dotnetframework) use the same license but don't enable telemetry (see [Scope](#scope)).</span></span>

> 2. <span data-ttu-id="c736f-184">VERİLER.</span><span class="sxs-lookup"><span data-stu-id="c736f-184">DATA.</span></span> <span data-ttu-id="c736f-185">Yazılım ve yazılımı kullanımınız hakkında bilgi toplamak ve Microsoft'a göndermek.</span><span class="sxs-lookup"><span data-stu-id="c736f-185">The software may collect information about you and your use of the software, and send that to Microsoft.</span></span> <span data-ttu-id="c736f-186">Microsoft, bu bilgiler, ürünlerimizi ve hizmetlerimizi geliştirmek için kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="c736f-186">Microsoft may use this information to improve our products and services.</span></span> <span data-ttu-id="c736f-187">Veri toplama hakkında daha fazla bilgi ve Yardım belgelerine ve http://go.microsoft.com/fwlink/?LinkId=528096 adresindeki Gizlilik Bildirimi'ne kullanın.</span><span class="sxs-lookup"><span data-stu-id="c736f-187">You can learn more about data collection and use in the help documentation and the privacy statement at http://go.microsoft.com/fwlink/?LinkId=528096.</span></span> <span data-ttu-id="c736f-188">Bu uygulamalar için onay yazılımı kullanımınız çalışır.</span><span class="sxs-lookup"><span data-stu-id="c736f-188">Your use of the software operates as your consent to these practices.</span></span>

## <a name="disclosure"></a><span data-ttu-id="c736f-189">Açığa çıkması</span><span class="sxs-lookup"><span data-stu-id="c736f-189">Disclosure</span></span>

<span data-ttu-id="c736f-190">.NET Core CLI araçlarını komutlarından birini ilk kez çalıştırdığınızda, aşağıdaki metni görüntüle (örneğin, `dotnet restore`).</span><span class="sxs-lookup"><span data-stu-id="c736f-190">The .NET Core CLI Tools display the following text when you first run one of the commands (for example, `dotnet restore`).</span></span> <span data-ttu-id="c736f-191">Metin, çalıştırmakta olduğunuz SDK'sı sürümüne bağlı olarak biraz değişebilir.</span><span class="sxs-lookup"><span data-stu-id="c736f-191">Text may vary slightly depending on the version of the SDK you're running.</span></span> <span data-ttu-id="c736f-192">Bu "ilk Çalıştır" nasıl Microsoft, verilerin toplanması hakkında bilgilendirir deneyimidir.</span><span class="sxs-lookup"><span data-stu-id="c736f-192">This "first run" experience is how Microsoft notifies you about data collection.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c736f-193">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c736f-193">See also</span></span>

[<span data-ttu-id="c736f-194">Ne biz .NET Core SDK Telemetri öğrendiniz</span><span class="sxs-lookup"><span data-stu-id="c736f-194">What we've learned from .NET Core SDK Telemetry</span></span>](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/)  
<span data-ttu-id="c736f-195">[Telemetri başvuru kaynağı (dotnet/CLI depodaki; release/2.0.0 dalı)](https://github.com/dotnet/cli/blob/release/2.0.0/src/dotnet/Telemetry.cs) </span><span class="sxs-lookup"><span data-stu-id="c736f-195">[Telemetry reference source (dotnet/cli repo; release/2.0.0 branch)](https://github.com/dotnet/cli/blob/release/2.0.0/src/dotnet/Telemetry.cs) </span></span>  
[<span data-ttu-id="c736f-196">.NET core SDK kullanım verileri</span><span class="sxs-lookup"><span data-stu-id="c736f-196">.NET Core SDK Usage Data</span></span>](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md)
