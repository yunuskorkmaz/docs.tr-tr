---
title: "(, C# Başvurusu)"
ms.date: 02/09/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- '@_CSharpKeyword'
- '@'
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 30f937951557ba65971a752b414cce6b485149be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="-c-reference"></a>(, C# Başvurusu)

`@` Özel karakter verbatim bir tanımlayıcı olarak görev yapar. Aşağıdaki şekillerde kullanılabilir:

1. Tanımlayıcı olarak kullanılacak C# anahtar sözcükleri etkinleştirmek için kullanılır. `@` Karakter derleyici C# anahtar sözcüğü yerine bir tanımlayıcı olarak yorumlamak için bir kod öğesi ekler. Aşağıdaki örnek kullanır `@` adlı bir tanımlayıcıyı tanımlamak için karakter `for` de kullanan bir `for` döngü.

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. Bir dize sabit değeri aynen yorumlanacağını olduğunu belirtmek için. `@` Bu örnekte karakter tanımlayan bir *verbatim dize sabit değeri*. Basit kaçış sıraları (gibi `"\\"` bir ters eğik çizgi için), onaltılık kaçış dizilerine (gibi `"\x0041"` bir büyük harf A ve Unicode için çıkış sıraları, gibi `"\u0041"` büyük bir için tam anlamıyla yorumlanır. Yalnızca bir teklif kaçış sırası (`""`) yorumlanmaması tam anlamıyla; tek tırnak işareti üretir. Aşağıdaki örnek, iki özdeş dosya yollarını kullanarak bir tane normal dize sabit değeri ve diğer verbatim dize sabit değeri kullanarak tanımlar. Bu, verbatim dize değişmez değerleri daha yaygın kullanımları biridir.

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   Aşağıdaki örnek, normal dize sabit değeri ve bir verbatim değişmez dize değeri aynı karakter sıralarının içeren tanımlama etkisini gösterilmektedir.

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. Ad çakışması durumlarda özniteliklerini ayırt etmek derleyici etkinleştirmek için kullanılır. Türetilen bir tür bir özniteliktir <xref:System.Attribute>. Tür adı genellikle soneki içerir **özniteliği**, derleyici, bu kural zorlamaz rağmen. Öznitelik sonra başvurulabilir tam tür adını kullanarak ya da kod (örneğin, `[InfoAttribute]` veya kısaltılmış adı (örneğin, `[Info]`). İki kısaltılmış ancak, bir ad çakışması öznitelik türü adları aynıdır ve bir tür adını içeren saptanmışsa **özniteliği** soneki ancak diğer desteklemez. Örneğin, derleyici belirleyemediğinden derlemek aşağıdaki kodu başarısız olup olmadığını `Info` veya `InfoAttribute` özniteliği uygulanan `Main` yöntemi.

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

   Verbatim tanımlayıcı tanımlamak için kullanılır, `Info` özniteliği, örnek derler başarıyla.

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim4.cs#1)]

## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# özel karakterler](../../../csharp/language-reference/tokens/index.md)
