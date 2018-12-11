---
title: .NET core SDK'sı telemetri
description: Analiz, hangi verileri toplanır ve nasıl devre dışı bırakmak için kullanım bilgileri toplamasına .NET Core SDK'sı telemetri özellikleri keşfedin.
author: richlander
ms.date: 06/20/2018
ms.custom: seodec18
ms.openlocfilehash: 8b0b546d70eab837c2e075f839990870ae9ea6b1
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53168851"
---
# <a name="net-core-sdk-telemetry"></a><span data-ttu-id="ab651-103">.NET core SDK'sı telemetri</span><span class="sxs-lookup"><span data-stu-id="ab651-103">.NET Core SDK telemetry</span></span>

<span data-ttu-id="ab651-104">[.NET Core SDK'sı](index.md) içeren bir [telemetri özellik](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry) , kullanım bilgilerini toplar.</span><span class="sxs-lookup"><span data-stu-id="ab651-104">The [.NET Core SDK](index.md) includes a [telemetry feature](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry) that collects usage information.</span></span> <span data-ttu-id="ab651-105">.NET ekibi geliştirilebilir bu nedenle araçları nasıl kullanıldığını anladığını önemlidir.</span><span class="sxs-lookup"><span data-stu-id="ab651-105">It's important that the .NET Team understands how the tools are used so they can be improved.</span></span> <span data-ttu-id="ab651-106">Daha fazla bilgi için [.NET Core SDK'sı Telemetri öğrendiklerimizi](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/).</span><span class="sxs-lookup"><span data-stu-id="ab651-106">For more information, see [What we've learned from .NET Core SDK Telemetry](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/).</span></span>

<span data-ttu-id="ab651-107">Anonim ve yayınlanan hem Microsoft hem de altında topluluk tarafından kullanım için toplu bir biçimde toplanan verileri [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span><span class="sxs-lookup"><span data-stu-id="ab651-107">The collected data is anonymous and published in an aggregated form for use by both Microsoft and the community under the [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span></span>

## <a name="scope"></a><span data-ttu-id="ab651-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="ab651-108">Scope</span></span>

<span data-ttu-id="ab651-109">`dotnet` Komutu, hem uygulama hem de .NET Core CLI başlatmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ab651-109">The `dotnet` command is used to launch both apps and the .NET Core CLI.</span></span> <span data-ttu-id="ab651-110">`dotnet` Komutun kendisindeki telemetri toplamak değil.</span><span class="sxs-lookup"><span data-stu-id="ab651-110">The `dotnet` command itself doesn't collect telemetry.</span></span> <span data-ttu-id="ab651-111">.NET Core CLI komutları tarafından çalıştırılan `dotnet` komut telemetri toplar.</span><span class="sxs-lookup"><span data-stu-id="ab651-111">The .NET Core CLI commands run by the `dotnet` command collect the telemetry.</span></span>

<span data-ttu-id="ab651-112">Telemetri *etkin değilse* kullanırken `dotnet` kendisine bağlı bir komut ile komutu:</span><span class="sxs-lookup"><span data-stu-id="ab651-112">Telemetry *isn't enabled* when using the `dotnet` command itself, with no command attached:</span></span>

- `dotnet`
- `dotnet [path-to-app]`

<span data-ttu-id="ab651-113">Telemetri *etkin* kullanırken [.NET Core CLI komutları](index.md), örneğin:</span><span class="sxs-lookup"><span data-stu-id="ab651-113">Telemetry *is enabled* when using the [.NET Core CLI commands](index.md), such as:</span></span>

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`

## <a name="how-to-opt-out"></a><span data-ttu-id="ab651-114">İptal etme</span><span class="sxs-lookup"><span data-stu-id="ab651-114">How to opt out</span></span>

<span data-ttu-id="ab651-115">.NET Core SDK'sı telemetri özellik varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="ab651-115">The .NET Core SDK telemetry feature is enabled by default.</span></span> <span data-ttu-id="ab651-116">Ayarlayarak telemetri özelliği iyileştirilmiş `DOTNET_CLI_TELEMETRY_OPTOUT` ortam değişkenine `1` veya `true`.</span><span class="sxs-lookup"><span data-stu-id="ab651-116">Opt out of the telemetry feature by setting the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span>

## <a name="data-points"></a><span data-ttu-id="ab651-117">Veri noktaları</span><span class="sxs-lookup"><span data-stu-id="ab651-117">Data points</span></span>

<span data-ttu-id="ab651-118">Bu özellik aşağıdaki verileri toplar:</span><span class="sxs-lookup"><span data-stu-id="ab651-118">The feature collects the following data:</span></span>

- <span data-ttu-id="ab651-119">Zaman damgası çağırma&#8224;</span><span class="sxs-lookup"><span data-stu-id="ab651-119">Timestamp of invocation&#8224;</span></span>
- <span data-ttu-id="ab651-120">Komutu (örneğin "derleme") çağrılır&#8224;</span><span class="sxs-lookup"><span data-stu-id="ab651-120">Command invoked (for example, "build")&#8224;</span></span>
- <span data-ttu-id="ab651-121">Coğrafi konumunu belirlemek için kullanılan üç sekizli IP adresi&#8224;</span><span class="sxs-lookup"><span data-stu-id="ab651-121">Three octet IP address used to determine geographical location&#8224;</span></span>
- <span data-ttu-id="ab651-122">`ExitCode` komutu</span><span class="sxs-lookup"><span data-stu-id="ab651-122">`ExitCode` of the command</span></span>
- <span data-ttu-id="ab651-123">Test Çalıştırıcısı (için test projeleri)</span><span class="sxs-lookup"><span data-stu-id="ab651-123">Test runner (for test projects)</span></span>
- <span data-ttu-id="ab651-124">İşletim sistemi ve sürümü&#8224;</span><span class="sxs-lookup"><span data-stu-id="ab651-124">Operating system and version&#8224;</span></span>
- <span data-ttu-id="ab651-125">Çalışma zamanı kimlikleri çalışma zamanları düğümünde mevcut olup olmadığı</span><span class="sxs-lookup"><span data-stu-id="ab651-125">Whether runtime IDs are present in the runtimes node</span></span>
- <span data-ttu-id="ab651-126">.NET core SDK sürümü&#8224;</span><span class="sxs-lookup"><span data-stu-id="ab651-126">.NET Core SDK version&#8224;</span></span>

<span data-ttu-id="ab651-127">&#8224;Bu ölçüm yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="ab651-127">&#8224;This metric is published.</span></span>

<span data-ttu-id="ab651-128">.NET Core 2.0 SDK'sı ile başlayarak, yeni veri noktaları toplanır:</span><span class="sxs-lookup"><span data-stu-id="ab651-128">Starting with .NET Core 2.0 SDK, new data points are collected:</span></span>

- <span data-ttu-id="ab651-129">`dotnet` komut bağımsız değişkenleri ve seçenekleri: yalnızca bağımsız değişkenleri ve seçenekleri toplanan (değil rasgele dizeleri) bilinir.</span><span class="sxs-lookup"><span data-stu-id="ab651-129">`dotnet` command arguments and options: only known arguments and options are collected (not arbitrary strings).</span></span>
- <span data-ttu-id="ab651-130">SDK'sı bir kapsayıcıda kullanılıp kullanılmadığını.</span><span class="sxs-lookup"><span data-stu-id="ab651-130">Whether the SDK is running in a container.</span></span>
- <span data-ttu-id="ab651-131">Hedef çerçeve.</span><span class="sxs-lookup"><span data-stu-id="ab651-131">Target frameworks.</span></span>
- <span data-ttu-id="ab651-132">Karma MAC adresi: bir şifreleme açısından (SHA256) anonim ve benzersiz bir kimliği için bir makine.</span><span class="sxs-lookup"><span data-stu-id="ab651-132">Hashed MAC address: a cryptographically (SHA256) anonymous and unique ID for a machine.</span></span> <span data-ttu-id="ab651-133">Bu ölçüm yayımlanan değil.</span><span class="sxs-lookup"><span data-stu-id="ab651-133">This metric isn't published.</span></span>
- <span data-ttu-id="ab651-134">Karma geçerli çalışma dizini.</span><span class="sxs-lookup"><span data-stu-id="ab651-134">Hashed current working directory.</span></span>

<span data-ttu-id="ab651-135">Bu özellik, kullanıcı adları veya e-posta adresleri gibi kişisel verileri toplamaz.</span><span class="sxs-lookup"><span data-stu-id="ab651-135">The feature doesn't collect personal data, such as usernames or email addresses.</span></span> <span data-ttu-id="ab651-136">Bu, kodunuzu taramaz ve adı, depo veya yazar gibi hassas proje düzeyi verileri ayıklamak değil.</span><span class="sxs-lookup"><span data-stu-id="ab651-136">It doesn't scan your code and doesn't extract sensitive project-level data, such as name, repo, or author.</span></span> <span data-ttu-id="ab651-137">Veriler güvenli bir şekilde kullanarak Microsoft sunucularına gönderilir [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) kısıtlı erişim'in altında tutulması ve katı güvenlik denetimleri güvenli altında yayımlanan teknoloji [Azuredepolama](https://azure.microsoft.com/services/storage/) sistemler.</span><span class="sxs-lookup"><span data-stu-id="ab651-137">The data is sent securely to Microsoft servers using [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technology, held under restricted access, and published under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

<span data-ttu-id="ab651-138">.NET ekibi araçları nasıl kullanıldığını ve bunlar da ne araçlarla hedeflediğiniz platformun değil çalışıyorsanız bilmek istemektedir.</span><span class="sxs-lookup"><span data-stu-id="ab651-138">The .NET team wants to know how the tools are used and if they're working well, not what you're building with the tools.</span></span> <span data-ttu-id="ab651-139">Telemetri hassas veriler ya da toplama şüpheleniyorsanız veri endpoınt yapılıyor veya uygunsuz bir şekilde ele, sorunu bildirin [dotnet/CLI](https://github.com/dotnet/cli/issues) araştırma için depo.</span><span class="sxs-lookup"><span data-stu-id="ab651-139">If you suspect that the telemetry is collecting sensitive data or that the data is being insecurely or inappropriately handled, file an issue in the [dotnet/cli](https://github.com/dotnet/cli/issues) repository for investigation.</span></span>

## <a name="published-data"></a><span data-ttu-id="ab651-140">Yayımlanan veriler</span><span class="sxs-lookup"><span data-stu-id="ab651-140">Published data</span></span>

<span data-ttu-id="ab651-141">Yayımlanan veriler üç aylık olarak kullanılabilir ve listelenen [.NET Core SDK'sı kullanım verilerini](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md).</span><span class="sxs-lookup"><span data-stu-id="ab651-141">Published data is available quarterly and are listed at [.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md).</span></span> <span data-ttu-id="ab651-142">Bir veri dosyasının sütunları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ab651-142">The columns of a data file are:</span></span>

- <span data-ttu-id="ab651-143">Zaman damgası</span><span class="sxs-lookup"><span data-stu-id="ab651-143">Timestamp</span></span>
- <span data-ttu-id="ab651-144">Örnekleri&#8224;</span><span class="sxs-lookup"><span data-stu-id="ab651-144">Occurrences&#8224;</span></span>
- <span data-ttu-id="ab651-145">Komut</span><span class="sxs-lookup"><span data-stu-id="ab651-145">Command</span></span>
- <span data-ttu-id="ab651-146">Coğrafi konum&#8225;</span><span class="sxs-lookup"><span data-stu-id="ab651-146">Geography&#8225;</span></span>
- <span data-ttu-id="ab651-147">OSFamily</span><span class="sxs-lookup"><span data-stu-id="ab651-147">OSFamily</span></span>
- <span data-ttu-id="ab651-148">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="ab651-148">RuntimeID</span></span>
- <span data-ttu-id="ab651-149">OSVersion</span><span class="sxs-lookup"><span data-stu-id="ab651-149">OSVersion</span></span>
- <span data-ttu-id="ab651-150">SDKVersion</span><span class="sxs-lookup"><span data-stu-id="ab651-150">SDKVersion</span></span>

<span data-ttu-id="ab651-151">&#8224;*Oluşum* sütunu bu komutun kullanın, sıranın ölçümler için o gün toplam sayısını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ab651-151">&#8224;The *Occurrences* column displays the aggregate count of that command's use for that row's metrics that day.</span></span>

<span data-ttu-id="ab651-152">&#8225;Genellikle, *Coğrafya* sütun ülke adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ab651-152">&#8225;Typically, the *Geography* column displays the name of a country.</span></span> <span data-ttu-id="ab651-153">Bazı durumlarda, bu sütunda, .NET Core Antarktika ya da yanlış konum verileri kullanarak Araştırmacıları nedeniyle Antarktika, kıta görünür.</span><span class="sxs-lookup"><span data-stu-id="ab651-153">In some cases, the continent of Antarctica appears in this column, either due to researchers using .NET Core in Antarctica or incorrect location data.</span></span>

### <a name="example"></a><span data-ttu-id="ab651-154">Örnek</span><span class="sxs-lookup"><span data-stu-id="ab651-154">Example</span></span>

| <span data-ttu-id="ab651-155">Zaman damgası</span><span class="sxs-lookup"><span data-stu-id="ab651-155">Timestamp</span></span>      | <span data-ttu-id="ab651-156">Örnekleri</span><span class="sxs-lookup"><span data-stu-id="ab651-156">Occurrences</span></span> | <span data-ttu-id="ab651-157">Komut</span><span class="sxs-lookup"><span data-stu-id="ab651-157">Command</span></span> | <span data-ttu-id="ab651-158">Coğrafi konum</span><span class="sxs-lookup"><span data-stu-id="ab651-158">Geography</span></span> | <span data-ttu-id="ab651-159">OSFamily</span><span class="sxs-lookup"><span data-stu-id="ab651-159">OSFamily</span></span> | <span data-ttu-id="ab651-160">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="ab651-160">RuntimeID</span></span>     | <span data-ttu-id="ab651-161">OSVersion</span><span class="sxs-lookup"><span data-stu-id="ab651-161">OSVersion</span></span> | <span data-ttu-id="ab651-162">SDKVersion</span><span class="sxs-lookup"><span data-stu-id="ab651-162">SDKVersion</span></span> |
| -------------- | ----------- | ------- | --------- | -------- | ------------- | --------- | ---------- |
| <span data-ttu-id="ab651-163">4/16/2017 0:00</span><span class="sxs-lookup"><span data-stu-id="ab651-163">4/16/2017 0:00</span></span> | <span data-ttu-id="ab651-164">8</span><span class="sxs-lookup"><span data-stu-id="ab651-164">8</span></span>           | <span data-ttu-id="ab651-165">Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="ab651-165">run</span></span>     | <span data-ttu-id="ab651-166">Uganda</span><span class="sxs-lookup"><span data-stu-id="ab651-166">Uganda</span></span>    | <span data-ttu-id="ab651-167">Darwin</span><span class="sxs-lookup"><span data-stu-id="ab651-167">Darwin</span></span>   | <span data-ttu-id="ab651-168">osx.10.12 x64</span><span class="sxs-lookup"><span data-stu-id="ab651-168">osx.10.12-x64</span></span> | <span data-ttu-id="ab651-169">10.12</span><span class="sxs-lookup"><span data-stu-id="ab651-169">10.12</span></span>     | <span data-ttu-id="ab651-170">1.0.1</span><span class="sxs-lookup"><span data-stu-id="ab651-170">1.0.1</span></span>      |

### <a name="datasets"></a><span data-ttu-id="ab651-171">Veri kümeleri</span><span class="sxs-lookup"><span data-stu-id="ab651-171">Datasets</span></span>

[<span data-ttu-id="ab651-172">2016 - S3</span><span class="sxs-lookup"><span data-stu-id="ab651-172">2016 - Q3</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q3.tsv)  
[<span data-ttu-id="ab651-173">2016 - 4</span><span class="sxs-lookup"><span data-stu-id="ab651-173">2016 - Q4</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q4.tsv)  
[<span data-ttu-id="ab651-174">2017 - S1</span><span class="sxs-lookup"><span data-stu-id="ab651-174">2017 - Q1</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q1.tsv)  
[<span data-ttu-id="ab651-175">2017 - S2</span><span class="sxs-lookup"><span data-stu-id="ab651-175">2017 - Q2</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q2.tsv)  
[<span data-ttu-id="ab651-176">2017 - S3</span><span class="sxs-lookup"><span data-stu-id="ab651-176">2017 - Q3</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q3.tsv)  
[<span data-ttu-id="ab651-177">2017 - 4</span><span class="sxs-lookup"><span data-stu-id="ab651-177">2017 - Q4</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q4.tsv)  

<span data-ttu-id="ab651-178">Ek veri kümeleri, standart bir URL biçimi kullanılarak gönderilir.</span><span class="sxs-lookup"><span data-stu-id="ab651-178">Additional datasets are posted using a standard URL format.</span></span> <span data-ttu-id="ab651-179">Değiştirin `<YEAR>` yıl ve Değiştir `<QUARTER>` yılın çeyreği ile (kullanın `1`, `2`, `3`, veya `4`).</span><span class="sxs-lookup"><span data-stu-id="ab651-179">Replace `<YEAR>` with the year and replace `<QUARTER>` with the quarter of the year (use `1`, `2`, `3`, or `4`).</span></span> <span data-ttu-id="ab651-180">Dosyaları sekmeyle ayrılmış değerler (*TSV*) biçimi.</span><span class="sxs-lookup"><span data-stu-id="ab651-180">The files are in tab-separated values (*TSV*) format.</span></span>

`https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-<YEAR>-q<QUARTER>.tsv`

## <a name="license"></a><span data-ttu-id="ab651-181">Lisans</span><span class="sxs-lookup"><span data-stu-id="ab651-181">License</span></span>

<span data-ttu-id="ab651-182">Microsoft Dağıtım .NET Core ile lisanslanan [MICROSOFT .NET kitaplığı EULA](https://aka.ms/dotnet-core-eula).</span><span class="sxs-lookup"><span data-stu-id="ab651-182">The Microsoft distribution of .NET Core is licensed with the [MICROSOFT .NET LIBRARY EULA](https://aka.ms/dotnet-core-eula).</span></span> <span data-ttu-id="ab651-183">Bu lisans telemetri (aşağıda gösterilen) etkinleştirmek için "Veri" bölümü içerir.</span><span class="sxs-lookup"><span data-stu-id="ab651-183">This license includes the "DATA" section to enable telemetry (shown below).</span></span>

<span data-ttu-id="ab651-184">[.NET NuGet paketleri](https://www.nuget.org/profiles/dotnetframework) aynı lisans kullanın, ancak telemetri etkinleştirme (bkz [kapsam](#scope)).</span><span class="sxs-lookup"><span data-stu-id="ab651-184">[.NET NuGet packages](https://www.nuget.org/profiles/dotnetframework) use the same license but don't enable telemetry (see [Scope](#scope)).</span></span>

> 2. <span data-ttu-id="ab651-185">VERİLER.</span><span class="sxs-lookup"><span data-stu-id="ab651-185">DATA.</span></span> <span data-ttu-id="ab651-186">Yazılım siz ve yazılımı kullanımınız hakkında bilgi toplamak ve bunları Microsoft'a gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="ab651-186">The software may collect information about you and your use of the software, and send that to Microsoft.</span></span> <span data-ttu-id="ab651-187">Microsoft, bu bilgiler, ürünlerimizi ve hizmetlerimizi geliştirmek için kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="ab651-187">Microsoft may use this information to improve our products and services.</span></span> <span data-ttu-id="ab651-188">Veri toplama hakkında daha fazla bilgi ve Yardım belgelerine ve gizlilik bildirimine kullanın <http://go.microsoft.com/fwlink/?LinkId=528096>.</span><span class="sxs-lookup"><span data-stu-id="ab651-188">You can learn more about data collection and use in the help documentation and the privacy statement at <http://go.microsoft.com/fwlink/?LinkId=528096>.</span></span> <span data-ttu-id="ab651-189">Bu uygulamalar onay yazılımı kullanımınız çalışır.</span><span class="sxs-lookup"><span data-stu-id="ab651-189">Your use of the software operates as your consent to these practices.</span></span>

## <a name="disclosure"></a><span data-ttu-id="ab651-190">Açığa çıkması</span><span class="sxs-lookup"><span data-stu-id="ab651-190">Disclosure</span></span>

<span data-ttu-id="ab651-191">İlk birini çalıştırdığınızda, .NET Core SDK'sı aşağıdaki metni görüntüler [.NET Core CLI komutları](index.md) (örneğin, `dotnet restore`).</span><span class="sxs-lookup"><span data-stu-id="ab651-191">The .NET Core SDK displays the following text when you first run one of the [.NET Core CLI commands](index.md) (for example, `dotnet restore`).</span></span> <span data-ttu-id="ab651-192">Metin, çalıştırmakta olduğunuz SDK'sı sürümüne bağlı olarak biraz değişebilir.</span><span class="sxs-lookup"><span data-stu-id="ab651-192">Text may vary slightly depending on the version of the SDK you're running.</span></span> <span data-ttu-id="ab651-193">Nasıl Microsoft, veri toplama hakkında size bildirir, bu "İlk Çalıştırma" deneyimi sunar.</span><span class="sxs-lookup"><span data-stu-id="ab651-193">This "first run" experience is how Microsoft notifies you about data collection.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ab651-194">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab651-194">See also</span></span>

- [<span data-ttu-id="ab651-195">.NET Core SDK'sı Telemetri öğrendiklerimizi</span><span class="sxs-lookup"><span data-stu-id="ab651-195">What we've learned from .NET Core SDK Telemetry</span></span>](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/)
- [<span data-ttu-id="ab651-196">Telemetri başvuru kaynağı (dotnet/CLI depo)</span><span class="sxs-lookup"><span data-stu-id="ab651-196">Telemetry reference source (dotnet/cli repo)</span></span>](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry)
- [<span data-ttu-id="ab651-197">.NET core SDK'sı kullanım verileri</span><span class="sxs-lookup"><span data-stu-id="ab651-197">.NET Core SDK Usage Data</span></span>](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md)
