---
title: "Nasıl yapılır: Genel Ad Alanı Diğer Adlarını Kullanma (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- aliases [C#]
- namespaces [C#], global namespace qualifier
- global namespace [C#]
ms.assetid: 98a1d89b-3c5a-44f7-8400-c4a3c0ec22a9
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f2a854d2f963578cb8b89da445af660f3c029fae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-global-namespace-alias-c-programming-guide"></a><span data-ttu-id="a0996-102">Nasıl yapılır: Genel Ad Alanı Diğer Adlarını Kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="a0996-102">How to: Use the Global Namespace Alias (C# Programming Guide)</span></span>
<span data-ttu-id="a0996-103">Genel olarak bir üyeye erişme olanağı [ad alanı](../../../csharp/language-reference/keywords/namespace.md) üye aynı ada sahip başka bir varlık tarafından gizlenebilir durumlarda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="a0996-103">The ability to access a member in the global [namespace](../../../csharp/language-reference/keywords/namespace.md) is useful when the member might be hidden by another entity of the same name.</span></span>  
  
 <span data-ttu-id="a0996-104">Örneğin, aşağıdaki kodda, `Console` çözümler `TestApp.Console` çok yerine `Console` yazın <xref:System> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="a0996-104">For example, in the following code, `Console` resolves to `TestApp.Console` instead of to the `Console` type in the <xref:System> namespace.</span></span>  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-use-the-global-namespace-alias_1.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#1](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_2.cs)]  
  
 <span data-ttu-id="a0996-105">Kullanarak `System.Console` çünkü hatayla sonuçlanır hala `System` ad alanı sınıf tarafından gizli `TestApp.System`:</span><span class="sxs-lookup"><span data-stu-id="a0996-105">Using `System.Console` still results in an error because the `System` namespace is hidden by the class `TestApp.System`:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#2](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_3.cs)]  
  
 <span data-ttu-id="a0996-106">Ancak, kullanarak bu hata için geçici çözüm bulabilirsiniz `global::System.Console`, şöyle:</span><span class="sxs-lookup"><span data-stu-id="a0996-106">However, you can work around this error by using `global::System.Console`, like this:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#3](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_4.cs)]  
  
 <span data-ttu-id="a0996-107">Sol tanımlayıcı olduğunda `global`, arama sağ tanımlayıcısı için genel ad alanında başlatır.</span><span class="sxs-lookup"><span data-stu-id="a0996-107">When the left identifier is `global`, the search for the right identifier starts at the global namespace.</span></span> <span data-ttu-id="a0996-108">Örneğin, aşağıdaki bildirimi başvuran `TestApp` genel alanının bir üyesi olarak.</span><span class="sxs-lookup"><span data-stu-id="a0996-108">For example, the following declaration is referencing `TestApp` as a member of the global space.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#4](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_5.cs)]  
  
 <span data-ttu-id="a0996-109">Belli ki, kendi ad alanları oluşturma adlı `System` tavsiye edilmez ve bu oluşmuş herhangi bir kod karşılaşırsınız düşüktür.</span><span class="sxs-lookup"><span data-stu-id="a0996-109">Obviously, creating your own namespaces called `System` is not recommended, and it is unlikely you will encounter any code in which this has happened.</span></span> <span data-ttu-id="a0996-110">Ancak, daha büyük projelerde bir form veya başka bir ad alanı çoğaltma oluşabilir çok gerçek olasılığı vardır.</span><span class="sxs-lookup"><span data-stu-id="a0996-110">However, in larger projects, it is a very real possibility that namespace duplication may occur in one form or another.</span></span> <span data-ttu-id="a0996-111">Bu durumda, genel ad alanı niteleyicisi kök ad alanını belirtebilirsiniz, garantisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a0996-111">In these situations, the global namespace qualifier is your guarantee that you can specify the root namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0996-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="a0996-112">Example</span></span>  
 <span data-ttu-id="a0996-113">Bu örnekte, ad alanı `System` sınıfı eklemek için kullanılan `TestClass` bu nedenle, `global::System.Console` kullanılmalıdır başvuru `System.Console` tarafından gizli sınıfı `System` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="a0996-113">In this example, the namespace `System` is used to include the class `TestClass` therefore, `global::System.Console` must be used to reference the `System.Console` class, which is hidden by the `System` namespace.</span></span> <span data-ttu-id="a0996-114">Ayrıca, diğer ad `colAlias` ad alanına başvurmak için kullanılan `System.Collections`; bu nedenle, örneği bir <xref:System.Collections.Hashtable?displayProperty=nameWithType> ad alanı yerine bu diğer adı kullanılarak oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="a0996-114">Also, the alias `colAlias` is used to refer to the namespace `System.Collections`; therefore, the instance of a <xref:System.Collections.Hashtable?displayProperty=nameWithType> was created using this alias instead of the namespace.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#5](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_6.cs)]  
  
 <span data-ttu-id="a0996-115">**1**</span><span class="sxs-lookup"><span data-stu-id="a0996-115">**A 1**</span></span>  
<span data-ttu-id="a0996-116">**B 2**</span><span class="sxs-lookup"><span data-stu-id="a0996-116">**B 2**</span></span>  
<span data-ttu-id="a0996-117">**C 3**</span><span class="sxs-lookup"><span data-stu-id="a0996-117">**C 3**</span></span>   
## <a name="see-also"></a><span data-ttu-id="a0996-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a0996-118">See Also</span></span>  
 [<span data-ttu-id="a0996-119">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a0996-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a0996-120">Ad alanları</span><span class="sxs-lookup"><span data-stu-id="a0996-120">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
 [<span data-ttu-id="a0996-121">. İşleci</span><span class="sxs-lookup"><span data-stu-id="a0996-121">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)  
 [<span data-ttu-id="a0996-122">:: İşleci</span><span class="sxs-lookup"><span data-stu-id="a0996-122">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [<span data-ttu-id="a0996-123">extern</span><span class="sxs-lookup"><span data-stu-id="a0996-123">extern</span></span>](../../../csharp/language-reference/keywords/extern.md)
