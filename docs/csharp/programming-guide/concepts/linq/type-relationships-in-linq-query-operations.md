---
title: LINQ Sorgu İşlemlerinde Tür İlişkileri (C#)
description: LINQ sorgusundaki değişkenlerin türlerinin birbirleriyle ilişkisini öğrenin. LINQ sorgu işlemleri veri kaynağında, sorguda ve yürütmede kesin olarak yazılır.
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
ms.openlocfilehash: 78cdb550e59bc82386d34f0e2bf6b1cae11d72de
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203988"
---
# <a name="type-relationships-in-linq-query-operations-c"></a>LINQ Sorgu İşlemlerinde Tür İlişkileri (C#)

Sorguları etkili bir şekilde yazmak için, bir bütün sorgu işlemindeki değişkenlerin türlerinin birbirleriyle ilişkisini anlamalısınız. Bu ilişkileri anladıysanız, belgede LINQ örneklerini ve kod örneklerini daha kolay anlarsınız. Ayrıca, değişkenler, kullanılarak örtük olarak yazıldığında ne olduğunu anlamış olursunuz `var` .  
  
 LINQ sorgu işlemleri veri kaynağında, sorgunun kendisinde ve sorgu yürütmesinde kesin olarak türdedir. Sorgudaki değişkenlerin türü, veri kaynağındaki öğelerin türüyle ve deyimdeki yineleme değişkeni türüyle uyumlu olmalıdır) `foreach` . Bu güçlü yazma, tür hatalarının Kullanıcı tarafından karşılaşmadan önce düzeltilebilecekleri derleme zamanında yakalanmasını güvence altına alır.  
  
 Bu tür ilişkilerini göstermek için, aşağıdaki örneklerin çoğu tüm değişkenler için açık yazma kullanır. Son örnek, [var](../../../language-reference/keywords/var.md)kullanarak örtük yazma kullandığınızda bile aynı ilkelerin nasıl uygulanacağını gösterir.  
  
## <a name="queries-that-do-not-transform-the-source-data"></a>Kaynak verileri dönüştürmeksizin sorgular  

 Aşağıdaki çizimde, verilerde dönüştürme gerçekleştirmeyen bir LINQ to Objects sorgu işlemi gösterilmektedir. Kaynak bir dize dizisi içerir ve sorgu çıktısı da dizeler dizisidir.  
  
 ![LINQ sorgusundaki veri türlerinin ilişkisini gösteren diyagram.](./media/type-relationships-in-linq-query-operations/linq-query-data-type-relation.png)  
  
1. Veri kaynağının tür bağımsız değişkeni, Aralık değişkeninin türünü belirler.  
  
2. Seçilen nesnenin türü, sorgu değişkeninin türünü belirler. İşte `name` bir dize. Bu nedenle, sorgu değişkeni bir `IEnumerable<string>` .  
  
3. Sorgu değişkeni, ifadesinde tekrarlanıyor `foreach` . Sorgu değişkeni bir dizeler dizisi olduğundan, yineleme değişkeni de bir dizedir.  
  
## <a name="queries-that-transform-the-source-data"></a>Kaynak verileri dönüştüren sorgular  

 Aşağıdaki çizimde, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] verilerde basit bir dönüşüm gerçekleştiren bir sorgu işlemi gösterilmektedir. Sorgu `Customer` , giriş olarak bir dizi nesne alır ve yalnızca `Name` sonuç içindeki özelliği seçer. `Name`Bir dize olduğundan, sorgu çıktı olarak bir dize dizisi üretir.  
  
 ![Veri türünü dönüştüren bir sorgu gösteren diyagram.](./media/type-relationships-in-linq-query-operations/linq-query-transform-data-type.png)  
  
1. Veri kaynağının tür bağımsız değişkeni, Aralık değişkeninin türünü belirler.  
  
2. `select`İfade, `Name` tüm nesne yerine özelliği döndürür `Customer` . `Name`Bir dize olduğundan, öğesinin tür bağımsız değişkeni `custNameQuery` `string` değildir `Customer` .  
  
3. `custNameQuery`Bir dize dizisi olduğundan, `foreach` döngünün yineleme değişkeni de bir olmalıdır `string` .  
  
 Aşağıdaki çizimde biraz daha karmaşık bir dönüştürme gösterilmektedir. `select`İfade, özgün nesnenin yalnızca iki üyesini yakalayan bir anonim tür döndürür `Customer` .  
  
 ![Veri türünü dönüştüren daha karmaşık bir sorgu gösteren diyagram.](./media/type-relationships-in-linq-query-operations/linq-complex-query-transform-data-type.png)  
  
1. Veri kaynağının tür bağımsız değişkeni her zaman sorgudaki aralık değişkeninin türüdür.  
  
2. `select`İfade anonim bir tür oluşturduğundan, sorgu değişkeninin kullanılarak örtük olarak yazılması gerekir `var` .  
  
3. Sorgu değişkeninin türü örtük olduğundan, `foreach` döngüdeki yineleme değişkeni de örtük olmalıdır.  
  
## <a name="letting-the-compiler-infer-type-information"></a>Derleyicinin tür bilgilerini çıkarmalarına izin verme  

 Bir sorgu işlemindeki tür ilişkilerini anlamanız gerekse de, derleyicinin tüm işleri gerçekleştirmesini sağlamak için seçeneğiniz vardır. [Var](../../../language-reference/keywords/var.md) anahtar sözcüğü, bir sorgu işlemindeki herhangi bir yerel değişken için kullanılabilir. Aşağıdaki çizim, daha önce açıklanan örnek numarası 2 ' ye benzer. Ancak, derleyici sorgu işlemindeki her değişken için güçlü tür sağlar.  
  
 ![Türü örtük olarak yazılan tür akışını gösteren diyagram.](./media/type-relationships-in-linq-query-operations/linq-type-flow-implicit-typing.png)  
  
 Hakkında daha fazla bilgi için `var` bkz. [örtülü olarak yazılan yerel değişkenler](../../classes-and-structs/implicitly-typed-local-variables.md).  
