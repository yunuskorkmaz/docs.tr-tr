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
ms.openlocfilehash: 1330e20cc4fe7df86e51bebca28e4a71e3108673
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530549"
---
# <a name="how-to-create-an-html-document-viewer-in-a-windows-forms-application"></a>Nasıl yapılır: Bir Windows Forms Uygulamasında HTML Belge Görüntüleyicisi Oluşturma
Kullanabileceğiniz <xref:System.Windows.Forms.WebBrowser> görüntülemek ve Internet Web tarayıcısı tam işlevselliğini sağlamadan HTML belgeleri yazdırmak için denetim. HTML biçimlendirme özelliklerinden yararlanmak istiyor, ancak güvenilmeyen Web denetimleri veya kötü amaçlı kod içerebilen rasgele Web sayfalarını yüklemek için kullanıcılarınızın istemediğiniz zaman yararlıdır. Yeteneğini sınırlamak isteyebilirsiniz <xref:System.Windows.Forms.WebBrowser> kontrol bu şekilde, örneğin, bir HTML e-posta görüntüleyici olarak kullanmak için veya HTML biçimli Yardım uygulamanızda sağlamak için.  
  
### <a name="to-create-an-html-document-viewer"></a>HTML belge Görüntüleyici oluşturmak için  
  
1.  Ayarlama <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> özelliğine `false` önlemek için <xref:System.Windows.Forms.WebBrowser> sürüklediğinizde bırakılan dosyaları açmasını denetim.  
  
     [!code-csharp[WebBrowserMisc#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#20)]
     [!code-vb[WebBrowserMisc#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#20)]  
  
2.  Ayarlama <xref:System.Windows.Forms.WebBrowser.Url%2A> görüntülemek için ilk dosyasının konumu özelliği.  
  
     [!code-csharp[WebBrowserMisc#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#21)]
     [!code-vb[WebBrowserMisc#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#21)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   A <xref:System.Windows.Forms.WebBrowser> adlı Denetim `webBrowser1`.  
  
-   Başvurular `System` ve `System.Windows.Forms` derlemeler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.WebBrowser>  
 <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>  
 <xref:System.Windows.Forms.WebBrowser.Url%2A>  
 [WebBrowser Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)  
 [WebBrowser Güvenliği](../../../../docs/framework/winforms/controls/webbrowser-security.md)  
 [Nasıl yapılır: WebBrowser Denetimi ile URL'ye Gitme](../../../../docs/framework/winforms/controls/how-to-navigate-to-a-url-with-the-webbrowser-control.md)  
 [Nasıl yapılır: Bir WebBrowser Denetimi ile Yazdırma](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)
