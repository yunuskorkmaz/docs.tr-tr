---
title: LINQ ile Veri Dönüştürmeler (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], data transformations
- source elements [LINQ in C#]
- joining multiple inputs [LINQ in C#]
- multiple outputs for one output sequence [LINQ in C#]
- subset of source elements [LINQ in C#]
- data sources [LINQ in C#], data transformations
- data transformations [LINQ in C#]
ms.assetid: 674eae9e-bc72-4a88-aed3-802b45b25811
ms.openlocfilehash: 393e3bd24c4bc8b89064e01e1048b24254f5f83b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635957"
---
# <a name="data-transformations-with-linq-c"></a>LINQ ile Veri Dönüştürmeler (C#)
Dil-Tümleşik Sorgu (LINQ) sadece veri almakla ilgili değildir. Aynı zamanda verileri dönüştürmek için güçlü bir araçtır. BIR LINQ sorgusu kullanarak, giriş olarak bir kaynak dizisi kullanabilir ve yeni bir çıktı dizisi oluşturmak için birçok şekilde değiştirebilirsiniz. Sıralama ve gruplandırma ile öğelerin kendilerini değiştirmeden sıranın kendisini değiştirebilirsiniz. Ama belki de LINQ sorgularının en güçlü özelliği yeni türler oluşturma yeteneğidir. Bu, [seçme](../../../language-reference/keywords/select-clause.md) yan tümcesinde gerçekleştirilir. Örneğin, aşağıdaki görevleri gerçekleştirebilirsiniz:  
  
- Birden çok giriş dizisini yeni bir türü olan tek bir çıkış dizisinde birleştirin.  
  
- Öğeleri kaynak dizisinde her öğenin yalnızca bir veya birkaç özelliğinden oluşan çıktı dizileri oluşturun.  
  
- Öğeleri kaynak veriler üzerinde gerçekleştirilen işlemlerin sonuçlarından oluşan çıktı dizileri oluşturun.  
  
- Farklı bir biçimde çıkış dizileri oluşturun. Örneğin, SQL satırlarından veya metin dosyalarından gelen verileri XML'e dönüştürebilirsiniz.  
  
 Bunlar sadece birkaç örnektir. Tabii ki, bu dönüşümler aynı sorguda çeşitli şekillerde birleştirilebilir. Ayrıca, bir sorgunun çıkış sırası yeni bir sorgu için giriş sırası olarak kullanılabilir.  
  
## <a name="joining-multiple-inputs-into-one-output-sequence"></a>Birden Çok Girdiyi Bir Çıkış Sırasına Katma  
 Birden fazla giriş dizisinden öğeler içeren bir çıktı dizisi oluşturmak için linq sorgusu kullanabilirsiniz. Aşağıdaki örnek, iki bellek içi veri yapısının nasıl birleştirilebildiğini gösterir, ancak XML veya SQL veya DataSet kaynaklarından gelen verileri birleştirmek için aynı ilkeler uygulanabilir. Aşağıdaki iki sınıf türünü varsayalım:  
  
 [!code-csharp[CsLINQGettingStarted#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#7)]  
  
 Aşağıdaki örnekte sorgu gösterilmektedir:  
  
 [!code-csharp[CSLinqGettingStarted#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#8)]  
  
 Daha fazla bilgi için [join yan tümcesi](../../../language-reference/keywords/join-clause.md) ve [seçme yan tümcesi'ne](../../../language-reference/keywords/select-clause.md)bakın.  
  
## <a name="selecting-a-subset-of-each-source-element"></a>Her Kaynak Öğesinin alt kümesini seçme  
 Kaynak dizideki her öğenin bir alt kümesini seçmenin iki birincil yolu vardır:  
  
1. Kaynak öğenin yalnızca bir üyesini seçmek için nokta işlemini kullanın. Aşağıdaki örnekte, bir `Customer` nesnenin adlı `City`dize de dahil olmak üzere birkaç ortak özellik içerdiğini varsayalım. Yürütüldüğünde, bu sorgu dizeleri bir çıkış dizisi üretecek.  
  
    ```csharp
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2. Kaynak öğeden birden fazla özellik içeren öğeler oluşturmak için, adlandırılmış bir nesne veya anonim türiçeren bir nesne başlatılması nı kullanabilirsiniz. Aşağıdaki örnek, her `Customer` öğeden iki özelliği kapsüllemek için anonim bir türün kullanımını gösterir:  
  
    ```csharp
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 Daha fazla bilgi için [Nesne ve Koleksiyon Başlangıç Layıcıları](../../classes-and-structs/object-and-collection-initializers.md) ve Anonim [Türleri'ne](../../classes-and-structs/anonymous-types.md)bakın.  
  
## <a name="transforming-in-memory-objects-into-xml"></a>Bellek İçi Nesneleri XML'e dönüştürme  
 LINQ sorguları, bellek içi veri yapıları, SQL veritabanları, ADO.NET Datasets ve XML akışları veya belgeler arasındaki verileri dönüştürmeyi kolaylaştırır. Aşağıdaki örnek, bellek içi veri yapısındaki nesneleri XML öğelerine dönüştürür.  
  
 [!code-csharp[CsLINQGettingStarted#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#9)]  
  
 Kod aşağıdaki XML çıktısını üretir:  
  
```xml  
<Root>  
  <student>  
    <First>Svetlana</First>  
    <Last>Omelchenko</Last>  
    <Scores>97,92,81,60</Scores>  
  </student>  
  <student>  
    <First>Claire</First>  
    <Last>O'Donnell</Last>  
    <Scores>75,84,91,39</Scores>  
  </student>  
  <student>  
    <First>Sven</First>  
    <Last>Mortensen</Last>  
    <Scores>88,94,65,91</Scores>  
  </student>  
</Root>  
```  
  
 Daha fazla bilgi için [C# (LINQ-XML) xml ağaçları oluşturma'ya](./creating-xml-trees-linq-to-xml-2.md)bakın.  
  
## <a name="performing-operations-on-source-elements"></a>Kaynak Öğeler Üzerinde İşlemler Gerçekleştirme  
 Bir çıktı dizisi kaynak diziden herhangi bir öğe veya öğe özelliği içermeyebilir. Çıktı bunun yerine, kaynak öğeleri girdi bağımsız değişkenleri olarak kullanılarak hesaplanan bir değer dizisi olabilir. Aşağıdaki basit sorgu, yürütüldüğünde, değerleri tür `double`elemanlarının kaynak sırasını temel alan bir hesaplamayı temsil eden bir dize dizisi verir.  
  
> [!NOTE]
> Sorgu başka bir etki alanına çevrilecekse, sorgu ifadelerindeki arama yöntemleri desteklenmez. Örneğin, SQL Server'ın bağlamı [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] olmadığı için sıradan bir C# yöntemini çağıramazsınız. Ancak, depolanan yordamları yöntemlerle eşleyebilir ve bunları çağırabilirsiniz. Daha fazla bilgi [için, Depolanan Yordamlar'a](../../../../framework/data/adonet/sql/linq/stored-procedures.md)bakın.  
  
 [!code-csharp[CsLINQGettingStarted#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#10)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dil-Tümleşik Sorgu (LINQ) (C#)](./index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)
- [LinQ xml (C#) için](./linq-to-xml-overview.md)
- [LINQ Sorgu İfadeleri](../../../linq/index.md)
- [yan tümceyi seçin](../../../language-reference/keywords/select-clause.md)
