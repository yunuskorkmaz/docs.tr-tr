---
title: 'Nasıl yapılır: Gelen Talepleri Dönüştürme'
ms.date: 03/30/2017
ms.assetid: 2831d514-d9d8-4200-9192-954bb6da1126
author: BrucePerlerMS
ms.openlocfilehash: ce99b97007bf7608856345d6da87cd9e422d2266
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041474"
---
# <a name="how-to-transform-incoming-claims"></a>Nasıl yapılır: Gelen Talepleri Dönüştürme

## <a name="applies-to"></a>Uygulanan Öğe

- Microsoft® Windows® Identity Foundation (WIF)

- ASP.NET® Web Forms

## <a name="summary"></a>Özet

Bu nasıl yapılır, basit bir talep kullanan ASP.NET Web Forms uygulaması oluşturmak ve gelen talepleri dönüştürmek için ayrıntılı adım adım yordamlar sağlar. Ayrıca, uygulama çalıştırıldığında dönüştürülen taleplerin sunulduğunu doğrulamak üzere uygulamayı test etmek için yönergeler sağlar.

## <a name="contents"></a>İçindekiler

- Amaçlar

- Genel Bakış

- Adımların Özeti

- 1\. adım – basit bir ASP.NET Web Forms uygulaması oluşturma

- 2\. Adım: özel bir ClaimsAuthenticationManager kullanarak talep dönüştürmeyi uygulama

- 3\. Adım – Çözümünüzü Test Etme

## <a name="objectives"></a>Amaçlar

- Talep tabanlı kimlik doğrulaması için bir ASP.NET Web Forms uygulaması yapılandırma

- Yönetici rolü talebi ekleyerek gelen talepleri dönüştürme

- Düzgün çalışıp çalışmadığını görmek için ASP.NET Web Forms uygulamasını test etme

## <a name="overview"></a>Genel Bakış

WIF, kullanıcıların bir bağlı <xref:System.Security.Claims.ClaimsAuthenticationManager> olan taraf (RP) uygulamasına sunulmadan önce talepleri değiştirmesine olanak tanıyan adlı bir sınıfı kullanıma sunar. , <xref:System.Security.Claims.ClaimsAuthenticationManager> Kimlik doğrulaması ve temel alınan uygulama kodu arasındaki kaygılara ayrılması yararlı olur. Aşağıdaki örnekte, RP tarafından gerekebilecek, gelen <xref:System.Security.Claims.ClaimsPrincipal> taleplere nasıl rol ekleyeceğiniz gösterilmektedir.

## <a name="summary-of-steps"></a>Adımların Özeti

- 1\. adım – basit bir ASP.NET Web Forms uygulaması oluşturma

- 2\. Adım: özel bir ClaimsAuthenticationManager kullanarak talep dönüştürmeyi uygulama

- 3\. Adım – Çözümünüzü Test Etme

## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>1\. adım – basit bir ASP.NET Web Forms uygulaması oluşturma

Bu adımda, yeni bir ASP.NET Web Forms uygulaması oluşturacaksınız.

#### <a name="to-create-a-simple-aspnet-application"></a>Basit bir ASP.NET uygulaması oluşturmak için

1. Visual Studio'yu yönetici olarak yükseltilmiş modda başlatın.

2. Visual Studio 'da **Dosya**' ya, **Yeni**' ye ve ardından **Proje**' ye tıklayın.

3. **Yeni proje** penceresinde, **ASP.NET Web Forms uygulama**' ya tıklayın.

4. **Ad**alanına girin `TestApp` ve **Tamam**' a basın.

5. **Çözüm Gezgini**altında **TestApp** projesine sağ tıklayın **ve ardından kimlik ve erişim**' i seçin.

6. **Kimlik ve erişim** penceresi görüntülenir. **Sağlayıcılar**bölümünde, **yerel geliştirme sts 'Si Ile uygulamanızı test et**' i seçin ve **Uygula**' ya tıklayın.

7. *Default. aspx* dosyasında, varolan biçimlendirmeyi aşağıdaki kodla değiştirin, ardından dosyayı kaydedin:

    ```aspx-csharp
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true"
        CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>

    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">
          <h3>Your Claims</h3>
        <p>
            <asp:GridView ID="ClaimsGridView" runat="server" CellPadding="3">
                <AlternatingRowStyle BackColor="White" />
                <HeaderStyle BackColor="#7AC0DA" ForeColor="White" />
            </asp:GridView>
        </p>
    </asp:Content>
    ```

