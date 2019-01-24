---
title: 'Nasıl yapılır: Veri CollectionView İçindeki Nesneler Aracılığıyla Gezinme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CollectionView [WPF], navigating through objects
- data binding [WPF], navigating through objects in data CollectionView
- navigating through objects in data CollectionView [WPF]
ms.assetid: fcd37590-bce1-4ac9-8b74-3b96c7458b8a
ms.openlocfilehash: c7de491a76ba6f8d5164c91f8c20bea4a8fa56d7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688408"
---
# <a name="how-to-navigate-through-the-objects-in-a-data-collectionview"></a><span data-ttu-id="a1d3b-102">Nasıl yapılır: Veri CollectionView İçindeki Nesneler Aracılığıyla Gezinme</span><span class="sxs-lookup"><span data-stu-id="a1d3b-102">How to: Navigate Through the Objects in a Data CollectionView</span></span>
<span data-ttu-id="a1d3b-103">Görünümler, aynı veri koleksiyonunu sıralama, filtreleme ve gruplandırma bağlı olarak farklı şekillerde görüntülenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="a1d3b-103">Views allow the same data collection to be viewed in different ways, depending on sorting, filtering, or grouping.</span></span> <span data-ttu-id="a1d3b-104">Görünümleri, ayrıca geçerli bir kayıt işaretçi kavramı sağlar ve imleci taşıma etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="a1d3b-104">Views also provide a current record pointer concept and enable moving the pointer.</span></span> <span data-ttu-id="a1d3b-105">Bu örnek geçerli nesne olarak sunulan işlevleri kullanarak bir veri koleksiyonu içindeki nesneler aracılığıyla gezinme nasıl gösterir <xref:System.Windows.Data.CollectionView> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a1d3b-105">This example shows how to get the current object as well as navigate through the objects in a data collection using the functionality provided in the <xref:System.Windows.Data.CollectionView> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1d3b-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="a1d3b-106">Example</span></span>  
 <span data-ttu-id="a1d3b-107">Bu örnekte, `myCollectionView` olduğu bir <xref:System.Windows.Data.CollectionView> bağlı bir koleksiyon üzerinde bir görünümü olan nesne.</span><span class="sxs-lookup"><span data-stu-id="a1d3b-107">In this example, `myCollectionView` is a <xref:System.Windows.Data.CollectionView> object that is a view over a bound collection.</span></span>  
  
 <span data-ttu-id="a1d3b-108">Aşağıdaki örnekte, `OnButton` için bir olay işleyicisi `Previous` ve `Next` bir uygulamada, veri toplama gitmek kullanıcının olanak tanıyan düğmeler düğmeleri.</span><span class="sxs-lookup"><span data-stu-id="a1d3b-108">In the following example, `OnButton` is an event handler for the `Previous` and `Next` buttons in an application, which are buttons that allow the user to navigate the data collection.</span></span> <span data-ttu-id="a1d3b-109">Unutmayın <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> ve <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> rapor özelliklerini geçerli kayıt işaretçisine başında ve sonunda listesinin için sırasıyla şekilde gelip gelmediğini <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> ve <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> uygun olarak çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="a1d3b-109">Note that the <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> and <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> properties report whether the current record pointer has come to the beginning and the end of the list respectively so that <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> and <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> can be called as appropriately.</span></span>  
  
 <span data-ttu-id="a1d3b-110"><xref:System.Windows.Data.CollectionView.CurrentItem%2A> Görünümün özelliği olarak atandığında bir `Order` koleksiyonda geçerli sipariş öğesi döndürülecek.</span><span class="sxs-lookup"><span data-stu-id="a1d3b-110">The <xref:System.Windows.Data.CollectionView.CurrentItem%2A> property of the view is cast as an `Order` to return the current order item in the collection.</span></span>  
  
 [!code-csharp[CollectionView#OnButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#onbutton)]
 [!code-vb[CollectionView#OnButton](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#onbutton)]  
  
## <a name="see-also"></a><span data-ttu-id="a1d3b-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1d3b-111">See also</span></span>
- [<span data-ttu-id="a1d3b-112">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a1d3b-112">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [<span data-ttu-id="a1d3b-113">Görünümde Verileri Sıralama</span><span class="sxs-lookup"><span data-stu-id="a1d3b-113">Sort Data in a View</span></span>](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)
- [<span data-ttu-id="a1d3b-114">Görünümde Veri Filtreleme</span><span class="sxs-lookup"><span data-stu-id="a1d3b-114">Filter Data in a View</span></span>](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)
- [<span data-ttu-id="a1d3b-115">XAML İçerisinde bir Görüntü Kullanarak Verileri Sıralama ve Gruplama</span><span class="sxs-lookup"><span data-stu-id="a1d3b-115">Sort and Group Data Using a View in XAML</span></span>](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [<span data-ttu-id="a1d3b-116">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="a1d3b-116">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
