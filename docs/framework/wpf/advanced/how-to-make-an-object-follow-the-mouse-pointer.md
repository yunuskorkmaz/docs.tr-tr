---
title: 'Nasıl yapılır: Fare İşaretçisini İzleyen Bir Nesne Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- following the mouse pointer (cursor)
- mouse pointer (cursor), making objects follow
- cursor (mouse pointer), making objects follow
ms.assetid: 50b20415-14bc-405c-baf3-2fb254fffde3
ms.openlocfilehash: 6b86cadba19e82c487be88bcfb08edb51f93c540
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358307"
---
# <a name="how-to-make-an-object-follow-the-mouse-pointer"></a>Nasıl yapılır: Fare İşaretçisini İzleyen Bir Nesne Oluşturma
Bu örnek, ekranda fare işaretçisi hareket ettirildiğinde nesnenin boyutunu değiştirmek nasıl gösterir.  
  
 Örnek içeren bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] oluşturan dosya [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ve arka plan kod dosyası, olay işleyicisi oluşturur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] oluşturur [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], oluşan ve bir <xref:System.Windows.Shapes.Ellipse> içine bir <xref:System.Windows.Controls.StackPanel>ve olay işleyicisi ekler <xref:System.Windows.UIElement.MouseMove> olay.  
  
 [!code-xaml[mouseMoveWithPointer#MouseMoveWithPointerXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml#mousemovewithpointerxaml)]  
  
 Aşağıdaki kod oluşturur <xref:System.Windows.UIElement.MouseMove> olay işleyicisi.  Ne zaman fare işaretçisi hareket yüksekliğini ve genişliğini <xref:System.Windows.Shapes.Ellipse> artırılır ve azaltılır.  
  
 [!code-csharp[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml.cs#mousemovepointergetposition)]
 [!code-vb[mouseMoveWithPointer#MouseMovePointerGetPosition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseMoveWithPointer/VisualBasic/Window1.xaml.vb#mousemovepointergetposition)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Girişe Genel Bakış](input-overview.md)
