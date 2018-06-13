---
title: WebBrowser Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- WebBrowser
helpviewer_keywords:
- WebBrowser control [Windows Forms], about
- Web pages [Windows Forms], displaying in applications
ms.assetid: 6e3e1cc2-9c48-4136-9659-e99e4e60b7e9
ms.openlocfilehash: 2e69b71b3e354101d950d6f7011b13fc7c0de030
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540998"
---
# <a name="webbrowser-control-overview"></a>WebBrowser Denetimine Genel Bakış
<xref:System.Windows.Forms.WebBrowser> Denetimi WebBrowser ActiveX denetimi için yönetilen sarmalayıcı sağlar. Yönetilen sarmalayıcı Windows Forms istemci uygulamalarınızda Web sayfaları görüntülemenizi sağlar. Kullanabileceğiniz <xref:System.Windows.Forms.WebBrowser> Internet Explorer Web uygulamanızı veya gözatma işlevselliği çoğaltmak için denetim varsayılan Internet Explorer işlevselliği devre dışı bırakabilir ve basit bir HTML belge görüntüleyici olarak denetimi kullanın. DHTML tabanlı kullanıcı arabirimi öğeleri formunuza eklemek ve içinde barındırılan olgu gizlemek için denetimi de kullanabilirsiniz <xref:System.Windows.Forms.WebBrowser> denetim. Bu yaklaşım, tek bir uygulamada Windows Forms denetimleri ile Web denetimleri sorunsuzca birleştirin olanak tanır.  
  
## <a name="frequently-used-properties-methods-and-events"></a>Sık kullanılan özellikleri, yöntemleri ve olayları  
 <xref:System.Windows.Forms.WebBrowser> Çeşitli özellikleri, yöntemleri ve Internet Explorer'da bulunan denetimler uygulamak için kullanabileceğiniz olaylar denetime sahiptir. Örneğin, kullanabileceğiniz `Navigate` bir adres çubuğuna uygulamak için yöntem ve `GoBack`, `GoForward`, `Stop`, ve `Refresh` gezinti düğmeleri araç çubuğunda uygulamaya yönelik yöntemleri. İşleyebilir `Navigated` adres çubuğuna değeriyle güncelleştirmek için olay `Url` özelliği ve değeriyle başlık çubuğu `DocumentTitle` özelliği.  
  
 Kendi sayfa içeriği, uygulamanızda oluşturmak istiyorsanız, ayarlayabileceğiniz `DocumentText` özelliği. HTML belge nesne modeli (DOM) ile bilginiz varsa, aynı zamanda geçerli Web sayfasının içeriği işleyebileceğiniz `Document` özelliği. Bu özellik ile depolamak ve dosyaların arasında gezinmek yerine bellek belgelerde değiştirin.  
  
 `Document` Özelliği de sağlar betiği yazma kodu istemci uygulama kodunuzdan Web sayfasındaki uygulanan yöntemlerini çağırın. İstemci uygulaması kodu komut dosyası kodunuzdan erişmek için ayarlanmış `ObjectForScripting` özelliği. Nesne betik kodunuzu tarafından erişilebilecek `window.external` nesnesi.  
  
|Ad|Açıklama|  
|----------|-----------------|  
|<xref:System.Windows.Forms.WebBrowser.Document%2A> Özelliği|Geçerli Web sayfasının HTML belge nesne modeli (DOM) yönetilen erişim sağlayan bir nesne alır.|  
|<xref:System.Windows.Forms.WebBrowser.DocumentCompleted> Olay|Bir Web sayfası yüklenmesi tamamlandığında oluşur.|  
|<xref:System.Windows.Forms.WebBrowser.DocumentText%2A> Özelliği|Alır veya HTML geçerli Web sayfasının içeriği ayarlar.|  
|<xref:System.Windows.Forms.WebBrowser.DocumentTitle%2A> Özelliği|Geçerli Web sayfasının başlığını alır.|  
|<xref:System.Windows.Forms.WebBrowser.GoBack%2A> Yöntemi|Geçmiş önceki sayfasına götürür.|  
|<xref:System.Windows.Forms.WebBrowser.GoForward%2A> Yöntemi|Geçmiş sonraki sayfaya gider.|  
|<xref:System.Windows.Forms.WebBrowser.Navigate%2A> Yöntemi|Belirtilen URL'ye gider.|  
|<xref:System.Windows.Forms.WebBrowser.Navigating> Olay|İptal edilecek eylem etkinleştirme Gezinti başlangıcından önceye denk geliyor.|  
|<xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> Özelliği|Nesneyi alır veya Web sayfası betiği yazma kodu, uygulamayla iletişim kurmak için kullanabileceğiniz bir ayarlar.|  
|<xref:System.Windows.Forms.WebBrowser.Print%2A> Yöntemi|Geçerli Web sayfasını yazdırır.|  
|<xref:System.Windows.Forms.WebBrowser.Refresh%2A> Yöntemi|Geçerli Web sayfasını yeniden yükler.|  
|<xref:System.Windows.Forms.WebBrowser.Stop%2A> Yöntemi|Geçerli Gezinti durdurur ve dinamik sayfası öğeleri ses ve animasyon gibi durur.|  
|<xref:System.Windows.Forms.WebBrowser.Url%2A> Özelliği|Alır veya geçerli Web sayfasının URL'sini ayarlar. Bu özelliği ayarlamak yeni URL denetime gider.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.WebBrowser>  
 <xref:System.Windows.Forms.WebBrowserDocumentCompletedEventArgs>  
 <xref:System.Windows.Forms.WebBrowserDocumentCompletedEventHandler>  
 <xref:System.Windows.Forms.WebBrowserEncryptionLevel>  
 <xref:System.Windows.Forms.WebBrowserNavigatedEventArgs>  
 <xref:System.Windows.Forms.WebBrowserNavigatedEventHandler>  
 <xref:System.Windows.Forms.WebBrowserNavigatingEventArgs>  
 <xref:System.Windows.Forms.WebBrowserNavigatingEventHandler>  
 <xref:System.Windows.Forms.WebBrowserProgressChangedEventArgs>  
 <xref:System.Windows.Forms.WebBrowserReadyState>  
 <xref:System.Windows.Forms.WebBrowserRefreshOption>  
 [Nasıl yapılır: WebBrowser Denetimi ile URL'ye Gitme](../../../../docs/framework/winforms/controls/how-to-navigate-to-a-url-with-the-webbrowser-control.md)  
 [Nasıl yapılır: Bir WebBrowser Denetimi ile Yazdırma](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)  
 [Nasıl yapılır: Bir Windows Forms Uygulamasına Web Tarayıcısı Yetenekleri Ekleme](../../../../docs/framework/winforms/controls/how-to-add-web-browser-capabilities-to-a-windows-forms-application.md)  
 [Nasıl yapılır: Bir Windows Forms Uygulamasında HTML Belge Görüntüleyicisi Oluşturma](../../../../docs/framework/winforms/controls/how-to-create-an-html-document-viewer-in-a-windows-forms-application.md)  
 [Nasıl yapılır: DHTML Koduyla İstemci Uygulaması Kodu Arasında İki Yönlü İletişim Gerçekleştirme](../../../../docs/framework/winforms/controls/implement-two-way-com-between-dhtml-and-client.md)  
 [WebBrowser Güvenliği](../../../../docs/framework/winforms/controls/webbrowser-security.md)
