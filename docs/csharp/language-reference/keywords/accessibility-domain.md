---
title: "Erişilebilirlik Etki Alanı (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 127bacda4bf8363fccff3dd3ef6770ad50984cfb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="accessibility-domain-c-reference"></a>Erişilebilirlik Etki Alanı (C# Başvurusu)
Erişilebilirlik etki alanı üyesi hangi program bölümlerde üyesi başvurulabilir belirtir. Üye içinde başka bir tür geçmişse erişilebilirlik etki alanı her ikisi için de belirlenir [erişilebilirlik düzeyi](../../../csharp/language-reference/keywords/accessibility-levels.md) üye ve erişilebilirlik etki alanı hemen içeren türü.  
  
 Erişilebilirlik etki alanı en üst düzey bir türde en az içinde bildirilen projesinin program metindir. Diğer bir deyişle, etki alanı tüm bu projenin kaynak dosyalarını içerir. Erişilebilirlik etki alanı iç içe bir türde en az hangi bildirilmiş türü program metindir. Diğer bir deyişle, tüm iç içe geçmiş türler içeren türü gövdesi etki alanıdır. Erişilebilirlik etki alanı iç içe geçmiş tür hiçbir zaman, kapsayan tür aşıyor. Bu kavram aşağıdaki örnekte gösterilmiştir.  
  
## <a name="example"></a>Örnek  
 Bu örnek bir üst düzey türünü içeren `T1`ve iki iç içe geçmiş sınıflar `M1` ve `M2`. Sınıfları farklı bildirilen eriþebilirlik sahip alanlar içeriyor. İçinde `Main` yöntemi, bir açıklamayı izleyen her üyesinin erişilebilirlik etki alanı belirtmek için her bir deyimi. Erişilemez üyeleri başvurmak için deneyin deyimleri kılınmıştır dikkat edin. Erişilemez bir üye başvurarak kaynaklanan derleyici hataları görmek istiyorsanız, bir açıklama aynı anda kaldırın.  
  
 [!code-csharp[csrefKeywordsModifiers#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/accessibility-domain_1.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Erişim değiştiricileri](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [Erişilebilirlik düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [Erişilebilirlik düzeylerinin kullanılmasındaki kısıtlamalar](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)  
 [Erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [Ortak](../../../csharp/language-reference/keywords/public.md)  
 [Özel](../../../csharp/language-reference/keywords/private.md)  
 [korumalı](../../../csharp/language-reference/keywords/protected.md)  
 [İç](../../../csharp/language-reference/keywords/internal.md)
