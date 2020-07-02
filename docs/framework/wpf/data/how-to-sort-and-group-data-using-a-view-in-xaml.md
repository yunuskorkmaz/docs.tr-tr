---
title: 'Nasıl yapılır: XAML İçerisinde bir Görüntü Kullanarak Verileri Sıralama ve Gruplandırma'
description: Windows Presentation Foundation (WPF) içinde gruplandırma, sıralama ve filtreleme için bir veri koleksiyonunun görünümünü oluşturmayı öğrenin.
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
ms.openlocfilehash: a4f8e2de9345dba8e4ea0d3a16a32d57a9adb55c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621684"
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a>Nasıl yapılır: XAML İçerisinde bir Görüntü Kullanarak Verileri Sıralama ve Gruplandırma
Bu örnek, ' de bir veri koleksiyonunun bir görünümünün nasıl oluşturulacağını gösterir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] . Görünümler gruplandırma, sıralama, filtreleme ve geçerli bir öğenin kavramının işlevlerini sağlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, *yerleri* adlı statik kaynak, her bir *Yerleştir* nesnesinin bir şehir adı ve eyalet olarak oluşturulduğu bir *Yerleştir* nesneleri koleksiyonu olarak tanımlanmıştır. *Src* ön eki, veri kaynağı *yerlerinin* tanımlandığı ad alanı ile eşleştirilir. *SCM* öneki `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` ile ve *dat* Maps ile eşlenir `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"` .  
  
 Aşağıdaki örnek, şehir adına göre sıralanmış ve duruma göre gruplandırılan veri koleksiyonunun bir görünümünü oluşturur.  
  
 [!code-xaml[CollectionViewSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 Görünüm daha sonra aşağıdaki örnekte olduğu gibi bir bağlama kaynağı olabilir:  
  
 [!code-xaml[CollectionViewSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 Bir kaynakta tanımlanan XML verilerine bağlamalar için <xref:System.Windows.Data.XmlDataProvider> , XML adından önce bir @ simgesiyle önüne geçin.  
  
 [!code-xaml[CollectionViewSource#XDPChunk](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Data.CollectionViewSource>
- [Veri koleksiyonunun varsayılan görünümünü al](how-to-get-the-default-view-of-a-data-collection.md)
- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
