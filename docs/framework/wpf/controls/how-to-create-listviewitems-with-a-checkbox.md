---
title: 'Nasıl yapılır: CheckBox ile ListViewItems Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], ListView
- controls [WPF], CheckBox
- ListView controls [WPF], CheckBox controls
- CheckBox control [WPF], ListView control
ms.assetid: f6d66c7f-906c-4f65-a55a-0ede9d00e26a
ms.openlocfilehash: 1ed623495529609c83c0ced68bfc1696c29d4570
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54682248"
---
# <a name="how-to-create-listviewitems-with-a-checkbox"></a><span data-ttu-id="3deb6-102">Nasıl yapılır: CheckBox ile ListViewItems Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3deb6-102">How to: Create ListViewItems with a CheckBox</span></span>
<span data-ttu-id="3deb6-103">Bu örnek, bir sütunun görüntülenecek gösterilmektedir <xref:System.Windows.Controls.CheckBox> denetimlerini bir <xref:System.Windows.Controls.ListView> kullanan denetimi bir <xref:System.Windows.Controls.GridView>.</span><span class="sxs-lookup"><span data-stu-id="3deb6-103">This example shows how to display a column of <xref:System.Windows.Controls.CheckBox> controls in a <xref:System.Windows.Controls.ListView> control that uses a <xref:System.Windows.Controls.GridView>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3deb6-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="3deb6-104">Example</span></span>  
 <span data-ttu-id="3deb6-105">İçeren bir sütun oluşturmak için <xref:System.Windows.Controls.CheckBox> denetimlerini bir <xref:System.Windows.Controls.ListView>, oluşturun bir <xref:System.Windows.DataTemplate> içeren bir <xref:System.Windows.Controls.CheckBox>.</span><span class="sxs-lookup"><span data-stu-id="3deb6-105">To create a column that contains <xref:System.Windows.Controls.CheckBox> controls in a <xref:System.Windows.Controls.ListView>, create a <xref:System.Windows.DataTemplate> that contains a <xref:System.Windows.Controls.CheckBox>.</span></span> <span data-ttu-id="3deb6-106">Ardından <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> , bir <xref:System.Windows.Controls.GridViewColumn> için <xref:System.Windows.DataTemplate>.</span><span class="sxs-lookup"><span data-stu-id="3deb6-106">Then set the <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> of a <xref:System.Windows.Controls.GridViewColumn> to the <xref:System.Windows.DataTemplate>.</span></span>  
  
 <span data-ttu-id="3deb6-107">Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.DataTemplate> içeren bir <xref:System.Windows.Controls.CheckBox>.</span><span class="sxs-lookup"><span data-stu-id="3deb6-107">The following example shows a <xref:System.Windows.DataTemplate> that contains a <xref:System.Windows.Controls.CheckBox>.</span></span> <span data-ttu-id="3deb6-108">Örnek bağlar <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> özelliği <xref:System.Windows.Controls.CheckBox> için <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> özelliği değerinin <xref:System.Windows.Controls.ListViewItem> , içerir.</span><span class="sxs-lookup"><span data-stu-id="3deb6-108">The example binds the <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> property of the <xref:System.Windows.Controls.CheckBox> to the <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> property value of the <xref:System.Windows.Controls.ListViewItem> that contains it.</span></span> <span data-ttu-id="3deb6-109">Bu nedenle, <xref:System.Windows.Controls.ListViewItem> içeren <xref:System.Windows.Controls.CheckBox> seçildiğinde <xref:System.Windows.Controls.CheckBox> denetlenir.</span><span class="sxs-lookup"><span data-stu-id="3deb6-109">Therefore, when the <xref:System.Windows.Controls.ListViewItem> that contains the <xref:System.Windows.Controls.CheckBox> is selected, the <xref:System.Windows.Controls.CheckBox> is checked.</span></span>  
  
 [!code-xaml[ListViewChkBox#CheckBoxDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#checkboxdatatemplate)]  
  
 <span data-ttu-id="3deb6-110">Aşağıdaki örnek, bir sütun oluşturma işlemi gösterilmektedir <xref:System.Windows.Controls.CheckBox> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="3deb6-110">The following example shows how to create a column of <xref:System.Windows.Controls.CheckBox> controls.</span></span> <span data-ttu-id="3deb6-111">Sütunu, örnek yapmak için <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> özelliği <xref:System.Windows.Controls.GridViewColumn> için <xref:System.Windows.DataTemplate>.</span><span class="sxs-lookup"><span data-stu-id="3deb6-111">To make the column, the example sets the <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> property of the <xref:System.Windows.Controls.GridViewColumn> to the <xref:System.Windows.DataTemplate>.</span></span>  
  
 [!code-xaml[ListViewChkBox#GridViewColumnCheckBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#gridviewcolumncheckbox)]  
  
## <a name="see-also"></a><span data-ttu-id="3deb6-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3deb6-112">See also</span></span>
- <xref:System.Windows.Controls.Control>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="3deb6-113">ListView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3deb6-113">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)
- [<span data-ttu-id="3deb6-114">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="3deb6-114">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
- [<span data-ttu-id="3deb6-115">GridView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3deb6-115">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
