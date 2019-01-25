---
title: WSFederation kimlik doğrulama modülüne genel bakış
ms.date: 03/30/2017
ms.assetid: 02c4d5e8-f0a7-49ee-9cf5-3647578510ad
author: BrucePerlerMS
ms.openlocfilehash: cebdb0e69ae151afd9a1cc422cf48a201176313a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54703672"
---
# <a name="wsfederation-authentication-module-overview"></a>WSFederation kimlik doğrulama modülüne genel bakış
Windows Identity Foundation (WIF), ASP.NET uygulamalarında WS-Federated kimlik doğrulama Modülü (WS-FAM) aracılığıyla şirket dışı kimlik doğrulaması için destek içerir. Bu konu nasıl Federasyon kimlik doğrulaması çalışır ve nasıl kullanılacağını anlamanıza yardımcı olur.  
  
### <a name="overview-of-federated-authentication"></a>Federe kimlik doğrulamasına genel bakış  
 Bir güvenlik belirteci hizmeti (iki etki alanı arasında bir güven ilişkisi olduğunda başka bir güven etki alanındaki bir STS'ye kimlik doğrulama bilgilerini sağlamak için STS) bir güven etki alanında Federasyon kimlik doğrulaması sağlar. Buna örnek olarak aşağıdaki çizimde gösterilmektedir.  
  
 ![Federasyon kimlik doğrulama senaryosu](../../../docs/framework/security/media/federatedauthentication.gif "FederatedAuthentication")  
  
1.  Fabrikam güven etki alanındaki bir istemci bir bağlı olan taraf (RP) uygulaması Contoso güven etki alanındaki bir istek gönderir.  
  
2.  RP istemciyi Contoso güven etki alanındaki bir sts'ye yönlendirir. Bu STS istemci bilgisi yok.  
  
3.  Contoso STS istemci Contoso güven etki alanı ile bir güven ilişkisine sahip Fabrikam güven etki alanındaki bir sts'ye yönlendirir.  
  
4.  Fabrikam STS, istemcinin kimliğini doğrular ve Contoso STS'ye bir güvenlik belirteci verir.  
  
5.  Contoso STS Fabrikam belirtecini RP'ye tarafından kullanılabilir ve RP için gönderen kendi belirteci oluşturmak için kullanır.  
  
6.  RP istemcinin talep güvenlik belirteci ayıklar ve bir yetkilendirme kararı verir.  
  
### <a name="using-the-federated-authentication-module-with-aspnet"></a>ASP.NET ile Federasyon kimlik doğrulama modülünü kullanma  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> Federe kimlik doğrulaması eklemenize olanak sağlayan bir HTTP modülü (WS-FAM) olan bir [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] uygulama. Federe kimlik doğrulaması, iş mantığı yazmaya odaklanmasına olanak tanır ve STS tarafından işlenen kimlik doğrulama mantığı sağlar.  
  
 STS doğrulanmamış istekleri yönlendirilmesi gerektiğini belirtmek için WS FAM yapılandırırsınız. WIF iki yolla bir kullanıcının kimliğini sağlar:  
  
1.  Pasif yeniden yönlendirme: Kimliği doğrulanmamış bir kullanıcı, korunan bir kaynağa erişmeye ve yalnızca bunları bir STS'ye bir oturum açma sayfası gerek kalmadan yönlendirmek istiyorsanız, ardından aldığı doğru yaklaşım budur. STS kullanıcının kimliğini doğrular ve bu kullanıcı için uygun talepleri içeren bir güvenlik belirteci verir. Bu seçenek, HTTP modülleri işlem hattında eklenecek WS FAM gerektirir. WS-FAM kullanın ve bir STS ile federasyona eklemek için uygulamanızın yapılandırma dosyasını değiştirmek için kimlik ve erişim aracı Visual Studio 2012 için kullanabilirsiniz. Daha fazla bilgi için [kimlik ve erişim aracı Visual Studio 2012 için](../../../docs/framework/security/identity-and-access-tool-for-vs.md).  
  
2.  Çağırabilirsiniz <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SignIn%2A?displayProperty=nameWithType> yöntemi veya <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectToIdentityProvider%2A> RP uygulamanızın oturum açma sayfası için arka plan kod yöntemi.  
  
 Pasif yeniden yönlendirme tüm iletişimin (genellikle bir tarayıcı) istemciden yanıt/yeniden yönlendirme aracılığıyla gerçekleştirilir. WS-FAM burada izler kimliği doğrulanmamış için kullanıcı istekleri ve kullanıcıların yönlendirir, uygulamanızın HTTP ardışık düzenine eklemek, STS'ye belirtin.  
  
 WS-FAM işlevselliğini de özelleştirmenize olanak tanıyan çeşitli olayları da başlatır. bir [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] uygulama.  
  
### <a name="how-the-ws-fam-works"></a>WS-FAM nasıl çalışır?  
 WS-FAM uygulanan <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> sınıfı. Genellikle, WS-FAM HTTP ardışık düzen ekleyin, [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] RP uygulaması. Kimliği doğrulanmamış bir kullanıcı korunan bir kaynağa erişmeyi denediğinde, RP "401 yetkilendirme reddedildi" HTTP yanıtı döndürür. WS-FAM alması rotasyonunun yerine bu yanıtı yakalar ve ardından bu kullanıcının belirtilen STS'ye yönlendirir. STS WS-FAM yeniden kesen bir güvenlik belirteci verir. WS-FAM bir örneğini oluşturmak için bu belirteci kullanır <xref:System.Security.Claims.ClaimsPrincipal> kimliği doğrulanmış kullanıcı için sağlayan normal [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] çalışması için yetkilendirme mekanizmalarını.  
  
 HTTP durum bilgisiz olduğundan, kullanıcının başka bir korumalı kaynağa erişmeye çalışan her zaman tüm bu işlem yinelenen önlemek için bir yol ihtiyacımız var. Burada <xref:System.IdentityModel.Services.SessionAuthenticationModule> halinde sunulur. STS, kullanıcı için bir güvenlik belirteci verdiğinde <xref:System.IdentityModel.Services.SessionAuthenticationModule> aynı zamanda kullanıcı için bir oturum güvenlik belirteci oluşturur ve bir tanımlama bilgisinde koyar. Sonraki isteklerde <xref:System.IdentityModel.Services.SessionAuthenticationModule> bu tanımlama bilgisi durdurur ve kullanıcının yeniden oluşturmak için kullandığı <xref:System.Security.Claims.ClaimsPrincipal>.  
  
 Aşağıdaki diyagramda, pasif yeniden yönlendirme durumda bilgi genel akışı gösterilmektedir. İstek, STS'ye kimlik bilgileri olmadan oturum açma sayfası oluşturmak için aracılığıyla otomatik olarak yönlendirilir:  
  
 ![Oturum için zamanlama diyagramı&#45;pasif yeniden yönlendirme oturum](../../../docs/framework/security/media/signinusingpassiveredirect.gif "SignInUsingPassiveRedirect")  
  
 Aşağıdaki diyagramda, kullanıcı, STS'ye kimlik doğrulaması olduğunda ne olacağını üzerinde daha fazla ayrıntı gösterilmektedir ve kendi güvenlik belirteçlerini tarafından işlenen <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>:  
  
 ![Pasif yeniden yönlendirme ile belirteç işleme için zamanlama](../../../docs/framework/security/media/signinusingpassiveredirect-tokenprocessing.gif "SignInUsingPassiveRedirect_TokenProcessing")  
  
 Kullanıcının güvenlik belirteçleri tanımlama serileştirilmiş ve tarafından müdahale ne olur üzerinde daha fazla detay Aşağıdaki diyagramda gösterilmiştir <xref:System.IdentityModel.Services.SessionAuthenticationModule>:  
  
 ![Oturum açma gösteren SAM zamanlama diyagram&#45;denetimleri kullanarak](../../../docs/framework/security/media/signinusingconrols-sam.gif "SignInUsingConrols_SAM")  
  
### <a name="events"></a>Olaylar  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>, <xref:System.IdentityModel.Services.SessionAuthenticationModule>ve kendi üst sınıfı <xref:System.IdentityModel.Services.HttpModuleBase>, bir HTTP isteğinin işlenmesi çeşitli aşamalarında olayları tetikleyebilir. Bu olayları işleyebilir `global.asax` dosyası, [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] uygulama.  
  
-   ASP.NET altyapısının modülün çağırır <xref:System.IdentityModel.Services.HttpModuleBase.Init%2A> yöntemi modülü başlatılamadı.  
  
-   <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated?displayProperty=nameWithType> ASP.NET altyapısının çağırdığında olayı oluşturulur <xref:System.IdentityModel.Services.HttpModuleBase.Init%2A> yöntemi ilk kez bir türetilen uygulamanın modüllerinin <xref:System.IdentityModel.Services.HttpModuleBase>. Bu yöntem statik erişir <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> özelliğe, ki bu yapılandırma Web.config dosyasından yüklenmesine neden olur. Bu olay, yalnızca bu özellik erişilen ilk kez ortaya çıkar. <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> Yapılandırmadan başlatılır nesnesi üzerinden erişilebilir <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> özellik bir olay işleyicisi. Bu olay için modüllerin uygulanmadan önce yapılandırmasını değiştirmek için kullanabilirsiniz. Bu olay işleyicisi uygulama_başlatma yöntemi ekleyebilirsiniz:  
  
    ```  
    void Application_Start(object sender, EventArgs e)  
    {  
        FederatedAuthentication.FederationConfigurationCreated += new EventHandler<FederationConfigurationCreatedEventArgs>(FederatedAuthentication_FederationConfigurationCreated);  
    }  
    ```  
  
     Her modülü geçersiz kılmalar <xref:System.IdentityModel.Services.HttpModuleBase.InitializeModule%2A?displayProperty=nameWithType> ve <xref:System.IdentityModel.Services.HttpModuleBase.InitializePropertiesFromConfiguration%2A?displayProperty=nameWithType> soyut yöntemler. Bu yöntemlerin ilki olan modül ilgi ASP.NET ardışık düzen olayları için işleyiciler ekler. Çoğu durumda modülün varsayılan uygulama yeterli olacaktır. Bu yöntemlerin ikincisi modülün özelliklerinden başlatır, <xref:System.IdentityModel.Services.HttpModuleBase.FederationConfiguration%2A?displayProperty=nameWithType> özelliği. (Daha önce yüklenen yapılandırmasının bir kopyasını budur.) Öğesinden türetilen sınıflarda başlatma yapılandırmasından yeni özellikleri desteklemek istiyorsanız ikinci bu yöntemi geçersiz kılmanız gerekebilir <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> veya <xref:System.IdentityModel.Services.SessionAuthenticationModule>. Bu gibi durumlarda ek yapılandırma özelliklerini desteklemek için uygun yapılandırma nesnelerden türetilmesi gerekir; Örneğin, <xref:System.IdentityModel.Configuration.IdentityConfiguration>, <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration>, veya <xref:System.IdentityModel.Services.Configuration.FederationConfiguration>.  
  
-   WS-FAM başlatır <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SecurityTokenReceived> olay STS tarafından verilen bir güvenlik belirteci durdurur.  
  
-   WS-FAM başlatır <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SecurityTokenValidated> belirteci doğruladıktan sonra olay.  
  
-   <xref:System.IdentityModel.Services.SessionAuthenticationModule> Başlatır <xref:System.IdentityModel.Services.SessionAuthenticationModule.SessionSecurityTokenCreated> olay kullanıcı için bir oturum güvenlik belirteci oluşturur.  
  
-   <xref:System.IdentityModel.Services.SessionAuthenticationModule> Başlatır <xref:System.IdentityModel.Services.SessionAuthenticationModule.SessionSecurityTokenReceived> olay oturum güvenlik belirteci içeren bir tanımlama bilgisi ile sonraki istekleri durdurur.  
  
-   WS-FAM kullanıcı yayınlayanla yönlendirir. önce bilmemektedir <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider> olay. WS-Federasyon oturum açma isteği aracılığıyla kullanılabilir <xref:System.IdentityModel.Services.RedirectingToIdentityProviderEventArgs.SignInRequestMessage%2A> özelliği <xref:System.IdentityModel.Services.RedirectingToIdentityProviderEventArgs> olayda geçirildi. Bu yayınlayanla göndermeden önce istek değiştirmek isteyebilirsiniz.  
  
-   WS-FAM başlatır <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SignedIn> tanımlama bilgisi başarıyla yazılır ve kullanıcının oturum açtığı zaman olay.  
  
-   WS-FAM başlatır <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SigningOut> olay oturumu olarak oturumu başına bir kez kapatılıyor her kullanıcı için. Oturum istemci tarafında (örneğin, oturum tanımlama bilgisinin silerek) kapalıysa harekete Geçirilmemesi. SSO ortamında, IP-STS, çok imzalamak için her RP isteyebilir. Bu da bu olay ile oluşturacağı <xref:System.IdentityModel.Services.SigningOutEventArgs.IsIPInitiated%2A> kümesine `true`.  
  
> [!NOTE]
>  Kullanmamalısınız <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> özelliği tarafından gerçekleştirilen herhangi bir olay sırasında <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> veya <xref:System.IdentityModel.Services.SessionAuthenticationModule>. Bunun nedeni, <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> kimlik doğrulama işlemi sırasında tetiklenen olayları sırasında kimlik doğrulama işleminden sonra ayarlanır.  
  
### <a name="configuration-of-federated-authentication"></a>Federe kimlik doğrulamasının yapılandırması  
 WS-FAM ve VEDAT aracılığıyla yapılandırılan [ \<Federationconfiguration'a >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) öğesi. [ \<WsFederation >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation.md) alt öğesi yapılandırır, varsayılan değerleri olduğu gibi; WS-FAM özellikleri için <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.Issuer%2A> özelliği ve <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.Realm%2A> özelliği. (Bazı; WS-FAM olayları için işleyiciler sağlayarak, bu değerleri üzerinde istek başına değiştirilebilir gibi <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider>.) SAM tarafından kullanılan tanımlama bilgisi işleyicisi üzerinden yapılandırılan [ \<cookieHandler >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md) alt öğesi. WIF sağlar, uygulanan varsayılan bir tanımlama bilgisi işleyici <xref:System.IdentityModel.Services.ChunkedCookieHandler> aracılığıyla ayarlanan öbek boyutu olan sınıf [ \<chunkedCookieHandler >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/chunkedcookiehandler.md) öğesi. `<federationConfiguration>` Öğesi başvuruları bir <xref:System.IdentityModel.Configuration.IdentityConfiguration>, uygulamada kullanılan diğer WIF bileşenleri için yapılandırma sağlayan <xref:System.Security.Claims.ClaimsAuthenticationManager> ve <xref:System.Security.Claims.ClaimsAuthorizationManager>. Kimlik yapılandırması açıkça adlandırılmış belirterek başvurulabilir [ \<identityConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesinde `identityConfigurationName` özniteliği `<federationConfiguration>` öğesi. Kimlik yapılandırması açıkça başvurulmuyorsa, varsayılan kimlik yapılandırması kullanılır.  
  
 Aşağıdaki XML, bağlı olan taraf (RP) uygulaması, bir ASP.NET bir yapılandırılmasını gösterir. <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> Ve <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> yapılandırma bölümlerini altında eklenir `<configSections>` öğesi. WS-FAM ve SAM altında HTTP modüllerini eklenir `<system.webServer>` / `<modules>` öğesi. WIF bileşenleri altında yapılandırılmış son `<system.identityModel>` / `<identityConfiguration>` ve `<system.identityModel.services>` / `<federationConfiguration>` öğeleri. Bu yapılandırma varsayılan tanımlama bilgisi işleyicisi ve belirtilen bir tanımlama bilgisi işleyici türü değil olarak öbekli tanımlama bilgisi işleyici belirtir `<cookieHandler>` öğesi.  
  
> [!WARNING]
>  Aşağıdaki örnekte, hem `requireHttps` özniteliği `<wsFederation>` öğesi ve `requireSsl` özniteliği `<cookieHandler>` öğesidir `false`. Bu, olası bir güvenlik tehdidi sunar. Üretimde bu değerleri ayarlanmalıdır `true`.  
  
```xml  
<configuration>  
  <configSections>  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
  </configSections>  
  
  ...  
  
  <system.webServer>  
    <modules>  
      <add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
      <add name="SessionAuthenticationModule" type="System.IdentityModel.Services.SessionAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
    </modules>  
  </system.webServer>  
  
  <system.identityModel>  
    <identityConfiguration>  
      <audienceUris>  
        <add value="http://localhost:50969/" />  
      </audienceUris>  
      <certificateValidation certificateValidationMode="None" />  
      <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
        <trustedIssuers>  
          <add thumbprint="9B74CB2F320F7AAFC156E1252270B1DC01EF40D0" name="LocalSTS" />  
        </trustedIssuers>  
      </issuerNameRegistry>  
    </identityConfiguration>  
  </system.identityModel>  
  <system.identityModel.services>  
    <federationConfiguration>  
      <wsFederation passiveRedirectEnabled="true" issuer="http://localhost:15839/wsFederationSTS/Issue" realm="http://localhost:50969/" reply="http://localhost:50969/" requireHttps="false" />  
      <cookieHandler requireSsl="false" />  
    </federationConfiguration>  
  </system.identityModel.services>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.IdentityModel.Services.SessionAuthenticationModule>
- <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>
- [\<Federationconfiguration'a >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)
