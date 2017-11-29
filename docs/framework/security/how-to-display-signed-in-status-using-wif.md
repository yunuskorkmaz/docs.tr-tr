---
title: "Nasıl yapılır: Görüntü WIF kullanarak durumunda imzalı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d1174e4-5397-4962-9a5f-3b1ad7b3fc14
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 494e67b39187a2a38f29f994e17051430d90f708
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-display-signed-in-status-using-wif"></a>Nasıl yapılır: Görüntü WIF kullanarak durumunda imzalı
## <a name="applies-to"></a>Uygulandığı öğe:  
  
-   Microsoft® Windows® Identity Foundation (WIF) 4.5  
  
-   ASP.NET® Web formları  
  
## <a name="summary"></a>Özet  
 Bu konuda, oturum WIF etkinleştirilmiş ASP.NET uygulamasının durumu görüntülemek açıklar. WIF, talep kullanan, uygulama ve yönetme kimlik doğrulama ve yetkilendirme için uygulama kaynaklarını yapmak için mekanizma sağlar.  
  
## <a name="contents"></a>İçindekiler  
  
-   Genel Bakış  
  
-   Adımların Özeti  
  
-   1. adım – kimlik yüklemek ve erişim uzantısı  
  
-   Adım 2 – bir bağlı olan taraf ASP.NET uygulaması oluşturma  
  
-   Adım 3 – kullanıcıların kimliklerini doğrulamak için etkinleştir yerel geliştirme STS  
  
-   4. adım – oturum durumunu görüntülemek için ASP.NET uygulamanızın değiştirme  
  
-   5. adım – WIF ve ASP.NET uygulamanızın arasında tümleştirme Test  
  
## <a name="overview"></a>Genel Bakış  
 Bu konu, WIF kullanarak basit bir talep kullanan uygulama oluşturma ve kolay bir kullanıcı veya oturum eşleşmediğini gösterir. Kimlik ve erişim Visual Studio uzantısı bulunan yerel geliştirme STS aşağıdaki adımları kullanın. Yerel geliştirme STS talepler uygulamanıza tümleştirmek için basit bir yöntem sağlamak bir test ve geliştirme ortamı için tasarlanmıştır. Bunu hiçbir zaman bir üretim ortamında gerçek kimlik doğrulaması gerçekleştirmez ve kimlik bilgileri gerekli değil olarak kullanılmalıdır. Ancak, kesinlik temelli kod aşağıdaki adımlarda gerçek kimlik doğrulaması kullanılarak üretime hazır bir uygulama için aynıdır.  
  
## <a name="summary-of-steps"></a>Adımların Özeti  
  
-   1. adım – kimlik yüklemek ve erişim uzantısı  
  
-   Adım 2 – bir bağlı olan taraf ASP.NET uygulaması oluşturma  
  
-   Adım 3 – kullanıcıların kimliklerini doğrulamak için etkinleştir yerel geliştirme STS  
  
-   4. adım – oturum durumunu görüntülemek için ASP.NET uygulamanızın değiştirme  
  
-   5. adım – WIF ve ASP.NET uygulamanızın arasında tümleştirme Test  
  
## <a name="step-1--install-the-identity-and-access-extension"></a>1. adım – kimlik yüklemek ve erişim uzantısı  
 Bu adım, Visual Studio 2012 için kimlik ve erişim uzantısının nasıl yapılandırılacağı açıklanmaktadır. Bu uzantı STS uç ile iletişim kurmak için uygulamanızın yapılandırma işlemini otomatikleştirir.  
  
#### <a name="to-install-the-identity-and-access-extension"></a>Kimlik ve erişim uzantıyı yüklemek için  
  
1.  Visual Studio'yu yönetici olarak yükseltilmiş modda başlatın.  
  
2.  Visual Studio'da sırasıyla **Araçları** tıklatıp **Uzantı Yöneticisi**. **Uzantı Yöneticisi** penceresi görüntülenir.  
  
3.  İçinde **Uzantı Yöneticisi**, tıklatın **çevrimiçi uzantıları** sol menüden seçip **Visual Studio Galerisi**.  
  
4.  Sağ üst köşesindeki **Uzantı Yöneticisi**, arama *kimlik ve erişim*.  
  
5.  **Kimlik ve erişim** öğesi, arama sonuçlarında görünür. Onu tıklayın ve ardından **karşıdan**.  
  
