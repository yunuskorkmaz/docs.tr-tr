---
title: Sorgu İşlemlerinde Tür İlişkileri
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
ms.openlocfilehash: 73a287541ddf115510bf6ab5c830eafac370cc3a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406735"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a>LINQ Sorgu İşlemlerinde Tür İlişkileri (Visual Basic)

Dil ile tümleşik sorgu (LINQ) sorgu işlemlerinde kullanılan değişkenler kesin olarak türdedir ve birbirleriyle uyumlu olmalıdır. Güçlü yazma, veri kaynağında, sorgunun kendisinde ve sorgu yürütmesinde kullanılır. Aşağıdaki çizimde, bir LINQ sorgusunu tanımlamak için kullanılan terimler tanımlanmaktadır. Bir sorgunun kısımları hakkında daha fazla bilgi için bkz. [temel sorgu işlemleri (Visual Basic)](basic-query-operations.md).

![Öğeleri vurgulanmış bir sözde kod sorgusunu gösteren ekran görüntüsü.](./media/type-relationships-in-query-operations/linq-query-description-terms.png)

Sorgudaki aralık değişkeninin türü, veri kaynağındaki öğelerin türüyle uyumlu olmalıdır. Sorgu değişkeninin türü, yan tümcesinde tanımlanan dizi öğesiyle uyumlu olmalıdır `Select` . Son olarak, dizi öğelerinin türü sorguyu yürüten ifadede kullanılan döngü denetimi değişkeninin türüyle uyumlu olmalıdır `For Each` . Bu güçlü yazma, derleme zamanında tür hatalarının tanımlanmasını kolaylaştırır.

Visual Basic, *örtülü yazma*olarak da bilinen yerel tür çıkarımı uygulayarak güçlü yazma kullanışlı hale getirir. Bu özellik önceki örnekte kullanılır ve LINQ örnekleri ve belgelerinin tamamında kullanıldığını görürsünüz. Visual Basic, yerel tür çıkarımı yalnızca `Dim` yan tümce olmadan bir deyimi kullanılarak gerçekleştirilir `As` . Aşağıdaki örnekte, `city` kesin bir dize olarak türdedir.

