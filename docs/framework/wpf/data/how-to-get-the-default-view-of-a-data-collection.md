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
ms.openlocfilehash: 746331e69ee1e5eee795a0e35202f4889b72c53f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59222113"
---
# <a name="how-to-get-the-default-view-of-a-data-collection"></a>Nasıl yapılır: Veri Koleksiyonunun Varsayılan Görünümünü Alma
Görünümler, aynı veri koleksiyonunu sıralama, filtreleme ve gruplandırma ölçütü bağlı olarak farklı şekillerde görüntülenmesine izin verir. Her koleksiyon bir bağlama, kaynağı olarak bir koleksiyon belirttiğinde gerçek bağlama kaynağı olarak kullanılan bir paylaşılan varsayılan görünüme sahiptir. Bu örnek, koleksiyonunun varsayılan görünümünü alma gösterir.  
  
## <a name="example"></a>Örnek  
 Görünümü oluşturmak için bir nesne başvurusunu koleksiyona gerekir. Bu veri nesnesi, kendi arka plan kod nesnesi alarak veri kaynağının bir özelliği ya da bağlamanın bir özelliği alarak veri bağlamı alarak başvurarak alınabilir. Bu örnek nasıl alınacağı gösterilmiştir <xref:System.Windows.FrameworkElement.DataContext%2A> doğrudan varsayılan koleksiyonu almak üzere bir veri nesnesi ve kullanmak bu koleksiyon için görüntüleyin.  
  
 [!code-csharp[CollectionView#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#2)]
 [!code-vb[CollectionView#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#2)]  
  
 Bu örnekte, kök öğe olduğundan bir <xref:System.Windows.Controls.StackPanel>. <xref:System.Windows.FrameworkElement.DataContext%2A> Ayarlanır *gelen veriKaynağım'a*, olan bir veri sağlayıcısı başvuran bir <xref:System.Collections.ObjectModel.ObservableCollection%601> , *sipariş* nesneleri.  
  
 [!code-xaml[CollectionView#CollectionViewDataContext](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml#collectionviewdatacontext)]  
  
 Alternatif olarak, oluşturmak ve bağlamak için kendi koleksiyonu görünümüyle <xref:System.Windows.Data.CollectionViewSource> sınıfı. Bu koleksiyon görünümü yalnızca doğrudan bağlayan denetimleri tarafından paylaşılır. Bir görünüm konusundaki oluşturma nasıl bir örnek için bakınız [Data Binding Overview](data-binding-overview.md).  
  
 Koleksiyon görünümü tarafından sağlanan işlevselliği örnekleri için bkz: [görünümde verileri sıralama](how-to-sort-data-in-a-view.md), [görünümde veri filtreleme](how-to-filter-data-in-a-view.md), ve [Git aracılığıyla CollectionView içindeki nesneler veri](how-to-navigate-through-the-objects-in-a-data-collectionview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML İçerisinde bir Görüntü Kullanarak Verileri Sıralama ve Gruplama](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
