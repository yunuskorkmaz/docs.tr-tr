---
title: Erişilebilirlik Düzeyleri (C# Başvurusu)
ms.date: 12/06/2017
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
ms.openlocfilehash: 4679fd2564454e7f1ade5cb4813729b65f433012
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44360719"
---
# <a name="accessibility-levels-c-reference"></a>Erişilebilirlik Düzeyleri (C# Başvurusu)

Erişim değiştiricileri kullanma `public`, `protected`, `internal`, veya `private`, üyeleri için aşağıdaki bildirilen erişilebilirliği düzeylerinden birini belirtin.  
  
|Bildirilen erişilebilirliği|Açıklama|  
|----------------------------|-------------|  
|[`public`](public.md)|Erişim sınırlı değildir.|  
|[`protected`](protected.md)|Erişim içeren sınıfı veya içeren sınıfından türetilen türler sınırlıdır.|  
|[`internal`](internal.md)|Geçerli derleme için erişim sınırlıdır.|  
|[`protected internal`](protected-internal.md)|Geçerli derleme veya içeren sınıfından türetilen türler için erişim sınırlıdır.|  
|[`private`](private.md)|Erişimi, kapsadığı tür için sınırlıdır.|  
|[`private protected`](private-protected.md)|Erişim içeren sınıfı veya geçerli derlemedeki içeren sınıfından türetilen türler sınırlıdır. C# 7.2 sonrasında kullanılabilir. |  
  
 Yalnızca bir erişim değiştiricisi izin verilen bir üye veya tür, dışında kullandığınızda `protected internal` veya `private protected` birleşimleri.  
  
 Erişim değiştiricileri ad alanları üzerinde izin verilmez. Ad alanları, hiçbir erişim kısıtlamasına sahip.  
  
 Üye bildirimi oluştuğu bağlama bağlı olarak, yalnızca belirli bildirilen erişilebilirlikleri izin verilir. Hiçbir erişim değiştiricisi üye bildiriminde belirtilmezse, varsayılan erişilebilirlik kullanılır.  
  
 Diğer türleri iç içe değil, en üst düzey türleri dbmigrationsconfiguration `internal` veya `public` erişilebilirlik. Bu tür için varsayılan erişilebilirlik, `internal`.  
  
 Diğer tür üyeleri olan iç içe geçmiş türleri erişilebilirlikleri aşağıdaki tabloda gösterildiği gibi bildirilen.  
  
|Üyeleri|Varsayılan üye erişilebilirliği|İzin verilen, üyenin bildirilen erişilebilirliği|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|Yok.|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|Yok.|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 İç içe türün erişilebilirliği bağlıdır, [erişilebilirlik etki alanı](../../../csharp/language-reference/keywords/accessibility-domain.md), üyenin bildirilen erişilebilirliği ve hemen içeren türün erişilebilirlik etki alanı tarafından belirlenir. Ancak, iç içe türün erişilebilirlik etki alanı, kapsayan türdeki aşamaz.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
- [Erişim Değiştiricileri](../../../csharp/language-reference/keywords/access-modifiers.md)  
- [Erişilebilirlik Etki Alanı](../../../csharp/language-reference/keywords/accessibility-domain.md)  
- [Erişilebilirlik Düzeylerinin Kullanılmasındaki Kısıtlamalar](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)  
- [Erişim Değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
- [public](../../../csharp/language-reference/keywords/public.md)  
- [private](../../../csharp/language-reference/keywords/private.md)  
- [protected](../../../csharp/language-reference/keywords/protected.md)  
- [internal](../../../csharp/language-reference/keywords/internal.md)
