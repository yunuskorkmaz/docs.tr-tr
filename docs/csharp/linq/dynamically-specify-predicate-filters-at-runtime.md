---
title: (C# üzerinde LINQ) çalışma zamanında koşul filtrelerini dinamik olarak belirtme
description: C# içinde LINQ kullanarak çalışma zamanında koşul filtrelerini dinamik olarak belirtme hakkında bilgi edinin.
ms.date: 12/1/2016
ms.assetid: 90238470-0767-497c-916c-52d0d16845e0
ms.openlocfilehash: 7051d7c754a0db29771a2e03a3b624c0e434eecd
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404096"
---
# <a name="dynamically-specify-predicate-filters-at-runtime"></a>Çalışma zamanında koşul filtrelerini dinamik olarak belirtme

Bazı durumlarda, doğrulamaları kaç kaynak öğeleri uygulamak sahip olduğunuz çalışma zamanına kadar bilmiyorum `where` yan tümcesi. Birden çok koşul filtrelerini dinamik olarak belirtmek için tek bir yolu <xref:System.Linq.Enumerable.Contains%2A> yöntemi, aşağıdaki örnekte gösterildiği gibi. Örneğin, iki şekilde oluşturulur. İlk olarak, projeyi programda sağlanan değerleri filtreleyerek çalıştırılır. Ardından projeyi yeniden çalışma zamanında sağlanan giriş kullanılarak çalıştırılır.

## <a name="to-filter-by-using-the-contains-method"></a>Contains yöntemi kullanarak filtre uygulamak için

1. Yeni bir konsol uygulaması'nı açın ve adlandırın `PredicateFilters`.

2. Kopyalama `StudentClass` gelen sınıfı [nesneler koleksiyonunu sorgulama](query-a-collection-of-objects.md) ve ad alanına yapıştırın `PredicateFilters` sınıfı altında `Program`. `StudentClass` bir listesini sağlar `Student` nesneleri.

3. Açıklama `Main` yönteminde `StudentClass`.

4. Sınıf değiştirin `Program` aşağıdaki kod ile:

     [!code-csharp[csProgGuideLINQ#26](~/samples/snippets/csharp/concepts/linq/how-to-dynamically-specify-predicate-filters-at-runtime_1.cs)]

5. Aşağıdaki satırı ekleyin `Main` sınıfındaki yöntemi `DynamicPredicates`, bildirimi altında `ids`.

     ```csharp
     QueryById(ids);
     ```

6. Projeyi çalıştırın.

7. Aşağıdaki çıktıyı konsol penceresinde görüntülenir:

     Garcia: 114

     O'Donnell: 112

     Omelchenko: 111

8. Sonraki adımda projeyi yeniden çalıştırmak için çalışma zamanında dizi yerine Giriş kullanarak bu saati girildi. `ids`. Değişiklik `QueryByID(ids)` için `QueryByID(args)` içinde `Main` yöntemi.

9. Komut satırı bağımsız değişkenleri ile projeyi Çalıştır `122 117 120 115`. Projeyi çalıştırdığınızda, bu değerleri öğelerini haline `args`, parametresi `Main` yöntemi...

10. Aşağıdaki çıktıyı konsol penceresinde görüntülenir:

     Adams: 120

     Feng: 117

     Garcia: 115

     Tucker: 122

## <a name="to-filter-by-using-a-switch-statement"></a>Switch deyimi kullanarak filtre uygulamak için

1. Kullanabileceğiniz bir `switch` arasından seçim yapmak deyimi önceden alternatif sorgular. Aşağıdaki örnekte, `studentQuery` farklı bir kullanan `where` bağlı olarak hangi sınıf düzeyinde veya yıl, belirtilen çalışma zamanında yan tümcesi.

2. Aşağıdaki yöntemi kopyalayın ve sınıfına yapıştırın `DynamicPredicates`.

     [!code-csharp[csProgGuideLINQ#27](~/samples/snippets/csharp/concepts/linq//how-to-dynamically-specify-predicate-filters-at-runtime_2.cs)]

3. İçinde `Main` yöntemi çağrısını `QueryByID` aşağıdaki çağrısıyla, gönderdiği ilk öğenin `args` kendi bağımsız değişkeni olarak bir dizi: `QueryByYear(args[0])`.

4. Projeyi, 1 ile 4 arasında bir tamsayı değeri bir komut satırı bağımsız değişkeni ile çalıştırın.

## <a name="see-also"></a>Ayrıca bkz.

[Dil ile Tümleşik Sorgu (LINQ)](index.md)  
[where yan tümcesi](../language-reference/keywords/where-clause.md)  