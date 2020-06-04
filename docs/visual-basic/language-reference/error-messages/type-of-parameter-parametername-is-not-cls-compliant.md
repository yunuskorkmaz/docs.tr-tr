---
title: "'<parametername>' parametresinin türü CLS uyumlu değil"
ms.date: 07/20/2015
f1_keywords:
- vbc40028
- bc40028
helpviewer_keywords:
- BC40028
ms.assetid: dfa1f6f9-bb88-44ad-b85f-149144363d41
ms.openlocfilehash: edbcadf271c4ccafc11e5b64eb103a0290976179
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413020"
---
# <a name="type-of-parameter-parametername-is-not-cls-compliant"></a>'\<parametername>' parametresinin türü CLS uyumlu değil
Bir yordam olarak işaretlenir `<CLSCompliant(True)>` , ancak olarak işaretlenen `<CLSCompliant(False)>` , işaretlenmemiş veya uyumsuz bir tür olduğundan uygun olmayan bir parametre bildirir.  
  
 Bir yordamın [Dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS) ile uyumlu olması için, yalnızca CLS uyumlu türler kullanması gerekir. Bu, parametre türleri, dönüş türü ve tüm yerel değişkenlerinin türleri için geçerlidir.  
  
 Aşağıdaki Visual Basic veri türleri CLS uyumlu değildir:  
  
- [SByte Veri Türü](../data-types/sbyte-data-type.md)  
  
- [UInteger Veri Türü](../data-types/uinteger-data-type.md)  
  
- [ULong Veri Türü](../data-types/ulong-data-type.md)  
  
- [UShort Veri Türü](../data-types/ushort-data-type.md)  
  
 <xref:System.CLSCompliantAttribute>' I bir programlama öğesine uyguladığınızda, ya `isCompliant` da `True` `False` Uyumluluk veya uyumsuzluk olduğunu göstermek için özniteliğin parametresini veya olarak ayarlayın. Bu parametre için varsayılan yoktur ve bir değer belirtmeniz gerekir.  
  
 <xref:System.CLSCompliantAttribute>Öğesini bir öğesine uygulamazsanız, uyumsuz olduğu kabul edilir.  
  
 Bu ileti, varsayılan olarak bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata kimliği:** BC40028  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Yordam bu belirli türden bir parametre almalıdır, öğesini kaldırın <xref:System.CLSCompliantAttribute> . Yordam CLS uyumlu olamaz.  
  
- Yordamın CLS uyumlu olması gerekiyorsa, bu parametrenin türünü, en yakın CLS uyumlu türle değiştirin. Örneğin, yerine `UInteger` `Integer` 2.147.483.647 üzerinde değer aralığına ihtiyacınız yoksa, kullanabilirsiniz. Genişletilmiş aralığa ihtiyacınız varsa, `UInteger` ile değiştirebilirsiniz `Long` .  
  
- Otomasyon veya COM nesneleriyle arabirimsiz değilseniz, bazı türlerin .NET Framework farklı veri genişliklerine sahip olduğunu aklınızda bulundurun. Örneğin, `int` genellikle diğer ortamlarda 16 bittir. Böyle bir bileşenden 16 bit tam sayı kabul ediyorsanız, bunu `Short` `Integer` yönetilen Visual Basic kodunuzda değil olarak bildirin.
