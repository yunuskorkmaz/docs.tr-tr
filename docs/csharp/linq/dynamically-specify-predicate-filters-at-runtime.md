---
title: "Çalışma zamanında koşul filtrelerini dinamik olarak belirtme"
description: "Çalışma zamanında koşul filtrelerini dinamik olarak belirleme konusunda."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 90238470-0767-497c-916c-52d0d16845e0
ms.openlocfilehash: 06bc594ac1357e7dca6c182fa28310559a79875c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="dynamically-specify-predicate-filters-at-runtime"></a>Çalışma zamanında koşul filtrelerini dinamik olarak belirtme

Bazı durumlarda, çalışma zamanına kadar sahip kaynak öğelerine uygulamak kaç tane doğrulamaları bilmiyorsanız `where` yan tümcesi. Birden çok koşul filtrelerini dinamik olarak belirtmek için bir yol kullanmaktır <xref:System.Linq.Enumerable.Contains%2A> aşağıdaki örnekte gösterildiği gibi yöntemi. Örneğin, iki şekilde oluşturulur. İlk olarak, projeyi programa sağlanan değerleri üzerinde filtreleme yaparak çalıştırılır. Daha sonra projeyi yeniden çalışma zamanında sağlanan giriş kullanarak çalıştırılır.  
  
## <a name="to-filter-by-using-the-contains-method"></a>Contains yöntemi kullanarak filtre uygulamak için  
  
1.  Yeni bir konsol uygulaması açın ve adını `PredicateFilters`.  
  
2.  Kopya `StudentClass` sınıfıyla [nesneler koleksiyonunu sorgulama](query-a-collection-of-objects.md) ve ad alanına yapıştırın `PredicateFilters` sınıfı altında `Program`. `StudentClass`bir listesini sağlar `Student` nesneleri.  
  
3.  Out açıklama `Main` yönteminde `StudentClass`.  
  
4.  Sınıf Değiştir `Program` aşağıdaki kod ile.  
  
     [!code-csharp[csProgGuideLINQ#26](../../../samples/snippets/csharp/concepts/linq/how-to-dynamically-specify-predicate-filters-at-runtime_1.cs)]  
  
5.  Aşağıdaki satırı ekleyin `Main` sınıfında yöntemi `DynamicPredicates`, bildirimi altında `ids`.  
  
     ```csharp
     QueryById(ids);
     ```

6.  Projeyi çalıştırın.  
  
7.  Aşağıdaki çıkış konsol penceresinde görüntülenir:  
  
     Garcia: 114  
  
     O'Donnell: 112  
  
     Omelchenko: 111  
  
8.  Sonraki adım projeyi yeniden çalıştırmak için dizi yerine çalışma zamanında giriş kullanarak bu saati girildi. `ids`. Değişiklik `QueryByID(ids)` için `QueryByID(args)` içinde `Main` yöntemi.  
  
9. Komut satırı bağımsız değişkenleri ile projeyi çalıştırın `122 117 120 115`. Projeyi çalıştırdığınızda bu değerleri öğeleri hale `args`, parametresinin `Main` yöntemi...  
  
10. Aşağıdaki çıkış konsol penceresinde görüntülenir:  
  
     Adams: 120  
  
     Feng: 117  
  
     Garcia: 115  
  
     Tucker: 122  
  
## <a name="to-filter-by-using-a-switch-statement"></a>Switch deyimi kullanarak filtre uygulamak için  
  
1.  Kullanabileceğiniz bir `switch` arasından seçim yapmak deyimi önceden alternatif sorgular. Aşağıdaki örnekte, `studentQuery` farklı bir kullanan `where` bağlı olarak hangi düzeyde düzeyini yılı, belirtilmişse, veya çalışma zamanında yan tümcesi.  
  
2.  Aşağıdaki yöntem kopyalayın ve sınıfına yapıştırın `DynamicPredicates`.  
  
     [!code-csharp[csProgGuideLINQ#27](../../../samples/snippets/csharp/concepts/linq//how-to-dynamically-specify-predicate-filters-at-runtime_2.cs)]  
  
3.  İçinde `Main` yöntemi çağrısı Değiştir `QueryByID` aşağıdaki çağrısı ile gönderdiği ilk öğeden `args` bağımsız değişkeni olarak bir dizi: `QueryByYear(args[0])`.  
  
4.  Proje, 1 ile 4 arasında bir tamsayı değeri bir komut satırı bağımsız değişkeni ile çalıştırın.  
  
 
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ Sorgu ifadeleri](index.md)  
 [Burada yan tümcesi](../language-reference/keywords/where-clause.md)
