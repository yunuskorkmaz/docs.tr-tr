---
description: 'Daha fazla bilgi için: Nullable değer türleri (Visual Basic)'
title: Boş Değer Atanabilen Değer Türleri
ms.date: 07/20/2015
f1_keywords:
- vb.Nullable
helpviewer_keywords:
- nullable types [Visual Basic]
- '? [Visual Basic]'
- types [Visual Basic], nullable
- nullable types [Visual Basic]
- data types [Visual Basic], nullable
ms.assetid: 9ac3b602-6f96-4e6d-96f7-cd4e81c468a6
ms.openlocfilehash: acc91d98a3ed288a9bf0bcf6abbd3d8a516bd699
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100483891"
---
# <a name="nullable-value-types-visual-basic"></a>Boş Değer Atanabilen Değer Türleri (Visual Basic)

Bazen belirli koşullarda tanımlı bir değere sahip olmayan bir değer türüyle çalışırsınız. Örneğin, bir veritabanındaki bir alanın anlamlı bir değere sahip olan ve atanan bir değere sahip olmayan bir değeri ayırt etmek zorunda olması gerekebilir. Değer türleri, normal değerlerini veya null değeri alacak şekilde genişletilebilir. Böyle bir uzantıya *null atanabilir tür* denir.

Her null yapılabilir değer türü genel <xref:System.Nullable%601> yapıdan oluşturulur. İş ile ilgili etkinlikleri izleyen bir veritabanını göz önünde bulundurun. Aşağıdaki örnek, null yapılabilir bir `Boolean` tür oluşturur ve bu türde bir değişken bildirir. Bildirimi üç şekilde yazabilirsiniz:

[!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]

Değişken, bir değeri `ridesBusToWork` `True` , değeri veya herhangi bir değer içerebilir `False` . İlk varsayılan değeri hiçbir değer değildir, bu durumda bilgilerin bu kişi için henüz alınmamıştır. Buna karşılık, `False` bilgilerin alındığı ve kişinin veri yolunun işe yönelik olmadığı anlamına gelir.

Null yapılabilir değer türleriyle değişkenleri ve özellikleri bildirebilirsiniz ve null olabilen bir değer türünün öğeleriyle bir dizi bildirebilirsiniz. Null yapılabilir değer türleri olan yordamları parametreler olarak bildirebilirsiniz ve bir yordamdan null yapılabilir bir değer türü döndürebilirsiniz `Function` .

Dizi, a veya sınıf gibi bir başvuru türü üzerinde null yapılabilir bir tür oluşturamazsınız `String` . Temel alınan tür bir değer türü olmalıdır. Daha fazla bilgi için bkz. [değer türleri ve başvuru türleri](value-types-and-reference-types.md).

## <a name="using-a-nullable-type-variable"></a>Null yapılabilir bir tür değişkeni kullanma

Null olabilen bir değer türünün en önemli üyeleri, <xref:System.Nullable%601.HasValue%2A> ve <xref:System.Nullable%601.Value%2A> özellikleridir. Null yapılabilir değer türünde bir değişken için, <xref:System.Nullable%601.HasValue%2A> değişkenin tanımlı bir değer içerip içermediğini söyler. <xref:System.Nullable%601.HasValue%2A>İse `True` , öğesinden değeri okuyabilirsiniz <xref:System.Nullable%601.Value%2A> . Hem hem de <xref:System.Nullable%601.HasValue%2A> özelliklerinin olduğunu unutmayın <xref:System.Nullable%601.Value%2A> `ReadOnly` .

### <a name="default-values"></a>Varsayılan Değerler

Null yapılabilir değer türüne sahip bir değişken bildirdiğinizde, <xref:System.Nullable%601.HasValue%2A> özelliği varsayılan değerine sahiptir `False` . Bu, varsayılan olarak değişkenin temel alınan değer türünün varsayılan değeri yerine tanımlanmış bir değere sahip olmadığı anlamına gelir. Aşağıdaki örnekte, `numberOfChildren` türünün varsayılan değeri 0 olsa bile başlangıçta tanımlı bir değere sahip değildir `Integer` .

[!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]

Null değer, tanımsız veya bilinmeyen bir değeri göstermek için yararlıdır. `numberOfChildren`Olarak bildirilirse `Integer` , bilgilerin şu anda kullanılabilir olmadığını gösterebilen bir değer yoktur.

### <a name="storing-values"></a>Değerler depolanıyor

Bir değeri, null olabilen bir değer türünün bir değişkeninde veya özelliğinde normal şekilde depoladığınızda. Aşağıdaki örnek, önceki örnekte belirtilen değişkenine bir değer atar `numberOfChildren` .

[!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]

Null yapılabilir bir değer türünün bir değişkeni veya özelliği tanımlanmış bir değer içeriyorsa, kendisine atanmış bir değere sahip olmadığı ilk durumuna dönüşmesine neden olabilirsiniz. Bunu, `Nothing` Aşağıdaki örnekte gösterildiği gibi değişkeni veya özelliğini olarak ayarlayarak yapabilirsiniz.

