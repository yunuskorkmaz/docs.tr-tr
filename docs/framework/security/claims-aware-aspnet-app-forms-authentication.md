---
title: 'Nasıl yapılır: Forms Tabanlı Kimlik Doğrulaması Kullanarak Talep Kullanan ASP.NET Uygulaması Derleme'
ms.date: 03/30/2017
ms.assetid: 98a3e029-1a9b-4e0c-b5d0-29d3f23f5b15
author: BrucePerlerMS
ms.openlocfilehash: 75db96a621d7863ef445efb24814111b34da6960
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971843"
---
# <a name="how-to-build-claims-aware-aspnet-application-using-forms-based-authentication"></a>Nasıl yapılır: Forms Tabanlı Kimlik Doğrulaması Kullanarak Talep Kullanan ASP.NET Uygulaması Derleme

## <a name="applies-to"></a>Uygulanan Öğe

- Microsoft® Windows® Identity Foundation (WIF)

- ASP.NET® Web Forms

## <a name="summary"></a>Özet

Bu nasıl yapılır, Forms kimlik doğrulaması kullanan basit bir talep kullanan ASP.NET Web Forms uygulaması oluşturmaya yönelik ayrıntılı adım adım yordamlar sağlar. Ayrıca, bir kullanıcı form kimlik doğrulamasıyla oturum açtığında taleplerin sunulduğunu doğrulamak için uygulamanın nasıl test alınacağını belirten yönergeler de sağlar.

## <a name="contents"></a>İçindekiler

- Amaçlar

- Genel Bakış

- Adımların Özeti

- 1\. adım – basit bir ASP.NET Web Forms uygulaması oluşturma

- 2\. adım – Forms kimlik doğrulamasını kullanarak talepler için ASP.NET Web Forms uygulamasını yapılandırma

- 3\. Adım – Çözümünüzü Test Etme

## <a name="objectives"></a>Amaçlar

- Forms kimlik doğrulaması kullanarak talepler için bir ASP.NET Web Forms uygulaması yapılandırma

- Düzgün çalışıp çalışmadığını görmek için ASP.NET Web Forms uygulamasını test etme

## <a name="overview"></a>Genel Bakış

.NET 4,5 ' de, WıF ve talep tabanlı yetkilendirme, Framework 'ün ayrılmaz bir parçası olarak eklenmiştir. Daha önce, bir ASP.net kullanıcısının taleplerini istediyseniz, WIF 'yi yüklemeli ve ardından arabirimleri veya `Thread.CurrentPrincipal` `HttpContext.Current.User`gibi Principal nesnelerine atamalısınız. Artık talepler, bu Principal nesneleri tarafından otomatik olarak sunulur.

Forms kimlik doğrulaması, form tarafından kimliği doğrulanan tüm kullanıcılar otomatik olarak bunlarla ilişkili talepler içerdiğinden, .NET 4,5 ' a dahil benefited. Bu talepleri, nasıl gösterildiği gibi, Forms kimlik doğrulaması kullanan bir ASP.NET uygulamasında hemen kullanmaya başlayabilirsiniz.

## <a name="summary-of-steps"></a>Adımların Özeti

- 1\. adım – basit bir ASP.NET Web Forms uygulaması oluşturma

- 2\. adım – Forms kimlik doğrulamasını kullanarak talepler için ASP.NET Web Forms uygulamasını yapılandırma

- 3\. Adım – Çözümünüzü Test Etme

## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>1\. adım – basit bir ASP.NET Web Forms uygulaması oluşturma

Bu adımda, yeni bir ASP.NET Web Forms uygulaması oluşturacaksınız.

### <a name="to-create-a-simple-aspnet-application"></a>Basit bir ASP.NET uygulaması oluşturmak için

1. Visual Studio 'Yu başlatın ve **Dosya**, **Yeni**ve ardından **Proje**' ye tıklayın.

2. **Yeni proje** penceresinde, **ASP.NET Web Forms uygulama**' ya tıklayın.

3. **Ad**alanına girin `TestApp` ve **Tamam**' a basın.

## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>2\. adım – Forms kimlik doğrulamasını kullanarak talepler için ASP.NET Web Forms uygulamasını yapılandırma

Bu adımda, *Web. config* yapılandırma dosyasına bir yapılandırma girişi ekleyecek ve bir hesabın talep bilgilerini görüntülemesi için *default. aspx* dosyasını düzenleyecaksınız.

### <a name="to-configure-aspnet-application-for-claims-using-forms-authentication"></a>Forms kimlik doğrulamasını kullanarak talepler için ASP.NET uygulamasını yapılandırmak için

1. *Default. aspx* dosyasında, varolan biçimlendirmeyi aşağıdaki kodla değiştirin:

    ```aspx
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

    Bu adım, *varsayılan. aspx* sayfanıza, Forms kimlik doğrulamasından alınan taleplerle doldurulacak bir GridView denetimi ekler.

2. *Default. aspx* dosyasını kaydedin, sonra *default.aspx.cs*adlı arka plan kod dosyasını açın. Mevcut kodu şu kodla değiştirin:

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

    Yukarıdaki kod, Forms kimlik doğrulaması tarafından tanımlanan kullanıcılar da dahil olmak üzere kimliği doğrulanmış bir kullanıcı hakkında talepler görüntüler.

## <a name="step-3--test-your-solution"></a>3\. Adım – Çözümünüzü Test Etme

Bu adımda, ASP.NET Web Forms uygulamanızı test edecek ve Kullanıcı form kimlik doğrulamasıyla oturum açtığında taleplerin sunulduğunu doğrulayacaksınız.

### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>Forms kimlik doğrulaması kullanarak ASP.NET Web Forms uygulamanızı talepler için test etme

1. Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın. Sayfanın sağ üst kısmındaki, **kayıt** ve **oturum açma** bağlantılarına sahip *default. aspx*ile sunulmalısınız. **Kaydol**' a tıklayın.

2. **Kaydet** sayfasında, bir kullanıcı hesabı oluşturun ve ardından **Kaydet**' e tıklayın. Hesabınız, form kimlik doğrulaması kullanılarak oluşturulur ve oturumunuz otomatik olarak açılır.

3. Giriş sayfasına yönlendirildikten sonra, **talep** başlığının altında yer alan **veren**, **OriginalIssuer**, **Type**, **Value**ve **ValueType** talep bilgilerini içeren bir tablo görmeniz gerekir. hesabı.
