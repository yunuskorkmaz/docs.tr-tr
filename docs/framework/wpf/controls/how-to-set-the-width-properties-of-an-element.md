---
title: 'Nasıl yapılır: Öğenin Genişlik Özelliklerini Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- width properties [WPF]
- Panel control [WPF], width properties of elements
ms.assetid: 6ee04a9d-63f0-4f5b-a406-0a8cd4c35729
ms.openlocfilehash: 682929625612114d042e4619d8388617988b3c48
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124279"
---
# <a name="how-to-set-the-width-properties-of-an-element"></a><span data-ttu-id="862fd-102">Nasıl yapılır: Öğenin Genişlik Özelliklerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="862fd-102">How to: Set the Width Properties of an Element</span></span>
## <a name="example"></a><span data-ttu-id="862fd-103">Örnek</span><span class="sxs-lookup"><span data-stu-id="862fd-103">Example</span></span>  
 <span data-ttu-id="862fd-104">Bu örnek, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]içindeki dört Genişlik ile ilgili özellikler arasındaki işleme davranışlarındaki farkları görsel olarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="862fd-104">This example visually shows the differences in rendering behavior among the four width-related properties in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="862fd-105"><xref:System.Windows.FrameworkElement> sınıfı, bir öğenin genişlik özelliklerini tanımlayan dört özellik sunar.</span><span class="sxs-lookup"><span data-stu-id="862fd-105">The <xref:System.Windows.FrameworkElement> class exposes four properties that describe the width characteristics of an element.</span></span> <span data-ttu-id="862fd-106">Bu dört Özellik çakışabilir ve ne zaman, öncelik veren değer aşağıdaki şekilde belirlenir: <xref:System.Windows.FrameworkElement.MinWidth%2A> değeri <xref:System.Windows.FrameworkElement.MaxWidth%2A> değerine göre önceliklidir ve bu da <xref:System.Windows.FrameworkElement.Width%2A> değerinden önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="862fd-106">These four properties can conflict, and when they do, the value that takes precedence is determined as follows: the <xref:System.Windows.FrameworkElement.MinWidth%2A> value takes precedence over the <xref:System.Windows.FrameworkElement.MaxWidth%2A> value, which in turn takes precedence over the <xref:System.Windows.FrameworkElement.Width%2A> value.</span></span> <span data-ttu-id="862fd-107">Dördüncü bir özellik <xref:System.Windows.FrameworkElement.ActualWidth%2A>, salt okunurdur ve düzen süreciyle etkileşimler tarafından belirlendiği şekilde gerçek genişliği raporlar.</span><span class="sxs-lookup"><span data-stu-id="862fd-107">A fourth property, <xref:System.Windows.FrameworkElement.ActualWidth%2A>, is read-only, and reports the actual width as determined by interactions with the layout process.</span></span>  
  
 <span data-ttu-id="862fd-108">Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnekler, <xref:System.Windows.Controls.Canvas>alt öğesi olarak bir <xref:System.Windows.Shapes.Rectangle> öğesi (`rect1`) çizer.</span><span class="sxs-lookup"><span data-stu-id="862fd-108">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples draw a <xref:System.Windows.Shapes.Rectangle> element (`rect1`) as a child of <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="862fd-109">Bir <xref:System.Windows.Shapes.Rectangle> Width özelliklerini <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>ve <xref:System.Windows.FrameworkElement.Width%2A>özellik değerlerini temsil eden bir dizi <xref:System.Windows.Controls.ListBox> öğesi kullanarak değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="862fd-109">You can change the width properties of a <xref:System.Windows.Shapes.Rectangle> by using a series of <xref:System.Windows.Controls.ListBox> elements that represent the property values of <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>, and <xref:System.Windows.FrameworkElement.Width%2A>.</span></span> <span data-ttu-id="862fd-110">Bu şekilde, her bir özelliğin önceliği görsel olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="862fd-110">In this manner, the precedence of each property is visually displayed.</span></span>  
  
 [!code-xaml[WidthMinWidthMaxWidth#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#1)]  
[!code-xaml[WidthMinWidthMaxWidth#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="862fd-111">Aşağıdaki arka plan kod örnekleri <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> olayının harekete geçirme olaylarını işler.</span><span class="sxs-lookup"><span data-stu-id="862fd-111">The following code-behind examples handle the events that the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event raises.</span></span> <span data-ttu-id="862fd-112">Her özel yöntem <xref:System.Windows.Controls.ListBox>girişi alır, değeri bir <xref:System.Double>ayrıştırır ve değeri belirtilen genişlik ile ilgili özelliğe uygular.</span><span class="sxs-lookup"><span data-stu-id="862fd-112">Each custom method takes the input from the <xref:System.Windows.Controls.ListBox>, parses the value as a <xref:System.Double>, and applies the value to the specified width-related property.</span></span> <span data-ttu-id="862fd-113">Width değerleri Ayrıca bir dizeye dönüştürülür ve çeşitli <xref:System.Windows.Controls.TextBlock> öğelerine yazılır (Bu öğelerin tanımı seçili XAML 'de gösterilmez).</span><span class="sxs-lookup"><span data-stu-id="862fd-113">The width values are also converted to a string and written to various <xref:System.Windows.Controls.TextBlock> elements (definition of those elements is not shown in the selected XAML).</span></span>  
  
 [!code-csharp[WidthMinWidthMaxWidth#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml.cs#3)]
 [!code-vb[WidthMinWidthMaxWidth#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WidthMinWidthMaxWidth/VisualBasic/Window1.xaml.vb#3)]  
  
 <span data-ttu-id="862fd-114">Tüm örnek için bkz. [Width özellikleri karşılaştırma örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Elements/WidthProperties).</span><span class="sxs-lookup"><span data-stu-id="862fd-114">For the complete sample, see [Width Properties Comparison Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Elements/WidthProperties).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="862fd-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="862fd-115">See also</span></span>

- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.ActualWidth%2A>
- <xref:System.Windows.FrameworkElement.MaxWidth%2A>
- <xref:System.Windows.FrameworkElement.MinWidth%2A>
- <xref:System.Windows.FrameworkElement.Width%2A>
- [<span data-ttu-id="862fd-116">Panellere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="862fd-116">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="862fd-117">Öğenin Yükseklik Özelliklerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="862fd-117">Set the Height Properties of an Element</span></span>](how-to-set-the-height-properties-of-an-element.md)
- [<span data-ttu-id="862fd-118">Width özellikleri karşılaştırma örneği</span><span class="sxs-lookup"><span data-stu-id="862fd-118">Width Properties Comparison Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Elements/WidthProperties)
