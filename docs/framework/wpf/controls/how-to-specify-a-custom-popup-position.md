---
title: 'Nasıl yapılır: Özel Açılan Pencerenin Konumunu Belirtin'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
ms.openlocfilehash: b61ab6ab02d65d0549941b0055f7aef480d7d644
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54726799"
---
# <a name="how-to-specify-a-custom-popup-position"></a><span data-ttu-id="baf0b-102">Nasıl yapılır: Özel Açılan Pencerenin Konumunu Belirtin</span><span class="sxs-lookup"><span data-stu-id="baf0b-102">How to: Specify a Custom Popup Position</span></span>
<span data-ttu-id="baf0b-103">Bu örnek için özel bir konum belirtmek nasıl gösterir bir <xref:System.Windows.Controls.Primitives.Popup> denetimi <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliği <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="baf0b-103">This example shows how to specify a custom position for a <xref:System.Windows.Controls.Primitives.Popup> control when the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="baf0b-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="baf0b-104">Example</span></span>  
 <span data-ttu-id="baf0b-105">Zaman <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliği <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>, <xref:System.Windows.Controls.Primitives.Popup> tanımlanmış bir örneğini çağırır <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> temsilci.</span><span class="sxs-lookup"><span data-stu-id="baf0b-105">When the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>, the <xref:System.Windows.Controls.Primitives.Popup> calls a defined instance of the <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate.</span></span> <span data-ttu-id="baf0b-106">Bu temsilci hedef alanın sol üst ve sol üst köşesine göre olan olası noktaları kümesini döndürür <xref:System.Windows.Controls.Primitives.Popup>.</span><span class="sxs-lookup"><span data-stu-id="baf0b-106">This delegate returns a set of possible points that are relative to the top left corner of the target area and the top left corner of the <xref:System.Windows.Controls.Primitives.Popup>.</span></span> <span data-ttu-id="baf0b-107"><xref:System.Windows.Controls.Primitives.Popup> Yerleştirme en iyi görünürlük sağlayan bir noktada gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="baf0b-107">The <xref:System.Windows.Controls.Primitives.Popup> placement occurs at the point that provides the best visibility.</span></span>  
  
 <span data-ttu-id="baf0b-108">Aşağıdaki örnek, konumunu tanımlamak gösterilmiştir bir <xref:System.Windows.Controls.Primitives.Popup> ayarlayarak <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliğini <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="baf0b-108">The following example shows how to define the position of a <xref:System.Windows.Controls.Primitives.Popup> by setting the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span> <span data-ttu-id="baf0b-109">Ayrıca nasıl oluşturulup atanacağını gösterir bir <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> konumlandırmak için temsilci <xref:System.Windows.Controls.Primitives.Popup>.</span><span class="sxs-lookup"><span data-stu-id="baf0b-109">It also shows how to create and assign a <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate in order to position the <xref:System.Windows.Controls.Primitives.Popup>.</span></span>  <span data-ttu-id="baf0b-110">İki geri çağırma temsilcisini döndürür <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="baf0b-110">The callback delegate returns two <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> objects.</span></span>  <span data-ttu-id="baf0b-111">Varsa <xref:System.Windows.Controls.Primitives.Popup> ilk konumunda bir ekranın kenarı tarafından gizleniyor <xref:System.Windows.Controls.Primitives.Popup> ikinci konumuna yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="baf0b-111">If the <xref:System.Windows.Controls.Primitives.Popup> is hidden by a screen edge at the first position, the <xref:System.Windows.Controls.Primitives.Popup> is placed at the second position.</span></span>  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 <span data-ttu-id="baf0b-112">Tam bir örnek için bkz. [açılan pencere yerleştirme örnek](https://go.microsoft.com/fwlink/?LinkID=160032).</span><span class="sxs-lookup"><span data-stu-id="baf0b-112">For the complete sample, see [Popup Placement Sample](https://go.microsoft.com/fwlink/?LinkID=160032).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baf0b-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="baf0b-113">See also</span></span>
- <xref:System.Windows.Controls.Primitives.Popup>
- [<span data-ttu-id="baf0b-114">Açılan Pencereye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="baf0b-114">Popup Overview</span></span>](../../../../docs/framework/wpf/controls/popup-overview.md)
- [<span data-ttu-id="baf0b-115">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="baf0b-115">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)
