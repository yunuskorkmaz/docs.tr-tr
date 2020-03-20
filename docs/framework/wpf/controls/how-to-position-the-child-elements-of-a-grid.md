---
title: 'Nasıl yapılır: Bir Kılavuzun Alt Öğelerini Konumlandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
ms.openlocfilehash: 44268c32732a9409ea30f028adaa8a2631a06c5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186714"
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a>Nasıl yapılır: Bir Kılavuzun Alt Öğelerini Konumlandırma
Bu örnek, alt öğeleri <xref:System.Windows.Controls.Grid> konumlandırmak için tanımlanan alma ve ayarlama yöntemlerinin nasıl kullanılacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, üç <xref:System.Windows.Controls.Grid> sütun`grid1`ve üç satıriçeren bir üst öğe ( ) tanımlanır. Bir <xref:System.Windows.Shapes.Rectangle> alt`rect1`öğe ( ) <xref:System.Windows.Controls.Grid> sütun konumu sıfır, satır konumu sıfır eklenir. <xref:System.Windows.Controls.Button>öğeleri içinde <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.Controls.Grid>öğeyi yeniden konumlandırmak için çağrılabilir yöntemleri temsil . Bir kullanıcı bir düğmeyi tıklattığında, ilgili yöntem etkinleştirilir.  
  
 [!code-xaml[gridGetSetMethods](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml)]  
  
 Aşağıdaki kod arkası örneği, düğme <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olaylarının yükselttiğini işler. Örnek, ilgili get <xref:System.Windows.Controls.TextBlock> yöntemlerini kullanan elemanlara bu yöntem çağrılarını yeni özellik değerlerini dizeleri olarak çıktıolarak yazar.  
  
 [!code-csharp[gridGetSetMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
 İşte bitmiş sonuç!

 ![ekran görüntüsü iki sütunlu bir WPF kullanıcı arabirimini betimliyor, sağ tarafında 3 x 3 ızgara ve sol tarafta ızgara sütunları ve satırları arasında renkli bir dikdörtgen taşımak için düğmeleri var](././media/grid-methods-sample.png)
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.Grid>
- [Panellere Genel Bakış](panels-overview.md)
