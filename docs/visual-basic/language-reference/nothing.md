---
title: Nothing (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Nothing
- vb.Nothing
helpviewer_keywords:
- Nothing keyword [Visual Basic]
- Nothing keyword [Visual Basic], syntax
ms.assetid: 06176e2d-bbf7-4a37-afaa-a86ad21ee99f
ms.openlocfilehash: 12c88db49dc7723fc269195e7d174bfa822c64d3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963755"
---
# <a name="nothing-visual-basic"></a>Nothing (Visual Basic)
Herhangi bir veri türünün varsayılan değerini temsil eder. Başvuru türleri için varsayılan değer `null` başvurudur. Değer türleri için, varsayılan değer değer türünün null yapılabilir olup olmamasına bağlıdır.  
  
> [!NOTE]
> Null yapılamayan değer türleri `Nothing` için Visual Basic içindeki öğesinden `null` farklıdır. C# Visual Basic ' de, null olamayan bir değer türü değişkenini olarak `Nothing`ayarlarsanız, değişken, belirtilen türü için varsayılan değere ayarlanır. ' C#De, null olamayan değer türünde bir değişkeni öğesine `null`atarsanız, derleme zamanı hatası oluşur.  
  
## <a name="remarks"></a>Açıklamalar  
 `Nothing`bir veri türünün varsayılan değerini temsil eder. Varsayılan değer, değişkenin bir değer türü veya bir başvuru türü olmasına bağlıdır.  
  
 *Değer türünde* bir değişken doğrudan değerini içerir. Değer türleri, tüm sayısal veri türlerini, `Boolean` `Char` `Date`,,, tüm yapıları ve tüm numaralandırmalar içerir. Bir *başvuru türü* değişkeni, bir nesne örneğine bir başvuruyu, bellekteki bir başvuruya depolar. Başvuru türleri sınıflar, diziler, temsilciler ve dizeler içerir. Daha fazla bilgi için bkz. [değer türleri ve başvuru türleri](../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
 Bir değişken bir değer türünde ise, öğesinin `Nothing` davranışı değişkenin null yapılabilir bir veri türünde olup olmamasına bağlıdır. Null olabilen bir değer türünü temsil etmek için tür `?` adına bir değiştirici ekleyin. Null `Nothing` atanabilir bir değişkene atama, değerini olarak `null`ayarlar. Daha fazla bilgi ve örnek için bkz. [Nullable değer türleri](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).  
  
 Bir değişken null değer atanabilir olmayan bir değer türünde ise, bu değere atama `Nothing` , kendisini belirtilen tür için varsayılan değere ayarlar. Bu tür değişken üyeleri içeriyorsa, hepsi varsayılan değerlerine ayarlanır. Aşağıdaki örnek, skalar türler için bunu gösterir.  
  
 [!code-vb[VbVbalrKeywords#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class2.vb#7)]  
  
 Bir değişken başvuru türünde ise değişkenine atama `Nothing` , değişkenin türünün bir `null` başvurusuna ayarlanır. `null` Başvuruya ayarlanmış bir değişken herhangi bir nesneyle ilişkilendirilmemiş. Aşağıdaki örnek bunu gösterir.  
  
 [!code-vb[VbVbalrKeywords#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class3.vb#8)]  
  
 Başvuru (veya null yapılabilir değer türü) değişkeninin `null`olup olmadığı denetlenirken, veya `<> Nothing`kullanmayın `= Nothing` . Her zaman `Is Nothing` veya `IsNot Nothing`kullanın.  
  
 Visual Basic dizeler için boş dize eşittir `Nothing`. Bu nedenle `"" = Nothing` , doğru.  
  
 Aşağıdaki örnek, `Is` ve `IsNot` işleçlerini kullanan karşılaştırmaları gösterir.  
  
 [!code-vb[VbVbalrKeywords#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class4.vb#9)]  
  
 Bir `As` yan tümce kullanmadan bir değişken bildirir ve öğesini olarak `Nothing`ayarlarsanız, `Object`değişkenin türü vardır. Buna bir örnektir `Dim something = Nothing`. Bu durumda açık ve `Option Strict` `Option Infer` kapalı olduğunda derleme zamanı hatası oluşur.  
  
 Bir nesne değişkenine `Nothing` atadığınızda, artık herhangi bir nesne örneğine başvurmayacaktır. Değişken daha önce bir örneğe başvurdıysa, `Nothing` örneği kendisini sonlandıramaz. Örnek sonlandırılır ve bununla ilişkili bellek ve sistem kaynakları serbest bırakılır ve yalnızca çöp toplayıcı (GC) kalan etkin bir başvuru olmadığını algılar.  
  
 `Nothing`Başlatılmamış bir varyantı veya varolmayan bir veritabanı sütununu temsil eden nesnesindenfarklıdır.<xref:System.DBNull>  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dim Deyimi](../../visual-basic/language-reference/statements/dim-statement.md)
- [Nesne ömrü: Nesneleri oluşturma ve yok etme](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Visual Basic ömrü](../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Is İşleci](../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot İşleci](../../visual-basic/language-reference/operators/isnot-operator.md)
- [Boş Değer Atanabilen Değer Türleri](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
