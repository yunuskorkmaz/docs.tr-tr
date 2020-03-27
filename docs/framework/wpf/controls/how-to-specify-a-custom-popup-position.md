---
title: 'Nasıl yapılır: Özel Açılan Pencerenin Konumunu Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
ms.openlocfilehash: ea8d73c51dd018608b95104f00bf341ff434225c
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344959"
---
# <a name="how-to-specify-a-custom-popup-position"></a><span data-ttu-id="1ed1a-102">Nasıl yapılır: Özel Açılan Pencerenin Konumunu Belirtme</span><span class="sxs-lookup"><span data-stu-id="1ed1a-102">How to: Specify a Custom Popup Position</span></span>
<span data-ttu-id="1ed1a-103">Bu örnek, <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özellik . <xref:System.Windows.Controls.Primitives.PlacementMode.Custom></span><span class="sxs-lookup"><span data-stu-id="1ed1a-103">This example shows how to specify a custom position for a <xref:System.Windows.Controls.Primitives.Popup> control when the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ed1a-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="1ed1a-104">Example</span></span>  
 <span data-ttu-id="1ed1a-105"><xref:System.Windows.Controls.Primitives.Popup.Placement%2A> Özellik <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>ayarlandığında, <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> temsilcinin tanımlı bir örneği çağırır.</span><span class="sxs-lookup"><span data-stu-id="1ed1a-105">When the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>, the <xref:System.Windows.Controls.Primitives.Popup> calls a defined instance of the <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate.</span></span> <span data-ttu-id="1ed1a-106">Bu temsilci, hedef alanın sol üst köşesine ve hedef alanın sol üst köşesine göregörebilen olası noktalar kümesini döndürür. <xref:System.Windows.Controls.Primitives.Popup></span><span class="sxs-lookup"><span data-stu-id="1ed1a-106">This delegate returns a set of possible points that are relative to the top left corner of the target area and the top left corner of the <xref:System.Windows.Controls.Primitives.Popup>.</span></span> <span data-ttu-id="1ed1a-107">Yerleşim, <xref:System.Windows.Controls.Primitives.Popup> en iyi görünürlüğü sağlayan noktada gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="1ed1a-107">The <xref:System.Windows.Controls.Primitives.Popup> placement occurs at the point that provides the best visibility.</span></span>  
  
 <span data-ttu-id="1ed1a-108">Aşağıdaki örnek, <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliği . <xref:System.Windows.Controls.Primitives.PlacementMode.Custom></span><span class="sxs-lookup"><span data-stu-id="1ed1a-108">The following example shows how to define the position of a <xref:System.Windows.Controls.Primitives.Popup> by setting the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span> <span data-ttu-id="1ed1a-109">Ayrıca, <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> <xref:System.Windows.Controls.Primitives.Popup>bir temsilciyi konumlandırmak için nasıl oluşturulup atanın caiz olduğunu da gösterir.</span><span class="sxs-lookup"><span data-stu-id="1ed1a-109">It also shows how to create and assign a <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate in order to position the <xref:System.Windows.Controls.Primitives.Popup>.</span></span>  <span data-ttu-id="1ed1a-110">Geri arama temsilcisi <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> iki nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="1ed1a-110">The callback delegate returns two <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> objects.</span></span>  <span data-ttu-id="1ed1a-111"><xref:System.Windows.Controls.Primitives.Popup> İlk konumda bir ekran kenarı tarafından <xref:System.Windows.Controls.Primitives.Popup> gizlenmişse, ikinci konuma yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1ed1a-111">If the <xref:System.Windows.Controls.Primitives.Popup> is hidden by a screen edge at the first position, the <xref:System.Windows.Controls.Primitives.Popup> is placed at the second position.</span></span>  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 <span data-ttu-id="1ed1a-112">Tam örnek için [Popup Yerleştirme Örneği'ne](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS)bakın.</span><span class="sxs-lookup"><span data-stu-id="1ed1a-112">For the complete sample, see [Popup Placement Sample](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ed1a-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ed1a-113">See also</span></span>

- <xref:System.Windows.Controls.Primitives.Popup>
- [<span data-ttu-id="1ed1a-114">Açılan Pencereye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1ed1a-114">Popup Overview</span></span>](popup-overview.md)
- [<span data-ttu-id="1ed1a-115">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="1ed1a-115">How-to Topics</span></span>](popup-how-to-topics.md)
