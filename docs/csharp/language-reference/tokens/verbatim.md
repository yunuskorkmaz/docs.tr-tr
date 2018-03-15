---
title: "(, C# Başvurusu)"
ms.date: 02/09/2017
ms.prod: .net
ms.technology:
- devlang-csharp
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
ms.openlocfilehash: 2b62231afc3014f9fc2b9ac7bd39168f40e12c8d
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="-c-reference"></a><span data-ttu-id="7f0c9-102">(, C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7f0c9-102">@ (C# Reference)</span></span>

<span data-ttu-id="7f0c9-103">`@` Özel karakter verbatim bir tanımlayıcı olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="7f0c9-103">The `@` special character serves as a verbatim identifier.</span></span> <span data-ttu-id="7f0c9-104">Aşağıdaki şekillerde kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="7f0c9-104">It can be used in the following ways:</span></span>

1. <span data-ttu-id="7f0c9-105">Tanımlayıcı olarak kullanılacak C# anahtar sözcükleri etkinleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7f0c9-105">To enable C# keywords to be used as identifiers.</span></span> <span data-ttu-id="7f0c9-106">`@` Karakter derleyici C# anahtar sözcüğü yerine bir tanımlayıcı olarak yorumlamak için bir kod öğesi ekler.</span><span class="sxs-lookup"><span data-stu-id="7f0c9-106">The `@` character prefixes a code element that the compiler is to interpret as an identifier rather than a C# keyword.</span></span> <span data-ttu-id="7f0c9-107">Aşağıdaki örnek kullanır `@` adlı bir tanımlayıcıyı tanımlamak için karakter `for` de kullanan bir `for` döngü.</span><span class="sxs-lookup"><span data-stu-id="7f0c9-107">The following example uses the `@` character to define an identifier named `for` that it uses in a `for` loop.</span></span>

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. <span data-ttu-id="7f0c9-108">Bir dize sabit değeri aynen yorumlanacağını olduğunu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="7f0c9-108">To indicate that a string literal is to be interpreted verbatim.</span></span> <span data-ttu-id="7f0c9-109">`@` Bu örnekte karakter tanımlayan bir *verbatim dize sabit değeri*.</span><span class="sxs-lookup"><span data-stu-id="7f0c9-109">The `@` character in this instance defines a *verbatim string literal*.</span></span> <span data-ttu-id="7f0c9-110">Basit kaçış sıraları (gibi `"\\"` bir ters eğik çizgi için), onaltılık kaçış dizilerine (gibi `"\x0041"` bir büyük harf A ve Unicode için çıkış sıraları, gibi `"\u0041"` büyük bir için tam anlamıyla yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="7f0c9-110">Simple escape sequences (such as `"\\"` for a backslash), hexadecimal escape sequences (such as `"\x0041"` for an uppercase A, and Unicode escape sequences, such as `"\u0041"` for an uppercase A, are interpreted literally.</span></span> <span data-ttu-id="7f0c9-111">Yalnızca bir teklif kaçış sırası (`""`) yorumlanmaması tam anlamıyla; tek tırnak işareti üretir.</span><span class="sxs-lookup"><span data-stu-id="7f0c9-111">Only a quote escape sequence (`""`) is not interpreted literally; it produces a single quotation mark.</span></span> <span data-ttu-id="7f0c9-112">Aşağıdaki örnek, iki özdeş dosya yollarını kullanarak bir tane normal dize sabit değeri ve diğer verbatim dize sabit değeri kullanarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7f0c9-112">The following example defines two identical file paths, one by using a regular string literal and the other by using a verbatim string literal.</span></span> <span data-ttu-id="7f0c9-113">Bu, verbatim dize değişmez değerleri daha yaygın kullanımları biridir.</span><span class="sxs-lookup"><span data-stu-id="7f0c9-113">This is one of the more common uses of verbatim string literals.</span></span>

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   <span data-ttu-id="7f0c9-114">Aşağıdaki örnek, normal dize sabit değeri ve bir verbatim değişmez dize değeri aynı karakter sıralarının içeren tanımlama etkisini gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7f0c9-114">The following example illustrates the effect of defining a regular string literal and a verbatim string literal that contain identical character sequences.</span></span>

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. <span data-ttu-id="7f0c9-115">Ad çakışması durumlarda özniteliklerini ayırt etmek derleyici etkinleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7f0c9-115">To enable the compiler to distinguish between attributes in cases of a naming conflict.</span></span> <span data-ttu-id="7f0c9-116">Türetilen bir tür bir özniteliktir <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="7f0c9-116">An attribute is a type that derives from <xref:System.Attribute>.</span></span> <span data-ttu-id="7f0c9-117">Tür adı genellikle soneki içerir **özniteliği**, derleyici, bu kural zorlamaz rağmen.</span><span class="sxs-lookup"><span data-stu-id="7f0c9-117">Its type name typically includes the suffix **Attribute**, although the compiler does not enforce this convention.</span></span> <span data-ttu-id="7f0c9-118">Öznitelik sonra başvurulabilir tam tür adını kullanarak ya da kod (örneğin, `[InfoAttribute]` veya kısaltılmış adı (örneğin, `[Info]`).</span><span class="sxs-lookup"><span data-stu-id="7f0c9-118">The attribute can then be referenced in code either by its full type name (for example, `[InfoAttribute]` or its shortened name (for example, `[Info]`).</span></span> <span data-ttu-id="7f0c9-119">İki kısaltılmış ancak, bir ad çakışması öznitelik türü adları aynıdır ve bir tür adını içeren saptanmışsa **özniteliği** soneki ancak diğer desteklemez.</span><span class="sxs-lookup"><span data-stu-id="7f0c9-119">However, a naming conflict occurs if two shortened attribute type names are identical, and one type name includes the **Attribute** suffix but the other does not.</span></span> <span data-ttu-id="7f0c9-120">Örneğin, derleyici belirleyemediğinden derlemek aşağıdaki kodu başarısız olup olmadığını `Info` veya `InfoAttribute` özniteliği uygulanan `Example` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7f0c9-120">For example, the following code fails to compile because the compiler cannot determine whether the `Info` or `InfoAttribute` attribute is applied to the `Example` class.</span></span>

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

   <span data-ttu-id="7f0c9-121">Verbatim tanımlayıcı tanımlamak için kullanılır, `Info` özniteliği, örnek derler başarıyla.</span><span class="sxs-lookup"><span data-stu-id="7f0c9-121">If the verbatim identifier is used to identify the `Info` attribute, the example compiles successfully.</span></span>

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim4.cs#1)]

## <a name="see-also"></a><span data-ttu-id="7f0c9-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7f0c9-122">See Also</span></span>  
 [<span data-ttu-id="7f0c9-123">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="7f0c9-123">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="7f0c9-124">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7f0c9-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="7f0c9-125">C# Özel Karakterleri</span><span class="sxs-lookup"><span data-stu-id="7f0c9-125">C# Special Characters</span></span>](../../../csharp/language-reference/tokens/index.md)
