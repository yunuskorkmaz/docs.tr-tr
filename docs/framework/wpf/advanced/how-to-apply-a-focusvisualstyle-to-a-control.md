---
title: 'Nasıl yapılır: Denetime FocusVisualStyle Uygulama'
ms.date: 03/30/2017
helpviewer_keywords:
- properties [WPF], FocusVisualStyle
- FocusVisualStyle property [WPF]
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
ms.openlocfilehash: b44330ee7554f953389556bd62ff49db120b5db9
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459813"
---
# <a name="how-to-apply-a-focusvisualstyle-to-a-control"></a><span data-ttu-id="f26a3-102">Nasıl yapılır: Denetime FocusVisualStyle Uygulama</span><span class="sxs-lookup"><span data-stu-id="f26a3-102">How to: Apply a FocusVisualStyle to a Control</span></span>
<span data-ttu-id="f26a3-103">Bu örnek, <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> özelliğini kullanarak kaynaklarda odak görsel stilinin nasıl oluşturulacağını ve stilin bir denetime nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f26a3-103">This example shows you how to create a focus visual style in resources and apply the style to a control, using the <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f26a3-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="f26a3-104">Example</span></span>  
 <span data-ttu-id="f26a3-105">Aşağıdaki örnek, yalnızca denetimin [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]odaklandığı zaman geçerli olan ek denetim birleştirmesini oluşturan bir stil tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f26a3-105">The following example defines a style that creates additional control compositing that only applies when that control is keyboard focused in the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span> <span data-ttu-id="f26a3-106">Bu, <xref:System.Windows.Controls.ControlTemplate>bir stil tanımlayarak ve <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> özelliği ayarlanırken bu stile kaynak olarak başvurularak yapılır.</span><span class="sxs-lookup"><span data-stu-id="f26a3-106">This is accomplished by defining a style with a <xref:System.Windows.Controls.ControlTemplate>, then referencing that style as a resource when setting the <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> property.</span></span>  
  
 <span data-ttu-id="f26a3-107">Bir kenarlığa benzeyen dış Dikdörtgen dikdörtgen alanın dışına yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f26a3-107">An external rectangle resembling a border is placed outside of the rectangular area.</span></span> <span data-ttu-id="f26a3-108">Aksi belirtilmedikçe, stilin boyutlandırılması, odak görsel stilinin uygulandığı dikdörtgen denetimin <xref:System.Windows.FrameworkElement.ActualHeight%2A> ve <xref:System.Windows.FrameworkElement.ActualWidth%2A> kullanır.</span><span class="sxs-lookup"><span data-stu-id="f26a3-108">Unless otherwise modified, the sizing of the style uses the <xref:System.Windows.FrameworkElement.ActualHeight%2A> and <xref:System.Windows.FrameworkElement.ActualWidth%2A> of the rectangular control where the focus visual style is applied.</span></span> <span data-ttu-id="f26a3-109">Bu örnek, kenarlığın odaklanmış denetimin dışında biraz görünmesi için <xref:System.Windows.FrameworkElement.Margin%2A> negatif değerlerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f26a3-109">This example sets negative values for the <xref:System.Windows.FrameworkElement.Margin%2A> to make the border appear slightly outside the focused control.</span></span>  
  
 [!code-xaml[FEFocusVisualStyle#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 <span data-ttu-id="f26a3-110"><xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>, açık bir stille veya tema stilinden gelen herhangi bir denetim şablonu stiline eklenebilir; bir denetimin birincil stili hala bir <xref:System.Windows.Controls.ControlTemplate> kullanılarak oluşturulabilir ve bu stil <xref:System.Windows.FrameworkElement.Style%2A> özelliğine ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="f26a3-110">A <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> is additive to any control template style that comes either from an explicit style or a theme style; the primary style for a control can still be created by using a <xref:System.Windows.Controls.ControlTemplate> and setting that style to the <xref:System.Windows.FrameworkElement.Style%2A> property.</span></span>  
  
 <span data-ttu-id="f26a3-111">Odak görsel stilleri, odaklanacak her öğe için farklı bir tane kullanmak yerine bir tema veya Kullanıcı arabirimi genelinde sürekli olarak kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f26a3-111">Focus visual styles should be used consistently across a theme or a UI, rather than using a different one for each focusable element.</span></span> <span data-ttu-id="f26a3-112">Ayrıntılar için bkz. [denetimlerde odak Için stil oluşturma ve FocusVisualStyle](styling-for-focus-in-controls-and-focusvisualstyle.md).</span><span class="sxs-lookup"><span data-stu-id="f26a3-112">For details, see [Styling for Focus in Controls, and FocusVisualStyle](styling-for-focus-in-controls-and-focusvisualstyle.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f26a3-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f26a3-113">See also</span></span>

- <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>
- [<span data-ttu-id="f26a3-114">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f26a3-114">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="f26a3-115">Denetimlerde Odak için Stil Oluşturma ve FocusVisualStyle</span><span class="sxs-lookup"><span data-stu-id="f26a3-115">Styling for Focus in Controls, and FocusVisualStyle</span></span>](styling-for-focus-in-controls-and-focusvisualstyle.md)
