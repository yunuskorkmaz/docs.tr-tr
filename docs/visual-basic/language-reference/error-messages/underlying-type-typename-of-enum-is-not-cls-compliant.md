---
title: Enum tarafından temel olarak kullanılan <typename> türü CLS uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- vbc40032
- bc40032
helpviewer_keywords:
- BC40032
ms.assetid: 32bf1949-fd73-456c-a323-bf1ffe1320ed
ms.openlocfilehash: b58759502b9297f9cd5ac89296ab147c40fc89f1
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64913355"
---
# <a name="underlying-type-typename-of-enum-is-not-cls-compliant"></a>Temel alınan türü \<typename > Enum CLS uyumlu değil
Bu sabit listesi değil için belirtilen veri türü parçası [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS). Bu, bileşen içinde bir hata olmadığından [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] ve Visual Basic desteği bu veri türü. Ancak, başka bir bileşen kesinlikle CLS uyumlu bir kod halinde yazılmış bu veri türünü desteklemiyor olabilir. Böyle bir bileşene başarıyla bileşeniniz ile etkileşim kurmak mümkün olmayabilir.  
  
 Aşağıdaki Visual Basic veri türleri CLS uyumlu değildir:  
  
- [SByte Veri Türü](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
- [UInteger Veri Türü](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
- [ULong Veri Türü](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
- [UShort Veri Türü](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini daha fazla bilgi için bkz: [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC40032  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Bileşeniniz yalnızca diğer arabirimleri varsa [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] bileşenler veya yoksa diğer bileşenlerle arabirimi değil, herhangi bir ayarı değiştirmek gerekmez.  
  
- Bir bileşen için yazılmış değil ile arabirim, [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]belgelerinden destekleyip bu veri türü veya belirlemek her iki ile yansıma mümkün olabilir. Aşması durumunda, değişikliği gerekmez.  
  
- Bu veri türü desteklemeyen bir bileşen ile arabirim, en yakın CLS uyumlu türü ile değiştirmeniz gerekir. Örneğin, içinde yerine, `UInteger` kullanmanız mümkün olabilir `Integer` 2.147.483.647 yukarıda değer aralığı gerekmiyorsa. Genişletilmiş aralık gerekiyorsa, değiştirebileceğiniz `UInteger` ile `Long`.  
  
- Otomasyon ve COM nesneleri ile arabirim, bazı türleri farklı veri genişliği kıyasla olduğunu aklınızda bulundurun [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Örneğin, `uint` 16 bit diğer ortamlarda genellikle olur. Bir 16 bit bağımsız değişkeni böyle bir bileşene geçiriyorsanız, olarak bildirin `UShort` yerine `UInteger` Yönetilen Visual Basic kodunuzda.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yansıma (Visual Basic)](../../programming-guide/concepts/reflection.md)
- [Yansıma](../../../framework/reflection-and-codedom/reflection.md)
