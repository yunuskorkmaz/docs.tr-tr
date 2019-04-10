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
ms.openlocfilehash: 5928478518b0bc1eb498381567d52d5ddba4d8b7
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59326066"
---
# <a name="data-transformations-with-linq-c"></a>LINQ ile Veri Dönüştürmeler (C#)
[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] yalnızca veri alma hakkında değil. Veri dönüştürme için de güçlü bir araçtır. Kullanarak bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu, giriş ve yeni bir çıkış dizisi oluşturmak için birçok şekilde değiştirme gibi bir kaynak sırası kullanabilirsiniz. Öğeleri sıralama ve gruplandırma değiştirmeden dizisi kendisini değiştirebilirsiniz. Ancak belki de en güçlü özelliğidir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgulardır yeni türleri oluşturma olanağı. Bu, gerçekleştirilir [seçin](../../../../csharp/language-reference/keywords/select-clause.md) yan tümcesi. Örneğin, aşağıdaki görevleri gerçekleştirebilirsiniz:  
  
-   Birden çok giriş dizilerini yeni bir türü olan bir tek bir çıkış sırasına birleştirin.  
  
-   Öğeleri kaynak sırasındaki her öğenin yalnızca bir veya birkaç özellikleri oluşur çıkış sıraları oluşturun.  
  
-   Kaynak veriler üzerinde gerçekleştirilen işlemlerin sonuçlarını öğeleri oluşur çıkış sıraları oluşturun.  
  
-   Çıkış sıraları farklı bir biçimde oluşturun. Örneğin, verileri SQL satırları veya metin dosyalarından XML'e dönüştürebilirsiniz.  
  
 Bunlar yalnızca birkaç örnektir. Elbette, bu dönüştürmeleri, çeşitli yollarla aynı sorguda birleştirilebilir. Ayrıca, bir sorgu çıkış dizisi, yeni bir sorgu için giriş dizisi kullanılabilir.  
  
## <a name="joining-multiple-inputs-into-one-output-sequence"></a>Birden Çok Girdiyi Bir Çıkış Sırasına Katma  
 Kullanabileceğiniz bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] birden fazla giriş dizisinin öğeleri içeren bir çıkış dizisi oluşturmak için sorgu. Aşağıdaki örnek, iki bellek içi veri yapılarını birleştirilecek gösterilmektedir, ancak aynı ilkeler, XML veya SQL veya veri kaynaklarından alınan verileri birleştirmek için uygulanabilir. Aşağıdaki iki sınıf türleri varsayın:  
  
 [!code-csharp[CsLINQGettingStarted#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#7)]  
  
 Aşağıdaki örnek sorgu gösterir:  
  
 [!code-csharp[CSLinqGettingStarted#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#8)]  
  
 Daha fazla bilgi için [JOIN yan tümcesi](../../../../csharp/language-reference/keywords/join-clause.md) ve [select yan tümcesi](../../../../csharp/language-reference/keywords/select-clause.md).  
  
## <a name="selecting-a-subset-of-each-source-element"></a>Her Kaynak Öğesinin alt kümesini seçme  
 Kaynak dizideki her öğe kümesini seçmek için iki temel yol vardır:  
  
1. Kaynak öğesi yalnızca bir üye seçmek için nokta işlemi kullanın. Aşağıdaki örnekte, varsayımında bir `Customer` nesnesini içeren bir dize adlı de dahil olmak üzere birkaç ortak özellikler `City`. Bu sorgu yürütüldüğünde, dize bir çıkış sırası oluşturur.  
  
    ```csharp
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2. Kaynak öğesi birden fazla özelliği içeren öğeler oluşturmak için bir nesne Başlatıcı adlandırılmış bir nesneye veya anonim bir tür ile kullanabilirsiniz. Aşağıdaki örnek her iki özellik yalıtılacak anonim bir türün kullanımı gösterilmektedir `Customer` öğesi:  
  
    ```csharp
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 Daha fazla bilgi için [nesne ve koleksiyon başlatıcıları](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md) ve [anonim türler](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
## <a name="transforming-in-memory-objects-into-xml"></a>Bellek İçi Nesneleri XML'e dönüştürme  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorguları bellek içi veri yapıları, SQL veritabanları arasında verileri dönüştürmek kolaylaştırır [!INCLUDE[vstecado](~/includes/vstecado-md.md)] veri kümeleri ve XML akışlarını veya belgeler. Aşağıdaki örnek, nesneleri bir bellek içi veri yapısı XML öğeleri dönüştürür.  
  
 [!code-csharp[CsLINQGettingStarted#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#9)]  
  
 Kod aşağıdaki XML çıktıyı üretir:  
  
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
  
 Daha fazla bilgi için [C# (LINQ to XML) XML ağaçları oluşturma](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees-linq-to-xml-2.md).  
  
## <a name="performing-operations-on-source-elements"></a>Kaynak Öğeler Üzerinde İşlemler Gerçekleştirme  
 Bir çıkış dizisi, herhangi bir öğe veya öğe özellikleri için kaynak sırasından içermeyebilir. Çıkışı, bunun yerine kaynak öğeleri giriş bağımsız değişkeni kullanarak hesaplanan değerler bir dizi olabilir. Yürütüldüğünde, aşağıdaki basit sorgu, bir dizi dize değerleri temsil eden türünde öğeler kaynak dizi temel hesaplama çıkarır `double`.  
  
> [!NOTE]
>  Sorgu başka bir etki alanına çevrilir, sorgu ifadelerinde yöntem çağırma desteklenmiyor. Örneğin, bir normal C# tuto metodu nelze vyvolat [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] SQL Server için hiçbir bağlam olduğundan. Ancak, eşleştirme yöntemleri için saklı yordamlar ve bu çağırın. Daha fazla bilgi için [saklı yordamlar](../../../../framework/data/adonet/sql/linq/stored-procedures.md).  
  
 [!code-csharp[CsLINQGettingStarted#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#10)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dil ile tümleşik sorgu (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)
- [LINQ - SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)
- [LINQ - DataSet](../../../../framework/data/adonet/linq-to-dataset.md)
- [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)
- [LINQ Sorgu İfadeleri](../../../../csharp/programming-guide/linq-query-expressions/index.md)
- [select tümcesi](../../../../csharp/language-reference/keywords/select-clause.md)
