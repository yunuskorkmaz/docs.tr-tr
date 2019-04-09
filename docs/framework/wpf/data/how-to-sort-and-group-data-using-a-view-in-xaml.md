---
title: 'Nasıl yapılır: XAML İçerisinde bir Görüntü Kullanarak Verileri Sıralama ve Gruplama'
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
ms.openlocfilehash: ca4439b574264ebebfda745f0765f750099bc95f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59144527"
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a>Nasıl yapılır: XAML İçerisinde bir Görüntü Kullanarak Verileri Sıralama ve Gruplama
Bu örnek, bir veri toplama bir görünümün nasıl oluşturulacağını gösterir. [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Görünümler işlevleri gruplandırma, sıralama, filtreleme ve geçerli öğenin kavram izin verir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte adlı statik kaynak *yerleştirir* koleksiyonu olarak tanımlanır *yerde* nesneleri, her *yerde* nesne bir şehir adı toplamda ve durumu. Önek *src* ad alanına eşlenen burada veri kaynağı *yerler* tanımlanır. Önek *scm* eşlendiği `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` ve *dat* eşlendiği `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.  
  
 Aşağıdaki örnek Şehir adına göre sıralanır ve durumlarına göre gruplandırılan veri koleksiyonunu bir görünümünü oluşturur.  
  
 [!code-xaml[CollectionViewSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 Görünüm, ardından aşağıdaki örnekteki gibi bir bağlama kaynağı olabilir:  
  
 [!code-xaml[CollectionViewSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 Tanımlanan XML veri bağlama için bir <xref:System.Windows.Data.XmlDataProvider> kaynak ile XML adın önüne bir @ sembolü.  
  
 [!code-xaml[CollectionViewSource#XDPChunk](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Data.CollectionViewSource>
- [Veri Koleksiyonunun Varsayılan Görünümünü Alma](how-to-get-the-default-view-of-a-data-collection.md)
- [Veri Bağlamaya Genel Bakış](data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