[!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]

> [!NOTE]
> `Nothing`Null olabilen bir değer türünün değişkenine atayabilirsiniz, ancak `Nothing` eşittir işaretini kullanarak için test edilemez. Eşittir işaretini kullanan karşılaştırma, `someVar = Nothing` her zaman olarak değerlendirilir `Nothing` . <xref:System.Nullable%601.HasValue%2A>Veya işlecini kullanarak değişkeninin özelliğini test edebilir `False` veya test edebilirsiniz `Is` `IsNot` .

### <a name="retrieving-values"></a>Değerler alınıyor

Null olabilen değer türündeki bir değişkenin değerini almak için, <xref:System.Nullable%601.HasValue%2A> bir değeri olduğunu doğrulamak üzere öncelikle özelliğini sınamalısınız. Olduğunda değeri okumaya çalışırsanız <xref:System.Nullable%601.HasValue%2A> `False` , Visual Basic bir <xref:System.InvalidOperationException> özel durum oluşturur. Aşağıdaki örnek, önceki örneklerin değişkenini okumak için önerilen yöntemi gösterir `numberOfChildren` .

[!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]

## <a name="comparing-nullable-types"></a>Null yapılabilir türleri karşılaştırma

`Boolean`Boolean ifadelerde null yapılabilir değişkenler kullanıldığında, sonuç, `True` veya olabilir `False` `Nothing` . Ve için Truth tablosu aşağıda verilmiştir `And` `Or` . `b1`Ve `b2` Şu anda üç olası değer olduğundan, değerlendirmek için dokuz birleşim vardır.

|B1|B2|B1 ve B2|B1 veya B2|
|--------|--------|---------------|--------------|
|`Nothing`|`Nothing`|`Nothing`|`Nothing`|
|`Nothing`|`True`|`Nothing`|`True`|
|`Nothing`|`False`|`False`|`Nothing`|
|`True`|`Nothing`|`Nothing`|`True`|
|`True`|`True`|`True`|`True`|
|`True`|`False`|`False`|`True`|
|`False`|`Nothing`|`False`|`Nothing`|
|`False`|`True`|`False`|`True`|
|`False`|`False`|`False`|`False`|

Bir Boole değişkeninin veya ifadesinin değeri olduğunda `Nothing` , ne `true` de değildir `false` . Aşağıdaki örneği inceleyin.

[!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]

Bu örnekte, `b1 And b2` olarak değerlendirilir `Nothing` . Sonuç olarak, `Else` yan tümce her `If` ifadede yürütülür ve çıktı aşağıdaki gibidir:

`Expression is not true`

`Expression is not false`

> [!NOTE]
> `AndAlso` ve `OrElse` kısa devre değerlendirmesi kullanan, ilk olarak değerlendirilen ikinci işlenenlerini değerlendirmelidir `Nothing` .

## <a name="propagation"></a>Yayma

Aritmetik, karşılaştırma, kaydırma veya tür işleminin işlenenlerinin bir veya her ikisi null yapılabilir bir değer türü ise, işlemin sonucu aynı zamanda null yapılabilir bir değer türüdür. Her iki işlenen de olmayan değerler içeriyorsa `Nothing` , işlem null yapılabilir bir değer türünde olmadığı gibi, işlenen değerlerinin temel alınarak gerçekleştirilir. Aşağıdaki örnekte, değişkenleri `compare1` ve `sum1` örtülü olarak türdedir. Fare işaretçisini bunlar üzerinde bekletirseniz, derleyicinin her ikisi için null yapılabilir değer türlerini ele alabileceğini görürsünüz.

[!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]

Bir veya iki işlenenin bir değeri varsa `Nothing` , sonuç olur `Nothing` .

[!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]

## <a name="using-nullable-types-with-data"></a>Null yapılabilir türleri verilerle kullanma

Veritabanı, null olabilen değer türlerini kullanmak için en önemli yerlerden biridir. Tüm veritabanı nesneleri şu anda null yapılabilir değer türlerini desteklememektedir, ancak tasarımcı tarafından oluşturulan tablo bağdaştırıcıları. [Nullable türler Için TableAdapter desteği](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types)'ne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.InvalidOperationException>
- <xref:System.Nullable%601.HasValue%2A>
- [Veri türleri](index.md)
- [Değer türleri ve başvuru türleri](value-types-and-reference-types.md)
- [Veri Türü Sorunlarını Giderme](troubleshooting-data-types.md)
- [TableAdapter'ları kullanarak veri kümelerini doldurma](/visualstudio/data-tools/fill-datasets-by-using-tableadapters)
- [If İşleci](../../../language-reference/operators/if-operator.md)
- [Yerel Tür Arabirimi](../variables/local-type-inference.md)
- [Is İşleci](../../../language-reference/operators/is-operator.md)
- [IsNot İşleci](../../../language-reference/operators/isnot-operator.md)
- [Nullable değer türleri (C#)](../../../../csharp/language-reference/builtin-types/nullable-value-types.md)
