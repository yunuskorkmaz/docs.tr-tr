---
title: checked (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
ms.openlocfilehash: b05af798217a4f312bcf134d531135713efa8c66
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="checked-c-reference"></a>checked (C# Başvurusu)
`checked` Anahtar sözcüğü açıkça taşma integral türü aritmetik işlemler ve dönüştürmeleri için denetimini etkinleştirmek için kullanılır.  
  
 Varsayılan olarak, hedef türü aralık dışında bir değer ifadesi neden oluyorsa yalnızca sabit değerler içeren bir ifade derleyici hatası neden olur. İfade bir veya daha fazla sabit olmayan değerler içeriyorsa, derleyicinin taşma algılamaz. Atanan ifade değerlendirme `i2` aşağıdaki örnekte bir derleyici hatası neden olmaz.  
  
 [!code-csharp[csrefKeywordsChecked#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_1.cs)]  
  
 Varsayılan olarak, bu sabit olmayan ifadeleri taşma için çalışma zamanında ya da denetlenmez ve taşma özel durumlar yükseltmeyin. Önceki örnekte-2,147,483,639 iki pozitif tamsayıdır toplamı olarak görüntüler.  
  
 Taşma denetimi etkinleştirilebilir derleyici seçenekleri, ortamı yapılandırması veya kullanımı `checked` anahtar sözcüğü. Aşağıdaki örneklerde nasıl kullanılacağını gösteren bir `checked` ifadesi veya bir `checked` tarafından önceki toplam çalışma zamanında üretilen taşma algılamak için blok. Örneklerin her ikisi de taşma özel durumu yükseltin.  
  
 [!code-csharp[csrefKeywordsChecked#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_2.cs)]  
  
 [Denetlenmeyen](../../../csharp/language-reference/keywords/unchecked.md) anahtar sözcüğü, taşma denetimi önlemek için kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Bu örnek nasıl kullanılacağını göstermektedir `checked` taşma çalışma zamanında denetimini etkinleştirmek için.  
  
 [!code-csharp[csrefKeywordsChecked#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_3.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [İşaretli ve İşaretsiz](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
 [unchecked](../../../csharp/language-reference/keywords/unchecked.md)
