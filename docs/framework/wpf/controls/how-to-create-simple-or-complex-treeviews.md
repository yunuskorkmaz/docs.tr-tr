---
title: 'Nasıl yapılır: Basit veya Karmaşık TreeViews Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- TreeView control [WPF], creating
- Control class [WPF], TreeView [WPF], creating
ms.assetid: 1defbb78-b8e7-4c0e-b650-576453ac828d
ms.openlocfilehash: 54e9218ea1460a0c29d8b9d7b9c740c18ac7ab24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553004"
---
# <a name="how-to-create-simple-or-complex-treeviews"></a><span data-ttu-id="7313b-102">Nasıl yapılır: Basit veya Karmaşık TreeViews Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7313b-102">How to: Create Simple or Complex TreeViews</span></span>
<span data-ttu-id="7313b-103">Bu örnekte basit veya karmaşık oluşturulacağını gösterir <xref:System.Windows.Controls.TreeView> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="7313b-103">This example shows how to create simple or complex <xref:System.Windows.Controls.TreeView> controls.</span></span>  
  
 <span data-ttu-id="7313b-104">A <xref:System.Windows.Controls.TreeView> bir hiyerarşisinden oluşur <xref:System.Windows.Controls.TreeViewItem> basit metin dizelerini ve ayrıca daha karmaşık içerik gibi içerebilir denetimleri <xref:System.Windows.Controls.Button> denetimleri veya <xref:System.Windows.Controls.StackPanel> katıştırılmış içeriğe sahip.</span><span class="sxs-lookup"><span data-stu-id="7313b-104">A <xref:System.Windows.Controls.TreeView> consists of a hierarchy of <xref:System.Windows.Controls.TreeViewItem> controls, which can contain simple text strings and also more complex content, such as <xref:System.Windows.Controls.Button> controls or a <xref:System.Windows.Controls.StackPanel> with embedded content.</span></span> <span data-ttu-id="7313b-105">Açıkça tanımlayabilirsiniz <xref:System.Windows.Controls.TreeView> içerik veya bir veri kaynağı içeriği sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="7313b-105">You can explicitly define the <xref:System.Windows.Controls.TreeView> content or a data source can provide the content.</span></span> <span data-ttu-id="7313b-106">Bu konu bu kavramların örneklerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="7313b-106">This topic provides examples of these concepts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7313b-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="7313b-107">Example</span></span>  
 <span data-ttu-id="7313b-108"><xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> Özelliği <xref:System.Windows.Controls.TreeViewItem> içeriği, <xref:System.Windows.Controls.TreeView> bu öğe için görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7313b-108">The <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> property of the <xref:System.Windows.Controls.TreeViewItem> contains the content that the <xref:System.Windows.Controls.TreeView> displays for that item.</span></span> <span data-ttu-id="7313b-109">A <xref:System.Windows.Controls.TreeViewItem> da sahip olabilirsiniz <xref:System.Windows.Controls.TreeViewItem> ve alt öğeleri olarak denetimleri kullanarak bu alt öğeleri tanımlayabilirsiniz <xref:System.Windows.Controls.ItemsControl.Items%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="7313b-109">A <xref:System.Windows.Controls.TreeViewItem> can also have <xref:System.Windows.Controls.TreeViewItem> controls as its child elements and you can define these child elements by using the <xref:System.Windows.Controls.ItemsControl.Items%2A> property.</span></span>  
  
 <span data-ttu-id="7313b-110">Aşağıdaki örnek açıkça nasıl tanımlanacağı gösterilmektedir <xref:System.Windows.Controls.TreeViewItem> ayarlayarak içerik <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> özelliği için bir metin dizesi.</span><span class="sxs-lookup"><span data-stu-id="7313b-110">The following example shows how to explicitly define <xref:System.Windows.Controls.TreeViewItem> content by setting the <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> property to a text string.</span></span>  
  
 [!code-xaml[TreeViewSimple#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#1)]  
  
 <span data-ttu-id="7313b-111">Aşağıdaki örnek Göster alt öğeleri tanımlamak nasıl bir <xref:System.Windows.Controls.TreeViewItem> tanımlayarak <xref:System.Windows.Controls.ItemsControl.Items%2A> olan <xref:System.Windows.Controls.Button> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="7313b-111">The following example show how to define child elements of a <xref:System.Windows.Controls.TreeViewItem> by defining <xref:System.Windows.Controls.ItemsControl.Items%2A> that are <xref:System.Windows.Controls.Button> controls.</span></span>  
  
 [!code-xaml[TreeViewSimple#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#3)]  
  
 <span data-ttu-id="7313b-112">Aşağıdaki örnekte nasıl oluşturulacağını gösterir bir <xref:System.Windows.Controls.TreeView> burada bir <xref:System.Windows.Data.XmlDataProvider> sağlar <xref:System.Windows.Controls.TreeViewItem> içerik ve <xref:System.Windows.HierarchicalDataTemplate> içeriğinin görünümünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7313b-112">The following example shows how to create a <xref:System.Windows.Controls.TreeView> where an <xref:System.Windows.Data.XmlDataProvider> provides <xref:System.Windows.Controls.TreeViewItem> content and a <xref:System.Windows.HierarchicalDataTemplate> defines the appearance of the content.</span></span>  
  
 [!code-xaml[TreeViewSimple#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#6)]  
  
 [!code-xaml[TreeViewSimple#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#7)]  
  
 [!code-xaml[TreeViewSimple#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#5)]  
  
 <span data-ttu-id="7313b-113">Aşağıdaki örnekte nasıl oluşturulacağını gösterir bir <xref:System.Windows.Controls.TreeView> nerede <xref:System.Windows.Controls.TreeViewItem> içeriği <xref:System.Windows.Controls.DockPanel> katıştırılmış içeriğe sahip kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="7313b-113">The following example shows how to create a <xref:System.Windows.Controls.TreeView> where the <xref:System.Windows.Controls.TreeViewItem> content contains <xref:System.Windows.Controls.DockPanel> controls that have embedded content.</span></span>  
  
 [!code-xaml[TreeViewSimple#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#9)]  
  
## <a name="see-also"></a><span data-ttu-id="7313b-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7313b-114">See Also</span></span>  
 <xref:System.Windows.Controls.TreeView>  
 <xref:System.Windows.Controls.TreeViewItem>  
 [<span data-ttu-id="7313b-115">TreeView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7313b-115">TreeView Overview</span></span>](../../../../docs/framework/wpf/controls/treeview-overview.md)  
 [<span data-ttu-id="7313b-116">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="7313b-116">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)
