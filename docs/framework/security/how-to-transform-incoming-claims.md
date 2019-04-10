---
title: 'Nasıl yapılır: Gelen Talepleri Dönüştürme'
ms.date: 03/30/2017
ms.assetid: 2831d514-d9d8-4200-9192-954bb6da1126
author: BrucePerlerMS
ms.openlocfilehash: f836356125f1462f302b7e9f45a841c869c9a690
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59344643"
---
# <a name="how-to-transform-incoming-claims"></a>Nasıl yapılır: Gelen Talepleri Dönüştürme
## <a name="applies-to"></a>Uygulanan Öğe  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® Web formları  
  
## <a name="summary"></a>Özet  
 Bu yöntem, basit bir talep kullanan ASP.NET Web Forms uygulaması oluşturma ve gelen talepleri dönüştürme için adım adım ayrıntılı yordamları sağlar. Ayrıca, uygulamayı çalıştırdığınızda dönüştürülmüş beyanların sunulduğunu doğrulamak için uygulamayı test etme için yönergeler sağlar.  
  
## <a name="contents"></a>İçindekiler  
  
-   Amaçlar  
  
-   Genel Bakış  
  
-   Adımların Özeti  
  
-   1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma  
  
-   Adım 2 – uygulama talepleri özel bir ClaimsAuthenticationManager kullanarak dönüştürme  
  
-   3. Adım – Çözümünüzü Test Etme  
  
## <a name="objectives"></a>Amaçlar  
  
-   Bir ASP.NET Web Forms uygulaması talep tabanlı kimlik doğrulaması için yapılandırma  
  
-   Bir yönetici rolü talep ekleyerek gelen talepleri dönüştürme  
  
-   Düzgün çalışıp çalışmadığını görmek için ASP.NET Web Forms uygulamayı test etme  
  
## <a name="overview"></a>Genel Bakış  
 WIF sunan adlı bir sınıf <xref:System.Security.Claims.ClaimsAuthenticationManager> kullanıcıların bir bağlı olan taraf (RP) uygulaması verildikleri önce talep değiştirmesine izin verir. <xref:System.Security.Claims.ClaimsAuthenticationManager> Kimlik doğrulama ve temel uygulama kodu arasındaki ayrımı için kullanışlıdır. Aşağıdaki örnekte, gelen talepleri bir role eklemek gösterilmiştir <xref:System.Security.Claims.ClaimsPrincipal> tarafından RP gerekebilir.  
  
## <a name="summary-of-steps"></a>Adımların Özeti  
  
-   1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma  
  
-   Adım 2 – uygulama talepleri özel bir ClaimsAuthenticationManager kullanarak dönüştürme  
  
-   3. Adım – Çözümünüzü Test Etme  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma  
 Bu adımda, yeni bir ASP.NET Web Forms uygulaması oluşturacaksınız.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Basit bir ASP.NET uygulaması oluşturmak için  
  
1. Visual Studio'yu yönetici olarak yükseltilmiş modda başlatın.  
  
2. Visual Studio'da **dosya**, tıklayın **yeni**ve ardından **proje**.  
  
3. İçinde **yeni proje** penceresinde tıklayın **ASP.NET Web Forms uygulaması**.  
  
4. İçinde **adı**, girin `TestApp` basın **Tamam**.  
  
5. Sağ **TestApp** altındaki proje **Çözüm Gezgini**, ardından **kimlik ve erişim**.  
  
6. **Kimlik ve erişim** penceresi görüntülenir. Altında **sağlayıcıları**seçin **uygulamanızı yerel geliştirme STS'si ile Test**, ardından **Uygula**.  
  
