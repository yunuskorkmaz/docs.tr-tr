---
title: 'Nasıl yapılır: Tuval Konumlandırma Özelliklerini Alma veya Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Canvas control [WPF], setting positioning properties
ms.assetid: 1636b950-2b5a-4507-8a10-c5034cc58b1c
ms.openlocfilehash: 294b49d427a67da849ce930cf29a48f1735bf135
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33551986"
---
# <a name="how-to-get-or-set-canvas-positioning-properties"></a><span data-ttu-id="4e6db-102">Nasıl yapılır: Tuval Konumlandırma Özelliklerini Alma veya Ayarlama</span><span class="sxs-lookup"><span data-stu-id="4e6db-102">How to: Get or Set Canvas Positioning Properties</span></span>
<span data-ttu-id="4e6db-103">Bu örnek konumlandırma yöntemlerini kullanmayı gösterir <xref:System.Windows.Controls.Canvas> alt konumlandırmak için öğesi.</span><span class="sxs-lookup"><span data-stu-id="4e6db-103">This example shows how to use the positioning methods of the <xref:System.Windows.Controls.Canvas> element to position child content.</span></span> <span data-ttu-id="4e6db-104">Bu örnek içeriği kullanan bir <xref:System.Windows.Controls.ListBoxItem> temsil etmek için konumlandırma değerler ve değerlerin örneğine dönüştürür <xref:System.Double>, konumlandırma için gerekli bir bağımsız değişken olduğu.</span><span class="sxs-lookup"><span data-stu-id="4e6db-104">This example uses content in a <xref:System.Windows.Controls.ListBoxItem> to represent positioning values and converts the values into instances of <xref:System.Double>, which is a required argument for positioning.</span></span> <span data-ttu-id="4e6db-105">Değerler sonra dizelere geri dönüştürülür ve metin olarak görüntülenen bir <xref:System.Windows.Controls.TextBlock> kullanarak öğesi <xref:System.Windows.Controls.Canvas.GetLeft%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4e6db-105">The values are then converted back into strings and displayed as text in a <xref:System.Windows.Controls.TextBlock> element by using the <xref:System.Windows.Controls.Canvas.GetLeft%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e6db-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="4e6db-106">Example</span></span>  
 <span data-ttu-id="4e6db-107">Aşağıdaki örnekte bir <xref:System.Windows.Controls.ListBox> seçilebilir on sahip öğe <xref:System.Windows.Controls.ListBoxItem> öğeleri.</span><span class="sxs-lookup"><span data-stu-id="4e6db-107">The following example creates a <xref:System.Windows.Controls.ListBox> element that has eleven selectable <xref:System.Windows.Controls.ListBoxItem> elements.</span></span> <span data-ttu-id="4e6db-108"><xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> Olay tetikleyicileri `ChangeLeft` izleyen kod bloğunun tanımladığı özel yöntem.</span><span class="sxs-lookup"><span data-stu-id="4e6db-108">The <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event triggers the `ChangeLeft` custom method, which the subsequent code block defines.</span></span>  
  
 <span data-ttu-id="4e6db-109">Her <xref:System.Windows.Controls.ListBoxItem> temsil eden bir <xref:System.Double> bir bağımsız değişken değeri, <xref:System.Windows.Controls.Canvas.SetLeft%2A> yöntemi <xref:System.Windows.Controls.Canvas> kabul eder.</span><span class="sxs-lookup"><span data-stu-id="4e6db-109">Each <xref:System.Windows.Controls.ListBoxItem> represents a <xref:System.Double> value, which is one of the arguments that the <xref:System.Windows.Controls.Canvas.SetLeft%2A> method of <xref:System.Windows.Controls.Canvas> accepts.</span></span> <span data-ttu-id="4e6db-110">Kullanmak için bir <xref:System.Windows.Controls.ListBoxItem> örneğini temsil etmek için <xref:System.Double>, dönüştürmeniz gerekir <xref:System.Windows.Controls.ListBoxItem> doğru veri türü.</span><span class="sxs-lookup"><span data-stu-id="4e6db-110">In order to use a <xref:System.Windows.Controls.ListBoxItem> to represent an instance of <xref:System.Double>, you must first convert the <xref:System.Windows.Controls.ListBoxItem> to the correct data type.</span></span>  
  
 [!code-xaml[CanvasPositioningProperties#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="4e6db-111">Bir kullanıcı değiştiğinde <xref:System.Windows.Controls.ListBox> seçimi çağırılır `ChangeLeft` özel yöntem.</span><span class="sxs-lookup"><span data-stu-id="4e6db-111">When a user changes the <xref:System.Windows.Controls.ListBox> selection, it invokes the `ChangeLeft` custom method.</span></span> <span data-ttu-id="4e6db-112">Bu yöntem geçirir <xref:System.Windows.Controls.ListBoxItem> için bir <xref:System.Windows.LengthConverter> dönüştürür Nesne <xref:System.Windows.Controls.ContentControl.Content%2A> , bir <xref:System.Windows.Controls.ListBoxItem> örneğine <xref:System.Double> (Bu değer için zaten dönüştürülmüş bildirimi bir <xref:System.String> kullanarak <xref:System.Windows.Controls.Control.ToString%2A> yöntem).</span><span class="sxs-lookup"><span data-stu-id="4e6db-112">This method passes the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.Windows.LengthConverter> object, which converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of a <xref:System.Windows.Controls.ListBoxItem> to an instance of <xref:System.Double> (notice that this value has already been converted to a <xref:System.String> by using the <xref:System.Windows.Controls.Control.ToString%2A> method).</span></span> <span data-ttu-id="4e6db-113">Bu değer daha sonra geri geçirilir <xref:System.Windows.Controls.Canvas.SetLeft%2A> ve <xref:System.Windows.Controls.Canvas.GetLeft%2A> yöntemlerinin <xref:System.Windows.Controls.Canvas> konumunu değiştirmek için `text1` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="4e6db-113">This value is then passed back to the <xref:System.Windows.Controls.Canvas.SetLeft%2A> and <xref:System.Windows.Controls.Canvas.GetLeft%2A> methods of <xref:System.Windows.Controls.Canvas> in order to change the position of the `text1` object.</span></span>  
  
 [!code-csharp[CanvasPositioningProperties#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml.cs#2)]
 [!code-vb[CanvasPositioningProperties#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasPositioningProperties/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="4e6db-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4e6db-114">See Also</span></span>  
 <xref:System.Windows.Controls.Canvas>  
 <xref:System.Windows.Controls.ListBoxItem>  
 <xref:System.Windows.LengthConverter>  
 [<span data-ttu-id="4e6db-115">Panellere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4e6db-115">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
