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
ms.openlocfilehash: e82d252ed82e4d2e6d641e8b60e890cc93bb0427
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459121"
---
# <a name="how-to-get-the-default-view-of-a-data-collection"></a><span data-ttu-id="d34bb-102">Nasıl yapılır: Veri Koleksiyonunun Varsayılan Görünümünü Alma</span><span class="sxs-lookup"><span data-stu-id="d34bb-102">How to: Get the Default View of a Data Collection</span></span>
<span data-ttu-id="d34bb-103">Görünümler, sıralama, filtreleme veya gruplandırma ölçütlerine bağlı olarak aynı veri koleksiyonunun farklı şekillerde görüntülenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="d34bb-103">Views allow the same data collection to be viewed in different ways, depending on sorting, filtering, or grouping criteria.</span></span> <span data-ttu-id="d34bb-104">Her koleksiyonda bir bağlama kaynağı olarak bir koleksiyon belirttiğinde gerçek bağlama kaynağı olarak kullanılan bir paylaşılan varsayılan görünüm bulunur.</span><span class="sxs-lookup"><span data-stu-id="d34bb-104">Every collection has one shared default view, which is used as the actual binding source when a binding specifies a collection as its source.</span></span> <span data-ttu-id="d34bb-105">Bu örnek, bir koleksiyonun varsayılan görünümünün nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d34bb-105">This example shows how to get the default view of a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d34bb-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="d34bb-106">Example</span></span>  
 <span data-ttu-id="d34bb-107">Görünümü oluşturmak için, koleksiyona bir nesne başvurusu gerekir.</span><span class="sxs-lookup"><span data-stu-id="d34bb-107">To create the view, you need an object reference to the collection.</span></span> <span data-ttu-id="d34bb-108">Bu veri nesnesi, veri bağlamını alarak, veri kaynağının bir özelliğini alarak ya da bağlamanın bir özelliği alarak, kendi arka plan kod nesneniz aracılığıyla elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="d34bb-108">This data object can be obtained by referencing your own code-behind object, by getting the data context, by getting a property of the data source, or by getting a property of the binding.</span></span> <span data-ttu-id="d34bb-109">Bu örnek, bir veri nesnesinin <xref:System.Windows.FrameworkElement.DataContext%2A> nasıl alınacağını ve bu koleksiyon için varsayılan koleksiyon görünümünü doğrudan elde etmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d34bb-109">This example shows how to get the <xref:System.Windows.FrameworkElement.DataContext%2A> of a data object and use it to directly obtain the default collection view for this collection.</span></span>  
  
 [!code-csharp[CollectionView#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#2)]
 [!code-vb[CollectionView#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#2)]  
  
 <span data-ttu-id="d34bb-110">Bu örnekte, kök öğe bir <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="d34bb-110">In this example, the root element is a <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="d34bb-111"><xref:System.Windows.FrameworkElement.DataContext%2A>, nesneleri *sıralama* <xref:System.Collections.ObjectModel.ObservableCollection%601> bir veri sağlayıcısına başvuran *myDataSource*olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d34bb-111">The <xref:System.Windows.FrameworkElement.DataContext%2A> is set to *myDataSource*, which refers to a data provider that is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of *Order* objects.</span></span>  
  
 [!code-xaml[CollectionView#CollectionViewDataContext](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml#collectionviewdatacontext)]  
  
 <span data-ttu-id="d34bb-112">Alternatif olarak, <xref:System.Windows.Data.CollectionViewSource> sınıfını kullanarak kendi koleksiyon görünümünüzü oluşturabilir ve bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d34bb-112">Alternatively, you can instantiate and bind to your own collection view using the <xref:System.Windows.Data.CollectionViewSource> class.</span></span> <span data-ttu-id="d34bb-113">Bu koleksiyon görünümü yalnızca doğrudan buna bağlanan denetimler tarafından paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="d34bb-113">This collection view is only shared by controls that bind to it directly.</span></span> <span data-ttu-id="d34bb-114">Bir örnek için, [veri bağlamaya genel bakış](../../../desktop-wpf/data/data-binding-overview.md)konusunun görünüm oluşturma bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="d34bb-114">For an example, see the How to Create a View section in the [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="d34bb-115">Bir koleksiyon görünümü tarafından sunulan işlevselliğe örnek olarak, bkz. [verileri bir görünümde sıralama](how-to-sort-data-in-a-view.md), [görünümdeki verileri filtreleme](how-to-filter-data-in-a-view.md)ve [Veri CollectionView içindeki nesneler üzerinde gezinme](how-to-navigate-through-the-objects-in-a-data-collectionview.md).</span><span class="sxs-lookup"><span data-stu-id="d34bb-115">For examples of the functionality provided by a collection view, see [Sort Data in a View](how-to-sort-data-in-a-view.md), [Filter Data in a View](how-to-filter-data-in-a-view.md), and [Navigate Through the Objects in a Data CollectionView](how-to-navigate-through-the-objects-in-a-data-collectionview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d34bb-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d34bb-116">See also</span></span>

- [<span data-ttu-id="d34bb-117">XAML İçerisinde bir Görüntü Kullanarak Verileri Sıralama ve Gruplama</span><span class="sxs-lookup"><span data-stu-id="d34bb-117">Sort and Group Data Using a View in XAML</span></span>](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [<span data-ttu-id="d34bb-118">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="d34bb-118">How-to Topics</span></span>](data-binding-how-to-topics.md)
