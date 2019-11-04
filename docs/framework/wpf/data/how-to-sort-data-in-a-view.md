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
ms.openlocfilehash: 14314ed019f9194a657787bd767ae68615e94ac7
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454832"
---
# <a name="how-to-sort-data-in-a-view"></a>Nasıl yapılır: Görünümde Verileri Sıralama
Bu örnek, bir görünümdeki verilerin nasıl sıralanacağını açıklar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek basit bir <xref:System.Windows.Controls.ListBox> ve <xref:System.Windows.Controls.Button>oluşturur:  
  
 [!code-xaml[ListBoxSort_snip#HowTo](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml#howto)]  
  
 Düğmenin <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay işleyicisi, <xref:System.Windows.Controls.ListBox> öğeleri azalan düzende sıralamak için mantık içerir. Bu şekilde, <xref:System.Windows.Controls.ListBox> öğe eklemek <xref:System.Windows.Controls.ListBox><xref:System.Windows.Controls.ItemCollection> <xref:System.Windows.Controls.ItemCollection> ve <xref:System.Windows.Data.CollectionView> sınıfından türediği için bunu yapabilirsiniz. <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliğini kullanarak bir koleksiyona bağlıyorsanız, sıralamak için aynı tekniği kullanabilirsiniz.  
  
 [!code-csharp[ListBoxSort_snip#HowToCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml.cs#howtocode)]
 [!code-vb[ListBoxSort_snip#HowToCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxSort_snip/visualbasic/window1.xaml.vb#howtocode)]  
  
 Görünüm nesnesine bir başvurunuz olduğu sürece, diğer koleksiyon görünümlerinin içeriğini sıralamak için aynı tekniği kullanabilirsiniz. Görünüm alma hakkında bir örnek için bkz. [veri koleksiyonunun varsayılan görünümünü alma](how-to-get-the-default-view-of-a-data-collection.md). Diğer bir örnek için bkz. [bir başlık tıklandığında GridView sütununu sıralama](../controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md). Görünümler hakkında daha fazla bilgi için bkz. [veri bağlamasındaki koleksiyonlara bağlama genel bakış](../../../desktop-wpf/data/data-binding-overview.md).  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]sıralama mantığının nasıl uygulanacağı hakkında bir örnek için bkz. [xaml 'de bir görünüm kullanarak verileri sıralama ve gruplama](how-to-sort-and-group-data-using-a-view-in-xaml.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Data.ListCollectionView.CustomSort%2A>
- [Üst Bilgiye Tıklandığında GridView Sütununu Sıralama](../controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)
- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Görünümde Veri Filtreleme](how-to-filter-data-in-a-view.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
