---
title: Nothing anahtar sözcüğü
ms.date: 07/20/2015
f1_keywords:
- Nothing
- vb.Nothing
helpviewer_keywords:
- Nothing keyword [Visual Basic]
- Nothing keyword [Visual Basic], syntax
ms.assetid: 06176e2d-bbf7-4a37-afaa-a86ad21ee99f
ms.openlocfilehash: 3bd4681341a33cc8db4ecbc2b284be243db56549
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344171"
---
# <a name="nothing-keyword-visual-basic"></a>Nothing anahtar sözcüğü (Visual Basic)

Herhangi bir veri türünün varsayılan değerini temsil eder. Başvuru türleri için, varsayılan değer `null` başvurusudur. Değer türleri için, varsayılan değer değer türünün null yapılabilir olup olmamasına bağlıdır.

> [!NOTE]
> Null yapılamayan değer türleri için Visual Basic `Nothing` içindeki `null` farklıdır C#. Visual Basic, null olamayan bir değer türü değişkenini `Nothing`olarak ayarlarsanız, değişken, belirtilen türü için varsayılan değere ayarlanır. ' C#De, `null`null yapılamayan bir değer türü değişkeni atarsanız, derleme zamanı hatası oluşur.

## <a name="remarks"></a>Açıklamalar

`Nothing`, bir veri türünün varsayılan değerini temsil eder. Varsayılan değer, değişkenin bir değer türü veya bir başvuru türü olmasına bağlıdır.

*Değer türünde* bir değişken doğrudan değerini içerir. Değer türleri, tüm sayısal veri türlerini, `Boolean`, `Char`, `Date`, tüm yapıları ve tüm numaralandırmalar içerir. Bir *başvuru türü* değişkeni, bir nesne örneğine bir başvuruyu, bellekteki bir başvuruya depolar. Başvuru türleri sınıflar, diziler, temsilciler ve dizeler içerir. Daha fazla bilgi için bkz. [değer türleri ve başvuru türleri](../programming-guide/language-features/data-types/value-types-and-reference-types.md).

Bir değişken bir değer türünde ise, `Nothing` davranışı değişkenin null yapılabilir bir veri türünde olup olmamasına bağlıdır. Null olabilen bir değer türünü temsil etmek için tür adına bir `?` değiştiricisi ekleyin. Null atanabilir bir değişkene `Nothing` atamak, değeri `null`olarak ayarlar. Daha fazla bilgi ve örnek için bkz. [Nullable değer türleri](../programming-guide/language-features/data-types/nullable-value-types.md).

Bir değişken null değer atanabilir olmayan bir değer türünde ise, `Nothing` atamak, kendisini belirtilen tür için varsayılan değere ayarlar. Bu tür değişken üyeleri içeriyorsa, hepsi varsayılan değerlerine ayarlanır. Aşağıdaki örnek, skalar türler için bunu gösterir.

[!code-vb[VbVbalrKeywords#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class2.vb#7)]

Bir değişken başvuru türünde ise, değişkenine `Nothing` atamak, değişkenin türünün `null` başvurusuna ayarlar. `null` başvuruya ayarlanmış bir değişken herhangi bir nesneyle ilişkili değildir. Aşağıdaki örnek şunu gösterir:

[!code-vb[VbVbalrKeywords#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class3.vb#8)]

Başvuru (veya null yapılabilir değer türü) değişkeninin `null`olup olmadığı denetlenirken `= Nothing` veya `<> Nothing`kullanmayın. `Is Nothing` veya `IsNot Nothing`her zaman kullanın.

Visual Basic dizeler için boş dize `Nothing`eşittir. Bu nedenle, `"" = Nothing` true 'dur.

Aşağıdaki örnek, `Is` ve `IsNot` işleçlerini kullanan karşılaştırmaları gösterir:

[!code-vb[VbVbalrKeywords#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class4.vb#9)]

Bir `As` yan tümcesi kullanmadan bir değişken bildirir ve `Nothing`olarak ayarlarsanız, değişkenin türü `Object`olur. Buna bir örnek `Dim something = Nothing`. `Option Strict` açık olduğunda ve `Option Infer` kapalı olduğunda bu durumda derleme zamanı hatası oluşur.

Bir nesne değişkenine `Nothing` atadığınızda, artık herhangi bir nesne örneğine başvurmayacaktır. Değişken daha önce bir örneğe başvurdıysa, `Nothing` olarak ayarlanması, örneğin kendisini sonlandıramaz. Örnek sonlandırılır ve bununla ilişkili bellek ve sistem kaynakları serbest bırakılır ve yalnızca çöp toplayıcı (GC) kalan etkin bir başvuru olmadığını algılar.

`Nothing`, başlatılmamış bir varyantı veya varolmayan bir veritabanı sütununu temsil eden <xref:System.DBNull> nesnesinden farklıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [Dim Deyimi](./statements/dim-statement.md)
- [Nesne Ömrü: Nesneleri Oluşturma ve Yok Etme](../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Visual Basic ömrü](../programming-guide/language-features/declared-elements/lifetime.md)
- [Is İşleci](./operators/is-operator.md)
- [IsNot İşleci](./operators/isnot-operator.md)
- [Boş Değer Atanabilen Değer Türleri](../programming-guide/language-features/data-types/nullable-value-types.md)
