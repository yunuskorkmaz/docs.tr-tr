---
title: 'Nasıl yapılır: WIF Kullanarak Talep Kullanan ASP.NET MVC Web Uygulaması Derleme'
ms.date: 03/30/2017
ms.assetid: 0efb76bc-9f7b-4afe-be1c-2a57c917010b
author: BrucePerlerMS
ms.openlocfilehash: 4d245288b04d8ed3d997bc5572b40c7f8a9334e5
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045441"
---
# <a name="how-to-build-claims-aware-aspnet-mvc-web-application-using-wif"></a>Nasıl yapılır: WIF Kullanarak Talep Kullanan ASP.NET MVC Web Uygulaması Derleme
## <a name="applies-to"></a>Uygulanan Öğe  
  
- Microsoft® Windows® Identity Foundation (WIF)  
  
- ASP.NET® MVC  
  
## <a name="summary"></a>Özet  
 Bu nasıl yapılır, basit talepler kullanan ASP.NET MVC web uygulaması oluşturmaya yönelik ayrıntılı adım adım yordamlar sağlar. Ayrıca, talep tabanlı kimlik doğrulamasının başarılı bir şekilde uygulanması için basit talep kullanan ASP.NET MVC web uygulamasını test etme hakkında yönergeler de sağlar. Bu nasıl yapılır, güvenlik belirteci hizmeti (STS) oluşturmaya yönelik ayrıntılı yönergeler içermez ve zaten bir STS yapılandırdığınızı varsayar.  
  
## <a name="contents"></a>İçindekiler  
  
- Amaçlar  
  
- Adımların Özeti  
  
- 1\. adım – basit ASP.NET MVC uygulaması oluşturma  
  
- 2\. adım – ASP.NET MVC uygulamasını talep tabanlı kimlik doğrulaması için yapılandırma  
  
- 3\. Adım – Çözümünüzü Test Etme  
  
- İlgili öğeler  
  
## <a name="objectives"></a>Amaçlar  
  
- Talep tabanlı kimlik doğrulaması için ASP.NET MVC web uygulamasını yapılandırma  
  
- Test başarılı talep kullanan ASP.NET MVC web uygulaması  
  
## <a name="summary-of-steps"></a>Adımların Özeti  
  
- 1\. adım – basit ASP.NET MVC uygulaması oluşturma  
  
- 2\. adım – ASP.NET MVC uygulamasını talep tabanlı kimlik doğrulaması için yapılandırma  
  
- 3\. Adım – Çözümünüzü Test Etme  
  
## <a name="step-1--create-simple-aspnet-mvc-application"></a>1\. adım – basit ASP.NET MVC uygulaması oluşturma  
 Bu adımda, yeni bir ASP.NET MVC uygulaması oluşturacaksınız.  
  
#### <a name="to-create-simple-aspnet-mvc-application"></a>Basit ASP.NET MVC uygulaması oluşturmak için  
  
1. Visual Studio 'Yu başlatın ve **Dosya**, **Yeni**ve ardından **Proje**' ye tıklayın.  
  
2. **Yeni proje** penceresinde, **ASP.NET MVC 3 Web uygulaması**' na tıklayın.  
  
3. **Ad**alanına girin `TestApp` ve **Tamam**' a basın.  
  
4. **Yeni ASP.NET MVC 3 proje** iletişim kutusunda, kullanılabilir şablonlardan **Internet uygulaması** ' nı seçin, **Görünüm altyapısının** **Razor**olarak ayarlandığından emin olun ve ardından **Tamam**' a tıklayın.  
  
5. Yeni proje açıldığında, **Çözüm Gezgini** ' de **TestApp** projesine sağ tıklayın ve **Özellikler** seçeneğini belirleyin.  
  
6. Projenin Özellikler sayfasında, sol taraftaki **Web** sekmesine tıklayın ve **yerel IIS Web sunucusu kullan** seçeneğinin işaretli olduğundan emin olun.  
  
