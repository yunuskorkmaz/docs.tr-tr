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
ms.openlocfilehash: 5ca386db89dcaa66d364d2ed7169c67393cebead
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459710"
---
# <a name="how-to-navigate-through-the-objects-in-a-data-collectionview"></a>Nasıl yapılır: Veri CollectionView İçindeki Nesneler Aracılığıyla Gezinme
Görünümler aynı veri koleksiyonunun sıralamaya, filtrelemeye veya gruplandırmaya bağlı olarak farklı şekillerde görüntülenmesine izin verir. Görünümler aynı zamanda geçerli bir kayıt işaretçisi kavramı sağlar ve işaretçinin taşınmasını etkinleştirir. Bu örnek, <xref:System.Windows.Data.CollectionView> sınıfında sunulan işlevleri kullanarak, geçerli nesnenin nasıl alınacağını ve bir veri koleksiyonundaki nesneler arasında nasıl gezinilin olduğunu gösterir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, `myCollectionView`, bağlantılı bir koleksiyon üzerinde bir görünüm olan <xref:System.Windows.Data.CollectionView> nesnesidir.  
  
 Aşağıdaki örnekte `OnButton`, bir uygulamadaki `Previous` ve `Next` düğmeleri için bir olay işleyicisidir ve kullanıcının veri koleksiyonunda gezinmelerini sağlayan düğmelerdir. <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> ve <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> özelliklerinin, <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> ve <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> uygun şekilde çağrılabilmesi için, geçerli kayıt işaretçisinin listenin başına ve sonuna gelip gelmediğini raporlamayacağını unutmayın.  
  
 Görünümün <xref:System.Windows.Data.CollectionView.CurrentItem%2A> özelliği, koleksiyondaki geçerli sıra öğesini döndürmek için bir `Order` olarak dönüştürüldü.  
  
 [!code-csharp[CollectionView#OnButton](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#onbutton)]
 [!code-vb[CollectionView#OnButton](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#onbutton)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Görünümde Verileri Sıralama](how-to-sort-data-in-a-view.md)
- [Görünümde Veri Filtreleme](how-to-filter-data-in-a-view.md)
- [XAML İçerisinde bir Görüntü Kullanarak Verileri Sıralama ve Gruplama](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
