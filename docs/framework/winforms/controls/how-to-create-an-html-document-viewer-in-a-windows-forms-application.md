---
title: 'Nasıl yapılır: Bir Windows Forms uygulamasında HTML belge Görüntüleyicisi oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebBrowser control [Windows Forms], creating an HTML document viewer
- document viewers
- Windows Forms, creating document viewers
ms.assetid: 6a6338fe-f7ee-4f5e-9d8f-0465c57e9039
ms.openlocfilehash: a25d8bf413614ae71676335c0c8e672caadbf885
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717758"
---
# <a name="how-to-create-an-html-document-viewer-in-a-windows-forms-application"></a>Nasıl yapılır: Bir Windows Forms uygulamasında HTML belge Görüntüleyicisi oluşturma
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
- [Nasıl yapılır: WebBrowser denetimi ile URL'ye gitme](how-to-navigate-to-a-url-with-the-webbrowser-control.md)
- [Nasıl yapılır: WebBrowser denetimi ile yazdırma](how-to-print-with-a-webbrowser-control.md)
