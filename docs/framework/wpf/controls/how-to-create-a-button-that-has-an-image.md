---
title: 'Nasıl yapılır: Görüntüsü Bulunan bir Düğme Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Button controls [WPF], creating
ms.assetid: 607a193c-4098-4dd8-8dc0-51256cec2020
ms.openlocfilehash: cfebe53047531ecddde42a3a0596dfd949629ecd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54682082"
---
# <a name="how-to-create-a-button-that-has-an-image"></a>Nasıl yapılır: Görüntüsü Bulunan bir Düğme Oluşturma
Bu örnek nasıl görüntü ekleneceğini gösterir. bir <xref:System.Windows.Controls.Button>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek iki oluşturur <xref:System.Windows.Controls.Button> kontrol eder. Bir <xref:System.Windows.Controls.Button> metni içeren ve diğeri bir görüntü içerir. Örneğin proje klasörünün alt klasörüdür verileri, adlı bir klasöre görüntüsüdür. Kullanıcı tıkladığında <xref:System.Windows.Controls.Button> görüntü, arka plan ve diğer metin olan <xref:System.Windows.Controls.Button> değiştirin.  
  
 Bu örnekte <xref:System.Windows.Controls.Button> denetleyen biçimlendirme kullanarak ancak kod yazmak için kullandığı <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay işleyicileri.  
  
 [!code-xaml[BtnColor#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml#4)]  
  
 [!code-csharp[BtnColor#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml.cs#6)]
 [!code-vb[BtnColor#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BtnColor/VisualBasic/Pane1.xaml.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Denetimler](../../../../docs/framework/wpf/controls/index.md)
- [Denetim Kitaplığı](../../../../docs/framework/wpf/controls/control-library.md)
