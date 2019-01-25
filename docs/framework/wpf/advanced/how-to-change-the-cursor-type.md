---
title: 'Nasıl yapılır: İmleç Türünü Değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mouse pointer [WPF], cursor type
- cursor (mouse pointer)
ms.assetid: 08c945a7-8ab0-4320-acf3-0b4955a344c2
ms.openlocfilehash: 2330cdd3be35dc4e4b555db6401dd55d9946ed1f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745057"
---
# <a name="how-to-change-the-cursor-type"></a>Nasıl yapılır: İmleç Türünü Değiştirme
Bu örnek nasıl değiştirileceğini gösterir <xref:System.Windows.Input.Cursor> uygulama ve belirli bir öğe için fare işaretçisi.  
  
 Bu örnekte oluşan bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyası ve bir arka plan kod dosyasında.  
  
## <a name="example"></a>Örnek  
 Kullanıcı arabirimi oluşturulur, oluşan bir <xref:System.Windows.Controls.ComboBox> istenen seçilecek <xref:System.Windows.Input.Cursor>, bir çift <xref:System.Windows.Controls.RadioButton> imleç değişiklik yalnızca tek bir öğeyi uygular veya tüm uygulama için geçerli belirlemek için nesneleri ve <xref:System.Windows.Controls.Border> Yeni imleç uygulanan bir öğenin olan.  
  
 [!code-xaml[cursors#ChangeCursorsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 Aşağıdaki kod oluşturur bir <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> İmleç türünü değiştiğinde çağrılan olay işleyicisi <xref:System.Windows.Controls.ComboBox>.  Switch deyimi filtreler imleç adı ve kümelerini <xref:System.Windows.FrameworkElement.Cursor%2A> özelliği <xref:System.Windows.Controls.Border> olarak adlandırılmış *DisplayArea*.  
  
 İmleç Değiştir "Tüm uygulamaya" olarak ayarlanmışsa <xref:System.Windows.Input.Mouse.OverrideCursor%2A> özelliği <xref:System.Windows.FrameworkElement.Cursor%2A> özelliği <xref:System.Windows.Controls.Border> denetimi.  Bu, tüm uygulama için değiştirmek için imleç zorlar.  
  
 [!code-csharp[cursors#ChangeCursorsSample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Girişe Genel Bakış](../../../../docs/framework/wpf/advanced/input-overview.md)
