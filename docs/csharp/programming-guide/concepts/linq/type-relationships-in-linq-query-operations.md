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
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635619"
---
# <a name="type-relationships-in-linq-query-operations-c"></a>LINQ Sorgu İşlemlerinde Tür İlişkileri (C#)
Sorguları etkili bir şekilde yazmak için, bir bütün sorgu işlemindeki değişkenlerin türlerinin birbirleriyle ilişkisini anlamalısınız. Bu ilişkileri anladıysanız, belgede LINQ örneklerini ve kod örneklerini daha kolay anlarsınız. Ayrıca, değişkenler `var`kullanılarak örtük olarak yazıldığında, arka planda neler olduğunu anlamış olursunuz.  
  
 LINQ sorgu işlemleri veri kaynağında, sorgunun kendisinde ve sorgu yürütmesinde kesin olarak türdedir. Sorgudaki değişkenlerin türü, veri kaynağındaki öğelerin türü ile ve `foreach` deyimindeki yineleme değişkeni türüyle uyumlu olmalıdır). Bu güçlü yazma, tür hatalarının Kullanıcı tarafından karşılaşmadan önce düzeltilebilecekleri derleme zamanında yakalanmasını güvence altına alır.  
  
 Bu tür ilişkilerini göstermek için, aşağıdaki örneklerin çoğu tüm değişkenler için açık yazma kullanır. Son örnek, [var](../../../language-reference/keywords/var.md)kullanarak örtük yazma kullandığınızda bile aynı ilkelerin nasıl uygulanacağını gösterir.  
  
## <a name="queries-that-do-not-transform-the-source-data"></a>Kaynak verileri dönüştürmeksizin sorgular  
 Aşağıdaki çizimde, verilerde dönüştürme gerçekleştirmeyen bir LINQ to Objects sorgu işlemi gösterilmektedir. Kaynak bir dize dizisi içerir ve sorgu çıktısı da dizeler dizisidir.  
  
 ![LINQ sorgusundaki veri türlerinin ilişkisini gösteren diyagram.](./media/type-relationships-in-linq-query-operations/linq-query-data-type-relation.png)  
  
1. Veri kaynağının tür bağımsız değişkeni, Aralık değişkeninin türünü belirler.  
  
2. Seçilen nesnenin türü, sorgu değişkeninin türünü belirler. Burada `name` bir dizedir. Bu nedenle, sorgu değişkeni bir `IEnumerable<string>`.  
  
3. Sorgu değişkeni `foreach` bildiriminde tekrarlanıyor. Sorgu değişkeni bir dizeler dizisi olduğundan, yineleme değişkeni de bir dizedir.  
  
## <a name="queries-that-transform-the-source-data"></a>Kaynak verileri dönüştüren sorgular  
 Aşağıdaki çizimde, verilerde basit bir dönüşüm gerçekleştiren [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] bir sorgu işlemi gösterilmektedir. Sorgu, girdi olarak `Customer` nesnelerden oluşan bir dizi alır ve yalnızca sonuç içinde `Name` özelliğini seçer. `Name` bir dize olduğundan, sorgu çıktı olarak bir dizi dize üretir.  
  
 ![Veri türünü dönüştüren bir sorgu gösteren diyagram.](./media/type-relationships-in-linq-query-operations/linq-query-transform-data-type.png)  
  
1. Veri kaynağının tür bağımsız değişkeni, Aralık değişkeninin türünü belirler.  
  
2. `select` ifade, tüm `Customer` nesnesi yerine `Name` özelliğini döndürür. `Name` bir dize olduğundan, `custNameQuery` tür bağımsız değişkeni `Customer`değil `string`.  
  
3. `custNameQuery` bir dizeler dizisi olduğundan, `foreach` döngüsünün yineleme değişkeni de bir `string`olmalıdır.  
  
 Aşağıdaki çizimde biraz daha karmaşık bir dönüştürme gösterilmektedir. `select` ifade, özgün `Customer` nesnesinin yalnızca iki üyesini yakalayan bir anonim tür döndürür.  
  
 ![Veri türünü dönüştüren daha karmaşık bir sorgu gösteren diyagram.](./media/type-relationships-in-linq-query-operations/linq-complex-query-transform-data-type.png)  
  
1. Veri kaynağının tür bağımsız değişkeni her zaman sorgudaki aralık değişkeninin türüdür.  
  
2. `select` deyimleri anonim bir tür oluşturduğundan, sorgu değişkeni `var`kullanılarak örtük olarak yazılmalıdır.  
  
3. Sorgu değişkeninin türü örtük olduğundan, `foreach` döngüsünde yineleme değişkeni de örtük olmalıdır.  
  
## <a name="letting-the-compiler-infer-type-information"></a>Derleyicinin tür bilgilerini çıkarmalarına izin verme  
 Bir sorgu işlemindeki tür ilişkilerini anlamanız gerekse de, derleyicinin tüm işleri gerçekleştirmesini sağlamak için seçeneğiniz vardır. [Var](../../../language-reference/keywords/var.md) anahtar sözcüğü, bir sorgu işlemindeki herhangi bir yerel değişken için kullanılabilir. Aşağıdaki çizim, daha önce açıklanan örnek numarası 2 ' ye benzer. Ancak, derleyici sorgu işlemindeki her değişken için güçlü tür sağlar.  
  
 ![Türü örtük olarak yazılan tür akışını gösteren diyagram.](./media/type-relationships-in-linq-query-operations/linq-type-flow-implicit-typing.png)  
  
 `var`hakkında daha fazla bilgi için bkz. [örtülü olarak yazılan yerel değişkenler](../../classes-and-structs/implicitly-typed-local-variables.md).  
