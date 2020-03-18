---
title: Çalışma zamanında yüklem filtrelerini dinamik olarak belirtin (C#'da LINQ)
description: C#'da LINQ kullanarak çalışma zamanında yüklem filtrelerini dinamik olarak nasıl belirtebilirsiniz öğrenin.
ms.date: 12/01/2016
ms.assetid: 90238470-0767-497c-916c-52d0d16845e0
ms.openlocfilehash: 314be8f98b9ff014f14bef11a1f3581eff8574b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659949"
---
# <a name="dynamically-specify-predicate-filters-at-runtime"></a>Çalışma zamanında koşul filtrelerini dinamik olarak belirtme

Bazı durumlarda, `where` çalışma süresine kadar yan tümcedeki kaynak öğelere kaç yüklem uygulamanız gerektiğini bilemezsin. Birden çok yüklem filtresini dinamik olarak belirtmenin <xref:System.Linq.Enumerable.Contains%2A> bir yolu, aşağıdaki örnekte gösterildiği gibi yöntemi kullanmaktır. Örnek iki şekilde oluşturulmuştur. İlk olarak, proje programda sağlanan değerlere filtre uygulanarak çalıştırılır. Daha sonra proje, çalışma zamanında sağlanan giriş kullanılarak yeniden çalıştırılır.

## <a name="to-filter-by-using-the-contains-method"></a>İçle yöntemini kullanarak filtrelemek için

1. Yeni bir konsol uygulaması `PredicateFilters`açın ve adlandırın.

2. Sınıfı `StudentClass` Sorgula'dan [nesnelerin bir koleksiyonunu](query-a-collection-of-objects.md) kopyalayın ve `PredicateFilters` sınıfın `Program`altındaki ad alanına yapıştırın. `StudentClass``Student` nesnelerin bir listesini sağlar.

3. Yöntemi ' `Main` de `StudentClass`yorumla.

4. Sınıfı `Program` aşağıdaki kodla değiştirin:

     [!code-csharp[csProgGuideLINQ#26](~/samples/snippets/csharp/concepts/linq/how-to-dynamically-specify-predicate-filters-at-runtime_1.cs)]

5. Sınıftaki `Main` `DynamicPredicates`yönteme aşağıdaki satırı ekleyin, `ids`.

     ```csharp
     QueryById(ids);
     ```

6. Projeyi çalıştırın.

7. Aşağıdaki çıktı konsol penceresinde görüntülenir:

     Garcia: 114

     O'Donnell: 112

     Omelchenko: 111

8. Bir sonraki adım, bu kez dizi `ids`yerine çalışma zamanında girilen girişi kullanarak projeyi yeniden çalıştırmaktır. Yöntemde değiştirin. `Main` `QueryByID(ids)` `QueryByID(args)`

9. Komut satırı bağımsız değişkenleriyle `122 117 120 115`projeyi çalıştırın. Proje çalıştırıldığında, bu değerler `args` `Main` yöntemin parametresi olan öğeler haline gelir.

10. Aşağıdaki çıktı konsol penceresinde görüntülenir:

     Adam sayısı: 120

     Feng: 117

     Garcia: 115

     Tucker: 122

## <a name="to-filter-by-using-a-switch-statement"></a>Anahtar deyimi kullanarak filtre lemek için

1. Önceden belirlenmiş `switch` alternatif sorgular arasından seçim yapmak için bir deyim kullanabilirsiniz. Aşağıdaki örnekte, `studentQuery` çalışma `where` zamanında hangi sınıf düzeyine veya yıla bağlı olarak farklı bir tümce kullanır.

2. Aşağıdaki yöntemi kopyalayın ve sınıfa `DynamicPredicates`yapıştırın.

     [!code-csharp[csProgGuideLINQ#27](~/samples/snippets/csharp/concepts/linq//how-to-dynamically-specify-predicate-filters-at-runtime_2.cs)]

3. `Main` Yöntemde, çağrıyı `QueryByID` aşağıdaki çağrıyla değiştirin, bu da `args` diziden ilk `QueryByYear(args[0])`öğeyi bağımsız değişken olarak gönderir: .

4. Projeyi, 1 ile 4 arasında bir tamsayı değerinin komut satırı bağımsız değişkeniyle çalıştırın.

## <a name="see-also"></a>Ayrıca bkz.

- [Dil ile Tümleşik Sorgu (LINQ)](index.md)
- [where tümcesi](../language-reference/keywords/where-clause.md)
