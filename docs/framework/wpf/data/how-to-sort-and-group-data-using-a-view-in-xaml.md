---
title: 'Nasıl yapılır: XAML İçerisinde bir Görüntü Kullanarak Verileri Sıralama ve Gruplandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], grouping data in views in XAML
- XAML [WPF], sorting data in views
- grouping data in views in XAML [WPF]
- data binding [WPF], sorting data in views in XAML
- sorting data in views in XAML [WPF]
- XAML [WPF], grouping data in views
- views [WPF], sorting data
- views [WPF], grouping data
ms.assetid: 145c8c3f-dbdd-4d0d-816f-90b35eba7eda
ms.openlocfilehash: 80529420bcc5fdca473313e164b3d096732953f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a>Nasıl yapılır: XAML İçerisinde bir Görüntü Kullanarak Verileri Sıralama ve Gruplandırma
Bu örnek, bir veri toplama bir görünümün nasıl oluşturulacağını gösterir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Görünümler gruplandırma, sıralama, filtreleme işlevler ve güncel bir öğenin kavramı izin verir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, statik kaynak adlı *yerleştirir* koleksiyonu olarak tanımlanır *yer* her nesneleri *yer* nesne şehir adını içermektedir ve durumu. Önek *src* ad alanına eşlenen burada veri kaynağı *yerler* tanımlanır. Önek *scm* eşlendiği `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` ve *verilerinin* eşlendiği `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.  
  
 Aşağıdaki örnek Şehir adına göre sıralanır ve duruma göre gruplandırılmış veri koleksiyonunun bir görünüm oluşturur.  
  
 [!code-xaml[CollectionViewSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 Görünüm sonra aşağıdaki örnekteki gibi bir bağlama kaynağı olabilir:  
  
 [!code-xaml[CollectionViewSource#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 Bağlamaları tanımlanan XML veri için bir <xref:System.Windows.Data.XmlDataProvider> kaynak XML adından bir @ simgesinden.  
  
 [!code-xaml[CollectionViewSource#XDPChunk](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Data.CollectionViewSource>  
 [Veri Koleksiyonunun Varsayılan Görünümünü Alma](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md)  
 [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
