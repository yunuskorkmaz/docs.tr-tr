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
ms.openlocfilehash: 154501d666b467c94f5d1dd721f1e2303189c908
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43484830"
---
# <a name="type-relationships-in-linq-query-operations-c"></a>LINQ Sorgu İşlemlerinde Tür İlişkileri (C#)
Etkili bir şekilde sorgu yazmak için bir sorgu işleminde değişken türlerinin birbirleriyle nasıl ilişkili olduğunu anlamanız gerekir. Bu ilişkileri anladıysanız, daha kolay anlarsınız [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] örneklerini ve kod örneklerini belgelerinde. Ayrıca, değişkenleri kullanarak örtük olarak belirlenmiş ne olacağını perde arkasında anlayacaksınız `var`.  
  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu işlemleri veri kaynağının, sorgu ve sorgu yürütme kesin olarak belirlenmiştir. Sorgudaki değişkenlerin türü veri kaynağındaki öğelerin türüyle ve yineleme değişkeni türüyle uyumlu olacak `foreach` deyimi. Bu güçlü yazım, Yazım hatalarının kullanıcılar karşılaşmadan olduğunda bunlar düzeltilebilir derleme zamanında yakalanabilmesini ve garanti eder.  
  
 Bu tür ilişkilerini göstermek için aşağıdaki örneklerde çoğunu tüm değişkenler için açık yazım kullanın. Son örnek nasıl bile kullanarak dolaylı yazma kullandığınızda, aynı ilkeler geçerlidir gösterir [var](../../../../csharp/language-reference/keywords/var.md).  
  
## <a name="queries-that-do-not-transform-the-source-data"></a>Kaynak verileri Dönüştürmeyen sorgular  
 Aşağıdaki çizimde gösterildiği bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] nesneler sorgu veriler üzerinde hiçbir dönüştürme gerçekleştirdiği bir işlem. Kaynak bir dize sırası içerir ve sorgu çıktısı da dizeler dizisidir.  
  
 ![Veri ilişkisi türleri bir LINQ Sorgu](../../../../csharp/programming-guide/concepts/linq/media/linq_flow1.png "LINQ_flow1")  
  
1.  Veri kaynağının tür bağımsız değişkeni aralık değişkeninin türünü belirler.  
  
2.  Seçilen nesne türü, sorgu değişkeni türünü belirler. Burada `name` bir dizedir. Bu nedenle sorgu değişkeni olan bir `IEnumerable<string>`.  
  
3.  Sorgu değişkeni yinelenir `foreach` deyimi. Sorgu değişkeni bir dizeler sırası olduğundan, yineleme değişkeni de bir dizedir.  
  
## <a name="queries-that-transform-the-source-data"></a>Kaynak verileri dönüştüren sorgular  
 Aşağıdaki çizimde gösterildiği bir [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] sorgu veri üzerinde basit bir dönüştürme gerçekleştiren işlemi. Sorgu dizisi alır `Customer` nesneler giriş olarak ve yalnızca seçer `Name` sonucun bir özellik. Çünkü `Name` bir dize, dize sırası çıktı olarak bir sorgu oluşturur.  
  
 ![Veri türünü dönüştüren bir sorgu](../../../../csharp/programming-guide/concepts/linq/media/linq_flow2.png "LINQ_flow2")  
  
1.  Veri kaynağının tür bağımsız değişkeni aralık değişkeninin türünü belirler.  
  
2.  `select` Deyimi döndürür `Name` özelliği yerine tam `Customer` nesne. Çünkü `Name` tür bağımsız değişkeni bir dize ise `custNameQuery` olduğu `string`değil `Customer`.  
  
3.  Çünkü `custNameQuery` dizeler dizisidir `foreach` döngüsünün yineleme değişkeni de olmalıdır bir `string`.  
  
 Aşağıdaki çizim biraz daha karmaşık bir dönüştürmeyi gösterir. `select` Deyimi özgün yalnızca iki üyesini yakalayan, anonim bir tür döndürür `Customer` nesne.  
  
 ![Veri türünü dönüştüren bir sorgu](../../../../csharp/programming-guide/concepts/linq/media/linq_flow3.png "LINQ_flow3")  
  
1.  Veri kaynağının tür bağımsız değişkeni her zaman sorgudaki Aralık değişkeninin türüdür.  
  
2.  Çünkü `select` deyimi anonim bir tür ürettiğinden, sorgu değişkeni kullanarak dolaylı olarak yazılmalıdır `var`.  
  
3.  Sorgu değişkeninin türü örtülü olduğundan yineleme değişkeni `foreach` döngü de örtülü olmalıdır.  
  
## <a name="letting-the-compiler-infer-type-information"></a>Derleyicinin tür bilgilerini çıkarmasına izin vererek  
 Sorgu işlemindeki tür ilişkilerini anlamanız gerekir, ancak derleyicinin tüm çalışmayı sizin için gerçekleştirmesini sağlamak için seçeneğiniz vardır. Anahtar sözcüğü [var](../../../../csharp/language-reference/keywords/var.md) sorgu işlemindeki herhangi bir yerel değişken için kullanılabilir. Aşağıdaki çizim, daha önce bahsedilen 2 numaralı örneğe benzer. Ancak, derleyici, sorgu işlemindeki her değişken için güçlü tür sağlar.  
  
 ![Akış türü örtülü yazma ile](../../../../csharp/programming-guide/concepts/linq/media/linq_flow4.png "LINQ_flow4")  
  
 Hakkında daha fazla bilgi için `var`, bkz: [örtük olarak yazılan yerel değişkenler](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C#'de LINQ Kullanmaya Başlama](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
