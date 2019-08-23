---
title: 'Nasıl yapılır: WIF Kullanarak Talep Kullanan ASP.NET Web Forms Uygulaması Derleme'
ms.date: 03/30/2017
ms.assetid: efb264dd-f47b-49a9-85ee-9f45d4425765
author: BrucePerlerMS
ms.openlocfilehash: 82b0649a7324987581cc3c97570a0fc42ffdf6d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941291"
---
# <a name="how-to-build-claims-aware-aspnet-web-forms-application-using-wif"></a>Nasıl yapılır: WIF Kullanarak Talep Kullanan ASP.NET Web Forms Uygulaması Derleme
## <a name="applies-to"></a>Uygulanan Öğe  
  
- Microsoft® Windows® Identity Foundation (WIF)  
  
- ASP.NET® Web Forms  
  
## <a name="summary"></a>Özet  
 Bu nasıl yapılır, basit talep kullanan ASP.NET Web Forms uygulaması oluşturmaya yönelik ayrıntılı adım adım yordamlar sağlar. Ayrıca, Federasyon kimlik doğrulamasının başarılı bir şekilde uygulanması için basit talep kullanan ASP.NET Web Forms uygulamasının nasıl test edildiği hakkında yönergeler de sağlar. Bu nasıl yapılır, güvenlik belirteci hizmeti (STS) oluşturmaya yönelik ayrıntılı yönergeler içermez ve zaten bir STS yapılandırdığınızı varsayar.  
  
## <a name="contents"></a>İçindekiler  
  
- Amaçlar  
  
- Adımların Özeti  
  
- 1\. adım – basit bir ASP.NET Web Forms uygulaması oluşturma  
  
- 2\. adım – ASP.NET Web Forms uygulamasını talep tabanlı kimlik doğrulaması için yapılandırma  
  
- 3\. Adım – Çözümünüzü Test Etme  
  
## <a name="objectives"></a>Amaçlar  
  
- Talep tabanlı kimlik doğrulaması için ASP.NET Web Forms uygulamasını yapılandırma  
  
- Test başarılı talep kullanan ASP.NET Web Forms uygulaması  
  
## <a name="summary-of-steps"></a>Adımların Özeti  
  
- 1\. adım – basit ASP.NET Web Forms uygulaması oluşturma  
  
- 2\. adım – Federasyon kimlik doğrulaması için ASP.NET Web Forms uygulamasını yapılandırma  
  
- 3\. Adım – Çözümünüzü Test Etme  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>1\. adım – basit bir ASP.NET Web Forms uygulaması oluşturma  
 Bu adımda, yeni bir ASP.NET Web Forms uygulaması oluşturacaksınız.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Basit bir ASP.NET uygulaması oluşturmak için  
  
1. Visual Studio 'Yu başlatın ve **Dosya**, **Yeni**ve ardından **Proje**' ye tıklayın.  
  
2. **Yeni proje** penceresinde, **ASP.NET Web Forms uygulama**' ya tıklayın.  
  
3. **Ad**alanına girin `TestApp` ve **Tamam**' a basın.  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-based-authentication"></a>2\. adım – ASP.NET Web Forms uygulamasını talep tabanlı kimlik doğrulaması için yapılandırma  
 Bu adımda, ASP.NET Web Forms uygulamanızın *Web. config* yapılandırma dosyasına, talebe göre haberdar olmak için yapılandırma girdileri ekleyeceksiniz.  
  
#### <a name="to-configure-aspnet-application-for-claims-based-authentication"></a>Talep tabanlı kimlik doğrulaması için ASP.NET uygulamasını yapılandırmak için  
  
1. Yapılandırma > açma öğesinden hemen sonra **aşağıdaki yapılandırma bölümü girdilerini Web. config yapılandırma dosyasına ekleyin: \<**  
  
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
  
4. Federe kimlik doğrulaması için modülleri tanımlayan bir  **\<System. webserver >** öğesi ekleyin. *PublicKeyToken* özniteliğinin, daha önce eklenen  **\<configSections >** girdilerinin *PublicKeyToken* özniteliğiyle aynı olması gerektiğini unutmayın:  
  
    ```xml  
    <system.webServer>  
      <modules>  
        <add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
        <add name="SessionAuthenticationModule" type="System.IdentityModel.Services.SessionAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
      </modules>  
    </system.webServer>  
    ```  
  
5. Aşağıdaki Windows Identity Foundation ile ilgili yapılandırma girdilerini ekleyin ve ASP.net uygulamanızın URL 'si ile bağlantı noktası  **\<>** numarasının,  **\<** WSFederation > öğesi ve  **\<WSFederation >** öğesinin **Reply** özniteliği. Ayrıca, **verenin** değerinin güvenlik belirteci HIZMETI (STS) URL 'nize uygun olduğundan emin olun.  
  
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
  
6. <xref:System.IdentityModel> Derlemeye başvuru ekleyin.  
  
7. Bir hata olmadığından emin olmak için çözümü derleyin.  
  
## <a name="step-3--test-your-solution"></a>3\. Adım – Çözümünüzü Test Etme  
 Bu adımda, talep tabanlı kimlik doğrulaması için yapılandırılmış olan ASP.NET Web Forms uygulamanızı test edersiniz. Temel bir test gerçekleştirmek için, güvenlik belirteci hizmeti (STS) tarafından verilen belirteçte talepleri görüntüleyen bir kod ekleyeceksiniz.  
  
#### <a name="to-test-your-aspnet-web-form-application-for-claims-based-authentication"></a>Talep tabanlı kimlik doğrulaması için ASP.NET Web formu uygulamanızı test etmek için  
  
1. **TestApp** projesi altındaki **default. aspx** dosyasını açın ve var olan işaretlemesini aşağıdaki biçimlendirme ile değiştirin:  
  
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
  
2. **Default. aspx**' i kaydedin ve sonra kodu **default.aspx.cs**adlı dosyanın arkasında açın.  
  
    > [!NOTE]
    > **Default.aspx.cs** , Çözüm Gezgini içinde **default. aspx** altında gizlenebilir. **Default.aspx.cs** görünür değilse, bunun yanındaki üçgene tıklayarak **default. aspx** ' i genişletin.  
  
3. **Default.aspx.cs** öğesinin **Page_Load** yöntemindeki mevcut kodu şu kodla değiştirin:  
  
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
  
4. **Default.aspx.cs**kaydedin ve Çözümü derleyin.  
  
5. **F5** tuşuna basarak çözümü çalıştırın.  
  
6. Güvenlik belirteci hizmeti tarafından size verilen belirteçteki talepleri görüntüleyen sayfayla birlikte sunulmalısınız.
