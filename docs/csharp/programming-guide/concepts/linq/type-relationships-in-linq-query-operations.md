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
ms.openlocfilehash: 41853e6858fae9e8d449aeed95a6a84f343d5874
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635619"
---
# <a name="type-relationships-in-linq-query-operations-c"></a>LINQ Sorgu İşlemlerinde Tür İlişkileri (C#)
Sorguları etkili bir şekilde yazmak için, tam bir sorgu işlemindeki değişken türlerinin birbiriyle nasıl ilişkili olduğunu anlamanız gerekir. Bu ilişkileri anlarsanız, belgelerdeki LINQ örneklerini ve kod örneklerini daha kolay kavrarsınız. Ayrıca, değişkenler kullanılarak örtülü olarak yazıldığında perde arkasında neler oluştuğunu `var`anlayacaksınız.  
  
 LINQ sorgu işlemleri güçlü veri kaynağı, sorgu kendisi ve sorgu yürütme olarak yazılır. Sorgudaki değişkenlerin türü, veri kaynağındaki öğelerin türüyle ve `foreach` deyimdeki yineleme değişkeninin türüyle uyumlu olmalıdır. Bu güçlü yazım hatası, tür hatalarının, kullanıcılar bunlarla karşılaşmadan önce düzeltilmedikleri zaman derleme zamanında yakalandığını garanti eder.  
  
 Bu tür ilişkileri göstermek için, izleyen örneklerin çoğu tüm değişkenler için açık yazma kullanır. Son örnek, [var'ı](../../../language-reference/keywords/var.md)kullanarak örtülü yazı yı kullandığınızda bile aynı ilkelerin nasıl uygulandığını gösterir.  
  
## <a name="queries-that-do-not-transform-the-source-data"></a>Kaynak Verileri Dönüştürmeyan Sorgular  
 Aşağıdaki resimde, verilerde dönüşüm olmayan nesneler sorgu işlemi için bir LINQ gösterilmektedir. Kaynak dizeleri bir dizi içerir ve sorgu çıktısı da dizeleri bir dizidir.  
  
 ![LINQ sorgusundaki veri türlerinin ilişkisini gösteren diyagram.](./media/type-relationships-in-linq-query-operations/linq-query-data-type-relation.png)  
  
1. Veri kaynağının tür bağımsız değişkeni aralık değişkeninin türünü belirler.  
  
2. Seçili nesnenin türü sorgu değişkeninin türünü belirler. İşte `name` bir ip. Bu nedenle, sorgu `IEnumerable<string>`değişkeni bir .  
  
3. Sorgu değişkeni `foreach` deyimde üzerinde yinelenir. Sorgu değişkeni bir dize dizisi olduğundan, yineleme değişkeni de bir dizedir.  
  
## <a name="queries-that-transform-the-source-data"></a>Kaynak Verileri Dönüştüren Sorgular  
 Aşağıdaki resimde, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] veriler üzerinde basit bir dönüşüm gerçekleştiren bir sorgu işlemi gösterilmektedir. Sorgu, giriş olarak `Customer` nesnelerin bir dizi alır ve `Name` sonuç yalnızca özelliği seçer. Bir `Name` dize olduğundan, sorgu çıktı olarak dizeleri bir dizi üretir.  
  
 ![Veri türünü dönüştüren bir sorguyu gösteren diyagram.](./media/type-relationships-in-linq-query-operations/linq-query-transform-data-type.png)  
  
1. Veri kaynağının tür bağımsız değişkeni aralık değişkeninin türünü belirler.  
  
2. İfade, `select` nesnenin `Name` tamamı `Customer` yerine özelliği döndürür. Bir `Name` dize olduğundan, tür `custNameQuery` `string`bağımsız `Customer`değişkeni , değil.  
  
3. Dizeleri bir dizi `custNameQuery` olduğundan, `foreach` döngü yineleme değişkeni de bir `string`.  
  
 Aşağıdaki resimde biraz daha karmaşık bir dönüşüm gösterilmektedir. İfade, `select` özgün `Customer` nesnenin yalnızca iki üyesini yakalayan anonim bir türü döndürür.  
  
 ![Veri türünü dönüştüren daha karmaşık bir sorgu gösteren diyagram.](./media/type-relationships-in-linq-query-operations/linq-complex-query-transform-data-type.png)  
  
1. Veri kaynağının tür bağımsız değişkeni her zaman sorgudaki aralık değişkeninin türüdür.  
  
2. İfade `select` anonim bir tür oluşturduğundan, sorgu değişkeni örtülü `var`olarak yazılmalıdır.  
  
3. Sorgu değişkeninin türü örtülü olduğundan, döngüdeki yineleme `foreach` değişkeninin de örtülü olması gerekir.  
  
## <a name="letting-the-compiler-infer-type-information"></a>Derleyicinin tür bilgilerini çıkarmasını izin verme  
 Bir sorgu işlemindeki tür ilişkilerini anlamanız gerekirken, derleyicinin tüm işi sizin için yapmasına izin verme seçeneğiniz vardır. [Var](../../../language-reference/keywords/var.md) anahtar sözcüğü, sorgu işlemindeki herhangi bir yerel değişken için kullanılabilir. Aşağıdaki çizim, daha önce tartışılan örnek 2'ye benzer. Ancak, derleyici sorgu işleminde her değişken için güçlü türü sağlar.  
  
 ![Örtük yazı ile tür akışını gösteren diyagram.](./media/type-relationships-in-linq-query-operations/linq-type-flow-implicit-typing.png)  
  
 Hakkında `var`daha fazla bilgi için bkz: [Örtülü Olarak Yazılan Yerel Değişkenler.](../../classes-and-structs/implicitly-typed-local-variables.md)  
