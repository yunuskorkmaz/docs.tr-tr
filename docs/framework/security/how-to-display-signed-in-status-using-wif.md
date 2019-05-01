---
title: 'Nasıl yapılır: WIF Kullanarak Oturum Açmış Durumu Gösterme'
ms.date: 03/30/2017
ms.assetid: 4d1174e4-5397-4962-9a5f-3b1ad7b3fc14
author: BrucePerlerMS
ms.openlocfilehash: b07a8930255786686fb1e587b2a29bbc708eff63
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940510"
---
# <a name="how-to-display-signed-in-status-using-wif"></a>Nasıl yapılır: WIF Kullanarak Oturum Açmış Durumu Gösterme
## <a name="applies-to"></a>Uygulanan Öğe  
  
- Microsoft® Windows® Identity Foundation (WIF) 4.5  
  
- ASP.NET® Web formları  
  
## <a name="summary"></a>Özet  
 Bu konuda, oturum durumu WIF özelliği etkinleştirilmiş bir ASP.NET uygulamasında görüntülenecek açıklar. WIF, talep kullanan, uygulama ve yönetme kimlik doğrulaması ve yetkilendirme için uygulama kaynakları oluşturmaya yönelik bir mekanizma sağlar.  
  
## <a name="contents"></a>İçindekiler  
  
- Genel Bakış  
  
- Adımların Özeti  
  
- 1. adım – yükleme kimlik ve erişim uzantısı  
  
- 2. adım – bir bağlı olan taraf ASP.NET uygulaması oluşturma  
  
- Adım 3 – kullanıcıların kimliğini doğrulamak için etkinleştirme yerel geliştirme  
  
- 4. adım: ASP.NET uygulamanız oturum durumu görüntülemek için değiştirin  
  
- 5. adım – WIF ve ASP.NET uygulamanız arasındaki tümleştirme testi  
  
## <a name="overview"></a>Genel Bakış  
 Bu konuda, WIF kullanarak talep kullanan uygulama oluşturmak nasıl ve nasıl kolayca veya bir kullanıcı oturumu açıkken eşleşmediğini gösterir. Kimlik ve erişim Visual Studio uzantısı dahil olan yerel geliştirme STS'si aşağıdaki adımları kullanın. Yerel geliştirme STS'si talep uygulamanızla tümleştirmenin basit bir yöntem sağlamak amacıyla bir test ve geliştirme ortamı için tasarlanmıştır. Hiçbir zaman bir üretim ortamında gerçek kimlik doğrulaması gerçekleştirmez ve kimlik bilgileri gerekli değil olarak kullanılmalıdır. Ancak, kesinlik temelli kod aşağıdaki adımlarda gerçek kimlik doğrulaması kullanarak üretime hazır bir uygulama için aynıdır.  
  
## <a name="summary-of-steps"></a>Adımların Özeti  
  
- 1. adım – yükleme kimlik ve erişim uzantısı  
  
- 2. adım – bir bağlı olan taraf ASP.NET uygulaması oluşturma  
  
- Adım 3 – kullanıcıların kimliğini doğrulamak için etkinleştirme yerel geliştirme  
  
- 4. adım: ASP.NET uygulamanız oturum durumu görüntülemek için değiştirin  
  
- 5. adım – WIF ve ASP.NET uygulamanız arasındaki tümleştirme testi  
  
## <a name="step-1--install-the-identity-and-access-extension"></a>1. adım – yükleme kimlik ve erişim uzantısı  
 Bu adımda, Visual Studio 2012 için kimlik ve erişim uzantısının nasıl yapılandırılacağı açıklanır. Bu uzantı STS uç noktaları ile iletişim kurmak için uygulamanızı yapılandırma işlemi otomatik hale getirir.  
  
#### <a name="to-install-the-identity-and-access-extension"></a>Kimlik ve erişim uzantıyı yüklemek için  
  
1. Visual Studio'yu yönetici olarak yükseltilmiş modda başlatın.  
  
2. Visual Studio'da **Araçları** tıklatıp **Uzantı Yöneticisi**. **Uzantı Yöneticisi** penceresi görüntülenir.  
  
3. İçinde **Uzantı Yöneticisi**, tıklayın **çevrimiçi uzantılara** seçip sol menüden **Visual Studio Galerisi**.  
  
4. Sağ üst köşesindeki içinde **Uzantı Yöneticisi**, arama *kimlik ve erişim*.  
  
5. **Kimlik ve erişim** öğesi, arama sonuçlarında görünür. Tıklayın ve ardından **indirme**.  
  
