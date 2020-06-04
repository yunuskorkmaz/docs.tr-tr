---
title: "'<procedurename>' işlevinin dönüş türü CLS uyumlu değil"
ms.date: 07/20/2015
f1_keywords:
- bc40027
- vbc40027
helpviewer_keywords:
- BC40027
ms.assetid: 33c088c7-48e7-400c-920e-6d8967e1f3fc
ms.openlocfilehash: 9cc7e25ef1be21ff2f6a71dcb61bc29ec92da30f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400363"
---
# <a name="return-type-of-function-procedurename-is-not-cls-compliant"></a>'\<procedurename>' işlevinin dönüş türü CLS uyumlu değil
Bir `Function` yordam olarak işaretlenir `<CLSCompliant(True)>` , ancak olarak işaretlenen `<CLSCompliant(False)>` , işaretlenmemiş veya uyumsuz bir tür olduğundan uygun olmayan bir tür döndürür.  
  
 Bir yordamın [Dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS) ile uyumlu olması için, yalnızca CLS uyumlu türler kullanması gerekir. Bu, parametre türleri, dönüş türü ve tüm yerel değişkenlerinin türleri için geçerlidir.  
  
 Aşağıdaki Visual Basic veri türleri CLS uyumlu değildir:  
  
- [SByte Veri Türü](../data-types/sbyte-data-type.md)  
  
- [UInteger Veri Türü](../data-types/uinteger-data-type.md)  
  
- [ULong Veri Türü](../data-types/ulong-data-type.md)  
  
- [UShort Veri Türü](../data-types/ushort-data-type.md)  
  
 <xref:System.CLSCompliantAttribute>' I bir programlama öğesine uyguladığınızda, ya `isCompliant` da `True` `False` Uyumluluk veya uyumsuzluk olduğunu göstermek için özniteliğin parametresini veya olarak ayarlayın. Bu parametre için varsayılan yoktur ve bir değer belirtmeniz gerekir.  
  
 <xref:System.CLSCompliantAttribute>Öğesini bir öğesine uygulamazsanız, uyumsuz olduğu kabul edilir.  
  
 Bu ileti, varsayılan olarak bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata kimliği:** BC40027  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- `Function`Yordamın bu belirli türü döndürmesi gerekiyorsa, öğesini kaldırın <xref:System.CLSCompliantAttribute> . Yordam CLS uyumlu olamaz.  
  
- `Function`YORDAMıN CLS uyumlu olması gerekiyorsa, dönüş türünü en yakın CLS uyumlu türle değiştirin. Örneğin, yerine `UInteger` `Integer` 2.147.483.647 üzerinde değer aralığına ihtiyacınız yoksa, kullanabilirsiniz. Genişletilmiş aralığa ihtiyacınız varsa, `UInteger` ile değiştirebilirsiniz `Long` .  
  
- Otomasyon veya COM nesneleriyle arabirimsiz değilseniz, bazı türlerin .NET Framework farklı veri genişliklerine sahip olduğunu aklınızda bulundurun. Örneğin, `int` genellikle diğer ortamlarda 16 bittir. Böyle bir bileşene 16 bit tam sayı döndürüyorsunuz, bunu `Short` `Integer` yönetilen Visual Basic kodunuzda değil olarak bildirin.
