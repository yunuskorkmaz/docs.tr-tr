---
title: 'Nasıl yapılır: WIF kullanarak talep kullanan ASP.NET MVC Web uygulaması oluşturma'
ms.date: 03/30/2017
ms.assetid: 0efb76bc-9f7b-4afe-be1c-2a57c917010b
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 146724f31e1d09f09f94d102366539dc79ddfe02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399155"
---
# <a name="how-to-build-claims-aware-aspnet-mvc-web-application-using-wif"></a>Nasıl yapılır: WIF kullanarak talep kullanan ASP.NET MVC Web uygulaması oluşturma
## <a name="applies-to"></a>Uygulandığı öğe:  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® MVC  
  
## <a name="summary"></a>Özet  
 Bu yöntem, basit talep kullanan ASP.NET MVC web uygulaması oluşturmak için ayrıntılı adım adım yordamlar verilmektedir. Ayrıca basit talep kullanan ASP.NET MVC web uygulaması için talep tabanlı kimlik doğrulaması başarılı uyarlamasını test etme yönergeleri sağlar. Bu yöntem bir güvenlik belirteci hizmeti (STS) oluşturmak için ayrıntılı yönergeler sahip değil ve bir STS zaten yapılandırmış olduğunuz varsayılır.  
  
## <a name="contents"></a>İçindekiler  
  
-   Amaçlar  
  
-   Adımların Özeti  
  
-   1. adım – basit ASP.NET MVC uygulaması oluşturma  
  
-   2. adım – ASP.NET MVC uygulaması talep tabanlı kimlik doğrulaması için yapılandırma  
  
-   3. Adım – Çözümünüzü Test Etme  
  
-   İlgili öğeler  
  
## <a name="objectives"></a>Amaçlar  
  
-   ASP.NET MVC web uygulaması talep tabanlı kimlik doğrulaması için yapılandırma  
  
-   Başarılı talep kullanan ASP.NET MVC web uygulamasını test  
  
## <a name="summary-of-steps"></a>Adımların Özeti  
  
-   1. adım – basit ASP.NET MVC uygulaması oluşturma  
  
-   2. adım – ASP.NET MVC uygulaması talep tabanlı kimlik doğrulaması için yapılandırma  
  
-   3. Adım – Çözümünüzü Test Etme  
  
## <a name="step-1--create-simple-aspnet-mvc-application"></a>1. adım – basit ASP.NET MVC uygulaması oluşturma  
 Bu adımda, yeni bir ASP.NET MVC uygulaması oluşturacaksınız.  
  
#### <a name="to-create-simple-aspnet-mvc-application"></a>Basit bir ASP.NET MVC uygulaması oluşturmak için  
  
1.  Visual Studio'yu başlatın ve tıklatın **dosya**, **yeni**ve ardından **proje**.  
  
2.  İçinde **yeni proje** penceresinde tıklatın **ASP.NET MVC 3 Web uygulaması**.  
  
3.  İçinde **adı**, girin `TestApp` ve basın **Tamam**.  
  
4.  İçinde **yeni ASP.NET MVC 3 projesinin** iletişim kutusunda **Internet uygulama** kullanılabilir şablonlardan olun **görünüm altyapısı** ayarlanır **Razor**ve ardından **Tamam**.  
  
5.  Yeni proje açıldığında sağ **TestApp** proje **Çözüm Gezgini** seçip **özellikleri** seçeneği.  
  
6.  Projenin Özellikler sayfasında, tıklatın **Web** sekmesinde solda ve emin olun **kullanım yerel IIS Web sunucusu** seçeneği işaretlidir.  
  
## <a name="step-2--configure-aspnet-mvc-application-for-claims-based-authentication"></a>2. adım – ASP.NET MVC uygulaması talep tabanlı kimlik doğrulaması için yapılandırma  
 Bu adımda yapılandırma girişlere ekleyeceksiniz *Web.config* talep kullanan yapmak için ASP.NET MVC web uygulamanızın yapılandırma dosyası.  
  
#### <a name="to-configure-aspnet-mvc-application-for-claims-based-authentication"></a>ASP.NET MVC uygulaması talep tabanlı kimlik doğrulaması için yapılandırmak için  
  
