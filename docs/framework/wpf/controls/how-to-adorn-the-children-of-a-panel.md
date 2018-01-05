---
title: "Nasıl yapılır: Panelin Alt Öğelerini Donatma"
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
- adorners [WPF], binding to children of Panels
- Panel control [WPF], binding adorners to children
ms.assetid: 4cc9b972-b472-4e5c-bdf3-3702d7fbb1f5
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 70a2c1e7735a6df31a44fce7eb9bb2371acc208b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-adorn-the-children-of-a-panel"></a>Nasıl yapılır: Panelin Alt Öğelerini Donatma
Bu örnek belirtilen bir alt öğeleri için bir donatıcıyı programlı olarak bağlamak nasıl gösterir <xref:System.Windows.Controls.Panel>.  
  
## <a name="example"></a>Örnek  
 Alt öğelerinin donatıcı bağlamak için bir <xref:System.Windows.Controls.Panel>, şu adımları izleyin:  
  
1.  Yeni bir bildirme <xref:System.Windows.Documents.AdornerLayer> nesne ve çağrı `static` <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> alt öğeleri olan donatılacak öğe için donatıcı katmanı bulmak için yöntem.  
  
2.  Çağrı ve üst öğenin alt öğeleri listeleme <xref:System.Windows.Documents.AdornerLayer.Add%2A> donatıcı her alt öğeye bağlamak için yöntem.  
  
 Aşağıdaki örnek bir SimpleCircleAdorner (yukarıda alt öğelerinin gösterilen) bağlanır bir <xref:System.Windows.Controls.StackPanel> adlı *myStackPanel*.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
> [!NOTE]
>  Kullanarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] donatıcı başka bir öğeye bağlamak için şu anda desteklenmiyor.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Donatıcılara Genel Bakış](../../../../docs/framework/wpf/controls/adorners-overview.md)
