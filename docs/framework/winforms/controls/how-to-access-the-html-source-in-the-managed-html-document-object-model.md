---
title: 'Nasıl yapılır: Yönetilen HTML Belgesi Nesne Modelinde HTML Kaynağına Erişme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- managed HTML DOM
- HTML [Windows Forms], accessing in Windows Forms
ms.assetid: 53db79fa-8a5e-448e-88c2-f54ace3860b6
ms.openlocfilehash: f2306e3405aa0ff37060d987bdc82b58fbaa7784
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59345566"
---
# <a name="how-to-access-the-html-source-in-the-managed-html-document-object-model"></a>Nasıl yapılır: Yönetilen HTML Belgesi Nesne Modelinde HTML Kaynağına Erişme
<xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> Ve <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> özellikleri <xref:System.Windows.Forms.WebBrowser> denetim önce görüntülenen edildiğinde bulunduğu gibi geçerli belgenin HTML döndürür. Ancak, yöntem ve özellik çağrılarını gibi kullanarak sayfayı değiştirirseniz <xref:System.Windows.Forms.HtmlElement.AppendChild%2A> ve <xref:System.Windows.Forms.HtmlElement.InnerHtml%2A>, çağırdığınızda bu değişiklikleri görünmez <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> ve <xref:System.Windows.Forms.WebBrowser.DocumentText%2A>. DOM için en güncel HTML kaynağını almak için çağırmalıdır <xref:System.Windows.Forms.HtmlElement.OuterHtml%2A> HTML öğesi özelliği.  
  
 Aşağıdaki yordam, dinamik kaynak almak ve ayrı kısayol menüsünde görüntüleme gösterilmektedir.  
  
### <a name="retrieving-the-dynamic-source-with-the-outerhtml-property"></a>Dinamik kaynak Outerhtml'i özelliğiyle alınıyor  
  
1. Yeni bir Windows Forms uygulaması oluşturun. Tek bir başlangıç <xref:System.Windows.Forms.Form>ve onu çağırmak `Form1`.  
  
2. Konak <xref:System.Windows.Forms.WebBrowser> Windows Forms uygulaması'nda denetim ve adlandırın `WebBrowser1`. Daha fazla bilgi için [nasıl yapılır: Bir Windows Forms uygulamasına Web tarayıcısı yetenekleri ekleme](how-to-add-web-browser-capabilities-to-a-windows-forms-application.md).  
  
3. Bir saniye oluşturun <xref:System.Windows.Forms.Form> adlı uygulamanızdaki `CodeForm`.  
  
4. Ekleme bir <xref:System.Windows.Forms.RichTextBox> denetimini `CodeForm` ve kendi <xref:System.Windows.Forms.Control.Dock%2A> özelliğini `Fill`.  
  
5. Ortak bir özellik oluşturmak `CodeForm` adlı `Code`.  
  
     [!code-csharp[DisplayWebBrowserCode#1](~/samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/CodeForm.cs#1)]
     [!code-vb[DisplayWebBrowserCode#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/CodeForm.vb#1)]  
  
6. Ekleme bir <xref:System.Windows.Forms.Button> adlı Denetim `Button1` için <xref:System.Windows.Forms.Form>ve izlemek için <xref:System.Windows.Forms.Control.Click> olay. Olayları izleme hakkında daha fazla bilgi için bkz [olayları](../../../standard/events/index.md).  
  
7. Aşağıdaki kodu ekleyin <xref:System.Windows.Forms.Control.Click> olay işleyicisi.  
  
     [!code-csharp[DisplayWebBrowserCode#2](~/samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/Form1.cs#2)]
     [!code-vb[DisplayWebBrowserCode#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/Form1.vb#2)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Değeri her zaman test <xref:System.Windows.Forms.WebBrowser.Document%2A> onu işlemeden önce. Geçerli sayfa tamamlanmazsa yükleniyor, <xref:System.Windows.Forms.WebBrowser.Document%2A> ya da bir veya daha fazla alt nesneleri başlatılmamış olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen HTML Belgesi Nesne Modelini Kullanma](using-the-managed-html-document-object-model.md)
- [WebBrowser Denetimine Genel Bakış](webbrowser-control-overview.md)
