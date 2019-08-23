---
title: WSFederation Kimlik Doğrulaması Modülüne Genel Bakış
ms.date: 03/30/2017
ms.assetid: 02c4d5e8-f0a7-49ee-9cf5-3647578510ad
author: BrucePerlerMS
ms.openlocfilehash: 0873e878fca3fe9723c23f78d647aa443f6d0152
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915513"
---
# <a name="wsfederation-authentication-module-overview"></a>WSFederation Kimlik Doğrulaması Modülüne Genel Bakış
Windows Identity Foundation (WıF), WS-Federasyon kimlik doğrulama modülü (WS-FAD) aracılığıyla ASP.NET uygulamalarında federal kimlik doğrulaması desteği içerir. Bu konu, federal kimlik doğrulamanın nasıl çalıştığını ve nasıl kullanılacağını anlamanıza yardımcı olur.  
  
### <a name="overview-of-federated-authentication"></a>Federal kimlik doğrulamasına genel bakış  
 Federe kimlik doğrulaması, iki etki alanı arasında bir güven ilişkisi olduğunda, bir güven etki alanındaki güvenlik belirteci hizmeti 'nin (STS) başka bir güven etki alanındaki STS 'ye kimlik doğrulaması bilgilerini sağlamasına izin verir. Aşağıdaki çizimde buna bir örnek gösterilmektedir:  
  
 ![Federal Kimlik doğrulama senaryosunu gösteren diyagram.](./media/wsfederation-authentication-module-overview/federated-authentication.gif)  
  
1. Fabrikam Trust etki alanındaki bir istemci, Contoso güven etki alanındaki bir bağlı olan taraf (RP) uygulamasına bir istek gönderir.  
  
2. RP, istemciyi Contoso güven etki alanındaki bir STS 'ye yönlendirir. Bu STS 'nin istemci bilgisi yok.  
  
3. Contoso STS, bu istemciyi, Contoso güven etki alanının bir güven ilişkisine sahip olduğu Fabrikam güven etki alanındaki bir STS 'ye yönlendirir.  
  
4. Fabrikam STS, istemcinin kimliğini doğrular ve Contoso STS 'ye bir güvenlik belirteci yayınlar.  
  
5. Contoso STS, RP tarafından kullanılabilecek kendi belirtecini oluşturmak için fabrikam belirtecini kullanır ve bunu RP 'ye gönderir.  
  
6. RP, istemcinin taleplerini güvenlik belirtecinden ayıklar ve yetkilendirme kararı vermez.  
  
### <a name="using-the-federated-authentication-module-with-aspnet"></a>ASP.NET ile federal kimlik doğrulama modülünü kullanma  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(WS-Fae), bir ASP.NET uygulamasına federe kimlik doğrulaması eklemenize olanak tanıyan bir HTTP modülüdür. Federal kimlik doğrulaması, kimlik doğrulama mantığının STS tarafından işlenmesini sağlar ve iş mantığı yazmaya odaklanmanızı sağlar.  
  
 WS-FAD 'yi, kimliği doğrulanmamış isteklerin yeniden yönlendirilmesi gereken STS 'yi belirtecek şekilde yapılandırırsınız. WıF, bir kullanıcının kimlik doğrulamasını iki şekilde yapmanızı sağlar:  
  
1. Pasif yeniden yönlendirme: Kimliği doğrulanmamış bir Kullanıcı, korumalı bir kaynağa erişmeye çalıştığında ve yalnızca bir oturum açma sayfası gerekmeden bunları bir STS 'ye yönlendirmek istediğinizde, bu doğru yaklaşımdır. STS kullanıcının kimliğini doğrular ve bu kullanıcı için uygun talepleri içeren bir güvenlik belirteci yayınlar. Bu seçenek, HTTP modülleri ardışık düzeninde WS-Fae eklenmesini gerektirir. Visual Studio 2012 için kimlik ve erişim aracı 'nı kullanarak, uygulamanızın yapılandırma dosyasını WS-FAD kullanacak şekilde değiştirebilir ve bir STS ile federasyona bağlayabilirsiniz. Daha fazla bilgi için bkz. [Visual Studio Için kimlik ve erişim aracı 2012](../../../docs/framework/security/identity-and-access-tool-for-vs.md).  
  
