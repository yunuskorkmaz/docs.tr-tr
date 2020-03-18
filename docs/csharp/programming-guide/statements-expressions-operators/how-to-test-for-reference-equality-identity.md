---
title: Referans eşitliği (Identity) için nasıl test yapılır ?
ms.date: 07/20/2015
helpviewer_keywords:
- object identity [C#]
- reference equality [C#]
ms.assetid: 91307fda-267b-4fd2-a338-2aada39ee791
ms.openlocfilehash: 77ce2ef0ccf47d619134c120101ba2aa04f485e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75699060"
---
# <a name="how-to-test-for-reference-equality-identity-c-programming-guide"></a><span data-ttu-id="12268-102">Referans eşitliği (Identity) (C# Programlama Kılavuzu) için nasıl test yapılır?</span><span class="sxs-lookup"><span data-stu-id="12268-102">How to test for reference equality (Identity) (C# Programming Guide)</span></span>
<span data-ttu-id="12268-103">Türlerinizde başvuru eşitliği karşılaştırmalarını desteklemek için herhangi bir özel mantık uygulamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="12268-103">You do not have to implement any custom logic to support reference equality comparisons in your types.</span></span> <span data-ttu-id="12268-104">Bu işlevsellik statik <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> yöntem ile tüm türler için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="12268-104">This functionality is provided for all types by the static <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="12268-105">Aşağıdaki örnek, iki değişkenin referans *eşitliği*olup olmadığını nasıl belirleyeceklerini gösterir , bu da bellekte aynı nesneye atıfta bulunduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="12268-105">The following example shows how to determine whether two variables have *reference equality*, which means that they refer to the same object in memory.</span></span>  
  
 <span data-ttu-id="12268-106">Örnek, neden <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> her `false` zaman değer türleri için döndürür ve dize eşitliğini belirlemek için neden kullanmamanız <xref:System.Object.ReferenceEquals%2A> gerektiğini de gösterir.</span><span class="sxs-lookup"><span data-stu-id="12268-106">The example also shows why <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> always returns `false` for value types and why you should not use  <xref:System.Object.ReferenceEquals%2A> to determine string equality.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12268-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="12268-107">Example</span></span>  
 [!code-csharp[csProgGuideObjects#90](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#90)]  
  
 <span data-ttu-id="12268-108">Evrensel taban `Equals` sınıfında uygulanması da bir başvuru eşitliği denetimi gerçekleştirir, ancak bir sınıf yöntemi geçersiz kılmak için olur, çünkü bu kullanmak için en iyisidir, sonuçlar beklediğiniz olmayabilir. <xref:System.Object?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="12268-108">The implementation of `Equals` in the <xref:System.Object?displayProperty=nameWithType> universal base class also performs a reference equality check, but it is best not to use this because, if a class happens to override the method, the results might not be what you expect.</span></span> <span data-ttu-id="12268-109">Aynı ve `==` `!=` operatörler için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="12268-109">The same is true for the `==` and `!=` operators.</span></span> <span data-ttu-id="12268-110">Başvuru türlerinde çalışırken, varsayılan davranış `==` ve `!=` bir başvuru eşitliği denetimi gerçekleştirmektir.</span><span class="sxs-lookup"><span data-stu-id="12268-110">When they are operating on reference types, the default behavior of `==` and `!=` is to perform a reference equality check.</span></span> <span data-ttu-id="12268-111">Ancak, türetilen sınıflar bir değer eşitliği denetimi gerçekleştirmek için işleci aşırı yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="12268-111">However, derived classes can overload the operator to perform a value equality check.</span></span> <span data-ttu-id="12268-112">Hata potansiyelini en aza indirmek için, <xref:System.Object.ReferenceEquals%2A> iki nesnenin başvuru eşitliğiolup olmadığını belirlemeniz gerektiğinde her zaman kullanmak en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="12268-112">To minimize the potential for error, it is best to always use <xref:System.Object.ReferenceEquals%2A> when you have to determine whether two objects have reference equality.</span></span>  
  
 <span data-ttu-id="12268-113">Aynı derleme içindeki sabit dizeleri her zaman çalışma süresine göre interned.</span><span class="sxs-lookup"><span data-stu-id="12268-113">Constant strings within the same assembly are always interned by the runtime.</span></span> <span data-ttu-id="12268-114">Diğer bir tanesi, her benzersiz edebi dizenin yalnızca bir örneği korunur.</span><span class="sxs-lookup"><span data-stu-id="12268-114">That is, only one instance of each unique literal string is maintained.</span></span> <span data-ttu-id="12268-115">Ancak, çalışma zamanı, çalışma zamanında oluşturulan dizeleri interned garanti etmez, ne de farklı derlemelerde iki eşit sabit dizeleri interned garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="12268-115">However, the runtime does not guarantee that strings created at runtime are interned, nor does it guarantee that two equal constant strings in different assemblies are interned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12268-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12268-116">See also</span></span>

- [<span data-ttu-id="12268-117">Eşitlik Karşılaştırmaları</span><span class="sxs-lookup"><span data-stu-id="12268-117">Equality Comparisons</span></span>](./equality-comparisons.md)
