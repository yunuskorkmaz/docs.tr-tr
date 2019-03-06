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
ms.openlocfilehash: 2e778adfb79a64c8f248992aee92de9471906129
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368707"
---
# <a name="how-to-create-a-custom-panel-element"></a><span data-ttu-id="b600b-102">Nasıl yapılır: Özel Panel Öğesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b600b-102">How to: Create a Custom Panel Element</span></span>
## <a name="example"></a><span data-ttu-id="b600b-103">Örnek</span><span class="sxs-lookup"><span data-stu-id="b600b-103">Example</span></span>  
 <span data-ttu-id="b600b-104">Bu örnekte, varsayılan düzen davranışını geçersiz kılmak gösterilmektedir <xref:System.Windows.Controls.Panel> öğesi öğesinden türetilen özel düzen öğelerini oluşturup <xref:System.Windows.Controls.Panel>.</span><span class="sxs-lookup"><span data-stu-id="b600b-104">This example shows how to override the default layout behavior of the <xref:System.Windows.Controls.Panel> element and create custom layout elements that are derived from <xref:System.Windows.Controls.Panel>.</span></span>  
  
 <span data-ttu-id="b600b-105">Örnek, basit bir özel tanımlar <xref:System.Windows.Controls.Panel> adlı öğesi `PlotPanel`, alt öğeleri göre iki sabit kodlanmış x ve y-koordinatlarına yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="b600b-105">The example defines a simple custom <xref:System.Windows.Controls.Panel> element called `PlotPanel`, which positions child elements according to two hard-coded x- and y-coordinates.</span></span> <span data-ttu-id="b600b-106">Bu örnekte, `x` ve `y` hem ayarlamak `50`; bu nedenle, tüm alt öğeleri x ve y yerde konumlandırılır eksenleri.</span><span class="sxs-lookup"><span data-stu-id="b600b-106">In this example, `x` and `y` are both set to `50`; therefore, all child elements are positioned at that location on the x and y axes.</span></span>  
  
 <span data-ttu-id="b600b-107">Özel uygulamak için <xref:System.Windows.Controls.Panel> davranışları örnekte <xref:System.Windows.FrameworkElement.MeasureOverride%2A> ve <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="b600b-107">To implement custom <xref:System.Windows.Controls.Panel> behaviors, the example uses the <xref:System.Windows.FrameworkElement.MeasureOverride%2A> and <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> methods.</span></span> <span data-ttu-id="b600b-108">Her yöntem döndürür <xref:System.Windows.Size> alt öğeleri konumlandırmak ve işlemek gerekli olan veriler.</span><span class="sxs-lookup"><span data-stu-id="b600b-108">Each method returns the <xref:System.Windows.Size> data that is necessary to position and render child elements.</span></span>  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b600b-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b600b-109">See also</span></span>
- <xref:System.Windows.Controls.Panel>
- [<span data-ttu-id="b600b-110">Panellere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b600b-110">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="b600b-111">Özel içerik kaydırma paneli örneği oluşturma</span><span class="sxs-lookup"><span data-stu-id="b600b-111">Create a Custom Content-Wrapping Panel Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159979)
