---
title: 'Nasıl yapılır: StackPanel İçinde Yatay veya Dikey Olarak İçerik Hizalama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StackPanel control [WPF], content alignment [WPF]
- content alignment [WPF]
- aligning [WPF], content
ms.assetid: c1e8f962-72c8-4e7a-8670-7a2d7e021791
ms.openlocfilehash: a03cb1ed9b3e5bd42b28e37f5bbb3e1d0446a4ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33550764"
---
# <a name="how-to-horizontally-or-vertically-align-content-in-a-stackpanel"></a><span data-ttu-id="8cc58-102">Nasıl yapılır: StackPanel İçinde Yatay veya Dikey Olarak İçerik Hizalama</span><span class="sxs-lookup"><span data-stu-id="8cc58-102">How to: Horizontally or Vertically Align Content in a StackPanel</span></span>
<span data-ttu-id="8cc58-103">Bu örnek nasıl ayarlanacağını gösterir <xref:System.Windows.Controls.StackPanel.Orientation%2A> içindeki içeriğin bir <xref:System.Windows.Controls.StackPanel> öğesi ve nasıl ayarlanacağını <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> ve <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> alt içerik.</span><span class="sxs-lookup"><span data-stu-id="8cc58-103">This example shows how to adjust the <xref:System.Windows.Controls.StackPanel.Orientation%2A> of content within a <xref:System.Windows.Controls.StackPanel> element, and also how to adjust the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> of child content.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8cc58-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="8cc58-104">Example</span></span>  
 <span data-ttu-id="8cc58-105">Aşağıdaki örnek, üç oluşturur <xref:System.Windows.Controls.ListBox> öğelerinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8cc58-105">The following example creates three <xref:System.Windows.Controls.ListBox> elements in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="8cc58-106">Her <xref:System.Windows.Controls.ListBox> olası değerlerini temsil eden <xref:System.Windows.Controls.StackPanel.Orientation%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, ve <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> özelliklerini bir <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="8cc58-106">Each <xref:System.Windows.Controls.ListBox> represents the possible values of the <xref:System.Windows.Controls.StackPanel.Orientation%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> properties of a <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="8cc58-107">Bir kullanıcı seçtiğinde bir değer hiçbirinde <xref:System.Windows.Controls.ListBox> öğeleri, ilişkili özelliğinin <xref:System.Windows.Controls.StackPanel> ve alt <xref:System.Windows.Controls.Button> öğelerini değiştirme.</span><span class="sxs-lookup"><span data-stu-id="8cc58-107">When a user selects a value in any of the <xref:System.Windows.Controls.ListBox> elements, the associated property of the <xref:System.Windows.Controls.StackPanel> and its child <xref:System.Windows.Controls.Button> elements change.</span></span>  
  
 [!code-xaml[StackPanelIntroSamp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="8cc58-108">Aşağıdaki arka plan kod dosyası ile ilişkili olaylar değişiklikleri tanımlar <xref:System.Windows.Controls.ListBox> seçim değişir.</span><span class="sxs-lookup"><span data-stu-id="8cc58-108">The following code-behind file defines the changes to the events that are associated with the <xref:System.Windows.Controls.ListBox> selection changes.</span></span> <span data-ttu-id="8cc58-109"><xref:System.Windows.Controls.StackPanel> tarafından tanımlanan <xref:System.Windows.FrameworkElement.Name%2A> `sp1`.</span><span class="sxs-lookup"><span data-stu-id="8cc58-109"><xref:System.Windows.Controls.StackPanel> is identified by the <xref:System.Windows.FrameworkElement.Name%2A> `sp1`.</span></span>  
  
 [!code-csharp[StackPanelIntroSamp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[StackPanelIntroSamp#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelIntroSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="8cc58-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8cc58-110">See Also</span></span>  
 <xref:System.Windows.Controls.StackPanel>  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>  
 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>  
 [<span data-ttu-id="8cc58-111">Panellere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8cc58-111">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
