---
title: Erişilebilirlik Etki Alanı (C# Başvurusu)
ms.date: 07/20/2015
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
ms.openlocfilehash: 01854b60fb58d4dcd0a217552f19d6c0cd32ec78
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45664442"
---
# <a name="accessibility-domain-c-reference"></a>Erişilebilirlik Etki Alanı (C# Başvurusu)
Hangi program bölümlerde üyesi başvurulabilir üyesi erişilebilirlik etki alanını belirtir. Başka bir türde üye içe yerleştirilmişse, onun erişilebilirlik etki alanı tarafından belirlenir [erişilebilirlik düzeyi](../../../csharp/language-reference/keywords/accessibility-levels.md) üyesi ve hemen içeren türün erişilebilirlik etki alanı.  
  
 Üst düzey tür erişilebilirlik etki alanı en az içinde bildirildiği proje öğesinin program metnidir. Diğer bir deyişle, etki alanı, tüm bu projenin kaynak dosyaları içerir. İç içe türün erişilebilirlik etki alanı en az tür içinde bildirildiği program metnidir. Diğer bir deyişle, tüm iç içe geçmiş türler içeren tür gövdesi etki alanıdır. İç içe türün erişilebilirlik etki alanı hiçbir zaman, kapsayan türdeki aşıyor. Bu kavramlar, aşağıdaki örnekte gösterilmiştir.  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir üst düzey tür içerir `T1`ve iç içe iki sınıf `M1` ve `M2`. Sınıflar, farklı bildirilen erişilebilirlikleri alanlar içerir. İçinde `Main` yöntemi, bir açıklama her üyesinin erişilebilirlik etki alanı belirtmek için her deyim izler. Erişilemeyen üyeler başvurmak için deneyin deyimleri satırlarıdır dikkat edin. Erişilemez bir üye başvurarak kaynaklanan derleyici hataları görmek istiyorsanız, bir kerede bir yorum kaldırın.  
  
[!code-csharp[csrefKeywordsModifiers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#4)]
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
- [Erişim Değiştiricileri](../../../csharp/language-reference/keywords/access-modifiers.md)  
- [Erişilebilirlik Düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md)  
- [Erişilebilirlik Düzeylerinin Kullanılmasındaki Kısıtlamalar](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)  
- [Erişim Değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
- [public](../../../csharp/language-reference/keywords/public.md)  
- [private](../../../csharp/language-reference/keywords/private.md)  
- [protected](../../../csharp/language-reference/keywords/protected.md)  
- [internal](../../../csharp/language-reference/keywords/internal.md)