6. **Yükleyip** iletişim kutusu görüntülenir. Lisans şartlarını kabul ediyorsanız tıklayın **yükleme**.  
  
7. Zaman **kimlik ve erişim** uzantı yükleme tamamlandığında, Visual Studio'yu Yönetici modunda yeniden başlatın.  
  
## <a name="step-2--create-a-relying-party-aspnet-application"></a>2. adım – bir bağlı olan taraf ASP.NET uygulaması oluşturma  
 Bu adım, bağlı olan taraf WIF ile tümleştirilecek bir ASP.NET Web Forms uygulaması oluşturmayı açıklar.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Basit bir ASP.NET uygulaması oluşturmak için  
  
1. Visual Studio'yu başlatın ve tıklayın **dosya**, **yeni**, ardından **proje**.  
  
2. İçinde **yeni proje** penceresinde tıklayın **ASP.NET Web Forms uygulaması**.  
  
3. İçinde **adı**, girin `TestApp` basın **Tamam**.  
  
## <a name="step-3--enable-local-development-sts-to-authenticate-users"></a>Adım 3 – kullanıcıların kimliğini doğrulamak için etkinleştirme yerel geliştirme  
 Bu adım, uygulamanızı yerel geliştirme STS'si etkinleştirmeyi açıklar. Yerel geliştirme STS'si kimlik ve erişim uzantısı için Visual Studio aracılığıyla etkinleştirilir.  
  
#### <a name="to-enable-local-development-sts-in-your-aspnet-application"></a>ASP.NET uygulamanızı yerel geliştirme STS'si etkinleştirmek için  
  
1. Visual Studio'da sağ **TestApp** altındaki proje **Çözüm Gezgini**, ardından **kimlik ve erişim**.  
  
2. **Kimlik ve erişim** penceresi görüntülenir. Altında **sağlayıcıları**seçin **uygulamanızı yerel geliştirme STS'si ile Test**, ardından **Uygula**.  
  
## <a name="step-4--modify-your-aspnet-application-to-display-sign-in-status"></a>4. adım: ASP.NET uygulamanız oturum durumu görüntülemek için değiştirin  
 Bu adım, ASP.NET uygulamanızı, geçerli kullanıcının oturum açtığı olmadığını dinamik olarak görüntülenecek değiştirmeniz açıklar. WIF, STS sağlayıcınız yapılandırıldıktan sonra gelen talepleri işler. Şimdi, kimlik doğrulaması sonucu görüntülemek için uygulamanızın kod yapılandırmanız gerekir.  
  
#### <a name="to-display-sign-in-status"></a>Oturum durumunu görüntülemek için  
  
1. Visual Studio'da açın **Default.aspx** altında dosya **TestApp** proje.  
  
2. Mevcut biçimlendirmeyi Değiştir **Default.aspx** aşağıdaki işaretlemeyle dosyası:  
  
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
  
3. Kaydet **Default.aspx**ve ardından adlı dosyanın arkasındaki kodunu açın **Default.aspx.cs**.  
  
    > [!NOTE]
    >  **Default.aspx.cs** altındaki gizlenebilir **Default.aspx** Çözüm Gezgini'nde. Varsa **Default.aspx.cs** görünür durumda değilse genişletin **Default.aspx** yanında üçgeni tıklayarak.  
  
4. Varolan kodda değiştirin **Default.aspx.cs** aşağıdaki kod ile:  
  
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
  
5. Kaydet **Default.aspx.cs**ve uygulamayı derleyin.  
  
## <a name="step-5--test-the-integration-between-wif-and-your-aspnet-application"></a>5. adım – WIF ve ASP.NET uygulamanız arasındaki tümleştirme testi  
 Bu adımda, WIF ve ASP.NET uygulamanızı arasında tümleştirmeyi nasıl sınayıp doğrulayabileceğiniz açıklanır.  
  
#### <a name="to-test-the-integration-between-wif-and-aspnet"></a>WIF ve ASP.NET arasındaki tümleştirmeden test etmek için  
  
1. Visual Studio'da **F5** uygulamanızı hata ayıklama başlatılamıyor. Hiçbir hata bulunamazsa, yeni bir tarayıcı penceresi açılır.  
  
2. Tarayıcı sessizce isteğiniz STS'ye yönlendirir ve ardından Default.aspx sayfasında açılır fark edebilirsiniz. WIF düzgün şekilde yapılandırılmışsa, aşağıdaki metni görüntüle sitesini görmeniz gerekir: **"Oturum"**.
