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
ms.openlocfilehash: 6d5d13064cceba10d27901ee95aa8b6731620dbb
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524116"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a>LINQ Sorgu İşlemlerinde Tür İlişkileri (Visual Basic)

@No__t_0 sorgu işlemlerinde kullanılan değişkenler kesin olarak türdedir ve birbirleriyle uyumlu olmalıdır. Güçlü yazma, veri kaynağında, sorgunun kendisinde ve sorgu yürütmesinde kullanılır. Aşağıdaki çizimde, bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgusunu tanımlamak için kullanılan terimler tanımlanmaktadır. Bir sorgunun kısımları hakkında daha fazla bilgi için bkz. [temel sorgu işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).

![Öğeleri vurgulanmış bir sözde kod sorgusunu gösteren ekran görüntüsü.](./media/type-relationships-in-query-operations/linq-query-description-terms.png)

Sorgudaki aralık değişkeninin türü, veri kaynağındaki öğelerin türüyle uyumlu olmalıdır. Sorgu değişkeninin türü, `Select` yan tümcesinde tanımlanan dizi öğesiyle uyumlu olmalıdır. Son olarak, dizi öğelerinin türü sorguyu yürüten `For Each` bildiriminde kullanılan döngü denetimi değişkeninin türüyle uyumlu olmalıdır. Bu güçlü yazma, derleme zamanında tür hatalarının tanımlanmasını kolaylaştırır.

Visual Basic, *örtülü yazma*olarak da bilinen yerel tür çıkarımı uygulayarak güçlü yazma kullanışlı hale getirir. Bu özellik önceki örnekte kullanılır ve [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] örnekleri ve belgeler boyunca bu özelliği kullanır. Visual Basic, yerel tür çıkarımı yalnızca bir `As` yan tümcesi olmadan bir `Dim` deyimi kullanılarak gerçekleştirilir. Aşağıdaki örnekte, `city` kesin bir dize olarak türdedir.

