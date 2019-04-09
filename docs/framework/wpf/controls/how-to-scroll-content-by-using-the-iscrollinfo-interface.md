---
title: 'Nasıl yapılır: IScrollInfo Arabirimini Kullanarak İçerik Kaydırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ScrollViewer control [WPF], scrolling content
- scrolling content [WPF]
- IScrollInfo interface [WPF]
ms.assetid: d8700bef-a3f8-4c12-9de2-fc3b79f32cd3
ms.openlocfilehash: 6ebd8268e1358b45709885c07e6b096d5f806ebb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098552"
---
# <a name="how-to-scroll-content-by-using-the-iscrollinfo-interface"></a><span data-ttu-id="9990c-102">Nasıl yapılır: IScrollInfo Arabirimini Kullanarak İçerik Kaydırma</span><span class="sxs-lookup"><span data-stu-id="9990c-102">How to: Scroll Content by Using the IScrollInfo Interface</span></span>
<span data-ttu-id="9990c-103">Bu örnekte kullanarak içerik kaydırma gösterilmektedir <xref:System.Windows.Controls.Primitives.IScrollInfo> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="9990c-103">This example shows how to scroll content by using the <xref:System.Windows.Controls.Primitives.IScrollInfo> interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9990c-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="9990c-104">Example</span></span>  
 <span data-ttu-id="9990c-105">Aşağıdaki örnek özelliklerini gösterir <xref:System.Windows.Controls.Primitives.IScrollInfo> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="9990c-105">The following example demonstrates the features of the <xref:System.Windows.Controls.Primitives.IScrollInfo> interface.</span></span> <span data-ttu-id="9990c-106">Örnek bir <xref:System.Windows.Controls.StackPanel> öğesinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] bir üst içe <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="9990c-106">The example creates a <xref:System.Windows.Controls.StackPanel> element in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that is nested in a parent <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="9990c-107">Alt öğeleri <xref:System.Windows.Controls.StackPanel> tarafından tanımlanan yöntemler kullanılarak mantıksal olarak kaydırılabileceğini <xref:System.Windows.Controls.Primitives.IScrollInfo> arabirimi ve atama örneğine <xref:System.Windows.Controls.StackPanel> (`sp1`) kod.</span><span class="sxs-lookup"><span data-stu-id="9990c-107">The child elements of the <xref:System.Windows.Controls.StackPanel> can be scrolled logically by using the methods defined by the <xref:System.Windows.Controls.Primitives.IScrollInfo> interface and cast to the instance of <xref:System.Windows.Controls.StackPanel> (`sp1`) in code.</span></span>  
  
 [!code-xaml[IScrollInfoMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="9990c-108">Her <xref:System.Windows.Controls.Button> içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya içinde kaydırma davranışını denetleyen bir ilişkili özel yöntemi tetikler <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="9990c-108">Each <xref:System.Windows.Controls.Button> in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file triggers an associated custom method that controls scrolling behavior in <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="9990c-109">Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> ve <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A> yöntemleri; ayrıca genel konumlandırma tüm yöntemlerin nasıl kullanılacağını gösterir, <xref:System.Windows.Controls.Primitives.IScrollInfo> sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9990c-109">The following example shows how to use the <xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> and <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A> methods; it also generically shows how to use all the positioning methods that the <xref:System.Windows.Controls.Primitives.IScrollInfo> class defines.</span></span>  
  
 [!code-csharp[IScrollInfoMethods#3](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="9990c-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9990c-110">See also</span></span>

- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.Primitives.IScrollInfo>
- <xref:System.Windows.Controls.StackPanel>
- [<span data-ttu-id="9990c-111">ScrollViewer Genel Bakışı</span><span class="sxs-lookup"><span data-stu-id="9990c-111">ScrollViewer Overview</span></span>](scrollviewer-overview.md)
- [<span data-ttu-id="9990c-112">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="9990c-112">How-to Topics</span></span>](scrollviewer-how-to-topics.md)
- [<span data-ttu-id="9990c-113">Panellere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9990c-113">Panels Overview</span></span>](panels-overview.md)
