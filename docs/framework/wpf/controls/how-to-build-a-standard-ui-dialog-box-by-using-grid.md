---
title: 'Nasıl yapılır: Kılavuz Kullanarak Standart UI İletişim Kutusu Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], creating
- Grid control [WPF], creating [WPF], dialog box
ms.assetid: d6ac3d51-844b-4d29-96d8-81a696a7b960
ms.openlocfilehash: 68c9653e616388374aad2ad33ac7dab68446241d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923415"
---
# <a name="how-to-build-a-standard-ui-dialog-box-by-using-grid"></a>Nasıl yapılır: Kılavuz Kullanarak Standart UI İletişim Kutusu Oluşturma
Bu örnek, [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] <xref:System.Windows.Controls.Grid> öğesini kullanarak bir standart iletişim kutusu oluşturmayı gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Windows işletim sistemindeki **Çalıştır** iletişim kutusu gibi bir iletişim kutusu oluşturur.  
  
 Örnek bir <xref:System.Windows.Controls.Grid> oluşturur ve beş sütun ve dört <xref:System.Windows.Controls.RowDefinition> satır tanımlamak için <xref:System.Windows.Controls.ColumnDefinition> ve sınıflarını kullanır.  
  
 Daha sonra bu örnek, iletişim kutusunda <xref:System.Windows.Controls.Image>bulunan `RunIcon.png`görüntüyü göstermek için bir, ekler ve konumlandırır. Görüntü, <xref:System.Windows.Controls.Grid> (sol üst köşenin) ilk sütununa ve satırına yerleştirilir.  
  
 Sonra, örnek ilk sütuna bir <xref:System.Windows.Controls.TextBlock> öğe ekler ve ilk satırın kalan sütunlarını kapsar. **Açık** metin kutusunu <xref:System.Windows.Controls.TextBlock> göstermek için ilk sütundaki ikinci satıra bir öğe ekler. Veri <xref:System.Windows.Controls.TextBlock> girişi alanını temsil eden aşağıdaki bir.  
  
 Son olarak, örnek, son <xref:System.Windows.Controls.Button> satıra, **Tamam**, **iptal**ve **Gözden** geçirme olaylarını temsil eden üç öğe ekler.  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.GridUnitType>
- [Panellere Genel Bakış](panels-overview.md)
- [Nasıl Yapılır Konuları](grid-how-to-topics.md)
