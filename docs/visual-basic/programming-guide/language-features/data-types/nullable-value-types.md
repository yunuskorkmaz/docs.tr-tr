---
title: Null yapılabilir değer türleri-Visual Basic
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
ms.openlocfilehash: 072496a560775a8f79274f1d44dd389d6ed5b40d
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71351768"
---
# <a name="nullable-value-types-visual-basic"></a>Boş Değer Atanabilen Değer Türleri (Visual Basic)

Bazen belirli koşullarda tanımlı bir değere sahip olmayan bir değer türüyle çalışırsınız. Örneğin, bir veritabanındaki bir alanın anlamlı bir değere sahip olan ve atanan bir değere sahip olmayan bir değeri ayırt etmek zorunda olması gerekebilir. Değer türleri, normal değerlerini veya null değeri alacak şekilde genişletilebilir. Böyle bir uzantıya *null atanabilir tür*denir.

Her null yapılabilir tür, genel <xref:System.Nullable%601> yapısından oluşturulur. İş ile ilgili etkinlikleri izleyen bir veritabanını göz önünde bulundurun. Aşağıdaki örnek, null olabilen `Boolean` türü oluşturur ve bu türde bir değişken bildirir. Bildirimi üç şekilde yazabilirsiniz:

[!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]

@No__t-0 değişkeni, `True` değeri, `False` değeri veya hiçbir değer içermiyor olabilir. İlk varsayılan değeri hiçbir değer değildir, bu durumda bilgilerin bu kişi için henüz alınmamıştır. Buna karşılık, `False`, bilgilerin elde edilildiği ve kişinin veri yolunun çalışmasına izin verebilecek anlamına gelebilir.

Null yapılabilir türler ile değişkenleri ve özellikleri bildirebilirsiniz ve null yapılabilir bir türdeki öğelerle bir dizi bildirebilirsiniz. Null yapılabilir türler içeren yordamları parametreler olarak bildirebilirsiniz ve bir `Function` yordamından null yapılabilir bir tür döndürebilirsiniz.

Dizi, `String` veya sınıf gibi bir başvuru türü üzerinde null yapılabilir bir tür oluşturamazsınız. Temel alınan tür bir değer türü olmalıdır. Daha fazla bilgi için bkz. [değer türleri ve başvuru türleri](value-types-and-reference-types.md).

## <a name="using-a-nullable-type-variable"></a>Null yapılabilir bir tür değişkeni kullanma

Null yapılabilir bir türün en önemli üyeleri <xref:System.Nullable%601.HasValue%2A> ve <xref:System.Nullable%601.Value%2A> özelliklerdir. Null yapılabilir bir tür değişkeni için <xref:System.Nullable%601.HasValue%2A>, değişkenin tanımlanmış bir değer içerip içermediğini söyler. @No__t-0 `True` ise, <xref:System.Nullable%601.Value%2A> ' den değeri okuyabilirsiniz. Hem <xref:System.Nullable%601.HasValue%2A> hem de <xref:System.Nullable%601.Value%2A> ' in `ReadOnly` özellikleri olduğunu unutmayın.

### <a name="default-values"></a>Varsayılan Değerler

Null yapılabilir bir türe sahip bir değişken bildirdiğinizde <xref:System.Nullable%601.HasValue%2A> özelliği varsayılan değer olan `False` ' dir. Bu, varsayılan olarak değişkenin temel alınan değer türünün varsayılan değeri yerine tanımlanmış bir değere sahip olmadığı anlamına gelir. Aşağıdaki örnekte, `Integer` türünün varsayılan değeri 0 olsa da, başlangıçta `numberOfChildren` değişkeni tanımlı bir değere sahip değildir.

[!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]

Null değer, tanımsız veya bilinmeyen bir değeri göstermek için yararlıdır. @No__t-0 `Integer` olarak bildirilirse, bilgilerin şu anda kullanılabilir olmadığını gösterebilen bir değer yoktur.

### <a name="storing-values"></a>Değerler depolanıyor

Bir değeri, genel olarak null yapılabilir bir türdeki bir değişkende veya özellikte depoladığınızda. Aşağıdaki örnek, önceki örnekte belirtilen `numberOfChildren` değişkenine bir değer atar.

[!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]

Null yapılabilir bir türün bir değişkeni veya özelliği tanımlanmış bir değer içeriyorsa, kendisine atanmış bir değere sahip olmadığı ilk durumuna dönüşmesine neden olabilirsiniz. Bu, aşağıdaki örnekte gösterildiği gibi değişkeni veya özelliği `Nothing` olarak ayarlayarak yapabilirsiniz.

