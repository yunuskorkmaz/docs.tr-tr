---
title: 'Nasıl yapılır: WIF Kullanarak Oturum Açmış Durumu Gösterme'
ms.date: 03/30/2017
ms.assetid: 4d1174e4-5397-4962-9a5f-3b1ad7b3fc14
author: BrucePerlerMS
ms.openlocfilehash: e44dc80260e46b81ac723ada32085390a18a153a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945695"
---
# <a name="how-to-display-signed-in-status-using-wif"></a>Nasıl yapılır: WIF Kullanarak Oturum Açmış Durumu Gösterme
## <a name="applies-to"></a>Uygulanan Öğe  
  
- Microsoft® Windows® Identity Foundation (WıF) 4,5  
  
- ASP.NET® Web Forms  
  
## <a name="summary"></a>Özet  
 Bu konu, bir WıF-Enabled ASP.NET uygulamasında oturum açma durumunun nasıl görüntüleneceğini açıklamaktadır. WıF, uygulamanızı talep kullanan hale getirme ve uygulama kaynakları için kimlik doğrulama ve Yetkilendirmeyi Yönetme mekanizması sağlar.  
  
## <a name="contents"></a>İçindekiler  
  
- Genel Bakış  
  
- Adımların Özeti  
  
- 1\. Adım – kimlik ve erişim uzantısını yükler  
  
- 2\. adım – bağlı olan taraf ASP.NET uygulaması oluşturma  
  
- 3\. adım – kullanıcıların kimliğini doğrulamak için yerel geliştirme STS 'yi etkinleştirin  
  
- 4\. adım – oturum açma durumunu göstermek için ASP.NET uygulamanızı değiştirme  
  
- 5\. adım – WıF ve ASP.NET uygulamanız arasındaki tümleştirmeyi test edin  
  
## <a name="overview"></a>Genel Bakış  
 Bu konuda, WıF kullanılarak basit bir talep kullanan uygulama oluşturma ve bir kullanıcının oturum açmış olup olmadığını kolayca görüntüleme gösterilmektedir. Aşağıdaki adımlarda, Identity ve Access Visual Studio uzantısına dahil olan yerel geliştirme STS 'si kullanılır. Yerel geliştirme STS, bir test ve geliştirme ortamına, talepleri uygulamanızla tümleştirmeyle ilgili basit bir yöntem sağlamak için tasarlanmıştır. Bu, gerçek kimlik doğrulaması gerçekleştirmediğinden ve kimlik bilgilerinin gerekli olmadığından, bir üretim ortamında asla kullanılmamalıdır. Ancak, aşağıdaki adımlarda zorunlu kod, gerçek kimlik doğrulaması kullanan üretime yönelik bir uygulama için aynıdır.  
  
## <a name="summary-of-steps"></a>Adımların Özeti  
  
- 1\. Adım – kimlik ve erişim uzantısını yükler  
  
- 2\. adım – bağlı olan taraf ASP.NET uygulaması oluşturma  
  
- 3\. adım – kullanıcıların kimliğini doğrulamak için yerel geliştirme STS 'yi etkinleştirin  
  
- 4\. adım – oturum açma durumunu göstermek için ASP.NET uygulamanızı değiştirme  
  
- 5\. adım – WıF ve ASP.NET uygulamanız arasındaki tümleştirmeyi test edin  
  
## <a name="step-1--install-the-identity-and-access-extension"></a>1\. Adım – kimlik ve erişim uzantısını yükler  
 Bu adım, kimlik ve erişim uzantısının Visual Studio 2012 ' a nasıl yapılandırılacağını açıklar. Bu uzantı, uygulamanızı STS uç noktalarıyla iletişim kuracak şekilde yapılandırma sürecini otomatikleştirir.  
  
### <a name="to-install-the-identity-and-access-extension"></a>Kimliği ve erişim uzantısını yüklemek için  
  
1. Visual Studio'yu yönetici olarak yükseltilmiş modda başlatın.  
  
2. Visual Studio 'da **Araçlar** ' a tıklayın ve **Uzantı Yöneticisi**' ne tıklayın. **Uzantı Yöneticisi** penceresi görüntülenir.  
  
3. **Uzantı Yöneticisi**'nde sol menüden **çevrimiçi uzantılar** ' a tıklayın ve ardından **Visual Studio Galerisi**' ni seçin.  
  
4. **Uzantı yöneticisinin**sağ üst köşesinde *kimlik ve erişim*' i arayın.  
  
5. **Kimlik ve erişim** öğesi arama sonuçlarında görünür. Tıklayın ve ardından **İndir**' e tıklayın.  
  
6. **İndir ve yükle** iletişim kutusu görüntülenir. Lisans koşullarını kabul ediyorsanız, **yükler**' e tıklayın.  
  
7. **Kimlik ve erişim** uzantısının yüklenmesi tamamlandığında, Visual Studio 'yu yönetici modunda yeniden başlatın.  
  
## <a name="step-2--create-a-relying-party-aspnet-application"></a>2\. adım – bağlı olan taraf ASP.NET uygulaması oluşturma  
 Bu adımda, WıF ile tümleştirilecek bir bağlı olan taraf ASP.NET Web Forms uygulamasının nasıl oluşturulacağı açıklanmaktadır.  
  
