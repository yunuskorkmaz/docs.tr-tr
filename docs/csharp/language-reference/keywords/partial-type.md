---
title: partial (Tür) (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
ms.openlocfilehash: 4f57149dd18deb08aa11b72d0a6d5f71b3838bd1
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960303"
---
# <a name="partial-type-c-reference"></a><span data-ttu-id="362d9-102">partial (Tür) (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="362d9-102">partial (Type) (C# Reference)</span></span>
<span data-ttu-id="362d9-103">Kısmi tür tanımlarını bir sınıf, yapı veya arabirim tanımı için birden fazla dosyaya bölünmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="362d9-103">Partial type definitions allow for the definition of a class, struct, or interface to be split into multiple files.</span></span>  
  
 <span data-ttu-id="362d9-104">File1.cs içinde:</span><span class="sxs-lookup"><span data-stu-id="362d9-104">In File1.cs:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_1.cs)]  
  
 <span data-ttu-id="362d9-105">File2.cs bildirimi:</span><span class="sxs-lookup"><span data-stu-id="362d9-105">In File2.cs the declaration:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="362d9-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="362d9-106">Remarks</span></span>  
 <span data-ttu-id="362d9-107">Büyük projeler veya sağladığı gibi otomatik olarak oluşturulan kod ile çalışırken, bir sınıf bölme, yapı veya arabirim türü çeşitli dosyalar üzerinde yararlı olabilir [Windows Form Tasarımcısı](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="362d9-107">Splitting a class, struct or interface type over several files can be useful when you are working with large projects, or with automatically generated code such as that provided by the [Windows Forms Designer](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span></span> <span data-ttu-id="362d9-108">Kısmi bir tür içerebilir bir [kısmi yöntem](../../../csharp/language-reference/keywords/partial-method.md).</span><span class="sxs-lookup"><span data-stu-id="362d9-108">A partial type may contain a [partial method](../../../csharp/language-reference/keywords/partial-method.md).</span></span> <span data-ttu-id="362d9-109">Daha fazla bilgi için [kısmi sınıflar ve yöntemler](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="362d9-109">For more information, see [Partial Classes and Methods](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="362d9-110">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="362d9-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="362d9-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="362d9-111">See Also</span></span>  
 [<span data-ttu-id="362d9-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="362d9-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="362d9-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="362d9-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="362d9-114">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="362d9-114">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="362d9-115">Genel Türlere Giriş</span><span class="sxs-lookup"><span data-stu-id="362d9-115">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)
