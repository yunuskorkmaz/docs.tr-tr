---
title: <typename> türü CLS uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
ms.openlocfilehash: 369516fb12b24981eaecfe467bf421dec279aa01
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875102"
---
# <a name="type-typename-is-not-cls-compliant"></a>\<typename> türü CLS uyumlu değil

Değişken, özellik veya işlev dönüşü, CLS uyumlu olmayan bir veri türü ile birlikte bildirilmiştir.  
  
 Bir uygulamanın [Dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS) ile uyumlu olması için, yalnızca CLS uyumlu türler kullanması gerekir.  
  
 Aşağıdaki Visual Basic veri türleri CLS uyumlu değildir:  
  
- [SByte Veri Türü](../data-types/sbyte-data-type.md)  
  
- [UInteger Veri Türü](../data-types/uinteger-data-type.md)  
  
- [ULong Veri Türü](../data-types/ulong-data-type.md)  
  
- [UShort Veri Türü](../data-types/ushort-data-type.md)  
  
 **Hata kimliği:** BC40041  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Uygulamanızın CLS uyumlu olması gerekiyorsa, bu öğenin veri türünü en yakın CLS uyumlu türle değiştirin. Örneğin, yerine `UInteger` `Integer` 2.147.483.647 üzerinde değer aralığına ihtiyacınız yoksa, kullanabilirsiniz. Genişletilmiş aralığa ihtiyacınız varsa, `UInteger` ile değiştirebilirsiniz `Long` .  
  
- Uygulamanızın CLS uyumlu olması gerekmiyorsa, herhangi bir değişiklik yapmanız gerekmez. Bununla birlikte, uyumsuzluğun farkında olmanız gerekir.
