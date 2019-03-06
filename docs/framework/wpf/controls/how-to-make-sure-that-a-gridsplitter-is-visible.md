---
title: "Nasıl yapılır: Bir GridSplitter'ın Görünür Olduğundan Emin Olma"
ms.date: 03/30/2017
helpviewer_keywords:
- GridSplitter control [WPF], ensuring visibility of
ms.assetid: 0a62a964-89c8-48f0-9023-5df721a8cf47
ms.openlocfilehash: 0e1984241c07a69e2b350a61dc5873716c6fa5df
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375707"
---
# <a name="how-to-make-sure-that-a-gridsplitter-is-visible"></a><span data-ttu-id="f3f53-102">Nasıl yapılır: Bir GridSplitter'ın Görünür Olduğundan Emin Olma</span><span class="sxs-lookup"><span data-stu-id="f3f53-102">How to: Make Sure That a GridSplitter Is Visible</span></span>
<span data-ttu-id="f3f53-103">Bu örnek nasıl emin olunacağı gösterir bir <xref:System.Windows.Controls.GridSplitter> denetim, diğer denetimleri gizli bir <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="f3f53-103">This example shows how to make sure a <xref:System.Windows.Controls.GridSplitter> control is not hidden by the other controls in a <xref:System.Windows.Controls.Grid>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3f53-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="f3f53-104">Example</span></span>  
 <span data-ttu-id="f3f53-105"><xref:System.Windows.Controls.Panel.Children%2A> , Bir <xref:System.Windows.Controls.Grid> denetim işaretleme veya kod içinde tanımlanan sırada işlenir.</span><span class="sxs-lookup"><span data-stu-id="f3f53-105">The <xref:System.Windows.Controls.Panel.Children%2A> of a <xref:System.Windows.Controls.Grid> control are rendered in the order that they are defined in markup or code.</span></span> <span data-ttu-id="f3f53-106"><xref:System.Windows.Controls.GridSplitter> denetimler gizli göre diğer denetimler, bunları son öğeleri olarak tanımlamazsanız <xref:System.Windows.Controls.Panel.Children%2A> koleksiyonu veya diğer verin, daha yüksek bir denetimleri <xref:System.Windows.Controls.Panel.ZIndexProperty>.</span><span class="sxs-lookup"><span data-stu-id="f3f53-106"><xref:System.Windows.Controls.GridSplitter> controls can be hidden by other controls if you do not define them as the last elements in the <xref:System.Windows.Controls.Panel.Children%2A> collection or if you give other controls a higher <xref:System.Windows.Controls.Panel.ZIndexProperty>.</span></span>  
  
 <span data-ttu-id="f3f53-107">Önlemek için gizli <xref:System.Windows.Controls.GridSplitter> denetimleri, aşağıdakilerden birini yapın.</span><span class="sxs-lookup"><span data-stu-id="f3f53-107">To prevent hidden <xref:System.Windows.Controls.GridSplitter> controls, do one of the following.</span></span>  
  
-   <span data-ttu-id="f3f53-108">Emin olun <xref:System.Windows.Controls.GridSplitter> denetimlerdir son <xref:System.Windows.Controls.Panel.Children%2A> eklenen <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="f3f53-108">Make sure that <xref:System.Windows.Controls.GridSplitter> controls are the last <xref:System.Windows.Controls.Panel.Children%2A> added to the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="f3f53-109">Aşağıdaki örnekte gösterildiği <xref:System.Windows.Controls.GridSplitter> içerisindeki son öğe olarak <xref:System.Windows.Controls.Panel.Children%2A> koleksiyonunu <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="f3f53-109">The following example shows the <xref:System.Windows.Controls.GridSplitter> as the last element in the <xref:System.Windows.Controls.Panel.Children%2A> collection of the <xref:System.Windows.Controls.Grid>.</span></span>  
  
 [!code-xaml[GridSplitterSnips#GridSplitterLastChild](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterlastchild)]  
  
-   <span data-ttu-id="f3f53-110">Ayarlama <xref:System.Windows.Controls.Panel.ZIndexProperty> üzerinde <xref:System.Windows.Controls.GridSplitter> Aksi halde gizleyecek bir denetimi yüksek olabilir.</span><span class="sxs-lookup"><span data-stu-id="f3f53-110">Set the <xref:System.Windows.Controls.Panel.ZIndexProperty> on the <xref:System.Windows.Controls.GridSplitter> to be higher than a control that would otherwise hide it.</span></span> <span data-ttu-id="f3f53-111">Aşağıdaki örnek verir <xref:System.Windows.Controls.GridSplitter> daha yüksek bir denetim <xref:System.Windows.Controls.Panel.ZIndexProperty> daha <xref:System.Windows.Controls.Button> denetimi.</span><span class="sxs-lookup"><span data-stu-id="f3f53-111">The following example gives the <xref:System.Windows.Controls.GridSplitter> control a higher <xref:System.Windows.Controls.Panel.ZIndexProperty> than the <xref:System.Windows.Controls.Button> control.</span></span>  
  
 [!code-xaml[GridSplitterSnips#GridSplitterZIndex](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterzindex)]  
  
-   <span data-ttu-id="f3f53-112">Aksi halde gizleyecek denetimde kenar boşluklarını ayarlama <xref:System.Windows.Controls.GridSplitter> böylece <xref:System.Windows.Controls.GridSplitter> sunulur.</span><span class="sxs-lookup"><span data-stu-id="f3f53-112">Set margins on the control that would otherwise hide the <xref:System.Windows.Controls.GridSplitter> so that the <xref:System.Windows.Controls.GridSplitter> is exposed.</span></span> <span data-ttu-id="f3f53-113">Aşağıdaki örnek, aksi takdirde kaplama bir denetim ve Gizle kenar boşlukları ayarlar <xref:System.Windows.Controls.GridSplitter>.</span><span class="sxs-lookup"><span data-stu-id="f3f53-113">The following example sets margins on a control that would otherwise overlay and hide the <xref:System.Windows.Controls.GridSplitter>.</span></span>  
  
 [!code-xaml[GridSplitterSnips#GridSplitterMargin](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplittermargin)]  
  
## <a name="see-also"></a><span data-ttu-id="f3f53-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3f53-114">See also</span></span>
- <xref:System.Windows.Controls.GridSplitter>
- [<span data-ttu-id="f3f53-115">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="f3f53-115">How-to Topics</span></span>](gridsplitter-how-to-topics.md)
