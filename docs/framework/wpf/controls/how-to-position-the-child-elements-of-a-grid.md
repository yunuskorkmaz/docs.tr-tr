---
title: 'Nasıl yapılır: Bir Kılavuzun Alt Öğelerini Konumlandırma'
description: Alt öğeleri konumlandırmak için bir Windows Presentation Foundation kılavuzunda tanımlanan get ve set yöntemlerini nasıl kullanacağınızı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
ms.openlocfilehash: 926d223097dd21dd0292c9523903b4be8aba8ba9
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167398"
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a>Nasıl yapılır: Bir Kılavuzun Alt Öğelerini Konumlandırma
Bu örnek, <xref:System.Windows.Controls.Grid> alt öğeleri konumlandırmak için üzerinde tanımlanan get ve set yöntemlerinin nasıl kullanılacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Windows.Controls.Grid> `grid1` üç sütun ve üç satır içeren bir üst öğe () tanımlar. Bir alt <xref:System.Windows.Shapes.Rectangle> öğe ( `rect1` ) <xref:System.Windows.Controls.Grid> sütun konumu sıfır, satır konumu sıfır olarak eklenir. <xref:System.Windows.Controls.Button>öğeleri, içindeki öğesini yeniden konumlandırmak için çağrılabilecek yöntemleri temsil eder <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.Controls.Grid> . Kullanıcı bir düğmeye tıkladığında ilgili yöntem etkinleştirilir.  
  
 [!code-xaml[gridGetSetMethods](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml)]  
  
 Aşağıdaki kod arkasındaki örnek, düğme olaylarının işlediği yöntemleri işler <xref:System.Windows.Controls.Primitives.ButtonBase.Click> . Örnek, <xref:System.Windows.Controls.TextBlock> yeni özellik değerlerini dizeler olarak çıkarmak için ilgili Get yöntemlerini kullanan öğelere bu yöntem çağrılarını yazar.  
  
 [!code-csharp[gridGetSetMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
 İşte tamamlanan sonuç!

 ![bir ekran görüntüsü, iki sütunlu bir WPF Kullanıcı arabirimini gösterir ve sağ tarafta 3 x 3 ızgara bulunur ve sol tarafta, kılavuzun sütunları ve satırları arasında renkli bir dikdörtgeni taşıma düğmeleri vardır](././media/grid-methods-sample.png)
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.Grid>
- [Panellere Genel Bakış](panels-overview.md)
