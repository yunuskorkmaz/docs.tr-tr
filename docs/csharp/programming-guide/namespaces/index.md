---
title: Ad alanları C# -Programlama Kılavuzu
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 79b7057b1f6a9cdba2215124160b28efb9a1c0be
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629527"
---
# <a name="namespaces-c-programming-guide"></a><span data-ttu-id="fc73a-102">Ad Alanları (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="fc73a-102">Namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="fc73a-103">Ad alanları, C# programlamada iki şekilde çok fazla kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fc73a-103">Namespaces are heavily used in C# programming in two ways.</span></span> <span data-ttu-id="fc73a-104">İlk olarak .NET Framework, aşağıdaki gibi birçok sınıfını düzenlemek için ad alanlarını kullanır:</span><span class="sxs-lookup"><span data-stu-id="fc73a-104">First, the .NET Framework uses namespaces to organize its many classes, as follows:</span></span>  
  
 [!code-csharp[csProgGuide#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#22)]  
  
<span data-ttu-id="fc73a-105">`System`bir ad alanıdır ve `Console` bu ad alanındaki bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="fc73a-105">`System` is a namespace and `Console` is a class in that namespace.</span></span> <span data-ttu-id="fc73a-106">`using` Anahtar sözcüğü, aşağıdaki örnekte olduğu gibi, tüm adı gerekli olmaması için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="fc73a-106">The `using` keyword can be used so that the complete name is not required, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 [!code-csharp[csProgGuide#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#25)]  
  
<span data-ttu-id="fc73a-107">Daha fazla bilgi için bkz. [using yönergesi](../../language-reference/keywords/using-directive.md).</span><span class="sxs-lookup"><span data-stu-id="fc73a-107">For more information, see the [using Directive](../../language-reference/keywords/using-directive.md).</span></span>  
  
<span data-ttu-id="fc73a-108">İkincisi, kendi ad alanlarınızı bildirmek daha büyük programlama projelerindeki sınıf ve yöntem adlarının kapsamını denetlemenize yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="fc73a-108">Second, declaring your own namespaces can help you control the scope of class and method names in larger programming projects.</span></span> <span data-ttu-id="fc73a-109">Aşağıdaki örnekte olduğu gibi bir ad alanı bildirmek için [Namespace](../../language-reference/keywords/namespace.md) anahtar sözcüğünü kullanın:</span><span class="sxs-lookup"><span data-stu-id="fc73a-109">Use the [namespace](../../language-reference/keywords/namespace.md) keyword to declare a namespace, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#6)]

<span data-ttu-id="fc73a-110">Ad alanının adı geçerli C# bir [tanımlayıcı adı](../inside-a-program/identifier-names.md)olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fc73a-110">The name of the namespace must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span>

## <a name="namespaces-overview"></a><span data-ttu-id="fc73a-111">Ad alanlarına genel bakış</span><span class="sxs-lookup"><span data-stu-id="fc73a-111">Namespaces Overview</span></span>  

<span data-ttu-id="fc73a-112">Ad alanları aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="fc73a-112">Namespaces have the following properties:</span></span>  
  
- <span data-ttu-id="fc73a-113">Büyük kod projelerini düzenler.</span><span class="sxs-lookup"><span data-stu-id="fc73a-113">They organize large code projects.</span></span>  
- <span data-ttu-id="fc73a-114">`.` İşleci kullanılarak sınırlandırılır.</span><span class="sxs-lookup"><span data-stu-id="fc73a-114">They are delimited by using the `.` operator.</span></span>  
- <span data-ttu-id="fc73a-115">`using` Yönergesi, her sınıf için ad alanının adını belirtmek için gereksinimi obviates.</span><span class="sxs-lookup"><span data-stu-id="fc73a-115">The `using` directive obviates the requirement to specify the name of the namespace for every class.</span></span>  
- <span data-ttu-id="fc73a-116">Ad alanı "root" ad alanıdır: `global::System` her zaman .net <xref:System> ad alanına başvurur. `global`</span><span class="sxs-lookup"><span data-stu-id="fc73a-116">The `global` namespace is the "root" namespace: `global::System` will always refer to the .NET <xref:System> namespace.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="fc73a-117">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="fc73a-117">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fc73a-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc73a-118">See also</span></span>

- [<span data-ttu-id="fc73a-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="fc73a-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="fc73a-120">Ad Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="fc73a-120">Using Namespaces</span></span>](using-namespaces.md)
- [<span data-ttu-id="fc73a-121">Nasıl yapılır: Genel ad alanı diğer adını kullan</span><span class="sxs-lookup"><span data-stu-id="fc73a-121">How to: Use the Global Namespace Alias</span></span>](how-to-use-the-global-namespace-alias.md)
- [<span data-ttu-id="fc73a-122">Nasıl yapılır: My Namespace 'i kullanma</span><span class="sxs-lookup"><span data-stu-id="fc73a-122">How to: Use the My Namespace</span></span>](how-to-use-the-my-namespace.md)
- [<span data-ttu-id="fc73a-123">Tanımlayıcı adları</span><span class="sxs-lookup"><span data-stu-id="fc73a-123">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="fc73a-124">using Yönergesi</span><span class="sxs-lookup"><span data-stu-id="fc73a-124">using Directive</span></span>](../../language-reference/keywords/using-directive.md)
- [<span data-ttu-id="fc73a-125">:: İşleç</span><span class="sxs-lookup"><span data-stu-id="fc73a-125">:: Operator</span></span>](../../language-reference/operators/namespace-alias-qualifier.md)
