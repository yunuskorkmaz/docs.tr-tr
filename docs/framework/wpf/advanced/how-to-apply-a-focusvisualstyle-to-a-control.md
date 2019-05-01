---
title: 'Nasıl yapılır: Denetime FocusVisualStyle Uygulama'
ms.date: 03/30/2017
helpviewer_keywords:
- properties [WPF], FocusVisualStyle
- FocusVisualStyle property [WPF]
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
ms.openlocfilehash: 53d4984946143c15c4a2b71095529fb5ee7de4b1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051331"
---
# <a name="how-to-apply-a-focusvisualstyle-to-a-control"></a><span data-ttu-id="5f72d-102">Nasıl yapılır: Denetime FocusVisualStyle Uygulama</span><span class="sxs-lookup"><span data-stu-id="5f72d-102">How to: Apply a FocusVisualStyle to a Control</span></span>
<span data-ttu-id="5f72d-103">Bu örnek nasıl odak görsel stili kaynakları oluşturup bir denetime stil uygulama gösterir kullanarak <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="5f72d-103">This example shows you how to create a focus visual style in resources and apply the style to a control, using the <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f72d-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="5f72d-104">Example</span></span>  
 <span data-ttu-id="5f72d-105">Aşağıdaki örnek, denetimin klavye odaklı içinde olduğunda yalnızca geçerli olan ek denetim birleştirmesini oluşturur bir stil tanımlar [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5f72d-105">The following example defines a style that creates additional control compositing that only applies when that control is keyboard focused in the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span> <span data-ttu-id="5f72d-106">Bu stil ile tanımlayarak gerçekleştirilir bir <xref:System.Windows.Controls.ControlTemplate>, o stilin ayarlanırken bir kaynak olarak başvuran sonra <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="5f72d-106">This is accomplished by defining a style with a <xref:System.Windows.Controls.ControlTemplate>, then referencing that style as a resource when setting the <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> property.</span></span>  
  
 <span data-ttu-id="5f72d-107">Benzeyen bir kenarlık dış bir dikdörtgen dışında dikdörtgen alan yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5f72d-107">An external rectangle resembling a border is placed outside of the rectangular area.</span></span> <span data-ttu-id="5f72d-108">Aksi takdirde değiştirilmediği sürece stili boyutlandırması kullanır <xref:System.Windows.FrameworkElement.ActualHeight%2A> ve <xref:System.Windows.FrameworkElement.ActualWidth%2A> dikdörtgen denetimi odak görsel stili burada uygulanır.</span><span class="sxs-lookup"><span data-stu-id="5f72d-108">Unless otherwise modified, the sizing of the style uses the <xref:System.Windows.FrameworkElement.ActualHeight%2A> and <xref:System.Windows.FrameworkElement.ActualWidth%2A> of the rectangular control where the focus visual style is applied.</span></span> <span data-ttu-id="5f72d-109">Bu örnek için negatif değerler ayarlar <xref:System.Windows.FrameworkElement.Margin%2A> kenarlık biraz odaklı denetimin dışında görünür hale getirmek için.</span><span class="sxs-lookup"><span data-stu-id="5f72d-109">This example sets negative values for the <xref:System.Windows.FrameworkElement.Margin%2A> to make the border appear slightly outside the focused control.</span></span>  
  
 [!code-xaml[FEFocusVisualStyle#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 <span data-ttu-id="5f72d-110">A <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> olan gelen herhangi bir denetim şablonu stilini eklenebilir ya da açık bir stil veya bir tema stili; bir denetim için birincil stil yine de kullanarak oluşturulabilir bir <xref:System.Windows.Controls.ControlTemplate> ve o stilin ayarını <xref:System.Windows.FrameworkElement.Style%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="5f72d-110">A <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> is additive to any control template style that comes either from an explicit style or a theme style; the primary style for a control can still be created by using a <xref:System.Windows.Controls.ControlTemplate> and setting that style to the <xref:System.Windows.FrameworkElement.Style%2A> property.</span></span>  
  
 <span data-ttu-id="5f72d-111">Odak görsel stilleri kullanılmalıdır tutarlı bir şekilde bir tema veya bir kullanıcı Arabirimi odaklanabilir her öğe için farklı bir kullanmak yerine.</span><span class="sxs-lookup"><span data-stu-id="5f72d-111">Focus visual styles should be used consistently across a theme or a UI, rather than using a different one for each focusable element.</span></span> <span data-ttu-id="5f72d-112">Ayrıntılar için bkz [denetimleri ve FocusVisualStyle odak için stil oluşturma](styling-for-focus-in-controls-and-focusvisualstyle.md).</span><span class="sxs-lookup"><span data-stu-id="5f72d-112">For details, see [Styling for Focus in Controls, and FocusVisualStyle](styling-for-focus-in-controls-and-focusvisualstyle.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f72d-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f72d-113">See also</span></span>

- <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>
- [<span data-ttu-id="5f72d-114">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5f72d-114">Styling and Templating</span></span>](../controls/styling-and-templating.md)
- [<span data-ttu-id="5f72d-115">Denetimlerde Odak için Stil Oluşturma ve FocusVisualStyle</span><span class="sxs-lookup"><span data-stu-id="5f72d-115">Styling for Focus in Controls, and FocusVisualStyle</span></span>](styling-for-focus-in-controls-and-focusvisualstyle.md)
