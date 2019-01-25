---
title: 'Nasıl yapılır: LINQ Sorgusunun Sonuçlarına Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- running a LINQ query [WPF], bind to results
- binding to LINQ query results [WPF]
ms.assetid: ff2844d9-17ed-4ea6-aab1-5111af0bc684
ms.openlocfilehash: f39715cbfa0fe861f369ab313ac8fad11a347dbe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54583074"
---
# <a name="how-to-bind-to-the-results-of-a-linq-query"></a>Nasıl yapılır: LINQ Sorgusunun Sonuçlarına Bağlama
Bu örnekte, LINQ sorgusu çalıştırın ve ardından sonuçları gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek iki liste kutusu oluşturur. İlk liste kutusu üç liste öğelerini içerir.  
  
 [!code-xaml[LinqExample#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml#ui)]  
  
 İlk liste kutusundan bir öğe seçtiğinizde, aşağıdaki olay işleyicisini çağırır. Bu örnekte, `Tasks` koleksiyonudur `Task` nesneleri. `Task` Sınıfında adlı bir özellik `Priority`. Bu olay işleyicisi koleksiyonunu döndüren LINQ sorgusu çalıştırır `Task` seçili öncelik değerine sahip ve bu ayarlar nesneler <xref:System.Windows.FrameworkElement.DataContext%2A>:  
  
 [!code-csharp[LinqExample#Using](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#using)]  
[!code-csharp[LinqExample#Tasks](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#tasks)]  
[!code-csharp[LinqExample#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#handler)]  
  
 İkinci liste kutusu çünkü bu koleksiyona bağlar, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> değeri ayarı `{Binding}`. Sonuç olarak, döndürülen koleksiyon gösterir (temel `myTaskTemplate` <xref:System.Windows.DataTemplate>).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [XAML'de Bağlama için Veriyi Kullanılabilir Yapma](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)
- [Koleksiyona Bağlama ve Seçime Göre Bilgi Görüntüleme](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [WPF Sürüm 4.5'teki Yenilikler](../../../../docs/framework/wpf/getting-started/whats-new.md)
- [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
