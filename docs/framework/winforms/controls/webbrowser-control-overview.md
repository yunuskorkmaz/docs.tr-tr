---
title: WebBrowser Denetimine Genel Bakış
description: Web denetimlerini tek bir uygulamadaki Windows Forms denetimleriyle sorunsuzca birleştirmek için WebBrowser denetimini nasıl kullanacağınızı öğrenin.
ms.date: 03/30/2017
f1_keywords:
- WebBrowser
helpviewer_keywords:
- WebBrowser control [Windows Forms], about
- Web pages [Windows Forms], displaying in applications
ms.assetid: 6e3e1cc2-9c48-4136-9659-e99e4e60b7e9
ms.openlocfilehash: 6a0548bb0f5905d8f848ab13fb82d32b50caa891
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325743"
---
# <a name="webbrowser-control-overview"></a>WebBrowser Denetimine Genel Bakış
<xref:System.Windows.Forms.WebBrowser>Denetim, WebBrowser ActiveX denetimi için yönetilen bir sarmalayıcı sağlar. Yönetilen sarmalayıcı, Windows Forms istemci uygulamalarınızda Web sayfalarını görüntülemenize olanak sağlar. <xref:System.Windows.Forms.WebBrowser>Uygulamanızda Internet Explorer Web 'e göz atma işlevini yinelemek için denetimi kullanabilir veya varsayılan Internet Explorer işlevselliğini devre dışı bırakabilir ve denetimi Basit BIR HTML belge Görüntüleyicisi olarak kullanabilirsiniz. Formunuza DHTML tabanlı kullanıcı arabirimi öğeleri eklemek ve denetimde barındırıldığından emin olmak için denetimi de kullanabilirsiniz <xref:System.Windows.Forms.WebBrowser> . Bu yaklaşım, Web denetimlerini tek bir uygulamadaki Windows Forms denetimleriyle sorunsuzca birleştirmenize olanak tanır.  
  
## <a name="frequently-used-properties-methods-and-events"></a>Sık kullanılan özellikler, Yöntemler ve olaylar  
 <xref:System.Windows.Forms.WebBrowser>Denetimde, Internet Explorer 'da bulunan denetimleri uygulamak için kullanabileceğiniz çeşitli özellikler, Yöntemler ve olaylar bulunur. Örneğin, bir `Navigate` Adres çubuğunu uygulamak için yöntemini ve `GoBack` `GoForward` `Stop` `Refresh` bir araç çubuğunda gezinti düğmeleri uygulamak için,, ve yöntemlerini kullanabilirsiniz. `Navigated`Adres çubuğunu `Url` özellik değeriyle ve başlık çubuğu ile birlikte güncelleştirmek için olayı idare edebilirsiniz `DocumentTitle` .  
  
 Uygulamanızda kendi sayfa içeriğinizi oluşturmak istiyorsanız `DocumentText` özelliği ayarlayabilirsiniz. HTML belge nesne modeli (DOM) hakkında bilgi sahibiyseniz, özelliği aracılığıyla geçerli Web sayfasının içeriğini de düzenleyebilirsiniz `Document` . Bu özellikle, dosyalar arasında gezinmek yerine belgeleri bellekte saklayabilir ve değiştirebilirsiniz.  
  
 `Document`Özelliği, istemci uygulama kodunuzun Web sayfası betik kodu 'nda uygulanan yöntemleri çağırmanıza de imkan tanır. Komut dosyası kodınızdan istemci uygulama kodunuza erişmek için `ObjectForScripting` özelliği ayarlayın. Belirttiğiniz nesneye, komut dosyası kodunuz tarafından nesne olarak erişilebilir `window.external` .  
  
|Name|Description|  
|----------|-----------------|  
|<xref:System.Windows.Forms.WebBrowser.Document%2A>özelliði|Geçerli Web sayfasının HTML belge nesne modeli 'ne (DOM) yönetilen erişim sağlayan bir nesne alır.|  
|<xref:System.Windows.Forms.WebBrowser.DocumentCompleted>olay|Bir Web sayfası yükleme tamamlandığında gerçekleşir.|  
|<xref:System.Windows.Forms.WebBrowser.DocumentText%2A>özelliði|Geçerli Web sayfasının HTML içeriğini alır veya ayarlar.|  
|<xref:System.Windows.Forms.WebBrowser.DocumentTitle%2A>özelliði|Geçerli Web sayfasının başlığını alır.|  
|<xref:System.Windows.Forms.WebBrowser.GoBack%2A> yöntemi|Geçmişteki bir önceki sayfaya gider.|  
|<xref:System.Windows.Forms.WebBrowser.GoForward%2A> yöntemi|Geçmişteki bir sonraki sayfaya gider.|  
|<xref:System.Windows.Forms.WebBrowser.Navigate%2A> yöntemi|Belirtilen URL 'ye gider.|  
|<xref:System.Windows.Forms.WebBrowser.Navigating>olay|Gezinme başlamadan önce gerçekleşir ve eylemin iptal edilmesine olanak sağlar.|  
|<xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A>özelliði|Web sayfası betik kodunun, uygulamanızla iletişim kurmak için kullanabileceği bir nesne alır veya ayarlar.|  
|<xref:System.Windows.Forms.WebBrowser.Print%2A> yöntemi|Geçerli Web sayfasını yazdırır.|  
|<xref:System.Windows.Forms.WebBrowser.Refresh%2A> yöntemi|Geçerli Web sayfasını yeniden yükler.|  
|<xref:System.Windows.Forms.WebBrowser.Stop%2A> yöntemi|Geçerli gezintiyi durdurur ve sesler ve animasyon gibi dinamik sayfa öğelerini durdurur.|  
|<xref:System.Windows.Forms.WebBrowser.Url%2A>özelliði|Geçerli Web sayfasının URL 'sini alır veya ayarlar. Bu özellik ayarlandığında, denetim yeni URL 'ye gider.|  
  
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
- [Nasıl yapılır: WebBrowser Denetimi ile URL'ye Gitme](how-to-navigate-to-a-url-with-the-webbrowser-control.md)
- [Nasıl yapılır: Bir WebBrowser Denetimi ile Yazdırma](how-to-print-with-a-webbrowser-control.md)
- [Nasıl yapılır: Bir Windows Forms Uygulamasına Web Tarayıcısı Yetenekleri Ekleme](how-to-add-web-browser-capabilities-to-a-windows-forms-application.md)
- [Nasıl yapılır: Bir Windows Forms Uygulamasında HTML Belge Görüntüleyicisi Oluşturma](how-to-create-an-html-document-viewer-in-a-windows-forms-application.md)
- [Nasıl yapılır: DHTML Koduyla İstemci Uygulaması Kodu Arasında İki Yönlü İletişim Gerçekleştirme](implement-two-way-com-between-dhtml-and-client.md)
- [WebBrowser Güvenliği](webbrowser-security.md)
