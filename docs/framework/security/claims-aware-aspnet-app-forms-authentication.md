---
title: 'Nasıl yapılır: Forms tabanlı kimlik doğrulaması kullanarak talep kullanan ASP.NET uygulaması derleme'
ms.date: 03/30/2017
ms.assetid: 98a3e029-1a9b-4e0c-b5d0-29d3f23f5b15
author: BrucePerlerMS
ms.openlocfilehash: 8dab5cfbcf14707699e6672017f5f80db232f01d
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48025544"
---
# <a name="how-to-build-claims-aware-aspnet-application-using-forms-based-authentication"></a>Nasıl yapılır: Forms tabanlı kimlik doğrulaması kullanarak talep kullanan ASP.NET uygulaması derleme
## <a name="applies-to"></a>Uygulandığı öğe:  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® Web formları  
  
## <a name="summary"></a>Özet  
 Bu nasıl yapılır, Forms kimlik doğrulaması kullanan basit bir talep kullanan ASP.NET Web Forms uygulaması oluşturmak için adım adım ayrıntılı yordamları sağlar. Ayrıca, bir kullanıcı, Forms kimlik doğrulaması ile oturum açtığında beyanların sunulduğunu doğrulamak için uygulamayı test etme için yönergeler sağlar.  
  
## <a name="contents"></a>İçindekiler  
  
-   Amaçlar  
  
-   Genel Bakış  
  
-   Adımların Özeti  
  
-   1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma  
  
-   2. adım: ASP.NET Web Forms uygulaması için form kimlik doğrulaması kullanarak talep yapılandırma  
  
-   3. Adım – Çözümünüzü Test Etme  
  
## <a name="objectives"></a>Amaçlar  
  
-   Bir ASP.NET Web Forms uygulaması için form kimlik doğrulaması kullanarak talep yapılandırma  
  
-   Düzgün çalışıp çalışmadığını görmek için ASP.NET Web Forms uygulamayı test etme  
  
## <a name="overview"></a>Genel Bakış  
 WIF ve kendi beyana dayalı yetkilendirme, .NET 4.5 içinde Framework ayrılmaz bir parçası dahil edilmiştir. Daha önce bir ASP.NET kullanıcı gelen talepleri istediyseniz, WIF yüklemek için gerekli ve ardından atama asıl nesneleri gibi arabirimleri `Thread.CurrentPrincipal` veya `HttpContext.Current.User`. Artık, talep nesneleri otomatik olarak bu sorumlusu tarafından sunulur.  
  
 Forms tarafından otomatik olarak kimliği doğrulanmış tüm kullanıcılar kendileriyle ilişkili talep olduğundan form kimlik doğrulaması .NET 4.5 WIF'ın eklenmesi benefited. Bu nasıl yapılır gösterildiği gibi bu talepler form kimlik doğrulaması kullanan bir ASP.NET uygulamasında hemen kullanmaya başlayabilirsiniz.  
  
## <a name="summary-of-steps"></a>Adımların Özeti  
  
-   1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma  
  
-   2. adım: ASP.NET Web Forms uygulaması için form kimlik doğrulaması kullanarak talep yapılandırma  
  
-   3. Adım – Çözümünüzü Test Etme  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma  
 Bu adımda, yeni bir ASP.NET Web Forms uygulaması oluşturacaksınız.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Basit bir ASP.NET uygulaması oluşturmak için  
  
1.  Visual Studio'yu başlatın ve tıklayın **dosya**, **yeni**, ardından **proje**.  
  
2.  İçinde **yeni proje** penceresinde tıklayın **ASP.NET Web Forms uygulaması**.  
  
3.  İçinde **adı**, girin `TestApp` basın **Tamam**.  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>2. adım: ASP.NET Web Forms uygulaması için form kimlik doğrulaması kullanarak talep yapılandırma  
 Bu adımda, bir yapılandırma girişi için ekler *Web.config* yapılandırma dosyası ve düzenleme *Default.aspx* dosyayı görüntülemek için bir hesap için bilgileri talep.  
  
#### <a name="to-configure-aspnet-application-for-claims-using-forms-authentication"></a>Form kimlik doğrulaması kullanarak talep için ASP.NET uygulamanızı yapılandırmak için  
  
1.  İçinde *Default.aspx* dosya, var olan bir biçimlendirme aşağıdakiyle değiştirin:  
  
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
  
     Bu adım için bir GridView denetimi ekler, *Default.aspx* talepleri ile doldurulacak sayfa Forms kimlik doğrulamasını alınır.  
  
2.  Kaydet *Default.aspx* dosya sonra adlı arka plan kod dosyasını açabilir *Default.aspx.cs*. Varolan kodu aşağıdakiyle değiştirin:  
  
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
  
     Yukarıdaki kod, form kimlik doğrulaması tarafından tanımlanan kullanıcılar dahil olmak üzere, kimliği doğrulanmış bir kullanıcı hakkında talepleri görüntüler.  
  
## <a name="step-3--test-your-solution"></a>3. Adım – Çözümünüzü Test Etme  
 Bu adımda ASP.NET Web Forms uygulamanızı test edin ve bir kullanıcı, Forms kimlik doğrulaması ile oturum açtığında beyanların sunulduğunu doğrulayın.  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>Form kimlik doğrulaması kullanarak talep için ASP.NET Web Forms uygulamanızı test etmek için  
  
1.  Tuşuna **F5** oluşturun ve uygulamayı çalıştırın. İle sunulan *Default.aspx*, sahip olduğu **kaydetme** ve **oturum** üst bağlantılar sayfasının sağ. Tıklayın **kaydetme**.  
  
2.  Üzerinde **kaydetme** sayfasında bir kullanıcı hesabı oluşturun ve ardından **kaydetme**. Hesabınız, form kimlik doğrulaması kullanılarak oluşturulur ve size otomatik olarak oturum açacaksınız.  
  
3.  Giriş sayfasına yönlendirildiniz sonra bir tablo altındaki görmelisiniz **bilgisayarınızı talep** içeren başlık **veren**, **OriginalIssuer**, **Türü**, **değer**, ve **ValueType** talep, hesabınız hakkında bilgiler.
