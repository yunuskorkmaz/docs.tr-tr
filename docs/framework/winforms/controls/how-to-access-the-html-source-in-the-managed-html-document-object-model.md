---
title: "Nasıl yapılır: Yönetilen HTML Belgesi Nesne Modelinde HTML Kaynağına Erişme"
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
- managed HTML DOM
- HTML [Windows Forms], accessing in Windows Forms
ms.assetid: 53db79fa-8a5e-448e-88c2-f54ace3860b6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b0c4f894c3d9178f1dc32f7c99481a7daf565511
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-access-the-html-source-in-the-managed-html-document-object-model"></a>Nasıl yapılır: Yönetilen HTML Belgesi Nesne Modelinde HTML Kaynağına Erişme
<xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> Ve <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> özellikleri <xref:System.Windows.Forms.WebBrowser> denetimi döndürmek geçerli belgenin HTML ilk görüntülendiği zaman var gibi. Ancak, yöntem ve özellik çağrılarını kullanarak sayfa değiştirirseniz <xref:System.Windows.Forms.HtmlElement.AppendChild%2A> ve <xref:System.Windows.Forms.HtmlElement.InnerHtml%2A>, bu değişiklikleri çağırdığınızda görünmez <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> ve <xref:System.Windows.Forms.WebBrowser.DocumentText%2A>. DOM için en güncel HTML kaynağını almak için çağırmalısınız <xref:System.Windows.Forms.HtmlElement.OuterHtml%2A> HTML öğesi özelliği.  
  
 Aşağıdaki yordamda, dinamik kaynak almak ve ayrı kısayol menüsünde görüntülemek gösterilmiştir.  
  
### <a name="retrieving-the-dynamic-source-with-the-outerhtml-property"></a>Dinamik kaynak OuterHtml özelliğiyle alınıyor  
  
1.  Yeni bir Windows Forms uygulaması oluşturma. Tek bir başlangıç <xref:System.Windows.Forms.Form>ve bunu `Form1`.  
  
2.  Ana bilgisayar <xref:System.Windows.Forms.WebBrowser> kontrol Windows Forms uygulaması'nda ve adlandırın `WebBrowser1`. Daha fazla bilgi için bkz: [nasıl yapılır: bir Windows Forms uygulamasına Web tarayıcısı yetenekleri ekleme](../../../../docs/framework/winforms/controls/how-to-add-web-browser-capabilities-to-a-windows-forms-application.md).  
  
3.  İkinci bir oluşturma <xref:System.Windows.Forms.Form> adlı uygulamanızda `CodeForm`.  
  
4.  Ekleme bir <xref:System.Windows.Forms.RichTextBox> denetimini `CodeForm` ve kendi <xref:System.Windows.Forms.Control.Dock%2A> özelliğine `Fill`.  
  
5.  Bir ortak özellik oluşturma `CodeForm` adlı `Code`.  
  
     [!code-csharp[DisplayWebBrowserCode#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/CodeForm.cs#1)]
     [!code-vb[DisplayWebBrowserCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/CodeForm.vb#1)]  
  
6.  Ekleme bir <xref:System.Windows.Forms.Button> adlı Denetim `Button1` için <xref:System.Windows.Forms.Form>ve izlemek <xref:System.Windows.Forms.Control.Click> olay. Olayları izleme hakkında daha fazla bilgi için bkz: [olayları](../../../../docs/standard/events/index.md).  
  
7.  Aşağıdaki kodu ekleyin <xref:System.Windows.Forms.Control.Click> olay işleyicisi.  
  
     [!code-csharp[DisplayWebBrowserCode#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/Form1.cs#2)]
     [!code-vb[DisplayWebBrowserCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/Form1.vb#2)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Her zaman değerini test <xref:System.Windows.Forms.WebBrowser.Document%2A> bunu almak denemeden önce. Geçerli sayfa tamamlanmazsa yüklenirken, <xref:System.Windows.Forms.WebBrowser.Document%2A> veya bir veya daha fazla alt nesneleri başlatılmamış olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen HTML Belgesi Nesne Modelini Kullanma](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)  
 [WebBrowser Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)
