---
title: Erişilebilirlik Düzeyleri - C# Referans
ms.date: 12/06/2017
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
ms.openlocfilehash: 26fbc2a6d86aead537465c304146630f8bcd3ad4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713823"
---
# <a name="accessibility-levels-c-reference"></a>Erişilebilirlik Düzeyleri (C# Başvurusu)

Üyeler için aşağıdaki bildirilen `public` `protected`erişilebilirlik düzeylerinden birini belirtmek için erişim değiştiriciler, , , `internal`, veya `private`, kullanın.  
  
|Bildirilen erişilebilirlik|Anlamı|  
|----------------------------|-------------|  
|[`public`](public.md)|Erişim sınırlı değildir.|  
|[`protected`](protected.md)|Erişim, içeren sınıfveya içeren sınıftan türetilen türlerle sınırlıdır.|  
|[`internal`](internal.md)|Erişim geçerli derleme ile sınırlıdır.|  
|[`protected internal`](protected-internal.md)|Erişim, geçerli derleme yle veya içeren sınıftan türetilen türlerle sınırlıdır.|  
|[`private`](private.md)|Erişim, içeren türle sınırlıdır.|  
|[`private protected`](private-protected.md)|Erişim, geçerli derleme içindeki içeren sınıftan türetilen sınıf veya türlerle sınırlıdır. C# 7.2'den beri mevcuttur. |  
  
 Bir üye veya tür için, bir üye `protected internal` veya `private protected` kombinasyonları kullandığınız zamanlar dışında yalnızca bir erişim değiştiricisine izin verilir.  
  
 Ad alanlarında erişim değiştiricilere izin verilmez. Ad alanlarının erişim kısıtlaması yoktur.  
  
 Üye bildiriminin gerçekleştiği içeriğe bağlı olarak, yalnızca belirli bildirilen erişimlere izin verilir. Üye bildiriminde erişim değiştirici belirtilmemişse, varsayılan erişilebilirlik kullanılır.  
  
 Diğer türlerde iç içe olmayan üst düzey türler `internal` yalnızca `public` erişebilirveya erişilebilirolabilir. Bu türler için varsayılan erişilebilirlik. `internal`  
  
 Diğer türlerin üyesi olan iç içe geçen türler, aşağıdaki tabloda belirtildiği gibi erişilebilirliklerini bildirmiş olabilir.  
  
|Üyeleri|Varsayılan üye erişilebilirliği|Üyenin bildirilen erişilebilirliğine izin verilen|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|None|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|None|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 İç içe geçen bir türün [erişilebilirliği,](./accessibility-domain.md)hem üyenin bildirilen erişilebilirliği hem de hemen içeren türün erişilebilirlik etki alanı tarafından belirlenen erişilebilirlik etki alanına bağlıdır. Ancak, iç içe bir türün erişilebilirlik etki alanı, içeren türü aşamaz.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](./index.md)
- [Erişim Değiştiricileri](./access-modifiers.md)
- [Erişilebilirlik Etki Alanı](./accessibility-domain.md)
- [Erişilebilirlik Düzeylerinin Kullanılmasındaki Kısıtlamalar](./restrictions-on-using-accessibility-levels.md)
- [Erişim Değiştiricileri](../../programming-guide/classes-and-structs/access-modifiers.md)
- [Kamu](./public.md)
- [Özel](./private.md)
- [protected](./protected.md)
- [Iç](./internal.md)
