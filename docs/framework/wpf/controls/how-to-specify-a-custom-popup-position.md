---
title: 'Nasıl yapılır: Özel Açılan Pencerenin Konumunu Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
ms.openlocfilehash: 8714cfa4f7e5bb0ca157ee9d551392571303f60e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33551745"
---
# <a name="how-to-specify-a-custom-popup-position"></a><span data-ttu-id="2d5bd-102">Nasıl yapılır: Özel Açılan Pencerenin Konumunu Belirtme</span><span class="sxs-lookup"><span data-stu-id="2d5bd-102">How to: Specify a Custom Popup Position</span></span>
<span data-ttu-id="2d5bd-103">Bu örnek için özel bir konum belirtmek nasıl gösterir bir <xref:System.Windows.Controls.Primitives.Popup> denetimi <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliği ayarlanmış <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="2d5bd-103">This example shows how to specify a custom position for a <xref:System.Windows.Controls.Primitives.Popup> control when the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d5bd-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="2d5bd-104">Example</span></span>  
 <span data-ttu-id="2d5bd-105">Zaman <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliği ayarlanmış <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>, <xref:System.Windows.Controls.Primitives.Popup> tanımlanmış bir örneğini çağırır <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> temsilci.</span><span class="sxs-lookup"><span data-stu-id="2d5bd-105">When the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>, the <xref:System.Windows.Controls.Primitives.Popup> calls a defined instance of the <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate.</span></span> <span data-ttu-id="2d5bd-106">Bu temsilci hedef alanının sol üst ve sol üst köşesine göre olası noktalar kümesini döndürür <xref:System.Windows.Controls.Primitives.Popup>.</span><span class="sxs-lookup"><span data-stu-id="2d5bd-106">This delegate returns a set of possible points that are relative to the top left corner of the target area and the top left corner of the <xref:System.Windows.Controls.Primitives.Popup>.</span></span> <span data-ttu-id="2d5bd-107"><xref:System.Windows.Controls.Primitives.Popup> Yerleştirme en iyi görünürlük sağlayan bir noktada ortaya çıkar.</span><span class="sxs-lookup"><span data-stu-id="2d5bd-107">The <xref:System.Windows.Controls.Primitives.Popup> placement occurs at the point that provides the best visibility.</span></span>  
  
 <span data-ttu-id="2d5bd-108">Aşağıdaki örnek konumunu tanımlamak nasıl gösterir bir <xref:System.Windows.Controls.Primitives.Popup> ayarlayarak <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliğine <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="2d5bd-108">The following example shows how to define the position of a <xref:System.Windows.Controls.Primitives.Popup> by setting the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span> <span data-ttu-id="2d5bd-109">Ayrıca oluşturmak ve atamak nasıl gösterir bir <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> konumlandırmak için temsilci <xref:System.Windows.Controls.Primitives.Popup>.</span><span class="sxs-lookup"><span data-stu-id="2d5bd-109">It also shows how to create and assign a <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate in order to position the <xref:System.Windows.Controls.Primitives.Popup>.</span></span>  <span data-ttu-id="2d5bd-110">Geri çağırma temsilcisini iki döndürür <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="2d5bd-110">The callback delegate returns two <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> objects.</span></span>  <span data-ttu-id="2d5bd-111">Varsa <xref:System.Windows.Controls.Primitives.Popup> ilk konumunda ekran kenarı tarafından gizli <xref:System.Windows.Controls.Primitives.Popup> ikinci konumuna yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="2d5bd-111">If the <xref:System.Windows.Controls.Primitives.Popup> is hidden by a screen edge at the first position, the <xref:System.Windows.Controls.Primitives.Popup> is placed at the second position.</span></span>  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 <span data-ttu-id="2d5bd-112">Tam bir örnek için bkz: [açılan yerleştirme örnek](http://go.microsoft.com/fwlink/?LinkID=160032).</span><span class="sxs-lookup"><span data-stu-id="2d5bd-112">For the complete sample, see [Popup Placement Sample](http://go.microsoft.com/fwlink/?LinkID=160032).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d5bd-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2d5bd-113">See Also</span></span>  
 <xref:System.Windows.Controls.Primitives.Popup>  
 [<span data-ttu-id="2d5bd-114">Açılan Pencereye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2d5bd-114">Popup Overview</span></span>](../../../../docs/framework/wpf/controls/popup-overview.md)  
 [<span data-ttu-id="2d5bd-115">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="2d5bd-115">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)
