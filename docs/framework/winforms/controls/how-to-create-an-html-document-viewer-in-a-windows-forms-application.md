---
title: 'Nasıl yapılır: Bir Windows Forms Uygulamasında HTML Belge Görüntüleyicisi Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebBrowser control [Windows Forms], creating an HTML document viewer
- document viewers
- Windows Forms, creating document viewers
ms.assetid: 6a6338fe-f7ee-4f5e-9d8f-0465c57e9039
ms.openlocfilehash: 0eecefd961aed5408e7d02769056dc551e604b02
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214578"
---
# <a name="how-to-create-an-html-document-viewer-in-a-windows-forms-application"></a>Nasıl yapılır: Bir Windows Forms Uygulamasında HTML Belge Görüntüleyicisi Oluşturma
Kullanabileceğiniz <xref:System.Windows.Forms.WebBrowser> görüntülemek ve bir Internet Web tarayıcısı tam işlevselliğini sağlamadan HTML belge yazdırma için denetimi. HTML biçimlendirme özelliklerinden yararlanmak istiyorsanız ancak kullanıcılarınızın güvenilmeyen Web denetimleri veya kötü amaçlı kod içerebilecek isteğe bağlı Web sayfalarını yüklemek istemiyorsanız bu yararlı olur. Yeteneğini kısıtlamak isteyebilirsiniz <xref:System.Windows.Forms.WebBrowser> denetimi bu şekilde, örneğin, bir HTML e-posta görüntüleyici olarak kullanın veya uygulamanızda HTML biçimli Yardım sağlamak için.  
  
### <a name="to-create-an-html-document-viewer"></a>Bir HTML belge Görüntüleyicisi oluşturma  
  
1.  Ayarlama <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> özelliğini `false` önlemek için <xref:System.Windows.Forms.WebBrowser> sürüklediğinizde bırakılan dosyaları açma denetimi.  
  
     [!code-csharp[WebBrowserMisc#20](~/samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#20)]
     [!code-vb[WebBrowserMisc#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#20)]  
  
2.  Ayarlama <xref:System.Windows.Forms.WebBrowser.Url%2A> özelliğini görüntülenecek ilk dosyasının konumu.  
  
     [!code-csharp[WebBrowserMisc#21](~/samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#21)]
     [!code-vb[WebBrowserMisc#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#21)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   A <xref:System.Windows.Forms.WebBrowser> adlı Denetim `webBrowser1`.  
  
-   Başvurular `System` ve `System.Windows.Forms` derlemeler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>
- <xref:System.Windows.Forms.WebBrowser.Url%2A>
- [WebBrowser Denetimine Genel Bakış](webbrowser-control-overview.md)
- [WebBrowser Güvenliği](webbrowser-security.md)
- [Nasıl yapılır: WebBrowser Denetimi ile URL'ye Gitme](how-to-navigate-to-a-url-with-the-webbrowser-control.md)
- [Nasıl yapılır: Bir WebBrowser Denetimi ile Yazdırma](how-to-print-with-a-webbrowser-control.md)
