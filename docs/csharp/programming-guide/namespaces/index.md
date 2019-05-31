---
title: Ad alanları - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 893ac7bbfcfe159787789238c3142f34ac7ecf35
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423295"
---
# <a name="namespaces-c-programming-guide"></a><span data-ttu-id="76c95-102">Ad Alanları (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="76c95-102">Namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="76c95-103">Ad alanlarında, C# programlama iki yolla yoğun olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="76c95-103">Namespaces are heavily used in C# programming in two ways.</span></span> <span data-ttu-id="76c95-104">İlk olarak, .NET Framework ad alanları, çok sayıda sınıfa gibi düzenlemek için kullanır:</span><span class="sxs-lookup"><span data-stu-id="76c95-104">First, the .NET Framework uses namespaces to organize its many classes, as follows:</span></span>  
  
 [!code-csharp[csProgGuide#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#22)]  
  
<span data-ttu-id="76c95-105">`System` bir ad alanı ve `Console` bu ad alanındaki bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="76c95-105">`System` is a namespace and `Console` is a class in that namespace.</span></span> <span data-ttu-id="76c95-106">`using` Anahtar sözcüğü kullanılabilir, böylece tam adı, aşağıdaki örnekte olduğu gibi gerekli değildir:</span><span class="sxs-lookup"><span data-stu-id="76c95-106">The `using` keyword can be used so that the complete name is not required, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 [!code-csharp[csProgGuide#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#25)]  
  
<span data-ttu-id="76c95-107">Daha fazla bilgi için [using yönergesi](../../language-reference/keywords/using-directive.md).</span><span class="sxs-lookup"><span data-stu-id="76c95-107">For more information, see the [using Directive](../../language-reference/keywords/using-directive.md).</span></span>  
  
<span data-ttu-id="76c95-108">İkinci olarak, kendi ad alanlarını bildirme sınıf ve yöntem adları büyük programlama projelerinde kapsamını denetlemenize yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="76c95-108">Second, declaring your own namespaces can help you control the scope of class and method names in larger programming projects.</span></span> <span data-ttu-id="76c95-109">Kullanım [ad alanı](../../language-reference/keywords/namespace.md) aşağıdaki örnekteki gibi bir ad alanı bildirmek için anahtar:</span><span class="sxs-lookup"><span data-stu-id="76c95-109">Use the [namespace](../../language-reference/keywords/namespace.md) keyword to declare a namespace, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#6)]

<span data-ttu-id="76c95-110">Ad geçerli C# olmalıdır [tanımlayıcı adı](../inside-a-program/identifier-names.md).</span><span class="sxs-lookup"><span data-stu-id="76c95-110">The name of the namespace must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span>

## <a name="namespaces-overview"></a><span data-ttu-id="76c95-111">Ad alanlarına genel bakış</span><span class="sxs-lookup"><span data-stu-id="76c95-111">Namespaces Overview</span></span>  

<span data-ttu-id="76c95-112">Ad alanları, aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="76c95-112">Namespaces have the following properties:</span></span>  
  
- <span data-ttu-id="76c95-113">Bunlar, büyük kod projeleri düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="76c95-113">They organize large code projects.</span></span>  
- <span data-ttu-id="76c95-114">Kullanarak sınırlandırılmıştır `.` işleci.</span><span class="sxs-lookup"><span data-stu-id="76c95-114">They are delimited by using the `.` operator.</span></span>  
- <span data-ttu-id="76c95-115">`using` Yönergesi obviates gereksinimi her sınıf ad alanının adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="76c95-115">The `using` directive obviates the requirement to specify the name of the namespace for every class.</span></span>  
- <span data-ttu-id="76c95-116">`global` Ad "Kök" ad alanı: `global::System` .NET için her zaman başvuracaktır <xref:System> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="76c95-116">The `global` namespace is the "root" namespace: `global::System` will always refer to the .NET <xref:System> namespace.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="76c95-117">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="76c95-117">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="76c95-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76c95-118">See also</span></span>

- [<span data-ttu-id="76c95-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="76c95-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="76c95-120">Ad Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="76c95-120">Using Namespaces</span></span>](using-namespaces.md)
- [<span data-ttu-id="76c95-121">Nasıl yapılır: Genel Namespace diğer adlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="76c95-121">How to: Use the Global Namespace Alias</span></span>](how-to-use-the-global-namespace-alias.md)
- [<span data-ttu-id="76c95-122">Nasıl yapılır: Kullanım My Namespace</span><span class="sxs-lookup"><span data-stu-id="76c95-122">How to: Use the My Namespace</span></span>](how-to-use-the-my-namespace.md)
- [<span data-ttu-id="76c95-123">Tanımlayıcı adları</span><span class="sxs-lookup"><span data-stu-id="76c95-123">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="76c95-124">using Yönergesi</span><span class="sxs-lookup"><span data-stu-id="76c95-124">using Directive</span></span>](../../language-reference/keywords/using-directive.md)
- [<span data-ttu-id="76c95-125">:: İşleç</span><span class="sxs-lookup"><span data-stu-id="76c95-125">:: Operator</span></span>](../../language-reference/operators/namespace-alias-qualifer.md)
