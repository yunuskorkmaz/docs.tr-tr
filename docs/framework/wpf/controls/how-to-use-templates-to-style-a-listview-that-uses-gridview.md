---
title: "Nasıl yapılır: GridView Kullanan ListView'da Stil Oluşturmak için Şablonları Kullanma"
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 94bf964b-96c8-4bdf-a0c3-f5271b7cb565
ms.openlocfilehash: baef8bdee73d8493ba406f5eef1e3e3676680704
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355772"
---
# <a name="how-to-use-templates-to-style-a-listview-that-uses-gridview"></a><span data-ttu-id="6736d-102">Nasıl yapılır: GridView Kullanan ListView'da Stil Oluşturmak için Şablonları Kullanma</span><span class="sxs-lookup"><span data-stu-id="6736d-102">How to: Use Templates to Style a ListView That Uses GridView</span></span>
<span data-ttu-id="6736d-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.DataTemplate> ve <xref:System.Windows.Style> nesnelerin görünümünü belirtmek için bir <xref:System.Windows.Controls.ListView> kullanan denetimi bir <xref:System.Windows.Controls.GridView> görünüm modu.</span><span class="sxs-lookup"><span data-stu-id="6736d-103">This example shows how to use the <xref:System.Windows.DataTemplate> and <xref:System.Windows.Style> objects to specify the appearance of a <xref:System.Windows.Controls.ListView> control that uses a <xref:System.Windows.Controls.GridView> view mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6736d-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="6736d-104">Example</span></span>  
 <span data-ttu-id="6736d-105">Aşağıdaki örneklerde gösterildiği <xref:System.Windows.Style> ve <xref:System.Windows.DataTemplate> için sütun başlığını özelleştirme nesneleri bir <xref:System.Windows.Controls.GridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="6736d-105">The following examples show <xref:System.Windows.Style> and <xref:System.Windows.DataTemplate> objects that customize the appearance of a column header for a <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheaderstyle)]  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheadertemplate)]  
  
 <span data-ttu-id="6736d-106">Aşağıdaki örnek bu kullanmayı gösterir <xref:System.Windows.Style> ve <xref:System.Windows.DataTemplate> ayarlamak için nesneleri <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> ve <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> özelliklerini bir <xref:System.Windows.Controls.GridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="6736d-106">The following example shows how to use these <xref:System.Windows.Style> and <xref:System.Windows.DataTemplate> objects to set the <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> and <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> properties of a <xref:System.Windows.Controls.GridViewColumn>.</span></span> <span data-ttu-id="6736d-107"><xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> Sütun hücrelerin içeriğinin özelliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6736d-107">The <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> property defines the content of the column cells.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewColumnTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcolumntemplate)]  
  
 <span data-ttu-id="6736d-108"><xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> Ve <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> yalnızca iki sütun üst bilgisi görünümünü özelleştirmek için kullanabileceğiniz çeşitli özelliklerin bir <xref:System.Windows.Controls.GridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="6736d-108">The <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> and <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> are only two of several properties that you can use to customize column header appearance for a <xref:System.Windows.Controls.GridView> control.</span></span> <span data-ttu-id="6736d-109">Daha fazla bilgi için [GridView sütun üstbilgi stil ve şablonlarına genel bakış](gridview-column-header-styles-and-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6736d-109">For more information, see [GridView Column Header Styles and Templates Overview](gridview-column-header-styles-and-templates-overview.md).</span></span>  
  
 <span data-ttu-id="6736d-110">Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.DataTemplate> hücrelerin görünüşünü özelleştiren bir <xref:System.Windows.Controls.GridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="6736d-110">The following example shows how to define a <xref:System.Windows.DataTemplate> that customizes the appearance of the cells in a <xref:System.Windows.Controls.GridViewColumn>.</span></span>  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 <span data-ttu-id="6736d-111">Aşağıdaki örnek bunu kullanmayı gösterir <xref:System.Windows.DataTemplate> içeriğini tanımlamak için bir <xref:System.Windows.Controls.GridViewColumn> hücre.</span><span class="sxs-lookup"><span data-stu-id="6736d-111">The following example shows how to use this <xref:System.Windows.DataTemplate> to define the content of a <xref:System.Windows.Controls.GridViewColumn> cell.</span></span> <span data-ttu-id="6736d-112">Bu şablon yerine kullanılan <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> önceki gösterilen özelliği <xref:System.Windows.Controls.GridViewColumn> örnek.</span><span class="sxs-lookup"><span data-stu-id="6736d-112">This template is used instead of the <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> property that is shown in the previous <xref:System.Windows.Controls.GridViewColumn> example.</span></span>  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="6736d-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6736d-113">See also</span></span>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="6736d-114">GridView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6736d-114">GridView Overview</span></span>](gridview-overview.md)
- [<span data-ttu-id="6736d-115">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="6736d-115">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="6736d-116">ListView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6736d-116">ListView Overview</span></span>](listview-overview.md)
