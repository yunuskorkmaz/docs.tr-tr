---
title: İçinde sabitleri tanımlamaC#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: 6681b1987ec9b5bce40b3abffb9b7d11d4a82bcc
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73970956"
---
# <a name="how-to-define-constants-in-c"></a><span data-ttu-id="75b5a-102">C\# sabitleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="75b5a-102">How to define constants in C\#</span></span>
<span data-ttu-id="75b5a-103">Sabitler, değerleri derleme zamanında ayarlanan alanlardır ve hiçbir zaman değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="75b5a-103">Constants are fields whose values are set at compile time and can never be changed.</span></span> <span data-ttu-id="75b5a-104">Özel değerler için sayısal değişmez değerler ("sihirli sayılar") yerine anlamlı adlar sağlamak için sabitleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="75b5a-104">Use constants to provide meaningful names instead of numeric literals ("magic numbers") for special values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="75b5a-105">C# [#Define](../../language-reference/preprocessor-directives/preprocessor-define.md) Önişlemci yönergesinde, sabitleri genellikle C ve C++içinde kullanılan biçimde tanımlamak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="75b5a-105">In C# the [#define](../../language-reference/preprocessor-directives/preprocessor-define.md) preprocessor directive cannot be used to define constants in the way that is typically used in C and C++.</span></span>  
  
 <span data-ttu-id="75b5a-106">İntegral türlerinin sabit değerlerini (`int`, `byte`vb.) tanımlamak için numaralandırılmış bir tür kullanın.</span><span class="sxs-lookup"><span data-stu-id="75b5a-106">To define constant values of integral types (`int`, `byte`, and so on) use an enumerated type.</span></span> <span data-ttu-id="75b5a-107">Daha fazla bilgi için bkz. [enum](../../language-reference/keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="75b5a-107">For more information, see [enum](../../language-reference/keywords/enum.md).</span></span>  
  
 <span data-ttu-id="75b5a-108">Tamsayı olmayan sabitleri tanımlamak için, tek bir yaklaşım onları `Constants`adlı tek bir statik sınıfta gruplandırmaya yönelik bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="75b5a-108">To define non-integral constants, one approach is to group them in a single static class named `Constants`.</span></span> <span data-ttu-id="75b5a-109">Bu, aşağıdaki örnekte gösterildiği gibi sabitlerin tüm başvurularının sınıf adı ile önceden görüntülenmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="75b5a-109">This will require that all references to the constants be prefaced with the class name, as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75b5a-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="75b5a-110">Example</span></span>  
 [!code-csharp[csProgGuideObjects#89](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#89)]  
  
 <span data-ttu-id="75b5a-111">Sınıf adı niteleyicisi kullanımı, siz ve sabit kullanan diğer kişilerin sabit olduğunu ve değiştirilemeyeceğini anlamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="75b5a-111">The use of the class name qualifier helps ensure that you and others who use the constant understand that it is constant and cannot be modified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75b5a-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75b5a-112">See also</span></span>

- [<span data-ttu-id="75b5a-113">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="75b5a-113">Classes and Structs</span></span>](./index.md)
