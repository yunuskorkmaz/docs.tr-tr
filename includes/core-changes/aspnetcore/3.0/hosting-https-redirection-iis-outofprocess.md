---
ms.openlocfilehash: eb3fa768a491f6c0ff4b15479beabd71b0670338
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937292"
---
### <a name="hosting-https-redirection-enabled-for-iis-out-of-process-apps"></a>Barındırma: IIS işlem dışı uygulamalar için HTTPS yönlendirmesi etkinleştirildi

IIS işlem dışı ile barındırmak için [ASP.NET Core modülünün (ANCM)](/aspnet/core/host-and-deploy/aspnet-core-module) sürüm 13.0.19218.0, var olan bir https yeniden yönlendirme özelliğini ASP.NET Core 3,0 ve 2,2 uygulamaları için sunar.

Tartışma için bkz. [DotNet/AspNetCore # 15243](https://github.com/dotnet/AspNetCore/issues/15243).

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

ASP.NET Core 2,1 proje şablonu, önce <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A> ve <xref:Microsoft.AspNetCore.Builder.HstsBuilderExtensions.UseHsts%2A>gibi HTTPS ara yazılım yöntemlerine yönelik destek sunmuştur. Geliştirme aşamasında uygulamalar varsayılan 443 bağlantı noktasını kullandıklarından, HTTPS yeniden yönlendirme özelliğinin etkinleştirilmesi, yapılandırmanın eklenmesi için gereklidir. [Http katı aktarım güvenliği (HSTS)](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html) yalnızca Istek zaten https kullanıyorsa etkindir. Localhost varsayılan olarak atlanır.

#### <a name="new-behavior"></a>Yeni davranış

ASP.NET Core 3,0 ' de IIS HTTPS senaryosu [geliştirilmiştir](https://github.com/dotnet/AspNetCore/pull/4685). Geliştirme sayesinde, bir uygulama sunucunun HTTPS bağlantı noktalarını bulabilir ve varsayılan olarak `UseHttpsRedirection` çalışır. İşlem içi bileşen bağlantı noktası bulma işlemini yalnızca ASP.NET Core 3,0 uygulamalarını etkileyen `IServerAddresses` özelliği ile gerçekleştirdi. böylece işlem içi kitaplık Framework ile birlikte sürümlüdür. `ASPNETCORE_HTTPS_PORT` ortam değişkenini otomatik olarak eklemek için işlem dışı bileşen değişti. Bu değişiklik, işlem dışı bileşen genel olarak paylaşıldığı için ASP.NET Core 2,2 ve 3,0 uygulamalarından her ikisini de etkilemiştir. ASP.NET Core 2,1 uygulamaları, varsayılan olarak ANCM 'nin önceki bir sürümünü kullandıkları için etkilenmez.

Önceki davranış ASP.NET Core 3.0.1 ve 3.1.0 Preview 3 ' te değiştirilmiştir ASP.NET Core 2. x içindeki davranış değişiklikleri tersine çevirin. Bu değişiklikler yalnızca IIS işlem dışı uygulamaları etkiler.

Yukarıda açıklandığı gibi, yükleme ASP.NET Core 3.0.0, ASP.NET Core 2. x uygulamalarında `UseHttpsRedirection` ara yazılımını da etkinleştiren yan etkiye sahiptir. ASP.NET Core 3.0.1 ve 3.1.0 Preview 3 ' te bir değişiklik yapılmıştır. bu nedenle, bunları yüklemek artık ASP.NET Core 2. x uygulamaları üzerinde bu etkiye sahip değildir. ASP.NET Core 3.0.0 içinde doldurulmuş bir `ASPNETCORE_HTTPS_PORT` ortam değişkeni, ASP.NET Core 3.0.1 ve 3.1.0 Preview 3 ' te `ASPNETCORE_ANCM_HTTPS_PORT` olarak değiştirilmiştir. `UseHttpsRedirection` Ayrıca, hem yeni hem de eski değişkenleri anlamak için bu sürümlerde güncelleştirildi. 2\. x ASP.NET Core güncelleştirilmeyecek. Sonuç olarak, varsayılan olarak devre dışı bırakılmakta olan önceki davranışa geri döner.

#### <a name="reason-for-change"></a>Değişiklik nedeni

ASP.NET Core 3,0 işlevselliği geliştirildi.

#### <a name="recommended-action"></a>Önerilen eylem

Tüm istemcilerin HTTPS kullanmasını istiyorsanız herhangi bir eylem gerekmez. Bazı istemcilerin HTTP kullanmasına izin vermek için aşağıdaki adımlardan birini uygulayın:

* `UseHttpsRedirection` ve `UseHsts` olan çağrıları projenizin `Startup.Configure` yönteminden kaldırın ve uygulamayı yeniden dağıtın.
* *Web. config* dosyanızda `ASPNETCORE_HTTPS_PORT` ortam değişkenini boş bir dizeye ayarlayın. Bu değişiklik, uygulamayı yeniden dağıtmaya gerek kalmadan doğrudan sunucuda meydana gelebilir. Örneğin:

    ```xml
    <aspNetCore processPath="dotnet" arguments=".\WebApplication3.dll" stdoutLogEnabled="false" stdoutLogFile="\\?\%home%\LogFiles\stdout" >
        <environmentVariables>
        <environmentVariable name="ASPNETCORE_HTTPS_PORT" value="" />
        </environmentVariables>
    </aspNetCore>
    ```

`UseHttpsRedirection` şu olmaya devam edebilir:

* `ASPNETCORE_HTTPS_PORT` ortam değişkenini uygun bağlantı noktası numarası olarak ayarlayarak ASP.NET Core 2. x içinde el ile etkinleştirilir (çoğu üretim senaryosunda 443).
* Boş bir dize değeriyle `ASPNETCORE_ANCM_HTTPS_PORT` tanımlayarak ASP.NET Core 3. x içinde devre dışı bırakıldı. Bu değer, yukarıdaki `ASPNETCORE_HTTPS_PORT` örnekle aynı biçimde ayarlanır.

ASP.NET Core 3.0.0 uygulamalarını çalıştıran makineler ASP.NET Core 3.1.0 Preview 3 ANCM 'yi yüklemeden önce ASP.NET Core 3.0.1 çalışma zamanını yüklemelidir. Bunun yapılması, `UseHttpsRedirection` ASP.NET Core 3,0 uygulamaları için beklendiği gibi çalışmaya devam etmesini sağlar.

Azure App Service ' de, genel doğası nedeniyle çalışma zamanından ayrı bir zamanlamaya göre dağıtılır. ANCM, ASP.NET Core 3.0.1 ve 3.1.0 dağıtıldıktan sonra bu değişikliklerle Azure 'a dağıtıldı.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)`

-->
