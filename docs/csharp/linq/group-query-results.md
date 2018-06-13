---
title: Grup sorgu sonuçları
description: Sonuçları gruplandırmak nasıl.
ms.date: 12/1/2016
ms.assetid: 2e4ec27f-06fb-4de7-8973-0189906d4520
ms.openlocfilehash: cb7808bfdd86dd23882d0722b87b1e013a84141e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33289041"
---
# <a name="group-query-results"></a>Grup sorgu sonuçları

Gruplandırma LINQ en güçlü özelliklerinden biridir. Aşağıdaki örnekler, çeşitli şekillerde verilerin nasıl gruplanacağını gösterir:  
  
-   Tek bir özelliğe göre.  
  
-   Bir dize özelliği ilk harfi ile.  
  
-   Hesaplanan sayısal bir aralık tarafından.  
  
-   Boole koşulu veya diğer ifade.  
  
-   Bileşik bir anahtar.  
  
 Ayrıca, son iki sorgu sonuçları Öğrenci ilk yalnızca içeren ve Soyadı yeni bir anonim tür yansıtın. Daha fazla bilgi için bkz: [group yan tümcesi](../language-reference/keywords/group-clause.md).  
  
## <a name="example"></a>Örnek  
 Bu konudaki tüm örnekleri aşağıdaki yardımcı sınıfları ve veri kaynaklarını kullanın.  
  
 [!code-csharp[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek Grup anahtarı olarak öğesinin tek bir özelliğini kullanarak kaynağı öğeleri gruplandırmak nasıl gösterir. Bu durumda anahtarıdır bir `string`, öğrencinin son adı. Anahtar için bir alt dizesi kullanmak da mümkündür. Gruplama işleminin türü için varsayılan eşitlik karşılaştırıcısını kullanır.  
  
 Aşağıdaki yöntem içine yapıştırma `StudentClass` sınıfı. Arama deyiminde değiştirme `Main` yöntemine `sc.GroupBySingleProperty()`.  
  
 [!code-csharp[csProgGuideLINQ#17](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, nesnenin bir özelliğini dışında bir şey için Grup anahtarı kullanarak kaynağı öğeleri gruplandırmak gösterilmiştir. Bu örnekte, öğrencinin son adının ilk harfi anahtardır.  
  
 Aşağıdaki yöntem içine yapıştırma `StudentClass` sınıfı. Arama deyiminde değiştirme `Main` yöntemine `sc.GroupBySubstring()`.  
  
 [!code-csharp[csProgGuideLINQ#18](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, sayısal bir aralık bir Grup anahtarı kullanarak kaynağı öğeleri gruplandırmak gösterilmiştir. Sorgu sonuçları yalnızca ilk ve son adı ve Öğrenci ait olduğu yüzdebirlik aralığı içeren bir anonim tür sonra projeleri. Anonim bir tür tam kullanmak için gerekli olmadığı için kullanılan `Student` sonuçları görüntülemek için nesne. `GetPercentile` bir yüzde birlik hesaplar yardımcı bir işlev öğrencinin ortalama puanı üzerinde temel alır. Yöntemi, 0 ile 10 arasında bir tamsayı döndürür.  
  
 [!code-csharp[csProgGuideLINQ#50](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]  
  
 Aşağıdaki yöntem içine yapıştırma `StudentClass` sınıfı. Arama deyiminde değiştirme `Main` yöntemine `sc.GroupByRange()`.  
  
 [!code-csharp[csProgGuideLINQ#19](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir Boolean karşılaştırma deyimi kullanarak kaynağı öğeleri gruplandırmak gösterilmiştir. Bu örnekte, öğrencinin ortalama incelemesi puan 75 büyük olup Boole ifadesi sınar. Önceki örneklerde olduğu gibi tam kaynak öğesi gerekli değildir çünkü sonuçları anonim bir tür öngörülen. Anonim tür özelliklerinde üzerinde özellikleri hale Not `Key` üye ve sorgu çalıştırıldığında adıyla erişilebilir.  
  
 Aşağıdaki yöntem içine yapıştırma `StudentClass` sınıfı. Arama deyiminde değiştirme `Main` yöntemine `sc.GroupByBoolean()`.  
  
 [!code-csharp[csProgGuideLINQ#20](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek anonim bir tür birden çok değer içeren bir anahtar kapsüllemek için nasıl kullanılacağını gösterir. Bu örnekte, ilk anahtar öğrencinin son adının ilk harfi değerdir. İkinci anahtar Öğrenci 85 üzerinde ilk incelemesi üzerinde skoru olup olmadığını belirten bir Boole değeri değerdir. Anahtar herhangi bir özellik tarafından grupları sıralayabilirsiniz.  
  
 Aşağıdaki yöntem içine yapıştırma `StudentClass` sınıfı. Arama deyiminde değiştirme `Main` yöntemine `sc.GroupByCompositeKey()`.  
  
 [!code-csharp[csProgGuideLINQ#21](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 <xref:System.Linq.Enumerable.GroupBy%2A>  
 <xref:System.Linq.IGrouping%602>  
 [LINQ Sorgu ifadeleri](index.md)  
 [group yan tümcesi](../language-reference/keywords/group-clause.md)  
 [Anonim Tipler](../programming-guide/classes-and-structs/anonymous-types.md)  
 [Gruplandırma işleminde alt sorgu gerçekleştirme](perform-a-subquery-on-a-grouping-operation.md)  
 [İç içe geçmiş grup oluşturma](create-a-nested-group.md)  
 [Verileri Gruplandırma](../programming-guide/concepts/linq/grouping-data.md)
