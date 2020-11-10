---
title: Ad alanları-C# Programlama Kılavuzu
description: C# programlamada ad alanları hakkında bilgi edinin. Bkz. ad alanı özelliklerine genel bakış ve ek kaynakları görüntüleme.
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 41a666fd5f368e6990e08a36700e18f648939213
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440347"
---
# <a name="namespaces-c-programming-guide"></a><span data-ttu-id="11f18-104">Ad Alanları (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="11f18-104">Namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="11f18-105">Ad alanları, C# programlamada iki şekilde çok fazla kullanılır.</span><span class="sxs-lookup"><span data-stu-id="11f18-105">Namespaces are heavily used in C# programming in two ways.</span></span> <span data-ttu-id="11f18-106">İlk olarak, .NET, aşağıdaki gibi birçok sınıfını düzenlemek için ad alanlarını kullanır:</span><span class="sxs-lookup"><span data-stu-id="11f18-106">First, .NET uses namespaces to organize its many classes, as follows:</span></span>  

[!code-csharp[csProgGuide#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#22)]

<span data-ttu-id="11f18-107"><xref:System> bir ad alanıdır ve <xref:System.Console> Bu ad alanındaki bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="11f18-107"><xref:System> is a namespace and <xref:System.Console> is a class in that namespace.</span></span> <span data-ttu-id="11f18-108">`using`Anahtar sözcüğü, aşağıdaki örnekte olduğu gibi, tüm adı gerekli olmaması için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="11f18-108">The `using` keyword can be used so that the complete name is not required, as in the following example:</span></span>

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

<span data-ttu-id="11f18-109">Daha fazla bilgi için bkz. [using yönergesi](../../language-reference/keywords/using-directive.md).</span><span class="sxs-lookup"><span data-stu-id="11f18-109">For more information, see the [using Directive](../../language-reference/keywords/using-directive.md).</span></span>

<span data-ttu-id="11f18-110">İkincisi, kendi ad alanlarınızı bildirmek daha büyük programlama projelerindeki sınıf ve yöntem adlarının kapsamını denetlemenize yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="11f18-110">Second, declaring your own namespaces can help you control the scope of class and method names in larger programming projects.</span></span> <span data-ttu-id="11f18-111">Aşağıdaki örnekte olduğu gibi bir ad alanı bildirmek için [Namespace](../../language-reference/keywords/namespace.md) anahtar sözcüğünü kullanın:</span><span class="sxs-lookup"><span data-stu-id="11f18-111">Use the [namespace](../../language-reference/keywords/namespace.md) keyword to declare a namespace, as in the following example:</span></span>

[!code-csharp[csProgGuideNamespaces#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#6)]

<span data-ttu-id="11f18-112">Ad alanının adı geçerli bir C# [tanımlayıcı adı](../inside-a-program/identifier-names.md)olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="11f18-112">The name of the namespace must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span>

## <a name="namespaces-overview"></a><span data-ttu-id="11f18-113">Ad alanlarına genel bakış</span><span class="sxs-lookup"><span data-stu-id="11f18-113">Namespaces overview</span></span>

<span data-ttu-id="11f18-114">Ad alanları aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="11f18-114">Namespaces have the following properties:</span></span>

- <span data-ttu-id="11f18-115">Büyük kod projelerini düzenler.</span><span class="sxs-lookup"><span data-stu-id="11f18-115">They organize large code projects.</span></span>
- <span data-ttu-id="11f18-116">İşleci kullanılarak sınırlandırılır `.` .</span><span class="sxs-lookup"><span data-stu-id="11f18-116">They are delimited by using the `.` operator.</span></span>
- <span data-ttu-id="11f18-117">`using`Yönergesi, her sınıf için ad alanının adını belirtmek için gereksinimi obviates.</span><span class="sxs-lookup"><span data-stu-id="11f18-117">The `using` directive obviates the requirement to specify the name of the namespace for every class.</span></span>
- <span data-ttu-id="11f18-118">`global`Ad alanı "root" ad alanıdır: `global::System` her zaman .net ad alanına başvurur <xref:System> .</span><span class="sxs-lookup"><span data-stu-id="11f18-118">The `global` namespace is the "root" namespace: `global::System` will always refer to the .NET <xref:System> namespace.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="11f18-119">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="11f18-119">C# language specification</span></span>

<span data-ttu-id="11f18-120">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [namespaces](~/_csharplang/spec/namespaces.md) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="11f18-120">For more information, see the [Namespaces](~/_csharplang/spec/namespaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="11f18-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11f18-121">See also</span></span>

- [<span data-ttu-id="11f18-122">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="11f18-122">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="11f18-123">Ad alanlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="11f18-123">Using Namespaces</span></span>](using-namespaces.md)
- [<span data-ttu-id="11f18-124">My ad alanını kullanma</span><span class="sxs-lookup"><span data-stu-id="11f18-124">How to use the My namespace</span></span>](how-to-use-the-my-namespace.md)
- [<span data-ttu-id="11f18-125">Tanımlayıcı adları</span><span class="sxs-lookup"><span data-stu-id="11f18-125">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="11f18-126">using Yönergesi</span><span class="sxs-lookup"><span data-stu-id="11f18-126">using Directive</span></span>](../../language-reference/keywords/using-directive.md)
- [<span data-ttu-id="11f18-127">:: İşleci</span><span class="sxs-lookup"><span data-stu-id="11f18-127">:: Operator</span></span>](../../language-reference/operators/namespace-alias-qualifier.md)
