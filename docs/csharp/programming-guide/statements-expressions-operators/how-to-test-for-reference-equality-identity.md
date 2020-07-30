---
title: Başvuru eşitlik için test etme (kimlik)-C# Programlama Kılavuzu
description: Başvuru eşitliği (kimlik) için test yapmayı öğrenin. Bir kod örneğine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
helpviewer_keywords:
- object identity [C#]
- reference equality [C#]
ms.assetid: 91307fda-267b-4fd2-a338-2aada39ee791
ms.openlocfilehash: fece0fbc0179f5707e7f3fcd62371b8dde84eb6a
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381391"
---
# <a name="how-to-test-for-reference-equality-identity-c-programming-guide"></a><span data-ttu-id="62f2b-104">Başvuru eşitlik için test etme (kimlik) (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="62f2b-104">How to test for reference equality (Identity) (C# Programming Guide)</span></span>
<span data-ttu-id="62f2b-105">Türlerinizin başvuru eşitlik karşılaştırmalarını desteklemek için herhangi bir özel mantık uygulamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="62f2b-105">You do not have to implement any custom logic to support reference equality comparisons in your types.</span></span> <span data-ttu-id="62f2b-106">Bu işlev, statik yönteme göre tüm türler için sağlanır <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="62f2b-106">This functionality is provided for all types by the static <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="62f2b-107">Aşağıdaki örnek, iki değişkenin *başvuru eşitliği*olup olmadığını nasıl belirleyeceğini gösterir. Bu, bellekteki aynı nesneye başvurdukları anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="62f2b-107">The following example shows how to determine whether two variables have *reference equality*, which means that they refer to the same object in memory.</span></span>  
  
 <span data-ttu-id="62f2b-108">Örnek ayrıca neden <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> her zaman `false` değer türleri için döndüğünü ve neden <xref:System.Object.ReferenceEquals%2A> dize eşitliğini belirlemede kullanmamalısınız gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="62f2b-108">The example also shows why <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> always returns `false` for value types and why you should not use  <xref:System.Object.ReferenceEquals%2A> to determine string equality.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62f2b-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="62f2b-109">Example</span></span>  
 [!code-csharp[csProgGuideObjects#90](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#90)]  
  
 <span data-ttu-id="62f2b-110">`Equals` <xref:System.Object?displayProperty=nameWithType> Evrensel temel sınıftaki uygulamasının uygulanması de bir başvuru eşitlik denetimi gerçekleştirir, ancak bunu kullanmak en iyisidir çünkü yöntemi geçersiz kılmak için bir sınıf olduğunda, sonuçlar beklediğiniz gibi olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="62f2b-110">The implementation of `Equals` in the <xref:System.Object?displayProperty=nameWithType> universal base class also performs a reference equality check, but it is best not to use this because, if a class happens to override the method, the results might not be what you expect.</span></span> <span data-ttu-id="62f2b-111">Aynı, ve işleçleri için de `==` geçerlidir `!=` .</span><span class="sxs-lookup"><span data-stu-id="62f2b-111">The same is true for the `==` and `!=` operators.</span></span> <span data-ttu-id="62f2b-112">Başvuru türleri üzerinde çalıştıklarında, varsayılan davranışı `==` ve `!=` başvuru eşitlik denetimi gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="62f2b-112">When they are operating on reference types, the default behavior of `==` and `!=` is to perform a reference equality check.</span></span> <span data-ttu-id="62f2b-113">Ancak, türetilmiş sınıflar bir değer eşitlik denetimi gerçekleştirmek için işlecini aşırı yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="62f2b-113">However, derived classes can overload the operator to perform a value equality check.</span></span> <span data-ttu-id="62f2b-114">Hata olasılığını en aza indirmek için, <xref:System.Object.ReferenceEquals%2A> iki nesnenin başvuru eşitlik içerip içermediğini belirlemekte her zaman en iyi şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="62f2b-114">To minimize the potential for error, it is best to always use <xref:System.Object.ReferenceEquals%2A> when you have to determine whether two objects have reference equality.</span></span>  
  
 <span data-ttu-id="62f2b-115">Aynı derleme içindeki sabit dizeler her zaman çalışma zamanı tarafından dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="62f2b-115">Constant strings within the same assembly are always interned by the runtime.</span></span> <span data-ttu-id="62f2b-116">Diğer bir deyişle, her benzersiz sabit değer dizesinin yalnızca bir örneği korunur.</span><span class="sxs-lookup"><span data-stu-id="62f2b-116">That is, only one instance of each unique literal string is maintained.</span></span> <span data-ttu-id="62f2b-117">Ancak çalışma zamanı, çalışma zamanında oluşturulan dizelerin birbirine bağlı olduğunu veya farklı derlemelerdeki iki eşit Sabit dizenin birbirine bağlı olduğunu garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="62f2b-117">However, the runtime does not guarantee that strings created at runtime are interned, nor does it guarantee that two equal constant strings in different assemblies are interned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62f2b-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62f2b-118">See also</span></span>

- [<span data-ttu-id="62f2b-119">Eşitlik karşılaştırmaları</span><span class="sxs-lookup"><span data-stu-id="62f2b-119">Equality Comparisons</span></span>](./equality-comparisons.md)
