---
title: <typename> türü CLS uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
ms.openlocfilehash: 4adbf38e448dad7634a4336d20b3fce8702be1db
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664279"
---
# <a name="type-typename-is-not-cls-compliant"></a>Tür \<typename > CLS uyumlu değil
Bir değişken, özellik veya işlev dönüş CLS uyumlu olmayan bir veri türü ile bildirilir.  
  
 Bir uygulama ile uyumlu olması için [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS), yalnızca CLS uyumlu türler kullanmalıdır.  
  
 Aşağıdaki Visual Basic veri türleri CLS uyumlu değildir:  
  
- [SByte Veri Türü](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
- [UInteger Veri Türü](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
- [ULong Veri Türü](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
- [UShort Veri Türü](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 **Hata Kimliği:** BC40041  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Uygulamanızı CLS uyumlu olması gerekiyorsa, bu öğe veri türü en yakın CLS uyumlu türüne değiştirin. Örneğin, içinde yerine, `UInteger` kullanmanız mümkün olabilir `Integer` 2.147.483.647 yukarıda değer aralığı gerekmiyorsa. Genişletilmiş aralık gerekiyorsa, değiştirebileceğiniz `UInteger` ile `Long`.  
  
- Uygulamanızı CLS uyumlu olması gerekmez, herhangi bir ayarı değiştirmek gerekmez. Ancak, uyumsuzluk farkında olmalıdır.