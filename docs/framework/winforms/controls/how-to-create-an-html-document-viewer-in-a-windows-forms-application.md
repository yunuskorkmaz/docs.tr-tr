---
title: "Nasıl yapılır: Bir Windows Forms Uygulamasında HTML Belge Görüntüleyicisi Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebBrowser control [Windows Forms], creating an HTML document viewer
- document viewers
- Windows Forms, creating document viewers
ms.assetid: 6a6338fe-f7ee-4f5e-9d8f-0465c57e9039
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e06fbfde68c0d02a94f8c7e4657e2907cd3fa7eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [WebBrowser denetimine genel bakış](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)  
 [WebBrowser güvenliği](../../../../docs/framework/winforms/controls/webbrowser-security.md)  
 [Nasıl yapılır: WebBrowser denetimi ile URL'ye gidin](../../../../docs/framework/winforms/controls/how-to-navigate-to-a-url-with-the-webbrowser-control.md)  
 [Nasıl yapılır: bir WebBrowser denetimi ile yazdırma](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)
