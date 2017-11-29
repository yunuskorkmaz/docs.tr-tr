---
title: "Nasıl yapılır: Denetime FocusVisualStyle Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- properties [WPF], FocusVisualStyle
- FocusVisualStyle property [WPF]
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f614e244293d08cd836edaf82496ca9e7b51423e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-apply-a-focusvisualstyle-to-a-control"></a><span data-ttu-id="50ea1-102">Nasıl yapılır: Denetime FocusVisualStyle Uygulama</span><span class="sxs-lookup"><span data-stu-id="50ea1-102">How to: Apply a FocusVisualStyle to a Control</span></span>
<span data-ttu-id="50ea1-103">Bu örnek kaynaklarında odak görsel stili oluşturmak ve bir denetim için stil uygulamak gösterilmiştir kullanarak <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="50ea1-103">This example shows you how to create a focus visual style in resources and apply the style to a control, using the <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50ea1-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="50ea1-104">Example</span></span>  
 <span data-ttu-id="50ea1-105">Aşağıdaki örnek, bu denetim nde klavye odaklı olduğunda uygulanan ek denetim birleştirmesini oluşturur bir stil tanımlar [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="50ea1-105">The following example defines a style that creates additional control compositing that only applies when that control is keyboard focused in the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span> <span data-ttu-id="50ea1-106">Bu bir stille tanımlayarak gerçekleştirilir bir <xref:System.Windows.Controls.ControlTemplate>, bu stili ayarlarken bir kaynak olarak başvuran sonra <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="50ea1-106">This is accomplished by defining a style with a <xref:System.Windows.Controls.ControlTemplate>, then referencing that style as a resource when setting the <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> property.</span></span>  
  
 <span data-ttu-id="50ea1-107">Kenarlık benzeyen bir dış dikdörtgen dikdörtgen dışında yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="50ea1-107">An external rectangle resembling a border is placed outside of the rectangular area.</span></span> <span data-ttu-id="50ea1-108">Aksi değiştirilmediği sürece, stil boyutlandırma kullanır <xref:System.Windows.FrameworkElement.ActualHeight%2A> ve <xref:System.Windows.FrameworkElement.ActualWidth%2A> dikdörtgen denetiminin odak görsel stil burada uygulanır.</span><span class="sxs-lookup"><span data-stu-id="50ea1-108">Unless otherwise modified, the sizing of the style uses the <xref:System.Windows.FrameworkElement.ActualHeight%2A> and <xref:System.Windows.FrameworkElement.ActualWidth%2A> of the rectangular control where the focus visual style is applied.</span></span> <span data-ttu-id="50ea1-109">Bu örnek için negatif değerler ayarlar <xref:System.Windows.FrameworkElement.Margin%2A> biraz daha odaklı denetimin dışında görünür kenarlık yapma.</span><span class="sxs-lookup"><span data-stu-id="50ea1-109">This example sets negative values for the <xref:System.Windows.FrameworkElement.Margin%2A> to make the border appear slightly outside the focused control.</span></span>  
  
 [!code-xaml[FEFocusVisualStyle#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 <span data-ttu-id="50ea1-110">A <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> olan gelen herhangi bir denetim şablonu stil eklenebilir ya da bir açık stili veya bir tema stili; denetimi için birincil stil hala kullanarak oluşturulabilir bir <xref:System.Windows.Controls.ControlTemplate> ve bu stili ayarını <xref:System.Windows.FrameworkElement.Style%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="50ea1-110">A <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> is additive to any control template style that comes either from an explicit style or a theme style; the primary style for a control can still be created by using a <xref:System.Windows.Controls.ControlTemplate> and setting that style to the <xref:System.Windows.FrameworkElement.Style%2A> property.</span></span>  
  
 <span data-ttu-id="50ea1-111">Görsel stiller kullanılmalıdır tutarlı bir tema veya bir kullanıcı Arabirimi odak odaklanabilir her öğe için farklı bir kullanarak yerine.</span><span class="sxs-lookup"><span data-stu-id="50ea1-111">Focus visual styles should be used consistently across a theme or a UI, rather than using a different one for each focusable element.</span></span> <span data-ttu-id="50ea1-112">Ayrıntılar için bkz [denetimleri ve FocusVisualStyle odakta için stil oluşturma](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md).</span><span class="sxs-lookup"><span data-stu-id="50ea1-112">For details, see [Styling for Focus in Controls, and FocusVisualStyle](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50ea1-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="50ea1-113">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>  
 [<span data-ttu-id="50ea1-114">Stil ve şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="50ea1-114">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="50ea1-115">Denetimleri ve FocusVisualStyle odakta için stil oluşturma</span><span class="sxs-lookup"><span data-stu-id="50ea1-115">Styling for Focus in Controls, and FocusVisualStyle</span></span>](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md)
