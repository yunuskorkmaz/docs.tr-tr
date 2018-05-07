---
title: WSFederation kimlik doğrulama Modülü'ne genel bakış
ms.date: 03/30/2017
ms.assetid: 02c4d5e8-f0a7-49ee-9cf5-3647578510ad
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: abfd211629c3c77c87cbefbc27c6b18ab6872977
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="wsfederation-authentication-module-overview"></a>WSFederation kimlik doğrulama Modülü'ne genel bakış
Windows Identity Foundation (WIF) WS-Federated kimlik doğrulama Modülü (WS-FAM) aracılığıyla ASP.NET uygulamalarında federe kimlik doğrulaması için destek içerir. Bu konu, nasıl federe kimlik doğrulaması çalışır ve nasıl kullanılacağını anlamanıza yardımcı olur.  
  
### <a name="overview-of-federated-authentication"></a>Federe kimlik doğrulamasına genel bakış  
 Bir güvenlik belirteci hizmeti (iki etki alanı arasında bir güven ilişkisi olduğunda başka bir güven etki alanındaki bir STS kimlik doğrulama bilgileri sağlamak için STS) bir güven etki alanındaki federe kimlik doğrulaması sağlar. Buna örnek olarak aşağıdaki çizimde gösterilmiştir.  
  
 ![Federasyon kimlik doğrulama senaryosu](../../../docs/framework/security/media/federatedauthentication.gif "FederatedAuthentication")  
  
1.  Fabrikam güven etki alanındaki bir istemci bir bağlı olan taraf (RP) uygulaması Contoso güven etki alanındaki bir isteği gönderir.  
  
2.  RP Contoso güven etki alanındaki bir STS yeniden yönlendirir. Bu STS istemci olanağıyla sahiptir.  
  
3.  Contoso STS ile Contoso güven etki alanı güven ilişkisi olan Fabrikam güven etki alanındaki bir STS yeniden yönlendirir.  
  
4.  Fabrikam STS istemcinin kimliğini doğrular ve Contoso STS bir güvenlik belirteci verir.  
  
5.  Contoso STS Fabrikam belirteci RP tarafından kullanılabilir ve RP gönderen kendi belirteç oluşturmak için kullanır.  
  
6.  RP güvenlik belirteci istemcinin talep ayıklar ve bir yetkilendirme kararı verir.  
  
### <a name="using-the-federated-authentication-module-with-aspnet"></a>ASP.NET ile federe kimlik doğrulama modülünü kullanma  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> Federe kimlik doğrulaması eklemenize olanak sağlayan bir HTTP modülü (WS-FAM) olan bir [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] uygulama. Federe kimlik doğrulama iş mantığı yazma odaklanmanıza olanak tanır ve STS tarafından işlenen kimlik doğrulama mantığı sağlar.  
  
 WS-STS doğrulanmamış istekler yönlendirilmesi belirtmek için FAM yapılandırın. WIF iki yolla kullanıcı kimlik doğrulaması sağlar:  
  
1.  Pasif yeniden yönlendirme: ne zaman kimliği doğrulanmamış bir kullanıcı korunan bir kaynağa erişmeyi dener ve yalnızca bunları bir STS bir oturum açma sayfası gerek kalmadan yeniden yönlendirmek istediğiniz sonra bu doğru bir yaklaşımdır. STS kullanıcının kimliğini doğrular ve bu kullanıcı için uygun talepleri içeren bir güvenlik belirteci verir. Bu seçenek HTTP modülleri ardışık düzeninde eklenecek WS FAM gerektirir. Uygulamanızın yapılandırma dosyasına WS-FAM kullanmak ve bir STS ile birleştirmek için değiştirmek için kimlik ve erişim aracı Visual Studio 2012 için kullanabilirsiniz. Daha fazla bilgi için bkz: [kimlik ve erişim aracı Visual Studio 2012 için](../../../docs/framework/security/identity-and-access-tool-for-vs.md).  
  
