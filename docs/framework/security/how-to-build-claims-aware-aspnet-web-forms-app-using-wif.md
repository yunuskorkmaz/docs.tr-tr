---
title: "Nasıl yapılır: WIF kullanarak talep kullanan ASP.NET Web Forms uygulaması oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: efb264dd-f47b-49a9-85ee-9f45d4425765
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 70d503448946b60f1d6b63bf850d8d62fb63acc2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-build-claims-aware-aspnet-web-forms-application-using-wif"></a>Nasıl yapılır: WIF kullanarak talep kullanan ASP.NET Web Forms uygulaması oluşturma
## <a name="applies-to"></a>Uygulandığı öğe:  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® Web formları  
  
## <a name="summary"></a>Özet  
 Bu yöntem basit talep kullanan ASP.NET Web Forms uygulaması oluşturmak için ayrıntılı adım adım yordamlar verilmektedir. Ayrıca, federe kimlik doğrulaması başarılı uygulama için basit talep kullanan ASP.NET Web Forms uygulamayı test etme için yönergeler sağlar. Bu yöntem bir güvenlik belirteci hizmeti (STS) oluşturmak için ayrıntılı yönergeler sahip değil ve bir STS zaten yapılandırmış olduğunuz varsayılır.  
  
## <a name="contents"></a>İçindekiler  
  
-   Amaçlar  
  
-   Adımların Özeti  
  
-   1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma  
  
-   2. adım – ASP.NET Web Forms uygulaması talep tabanlı kimlik doğrulaması için yapılandırma  
  
-   3. Adım – Çözümünüzü Test Etme  
  
## <a name="objectives"></a>Amaçlar  
  
-   ASP.NET Web Forms uygulaması talep tabanlı kimlik doğrulaması için yapılandırma  
  
-   Başarılı talep kullanan ASP.NET Web Forms uygulamayı test etme  
  
## <a name="summary-of-steps"></a>Adımların Özeti  
  
-   1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma  
  
-   2. adım – ASP.NET Web Forms uygulaması federe kimlik doğrulaması için yapılandırma  
  
-   3. Adım – Çözümünüzü Test Etme  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma  
 Bu adımda, yeni bir ASP.NET Web Forms uygulaması oluşturacaksınız.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Basit bir ASP.NET uygulaması oluşturmak için  
  
1.  Visual Studio'yu başlatın ve tıklatın **dosya**, **yeni**ve ardından **proje**.  
  
2.  İçinde **yeni proje** penceresinde tıklatın **ASP.NET Web Forms uygulaması**.  
  
3.  İçinde **adı**, girin `TestApp` ve basın **Tamam**.  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-based-authentication"></a>2. adım – ASP.NET Web Forms uygulaması talep tabanlı kimlik doğrulaması için yapılandırma  
 Bu adımda yapılandırma girişlere ekleyeceksiniz *Web.config* talep kullanan ASP.NET Web Forms uygulamanızın yapılandırma dosyası.  
  
#### <a name="to-configure-aspnet-application-for-claims-based-authentication"></a>ASP.NET uygulama talep tabanlı kimlik doğrulaması için yapılandırmak için  
  
1.  Aşağıdaki yapılandırma bölümü girdileri eklemek *Web.config* yapılandırma dosyası hemen sonra  **\<configuration >** açılış öğe:  
  
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
  
4.  Ekleme bir  **\<system.webServer >** şirket dışı kimlik doğrulaması modülleri tanımlar öğesi. Unutmayın *PublicKeyToken* özniteliği aynı olmalıdır *PublicKeyToken* için öznitelik  **\<configSections >** daha önce eklenen girdileri:  
  
    ```xml  
    <system.webServer>  
      <modules>  
        <add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
        <add name="SessionAuthenticationModule" type="System.IdentityModel.Services.SessionAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
      </modules>  
    </system.webServer>  
    ```  
  
5.  Aşağıdaki Windows Identity Foundation, ASP.NET uygulamanızın URL ve bağlantı noktası numarası değerleri eşleştiğinden emin olun ve ilgili yapılandırma girdileri eklemek  **\<AudienceUri >** girişi **bölgesi**  özniteliği  **\<wsFederation >** öğesi ve **yanıt** özniteliği  **\<wsFederation >**öğesi. Ayrıca emin **veren** değer uygun güvenlik belirteci hizmeti (STS) URL'nizi.  
  
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
  
6.  Başvuru ekleme <xref:System.IdentityModel> derleme.  
  
7.  Hiçbir hata bulunmadığından emin olmak için çözüm derleyin.  
  
## <a name="step-3--test-your-solution"></a>3. Adım – Çözümünüzü Test Etme  
 Bu adımda ASP.NET Web Forms uygulamanızı talep tabanlı kimlik doğrulaması için yapılandırılmış test. Basit bir sınama gerçekleştirmek için güvenlik belirteci hizmeti (STS) tarafından verilen belirteç talep görüntüler kod ekleyeceksiniz.  
  
#### <a name="to-test-your-aspnet-web-form-application-for-claims-based-authentication"></a>Talep tabanlı kimlik doğrulaması için ASP.NET Web formu uygulamanızı test etmek için  
  
1.  Açık **Default.aspx** altında dosya **TestApp** proje ve varolan biçimlendirme aşağıdaki biçimlendirme ile değiştirin:  
  
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
  
2.  Kaydet **Default.aspx**ve kendi kod adlı dosyanın arkasındaki açın **Default.aspx.cs**.  
  
    > [!NOTE]
    >  **Default.aspx.cs** altındaki gizlenebilir **Default.aspx** Çözüm Gezgini'nde. Varsa **Default.aspx.cs** görünür durumda değilse genişletin **Default.aspx** yanında üçgen tıklayarak.  
  
3.  Varolan kodla **Page_Load** yöntemi **Default.aspx.cs** aşağıdaki kod ile:  
  
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
  
4.  Kaydet **Default.aspx.cs**ve çözümü oluşturun.  
  
5.  Tuşlarına basarak çözümü çalıştırın **F5** anahtarı.  
  
6.  İçin güvenlik belirteci hizmeti tarafından verilen belirteç talep görüntüler sayfa sunulacaktır.
