---
title: Erişilebilirlik düzeyleri- C# başvuru
ms.date: 12/06/2017
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
ms.openlocfilehash: 26fbc2a6d86aead537465c304146630f8bcd3ad4
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713823"
---
# <a name="accessibility-levels-c-reference"></a>Erişilebilirlik Düzeyleri (C# Başvurusu)

Üyeler için aşağıdaki tanımlı erişilebilirlik düzeylerinden birini belirtmek için erişim değiştiricilerini `public`, `protected`, `internal`veya `private`kullanın.  
  
|Tanımlanan erişilebilirlik|Açıklama|  
|----------------------------|-------------|  
|[`public`](public.md)|Erişim kısıtlı değil.|  
|[`protected`](protected.md)|Erişim, kapsayan sınıftan türetilmiş kapsayan sınıf veya türlerle sınırlıdır.|  
|[`internal`](internal.md)|Erişim, geçerli derleme ile sınırlıdır.|  
|[`protected internal`](protected-internal.md)|Erişim, geçerli derleme veya kapsayan sınıftan türetilmiş türlerle sınırlıdır.|  
|[`private`](private.md)|Erişim, kapsayan tür ile sınırlıdır.|  
|[`private protected`](private-protected.md)|Erişim, geçerli derleme içindeki içeren sınıftan türetilmiş kapsayan sınıf veya türlerle sınırlıdır. 7,2 sürümünden C# itibaren kullanılabilir. |  
  
 Bir üye veya tür için yalnızca bir erişim değiştiricisine, `protected internal` veya `private protected` birleşimlerini kullandığınızda izin verilir.  
  
 Ad alanlarında erişim değiştiricilerine izin verilmez. Ad alanlarının erişim kısıtlamaları yoktur.  
  
 Üye bildiriminin gerçekleştiği içeriğe bağlı olarak, yalnızca belirli olarak tanımlanmış erişilebilirlik izin verilir. Üye bildiriminde erişim değiştiricisi belirtilmemişse, varsayılan bir erişilebilirlik kullanılır.  
  
 Diğer türlerde iç içe olmayan en üst düzey türler yalnızca `internal` veya `public` erişilebilirliği olabilir. Bu türler için varsayılan erişilebilirlik `internal`.  
  
 Diğer türlerin üyeleri olan iç içe türler, aşağıdaki tabloda gösterildiği gibi, erişilebilir olarak bildirilebilecek.  
  
|Üyeleri|Varsayılan üye erişilebilirliği|Üyenin izin verilen erişilebilirliği|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|Yok.|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|Yok.|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 İç içe bir türün erişilebilirliği, hem belirtilen üyenin hem de hem de hem de kapsayan türdeki erişilebilirlik etki alanı tarafından belirlenen [erişilebilirlik etki alanına](./accessibility-domain.md)bağlıdır. Ancak, iç içe geçmiş bir türün erişilebilirlik etki alanı, kapsayan türden bu türü aşamaz.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](./index.md)
- [Erişim Değiştiricileri](./access-modifiers.md)
- [Erişilebilirlik Etki Alanı](./accessibility-domain.md)
- [Erişilebilirlik Düzeylerinin Kullanılmasındaki Kısıtlamalar](./restrictions-on-using-accessibility-levels.md)
- [Erişim Değiştiricileri](../../programming-guide/classes-and-structs/access-modifiers.md)
- [public](./public.md)
- [private](./private.md)
- [protected](./protected.md)
- [internal](./internal.md)
