---
title: 'Nasıl yapılır: Görünümde Verileri Sıralama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], sorting data in views
- data binding [WPF], grouping data in views
- grouping data in views [WPF]
- views [WPF], sorting data
- views [WPF], grouping data
- sorting data in views [WPF]
ms.assetid: f4c43578-01b7-4774-a953-acb95a13b94a
ms.openlocfilehash: 14314ed019f9194a657787bd767ae68615e94ac7
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454832"
---
# <a name="how-to-sort-data-in-a-view"></a><span data-ttu-id="76314-102">Nasıl yapılır: Görünümde Verileri Sıralama</span><span class="sxs-lookup"><span data-stu-id="76314-102">How to: Sort Data in a View</span></span>
<span data-ttu-id="76314-103">Bu örnek, bir görünümdeki verilerin nasıl sıralanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="76314-103">This example describes how to sort data in a view.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76314-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="76314-104">Example</span></span>  
 <span data-ttu-id="76314-105">Aşağıdaki örnek basit bir <xref:System.Windows.Controls.ListBox> ve <xref:System.Windows.Controls.Button>oluşturur:</span><span class="sxs-lookup"><span data-stu-id="76314-105">The following example creates a simple <xref:System.Windows.Controls.ListBox> and a <xref:System.Windows.Controls.Button>:</span></span>  
  
 [!code-xaml[ListBoxSort_snip#HowTo](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml#howto)]  
  
 <span data-ttu-id="76314-106">Düğmenin <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay işleyicisi, <xref:System.Windows.Controls.ListBox> öğeleri azalan düzende sıralamak için mantık içerir.</span><span class="sxs-lookup"><span data-stu-id="76314-106">The <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler of the button contains logic to sort the items in the <xref:System.Windows.Controls.ListBox> in the descending order.</span></span> <span data-ttu-id="76314-107">Bu şekilde, <xref:System.Windows.Controls.ListBox> öğe eklemek <xref:System.Windows.Controls.ListBox><xref:System.Windows.Controls.ItemCollection> <xref:System.Windows.Controls.ItemCollection> ve <xref:System.Windows.Data.CollectionView> sınıfından türediği için bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76314-107">You can do this because adding items to a <xref:System.Windows.Controls.ListBox> this way adds them to the <xref:System.Windows.Controls.ItemCollection> of the <xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.ItemCollection> derives from the <xref:System.Windows.Data.CollectionView> class.</span></span> <span data-ttu-id="76314-108"><xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliğini kullanarak bir koleksiyona bağlıyorsanız, sıralamak için aynı tekniği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76314-108">If you are binding your <xref:System.Windows.Controls.ListBox> to a collection using the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property, you can use the same technique to sort.</span></span>  
  
 [!code-csharp[ListBoxSort_snip#HowToCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml.cs#howtocode)]
 [!code-vb[ListBoxSort_snip#HowToCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxSort_snip/visualbasic/window1.xaml.vb#howtocode)]  
  
 <span data-ttu-id="76314-109">Görünüm nesnesine bir başvurunuz olduğu sürece, diğer koleksiyon görünümlerinin içeriğini sıralamak için aynı tekniği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76314-109">As long as you have a reference to the view object, you can use the same technique to sort the content of other collection views.</span></span> <span data-ttu-id="76314-110">Görünüm alma hakkında bir örnek için bkz. [veri koleksiyonunun varsayılan görünümünü alma](how-to-get-the-default-view-of-a-data-collection.md).</span><span class="sxs-lookup"><span data-stu-id="76314-110">For an example of how to obtain a view, see [Get the Default View of a Data Collection](how-to-get-the-default-view-of-a-data-collection.md).</span></span> <span data-ttu-id="76314-111">Diğer bir örnek için bkz. [bir başlık tıklandığında GridView sütununu sıralama](../controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).</span><span class="sxs-lookup"><span data-stu-id="76314-111">For another example, see [Sort a GridView Column When a Header Is Clicked](../controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).</span></span> <span data-ttu-id="76314-112">Görünümler hakkında daha fazla bilgi için bkz. [veri bağlamasındaki koleksiyonlara bağlama genel bakış](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="76314-112">For more information about views, see Binding to Collections in [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="76314-113">[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]sıralama mantığının nasıl uygulanacağı hakkında bir örnek için bkz. [xaml 'de bir görünüm kullanarak verileri sıralama ve gruplama](how-to-sort-and-group-data-using-a-view-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="76314-113">For an example of how to apply sorting logic in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], see [Sort and Group Data Using a View in XAML](how-to-sort-and-group-data-using-a-view-in-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76314-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76314-114">See also</span></span>

- <xref:System.Windows.Data.ListCollectionView.CustomSort%2A>
- [<span data-ttu-id="76314-115">Üst Bilgiye Tıklandığında GridView Sütununu Sıralama</span><span class="sxs-lookup"><span data-stu-id="76314-115">Sort a GridView Column When a Header Is Clicked</span></span>](../controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)
- [<span data-ttu-id="76314-116">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="76314-116">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="76314-117">Görünümde Veri Filtreleme</span><span class="sxs-lookup"><span data-stu-id="76314-117">Filter Data in a View</span></span>](how-to-filter-data-in-a-view.md)
- [<span data-ttu-id="76314-118">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="76314-118">How-to Topics</span></span>](data-binding-how-to-topics.md)
