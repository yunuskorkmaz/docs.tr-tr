---
title: "Nasıl yapılır: LINQ Sorgusunun Sonuçlarına Bağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- running a LINQ query [WPF], bind to results
- binding to LINQ query results [WPF]
ms.assetid: ff2844d9-17ed-4ea6-aab1-5111af0bc684
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e77a0c698dae0330877c54422c15e14c82376891
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-to-the-results-of-a-linq-query"></a>Nasıl yapılır: LINQ Sorgusunun Sonuçlarına Bağlama
Bu örnek, bir LINQ Sorgu çalıştırmak ve sonuçları bağlamak gösterilmiştir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki liste kutusu oluşturur. İlk liste kutusu üç liste öğelerini içerir.  
  
 [!code-xaml[LinqExample#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml#ui)]  
  
 Bir öğenin ilk liste kutusundan seçilmesi, aşağıdaki olay işleyiciyi çağırır. Bu örnekte, `Tasks` koleksiyonudur `Task` nesneleri. `Task` Sınıfı adlı bir özelliğe sahiptir `Priority`. Bu olay işleyicisi koleksiyonu döndüren LINQ sorgusu çalıştırır `Task` , seçili öncelik değerine sahip ve aynı ayarlar nesneleri <xref:System.Windows.FrameworkElement.DataContext%2A>:  
  
 [!code-csharp[LinqExample#Using](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#using)]  
[!code-csharp[LinqExample#Tasks](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#tasks)]  
[!code-csharp[LinqExample#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#handler)]  
  
 İkinci liste kutusunu o koleksiyona bağlar çünkü kendi <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> değeri ayarı `{Binding}`. Sonuç olarak döndürülen koleksiyon gösterilir (temel `myTaskTemplate` <xref:System.Windows.DataTemplate>).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Verileri XAML'de bağlama için kullanılabilir yap](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)  
 [Seçim temelinde bilgi görüntüleme ve koleksiyonuna bağlama](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)  
 [WPF sürüm 4.5 yenilikler nelerdir?](../../../../docs/framework/wpf/getting-started/whats-new.md)  
 [Veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
