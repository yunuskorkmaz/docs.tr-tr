---
title: Ad alanları C# -Programlama Kılavuzu
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 21452e259596c9ab10b3d653ec1d8fb90fad131d
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937607"
---
# <a name="namespaces-c-programming-guide"></a><span data-ttu-id="ed2da-102">Ad Alanları (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="ed2da-102">Namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="ed2da-103">Ad alanları, C# programlamada iki şekilde çok fazla kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ed2da-103">Namespaces are heavily used in C# programming in two ways.</span></span> <span data-ttu-id="ed2da-104">İlk olarak, .NET, aşağıdaki gibi birçok sınıfını düzenlemek için ad alanlarını kullanır:</span><span class="sxs-lookup"><span data-stu-id="ed2da-104">First, .NET uses namespaces to organize its many classes, as follows:</span></span>  

[!code-csharp[csProgGuide#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#22)]

<span data-ttu-id="ed2da-105"><xref:System> bir ad alanıdır ve <xref:System.Console> bu ad alanındaki bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="ed2da-105"><xref:System> is a namespace and <xref:System.Console> is a class in that namespace.</span></span> <span data-ttu-id="ed2da-106">`using` anahtar sözcüğü, aşağıdaki örnekte olduğu gibi, tüm adı gerekli olmaması için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="ed2da-106">The `using` keyword can be used so that the complete name is not required, as in the following example:</span></span>

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#25)]

<span data-ttu-id="ed2da-107">Daha fazla bilgi için bkz. [using yönergesi](../../language-reference/keywords/using-directive.md).</span><span class="sxs-lookup"><span data-stu-id="ed2da-107">For more information, see the [using Directive](../../language-reference/keywords/using-directive.md).</span></span>

<span data-ttu-id="ed2da-108">İkincisi, kendi ad alanlarınızı bildirmek daha büyük programlama projelerindeki sınıf ve yöntem adlarının kapsamını denetlemenize yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="ed2da-108">Second, declaring your own namespaces can help you control the scope of class and method names in larger programming projects.</span></span> <span data-ttu-id="ed2da-109">Aşağıdaki örnekte olduğu gibi bir ad alanı bildirmek için [Namespace](../../language-reference/keywords/namespace.md) anahtar sözcüğünü kullanın:</span><span class="sxs-lookup"><span data-stu-id="ed2da-109">Use the [namespace](../../language-reference/keywords/namespace.md) keyword to declare a namespace, as in the following example:</span></span>

[!code-csharp[csProgGuideNamespaces#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#6)]

<span data-ttu-id="ed2da-110">Ad alanının adı geçerli C# bir [tanımlayıcı adı](../inside-a-program/identifier-names.md)olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ed2da-110">The name of the namespace must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span>

## <a name="namespaces-overview"></a><span data-ttu-id="ed2da-111">Ad alanlarına genel bakış</span><span class="sxs-lookup"><span data-stu-id="ed2da-111">Namespaces overview</span></span>

<span data-ttu-id="ed2da-112">Ad alanları aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="ed2da-112">Namespaces have the following properties:</span></span>

- <span data-ttu-id="ed2da-113">Büyük kod projelerini düzenler.</span><span class="sxs-lookup"><span data-stu-id="ed2da-113">They organize large code projects.</span></span>
- <span data-ttu-id="ed2da-114">`.` işleci kullanılarak sınırlandırılır.</span><span class="sxs-lookup"><span data-stu-id="ed2da-114">They are delimited by using the `.` operator.</span></span>
- <span data-ttu-id="ed2da-115">`using` yönergesi, her sınıf için ad alanının adını belirtmek için gereksinimi obviates.</span><span class="sxs-lookup"><span data-stu-id="ed2da-115">The `using` directive obviates the requirement to specify the name of the namespace for every class.</span></span>
- <span data-ttu-id="ed2da-116">`global` ad alanı "root" ad alanıdır: `global::System` her zaman .NET <xref:System> ad alanına başvuracaktır.</span><span class="sxs-lookup"><span data-stu-id="ed2da-116">The `global` namespace is the "root" namespace: `global::System` will always refer to the .NET <xref:System> namespace.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ed2da-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="ed2da-117">C# language specification</span></span>

<span data-ttu-id="ed2da-118">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [ad alanları](~/_csharplang/spec/namespaces.md) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="ed2da-118">For more information, see the [Namespaces](~/_csharplang/spec/namespaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ed2da-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed2da-119">See also</span></span>

- [<span data-ttu-id="ed2da-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ed2da-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ed2da-121">Ad Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="ed2da-121">Using Namespaces</span></span>](using-namespaces.md)
- [<span data-ttu-id="ed2da-122">My ad alanım 'ı kullanma</span><span class="sxs-lookup"><span data-stu-id="ed2da-122">How to use the My namespace</span></span>](how-to-use-the-my-namespace.md)
- [<span data-ttu-id="ed2da-123">Tanımlayıcı adları</span><span class="sxs-lookup"><span data-stu-id="ed2da-123">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="ed2da-124">using Yönergesi</span><span class="sxs-lookup"><span data-stu-id="ed2da-124">using Directive</span></span>](../../language-reference/keywords/using-directive.md)
- [<span data-ttu-id="ed2da-125">:: İşleci</span><span class="sxs-lookup"><span data-stu-id="ed2da-125">:: Operator</span></span>](../../language-reference/operators/namespace-alias-qualifier.md)
