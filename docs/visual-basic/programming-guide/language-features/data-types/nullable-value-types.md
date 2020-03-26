---
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
ms.openlocfilehash: beed8262c50dc68330b8f03aa3d864ed2f8df0d5
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249688"
---
# <a name="nullable-value-types-visual-basic"></a>Boş Değer Atanabilen Değer Türleri (Visual Basic)

Bazen belirli durumlarda tanımlı bir değeri olmayan bir değer türüyle çalışırsınız. Örneğin, veritabanındaki bir alanın anlamlı olan atanmış bir değere sahip olmakla atanmış bir değere sahip olmamak arasında ayrım yapmak gerekebilir. Değer türleri normal değerlerini veya null değerini alacak şekilde genişletilebilir. Böyle bir uzantı *geçersiz*türü olarak adlandırılır.

Her nullable değer türü genel <xref:System.Nullable%601> yapıdan oluşturulur. İşle ilgili etkinlikleri izleyen bir veritabanı düşünün. Aşağıdaki örnek, nullable `Boolean` türü inşa eder ve bu tür bir değişken bildirir. Bildirimi üç şekilde yazabilirsiniz:

[!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]

Değişken, `ridesBusToWork` bir değer , bir `False`değer veya hiç değer tutabilir. `True` İlk varsayılan değeri hiç bir değer değildir, bu durumda bu kişi için bilgi henüz elde edilmemiştir anlamına gelebilir. Buna karşılık, `False` bilgi elde edilmiş ve kişi işe otobüse binmek değil anlamına gelebilir.

Değişkenleri ve özellikleri nullable değer türleri ile bildirebilir ve nullable değer türü öğeleri ile bir dizi bildirebilirsiniz. Nullable değer türleri olan yordamları parametre olarak bildirebilir ve bir `Function` yordamdan nullable değer türü döndürebilirsiniz.

Bir dizi, bir `String`, veya bir sınıf gibi bir başvuru türü üzerinde geçersiz bir tür oluşturamazsınız. Temel türü bir değer türü olmalıdır. Daha fazla bilgi için [Bkz. Değer Türleri ve Başvuru Türleri.](value-types-and-reference-types.md)

## <a name="using-a-nullable-type-variable"></a>Nullable Tip Değişkeni Kullanma

Nullable değer türünün en önemli <xref:System.Nullable%601.HasValue%2A> üyeleri <xref:System.Nullable%601.Value%2A> onun ve özellikleridir. Nullable değer türünden bir <xref:System.Nullable%601.HasValue%2A> değişken için, değişkentanımlı bir değer iyp etmediğini söyler. Ise, <xref:System.Nullable%601.HasValue%2A> değerini <xref:System.Nullable%601.Value%2A> `True` Her ikisinin <xref:System.Nullable%601.Value%2A> `ReadOnly` de <xref:System.Nullable%601.HasValue%2A> ve özelliklerinin olduğunu unutmayın.

### <a name="default-values"></a>Varsayılan Değerler

Nullable değer türüne sahip bir değişken <xref:System.Nullable%601.HasValue%2A> idacattığınızda, özelliği `False`varsayılan değeri . Bu, varsayılan olarak değişkenin temel değer türünün varsayılan değeri yerine tanımlı bir değeri olmadığı anlamına gelir. Aşağıdaki örnekte, `numberOfChildren` `Integer` türün varsayılan değeri 0 olsa bile, değişkenin başlangıçta tanımlı bir değeri yoktur.

[!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]

Null değeri tanımlanmamış veya bilinmeyen bir değeri belirtmek için yararlıdır. Olarak `numberOfChildren` bildirilmiş `Integer`olsaydı, bilgilerin şu anda kullanılmadığını gösteren hiçbir değer olmazdı.

### <a name="storing-values"></a>Değerleri Depolama

Bir değeri, normal bir şekilde geçersiz bir değer türünde veya değişken desiyerinde saklarsınız. Aşağıdaki örnek, önceki örnekte `numberOfChildren` bildirilen değişkene bir değer atar.

[!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]

Geçersiz bir değer türünün değişkeni veya özelliği tanımlı bir değer içeriyorsa, bir değer atanmış olmayan ilk durumuna geri dönülmesine neden olabilirsiniz. Bunu, aşağıdaki örnekte görüldüğü `Nothing`gibi değişkeni veya özelliği , olarak ayarlayarak yaparsınız.