[!code-vb[VbLINQTypeRels#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#1)]

> [!NOTE]
> Yerel tür çıkarımı yalnızca `Option Infer` `On` olarak ayarlandığında kullanılır. Daha fazla bilgi için bkz. [Option Infer deyimleri](../../../../visual-basic/language-reference/statements/option-infer-statement.md).

Ancak, bir sorguda yerel tür çıkarımı kullanıyor olsanız bile, veri kaynağı, sorgu değişkeni ve sorgu yürütme döngüsünde değişkenler arasında aynı tür ilişkileri vardır. @No__t_0 sorguları yazarken veya belgelerde örnek ve kod örnekleriyle çalışırken, bu tür ilişkilerle ilgili temel bilgiye sahip olmanız yararlı olur.

Veri kaynağından döndürülen türle eşleşmeyen bir Aralık değişkeni için açık bir tür belirtmeniz gerekebilir. @No__t_0 yan tümcesini kullanarak Aralık değişkeninin türünü belirtebilirsiniz. Ancak, dönüştürme bir [daraltma dönüştürmedir](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) ve `Option Strict` `On` olarak ayarlanırsa bu hata oluşur. Bu nedenle, dönüştürmeyi veri kaynağından alınan değerlerle gerçekleştirmenizi öneririz. @No__t_0 yöntemini kullanarak veri kaynağındaki değerleri açık Aralık değişkeni türüne dönüştürebilirsiniz. @No__t_0 yan tümcesindeki seçili değerleri, Aralık değişkeninin türünden farklı bir açık türe de çevirebilirsiniz. Bu noktaları aşağıdaki kodda gösterilmiştir.

[!code-vb[VbLINQTypeRels#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#4)]

## <a name="queries-that-return-entire-elements-of-the-source-data"></a>Kaynak verilerin tüm öğelerini döndüren sorgular

Aşağıdaki örnek, kaynak verilerden seçilen bir dizi öğeyi döndüren [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] bir sorgu işlemini gösterir. Kaynak, `names`, bir dize dizisi içerir ve sorgu çıktısı, ı harfiyle başlayan dizeleri içeren bir dizidir.

[!code-vb[VbLINQTypeRels#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#2)]

Bu, aşağıdaki koda eşdeğerdir, ancak yazılması çok daha kısadır ve kolaydır. Sorgularda yerel tür çıkarımı, Visual Basic içinde tercih edilen stildir.

[!code-vb[VbLINQTypeRels#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#3)]

Aşağıdaki ilişkiler, türlerin örtük olarak mı yoksa açık olarak mı belirlendiği, önceki kod örneklerinde her ikisinde de mevcuttur.

1. @No__t_0 veri kaynağındaki öğelerin türü, `name` Aralık değişkeninin türüdür, sorgu.

2. @No__t_0, seçili nesnenin türü, `mNames` sorgu değişkeninin türünü belirler. Burada `name` bir dizedir, bu nedenle sorgu değişkeni Visual Basic IEnumerable (dize) olur.

3. @No__t_0 ' de tanımlanan sorgu `For Each` döngüsünde yürütülür. Döngü, sorguyu yürütmenin sonucunu yineler. @No__t_0, yürütüldüğü zaman bir dize dizisi döndürür, `nm` döngüsü yineleme değişkeni de bir dizedir.

## <a name="queries-that-return-one-field-from-selected-elements"></a>Seçili öğelerden bir alan döndüren sorgular

Aşağıdaki örnek, veri kaynağından seçilen her bir öğenin yalnızca bir kısmını içeren bir dizi döndüren [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] sorgu işlemini gösterir. Sorgu, veri kaynağı olarak bir `Customer` nesneleri koleksiyonu alır ve yalnızca sonuç içindeki `Name` özelliğini projeler. Müşteri adı bir dize olduğundan, sorgu çıktı olarak bir dizi dize üretir.

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

1. @No__t_0 veri kaynağındaki öğelerin türü, `cust` Aralık değişkeninin türüdür, sorgu. Bu örnekte, bu tür `Customer`.

2. @No__t_0 ifade, tüm nesne yerine her bir `Customer` nesnesinin `Name` özelliğini döndürür. @No__t_0 bir dize olduğundan, `custNames` sorgu değişkeni `Customer` değil IEnumerable (dize) olacaktır.

3. @No__t_0 bir dizi dizeyi temsil ettiğinden, `For Each` döngüsünün yineleme değişkeni `custName`, bir dize olmalıdır.

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

Aşağıdaki örnekte daha karmaşık bir durum gösterilmektedir. Önceki örnekte, tüm değişkenler için türleri açıkça belirtmek uygun değildi. Bu örnekte, olanaksızdır. Veri kaynağından tüm `Customer` öğeleri veya her öğeden tek bir alanı seçmek yerine, bu sorgudaki `Select` yan tümce orijinal `Customer` nesnesinin iki özelliğini döndürür: `Name` ve `City`. @No__t_0 yan tümcesine yanıt olarak, derleyici bu iki özelliği içeren anonim bir tür tanımlar. @No__t_1 döngüsünde `nameCityQuery` yürütmenin sonucu, yeni anonim türün örneklerinin bir koleksiyonudur. Anonim türün kullanılabilir bir adı olmadığından, `nameCityQuery` veya `custInfo` türünü açıkça belirtemezsiniz. Yani, anonim bir tür ile `IEnumerable(Of String)` `String` yerine kullanılacak tür adı yoktur. Daha fazla bilgi için bkz. [anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).

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

1. Veri kaynağındaki öğelerin türü, sorgudaki aralık değişkeninin türüdür. Bu örnekte, `cust` bir `Customer` örneğidir.

2. @No__t_0 deyimin anonim bir tür oluşturduğu için, `nameCityQuery` sorgu değişkeni örtük olarak anonim bir tür olarak yazılmalıdır. Anonim bir türün kullanılabilir adı yok ve bu nedenle açıkça belirtilemez.

3. @No__t_0 döngüsünde yineleme değişkeninin türü, adım 2 ' de oluşturulan anonim türüdür. Türün kullanılabilir bir adı olmadığından, döngü yineleme değişkeninin türü örtük olarak belirtilmelidir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic LINQ ile çalışmaya başlama](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Anonim Tipler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Yerel Çıkarım](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Visual Basic LINQ 'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Sorgular](../../../../visual-basic/language-reference/queries/index.md)
