---
title: "Nasıl yapılır: GridView Kullanan ListView'da Stil Oluşturmak için Şablonları Kullanma"
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 94bf964b-96c8-4bdf-a0c3-f5271b7cb565
ms.openlocfilehash: 481d92d4301401f8ba87c4912cd44b17c5104b1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553838"
---
# <a name="how-to-use-templates-to-style-a-listview-that-uses-gridview"></a><span data-ttu-id="8be09-102">Nasıl yapılır: GridView Kullanan ListView'da Stil Oluşturmak için Şablonları Kullanma</span><span class="sxs-lookup"><span data-stu-id="8be09-102">How to: Use Templates to Style a ListView That Uses GridView</span></span>
<span data-ttu-id="8be09-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.DataTemplate> ve <xref:System.Windows.Style> nesnelerinin görünümünü belirtmek için bir <xref:System.Windows.Controls.ListView> kullanan denetim bir <xref:System.Windows.Controls.GridView> görüntüleme modu.</span><span class="sxs-lookup"><span data-stu-id="8be09-103">This example shows how to use the <xref:System.Windows.DataTemplate> and <xref:System.Windows.Style> objects to specify the appearance of a <xref:System.Windows.Controls.ListView> control that uses a <xref:System.Windows.Controls.GridView> view mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8be09-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="8be09-104">Example</span></span>  
 <span data-ttu-id="8be09-105">Aşağıdaki örneklerde gösterildiği <xref:System.Windows.Style> ve <xref:System.Windows.DataTemplate> için sütun başlığını görünüşünü özelleştirme nesneleri bir <xref:System.Windows.Controls.GridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="8be09-105">The following examples show <xref:System.Windows.Style> and <xref:System.Windows.DataTemplate> objects that customize the appearance of a column header for a <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheaderstyle)]  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheadertemplate)]  
  
 <span data-ttu-id="8be09-106">Aşağıdaki örnekte bu kullanmayı gösterir <xref:System.Windows.Style> ve <xref:System.Windows.DataTemplate> ayarlamak için nesneleri <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> ve <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> özelliklerini bir <xref:System.Windows.Controls.GridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="8be09-106">The following example shows how to use these <xref:System.Windows.Style> and <xref:System.Windows.DataTemplate> objects to set the <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> and <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> properties of a <xref:System.Windows.Controls.GridViewColumn>.</span></span> <span data-ttu-id="8be09-107"><xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> Özelliği sütun hücrelerinin içeriğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8be09-107">The <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> property defines the content of the column cells.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewColumnTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcolumntemplate)]  
  
 <span data-ttu-id="8be09-108"><xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> Ve <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> yalnızca iki sütun üstbilgisi görünümünü özelleştirmek için kullanabileceğiniz çeşitli özelliklerin bir <xref:System.Windows.Controls.GridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="8be09-108">The <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> and <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> are only two of several properties that you can use to customize column header appearance for a <xref:System.Windows.Controls.GridView> control.</span></span> <span data-ttu-id="8be09-109">Daha fazla bilgi için bkz: [GridView sütun üstbilgi stilleri ve şablonlarına genel bakış](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8be09-109">For more information, see [GridView Column Header Styles and Templates Overview](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md).</span></span>  
  
 <span data-ttu-id="8be09-110">Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.DataTemplate> hücrelerde görünümünü özelleştiren bir <xref:System.Windows.Controls.GridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="8be09-110">The following example shows how to define a <xref:System.Windows.DataTemplate> that customizes the appearance of the cells in a <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 <span data-ttu-id="8be09-111">Aşağıdaki örnekte bu kullanmayı gösterir <xref:System.Windows.DataTemplate> içeriğini tanımlamak için bir <xref:System.Windows.Controls.GridViewColumn> hücre.</span><span class="sxs-lookup"><span data-stu-id="8be09-111">The following example shows how to use this <xref:System.Windows.DataTemplate> to define the content of a <xref:System.Windows.Controls.GridViewColumn> cell.</span></span> <span data-ttu-id="8be09-112">Bu şablon yerine kullanılır <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> önceki gösterilen özelliği <xref:System.Windows.Controls.GridViewColumn> örnek.</span><span class="sxs-lookup"><span data-stu-id="8be09-112">This template is used instead of the <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> property that is shown in the previous <xref:System.Windows.Controls.GridViewColumn> example.</span></span>  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="8be09-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8be09-113">See Also</span></span>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="8be09-114">GridView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8be09-114">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [<span data-ttu-id="8be09-115">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="8be09-115">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="8be09-116">ListView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8be09-116">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)
