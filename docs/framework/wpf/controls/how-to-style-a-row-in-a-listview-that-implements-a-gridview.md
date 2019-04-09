---
title: 'Nasıl yapılır: GridView Uygulayan ListView İçinde bir Satıra Stil Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
ms.openlocfilehash: 9af8d10c7db2d3bbe8b9443402cbb1cfeaa7edb3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091466"
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a><span data-ttu-id="9dcac-102">Nasıl yapılır: GridView Uygulayan ListView İçinde bir Satıra Stil Ekleme</span><span class="sxs-lookup"><span data-stu-id="9dcac-102">How to: Style a Row in a ListView That Implements a GridView</span></span>
<span data-ttu-id="9dcac-103">Bu örnekte, içinde bir satıra stil ekleme işlemi gösterilmektedir bir <xref:System.Windows.Controls.ListView> uygulayan denetimi bir <xref:System.Windows.Controls.GridView><xref:System.Windows.Controls.ListView.View%2A> modu.</span><span class="sxs-lookup"><span data-stu-id="9dcac-103">This example shows how to style a row in a <xref:System.Windows.Controls.ListView> control that implements a <xref:System.Windows.Controls.GridView><xref:System.Windows.Controls.ListView.View%2A> mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9dcac-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="9dcac-104">Example</span></span>  
 <span data-ttu-id="9dcac-105">Bir satıra stil uygulayabilirsiniz bir <xref:System.Windows.Controls.ListView> ayarlayarak denetimi bir <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> üzerinde <xref:System.Windows.Controls.ListView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="9dcac-105">You can style a row in a <xref:System.Windows.Controls.ListView> control by setting an <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> on the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="9dcac-106">Olarak temsil edilen öğeleri stilini ayarlayın <xref:System.Windows.Controls.ListViewItem> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="9dcac-106">Set the style for its items that are represented as <xref:System.Windows.Controls.ListViewItem> objects.</span></span> <span data-ttu-id="9dcac-107"><xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> Başvuruları <xref:System.Windows.Controls.ControlTemplate> satır içeriği görüntülemek için kullanılan nesneleri.</span><span class="sxs-lookup"><span data-stu-id="9dcac-107">The <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> references the <xref:System.Windows.Controls.ControlTemplate> objects that are used to display the row content.</span></span>  
  
 <span data-ttu-id="9dcac-108">Aşağıdaki örnekler ayıklandığı, tam örnek depolanan şarkı bilgilerini koleksiyonunu görüntüler bir [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] veritabanı.</span><span class="sxs-lookup"><span data-stu-id="9dcac-108">The complete sample, which the following examples are extracted from, displays a collection of song information that is stored in an [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] database.</span></span> <span data-ttu-id="9dcac-109">Veritabanındaki her bir şarkıyı Derecelendirme alanı vardır ve bu alanın değeri bir şarkıyı bilgi satırını görüntülemek nasıl belirtir.</span><span class="sxs-lookup"><span data-stu-id="9dcac-109">Each song in the database has a rating field and the value of this field specifies how to display a row of song information.</span></span>  
  
 <span data-ttu-id="9dcac-110">Aşağıdaki örnek nasıl tanımlanacağını gösterir <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> için <xref:System.Windows.Controls.ListViewItem> şarkı koleksiyondaki şarkıya temsil eden nesneleri.</span><span class="sxs-lookup"><span data-stu-id="9dcac-110">The following example shows how to define <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> for the <xref:System.Windows.Controls.ListViewItem> objects that represent the songs in the song collection.</span></span> <span data-ttu-id="9dcac-111"><xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> Başvuruları <xref:System.Windows.Controls.ControlTemplate> nasıl görüntüleneceğini şarkı bilgilerini içeren bir satırın belirttiğiniz nesneleri.</span><span class="sxs-lookup"><span data-stu-id="9dcac-111">The <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> references <xref:System.Windows.Controls.ControlTemplate> objects that specify how to display a row of song information.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#ItemContainerStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 <span data-ttu-id="9dcac-112">Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.Controls.ControlTemplate> metin dizesi ekleyen `"Strongly Recommended"` satır.</span><span class="sxs-lookup"><span data-stu-id="9dcac-112">The following example shows a <xref:System.Windows.Controls.ControlTemplate> that adds the text string `"Strongly Recommended"` to the row.</span></span> <span data-ttu-id="9dcac-113">Bu şablon başvurulduğundan <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> ve 5 (beş) değerini şarkıyı ait derecelendirme sahip olduğunda görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9dcac-113">This template is referenced in the <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> and displays when the song's rating has a value of 5 (five).</span></span> <span data-ttu-id="9dcac-114"><xref:System.Windows.Controls.ControlTemplate> İçeren bir <xref:System.Windows.Controls.GridViewRowPresenter> sütunlardaki satır içeriğini tarafından tanımlandığı şekilde yerleştirir nesne <xref:System.Windows.Controls.GridView> görünüm modu.</span><span class="sxs-lookup"><span data-stu-id="9dcac-114">The <xref:System.Windows.Controls.ControlTemplate> includes a <xref:System.Windows.Controls.GridViewRowPresenter> object that lays out the contents of the row in columns as defined by the <xref:System.Windows.Controls.GridView> view mode.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#ControlTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 <span data-ttu-id="9dcac-115">Aşağıdaki örnek tanımlar <xref:System.Windows.Controls.GridView>.</span><span class="sxs-lookup"><span data-stu-id="9dcac-115">The following example defines <xref:System.Windows.Controls.GridView>.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#GridView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a><span data-ttu-id="9dcac-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9dcac-116">See also</span></span>

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="9dcac-117">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="9dcac-117">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="9dcac-118">ListView Genel Bakışı</span><span class="sxs-lookup"><span data-stu-id="9dcac-118">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="9dcac-119">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9dcac-119">Styling and Templating</span></span>](styling-and-templating.md)
