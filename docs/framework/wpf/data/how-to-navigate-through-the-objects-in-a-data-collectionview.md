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
ms.workload: dotnet
ms.openlocfilehash: 215e3583d50567a2bfec8226e006bc7398628299
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-navigate-through-the-objects-in-a-data-collectionview"></a>Nasıl yapılır: Veri CollectionView İçindeki Nesneler Aracılığıyla Gezinme
Görünümler, aynı veri koleksiyonunu sıralama, filtreleme veya gruplandırma bağlı olarak farklı şekillerde görüntülenmesine izin verir. Görünümleri de geçerli bir kayıt işaretçi kavramını sağlar ve işaretçiyi taşıma etkinleştirin. Bu örnek yanı sıra geçerli nesne get sağlanan işlevini kullanarak bir veri toplama nesneleri gezinmek gösterilmektedir <xref:System.Windows.Data.CollectionView> sınıfı.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, `myCollectionView` olan bir <xref:System.Windows.Data.CollectionView> bir görünüm bağlı bir koleksiyon nesnesi.  
  
 Aşağıdaki örnekte, `OnButton` bir olay işleyicisi için `Previous` ve `Next` veri toplama gitmek kullanıcı izin düğmeleri olan bir uygulama düğmelerini. Unutmayın <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> ve <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> rapor özelliklerini geçerli kayıt işaretçisi başında ve sonunda listesinin için sırasıyla böylece gelip gelmediğini <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> ve <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> uygun olarak çağrılabilir.  
  
 <xref:System.Windows.Data.CollectionView.CurrentItem%2A> Görünümünün özelliği olarak atandığında bir `Order` güncel sıradaki öğeyi koleksiyonda döndürülecek.  
  
 [!code-csharp[CollectionView#OnButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#onbutton)]
 [!code-vb[CollectionView#OnButton](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#onbutton)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Görünümde Verileri Sıralama](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)  
 [Görünümde Veri Filtreleme](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)  
 [XAML İçerisinde bir Görüntü Kullanarak Verileri Sıralama ve Gruplama](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
