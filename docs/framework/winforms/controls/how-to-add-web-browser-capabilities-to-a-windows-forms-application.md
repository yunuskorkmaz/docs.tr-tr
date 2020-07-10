---
title: Uygulamaya Web tarayıcısı yetenekleri ekleme
description: Web tarayıcısı yeteneklerini bir Windows Forms uygulamasına WebBrowser denetimiyle nasıl ekleyeceğinizi öğrenin.
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
ms.openlocfilehash: a5a33961ac8301bda86bb5f34e65ac159308987f
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174555"
---
# <a name="how-to-add-web-browser-capabilities-to-a-windows-forms-application"></a>Windows Forms uygulamasına Web tarayıcısı yetenekleri ekleme

Denetim ile <xref:System.Windows.Forms.WebBrowser> uygulamanıza Web tarayıcı işlevselliği ekleyebilirsiniz. Denetim varsayılan olarak bir Web tarayıcısı gibi çalışmaktadır. Özelliği ayarlayarak bir başlangıç URL 'SI yükledikten sonra <xref:System.Windows.Forms.WebBrowser.Url%2A> , ileri ' ye tıklayarak veya gezinme geçmişi aracılığıyla geriye doğru ve ileri ilerlemek için klavye kısayollarını kullanarak gezinebilirsiniz. Varsayılan olarak, sağ tıklama kısayol menüsünde ek tarayıcı işlevlerine erişebilirsiniz. Ayrıca, denetimi üzerine bırakarak yeni belgeler açabilirsiniz. <xref:System.Windows.Forms.WebBrowser>Denetimde Ayrıca, Internet Explorer 'da bulunanlara benzer kullanıcı arabirimi özelliklerini uygulamak için kullanabileceğiniz çeşitli özellikler, Yöntemler ve olaylar bulunur.

Aşağıdaki kod örneği, bir adres çubuğunu, tipik tarayıcı düğmelerini, bir **Dosya** menüsünü, bir durum çubuğunu ve geçerli sayfa başlığını görüntüleyen bir başlık çubuğunu uygular.

## <a name="example"></a>Örnek

[!code-cpp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CPP/form1.cpp#0)]
[!code-csharp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CS/form1.cs#0)]
[!code-vb[System.Windows.Forms.WebBrowser#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/VB/form1.vb#0)]
  
## <a name="compile-the-code"></a>Kodu derle

Bu örnek şunları gerektirir:

- `System`, `System.Drawing` Ve `System.Windows.Forms` derlemelerinin başvuruları.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.WebBrowser>
- [WebBrowser Denetimi](webbrowser-control-windows-forms.md)
