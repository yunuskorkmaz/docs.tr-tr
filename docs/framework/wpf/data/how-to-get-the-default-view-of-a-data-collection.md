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
---
# <a name="how-to-get-the-default-view-of-a-data-collection"></a>Nasıl yapılır: Veri Koleksiyonunun Varsayılan Görünümünü Alma
Görünümler, aynı veri koleksiyonunu sıralama, filtreleme veya gruplandırma ölçütlerine bağlı olarak farklı şekillerde görüntülenmesine izin verir. Her koleksiyon bir bağlama, kaynağı olarak bir koleksiyon belirttiğinde gerçek bağlama kaynağı olarak kullanılan bir paylaşılan varsayılan görünüme sahiptir. Bu örnek, bir koleksiyon varsayılan görünümünü elde gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Görünümü oluşturmak için bir nesne başvurusu koleksiyonuna gerekir. Bu veri nesnesi, veri kaynağının bir özellik alma ya da bağlamanın bir özelliği alma veri bağlamı alarak kendi arka plan kodu nesneye başvuran tarafından alınabilir. Bu örnek nasıl alınacağını gösterir <xref:System.Windows.FrameworkElement.DataContext%2A> doğrudan varsayılan koleksiyonu almak üzere bir veri nesnesi ve kullanım bu koleksiyon için görüntüleyin.  
  
 [!code-csharp[CollectionView#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#2)]
 [!code-vb[CollectionView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#2)]  
  
 Bu örnekte, kök öğesi olan bir <xref:System.Windows.Controls.StackPanel>. <xref:System.Windows.FrameworkElement.DataContext%2A> Ayarlanır *gelen veriKaynağım'a*, olan bir veri sağlayıcısı başvuran bir <xref:System.Collections.ObjectModel.ObservableCollection%601> , *sipariş* nesneleri.  
  
 [!code-xaml[CollectionView#CollectionViewDataContext](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml#collectionviewdatacontext)]  
  
 Alternatif olarak, örneği ve bağlamak için kendi koleksiyonu görünümüyle <xref:System.Windows.Data.CollectionViewSource> sınıfı. Bu koleksiyon görünümü yalnızca doğrudan bağlayan denetimler tarafından paylaşılır. Bir örnek için bir görünüm içinde oluşturulur bölümüne nasıl bakın [veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Koleksiyon görünümü tarafından sağlanan işlevleri örnekleri için bkz: [bir görünümdeki verileri sıralama](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md), [görünümünde filtre veri](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md), ve [gidin aracılığıyla nesnelerindeki Veri CollectionView](../../../../docs/framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XAML İçerisinde bir Görüntü Kullanarak Verileri Sıralama ve Gruplama](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