[!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]

> [!NOTE]
> @No__t-0 ' ı null olabilen bir tür değişkenine atayabilseniz de, eşittir işaretini kullanarak `Nothing` için test edilemez. Eşittir işaretini kullanan karşılaştırma, `someVar = Nothing`, her zaman `Nothing` olarak değerlendirilir. Değişkenin <xref:System.Nullable%601.HasValue%2A> özelliğini `False` için test edebilir veya `Is` veya `IsNot` işlecini kullanarak test edebilirsiniz.

### <a name="retrieving-values"></a>Değerler alınıyor

Null yapılabilir bir türdeki değişkenin değerini almak için, ilk olarak bir değere sahip olduğunu onaylamak için <xref:System.Nullable%601.HasValue%2A> özelliğini sınamalısınız. @No__t-0 `False` olduğunda değeri okumaya çalışırsanız, Visual Basic <xref:System.InvalidOperationException> özel durumu oluşturur. Aşağıdaki örnek, önceki örneklerin `numberOfChildren` değişkenini okumak için önerilen yöntemi gösterir.

[!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]

## <a name="comparing-nullable-types"></a>Null yapılabilir türleri karşılaştırma

Null yapılabilir `Boolean` değişkenleri Boole ifadelerinde kullanıldığında, sonuç `True`, `False` veya `Nothing` olabilir. @No__t-0 ve `Or` için Truth tablosu aşağıda verilmiştir. @No__t-0 ve `b2` ' in artık üç olası değeri olduğundan, değerlendirmek için dokuz birleşim vardır.

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

Bir Boole değişkeninin veya ifadesinin değeri `Nothing` olduğunda, `true` veya `false` ' dir. Aşağıdaki örneği göz önünde bulundurun.

[!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]

Bu örnekte, `b1 And b2` `Nothing` olarak değerlendirilir. Sonuç olarak, `Else` yan tümcesi her `If` ifadesinde yürütülür ve çıkış aşağıdaki gibidir:

`Expression is not true`

`Expression is not false`

> [!NOTE]
> `AndAlso` ve `OrElse`, kısa devre değerlendirmesi kullanan, ilk @no__t 2 ' yi değerlendirirken ikinci işlenenlerini değerlendirmelidir.

## <a name="propagation"></a>Yayma

Aritmetik, karşılaştırma, kaydırma veya tür işleminin işlenenlerinin bir veya her ikisi null yapılabilir ise, işlemin sonucu da null yapılabilir olur. Her iki işlenen de `Nothing` olmayan değerler içeriyorsa, işlem null yapılabilir bir tür olmadığı gibi, işlenenlerin temel değerlerinde yapılır. Aşağıdaki örnekte `compare1` ve `sum1` değişkenleri örtük olarak türdedir. Fare işaretçisini bunlar üzerinde bekletirseniz, derleyicinin her ikisi için null yapılabilir türler olduğunu görürsünüz.

[!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]

Bir veya her iki işlenen de `Nothing` değerine sahip olursa sonuç `Nothing` olur.

[!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]

## <a name="using-nullable-types-with-data"></a>Null yapılabilir türleri verilerle kullanma

Veritabanı, null yapılabilir türler kullanmak için en önemli yerlerden biridir. Tüm veritabanı nesneleri şu anda null yapılabilir türleri desteklememektedir, ancak tasarımcı tarafından oluşturulan tablo bağdaştırıcıları. [Nullable türler Için TableAdapter desteği](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types)'ne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.InvalidOperationException>
- <xref:System.Nullable%601.HasValue%2A>
- [Veri Türleri](index.md)
- [Değer Türleri ve Başvuru Türleri](value-types-and-reference-types.md)
- [Veri Türü Sorunlarını Giderme](troubleshooting-data-types.md)
- [TableAdapter'ları kullanarak veri kümelerini doldurma](/visualstudio/data-tools/fill-datasets-by-using-tableadapters)
- [If İşleci](../../../language-reference/operators/if-operator.md)
- [Yerel Çıkarım](../variables/local-type-inference.md)
- [Is İşleci](../../../language-reference/operators/is-operator.md)
- [IsNot İşleci](../../../language-reference/operators/isnot-operator.md)
- [Nullable değer türlerini kullanma (C#)](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)
