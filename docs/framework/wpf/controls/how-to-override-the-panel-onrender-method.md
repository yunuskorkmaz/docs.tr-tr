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
# <a name="how-to-override-the-panel-onrender-method"></a><span data-ttu-id="d952e-102">Nasıl yapılır: Panel OnRender Yöntemini Geçersiz Kılma</span><span class="sxs-lookup"><span data-stu-id="d952e-102">How to: Override the Panel OnRender Method</span></span>
<span data-ttu-id="d952e-103">Bu örnek, <xref:System.Windows.Controls.Panel.OnRender%2A> bir düzen öğesine özel grafik efektleri <xref:System.Windows.Controls.Panel> eklemek için yönteminin nasıl geçersiz kılınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d952e-103">This example shows how to override the <xref:System.Windows.Controls.Panel.OnRender%2A> method of <xref:System.Windows.Controls.Panel> in order to add custom graphical effects to a layout element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d952e-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="d952e-104">Example</span></span>  
 <span data-ttu-id="d952e-105">Bir işlenmiş panel öğesine grafik etkileri eklemek için yönteminikullanın.<xref:System.Windows.Controls.Panel.OnRender%2A></span><span class="sxs-lookup"><span data-stu-id="d952e-105">Use the <xref:System.Windows.Controls.Panel.OnRender%2A> method in order to add graphical effects to a rendered panel element.</span></span> <span data-ttu-id="d952e-106">Örneğin, özel kenarlık veya arka plan etkileri eklemek için bu yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d952e-106">For example, you can use this method to add custom border or background effects.</span></span> <span data-ttu-id="d952e-107">Bir <xref:System.Windows.Media.DrawingContext> nesne, şekil, metin, resim veya video çizmek için yöntemler sağlayan bir bağımsız değişken olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="d952e-107">A <xref:System.Windows.Media.DrawingContext> object is passed as an argument, which provides methods for drawing shapes, text, images, or videos.</span></span> <span data-ttu-id="d952e-108">Sonuç olarak, bu yöntem panel nesnesinin özelleştirilmesi için faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="d952e-108">As a result, this method is useful for customization of a panel object.</span></span>  
  
 [!code-csharp[LightWeightCustomPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LightWeightCustomPanel/CSharp/OffsetPanel.cs#1)]
 [!code-vb[LightWeightCustomPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LightWeightCustomPanel/visualbasic/offsetpanel.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d952e-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d952e-109">See also</span></span>

- <xref:System.Windows.Controls.Panel>
- [<span data-ttu-id="d952e-110">Panellere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d952e-110">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="d952e-111">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="d952e-111">How-to Topics</span></span>](panel-how-to-topics.md)
