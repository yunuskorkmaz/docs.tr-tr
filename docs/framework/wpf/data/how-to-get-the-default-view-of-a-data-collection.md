---
title: 'Nasıl yapılır: Veri Koleksiyonunun Varsayılan Görünümünü Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data collections [WPF], creating views of
- data binding [WPF], creating views of data collections
ms.assetid: b641e96c-c2f6-42ea-9c5d-bac81176ad65
ms.openlocfilehash: 386c25998c85de2f674200fe7d269ae2fdabd72d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54588411"
---
# <a name="how-to-get-the-default-view-of-a-data-collection"></a><span data-ttu-id="4d7df-102">Nasıl yapılır: Veri Koleksiyonunun Varsayılan Görünümünü Alma</span><span class="sxs-lookup"><span data-stu-id="4d7df-102">How to: Get the Default View of a Data Collection</span></span>
<span data-ttu-id="4d7df-103">Görünümler, aynı veri koleksiyonunu sıralama, filtreleme ve gruplandırma ölçütü bağlı olarak farklı şekillerde görüntülenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="4d7df-103">Views allow the same data collection to be viewed in different ways, depending on sorting, filtering, or grouping criteria.</span></span> <span data-ttu-id="4d7df-104">Her koleksiyon bir bağlama, kaynağı olarak bir koleksiyon belirttiğinde gerçek bağlama kaynağı olarak kullanılan bir paylaşılan varsayılan görünüme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="4d7df-104">Every collection has one shared default view, which is used as the actual binding source when a binding specifies a collection as its source.</span></span> <span data-ttu-id="4d7df-105">Bu örnek, koleksiyonunun varsayılan görünümünü alma gösterir.</span><span class="sxs-lookup"><span data-stu-id="4d7df-105">This example shows how to get the default view of a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d7df-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="4d7df-106">Example</span></span>  
 <span data-ttu-id="4d7df-107">Görünümü oluşturmak için bir nesne başvurusunu koleksiyona gerekir.</span><span class="sxs-lookup"><span data-stu-id="4d7df-107">To create the view, you need an object reference to the collection.</span></span> <span data-ttu-id="4d7df-108">Bu veri nesnesi, kendi arka plan kod nesnesi alarak veri kaynağının bir özelliği ya da bağlamanın bir özelliği alarak veri bağlamı alarak başvurarak alınabilir.</span><span class="sxs-lookup"><span data-stu-id="4d7df-108">This data object can be obtained by referencing your own code-behind object, by getting the data context, by getting a property of the data source, or by getting a property of the binding.</span></span> <span data-ttu-id="4d7df-109">Bu örnek nasıl alınacağı gösterilmiştir <xref:System.Windows.FrameworkElement.DataContext%2A> doğrudan varsayılan koleksiyonu almak üzere bir veri nesnesi ve kullanmak bu koleksiyon için görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="4d7df-109">This example shows how to get the <xref:System.Windows.FrameworkElement.DataContext%2A> of a data object and use it to directly obtain the default collection view for this collection.</span></span>  
  
 [!code-csharp[CollectionView#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#2)]
 [!code-vb[CollectionView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#2)]  
  
 <span data-ttu-id="4d7df-110">Bu örnekte, kök öğe olduğundan bir <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="4d7df-110">In this example, the root element is a <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="4d7df-111"><xref:System.Windows.FrameworkElement.DataContext%2A> Ayarlanır *gelen veriKaynağım'a*, olan bir veri sağlayıcısı başvuran bir <xref:System.Collections.ObjectModel.ObservableCollection%601> , *sipariş* nesneleri.</span><span class="sxs-lookup"><span data-stu-id="4d7df-111">The <xref:System.Windows.FrameworkElement.DataContext%2A> is set to *myDataSource*, which refers to a data provider that is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of *Order* objects.</span></span>  
  
 [!code-xaml[CollectionView#CollectionViewDataContext](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml#collectionviewdatacontext)]  
  
 <span data-ttu-id="4d7df-112">Alternatif olarak, oluşturmak ve bağlamak için kendi koleksiyonu görünümüyle <xref:System.Windows.Data.CollectionViewSource> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4d7df-112">Alternatively, you can instantiate and bind to your own collection view using the <xref:System.Windows.Data.CollectionViewSource> class.</span></span> <span data-ttu-id="4d7df-113">Bu koleksiyon görünümü yalnızca doğrudan bağlayan denetimleri tarafından paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="4d7df-113">This collection view is only shared by controls that bind to it directly.</span></span> <span data-ttu-id="4d7df-114">Bir görünüm konusundaki oluşturma nasıl bir örnek için bakınız [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="4d7df-114">For an example, see the How to Create a View section in the [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="4d7df-115">Koleksiyon görünümü tarafından sağlanan işlevselliği örnekleri için bkz: [görünümde verileri sıralama](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md), [görünümde veri filtreleme](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md), ve [Git aracılığıyla CollectionView içindeki nesneler veri](../../../../docs/framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).</span><span class="sxs-lookup"><span data-stu-id="4d7df-115">For examples of the functionality provided by a collection view, see [Sort Data in a View](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md), [Filter Data in a View](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md), and [Navigate Through the Objects in a Data CollectionView](../../../../docs/framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d7df-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d7df-116">See also</span></span>
- [<span data-ttu-id="4d7df-117">XAML İçerisinde bir Görüntü Kullanarak Verileri Sıralama ve Gruplama</span><span class="sxs-lookup"><span data-stu-id="4d7df-117">Sort and Group Data Using a View in XAML</span></span>](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [<span data-ttu-id="4d7df-118">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="4d7df-118">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
