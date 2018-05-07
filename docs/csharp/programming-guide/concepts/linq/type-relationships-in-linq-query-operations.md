---
title: LINQ Sorgu İşlemlerinde Tür İlişkileri (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- inferring type information [LINQ in C#]
- data sources [LINQ in C#], type relationships
- queries [LINQ in C#], type relationships
- relationships [LINQ in C#]
- type relationships [LINQ in C#]
- variable relationships [LINQ in C#]
- type information inferred [LINQ in C#]
- data transformations [LINQ in C#]
- LINQ [C#], type relationships
ms.assetid: 99118938-d47c-4d7e-bb22-2657a9f95268
ms.openlocfilehash: 274c5eaee2b4bf0e1331fb7a4a1a89a432a567c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="type-relationships-in-linq-query-operations-c"></a>LINQ Sorgu İşlemlerinde Tür İlişkileri (C#)
Sorguları etkili bir şekilde yazmak için tam bir sorgu işlemi tüm değişken türleri, birbirleriyle nasıl ilişkili olduğunu anlamanız gerekir. Bu ilişkileri anlarsanız, daha kolay kavrama [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] belgelerinde örnekleri ve kod. Ayrıca, değişkenleri kullanarak örtük olarak yazılan ne olacağı arka planda anlayabileceği `var`.  
  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu işlemleri, veri kaynağı, sorgu ve sorgu yürütmesi kesin türü belirtilmiş. Sorgu değişkenleri türünde veri kaynağındaki öğelerin türü ve yineleme değişkenin türü ile uyumlu olmalıdır `foreach` deyimi. Bu güçlü yazarak türü hataları kullanıcılar bunları karşılaşmadan önce zaman bunlar düzeltilebilir derleme zamanında yakalanır güvence altına alır.  
  
 Bu tür ilişkileri göstermek için açık tüm değişkenleri yazarak izleyin örnekler çoğunu kullanın. Son örnek bile kullanarak örtük yazarak kullandığınızda, aynı ilkeleri nasıl uygulandığını gösterir [var](../../../../csharp/language-reference/keywords/var.md).  
  
## <a name="queries-that-do-not-transform-the-source-data"></a>Veri kaynağını dönüştürülmez sorguları  
 Aşağıdaki çizimde gösterildiği bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] nesnelere sorgu verileri hiçbir dönüşümleri gerçekleştirir işlemi. Kaynak dizeleri dizisi içerir ve sorgu çıktısı da dizeleri dizisidir.  
  
 ![İlişki veri türleri bir LINQ Sorgu](../../../../csharp/programming-guide/concepts/linq/media/linq_flow1.png "LINQ_flow1")  
  
1.  Veri kaynağının tür bağımsız değişkeni aralık değişkeninin türünü belirler.  
  
2.  Seçili nesne türünü sorgu değişken türünü belirler. Burada `name` bir dizedir. Bu nedenle, sorgu değişkeni, bir `IEnumerable` \<dize >.  
  
3.  İçinde üzerinden sorgu değişkeni yinelendiğinde `foreach` deyimi. Sorgu değişkeni bir dizi dize olduğundan, yineleme değişkeni de bir dizedir.  
  
## <a name="queries-that-transform-the-source-data"></a>Kaynak veri dönüştürme sorguları  
 Aşağıdaki çizimde gösterildiği bir [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] sorgu basit bir dönüşüm verileri üzerindeki işlevini işlemi. Sorgu bir dizisini alır `Customer` nesneleri giriş olarak ve yalnızca seçer `Name` sonucun bir özellik. Çünkü `Name` bir dize, dize dizisi çıktı olarak bir sorgu oluşturur.  
  
 ![Veri türü dönüşümleri bir sorgu](../../../../csharp/programming-guide/concepts/linq/media/linq_flow2.png "LINQ_flow2")  
  
1.  Veri kaynağının tür bağımsız değişkeni aralık değişkeninin türünü belirler.  
  
2.  `select` Deyiminin döndüreceği `Name` özelliği tam yerine `Customer` nesnesi. Çünkü `Name` tür bağımsız değişkeni bir dize `custNameQuery` olan `string`değil `Customer`.  
  
3.  Çünkü `custNameQuery` dizeleri dizisidir `foreach` döngünün yineleme değişkeni de olmalıdır bir `string`.  
  
 Aşağıdaki çizimde biraz daha karmaşık bir dönüşüm gösterir. `select` Deyimi yalnızca iki üyeleri özgün yakalar anonim bir tür döndürür `Customer` nesnesi.  
  
 ![Veri türü dönüşümleri bir sorgu](../../../../csharp/programming-guide/concepts/linq/media/linq_flow3.png "LINQ_flow3")  
  
1.  Tür bağımsız değişkeni veri kaynağının her zaman sorgu aralık değişkeni türüdür.  
  
2.  Çünkü `select` bildirimi üreten anonim bir tür, sorgu değişkeni kullanarak örtük olarak yazılmalıdır `var`.  
  
3.  Sorgu değişkeninin türü örtük, olduğundan yineleme değişkeni `foreach` döngü de örtük olmalıdır.  
  
## <a name="letting-the-compiler-infer-type-information"></a>Tür bilgileri Infer derleyici izin vererek  
 Bir sorgu işlemi türü ilişkilerde anlamalısınız olmamakla birlikte, tüm iş bunu derleyici izin verme seçeneğini vardır. Anahtar sözcüğü [var](../../../../csharp/language-reference/keywords/var.md) herhangi bir yerel değişken bir sorgu işlemi olarak kullanılabilir. Aşağıdaki çizimde, yukarıda açıklanan örnek sayısı için 2 benzer. Ancak, sorgu işlemi her bir değişken için güçlü tür derleyici sağlar.  
  
 ![Örtülü yazma ile akış türü](../../../../csharp/programming-guide/concepts/linq/media/linq_flow4.png "LINQ_flow4")  
  
 Hakkında daha fazla bilgi için `var`, bkz: [örtük olarak yazılan yerel değişkenler](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C#'de LINQ Kullanmaya Başlama](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