7. İçinde *Default.aspx* dosya, var olan bir biçimlendirme aşağıdakiyle değiştirin ve ardından dosyayı kaydedin:  
  
    ```  
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
  
8. Adlı arka plan kod dosyası açın *Default.aspx.cs*. Ardından dosyayı kaydedin, aşağıdaki varolan kodu değiştirin:  
  
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
  
## <a name="step-2--implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a>Adım 2 – uygulama talepleri özel bir ClaimsAuthenticationManager kullanarak dönüştürme  
 Bu adımda varsayılan işlevler geçersiz kılacak olan <xref:System.Security.Claims.ClaimsAuthenticationManager> gelen sorumlusuna bir yönetici rolü eklemek için sınıfı.  
  
#### <a name="to-implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a>Özel ClaimsAuthenticationManager kullanarak talep dönüştürme uygulamak için  
  
1. Visual Studio'da sağ tıklayın, çözümü tıklayın **Ekle**ve ardından **yeni proje**.  
  
2. İçinde **Yeni Proje Ekle** penceresinde **sınıf kitaplığı** gelen **Visual C#** şablonları listesinde, girin `ClaimsTransformation`ve tuşuna **Tamam**. Yeni proje, çözüm klasörünüzde oluşturulur.  
  
3. Sağ **başvuruları** altında **ClaimsTransformation** proje ve ardından **Başvuru Ekle**.  
  
4. İçinde **başvuru Yöneticisi** penceresinde **System.IdentityModel**ve ardından **Tamam**.  
  
5. Açık **Class1.cs**, veya yoksa, sağ **ClaimsTransformation**, tıklayın **Ekle**, ardından **sınıfı...**  
  
6. Aşağıdaki kod dosyasına using yönergeleri:  
  
    ```csharp  
    using System.Security.Claims;  
    using System.Security.Principal;  
    ```  
  
7. Aşağıdaki sınıf ve yöntem kod dosyasını ekleyin.  
  
    > [!WARNING]
    >  Aşağıdaki kod, yalnızca gösterim amaçlıdır; hedeflenen izinlerinizi üretim kodunda doğruladığınızdan emin olun.  
  
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
  
8. Dosyayı kaydedin ve yapı **ClaimsTransformation** proje.  
  
9. İçinde **TestApp** ASP.NET projesi başvuruları üzerinde sağ tıklayın ve ardından **Başvuru Ekle**.  
  
10. İçinde **başvuru Yöneticisi** penceresinde **çözüm** sol menüden **ClaimsTransformation** doldurulmuş seçenekleri ve ardından  **Tamam**.  
  
11. Kök **Web.config** gidin, dosya  **\<system.identityModel >** girişi. İçinde  **\<identityConfiguration >** öğeleri eklemek için aşağıdakileri satır ve dosyayı kaydedin:  
  
    ```xml  
    <claimsAuthenticationManager type="ClaimsTransformation.ClaimsTransformationModule, ClaimsTransformation" />  
    ```  
  
## <a name="step-3--test-your-solution"></a>3. Adım – Çözümünüzü Test Etme  
 Bu adımda ASP.NET Web Forms uygulamanızı test edin ve bir kullanıcı, Forms kimlik doğrulaması ile oturum açtığında beyanların sunulduğunu doğrulayın.  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>Form kimlik doğrulaması kullanarak talep için ASP.NET Web Forms uygulamanızı test etmek için  
  
1. Tuşuna **F5** oluşturun ve uygulamayı çalıştırın. İle sunulan *Default.aspx*.  
  
2. Üzerinde *Default.aspx* sayfasında, bir tablonun altına görmeniz **bilgisayarınızı talep** içeren başlık **veren**, **OriginalIssuer**, **Türü**, **değer**, ve **ValueType** talep, hesabınız hakkında bilgiler. Son satırı aşağıdaki şekilde sunulması:  
  
    ||||||  
    |-|-|-|-|-|  
    |YEREL YETKİLİSİ|YEREL YETKİLİSİ|`http://schemas.microsoft.com/ws/2008/06/identity/claims/role`|Yönetici|<https://www.w3.org/2001/XMLSchema#string>|
