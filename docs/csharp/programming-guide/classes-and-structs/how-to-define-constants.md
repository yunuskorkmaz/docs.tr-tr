---
title: C# içinde sabitleri tanımlama
description: Değerlerini derleme zamanında ayarlanan alanlar olan C# ' de sabitleri nasıl tanımlayacağınızı öğrenin. Özel değerler için anlamlı adlar sağlamak üzere sabitleri kullanın.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: dd8c6469c4d72da5588f0dce5314308bcc7e3b95
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91199126"
---
# <a name="how-to-define-constants-in-c"></a><span data-ttu-id="65cbd-104">C 'de sabitleri tanımlama\#</span><span class="sxs-lookup"><span data-stu-id="65cbd-104">How to define constants in C\#</span></span>

<span data-ttu-id="65cbd-105">Sabitler, değerleri derleme zamanında ayarlanan alanlardır ve hiçbir zaman değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="65cbd-105">Constants are fields whose values are set at compile time and can never be changed.</span></span> <span data-ttu-id="65cbd-106">Özel değerler için sayısal değişmez değerler ("sihirli sayılar") yerine anlamlı adlar sağlamak için sabitleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="65cbd-106">Use constants to provide meaningful names instead of numeric literals ("magic numbers") for special values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="65cbd-107">C# ' de [#define](../../language-reference/preprocessor-directives/preprocessor-define.md) Önişlemci yönergesi, sabitleri genellikle C ve C++ ' da kullanılan biçimde tanımlamak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="65cbd-107">In C# the [#define](../../language-reference/preprocessor-directives/preprocessor-define.md) preprocessor directive cannot be used to define constants in the way that is typically used in C and C++.</span></span>  
  
 <span data-ttu-id="65cbd-108">İntegral türlerinin sabit değerlerini ( `int` , `byte` , vb.) tanımlamak için numaralandırılmış bir tür kullanın.</span><span class="sxs-lookup"><span data-stu-id="65cbd-108">To define constant values of integral types (`int`, `byte`, and so on) use an enumerated type.</span></span> <span data-ttu-id="65cbd-109">Daha fazla bilgi için bkz. [enum](../../language-reference/builtin-types/enum.md).</span><span class="sxs-lookup"><span data-stu-id="65cbd-109">For more information, see [enum](../../language-reference/builtin-types/enum.md).</span></span>  
  
 <span data-ttu-id="65cbd-110">Tamsayı olmayan sabitleri tanımlamak için, tek bir yaklaşım bunları adlı tek bir statik sınıfta gruplamak olur `Constants` .</span><span class="sxs-lookup"><span data-stu-id="65cbd-110">To define non-integral constants, one approach is to group them in a single static class named `Constants`.</span></span> <span data-ttu-id="65cbd-111">Bu, aşağıdaki örnekte gösterildiği gibi sabitlerin tüm başvurularının sınıf adı ile önceden görüntülenmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="65cbd-111">This will require that all references to the constants be prefaced with the class name, as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65cbd-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="65cbd-112">Example</span></span>  

 [!code-csharp[csProgGuideObjects#89](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#89)]  
  
 <span data-ttu-id="65cbd-113">Sınıf adı niteleyicisi kullanımı, siz ve sabit kullanan diğer kişilerin sabit olduğunu ve değiştirilemeyeceğini anlamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="65cbd-113">The use of the class name qualifier helps ensure that you and others who use the constant understand that it is constant and cannot be modified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65cbd-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65cbd-114">See also</span></span>

- [<span data-ttu-id="65cbd-115">Sınıflar ve yapılar</span><span class="sxs-lookup"><span data-stu-id="65cbd-115">Classes and Structs</span></span>](./index.md)
