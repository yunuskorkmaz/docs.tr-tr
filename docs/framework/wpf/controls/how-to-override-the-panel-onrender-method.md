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
ms.openlocfilehash: 23c3353e130585ed83726816a467ca73f6aa9152
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666711"
---
# <a name="how-to-override-the-panel-onrender-method"></a>Nasıl yapılır: Panel OnRender Yöntemini Geçersiz Kılma
Bu örnek, <xref:System.Windows.Controls.Panel.OnRender%2A> bir düzen öğesine özel grafik efektleri <xref:System.Windows.Controls.Panel> eklemek için yönteminin nasıl geçersiz kılınacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Bir işlenmiş panel öğesine grafik etkileri eklemek için yönteminikullanın.<xref:System.Windows.Controls.Panel.OnRender%2A> Örneğin, özel kenarlık veya arka plan etkileri eklemek için bu yöntemi kullanabilirsiniz. Bir <xref:System.Windows.Media.DrawingContext> nesne, şekil, metin, resim veya video çizmek için yöntemler sağlayan bir bağımsız değişken olarak geçirilir. Sonuç olarak, bu yöntem panel nesnesinin özelleştirilmesi için faydalıdır.  
  
 [!code-csharp[LightWeightCustomPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LightWeightCustomPanel/CSharp/OffsetPanel.cs#1)]
 [!code-vb[LightWeightCustomPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LightWeightCustomPanel/visualbasic/offsetpanel.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.Panel>
- [Panellere Genel Bakış](panels-overview.md)
- [Nasıl Yapılır Konuları](panel-how-to-topics.md)
