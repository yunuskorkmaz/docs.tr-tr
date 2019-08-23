---
title: LINQ Sorgu İşlemlerinde Tür İlişkileri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variable relationships [LINQ in Visual Basic]
- type information inferred [LINQ in Visual Basic]
- type relationships [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], type relationships
- data sources [LINQ in Visual Basic], type relationships
- LINQ [Visual Basic], type relationships
- inferring type information [LINQ in Visual Basic]
- relationships [LINQ in Visual Basic]
ms.assetid: b5ff4da5-f3fd-4a8e-aaac-1cbf52fa16f6
ms.openlocfilehash: 4851d0a74de38f0fb6b6deee34cf7b3e66eb11b4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937487"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a>LINQ Sorgu İşlemlerinde Tür İlişkileri (Visual Basic)
[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] Sorgu işlemlerinde kullanılan değişkenler kesin olarak türdedir ve birbirleriyle uyumlu olmalıdır. Güçlü yazma, veri kaynağında, sorgunun kendisinde ve sorgu yürütmesinde kullanılır. Aşağıdaki çizimde bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorguyu tanımlamak için kullanılan terimler tanımlanmaktadır. Bir sorgunun kısımları hakkında daha fazla bilgi için bkz. [temel sorgu işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).  
  
 ![Öğeleri vurgulanmış bir sözde kod sorgusunu gösteren ekran görüntüsü.](./media/type-relationships-in-query-operations/linq-query-description-terms.png)  
  
 Sorgudaki aralık değişkeninin türü, veri kaynağındaki öğelerin türüyle uyumlu olmalıdır. Sorgu değişkeninin türü, `Select` yan tümcesinde tanımlanan dizi öğesiyle uyumlu olmalıdır. Son olarak, dizi öğelerinin türü sorguyu yürüten `For Each` ifadede kullanılan döngü denetimi değişkeninin türüyle uyumlu olmalıdır. Bu güçlü yazma, derleme zamanında tür hatalarının tanımlanmasını kolaylaştırır.  
  
 Visual Basic, *örtülü yazma*olarak da bilinen yerel tür çıkarımı uygulayarak güçlü yazma kullanışlı hale getirir. Bu özellik, önceki örnekte kullanılır ve bu özellik, [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] örnek ve belgeler genelinde kullanıldığını görürsünüz. Visual Basic, yerel tür çıkarımı yalnızca `Dim` `As` yan tümce olmadan bir deyimi kullanılarak gerçekleştirilir. Aşağıdaki örnekte, `city` kesin bir dize olarak türdedir.  
  
 [!code-vb[VbLINQTypeRels#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#1)]  
  
> [!NOTE]
> Yerel tür çıkarımı yalnızca `Option Infer` olarak `On`ayarlandığında kullanılabilir. Daha fazla bilgi için bkz. [Option Infer deyimleri](../../../../visual-basic/language-reference/statements/option-infer-statement.md).  
  
 Ancak, bir sorguda yerel tür çıkarımı kullanıyor olsanız bile, veri kaynağı, sorgu değişkeni ve sorgu yürütme döngüsünde değişkenler arasında aynı tür ilişkileri vardır. Sorgu yazarken [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] veya belgelerde örnek ve kod örnekleriyle çalışırken, bu tür ilişkilerden temel olarak anlaşılmak yararlıdır.  
  
 Veri kaynağından döndürülen türle eşleşmeyen bir Aralık değişkeni için açık bir tür belirtmeniz gerekebilir. Bir `As` yan tümce kullanarak Aralık değişkeninin türünü belirtebilirsiniz. Ancak, dönüştürme bir [daraltma dönüştürmesi](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) ise ve `Option Strict` olarak `On`ayarlanmışsa bu hata oluşur. Bu nedenle, dönüştürmeyi veri kaynağından alınan değerlerle gerçekleştirmenizi öneririz. <xref:System.Linq.Enumerable.Cast%2A> Yöntemini kullanarak veri kaynağındaki değerleri açık Aralık değişkeni türüne dönüştürebilirsiniz. `Select` Yan tümcesindeki seçili değerleri, Aralık değişkeninin türünden farklı bir açık türe de çevirebilirsiniz. Bu noktaları aşağıdaki kodda gösterilmiştir.  
  
 [!code-vb[VbLINQTypeRels#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#4)]  
  
## <a name="queries-that-return-entire-elements-of-the-source-data"></a>Kaynak verilerin tüm öğelerini döndüren sorgular  
 Aşağıdaki örnek, kaynak verilerden [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] seçilen öğelerin dizisini döndüren bir sorgu işlemini gösterir. Kaynak, `names`bir dize dizisi içerir ve sorgu çıktısı, ı harfiyle başlayan dizeleri içeren bir dizidir.  
  
 [!code-vb[VbLINQTypeRels#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#2)]  
  
 Bu, aşağıdaki koda eşdeğerdir, ancak yazılması çok daha kısadır ve kolaydır. Sorgularda yerel tür çıkarımı, Visual Basic içinde tercih edilen stildir.  
  
 [!code-vb[VbLINQTypeRels#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#3)]  
  
 Aşağıdaki ilişkiler, türlerin örtük olarak mı yoksa açık olarak mı belirlendiği, önceki kod örneklerinde her ikisinde de mevcuttur.  
  
1. Veri kaynağındaki `names`öğelerin türü, sorgusunda,,,, Aralık `name`değişkeninin türüdür.  
  
2. Seçilen `name`nesnenin türü, sorgu `mNames`değişkeninin türünü belirler. Burada `name` bir dize olduğundan sorgu değişkeni Visual Basic IEnumerable (dize) olur.  
  
3. İçinde `mNames` tanımlanan sorgu, `For Each` döngüsünde yürütülür. Döngü, sorguyu yürütmenin sonucunu yineler. Yürütüldüğünde, bir dize dizisi döndürür, Loop yineleme `nm`değişkeni de bir dizedir. `mNames`  
  
## <a name="queries-that-return-one-field-from-selected-elements"></a>Seçili öğelerden bir alan döndüren sorgular  
 Aşağıdaki örnek, veri kaynağından [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] seçilen her bir öğenin yalnızca bir kısmını içeren bir dizi döndüren bir sorgu işlemini gösterir. Sorgu, veri kaynağı olarak `Customer` nesneler koleksiyonunu ve `Name` yalnızca sonuç içindeki özelliği kullanır. Müşteri adı bir dize olduğundan, sorgu çıktı olarak bir dizi dize üretir.  
  
```vb  
' Method GetTable returns a table of Customer objects.  
Dim customers = db.GetTable(Of Customer)()  
Dim custNames = From cust In customers   
                Where cust.City = "London"   
                Select cust.Name  
  
For Each custName In custNames  
    Console.WriteLine(custName)  
Next  
```  
  
 Değişkenler arasındaki ilişkiler, daha basit örnekteki gibi bir örnektir.  
  
1. Veri kaynağındaki `customers`öğelerin türü, sorgusunda,,,, Aralık `cust`değişkeninin türüdür. Bu örnekte, bu tür olur `Customer`.  
  
2. İfade, tüm nesne `Name` yerine her `Customer` nesnenin özelliğini döndürür. `Select` Bir dize olduğundan, sorgu `custNames`değişkeni yeniden IEnumerable ( `Customer`dize) olacaktır, değil. `Name`  
  
3. , Bir dizi dizeyi `custName` `For Each` `custNames` temsil ettiğinden, döngünün yineleme değişkeni, bir dize olmalıdır.  
  
 Yerel tür çıkarımı olmadan, aşağıdaki örnekte gösterildiği gibi önceki örnek yazmak ve anlamak için daha fazla kullanışsız olacaktır.  
  
```vb  
' Method GetTable returns a table of Customer objects.  
 Dim customers As Table(Of Customer) = db.GetTable(Of Customer)()  
 Dim custNames As IEnumerable(Of String) =  
     From cust As Customer In customers   
     Where cust.City = "London"   
     Select cust.Name  
  
 For Each custName As String In custNames  
     Console.WriteLine(custName)  
 Next  
```  
  
## <a name="queries-that-require-anonymous-types"></a>Anonim türler gerektiren sorgular  
 Aşağıdaki örnekte daha karmaşık bir durum gösterilmektedir. Önceki örnekte, tüm değişkenler için türleri açıkça belirtmek uygun değildi. Bu örnekte, olanaksızdır. Tüm `Customer` öğeleri veri kaynağından veya her öğeden tek bir alandan seçmek yerine `Select` , bu sorgudaki yan tümce özgün `Customer` nesnenin iki özelliğini döndürür: `Name` ve `City`. `Select` Yan tümcesine yanıt olarak, derleyici bu iki özelliği içeren anonim bir tür tanımlar. Döngüde`For Each` yürütmenin `nameCityQuery` sonucu, yeni anonim türün örneklerinin bir koleksiyonudur. Anonim türün kullanılabilir bir `nameCityQuery` adı olmadığından, türü veya `custInfo` açıkça belirtemezsiniz. Diğer bir deyişle, bir anonim tür ile, ' `String` de `IEnumerable(Of String)`' ın yerine kullanılacak tür adı yoktur. Daha fazla bilgi için bkz. [anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
```vb  
' Method GetTable returns a table of Customer objects.  
Dim customers = db.GetTable(Of Customer)()  
Dim nameCityQuery = From cust In customers   
                    Where cust.City = "London"   
                    Select cust.Name, cust.City  
  
For Each custInfo In nameCityQuery  
    Console.WriteLine(custInfo.Name)  
Next  
```  
  
 Önceki örnekteki tüm değişkenlerin türlerini belirtmek mümkün olmasa da ilişkiler aynı kalır.  
  
1. Veri kaynağındaki öğelerin türü, sorgudaki aralık değişkeninin türüdür. Bu örnekte, `cust` bir `Customer`örneğidir.  
  
2. İfade anonim bir tür oluşturduğundan, sorgu `nameCityQuery`değişkeni örtülü olarak anonim bir tür olarak yazılmalıdır. `Select` Anonim bir türün kullanılabilir adı yok ve bu nedenle açıkça belirtilemez.  
  
3. `For Each` Döngüdeki yineleme değişkeninin türü 2. adımda oluşturulan anonim türüdür. Türün kullanılabilir bir adı olmadığından, döngü yineleme değişkeninin türü örtük olarak belirtilmelidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic LINQ ile çalışmaya başlama](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Anonim Tipler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Yerel Çıkarım](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Visual Basic LINQ 'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Sorgular](../../../../visual-basic/language-reference/queries/index.md)
