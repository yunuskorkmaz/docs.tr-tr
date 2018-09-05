---
title: 'Nasıl yapılır: Bir Windows Forms Uygulamasına Web Tarayıcısı Yetenekleri Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- WebBrowser control [Windows Forms], adding Web browser capabilities to your application
- WebBrowser control [Windows Forms], examples
- Web browsers [.NET Framework], adding to Windows Forms
- examples [Windows Forms], WebBrowser control
- Windows Forms, adding Web browser functionality
ms.assetid: 3871f072-b57a-435b-9976-e5da28df04a7
ms.openlocfilehash: 514895d11ba5a9c4ac47538f2d1a9c1d0e9d7995
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43557819"
---
# <a name="how-to-add-web-browser-capabilities-to-a-windows-forms-application"></a>Nasıl yapılır: Bir Windows Forms Uygulamasına Web Tarayıcısı Yetenekleri Ekleme
İle <xref:System.Windows.Forms.WebBrowser> denetimi, Web tarayıcısı işlevselliği uygulamanıza ekleyebilirsiniz. Denetim varsayılan olarak bir Web tarayıcısı gibi çalışır. Bir başlangıç URL'si ayarlayarak yükledikten sonra <xref:System.Windows.Forms.WebBrowser.Url%2A> özelliği köprüleri tıklatarak veya gezinme geçmişinde İleri ve geri taşımak için klavye kısayollarını kullanarak gidebilirsiniz. Varsayılan olarak, ek tarayıcısı işlevselliği sağ kısayol menüsünden erişebilirsiniz. Yeni belgeler, denetimin bırakarak da açabilirsiniz. <xref:System.Windows.Forms.WebBrowser> Denetimi ayrıca çeşitli özellikleri, yöntemleri ve Internet Explorer'da bulunanlar benzer kullanıcı arabirimi özellikleri uygulamak için kullanabileceğiniz olaylar vardır.  
  
 Aşağıdaki kod örneği, bir adres çubuğuna, tipik tarayıcı düğmeleri, uygulayan bir **dosya** menü, durum çubuğu ve geçerli sayfa başlığının görüntüleyen bir başlık çubuğu.  
  
## <a name="example"></a>Örnek  
 [!code-cpp[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CPP/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Başvurular `System,``System.Drawing`, ve `System.Windows.Forms` derlemeler.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.  Ayrıca bkz: [nasıl yapılır: derleme ve çalıştırma bir tam Windows Formları kod örneği kullanarak Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.WebBrowser>  
 [WebBrowser Denetimi](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)
