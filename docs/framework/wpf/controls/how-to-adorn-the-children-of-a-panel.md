---
title: 'Nasıl yapılır: Panelin Alt Öğelerini Donatma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], binding to children of Panels
- Panel control [WPF], binding adorners to children
ms.assetid: 4cc9b972-b472-4e5c-bdf3-3702d7fbb1f5
ms.openlocfilehash: 739ccaa0273e66c4650c35217a1156d64336dbbb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923520"
---
# <a name="how-to-adorn-the-children-of-a-panel"></a>Nasıl yapılır: Panelin Alt Öğelerini Donatma
Bu örnekte, bir donatıcının, belirtilen <xref:System.Windows.Controls.Panel>bir alt öğeye programlı bir şekilde nasıl bağlanacağı gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Bir donatıcıyı a <xref:System.Windows.Controls.Panel>'nın alt öğelerine bağlamak için şu adımları izleyin:  
  
1. Yeni <xref:System.Windows.Documents.AdornerLayer> bir nesne bildirin ve alt öğeleri `static` donatılacak olan öğe için bir donatıcı katmanı bulmak üzere <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> yöntemini çağırın.  
  
2. Üst öğenin alt öğelerini numaralandırın ve her bir alt öğeye bir <xref:System.Windows.Documents.AdornerLayer.Add%2A> donatıcı bağlamak için yöntemini çağırın.  
  
 Aşağıdaki örnek bir SimpleCircleAdorner (yukarıda gösterilen) <xref:System.Windows.Controls.StackPanel> adlı bir *myStackPanel*alt öğesine bağlar.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
> [!NOTE]
> Bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] donatıcıyı başka bir öğeye bağlamak için kullanılması şu anda desteklenmiyor.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Donatıcılara Genel Bakış](adorners-overview.md)
