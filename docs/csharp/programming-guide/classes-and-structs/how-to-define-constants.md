---
title: C# içinde sabitleri tanımlama
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: 15526655de8af6fed464376db1ac761468215210
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75337651"
---
# <a name="how-to-define-constants-in-c"></a><span data-ttu-id="6f244-102">C'de sabitler nasıl tanımlanır?\#</span><span class="sxs-lookup"><span data-stu-id="6f244-102">How to define constants in C\#</span></span>
<span data-ttu-id="6f244-103">Sabitler, değerleri derleme zamanında ayarlanan ve asla değiştirilemeyecek alanlardır.</span><span class="sxs-lookup"><span data-stu-id="6f244-103">Constants are fields whose values are set at compile time and can never be changed.</span></span> <span data-ttu-id="6f244-104">Özel değerler için sayısal literaller ("sihirli sayılar") yerine anlamlı adlar sağlamak için sabitleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="6f244-104">Use constants to provide meaningful names instead of numeric literals ("magic numbers") for special values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6f244-105">C# #define [önişlemci](../../language-reference/preprocessor-directives/preprocessor-define.md) yönergesi, sabitleri c ve c++'da genellikle kullanılan şekilde tanımlamak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6f244-105">In C# the [#define](../../language-reference/preprocessor-directives/preprocessor-define.md) preprocessor directive cannot be used to define constants in the way that is typically used in C and C++.</span></span>  
  
 <span data-ttu-id="6f244-106">İntegral türlerinin`int`sabit `byte`değerlerini tanımlamak için (, , vb.) numaralandırılmış bir tür kullanın.</span><span class="sxs-lookup"><span data-stu-id="6f244-106">To define constant values of integral types (`int`, `byte`, and so on) use an enumerated type.</span></span> <span data-ttu-id="6f244-107">Daha fazla bilgi için [enum' a](../../language-reference/builtin-types/enum.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="6f244-107">For more information, see [enum](../../language-reference/builtin-types/enum.md).</span></span>  
  
 <span data-ttu-id="6f244-108">İntegral olmayan sabitleri tanımlamak için bir yaklaşım, bunları `Constants`.</span><span class="sxs-lookup"><span data-stu-id="6f244-108">To define non-integral constants, one approach is to group them in a single static class named `Constants`.</span></span> <span data-ttu-id="6f244-109">Bu, aşağıdaki örnekte gösterildiği gibi, sabitlere yapılan tüm başvuruların sınıf adı ile ön karşıkarşıya olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6f244-109">This will require that all references to the constants be prefaced with the class name, as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f244-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="6f244-110">Example</span></span>  
 [!code-csharp[csProgGuideObjects#89](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#89)]  
  
 <span data-ttu-id="6f244-111">Sınıf adı niteleyicisinin kullanımı, sizin ve sabiti kullanan diğer insanların bunun sabit olduğunu ve değiştirilemeyeceğini anlamanızı sağlamaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="6f244-111">The use of the class name qualifier helps ensure that you and others who use the constant understand that it is constant and cannot be modified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f244-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f244-112">See also</span></span>

- [<span data-ttu-id="6f244-113">Sınıflar ve Structs</span><span class="sxs-lookup"><span data-stu-id="6f244-113">Classes and Structs</span></span>](./index.md)
