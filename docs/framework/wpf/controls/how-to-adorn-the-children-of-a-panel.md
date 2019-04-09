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
ms.openlocfilehash: e96e1772794a1594d97e1a0109d944d23515468d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100892"
---
# <a name="how-to-adorn-the-children-of-a-panel"></a>Nasıl yapılır: Panelin Alt Öğelerini Donatma
Bu örnekte, program aracılığıyla belirli bir alt öğelere donatıcıyı bağlama işlemi gösterilmektedir <xref:System.Windows.Controls.Panel>.  
  
## <a name="example"></a>Örnek  
 Alt öğeye bir donatıcı bağlama için bir <xref:System.Windows.Controls.Panel>, şu adımları izleyin:  
  
1.  Yeni bir <xref:System.Windows.Documents.AdornerLayer> nesne ve çağrı `static`<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> alt öğeleri olan donatılmış için öğeye bir donatıcı katmanı bulmak için yöntemi.  
  
2.  Çağrı ve üst öğenin alt öğelerini numaralandırın <xref:System.Windows.Documents.AdornerLayer.Add%2A> her alt öğeye bir donatıcı bağlama için yöntemi.  
  
 Aşağıdaki örnek SimpleCircleAdorner (yukarıda alt için gösterilen) bağlanır bir <xref:System.Windows.Controls.StackPanel> adlı *myStackPanel*.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
> [!NOTE]
>  Kullanarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] başka bir öğeye bir donatıcı bağlamak için şu anda desteklenmiyor.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Donatıcılara Genel Bakış](adorners-overview.md)
