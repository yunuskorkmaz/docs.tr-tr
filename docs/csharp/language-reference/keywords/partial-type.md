---
title: partial (Tür) (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
ms.openlocfilehash: 362a02815cb249d57c0bd19706714df1d71644f4
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42929669"
---
# <a name="partial-type-c-reference"></a><span data-ttu-id="329ae-102">partial (Tür) (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="329ae-102">partial (Type) (C# Reference)</span></span>
<span data-ttu-id="329ae-103">Kısmi tür tanımlarını bir sınıf, yapı veya arabirim tanımı için birden fazla dosyaya bölünmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="329ae-103">Partial type definitions allow for the definition of a class, struct, or interface to be split into multiple files.</span></span>  
  
 <span data-ttu-id="329ae-104">File1.cs içinde:</span><span class="sxs-lookup"><span data-stu-id="329ae-104">In File1.cs:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_1.cs)]  
  
 <span data-ttu-id="329ae-105">File2.cs bildirimi:</span><span class="sxs-lookup"><span data-stu-id="329ae-105">In File2.cs the declaration:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="329ae-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="329ae-106">Remarks</span></span>  
 <span data-ttu-id="329ae-107">Büyük projeler veya sağladığı gibi otomatik olarak oluşturulan kod ile çalışırken, bir sınıf bölme, yapı veya arabirim türü çeşitli dosyalar üzerinde yararlı olabilir [Windows Form Tasarımcısı](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="329ae-107">Splitting a class, struct or interface type over several files can be useful when you are working with large projects, or with automatically generated code such as that provided by the [Windows Forms Designer](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span></span> <span data-ttu-id="329ae-108">Kısmi bir tür içerebilir bir [kısmi yöntem](../../../csharp/language-reference/keywords/partial-method.md).</span><span class="sxs-lookup"><span data-stu-id="329ae-108">A partial type may contain a [partial method](../../../csharp/language-reference/keywords/partial-method.md).</span></span> <span data-ttu-id="329ae-109">Daha fazla bilgi için [kısmi sınıflar ve yöntemler](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="329ae-109">For more information, see [Partial Classes and Methods](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="329ae-110">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="329ae-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="329ae-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="329ae-111">See Also</span></span>

- [<span data-ttu-id="329ae-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="329ae-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="329ae-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="329ae-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="329ae-114">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="329ae-114">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
- [<span data-ttu-id="329ae-115">Genel Türlere Giriş</span><span class="sxs-lookup"><span data-stu-id="329ae-115">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)
