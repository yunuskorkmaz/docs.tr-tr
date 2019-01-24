---
title: 'Nasıl yapılır: Görünümde Veri Filtreleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- views [WPF], filtering data
- filtering data in views [WPF]
- data binding [WPF], filtering data in views
ms.assetid: c76e8606-4cc4-45a8-9110-e2ec66dc6afd
ms.openlocfilehash: 33af517c086f8f89cc06a1de7a2979c5b1624109
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689331"
---
# <a name="how-to-filter-data-in-a-view"></a><span data-ttu-id="b584d-102">Nasıl yapılır: Görünümde Veri Filtreleme</span><span class="sxs-lookup"><span data-stu-id="b584d-102">How to: Filter Data in a View</span></span>
<span data-ttu-id="b584d-103">Bu örnek, görünümde veri filtreleme yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b584d-103">This example shows how to filter data in a view.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b584d-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="b584d-104">Example</span></span>  
 <span data-ttu-id="b584d-105">Bir filtre oluşturmak için filtreleme mantığı sağlayan bir yöntem tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="b584d-105">To create a filter, define a method that provides the filtering logic.</span></span> <span data-ttu-id="b584d-106">Yöntemi, bir geri arama olarak kullanılan ve türünde bir parametreyi kabul eden `object`.</span><span class="sxs-lookup"><span data-stu-id="b584d-106">The method is used as a callback and accepts a parameter of type `object`.</span></span> <span data-ttu-id="b584d-107">Aşağıdaki yöntem tüm döndürür `Order` nesnelerini `filled` "Hayır", geri kalan nesneleri filtreleme özelliği.</span><span class="sxs-lookup"><span data-stu-id="b584d-107">The following method returns all the `Order` objects with the `filled` property set to "No", filtering out the rest of the objects.</span></span>  
  
 [!code-csharp[SortFilter#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#2)]
 [!code-vb[SortFilter#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#2)]  
  
 <span data-ttu-id="b584d-108">Ardından, aşağıdaki örnekte gösterildiği gibi filtre uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b584d-108">You can then apply the filter, as shown in the following example.</span></span> <span data-ttu-id="b584d-109">Bu örnekte, `myCollectionView` olduğu bir <xref:System.Windows.Data.ListCollectionView> nesne.</span><span class="sxs-lookup"><span data-stu-id="b584d-109">In this example, `myCollectionView` is a <xref:System.Windows.Data.ListCollectionView> object.</span></span>  
  
 [!code-csharp[SortFilter#Filter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#filter)]
 [!code-vb[SortFilter#Filter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#filter)]  
  
 <span data-ttu-id="b584d-110">Filtreleme geri almak için ayarlayabileceğiniz <xref:System.Windows.Data.CollectionView.Filter%2A> özelliğini `null`:</span><span class="sxs-lookup"><span data-stu-id="b584d-110">To undo filtering, you can set the <xref:System.Windows.Data.CollectionView.Filter%2A> property to `null`:</span></span>  
  
 [!code-csharp[SortFilter#Unfilter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#unfilter)]
 [!code-vb[SortFilter#Unfilter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#unfilter)]  
  
 <span data-ttu-id="b584d-111">Oluşturma ve bir görünüm elde etme hakkında daha fazla bilgi için bkz. [veri koleksiyonunun varsayılan görünümünü alma](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).</span><span class="sxs-lookup"><span data-stu-id="b584d-111">For information about how to create or obtain a view, see [Get the Default View of a Data Collection](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).</span></span> <span data-ttu-id="b584d-112">Tam bir örnek için bkz. [sıralama ve filtreleme öğeleri görünüm örnek](https://go.microsoft.com/fwlink/?LinkID=160040).</span><span class="sxs-lookup"><span data-stu-id="b584d-112">For the complete example, see [Sorting and Filtering Items in a View Sample](https://go.microsoft.com/fwlink/?LinkID=160040).</span></span>  
  
 <span data-ttu-id="b584d-113">Görünüm nesnesi geliyorsa bir <xref:System.Windows.Data.CollectionViewSource> nesne için bir olay işleyicisi ayarlayarak filtreleme mantığı uygulamak <xref:System.Windows.Data.CollectionViewSource.Filter> olay.</span><span class="sxs-lookup"><span data-stu-id="b584d-113">If your view object comes from a <xref:System.Windows.Data.CollectionViewSource> object, you apply filtering logic by setting an event handler for the <xref:System.Windows.Data.CollectionViewSource.Filter> event.</span></span> <span data-ttu-id="b584d-114">Aşağıdaki örnekte, `listingDataView` örneğidir <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="b584d-114">In the following example, `listingDataView` is an instance of <xref:System.Windows.Data.CollectionViewSource>.</span></span>  
  
 [!code-csharp[DataBindingLab#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 <span data-ttu-id="b584d-115">Aşağıdaki örnek uygulamasını gösterir `ShowOnlyBargainsFilter` filtre olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="b584d-115">The following shows the implementation of the example `ShowOnlyBargainsFilter` filter event handler.</span></span> <span data-ttu-id="b584d-116">Bu olay işleyicisi kullanır <xref:System.Windows.Data.FilterEventArgs.Accepted%2A> filtrelemek için özellik `AuctionItem` olan nesneleri bir `CurrentPrice` $25 veya daha büyük.</span><span class="sxs-lookup"><span data-stu-id="b584d-116">This event handler uses the <xref:System.Windows.Data.FilterEventArgs.Accepted%2A> property to filter out `AuctionItem` objects that have a `CurrentPrice` of $25 or greater.</span></span>  
  
 [!code-csharp[DataBindingLab#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="b584d-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b584d-117">See also</span></span>
- <xref:System.Windows.Data.CollectionView.CanFilter%2A>
- <xref:System.Windows.Data.BindingListCollectionView.CustomFilter%2A>
- [<span data-ttu-id="b584d-118">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b584d-118">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [<span data-ttu-id="b584d-119">Görünümde Verileri Sıralama</span><span class="sxs-lookup"><span data-stu-id="b584d-119">Sort Data in a View</span></span>](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)
- [<span data-ttu-id="b584d-120">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="b584d-120">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
