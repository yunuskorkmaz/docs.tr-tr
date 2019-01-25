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
ms.openlocfilehash: 50e1426f2a220c7d947f7feb9c3ec7e1c4de7643
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522680"
---
# <a name="how-to-sort-data-in-a-view"></a><span data-ttu-id="ff018-102">Nasıl yapılır: Görünümde Verileri Sıralama</span><span class="sxs-lookup"><span data-stu-id="ff018-102">How to: Sort Data in a View</span></span>
<span data-ttu-id="ff018-103">Bu örnek, bir görünümde verileri sıralama açıklar.</span><span class="sxs-lookup"><span data-stu-id="ff018-103">This example describes how to sort data in a view.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff018-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="ff018-104">Example</span></span>  
 <span data-ttu-id="ff018-105">Aşağıdaki örnek, basit bir oluşturur <xref:System.Windows.Controls.ListBox> ve <xref:System.Windows.Controls.Button>:</span><span class="sxs-lookup"><span data-stu-id="ff018-105">The following example creates a simple <xref:System.Windows.Controls.ListBox> and a <xref:System.Windows.Controls.Button>:</span></span>  
  
 [!code-xaml[ListBoxSort_snip#HowTo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml#howto)]  
  
 <span data-ttu-id="ff018-106"><xref:System.Windows.Controls.Primitives.ButtonBase.Click> Düğmesi olay işleyicisi içindeki öğeleri sıralamak için mantık içerir <xref:System.Windows.Controls.ListBox> azalan düzende.</span><span class="sxs-lookup"><span data-stu-id="ff018-106">The <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler of the button contains logic to sort the items in the <xref:System.Windows.Controls.ListBox> in the descending order.</span></span> <span data-ttu-id="ff018-107">Öğeler ekleme çünkü bunu bir <xref:System.Windows.Controls.ListBox> bu şekilde eklenmeye <xref:System.Windows.Controls.ItemCollection> , <xref:System.Windows.Controls.ListBox>, ve <xref:System.Windows.Controls.ItemCollection> türetildiği <xref:System.Windows.Data.CollectionView> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ff018-107">You can do this because adding items to a <xref:System.Windows.Controls.ListBox> this way adds them to the <xref:System.Windows.Controls.ItemCollection> of the <xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.ItemCollection> derives from the <xref:System.Windows.Data.CollectionView> class.</span></span> <span data-ttu-id="ff018-108">Bağlıyorsanız, <xref:System.Windows.Controls.ListBox> kullanarak bir koleksiyon <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliği sıralamak için aynı tekniği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ff018-108">If you are binding your <xref:System.Windows.Controls.ListBox> to a collection using the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property, you can use the same technique to sort.</span></span>  
  
 [!code-csharp[ListBoxSort_snip#HowToCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml.cs#howtocode)]
 [!code-vb[ListBoxSort_snip#HowToCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxSort_snip/visualbasic/window1.xaml.vb#howtocode)]  
  
 <span data-ttu-id="ff018-109">Görünüm nesnesine bir başvuru olduğu sürece, diğer koleksiyon görünümlerini içeriğini sıralamak için aynı tekniği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ff018-109">As long as you have a reference to the view object, you can use the same technique to sort the content of other collection views.</span></span> <span data-ttu-id="ff018-110">Bir görünüm elde etmek nasıl bir örnek için bkz [veri koleksiyonunun varsayılan görünümünü alma](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).</span><span class="sxs-lookup"><span data-stu-id="ff018-110">For an example of how to obtain a view, see [Get the Default View of a Data Collection](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).</span></span> <span data-ttu-id="ff018-111">Başka bir örnek için bkz: [bir GridView Sütun, bir üstbilgi tıklandığında sıralama](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).</span><span class="sxs-lookup"><span data-stu-id="ff018-111">For another example, see [Sort a GridView Column When a Header Is Clicked](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).</span></span> <span data-ttu-id="ff018-112">Koleksiyonlarında bağlama görünümleri hakkında daha fazla bilgi için bkz. [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ff018-112">For more information about views, see Binding to Collections in [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="ff018-113">Sıralama mantığı uygulamak nasıl bir örnek için [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], bkz: [sıralama ve Grup verileri kullanarak XAML görünümünde](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="ff018-113">For an example of how to apply sorting logic in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], see [Sort and Group Data Using a View in XAML](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff018-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff018-114">See also</span></span>
- <xref:System.Windows.Data.ListCollectionView.CustomSort%2A>
- [<span data-ttu-id="ff018-115">Üst Bilgiye Tıklandığında GridView Sütununu Sıralama</span><span class="sxs-lookup"><span data-stu-id="ff018-115">Sort a GridView Column When a Header Is Clicked</span></span>](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)
- [<span data-ttu-id="ff018-116">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ff018-116">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [<span data-ttu-id="ff018-117">Görünümde Veri Filtreleme</span><span class="sxs-lookup"><span data-stu-id="ff018-117">Filter Data in a View</span></span>](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)
- [<span data-ttu-id="ff018-118">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="ff018-118">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
