---
title: operator (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- operator_CSharpKeyword
- operator
helpviewer_keywords:
- operator keyword [C#]
ms.assetid: 59218cce-e90e-42f6-a6bb-30300981b86a
ms.openlocfilehash: d633a46e21f913aa8c05289dccfb63e71efd697e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33267954"
---
# <a name="operator-c-reference"></a><span data-ttu-id="99a9c-102">operator (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="99a9c-102">operator (C# Reference)</span></span>
<span data-ttu-id="99a9c-103">Kullanım `operator` anahtar sözcüğü bir yerleşik işleci aşırı yükleme veya kullanıcı tanımlı bir sınıf veya yapı bildirimi dönüştürmede sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="99a9c-103">Use the `operator` keyword to overload a built-in operator or to provide a user-defined conversion in a class or struct declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99a9c-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="99a9c-104">Example</span></span>  
 <span data-ttu-id="99a9c-105">Kesirli sayılar için oldukça basitleştirilmiş bir sınıf verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="99a9c-105">The following is a very simplified class for fractional numbers.</span></span> <span data-ttu-id="99a9c-106">Bunu overloads `+` ve `*` kesirli toplama ve çarpma gerçekleştirmek için işleçler ve ayrıca bir dönüşüm işleci bu dönüştürür sağlar bir `Fraction` için yazın bir `double` türü.</span><span class="sxs-lookup"><span data-stu-id="99a9c-106">It overloads the `+` and `*` operators to perform fractional addition and multiplication, and also provides a conversion operator that converts a `Fraction` type to a `double` type.</span></span>  
  
 [!code-csharp[csrefKeywordsConversion#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/operator_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="99a9c-107">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="99a9c-107">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="99a9c-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="99a9c-108">See Also</span></span>  
 [<span data-ttu-id="99a9c-109">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="99a9c-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="99a9c-110">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="99a9c-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="99a9c-111">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="99a9c-111">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="99a9c-112">implicit</span><span class="sxs-lookup"><span data-stu-id="99a9c-112">implicit</span></span>](../../../csharp/language-reference/keywords/implicit.md)  
 [<span data-ttu-id="99a9c-113">explicit</span><span class="sxs-lookup"><span data-stu-id="99a9c-113">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
 [<span data-ttu-id="99a9c-114">Nasıl yapılır: Yapılar Arasında Kullanıcı Tanımlı Dönüştürmeler Uygulama</span><span class="sxs-lookup"><span data-stu-id="99a9c-114">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
