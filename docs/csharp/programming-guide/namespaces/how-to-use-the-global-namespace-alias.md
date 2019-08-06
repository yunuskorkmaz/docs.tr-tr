---
title: 'Nasıl yapılır: Genel ad alanı diğer ad C# programlama kılavuzunu kullanın'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- aliases [C#]
- namespaces [C#], global namespace qualifier
- global namespace [C#]
ms.assetid: 98a1d89b-3c5a-44f7-8400-c4a3c0ec22a9
ms.openlocfilehash: b163981d3cf6d56ab953757931b0b386a47263ff
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796282"
---
# <a name="how-to-use-the-global-namespace-alias-c-programming-guide"></a><span data-ttu-id="1946d-102">Nasıl yapılır: Genel ad alanı diğer adını kullanınC# (Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="1946d-102">How to: Use the Global Namespace Alias (C# Programming Guide)</span></span>
<span data-ttu-id="1946d-103">Genel [ad](../../../csharp/language-reference/keywords/namespace.md) alanındaki bir üyeye erişme özelliği, üyenin aynı ada sahip başka bir varlık tarafından gizlenmesi durumunda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="1946d-103">The ability to access a member in the global [namespace](../../../csharp/language-reference/keywords/namespace.md) is useful when the member might be hidden by another entity of the same name.</span></span>  
  
 <span data-ttu-id="1946d-104">Örneğin, aşağıdaki `Console` kodda, <xref:System> ad alanındaki `Console` türü yerine öğesine `TestApp.Console` çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="1946d-104">For example, in the following code, `Console` resolves to `TestApp.Console` instead of to the `Console` type in the <xref:System> namespace.</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 [!code-csharp[csProgGuideNamespaces#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#1)]  
  
 <span data-ttu-id="1946d-105">Ad `System.Console` alanı sınıf `System` tarafından`TestApp.System`gizlendiğinden, hâlâ bir hata ile sonuçlanır:</span><span class="sxs-lookup"><span data-stu-id="1946d-105">Using `System.Console` still results in an error because the `System` namespace is hidden by the class `TestApp.System`:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#2)]  
  
 <span data-ttu-id="1946d-106">Bununla birlikte, aşağıdaki gibi kullanarak `global::System.Console`bu hatayı geçici olarak çözebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1946d-106">However, you can work around this error by using `global::System.Console`, like this:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#3)]  
  
 <span data-ttu-id="1946d-107">Sol tanımlayıcı `global`olduğunda, doğru tanımlayıcı için arama genel ad alanında başlar.</span><span class="sxs-lookup"><span data-stu-id="1946d-107">When the left identifier is `global`, the search for the right identifier starts at the global namespace.</span></span> <span data-ttu-id="1946d-108">Örneğin, aşağıdaki bildirim genel alanın bir üyesi `TestApp` olarak başvuru yapılır.</span><span class="sxs-lookup"><span data-stu-id="1946d-108">For example, the following declaration is referencing `TestApp` as a member of the global space.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#4)]  
  
 <span data-ttu-id="1946d-109">Kuşkusuz, adlı `System` kendi ad alanlarınızı oluşturmanız önerilmez ve bunun gerçekleştiği bir kodla karşılaşmanız düşüktür.</span><span class="sxs-lookup"><span data-stu-id="1946d-109">Obviously, creating your own namespaces called `System` is not recommended, and it is unlikely you will encounter any code in which this has happened.</span></span> <span data-ttu-id="1946d-110">Ancak, daha büyük projelerde ad alanı çoğaltmasının tek bir formda veya başka bir biçimde gerçekleşebileceğini çok gerçek bir olasılık.</span><span class="sxs-lookup"><span data-stu-id="1946d-110">However, in larger projects, it is a very real possibility that namespace duplication may occur in one form or another.</span></span> <span data-ttu-id="1946d-111">Bu durumlarda, genel ad alanı niteleyicisi, kök ad alanını belirleyebilmenizi güvence altına alabilir.</span><span class="sxs-lookup"><span data-stu-id="1946d-111">In these situations, the global namespace qualifier is your guarantee that you can specify the root namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1946d-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1946d-112">See also</span></span>

- [<span data-ttu-id="1946d-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1946d-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="1946d-114">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="1946d-114">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)
- [<span data-ttu-id="1946d-115">:: İşleç</span><span class="sxs-lookup"><span data-stu-id="1946d-115">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="1946d-116">extern</span><span class="sxs-lookup"><span data-stu-id="1946d-116">extern</span></span>](../../../csharp/language-reference/keywords/extern.md)
