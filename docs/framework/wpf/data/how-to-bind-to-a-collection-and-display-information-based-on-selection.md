---
title: "Nasıl yapılır: Koleksiyona Bağlama ve Seçime Göre Bilgi Görüntüleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data collections [WPF], selecting data for views
- data binding [WPF], creating views of data collections
- data binding [WPF], selecting data for views
- data binding [WPF], binding to collections
ms.assetid: 952a7d76-dd29-49e5-86f5-32c4530e70eb
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a751025470b566ef1e735e4ddd192cfd8fc354ad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a>Nasıl yapılır: Koleksiyona Bağlama ve Seçime Göre Bilgi Görüntüleme
Verilere bağlı olan bir basit ana-ayrıntı senaryosunda <xref:System.Windows.Controls.ItemsControl> gibi bir <xref:System.Windows.Controls.ListBox>. Kullanıcı seçimi temel alınarak, seçili öğe hakkında daha fazla bilgi görüntüleyin. Bu örnek, bu senaryonun nasıl uygulanacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, `People` olan bir <xref:System.Collections.ObjectModel.ObservableCollection%601> , `Person` sınıfları. Bu `Person` sınıfı üç özellik içerir: `FirstName`, `LastName`, ve `HomeTown`, tüm türü `string`.  
  
 [!code-xaml[CollectionBinding#Source](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <xref:System.Windows.Controls.ContentControl> Aşağıdaki kullanan <xref:System.Windows.DataTemplate> tanımlayan nasıl bilgilerinin bir `Person` sunulur:  
  
 [!code-xaml[CollectionBinding#DetailTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 Örneğin ürettiği, bir ekran görüntüsü verilmiştir. <xref:System.Windows.Controls.ContentControl> Seçilen kişinin diğer özelliklerini gösterir.  
  
 ![Bir koleksiyona bağlama](../../../../docs/framework/wpf/data/media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")  
  
 Bu örnekte fark için iki şey vardır:  
  
1.  <xref:System.Windows.Controls.ListBox> Ve <xref:System.Windows.Controls.ContentControl> aynı kaynağa bağlanır. <xref:System.Windows.Data.Binding.Path%2A> Özellikleri belirtilmemiştir çünkü her iki denetimleri tüm koleksiyon nesnesine bağlama belirtilmedi.  
  
2.  Ayarlamalısınız <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> özelliğine `true` Bunun çalışması. Bu özelliği ayarlamak sağlar Seçili öğe olarak her zaman ayarlanır <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>. Alternatif olarak, varsa <xref:System.Windows.Controls.ListBox> verilerinden alır bir <xref:System.Windows.Data.CollectionViewSource>, seçimi ve para birimi otomatik olarak eşitler.  
  
 Unutmayın `Person` geçersiz kılmaları sınıf `ToString` yöntemini aşağıdaki şekilde. Varsayılan olarak, <xref:System.Windows.Controls.ListBox> çağrıları `ToString` ve ilişkili koleksiyonunda her nesnenin dize gösterimini görüntüler. İşte bu nedenle her `Person` ilk adı olarak görünür <xref:System.Windows.Controls.ListBox>.  
  
 [!code-csharp[CollectionBinding#ToString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hiyerarşik Veriler ile Ana Öğe-Ayrıntı Desenini Kullanma](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)  
 [Hiyerarşik XML Verileri ile Ana Öğe-Ayrıntı Desenini Kullanma](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)  
 [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Veri Şablonu Oluşturmaya Genel Bakış](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
