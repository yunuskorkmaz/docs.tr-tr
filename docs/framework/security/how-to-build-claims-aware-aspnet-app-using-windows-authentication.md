---
title: 'Nasıl yapılır: Windows Kimlik Doğrulaması Kullanarak Talep Kullanan ASP.NET Uygulaması Derleme'
ms.date: 03/30/2017
ms.assetid: 11c53d9d-d34a-44b4-8b5e-22e3eaeaee93
author: BrucePerlerMS
ms.openlocfilehash: 34d6c7916b3035e9896b1dd9d7c7d8b3e7b0fcfc
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040991"
---
# <a name="how-to-build-claims-aware-aspnet-application-using-windows-authentication"></a>Nasıl yapılır: Windows Kimlik Doğrulaması Kullanarak Talep Kullanan ASP.NET Uygulaması Derleme

## <a name="applies-to"></a>Uygulanan Öğe

- Microsoft® Windows® Identity Foundation (WIF)

- ASP.NET® Web Forms

## <a name="summary"></a>Özet

Bu nasıl yapılır, Windows kimlik doğrulaması kullanan basit bir talep kullanan ASP.NET Web Forms uygulaması oluşturmaya yönelik ayrıntılı adım adım yordamlar sağlar. Ayrıca, bir Kullanıcı Windows kimlik doğrulaması kullanarak oturum açtığında taleplerin sunulduğunu doğrulamak için uygulamanın nasıl test alınacağını belirten yönergeler de sağlar.

## <a name="contents"></a>İçindekiler

- Amaçlar

- Genel Bakış

- Adımların Özeti

- 1\. adım – basit bir ASP.NET Web Forms uygulaması oluşturma

- 2\. Adım – Windows kimlik doğrulamasını kullanarak talepler için ASP.NET Web Forms uygulamasını yapılandırma

- 3\. Adım – Çözümünüzü Test Etme

## <a name="objectives"></a>Amaçlar

- Windows kimlik doğrulamasını kullanarak talepler için bir ASP.NET Web Forms uygulaması yapılandırma

- Düzgün çalışıp çalışmadığını görmek için ASP.NET Web Forms uygulamasını test etme

## <a name="overview"></a>Genel Bakış

.NET 4,5 ' de, WıF ve talep tabanlı yetkilendirme, Framework 'ün ayrılmaz bir parçası olarak eklenmiştir. Daha önce, bir ASP.net kullanıcısının taleplerini istediyseniz, WIF 'yi yüklemeli ve ardından arabirimleri veya `Thread.CurrentPrincipal` `HttpContext.Current.User`gibi Principal nesnelerine atamalısınız. Artık talepler, bu Principal nesneleri tarafından otomatik olarak sunulur.

Windows kimlik bilgileri tarafından kimlik doğrulaması yapılan tüm kullanıcılar otomatik olarak bunlarla ilişkili talepler içerdiğinden, Windows kimlik doğrulamasının .NET 4,5 ' ye dahil edildiği benefited vardır. Bu talepleri, nasıl gösterildiği gibi, Windows kimlik doğrulaması kullanan bir ASP.NET uygulamasında hemen kullanmaya başlayabilirsiniz.

## <a name="summary-of-steps"></a>Adımların Özeti

- 1\. adım – basit bir ASP.NET Web Forms uygulaması oluşturma

- 2\. Adım – Windows kimlik doğrulamasını kullanarak talepler için ASP.NET Web Forms uygulamasını yapılandırma

- 3\. Adım – Çözümünüzü Test Etme

## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>1\. adım – basit bir ASP.NET Web Forms uygulaması oluşturma

Bu adımda, yeni bir ASP.NET Web Forms uygulaması oluşturacaksınız.

### <a name="to-create-a-simple-aspnet-application"></a>Basit bir ASP.NET uygulaması oluşturmak için

1. Visual Studio 'yu başlatın ve ardından **Dosya**, **Yeni**ve ardından **Proje**' ye tıklayın.

2. **Yeni proje** penceresinde, **ASP.NET Web Forms uygulama**' ya tıklayın.

3. **Ad**alanına girin `TestApp` ve **Tamam**' a basın.

4. **TestApp** projesi oluşturulduktan sonra **Çözüm Gezgini**' de tıklayın. Projenin özellikleri **Çözüm Gezgini**aşağıdaki **Özellikler** bölmesinde görünür. **Windows kimlik doğrulama** özelliğini **etkin**olarak ayarlayın.

    > [!WARNING]
    > Windows kimlik doğrulaması, yeni ASP.NET uygulamalarında varsayılan olarak devre dışıdır, bu yüzden el ile etkinleştirmeniz gerekir.

## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-windows-authentication"></a>2\. Adım – Windows kimlik doğrulamasını kullanarak talepler için ASP.NET Web Forms uygulamasını yapılandırma

Bu adımda, *Web. config* yapılandırma dosyasına bir yapılandırma girişi ekleyecek ve *varsayılan. aspx* dosyasını değiştirerek bir hesabın talep bilgilerini görüntüleyecek şekilde değiştirirsiniz.

### <a name="to-configure-aspnet-application-for-claims-using-windows-authentication"></a>Windows kimlik doğrulamasını kullanarak ASP.NET uygulamasını talepler için yapılandırmak için

1. **TestApp** projesinin *default. aspx* dosyasında, varolan biçimlendirmeyi aşağıdaki kodla değiştirin:

    ```aspx-csharp
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

    Bu adım, *default. aspx* sayfanıza, Windows kimlik doğrulamasından alınan taleplerle doldurulacak bir GridView denetimi ekler.

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
                this.ClaimsGridView.DataSource = claimsPrincipal.Claims;
                this.ClaimsGridView.DataBind();
            }
        }
    }
    ```

    Yukarıdaki kodda kimliği doğrulanmış bir kullanıcı hakkında talepler görüntülenir.

3. Uygulamanın kimlik doğrulaması türünü değiştirmek için, projenin kök *Web. config* dosyasının  **\<System. Web >** bölümündeki  **\<Authentication >** bloğunu yalnızca aşağıdakileri içerecek şekilde değiştirin yapılandırma girişi:

    ```xml
    <authentication mode="Windows" />
    ```

4. Son olarak, kimlik doğrulamayı zorlamak için aynı *Web. config* dosyasının  **\<System. Web >** bölümündeki  **\<Authorization >** bloğunu değiştirin:

    ```xml
    <authorization>
        <deny users="?" />
    </authorization>
    ```

## <a name="step-3--test-your-solution"></a>3\. Adım – Çözümünüzü Test Etme

Bu adımda, ASP.NET Web Forms uygulamanızı test edecek ve Kullanıcı Windows kimlik doğrulamasıyla oturum açtığında taleplerin sunulduğunu doğrulayacaksınız.

### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-windows-authentication"></a>Windows kimlik doğrulamasını kullanarak ASP.NET Web Forms uygulamanızı talepler için test etme

1. Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın. *Default. aspx*ve Windows hesabınızın adı (etki alanı adı dahil), sayfanın sağ üst kısmında kimliği doğrulanmış kullanıcı olarak gösterilmelidir. Sayfanın içeriği, Windows hesabınızdan alınan taleplerle doldurulmuş bir tablo içermelidir.
