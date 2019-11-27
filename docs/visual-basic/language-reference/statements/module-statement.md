---
title: Module Deyimi
ms.date: 07/20/2015
f1_keywords:
- Module
- vb.Module
helpviewer_keywords:
- modules, classes
- modules
- Module statement [Visual Basic]
- modules, declaring
- standard modules
- classes [Visual Basic], vs. modules
- declarations [Visual Basic], modules
ms.assetid: a1243afc-14a5-45df-95d5-51118aeac362
ms.openlocfilehash: 56fc4f9383f1fc4779358ef18a4e5c611d897eda
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348014"
---
# <a name="module-statement"></a>Module Deyimi

Modülün adını bildirir ve modülün içerdiği değişkenlerin, özelliklerin, olayların ve yordamların tanımını tanıtır.

## <a name="syntax"></a>Sözdizimi

```vb
[ <attributelist> ] [ accessmodifier ]  Module name
    [ statements ]
End Module
```

## <a name="parts"></a>Bölümler

`attributelist`  
İsteğe bağlı. Bkz. [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md).

`accessmodifier`  
İsteğe bağlı. Aşağıdakilerden biri olabilir:

- [Public](../../../visual-basic/language-reference/modifiers/public.md)

- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)

[Visual Basic erişim düzeylerine](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)bakın.

`name`  
Gerekli. Bu modülün adı. Bkz. [tanımlanmış öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).

`statements`  
İsteğe bağlı. Değişkenleri, özellikleri, olayları, yordamları ve bu modülün iç içe geçmiş türlerini tanımlayan deyimler.

`End Module`  
`Module` tanımını sonlandırır.

## <a name="remarks"></a>Açıklamalar

`Module` bir ifade, ad alanı genelinde kullanılabilir bir başvuru türü tanımlar. *Modül* (bazen *Standart Modül*olarak adlandırılır), bir sınıfa benzer ancak bazı önemli ayrımlarla benzerdir. Her modülün tam olarak bir örneği vardır ve oluşturulması veya bir değişkene atanması gerekmez. Modüller devralmayı veya uygulama arabirimlerini desteklemez. Bir modülün bir sınıfın veya yapının olduğu anlamda bir *tür* olmadığına dikkat edin; bir modül veri türüne sahip olacak bir programlama öğesi bildiremezsiniz.

`Module` yalnızca ad alanı düzeyinde kullanabilirsiniz. Bu, bir modülün *bildirim bağlamının* bir kaynak dosya veya ad alanı olması ve bir sınıf, yapı, modül, arabirim, yordam veya blok olamayacağı anlamına gelir. Bir modülün başka bir modül içinde veya herhangi bir türde iç içe geçirilemez. Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).

Bir modül, programınız ile aynı yaşam süresine sahiptir. Üyeleri tüm `Shared`olduğundan, ayrıca yaşam sürelerinin programa eşit olması gerekir.

Modüller varsayılan olarak [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md) erişimine sahiptir. Erişim değiştiricilerini kullanarak erişim düzeylerini ayarlayabilirsiniz. Daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

Modülün tüm üyeleri örtülü olarak `Shared`.

## <a name="classes-and-modules"></a>Sınıflar ve modüller

Bu öğelerin birçok benzerlikleri vardır ancak bazı önemli farklılıklar da vardır.

- **Terminolojiyi.** Önceki Visual Basic sürümleri iki tür modül tanır: *sınıf modülleri* (. CLS dosyaları) ve *Standart modüller* (. bas dosyaları). Geçerli sürüm, sırasıyla bu *sınıfları* ve *modülleri*çağırır.

- **Paylaşılan Üyeler.** Bir sınıfın bir üyesinin paylaşılan bir veya örnek üye olup olmadığını kontrol edebilirsiniz.

- **Nesne yönü.** Sınıflar nesne yönelimlidir, ancak modüller değildir. Bu nedenle, yalnızca sınıflar nesne olarak oluşturulabilir. Daha fazla bilgi için bkz. [nesneler ve sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).

## <a name="rules"></a>Kurallar

- **İlerine.** Tüm modül üyeleri örtülü olarak [paylaşılır](../../../visual-basic/language-reference/modifiers/shared.md). Bir üyeyi bildirirken `Shared` anahtar sözcüğünü kullanamazsınız ve herhangi bir üyenin paylaşılan durumunu değiştiremezsiniz.

- **Devralmayı.** Modül, tüm modüllerin devraldığı <xref:System.Object>dışındaki herhangi bir türden devralınabilir. Özellikle, bir modül diğerinden devralınabilir.

  <xref:System.Object>belirtmek için de, bir modül tanımında [Inherits ifadesini](../../../visual-basic/language-reference/statements/inherits-statement.md) kullanamazsınız.

- **Varsayılan özellik.** Modülde herhangi bir varsayılan özellik tanımlayamazsınız. Daha fazla bilgi için bkz. [Default](../../../visual-basic/language-reference/modifiers/default.md).

## <a name="behavior"></a>Davranış

- **Erişim düzeyi.** Bir modül içinde, her üyeyi kendi erişim düzeyiyle bildirebilirsiniz. Modül üyeleri varsayılan olarak [özel](../../../visual-basic/language-reference/modifiers/private.md) erişim için varsayılan olarak, değişkenler ve sabitler hariç [genel](../../../visual-basic/language-reference/modifiers/public.md) erişime açıktır. Bir modülün üyelerinden birine göre daha kısıtlı erişimi olduğunda, belirtilen modül erişim düzeyi öncelik kazanır.

- **Kapsam.** Modül, ad alanının tamamında kapsam içinde yer alan bir modüldür.

  Her modül üyesinin kapsamı tüm modüldür. Tüm üyelerin *tür promosyonu*olduğuna dikkat edin ve bu, kapsamının modülü içeren ad alanına yükseltilmesine neden olur. Daha fazla bilgi için bkz. [yükseltme türü](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).

- **Yeter.** Bir projede birden fazla modülünüz olabilir ve aynı ada sahip üyeleri iki veya daha fazla modülle bildirebilirsiniz. Bununla birlikte, başvurunun bu modülün dışından olması durumunda, ilgili modül adı ile böyle bir üyeye yönelik herhangi bir başvuruyu nitelemeniz gerekir. Daha fazla bilgi için bkz. [bildirilmemiş öğelere başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).

## <a name="example"></a>Örnek

[!code-vb[VbVbalrStatements#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#69)]

## <a name="see-also"></a>Ayrıca bkz.

- [Class Deyimi](../../../visual-basic/language-reference/statements/class-statement.md)
- [Namespace Deyimi](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Structure Deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Interface Deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)
- [Tür Yükseltme](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
