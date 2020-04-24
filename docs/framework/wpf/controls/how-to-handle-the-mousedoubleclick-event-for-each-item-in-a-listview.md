---
title: "Nasıl yapılır: ListView'daki Her Öğe için MouseDoubleClick Olayını İşleme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 7bbc7bad36b3b1f2c92065e5f5699e5a86ac6189
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646105"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a><span data-ttu-id="aa623-102">Nasıl yapılır: ListView'daki Her Öğe için MouseDoubleClick Olayını İşleme</span><span class="sxs-lookup"><span data-stu-id="aa623-102">How to: Handle the MouseDoubleClick Event for Each Item in a ListView</span></span>
<span data-ttu-id="aa623-103">Bir öğenin olaylarını işlemek <xref:System.Windows.Controls.ListView>için, her <xref:System.Windows.Controls.ListViewItem>birine bir olay işleyicisi eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="aa623-103">To handle an event for an item in a <xref:System.Windows.Controls.ListView>, you need to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span> <span data-ttu-id="aa623-104">A <xref:System.Windows.Controls.ListView> bir veri kaynağına bağlandığında, açıkça bir <xref:System.Windows.Controls.ListViewItem>, ancak bir <xref:System.Windows.EventSetter> . <xref:System.Windows.Controls.ListViewItem></span><span class="sxs-lookup"><span data-stu-id="aa623-104">When a <xref:System.Windows.Controls.ListView> is bound to a data source, you don't explicitly create a <xref:System.Windows.Controls.ListViewItem>, but you can handle the event for each item by adding an <xref:System.Windows.EventSetter> to a style of a <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa623-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="aa623-105">Example</span></span>  
 <span data-ttu-id="aa623-106">Aşağıdaki örnek, veriye bağlı <xref:System.Windows.Controls.ListView> bir oluşturur <xref:System.Windows.Style> ve her <xref:System.Windows.Controls.ListViewItem>birine bir olay işleyicisi eklemek için bir tane oluşturur.</span><span class="sxs-lookup"><span data-stu-id="aa623-106">The following example creates a data-bound <xref:System.Windows.Controls.ListView> and creates a <xref:System.Windows.Style> to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="aa623-107">Aşağıdaki örnek <xref:System.Windows.Controls.Control.MouseDoubleClick> olayı işler.</span><span class="sxs-lookup"><span data-stu-id="aa623-107">The following example handles the <xref:System.Windows.Controls.Control.MouseDoubleClick> event.</span></span>  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
> <span data-ttu-id="aa623-108">Bir veri <xref:System.Windows.Controls.ListView> kaynağına a bağlamak en yaygın olsa da, açıkça bir tane oluşturup oluşturmadığınıza bakılmaksızın, her <xref:System.Windows.Controls.ListViewItem> birine veri ye bağlı <xref:System.Windows.Controls.ListView> olmayan bir olay işleyicisi eklemek için bir <xref:System.Windows.Controls.ListViewItem>stil kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa623-108">Although it is most common to bind a <xref:System.Windows.Controls.ListView> to a data source, you can use a style to add an event handler to each <xref:System.Windows.Controls.ListViewItem> in a non-data-bound <xref:System.Windows.Controls.ListView> regardless of whether you explicitly create a <xref:System.Windows.Controls.ListViewItem>.</span></span>  <span data-ttu-id="aa623-109">Açık ve örtülü olarak oluşturulan <xref:System.Windows.Controls.ListViewItem> denetimler <xref:System.Windows.Controls.ItemsControl>hakkında daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="aa623-109">For more information about explicitly and implicitly created <xref:System.Windows.Controls.ListViewItem> controls, see <xref:System.Windows.Controls.ItemsControl>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa623-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa623-110">See also</span></span>

- <xref:System.Xml.XmlElement>
- [<span data-ttu-id="aa623-111">Veri Bağlama Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="aa623-111">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="aa623-112">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="aa623-112">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="aa623-113">XMLDataProvider ve XPath Sorguları Kullanarak XML Verilerine Bağlama</span><span class="sxs-lookup"><span data-stu-id="aa623-113">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [<span data-ttu-id="aa623-114">ListView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="aa623-114">ListView Overview</span></span>](listview-overview.md)
