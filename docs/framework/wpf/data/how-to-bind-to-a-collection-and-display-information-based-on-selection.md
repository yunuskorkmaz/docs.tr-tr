---
title: 'Nasıl yapılır: Koleksiyona Bağlama ve Seçime Göre Bilgi Görüntüleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data collections [WPF], selecting data for views
- data binding [WPF], creating views of data collections
- data binding [WPF], selecting data for views
- data binding [WPF], binding to collections
ms.assetid: 952a7d76-dd29-49e5-86f5-32c4530e70eb
ms.openlocfilehash: 549f4e7af1a9aa623c7f8ff12b528f771a8ff806
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54504790"
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a>Nasıl yapılır: Koleksiyona Bağlama ve Seçime Göre Bilgi Görüntüleme
Basit bir ana öğe-ayrıntı senaryosunda elinizdeki verilere bağlı <xref:System.Windows.Controls.ItemsControl> gibi bir <xref:System.Windows.Controls.ListBox>. Kullanıcı seçimine göre seçili öğe hakkında daha fazla bilgi görüntüler. Bu örnek, bu senaryonun nasıl uygulanacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, `People` olduğu bir <xref:System.Collections.ObjectModel.ObservableCollection%601> , `Person` sınıfları. Bu `Person` sınıfı üç özellik içerir: `FirstName`, `LastName`, ve `HomeTown`, tümü `string`.  
  
 [!code-xaml[CollectionBinding#Source](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <xref:System.Windows.Controls.ContentControl> Aşağıdaki kullanan <xref:System.Windows.DataTemplate> tanımlayan nasıl bilgilerini bir `Person` sunulur:  
  
 [!code-xaml[CollectionBinding#DetailTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 Örneğin ürettiği bir ekran görüntüsü aşağıda verilmiştir. <xref:System.Windows.Controls.ContentControl> Seçilen kişinin diğer özelliklerini gösterir.  
  
 ![Koleksiyona bağlama](../../../../docs/framework/wpf/data/media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")  
  
 Bu örnekte fark etmeye iki şey vardır:  
  
1.  <xref:System.Windows.Controls.ListBox> Ve <xref:System.Windows.Controls.ContentControl> aynı kaynağa bağlanır. <xref:System.Windows.Data.Binding.Path%2A> Özellikleri belirtilmemiştir çünkü her iki denetim için tüm koleksiyon nesnesi belirtilmedi.  
  
2.  Ayarlamalısınız <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> özelliğini `true` Bunun çalışması. Bu özelliğin ayarlanması sağlar Seçili öğe olarak her zaman ayarlandığından <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>. Alternatif olarak, <xref:System.Windows.Controls.ListBox> öğesinden veri alır bir <xref:System.Windows.Data.CollectionViewSource>, seçim ve para birimi otomatik olarak eşitler.  
  
 Unutmayın `Person` sınıf geçersiz kılmalarını `ToString` yöntemini aşağıdaki şekilde. Varsayılan olarak, <xref:System.Windows.Controls.ListBox> çağrıları `ToString` ve ilişkili koleksiyondaki her bir nesnenin dize gösterimini görüntüler. İşte bu nedenle her `Person` ilk adı olarak görünür <xref:System.Windows.Controls.ListBox>.  
  
 [!code-csharp[CollectionBinding#ToString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Hiyerarşik Veriler ile Ana Öğe-Ayrıntı Desenini Kullanma](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)
- [Hiyerarşik XML Verileri ile Ana Öğe-Ayrıntı Desenini Kullanma](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Veri Şablonu Oluşturmaya Genel Bakış](../../../../docs/framework/wpf/data/data-templating-overview.md)
- [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
