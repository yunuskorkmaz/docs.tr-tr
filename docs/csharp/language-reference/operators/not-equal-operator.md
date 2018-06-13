---
title: '!= İşleci (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '!=_CSharpKeyword'
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
ms.openlocfilehash: e409e2a80886fd5f7f4cdbeaa9b4e3325f8a967b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33272445"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="1e35a-102">!= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="1e35a-102">!= Operator (C# Reference)</span></span>
<span data-ttu-id="1e35a-103">Eşitsizlik işleci (`!=`) işlenenleri true tersi durumda, eşitse, false değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="1e35a-103">The inequality operator (`!=`) returns false if its operands are equal, true otherwise.</span></span> <span data-ttu-id="1e35a-104">Eşitsizlik işleçleri dize ve nesne dahil olmak üzere tüm türleri için önceden tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="1e35a-104">Inequality operators are predefined for all types, including string and object.</span></span> <span data-ttu-id="1e35a-105">Kullanıcı tanımlı türler aşırı yükleme `!=` işleci.</span><span class="sxs-lookup"><span data-stu-id="1e35a-105">User-defined types can overload the `!=` operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e35a-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1e35a-106">Remarks</span></span>  
 <span data-ttu-id="1e35a-107">İçin önceden tanımlanmış değer türleri, eşitsizlik işleci (`!=`) işlenenleri Aksi durumda farklı, false değerleri, true değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="1e35a-107">For predefined value types, the inequality operator (`!=`) returns true if the values of its operands are different, false otherwise.</span></span> <span data-ttu-id="1e35a-108">Başvuru türleri dışında `string`, `!=` iki işlenenleri farklı nesnelere atıfta, true değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="1e35a-108">For reference types other than `string`, `!=` returns true if its two operands refer to different objects.</span></span> <span data-ttu-id="1e35a-109">İçin `string` türü, `!=` dize değerlerini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="1e35a-109">For the `string` type, `!=` compares the values of the strings.</span></span>  
  
 <span data-ttu-id="1e35a-110">Kullanıcı tanımlı bir değer türleri aşırı yükleme `!=` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="1e35a-110">User-defined value types can overload the `!=` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="1e35a-111">Bu nedenle ancak varsayılan olarak kullanıcı tanımlı başvuru türleri için `!=` hem önceden tanımlanmış ve kullanıcı tanımlı referans türleri için yukarıda açıklandığı gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="1e35a-111">So can user-defined reference types, although by default `!=` behaves as described above for both predefined and user-defined reference types.</span></span> <span data-ttu-id="1e35a-112">Varsa `!=` aşırı yüklendi [ == ](../../../csharp/language-reference/operators/equality-comparison-operator.md) da aşırı yüklenmiş gerekir.</span><span class="sxs-lookup"><span data-stu-id="1e35a-112">If `!=` is overloaded, [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) must also be overloaded.</span></span> <span data-ttu-id="1e35a-113">Tam sayı türleri üzerinde işlemler genellikle numaralandırma üzerinde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="1e35a-113">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e35a-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="1e35a-114">Example</span></span>  
 [!code-csharp[csRefOperators#33](../../../csharp/language-reference/operators/codesnippet/CSharp/not-equal-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="1e35a-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1e35a-115">See Also</span></span>  
 [<span data-ttu-id="1e35a-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="1e35a-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1e35a-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1e35a-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1e35a-118">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="1e35a-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
