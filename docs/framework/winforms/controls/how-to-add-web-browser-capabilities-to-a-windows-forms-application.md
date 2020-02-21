---
title: Uygulamaya Web tarayıcısı yetenekleri ekleme
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
ms.openlocfilehash: 7cb789121f4aa9a1e7cef54f992d0697ce6dfc62
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543579"
---
# <a name="how-to-add-web-browser-capabilities-to-a-windows-forms-application"></a>Windows Forms uygulamasına Web tarayıcısı yetenekleri ekleme

<xref:System.Windows.Forms.WebBrowser> denetimiyle, uygulamanıza Web tarayıcı işlevselliği ekleyebilirsiniz. Denetim varsayılan olarak bir Web tarayıcısı gibi çalışmaktadır. <xref:System.Windows.Forms.WebBrowser.Url%2A> özelliğini ayarlayarak bir başlangıç URL 'SI yükledikten sonra, ileri ' ye tıklayarak veya gezinme geçmişinde geriye doğru ve ileri gitmek için klavye kısayollarını kullanarak gezinebilirsiniz. Varsayılan olarak, sağ tıklama kısayol menüsünde ek tarayıcı işlevlerine erişebilirsiniz. Ayrıca, denetimi üzerine bırakarak yeni belgeler açabilirsiniz. <xref:System.Windows.Forms.WebBrowser> denetim Ayrıca, Internet Explorer 'da bulunanlara benzer kullanıcı arabirimi özelliklerini uygulamak için kullanabileceğiniz çeşitli özelliklere, yöntemlere ve olaylara sahip olabilir.

Aşağıdaki kod örneği, bir adres çubuğunu, tipik tarayıcı düğmelerini, bir **Dosya** menüsünü, bir durum çubuğunu ve geçerli sayfa başlığını görüntüleyen bir başlık çubuğunu uygular.

## <a name="example"></a>Örnek

[!code-cpp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CPP/form1.cpp#0)]
[!code-csharp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CS/form1.cs#0)]
[!code-vb[System.Windows.Forms.WebBrowser#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/VB/form1.vb#0)]
  
## <a name="compile-the-code"></a>Kod derleme

Bu örnek şunları gerektirir:

- `System`, `System.Drawing`ve `System.Windows.Forms` derlemelerine başvurular.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.WebBrowser>
- [WebBrowser Denetimi](webbrowser-control-windows-forms.md)
