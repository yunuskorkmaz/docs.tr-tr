---
ms.openlocfilehash: eb3fa768a491f6c0ff4b15479beabd71b0670338
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937292"
---
### <a name="hosting-https-redirection-enabled-for-iis-out-of-process-apps"></a>Barındırma: IIS işlem dışı uygulamalar için HTTPS yeniden yönlendirmesi etkin

IIS out-of-process üzerinden barındırma için [ASP.NET Çekirdek Modülü (ANCM)](/aspnet/core/host-and-deploy/aspnet-core-module) Sürüm 13.0.19218.0 ASP.NET Core 3.0 ve 2.2 uygulamaları için mevcut bir HTTPS yönlendirme özelliği sağlar.

Tartışma için [dotnet/AspNetCore#15243'e](https://github.com/dotnet/AspNetCore/issues/15243)bakın.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="old-behavior"></a>Eski davranış

ASP.NET Core 2.1 proje şablonu ilk gibi <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A> HTTPS <xref:Microsoft.AspNetCore.Builder.HstsBuilderExtensions.UseHsts%2A>ara yazılım yöntemleri için destek tanıttı ve . Geliştirme deki uygulamalar varsayılan 443 bağlantı noktasını kullanmadığından, HTTPS yeniden yönlendirmesini etkinleştirmek için yapılandırmanın eklenmesi gerekiyordu. [HTTP Katı Aktarım Güvenliği (HSTS),](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html) yalnızca istek zaten HTTPS kullanıyorsa etkindir. Localhost varsayılan olarak atlanır.

#### <a name="new-behavior"></a>Yeni davranış

Core 3.0ASP.NET, IIS HTTPS senaryosu [geliştirildi.](https://github.com/dotnet/AspNetCore/pull/4685) Geliştirme yle, bir uygulama sunucunun HTTPS bağlantı `UseHttpsRedirection` noktalarını keşfedebilir ve varsayılan olarak çalışır hale getirebilir. Süreç içi kitaplık çerçeveyle sürülmeden yalnızca ASP.NET Core 3.0 uygulamalarını etkileyen `IServerAddresses` özellik ile işlem bileşeni bağlantı noktası keşfini gerçekleştirir. İşlem dışı bileşen, ortam değişkenini `ASPNETCORE_HTTPS_PORT` otomatik olarak eklemek üzere değiştirildi. Bu değişiklik, işlem dışı bileşen küresel olarak paylaşıldığından hem ASP.NET Core 2.2 hem de 3.0 uygulamalarını etkiledi. ASP.NET Core 2.1 uygulamaları, varsayılan olarak ANCM'nin önceki bir sürümünü kullandıkları için etkilenmez.

Önceki davranış, Core 3.0.1 ve 3.1.0 Preview 3'ASP.NET ASP.NET Core 2.x'teki davranış değişikliklerini tersine çevirmek için değiştirildi. Bu değişiklikler yalnızca IIS'nin işlem dışı uygulamalarını etkiler.

Yukarıda ayrıntılı olarak, Core 3.0.0 ASP.NET yükleme de ASP.NET `UseHttpsRedirection` Core 2.x uygulamalarda ara etkinleştirme yan etkisi vardı. ASP.NET Core 3.0.1 ve 3.1.0 Preview 3'te ANCM'de bir değişiklik yapıldı ve bunları yüklemek artık ASP.NET Core 2.x uygulamaları üzerinde bu etkiye sahip değil. ANCM'nin core 3.0.0'ASP.NET doldurulan `ASPNETCORE_HTTPS_PORT` ortam `ASPNETCORE_ANCM_HTTPS_PORT` değişkeni, 3.0.1 ve 3.1.0 Önizleme 3'ASP.NET olarak değiştirildi. `UseHttpsRedirection`hem yeni hem de eski değişkenleri anlamak için bu sürümlerde de güncelleştirildi. ASP.NET Core 2.x güncelleştirilmez. Sonuç olarak, varsayılan olarak devre dışı bırakılmış olmanın önceki davranışına geri döner.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Core 3.0 işlevselliği ASP.NET geliştirildi.

#### <a name="recommended-action"></a>Önerilen eylem

Tüm istemcilerin HTTPS kullanmasını istiyorsanız hiçbir işlem gerekmez. Bazı istemcilerin HTTP'yi kullanmasına izin vermek için aşağıdaki adımlardan birini izleyin:

* Projenizin `UseHttpsRedirection` `UseHsts` `Startup.Configure` yöntemine yapılan aramaları kaldırın ve uygulamayı yeniden dağıtın.
* *web.config* dosyanızda, ortam `ASPNETCORE_HTTPS_PORT` değişkenini boş bir dize olarak ayarlayın. Bu değişiklik, uygulamayı yeniden dağıtmadan doğrudan sunucuda oluşabilir. Örnek:

    ```xml
    <aspNetCore processPath="dotnet" arguments=".\WebApplication3.dll" stdoutLogEnabled="false" stdoutLogFile="\\?\%home%\LogFiles\stdout" >
        <environmentVariables>
        <environmentVariable name="ASPNETCORE_HTTPS_PORT" value="" />
        </environmentVariables>
    </aspNetCore>
    ```

`UseHttpsRedirection`hala olabilir:

* ASP.NET Core 2.x'te ortam `ASPNETCORE_HTTPS_PORT` değişkenini uygun bağlantı noktası numarasına ayarlayarak el ile etkinleştirilir (çoğu üretim senaryosunda 443).
* Boş bir dize değeri ile `ASPNETCORE_ANCM_HTTPS_PORT` tanımlayarak Core 3.x ASP.NET devre dışı bırakılır. Bu değer, önceki `ASPNETCORE_HTTPS_PORT` örnekle aynı şekilde ayarlanır.

Core 3.0.0 uygulamaları ASP.NET çalışan makineler, ASP.NET Core 3.1.0 Preview 3 ANCM'yi yüklemeden önce ASP.NET Core 3.0.1 çalışma süresini yüklemelidir. Bunu yapmak, `UseHttpsRedirection` ASP.NET Core 3.0 uygulamaları için beklendiği gibi çalışmaya devam etmesini sağlar.

Azure Uygulama Hizmeti'nde ANCM, genel yapısı nedeniyle çalışma zamanından ayrı bir zamanlamada dağıtılır. ANCM, Core 3.0.1 ve 3.1.0 ASP.NET dağıtıldıktan sonra bu değişikliklerle birlikte Azure'a dağıtıldı.

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)`

-->
