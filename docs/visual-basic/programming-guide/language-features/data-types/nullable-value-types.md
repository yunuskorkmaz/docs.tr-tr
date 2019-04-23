---
title: Boş değer atanabilen değer türleri - Visual Basic
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
ms.openlocfilehash: d17d2ad3fd99c6d563c21ddd646396ccb1c1ca48
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58921318"
---
# <a name="nullable-value-types-visual-basic"></a>Boş Değer Atanabilen Değer Türleri (Visual Basic)

Bazen belirli durumlarda tanımlı bir değer olmayan bir değer türü ile çalışır. Örneğin, bir veritabanı bir alana atanan bir değere sahip değil ve anlamlı atanan bir değere sahip arasında ayırt etmek olabilir. Değer türleri, normal değerlerini veya null değeri olması için genişletilebilir. Böyle bir uzantı olarak adlandırılan bir *boş değer atanabilir tür*.

Her bir boş değer atanabilir tür genel oluşturulan <xref:System.Nullable%601> yapısı. İşle ilgili etkinlikler izleyen bir veritabanı göz önünde bulundurun. Aşağıdaki örnek bir boş değer atanabilir yapıları `Boolean` yazın ve bu tür bir değişken bildirir. Bildirim üç şekilde yazabilirsiniz:

[!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]

Değişken `ridesBusToWork` değerini tutabilen `True`, değerini `False`, ya da hiç değer. İlk varsayılan değeri yok, hangi bilgilerin henüz bu kişinin elde edilmiş değil, bu durumda gelebilir değerdir. Buna karşılık, `False` bilgi edinmiş olması ve kişi çalışmak için veri yolu bulutumuzda değil anlamına gelebilir.

Boş değer atanabilir türler ile değişkenleri ve özellikleri bildirme ve bir dizi öğelerini boş değer atanabilir bir tür bildirebilirsiniz. Parametre olarak boş değer atanabilir tiplerde yordamları bildirebilir ve boş değer atanabilir bir tür döndürebilir bir `Function` yordamı.

Bir dizi gibi bir başvuru türü üzerinde boş değer atanabilir bir tür oluşturulamaz bir `String`, veya bir sınıf. Temel alınan türü bir değer türü olması gerekir. Daha fazla bilgi için [değer türleri ve başvuru türleri](value-types-and-reference-types.md).

## <a name="using-a-nullable-type-variable"></a>Boş değer atanabilir tür değişken kullanma

Boş değer atanabilir bir tür en önemli üyeleri kendi <xref:System.Nullable%601.HasValue%2A> ve <xref:System.Nullable%601.Value%2A> özellikleri. Boş değer atanabilir bir türde bir değişken için <xref:System.Nullable%601.HasValue%2A> değişkeni tanımlı bir değer içerip içermediğini belirtir. Varsa <xref:System.Nullable%601.HasValue%2A> olduğu `True`, değerini okuyabilirsiniz <xref:System.Nullable%601.Value%2A>. Unutmayın hem <xref:System.Nullable%601.HasValue%2A> ve <xref:System.Nullable%601.Value%2A> olan `ReadOnly` özellikleri.

### <a name="default-values"></a>Varsayılan değerler

Null yapılabilir bir tür bir değişken bildirdiğinizde, <xref:System.Nullable%601.HasValue%2A> özelliği varsayılan değerine sahip `False`. Bu, varsayılan olarak, kendi temel değer türünün varsayılan değeri yerine tanımlı hiçbir değer değişkeni olduğu anlamına gelir. Aşağıdaki örnekte, değişken `numberOfChildren` tanımlanmış hiçbir değer olsa bile varsayılan değerine sahip başlangıçta `Integer` türü: 0.

[!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]

Bir null değer tanımsız veya bilinmeyen bir değeri belirtmek kullanışlıdır. Varsa `numberOfChildren` olarak bildirilmiş `Integer`, bilgileri şu anda kullanılabilir değil oluşturabilecek herhangi bir değer olacaktır.

### <a name="storing-values"></a>Değerlerini depolama

Bir değer bir değişken veya özellik boş değer atanabilir bir tür içinde normal şekilde depolayın. Aşağıdaki örnek bir değişkene bir değer atar `numberOfChildren` önceki örnekte bildirilen.

[!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]

Bir değişken veya boş değer atanabilir bir tür özelliği tanımlı bir değer içeriyorsa, atanan bir değere sahip değil, ilk durumuna geri dönmek neden olabilir. Değişken veya özelliğini ayarlayarak bunu `Nothing`aşağıdaki örnekte gösterildiği gibi.

