---
title: "İsteğe bağlı bir parametre için isteğe bağlı değer türü &lt;parametername&gt; CLS uyumlu değil"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- BC40042
- vbc40042
helpviewer_keywords:
- BC40042
ms.assetid: 1d6eae29-4ad3-4434-bde4-a53b6051adf5
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 50ea7ce108796d099272c4a909f2fc6c81e9c77c
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="type-of-optional-value-for-optional-parameter-ltparameternamegt-is-not-cls-compliant"></a>İsteğe bağlı bir parametre için isteğe bağlı değer türü &lt;parametername&gt; CLS uyumlu değil
Bir yordam olarak işaretlenmiş `<CLSCompliant(True)>` ancak bildiren bir [isteğe bağlı](../../../visual-basic/language-reference/modifiers/optional.md) parametresi uyumsuz bir türde varsayılan değere sahip.  
  
 Uyumlu olması için bir yordam için [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS), onu yalnızca CLS uyumlu türleri kullanmalıdır. Bu parametre türleri, dönüş türü ve tüm yerel değişkenler türleri için geçerlidir. Ayrıca, isteğe bağlı parametreler varsayılan değerlere uygulanır.  
  
 Aşağıdaki [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] veri türleri, CLS uyumlu değildir:  
  
-   [SByte Veri Türü](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [UInteger Veri Türü](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [ULong Veri Türü](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [UShort Veri Türü](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 Uyguladığınızda <xref:System.CLSCompliantAttribute> özniteliği özniteliğin bir programlama öğesi için ayarladığınız `isCompliant` ya da parametre `True` veya `False` uyumluluğu veya uyumsuzluğu belirtmek için. Bu parametre için varsayılan yok ve bir değer sağlamanız gerekir.  
  
 Geçerli <xref:System.CLSCompliantAttribute> bir öğe olarak uyumsuz olarak değerlendirilir.  
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC40042  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   İsteğe bağlı parametresi bu türdeki bir varsayılan değeri olması gerekiyorsa kaldırma <xref:System.CLSCompliantAttribute>. Yordam, CLS uyumlu olamaz.  
  
-   Yordam CLS ile uyumlu olması gerekiyorsa, bu varsayılan değerin türü en yakın CLS uyumlu türüne değiştirin. Örneğin, içinde yerine, `UInteger` kullanmak olabilir `Integer` 2.147.483.647 yukarıda değer aralığı gerekmiyorsa. Genişletilmiş aralık gerekiyorsa değiştirebilirsiniz `UInteger` ile `Long`.  
  
-   Otomasyon veya COM nesnesi ile arabirim, bazı türleri farklı veri genişliği biçimde olduğunu aklınızda bulundurun [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Örneğin, `int` diğer ortamlarda 16 bit görülür. Bir 16 bit tamsayı böyle bir bileşenin kabul ettiğiniz, olarak bildirme `Short` yerine `Integer` , yönetilen içinde [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kodu.