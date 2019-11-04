---
title: 'Nasıl yapılır: GridView Uygulayan ListView İçinde bir Satıra Stil Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
ms.openlocfilehash: 150988aab368e3ffef0107d29bea5ebc53163946
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459314"
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a><span data-ttu-id="06de7-102">Nasıl yapılır: GridView Uygulayan ListView İçinde bir Satıra Stil Ekleme</span><span class="sxs-lookup"><span data-stu-id="06de7-102">How to: Style a Row in a ListView That Implements a GridView</span></span>
<span data-ttu-id="06de7-103">Bu örnek, <xref:System.Windows.Controls.GridView><xref:System.Windows.Controls.ListView.View%2A> modunu uygulayan <xref:System.Windows.Controls.ListView> denetimindeki bir satırın nasıl stilli olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="06de7-103">This example shows how to style a row in a <xref:System.Windows.Controls.ListView> control that implements a <xref:System.Windows.Controls.GridView><xref:System.Windows.Controls.ListView.View%2A> mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06de7-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="06de7-104">Example</span></span>  
 <span data-ttu-id="06de7-105"><xref:System.Windows.Controls.ListView> denetiminde bir <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> ayarlayarak <xref:System.Windows.Controls.ListView> denetimindeki bir satıra stil uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06de7-105">You can style a row in a <xref:System.Windows.Controls.ListView> control by setting an <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> on the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="06de7-106"><xref:System.Windows.Controls.ListViewItem> nesne olarak temsil edilen öğelerinin stilini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="06de7-106">Set the style for its items that are represented as <xref:System.Windows.Controls.ListViewItem> objects.</span></span> <span data-ttu-id="06de7-107"><xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>, satır içeriğini göstermek için kullanılan <xref:System.Windows.Controls.ControlTemplate> nesnelerine başvurur.</span><span class="sxs-lookup"><span data-stu-id="06de7-107">The <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> references the <xref:System.Windows.Controls.ControlTemplate> objects that are used to display the row content.</span></span>  
  
 <span data-ttu-id="06de7-108">Aşağıdaki örneklerin ayıklandığı tüm örnek, [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] veritabanında depolanan bir şarkı bilgileri koleksiyonunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="06de7-108">The complete sample, which the following examples are extracted from, displays a collection of song information that is stored in an [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] database.</span></span> <span data-ttu-id="06de7-109">Veritabanındaki her şarkının bir derecelendirme alanı vardır ve bu alanın değeri bir şarkı bilgileri satırının nasıl görüntüleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="06de7-109">Each song in the database has a rating field and the value of this field specifies how to display a row of song information.</span></span>  
  
 <span data-ttu-id="06de7-110">Aşağıdaki örnek, Song koleksiyonundaki şarkıları temsil eden <xref:System.Windows.Controls.ListViewItem> nesneleri için <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> nasıl tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="06de7-110">The following example shows how to define <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> for the <xref:System.Windows.Controls.ListViewItem> objects that represent the songs in the song collection.</span></span> <span data-ttu-id="06de7-111"><xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>, şarkı bilgilerinin bir satırını görüntülemeyi belirten <xref:System.Windows.Controls.ControlTemplate> nesnelerine başvurur.</span><span class="sxs-lookup"><span data-stu-id="06de7-111">The <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> references <xref:System.Windows.Controls.ControlTemplate> objects that specify how to display a row of song information.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#ItemContainerStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 <span data-ttu-id="06de7-112">Aşağıdaki örnek, `"Strongly Recommended"` metin dizesini satıra ekleyen bir <xref:System.Windows.Controls.ControlTemplate> gösterir.</span><span class="sxs-lookup"><span data-stu-id="06de7-112">The following example shows a <xref:System.Windows.Controls.ControlTemplate> that adds the text string `"Strongly Recommended"` to the row.</span></span> <span data-ttu-id="06de7-113">Bu şablona <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> başvurulur ve şarkının derecelendirmesinin 5 (beş) değerine sahip olduğu zaman görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="06de7-113">This template is referenced in the <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> and displays when the song's rating has a value of 5 (five).</span></span> <span data-ttu-id="06de7-114"><xref:System.Windows.Controls.ControlTemplate>, <xref:System.Windows.Controls.GridView> görünüm modu tarafından tanımlanan şekilde sütunlarda satır içeriğini oluşturan bir <xref:System.Windows.Controls.GridViewRowPresenter> nesnesi içerir.</span><span class="sxs-lookup"><span data-stu-id="06de7-114">The <xref:System.Windows.Controls.ControlTemplate> includes a <xref:System.Windows.Controls.GridViewRowPresenter> object that lays out the contents of the row in columns as defined by the <xref:System.Windows.Controls.GridView> view mode.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#ControlTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 <span data-ttu-id="06de7-115">Aşağıdaki örnek <xref:System.Windows.Controls.GridView>tanımlar.</span><span class="sxs-lookup"><span data-stu-id="06de7-115">The following example defines <xref:System.Windows.Controls.GridView>.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#GridView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a><span data-ttu-id="06de7-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06de7-116">See also</span></span>

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="06de7-117">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="06de7-117">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="06de7-118">ListView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="06de7-118">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="06de7-119">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="06de7-119">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
