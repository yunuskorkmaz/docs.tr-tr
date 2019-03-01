---
title: 'Nasıl yapılır: İçinde sabitleri tanımlamaC#'
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: cf57589df2eb375f34d175939a7f685a4abf59a2
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975426"
---
# <a name="how-to-define-constants-in-c"></a><span data-ttu-id="38f3b-102">Nasıl yapılır: C sabitleri tanımlama\#</span><span class="sxs-lookup"><span data-stu-id="38f3b-102">How to: Define Constants in C\#</span></span>
<span data-ttu-id="38f3b-103">Alanlar, değerleri kümesine derleme zamanı ve hiçbir zaman değiştirilebilir sabittir.</span><span class="sxs-lookup"><span data-stu-id="38f3b-103">Constants are fields whose values are set at compile time and can never be changed.</span></span> <span data-ttu-id="38f3b-104">Özel değerler için sayısal değişmez değerleri ("Sihirli sayı") yerine anlamlı adlar sağlamak için sabitleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="38f3b-104">Use constants to provide meaningful names instead of numeric literals ("magic numbers") for special values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38f3b-105">C# [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) önişlemci yönergesi, genellikle C ve C++ içinde kullanılan bir şekilde sabitleri tanımlamak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="38f3b-105">In C# the [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) preprocessor directive cannot be used to define constants in the way that is typically used in C and C++.</span></span>  
  
 <span data-ttu-id="38f3b-106">İntegral türündeki sabit değerler tanımlamak için (`int`, `byte`, vb.) bir listeden seçimli türü kullanın.</span><span class="sxs-lookup"><span data-stu-id="38f3b-106">To define constant values of integral types (`int`, `byte`, and so on) use an enumerated type.</span></span> <span data-ttu-id="38f3b-107">Daha fazla bilgi için [enum](../../../csharp/language-reference/keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="38f3b-107">For more information, see [enum](../../../csharp/language-reference/keywords/enum.md).</span></span>  
  
 <span data-ttu-id="38f3b-108">Tamsayı olmayan sabitleri tanımlamak için adlı tek bir statik sınıf içinde gruplamak için bir yaklaşım ise `Constants`.</span><span class="sxs-lookup"><span data-stu-id="38f3b-108">To define non-integral constants, one approach is to group them in a single static class named `Constants`.</span></span> <span data-ttu-id="38f3b-109">Bu sınıfı adıyla sabitlere yapılan tüm başvurular başında, aşağıdaki örnekte gösterildiği gibi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="38f3b-109">This will require that all references to the constants be prefaced with the class name, as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="38f3b-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="38f3b-110">Example</span></span>  
 [!code-csharp[csProgGuideObjects#89](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-constants_1.cs)]  
  
 <span data-ttu-id="38f3b-111">Sınıf adı niteleyici kullanımını yardımcı olur ve sabit diğer sabittir ve değiştirilemez anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="38f3b-111">The use of the class name qualifier helps ensure that you and others who use the constant understand that it is constant and cannot be modified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38f3b-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38f3b-112">See also</span></span>

- [<span data-ttu-id="38f3b-113">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="38f3b-113">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
