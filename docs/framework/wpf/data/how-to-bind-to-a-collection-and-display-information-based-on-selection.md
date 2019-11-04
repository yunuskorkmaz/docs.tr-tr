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
ms.openlocfilehash: 032a1d98e1aa80ea755f5922f79d43a796e9697e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459148"
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a>Nasıl yapılır: Koleksiyona Bağlama ve Seçime Göre Bilgi Görüntüleme
Basit bir ana ayrıntı senaryosunda, <xref:System.Windows.Controls.ListBox>gibi bir veri bağlantılı <xref:System.Windows.Controls.ItemsControl> vardır. Kullanıcı seçimine bağlı olarak, seçili öğe hakkında daha fazla bilgi görüntülenir. Bu örnek, bu senaryonun nasıl uygulanacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, `People` `Person` sınıflarının bir <xref:System.Collections.ObjectModel.ObservableCollection%601>. Bu `Person` sınıfı üç özellik içerir: `FirstName`, `LastName`ve `HomeTown`, hepsi tür `string`.  
  
 [!code-xaml[CollectionBinding#Source](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <xref:System.Windows.Controls.ContentControl>, `Person` bilgilerinin nasıl sunulduğunu tanımlayan aşağıdaki <xref:System.Windows.DataTemplate> kullanır:  
  
 [!code-xaml[CollectionBinding#DetailTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 Aşağıda, örneğin ürettiği bir ekran görüntüsü verilmiştir. <xref:System.Windows.Controls.ContentControl>, seçilen kişinin diğer özelliklerini gösterir.  
  
 ![Koleksiyona bağlama](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")  
  
 Bu örnekte dikkat etmeniz gereken iki şey şunlardır:  
  
1. <xref:System.Windows.Controls.ListBox> ve <xref:System.Windows.Controls.ContentControl> aynı kaynağa bağlanır. Her iki bağlamanın <xref:System.Windows.Data.Binding.Path%2A> özellikleri belirtilmedi çünkü her iki denetim de tüm koleksiyon nesnesine bağlanıyor.  
  
2. Bunun çalışması için <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> özelliğini `true` olarak ayarlamanız gerekir. Bu özelliğin ayarlanması, seçilen öğenin her zaman <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>olarak ayarlanmasını sağlar. Alternatif olarak, <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Data.CollectionViewSource>verileri alırsa, seçim ve para birimini otomatik olarak eşitler.  
  
 `Person` sınıfının `ToString` yöntemini aşağıdaki şekilde geçersiz kıldığını unutmayın. Varsayılan olarak, <xref:System.Windows.Controls.ListBox> `ToString` çağırır ve bağlantılı koleksiyondaki her nesnenin dize temsilini görüntüler. Bu nedenle, her bir `Person` <xref:System.Windows.Controls.ListBox>ilk adı olarak görünür.  
  
 [!code-csharp[CollectionBinding#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hiyerarşik Veriler ile Ana Öğe-Ayrıntı Desenini Kullanma](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)
- [Hiyerarşik XML Verileri ile Ana Öğe-Ayrıntı Desenini Kullanma](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Veri Şablonu Oluşturmaya Genel Bakış](data-templating-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
