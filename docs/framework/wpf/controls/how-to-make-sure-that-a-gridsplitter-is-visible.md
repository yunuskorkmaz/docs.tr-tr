---
title: "Nasıl yapılır: Bir GridSplitter'ın Görünür Olduğundan Emin Olma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: GridSplitter control [WPF], ensuring visibility of
ms.assetid: 0a62a964-89c8-48f0-9023-5df721a8cf47
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b7587a093b2b43856a05693bb785a0465211782
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-sure-that-a-gridsplitter-is-visible"></a><span data-ttu-id="bc12f-102">Nasıl yapılır: Bir GridSplitter'ın Görünür Olduğundan Emin Olma</span><span class="sxs-lookup"><span data-stu-id="bc12f-102">How to: Make Sure That a GridSplitter Is Visible</span></span>
<span data-ttu-id="bc12f-103">Bu örnek emin olmak nasıl gösterir bir <xref:System.Windows.Controls.GridSplitter> denetim, diğer denetimlerinde gizli bir <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="bc12f-103">This example shows how to make sure a <xref:System.Windows.Controls.GridSplitter> control is not hidden by the other controls in a <xref:System.Windows.Controls.Grid>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc12f-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="bc12f-104">Example</span></span>  
 <span data-ttu-id="bc12f-105"><xref:System.Windows.Controls.Panel.Children%2A> , Bir <xref:System.Windows.Controls.Grid> denetim işaretleme veya kod tanımlanan sırada işlenir.</span><span class="sxs-lookup"><span data-stu-id="bc12f-105">The <xref:System.Windows.Controls.Panel.Children%2A> of a <xref:System.Windows.Controls.Grid> control are rendered in the order that they are defined in markup or code.</span></span> <span data-ttu-id="bc12f-106"><xref:System.Windows.Controls.GridSplitter>denetimler gizli diğer denetimler tarafından bunları son öğeleri olarak tanımlamıyorsa <xref:System.Windows.Controls.Panel.Children%2A> koleksiyonu veya diğer verin, daha yüksek denetimleri <xref:System.Windows.Controls.Panel.ZIndexProperty>.</span><span class="sxs-lookup"><span data-stu-id="bc12f-106"><xref:System.Windows.Controls.GridSplitter> controls can be hidden by other controls if you do not define them as the last elements in the <xref:System.Windows.Controls.Panel.Children%2A> collection or if you give other controls a higher <xref:System.Windows.Controls.Panel.ZIndexProperty>.</span></span>  
  
 <span data-ttu-id="bc12f-107">Önlemek için gizli <xref:System.Windows.Controls.GridSplitter> denetimleri, aşağıdakilerden birini yapın.</span><span class="sxs-lookup"><span data-stu-id="bc12f-107">To prevent hidden <xref:System.Windows.Controls.GridSplitter> controls, do one of the following.</span></span>  
  
-   <span data-ttu-id="bc12f-108">Olduğundan emin olun <xref:System.Windows.Controls.GridSplitter> denetimleridir son <xref:System.Windows.Controls.Panel.Children%2A> eklenen <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="bc12f-108">Make sure that <xref:System.Windows.Controls.GridSplitter> controls are the last <xref:System.Windows.Controls.Panel.Children%2A> added to the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="bc12f-109">Aşağıdaki örnekte gösterildiği <xref:System.Windows.Controls.GridSplitter> son öğesi olarak <xref:System.Windows.Controls.Panel.Children%2A> koleksiyonu <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="bc12f-109">The following example shows the <xref:System.Windows.Controls.GridSplitter> as the last element in the <xref:System.Windows.Controls.Panel.Children%2A> collection of the <xref:System.Windows.Controls.Grid>.</span></span>  
  
 [!code-xaml[GridSplitterSnips#GridSplitterLastChild](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterlastchild)]  
  
-   <span data-ttu-id="bc12f-110">Ayarlama <xref:System.Windows.Controls.Panel.ZIndexProperty> üzerinde <xref:System.Windows.Controls.GridSplitter> , aksi takdirde Gizle denetimden daha yüksek olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bc12f-110">Set the <xref:System.Windows.Controls.Panel.ZIndexProperty> on the <xref:System.Windows.Controls.GridSplitter> to be higher than a control that would otherwise hide it.</span></span> <span data-ttu-id="bc12f-111">Aşağıdaki örnek verir <xref:System.Windows.Controls.GridSplitter> daha yüksek denetim <xref:System.Windows.Controls.Panel.ZIndexProperty> daha <xref:System.Windows.Controls.Button> denetim.</span><span class="sxs-lookup"><span data-stu-id="bc12f-111">The following example gives the <xref:System.Windows.Controls.GridSplitter> control a higher <xref:System.Windows.Controls.Panel.ZIndexProperty> than the <xref:System.Windows.Controls.Button> control.</span></span>  
  
 [!code-xaml[GridSplitterSnips#GridSplitterZIndex](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterzindex)]  
  
-   <span data-ttu-id="bc12f-112">Aksi takdirde Gizle denetiminde kenar boşluklarını ayarlama <xref:System.Windows.Controls.GridSplitter> böylece <xref:System.Windows.Controls.GridSplitter> sunulur.</span><span class="sxs-lookup"><span data-stu-id="bc12f-112">Set margins on the control that would otherwise hide the <xref:System.Windows.Controls.GridSplitter> so that the <xref:System.Windows.Controls.GridSplitter> is exposed.</span></span> <span data-ttu-id="bc12f-113">Aşağıdaki örnek, aksi takdirde kaplama bir denetim ve Gizle kenar boşluklarını ayarlar <xref:System.Windows.Controls.GridSplitter>.</span><span class="sxs-lookup"><span data-stu-id="bc12f-113">The following example sets margins on a control that would otherwise overlay and hide the <xref:System.Windows.Controls.GridSplitter>.</span></span>  
  
 [!code-xaml[GridSplitterSnips#GridSplitterMargin](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplittermargin)]  
  
## <a name="see-also"></a><span data-ttu-id="bc12f-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bc12f-114">See Also</span></span>  
 <xref:System.Windows.Controls.GridSplitter>  
 [<span data-ttu-id="bc12f-115">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="bc12f-115">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
