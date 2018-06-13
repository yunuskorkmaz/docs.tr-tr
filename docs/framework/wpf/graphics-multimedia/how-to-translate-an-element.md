---
title: 'Nasıl yapılır: Bir Öğeyi Çevirme'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], translations
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
ms.openlocfilehash: 0089f294c54662d1ea4929ec25c08464072cbdde
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561949"
---
# <a name="how-to-translate-an-element"></a><span data-ttu-id="0def3-102">Nasıl yapılır: Bir Öğeyi Çevirme</span><span class="sxs-lookup"><span data-stu-id="0def3-102">How to: Translate an Element</span></span>
<span data-ttu-id="0def3-103">Bu örnek, kullanarak bir öğe (Taşı) çevirmek nasıl gösterir bir <xref:System.Windows.Media.TranslateTransform>.</span><span class="sxs-lookup"><span data-stu-id="0def3-103">This example shows how to translate (move) an element by using a <xref:System.Windows.Media.TranslateTransform>.</span></span>  
  
 <span data-ttu-id="0def3-104"><xref:System.Windows.Media.TranslateTransform> Sınıfı, mutlak konumlandırmayı desteklemeyen panolar içinde öğeleri taşımak için özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="0def3-104">The <xref:System.Windows.Media.TranslateTransform> class is especially useful for moving elements inside panels that do not support absolute positioning.</span></span> <span data-ttu-id="0def3-105">Örneğin, uygulama tarafından bir <xref:System.Windows.Media.TranslateTransform> için <xref:System.Windows.UIElement.RenderTransform%2A> özelliği, bir öğenin bir öğenin içine taşıyabilirsiniz bir <xref:System.Windows.Controls.StackPanel> veya <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="0def3-105">For example, by applying a <xref:System.Windows.Media.TranslateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of an element, you can move an element within a <xref:System.Windows.Controls.StackPanel> or <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
 <span data-ttu-id="0def3-106">Kullanım <xref:System.Windows.Media.TranslateTransform.X%2A> özelliği <xref:System.Windows.Media.TranslateTransform> x ekseni boyunca öğe taşımak için piksel cinsinden miktarı belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="0def3-106">Use the <xref:System.Windows.Media.TranslateTransform.X%2A> property of the <xref:System.Windows.Media.TranslateTransform> to specify the amount, in pixels, to move the element along the x-axis.</span></span> <span data-ttu-id="0def3-107">Kullanım <xref:System.Windows.Media.TranslateTransform.Y%2A> özelliği y ekseni boyunca öğe taşımak için piksel cinsinden miktarını belirtin.</span><span class="sxs-lookup"><span data-stu-id="0def3-107">Use the <xref:System.Windows.Media.TranslateTransform.Y%2A> property to specify the amount, in pixels, to move the element along the y-axis.</span></span> <span data-ttu-id="0def3-108">Son olarak, uygulama <xref:System.Windows.Media.TranslateTransform> için <xref:System.Windows.UIElement.RenderTransform%2A> öğesi özelliği.</span><span class="sxs-lookup"><span data-stu-id="0def3-108">Finally, apply the <xref:System.Windows.Media.TranslateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span>  
  
 <span data-ttu-id="0def3-109">Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.TranslateTransform> bir öğe 50 piksel sağ ve 50 piksel olarak aşağı taşımak için.</span><span class="sxs-lookup"><span data-stu-id="0def3-109">The following example uses a <xref:System.Windows.Media.TranslateTransform> to move an element 50 pixels to the right and 50 pixels down.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0def3-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="0def3-110">Example</span></span>  
 [!code-xaml[transformsSample#53](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 <span data-ttu-id="0def3-111">Tam bir örnek için bkz: [2-D dönüşümler örnek](http://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="0def3-111">For the complete sample, see [2-D Transforms Sample](http://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0def3-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0def3-112">See Also</span></span>  
 [<span data-ttu-id="0def3-113">Dönüşümlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0def3-113">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
