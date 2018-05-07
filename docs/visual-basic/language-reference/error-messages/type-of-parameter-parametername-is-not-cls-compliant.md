---
title: Parametrenin türü &#39; &lt;parametername&gt; &#39; CLS uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- vbc40028
- bc40028
helpviewer_keywords:
- BC40028
ms.assetid: dfa1f6f9-bb88-44ad-b85f-149144363d41
ms.openlocfilehash: 13a4e35cd27ed5aa135cec77c4415f223cba70f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="type-of-parameter-39ltparameternamegt39-is-not-cls-compliant"></a>Parametrenin türü &#39; &lt;parametername&gt; &#39; CLS uyumlu değil
Bir yordam olarak işaretlenmiş `<CLSCompliant(True)>` ancak bir parametresi olarak işaretlenmiş bir türüyle bildirir `<CLSCompliant(False)>`işaretlenmemiş veya uyumlu olmayan bir tür olduğundan geçerli değil.  
  
 Uyumlu olması için bir yordam için [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS), onu yalnızca CLS uyumlu türleri kullanmalıdır. Bu parametre türleri, dönüş türü ve tüm yerel değişkenler türleri için geçerlidir.  
  
 Aşağıdaki Visual Basic veri türleri CLS uyumlu değil:  
  
-   [SByte Veri Türü](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [UInteger Veri Türü](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [ULong Veri Türü](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [UShort Veri Türü](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 Uyguladığınızda <xref:System.CLSCompliantAttribute> bir programlama öğesi için ayarladığınız özniteliğin `isCompliant` ya da parametre `True` veya `False` uyumluluğu veya uyumsuzluğu belirtmek için. Bu parametre için varsayılan yok ve bir değer sağlamanız gerekir.  
  
 Geçerli <xref:System.CLSCompliantAttribute> bir öğe olarak uyumsuz olarak değerlendirilir.  
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC40028  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Yordamın bu belirli türde bir parametre almalıdır, kaldırmanız <xref:System.CLSCompliantAttribute>. Yordam, CLS uyumlu olamaz.  
  
-   Yordam CLS ile uyumlu olması gerekiyorsa, bu parametrenin türü en yakın CLS uyumlu türüne değiştirin. Örneğin, içinde yerine, `UInteger` kullanmak olabilir `Integer` 2.147.483.647 yukarıda değer aralığı gerekmiyorsa. Genişletilmiş aralık gerekiyorsa değiştirebilirsiniz `UInteger` ile `Long`.  
  
-   Otomasyon veya COM nesnesi ile arabirim, bazı türleri farklı veri genişliği biçimde olduğunu aklınızda bulundurun [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Örneğin, `int` diğer ortamlarda 16 bit görülür. Bir 16 bit tamsayı böyle bir bileşenin kabul ettiğiniz, olarak bildirme `Short` yerine `Integer` Yönetilen Visual Basic kod.