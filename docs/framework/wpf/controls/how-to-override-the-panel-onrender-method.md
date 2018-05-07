---
title: 'Nasıl yapılır: Panel OnRender Yöntemini Geçersiz Kılma'
ms.date: 03/30/2017
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
ms.openlocfilehash: e591bc195d3b0ba58002bda42ddb3e9ed35d312e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
