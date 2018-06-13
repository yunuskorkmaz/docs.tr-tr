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
ms.openlocfilehash: ec78b7350d23364cfb0eaa9a0611be8449073cd7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557010"
---
# <a name="how-to-navigate-through-the-objects-in-a-data-collectionview"></a><span data-ttu-id="b5c7c-102">Nasıl yapılır: Veri CollectionView İçindeki Nesneler Aracılığıyla Gezinme</span><span class="sxs-lookup"><span data-stu-id="b5c7c-102">How to: Navigate Through the Objects in a Data CollectionView</span></span>
<span data-ttu-id="b5c7c-103">Görünümler, aynı veri koleksiyonunu sıralama, filtreleme veya gruplandırma bağlı olarak farklı şekillerde görüntülenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="b5c7c-103">Views allow the same data collection to be viewed in different ways, depending on sorting, filtering, or grouping.</span></span> <span data-ttu-id="b5c7c-104">Görünümleri de geçerli bir kayıt işaretçi kavramını sağlar ve işaretçiyi taşıma etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="b5c7c-104">Views also provide a current record pointer concept and enable moving the pointer.</span></span> <span data-ttu-id="b5c7c-105">Bu örnek yanı sıra geçerli nesne get sağlanan işlevini kullanarak bir veri toplama nesneleri gezinmek gösterilmektedir <xref:System.Windows.Data.CollectionView> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b5c7c-105">This example shows how to get the current object as well as navigate through the objects in a data collection using the functionality provided in the <xref:System.Windows.Data.CollectionView> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5c7c-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="b5c7c-106">Example</span></span>  
 <span data-ttu-id="b5c7c-107">Bu örnekte, `myCollectionView` olan bir <xref:System.Windows.Data.CollectionView> bir görünüm bağlı bir koleksiyon nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b5c7c-107">In this example, `myCollectionView` is a <xref:System.Windows.Data.CollectionView> object that is a view over a bound collection.</span></span>  
  
 <span data-ttu-id="b5c7c-108">Aşağıdaki örnekte, `OnButton` bir olay işleyicisi için `Previous` ve `Next` veri toplama gitmek kullanıcı izin düğmeleri olan bir uygulama düğmelerini.</span><span class="sxs-lookup"><span data-stu-id="b5c7c-108">In the following example, `OnButton` is an event handler for the `Previous` and `Next` buttons in an application, which are buttons that allow the user to navigate the data collection.</span></span> <span data-ttu-id="b5c7c-109">Unutmayın <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> ve <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> rapor özelliklerini geçerli kayıt işaretçisi başında ve sonunda listesinin için sırasıyla böylece gelip gelmediğini <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> ve <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> uygun olarak çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="b5c7c-109">Note that the <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> and <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> properties report whether the current record pointer has come to the beginning and the end of the list respectively so that <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> and <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> can be called as appropriately.</span></span>  
  
 <span data-ttu-id="b5c7c-110"><xref:System.Windows.Data.CollectionView.CurrentItem%2A> Görünümünün özelliği olarak atandığında bir `Order` güncel sıradaki öğeyi koleksiyonda döndürülecek.</span><span class="sxs-lookup"><span data-stu-id="b5c7c-110">The <xref:System.Windows.Data.CollectionView.CurrentItem%2A> property of the view is cast as an `Order` to return the current order item in the collection.</span></span>  
  
 [!code-csharp[CollectionView#OnButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#onbutton)]
 [!code-vb[CollectionView#OnButton](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#onbutton)]  
  
## <a name="see-also"></a><span data-ttu-id="b5c7c-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b5c7c-111">See Also</span></span>  
 [<span data-ttu-id="b5c7c-112">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b5c7c-112">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="b5c7c-113">Görünümde Verileri Sıralama</span><span class="sxs-lookup"><span data-stu-id="b5c7c-113">Sort Data in a View</span></span>](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)  
 [<span data-ttu-id="b5c7c-114">Görünümde Veri Filtreleme</span><span class="sxs-lookup"><span data-stu-id="b5c7c-114">Filter Data in a View</span></span>](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)  
 [<span data-ttu-id="b5c7c-115">XAML İçerisinde bir Görüntü Kullanarak Verileri Sıralama ve Gruplama</span><span class="sxs-lookup"><span data-stu-id="b5c7c-115">Sort and Group Data Using a View in XAML</span></span>](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)  
 [<span data-ttu-id="b5c7c-116">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="b5c7c-116">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
