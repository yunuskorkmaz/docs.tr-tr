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
ms.openlocfilehash: 41ee5cded04559acac5e7270c5e1a2450c70a5aa
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377125"
---
# <a name="how-to-sort-data-in-a-view"></a>Nasıl yapılır: Görünümde Verileri Sıralama
Bu örnek, bir görünümde verileri sıralama açıklar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, basit bir oluşturur <xref:System.Windows.Controls.ListBox> ve <xref:System.Windows.Controls.Button>:  
  
 [!code-xaml[ListBoxSort_snip#HowTo](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml#howto)]  
  
 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Düğmesi olay işleyicisi içindeki öğeleri sıralamak için mantık içerir <xref:System.Windows.Controls.ListBox> azalan düzende. Öğeler ekleme çünkü bunu bir <xref:System.Windows.Controls.ListBox> bu şekilde eklenmeye <xref:System.Windows.Controls.ItemCollection> , <xref:System.Windows.Controls.ListBox>, ve <xref:System.Windows.Controls.ItemCollection> türetildiği <xref:System.Windows.Data.CollectionView> sınıfı. Bağlıyorsanız, <xref:System.Windows.Controls.ListBox> kullanarak bir koleksiyon <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliği sıralamak için aynı tekniği kullanabilirsiniz.  
  
 [!code-csharp[ListBoxSort_snip#HowToCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxSort_snip/CSharp/Window1.xaml.cs#howtocode)]
 [!code-vb[ListBoxSort_snip#HowToCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxSort_snip/visualbasic/window1.xaml.vb#howtocode)]  
  
 Görünüm nesnesine bir başvuru olduğu sürece, diğer koleksiyon görünümlerini içeriğini sıralamak için aynı tekniği kullanabilirsiniz. Bir görünüm elde etmek nasıl bir örnek için bkz [veri koleksiyonunun varsayılan görünümünü alma](how-to-get-the-default-view-of-a-data-collection.md). Başka bir örnek için bkz: [bir GridView Sütun, bir üstbilgi tıklandığında sıralama](../controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md). Koleksiyonlarında bağlama görünümleri hakkında daha fazla bilgi için bkz. [Data Binding Overview](data-binding-overview.md).  
  
 Sıralama mantığı uygulamak nasıl bir örnek için [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], bkz: [sıralama ve Grup verileri kullanarak XAML görünümünde](how-to-sort-and-group-data-using-a-view-in-xaml.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Data.ListCollectionView.CustomSort%2A>
- [Üst Bilgiye Tıklandığında GridView Sütununu Sıralama](../controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)
- [Veri Bağlamaya Genel Bakış](data-binding-overview.md)
- [Görünümde Veri Filtreleme](how-to-filter-data-in-a-view.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
