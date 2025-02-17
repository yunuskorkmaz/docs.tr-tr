---
description: 'Hakkında daha fazla bilgi edinin: BC40041: Type <typename> CLS uyumlu değil'
title: <typename> türü CLS uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
ms.openlocfilehash: a1e807dba64f2fce70b0fb39147087d91ca80fbc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675045"
---
# <a name="bc40041-type-typename-is-not-cls-compliant"></a>BC40041: tür \<typename> CLS uyumlu değil

Değişken, özellik veya işlev dönüşü, CLS uyumlu olmayan bir veri türü ile birlikte bildirilmiştir.

 Bir uygulamanın [Dil bağımsızlığı ve Language-Independent bileşenleri](../../../standard/language-independence-and-language-independent-components.md) (CLS) ile uyumlu olması için, yalnızca CLS uyumlu türler kullanması gerekir.

 Aşağıdaki Visual Basic veri türleri CLS uyumlu değildir:

- [SByte Veri Türü](../data-types/sbyte-data-type.md)

- [UInteger Veri Türü](../data-types/uinteger-data-type.md)

- [ULong Veri Türü](../data-types/ulong-data-type.md)

- [UShort Veri Türü](../data-types/ushort-data-type.md)

 **Hata kimliği:** BC40041

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Uygulamanızın CLS uyumlu olması gerekiyorsa, bu öğenin veri türünü en yakın CLS uyumlu türle değiştirin. Örneğin, yerine `UInteger` `Integer` 2.147.483.647 üzerinde değer aralığına ihtiyacınız yoksa, kullanabilirsiniz. Genişletilmiş aralığa ihtiyacınız varsa, `UInteger` ile değiştirebilirsiniz `Long` .

- Uygulamanızın CLS uyumlu olması gerekmiyorsa, herhangi bir değişiklik yapmanız gerekmez. Bununla birlikte, uyumsuzluğun farkında olmanız gerekir.
