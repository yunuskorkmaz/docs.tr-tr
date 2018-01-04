---
title: "Nasıl yapılır: Fare İşaretçisini İzleyen Bir Nesne Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- following the mouse pointer (cursor)
- mouse pointer (cursor), making objects follow
- cursor (mouse pointer), making objects follow
ms.assetid: 50b20415-14bc-405c-baf3-2fb254fffde3
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7571b437c3879e829a11ed81c22dd12a0a1b592b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-an-object-follow-the-mouse-pointer"></a>Nasıl yapılır: Fare İşaretçisini İzleyen Bir Nesne Oluşturma
Bu örnek, fare işaretçisini ekrandaki getirdiğinde bir nesnenin boyutlarını değiştirmek gösterilmektedir.  
  
 Örnek içeren bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] oluşturur dosya [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ve olay işleyicisi oluşturan bir arka plan kod dosyası.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] oluşturur [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], oluşan ve bir <xref:System.Windows.Shapes.Ellipse> içine bir <xref:System.Windows.Controls.StackPanel>ve için olay işleyicisini ekler <xref:System.Windows.UIElement.MouseMove> olay.  
  
 [!code-xaml[mouseMoveWithPointer#MouseMoveWithPointerXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml#mousemovewithpointerxaml)]  
  
 Aşağıdaki arka plan kodu oluşturur <xref:System.Windows.UIElement.MouseMove> olay işleyicisi.  Ne zaman fare işaretçisi hareket yüksekliğini ve genişliğini <xref:System.Windows.Shapes.Ellipse> artırılır ve azaltılır.  
  
 [!code-csharp[mouseMoveWithPointer#MouseMovePointerGetPosition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml.cs#mousemovepointergetposition)]
 [!code-vb[mouseMoveWithPointer#MouseMovePointerGetPosition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/mouseMoveWithPointer/VisualBasic/Window1.xaml.vb#mousemovepointergetposition)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Girişe Genel Bakış](../../../../docs/framework/wpf/advanced/input-overview.md)
