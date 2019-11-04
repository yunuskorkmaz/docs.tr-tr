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
ms.openlocfilehash: 8dd57a43f814d7e41ec74af3eeb6d797fef41c9c
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418626"
---
# <a name="data-transformations-with-linq-c"></a>LINQ ile Veri Dönüştürmeler (C#)
[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] yalnızca verileri alma hakkında değildir. Ayrıca, verileri dönüştürmek için güçlü bir araçtır. Bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgusu kullanarak, giriş olarak bir kaynak sırası kullanabilir ve yeni bir çıkış sırası oluşturmak için bunu birçok şekilde değiştirebilirsiniz. Sıralamayı sıralama ve gruplama yoluyla öğeleri değiştirmeden değiştirebilirsiniz. Ancak, [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgularının en güçlü özelliği yeni türler oluşturma olanağıdır. Bu, [Select](../../../language-reference/keywords/select-clause.md) yan tümcesinde gerçekleştirilir. Örneğin, aşağıdaki görevleri gerçekleştirebilirsiniz:  
  
- Birden çok giriş dizisini yeni bir türe sahip tek bir çıkış dizisinde birleştirin.  
  
- Öğeleri, kaynak dizideki her öğenin yalnızca bir veya birkaç özelliklerinden oluşan çıkış dizileri oluşturun.  
  
- Öğeleri, kaynak verilerde gerçekleştirilen işlemlerin sonuçlarından oluşan çıkış dizileri oluşturun.  
  
- Çıkış dizilerini farklı biçimde oluşturun. Örneğin, verileri SQL satırlarından veya metin dosyalarından XML 'e dönüştürebilirsiniz.  
  
 Bunlar yalnızca birkaç örnektir. Tabii ki, bu dönüşümler aynı sorgudaki çeşitli şekillerde birleştirilebilir. Ayrıca, bir sorgunun çıkış sırası yeni bir sorgu için giriş sırası olarak kullanılabilir.  
  
## <a name="joining-multiple-inputs-into-one-output-sequence"></a>Birden Çok Girdiyi Bir Çıkış Sırasına Katma  
 Birden fazla giriş dizisinin öğelerini içeren bir çıkış sırası oluşturmak için [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] bir sorgu kullanabilirsiniz. Aşağıdaki örnek, iki bellek içi veri yapısının nasıl birleştirileceğini gösterir, ancak aynı ilkeler XML veya SQL veya veri kümesi kaynaklarından verileri birleştirmek için uygulanabilir. Aşağıdaki iki sınıf türünü varsayın:  
  
 [!code-csharp[CsLINQGettingStarted#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#7)]  
  
 Aşağıdaki örnekte sorgu gösterilmektedir:  
  
 [!code-csharp[CSLinqGettingStarted#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#8)]  
  
 Daha fazla bilgi için bkz. [JOIN yan tümcesi](../../../language-reference/keywords/join-clause.md) ve [Select yan tümcesi](../../../language-reference/keywords/select-clause.md).  
  
## <a name="selecting-a-subset-of-each-source-element"></a>Her Kaynak Öğesinin alt kümesini seçme  
 Kaynak dizideki her bir öğenin alt kümesini seçmek için iki temel yol vardır:  
  
1. Kaynak öğenin yalnızca bir üyesini seçmek için, nokta işlemini kullanın. Aşağıdaki örnekte, bir `Customer` nesnesinin `City`adlı bir dize de dahil olmak üzere birkaç ortak özellik içerdiğini varsayın. Yürütüldüğünde, bu sorgu dizelerin çıkış dizisini üretir.  
  
    ```csharp
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2. Kaynak öğeden birden fazla özellik içeren öğeler oluşturmak için, bir nesne başlatıcısını adlandırılmış bir nesne veya anonim bir türle birlikte kullanabilirsiniz. Aşağıdaki örnek, her bir `Customer` öğesinden iki özelliği kapsüllemek için anonim bir türün kullanımını gösterir:  
  
    ```csharp
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 Daha fazla bilgi için bkz. [nesne ve koleksiyon başlatıcıları](../../classes-and-structs/object-and-collection-initializers.md) ve [anonim türler](../../classes-and-structs/anonymous-types.md).  
  
## <a name="transforming-in-memory-objects-into-xml"></a>Bellek İçi Nesneleri XML'e dönüştürme  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorguları, bellek içi veri yapıları, SQL veritabanları, ADO.NET veri kümeleri ve XML akışları veya belgeler arasında veri dönüştürmeyi kolaylaştırır. Aşağıdaki örnek, bellek içi veri yapısındaki nesneleri XML öğelerine dönüştürür.  
  
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
  
 Daha fazla bilgi için bkz. [XML ağaçlarını oluşturma C# (LINQ to XML)](./creating-xml-trees-linq-to-xml-2.md).  
  
## <a name="performing-operations-on-source-elements"></a>Kaynak Öğeler Üzerinde İşlemler Gerçekleştirme  
 Çıkış sırası, kaynak dizisinden herhangi bir öğe veya öğe özelliği içermeyebilir. Çıktı bunun yerine, kaynak öğeleri giriş bağımsız değişkenleri olarak kullanılarak hesaplanan bir değer dizisi olabilir. Aşağıdaki basit sorgu yürütüldüğünde, değerleri, `double`türündeki öğelerin kaynak dizisine göre hesaplamayı temsil eden bir dize dizisi çıkarır.  
  
> [!NOTE]
> Sorgu başka bir etki alanına çevrilecektir sorgu ifadelerinde çağırma yöntemi desteklenmez. Örneğin, SQL Server hiçbir bağlamı olmadığından [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] sıradan C# bir yöntem çağrılamaz. Ancak, saklı yordamları yöntemlere eşleyebilir ve bunları çağırabilirsiniz. Daha fazla bilgi için bkz. [saklı yordamlar](../../../../framework/data/adonet/sql/linq/stored-procedures.md).  
  
 [!code-csharp[CsLINQGettingStarted#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#10)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dil ile tümleşik sorgu (LINQ) (C#)](./index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)
- [LINQ to XML (C#)](./linq-to-xml-overview.md)
- [LINQ sorgu Ifadeleri](../../../linq/index.md)
- [select yan tümcesi](../../../language-reference/keywords/select-clause.md)
