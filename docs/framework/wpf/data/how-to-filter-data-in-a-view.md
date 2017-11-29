---
title: "Nasıl yapılır: Görünümde Veri Filtreleme"
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
- views [WPF], filtering data
- filtering data in views [WPF]
- data binding [WPF], filtering data in views
ms.assetid: c76e8606-4cc4-45a8-9110-e2ec66dc6afd
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: de51aa83af71027ce86909a15f3ceee58fb47814
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-filter-data-in-a-view"></a><span data-ttu-id="a49d0-102">Nasıl yapılır: Görünümde Veri Filtreleme</span><span class="sxs-lookup"><span data-stu-id="a49d0-102">How to: Filter Data in a View</span></span>
<span data-ttu-id="a49d0-103">Bu örnek bir görünümündeki verileri filtrelemek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="a49d0-103">This example shows how to filter data in a view.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a49d0-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="a49d0-104">Example</span></span>  
 <span data-ttu-id="a49d0-105">Bir filtre oluşturmak için filtreleme mantığı sağlayan bir yöntemi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="a49d0-105">To create a filter, define a method that provides the filtering logic.</span></span> <span data-ttu-id="a49d0-106">Yöntem geri arama olarak kullanılan ve türünde bir parametre kabul eden `object`.</span><span class="sxs-lookup"><span data-stu-id="a49d0-106">The method is used as a callback and accepts a parameter of type `object`.</span></span> <span data-ttu-id="a49d0-107">Aşağıdaki yöntem tüm döndürür `Order` nesnelerini `filled` özelliği "Hayır" geri kalan nesneleri filtreleme, ayarlanmış.</span><span class="sxs-lookup"><span data-stu-id="a49d0-107">The following method returns all the `Order` objects with the `filled` property set to "No", filtering out the rest of the objects.</span></span>  
  
 [!code-csharp[SortFilter#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#2)]
 [!code-vb[SortFilter#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#2)]  
  
 <span data-ttu-id="a49d0-108">Aşağıdaki örnekte gösterildiği gibi daha sonra filtre uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a49d0-108">You can then apply the filter, as shown in the following example.</span></span> <span data-ttu-id="a49d0-109">Bu örnekte, `myCollectionView` olan bir <xref:System.Windows.Data.ListCollectionView> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="a49d0-109">In this example, `myCollectionView` is a <xref:System.Windows.Data.ListCollectionView> object.</span></span>  
  
 [!code-csharp[SortFilter#Filter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#filter)]
 [!code-vb[SortFilter#Filter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#filter)]  
  
 <span data-ttu-id="a49d0-110">Filtreleme geri almak için ayarlayabileceğiniz <xref:System.Windows.Data.CollectionView.Filter%2A> özelliğine `null`:</span><span class="sxs-lookup"><span data-stu-id="a49d0-110">To undo filtering, you can set the <xref:System.Windows.Data.CollectionView.Filter%2A> property to `null`:</span></span>  
  
 [!code-csharp[SortFilter#Unfilter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#unfilter)]
 [!code-vb[SortFilter#Unfilter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#unfilter)]  
  
 <span data-ttu-id="a49d0-111">Oluşturma ve bir görünüm elde etme hakkında daha fazla bilgi için bkz: [veri koleksiyonunun varsayılan görünümünü elde](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).</span><span class="sxs-lookup"><span data-stu-id="a49d0-111">For information about how to create or obtain a view, see [Get the Default View of a Data Collection](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).</span></span> <span data-ttu-id="a49d0-112">Tam bir örnek için bkz: [sıralama ve filtreleme öğeleri görünüm örnekteki](http://go.microsoft.com/fwlink/?LinkID=160040).</span><span class="sxs-lookup"><span data-stu-id="a49d0-112">For the complete example, see [Sorting and Filtering Items in a View Sample](http://go.microsoft.com/fwlink/?LinkID=160040).</span></span>  
  
 <span data-ttu-id="a49d0-113">Görünüm nesnesi geliyorsa bir <xref:System.Windows.Data.CollectionViewSource> nesne için bir olay işleyicisi ayarlayarak filtreleme mantığını uygulamak <xref:System.Windows.Data.CollectionViewSource.Filter> olay.</span><span class="sxs-lookup"><span data-stu-id="a49d0-113">If your view object comes from a <xref:System.Windows.Data.CollectionViewSource> object, you apply filtering logic by setting an event handler for the <xref:System.Windows.Data.CollectionViewSource.Filter> event.</span></span> <span data-ttu-id="a49d0-114">Aşağıdaki örnekte, `listingDataView` örneği <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="a49d0-114">In the following example, `listingDataView` is an instance of <xref:System.Windows.Data.CollectionViewSource>.</span></span>  
  
 [!code-csharp[DataBindingLab#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 <span data-ttu-id="a49d0-115">Aşağıdaki örnek uygulamasını gösterir `ShowOnlyBargainsFilter` filtre olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="a49d0-115">The following shows the implementation of the example `ShowOnlyBargainsFilter` filter event handler.</span></span> <span data-ttu-id="a49d0-116">Bu olay işleyicisi kullanan <xref:System.Windows.Data.FilterEventArgs.Accepted%2A> filtrelemek için özellik `AuctionItem` sahip nesneleri bir `CurrentPrice` $25 veya daha büyük.</span><span class="sxs-lookup"><span data-stu-id="a49d0-116">This event handler uses the <xref:System.Windows.Data.FilterEventArgs.Accepted%2A> property to filter out `AuctionItem` objects that have a `CurrentPrice` of $25 or greater.</span></span>  
  
 [!code-csharp[DataBindingLab#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="a49d0-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a49d0-117">See Also</span></span>  
 <xref:System.Windows.Data.CollectionView.CanFilter%2A>  
 <xref:System.Windows.Data.BindingListCollectionView.CustomFilter%2A>  
 [<span data-ttu-id="a49d0-118">Veri bağlama genel bakış</span><span class="sxs-lookup"><span data-stu-id="a49d0-118">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="a49d0-119">Bir görünümdeki verileri sıralama</span><span class="sxs-lookup"><span data-stu-id="a49d0-119">Sort Data in a View</span></span>](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)  
 [<span data-ttu-id="a49d0-120">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="a49d0-120">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
