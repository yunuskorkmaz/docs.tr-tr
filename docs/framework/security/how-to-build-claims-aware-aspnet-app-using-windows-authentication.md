---
title: 'Nasıl yapılır: Windows Kimlik Doğrulaması Kullanarak Talep Kullanan ASP.NET Uygulaması Derleme'
ms.date: 03/30/2017
ms.assetid: 11c53d9d-d34a-44b4-8b5e-22e3eaeaee93
author: BrucePerlerMS
ms.openlocfilehash: 48b1b4715e9e2613757a981ba692d84ad06a1ec6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59323674"
---
# <a name="how-to-build-claims-aware-aspnet-application-using-windows-authentication"></a>Nasıl yapılır: Windows Kimlik Doğrulaması Kullanarak Talep Kullanan ASP.NET Uygulaması Derleme
## <a name="applies-to"></a>Uygulanan Öğe  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® Web formları  
  
## <a name="summary"></a>Özet  
 Bu nasıl yapılır Windows kimlik doğrulaması kullanan basit bir talep kullanan ASP.NET Web Forms uygulaması oluşturmak için adım adım ayrıntılı yordamları sağlar. Ayrıca, kullanıcı Windows kimlik doğrulaması kullanarak oturum açtığında beyanların sunulduğunu doğrulamak için uygulamayı test etme için yönergeler sağlar.  
  
## <a name="contents"></a>İçindekiler  
  
-   Amaçlar  
  
-   Genel Bakış  
  
-   Adımların Özeti  
  
-   1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma  
  
-   2. adım: ASP.NET Web Forms uygulaması Windows kimlik doğrulaması kullanarak talep için yapılandırma  
  
-   3. Adım – Çözümünüzü Test Etme  
  
## <a name="objectives"></a>Amaçlar  
  
-   Bir ASP.NET Web Forms uygulaması Windows kimlik doğrulaması kullanarak talep için yapılandırma  
  
-   Düzgün çalışıp çalışmadığını görmek için ASP.NET Web Forms uygulamayı test etme  
  
## <a name="overview"></a>Genel Bakış  
 WIF ve kendi beyana dayalı yetkilendirme, .NET 4.5 içinde Framework ayrılmaz bir parçası dahil edilmiştir. Daha önce bir ASP.NET kullanıcı gelen talepleri istediyseniz, WIF yüklemek için gerekli ve ardından atama asıl nesneleri gibi arabirimleri `Thread.CurrentPrincipal` veya `HttpContext.Current.User`. Artık, talep nesneleri otomatik olarak bu sorumlusu tarafından sunulur.  
  
 Windows kimlik bilgileri tarafından otomatik olarak kimliği doğrulanmış tüm kullanıcılar kendileriyle ilişkili talep olduğundan Windows kimlik doğrulaması .NET 4.5 WIF'ın eklenmesi benefited. Bu nasıl yapılır gösterildiği gibi bu talepler Windows kimlik doğrulaması kullanan bir ASP.NET uygulamasında hemen kullanmaya başlayabilirsiniz.  
  
## <a name="summary-of-steps"></a>Adımların Özeti  
  
-   1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma  
  
-   2. adım: ASP.NET Web Forms uygulaması Windows kimlik doğrulaması kullanarak talep için yapılandırma  
  
-   3. Adım – Çözümünüzü Test Etme  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma  
 Bu adımda, yeni bir ASP.NET Web Forms uygulaması oluşturacaksınız.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Basit bir ASP.NET uygulaması oluşturmak için  
  
1. Visual Studio'yu başlatın, ardından tıklatın **dosya**, **yeni**, ardından **proje**.  
  
2. İçinde **yeni proje** penceresinde tıklayın **ASP.NET Web Forms uygulaması**.  
  
3. İçinde **adı**, girin `TestApp` basın **Tamam**.  
  
4. Sonra **TestApp** proje oluşturuldu, içine tıklayarak **Çözüm Gezgini**. Projenin özelliklerini görünür **özellikleri** bölmesinde aşağıdaki **Çözüm Gezgini**. Ayarlama **Windows kimlik doğrulaması** özelliğini **etkin**.  
  
    > [!WARNING]
    >  El ile etkinleştirmeniz gerekir böylece Windows kimlik doğrulaması, yeni ASP.NET uygulamalarında varsayılan olarak devre dışıdır.  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-windows-authentication"></a>2. adım: ASP.NET Web Forms uygulaması Windows kimlik doğrulaması kullanarak talep için yapılandırma  
 Bu adımda, bir yapılandırma girişi için ekler *Web.config* yapılandırma dosyası ve değiştirme *Default.aspx* dosyayı görüntülemek için bir hesap için bilgileri talep.  
  
#### <a name="to-configure-aspnet-application-for-claims-using-windows-authentication"></a>ASP.NET uygulaması için Windows kimlik doğrulaması kullanarak talep yapılandırmak için  
  
1. İçinde **TestApp** projenin *Default.aspx* dosya, var olan bir biçimlendirme aşağıdakiyle değiştirin:  
  
    ```  
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true"  
        CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>  
  
    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">  
        <p>  
            This page displays the claims associated with a Windows authenticated user.          
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
  
     Bu adım için bir GridView denetimi ekler, *Default.aspx* talepleri ile doldurulacak sayfasında Windows kimlik doğrulamasını alınır.  
  
2. Kaydet *Default.aspx* dosya sonra adlı arka plan kod dosyasını açabilir *Default.aspx.cs*. Varolan kodu aşağıdakiyle değiştirin:  
  
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
  
     Yukarıdaki kod, kimliği doğrulanmış bir kullanıcı hakkında talepleri görüntüler.  
  
3. Uygulamanın kimlik doğrulama türünü değiştirmek için değiştirme  **\<kimlik doğrulama >** engelleyin  **\<system.web >** projenin kök bölümünü  *Web.config* yalnızca aşağıdaki yapılandırma girişi içeren dosya:  
  
    ```xml  
    <authentication mode="Windows" />  
    ```  
  
4. Son olarak, değişiklik  **\<yetkilendirme >** engelleyin  **\<system.web >** aynı bölümünü *Web.config* zorlamak için dosya kimlik doğrulaması:  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    ```  
  
## <a name="step-3--test-your-solution"></a>3. Adım – Çözümünüzü Test Etme  
 Bu adımda ASP.NET Web Forms uygulamanızı test edin ve bir kullanıcı Windows kimlik doğrulaması ile oturum açtığında beyanların sunulduğunu doğrulayın.  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-windows-authentication"></a>Windows kimlik doğrulaması kullanarak talep için ASP.NET Web Forms uygulamanızı test etmek için  
  
1. Tuşuna **F5** oluşturun ve uygulamayı çalıştırın. İle sunulan *Default.aspx*, ve (etki alanı adı dahil), Windows hesap adı zaten üst kimliği doğrulanmış kullanıcı olarak görünmesi gereken sayfanın sağ. Sayfanın içeriğinin Windows hesabınızdan alınan talepleri ile doldurulan bir tablo içermelidir.
