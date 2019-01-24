---
title: WebBrowser Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- WebBrowser
helpviewer_keywords:
- WebBrowser control [Windows Forms], about
- Web pages [Windows Forms], displaying in applications
ms.assetid: 6e3e1cc2-9c48-4136-9659-e99e4e60b7e9
ms.openlocfilehash: 919098fd5eb6578b91a7b44cf99ba3aef9076081
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610987"
---
# <a name="webbrowser-control-overview"></a>WebBrowser Denetimine Genel Bakış
<xref:System.Windows.Forms.WebBrowser> Denetim WebBrowser ActiveX denetimi yönetilen sarmalayıcı sağlar. Yönetilen sarmalayıcı Windows Forms istemci uygulamalarınızı Web sayfaları görüntülemenizi sağlar. Kullanabileceğiniz <xref:System.Windows.Forms.WebBrowser> Internet Explorer Web uygulamanızı veya gözatma işlevselliği çoğaltmak için denetimi, varsayılan Internet Explorer işlevini devre dışı bırakın ve basit bir HTML belge Görüntüleyicisi denetimi kullanın. DHTML tabanlı kullanıcı arabirimi öğeleri formunuza eklemek ve içinde barındırılan olgu gizlemek için denetimi de kullanabilirsiniz <xref:System.Windows.Forms.WebBrowser> denetimi. Bu yaklaşım, Web denetimleri Windows Forms denetimlerinde Tek bir uygulama ile sorunsuzca birleştirin sağlar.  
  
## <a name="frequently-used-properties-methods-and-events"></a>Sık kullanılan özellikler, yöntemler ve olaylar  
 <xref:System.Windows.Forms.WebBrowser> Çeşitli özellikleri, yöntemleri ve Internet Explorer'ın bulunan denetim uygulamak için kullanabileceğiniz olaylar denetime sahiptir. Örneğin, kullanabileceğiniz `Navigate` adres çubuğu uygulamak için yöntemi ve `GoBack`, `GoForward`, `Stop`, ve `Refresh` gezinti düğmeleri araç çubuğunda uygulamaya yönelik yöntemleri. İşleyebilirsiniz `Navigated` değeriyle adres çubuğuna güncelleştirilecek olay `Url` özelliği ve değerini başlık çubuğuyla `DocumentTitle` özelliği.  
  
 Kendi uygulamanızın içinde sayfa içeriği oluşturmak istiyorsanız, ayarlayabileceğiniz `DocumentText` özelliği. HTML belge nesne modeli (DOM) ile biliyorsanız geçerli Web sayfasının içeriğini de işleyebilirsiniz `Document` özelliği. Bu özellik ile depolayın ve dosyalar arasında gezinmek yerine bellek belgeleri değiştirin.  
  
 `Document` Özelliği de sağlar, Web sayfası betiği yazma kodu, istemci uygulama kodundan uygulanan yöntemleri çağırın. İstemci uygulama kodunuzun betik kodunuz içinden erişmek için `ObjectForScripting` özelliği. Belirttiğiniz nesnesi betik kodunuzu tarafından erişilebilen `window.external` nesne.  
  
|Ad|Açıklama|  
|----------|-----------------|  
|<xref:System.Windows.Forms.WebBrowser.Document%2A> Özelliği|Geçerli Web sayfasının HTML belge nesne modeli (DOM) yönetilen erişim sağlayan bir nesne alır.|  
|<xref:System.Windows.Forms.WebBrowser.DocumentCompleted> Olay|Bir Web sayfasının yüklenmesi tamamlandığında gerçekleşir.|  
|<xref:System.Windows.Forms.WebBrowser.DocumentText%2A> Özelliği|İçeriğini alır veya HTML geçerli Web sayfasının ayarlar.|  
|<xref:System.Windows.Forms.WebBrowser.DocumentTitle%2A> Özelliği|Geçerli Web sayfasının başlığını alır.|  
|<xref:System.Windows.Forms.WebBrowser.GoBack%2A> Yöntemi|Önceki sayfaya geçmişinde gezinir.|  
|<xref:System.Windows.Forms.WebBrowser.GoForward%2A> Yöntemi|Sonraki sayfaya geçmişinde gezinir.|  
|<xref:System.Windows.Forms.WebBrowser.Navigate%2A> Yöntemi|Belirtilen URL'ye gider.|  
|<xref:System.Windows.Forms.WebBrowser.Navigating> Olay|İptal edilecek eylem etkinleştirme Gezinti başlamadan önce gerçekleşir.|  
|<xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> Özelliği|Alır veya ayarlar Web sayfası betiği yazma kodu, uygulamanız ile iletişim kurmak için kullanabileceğiniz bir nesne.|  
|<xref:System.Windows.Forms.WebBrowser.Print%2A> Yöntemi|Geçerli Web sayfasını yazdırır.|  
|<xref:System.Windows.Forms.WebBrowser.Refresh%2A> Yöntemi|Geçerli Web sayfasını yeniden yükler.|  
|<xref:System.Windows.Forms.WebBrowser.Stop%2A> Yöntemi|Geçerli Gezinti durdurur ve dinamik sayfa öğeleri ses ve animasyon gibi durur.|  
|<xref:System.Windows.Forms.WebBrowser.Url%2A> Özelliği|Alır veya ayarlar geçerli Web sayfasının URL'si. Bu özelliği ayarlamak, yeni URL'yi denetime gider.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowserDocumentCompletedEventArgs>
- <xref:System.Windows.Forms.WebBrowserDocumentCompletedEventHandler>
- <xref:System.Windows.Forms.WebBrowserEncryptionLevel>
- <xref:System.Windows.Forms.WebBrowserNavigatedEventArgs>
- <xref:System.Windows.Forms.WebBrowserNavigatedEventHandler>
- <xref:System.Windows.Forms.WebBrowserNavigatingEventArgs>
- <xref:System.Windows.Forms.WebBrowserNavigatingEventHandler>
- <xref:System.Windows.Forms.WebBrowserProgressChangedEventArgs>
- <xref:System.Windows.Forms.WebBrowserReadyState>
- <xref:System.Windows.Forms.WebBrowserRefreshOption>
- [Nasıl yapılır: WebBrowser denetimi ile URL'ye gitme](../../../../docs/framework/winforms/controls/how-to-navigate-to-a-url-with-the-webbrowser-control.md)
- [Nasıl yapılır: WebBrowser denetimi ile yazdırma](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)
- [Nasıl yapılır: Bir Windows Forms uygulamasına Web tarayıcısı yetenekleri ekleme](../../../../docs/framework/winforms/controls/how-to-add-web-browser-capabilities-to-a-windows-forms-application.md)
- [Nasıl yapılır: Bir Windows Forms uygulamasında HTML belge Görüntüleyicisi oluşturma](../../../../docs/framework/winforms/controls/how-to-create-an-html-document-viewer-in-a-windows-forms-application.md)
- [Nasıl yapılır: DHTML koduyla istemci uygulaması kodu arasında iki yönlü iletişim uygulamak](../../../../docs/framework/winforms/controls/implement-two-way-com-between-dhtml-and-client.md)
- [WebBrowser Güvenliği](../../../../docs/framework/winforms/controls/webbrowser-security.md)
