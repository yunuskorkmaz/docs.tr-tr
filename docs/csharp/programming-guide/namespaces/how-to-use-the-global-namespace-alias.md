---
title: 'Nasıl yapılır: Genel - Namespace diğer kullanın C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- aliases [C#]
- namespaces [C#], global namespace qualifier
- global namespace [C#]
ms.assetid: 98a1d89b-3c5a-44f7-8400-c4a3c0ec22a9
ms.openlocfilehash: 6d3e0740a472f74116712e737e49f86d4202dea5
ms.sourcegitcommit: 4c10802ad003374641a2c2373b8a92e3c88babc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65452796"
---
# <a name="how-to-use-the-global-namespace-alias-c-programming-guide"></a><span data-ttu-id="365e7-102">Nasıl yapılır: Genel Namespace diğer adlarını kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="365e7-102">How to: Use the Global Namespace Alias (C# Programming Guide)</span></span>
<span data-ttu-id="365e7-103">Genel bir üyeye erişme olanağı [ad alanı](../../../csharp/language-reference/keywords/namespace.md) üye aynı ada sahip başka bir varlık tarafından gizlenmiş olabilir durumlarda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="365e7-103">The ability to access a member in the global [namespace](../../../csharp/language-reference/keywords/namespace.md) is useful when the member might be hidden by another entity of the same name.</span></span>  
  
 <span data-ttu-id="365e7-104">Örneğin, aşağıdaki kodda, `Console` çözümler `TestApp.Console` çok yerine `Console` yazın <xref:System> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="365e7-104">For example, in the following code, `Console` resolves to `TestApp.Console` instead of to the `Console` type in the <xref:System> namespace.</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 [!code-csharp[csProgGuideNamespaces#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#1)]  
  
 <span data-ttu-id="365e7-105">Kullanarak `System.Console` olduğundan hata sonuçları hala `System` ad alanı, sınıf tarafından gizlenir `TestApp.System`:</span><span class="sxs-lookup"><span data-stu-id="365e7-105">Using `System.Console` still results in an error because the `System` namespace is hidden by the class `TestApp.System`:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#2)]  
  
 <span data-ttu-id="365e7-106">Kullanarak bu hatayı çözmek ancak çalışabilirsiniz `global::System.Console`, şöyle:</span><span class="sxs-lookup"><span data-stu-id="365e7-106">However, you can work around this error by using `global::System.Console`, like this:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#3)]  
  
 <span data-ttu-id="365e7-107">Sol tanımlayıcısı olduğunda `global`, aramayı sağ tanımlayıcısı için genel ad alanında başlatır.</span><span class="sxs-lookup"><span data-stu-id="365e7-107">When the left identifier is `global`, the search for the right identifier starts at the global namespace.</span></span> <span data-ttu-id="365e7-108">Örneğin, aşağıdaki bildirimi başvuruyor `TestApp` genel alanının bir üyesi olarak.</span><span class="sxs-lookup"><span data-stu-id="365e7-108">For example, the following declaration is referencing `TestApp` as a member of the global space.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#4)]  
  
 <span data-ttu-id="365e7-109">Kuşkusuz, kendi ad alanları oluşturma adlı `System` önerilmez ve herhangi bir kod da gerçekleştiği karşılaşırsınız düşüktür.</span><span class="sxs-lookup"><span data-stu-id="365e7-109">Obviously, creating your own namespaces called `System` is not recommended, and it is unlikely you will encounter any code in which this has happened.</span></span> <span data-ttu-id="365e7-110">Ancak, daha büyük projelerinde, bir form veya başka bir ad alanı çoğaltma oluşabilir olasılığı yüksektir olur.</span><span class="sxs-lookup"><span data-stu-id="365e7-110">However, in larger projects, it is a very real possibility that namespace duplication may occur in one form or another.</span></span> <span data-ttu-id="365e7-111">Bu durumda, genel ad alanı niteleyicisi kök ad belirtebilirsiniz, bir garanti sağlar.</span><span class="sxs-lookup"><span data-stu-id="365e7-111">In these situations, the global namespace qualifier is your guarantee that you can specify the root namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="365e7-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="365e7-112">Example</span></span>  
 <span data-ttu-id="365e7-113">Bu örnekte, ad alanı `System` sınıfı eklemek için kullanılan `TestClass` bu nedenle, `global::System.Console` kullanılmalıdır başvurusuna `System.Console` tarafından gizlenmiş sınıfı `System` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="365e7-113">In this example, the namespace `System` is used to include the class `TestClass` therefore, `global::System.Console` must be used to reference the `System.Console` class, which is hidden by the `System` namespace.</span></span> <span data-ttu-id="365e7-114">Ayrıca, diğer `colAlias` ad alanına başvurmak için kullanılan `System.Collections`; bu nedenle, örneği bir <xref:System.Collections.Hashtable?displayProperty=nameWithType> ad alanı yerine bu diğer adı kullanılarak oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="365e7-114">Also, the alias `colAlias` is used to refer to the namespace `System.Collections`; therefore, the instance of a <xref:System.Collections.Hashtable?displayProperty=nameWithType> was created using this alias instead of the namespace.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#5)]  
  
<span data-ttu-id="365e7-115">**1**
**B 2**
**3 C**</span><span class="sxs-lookup"><span data-stu-id="365e7-115">**A 1**
**B 2**
**C 3**</span></span>

## <a name="see-also"></a><span data-ttu-id="365e7-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="365e7-116">See also</span></span>

- [<span data-ttu-id="365e7-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="365e7-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="365e7-118">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="365e7-118">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)
- [<span data-ttu-id="365e7-119">:: İşleç</span><span class="sxs-lookup"><span data-stu-id="365e7-119">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)
- [<span data-ttu-id="365e7-120">extern</span><span class="sxs-lookup"><span data-stu-id="365e7-120">extern</span></span>](../../../csharp/language-reference/keywords/extern.md)