[!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]

> [!NOTE]
> Atayabilseniz `Nothing` boş değer atanabilir bir tür bir değişken için sizin için test edilemez `Nothing` eşittir işareti kullanılarak. Eşittir işareti kullanan karşılaştırma `someVar = Nothing`, her zaman değerlendirilir `Nothing`. Değişkenin sınayabilirsiniz <xref:System.Nullable%601.HasValue%2A> özelliği `False`, veya test kullanarak `Is` veya `IsNot` işleci.

### <a name="retrieving-values"></a>Değerlerini alma

Boş değer atanabilir bir tür değişkeninin değerini almak için önce test etmelisiniz kendi <xref:System.Nullable%601.HasValue%2A> özellik değeri olduğundan emin olmak için. Değeri okunamıyor çalışırsanız, <xref:System.Nullable%601.HasValue%2A> olduğu `False`, Visual Basic oluşturur bir <xref:System.InvalidOperationException> özel durum. Aşağıdaki örnek, değişken okumak için önerilen yol gösterir. `numberOfChildren` önceki örneklerin.

[!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]

## <a name="comparing-nullable-types"></a>Boş değer atanabilir türler karşılaştırma

Boş değer atanabilir olduğunda `Boolean` değişkenleri, Boolean ifadeleri kullanılır, sonucu olabilir `True`, `False`, veya `Nothing`. Gerçekte tablosudur aşağıdaki `And` ve `Or`. Çünkü `b1` ve `b2` artık üç olası değer vardır değerlendirilecek dokuz birleşimleri vardır.

|b1|b2|B1 ve b2|B1 veya b2|
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

Bir Boolean değişkenin veya ifadenin değerini olduğunda `Nothing`, ne olduğunu `true` ya da `false`. Aşağıdaki örnek göz önünde bulundurun.

[!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]

Bu örnekte, `b1 And b2` değerlendiren `Nothing`. Sonuç olarak, `Else` yan tümcesi her yürütüldüğünde `If` bildirimi ve çıktı şu şekildedir:

`Expression is not true`

`Expression is not false`

> [!NOTE]
> `AndAlso` ve `OrElse`, kullanım, değerlendirme, kısa devre oluşturur gerekir değerlendirmek için ikinci işlenenleri ilk olarak değerlendirildiğinde `Nothing`.

## <a name="propagation"></a>Yayma

Birini veya her ikisini işlenenlerin aritmetik, karşılaştırma, kaydırma veya türü işlem, boş değer atanabilir işleminin sonucu ayrıca boş değer atanabilir. Her iki işlenen de olmayan değerlere sahip `Nothing`, ne gibi temel alınan değerlerin işlenenden işlemin gerçekleştirilmesinden boş değer atanabilir bir tür. Aşağıdaki örnekte, değişken `compare1` ve `sum1` örtük olarak belirlenmiş. Bunlar üzerinde fare işaretçisini getirdiğinizde, derleyici boş değer atanabilir türler ikisinin için çıkarsar olduğunu görürsünüz.

[!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]

Bir veya iki işlenenin değerini varsa `Nothing`, sonuç olacaktır `Nothing`.

[!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]

## <a name="using-nullable-types-with-data"></a>Verilerle boş değer atanabilir türleri kullanma

Boş değer atanabilir türler kullanmak için en önemli yerlerden biri bir veritabanı hizmetidir. Tüm veritabanı nesneleri şu anda boş değer atanabilir türler desteklese de, tasarımcı tarafından oluşturulan tablo bağdaştırıcıları yapın. Bkz: [boş değer atanabilir türler için TableAdapter desteği](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.InvalidOperationException>
- <xref:System.Nullable%601.HasValue%2A>
- [Boş Değer Atanabilir Tipleri Kullanma](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)
- [Veri Türleri](index.md)
- [Değer Türleri ve Başvuru Türleri](value-types-and-reference-types.md)
- [Veri Türü Sorunlarını Giderme](troubleshooting-data-types.md)
- [TableAdapter'ları kullanarak veri kümelerini doldurma](/visualstudio/data-tools/fill-datasets-by-using-tableadapters)
- [If İşleci](../../../language-reference/operators/if-operator.md)
- [Yerel Çıkarım](../variables/local-type-inference.md)
- [Is İşleci](../../../language-reference/operators/is-operator.md)
- [IsNot İşleci](../../../language-reference/operators/isnot-operator.md)