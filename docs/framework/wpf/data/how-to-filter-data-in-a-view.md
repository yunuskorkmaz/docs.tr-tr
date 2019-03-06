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
ms.openlocfilehash: 51f95834556153448d416157460cf63da0d409e1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373952"
---
# <a name="how-to-filter-data-in-a-view"></a>Nasıl yapılır: Görünümde Veri Filtreleme
Bu örnek, görünümde veri filtreleme yapılacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Bir filtre oluşturmak için filtreleme mantığı sağlayan bir yöntem tanımlayın. Yöntemi, bir geri arama olarak kullanılan ve türünde bir parametreyi kabul eden `object`. Aşağıdaki yöntem tüm döndürür `Order` nesnelerini `filled` "Hayır", geri kalan nesneleri filtreleme özelliği.  
  
 [!code-csharp[SortFilter#2](~/samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#2)]
 [!code-vb[SortFilter#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#2)]  
  
 Ardından, aşağıdaki örnekte gösterildiği gibi filtre uygulayabilirsiniz. Bu örnekte, `myCollectionView` olduğu bir <xref:System.Windows.Data.ListCollectionView> nesne.  
  
 [!code-csharp[SortFilter#Filter](~/samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#filter)]
 [!code-vb[SortFilter#Filter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#filter)]  
  
 Filtreleme geri almak için ayarlayabileceğiniz <xref:System.Windows.Data.CollectionView.Filter%2A> özelliğini `null`:  
  
 [!code-csharp[SortFilter#Unfilter](~/samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#unfilter)]
 [!code-vb[SortFilter#Unfilter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#unfilter)]  
  
 Oluşturma ve bir görünüm elde etme hakkında daha fazla bilgi için bkz. [veri koleksiyonunun varsayılan görünümünü alma](how-to-get-the-default-view-of-a-data-collection.md). Tam bir örnek için bkz. [sıralama ve filtreleme öğeleri görünüm örnek](https://go.microsoft.com/fwlink/?LinkID=160040).  
  
 Görünüm nesnesi geliyorsa bir <xref:System.Windows.Data.CollectionViewSource> nesne için bir olay işleyicisi ayarlayarak filtreleme mantığı uygulamak <xref:System.Windows.Data.CollectionViewSource.Filter> olay. Aşağıdaki örnekte, `listingDataView` örneğidir <xref:System.Windows.Data.CollectionViewSource>.  
  
 [!code-csharp[DataBindingLab#10](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 Aşağıdaki örnek uygulamasını gösterir `ShowOnlyBargainsFilter` filtre olay işleyicisi. Bu olay işleyicisi kullanır <xref:System.Windows.Data.FilterEventArgs.Accepted%2A> filtrelemek için özellik `AuctionItem` olan nesneleri bir `CurrentPrice` $25 veya daha büyük.  
  
 [!code-csharp[DataBindingLab#5](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Data.CollectionView.CanFilter%2A>
- <xref:System.Windows.Data.BindingListCollectionView.CustomFilter%2A>
- [Veri Bağlamaya Genel Bakış](data-binding-overview.md)
- [Görünümde Verileri Sıralama](how-to-sort-data-in-a-view.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
