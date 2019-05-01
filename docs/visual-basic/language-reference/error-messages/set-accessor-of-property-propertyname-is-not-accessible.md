---
title: "'<propertyname>' özelliğinin 'Set' erişimcisine erişilemiyor"
ms.date: 07/20/2015
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
ms.openlocfilehash: 3bc50d6762998ca5d8f445d84c8b698c9f46436f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055153"
---
# <a name="set-accessor-of-property-propertyname-is-not-accessible"></a>'Set' erişimcisi'özelliğinin '\<propertyname >' erişilebilir değil
Özelliğin erişimi olmadığında bir özellik değerini depolamak bir deyim çalışır `Set` yordamı.  
  
 Varsa [bildirimine](../../../visual-basic/language-reference/statements/set-statement.md) ile daha kısıtlayıcı bir erişim düzeyi daha işaretlenmiş kendi [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md), aşağıdaki durumlarda özellik değerini ayarlama girişimi başarısız olabilir:  
  
- `Set` Deyimi işaretlenmiş [özel](../../../visual-basic/language-reference/modifiers/private.md) ve çağrıldığı koda bir sınıf veya yapı özelliği tanımlanır dışında.  
  
- `Set` Deyimi işaretlenmiş [korumalı](../../../visual-basic/language-reference/modifiers/protected.md) ve çağıran kod değil, sınıf veya yapı özelliği tanımlanır, ya da türetilen bir sınıfta değil.  
  
- `Set` Deyimi işaretlenmiş [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md) ve çağıran kod özelliği tanımlanır derlemede değil.  
  
 **Hata Kimliği:** BC31102  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Özellik tanımlama kaynak kodu denetim varsa bildirmeyi göz önünde bulundurun `Set` yordamla aynı erişim düzeyi özelliği olarak.  
  
- Özellik tanımlama kaynak kodu denetim sahibi olmadığınız ya da kısıtlamanız gerekir `Set` yordamı erişim düzeyi özelliği kendisini deneyin birden fazla özellik değeri, daha iyi erişimi olan kod bir bölgeye ayarlar deyimi taşımak özellik.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özellik Yordamları](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [Nasıl yapılır: Bir özelliği karışık erişim düzeyleriyle bildirme](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