2. RP uygulamanızdaki bir oturum <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SignIn%2A?displayProperty=nameWithType> açma sayfası için <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectToIdentityProvider%2A> arka plan kodundaki yöntemi veya yöntemi çağırabilirsiniz.  
  
 Pasif yeniden yönlendirmeye yönelik tüm iletişimler istemciden yanıt/yeniden yönlendirme (genellikle bir tarayıcı) yoluyla gerçekleştirilir. WS-Fae 'yi uygulamanızın HTTP işlem hattına ekleyerek kimliği doğrulanmamış kullanıcı isteklerini izler ve belirttiğiniz STS 'ye Kullanıcı yeniden yönlendirir.  
  
 WS-FAM Ayrıca bir ASP.NET uygulamasında işlevlerini özelleştirmenizi sağlayan çeşitli olaylar oluşturur.  
  
### <a name="how-the-ws-fam-works"></a>WS-fab nasıl çalıştığı  
 WS-FAD, <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> sınıfında uygulanır. Genellikle, WS-Fae 'yi ASP.NET RP uygulamanızın HTTP işlem hattına eklersiniz. Kimliği doğrulanmamış bir kullanıcı korumalı bir kaynağa erişmeyi denediğinde, RP bir "401 yetkilendirme reddedildi" HTTP yanıtı döndürür. WS-FAD bu yanıtı, istemcinin almasına izin vermek yerine karşılar, ardından kullanıcıyı belirtilen STS 'ye yeniden yönlendirir. STS, WS-FAD 'nin yeniden aldığı bir güvenlik belirteci verir. WS-FAD, kimliği doğrulanmış kullanıcı <xref:System.Security.Claims.ClaimsPrincipal> için, normal .NET Framework yetkilendirme mekanizmalarının çalışmasını sağlayan bir örneğini oluşturmak için belirtecini kullanır.  
  
 HTTP durum bilgisiz olduğundan, Kullanıcı başka bir korumalı kaynağa erişmeyi her denediğinde bu işlemin tamamını tekrarlamadan kaçınmak için bir yol gerekir. Burada <xref:System.IdentityModel.Services.SessionAuthenticationModule> geldiği yerdir. STS Kullanıcı için bir güvenlik belirteci oluşturduğunda, <xref:System.IdentityModel.Services.SessionAuthenticationModule> Kullanıcı için bir oturum güvenlik belirteci de oluşturur ve bir tanımlama bilgisine koyar. Sonraki isteklerde <xref:System.IdentityModel.Services.SessionAuthenticationModule> , bu tanımlama bilgisini karşılar ve <xref:System.Security.Claims.ClaimsPrincipal>Kullanıcı tarafından yeniden oluşturmak için kullanır.  
  
 Aşağıdaki diyagramda, pasif yeniden yönlendirme kasasının genel bilgi akışı gösterilmektedir. İstek bir oturum açma sayfası olmadan kimlik bilgileri oluşturmak için STS aracılığıyla otomatik olarak yönlendirilir:  
  
 ![Pasif yeniden yönlendirme ile oturum açma gösteren diyagram.](./media/wsfederation-authentication-module-overview/sign-in-using-passive-redirect.gif)  
  
 Aşağıdaki diyagramda, Kullanıcı STS 'ye kimlik doğrulaması yapıldığında ne olacağı ve bunların güvenlik belirteçleri tarafından <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>işlendiği konusunda daha fazla ayrıntı gösterilmektedir:  
  
 ![Pasif yönlendirme ile belirteç Işleme zamanlaması](../../../docs/framework/security/media/signinusingpassiveredirect-tokenprocessing.gif "SignInUsingPassiveRedirect_TokenProcessing")  
  
 Aşağıdaki diyagramda, kullanıcının güvenlik belirteçleri tanımlama bilgilerine serileştirildiğinde ve tarafından yakalanarak <xref:System.IdentityModel.Services.SessionAuthenticationModule>ne olacağı hakkında daha fazla ayrıntı gösterilmektedir:  
  
 ![Denetimleri kullanarak oturum açma&#45;gösteren Sam zamanlama diyagramı](../../../docs/framework/security/media/signinusingconrols-sam.gif "SignInUsingConrols_SAM")  
  
### <a name="events"></a>Olaylar  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>, ve üst <xref:System.IdentityModel.Services.HttpModuleBase>sınıfları, bir http isteğinin işlenmesi için çeşitli aşamalarda olay yükseltir. <xref:System.IdentityModel.Services.SessionAuthenticationModule> Bu olayları `global.asax` ASP.net uygulamanızın dosyasında işleyebilirsiniz.  
  
- ASP.NET altyapısı modülü başlatmak için modülün <xref:System.IdentityModel.Services.HttpModuleBase.Init%2A> yöntemini çağırır.  
  
- Olay, ASP.NET altyapısı, uygulamanın sınıfından türetilen <xref:System.IdentityModel.Services.HttpModuleBase>modüllerden <xref:System.IdentityModel.Services.HttpModuleBase.Init%2A> birinin ilk kez çağırışında tetiklenir. <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated?displayProperty=nameWithType> Bu yöntem, yapılandırmanın Web <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> . config dosyasından yüklenmesine neden olan static özelliğine erişir. Bu olay yalnızca bu özelliğe ilk kez erişildiğinde oluşturulur. Yapılandırmadan başlatılan <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> nesneye bir olay işleyicisindeki özelliği aracılığıyla erişilebilir. <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> Bu olayı, herhangi bir modüle uygulanmadan önce yapılandırmayı değiştirmek için kullanabilirsiniz. Application_Start yönteminde bu olay için bir işleyici ekleyebilirsiniz:  
  
    ```  
    void Application_Start(object sender, EventArgs e)  
    {  
        FederatedAuthentication.FederationConfigurationCreated += new EventHandler<FederationConfigurationCreatedEventArgs>(FederatedAuthentication_FederationConfigurationCreated);  
    }  
    ```  
  
     Her modül <xref:System.IdentityModel.Services.HttpModuleBase.InitializeModule%2A?displayProperty=nameWithType> ve <xref:System.IdentityModel.Services.HttpModuleBase.InitializePropertiesFromConfiguration%2A?displayProperty=nameWithType> soyut yöntemleri geçersiz kılar. Bu yöntemlerin ilki, modülün ilgisini çeken ASP.NET işlem hattı olayları için işleyiciler ekler. Çoğu durumda, modülün varsayılan uygulama yeterli olacaktır. Bu yöntemlerin İkincisi, modülünün özelliklerini <xref:System.IdentityModel.Services.HttpModuleBase.FederationConfiguration%2A?displayProperty=nameWithType> özelliğinden başlatır. (Bu, daha önce yüklenen yapılandırmanın bir kopyasıdır.) <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> Veya<xref:System.IdentityModel.Services.SessionAuthenticationModule>' den türettiğiniz sınıflarda yapılandırmadan yeni özelliklerin başlatılmasını desteklemek istiyorsanız bu ikinci yöntemi geçersiz kılmanız gerekebilir. Bu gibi durumlarda, eklenen yapılandırma özelliklerini desteklemek için uygun yapılandırma nesnelerinden de türetmeniz gerekir; Örneğin,, veya <xref:System.IdentityModel.Configuration.IdentityConfiguration> <xref:System.IdentityModel.Services.Configuration.FederationConfiguration>' <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration>den.  
  
- WS-Fab, STS tarafından <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SecurityTokenReceived> verilen bir güvenlik belirtecini keserken olayı oluşturur.  
  
- WS-Fab, belirteci doğruladıktan <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SecurityTokenValidated> sonra olayı oluşturur.  
  
- , <xref:System.IdentityModel.Services.SessionAuthenticationModule>Kullanıcı için bir oturum güvenlik belirteci oluşturduğunda olayınıoluşturur.<xref:System.IdentityModel.Services.SessionAuthenticationModule.SessionSecurityTokenCreated>  
  
- , <xref:System.IdentityModel.Services.SessionAuthenticationModule> Oturum güvenlik <xref:System.IdentityModel.Services.SessionAuthenticationModule.SessionSecurityTokenReceived> belirtecini içeren tanımlama bilgisiyle sonraki istekleri algıladığında olayı başlatır.  
  
- WS-FAD, kullanıcıyı veren kullanıcıya yönlendirdikten sonra <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider> olayı başlatır. WS-Federation oturum açma isteği, olayın <xref:System.IdentityModel.Services.RedirectingToIdentityProviderEventArgs.SignInRequestMessage%2A> <xref:System.IdentityModel.Services.RedirectingToIdentityProviderEventArgs> geçirildiği özelliği aracılığıyla kullanılabilir. Sertifikayı verene göndermeden önce isteği değiştirmeyi tercih edebilirsiniz.  
  
- WS-Fab, tanımlama bilgisi <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SignedIn> başarıyla yazıldığında ve Kullanıcı oturum açınca olayı oluşturur.  
  
- WS-Fab, oturum her <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SigningOut> bir kullanıcı için kapatıldığından, her oturum için bir kez olay oluşturur. Oturum, istemci tarafında kapalıysa (örneğin, oturum tanımlama bilgisini silerek) oluşturulmaz. Bir SSO ortamında, IP STS, her bir RP 'yi da oturumu kapatmak için isteyebilir. Bu, olarak <xref:System.IdentityModel.Services.SigningOutEventArgs.IsIPInitiated%2A> `true`ayarlanmış olan bu olayı da yükseltir.  
  
> [!NOTE]
> Veya <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> tarafından oluşturulanherhangibirolaysırasındaözelliğinikullanmamalısınız.<xref:System.IdentityModel.Services.SessionAuthenticationModule> Bunun nedeni <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> , kimlik doğrulama işlemi sırasında olaylar oluşturulduğunda, kimlik doğrulama işleminden sonra ayarlanır.  
  
### <a name="configuration-of-federated-authentication"></a>Federal kimlik doğrulaması yapılandırması  
 WS-fak ve Sam, [ \<FederationConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) öğesi aracılığıyla yapılandırılır. <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.Issuer%2A> <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.Realm%2A> [ Wsfeder>altöğesi,WS-FADözellikleriiçinvarsayılan\<](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation.md) değerleri yapılandırır; Örneğin, özelliği ve özelliği. (Bu değerler, bazı WS-FAı olayları için işleyiciler sağlayarak istek başına temelinde değiştirilebilir; Örneğin, <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider>.) Sam tarafından kullanılan tanımlama bilgisi işleyicisi, tanımlayan [ \<ıehandler >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md) alt öğesi aracılığıyla yapılandırılır. WIF, bir <xref:System.IdentityModel.Services.ChunkedCookieHandler> sınıfta uygulanan, öbek boyutu [ \<parçalama >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/chunkedcookiehandler.md) öğesi aracılığıyla ayarlanmış bir varsayılan tanımlama bilgisi işleyicisi sağlar. Öğesi, <xref:System.IdentityModel.Configuration.IdentityConfiguration>uygulamada kullanılan ve<xref:System.Security.Claims.ClaimsAuthorizationManager>gibidiğer WIF bileşenleri için yapılandırma sağlayan bir öğesine başvurur. <xref:System.Security.Claims.ClaimsAuthenticationManager> `<federationConfiguration>` `identityConfigurationName` Öğe özniteliğinde [ \<](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) adlandırılmış bir IdentityConfiguration > öğesi belirtilerek kimlik yapılandırmasına açıkça başvurulabilir. `<federationConfiguration>` Kimlik yapılandırmasına açıkça başvurulmuyorsa, varsayılan kimlik yapılandırması kullanılacaktır.  
  
 Aşağıdaki XML, bir ASP.NET bağlı olan taraf (RP) uygulamasının yapılandırmasını gösterir. <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> Ve yapılandırma<xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection>bölümleriöğesialtınaeklenir `<configSections>` . Sam ve WS-FAD, `<system.webServer>` `<modules>` öğesinin altındaki / http modüllerine eklenir. Son olarak, `<system.identityModel>` WIF bileşenleri `<identityConfiguration>` ve / `<system.identityModel.services>` öğelerialtındayapılandırılır`<federationConfiguration>` . / Bu yapılandırma, varsayılan tanımlama bilgisi işleyicisidir ve `<cookieHandler>` öğesinde belirtilen bir tanımlama bilgisi işleyici türü olmadığından, öbekli tanımlama bilgisi işleyicisini belirtir.  
  
> [!WARNING]
>  Aşağıdaki örnekte `requireHttps` , hem `<wsFederation>` öğesinin `requireSsl` özniteliği hem de `<cookieHandler>` öğesi `false`özniteliği. Bu, olası bir güvenlik tehdidi sunar. Üretimde, bu değerlerin her ikisi de ayarlanmalıdır `true`.  
  
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
- [\<federationConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)
