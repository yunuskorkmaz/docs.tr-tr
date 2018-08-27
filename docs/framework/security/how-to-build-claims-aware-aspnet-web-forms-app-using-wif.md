---
title: 'Nasıl yapılır: WIF kullanarak talep kullanan ASP.NET Web Forms uygulaması derleme'
ms.date: 03/30/2017
ms.assetid: efb264dd-f47b-49a9-85ee-9f45d4425765
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 764e7fba31a7fb3fc40ec85ab4d0fb6e18e57390
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42931778"
---
# <a name="how-to-build-claims-aware-aspnet-web-forms-application-using-wif"></a>Nasıl yapılır: WIF kullanarak talep kullanan ASP.NET Web Forms uygulaması derleme
## <a name="applies-to"></a>Uygulandığı öğe:  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® Web formları  
  
## <a name="summary"></a>Özet  
 Bu nasıl yapılır basit talep kullanan ASP.NET Web Forms uygulaması oluşturmak için adım adım ayrıntılı yordamları sağlar. Ayrıca, basit talep kullanan ASP.NET Web Forms uygulaması şirket dışı kimlik doğrulaması başarılı uygulaması için test etme için yönergeler sağlar. Bu nasıl yapılır bir güvenlik belirteci hizmeti (STS) oluşturmaya yönelik ayrıntılı yönergeler yer almaz ve bir STS'ye zaten yapılandırmış olduğunuz varsayılır.  
  
## <a name="contents"></a>İçindekiler  
  
-   Amaçlar  
  
-   Adımların Özeti  
  
-   1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma  
  
-   2. adım: ASP.NET Web Forms uygulaması talep tabanlı kimlik doğrulaması için yapılandırma  
  
-   3. Adım – Çözümünüzü Test Etme  
  
## <a name="objectives"></a>Amaçlar  
  
-   ASP.NET Web Forms uygulaması talep tabanlı kimlik doğrulaması için yapılandırma  
  
-   Test başarılı talep kullanan ASP.NET Web Forms uygulaması  
  
## <a name="summary-of-steps"></a>Adımların Özeti  
  
-   1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma  
  
-   2. adım: ASP.NET Web Forms uygulaması şirket dışı kimlik doğrulaması yapılandırma  
  
-   3. Adım – Çözümünüzü Test Etme  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma  
 Bu adımda, yeni bir ASP.NET Web Forms uygulaması oluşturacaksınız.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Basit bir ASP.NET uygulaması oluşturmak için  
  
1.  Visual Studio'yu başlatın ve tıklayın **dosya**, **yeni**, ardından **proje**.  
  
2.  İçinde **yeni proje** penceresinde tıklayın **ASP.NET Web Forms uygulaması**.  
  
3.  İçinde **adı**, girin `TestApp` basın **Tamam**.  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-based-authentication"></a>2. adım: ASP.NET Web Forms uygulaması talep tabanlı kimlik doğrulaması için yapılandırma  
 Bu adımda, yapılandırma girdileri ekler *Web.config* talep kullanan ASP.NET Web Forms uygulamanızın yapılandırma dosyası.  
  
#### <a name="to-configure-aspnet-application-for-claims-based-authentication"></a>ASP.NET uygulamanızı beyana dayalı kimlik doğrulaması için yapılandırmak için  
  
1.  Aşağıdaki yapılandırma bölümü girdileri ekleme *Web.config* yapılandırma dosyası hemen sonra  **\<yapılandırma >** açılış öğesi:  
  
    ```xml  
    <configSections>  
      <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
      <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2.  Ekleme bir  **\<konum >** uygulamanın Federasyon meta verilerine erişim sağlayan bir öğe:  
  
    ```xml  
    <location path="FederationMetadata">  
      <system.web>  
        <authorization>  
          <allow users="*" />  
        </authorization>  
      </system.web>  
    </location>  
    ```  
  
3.  İçinde aşağıdaki yapılandırma girdileri eklemek  **\<system.web >** kullanıcıları engellemek için öğeleri yerel kimlik doğrulamasını devre dışı ve kimlik doğrulamasını yönetmek WIF etkinleştirme.  
  
    ```xml  
    <authorization>  
      <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4.  Ekleme bir  **\<system.webServer >** şirket dışı kimlik doğrulaması modülleri tanımlayan öğe. Unutmayın *PublicKeyToken* özniteliği aynı olmalıdır *PublicKeyToken* özniteliğini  **\<configSections >** daha önce eklediğiniz girişleri:  
  
    ```xml  
    <system.webServer>  
      <modules>  
        <add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
        <add name="SessionAuthenticationModule" type="System.IdentityModel.Services.SessionAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
      </modules>  
    </system.webServer>  
    ```  
  
