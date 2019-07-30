---
title: 'Nasıl yapılır: Genel ad alanı diğer ad C# programlama kılavuzunu kullanın'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- aliases [C#]
- namespaces [C#], global namespace qualifier
- global namespace [C#]
ms.assetid: 98a1d89b-3c5a-44f7-8400-c4a3c0ec22a9
ms.openlocfilehash: f44bb1f010f154973fc6982882c9b5a09528da76
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629448"
---
# <a name="how-to-use-the-global-namespace-alias-c-programming-guide"></a><span data-ttu-id="da01a-102">Nasıl yapılır: Genel ad alanı diğer adını kullanınC# (Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="da01a-102">How to: Use the Global Namespace Alias (C# Programming Guide)</span></span>
<span data-ttu-id="da01a-103">Genel [ad](../../../csharp/language-reference/keywords/namespace.md) alanındaki bir üyeye erişme özelliği, üyenin aynı ada sahip başka bir varlık tarafından gizlenmesi durumunda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="da01a-103">The ability to access a member in the global [namespace](../../../csharp/language-reference/keywords/namespace.md) is useful when the member might be hidden by another entity of the same name.</span></span>  
  
 <span data-ttu-id="da01a-104">Örneğin, aşağıdaki `Console` kodda, <xref:System> ad alanındaki `Console` türü yerine öğesine `TestApp.Console` çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="da01a-104">For example, in the following code, `Console` resolves to `TestApp.Console` instead of to the `Console` type in the <xref:System> namespace.</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 [!code-csharp[csProgGuideNamespaces#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#1)]  
  
 <span data-ttu-id="da01a-105">Ad `System.Console` alanı sınıf `System` tarafından`TestApp.System`gizlendiğinden, hâlâ bir hata ile sonuçlanır:</span><span class="sxs-lookup"><span data-stu-id="da01a-105">Using `System.Console` still results in an error because the `System` namespace is hidden by the class `TestApp.System`:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#2)]  
  
 <span data-ttu-id="da01a-106">Bununla birlikte, aşağıdaki gibi kullanarak `global::System.Console`bu hatayı geçici olarak çözebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="da01a-106">However, you can work around this error by using `global::System.Console`, like this:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#3)]  
  
 <span data-ttu-id="da01a-107">Sol tanımlayıcı `global`olduğunda, doğru tanımlayıcı için arama genel ad alanında başlar.</span><span class="sxs-lookup"><span data-stu-id="da01a-107">When the left identifier is `global`, the search for the right identifier starts at the global namespace.</span></span> <span data-ttu-id="da01a-108">Örneğin, aşağıdaki bildirim genel alanın bir üyesi `TestApp` olarak başvuru yapılır.</span><span class="sxs-lookup"><span data-stu-id="da01a-108">For example, the following declaration is referencing `TestApp` as a member of the global space.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#4)]  
  
 <span data-ttu-id="da01a-109">Kuşkusuz, adlı `System` kendi ad alanlarınızı oluşturmanız önerilmez ve bunun gerçekleştiği bir kodla karşılaşmanız düşüktür.</span><span class="sxs-lookup"><span data-stu-id="da01a-109">Obviously, creating your own namespaces called `System` is not recommended, and it is unlikely you will encounter any code in which this has happened.</span></span> <span data-ttu-id="da01a-110">Ancak, daha büyük projelerde ad alanı çoğaltmasının tek bir formda veya başka bir biçimde gerçekleşebileceğini çok gerçek bir olasılık.</span><span class="sxs-lookup"><span data-stu-id="da01a-110">However, in larger projects, it is a very real possibility that namespace duplication may occur in one form or another.</span></span> <span data-ttu-id="da01a-111">Bu durumlarda, genel ad alanı niteleyicisi, kök ad alanını belirleyebilmenizi güvence altına alabilir.</span><span class="sxs-lookup"><span data-stu-id="da01a-111">In these situations, the global namespace qualifier is your guarantee that you can specify the root namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da01a-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="da01a-112">Example</span></span>  
 <span data-ttu-id="da01a-113">Bu örnekte, ad alanı `System` sınıfı `TestClass` eklemek için kullanılır, bu nedenle, `global::System.Console` `System` ad alanı tarafından gizlenen `System.Console` sınıfa başvurmak için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="da01a-113">In this example, the namespace `System` is used to include the class `TestClass` therefore, `global::System.Console` must be used to reference the `System.Console` class, which is hidden by the `System` namespace.</span></span> <span data-ttu-id="da01a-114">Ayrıca, diğer `colAlias` ad ad alanına `System.Collections`başvurmak için kullanılır; bu nedenle <xref:System.Collections.Hashtable?displayProperty=nameWithType> , öğesinin örneği ad alanı yerine bu diğer ad kullanılarak oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="da01a-114">Also, the alias `colAlias` is used to refer to the namespace `System.Collections`; therefore, the instance of a <xref:System.Collections.Hashtable?displayProperty=nameWithType> was created using this alias instead of the namespace.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#5)]  
  
<span data-ttu-id="da01a-115">**A 1**
**B 2**
**C 3**</span><span class="sxs-lookup"><span data-stu-id="da01a-115">**A 1**
**B 2**
**C 3**</span></span>

## <a name="see-also"></a><span data-ttu-id="da01a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da01a-116">See also</span></span>

- [<span data-ttu-id="da01a-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="da01a-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="da01a-118">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="da01a-118">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)
- [<span data-ttu-id="da01a-119">:: İşleç</span><span class="sxs-lookup"><span data-stu-id="da01a-119">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="da01a-120">extern</span><span class="sxs-lookup"><span data-stu-id="da01a-120">extern</span></span>](../../../csharp/language-reference/keywords/extern.md)