[!code-vb[VbLINQTypeRels#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#1)]

> [!NOTE]
> Yerel tür çıkarımı yalnızca `Option Infer` olarak ayarlandığında kullanılabilir `On` . Daha fazla bilgi için bkz. [Option Infer deyimleri](../../../language-reference/statements/option-infer-statement.md).

Ancak, bir sorguda yerel tür çıkarımı kullanıyor olsanız bile, veri kaynağı, sorgu değişkeni ve sorgu yürütme döngüsünde değişkenler arasında aynı tür ilişkileri vardır. LINQ sorguları yazarken veya belgelerde örnek ve kod örnekleriyle çalışırken, bu tür ilişkilerden temel olarak anlaşılmak yararlıdır.

Veri kaynağından döndürülen türle eşleşmeyen bir Aralık değişkeni için açık bir tür belirtmeniz gerekebilir. Bir yan tümce kullanarak Aralık değişkeninin türünü belirtebilirsiniz `As` . Ancak, dönüştürme bir [daraltma dönüştürmesi](../../language-features/data-types/widening-and-narrowing-conversions.md) ise ve olarak ayarlanmışsa bu hata oluşur `Option Strict` `On` . Bu nedenle, dönüştürmeyi veri kaynağından alınan değerlerle gerçekleştirmenizi öneririz. Yöntemini kullanarak veri kaynağındaki değerleri açık Aralık değişkeni türüne dönüştürebilirsiniz <xref:System.Linq.Enumerable.Cast%2A> . Yan tümcesindeki seçili değerleri, `Select` Aralık değişkeninin türünden farklı bir açık türe de çevirebilirsiniz. Bu noktaları aşağıdaki kodda gösterilmiştir.

[!code-vb[VbLINQTypeRels#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#4)]

## <a name="queries-that-return-entire-elements-of-the-source-data"></a>Kaynak verilerin tüm öğelerini döndüren sorgular

Aşağıdaki örnek, kaynak verilerden seçilen öğelerin dizisini döndüren bir LINQ sorgu işlemini gösterir. Kaynak, `names` bir dize dizisi içerir ve sorgu çıktısı, ı harfiyle başlayan dizeleri içeren bir dizidir.

[!code-vb[VbLINQTypeRels#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#2)]

Bu, aşağıdaki koda eşdeğerdir, ancak yazılması çok daha kısadır ve kolaydır. Sorgularda yerel tür çıkarımı, Visual Basic içinde tercih edilen stildir.

[!code-vb[VbLINQTypeRels#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#3)]

Aşağıdaki ilişkiler, türlerin örtük olarak mı yoksa açık olarak mı belirlendiği, önceki kod örneklerinde her ikisinde de mevcuttur.

1. Veri kaynağındaki öğelerin türü, sorgusunda,,,, `names` Aralık değişkeninin türüdür `name` .

2. Seçilen nesnenin türü, `name` sorgu değişkeninin türünü belirler `mNames` . Burada `name` bir dize olduğundan sorgu değişkeni Visual Basic IEnumerable (dize) olur.

3. İçinde tanımlanan sorgu, `mNames` `For Each` döngüsünde yürütülür. Döngü, sorguyu yürütmenin sonucunu yineler. `mNames`Yürütüldüğünde, bir dize dizisi döndürür, Loop yineleme değişkeni `nm` de bir dizedir.

## <a name="queries-that-return-one-field-from-selected-elements"></a>Seçili öğelerden bir alan döndüren sorgular

Aşağıdaki örnek, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] veri kaynağından seçilen her bir öğenin yalnızca bir kısmını içeren bir dizi döndüren bir sorgu işlemini gösterir. Sorgu, `Customer` veri kaynağı olarak nesneler koleksiyonunu ve yalnızca `Name` sonuç içindeki özelliği kullanır. Müşteri adı bir dize olduğundan, sorgu çıktı olarak bir dizi dize üretir.

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

1. Veri kaynağındaki öğelerin türü, sorgusunda,,,, `customers` Aralık değişkeninin türüdür `cust` . Bu örnekte, bu tür olur `Customer` .

2. `Select`İfade, `Name` `Customer` tüm nesne yerine her nesnenin özelliğini döndürür. `Name`Bir dize olduğundan, sorgu değişkeni `custNames` yeniden IEnumerable (dize) olacaktır, değil `Customer` .

3. , `custNames` Bir dizi dizeyi temsil ettiğinden, `For Each` döngünün yineleme değişkeni, `custName` bir dize olmalıdır.

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

Aşağıdaki örnekte daha karmaşık bir durum gösterilmektedir. Önceki örnekte, tüm değişkenler için türleri açıkça belirtmek uygun değildi. Bu örnekte, olanaksızdır. Tüm `Customer` öğeleri veri kaynağından veya her öğeden tek bir alandan seçmek yerine, `Select` Bu sorgudaki yan tümce özgün nesnenin iki özelliğini döndürür `Customer` : `Name` ve `City` . Yan tümcesine yanıt olarak `Select` , derleyici bu iki özelliği içeren anonim bir tür tanımlar. Döngüde yürütmenin sonucu, `nameCityQuery` `For Each` yeni anonim türün örneklerinin bir koleksiyonudur. Anonim türün kullanılabilir bir adı olmadığından, türü `nameCityQuery` veya `custInfo` açıkça belirtemezsiniz. Diğer bir deyişle, bir anonim tür ile, ' de ' ın yerine kullanılacak tür adı yoktur `String` `IEnumerable(Of String)` . Daha fazla bilgi için bkz. [anonim türler](../../language-features/objects-and-classes/anonymous-types.md).

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

1. Veri kaynağındaki öğelerin türü, sorgudaki aralık değişkeninin türüdür. Bu örnekte, `cust` bir örneğidir `Customer` .

2. `Select`İfade anonim bir tür oluşturduğundan, sorgu değişkeni `nameCityQuery` örtülü olarak anonim bir tür olarak yazılmalıdır. Anonim bir türün kullanılabilir adı yok ve bu nedenle açıkça belirtilemez.

3. Döngüdeki yineleme değişkeninin türü `For Each` 2. adımda oluşturulan anonim türüdür. Türün kullanılabilir bir adı olmadığından, döngü yineleme değişkeninin türü örtük olarak belirtilmelidir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'te LINQ'e Başlarken](getting-started-with-linq.md)
- [Anonim Türler](../../language-features/objects-and-classes/anonymous-types.md)
- [Yerel Tür Arabirimi](../../language-features/variables/local-type-inference.md)
- [Visual Basic'de LINQ'e Giriş](../../language-features/linq/introduction-to-linq.md)
- [LINQ](../../language-features/linq/index.md)
- [Sorgular](../../../language-reference/queries/index.md)
