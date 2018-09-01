---
title: (, C# Başvurusu)
ms.date: 02/09/2017
f1_keywords:
- '@_CSharpKeyword'
- '@'
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7dbab5a743b4f9fed759210e8410cd6e3459efac
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43385639"
---
# <a name="-c-reference"></a>(, C# Başvurusu)

`@` Özel karakter bir tam tanımlayıcı işlevi görür. Aşağıdaki şekillerde kullanılabilir:

1. Tanımlayıcı olarak kullanılacak C# anahtar sözcükleri etkinleştirmek için. `@` Karakter derleyici C# anahtar sözcüğü yerine bir tanımlayıcı olarak yorumlamak için bir kod öğesi ekler. Aşağıdaki örnekte `@` adlı bir tanımlayıcının tanımlamak için karakter `for` de kullanan bir `for` döngü.

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. Bir dize sabit değeri verbatim yorumlanacağını olduğunu belirtmek için. `@` Karakterin bu örneğinde tanımlayan bir *verbatim dize sabit değeri*. Basit çıkış sıraları (gibi `"\\"` için ters eğik çizgi), onaltılık kaçış dizilerine (gibi `"\x0041"` bir büyük harf a) ve Unicode kaçış dizileri (gibi `"\u0041"` bir büyük harf a) genel anlamıyla yorumlanması. Yalnızca bir teklif kaçış dizisi (`""`) yorumlanmaması tam anlamıyla; bu tek tırnak işareti üretir. Ayrıca, durumunda bir verbatim [ilişkilendirilmiş bir dizedir](interpolated.md) küme ayracı kaçış dizilerine (`{{` ve `}}`) değil olarak yorumlanır tek küme ayracı karakterleri tam anlamıyla; ürettikleri. Aşağıdaki örnek, bir normal bir dize sabit değeri ve diğer verbatim dize değişmez değeri kullanarak iki aynı dosya yolları tanımlar. Bu, aynen dize değişmez değerleri daha yaygın kullanımlarından biridir.

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   Aşağıdaki örnek, normal bir dize sabit değeri ve aynı karakter dizileri içeren sabit bir verbatim dizesi tanımlama etkisini gösterir.

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. Ad çakışması örneklerini öznitelikleri arasında ayrım yapmak derleyici etkinleştirmek için. Türetilen bir tür bir özniteliktir <xref:System.Attribute>. Tür adı genellikle soneki içerir **özniteliği**, ancak derleyici, bu kural uygulamaz. Öznitelik başvurulabilir tam tür adıyla ya da kod (örneğin, `[InfoAttribute]` ya da kısaltılmış adını (örneğin, `[Info]`). İki kısalttık, ancak bir adlandırma çakışması öznitelik türü adları aynıdır ve bir tür adını içeren meydana gelir **özniteliği** soneki ancak diğer desteklemez. Örneğin, aşağıdaki kod derleyici belirlenemiyor çünkü derleme başarısız olup olmadığını `Info` veya `InfoAttribute` özniteliği uygulandığı `Example` sınıfı.

   ```csharp
   using System;

   [AttributeUsage(AttributeTargets.Class)]
   public class Info : Attribute
   {
      private string information;
      
      public Info(string info)
      {
          information = info;
      }
   }

   [AttributeUsage(AttributeTargets.Method)]
   public class InfoAttribute : Attribute
   {
      private string information;
      
      public InfoAttribute(string info)
      {
          information = info;
      }
   }

   [Info("A simple executable.")]
   public class Example
   {
      [InfoAttribute("The entry point.")]
      public static void Main()
      {
      }
   }
   ```  

   Tam tanımlayıcı tanımlamak için kullanılıyorsa `Info` özniteliği, örnek derler başarıyla.

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim4.cs#1)]

## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# Özel Karakterleri](../../../csharp/language-reference/tokens/index.md)
