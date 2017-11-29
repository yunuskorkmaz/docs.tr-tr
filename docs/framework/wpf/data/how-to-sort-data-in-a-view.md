---
title: "Nasıl yapılır: Görünümde Verileri Sıralama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2c39cec8aaf12b268790c19751562b16fa34cfdc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-sort-data-in-a-view"></a><span data-ttu-id="9da04-102">Nasıl yapılır: Görünümde Verileri Sıralama</span><span class="sxs-lookup"><span data-stu-id="9da04-102">How to: Sort Data in a View</span></span>
<span data-ttu-id="9da04-103">Bu örnek, bir görünümündeki verileri sıralamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="9da04-103">This example describes how to sort data in a view.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9da04-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="9da04-104">Example</span></span>  
 <span data-ttu-id="9da04-105">Aşağıdaki örnek, basit bir oluşturur <xref:System.Windows.Controls.ListBox> ve <xref:System.Windows.Controls.Button>:</span><span class="sxs-lookup"><span data-stu-id="9da04-105">The following example creates a simple <xref:System.Windows.Controls.ListBox> and a <xref:System.Windows.Controls.Button>:</span></span>  
  
 [!code-xaml[ListBoxSort_snip#HowTo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml#howto)]  
  
 <span data-ttu-id="9da04-106"><xref:System.Windows.Controls.Primitives.ButtonBase.Click> Düğmesinin olay işleyiciyi içeriyor öğeleri sıralamak için mantık <xref:System.Windows.Controls.ListBox> azalan düzende.</span><span class="sxs-lookup"><span data-stu-id="9da04-106">The <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler of the button contains logic to sort the items in the <xref:System.Windows.Controls.ListBox> in the descending order.</span></span> <span data-ttu-id="9da04-107">Öğeler ekleme çünkü bunu yapabilirsiniz bir <xref:System.Windows.Controls.ListBox> bu şekilde eklenmektedir <xref:System.Windows.Controls.ItemCollection> , <xref:System.Windows.Controls.ListBox>, ve <xref:System.Windows.Controls.ItemCollection> türetilen <xref:System.Windows.Data.CollectionView> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9da04-107">You can do this because adding items to a <xref:System.Windows.Controls.ListBox> this way adds them to the <xref:System.Windows.Controls.ItemCollection> of the <xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.ItemCollection> derives from the <xref:System.Windows.Data.CollectionView> class.</span></span> <span data-ttu-id="9da04-108">Bağlıyorsanız, <xref:System.Windows.Controls.ListBox> kullanarak bir koleksiyon için <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özellik, sıralama için aynı tekniği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9da04-108">If you are binding your <xref:System.Windows.Controls.ListBox> to a collection using the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property, you can use the same technique to sort.</span></span>  
  
 [!code-csharp[ListBoxSort_snip#HowToCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml.cs#howtocode)]
 [!code-vb[ListBoxSort_snip#HowToCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxSort_snip/visualbasic/window1.xaml.vb#howtocode)]  
  
 <span data-ttu-id="9da04-109">Görünüm nesnesine başvuru sahip olduğu sürece, diğer koleksiyon görünümlerinin içeriğini sıralamak için aynı tekniği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9da04-109">As long as you have a reference to the view object, you can use the same technique to sort the content of other collection views.</span></span> <span data-ttu-id="9da04-110">Bir görünüm elde etme örneği için bkz: [veri koleksiyonunun varsayılan görünümünü elde](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).</span><span class="sxs-lookup"><span data-stu-id="9da04-110">For an example of how to obtain a view, see [Get the Default View of a Data Collection](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).</span></span> <span data-ttu-id="9da04-111">Başka bir örnek için bkz: [bir GridView Sütun olduğunda bir üstbilgi tıklandığında sıralama](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).</span><span class="sxs-lookup"><span data-stu-id="9da04-111">For another example, see [Sort a GridView Column When a Header Is Clicked](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).</span></span> <span data-ttu-id="9da04-112">Koleksiyonlarda bağlama görünümler hakkında daha fazla bilgi için bkz [veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9da04-112">For more information about views, see Binding to Collections in [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="9da04-113">Sıralama mantığı uygulamaya nasıl bir örnek için [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], bkz: [sıralama ve grup verilerini kullanan XAML görünümünde](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="9da04-113">For an example of how to apply sorting logic in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], see [Sort and Group Data Using a View in XAML](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9da04-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9da04-114">See Also</span></span>  
 <xref:System.Windows.Data.ListCollectionView.CustomSort%2A>  
 [<span data-ttu-id="9da04-115">Üstbilgi Tıklatıldığında GridView sütununu sıralama</span><span class="sxs-lookup"><span data-stu-id="9da04-115">Sort a GridView Column When a Header Is Clicked</span></span>](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)  
 [<span data-ttu-id="9da04-116">Veri bağlama genel bakış</span><span class="sxs-lookup"><span data-stu-id="9da04-116">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="9da04-117">Bir görünümündeki verileri filtreleme</span><span class="sxs-lookup"><span data-stu-id="9da04-117">Filter Data in a View</span></span>](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)  
 [<span data-ttu-id="9da04-118">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="9da04-118">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
