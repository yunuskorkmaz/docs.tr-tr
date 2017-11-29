---
title: "Nasıl yapılır: Gelen talep dönüştürme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2831d514-d9d8-4200-9192-954bb6da1126
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: bcf0e640e6b6b45ddb87070c7d6df2fa6dadc834
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-transform-incoming-claims"></a>Nasıl yapılır: Gelen talep dönüştürme
## <a name="applies-to"></a>Uygulandığı öğe:  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® Web formları  
  
## <a name="summary"></a>Özet  
 Bu yöntem basit bir talep kullanan ASP.NET Web Forms uygulaması oluşturma ve gelen talepleri dönüştürmek için ayrıntılı adım adım yordamlar verilmektedir. Ayrıca, uygulamayı çalıştırdığınızda, dönüştürülmüş talep sunulduğundan emin doğrulamak için uygulamayı test etme için yönergeler sağlar.  
  
## <a name="contents"></a>İçindekiler  
  
-   Amaçlar  
  
-   Genel Bakış  
  
-   Adımların Özeti  
  
-   1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma  
  
-   Adım 2 – uygulama talep özel ClaimsAuthenticationManager kullanarak dönüşümleri  
  
-   3. Adım – Çözümünüzü Test Etme  
  
## <a name="objectives"></a>Amaçlar  
  
-   Bir ASP.NET Web Forms uygulaması talep tabanlı kimlik doğrulaması için yapılandırma  
  
-   Bir yönetici rolü talep ekleyerek gelen talep dönüştürme  
  
-   Düzgün çalışıp çalışmadığını görmek için ASP.NET Web Forms uygulamayı test etme  
  
## <a name="overview"></a>Genel Bakış  
 WIF sunan adlı bir sınıf <xref:System.Security.Claims.ClaimsAuthenticationManager> bir bağlı olan taraf (RP) uygulamaya verildikleri önce talep değiştirmek kullanıcıların sağlar. <xref:System.Security.Claims.ClaimsAuthenticationManager> Kimlik doğrulaması ve temel uygulama kodu arasında sorunları ayrılması için kullanışlıdır. Aşağıdaki örnek, gelen talepleri bir rolü eklemek gösterilmiştir <xref:System.Security.Claims.ClaimsPrincipal> , gereken tarafından RP.  
  
## <a name="summary-of-steps"></a>Adımların Özeti  
  
-   1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma  
  
-   Adım 2 – uygulama talep özel ClaimsAuthenticationManager kullanarak dönüşümleri  
  
-   3. Adım – Çözümünüzü Test Etme  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma  
 Bu adımda, yeni bir ASP.NET Web Forms uygulaması oluşturacaksınız.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Basit bir ASP.NET uygulaması oluşturmak için  
  
1.  Visual Studio'yu yönetici olarak yükseltilmiş modda başlatın.  
  
2.  Visual Studio'da sırasıyla **dosya**, tıklatın **yeni**ve ardından **proje**.  
  
3.  İçinde **yeni proje** penceresinde tıklatın **ASP.NET Web Forms uygulaması**.  
  
4.  İçinde **adı**, girin `TestApp` ve basın **Tamam**.  
  
5.  Sağ **TestApp** altında proje **Çözüm Gezgini**seçeneğini belirleyip **kimlik ve erişim**.  
  
6.  **Kimlik ve erişim** penceresi görüntülenir. Altında **sağlayıcıları**seçin **yerel geliştirme STS ile uygulamanızı Test**, ardından **Uygula**.  
  
7.  İçinde *Default.aspx* dosya, varolan biçimlendirme şununla değiştirin ve ardından dosyayı kaydedin:  
  
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
  
8.  Adlı arka plan kodu dosyasını açın *Default.aspx.cs*. Ardından dosyayı kaydedin aşağıdaki var olan kodu değiştirin:  
  
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
  
## <a name="step-2--implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a>Adım 2 – uygulama talep özel ClaimsAuthenticationManager kullanarak dönüşümleri  
 Bu adımda varsayılan işlevleri geçersiz kılar <xref:System.Security.Claims.ClaimsAuthenticationManager> gelen asıl bir yönetici rolü eklemek için sınıfı.  
  
#### <a name="to-implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a>Talep dönüştürme özel ClaimsAuthenticationManager kullanarak uygulamak için  
  
1.  Visual Studio'da sağ çözüm üzerinde tıklatın **Ekle**ve ardından **yeni proje**.  
  
2.  İçinde **Yeni Proje Ekle** penceresinde, seçin **sınıf kitaplığı** gelen **Visual C#** şablonları listesinde, girin `ClaimsTransformation`ve tuşuna basarak **Tamam**. Yeni proje, çözüm klasörünüzde oluşturulur.  
  
3.  Sağ **başvuruları** altında **ClaimsTransformation** proje ve ardından **Başvuru Ekle**.  
  
4.  İçinde **başvuru Yöneticisi** penceresinde, seçin **System.IdentityModel**ve ardından **Tamam**.  
  
5.  Açık **Class1.cs**, veya yoksa, sağ **ClaimsTransformation**, tıklatın **Ekle**, ardından **sınıfı...**  
  
6.  Aşağıdaki kod dosyasına yönergeleri kullanarak:  
  
    ```csharp  
    using System.Security.Claims;  
    using System.Security.Principal;  
    ```  
  
7.  Aşağıdaki sınıf ve yöntemi kod dosyasına ekleyin.  
  
    > [!WARNING]
    >  Aşağıdaki kod, yalnızca tanıtım amaçlıdır; hedeflenen izinlerinizi üretim kodunda doğruladığınızdan emin olun.  
  
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
  
8.  Dosyayı kaydedin ve yapı **ClaimsTransformation** projesi.  
  
9. İçinde **TestApp** ASP.NET proje başvuruları üzerinde sağ tıklayın ve ardından **Başvuru Ekle**.  
  
10. İçinde **başvuru Yöneticisi** penceresinde, seçin **çözüm** sol menüden seçin **ClaimsTransformation** doldurulan seçenekleri ve ardından  **Tamam**.  
  
11. Kök **Web.config** dosya, gitmek  **\<System.IdentityModel >** girişi. İçinde  **\<identityConfiguration >** öğeler eklemek için aşağıdakileri satır ve dosyayı kaydedin:  
  
    ```xml  
    <claimsAuthenticationManager type="ClaimsTransformation.ClaimsTransformationModule, ClaimsTransformation" />  
    ```  
  
## <a name="step-3--test-your-solution"></a>3. Adım – Çözümünüzü Test Etme  
 Bu adımda ASP.NET Web Forms uygulamanızı test etmek ve kullanıcı Forms kimlik doğrulaması ile oturum açtığında, talep sunulduğundan emin olun.  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>Form kimlik doğrulaması kullanarak talepler için ASP.NET Web Forms uygulamanızı test etmek için  
  
1.  Tuşuna **F5** oluşturun ve uygulamayı çalıştırın. İle sunulan *Default.aspx*.  
  
2.  Üzerinde *Default.aspx* sayfasında, bir tablonun altına görmelisiniz **bilgisayarınızı talep** içeren başlık **veren**, **Serileştirilmiştir**, **Türü**, **değeri**, ve **ValueType** , hesabınız hakkında bilgiler talepleri. Son satırını aşağıdaki şekilde sunulması gereken:  
  
    ||||||  
    |-|-|-|-|-|  
    |YEREL YETKİLİSİ|YEREL YETKİLİSİ|http://schemas.microsoft.com/ws/2008/06/identity/claims/role|Yönetici|http://www.w3.org/2001/XMLSchema#String|
