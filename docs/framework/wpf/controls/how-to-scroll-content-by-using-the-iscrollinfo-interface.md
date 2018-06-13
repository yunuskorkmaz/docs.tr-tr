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
ms.openlocfilehash: 8154a626c6bf48a59be0540f857c0c51d59a26c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552889"
---
# <a name="how-to-scroll-content-by-using-the-iscrollinfo-interface"></a><span data-ttu-id="7ebd4-102">Nasıl yapılır: IScrollInfo Arabirimini Kullanarak İçerik Kaydırma</span><span class="sxs-lookup"><span data-stu-id="7ebd4-102">How to: Scroll Content by Using the IScrollInfo Interface</span></span>
<span data-ttu-id="7ebd4-103">Bu örnek kullanarak içeriği kaydırmak nasıl gösterir <xref:System.Windows.Controls.Primitives.IScrollInfo> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="7ebd4-103">This example shows how to scroll content by using the <xref:System.Windows.Controls.Primitives.IScrollInfo> interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ebd4-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="7ebd4-104">Example</span></span>  
 <span data-ttu-id="7ebd4-105">Aşağıdaki örnek özelliklerini gösterir <xref:System.Windows.Controls.Primitives.IScrollInfo> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="7ebd4-105">The following example demonstrates the features of the <xref:System.Windows.Controls.Primitives.IScrollInfo> interface.</span></span> <span data-ttu-id="7ebd4-106">Örnekte bir <xref:System.Windows.Controls.StackPanel> öğesinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] bir üst içe <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="7ebd4-106">The example creates a <xref:System.Windows.Controls.StackPanel> element in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that is nested in a parent <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="7ebd4-107">Alt öğeleri <xref:System.Windows.Controls.StackPanel> mantıksal olarak tarafından tanımlanan yöntemler kullanılarak kaydırılabileceğini <xref:System.Windows.Controls.Primitives.IScrollInfo> arabirimi ve atama örneğine <xref:System.Windows.Controls.StackPanel> (`sp1`) kod.</span><span class="sxs-lookup"><span data-stu-id="7ebd4-107">The child elements of the <xref:System.Windows.Controls.StackPanel> can be scrolled logically by using the methods defined by the <xref:System.Windows.Controls.Primitives.IScrollInfo> interface and cast to the instance of <xref:System.Windows.Controls.StackPanel> (`sp1`) in code.</span></span>  
  
 [!code-xaml[IScrollInfoMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="7ebd4-108">Her <xref:System.Windows.Controls.Button> içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya içinde kaydırma davranışını denetleyen ilişkili özel metodu tetikler <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="7ebd4-108">Each <xref:System.Windows.Controls.Button> in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file triggers an associated custom method that controls scrolling behavior in <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="7ebd4-109">Aşağıdaki örnekte nasıl kullanılacağını gösterir <xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> ve <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A> yöntemleri; ayrıca genel tüm konumlandırma yöntemlerinin nasıl kullanılacağını gösterir, <xref:System.Windows.Controls.Primitives.IScrollInfo> sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7ebd4-109">The following example shows how to use the <xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> and <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A> methods; it also generically shows how to use all the positioning methods that the <xref:System.Windows.Controls.Primitives.IScrollInfo> class defines.</span></span>  
  
 [!code-csharp[IScrollInfoMethods#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="7ebd4-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7ebd4-110">See Also</span></span>  
 <xref:System.Windows.Controls.ScrollViewer>  
 <xref:System.Windows.Controls.Primitives.IScrollInfo>  
 <xref:System.Windows.Controls.StackPanel>  
 [<span data-ttu-id="7ebd4-111">ScrollViewer Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7ebd4-111">ScrollViewer Overview</span></span>](../../../../docs/framework/wpf/controls/scrollviewer-overview.md)  
 [<span data-ttu-id="7ebd4-112">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="7ebd4-112">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/scrollviewer-how-to-topics.md)  
 [<span data-ttu-id="7ebd4-113">Panellere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7ebd4-113">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
