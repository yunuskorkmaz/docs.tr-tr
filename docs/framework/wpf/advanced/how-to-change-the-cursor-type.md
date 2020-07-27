---
title: 'Nasıl yapılır: İmleç Türünü Değiştirme'
description: Öğe için fare işaretçisi Imlecini ve Windows Presentation Foundation bir uygulama için değiştirin. Bu örnek XAML ve arka plan kod dosyasından oluşur.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mouse pointer [WPF], cursor type
- cursor (mouse pointer)
ms.assetid: 08c945a7-8ab0-4320-acf3-0b4955a344c2
ms.openlocfilehash: ce0bc290948a0e52e85f76ceb62a330b49fd87ea
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165964"
---
# <a name="how-to-change-the-cursor-type"></a>Nasıl yapılır: İmleç Türünü Değiştirme
Bu örnek, <xref:System.Windows.Input.Cursor> fare işaretçisinin belirli bir öğe ve uygulama için nasıl değiştirileceğini gösterir.  
  
 Bu örnek, bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosya ve arka plan kod dosyasından oluşur.  
  
## <a name="example"></a>Örnek  
 İstenen kullanıcı arabirimi, <xref:System.Windows.Controls.ComboBox> <xref:System.Windows.Input.Cursor> <xref:System.Windows.Controls.RadioButton> imleç değişikliğinin yalnızca tek bir öğe için geçerli olduğunu veya tüm uygulama için geçerli olduğunu ya da <xref:System.Windows.Controls.Border> Yeni imlecin uygulandığı öğeyi belirleyen bir nesne çiftini seçmek için bir, bir dizi nesnenin oluşturulmasını sağlar.  
  
 [!code-xaml[cursors#ChangeCursorsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 Aşağıdaki kod arkasında, <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> imleç türü değiştiğinde çağrılan bir olay işleyicisi oluşturulur <xref:System.Windows.Controls.ComboBox> .  Switch ifadesinin imleci, imleç adı üzerinde filtreler ve <xref:System.Windows.FrameworkElement.Cursor%2A> ' de <xref:System.Windows.Controls.Border> *DisplayArea*olarak adlandırılan özelliği ayarlar.  
  
 İmleç değişikliği "tüm uygulama" olarak ayarlandıysa, <xref:System.Windows.Input.Mouse.OverrideCursor%2A> özelliği <xref:System.Windows.FrameworkElement.Cursor%2A> denetimin özelliğine ayarlanır <xref:System.Windows.Controls.Border> .  Bu, imleci uygulamanın tamamına göre değiştirmeye zorlar.  
  
 [!code-csharp[cursors#ChangeCursorsSample](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Girişe Genel Bakış](input-overview.md)
