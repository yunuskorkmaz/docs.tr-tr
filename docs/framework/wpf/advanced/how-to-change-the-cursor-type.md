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
ms.openlocfilehash: 26fc2584381307612c40b615f169902089d9d1f0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543399"
---
# <a name="how-to-change-the-cursor-type"></a>Nasıl yapılır: İmleç Türünü Değiştirme
Bu örnek nasıl değiştirileceğini gösterir <xref:System.Windows.Input.Cursor> uygulama ve belirli bir öğe için fare işaretçisi.  
  
 Bu örnek oluşan bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosya ve dosyanın arkasındaki kod.  
  
## <a name="example"></a>Örnek  
 Oluşan kullanıcı arayüzü oluşturulur bir <xref:System.Windows.Controls.ComboBox> istenen seçmek için <xref:System.Windows.Input.Cursor>, bir çift <xref:System.Windows.Controls.RadioButton> imleç değişiklik yalnızca tek bir öğe için geçerlidir tüm uygulama için geçerlidir gerekmediğini belirlemek üzere nesneleri ve bir <xref:System.Windows.Controls.Border> Yeni imlecin uygulandığı öğe olduğu.  
  
 [!code-xaml[cursors#ChangeCursorsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 Aşağıdaki arka plan kodu oluşturur bir <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> imleç türü olarak değiştiğinde çağrılan olay işleyicisi <xref:System.Windows.Controls.ComboBox>.  Switch deyimi filtreler imleç adı ve kümelerini <xref:System.Windows.FrameworkElement.Cursor%2A> özelliği <xref:System.Windows.Controls.Border> adlı *DisplayArea*.  
  
 İmleç Değiştir "Tüm uygulamayı", ayarlarsanız <xref:System.Windows.Input.Mouse.OverrideCursor%2A> özelliği ayarlanmış <xref:System.Windows.FrameworkElement.Cursor%2A> özelliği <xref:System.Windows.Controls.Border> denetim.  Bu, tüm uygulama için değiştirmek için imleci zorlar.  
  
 [!code-csharp[cursors#ChangeCursorsSample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Girişe Genel Bakış](../../../../docs/framework/wpf/advanced/input-overview.md)
