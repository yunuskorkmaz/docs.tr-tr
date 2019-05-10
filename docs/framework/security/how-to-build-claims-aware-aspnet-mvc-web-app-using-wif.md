---
title: 'Nasıl yapılır: WIF Kullanarak Talep Kullanan ASP.NET MVC Web Uygulaması Derleme'
ms.date: 03/30/2017
ms.assetid: 0efb76bc-9f7b-4afe-be1c-2a57c917010b
author: BrucePerlerMS
ms.openlocfilehash: f2ac263d8869c770594283923a45c7c53c9df4cb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626124"
---
# <a name="how-to-build-claims-aware-aspnet-mvc-web-application-using-wif"></a>Nasıl yapılır: WIF Kullanarak Talep Kullanan ASP.NET MVC Web Uygulaması Derleme
## <a name="applies-to"></a>Uygulanan Öğe  
  
- Microsoft® Windows® Identity Foundation (WIF)  
  
- ASP.NET® MVC  
  
## <a name="summary"></a>Özet  
 Bu nasıl yapılır basit talep kullanan ASP.NET MVC web uygulaması oluşturmak için adım adım ayrıntılı yordamları sağlar. Ayrıca basit talep kullanan ASP.NET MVC web uygulaması için talep tabanlı kimlik doğrulaması başarılı uygulamasını test etme yönergeleri sağlar. Bu nasıl yapılır bir güvenlik belirteci hizmeti (STS) oluşturmaya yönelik ayrıntılı yönergeler yer almaz ve bir STS'ye zaten yapılandırmış olduğunuz varsayılır.  
  
## <a name="contents"></a>İçindekiler  
  
- Amaçlar  
  
- Adımların Özeti  
  
- 1. adım – basit bir ASP.NET MVC uygulaması oluşturma  
  
- 2. adım: ASP.NET MVC uygulaması talep tabanlı kimlik doğrulaması için yapılandırma  
  
- 3. Adım – Çözümünüzü Test Etme  
  
- İlgili öğeler  
  
## <a name="objectives"></a>Amaçlar  
  
- ASP.NET MVC web uygulaması talep tabanlı kimlik doğrulaması için yapılandırma  
  
- Test başarılı talep kullanan ASP.NET MVC web uygulaması  
  
## <a name="summary-of-steps"></a>Adımların Özeti  
  
- 1. adım – basit bir ASP.NET MVC uygulaması oluşturma  
  
- 2. adım: ASP.NET MVC uygulaması talep tabanlı kimlik doğrulaması için yapılandırma  
  
- 3. Adım – Çözümünüzü Test Etme  
  
## <a name="step-1--create-simple-aspnet-mvc-application"></a>1. adım – basit bir ASP.NET MVC uygulaması oluşturma  
 Bu adımda, yeni bir ASP.NET MVC uygulaması oluşturacaksınız.  
  
#### <a name="to-create-simple-aspnet-mvc-application"></a>Basit bir ASP.NET MVC uygulaması oluşturma  
  
1. Visual Studio'yu başlatın ve tıklayın **dosya**, **yeni**, ardından **proje**.  
  
2. İçinde **yeni proje** penceresinde tıklayın **ASP.NET MVC 3, Web uygulaması**.  
  
3. İçinde **adı**, girin `TestApp` basın **Tamam**.  
  
4. İçinde **yeni ASP.NET MVC 3 projesini** iletişim kutusunda **Internet uygulaması** kullanılabilen şablonlardan birini olun **görünüm altyapısı** ayarlanır **Razor**ve ardından **Tamam**.  
  
5. Yeni bir proje açıldığında, sağ **TestApp** projesi **Çözüm Gezgini** seçip **özellikleri** seçeneği.  
  
6. Proje özellikleri sayfasında tıklayın **Web** sekmesinde solda ve emin **kullanım yerel IIS Web sunucusunda** seçeneğinin işaretli.  
  