1.  Aşağıdaki yapılandırma bölümüne tanımları eklemek *Web.config* yapılandırma dosyası. Bunlar Windows Identity Foundation tarafından gereken yapılandırma bölümlerinin tanımlar. Tanımları ekleme hemen sonra  **\<configuration >** açılış öğe:  
  
    ```xml  
    <configSections>  
        <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
        <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2.  Ekleme bir  **\<konumu >** uygulamanın Federasyon meta verilerine erişim sağlayan öğe:  
  
    ```xml  
    <location path="FederationMetadata">  
        <system.web>  
            <authorization>  
                <allow users="*" />  
            </authorization>  
        </system.web>  
    </location>  
    ```  
  
3.  İçinde aşağıdaki yapılandırma girdileri eklemek  **\<system.web >** kullanıcıları reddedecek şekilde öğeleri yerel kimlik doğrulamasını devre dışı ve kimlik doğrulamasını yönetmek WIF etkinleştirin.  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4.  Aşağıdaki Windows Identity Foundation, ASP.NET uygulamanızın URL ve bağlantı noktası numarası değerleri eşleştiğinden emin olun ve ilgili yapılandırma girdileri eklemek  **\<AudienceUri >** girişi **bölgesi**  özniteliği  **\<wsFederation >** öğesi ve **yanıt** özniteliği  **\<wsFederation >** öğesi. Ayrıca emin **veren** değer uygun güvenlik belirteci hizmeti (STS) URL'nizi.  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration>  
            <audienceUris>  
                <add value="http://localhost:28503/" />  
            </audienceUris>  
            <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
                <trustedIssuers>  
                    <add thumbprint="1234567890ABCDEFGHIJKLMNOPQRSTUVWXYZ1234" name="YourSTSName" />  
                </trustedIssuers>   
            </issuerNameRegistry>  
            <certificateValidation certificateValidationMode="None" />  
        </identityConfiguration>  
    </system.identityModel>  
    <system.identityModel.services>  
        <federationConfiguration>  
            <cookieHandler requireSsl="false" />  
            <wsFederation passiveRedirectEnabled="true" issuer="http://localhost:13922/wsFederationSTS/Issue" realm="http://localhost:28503/" reply="http://localhost:28503/" requireHttps="false" />  
        </federationConfiguration>  
    </system.identityModel.services>  
    ```  
  
5.  Başvuru ekleme <xref:System.IdentityModel> derleme.  
  
6.  Hataları emin olmak için çözüm derleyin.  
  
## <a name="step-3--test-your-solution"></a>3. Adım – Çözümünüzü Test Etme  
 Bu adımda talep tabanlı kimlik doğrulaması için yapılandırılmış ASP.NET MVC web uygulamanızı test. Temel test gerçekleştirmek için güvenlik belirteci hizmeti (STS) tarafından verilen belirteç talep görüntüler basit kod ekleyeceksiniz.  
  
#### <a name="to-test-your-aspnet-mvc-application-for-claims-based-authentication"></a>Talep tabanlı kimlik doğrulaması için ASP.NET MVC uygulamanızı test etmek için  
  
1.  İçinde **Çözüm Gezgini**, genişletin **denetleyicileri** klasörü ve açık *HomeController.cs* dosyayı düzenleyicide. Aşağıdaki kodu ekleyin **dizin** yöntemi:  
  
    ```csharp  
    public ActionResult Index()  
    {  
        ViewBag.ClaimsIdentity = Thread.CurrentPrincipal.Identity;  
  
        return View();  
    }  
    ```  
  
2.  İçinde **Çözüm Gezgini** genişletin **görünümleri** ve ardından **giriş** klasörleri ve açık *Index.cshtml* dosyayı düzenleyicide. İçeriğini silin ve aşağıdaki biçimlendirme ekleyin:  
  
    ```html  
    @{  
        ViewBag.Title = "Home Page";  
    }  
  
    <h2>Welcome: @ViewBag.ClaimsIdentity.Name</h2>  
    <h3>Values from Identity</h3>  
    <table>  
        <tr>  
            <th>  
                IsAuthenticated   
            </th>  
            <td>  
                @ViewBag.ClaimsIdentity.IsAuthenticated   
            </td>  
        </tr>  
        <tr>  
            <th>  
                Name   
            </th>          
            <td>  
                @ViewBag.ClaimsIdentity.Name  
            </td>          
        </tr>  
    </table>  
    <h3>Claims from ClaimsIdentity</h3>  
    <table>  
        <tr>  
            <th>  
                Claim Type  
            </th>  
            <th>  
                Claim Value  
            </th>  
            <th>  
                Value Type  
            </th>  
            <th>  
                Subject Name  
            </th>          
            <th>  
                Issuer Name  
            </th>          
        </tr>  
            @foreach (System.Security.Claims.Claim claim in ViewBag.ClaimsIdentity.Claims ) {  
        <tr>  
            <td>  
                @claim.Type  
            </td>  
            <td>  
                @claim.Value  
            </td>  
            <td>  
                @claim.ValueType  
            </td>  
            <td>  
                @claim.Subject.Name  
            </td>  
            <td>  
                @claim.Issuer  
            </td>  
        </tr>  
    }  
    </table>  
    ```  
  
3.  Tuşlarına basarak çözümü çalıştırın **F5** anahtarı.  
  
4.  İçin güvenlik belirteci hizmeti tarafından verilen belirteç talep görüntüler sayfa sunulacaktır.  
  
## <a name="related-items"></a>İlgili öğeler  
  
-   [Nasıl yapılır: WIF Kullanarak Talep Kullanan ASP.NET Web Forms Uygulaması Derleme](../../../docs/framework/security/how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)
