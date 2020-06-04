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
ms.openlocfilehash: 24a27ba41f5ac889f2f2725a2852368a4292a6fb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404466"
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
İsteğe bağlı. Bkz. [öznitelik listesi](attribute-list.md).

`accessmodifier`  
İsteğe bağlı. Aşağıdakilerden biri olabilir:

- [Geneldir](../modifiers/public.md)

- [Dost](../modifiers/friend.md)

[Visual Basic erişim düzeylerine](../../programming-guide/language-features/declared-elements/access-levels.md)bakın.

`name`  
Gereklidir. Bu modülün adı. Bkz. [tanımlanmış öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).

`statements`  
İsteğe bağlı. Değişkenleri, özellikleri, olayları, yordamları ve bu modülün iç içe geçmiş türlerini tanımlayan deyimler.

`End Module`  
Tanımı sonlandırır `Module` .

## <a name="remarks"></a>Açıklamalar

Bir `Module` ifade, ad alanı genelinde kullanılabilir bir başvuru türü tanımlar. *Modül* (bazen *Standart Modül*olarak adlandırılır), bir sınıfa benzer ancak bazı önemli ayrımlarla benzerdir. Her modülün tam olarak bir örneği vardır ve oluşturulması veya bir değişkene atanması gerekmez. Modüller devralmayı veya uygulama arabirimlerini desteklemez. Bir modülün bir sınıfın veya yapının olduğu anlamda bir *tür* olmadığına dikkat edin; bir modül veri türüne sahip olacak bir programlama öğesi bildiremezsiniz.

`Module`Yalnızca ad alanı düzeyinde kullanabilirsiniz. Bu, bir modülün *bildirim bağlamının* bir kaynak dosya veya ad alanı olması ve bir sınıf, yapı, modül, arabirim, yordam veya blok olamayacağı anlamına gelir. Bir modülün başka bir modül içinde veya herhangi bir türde iç içe geçirilemez. Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).

Bir modül, programınız ile aynı yaşam süresine sahiptir. Üyeleri tümü olduğundan `Shared` , ayrıca yaşam sürelerinin programa eşit olması gerekir.

Modüller varsayılan olarak [arkadaş](../modifiers/friend.md) erişimine sahiptir. Erişim değiştiricilerini kullanarak erişim düzeylerini ayarlayabilirsiniz. Daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](../../programming-guide/language-features/declared-elements/access-levels.md).

Modülün tüm üyeleri örtük olarak alınır `Shared` .

## <a name="classes-and-modules"></a>Sınıflar ve modüller

Bu öğelerin birçok benzerlikleri vardır ancak bazı önemli farklılıklar da vardır.

- **Terminolojiyi.** Önceki Visual Basic sürümleri iki tür modül tanır: *sınıf modülleri* (. CLS dosyaları) ve *Standart modüller* (. bas dosyaları). Geçerli sürüm, sırasıyla bu *sınıfları* ve *modülleri*çağırır.

- **Paylaşılan Üyeler.** Bir sınıfın bir üyesinin paylaşılan bir veya örnek üye olup olmadığını kontrol edebilirsiniz.

- **Nesne yönü.** Sınıflar nesne yönelimlidir, ancak modüller değildir. Bu nedenle, yalnızca sınıflar nesne olarak oluşturulabilir. Daha fazla bilgi için bkz. [nesneler ve sınıflar](../../programming-guide/language-features/objects-and-classes/index.md).

## <a name="rules"></a>Kurallar

- **İlerine.** Tüm modül üyeleri örtülü olarak [paylaşılır](../modifiers/shared.md). `Shared`Bir üyeyi bildirirken anahtar sözcüğünü kullanamaz ve herhangi bir üyenin paylaşılan durumunu değiştiremezsiniz.

- **Devralmayı.** Modül, tüm modüllerin devraldığı dışındaki herhangi bir türden devralınabilir <xref:System.Object> . Özellikle, bir modül diğerinden devralınabilir.

  ' I belirtmek için de, bir modül tanımında [Inherits ifadesini](inherits-statement.md) kullanamazsınız <xref:System.Object> .

- **Varsayılan özellik.** Modülde herhangi bir varsayılan özellik tanımlayamazsınız. Daha fazla bilgi için bkz. [Default](../modifiers/default.md).

## <a name="behavior"></a>Davranış

- **Erişim düzeyi.** Bir modül içinde, her üyeyi kendi erişim düzeyiyle bildirebilirsiniz. Modül üyeleri varsayılan olarak [özel](../modifiers/private.md) erişim için varsayılan olarak, değişkenler ve sabitler hariç [genel](../modifiers/public.md) erişime açıktır. Bir modülün üyelerinden birine göre daha kısıtlı erişimi olduğunda, belirtilen modül erişim düzeyi öncelik kazanır.

- **Kapsam.** Modül, ad alanının tamamında kapsam içinde yer alan bir modüldür.

  Her modül üyesinin kapsamı tüm modüldür. Tüm üyelerin *tür promosyonu*olduğuna dikkat edin ve bu, kapsamının modülü içeren ad alanına yükseltilmesine neden olur. Daha fazla bilgi için bkz. [yükseltme türü](../../programming-guide/language-features/declared-elements/type-promotion.md).

- **Yeter.** Bir projede birden fazla modülünüz olabilir ve aynı ada sahip üyeleri iki veya daha fazla modülle bildirebilirsiniz. Bununla birlikte, başvurunun bu modülün dışından olması durumunda, ilgili modül adı ile böyle bir üyeye yönelik herhangi bir başvuruyu nitelemeniz gerekir. Daha fazla bilgi için bkz. [bildirilmemiş öğelere başvurular](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).

## <a name="example"></a>Örnek

[!code-vb[VbVbalrStatements#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#69)]

## <a name="see-also"></a>Ayrıca bkz.

- [Class Deyimi](class-statement.md)
- [Namespace Deyimi](namespace-statement.md)
- [Structure Yapısı](structure-statement.md)
- [Interface Deyimi](interface-statement.md)
- [Property Deyimi](property-statement.md)
- [Tür Yükseltme](../../programming-guide/language-features/declared-elements/type-promotion.md)
