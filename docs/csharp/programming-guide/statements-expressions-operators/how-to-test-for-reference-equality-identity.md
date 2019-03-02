---
title: 'Nasıl yapılır: (Kimlik) - başvuru eşitliği testi C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- object identity [C#]
- reference equality [C#]
ms.assetid: 91307fda-267b-4fd2-a338-2aada39ee791
ms.openlocfilehash: 057532cae42d7a0b6d11750ae0e33e43108cfda9
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57203593"
---
# <a name="how-to-test-for-reference-equality-identity-c-programming-guide"></a><span data-ttu-id="e7168-102">Nasıl yapılır: (Kimlik) başvuru eşitliği testi (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="e7168-102">How to: Test for Reference Equality (Identity) (C# Programming Guide)</span></span>
<span data-ttu-id="e7168-103">Referans eşitlik karşılaştırmaları, türlerini desteklemek için tüm özel mantığı uygulamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e7168-103">You do not have to implement any custom logic to support reference equality comparisons in your types.</span></span> <span data-ttu-id="e7168-104">Bu işlev tarafından statik tüm türleri için sağlanan <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e7168-104">This functionality is provided for all types by the static <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="e7168-105">Aşağıdaki örnek, iki değişken sahip olup olmadığını belirlemek gösterilmektedir *eşitlik*, bellekte aynı nesneye başvuruda bulunan anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e7168-105">The following example shows how to determine whether two variables have *reference equality*, which means that they refer to the same object in memory.</span></span>  
  
 <span data-ttu-id="e7168-106">Örnek ayrıca neden gösterir <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> her zaman döndürür `false` değer türleri ve neden kullanmamalısınız <xref:System.Object.ReferenceEquals%2A> dize eşitliğini belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="e7168-106">The example also shows why <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> always returns `false` for value types and why you should not use  <xref:System.Object.ReferenceEquals%2A> to determine string equality.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7168-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="e7168-107">Example</span></span>  
 [!code-csharp[csProgGuideObjects#90](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#90)]  
  
 <span data-ttu-id="e7168-108">Uygulamasını `Equals` içinde <xref:System.Object?displayProperty=nameWithType> Evrensel temel sınıfı da bir referans eşitlik kontrolüne gerçekleştirir, ancak beklediğiniz sonuçları bir sınıf yöntemini geçersiz kılmak için devre dışı durumda olmayabileceğinden, bu kullanmak en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="e7168-108">The implementation of `Equals` in the <xref:System.Object?displayProperty=nameWithType> universal base class also performs a reference equality check, but it is best not to use this because, if a class happens to override the method, the results might not be what you expect.</span></span> <span data-ttu-id="e7168-109">Aynı true `==` ve `!=` işleçleri.</span><span class="sxs-lookup"><span data-stu-id="e7168-109">The same is true for the `==` and `!=` operators.</span></span> <span data-ttu-id="e7168-110">Türleri başvuru üzerinde ne zaman işletim, varsayılan davranışını `==` ve `!=` referans eşitlik kontrolüne gerçekleştirmektir.</span><span class="sxs-lookup"><span data-stu-id="e7168-110">When they are operating on reference types, the default behavior of `==` and `!=` is to perform a reference equality check.</span></span> <span data-ttu-id="e7168-111">Ancak, türetilen sınıfların bir değer eşitliği denetimi gerçekleştirmek için işleç aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="e7168-111">However, derived classes can overload the operator to perform a value equality check.</span></span> <span data-ttu-id="e7168-112">Hata olasılığını en aza indirmek için her zaman kullanmak en iyisidir <xref:System.Object.ReferenceEquals%2A> varsa iki nesne başvuru eşitliğine sahip olup olmadığını belirlemek.</span><span class="sxs-lookup"><span data-stu-id="e7168-112">To minimize the potential for error, it is best to always use <xref:System.Object.ReferenceEquals%2A> when you have to determine whether two objects have reference equality.</span></span>  
  
 <span data-ttu-id="e7168-113">Her zaman aynı bütünleştirilmiş kod içinde sabit dizelerini çalışma zamanı tarafından interned.</span><span class="sxs-lookup"><span data-stu-id="e7168-113">Constant strings within the same assembly are always interned by the runtime.</span></span> <span data-ttu-id="e7168-114">Diğer bir deyişle, her benzersiz bir değişmez değer dize yalnızca bir örneğini korunur.</span><span class="sxs-lookup"><span data-stu-id="e7168-114">That is, only one instance of each unique literal string is maintained.</span></span> <span data-ttu-id="e7168-115">Ancak, çalışma zamanı dizeleri çalışma zamanında oluşturulan interned veya iki eşit sabit dizelerini farklı derlemelerde interned olduğunu garanti etmez garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="e7168-115">However, the runtime does not guarantee that strings created at runtime are interned, nor does it guarantee that two equal constant strings in different assemblies are interned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7168-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7168-116">See also</span></span>

- [<span data-ttu-id="e7168-117">Eşitlik Karşılaştırmaları</span><span class="sxs-lookup"><span data-stu-id="e7168-117">Equality Comparisons</span></span>](../../../csharp/programming-guide/statements-expressions-operators/equality-comparisons.md)
