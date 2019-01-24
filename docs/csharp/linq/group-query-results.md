---
title: Sorgu sonuçlarını gruplandırma (C# üzerinde LINQ)
description: Grup C# içinde LINQ kullanarak sonuçları öğrenin.
ms.date: 12/1/2016
ms.assetid: 2e4ec27f-06fb-4de7-8973-0189906d4520
ms.openlocfilehash: 42f2a483f4ff9a405152250e3961fd267861b20d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54606802"
---
# <a name="group-query-results"></a>Sorgu sonuçlarını gruplandırma

Gruplandırma LINQ en güçlü özelliklerinden biridir. Aşağıdaki örnekler, çeşitli yollarla verilerin nasıl gruplanacağını gösterir:

- Tek bir özelliğe göre.

- Bir dize özelliği ilk harfi ile.

- Tarafından hesaplanan bir sayısal aralık.

- Boole koşulu veya diğer ifade.

- Bileşik bir anahtar.

Ayrıca, son iki sorguların sonuçlarını Öğrenci ilk yalnızca içeriyor ve Soyadı yeni bir anonim tür proje. Daha fazla bilgi için [group yan tümcesi](../language-reference/keywords/group-clause.md).

## <a name="example"></a>Örnek

Bu konunun tüm örnekleri aşağıdaki yardımcı sınıflar ve veri kaynaklarını kullanın.

[!code-csharp[csProgGuideLINQ#15](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, tek bir özellik öğesinin Grup anahtarı kullanarak kaynak öğeleri gruplandırmak gösterilmektedir. Bu durumda bu anahtar, bir `string`, öğrencinin soyadı. Anahtar için bir alt dizesi kullanmak da mümkündür. Gruplandırma işlemi türü için varsayılan eşitlik karşılaştırıcısını kullanır.

Aşağıdaki yönteme yapıştırın `StudentClass` sınıfı. Arama deyiminde değiştirme `Main` yönteme `sc.GroupBySingleProperty()`.

[!code-csharp[csProgGuideLINQ#17](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, nesnenin bir özelliğini dışında bir şey için Grup anahtarı kullanarak kaynak öğeleri gruplandırmak gösterilmektedir. Bu örnekte, öğrencinin son adının ilk harfi bir anahtardır.

Aşağıdaki yönteme yapıştırın `StudentClass` sınıfı. Arama deyiminde değiştirme `Main` yönteme `sc.GroupBySubstring()`.

[!code-csharp[csProgGuideLINQ#18](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, sayısal aralık bir Grup anahtarı kullanarak kaynak öğeleri gruplandırmak gösterilmektedir. Sorgu sonuçları yalnızca ilk ve son adı ve Öğrenci ait olduğu yüzdebirlik aralığı içeren bir anonim tür ardından yansıtıyor. Anonim bir tür, tam olarak kullanmak için gerekli olmadığından kullanılan `Student` sonuçları görüntülemek için nesne. `GetPercentile` yüzde hesaplayan bir yardımcı işlevi, öğrencinin ortalama puanına göre temel alır. Yöntemi, 0 ile 10 arasında bir tamsayı döndürür.

[!code-csharp[csProgGuideLINQ#50](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]

Aşağıdaki yönteme yapıştırın `StudentClass` sınıfı. Arama deyiminde değiştirme `Main` yönteme `sc.GroupByRange()`.

[!code-csharp[csProgGuideLINQ#19](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir Boolean karşılaştırma ifadesi kullanarak kaynak öğeleri gruplandırmak gösterilmektedir. Bu örnekte, bir öğrencinin ortalama sınavı puanı 75 büyük olup Boole ifadesi test eder. Önceki örneklerde olduğu gibi tam kaynak öğesi gerekli değildir çünkü sonuçları anonim bir tür yansıtılan. Anonim tür özellikleri Özellikler üzerinde hale geleceğini unutmayın `Key` üyesi ve sorgu yürütüldüğünde adı tarafından erişilebilir.

Aşağıdaki yönteme yapıştırın `StudentClass` sınıfı. Arama deyiminde değiştirme `Main` yönteme `sc.GroupByBoolean()`.

[!code-csharp[csProgGuideLINQ#20](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, birden çok değer içeren bir anahtar yalıtılacak anonim bir tür kullanmayı gösterir. Bu örnekte, ilk anahtar değeri öğrencinin Soyadı İlk harfidir. İkinci anahtar değeri Öğrenci 85 üzerinde ilk sınavı üzerinde puanlanmış olup olmadığını belirten Boolean bir değer var. Grupları anahtarında herhangi bir özelliğe göre sıralayabilirsiniz.

Aşağıdaki yönteme yapıştırın `StudentClass` sınıfı. Arama deyiminde değiştirme `Main` yönteme `sc.GroupByCompositeKey()`.

[!code-csharp[csProgGuideLINQ#21](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.Enumerable.GroupBy%2A>
- <xref:System.Linq.IGrouping%602>
- [Dil ile Tümleşik Sorgu (LINQ)](index.md)
- [group yan tümcesi](../language-reference/keywords/group-clause.md)
- [Anonim Tipler](../programming-guide/classes-and-structs/anonymous-types.md)
- [Gruplandırma işleminde alt sorgu gerçekleştirme](perform-a-subquery-on-a-grouping-operation.md)
- [İç içe geçmiş grup oluşturma](create-a-nested-group.md)
- [Verileri Gruplandırma](../programming-guide/concepts/linq/grouping-data.md)
