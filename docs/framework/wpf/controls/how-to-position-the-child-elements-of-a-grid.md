---
title: 'Nasıl yapılır: Bir Kılavuzun Alt Öğelerini Konumlandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
ms.openlocfilehash: c508f45c1ea3d0925503d6fe5600498a0558d5ad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770815"
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a>Nasıl yapılır: Bir Kılavuzun Alt Öğelerini Konumlandırma
Bu örnek, get ve üzerinde tanımlanan yöntemlerini nasıl kullanılacağını gösterir. <xref:System.Windows.Controls.Grid> alt öğeleri konumlandırmak için.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir üst tanımlar <xref:System.Windows.Controls.Grid> öğesi (`grid1`) üç ve üç satır vardır. Bir alt <xref:System.Windows.Shapes.Rectangle> öğesi (`rect1`) eklenir <xref:System.Windows.Controls.Grid> sütun konumu sıfır satır konumunu sıfır. <xref:System.Windows.Controls.Button> öğeleri yeniden konumlandırmak için çağrılan yöntemi temsil <xref:System.Windows.Shapes.Rectangle> öğesiyle <xref:System.Windows.Controls.Grid>. İlgili yöntem, bir kullanıcı bir düğmeyi tıkladığında etkinleştirilir.  
  
 [!code-xaml[gridGetSetMethods](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml)]  
  
 Aşağıdaki arka plan kod örnek yöntemleri işler, düğmeyi <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayları tetikleyebilir. Bu yöntem çağrıları örnek Yazar <xref:System.Windows.Controls.TextBlock> kullanımı ilgili öğeleri al yeni özellik değerlerinin dizeler olarak çıkış yöntemleri.  
  
 [!code-csharp[gridGetSetMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
 Tamamlanmış sonucu geldi!
 
 ![bir WPF kullanıcı arabirimi iki sütunlu bir ekran görüntüsü gösterilmektedir, sağ tarafındaki 3 x 3 kılavuz ve sol kılavuza satırlar ve sütunlar arasında renkli bir dikdörtgen geçmek düğmelerini sahiptir](././media/grid-methods-sample.png) 
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.Grid>
- [Panellere Genel Bakış](panels-overview.md)
