---
title: 'Nasıl yapılır: Özel Açılan Pencere Konumu Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
ms.openlocfilehash: dc516f0eb1cfcbac6662497eb4019041eefec2a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61911215"
---
# <a name="how-to-specify-a-custom-popup-position"></a><span data-ttu-id="e6d78-102">Nasıl yapılır: Özel Açılan Pencere Konumu Belirtme</span><span class="sxs-lookup"><span data-stu-id="e6d78-102">How to: Specify a Custom Popup Position</span></span>
<span data-ttu-id="e6d78-103">Bu örnek için özel bir konum belirtmek nasıl gösterir bir <xref:System.Windows.Controls.Primitives.Popup> denetimi <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliği <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="e6d78-103">This example shows how to specify a custom position for a <xref:System.Windows.Controls.Primitives.Popup> control when the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6d78-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="e6d78-104">Example</span></span>  
 <span data-ttu-id="e6d78-105">Zaman <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliği <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>, <xref:System.Windows.Controls.Primitives.Popup> tanımlanmış bir örneğini çağırır <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> temsilci.</span><span class="sxs-lookup"><span data-stu-id="e6d78-105">When the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>, the <xref:System.Windows.Controls.Primitives.Popup> calls a defined instance of the <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate.</span></span> <span data-ttu-id="e6d78-106">Bu temsilci hedef alanın sol üst ve sol üst köşesine göre olan olası noktaları kümesini döndürür <xref:System.Windows.Controls.Primitives.Popup>.</span><span class="sxs-lookup"><span data-stu-id="e6d78-106">This delegate returns a set of possible points that are relative to the top left corner of the target area and the top left corner of the <xref:System.Windows.Controls.Primitives.Popup>.</span></span> <span data-ttu-id="e6d78-107"><xref:System.Windows.Controls.Primitives.Popup> Yerleştirme en iyi görünürlük sağlayan bir noktada gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="e6d78-107">The <xref:System.Windows.Controls.Primitives.Popup> placement occurs at the point that provides the best visibility.</span></span>  
  
 <span data-ttu-id="e6d78-108">Aşağıdaki örnek, konumunu tanımlamak gösterilmiştir bir <xref:System.Windows.Controls.Primitives.Popup> ayarlayarak <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliğini <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="e6d78-108">The following example shows how to define the position of a <xref:System.Windows.Controls.Primitives.Popup> by setting the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span> <span data-ttu-id="e6d78-109">Ayrıca nasıl oluşturulup atanacağını gösterir bir <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> konumlandırmak için temsilci <xref:System.Windows.Controls.Primitives.Popup>.</span><span class="sxs-lookup"><span data-stu-id="e6d78-109">It also shows how to create and assign a <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate in order to position the <xref:System.Windows.Controls.Primitives.Popup>.</span></span>  <span data-ttu-id="e6d78-110">İki geri çağırma temsilcisini döndürür <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="e6d78-110">The callback delegate returns two <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> objects.</span></span>  <span data-ttu-id="e6d78-111">Varsa <xref:System.Windows.Controls.Primitives.Popup> ilk konumunda bir ekranın kenarı tarafından gizleniyor <xref:System.Windows.Controls.Primitives.Popup> ikinci konumuna yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e6d78-111">If the <xref:System.Windows.Controls.Primitives.Popup> is hidden by a screen edge at the first position, the <xref:System.Windows.Controls.Primitives.Popup> is placed at the second position.</span></span>  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 <span data-ttu-id="e6d78-112">Tam bir örnek için bkz. [açılan pencere yerleştirme örnek](https://go.microsoft.com/fwlink/?LinkID=160032).</span><span class="sxs-lookup"><span data-stu-id="e6d78-112">For the complete sample, see [Popup Placement Sample](https://go.microsoft.com/fwlink/?LinkID=160032).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6d78-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6d78-113">See also</span></span>

- <xref:System.Windows.Controls.Primitives.Popup>
- [<span data-ttu-id="e6d78-114">Açılan Pencereye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e6d78-114">Popup Overview</span></span>](popup-overview.md)
- [<span data-ttu-id="e6d78-115">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="e6d78-115">How-to Topics</span></span>](popup-how-to-topics.md)
