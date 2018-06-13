---
title: 'Nasıl yapılır: CheckBox ile ListViewItems Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], ListView
- controls [WPF], CheckBox
- ListView controls [WPF], CheckBox controls
- CheckBox control [WPF], ListView control
ms.assetid: f6d66c7f-906c-4f65-a55a-0ede9d00e26a
ms.openlocfilehash: 424bc25f9c584017d80ba1c8f1517211595fd247
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552681"
---
# <a name="how-to-create-listviewitems-with-a-checkbox"></a><span data-ttu-id="a6029-102">Nasıl yapılır: CheckBox ile ListViewItems Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a6029-102">How to: Create ListViewItems with a CheckBox</span></span>
<span data-ttu-id="a6029-103">Bu örnek bir sütunu görüntülemek nasıl gösterir <xref:System.Windows.Controls.CheckBox> denetimlerini bir <xref:System.Windows.Controls.ListView> kullanan denetim bir <xref:System.Windows.Controls.GridView>.</span><span class="sxs-lookup"><span data-stu-id="a6029-103">This example shows how to display a column of <xref:System.Windows.Controls.CheckBox> controls in a <xref:System.Windows.Controls.ListView> control that uses a <xref:System.Windows.Controls.GridView>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6029-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="a6029-104">Example</span></span>  
 <span data-ttu-id="a6029-105">İçeren bir sütun oluşturmak için <xref:System.Windows.Controls.CheckBox> denetimlerini bir <xref:System.Windows.Controls.ListView>, oluşturma bir <xref:System.Windows.DataTemplate> içeren bir <xref:System.Windows.Controls.CheckBox>.</span><span class="sxs-lookup"><span data-stu-id="a6029-105">To create a column that contains <xref:System.Windows.Controls.CheckBox> controls in a <xref:System.Windows.Controls.ListView>, create a <xref:System.Windows.DataTemplate> that contains a <xref:System.Windows.Controls.CheckBox>.</span></span> <span data-ttu-id="a6029-106">Ardından <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> , bir <xref:System.Windows.Controls.GridViewColumn> için <xref:System.Windows.DataTemplate>.</span><span class="sxs-lookup"><span data-stu-id="a6029-106">Then set the <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> of a <xref:System.Windows.Controls.GridViewColumn> to the <xref:System.Windows.DataTemplate>.</span></span>  
  
 <span data-ttu-id="a6029-107">Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.DataTemplate> içeren bir <xref:System.Windows.Controls.CheckBox>.</span><span class="sxs-lookup"><span data-stu-id="a6029-107">The following example shows a <xref:System.Windows.DataTemplate> that contains a <xref:System.Windows.Controls.CheckBox>.</span></span> <span data-ttu-id="a6029-108">Örnek bağlar <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> özelliği <xref:System.Windows.Controls.CheckBox> için <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> özellik değerinin <xref:System.Windows.Controls.ListViewItem> , içerir.</span><span class="sxs-lookup"><span data-stu-id="a6029-108">The example binds the <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> property of the <xref:System.Windows.Controls.CheckBox> to the <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> property value of the <xref:System.Windows.Controls.ListViewItem> that contains it.</span></span> <span data-ttu-id="a6029-109">Bu nedenle, <xref:System.Windows.Controls.ListViewItem> içeren <xref:System.Windows.Controls.CheckBox> seçili <xref:System.Windows.Controls.CheckBox> denetlenir.</span><span class="sxs-lookup"><span data-stu-id="a6029-109">Therefore, when the <xref:System.Windows.Controls.ListViewItem> that contains the <xref:System.Windows.Controls.CheckBox> is selected, the <xref:System.Windows.Controls.CheckBox> is checked.</span></span>  
  
 [!code-xaml[ListViewChkBox#CheckBoxDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#checkboxdatatemplate)]  
  
 <span data-ttu-id="a6029-110">Aşağıdaki örnek, bir sütun oluşturmak nasıl gösterir <xref:System.Windows.Controls.CheckBox> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="a6029-110">The following example shows how to create a column of <xref:System.Windows.Controls.CheckBox> controls.</span></span> <span data-ttu-id="a6029-111">Örnek kümeleri sütunu yapmak için <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> özelliği <xref:System.Windows.Controls.GridViewColumn> için <xref:System.Windows.DataTemplate>.</span><span class="sxs-lookup"><span data-stu-id="a6029-111">To make the column, the example sets the <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> property of the <xref:System.Windows.Controls.GridViewColumn> to the <xref:System.Windows.DataTemplate>.</span></span>  
  
 [!code-xaml[ListViewChkBox#GridViewColumnCheckBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#gridviewcolumncheckbox)]  
  
## <a name="see-also"></a><span data-ttu-id="a6029-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a6029-112">See Also</span></span>  
 <xref:System.Windows.Controls.Control>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="a6029-113">ListView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a6029-113">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="a6029-114">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="a6029-114">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="a6029-115">GridView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a6029-115">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
