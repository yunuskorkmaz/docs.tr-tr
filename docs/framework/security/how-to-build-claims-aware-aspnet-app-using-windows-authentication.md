---
title: "Nasıl yapılır: Windows kimlik doğrulaması kullanarak talep kullanan ASP.NET uygulaması oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11c53d9d-d34a-44b4-8b5e-22e3eaeaee93
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 676a03678cbdf6fe08e628806df2a1853fb71718
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-build-claims-aware-aspnet-application-using-windows-authentication"></a>Nasıl yapılır: Windows kimlik doğrulaması kullanarak talep kullanan ASP.NET uygulaması oluşturma
## <a name="applies-to"></a>Uygulandığı öğe:  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® Web formları  
  
## <a name="summary"></a>Özet  
 Bu yöntem Windows kimlik doğrulaması kullanan basit bir talep kullanan ASP.NET Web Forms uygulamayı oluşturmak için ayrıntılı adım adım yordamlar verilmektedir. Ayrıca, bir kullanıcının Windows kimlik doğrulaması kullanarak oturum açtığında, talep sunulduğundan emin doğrulamak için uygulamayı test etme için yönergeler sağlar.  
  
## <a name="contents"></a>İçindekiler  
  
-   Amaçlar  
  
-   Genel Bakış  
  
-   Adımların Özeti  
  
-   1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma  
  
-   2. adım – ASP.NET Web Forms uygulaması Windows kimlik doğrulaması kullanarak talep için yapılandırma  
  
-   3. Adım – Çözümünüzü Test Etme  
  
## <a name="objectives"></a>Amaçlar  
  
-   Bir ASP.NET Web Forms uygulaması Windows kimlik doğrulaması kullanarak talep için yapılandırma  
  
-   Düzgün çalışıp çalışmadığını görmek için ASP.NET Web Forms uygulamayı test etme  
  
## <a name="overview"></a>Genel Bakış  
 .NET 4.5 WIF ve onun talep tabanlı yetkilendirme Framework'ün ayrılmaz bir parçası dahil edilmiştir. Daha önce bir ASP.NET kullanıcı talepleri istediyseniz, WIF yüklemek için gerekli ve ardından cast asıl nesneleri gibi arabirimleri `Thread.CurrentPrincipal` veya `HttpContext.Current.User`. Şimdi, talep nesneleri otomatik olarak bu sorumlusu tarafından sunulur.  
  
 Windows kimlik bilgileri tarafından otomatik olarak kimliği doğrulanmış tüm kullanıcılarının kendileriyle ilişkili talep olduğundan Windows kimlik doğrulaması .NET 4.5 WIF'in eklenmesi benefited. Bu yöntem gösterdiği gibi bu talepler hemen Windows kimlik doğrulaması kullanan bir ASP.NET uygulamasındaki kullanmaya başlayabilirsiniz.  
  
## <a name="summary-of-steps"></a>Adımların Özeti  
  
-   1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma  
  
-   2. adım – ASP.NET Web Forms uygulaması Windows kimlik doğrulaması kullanarak talep için yapılandırma  
  
-   3. Adım – Çözümünüzü Test Etme  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma  
 Bu adımda, yeni bir ASP.NET Web Forms uygulaması oluşturacaksınız.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Basit bir ASP.NET uygulaması oluşturmak için  
  
1.  Visual Studio'yu başlatın, ardından **dosya**, **yeni**ve ardından **proje**.  
  
2.  İçinde **yeni proje** penceresinde tıklatın **ASP.NET Web Forms uygulaması**.  
  
3.  İçinde **adı**, girin `TestApp` ve basın **Tamam**.  
  
4.  Sonra **TestApp** proje oluşturuldu, içinde tıklayın **Çözüm Gezgini**. Proje Özellikleri görünür **özellikleri** bölmesinde aşağıdaki **Çözüm Gezgini**. Ayarlama **Windows kimlik doğrulaması** özelliğine **etkin**.  
  
    > [!WARNING]
    >  El ile etkinleştirmeniz gerekir böylece Windows kimlik doğrulaması yeni ASP.NET uygulamalarında varsayılan olarak devre dışıdır.  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-windows-authentication"></a>2. adım – ASP.NET Web Forms uygulaması Windows kimlik doğrulaması kullanarak talep için yapılandırma  
 Bu adımda, bir yapılandırma girişi ekleyeceksiniz *Web.config* yapılandırma dosyası ve değiştirme *Default.aspx* dosyayı görüntülemek için bir hesap için bilgi talep.  
  
#### <a name="to-configure-aspnet-application-for-claims-using-windows-authentication"></a>Windows kimlik doğrulaması kullanarak talepler için ASP.NET uygulamanızı yapılandırmak için  
  
1.  İçinde **TestApp** projenin *Default.aspx* dosya, varolan biçimlendirme şununla değiştirin:  
  
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
  
     Bu adım bir GridView denetimini ekler, *Default.aspx* talepleri ile doldurulur sayfasında Windows kimlik doğrulamasını alınır.  
  
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
                this.ClaimsGridView.DataSource = claimsPrincipal.Claims;  
                this.ClaimsGridView.DataBind();  
            }  
        }  
    }  
    ```  
  
     Yukarıdaki kod kimliği doğrulanmış bir kullanıcı hakkında talepleri görüntüler.  
  
3.  Uygulamanın kimlik doğrulaması türünü değiştirmek için değiştirmek  **\<kimlik doğrulama >** engelleyin  **\<system.web >** projenin kök bölümünü  *Web.config* yalnızca aşağıdaki yapılandırma girdisi içeren dosya:  
  
    ```xml  
    <authentication mode="Windows" />  
    ```  
  
4.  Son olarak, değişiklik  **\<yetkilendirme >** engelleyin  **\<system.web >** aynı bölümünü *Web.config* zorlamak için dosya kimlik doğrulaması:  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    ```  
  
## <a name="step-3--test-your-solution"></a>3. Adım – Çözümünüzü Test Etme  
 Bu adımda ASP.NET Web Forms uygulamanızı test etmek ve kullanıcı Windows kimlik doğrulaması ile oturum açtığında, talep sunulduğundan emin olun.  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-windows-authentication"></a>Windows kimlik doğrulaması kullanarak talepler için ASP.NET Web Forms uygulamanızı test etmek için  
  
1.  Tuşuna **F5** oluşturun ve uygulamayı çalıştırın. İle sunulan *Default.aspx*, ve (etki alanı adı dahil), Windows hesap adı zaten üst kimliği doğrulanmış kullanıcı olarak görünmesi gereken sağ sayfasının. Sayfanın içeriğinin Windows hesabınızdan alınan talep ile doldurulduğu bir tablo içermesi gerekir.