## <a name="step-2--configure-aspnet-mvc-application-for-claims-based-authentication"></a>2. adım: ASP.NET MVC uygulaması talep tabanlı kimlik doğrulaması için yapılandırma  
 Bu adımda, yapılandırma girdileri ekler *Web.config* talep kullanan yapmak için ASP.NET MVC web uygulamanızın yapılandırma dosyası.  
  
#### <a name="to-configure-aspnet-mvc-application-for-claims-based-authentication"></a>ASP.NET MVC uygulaması için talep tabanlı kimlik doğrulaması yapılandırmak için  
  
1. Aşağıdaki yapılandırma bölümüne tanımları ekleyin *Web.config* yapılandırma dosyası. Bunlar, Windows Identity Foundation'ı tarafından gereken yapılandırma bölümlerini tanımlar. Tanımları ekleme hemen sonra  **\<yapılandırma >** açılış öğesi:  
  
    ```xml  
    <configSections>  
        <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
        <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2. Ekleme bir  **\<konum >** uygulamanın Federasyon meta verilerine erişim sağlayan bir öğe:  
  
    ```xml  
    <location path="FederationMetadata">  
        <system.web>  
            <authorization>  
                <allow users="*" />  
            </authorization>  
        </system.web>  
    </location>  
    ```  
  
3. İçinde aşağıdaki yapılandırma girdileri eklemek  **\<system.web >** kullanıcıları engellemek için öğeleri yerel kimlik doğrulamasını devre dışı ve kimlik doğrulamasını yönetmek WIF etkinleştirme.  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4. Aşağıdaki Windows Identity Foundation, ASP.NET uygulamanızın URL'sini ve bağlantı noktası numarası değerlerin eşleştiğinden emin olun ve ilgili yapılandırma girdileri eklemek  **\<AudienceUri >** girişi **bölge**  özniteliği  **\<wsFederation >** öğesi ve **yanıt** özniteliği  **\<wsFederation >** öğesi. Ayrıca emin **veren** uygun güvenlik belirteci hizmeti (STS) URL'nizi değeri.  
  
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
  
5. Başvuru ekleme <xref:System.IdentityModel> derleme.  
  
6. Bir hata olmadığından emin olmak için çözümü derleyin.  
  
## <a name="step-3--test-your-solution"></a>3. Adım – Çözümünüzü Test Etme  
 Bu adımda, ASP.NET MVC web uygulamanızı beyana dayalı kimlik doğrulaması için yapılandırılmış test eder. Temel test gerçekleştirmek için güvenlik belirteci hizmeti (STS) tarafından verilen belirteçteki talepleri görüntüler basit kod ekleyeceksiniz.  
  
#### <a name="to-test-your-aspnet-mvc-application-for-claims-based-authentication"></a>Talep tabanlı kimlik doğrulaması için ASP.NET MVC uygulamanızı test etmek için  
  
1. İçinde **Çözüm Gezgini**, genişletme **denetleyicileri** klasörü ve açık *HomeController.cs* düzenleyicideki dosyada. Aşağıdaki kodu ekleyin **dizin** yöntemi:  
  
    ```csharp  
    public ActionResult Index()  
    {  
        ViewBag.ClaimsIdentity = Thread.CurrentPrincipal.Identity;  
  
        return View();  
    }  
    ```  
  
2. İçinde **Çözüm Gezgini** genişletin **görünümleri** ardından **giriş** klasörleri ve açık *Index.cshtml* düzenleyicideki dosyada. İçeriğini silin ve aşağıdaki işaretlemeyi ekleyin:  
  
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
  
3. Tuşlarına basarak çözümü çalıştırın **F5** anahtarı.  
  
4. İçin güvenlik belirteci hizmeti tarafından verilmiş belirteçteki talepleri gösteren sayfa ile sunulan.  
  
## <a name="related-items"></a>İlgili öğeler  
  
- [Nasıl yapılır: WIF kullanarak talep kullanan ASP.NET Web Forms uygulaması derleme](../../../docs/framework/security/how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)
