---
title: "Nasıl yapılır: Başvuru Eşitliği Testi (Kimlik) (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- object identity [C#]
- reference equality [C#]
ms.assetid: 91307fda-267b-4fd2-a338-2aada39ee791
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2dbbd7c0e5ebb507ca3dda0f248d9f1c8f9595fe
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-test-for-reference-equality-identity-c-programming-guide"></a><span data-ttu-id="ce60a-102">Nasıl yapılır: Başvuru Eşitliği Testi (Kimlik) (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="ce60a-102">How to: Test for Reference Equality (Identity) (C# Programming Guide)</span></span>
<span data-ttu-id="ce60a-103">Referans eşitlik karşılaştırmaları, türlerinizi desteklemek için hiçbir özel mantığı uygulamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="ce60a-103">You do not have to implement any custom logic to support reference equality comparisons in your types.</span></span> <span data-ttu-id="ce60a-104">Bu işlev tarafından statik tüm türleri için sağlanan <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ce60a-104">This functionality is provided for all types by the static <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="ce60a-105">Aşağıdaki örnekte, iki değişken sahip olup olmadığınızı belirlemek gösterilmiştir *başvuru eşitliği*, bellekte aynı nesnesi başvuruda bulunulan anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ce60a-105">The following example shows how to determine whether two variables have *reference equality*, which means that they refer to the same object in memory.</span></span>  
  
 <span data-ttu-id="ce60a-106">Bu örnek ayrıca neden gösterir <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> her zaman döndürür `false` değer türleri ve neden kullanılamaz <xref:System.Object.ReferenceEquals%2A> dize eşitlik belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="ce60a-106">The example also shows why <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> always returns `false` for value types and why you should not use  <xref:System.Object.ReferenceEquals%2A> to determine string equality.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce60a-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="ce60a-107">Example</span></span>  
 [!code-csharp[csProgGuideObjects#90](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-test-for-reference-equality-identity_1.cs)]  
  
 <span data-ttu-id="ce60a-108">Uygulaması `Equals` içinde <xref:System.Object?displayProperty=nameWithType> Evrensel taban sınıfı ayrıca bir referans eşitlik denetimi gerçekleştirir, ancak beklediğiniz sonuçları yöntemi geçersiz kılmak için bir sınıf meydana gelirse olmayabileceğinden, bu kullanmamanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="ce60a-108">The implementation of `Equals` in the <xref:System.Object?displayProperty=nameWithType> universal base class also performs a reference equality check, but it is best not to use this because, if a class happens to override the method, the results might not be what you expect.</span></span> <span data-ttu-id="ce60a-109">Aynı için doğrudur `==` ve `!=` işleçler.</span><span class="sxs-lookup"><span data-stu-id="ce60a-109">The same is true for the `==` and `!=` operators.</span></span> <span data-ttu-id="ce60a-110">Referans olarak ne zaman işletim türleri, == varsayılan davranışını ve `!=` referans eşitlik kontrolüne gerçekleştirmektir.</span><span class="sxs-lookup"><span data-stu-id="ce60a-110">When they are operating on reference types, the default behavior of == and `!=` is to perform a reference equality check.</span></span> <span data-ttu-id="ce60a-111">Ancak, türetilen sınıflar değeri eşitlik denetimi gerçekleştirmek için işleç aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="ce60a-111">However, derived classes can overload the operator to perform a value equality check.</span></span> <span data-ttu-id="ce60a-112">Hata olasılığını en aza indirmek için her zaman kullanmak en iyisidir <xref:System.Object.ReferenceEquals%2A> iki nesne başvuru eşitliği sahip olup olmadığınızı belirlemek olduğunda.</span><span class="sxs-lookup"><span data-stu-id="ce60a-112">To minimize the potential for error, it is best to always use <xref:System.Object.ReferenceEquals%2A> when you have to determine whether two objects have reference equality.</span></span>  
  
 <span data-ttu-id="ce60a-113">Sabit Dizeler aynı bütünleştirilmiş kod içinde her zaman çalışma zamanı tarafından interned.</span><span class="sxs-lookup"><span data-stu-id="ce60a-113">Constant strings within the same assembly are always interned by the runtime.</span></span> <span data-ttu-id="ce60a-114">Diğer bir deyişle, her benzersiz bir değişmez dize yalnızca bir örneği korunur.</span><span class="sxs-lookup"><span data-stu-id="ce60a-114">That is, only one instance of each unique literal string is maintained.</span></span> <span data-ttu-id="ce60a-115">Ancak, çalışma zamanı dizeleri çalışma zamanında oluşturulan interned veya farklı derlemelerde iki eşit sabit dizeler interned garanti etmez garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="ce60a-115">However, the runtime does not guarantee that strings created at runtime are interned, nor does it guarantee that two equal constant strings in different assemblies are interned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce60a-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ce60a-116">See Also</span></span>  
 [<span data-ttu-id="ce60a-117">Eşitlik karşılaştırmaları</span><span class="sxs-lookup"><span data-stu-id="ce60a-117">Equality Comparisons</span></span>](../../../csharp/programming-guide/statements-expressions-operators/equality-comparisons.md)
