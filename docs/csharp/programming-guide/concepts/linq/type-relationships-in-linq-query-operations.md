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
ms.openlocfilehash: b58219a8a4d45ce01f80fd367ed56b13a773e4bc
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66483405"
---
# <a name="type-relationships-in-linq-query-operations-c"></a>LINQ Sorgu İşlemlerinde Tür İlişkileri (C#)
Etkili bir şekilde sorgu yazmak için bir sorgu işleminde değişken türlerinin birbirleriyle nasıl ilişkili olduğunu anlamanız gerekir. Bu ilişkileri anladıysanız, daha kolay anlarsınız [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] örneklerini ve kod örneklerini belgelerinde. Ayrıca, değişkenleri kullanarak örtük olarak belirlenmiş ne olacağını perde arkasında anlayacaksınız `var`.  
  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu işlemleri veri kaynağının, sorgu ve sorgu yürütme kesin olarak belirlenmiştir. Sorgudaki değişkenlerin türü veri kaynağındaki öğelerin türüyle ve yineleme değişkeni türüyle uyumlu olacak `foreach` deyimi. Bu güçlü yazım, Yazım hatalarının kullanıcılar karşılaşmadan olduğunda bunlar düzeltilebilir derleme zamanında yakalanabilmesini ve garanti eder.  
  
 Bu tür ilişkilerini göstermek için aşağıdaki örneklerde çoğunu tüm değişkenler için açık yazım kullanın. Son örnek nasıl bile kullanarak dolaylı yazma kullandığınızda, aynı ilkeler geçerlidir gösterir [var](../../../../csharp/language-reference/keywords/var.md).  
  
## <a name="queries-that-do-not-transform-the-source-data"></a>Kaynak verileri Dönüştürmeyen sorgular  
 Aşağıdaki çizimde gösterildiği bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] nesneler sorgu veriler üzerinde hiçbir dönüştürme gerçekleştirdiği bir işlem. Kaynak bir dize sırası içerir ve sorgu çıktısı da dizeler dizisidir.  
  
 ![Bir LINQ Sorgu veri türlerinin ilişkiyi gösteren diyagram.](./media/type-relationships-in-linq-query-operations/linq-query-data-type-relation.png)  
  
1. Veri kaynağının tür bağımsız değişkeni aralık değişkeninin türünü belirler.  
  
2. Seçilen nesne türü, sorgu değişkeni türünü belirler. Burada `name` bir dizedir. Bu nedenle sorgu değişkeni olan bir `IEnumerable<string>`.  
  
3. Sorgu değişkeni yinelenir `foreach` deyimi. Sorgu değişkeni bir dizeler sırası olduğundan, yineleme değişkeni de bir dizedir.  
  
## <a name="queries-that-transform-the-source-data"></a>Kaynak verileri dönüştüren sorgular  
 Aşağıdaki çizimde gösterildiği bir [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] sorgu veri üzerinde basit bir dönüştürme gerçekleştiren işlemi. Sorgu dizisi alır `Customer` nesneler giriş olarak ve yalnızca seçer `Name` sonucun bir özellik. Çünkü `Name` bir dize, dize sırası çıktı olarak bir sorgu oluşturur.  
  
 ![Veri türünü dönüştüren bir sorgu gösteren diyagram.](./media/type-relationships-in-linq-query-operations/linq-query-transform-data-type.png)  
  
1. Veri kaynağının tür bağımsız değişkeni aralık değişkeninin türünü belirler.  
  
2. `select` Deyimi döndürür `Name` özelliği yerine tam `Customer` nesne. Çünkü `Name` tür bağımsız değişkeni bir dize ise `custNameQuery` olduğu `string`değil `Customer`.  
  
3. Çünkü `custNameQuery` dizeler dizisidir `foreach` döngüsünün yineleme değişkeni de olmalıdır bir `string`.  
  
 Aşağıdaki çizim biraz daha karmaşık bir dönüştürmeyi gösterir. `select` Deyimi özgün yalnızca iki üyesini yakalayan, anonim bir tür döndürür `Customer` nesne.  
  
 ![Veri türü dönüşümleri daha karmaşık bir sorgu gösteren diyagram.](./media/type-relationships-in-linq-query-operations/linq-complex-query-transform-data-type.png)  
  
1. Veri kaynağının tür bağımsız değişkeni her zaman sorgudaki Aralık değişkeninin türüdür.  
  
2. Çünkü `select` deyimi anonim bir tür ürettiğinden, sorgu değişkeni kullanarak dolaylı olarak yazılmalıdır `var`.  
  
3. Sorgu değişkeninin türü örtülü olduğundan yineleme değişkeni `foreach` döngü de örtülü olmalıdır.  
  
## <a name="letting-the-compiler-infer-type-information"></a>Derleyicinin tür bilgilerini çıkarmasına izin vererek  
 Sorgu işlemindeki tür ilişkilerini anlamanız gerekir, ancak derleyicinin tüm çalışmayı sizin için gerçekleştirmesini sağlamak için seçeneğiniz vardır. Anahtar sözcüğü [var](../../../../csharp/language-reference/keywords/var.md) sorgu işlemindeki herhangi bir yerel değişken için kullanılabilir. Aşağıdaki çizim, daha önce bahsedilen 2 numaralı örneğe benzer. Ancak, derleyici, sorgu işlemindeki her değişken için güçlü tür sağlar.  
  
 ![Örtülü yazma ile tür akışını gösteren diyagram.](./media/type-relationships-in-linq-query-operations/linq-type-flow-implicit-typing.png)  
  
 Hakkında daha fazla bilgi için `var`, bkz: [örtük olarak yazılan yerel değişkenler](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
