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
ms.openlocfilehash: a5ed67ba20176398a863a1e9826b1eab71b182f2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096881"
---
# <a name="how-to-set-the-width-properties-of-an-element"></a><span data-ttu-id="4e128-102">Nasıl yapılır: Öğenin Genişlik Özelliklerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="4e128-102">How to: Set the Width Properties of an Element</span></span>
## <a name="example"></a><span data-ttu-id="4e128-103">Örnek</span><span class="sxs-lookup"><span data-stu-id="4e128-103">Example</span></span>  
 <span data-ttu-id="4e128-104">Bu örnek, görsel olarak işleme davranışı dört genişliği ile ilgili özellikleri arasında farklılıklar gösterir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4e128-104">This example visually shows the differences in rendering behavior among the four width-related properties in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="4e128-105"><xref:System.Windows.FrameworkElement> Sınıfı, bir öğenin genişlik özelliklerini tanımlayan dört özelliği sunar.</span><span class="sxs-lookup"><span data-stu-id="4e128-105">The <xref:System.Windows.FrameworkElement> class exposes four properties that describe the width characteristics of an element.</span></span> <span data-ttu-id="4e128-106">Bu dört özellik çakışabilir ve bunu yaptıklarında önceliklidir değeri aşağıdaki şekilde belirlenir: <xref:System.Windows.FrameworkElement.MinWidth%2A> değeri önceliklidir <xref:System.Windows.FrameworkElement.MaxWidth%2A> sırayla önceliklidir değeri <xref:System.Windows.FrameworkElement.Width%2A> değeri.</span><span class="sxs-lookup"><span data-stu-id="4e128-106">These four properties can conflict, and when they do, the value that takes precedence is determined as follows: the <xref:System.Windows.FrameworkElement.MinWidth%2A> value takes precedence over the <xref:System.Windows.FrameworkElement.MaxWidth%2A> value, which in turn takes precedence over the <xref:System.Windows.FrameworkElement.Width%2A> value.</span></span> <span data-ttu-id="4e128-107">Dördüncü bir özellik <xref:System.Windows.FrameworkElement.ActualWidth%2A>, salt okunur ve düzen işlemine etkileşim tarafından belirlendiği gerçek genişliğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="4e128-107">A fourth property, <xref:System.Windows.FrameworkElement.ActualWidth%2A>, is read-only, and reports the actual width as determined by interactions with the layout process.</span></span>  
  
 <span data-ttu-id="4e128-108">Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnekler çizmek bir <xref:System.Windows.Shapes.Rectangle> öğesi (`rect1`) bir alt öğesi olarak <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="4e128-108">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples draw a <xref:System.Windows.Shapes.Rectangle> element (`rect1`) as a child of <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="4e128-109">Genişlik özelliklerini değiştirmek bir <xref:System.Windows.Shapes.Rectangle> bir dizi kullanarak <xref:System.Windows.Controls.ListBox> özellik değerlerini temsil eden öğeler <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>, ve <xref:System.Windows.FrameworkElement.Width%2A>.</span><span class="sxs-lookup"><span data-stu-id="4e128-109">You can change the width properties of a <xref:System.Windows.Shapes.Rectangle> by using a series of <xref:System.Windows.Controls.ListBox> elements that represent the property values of <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>, and <xref:System.Windows.FrameworkElement.Width%2A>.</span></span> <span data-ttu-id="4e128-110">Bu şekilde, her bir özellik önceliğini görsel olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4e128-110">In this manner, the precedence of each property is visually displayed.</span></span>  
  
 [!code-xaml[WidthMinWidthMaxWidth#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#1)]  
[!code-xaml[WidthMinWidthMaxWidth#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="4e128-111">Aşağıdaki arka plan kod örnekleri olaylarını işlemek, <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> olayını başlatır.</span><span class="sxs-lookup"><span data-stu-id="4e128-111">The following code-behind examples handle the events that the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event raises.</span></span> <span data-ttu-id="4e128-112">Özel yöntemler girişten alır <xref:System.Windows.Controls.ListBox>, değer olarak ayrıştırır bir <xref:System.Double>ve belirtilen genişlik ilgili özellik için değer geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4e128-112">Each custom method takes the input from the <xref:System.Windows.Controls.ListBox>, parses the value as a <xref:System.Double>, and applies the value to the specified width-related property.</span></span> <span data-ttu-id="4e128-113">Genişlik değerleri de bir dizeye dönüştürülür ve çeşitli yazılan <xref:System.Windows.Controls.TextBlock> öğeleri (söz konusu öğelerin tanımı içinde seçili XAML gösterilmez).</span><span class="sxs-lookup"><span data-stu-id="4e128-113">The width values are also converted to a string and written to various <xref:System.Windows.Controls.TextBlock> elements (definition of those elements is not shown in the selected XAML).</span></span>  
  
 [!code-csharp[WidthMinWidthMaxWidth#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml.cs#3)]
 [!code-vb[WidthMinWidthMaxWidth#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WidthMinWidthMaxWidth/VisualBasic/Window1.xaml.vb#3)]  
  
 <span data-ttu-id="4e128-114">Tam bir örnek için bkz. [genişlik özelliklerini karşılaştırma örneği](https://go.microsoft.com/fwlink/?LinkID=160050).</span><span class="sxs-lookup"><span data-stu-id="4e128-114">For the complete sample, see [Width Properties Comparison Sample](https://go.microsoft.com/fwlink/?LinkID=160050).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e128-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e128-115">See also</span></span>

- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.ActualWidth%2A>
- <xref:System.Windows.FrameworkElement.MaxWidth%2A>
- <xref:System.Windows.FrameworkElement.MinWidth%2A>
- <xref:System.Windows.FrameworkElement.Width%2A>
- [<span data-ttu-id="4e128-116">Panellere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4e128-116">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="4e128-117">Öğenin Yükseklik Özelliklerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="4e128-117">Set the Height Properties of an Element</span></span>](how-to-set-the-height-properties-of-an-element.md)
- [<span data-ttu-id="4e128-118">Genişlik özelliklerini karşılaştırma örneği</span><span class="sxs-lookup"><span data-stu-id="4e128-118">Width Properties Comparison Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160050)
