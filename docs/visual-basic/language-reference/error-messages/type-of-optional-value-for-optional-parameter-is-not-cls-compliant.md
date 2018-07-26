---
title: İsteğe bağlı parametre için isteğe bağlı değerin türü &lt;parametername&gt; CLS uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- BC40042
- vbc40042
helpviewer_keywords:
- BC40042
ms.assetid: 1d6eae29-4ad3-4434-bde4-a53b6051adf5
ms.openlocfilehash: dd77cd8cbd36f7681e2597d908dd8e55bf249392
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960355"
---
# <a name="type-of-optional-value-for-optional-parameter-ltparameternamegt-is-not-cls-compliant"></a>İsteğe bağlı parametre için isteğe bağlı değerin türü &lt;parametername&gt; CLS uyumlu değil
Bir yordam olarak işaretlenmiş `<CLSCompliant(True)>` bildirir, ancak bir [isteğe bağlı](../../../visual-basic/language-reference/modifiers/optional.md) parametresi ile uyumlu olmayan bir türün varsayılan değeri.  
  
 İle uyumlu olması için bir yordam için [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS), yalnızca CLS uyumlu türler kullanmalıdır. Bu parametre türleri, dönüş türü ve tüm yerel değişkenlerin türleri için geçerlidir. Ayrıca, isteğe bağlı parametrelerinin varsayılan değerleri için geçerlidir.  
  
 Aşağıdaki Visual Basic veri türleri CLS uyumlu değildir:  
  
-   [SByte Veri Türü](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [UInteger Veri Türü](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [ULong Veri Türü](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [UShort Veri Türü](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 Uyguladığınızda <xref:System.CLSCompliantAttribute> özniteliği özniteliğin ayarladığınız bir programlama öğesine `isCompliant` ya da parametre `True` veya `False` uyumluluk veya uyumsuzluk belirtmek için. Bu parametre için varsayılan yok ve bir değer sağlamanız gerekir.  
  
 Geçerli <xref:System.CLSCompliantAttribute> bir öğe için uyumsuz olarak değerlendirilir.  
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini hakkında daha fazla bilgi için bkz: [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC40042  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   İsteğe bağlı parametre isteyenler bu tür bir varsayılan değerine sahip olmalıdır, kaldırmanız <xref:System.CLSCompliantAttribute>. Yordamı, CLS uyumlu olamaz.  
  
-   Yordamı CLS uyumlu olması gerekiyorsa, bu varsayılan değer türü en yakın CLS uyumlu türüne değiştirin. Örneğin, içinde yerine, `UInteger` kullanmanız mümkün olabilir `Integer` 2.147.483.647 yukarıda değer aralığı gerekmiyorsa. Genişletilmiş aralık gerekiyorsa, değiştirebileceğiniz `UInteger` ile `Long`.  
  
-   Otomasyon ve COM nesneleri ile arabirim, bazı türleri farklı veri genişliği kıyasla olduğunu aklınızda bulundurun [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Örneğin, `int` 16 bit diğer ortamlarda genellikle olur. Böyle bir bileşenin bir 16 bitlik tamsayı kabul ediyorsanız, olarak bildirin `Short` yerine `Integer` Yönetilen Visual Basic kodunuzda.