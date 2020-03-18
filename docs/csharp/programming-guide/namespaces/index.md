---
title: İsim Alanları - C# Programlama Kılavuzu
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 21452e259596c9ab10b3d653ec1d8fb90fad131d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75937607"
---
# <a name="namespaces-c-programming-guide"></a><span data-ttu-id="1cb0e-102">Ad Alanları (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="1cb0e-102">Namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="1cb0e-103">Ad boşlukları C# programlamada iki şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1cb0e-103">Namespaces are heavily used in C# programming in two ways.</span></span> <span data-ttu-id="1cb0e-104">İlk olarak, .NET birçok sınıfını düzenlemek için ad boşluklarını aşağıdaki gibi kullanır:</span><span class="sxs-lookup"><span data-stu-id="1cb0e-104">First, .NET uses namespaces to organize its many classes, as follows:</span></span>  

[!code-csharp[csProgGuide#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#22)]

<span data-ttu-id="1cb0e-105"><xref:System>bir ad alanıdır ve <xref:System.Console> bu ad alanında bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="1cb0e-105"><xref:System> is a namespace and <xref:System.Console> is a class in that namespace.</span></span> <span data-ttu-id="1cb0e-106">Anahtar `using` kelime, aşağıdaki örnekte olduğu gibi tam adın gerekli olmaması için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="1cb0e-106">The `using` keyword can be used so that the complete name is not required, as in the following example:</span></span>

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#25)]

<span data-ttu-id="1cb0e-107">Daha fazla bilgi için [bkz.](../../language-reference/keywords/using-directive.md)</span><span class="sxs-lookup"><span data-stu-id="1cb0e-107">For more information, see the [using Directive](../../language-reference/keywords/using-directive.md).</span></span>

<span data-ttu-id="1cb0e-108">İkinci olarak, kendi ad alanlarınızı bildirmek, daha büyük programlama projelerinde sınıf ve yöntem adlarının kapsamını denetlemenize yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="1cb0e-108">Second, declaring your own namespaces can help you control the scope of class and method names in larger programming projects.</span></span> <span data-ttu-id="1cb0e-109">Aşağıdaki örnekte olduğu gibi ad alanı bildirmek için [ad alanı](../../language-reference/keywords/namespace.md) anahtar sözcük lerini kullanın:</span><span class="sxs-lookup"><span data-stu-id="1cb0e-109">Use the [namespace](../../language-reference/keywords/namespace.md) keyword to declare a namespace, as in the following example:</span></span>

[!code-csharp[csProgGuideNamespaces#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#6)]

<span data-ttu-id="1cb0e-110">Ad alanının adı geçerli bir C# [tanımlayıcı adı](../inside-a-program/identifier-names.md)olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1cb0e-110">The name of the namespace must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span>

## <a name="namespaces-overview"></a><span data-ttu-id="1cb0e-111">Ad boşluklarına genel bakış</span><span class="sxs-lookup"><span data-stu-id="1cb0e-111">Namespaces overview</span></span>

<span data-ttu-id="1cb0e-112">Ad alanları aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="1cb0e-112">Namespaces have the following properties:</span></span>

- <span data-ttu-id="1cb0e-113">Büyük kod projeleri düzenlerler.</span><span class="sxs-lookup"><span data-stu-id="1cb0e-113">They organize large code projects.</span></span>
- <span data-ttu-id="1cb0e-114">`.` İşleç kullanılarak sınırlandırılırlar.</span><span class="sxs-lookup"><span data-stu-id="1cb0e-114">They are delimited by using the `.` operator.</span></span>
- <span data-ttu-id="1cb0e-115">Yönerge, `using` her sınıf için ad alanının adını belirtme gereksinimini ortadan uzatır.</span><span class="sxs-lookup"><span data-stu-id="1cb0e-115">The `using` directive obviates the requirement to specify the name of the namespace for every class.</span></span>
- <span data-ttu-id="1cb0e-116">`global` Ad alanı "kök" ad alanıdır: `global::System` her zaman <xref:System> .NET ad alanına başvurur.</span><span class="sxs-lookup"><span data-stu-id="1cb0e-116">The `global` namespace is the "root" namespace: `global::System` will always refer to the .NET <xref:System> namespace.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1cb0e-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="1cb0e-117">C# language specification</span></span>

<span data-ttu-id="1cb0e-118">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Ad Alanları](~/_csharplang/spec/namespaces.md) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="1cb0e-118">For more information, see the [Namespaces](~/_csharplang/spec/namespaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1cb0e-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1cb0e-119">See also</span></span>

- [<span data-ttu-id="1cb0e-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1cb0e-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1cb0e-121">Ad Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="1cb0e-121">Using Namespaces</span></span>](using-namespaces.md)
- [<span data-ttu-id="1cb0e-122">My ad alanını kullanma</span><span class="sxs-lookup"><span data-stu-id="1cb0e-122">How to use the My namespace</span></span>](how-to-use-the-my-namespace.md)
- [<span data-ttu-id="1cb0e-123">Tanımlayıcı adları</span><span class="sxs-lookup"><span data-stu-id="1cb0e-123">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="1cb0e-124">using Yönergesi</span><span class="sxs-lookup"><span data-stu-id="1cb0e-124">using Directive</span></span>](../../language-reference/keywords/using-directive.md)
- [<span data-ttu-id="1cb0e-125">:: Operatör</span><span class="sxs-lookup"><span data-stu-id="1cb0e-125">:: Operator</span></span>](../../language-reference/operators/namespace-alias-qualifier.md)
