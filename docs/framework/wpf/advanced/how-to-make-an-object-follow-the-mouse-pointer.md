---
title: 'Nasıl yapılır: bir nesnenin fare Işaretçisini Izlemesini sağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- following the mouse pointer (cursor)
- mouse pointer (cursor), making objects follow
- cursor (mouse pointer), making objects follow
ms.assetid: 50b20415-14bc-405c-baf3-2fb254fffde3
ms.openlocfilehash: 4ef3028b6c71b94a593d168ad6570c4aec12b86b
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005073"
---
# <a name="how-to-make-an-object-follow-the-mouse-pointer"></a>Nasıl yapılır: bir nesnenin fare Işaretçisini Izlemesini sağlama
Bu örnek, fare işaretçisi ekranda taşırken bir nesnenin boyutlarının nasıl değiştirileceğini gösterir.  
  
 Örnek, [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ' i ve olay işleyicisini oluşturan arka plan kod dosyasını oluşturan [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyasını içerir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XAML, <xref:System.Windows.Controls.StackPanel> içindeki bir <xref:System.Windows.Shapes.Ellipse> ' den oluşan [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ' ı oluşturur ve <xref:System.Windows.UIElement.MouseMove> olayına yönelik olay işleyicisini ekler.  
  
 [!code-xaml[mouseMoveWithPointer#MouseMoveWithPointerXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml#mousemovewithpointerxaml)]  
  
 Aşağıdaki kod arkasında <xref:System.Windows.UIElement.MouseMove> olay işleyicisi oluşturulur.  Fare işaretçisi taşırken, <xref:System.Windows.Shapes.Ellipse> ' ın yüksekliği ve genişliği artar ve azalır.  
  
 [!code-csharp[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml.cs#mousemovepointergetposition)]
 [!code-vb[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseMoveWithPointer/VisualBasic/Window1.xaml.vb#mousemovepointergetposition)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Girişe genel bakış](input-overview.md)
