---
title: 'Nasıl yapılır: Form tabanlı kimlik doğrulaması kullanarak talep kullanan ASP.NET uygulaması oluşturma'
ms.date: 03/30/2017
ms.assetid: 98a3e029-1a9b-4e0c-b5d0-29d3f23f5b15
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 851a856d291da78265e9eac73e9e06028e24ef2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-build-claims-aware-aspnet-application-using-forms-based-authentication"></a>Nasıl yapılır: Form tabanlı kimlik doğrulaması kullanarak talep kullanan ASP.NET uygulaması oluşturma
## <a name="applies-to"></a>Uygulandığı öğe:  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® Web formları  
  
## <a name="summary"></a>Özet  
 Bu yöntem, form kimlik doğrulaması kullanan basit bir talep kullanan ASP.NET Web Forms uygulamayı oluşturmak için ayrıntılı adım adım yordamlar sağlar. Ayrıca, kullanıcı Forms kimlik doğrulaması ile oturum açtığında, talep sunulduğundan emin doğrulamak için uygulamayı test etme için yönergeler sağlar.  
  
## <a name="contents"></a>İçindekiler  
  
-   Amaçlar  
  
-   Genel Bakış  
  
-   Adımların Özeti  
  
-   1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma  
  
-   2. adım – ASP.NET Web Forms uygulaması talepleri kullanarak form kimlik doğrulaması için yapılandırma  
  
-   3. Adım – Çözümünüzü Test Etme  
  
## <a name="objectives"></a>Amaçlar  
  
-   Bir ASP.NET Web Forms uygulaması talepleri kullanarak form kimlik doğrulaması için yapılandırma  
  
-   Düzgün çalışıp çalışmadığını görmek için ASP.NET Web Forms uygulamayı test etme  
  
## <a name="overview"></a>Genel Bakış  
 .NET 4.5 WIF ve onun talep tabanlı yetkilendirme Framework'ün ayrılmaz bir parçası dahil edilmiştir. Daha önce bir ASP.NET kullanıcı talepleri istediyseniz, WIF yüklemek için gerekli ve ardından cast asıl nesneleri gibi arabirimleri `Thread.CurrentPrincipal` veya `HttpContext.Current.User`. Şimdi, talep nesneleri otomatik olarak bu sorumlusu tarafından sunulur.  
  
 Formları tarafından otomatik olarak kimliği doğrulanmış tüm kullanıcılarının kendileriyle ilişkili talep olduğundan form kimlik doğrulaması .NET 4.5 WIF'in eklenmesi benefited. Bu yöntem gösterdiği gibi bu talepler hemen form kimlik doğrulaması kullanan bir ASP.NET uygulamasındaki kullanmaya başlayabilirsiniz.  
  
## <a name="summary-of-steps"></a>Adımların Özeti  
  
-   1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma  
  
-   2. adım – ASP.NET Web Forms uygulaması talepleri kullanarak form kimlik doğrulaması için yapılandırma  
  
-   3. Adım – Çözümünüzü Test Etme  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma  
 Bu adımda, yeni bir ASP.NET Web Forms uygulaması oluşturacaksınız.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Basit bir ASP.NET uygulaması oluşturmak için  
  
1.  Visual Studio'yu başlatın ve tıklatın **dosya**, **yeni**ve ardından **proje**.  
  
2.  İçinde **yeni proje** penceresinde tıklatın **ASP.NET Web Forms uygulaması**.  
  
3.  İçinde **adı**, girin `TestApp` ve basın **Tamam**.  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>2. adım – ASP.NET Web Forms uygulaması talepleri kullanarak form kimlik doğrulaması için yapılandırma  
 Bu adımda, bir yapılandırma girişi ekleyeceksiniz *Web.config* yapılandırma dosyası ve düzenleme *Default.aspx* dosyayı görüntülemek için bir hesap için bilgi talep.  
  
#### <a name="to-configure-aspnet-application-for-claims-using-forms-authentication"></a>Form kimlik doğrulaması kullanarak talepler için ASP.NET uygulamanızı yapılandırmak için  
  
1.  İçinde *Default.aspx* dosya, varolan biçimlendirme şununla değiştirin:  
  
    ```  
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>  
  
    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">  
        <p>  
            This page displays the claims associated with a Forms authenticated user.          
        </p>  
        <h3>Your Claims</h3>  
        <p>  
            <asp:GridView ID="ClaimsGridView" runat="server" CellPadding="3">  
                <AlternatingRowStyle BackColor="White" />  
                <HeaderStyle BackColor="#7AC0DA" ForeColor="White" />  
            </asp:GridView>  
        </p>  
    </asp:Content>  
    ```  
  
     Bu adım bir GridView denetimini ekler, *Default.aspx* talepleri ile doldurulur sayfa alınan formları kimlik.  
  
2.  Kaydet *Default.aspx* dosya sonra adlı kendi arka plan kodu dosyasını açın *Default.aspx.cs*. Var olan kodu aşağıdakilerle değiştirin:  
  
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
  
                if (claimsPrincipal != null)  
                {  
                    this.ClaimsGridView.DataSource = claimsPrincipal.Claims;  
                    this.ClaimsGridView.DataBind();  
                }  
            }  
        }  
    }  
    ```  
  
     Yukarıdaki kod form kimlik doğrulaması tarafından tanımlanan kullanıcılar dahil olmak üzere, kimliği doğrulanmış bir kullanıcı hakkında talepleri görüntüler.  
  
## <a name="step-3--test-your-solution"></a>3. Adım – Çözümünüzü Test Etme  
 Bu adımda ASP.NET Web Forms uygulamanızı test etmek ve kullanıcı Forms kimlik doğrulaması ile oturum açtığında, talep sunulduğundan emin olun.  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>Form kimlik doğrulaması kullanarak talepler için ASP.NET Web Forms uygulamanızı test etmek için  
  
1.  Tuşuna **F5** oluşturun ve uygulamayı çalıştırın. İle sunulan *Default.aspx*, sahip olduğu **kaydetmek** ve **oturum** üst bağlantılar sağ sayfasının. Tıklatın **kaydetmek**.  
  
2.  Üzerinde **kaydetmek** sayfasında, bir kullanıcı hesabı oluşturun ve ardından **kaydetmek**. Hesabınız, form kimlik doğrulaması kullanılarak oluşturulur ve, otomatik olarak oturum açacaksınız.  
  
3.  Giriş sayfasına yönlendirildikten sonra bir tablonun altına görmelisiniz **bilgisayarınızı talep** içeren başlık **veren**, **Serileştirilmiştir**, **Türü**, **değeri**, ve **ValueType** , hesabınız hakkında bilgiler talepleri.
