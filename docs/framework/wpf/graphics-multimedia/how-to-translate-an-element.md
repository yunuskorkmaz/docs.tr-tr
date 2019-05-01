---
title: 'Nasıl yapılır: Bir Öğeyi Çevirme'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], translations
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
ms.openlocfilehash: 9c1b873a89820e85efb99789f483c4832fb23cf7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051448"
---
# <a name="how-to-translate-an-element"></a><span data-ttu-id="b408c-102">Nasıl yapılır: Bir Öğeyi Çevirme</span><span class="sxs-lookup"><span data-stu-id="b408c-102">How to: Translate an Element</span></span>
<span data-ttu-id="b408c-103">Bu örnek nasıl çevrileceği (taşıma) kullanarak bir öğe gösterir bir <xref:System.Windows.Media.TranslateTransform>.</span><span class="sxs-lookup"><span data-stu-id="b408c-103">This example shows how to translate (move) an element by using a <xref:System.Windows.Media.TranslateTransform>.</span></span>  
  
 <span data-ttu-id="b408c-104"><xref:System.Windows.Media.TranslateTransform> Sınıfı, konumlandırmayı mutlak desteklemeyen bir panel içinde öğeleri taşımak için özellikle kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="b408c-104">The <xref:System.Windows.Media.TranslateTransform> class is especially useful for moving elements inside panels that do not support absolute positioning.</span></span> <span data-ttu-id="b408c-105">Örneğin, uygulama tarafından bir <xref:System.Windows.Media.TranslateTransform> için <xref:System.Windows.UIElement.RenderTransform%2A> özellik öğesinin içindeki bir öğeye taşıyabilirsiniz bir <xref:System.Windows.Controls.StackPanel> veya <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="b408c-105">For example, by applying a <xref:System.Windows.Media.TranslateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of an element, you can move an element within a <xref:System.Windows.Controls.StackPanel> or <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
 <span data-ttu-id="b408c-106">Kullanım <xref:System.Windows.Media.TranslateTransform.X%2A> özelliği <xref:System.Windows.Media.TranslateTransform> miktarını piksel cinsinden öğe x ekseni boyunca taşımak için belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="b408c-106">Use the <xref:System.Windows.Media.TranslateTransform.X%2A> property of the <xref:System.Windows.Media.TranslateTransform> to specify the amount, in pixels, to move the element along the x-axis.</span></span> <span data-ttu-id="b408c-107">Kullanım <xref:System.Windows.Media.TranslateTransform.Y%2A> özelliği miktarını piksel cinsinden öğe ve y ekseni boyunca taşımak için belirtin.</span><span class="sxs-lookup"><span data-stu-id="b408c-107">Use the <xref:System.Windows.Media.TranslateTransform.Y%2A> property to specify the amount, in pixels, to move the element along the y-axis.</span></span> <span data-ttu-id="b408c-108">Son olarak, uygulama <xref:System.Windows.Media.TranslateTransform> için <xref:System.Windows.UIElement.RenderTransform%2A> öğesinin özelliği.</span><span class="sxs-lookup"><span data-stu-id="b408c-108">Finally, apply the <xref:System.Windows.Media.TranslateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span>  
  
 <span data-ttu-id="b408c-109">Aşağıdaki örnekte bir <xref:System.Windows.Media.TranslateTransform> öğesi 50 piksel doğru ve 50 piksel olarak aşağı taşımak için.</span><span class="sxs-lookup"><span data-stu-id="b408c-109">The following example uses a <xref:System.Windows.Media.TranslateTransform> to move an element 50 pixels to the right and 50 pixels down.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b408c-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="b408c-110">Example</span></span>  
 [!code-xaml[transformsSample#53](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 <span data-ttu-id="b408c-111">Tam bir örnek için bkz. [2B dönüşüm örnek](https://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="b408c-111">For the complete sample, see [2-D Transforms Sample](https://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b408c-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b408c-112">See also</span></span>

- [<span data-ttu-id="b408c-113">Dönüşümlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b408c-113">Transforms Overview</span></span>](transforms-overview.md)
