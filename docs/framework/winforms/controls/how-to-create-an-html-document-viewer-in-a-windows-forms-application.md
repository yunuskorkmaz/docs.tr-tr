---
title: Windows Forms uygulamasında HTML belge Görüntüleyicisi oluşturma
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebBrowser control [Windows Forms], creating an HTML document viewer
- document viewers
- Windows Forms, creating document viewers
ms.assetid: 6a6338fe-f7ee-4f5e-9d8f-0465c57e9039
ms.openlocfilehash: 913bc86af034645b4b8cf3d69da4c9def58fc19c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732839"
---
# <a name="how-to-create-an-html-document-viewer-in-a-windows-forms-application"></a>Nasıl yapılır: Bir Windows Forms Uygulamasında HTML Belge Görüntüleyicisi Oluşturma
<xref:System.Windows.Forms.WebBrowser> denetimini, bir Internet Web tarayıcısının tüm işlevselliğini sağlamaksızın HTML belgelerini görüntüleyip yazdırmak için kullanabilirsiniz. Bu, HTML 'nin biçimlendirme özelliğinden yararlanmak istediğinizde, ancak kullanıcılarınızın güvenilmeyen Web denetimleri veya olası kötü amaçlı betik kodu içerebilen rastgele Web sayfaları yüklemesini istemediğinizde yararlıdır. <xref:System.Windows.Forms.WebBrowser> denetimin yeteneklerini bu şekilde kısıtlamak isteyebilirsiniz, örneğin, bunu bir HTML e-posta Görüntüleyicisi olarak kullanmak veya uygulamanızda HTML biçimli yardım sağlamak için kullanabilirsiniz.  
  
### <a name="to-create-an-html-document-viewer"></a>HTML belge Görüntüleyicisi oluşturmak için  
  
1. <xref:System.Windows.Forms.WebBrowser> denetiminin bu dosya üzerinde bırakılan dosyaları açmasını engellemek için <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> özelliğini `false` olarak ayarlayın.  
  
     [!code-csharp[WebBrowserMisc#20](~/samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#20)]
     [!code-vb[WebBrowserMisc#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#20)]  
  
2. <xref:System.Windows.Forms.WebBrowser.Url%2A> özelliğini görüntülenecek ilk dosyanın konumuna ayarlayın.  
  
     [!code-csharp[WebBrowserMisc#21](~/samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#21)]
     [!code-vb[WebBrowserMisc#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#21)]  
  
## <a name="compiling-the-code"></a>Kod Derleme  
 Bu örnek şunları gerektirir:  
  
- `webBrowser1`adlı <xref:System.Windows.Forms.WebBrowser> denetim.  
  
- `System` ve `System.Windows.Forms` derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>
- <xref:System.Windows.Forms.WebBrowser.Url%2A>
- [WebBrowser Denetimine Genel Bakış](webbrowser-control-overview.md)
- [WebBrowser Güvenliği](webbrowser-security.md)
- [Nasıl yapılır: WebBrowser Denetimi ile URL'ye Gitme](how-to-navigate-to-a-url-with-the-webbrowser-control.md)
- [Nasıl yapılır: Bir WebBrowser Denetimi ile Yazdırma](how-to-print-with-a-webbrowser-control.md)