2.  Çağırabilirsiniz <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SignIn%2A?displayProperty=nameWithType> yöntemi veya <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectToIdentityProvider%2A> arka plan kodu yönteminden RP uygulamanızda oturum açma sayfası için.  
  
 Pasif yeniden yönlendirme tüm iletişimin (genellikle bir tarayıcı) istemciden yanıt/yeniden yönlendirme aracılığıyla gerçekleştirilir. WS-FAM burada izler kimliği doğrulanmamış için kullanıcı istekleri ve kullanıcıların yönlendirir, uygulamanızın HTTP ardışık düzenine eklemek için STS belirtin.  
  
 WS-FAM de işlevselliğini içinde özelleştirmenize olanak tanıyan çeşitli olayları başlatır bir [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] uygulama.  
  
### <a name="how-the-ws-fam-works"></a>WS-FAM nasıl çalışır?  
 WS-FAM uygulanan <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> sınıfı. Genellikle, WS-FAM HTTP ardışık düzenine eklemek, [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] RP uygulama. Kimliği doğrulanmamış bir kullanıcı korunan bir kaynağa erişmeyi denediğinde, RP "401 yetkilendirme reddedildi" HTTP yanıtı döndürür. WS-FAM alacak istemciye izin vermek yerine bu yanıt durdurur ve kullanıcı için belirtilen STS yönlendirir. STS WS-FAM yeniden karşılar bir güvenlik belirteci verir. WS-FAM bir örneğini oluşturmak için bu belirteci kullanır <xref:System.Security.Claims.ClaimsPrincipal> kimliği doğrulanmış kullanıcı için sağlayan normal [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] çalışması için yetkilendirme mekanizmaları.  
  
 HTTP durum bilgisiz olduğundan, bir kullanıcı başka bir korumalı kaynağa erişmeye çalışırsa her zaman bu sürecin tamamı kaçınmanızı şekilde ihtiyacımız var. Bu yerdir <xref:System.IdentityModel.Services.SessionAuthenticationModule> devreye girer. STS, kullanıcı için bir güvenlik belirteci verdiğinde <xref:System.IdentityModel.Services.SessionAuthenticationModule> de kullanıcı için bir oturum güvenlik belirteci oluşturur ve bir tanımlama bilgisinde yerleştirir. Sonraki isteklerde <xref:System.IdentityModel.Services.SessionAuthenticationModule> bu tanımlama bilgisi durdurur ve kullanıcının yeniden oluşturmak için kullandığı <xref:System.Security.Claims.ClaimsPrincipal>.  
  
 Aşağıdaki diyagramda pasif yeniden yönlendirme durumunda genel bilgi akışını gösterir. İstek, kimlik bilgileri olmadan oturum açma sayfasına kurmaya STS aracılığıyla otomatik olarak yönlendirilir:  
  
 ![Oturum için zamanlama diyagramı&#45;pasif yeniden yönlendirme oturum](../../../docs/framework/security/media/signinusingpassiveredirect.gif "SignInUsingPassiveRedirect")  
  
 Kullanıcı kimlik doğrulaması için STS ne olur hakkında daha fazla ayrıntı Aşağıdaki diyagramda gösterilmiştir ve kendi güvenlik belirteçlerini tarafından işlenen <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>:  
  
 ![Pasif yeniden yönlendirme ile belirteç işleme için zamanlama](../../../docs/framework/security/media/signinusingpassiveredirect-tokenprocessing.gif "SignInUsingPassiveRedirect_TokenProcessing")  
  
 Kullanıcının güvenlik belirteçleri tanımlama bilgisine ayrılır serileştirilmiş ve tarafından müdahale ne olur hakkında daha fazla ayrıntı Aşağıdaki diyagramda gösterilmiştir <xref:System.IdentityModel.Services.SessionAuthenticationModule>:  
  
 ![Oturum açma gösteren SAM zamanlama diyagramı&#45;denetimleri kullanarak](../../../docs/framework/security/media/signinusingconrols-sam.gif "SignInUsingConrols_SAM")  
  
### <a name="events"></a>Olaylar  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>, <xref:System.IdentityModel.Services.SessionAuthenticationModule>ve kendi üst sınıfı <xref:System.IdentityModel.Services.HttpModuleBase>, bir HTTP isteğinin işlenmesi çeşitli aşamalarında olayları Yükselt. Bu olayları işleyebilir `global.asax` dosyası, [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] uygulama.  
  
-   ASP.NET altyapısının modülün çağırır <xref:System.IdentityModel.Services.HttpModuleBase.Init%2A> yöntemi modülü başlatılamadı.  
  
-   <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated?displayProperty=nameWithType> Olayı ASP.NET altyapısının istediğinde <xref:System.IdentityModel.Services.HttpModuleBase.Init%2A> öğesinden türetilen uygulama modüllerinden birini ilk kez yöntemi <xref:System.IdentityModel.Services.HttpModuleBase>. Bu yöntem statik erişir <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> özelliği Web.config dosyasından yüklenmesi yapılandırma neden olur. Bu olay yalnızca bu özellik erişilen ilk kez tetiklenir. <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> Yapılandırmasından başlatılmamış nesne üzerinden erişilebilir <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> olay işleyicisi özelliği. Hiçbir modül uygulanmadan önce yapılandırmasını değiştirmek için bu olayı kullanın. Bu olay için bir işleyici Application_Start yönteminde ekleyebilirsiniz:  
  
    ```  
    void Application_Start(object sender, EventArgs e)  
    {  
        FederatedAuthentication.FederationConfigurationCreated += new EventHandler<FederationConfigurationCreatedEventArgs>(FederatedAuthentication_FederationConfigurationCreated);  
    }  
    ```  
  
     Her modül geçersiz kılmaları <xref:System.IdentityModel.Services.HttpModuleBase.InitializeModule%2A?displayProperty=nameWithType> ve <xref:System.IdentityModel.Services.HttpModuleBase.InitializePropertiesFromConfiguration%2A?displayProperty=nameWithType> soyut yöntemler. Bu yöntemlerin ilki modülüne ilgi ASP.NET ardışık düzen olayları için işleyiciler ekler. Çoğu durumda modülün varsayılan uygulaması yeterli olacaktır. Bu yöntemlerin ikincisi modülün özelliklerinden başlatır, <xref:System.IdentityModel.Services.HttpModuleBase.FederationConfiguration%2A?displayProperty=nameWithType> özelliği. (Daha önce yüklenen yapılandırmasının bir kopyasını budur.) Öğesinden türetilen sınıflarda yapılandırmasından yeni özellikleri başlatma desteklemek istiyorsanız bu ikinci yöntemini geçersiz kılmanız gerekebilir <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> veya <xref:System.IdentityModel.Services.SessionAuthenticationModule>. Bu gibi durumlarda eklenen yapılandırma özelliklerini desteklemek için uygun yapılandırma nesnelerden türetilmesi gerekir; Örneğin, <xref:System.IdentityModel.Configuration.IdentityConfiguration>, <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration>, veya <xref:System.IdentityModel.Services.Configuration.FederationConfiguration>.  
  
-   WS-FAM başlatır <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SecurityTokenReceived> olay STS tarafından verilen bir güvenlik belirteci durdurur.  
  
-   WS-FAM başlatır <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SecurityTokenValidated> belirteç doğruladı sonra olay.  
  
-   <xref:System.IdentityModel.Services.SessionAuthenticationModule> Başlatır <xref:System.IdentityModel.Services.SessionAuthenticationModule.SessionSecurityTokenCreated> olay kullanıcı için bir oturum güvenlik belirteci oluşturur.  
  
-   <xref:System.IdentityModel.Services.SessionAuthenticationModule> Başlatır <xref:System.IdentityModel.Services.SessionAuthenticationModule.SessionSecurityTokenReceived> olay oturum güvenlik belirteci içeren tanımlama bilgisi ile sonraki istekleri kesintiye uğratır.  
  
-   WS-FAM kullanıcı vereni yönlendiren önce başlatır <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider> olay. WS-Federasyon oturum açma isteği aracılığıyla kullanılabilir <xref:System.IdentityModel.Services.RedirectingToIdentityProviderEventArgs.SignInRequestMessage%2A> özelliği <xref:System.IdentityModel.Services.RedirectingToIdentityProviderEventArgs> olayda geçirildi. Bu şekilde veren göndermeden önce istek değiştirmeyi seçebilir.  
  
-   WS-FAM başlatır <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SignedIn> tanımlama bilgisi başarıyla yazılır ve kullanıcının oturum açtığı zaman olay.  
  
-   WS-FAM başlatır <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SigningOut> olay oturumu olarak oturumu başına bir kez kapalı her kullanıcı için. Oturumu istemci tarafında (örneğin, oturum tanımlama bilgisi silerek) kapalıysa yükseltilmiş değil. SSO ortamında IP STS, çok imzalamak için her RP isteyebilir. Bu aynı zamanda bu olay ile oluşturacağı <xref:System.IdentityModel.Services.SigningOutEventArgs.IsIPInitiated%2A> kümesine `true`.  
  
> [!NOTE]
>  Kullanılamaz <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> özelliği tarafından gerçekleştirilen herhangi bir olay sırasında <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> veya <xref:System.IdentityModel.Services.SessionAuthenticationModule>. Bunun nedeni, <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> olaylar kimlik doğrulama işlemi sırasında oluşturulur ancak kimlik doğrulama işleminden sonra ayarlanır.  
  
### <a name="configuration-of-federated-authentication"></a>Federe kimlik doğrulamasının yapılandırması  
 WS-FAM ve SAM aracılığıyla yapılandırılan [ \<Federationconfiguration'a >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) öğesi. [ \<WsFederation >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation.md) alt öğesi yapılandırır gibi; WS-FAM özellikler için varsayılan değerleri <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.Issuer%2A> özelliği ve <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.Realm%2A> özelliği. (WS-FAM olayları; bazıları için işleyiciler sağlayarak, bu değerleri bir istek başına temelinde değiştirilebilir Örneğin, <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider>.) SAM tarafından kullanılan tanımlama bilgisi işleyici ile yapılandırılmış [ \<cookieHandler >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md) alt öğesi. WIF sağlar uygulanan varsayılan tanımlama bilgisi işleyici <xref:System.IdentityModel.Services.ChunkedCookieHandler> aracılığıyla ayarlanabilir öbek boyutunu olabilir sınıfı [ \<chunkedCookieHandler >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/chunkedcookiehandler.md) öğesi. `<federationConfiguration>` Öğesi başvuruları bir <xref:System.IdentityModel.Configuration.IdentityConfiguration>, uygulamada kullanılan diğer WIF bileşenleri için yapılandırma sağlayan <xref:System.Security.Claims.ClaimsAuthenticationManager> ve <xref:System.Security.Claims.ClaimsAuthorizationManager>. Kimlik yapılandırması açıkça bir adlandırılmış belirterek başvurulabilir [ \<identityConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesinde `identityConfigurationName` özniteliği `<federationConfiguration>` öğesi. Kimlik yapılandırması açıkça başvurulmuyorsa, varsayılan kimlik yapılandırması kullanılır.  
  
 Aşağıdaki XML, bağlı olan taraf (RP) uygulama bir ASP.NET yapılandırmasını gösterir. <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> Ve <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> yapılandırma bölümlerinin altında eklenir `<configSections>` öğesi. WS-FAM ve SAM altında HTTP modülleri eklenir `<system.webServer>` / `<modules>` öğesi. WIF bileşenleri altında son olarak yapılandırılmış `<system.identityModel>` / `<identityConfiguration>` ve `<system.identityModel.services>` / `<federationConfiguration>` öğeleri. Bu yapılandırma parçalı tanımlama bilgileri işleyici, varsayılan tanımlama bilgisi işleyicisi ve belirtilen bir tanımlama bilgisi işleyici türü değil haliyle belirtir. `<cookieHandler>` öğesi.  
  
> [!WARNING]
>  Aşağıdaki örnekte, hem `requireHttps` özniteliği `<wsFederation>` öğesi ve `requireSsl` özniteliği `<cookieHandler>` öğesidir `false`. Bu, olası bir güvenlik tehdidi gösterir. Üretimde bu değerleri ayarlanmalıdır `true`.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IdentityModel.Services.SessionAuthenticationModule>  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>  
 [\<Federationconfiguration'a >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)
