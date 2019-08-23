---
title: "Nasıl yapılır: ListView'daki Her Öğe için MouseDoubleClick Olayını İşleme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 7e51c810a2e1e4bf4157aa1311255c5547021b60
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962072"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a><span data-ttu-id="da719-102">Nasıl yapılır: ListView'daki Her Öğe için MouseDoubleClick Olayını İşleme</span><span class="sxs-lookup"><span data-stu-id="da719-102">How to: Handle the MouseDoubleClick Event for Each Item in a ListView</span></span>
<span data-ttu-id="da719-103">İçindeki <xref:System.Windows.Controls.ListView>bir öğeye yönelik bir olayı işlemek için, her birine <xref:System.Windows.Controls.ListViewItem>bir olay işleyicisi eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="da719-103">To handle an event for an item in a <xref:System.Windows.Controls.ListView>, you need to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span> <span data-ttu-id="da719-104">Bir <xref:System.Windows.Controls.ListView> veri kaynağına bağlandığında, açıkça bir <xref:System.Windows.Controls.ListViewItem>oluşturmazsınız, ancak bir stil <xref:System.Windows.EventSetter> <xref:System.Windows.Controls.ListViewItem>öğesine ekleyerek her öğe için olayını işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da719-104">When a <xref:System.Windows.Controls.ListView> is bound to a data source, you don't explicitly create a <xref:System.Windows.Controls.ListViewItem>, but you can handle the event for each item by adding an <xref:System.Windows.EventSetter> to a style of a <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da719-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="da719-105">Example</span></span>  
 <span data-ttu-id="da719-106">Aşağıdaki örnek, bir veri sınırı <xref:System.Windows.Controls.ListView> oluşturur ve her birine <xref:System.Windows.Controls.ListViewItem>bir <xref:System.Windows.Style> olay işleyicisi eklemek için bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="da719-106">The following example creates a data-bound <xref:System.Windows.Controls.ListView> and creates a <xref:System.Windows.Style> to add an event handler to each <xref:System.Windows.Controls.ListViewItem>.</span></span>  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="da719-107">Aşağıdaki örnek <xref:System.Windows.Controls.Control.MouseDoubleClick> olayı işler.</span><span class="sxs-lookup"><span data-stu-id="da719-107">The following example handles the <xref:System.Windows.Controls.Control.MouseDoubleClick> event.</span></span>  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
> <span data-ttu-id="da719-108">Bir veri <xref:System.Windows.Controls.ListView> kaynağına bağlamak en yaygın olsa da, açıkça bir <xref:System.Windows.Controls.ListViewItem>oluşturup oluşturmasanız <xref:System.Windows.Controls.ListView> ne olursa olsun, her birine <xref:System.Windows.Controls.ListViewItem> bir olay işleyicisi eklemek için bir stil kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da719-108">Although it is most common to bind a <xref:System.Windows.Controls.ListView> to a data source, you can use a style to add an event handler to each <xref:System.Windows.Controls.ListViewItem> in a non-data-bound <xref:System.Windows.Controls.ListView> regardless of whether you explicitly create a <xref:System.Windows.Controls.ListViewItem>.</span></span>  <span data-ttu-id="da719-109">Açık ve örtük olarak oluşturulan <xref:System.Windows.Controls.ListViewItem> denetimler hakkında daha fazla bilgi için bkz <xref:System.Windows.Controls.ItemsControl>.</span><span class="sxs-lookup"><span data-stu-id="da719-109">For more information about explicitly and implicitly created <xref:System.Windows.Controls.ListViewItem> controls, see <xref:System.Windows.Controls.ItemsControl>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da719-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da719-110">See also</span></span>

- <xref:System.Xml.XmlElement>
- [<span data-ttu-id="da719-111">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="da719-111">Data Binding Overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="da719-112">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="da719-112">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="da719-113">XMLDataProvider ve XPath Sorgularını Kullanarak XML Verilerine Bağlama</span><span class="sxs-lookup"><span data-stu-id="da719-113">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [<span data-ttu-id="da719-114">ListView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="da719-114">ListView Overview</span></span>](listview-overview.md)
