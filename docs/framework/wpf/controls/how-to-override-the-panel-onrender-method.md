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
ms.openlocfilehash: c4539847368c1a5789e99ec92106d17077ed5943
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770844"
---
# <a name="how-to-override-the-panel-onrender-method"></a>Nasıl yapılır: Panel OnRender Yöntemini Geçersiz Kılma
Bu örnek nasıl geçersiz kılınacağını gösterir <xref:System.Windows.Controls.Panel.OnRender%2A> yöntemi <xref:System.Windows.Controls.Panel> özel grafik efektleri düzen öğesine eklemek için.  
  
## <a name="example"></a>Örnek  
 Kullanım <xref:System.Windows.Controls.Panel.OnRender%2A> grafik efektleri işlenen panel öğesine eklemek için yöntemi. Örneğin, özel kenarlık veya arka plan etkileri eklemek için bu yöntemi kullanabilirsiniz. A <xref:System.Windows.Media.DrawingContext> nesne şekiller, metin, görüntü veya videoları çizmek için yöntemler sağlar bir bağımsız değişken olarak geçirilir. Sonuç olarak, bu yöntem bir panel nesnesinin özelleştirme için kullanışlıdır.  
  
 [!code-csharp[LightWeightCustomPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LightWeightCustomPanel/CSharp/OffsetPanel.cs#1)]
 [!code-vb[LightWeightCustomPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LightWeightCustomPanel/visualbasic/offsetpanel.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.Panel>
- [Panellere Genel Bakış](panels-overview.md)
- [Özel Radyal Panel örnek](https://go.microsoft.com/fwlink/?LinkID=159982)
- [Nasıl Yapılır Konuları](panel-how-to-topics.md)
