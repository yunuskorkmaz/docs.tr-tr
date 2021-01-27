---
title: C# içinde sabitleri tanımlama
description: Değerlerini derleme zamanında ayarlanan alanlar olan C# ' de sabitleri nasıl tanımlayacağınızı öğrenin. Özel değerler için anlamlı adlar sağlamak üzere sabitleri kullanın.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: 4ee1b04cf30b7602ae563cb02daed49f82c04de7
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899002"
---
# <a name="how-to-define-constants-in-c"></a><span data-ttu-id="430f8-104">C 'de sabitleri tanımlama\#</span><span class="sxs-lookup"><span data-stu-id="430f8-104">How to define constants in C\#</span></span>

<span data-ttu-id="430f8-105">Sabitler, değerleri derleme zamanında ayarlanan alanlardır ve hiçbir zaman değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="430f8-105">Constants are fields whose values are set at compile time and can never be changed.</span></span> <span data-ttu-id="430f8-106">Özel değerler için sayısal değişmez değerler ("sihirli sayılar") yerine anlamlı adlar sağlamak için sabitleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="430f8-106">Use constants to provide meaningful names instead of numeric literals ("magic numbers") for special values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="430f8-107">C# ' de [#define](../../language-reference/preprocessor-directives/preprocessor-define.md) Önişlemci yönergesi, sabitleri genellikle C ve C++ ' da kullanılan biçimde tanımlamak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="430f8-107">In C# the [#define](../../language-reference/preprocessor-directives/preprocessor-define.md) preprocessor directive cannot be used to define constants in the way that is typically used in C and C++.</span></span>  
  
 <span data-ttu-id="430f8-108">İntegral türlerinin sabit değerlerini ( `int` , `byte` , vb.) tanımlamak için numaralandırılmış bir tür kullanın.</span><span class="sxs-lookup"><span data-stu-id="430f8-108">To define constant values of integral types (`int`, `byte`, and so on) use an enumerated type.</span></span> <span data-ttu-id="430f8-109">Daha fazla bilgi için bkz. [enum](../../language-reference/builtin-types/enum.md).</span><span class="sxs-lookup"><span data-stu-id="430f8-109">For more information, see [enum](../../language-reference/builtin-types/enum.md).</span></span>  
  
 <span data-ttu-id="430f8-110">Tamsayı olmayan sabitleri tanımlamak için, tek bir yaklaşım bunları adlı tek bir statik sınıfta gruplamak olur `Constants` .</span><span class="sxs-lookup"><span data-stu-id="430f8-110">To define non-integral constants, one approach is to group them in a single static class named `Constants`.</span></span> <span data-ttu-id="430f8-111">Bu, aşağıdaki örnekte gösterildiği gibi sabitlerin tüm başvurularının sınıf adı ile önceden görüntülenmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="430f8-111">This will require that all references to the constants be prefaced with the class name, as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="430f8-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="430f8-112">Example</span></span>  

 [!code-csharp[constants](snippets/how-to-define-constants/Program.cs)]  
  
 <span data-ttu-id="430f8-113">Sınıf adı niteleyicisi kullanımı, siz ve sabit kullanan diğer kişilerin sabit olduğunu ve değiştirilemeyeceğini anlamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="430f8-113">The use of the class name qualifier helps ensure that you and others who use the constant understand that it is constant and cannot be modified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="430f8-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="430f8-114">See also</span></span>

- [<span data-ttu-id="430f8-115">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="430f8-115">Classes and Structs</span></span>](./index.md)
