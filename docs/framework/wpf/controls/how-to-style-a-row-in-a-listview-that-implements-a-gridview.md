---
title: 'Nasıl yapılır: GridView kullanan ListView içindeki bir satırı stil oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
ms.openlocfilehash: 4b8b8e2f1b2d7207a37205d981bf2dab3f65122e
ms.sourcegitcommit: e0803b8975d3eb12e735a5d07637020dd6dac5ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2020
ms.locfileid: "89271951"
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a><span data-ttu-id="a874a-102">Nasıl yapılır: GridView Uygulayan ListView İçinde bir Satıra Stil Ekleme</span><span class="sxs-lookup"><span data-stu-id="a874a-102">How to: Style a Row in a ListView That Implements a GridView</span></span>
<span data-ttu-id="a874a-103">Bu örnek, mod kullanan bir denetimdeki bir satırın nasıl stilli <xref:System.Windows.Controls.ListView> olduğunu gösterir <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ListView.View%2A> .</span><span class="sxs-lookup"><span data-stu-id="a874a-103">This example shows how to style a row in a <xref:System.Windows.Controls.ListView> control that uses a <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ListView.View%2A> mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a874a-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="a874a-104">Example</span></span>  
 <span data-ttu-id="a874a-105">Denetimde bir satırı ayarlayarak bir denetimin bir satırına stil uygulayabilirsiniz <xref:System.Windows.Controls.ListView> <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> <xref:System.Windows.Controls.ListView> .</span><span class="sxs-lookup"><span data-stu-id="a874a-105">You can style a row in a <xref:System.Windows.Controls.ListView> control by setting an <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> on the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="a874a-106">Nesne olarak temsil edilen öğelerinin stilini ayarlayın <xref:System.Windows.Controls.ListViewItem> .</span><span class="sxs-lookup"><span data-stu-id="a874a-106">Set the style for its items that are represented as <xref:System.Windows.Controls.ListViewItem> objects.</span></span> <span data-ttu-id="a874a-107">, <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> <xref:System.Windows.Controls.ControlTemplate> Satır içeriğini göstermek için kullanılan nesnelere başvurur.</span><span class="sxs-lookup"><span data-stu-id="a874a-107">The <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> references the <xref:System.Windows.Controls.ControlTemplate> objects that are used to display the row content.</span></span>  
  
 <span data-ttu-id="a874a-108">Aşağıdaki örneklerin ayıklandığı tüm örnek, bir XML veritabanında depolanan bir şarkı bilgileri koleksiyonunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a874a-108">The complete sample, which the following examples are extracted from, displays a collection of song information that is stored in an XML database.</span></span> <span data-ttu-id="a874a-109">Veritabanındaki her şarkının bir derecelendirme alanı vardır ve bu alanın değeri bir şarkı bilgileri satırının nasıl görüntüleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a874a-109">Each song in the database has a rating field and the value of this field specifies how to display a row of song information.</span></span>  
  
 <span data-ttu-id="a874a-110">Aşağıdaki örnek, <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> <xref:System.Windows.Controls.ListViewItem> Song koleksiyonundaki şarkıları temsil eden nesneler için nasıl tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a874a-110">The following example shows how to define <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> for the <xref:System.Windows.Controls.ListViewItem> objects that represent the songs in the song collection.</span></span> <span data-ttu-id="a874a-111">, <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> <xref:System.Windows.Controls.ControlTemplate> Şarkı bilgilerinin bir satırını görüntülemeyi belirten nesneler başvurur.</span><span class="sxs-lookup"><span data-stu-id="a874a-111">The <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> references <xref:System.Windows.Controls.ControlTemplate> objects that specify how to display a row of song information.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#ItemContainerStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 <span data-ttu-id="a874a-112">Aşağıdaki örnek, <xref:System.Windows.Controls.ControlTemplate> metin dizesini satıra ekleyen bir gösterir `"Strongly Recommended"` .</span><span class="sxs-lookup"><span data-stu-id="a874a-112">The following example shows a <xref:System.Windows.Controls.ControlTemplate> that adds the text string `"Strongly Recommended"` to the row.</span></span> <span data-ttu-id="a874a-113">Bu şablona içinde başvurulur <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> ve şarkının derecelendirmesi 5 (beş) olduğunda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a874a-113">This template is referenced in the <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> and displays when the song's rating has a value of 5 (five).</span></span> <span data-ttu-id="a874a-114">, <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.GridViewRowPresenter> Görüntüleme modu tarafından tanımlanan şekilde sütunlarda satır içeriğini oluşturan bir nesne içerir <xref:System.Windows.Controls.GridView> .</span><span class="sxs-lookup"><span data-stu-id="a874a-114">The <xref:System.Windows.Controls.ControlTemplate> includes a <xref:System.Windows.Controls.GridViewRowPresenter> object that lays out the contents of the row in columns as defined by the <xref:System.Windows.Controls.GridView> view mode.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#ControlTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 <span data-ttu-id="a874a-115">Aşağıdaki örnek tanımlar <xref:System.Windows.Controls.GridView> .</span><span class="sxs-lookup"><span data-stu-id="a874a-115">The following example defines <xref:System.Windows.Controls.GridView>.</span></span>  
  
 [!code-xaml[ListViewItemStyleSnippet#GridView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a><span data-ttu-id="a874a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a874a-116">See also</span></span>

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="a874a-117">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="a874a-117">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="a874a-118">ListView Genel Bakışı</span><span class="sxs-lookup"><span data-stu-id="a874a-118">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="a874a-119">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a874a-119">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
