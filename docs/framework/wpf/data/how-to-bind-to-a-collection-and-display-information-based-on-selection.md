---
title: 'Nasıl yapılır: Koleksiyona Bağlama ve Seçime Göre Bilgi Görüntüleme'
description: Bir koleksiyona nasıl bağlanılacağını ve Windows Presentation Foundation (WPF) içindeki seçime göre bilgi görüntülemeyi öğrenmek için bu örneği izleyin.
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
ms.openlocfilehash: fb8757ee6818a2812308a0a132fa9d06951ad52e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619617"
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a>Nasıl yapılır: Koleksiyona Bağlama ve Seçime Göre Bilgi Görüntüleme
Basit bir ana ayrıntı senaryosunda, gibi bir veri bağladınız <xref:System.Windows.Controls.ItemsControl> <xref:System.Windows.Controls.ListBox> . Kullanıcı seçimine bağlı olarak, seçili öğe hakkında daha fazla bilgi görüntülenir. Bu örnek, bu senaryonun nasıl uygulanacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, `People` <xref:System.Collections.ObjectModel.ObservableCollection%601> `Person` sınıflardır. Bu `Person` sınıf üç özellik içerir: `FirstName` , `LastName` , ve `HomeTown` , hepsi türü `string` .  
  
 [!code-xaml[CollectionBinding#Source](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 , <xref:System.Windows.Controls.ContentControl> <xref:System.Windows.DataTemplate> Bir öğesinin bilgisinin nasıl sunulduğunu tanımlayan aşağıdakileri kullanır `Person` :  
  
 [!code-xaml[CollectionBinding#DetailTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 Aşağıda, örneğin ürettiği bir ekran görüntüsü verilmiştir. , <xref:System.Windows.Controls.ContentControl> Seçilen kişinin diğer özelliklerini gösterir.  
  
 ![Koleksiyona bağlama](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")  
  
 Bu örnekte dikkat etmeniz gereken iki şey şunlardır:  
  
1. <xref:System.Windows.Controls.ListBox>Ve <xref:System.Windows.Controls.ContentControl> aynı kaynağa bağlanır. Her iki <xref:System.Windows.Data.Binding.Path%2A> Denetim de tüm koleksiyon nesnesine bağladığından her iki bağlamanın özellikleri belirtilmedi.  
  
2. <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A>Bunun çalışması için özelliği olarak ayarlamanız gerekir `true` . Bu özelliğin ayarlanması, seçilen öğenin her zaman olarak ayarlanmasını sağlar <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A> . Alternatif olarak, <xref:System.Windows.Controls.ListBox> verileri bir öğesinden alırsa, <xref:System.Windows.Data.CollectionViewSource> seçim ve para birimini otomatik olarak eşitler.  
  
 `Person`Sınıfının yöntemi aşağıdaki şekilde geçersiz kıldığını unutmayın `ToString` . Varsayılan olarak, <xref:System.Windows.Controls.ListBox> çağırır `ToString` ve, bağlantılı koleksiyondaki her nesnenin dize gösterimini görüntüler. Bunun nedeni, her birinin `Person` ' de ilk ad olarak görüntülenmesidir <xref:System.Windows.Controls.ListBox> .  
  
 [!code-csharp[CollectionBinding#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hiyerarşik verilerle ana ayrıntı modelini kullanın](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)
- [Hiyerarşik XML verileriyle ana ayrıntı modelini kullanın](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Veri Şablonu Oluşturmaya Genel Bakış](data-templating-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
