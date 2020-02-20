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
ms.openlocfilehash: f15bcfd1e3c4175f8b4b97244f120d5edbdec9b8
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453084"
---
# <a name="how-to-filter-data-in-a-view"></a>Nasıl yapılır: Görünümde Veri Filtreleme
Bu örnekte, bir görünümdeki verilerin nasıl filtreleneceği gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Filtre oluşturmak için filtreleme mantığını sağlayan bir yöntem tanımlayın. Yöntemi, bir geri çağırma olarak kullanılır ve `object`türünde bir parametreyi kabul eder. Aşağıdaki yöntem, `filled` özelliği "Hayır" olarak ayarlanmış tüm `Order` nesnelerini döndürür ve nesnelerin geri kalanını filtreler.  
  
 [!code-csharp[SortFilter#2](~/samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#2)]
 [!code-vb[SortFilter#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#2)]  
  
 Ardından, aşağıdaki örnekte gösterildiği gibi filtreyi uygulayabilirsiniz. Bu örnekte, `myCollectionView` bir <xref:System.Windows.Data.ListCollectionView> nesnesidir.  
  
 [!code-csharp[SortFilter#Filter](~/samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#filter)]
 [!code-vb[SortFilter#Filter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#filter)]  
  
 Filtrelemeyi geri almak için <xref:System.Windows.Data.CollectionView.Filter%2A> özelliğini `null`olarak ayarlayabilirsiniz:  
  
 [!code-csharp[SortFilter#Unfilter](~/samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#unfilter)]
 [!code-vb[SortFilter#Unfilter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#unfilter)]  
  
 Bir görünüm oluşturma veya alma hakkında daha fazla bilgi için bkz. [veri koleksiyonunun varsayılan görünümünü alma](how-to-get-the-default-view-of-a-data-collection.md). Tüm örnek için bkz. [bir görünüm örneğinde öğeleri sıralama ve filtreleme](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/SortFilter).  
  
 Görünüm nesneniz bir <xref:System.Windows.Data.CollectionViewSource> nesnesinden geliyorsa, <xref:System.Windows.Data.CollectionViewSource.Filter> olayı için bir olay işleyicisi ayarlayarak filtreleme mantığını uygularsınız. Aşağıdaki örnekte, `listingDataView` bir <xref:System.Windows.Data.CollectionViewSource>örneğidir.  
  
 [!code-csharp[DataBindingLab#10](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 Aşağıda örnek `ShowOnlyBargainsFilter` Filter olay işleyicisi örneği verilmiştir. Bu olay işleyicisi, $25 veya daha büyük bir `CurrentPrice` sahip `AuctionItem` nesneleri filtrelemek için <xref:System.Windows.Data.FilterEventArgs.Accepted%2A> özelliğini kullanır.  
  
 [!code-csharp[DataBindingLab#5](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Data.CollectionView.CanFilter%2A>
- <xref:System.Windows.Data.BindingListCollectionView.CustomFilter%2A>
- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Görünümde Verileri Sıralama](how-to-sort-data-in-a-view.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
