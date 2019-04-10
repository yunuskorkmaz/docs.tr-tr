---
title: 'Nasıl yapılır: Basit veya Karmaşık TreeViews Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- TreeView control [WPF], creating
- Control class [WPF], TreeView [WPF], creating
ms.assetid: 1defbb78-b8e7-4c0e-b650-576453ac828d
ms.openlocfilehash: 7edb4933ebcc0f0d2cb02754238c2342ee9dd4a2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59205153"
---
# <a name="how-to-create-simple-or-complex-treeviews"></a><span data-ttu-id="f6887-102">Nasıl yapılır: Basit veya Karmaşık TreeViews Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f6887-102">How to: Create Simple or Complex TreeViews</span></span>
<span data-ttu-id="f6887-103">Bu örnek, basit veya karmaşık oluşturma işlemi gösterilmektedir <xref:System.Windows.Controls.TreeView> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="f6887-103">This example shows how to create simple or complex <xref:System.Windows.Controls.TreeView> controls.</span></span>  
  
 <span data-ttu-id="f6887-104">A <xref:System.Windows.Controls.TreeView> hiyerarşisinden oluşur <xref:System.Windows.Controls.TreeViewItem> gibi basit metin dizelerini ve ayrıca daha karmaşık içerik içerebilen denetimleri <xref:System.Windows.Controls.Button> denetimleri veya <xref:System.Windows.Controls.StackPanel> katıştırılmış içeriğe sahip.</span><span class="sxs-lookup"><span data-stu-id="f6887-104">A <xref:System.Windows.Controls.TreeView> consists of a hierarchy of <xref:System.Windows.Controls.TreeViewItem> controls, which can contain simple text strings and also more complex content, such as <xref:System.Windows.Controls.Button> controls or a <xref:System.Windows.Controls.StackPanel> with embedded content.</span></span> <span data-ttu-id="f6887-105">Açıkça tanımlayabilirsiniz <xref:System.Windows.Controls.TreeView> içerik veya bir veri kaynağı içerik sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="f6887-105">You can explicitly define the <xref:System.Windows.Controls.TreeView> content or a data source can provide the content.</span></span> <span data-ttu-id="f6887-106">Bu konu, bu kavramları örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="f6887-106">This topic provides examples of these concepts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6887-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="f6887-107">Example</span></span>  
 <span data-ttu-id="f6887-108"><xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> Özelliği <xref:System.Windows.Controls.TreeViewItem> içeriğin bulunduğu, <xref:System.Windows.Controls.TreeView> için bu öğeyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f6887-108">The <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> property of the <xref:System.Windows.Controls.TreeViewItem> contains the content that the <xref:System.Windows.Controls.TreeView> displays for that item.</span></span> <span data-ttu-id="f6887-109">A <xref:System.Windows.Controls.TreeViewItem> bulundurabilirsiniz <xref:System.Windows.Controls.TreeViewItem> denetimler ve onun alt öğeleri olarak kullanarak bu alt öğeleri tanımlayabilirsiniz <xref:System.Windows.Controls.ItemsControl.Items%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="f6887-109">A <xref:System.Windows.Controls.TreeViewItem> can also have <xref:System.Windows.Controls.TreeViewItem> controls as its child elements and you can define these child elements by using the <xref:System.Windows.Controls.ItemsControl.Items%2A> property.</span></span>  
  
 <span data-ttu-id="f6887-110">Aşağıdaki örnek, açıkça tanımlamak gösterilmektedir <xref:System.Windows.Controls.TreeViewItem> ayarlayarak içerik <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> özelliğini bir metin dizesi.</span><span class="sxs-lookup"><span data-stu-id="f6887-110">The following example shows how to explicitly define <xref:System.Windows.Controls.TreeViewItem> content by setting the <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> property to a text string.</span></span>  
  
 [!code-xaml[TreeViewSimple#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#1)]  
  
 <span data-ttu-id="f6887-111">Aşağıdaki örnek Göster alt öğeleri tanımlamak nasıl bir <xref:System.Windows.Controls.TreeViewItem> tanımlayarak <xref:System.Windows.Controls.ItemsControl.Items%2A> olan <xref:System.Windows.Controls.Button> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="f6887-111">The following example show how to define child elements of a <xref:System.Windows.Controls.TreeViewItem> by defining <xref:System.Windows.Controls.ItemsControl.Items%2A> that are <xref:System.Windows.Controls.Button> controls.</span></span>  
  
 [!code-xaml[TreeViewSimple#3](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#3)]  
  
 <span data-ttu-id="f6887-112">Aşağıdaki örnek nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Controls.TreeView> burada bir <xref:System.Windows.Data.XmlDataProvider> sağlar <xref:System.Windows.Controls.TreeViewItem> içeriği ve <xref:System.Windows.HierarchicalDataTemplate> içeriğinin görünümünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f6887-112">The following example shows how to create a <xref:System.Windows.Controls.TreeView> where an <xref:System.Windows.Data.XmlDataProvider> provides <xref:System.Windows.Controls.TreeViewItem> content and a <xref:System.Windows.HierarchicalDataTemplate> defines the appearance of the content.</span></span>  
  
 [!code-xaml[TreeViewSimple#6](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#6)]  
  
 [!code-xaml[TreeViewSimple#7](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#7)]  
  
 [!code-xaml[TreeViewSimple#5](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#5)]  
  
 <span data-ttu-id="f6887-113">Aşağıdaki örnek nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Controls.TreeView> burada <xref:System.Windows.Controls.TreeViewItem> içeriği <xref:System.Windows.Controls.DockPanel> katıştırılmış içeriğe sahip denetimler.</span><span class="sxs-lookup"><span data-stu-id="f6887-113">The following example shows how to create a <xref:System.Windows.Controls.TreeView> where the <xref:System.Windows.Controls.TreeViewItem> content contains <xref:System.Windows.Controls.DockPanel> controls that have embedded content.</span></span>  
  
 [!code-xaml[TreeViewSimple#9](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#9)]  
  
## <a name="see-also"></a><span data-ttu-id="f6887-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6887-114">See also</span></span>

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [<span data-ttu-id="f6887-115">TreeView Genel Bakışı</span><span class="sxs-lookup"><span data-stu-id="f6887-115">TreeView Overview</span></span>](treeview-overview.md)
- [<span data-ttu-id="f6887-116">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="f6887-116">How-to Topics</span></span>](treeview-how-to-topics.md)
