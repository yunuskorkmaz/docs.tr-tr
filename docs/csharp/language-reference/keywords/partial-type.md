---
title: "partial (Tür) (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords: partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5212984cc577ce05fc4697e0d648fb5545528562
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="partial-type-c-reference"></a><span data-ttu-id="ab54c-102">partial (Tür) (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ab54c-102">partial (Type) (C# Reference)</span></span>
<span data-ttu-id="ab54c-103">Kısmi türü tanımları bir sınıf, yapı veya arabirim tanımı için birden çok dosyaya bölme izin verir.</span><span class="sxs-lookup"><span data-stu-id="ab54c-103">Partial type definitions allow for the definition of a class, struct, or interface to be split into multiple files.</span></span>  
  
 <span data-ttu-id="ab54c-104">File1.cs içinde:</span><span class="sxs-lookup"><span data-stu-id="ab54c-104">In File1.cs:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_1.cs)]  
  
 <span data-ttu-id="ab54c-105">File2.cs bildirimi:</span><span class="sxs-lookup"><span data-stu-id="ab54c-105">In File2.cs the declaration:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="ab54c-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ab54c-106">Remarks</span></span>  
 <span data-ttu-id="ab54c-107">Büyük projeler ile veya otomatik olarak oluşturulan kodu tarafından sağlanan gibi ile çalışırken bir sınıf bölme, yapı veya arabirim türü birkaç dosyalar üzerinde yararlı olabilir [Windows Form Tasarımcısı](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="ab54c-107">Splitting a class, struct or interface type over several files can be useful when you are working with large projects, or with automatically generated code such as that provided by the [Windows Forms Designer](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span></span> <span data-ttu-id="ab54c-108">Kısmi bir türü içerebilir bir [kısmi yöntemi](../../../csharp/language-reference/keywords/partial-method.md).</span><span class="sxs-lookup"><span data-stu-id="ab54c-108">A partial type may contain a [partial method](../../../csharp/language-reference/keywords/partial-method.md).</span></span> <span data-ttu-id="ab54c-109">Daha fazla bilgi için bkz: [kısmi sınıflar ve yöntemler](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="ab54c-109">For more information, see [Partial Classes and Methods](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="ab54c-110">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="ab54c-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ab54c-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ab54c-111">See Also</span></span>  
 [<span data-ttu-id="ab54c-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="ab54c-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ab54c-113">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ab54c-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ab54c-114">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="ab54c-114">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="ab54c-115">Genel türlere giriş</span><span class="sxs-lookup"><span data-stu-id="ab54c-115">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)
