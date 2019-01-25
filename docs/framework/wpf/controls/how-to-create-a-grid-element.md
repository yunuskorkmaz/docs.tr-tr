---
title: 'Nasıl yapılır: Kılavuz Öğesi Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], creating [WPF], grid instance
ms.assetid: b2f07626-9df8-43b8-8d36-492f3cb42837
ms.openlocfilehash: b5bb9572b6a34b21208a8d8c0583068873772aae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54726605"
---
# <a name="how-to-create-a-grid-element"></a>Nasıl yapılır: Kılavuz Öğesi Oluşturma
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir örneğini oluşturup kullanacağınızı gösterilmektedir <xref:System.Windows.Controls.Grid> kullanarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] veya kod. Bu örnek, üç kullanır <xref:System.Windows.Controls.ColumnDefinition> nesneleri ve üç <xref:System.Windows.Controls.RowDefinition> dokuz sahip bir kılavuz oluşturmak için hücreleri gibi çalışma nesneleri. Her hücre içeren bir <xref:System.Windows.Controls.TextBlock> verileri ve üst satırı temsil eden öğe içeren bir <xref:System.Windows.Controls.TextBlock> ile <xref:System.Windows.Controls.Grid.ColumnSpan%2A> özellik uygulandı. Her bir hücresinde sınırları gösterilecek <xref:System.Windows.Controls.Grid.ShowGridLines%2A> özelliği etkin hale getirilir.  
  
 [!code-csharp[Grid#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Grid/CSharp/Grid_Code.cs#3)]
 [!code-vb[Grid#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Grid/VisualBasic/grid_vb.vb#3)]
 [!code-xaml[Grid#3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Grid/XAML/default.xaml#3)]  
  
  Her iki yöntemle de aynı, bir aşağıdaki gibi benzer bir kullanıcı arabirimi oluşturur.

  ![üç sütuna bozuk bir kılavuz içeren bir WPF kullanıcı arabirimi ekran gösterilmektedir.  Başlık '2018 ürünleri üst satırdaki tüm sütunlar kapsayan sevk' taşıyan ve üç sütunu her satış rakamlarını ile belirli bir Çeyreğin için vardır.  Metin iletisi iki sütun kapsayan en alttaki sahip ' toplam birimler: 300,000'](./media/how-to-create-a-grid-element/how-to-create-a-grid-element.png)
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Controls.Grid>
- [Panellere Genel Bakış](../../../../docs/framework/wpf/controls/panels-overview.md)
