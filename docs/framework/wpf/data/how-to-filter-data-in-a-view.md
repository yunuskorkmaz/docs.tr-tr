---
title: 'Nasıl yapılır: Görünümde Veri Filtreleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- views [WPF], filtering data
- filtering data in views [WPF]
- data binding [WPF], filtering data in views
ms.assetid: c76e8606-4cc4-45a8-9110-e2ec66dc6afd
ms.openlocfilehash: 55ec68e8918c9f7fbc9d3ac0062926cc03cb5e10
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556659"
---
# <a name="how-to-filter-data-in-a-view"></a>Nasıl yapılır: Görünümde Veri Filtreleme
Bu örnek bir görünümündeki verileri filtrelemek nasıl gösterir.  
  
## <a name="example"></a>Örnek  
 Bir filtre oluşturmak için filtreleme mantığı sağlayan bir yöntemi tanımlayın. Yöntem geri arama olarak kullanılan ve türünde bir parametre kabul eden `object`. Aşağıdaki yöntem tüm döndürür `Order` nesnelerini `filled` özelliği "Hayır" geri kalan nesneleri filtreleme, ayarlanmış.  
  
 [!code-csharp[SortFilter#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#2)]
 [!code-vb[SortFilter#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#2)]  
  
 Aşağıdaki örnekte gösterildiği gibi daha sonra filtre uygulayabilirsiniz. Bu örnekte, `myCollectionView` olan bir <xref:System.Windows.Data.ListCollectionView> nesnesi.  
  
 [!code-csharp[SortFilter#Filter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#filter)]
 [!code-vb[SortFilter#Filter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#filter)]  
  
 Filtreleme geri almak için ayarlayabileceğiniz <xref:System.Windows.Data.CollectionView.Filter%2A> özelliğine `null`:  
  
 [!code-csharp[SortFilter#Unfilter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#unfilter)]
 [!code-vb[SortFilter#Unfilter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#unfilter)]  
  
 Oluşturma ve bir görünüm elde etme hakkında daha fazla bilgi için bkz: [veri koleksiyonunun varsayılan görünümünü elde](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md). Tam bir örnek için bkz: [sıralama ve filtreleme öğeleri görünüm örnekteki](http://go.microsoft.com/fwlink/?LinkID=160040).  
  
 Görünüm nesnesi geliyorsa bir <xref:System.Windows.Data.CollectionViewSource> nesne için bir olay işleyicisi ayarlayarak filtreleme mantığını uygulamak <xref:System.Windows.Data.CollectionViewSource.Filter> olay. Aşağıdaki örnekte, `listingDataView` örneği <xref:System.Windows.Data.CollectionViewSource>.  
  
 [!code-csharp[DataBindingLab#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 Aşağıdaki örnek uygulamasını gösterir `ShowOnlyBargainsFilter` filtre olay işleyicisi. Bu olay işleyicisi kullanan <xref:System.Windows.Data.FilterEventArgs.Accepted%2A> filtrelemek için özellik `AuctionItem` sahip nesneleri bir `CurrentPrice` $25 veya daha büyük.  
  
 [!code-csharp[DataBindingLab#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Data.CollectionView.CanFilter%2A>  
 <xref:System.Windows.Data.BindingListCollectionView.CustomFilter%2A>  
 [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Görünümde Verileri Sıralama](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
