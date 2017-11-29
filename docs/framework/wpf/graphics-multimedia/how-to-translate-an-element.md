---
title: "Nasıl yapılır: Bir Öğeyi Çevirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: graphics [WPF], translations
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 222aebe0ffe3d2bb1d84002a2ad94b0b92ede15b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-translate-an-element"></a><span data-ttu-id="a0928-102">Nasıl yapılır: Bir Öğeyi Çevirme</span><span class="sxs-lookup"><span data-stu-id="a0928-102">How to: Translate an Element</span></span>
<span data-ttu-id="a0928-103">Bu örnek, kullanarak bir öğe (Taşı) çevirmek nasıl gösterir bir <xref:System.Windows.Media.TranslateTransform>.</span><span class="sxs-lookup"><span data-stu-id="a0928-103">This example shows how to translate (move) an element by using a <xref:System.Windows.Media.TranslateTransform>.</span></span>  
  
 <span data-ttu-id="a0928-104"><xref:System.Windows.Media.TranslateTransform> Sınıfı, mutlak konumlandırmayı desteklemeyen panolar içinde öğeleri taşımak için özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="a0928-104">The <xref:System.Windows.Media.TranslateTransform> class is especially useful for moving elements inside panels that do not support absolute positioning.</span></span> <span data-ttu-id="a0928-105">Örneğin, uygulama tarafından bir <xref:System.Windows.Media.TranslateTransform> için <xref:System.Windows.UIElement.RenderTransform%2A> özelliği, bir öğenin bir öğenin içine taşıyabilirsiniz bir <xref:System.Windows.Controls.StackPanel> veya <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="a0928-105">For example, by applying a <xref:System.Windows.Media.TranslateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of an element, you can move an element within a <xref:System.Windows.Controls.StackPanel> or <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
 <span data-ttu-id="a0928-106">Kullanım <xref:System.Windows.Media.TranslateTransform.X%2A> özelliği <xref:System.Windows.Media.TranslateTransform> x ekseni boyunca öğe taşımak için piksel cinsinden miktarı belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="a0928-106">Use the <xref:System.Windows.Media.TranslateTransform.X%2A> property of the <xref:System.Windows.Media.TranslateTransform> to specify the amount, in pixels, to move the element along the x-axis.</span></span> <span data-ttu-id="a0928-107">Kullanım <xref:System.Windows.Media.TranslateTransform.Y%2A> özelliği y ekseni boyunca öğe taşımak için piksel cinsinden miktarını belirtin.</span><span class="sxs-lookup"><span data-stu-id="a0928-107">Use the <xref:System.Windows.Media.TranslateTransform.Y%2A> property to specify the amount, in pixels, to move the element along the y-axis.</span></span> <span data-ttu-id="a0928-108">Son olarak, uygulama <xref:System.Windows.Media.TranslateTransform> için <xref:System.Windows.UIElement.RenderTransform%2A> öğesi özelliği.</span><span class="sxs-lookup"><span data-stu-id="a0928-108">Finally, apply the <xref:System.Windows.Media.TranslateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span>  
  
 <span data-ttu-id="a0928-109">Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.TranslateTransform> bir öğe 50 piksel sağ ve 50 piksel olarak aşağı taşımak için.</span><span class="sxs-lookup"><span data-stu-id="a0928-109">The following example uses a <xref:System.Windows.Media.TranslateTransform> to move an element 50 pixels to the right and 50 pixels down.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0928-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="a0928-110">Example</span></span>  
 [!code-xaml[transformsSample#53](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 <span data-ttu-id="a0928-111">Tam bir örnek için bkz: [2-D dönüşümler örnek](http://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="a0928-111">For the complete sample, see [2-D Transforms Sample](http://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0928-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a0928-112">See Also</span></span>  
 [<span data-ttu-id="a0928-113">Dönüşümler genel bakış</span><span class="sxs-lookup"><span data-stu-id="a0928-113">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
