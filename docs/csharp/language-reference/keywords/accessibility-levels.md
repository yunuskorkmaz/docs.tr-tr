---
title: Erişilebilirlik Düzeyleri (C# Başvurusu)
ms.date: 12/06/2017
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
ms.openlocfilehash: 085e99dd96074bd0f5bfe9d26d4364033f442404
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216697"
---
# <a name="accessibility-levels-c-reference"></a>Erişilebilirlik Düzeyleri (C# Başvurusu)

Erişim değiştiricileri kullanmak `public`, `protected`, `internal`, veya `private`, aşağıdaki bildirilen erişilebilirlik düzeylerinden birini üyeleri için belirtin.  
  
|Bildirilen erişilebilirlik|Açıklama|  
|----------------------------|-------------|  
|[`public`](public.md)|Erişim sınırlı değildir.|  
|[`protected`](protected.md)|Erişim sınıfı veya içeren sınıfından türetilen türler içeren sınırlıdır.|  
|[`internal`](internal.md)|Erişim geçerli derlemeye sınırlıdır.|  
|[`protected internal`](protected-internal.md)|Geçerli derleme veya içeren sınıfından türetilen türler için erişim sınırlıdır.|  
|[`private`](private.md)|Erişim içeren türü ile sınırlıdır.|  
|[`private protected`](private-protected.md)|Erişim sınıfı veya geçerli derlemedeki içeren sınıfından türetilmiş türler içeren sınırlıdır. C# 7.2 itibaren kullanılabilir. |  
  
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
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Erişim Değiştiricileri](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [Erişilebilirlik Etki Alanı](../../../csharp/language-reference/keywords/accessibility-domain.md)  
 [Erişilebilirlik Düzeylerinin Kullanılmasındaki Kısıtlamalar](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)  
 [Erişim Değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [public](../../../csharp/language-reference/keywords/public.md)  
 [private](../../../csharp/language-reference/keywords/private.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 [internal](../../../csharp/language-reference/keywords/internal.md)
