---
title: 'Nasıl yapılır: GridView Uygulayan ListView İçinde bir Satıra Stil Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
ms.openlocfilehash: 313ead6de45f2a137775adb0ad9aad8bd061c066
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33555207"
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a><span data-ttu-id="12d0a-102">Nasıl yapılır: GridView Uygulayan ListView İçinde bir Satıra Stil Ekleme</span><span class="sxs-lookup"><span data-stu-id="12d0a-102">How to: Style a Row in a ListView That Implements a GridView</span></span>
<span data-ttu-id="12d0a-103">Bu örnek bir satırda stil gösterilmektedir bir <xref:System.Windows.Controls.ListView> uygulayan denetim bir <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ListView.View%2A> modu.</span><span class="sxs-lookup"><span data-stu-id="12d0a-103">This example shows how to style a row in a <xref:System.Windows.Controls.ListView> control that implements a <xref:System.Windows.Controls.GridView><xref:System.Windows.Controls.ListView.View%2A> mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12d0a-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="12d0a-104">Example</span></span>  
 <span data-ttu-id="12d0a-105">Bir satır stili bir <xref:System.Windows.Controls.ListView> ayarlayarak denetimi bir <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> üzerinde <xref:System.Windows.Controls.ListView> denetim.</span><span class="sxs-lookup"><span data-stu-id="12d0a-105">You can style a row in a <xref:System.Windows.Controls.ListView> control by setting an <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> on the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="12d0a-106">Stil olarak temsil edilir öğelerinden için ayarlanmış <xref:System.Windows.Controls.ListViewItem> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="12d0a-106">Set the style for its items that are represented as <xref:System.Windows.Controls.ListViewItem> objects.</span></span> <span data-ttu-id="12d0a-107"><xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> Başvuruları <xref:System.Windows.Controls.ControlTemplate> satır içeriği görüntülemek için kullanılan nesne.</span><span class="sxs-lookup"><span data-stu-id="12d0a-107">The <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> references the <xref:System.Windows.Controls.ControlTemplate> objects that are used to display the row content.</span></span>  
  
 <span data-ttu-id="12d0a-108">Aşağıdaki örneklerde ayıklandığı tam örnek depolanan şarkı bilgilerinin koleksiyonunu görüntüleyen bir [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] veritabanı.</span><span class="sxs-lookup"><span data-stu-id="12d0a-108">The complete sample, which the following examples are extracted from, displays a collection of song information that is stored in an [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] database.</span></span> <span data-ttu-id="12d0a-109">Veritabanındaki her şarkının derecelendirme alanı vardır ve bu alanın değeri bir satır şarkı bilgilerinin görüntülemek nasıl belirtir.</span><span class="sxs-lookup"><span data-stu-id="12d0a-109">Each song in the database has a rating field and the value of this field specifies how to display a row of song information.</span></span>  
  
 <span data-ttu-id="12d0a-110">Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> için <xref:System.Windows.Controls.ListViewItem> şarkı koleksiyonundaki şarkıya temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="12d0a-110">The following example shows how to define <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> for the <xref:System.Windows.Controls.ListViewItem> objects that represent the songs in the song collection.</span></span> <span data-ttu-id="12d0a-111"><xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> Başvuruları <xref:System.Windows.Controls.ControlTemplate> şarkı bilgilerini satırının görüntülemek nasıl belirtin nesneleri.</span><span class="sxs-lookup"><span data-stu-id="12d0a-111">The <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> references <xref:System.Windows.Controls.ControlTemplate> objects that specify how to display a row of song information.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#ItemContainerStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 <span data-ttu-id="12d0a-112">Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.Controls.ControlTemplate> metin dizesini ekleyen `"Strongly Recommended"` satır.</span><span class="sxs-lookup"><span data-stu-id="12d0a-112">The following example shows a <xref:System.Windows.Controls.ControlTemplate> that adds the text string `"Strongly Recommended"` to the row.</span></span> <span data-ttu-id="12d0a-113">Bu şablon başvuru <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> ve şarkının derecesi 5 (beş) değerine sahip olduğunda görüntüler.</span><span class="sxs-lookup"><span data-stu-id="12d0a-113">This template is referenced in the <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> and displays when the song's rating has a value of 5 (five).</span></span> <span data-ttu-id="12d0a-114"><xref:System.Windows.Controls.ControlTemplate> İçeren bir <xref:System.Windows.Controls.GridViewRowPresenter> sütunlarda sıranın içeriğini tarafından tanımlandığı şekilde yerleştirir nesne <xref:System.Windows.Controls.GridView> görüntüleme modu.</span><span class="sxs-lookup"><span data-stu-id="12d0a-114">The <xref:System.Windows.Controls.ControlTemplate> includes a <xref:System.Windows.Controls.GridViewRowPresenter> object that lays out the contents of the row in columns as defined by the <xref:System.Windows.Controls.GridView> view mode.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#ControlTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 <span data-ttu-id="12d0a-115">Aşağıdaki örnek tanımlar <xref:System.Windows.Controls.GridView>.</span><span class="sxs-lookup"><span data-stu-id="12d0a-115">The following example defines <xref:System.Windows.Controls.GridView>.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#GridView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a><span data-ttu-id="12d0a-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="12d0a-116">See Also</span></span>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="12d0a-117">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="12d0a-117">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="12d0a-118">ListView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="12d0a-118">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="12d0a-119">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="12d0a-119">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
