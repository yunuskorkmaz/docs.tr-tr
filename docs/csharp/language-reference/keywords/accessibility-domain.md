---
description: Erişilebilirlik etki alanı-C# başvurusu
title: Erişilebilirlik etki alanı-C# başvurusu
ms.date: 07/20/2015
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
ms.openlocfilehash: 35fc619dd284ff9915662ba48fa06dd295cbbf42
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168848"
---
# <a name="accessibility-domain-c-reference"></a>Erişilebilirlik Etki Alanı (C# Başvurusu)

Üyenin erişilebilirlik etki alanı bir üyenin hangi program bölümlerine başvurduğunu belirtir. Üye başka bir tür içinde iç içe ise, erişilebilirlik etki alanı hem üyenin [Erişilebilirlik düzeyine](./accessibility-levels.md) hem de hemen kapsayan türdeki erişilebilirlik etki alanına göre belirlenir.  
  
 Üst düzey bir türün erişilebilirlik etki alanı, en azından içinde bildirildiği projenin program metni. Diğer bir deyişle, etki alanı bu projenin tüm kaynak dosyalarını içerir. İç içe bir türün erişilebilirlik etki alanı, bildirildiği türün en az program metniyle. Diğer bir deyişle, etki alanı tüm iç içe geçmiş türleri içeren tür gövdesidir. İç içe bir türün erişilebilirlik etki alanı, kendisini kapsayan türden hiçbir şekilde aşamaz. Bu kavramlar aşağıdaki örnekte gösterilmiştir.  
  
## <a name="example"></a>Örnek  

 Bu örnek, en üst düzey bir tür, ve `T1` iki iç içe geçmiş sınıf `M1` içerir `M2` . Sınıflar, farklı tanımlanmış erişilebilir alanlara sahip alanlar içerir. `Main`Yönteminde, her üyenin erişilebilirlik etki alanını göstermek için her deyimin bir açıklaması. Erişilemeyen üyelere başvuruda bulunan deyimlerin açıklama olarak oluşturulduğuna dikkat edin. Erişilemeyen bir üyeye başvuruda bulunarak oluşan derleyici hatalarını görmek isterseniz, açıklamaları tek seferde kaldırın.  
  
[!code-csharp[csrefKeywordsModifiers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#4)]
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](./index.md)
- [Erişim Değiştiricileri](./access-modifiers.md)
- [Erişilebilirlik Düzeyleri](./accessibility-levels.md)
- [Erişilebilirlik Düzeylerinin Kullanılmasındaki Kısıtlamalar](./restrictions-on-using-accessibility-levels.md)
- [Erişim Değiştiricileri](../../programming-guide/classes-and-structs/access-modifiers.md)
- [genel](./public.md)
- [private](./private.md)
- [protected](./protected.md)
- [internal](./internal.md)
