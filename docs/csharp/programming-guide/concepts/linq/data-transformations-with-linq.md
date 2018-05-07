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
ms.openlocfilehash: c165f78c53cec0417d39320580b812ff01fef68b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="data-transformations-with-linq-c"></a>LINQ ile Veri Dönüştürmeler (C#)
[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] yalnızca veri alma hakkında değil. Veri dönüştürme için de güçlü bir araçtır. Kullanarak bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu olarak giriş ve yeni bir çıkış sırası oluşturmak için birçok yolla değiştirme kaynağı sırası kullanabilirsiniz. Öğeleri sıralama ve Gruplama değiştirmeden dizisi kendisini değiştirebilirsiniz. Ancak, belki de en güçlü özelliği [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgudur yeni türleri oluşturma yeteneği. Bu, gerçekleştirilir [seçin](../../../../csharp/language-reference/keywords/select-clause.md) yan tümcesi. Örneğin, aşağıdaki görevleri gerçekleştirebilirsiniz:  
  
-   Birden çok giriş dizilerini yeni bir türe sahip bir tek bir çıkış sırası birleştirin.  
  
-   Kaynak sıradaki her bir öğe yalnızca bir veya birkaç özelliklerini öğeleri oluşur çıkış sıraları oluşturun.  
  
-   Kaynak veriler üzerinde gerçekleştirilen işlemler sonuçlarını öğeleri oluşur çıkış sıraları oluşturun.  
  
-   Çıkış sıraları farklı bir biçimde oluşturun. Örneğin, XML verileri SQL satırları veya metin dosyalarından dönüştürebilirsiniz.  
  
 Bu, yalnızca birkaç örnek verilmiştir. Elbette, bu dönüşümleri aynı sorguda çeşitli şekillerde birleştirilebilir. Ayrıca, bir sorgu çıkış dizisi giriş dizisi yeni bir sorgu için kullanılabilir.  
  
## <a name="joining-multiple-inputs-into-one-output-sequence"></a>Birden Çok Girdiyi Bir Çıkış Sırasına Katma  
 Kullanabileceğiniz bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] birden fazla giriş sırası öğeleri içeren bir çıkış sırası oluşturmak için sorgu. Aşağıdaki örnekte, iki bellek içi veri yapılarını birleştirmek gösterilmektedir, ancak aynı ilkeler XML veya SQL veya veri kümesi kaynaklardan veri birleştirmek için uygulanabilir. Aşağıdaki iki sınıf türleri varsayın:  
  
 [!code-csharp[CsLINQGettingStarted#7](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_1.cs)]  
  
 Aşağıdaki örnek sorgu gösterir:  
  
 [!code-csharp[CSLinqGettingStarted#8](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_2.cs)]  
  
 Daha fazla bilgi için bkz: [JOIN yan tümcesi](../../../../csharp/language-reference/keywords/join-clause.md) ve [select yan tümcesi](../../../../csharp/language-reference/keywords/select-clause.md).  
  
## <a name="selecting-a-subset-of-each-source-element"></a>Her Kaynak Öğesinin alt kümesini seçme  
 Her öğe kümesini kaynak sırasını seçmek için birincil iki yolu vardır:  
  
1.  Source öğesi yalnızca bir üye seçmek için nokta işlemi kullanın. Aşağıdaki örnekte, varsayımında bir `Customer` nesnesini içeren adlı bir dize dahil olmak üzere birkaç ortak özellikler `City`. Çalıştırıldığında, bu sorgu dizeleri çıkış dizisi oluşturur.  
  
    ```  
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2.  Source öğesi birden fazla özelliğinden içeren öğeleri oluşturmak için nesne Başlatıcı adlandırılmış bir nesne veya anonim bir tür ile kullanabilirsiniz. Aşağıdaki örnek, her iki özellik kapsülleyen anonim bir tür kullanımını gösterir `Customer` öğe:  
  
    ```  
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 Daha fazla bilgi için bkz: [nesne ve koleksiyon başlatıcıları](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md) ve [anonim türler](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
## <a name="transforming-in-memory-objects-into-xml"></a>Bellek İçi Nesneleri XML'e dönüştürme  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorguları bellek içi veri yapılarını, SQL veritabanları arasında verileri dönüştürmek kolaylaştırır [!INCLUDE[vstecado](~/includes/vstecado-md.md)] veri kümelerini ve XML akışları ya da belgeler. Aşağıdaki örnekte bir bellek içi veri yapısı nesneleri XML elemanlara dönüştürür.  
  
 [!code-csharp[CsLINQGettingStarted#9](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_3.cs)]  
  
 Kod şu XML çıkışı üretir:  
  
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
  
 Daha fazla bilgi için bkz: [oluşturma XML ağaçları C# (LINQ-XML)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees-linq-to-xml-2.md).  
  
## <a name="performing-operations-on-source-elements"></a>Kaynak Öğeler Üzerinde İşlemler Gerçekleştirme  
 Çıkış dizisi, herhangi bir öğe veya kaynak sıradaki öğenin özelliklerinden içermeyebilir. Çıkışı, bunun yerine kaynak öğelerin giriş bağımsız değişken olarak kullanarak hesaplanan bir değerleri dizisi olabilir. Yürütüldüğünde, aşağıdaki basit sorgu, bir dizi dize değerleri temsil eden türündeki öğeler kaynak sıralamasına dayalı bir hesaplama çıkarır `double`.  
  
> [!NOTE]
>  Sorgu başka bir etki alanına çevrilir, sorgu ifadelerinde yöntemleri çağırma desteklenmiyor. Örneğin, bir sıradan C# yöntemi çağrılamıyor [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] SQL Server bağlam için içerdiğinden. Ancak, saklı yordamlar eşleştirme için yöntemleri ve bu çağırın. Daha fazla bilgi için bkz: [saklı yordamlar](../../../../framework/data/adonet/sql/linq/stored-procedures.md).  
  
 [!code-csharp[CsLINQGettingStarted#10](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_4.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dil ile tümleşik sorgu (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)  
 [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
 [LINQ-XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)  
 [LINQ Sorgu ifadeleri](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [select yan tümcesi](../../../../csharp/language-reference/keywords/select-clause.md)