5.  Aşağıdaki Windows Identity Foundation, ASP.NET uygulamanızın URL'sini ve bağlantı noktası numarası değerlerin eşleştiğinden emin olun ve ilgili yapılandırma girdileri eklemek  **\<AudienceUri >** girişi **bölge**  özniteliği  **\<wsFederation >** öğesi ve **yanıt** özniteliği  **\<wsFederation >** öğesi. Ayrıca emin **veren** uygun güvenlik belirteci hizmeti (STS) URL'nizi değeri.  
  
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
            <cookieHandler requireSsl="true" />  
            <wsFederation passiveRedirectEnabled="true" issuer="http://localhost:13922/wsFederationSTS/Issue" realm="http://localhost:28503/" reply="http://localhost:28503/" requireHttps="true" />  
        </federationConfiguration>  
    </system.identityModel.services>  
    ```  
  
6.  Başvuru ekleme <xref:System.IdentityModel> derleme.  
  
7.  Hiçbir hata olmadığından emin olmak için çözümü derleyin.  
  
## <a name="step-3--test-your-solution"></a>3. Adım – Çözümünüzü Test Etme  
 Bu adımda, ASP.NET Web Forms uygulaması talep tabanlı kimlik doğrulaması için yapılandırılmış test eder. Temel bir test gerçekleştirmek için güvenlik belirteci hizmeti (STS) tarafından verilen belirteçteki talepleri görüntüler kod ekleyeceksiniz.  
  
#### <a name="to-test-your-aspnet-web-form-application-for-claims-based-authentication"></a>Talep tabanlı kimlik doğrulaması için ASP.NET Web formu uygulamanızı test etmek için  
  
1.  Açık **Default.aspx** altında dosya **TestApp** proje ve onun varolan biçimlendirmesini aşağıdaki biçimlendirme değiştirin:  
  
    ```  
    %@ Page Language="C#" AutoEventWireup="true" CodeFile="Default.aspx.cs" Inherits="_Default" %>  
  
    <!DOCTYPE html>  
  
    <html>  
    <head id="Head1" runat="server">  
        <title></title>  
    </head>  
    <body>  
        <h1><asp:label ID="signedIn" runat="server" /></h1>  
        <asp:label ID="claimType" runat="server" />  
        <asp:label ID="claimValue" runat="server" />  
        <asp:label ID="claimValueType" runat="server" />  
        <asp:label ID="claimSubjectName" runat="server" />  
        <asp:label ID="claimIssuer" runat="server" />  
    </body>  
    </html>  
    ```  
  
2.  Kaydet **Default.aspx**ve ardından adlı dosyanın arkasındaki kodunu açın **Default.aspx.cs**.  
  
    > [!NOTE]
    >  **Default.aspx.cs** altındaki gizlenebilir **Default.aspx** Çözüm Gezgini'nde. Varsa **Default.aspx.cs** görünür durumda değilse genişletin **Default.aspx** yanında üçgeni tıklayarak.  
  
3.  Varolan kodda değiştirin **Page_Load** yöntemi **Default.aspx.cs** aşağıdaki kod ile:  
  
    ```csharp  
    using System;  
    using System.IdentityModel;  
    using System.Security.Claims;  
    using System.Threading;  
    using System.Web.UI;  
  
    namespace TestApp  
    {  
        public partial class _Default : System.Web.UI.Page  
        {  
            protected void Page_Load(object sender, EventArgs e)  
            {  
                ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;  
  
                if (claimsPrincipal != null)  
                {  
                    signedIn.Text = "You are signed in.";  
  
                    foreach (Claim claim in claimsPrincipal.Claims)  
                    {  
                        claimType.Text = claim.Type;  
                        claimValue.Text = claim.Value;  
                        claimValueType.Text = claim.ValueType;  
                        claimSubjectName.Text = claim.Subject.Name;  
                        claimIssuer.Text = claim.Issuer;  
                    }  
                }  
                else  
                {  
                    signedIn.Text = "You are not signed in.";  
                }  
            }  
        }  
    }  
    ```  
  
4.  Kaydet **Default.aspx.cs**ve Çözümü derleyin.  
  
5.  Tuşlarına basarak çözümü çalıştırın **F5** anahtarı.  
  
6.  İçin güvenlik belirteci hizmeti tarafından verilmiş belirteçteki talepleri gösteren sayfa ile sunulan.
