---
title: 'Nasıl yapılır: LINQ Sorgusunun Sonuçlarına Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- running a LINQ query [WPF], bind to results
- binding to LINQ query results [WPF]
ms.assetid: ff2844d9-17ed-4ea6-aab1-5111af0bc684
ms.openlocfilehash: 70f4b439d231d69e5671216bc4e62d0789ce66c7
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920131"
---
# <a name="how-to-bind-to-the-results-of-a-linq-query"></a>Nasıl yapılır: LINQ Sorgusunun Sonuçlarına Bağlama

Bu örnek, bir LINQ sorgusunun nasıl çalıştırılacağını ve sonra sonuçlara nasıl bağlanacağını gösterir.

## <a name="example"></a>Örnek

Aşağıdaki örnek iki liste kutusu oluşturur. İlk liste kutusu üç liste öğesi içerir.

[!code-xaml[LinqExample#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml#ui)]

İlk liste kutusundan bir öğe seçilmesi aşağıdaki olay işleyicisini çağırır. Bu örnekte, `Tasks` bir `Task` nesneleri koleksiyonudur. `Task` sınıfı `Priority`adında bir özelliğe sahiptir. Bu olay işleyicisi, Seçili öncelik değerine sahip `Task` nesnelerinin koleksiyonunu döndüren bir LINQ sorgusu çalıştırır ve ardından bunu <xref:System.Windows.FrameworkElement.DataContext%2A>olarak ayarlar:

[!code-csharp[LinqExample#Using](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#using)]
[!code-csharp[LinqExample#Tasks](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#tasks)]
[!code-csharp[LinqExample#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#handler)]

İkinci liste kutusu bu koleksiyona bağlanır çünkü <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> değeri `{Binding}`olarak ayarlanmıştır. Sonuç olarak, döndürülen koleksiyonu (`myTaskTemplate` <xref:System.Windows.DataTemplate>göre) görüntüler.

## <a name="see-also"></a>Ayrıca bkz.

- [XAML'de Bağlama için Veriyi Kullanılabilir Yapma](how-to-make-data-available-for-binding-in-xaml.md)
- [Koleksiyona Bağlama ve Seçime Göre Bilgi Görüntüleme](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [WPF Sürüm 4.5'teki Yenilikler](../getting-started/whats-new.md)
- [Veri Bağlamaya Genel Bakış](data-binding-overview.md)