8. *Default.aspx.cs*adlı arka plan kod dosyasını açın. Mevcut kodu aşağıdaki kodla değiştirin, ardından dosyayı kaydedin:

    ```csharp
    using System;
    using System.Web.UI;
    using System.Security.Claims;

    namespace TestApp
    {
        public partial class _Default : Page
        {
            protected void Page_Load(object sender, EventArgs e)
            {
                ClaimsPrincipal claimsPrincipal = Page.User as ClaimsPrincipal;
                this.ClaimsGridView.DataSource = claimsPrincipal.Claims;
                this.ClaimsGridView.DataBind();
            }
        }
    }
    ```

## <a name="step-2--implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a>2\. Adım: özel bir ClaimsAuthenticationManager kullanarak talep dönüştürmeyi uygulama

Bu adımda, gelen sorumluya bir yönetici rolü eklemek <xref:System.Security.Claims.ClaimsAuthenticationManager> için sınıfındaki varsayılan işlevselliği geçersiz kılacaksınız.

#### <a name="to-implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a>Özel bir ClaimsAuthenticationManager kullanarak talep dönüşümünü uygulamak için

1. Visual Studio 'da çözüme sağ tıklayın, **Ekle**' ye tıklayın ve ardından **Yeni proje**' ye tıklayın.

2. **Yeni Proje Ekle** penceresinde,  **C# görsel** şablonlar listesinden **sınıf kitaplığı** ' nı seçin, yazın `ClaimsTransformation`ve ardından **Tamam**' a basın. Yeni proje, çözüm klasörünüzde oluşturulur.

3. **Claimstrans,** proje kapsamındaki **Başvurular** ' a sağ tıklayın ve ardından **Başvuru Ekle**' ye tıklayın.

4. **Başvuru Yöneticisi** penceresinde **System. IdentityModel**' i seçin ve ardından **Tamam**' a tıklayın.

5. **Class1.cs**açın veya yoksa, **Claimstransders**' e sağ tıklayın, **Ekle**' ye tıklayın, sonra **sınıf..** . öğesine tıklayın.

6. Aşağıdaki using yönergelerini kod dosyasına ekleyin:

    ```csharp
    using System.Security.Claims;
    using System.Security.Principal;
    ```

7. Aşağıdaki sınıf ve yöntemi kod dosyasına ekleyin.

    > [!WARNING]
    > Aşağıdaki kod yalnızca tanıtım amaçlıdır. üretim kodunda amaçlanan izinlerinizi doğruladığınızdan emin olun.

    ```csharp
    public class ClaimsTransformationModule : ClaimsAuthenticationManager
    {
        public override ClaimsPrincipal Authenticate(string resourceName, ClaimsPrincipal incomingPrincipal)
        {
            if (incomingPrincipal != null && incomingPrincipal.Identity.IsAuthenticated == true)
            {
               ((ClaimsIdentity)incomingPrincipal.Identity).AddClaim(new Claim(ClaimTypes.Role, "Admin"));
            }

            return incomingPrincipal;
        }
    }
    ```

8. Dosyayı kaydedin ve **Claimstransoluþturup** projesini derleyin.

9. **TestApp** ASP.net projenizde, başvurular ' a sağ tıklayın ve ardından **Başvuru Ekle**' ye tıklayın.

10. **Başvuru Yöneticisi** penceresinde, sol menüden **çözüm** ' i seçin, doldurulan seçeneklerden **claimstranssize** ' yı seçin ve ardından **Tamam**' a tıklayın.

11. Kök **Web. config** dosyasında  **\<System. IdentityModel >** girdisine gidin. IdentityConfiguration > öğeleri içinde aşağıdaki satırı ekleyin ve dosyayı kaydedin:  **\<**

    ```xml
    <claimsAuthenticationManager type="ClaimsTransformation.ClaimsTransformationModule, ClaimsTransformation" />
    ```

## <a name="step-3--test-your-solution"></a>3\. Adım – Çözümünüzü Test Etme

Bu adımda, ASP.NET Web Forms uygulamanızı test edecek ve Kullanıcı form kimlik doğrulamasıyla oturum açtığında taleplerin sunulduğunu doğrulayacaksınız.

#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>Forms kimlik doğrulaması kullanarak ASP.NET Web Forms uygulamanızı talepler için test etme

1. Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın. *Default. aspx*ile sunulmalısınız.

2. *Default. aspx* sayfasında, hesap hakkındaki **veren**, **OriginalIssuer**, **Type**, **Value**ve **ValueType** talep bilgilerini içeren **talep** başlığının altında bir tablo görmeniz gerekir. Son satır aşağıdaki şekilde sunulmalıdır:

    ||||||
    |-|-|-|-|-|
    |YEREL YETKILI|YEREL YETKILI|`http://schemas.microsoft.com/ws/2008/06/identity/claims/role`|Yönetici|<https://www.w3.org/2001/XMLSchema#string>|
