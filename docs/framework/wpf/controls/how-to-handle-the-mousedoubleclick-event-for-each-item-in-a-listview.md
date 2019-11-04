---
title: "Nasıl yapılır: ListView'daki Her Öğe için MouseDoubleClick Olayını İşleme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 25308ee87fb387787e20c8a8887ae8e4e60742b9
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460221"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a><span data-ttu-id="a7abe-102">Nasıl yapılır: ListView'daki Her Öğe için MouseDoubleClick Olayını İşleme</span><span class="sxs-lookup"><span data-stu-id="a7abe-102">How to: Handle the MouseDoubleClick Event for Each Item in a ListView</span></span>
<span data-ttu-id="a7abe-103"><xref:System.Windows.Controls.ListView>bir öğeye yönelik bir olayı işlemek için, her bir <xref:System.Windows.Controls.ListViewItem>bir olay işleyicisi eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a7abe-103">To handle an event for an item in a <xref:System.Windows.Controls.ListView>, you need to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span> <span data-ttu-id="a7abe-104">Bir <xref:System.Windows.Controls.ListView> bir veri kaynağına bağlandığında, açıkça bir <xref:System.Windows.Controls.ListViewItem>oluşturmazsınız, ancak <xref:System.Windows.Controls.ListViewItem>stiline <xref:System.Windows.EventSetter> ekleyerek her öğe için olayı işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7abe-104">When a <xref:System.Windows.Controls.ListView> is bound to a data source, you don't explicitly create a <xref:System.Windows.Controls.ListViewItem>, but you can handle the event for each item by adding an <xref:System.Windows.EventSetter> to a style of a <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7abe-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="a7abe-105">Example</span></span>  
 <span data-ttu-id="a7abe-106">Aşağıdaki örnek, bir veri-bağlantılı <xref:System.Windows.Controls.ListView> oluşturur ve her <xref:System.Windows.Controls.ListViewItem>bir olay işleyicisi eklemek için bir <xref:System.Windows.Style> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a7abe-106">The following example creates a data-bound <xref:System.Windows.Controls.ListView> and creates a <xref:System.Windows.Style> to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="a7abe-107">Aşağıdaki örnek <xref:System.Windows.Controls.Control.MouseDoubleClick> olayını işler.</span><span class="sxs-lookup"><span data-stu-id="a7abe-107">The following example handles the <xref:System.Windows.Controls.Control.MouseDoubleClick> event.</span></span>  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
> <span data-ttu-id="a7abe-108">Bir <xref:System.Windows.Controls.ListView> veri kaynağına bağlamak yaygın olsa da, açıkça bir <xref:System.Windows.Controls.ListViewItem>oluşturup oluşturmasanız bile, veri bağlama olmayan bir <xref:System.Windows.Controls.ListView> her bir <xref:System.Windows.Controls.ListViewItem> bir olay işleyicisi eklemek için bir stil kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7abe-108">Although it is most common to bind a <xref:System.Windows.Controls.ListView> to a data source, you can use a style to add an event handler to each <xref:System.Windows.Controls.ListViewItem> in a non-data-bound <xref:System.Windows.Controls.ListView> regardless of whether you explicitly create a <xref:System.Windows.Controls.ListViewItem>.</span></span>  <span data-ttu-id="a7abe-109">Açık ve örtük olarak oluşturulmuş <xref:System.Windows.Controls.ListViewItem> denetimleri hakkında daha fazla bilgi için bkz. <xref:System.Windows.Controls.ItemsControl>.</span><span class="sxs-lookup"><span data-stu-id="a7abe-109">For more information about explicitly and implicitly created <xref:System.Windows.Controls.ListViewItem> controls, see <xref:System.Windows.Controls.ItemsControl>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7abe-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7abe-110">See also</span></span>

- <xref:System.Xml.XmlElement>
- [<span data-ttu-id="a7abe-111">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a7abe-111">Data Binding Overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="a7abe-112">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a7abe-112">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="a7abe-113">XMLDataProvider ve XPath Sorgularını Kullanarak XML Verilerine Bağlama</span><span class="sxs-lookup"><span data-stu-id="a7abe-113">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [<span data-ttu-id="a7abe-114">ListView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a7abe-114">ListView Overview</span></span>](listview-overview.md)
