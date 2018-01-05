---
title: "Nasıl yapılır: Panel OnRender Yöntemini Geçersiz Kılma"
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
f1_keywords:
- overriding OnRender method
- Panel control, overriding OnRender method
- OnRender method
- controls, Panel, overriding OnRender method
helpviewer_keywords:
- overriding OnRender method of Panel control [WPF]
- OnRender method [WPF], overriding
- Panel control [WPF], overriding OnRender method
ms.assetid: 57397834-a085-4e36-90ab-416fad98f341
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 958595cdfa521b372270d6283c7134ef0ba0ef79
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-override-the-panel-onrender-method"></a>Nasıl yapılır: Panel OnRender Yöntemini Geçersiz Kılma
Bu örnek nasıl geçersiz kılınacağını gösterir <xref:System.Windows.Controls.Panel.OnRender%2A> yöntemi <xref:System.Windows.Controls.Panel> düzen öğesine özel grafik efektleri eklemek için.  
  
## <a name="example"></a>Örnek  
 Kullanım <xref:System.Windows.Controls.Panel.OnRender%2A> işlenen panel öğesine grafik efektleri eklemek için yöntem. Örneğin, özel kenarlık veya arka plan efektleri eklemek için bu yöntemi kullanabilirsiniz. A <xref:System.Windows.Media.DrawingContext> nesne çizim şekil, metin, görüntüler veya videolar için yöntemler sağlar bir bağımsız değişken olarak geçirilir. Sonuç olarak, bu yöntem panel nesnesi özelleştirmesi için kullanışlıdır.  
  
 [!code-csharp[LightWeightCustomPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LightWeightCustomPanel/CSharp/OffsetPanel.cs#1)]
 [!code-vb[LightWeightCustomPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LightWeightCustomPanel/visualbasic/offsetpanel.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.Panel>  
 [Panellere Genel Bakış](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Özel Radyal paneli örneği](http://go.microsoft.com/fwlink/?LinkID=159982)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/controls/panel-how-to-topics.md)