### <a name="to-create-a-simple-aspnet-application"></a>Basit bir ASP.NET uygulaması oluşturmak için  
  
1. Visual Studio 'Yu başlatın ve **Dosya**, **Yeni**ve ardından **Proje**' ye tıklayın.  
  
2. **Yeni proje** penceresinde, **ASP.NET Web Forms uygulama**' ya tıklayın.  
  
3. **Ad**alanına girin `TestApp` ve **Tamam**' a basın.  
  
## <a name="step-3--enable-local-development-sts-to-authenticate-users"></a>3\. adım – kullanıcıların kimliğini doğrulamak için yerel geliştirme STS 'yi etkinleştirin  
 Bu adımda, uygulamanızda yerel geliştirme STS 'nin nasıl etkinleştirileceği açıklanır. Yerel geliştirme STS, Visual Studio için kimlik ve erişim uzantısı kullanılarak etkinleştirilir.  
  
### <a name="to-enable-local-development-sts-in-your-aspnet-application"></a>ASP.NET uygulamanızda yerel geliştirme STS 'sini etkinleştirmek için  
  
1. Visual Studio 'da, **Çözüm Gezgini**altında **TestApp** projesine sağ tıklayın **ve ardından kimlik ve erişim**' i seçin.  
  
2. **Kimlik ve erişim** penceresi görüntülenir. **Sağlayıcılar**bölümünde, **yerel geliştirme sts 'Si Ile uygulamanızı test et**' i seçin ve **Uygula**' ya tıklayın.  
  
## <a name="step-4--modify-your-aspnet-application-to-display-sign-in-status"></a>4\. adım – oturum açma durumunu göstermek için ASP.NET uygulamanızı değiştirme  
 Bu adımda, geçerli kullanıcının oturum açmış olup olmadığını dinamik olarak göstermek için ASP.NET uygulamanızın nasıl değiştirileceği açıklanır. STS sağlayıcınız yapılandırıldıktan sonra, gelen talepleri işler. Şimdi, kimlik doğrulamasının sonucunu göstermek için uygulamanızın kodunu yapılandırmanız gerekir.  
  
### <a name="to-display-sign-in-status"></a>Oturum açma durumunu görüntüleme  
  
1. Visual Studio 'da **TestApp** projesi altındaki **default. aspx** dosyasını açın.  
  
2. **Default. aspx** dosyasındaki mevcut biçimlendirmeyi aşağıdaki biçimlendirme ile değiştirin:  
  
    ```  
    <%@ Page Language="C#" AutoEventWireup="true" CodeFile="Default.aspx.cs" Inherits="_Default" %>  
  
    <!DOCTYPE html>  
  
    <html>  
    <head runat="server">  
        <title>Logged In Status</title>  
    </head>  
    <body>  
        <asp:label ID="myLabel" runat="server" />  
    </body>  
    </html>  
    ```  
  
3. **Default. aspx**' i kaydedin ve sonra kodu **default.aspx.cs**adlı dosyanın arkasında açın.  
  
    > [!NOTE]
    > **Default.aspx.cs** , Çözüm Gezgini içinde **default. aspx** altında gizlenebilir. **Default.aspx.cs** görünür değilse, bunun yanındaki üçgene tıklayarak **default. aspx** ' i genişletin.  
  
4. **Default.aspx.cs** içindeki mevcut kodu şu kodla değiştirin:  
  
    ```csharp  
    using System;  
    using System.Web.UI;  
    using System.Security.Claims;  
  
    namespace TestApp  
    {  
        protected void Page_Load(object sender, EventArgs e)  
        {  
            ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;  
  
            if (claimsPrincipal != null)  
            {  
                myLabel.Text = "You are signed in.";  
            }  
            else  
            {  
                myLabel.Text = "You are not signed in.";  
            }  
        }  
    }  
    ```  
  
5. **Default.aspx.cs**kaydedin ve uygulamayı derleyin.  
  
## <a name="step-5--test-the-integration-between-wif-and-your-aspnet-application"></a>5\. adım – WıF ve ASP.NET uygulamanız arasındaki tümleştirmeyi test edin  
 Bu adım, WıF ve ASP.NET uygulamanız arasındaki tümleştirmeyi nasıl test kullanabileceğinizi açıklar.  
  
### <a name="to-test-the-integration-between-wif-and-aspnet"></a>WIF ve ASP.NET arasındaki tümleştirmeyi test etmek için  
  
1. Visual Studio 'da, uygulamanızda hata ayıklamayı başlatmak için **F5** ' e basın. Herhangi bir hata bulunmazsa yeni bir tarayıcı penceresi açılır.  
  
2. Tarayıcının isteğinizi sessizce yeniden yönlendirdiğine ve ardından default. aspx sayfasını açmasını fark edebilirsiniz. WıF düzgün yapılandırıldıysa, sitenin aşağıdaki metni görüntülemesini görmeniz gerekir: **"Oturumunuz açıldı"** .
