---
title: 'Nasıl yapılır: Görünümde Verileri Sıralama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], sorting data in views
- data binding [WPF], grouping data in views
- grouping data in views [WPF]
- views [WPF], sorting data
- views [WPF], grouping data
- sorting data in views [WPF]
ms.assetid: f4c43578-01b7-4774-a953-acb95a13b94a
ms.openlocfilehash: 5c79261983fcf6200120bcfbf180d155aca3c3c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-sort-data-in-a-view"></a>Nasıl yapılır: Görünümde Verileri Sıralama
Bu örnek, bir görünümündeki verileri sıralamak açıklar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, basit bir oluşturur <xref:System.Windows.Controls.ListBox> ve <xref:System.Windows.Controls.Button>:  
  
 [!code-xaml[ListBoxSort_snip#HowTo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml#howto)]  
  
 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Düğmesinin olay işleyiciyi içeriyor öğeleri sıralamak için mantık <xref:System.Windows.Controls.ListBox> azalan düzende. Öğeler ekleme çünkü bunu yapabilirsiniz bir <xref:System.Windows.Controls.ListBox> bu şekilde eklenmektedir <xref:System.Windows.Controls.ItemCollection> , <xref:System.Windows.Controls.ListBox>, ve <xref:System.Windows.Controls.ItemCollection> türetilen <xref:System.Windows.Data.CollectionView> sınıfı. Bağlıyorsanız, <xref:System.Windows.Controls.ListBox> kullanarak bir koleksiyon için <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özellik, sıralama için aynı tekniği kullanabilirsiniz.  
  
 [!code-csharp[ListBoxSort_snip#HowToCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml.cs#howtocode)]
 [!code-vb[ListBoxSort_snip#HowToCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxSort_snip/visualbasic/window1.xaml.vb#howtocode)]  
  
 Görünüm nesnesine başvuru sahip olduğu sürece, diğer koleksiyon görünümlerinin içeriğini sıralamak için aynı tekniği kullanabilirsiniz. Bir görünüm elde etme örneği için bkz: [veri koleksiyonunun varsayılan görünümünü elde](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md). Başka bir örnek için bkz: [bir GridView Sütun olduğunda bir üstbilgi tıklandığında sıralama](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md). Koleksiyonlarda bağlama görünümler hakkında daha fazla bilgi için bkz [veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Sıralama mantığı uygulamaya nasıl bir örnek için [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], bkz: [sıralama ve grup verilerini kullanan XAML görünümünde](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Data.ListCollectionView.CustomSort%2A>  
 [Üst Bilgiye Tıklandığında GridView Sütununu Sıralama](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)  
 [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Görünümde Veri Filtreleme](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
