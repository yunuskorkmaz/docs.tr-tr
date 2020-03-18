---
title: Erişilebilirlik Etki Alanı - C# Referans
ms.date: 07/20/2015
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
ms.openlocfilehash: 4a4319b03f3e0d7f9ec721e611b78c124a8a8ee5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713829"
---
# <a name="accessibility-domain-c-reference"></a>Erişilebilirlik Etki Alanı (C# Başvurusu)
Bir üyenin erişilebilirlik etki alanı, bir üyenin hangi program bölümlerine başvurulabileceğini belirtir. Üye başka bir türde iç içe yse, erişilebilirlik etki alanı hem üyenin [erişilebilirlik düzeyine](./accessibility-levels.md) hem de hemen içeren türün erişilebilirlik etki alanına göre belirlenir.  
  
 Üst düzey bir türün erişilebilirlik etki alanı, en azından beyan edildiği projenin program metnidir. Diğer bir zamanda, etki alanı bu projenin tüm kaynak dosyalarını içerir. İç içe geçmiş bir türün erişilebilirlik etki alanı, en azından beyan edildiği türün program metnidir. Diğer bir zamanda, etki alanı, iç içe olan tüm türleri içeren tür gövdesidir. İç içe bir türün erişilebilirlik etki alanı, içeren türün etki alanını asla aşmaz. Bu kavramlar aşağıdaki örnekte gösterilmiştir.  
  
## <a name="example"></a>Örnek  
 Bu örnek, `T1`üst düzey bir tür ve iki `M1` `M2`iç içe sınıf ve. Sınıflar, farklı bildirilen erişilebilirliklere sahip alanlar içerir. `Main` Yöntemde, her üyenin erişilebilirlik etki alanını belirtmek için bir açıklama her deyimi izler. Erişilemeyen üyelere başvuru yapmaya çalışan ifadelerin yorumlanabildiğine dikkat edin. Erişilemeyen bir üyeye başvurmaktan kaynaklanan derleyici hatalarını görmek istiyorsanız, yorumları teker teker kaldırın.  
  
[!code-csharp[csrefKeywordsModifiers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#4)]
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](./index.md)
- [Erişim Değiştiricileri](./access-modifiers.md)
- [Erişilebilirlik Düzeyleri](./accessibility-levels.md)
- [Erişilebilirlik Düzeylerinin Kullanılmasındaki Kısıtlamalar](./restrictions-on-using-accessibility-levels.md)
- [Erişim Değiştiricileri](../../programming-guide/classes-and-structs/access-modifiers.md)
- [Kamu](./public.md)
- [Özel](./private.md)
- [protected](./protected.md)
- [Iç](./internal.md)