## <a name="step-2--configure-aspnet-mvc-application-for-claims-based-authentication"></a>2\. adım – ASP.NET MVC uygulamasını talep tabanlı kimlik doğrulaması için yapılandırma  
 Bu adımda, ASP.NET MVC web uygulamanızın *Web. config* yapılandırma dosyasına, talebe göre haberdar olmak için yapılandırma girdileri ekleyeceksiniz.  
  
#### <a name="to-configure-aspnet-mvc-application-for-claims-based-authentication"></a>Talep tabanlı kimlik doğrulaması için ASP.NET MVC uygulamasını yapılandırmak için  
  
1. Aşağıdaki yapılandırma bölümü tanımlarını *Web. config* yapılandırma dosyasına ekleyin. Bu, Windows Identity Foundation için gereken yapılandırma bölümlerini tanımlar. Yapılandırma > açma öğesinden hemen sonra  **\<** tanımları ekleyin:  
  
    ```xml  
    <configSections>  
        <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
        <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2. Uygulamanın Federasyon meta verilerine erişim sağlayan bir  **\<konum >** öğesi ekleyin:  
  
    ```xml  
    <location path="FederationMetadata">  
        <system.web>  
            <authorization>  
                <allow users="*" />  
            </authorization>  
        </system.web>  
    </location>  
    ```  
  
3. Kullanıcıları reddetmek, yerel kimlik doğrulamasını devre dışı bırakmak ve kimlik doğrulamasını yönetmek için WIF 'yi etkinleştirmek için  **\<System. Web >** öğelerine aşağıdaki yapılandırma girdilerini ekleyin.  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4. Aşağıdaki Windows Identity Foundation ile ilgili yapılandırma girdilerini ekleyin ve ASP.net uygulamanızın URL 'si ile bağlantı noktası  **\<>** **numarasının,**  **\<** WSFederation > öğesi ve  **\<WSFederation >** öğesinin **Reply** özniteliği. Ayrıca, **verenin** değerinin güvenlik belirteci HIZMETI (STS) URL 'nize uygun olduğundan emin olun.  
  
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
  
5. <xref:System.IdentityModel> Derlemeye başvuru ekleyin.  
  
6. Hata olduğundan emin olmak için çözümü derleyin.  
  
## <a name="step-3--test-your-solution"></a>3\. Adım – Çözümünüzü Test Etme  
 Bu adımda, talep tabanlı kimlik doğrulaması için yapılandırılmış ASP.NET MVC web uygulamanızı test edersiniz. Temel test gerçekleştirmek için, güvenlik belirteci hizmeti (STS) tarafından verilen belirteçte talepleri görüntüleyen basit bir kod ekleyeceksiniz.  
  
#### <a name="to-test-your-aspnet-mvc-application-for-claims-based-authentication"></a>Talep tabanlı kimlik doğrulaması için ASP.NET MVC uygulamanızı test etmek için  
  
1. **Çözüm Gezgini**, **denetleyiciler** klasörünü genişletin ve *HomeController.cs* dosyasını düzenleyicide açın. Aşağıdaki kodu **Dizin** yöntemine ekleyin:  
  
    ```csharp  
    public ActionResult Index()  
    {  
        ViewBag.ClaimsIdentity = Thread.CurrentPrincipal.Identity;  
  
        return View();  
    }  
    ```  
  
2. **Çözüm Gezgini** , **Görünümler** ' i ve ardından **giriş** klasörleri ' ni genişletin ve ardından düzenleyicide *Index. cshtml* dosyasını açın. İçeriğini silin ve aşağıdaki biçimlendirmeyi ekleyin:  
  
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
  
3. **F5** tuşuna basarak çözümü çalıştırın.  
  
4. Güvenlik belirteci hizmeti tarafından size verilen belirteçteki talepleri görüntüleyen sayfayla birlikte sunulmalısınız.  
  
## <a name="related-items"></a>İlgili öğeler  
  
- [Nasıl yapılır: WıF kullanarak talep kullanan ASP.NET Web Forms uygulama oluşturma](how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)
