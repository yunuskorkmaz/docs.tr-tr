---
description: 'Hakkında daha fazla bilgi edinin: BC40042: isteğe bağlı parametre için isteğe bağlı değerin türü <parametername> CLS uyumlu değil'
title: <parametername> isteğe bağlı parametresi için isteğe bağlı değerin türü CLS uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- BC40042
- vbc40042
helpviewer_keywords:
- BC40042
ms.assetid: 1d6eae29-4ad3-4434-bde4-a53b6051adf5
ms.openlocfilehash: 44dee07120ebcd99be69257aef6a334f9067cdb3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774869"
---
# <a name="bc40042-type-of-optional-value-for-optional-parameter-parametername-is-not-cls-compliant"></a>BC40042: isteğe bağlı parametre için isteğe bağlı değerin türü \<parametername> CLS uyumlu değil

Bir yordam olarak işaretlenir, `<CLSCompliant(True)>` ancak uyumlu olmayan bir türün varsayılan değerine sahip [isteğe bağlı](../modifiers/optional.md) bir parametre bildirir.

 Bir yordamın [Dil bağımsızlığı ve Language-Independent bileşenleri](../../../standard/language-independence-and-language-independent-components.md) (CLS) ile uyumlu olması için, yalnızca CLS uyumlu türler kullanması gerekir. Bu, parametre türleri, dönüş türü ve tüm yerel değişkenlerinin türleri için geçerlidir. Ayrıca, isteğe bağlı parametrelerin varsayılan değerleri için de geçerlidir.

 Aşağıdaki Visual Basic veri türleri CLS uyumlu değildir:

- [SByte Veri Türü](../data-types/sbyte-data-type.md)

- [UInteger Veri Türü](../data-types/uinteger-data-type.md)

- [ULong Veri Türü](../data-types/ulong-data-type.md)

- [UShort Veri Türü](../data-types/ushort-data-type.md)

 <xref:System.CLSCompliantAttribute>Özniteliği bir programlama öğesine uyguladığınızda, ya `isCompliant` da `True` `False` Uyumluluk veya uyumsuzluk olduğunu belirtmek için özniteliğin parametresini veya olarak ayarlayın. Bu parametre için varsayılan yoktur ve bir değer belirtmeniz gerekir.

 <xref:System.CLSCompliantAttribute>Bir öğesi için uygulamazsanız, uyumsuz olduğu kabul edilir.

 Bu ileti, varsayılan olarak bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).

 **Hata kimliği:** BC40042

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- İsteğe bağlı parametrenin bu belirli türden bir varsayılan değeri olması gerekiyorsa, öğesini kaldırın <xref:System.CLSCompliantAttribute> . Yordam CLS uyumlu olamaz.

- Yordamın CLS uyumlu olması gerekiyorsa, bu varsayılan değerin türünü, en yakın CLS uyumlu türe değiştirin. Örneğin, yerine `UInteger` `Integer` 2.147.483.647 üzerinde değer aralığına ihtiyacınız yoksa, kullanabilirsiniz. Genişletilmiş aralığa ihtiyacınız varsa, `UInteger` ile değiştirebilirsiniz `Long` .

- Otomasyon veya COM nesneleriyle arabirimsiz değilseniz, bazı türlerin .NET Framework farklı veri genişliklerine sahip olduğunu aklınızda bulundurun. Örneğin, `int` genellikle diğer ortamlarda 16 bittir. Böyle bir bileşenden 16 bit tam sayı kabul ediyorsanız, bunu `Short` `Integer` yönetilen Visual Basic kodunuzda değil olarak bildirin.
