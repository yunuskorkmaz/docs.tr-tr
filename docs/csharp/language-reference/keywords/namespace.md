---
title: namespace anahtar sözcüğü C# -başvurusu
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: b35f0a2a5cc0b2895b491d4ee24f89955f4b8fed
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77625806"
---
# <a name="namespace-c-reference"></a><span data-ttu-id="b84c7-102">namespace (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b84c7-102">namespace (C# Reference)</span></span>

<span data-ttu-id="b84c7-103">`namespace` anahtar sözcüğü, ilgili nesneler kümesini içeren bir kapsamı bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b84c7-103">The `namespace` keyword is used to declare a scope that contains a set of related objects.</span></span> <span data-ttu-id="b84c7-104">Kod öğelerini düzenlemek ve genel benzersiz türler oluşturmak için bir ad alanı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b84c7-104">You can use a namespace to organize code elements and to create globally unique types.</span></span>

[!code-csharp[csrefKeywordsNamespace#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#1)]

## <a name="remarks"></a><span data-ttu-id="b84c7-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b84c7-105">Remarks</span></span>

<span data-ttu-id="b84c7-106">Bir ad alanı içinde, aşağıdaki türlerden sıfır veya daha fazlasını bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b84c7-106">Within a namespace, you can declare zero or more of the following types:</span></span>

- <span data-ttu-id="b84c7-107">başka bir ad alanı</span><span class="sxs-lookup"><span data-stu-id="b84c7-107">another namespace</span></span>

- [<span data-ttu-id="b84c7-108">class</span><span class="sxs-lookup"><span data-stu-id="b84c7-108">class</span></span>](class.md)

- [<span data-ttu-id="b84c7-109">interface</span><span class="sxs-lookup"><span data-stu-id="b84c7-109">interface</span></span>](interface.md)

- [<span data-ttu-id="b84c7-110">struct</span><span class="sxs-lookup"><span data-stu-id="b84c7-110">struct</span></span>](../builtin-types/struct.md)

- [<span data-ttu-id="b84c7-111">enum</span><span class="sxs-lookup"><span data-stu-id="b84c7-111">enum</span></span>](../builtin-types/enum.md)

- [<span data-ttu-id="b84c7-112">delegate</span><span class="sxs-lookup"><span data-stu-id="b84c7-112">delegate</span></span>](../builtin-types/reference-types.md#the-delegate-type)

<span data-ttu-id="b84c7-113">Bir C# kaynak dosyasında açıkça bir ad alanı bildirip bildirmeyeceğinizi belirtir, derleyici varsayılan bir ad alanı ekler.</span><span class="sxs-lookup"><span data-stu-id="b84c7-113">Whether or not you explicitly declare a namespace in a C# source file, the compiler adds a default namespace.</span></span> <span data-ttu-id="b84c7-114">Her zaman genel ad alanı olarak adlandırılan bu adlandırılmamış ad alanı her dosyada mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="b84c7-114">This unnamed namespace, sometimes referred to as the global namespace, is present in every file.</span></span> <span data-ttu-id="b84c7-115">Genel ad alanındaki herhangi bir tanımlayıcı, adlandırılmış bir ad alanında kullanılmak üzere kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b84c7-115">Any identifier in the global namespace is available for use in a named namespace.</span></span>

<span data-ttu-id="b84c7-116">Ad alanları örtük olarak ortak erişime sahiptir ve bu değiştirilebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="b84c7-116">Namespaces implicitly have public access and this is not modifiable.</span></span> <span data-ttu-id="b84c7-117">Bir ad alanındaki öğelere atayabileceğiniz erişim değiştiricilerine ilişkin bir tartışma için bkz. [erişim değiştiricileri](access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="b84c7-117">For a discussion of the access modifiers you can assign to elements in a namespace, see [Access Modifiers](access-modifiers.md).</span></span>

<span data-ttu-id="b84c7-118">İki veya daha fazla bildiriminde bir ad alanı tanımlamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="b84c7-118">It is possible to define a namespace in two or more declarations.</span></span> <span data-ttu-id="b84c7-119">Örneğin, aşağıdaki örnek, `MyCompany` ad alanının parçası olarak iki sınıfı tanımlar:</span><span class="sxs-lookup"><span data-stu-id="b84c7-119">For example, the following example defines two classes as part of the `MyCompany` namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#2)]

## <a name="example"></a><span data-ttu-id="b84c7-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="b84c7-120">Example</span></span>

<span data-ttu-id="b84c7-121">Aşağıdaki örnek, iç içe bir ad alanında statik bir yöntemin nasıl çağrılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b84c7-121">The following example shows how to call a static method in a nested namespace.</span></span>

[!code-csharp[csrefKeywordsNamespace#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="b84c7-122">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="b84c7-122">C# language specification</span></span>

<span data-ttu-id="b84c7-123">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [ad alanları](~/_csharplang/spec/namespaces.md) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="b84c7-123">For more information, see the [Namespaces](~/_csharplang/spec/namespaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b84c7-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b84c7-124">See also</span></span>

- [<span data-ttu-id="b84c7-125">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="b84c7-125">C# reference</span></span>](../index.md)
- [<span data-ttu-id="b84c7-126">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="b84c7-126">C# keywords</span></span>](index.md)
- [<span data-ttu-id="b84c7-127">using</span><span class="sxs-lookup"><span data-stu-id="b84c7-127">using</span></span>](using-directive.md)
- [<span data-ttu-id="b84c7-128">statik kullanma</span><span class="sxs-lookup"><span data-stu-id="b84c7-128">using static</span></span>](using-static.md)
- [<span data-ttu-id="b84c7-129">Ad alanı diğer adı niteleyicisi `::`</span><span class="sxs-lookup"><span data-stu-id="b84c7-129">Namespace alias qualifier `::`</span></span>](../operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="b84c7-130">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="b84c7-130">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
