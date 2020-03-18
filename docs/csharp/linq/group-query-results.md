---
title: Grup sorgu sonuçları (C#'da LINQ)
description: C#'da LINQ kullanarak sonuçları nasıl gruplatacağız öğrenin.
ms.date: 12/01/2016
ms.assetid: 2e4ec27f-06fb-4de7-8973-0189906d4520
ms.openlocfilehash: 577a358c31fcf5346e7aab7a2e2b6be10fd1beff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61688468"
---
# <a name="group-query-results"></a>Sorgu sonuçlarını gruplandırma

Gruplandırma, LINQ'un en güçlü özelliklerinden biridir. Aşağıdaki örnekler, verilerin çeşitli şekillerde nasıl gruplatını göstereceğimi gösterir:

- Tek bir mülkle.

- Bir dize özelliğinin ilk harfiyle.

- Sayısal olarak hesaplanmış bir aralıkla.

- Boolean edicate veya başka bir ifade ile.

- Bileşik bir anahtarla.

Buna ek olarak, son iki sorgu, sonuçlarını yalnızca öğrencinin adını ve soyadını içeren yeni bir anonim türe yansıttır. Daha fazla bilgi için [grup yan tümcesi'ne](../language-reference/keywords/group-clause.md)bakın.

## <a name="example"></a>Örnek

Bu konudaki tüm örnekleraşağıdaki yardımcı sınıfları ve veri kaynaklarını kullanır.

[!code-csharp[csProgGuideLINQ#15](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, grup anahtarı olarak öğenin tek bir özelliğini kullanarak kaynak öğelerinin nasıl gruplayaalın yapılacağını gösterir. Bu durumda `string`anahtar, öğrencinin soyadıdır. Anahtar için bir alt dize kullanmak da mümkündür. Gruplandırma işlemi türü için varsayılan eşitlik karşılayıcısı kullanır.

Aşağıdaki yöntemi sınıfa `StudentClass` yapıştırın. Yöntemdeki çağrı deyimini `sc.GroupBySingleProperty()`' ' ' olarak değiştirin `Main`

[!code-csharp[csProgGuideLINQ#17](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, grup anahtarı için nesnenin özelliği dışında bir şey kullanarak kaynak öğelerinasıl gruplendirilir gösterir. Bu örnekte anahtar, öğrencinin soyadının ilk harfidir.

Aşağıdaki yöntemi sınıfa `StudentClass` yapıştırın. Yöntemdeki çağrı deyimini `sc.GroupBySubstring()`' ' ' olarak değiştirin `Main`

[!code-csharp[csProgGuideLINQ#18](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]

## <a name="example"></a>Örnek

Aşağıdaki örnekte, grup anahtarı olarak sayısal aralık kullanılarak kaynak öğelerinin nasıl gruplaşılaşı yapılacağını gösterilmektedir. Sorgu daha sonra sonuçları yalnızca ad ve soyad ve öğrencinin ait olduğu yüzdelik aralığını içeren anonim bir türe dönüştürür. Sonuçları görüntülemek için tam `Student` nesneyi kullanmak gerekli olmadığından anonim bir tür kullanılır. `GetPercentile`öğrencinin ortalama puanına göre yüzdelik bir artış hesaplayan bir yardımcı işlevdir. Yöntem 0 ile 10 arasında bir arayla bir sonda döndürür.

[!code-csharp[csProgGuideLINQ#50](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]

Aşağıdaki yöntemi sınıfa `StudentClass` yapıştırın. Yöntemdeki çağrı deyimini `sc.GroupByRange()`' ' ' olarak değiştirin `Main`

[!code-csharp[csProgGuideLINQ#19](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, boolean karşılaştırma ifadesini kullanarak kaynak öğelerinin nasıl gruplandırılabildiğini gösterir. Bu örnekte, Boolean ifadesi bir öğrencinin ortalama sınav puanının 75'ten fazla olup olmadığını test eder. Önceki örneklerde olduğu gibi, tam kaynak öğesi gerekli olmadığından sonuçlar anonim bir türe yansıtılır. Anonim türdeki özelliklerin `Key` üyeüzerinde özellik haline geldiğini ve sorgu yürütüldüğünde adıyla erişilenebileni unutmayın.

Aşağıdaki yöntemi sınıfa `StudentClass` yapıştırın. Yöntemdeki çağrı deyimini `sc.GroupByBoolean()`' ' ' olarak değiştirin `Main`

[!code-csharp[csProgGuideLINQ#20](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, birden çok değer içeren bir anahtarı kapsüllemek için anonim bir türün nasıl kullanılacağını gösterir. Bu örnekte, ilk anahtar değeri öğrencinin soyadının ilk harfidir. İkinci anahtar değer, öğrencinin ilk sınavda 85 üzerinden puan alıp almadığına dair bir Boolean'dır. Gruplara anahtardaki herhangi bir özelliğe göre sipariş verebilirsiniz.

Aşağıdaki yöntemi sınıfa `StudentClass` yapıştırın. Yöntemdeki çağrı deyimini `sc.GroupByCompositeKey()`' ' ' olarak değiştirin `Main`

[!code-csharp[csProgGuideLINQ#21](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.Enumerable.GroupBy%2A>
- <xref:System.Linq.IGrouping%602>
- [Dil ile Tümleşik Sorgu (LINQ)](index.md)
- [group yan tümcesi](../language-reference/keywords/group-clause.md)
- [Anonim Türler](../programming-guide/classes-and-structs/anonymous-types.md)
- [Gruplandırma İşleminde Alt Sorgu Yap](perform-a-subquery-on-a-grouping-operation.md)
- [İç Içe Grup Oluşturma](create-a-nested-group.md)
- [Verileri Gruplandırma](../programming-guide/concepts/linq/grouping-data.md)
