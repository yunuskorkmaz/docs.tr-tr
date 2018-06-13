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
ms.openlocfilehash: e8e6928391a98a132f1dbb39edfda0d73d2eebdb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557179"
---
# <a name="how-to-get-the-default-view-of-a-data-collection"></a><span data-ttu-id="27e92-102">Nasıl yapılır: Veri Koleksiyonunun Varsayılan Görünümünü Alma</span><span class="sxs-lookup"><span data-stu-id="27e92-102">How to: Get the Default View of a Data Collection</span></span>
<span data-ttu-id="27e92-103">Görünümler, aynı veri koleksiyonunu sıralama, filtreleme veya gruplandırma ölçütlerine bağlı olarak farklı şekillerde görüntülenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="27e92-103">Views allow the same data collection to be viewed in different ways, depending on sorting, filtering, or grouping criteria.</span></span> <span data-ttu-id="27e92-104">Her koleksiyon bir bağlama, kaynağı olarak bir koleksiyon belirttiğinde gerçek bağlama kaynağı olarak kullanılan bir paylaşılan varsayılan görünüme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="27e92-104">Every collection has one shared default view, which is used as the actual binding source when a binding specifies a collection as its source.</span></span> <span data-ttu-id="27e92-105">Bu örnek, bir koleksiyon varsayılan görünümünü elde gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="27e92-105">This example shows how to get the default view of a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27e92-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="27e92-106">Example</span></span>  
 <span data-ttu-id="27e92-107">Görünümü oluşturmak için bir nesne başvurusu koleksiyonuna gerekir.</span><span class="sxs-lookup"><span data-stu-id="27e92-107">To create the view, you need an object reference to the collection.</span></span> <span data-ttu-id="27e92-108">Bu veri nesnesi, veri kaynağının bir özellik alma ya da bağlamanın bir özelliği alma veri bağlamı alarak kendi arka plan kodu nesneye başvuran tarafından alınabilir.</span><span class="sxs-lookup"><span data-stu-id="27e92-108">This data object can be obtained by referencing your own code-behind object, by getting the data context, by getting a property of the data source, or by getting a property of the binding.</span></span> <span data-ttu-id="27e92-109">Bu örnek nasıl alınacağını gösterir <xref:System.Windows.FrameworkElement.DataContext%2A> doğrudan varsayılan koleksiyonu almak üzere bir veri nesnesi ve kullanım bu koleksiyon için görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="27e92-109">This example shows how to get the <xref:System.Windows.FrameworkElement.DataContext%2A> of a data object and use it to directly obtain the default collection view for this collection.</span></span>  
  
 [!code-csharp[CollectionView#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#2)]
 [!code-vb[CollectionView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#2)]  
  
 <span data-ttu-id="27e92-110">Bu örnekte, kök öğesi olan bir <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="27e92-110">In this example, the root element is a <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="27e92-111"><xref:System.Windows.FrameworkElement.DataContext%2A> Ayarlanır *gelen veriKaynağım'a*, olan bir veri sağlayıcısı başvuran bir <xref:System.Collections.ObjectModel.ObservableCollection%601> , *sipariş* nesneleri.</span><span class="sxs-lookup"><span data-stu-id="27e92-111">The <xref:System.Windows.FrameworkElement.DataContext%2A> is set to *myDataSource*, which refers to a data provider that is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of *Order* objects.</span></span>  
  
 [!code-xaml[CollectionView#CollectionViewDataContext](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml#collectionviewdatacontext)]  
  
 <span data-ttu-id="27e92-112">Alternatif olarak, örneği ve bağlamak için kendi koleksiyonu görünümüyle <xref:System.Windows.Data.CollectionViewSource> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="27e92-112">Alternatively, you can instantiate and bind to your own collection view using the <xref:System.Windows.Data.CollectionViewSource> class.</span></span> <span data-ttu-id="27e92-113">Bu koleksiyon görünümü yalnızca doğrudan bağlayan denetimler tarafından paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="27e92-113">This collection view is only shared by controls that bind to it directly.</span></span> <span data-ttu-id="27e92-114">Bir örnek için bir görünüm içinde oluşturulur bölümüne nasıl bakın [veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="27e92-114">For an example, see the How to Create a View section in the [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="27e92-115">Koleksiyon görünümü tarafından sağlanan işlevleri örnekleri için bkz: [bir görünümdeki verileri sıralama](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md), [görünümünde filtre veri](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md), ve [gidin aracılığıyla nesnelerindeki Veri CollectionView](../../../../docs/framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).</span><span class="sxs-lookup"><span data-stu-id="27e92-115">For examples of the functionality provided by a collection view, see [Sort Data in a View](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md), [Filter Data in a View](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md), and [Navigate Through the Objects in a Data CollectionView](../../../../docs/framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27e92-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="27e92-116">See Also</span></span>  
 [<span data-ttu-id="27e92-117">XAML İçerisinde bir Görüntü Kullanarak Verileri Sıralama ve Gruplama</span><span class="sxs-lookup"><span data-stu-id="27e92-117">Sort and Group Data Using a View in XAML</span></span>](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)  
 [<span data-ttu-id="27e92-118">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="27e92-118">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
