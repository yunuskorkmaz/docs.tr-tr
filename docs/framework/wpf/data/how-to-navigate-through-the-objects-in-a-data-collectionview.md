---
title: "Nasıl yapılır: Veri CollectionView İçindeki Nesneler Aracılığıyla Gezinme"
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
- CollectionView [WPF], navigating through objects
- data binding [WPF], navigating through objects in data CollectionView
- navigating through objects in data CollectionView [WPF]
ms.assetid: fcd37590-bce1-4ac9-8b74-3b96c7458b8a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f20881ed452f1ec78381d17a32b4cc2c77305e0e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-navigate-through-the-objects-in-a-data-collectionview"></a><span data-ttu-id="1dabd-102">Nasıl yapılır: Veri CollectionView İçindeki Nesneler Aracılığıyla Gezinme</span><span class="sxs-lookup"><span data-stu-id="1dabd-102">How to: Navigate Through the Objects in a Data CollectionView</span></span>
<span data-ttu-id="1dabd-103">Görünümler, aynı veri koleksiyonunu sıralama, filtreleme veya gruplandırma bağlı olarak farklı şekillerde görüntülenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="1dabd-103">Views allow the same data collection to be viewed in different ways, depending on sorting, filtering, or grouping.</span></span> <span data-ttu-id="1dabd-104">Görünümleri de geçerli bir kayıt işaretçi kavramını sağlar ve işaretçiyi taşıma etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="1dabd-104">Views also provide a current record pointer concept and enable moving the pointer.</span></span> <span data-ttu-id="1dabd-105">Bu örnek yanı sıra geçerli nesne get sağlanan işlevini kullanarak bir veri toplama nesneleri gezinmek gösterilmektedir <xref:System.Windows.Data.CollectionView> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1dabd-105">This example shows how to get the current object as well as navigate through the objects in a data collection using the functionality provided in the <xref:System.Windows.Data.CollectionView> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1dabd-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="1dabd-106">Example</span></span>  
 <span data-ttu-id="1dabd-107">Bu örnekte, `myCollectionView` olan bir <xref:System.Windows.Data.CollectionView> bir görünüm bağlı bir koleksiyon nesnesi.</span><span class="sxs-lookup"><span data-stu-id="1dabd-107">In this example, `myCollectionView` is a <xref:System.Windows.Data.CollectionView> object that is a view over a bound collection.</span></span>  
  
 <span data-ttu-id="1dabd-108">Aşağıdaki örnekte, `OnButton` bir olay işleyicisi için `Previous` ve `Next` veri toplama gitmek kullanıcı izin düğmeleri olan bir uygulama düğmelerini.</span><span class="sxs-lookup"><span data-stu-id="1dabd-108">In the following example, `OnButton` is an event handler for the `Previous` and `Next` buttons in an application, which are buttons that allow the user to navigate the data collection.</span></span> <span data-ttu-id="1dabd-109">Unutmayın <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> ve <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> rapor özelliklerini geçerli kayıt işaretçisi başında ve sonunda listesinin için sırasıyla böylece gelip gelmediğini <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> ve <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> uygun olarak çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="1dabd-109">Note that the <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> and <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> properties report whether the current record pointer has come to the beginning and the end of the list respectively so that <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> and <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> can be called as appropriately.</span></span>  
  
 <span data-ttu-id="1dabd-110"><xref:System.Windows.Data.CollectionView.CurrentItem%2A> Görünümünün özelliği olarak atandığında bir `Order` güncel sıradaki öğeyi koleksiyonda döndürülecek.</span><span class="sxs-lookup"><span data-stu-id="1dabd-110">The <xref:System.Windows.Data.CollectionView.CurrentItem%2A> property of the view is cast as an `Order` to return the current order item in the collection.</span></span>  
  
 [!code-csharp[CollectionView#OnButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#onbutton)]
 [!code-vb[CollectionView#OnButton](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#onbutton)]  
  
## <a name="see-also"></a><span data-ttu-id="1dabd-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1dabd-111">See Also</span></span>  
 [<span data-ttu-id="1dabd-112">Veri bağlama genel bakış</span><span class="sxs-lookup"><span data-stu-id="1dabd-112">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="1dabd-113">Bir görünümdeki verileri sıralama</span><span class="sxs-lookup"><span data-stu-id="1dabd-113">Sort Data in a View</span></span>](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)  
 [<span data-ttu-id="1dabd-114">Bir görünümündeki verileri filtreleme</span><span class="sxs-lookup"><span data-stu-id="1dabd-114">Filter Data in a View</span></span>](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)  
 [<span data-ttu-id="1dabd-115">XAML'de bir görünümü kullanarak Grup verileri sıralama ve</span><span class="sxs-lookup"><span data-stu-id="1dabd-115">Sort and Group Data Using a View in XAML</span></span>](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)  
 [<span data-ttu-id="1dabd-116">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="1dabd-116">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
