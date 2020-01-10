---
title: Başvuru eşitlik için test etme (kimlik)- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- object identity [C#]
- reference equality [C#]
ms.assetid: 91307fda-267b-4fd2-a338-2aada39ee791
ms.openlocfilehash: 77ce2ef0ccf47d619134c120101ba2aa04f485e6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75699060"
---
# <a name="how-to-test-for-reference-equality-identity-c-programming-guide"></a><span data-ttu-id="649d9-102">Başvuru eşitlik için test etme (kimlik) (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="649d9-102">How to test for reference equality (Identity) (C# Programming Guide)</span></span>
<span data-ttu-id="649d9-103">Türlerinizin başvuru eşitlik karşılaştırmalarını desteklemek için herhangi bir özel mantık uygulamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="649d9-103">You do not have to implement any custom logic to support reference equality comparisons in your types.</span></span> <span data-ttu-id="649d9-104">Bu işlevsellik, statik <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> yöntemi tarafından tüm türler için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="649d9-104">This functionality is provided for all types by the static <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="649d9-105">Aşağıdaki örnek, iki değişkenin *başvuru eşitliği*olup olmadığını nasıl belirleyeceğini gösterir. Bu, bellekteki aynı nesneye başvurdukları anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="649d9-105">The following example shows how to determine whether two variables have *reference equality*, which means that they refer to the same object in memory.</span></span>  
  
 <span data-ttu-id="649d9-106">Örnek ayrıca, neden <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> her zaman değer türleri için `false` döndürdüğünü ve neden dize eşitliğini belirlemede <xref:System.Object.ReferenceEquals%2A> kullanmamalısınız olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="649d9-106">The example also shows why <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> always returns `false` for value types and why you should not use  <xref:System.Object.ReferenceEquals%2A> to determine string equality.</span></span>  
  
## <a name="example"></a><span data-ttu-id="649d9-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="649d9-107">Example</span></span>  
 [!code-csharp[csProgGuideObjects#90](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#90)]  
  
 <span data-ttu-id="649d9-108"><xref:System.Object?displayProperty=nameWithType> Universal temel sınıfındaki `Equals` uygulanması de bir başvuru eşitlik denetimi gerçekleştirir, ancak bunu kullanmak en iyisidir çünkü yöntemi geçersiz kılmak için bir sınıf olması durumunda sonuçlar beklediğiniz gibi olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="649d9-108">The implementation of `Equals` in the <xref:System.Object?displayProperty=nameWithType> universal base class also performs a reference equality check, but it is best not to use this because, if a class happens to override the method, the results might not be what you expect.</span></span> <span data-ttu-id="649d9-109">Aynı değer, `==` ve `!=` işleçleri için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="649d9-109">The same is true for the `==` and `!=` operators.</span></span> <span data-ttu-id="649d9-110">Başvuru türleri üzerinde çalışırken, `==` ve `!=` varsayılan davranışı bir başvuru eşitlik denetimi gerçekleştirdir.</span><span class="sxs-lookup"><span data-stu-id="649d9-110">When they are operating on reference types, the default behavior of `==` and `!=` is to perform a reference equality check.</span></span> <span data-ttu-id="649d9-111">Ancak, türetilmiş sınıflar bir değer eşitlik denetimi gerçekleştirmek için işlecini aşırı yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="649d9-111">However, derived classes can overload the operator to perform a value equality check.</span></span> <span data-ttu-id="649d9-112">Hata olasılığını en aza indirmek için, iki nesnenin başvuru eşitlik içerip içermediğini belirleyebilmek gerektiğinde <xref:System.Object.ReferenceEquals%2A> her zaman en iyi şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="649d9-112">To minimize the potential for error, it is best to always use <xref:System.Object.ReferenceEquals%2A> when you have to determine whether two objects have reference equality.</span></span>  
  
 <span data-ttu-id="649d9-113">Aynı derleme içindeki sabit dizeler her zaman çalışma zamanı tarafından dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="649d9-113">Constant strings within the same assembly are always interned by the runtime.</span></span> <span data-ttu-id="649d9-114">Diğer bir deyişle, her benzersiz sabit değer dizesinin yalnızca bir örneği korunur.</span><span class="sxs-lookup"><span data-stu-id="649d9-114">That is, only one instance of each unique literal string is maintained.</span></span> <span data-ttu-id="649d9-115">Ancak çalışma zamanı, çalışma zamanında oluşturulan dizelerin birbirine bağlı olduğunu veya farklı derlemelerdeki iki eşit Sabit dizenin birbirine bağlı olduğunu garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="649d9-115">However, the runtime does not guarantee that strings created at runtime are interned, nor does it guarantee that two equal constant strings in different assemblies are interned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="649d9-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="649d9-116">See also</span></span>

- [<span data-ttu-id="649d9-117">Eşitlik Karşılaştırmaları</span><span class="sxs-lookup"><span data-stu-id="649d9-117">Equality Comparisons</span></span>](./equality-comparisons.md)