6.  **Yükleyip** iletişim kutusu görüntülenir. Lisans şartlarını kabul ediyorsanız, tıklatın **yükleme**.  
  
7.  Zaman **kimlik ve erişim** uzantı yükleme tamamlandı, Visual Studio'yu Yönetici modunda yeniden başlatın.  
  
## <a name="step-2--create-a-relying-party-aspnet-application"></a>Adım 2 – bir bağlı olan taraf ASP.NET uygulaması oluşturma  
 Bu adım, bir bağlı olan taraf WIF ile tümleştirecek ASP.NET Web Forms uygulaması oluşturmayı açıklar.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Basit bir ASP.NET uygulaması oluşturmak için  
  
1.  Visual Studio'yu başlatın ve tıklatın **dosya**, **yeni**ve ardından **proje**.  
  
2.  İçinde **yeni proje** penceresinde tıklatın **ASP.NET Web Forms uygulaması**.  
  
3.  İçinde **adı**, girin `TestApp` ve basın **Tamam**.  
  
## <a name="step-3--enable-local-development-sts-to-authenticate-users"></a>Adım 3 – kullanıcıların kimliklerini doğrulamak için etkinleştir yerel geliştirme STS  
 Bu adım, uygulamanızda yerel geliştirme STS etkinleştirmeyi açıklar. Visual Studio için kimlik ve erişim uzantısını kullanarak yerel geliştirme STS etkinleştirilir.  
  
#### <a name="to-enable-local-development-sts-in-your-aspnet-application"></a>ASP.NET uygulamanızı yerel geliştirme STS etkinleştirmek için  
  
1.  Visual Studio'da sağ **TestApp** altında proje **Çözüm Gezgini**seçeneğini belirleyip **kimlik ve erişim**.  
  
2.  **Kimlik ve erişim** penceresi görüntülenir. Altında **sağlayıcıları**seçin **yerel geliştirme STS ile uygulamanızı Test**, ardından **Uygula**.  
  
## <a name="step-4--modify-your-aspnet-application-to-display-sign-in-status"></a>4. adım – oturum durumunu görüntülemek için ASP.NET uygulamanızın değiştirme  
 Bu adım, geçerli kullanıcının oturum açtığı olup olmadığını dinamik olarak görüntülemek için ASP.NET uygulamanızın değiştirmeyi açıklar. STS sağlayıcınız yapılandırıldıktan sonra WIF gelen talepleri işler. Şimdi kimlik doğrulaması sonucu görüntülemek için uygulamanızın kod yapılandırmanız gerekir.  
  
#### <a name="to-display-sign-in-status"></a>Oturum durumunu görüntülemek için  
  
1.  Visual Studio'da açın **Default.aspx** altında dosya **TestApp** projesi.  
  
2.  Varolan biçimlendirmede Değiştir **Default.aspx** aşağıdaki biçimlendirme dosyasıyla:  
  
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
  
3.  Kaydet **Default.aspx**ve kendi kod adlı dosyanın arkasındaki açın **Default.aspx.cs**.  
  
    > [!NOTE]
    >  **Default.aspx.cs** altındaki gizlenebilir **Default.aspx** Çözüm Gezgini'nde. Varsa **Default.aspx.cs** görünür durumda değilse genişletin **Default.aspx** yanında üçgen tıklayarak.  
  
4.  Varolan kodla **Default.aspx.cs** aşağıdaki kod ile:  
  
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
  
5.  Kaydet **Default.aspx.cs**ve uygulama oluşturun.  
  
## <a name="step-5--test-the-integration-between-wif-and-your-aspnet-application"></a>5. adım – WIF ve ASP.NET uygulamanızın arasında tümleştirme Test  
 Bu adım, WIF ve ASP.NET uygulamanızın arasında tümleştirme test nasıl açıklar.  
  
#### <a name="to-test-the-integration-between-wif-and-aspnet"></a>WIF ve ASP.NET arasında tümleştirme sınamak için  
  
1.  Visual Studio'da basın **F5** uygulamanızı hata ayıklama başlatılamıyor. Herhangi bir hata bulunursa, yeni bir tarayıcı penceresi açılır.  
  
2.  Tarayıcı sessizce isteğiniz STS yönlendirir ve Default.aspx sayfasında açılır fark edebilirsiniz. WIF düzgün şekilde yapılandırılmışsa, aşağıdaki metni görüntüle sitesini görmeniz gerekir: **", oturumunuz"**.
