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
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37959552"
---
# <a name="operator-c-reference"></a><span data-ttu-id="a5167-102">operator (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a5167-102">operator (C# Reference)</span></span>
<span data-ttu-id="a5167-103">Kullanım `operator` anahtar sözcük yerleşik bir işleç aşırı yüklemesi veya bir kullanıcı tanımlı dönüştürme bir class veya struct bildiriminde sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="a5167-103">Use the `operator` keyword to overload a built-in operator or to provide a user-defined conversion in a class or struct declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5167-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="a5167-104">Example</span></span>  
 <span data-ttu-id="a5167-105">Kesirli sayılar için çok basitleştirilmiş bir sınıf verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a5167-105">The following is a very simplified class for fractional numbers.</span></span> <span data-ttu-id="a5167-106">Aşırı `+` ve `*` kesirli toplama ve çarpma gerçekleştirmek için işleçler ve ayrıca bir dönüştürme işleci bu dönüştürür sağlar bir `Fraction` için yazın bir `double` türü.</span><span class="sxs-lookup"><span data-stu-id="a5167-106">It overloads the `+` and `*` operators to perform fractional addition and multiplication, and also provides a conversion operator that converts a `Fraction` type to a `double` type.</span></span>  
  
 [!code-csharp[csrefKeywordsConversion#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/operator_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="a5167-107">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="a5167-107">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a5167-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a5167-108">See Also</span></span>  
 [<span data-ttu-id="a5167-109">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="a5167-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a5167-110">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a5167-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a5167-111">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="a5167-111">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="a5167-112">implicit</span><span class="sxs-lookup"><span data-stu-id="a5167-112">implicit</span></span>](../../../csharp/language-reference/keywords/implicit.md)  
 [<span data-ttu-id="a5167-113">explicit</span><span class="sxs-lookup"><span data-stu-id="a5167-113">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
 [<span data-ttu-id="a5167-114">Nasıl yapılır: Yapılar Arasında Kullanıcı Tanımlı Dönüştürmeler Uygulama</span><span class="sxs-lookup"><span data-stu-id="a5167-114">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
