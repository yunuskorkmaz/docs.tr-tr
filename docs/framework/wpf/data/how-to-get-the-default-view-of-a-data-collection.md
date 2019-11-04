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
# <a name="how-to-get-the-default-view-of-a-data-collection"></a>Nasıl yapılır: Veri Koleksiyonunun Varsayılan Görünümünü Alma
Görünümler, sıralama, filtreleme veya gruplandırma ölçütlerine bağlı olarak aynı veri koleksiyonunun farklı şekillerde görüntülenmesine izin verir. Her koleksiyonda bir bağlama kaynağı olarak bir koleksiyon belirttiğinde gerçek bağlama kaynağı olarak kullanılan bir paylaşılan varsayılan görünüm bulunur. Bu örnek, bir koleksiyonun varsayılan görünümünün nasıl alınacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Görünümü oluşturmak için, koleksiyona bir nesne başvurusu gerekir. Bu veri nesnesi, veri bağlamını alarak, veri kaynağının bir özelliğini alarak ya da bağlamanın bir özelliği alarak, kendi arka plan kod nesneniz aracılığıyla elde edilebilir. Bu örnek, bir veri nesnesinin <xref:System.Windows.FrameworkElement.DataContext%2A> nasıl alınacağını ve bu koleksiyon için varsayılan koleksiyon görünümünü doğrudan elde etmek için nasıl kullanılacağını gösterir.  
  
 [!code-csharp[CollectionView#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#2)]
 [!code-vb[CollectionView#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#2)]  
  
 Bu örnekte, kök öğe bir <xref:System.Windows.Controls.StackPanel>. <xref:System.Windows.FrameworkElement.DataContext%2A>, nesneleri *sıralama* <xref:System.Collections.ObjectModel.ObservableCollection%601> bir veri sağlayıcısına başvuran *myDataSource*olarak ayarlanır.  
  
 [!code-xaml[CollectionView#CollectionViewDataContext](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml#collectionviewdatacontext)]  
  
 Alternatif olarak, <xref:System.Windows.Data.CollectionViewSource> sınıfını kullanarak kendi koleksiyon görünümünüzü oluşturabilir ve bağlayabilirsiniz. Bu koleksiyon görünümü yalnızca doğrudan buna bağlanan denetimler tarafından paylaşılır. Bir örnek için, [veri bağlamaya genel bakış](../../../desktop-wpf/data/data-binding-overview.md)konusunun görünüm oluşturma bölümüne bakın.  
  
 Bir koleksiyon görünümü tarafından sunulan işlevselliğe örnek olarak, bkz. [verileri bir görünümde sıralama](how-to-sort-data-in-a-view.md), [görünümdeki verileri filtreleme](how-to-filter-data-in-a-view.md)ve [Veri CollectionView içindeki nesneler üzerinde gezinme](how-to-navigate-through-the-objects-in-a-data-collectionview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML İçerisinde bir Görüntü Kullanarak Verileri Sıralama ve Gruplama](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
