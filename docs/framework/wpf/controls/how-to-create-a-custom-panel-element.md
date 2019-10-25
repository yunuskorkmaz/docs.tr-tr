---
title: 'Nasıl yapılır: Özel Panel Öğesi Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF]
- custom Panel elements [WPF]
ms.assetid: e0df4f1e-8c07-4e86-89a3-e22acfffdc2a
ms.openlocfilehash: 31edc75114c5dad613e5b65e7d8b051e2c3713af
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799138"
---
# <a name="how-to-create-a-custom-panel-element"></a><span data-ttu-id="35c76-102">Nasıl yapılır: Özel Panel Öğesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="35c76-102">How to: Create a Custom Panel Element</span></span>
## <a name="example"></a><span data-ttu-id="35c76-103">Örnek</span><span class="sxs-lookup"><span data-stu-id="35c76-103">Example</span></span>  
 <span data-ttu-id="35c76-104">Bu örnek, <xref:System.Windows.Controls.Panel> öğesinin varsayılan düzen davranışının nasıl geçersiz kılınacağını ve <xref:System.Windows.Controls.Panel>türetilen özel düzen öğelerinin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="35c76-104">This example shows how to override the default layout behavior of the <xref:System.Windows.Controls.Panel> element and create custom layout elements that are derived from <xref:System.Windows.Controls.Panel>.</span></span>  
  
 <span data-ttu-id="35c76-105">Örnek, alt öğeleri iki sabit kodlanmış x ve y koordinatlarına göre konumlandırır `PlotPanel`adlı basit bir özel <xref:System.Windows.Controls.Panel> öğesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="35c76-105">The example defines a simple custom <xref:System.Windows.Controls.Panel> element called `PlotPanel`, which positions child elements according to two hard-coded x- and y-coordinates.</span></span> <span data-ttu-id="35c76-106">Bu örnekte, `x` ve `y` her ikisi de `50`olarak ayarlanmıştır; Bu nedenle, tüm alt öğeler x ve y eksenlerinde bu konumda konumlandırılır.</span><span class="sxs-lookup"><span data-stu-id="35c76-106">In this example, `x` and `y` are both set to `50`; therefore, all child elements are positioned at that location on the x and y axes.</span></span>  
  
 <span data-ttu-id="35c76-107">Özel <xref:System.Windows.Controls.Panel> davranışları uygulamak için, örnek <xref:System.Windows.FrameworkElement.MeasureOverride%2A> ve <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> yöntemlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="35c76-107">To implement custom <xref:System.Windows.Controls.Panel> behaviors, the example uses the <xref:System.Windows.FrameworkElement.MeasureOverride%2A> and <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> methods.</span></span> <span data-ttu-id="35c76-108">Her yöntem alt öğeleri konumlandırmak ve işlemek için gereken <xref:System.Windows.Size> verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="35c76-108">Each method returns the <xref:System.Windows.Size> data that is necessary to position and render child elements.</span></span>  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="35c76-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35c76-109">See also</span></span>

- <xref:System.Windows.Controls.Panel>
- [<span data-ttu-id="35c76-110">Panellere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="35c76-110">Panels Overview</span></span>](panels-overview.md)
