---
description: 'Şu konuda daha fazla bilgi edinin: Nothing anahtar sözcüğü (Visual Basic)'
title: Nothing anahtar sözcüğü
ms.date: 07/20/2015
f1_keywords:
- Nothing
- vb.Nothing
helpviewer_keywords:
- Nothing keyword [Visual Basic]
- Nothing keyword [Visual Basic], syntax
ms.assetid: 06176e2d-bbf7-4a37-afaa-a86ad21ee99f
ms.openlocfilehash: c77f39c0a431dd05aabd24a235fb2dc88ea29e69
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99674733"
---
# <a name="nothing-keyword-visual-basic"></a>Nothing anahtar sözcüğü (Visual Basic)

Herhangi bir veri türünün varsayılan değerini temsil eder. Başvuru türleri için varsayılan değer `null` başvurudur. Değer türleri için, varsayılan değer değer türünün null yapılabilir olup olmamasına bağlıdır.

> [!NOTE]
> Null yapılamayan değer türleri için `Nothing` Visual Basic Içinde C# ' den farklıdır `null` . Visual Basic ' de, null olamayan bir değer türü değişkenini olarak ayarlarsanız `Nothing` , değişken, belirtilen türü için varsayılan değere ayarlanır. C# ' de, null olamayan değer türünde bir değişkeni öğesine atarsanız `null` , derleme zamanı hatası oluşur.

## <a name="remarks"></a>Açıklamalar

`Nothing` bir veri türünün varsayılan değerini temsil eder. Varsayılan değer, değişkenin bir değer türü veya bir başvuru türü olmasına bağlıdır.

*Değer türünde* bir değişken doğrudan değerini içerir. Değer türleri, tüm sayısal veri türlerini,,,, `Boolean` `Char` `Date` tüm yapıları ve tüm numaralandırmalar içerir. Bir *başvuru türü* değişkeni, bir nesne örneğine bir başvuruyu, bellekteki bir başvuruya depolar. Başvuru türleri sınıflar, diziler, temsilciler ve dizeler içerir. Daha fazla bilgi için bkz. [değer türleri ve başvuru türleri](../programming-guide/language-features/data-types/value-types-and-reference-types.md).

Bir değişken bir değer türünde ise, öğesinin davranışı `Nothing` değişkenin null yapılabilir bir veri türünde olup olmamasına bağlıdır. Null olabilen bir değer türünü temsil etmek için `?` tür adına bir değiştirici ekleyin. `Nothing`Null atanabilir bir değişkene atama, değerini olarak ayarlar `null` . Daha fazla bilgi ve örnek için bkz. [Nullable değer türleri](../programming-guide/language-features/data-types/nullable-value-types.md).

Bir değişken null değer atanabilir olmayan bir değer türünde ise, bu değere atama, `Nothing` kendisini belirtilen tür için varsayılan değere ayarlar. Bu tür değişken üyeleri içeriyorsa, hepsi varsayılan değerlerine ayarlanır. Aşağıdaki örnek, skalar türler için bunu gösterir.

[!code-vb[VbVbalrKeywords#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class2.vb#7)]

Bir değişken başvuru türünde ise değişkenine atama, `Nothing` `null` değişkenin türünün bir başvurusuna ayarlanır. Başvuruya ayarlanmış bir değişken `null` herhangi bir nesneyle ilişkilendirilmemiş. Aşağıdaki örnek şunu gösterir:

[!code-vb[VbVbalrKeywords#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class3.vb#8)]

Başvuru (veya null yapılabilir değer türü) değişkeninin olup olmadığı denetlenirken `null` , `= Nothing` veya kullanmayın `<> Nothing` . Her zaman `Is Nothing` veya kullanın `IsNot Nothing` .

Visual Basic dizeler için boş dize eşittir `Nothing` . Bu nedenle, `"" = Nothing` doğru.

Aşağıdaki örnek, ve işleçlerini kullanan karşılaştırmaları gösterir `Is` `IsNot` :

[!code-vb[VbVbalrKeywords#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class4.vb#9)]

Bir yan tümce kullanmadan bir değişken bildirir `As` ve öğesini olarak ayarlarsanız `Nothing` , değişkenin türü vardır `Object` . Buna bir örnektir `Dim something = Nothing` . Bu durumda açık ve kapalı olduğunda derleme zamanı hatası oluşur `Option Strict` `Option Infer` .

`Nothing`Bir nesne değişkenine atadığınızda, artık herhangi bir nesne örneğine başvurmayacaktır. Değişken daha önce bir örneğe başvurdıysa, `Nothing` örneği kendisini sonlandıramaz. Örnek sonlandırılır ve bununla ilişkili bellek ve sistem kaynakları serbest bırakılır ve yalnızca çöp toplayıcı (GC) kalan etkin bir başvuru olmadığını algılar.

`Nothing`<xref:System.DBNull>başlatılmamış bir varyantı veya varolmayan bir veritabanı sütununu temsil eden nesnesinden farklıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [Dim Deyimi](./statements/dim-statement.md)
- [Nesne Ömrü: Nesneleri Oluşturma ve Yok Etme](../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Visual Basic'de Ömür](../programming-guide/language-features/declared-elements/lifetime.md)
- [Is İşleci](./operators/is-operator.md)
- [IsNot İşleci](./operators/isnot-operator.md)
- [Null yapılabilir değer türleri](../programming-guide/language-features/data-types/nullable-value-types.md)
