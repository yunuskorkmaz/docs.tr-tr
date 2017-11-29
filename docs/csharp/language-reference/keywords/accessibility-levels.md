---
title: "Erişilebilirlik Düzeyleri (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 77124554d7a0b38414e154e024aceddbfffcfbd4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="accessibility-levels-c-reference"></a>Erişilebilirlik Düzeyleri (C# Başvurusu)
Erişim değiştiricileri kullanmak [ortak](../../../csharp/language-reference/keywords/public.md), [korumalı](../../../csharp/language-reference/keywords/protected.md), [iç](../../../csharp/language-reference/keywords/internal.md), veya [özel](../../../csharp/language-reference/keywords/private.md)bildirilen aşağıdakilerden birini belirtmek için Erişilebilirlik düzeyleri üyeleri için.  
  
|Bildirilen erişilebilirlik|Açıklama|  
|----------------------------|-------------|  
|`public`|Erişim sınırlı değildir.|  
|`protected`|Erişim sınıfı veya içeren sınıfından türetilen türler içeren sınırlıdır.|  
|`internal`|Erişim geçerli derlemeye sınırlıdır.|  
|`protected internal`|Geçerli derleme veya içeren sınıfından türetilen türler için erişim sınırlıdır.|  
|`private`|Erişim içeren türü ile sınırlıdır.|  
|`private protected`|Erişim sınıfı veya geçerli derlemedeki içeren sınıfından türetilmiş türler içeren sınırlıdır.|  
  
 Yalnızca bir erişim değiştiricisi izin verilen bir üye veya türü için dışında kullandığınızda `protected internal` veya `private protected` birleşimleri.  
  
 Erişim değiştiricileri ad alanında bulunan izin verilmez. Ad alanları, hiçbir erişim kısıtlamaları vardır.  
  
 Üye bildirimi gerçekleştiği bağlamı bağlı olarak, yalnızca belirli bildirilen eriþebilirlik izin verilir. Herhangi bir erişim değiştiricisi üye bildiriminde belirtilmezse, varsayılan erişilebilirlik kullanılır.  
  
 Diğer türlerinde içe değil, üst düzey türleri yalnızca olabilir `internal` veya `public` erişilebilirlik. Bu tür için varsayılan erişilebilirlik olduğu `internal`.  
  
 Diğer türleri üyeleri olan, iç içe geçmiş türler eriþebilirlik aşağıdaki tabloda gösterildiği gibi bildirilen.  
  
|Üyeleri|Varsayılan üye erişilebilirlik|Üyenin izin verilen bildirilen erişilebilirlik|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|Yok.|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|Yok.|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 İç içe geçmiş tür erişilebilirliğini bağlıdır, [erişilebilirlik etki alanı](../../../csharp/language-reference/keywords/accessibility-domain.md), üyenin bildirilen erişilebilirlik ve hemen kapsayan tür erişilebilirlik etki alanı tarafından belirlenir. Ancak, iç içe geçmiş tür erişilebilirlik etki alanı, kapsayan tür aşamaz.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Erişim değiştiricileri](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [Erişilebilirlik etki alanı](../../../csharp/language-reference/keywords/accessibility-domain.md)  
 [Erişilebilirlik düzeylerinin kullanılmasındaki kısıtlamalar](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)  
 [Erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [Ortak](../../../csharp/language-reference/keywords/public.md)  
 [Özel](../../../csharp/language-reference/keywords/private.md)  
 [korumalı](../../../csharp/language-reference/keywords/protected.md)  
 [İç](../../../csharp/language-reference/keywords/internal.md)
