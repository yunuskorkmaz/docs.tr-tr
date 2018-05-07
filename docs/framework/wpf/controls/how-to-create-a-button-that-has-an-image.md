---
title: 'Nasıl yapılır: Görüntüsü Bulunan bir Düğme Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Button controls [WPF], creating
ms.assetid: 607a193c-4098-4dd8-8dc0-51256cec2020
ms.openlocfilehash: 9fb871aa39461329654c0289f00bd3080a633913
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-button-that-has-an-image"></a>Nasıl yapılır: Görüntüsü Bulunan bir Düğme Oluşturma
Bu örnek, bir resim eklemek gösterilmiştir bir <xref:System.Windows.Controls.Button>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte iki oluşturur <xref:System.Windows.Controls.Button> kontrol eder. Bir <xref:System.Windows.Controls.Button> metni içeren ve diğeri bir görüntü içerir. Örneğin proje klasörün bir alt veri adlı bir klasöre görüntüdür. Bir kullanıcı tıkladığında <xref:System.Windows.Controls.Button> görüntü, arka plan ve diğer metin olan <xref:System.Windows.Controls.Button> değiştirin.  
  
 Bu örnekte <xref:System.Windows.Controls.Button> denetleyen biçimlendirme kullanarak ancak kod yazmak için kullandığı <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay işleyicileri.  
  
 [!code-xaml[BtnColor#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml#4)]  
  
 [!code-csharp[BtnColor#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml.cs#6)]
 [!code-vb[BtnColor#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BtnColor/VisualBasic/Pane1.xaml.vb#6)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Denetimler](../../../../docs/framework/wpf/controls/index.md)  
 [Denetim Kitaplığı](../../../../docs/framework/wpf/controls/control-library.md)