[!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]

> [!NOTE]
> Nullable değer `Nothing` türünden bir değişkene atayabilirsiniz, ancak `Nothing` eşit işareti kullanarak bunu sınayamazsınız. Eşit işareti kullanan karşılaştırma, `someVar = Nothing`her zaman `Nothing`. Değişkenin <xref:System.Nullable%601.HasValue%2A> özelliğini `False`veya testini veya işleci `IsNot` kullanarak test edebilirsiniz. `Is`

### <a name="retrieving-values"></a>Değerleri Alma

Nullable değer türünden bir değişkenin değerini almak için, <xref:System.Nullable%601.HasValue%2A> önce bir değeri olduğunu doğrulamak için özelliğini sınamalısınız. Değeri ne zaman <xref:System.Nullable%601.HasValue%2A> okumaya `False`çalışırsanız, Visual Basic <xref:System.InvalidOperationException> bir özel durum oluşturur. Aşağıdaki örnek, önceki örneklerin değişkenini `numberOfChildren` okumanın önerilen yolunu gösterir.

[!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]

## <a name="comparing-nullable-types"></a>Nullable Türleri Karşılaştırma

Boolean `Boolean` ifadelerinde nullable değişkenler kullanıldığında, sonuç `True`, `False`, `Nothing`veya . Aşağıdaki için gerçek tablo `And` `Or`ve . Çünkü `b1` `b2` ve şimdi üç olası değerleri var, değerlendirmek için dokuz kombinasyonları vardır.

|b1|B2|b1 Ve b2|b1 Veya b2|
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

Bir Boolean değişkeninin veya `Nothing`ifadesinin değeri `true` `false`ne de . Aşağıdaki örneği inceleyin.

[!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]

Bu örnekte, `b1 And b2` '' `Nothing` Sonuç olarak, `Else` yan tümce `If` her deyimde yürütülür ve çıktı aşağıdaki gibidir:

`Expression is not true`

`Expression is not false`

> [!NOTE]
> `AndAlso`ve `OrElse`kısa devre değerlendirmesini kullanan, ikinci operandları değerlendirmek `Nothing`zorundadır.

## <a name="propagation"></a>Yayma

Bir aritmetik, karşılaştırma, kaydırma veya tür işleminin operandlarından biri veya her ikisi geçersiz bir değer türüyse, işlemin sonucu da geçersiz bir değer türüdür. Her iki operands olmayan `Nothing`değerlervarsa, işlem operands temel değerleri üzerinde gerçekleştirilir, sanki ne nullable değer türü idi. Aşağıdaki örnekte, `compare1` değişkenler `sum1` ve örtülü olarak yazılır. Fare işaretçisini üzerlerine dinlendirmek durumunda, derleyicinin her ikisi için de geçersiz değer türlerini çıkardığını görürsünüz.

[!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]

Bir veya her iki operands `Nothing`bir değeri `Nothing`varsa , sonuç olacaktır.

[!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]

## <a name="using-nullable-types-with-data"></a>Verilerle Nullable Türleri Kullanma

Veritabanı, nullable değer türlerini kullanmak için en önemli yerlerden biridir. Tüm veritabanı nesneleri şu anda geçersiz değer türlerini desteklemez, ancak tasarımcı tarafından oluşturulan tablo bağdaştırıcıları destekler. [Nullable türleri için TableAdapter desteğine](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.InvalidOperationException>
- <xref:System.Nullable%601.HasValue%2A>
- [Veri Türleri](index.md)
- [Değer Türleri ve Başvuru Türleri](value-types-and-reference-types.md)
- [Veri Türleri Sorunlarını Giderme](troubleshooting-data-types.md)
- [TableAdapter'ları kullanarak veri kümelerini doldurma](/visualstudio/data-tools/fill-datasets-by-using-tableadapters)
- [If İşleci](../../../language-reference/operators/if-operator.md)
- [Yerel Tür Arabirimi](../variables/local-type-inference.md)
- [Is İşleci](../../../language-reference/operators/is-operator.md)
- [IsNot İşleci](../../../language-reference/operators/isnot-operator.md)
- [Nullable Değer Türleri (C#)](../../../../csharp/language-reference/builtin-types/nullable-value-types.md)
