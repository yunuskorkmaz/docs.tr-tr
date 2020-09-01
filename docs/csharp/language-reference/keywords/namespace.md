---
description: namespace anahtar sözcüğü-C# başvurusu
title: namespace anahtar sözcüğü-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: a6cfd1c3d37cbdef1f0dd72ddca85ce91f2e183b
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139586"
---
# <a name="namespace-c-reference"></a><span data-ttu-id="3f704-103">namespace (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="3f704-103">namespace (C# Reference)</span></span>

<span data-ttu-id="3f704-104">`namespace`Anahtar sözcüğü, ilgili nesneler kümesini içeren bir kapsamı bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3f704-104">The `namespace` keyword is used to declare a scope that contains a set of related objects.</span></span> <span data-ttu-id="3f704-105">Kod öğelerini düzenlemek ve genel benzersiz türler oluşturmak için bir ad alanı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f704-105">You can use a namespace to organize code elements and to create globally unique types.</span></span>

[!code-csharp[csrefKeywordsNamespace#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#1)]

## <a name="remarks"></a><span data-ttu-id="3f704-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3f704-106">Remarks</span></span>

<span data-ttu-id="3f704-107">Bir ad alanı içinde, aşağıdaki türlerden sıfır veya daha fazlasını bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3f704-107">Within a namespace, you can declare zero or more of the following types:</span></span>

- <span data-ttu-id="3f704-108">başka bir ad alanı</span><span class="sxs-lookup"><span data-stu-id="3f704-108">another namespace</span></span>

- [<span data-ttu-id="3f704-109">sınıfı</span><span class="sxs-lookup"><span data-stu-id="3f704-109">class</span></span>](class.md)

- [<span data-ttu-id="3f704-110">arayüz</span><span class="sxs-lookup"><span data-stu-id="3f704-110">interface</span></span>](interface.md)

- [<span data-ttu-id="3f704-111">sýný</span><span class="sxs-lookup"><span data-stu-id="3f704-111">struct</span></span>](../builtin-types/struct.md)

- [<span data-ttu-id="3f704-112">yardımının</span><span class="sxs-lookup"><span data-stu-id="3f704-112">enum</span></span>](../builtin-types/enum.md)

- [<span data-ttu-id="3f704-113">ğini</span><span class="sxs-lookup"><span data-stu-id="3f704-113">delegate</span></span>](../builtin-types/reference-types.md#the-delegate-type)

<span data-ttu-id="3f704-114">C# kaynak dosyasında açıkça bir ad alanı bildirip bildirmeyeceğinizi belirtir, derleyici varsayılan bir ad alanı ekler.</span><span class="sxs-lookup"><span data-stu-id="3f704-114">Whether or not you explicitly declare a namespace in a C# source file, the compiler adds a default namespace.</span></span> <span data-ttu-id="3f704-115">Her zaman genel ad alanı olarak adlandırılan bu adlandırılmamış ad alanı her dosyada mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="3f704-115">This unnamed namespace, sometimes referred to as the global namespace, is present in every file.</span></span> <span data-ttu-id="3f704-116">Genel ad alanındaki herhangi bir tanımlayıcı, adlandırılmış bir ad alanında kullanılmak üzere kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3f704-116">Any identifier in the global namespace is available for use in a named namespace.</span></span>

<span data-ttu-id="3f704-117">Ad alanları örtük olarak ortak erişime sahiptir ve bu değiştirilebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="3f704-117">Namespaces implicitly have public access and this is not modifiable.</span></span> <span data-ttu-id="3f704-118">Bir ad alanındaki öğelere atayabileceğiniz erişim değiştiricilerine ilişkin bir tartışma için bkz. [erişim değiştiricileri](access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="3f704-118">For a discussion of the access modifiers you can assign to elements in a namespace, see [Access Modifiers](access-modifiers.md).</span></span>

<span data-ttu-id="3f704-119">İki veya daha fazla bildiriminde bir ad alanı tanımlamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="3f704-119">It is possible to define a namespace in two or more declarations.</span></span> <span data-ttu-id="3f704-120">Örneğin, aşağıdaki örnek, ad alanının parçası olarak iki sınıfı tanımlar `MyCompany` :</span><span class="sxs-lookup"><span data-stu-id="3f704-120">For example, the following example defines two classes as part of the `MyCompany` namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#2)]

## <a name="example"></a><span data-ttu-id="3f704-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="3f704-121">Example</span></span>

<span data-ttu-id="3f704-122">Aşağıdaki örnek, iç içe bir ad alanında statik bir yöntemin nasıl çağrılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3f704-122">The following example shows how to call a static method in a nested namespace.</span></span>

[!code-csharp[csrefKeywordsNamespace#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="3f704-123">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="3f704-123">C# language specification</span></span>

<span data-ttu-id="3f704-124">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [namespaces](~/_csharplang/spec/namespaces.md) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="3f704-124">For more information, see the [Namespaces](~/_csharplang/spec/namespaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3f704-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f704-125">See also</span></span>

- [<span data-ttu-id="3f704-126">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="3f704-126">C# reference</span></span>](../index.md)
- [<span data-ttu-id="3f704-127">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="3f704-127">C# keywords</span></span>](index.md)
- [<span data-ttu-id="3f704-128">kullanma</span><span class="sxs-lookup"><span data-stu-id="3f704-128">using</span></span>](using-directive.md)
- [<span data-ttu-id="3f704-129">statik kullanma</span><span class="sxs-lookup"><span data-stu-id="3f704-129">using static</span></span>](using-static.md)
- [<span data-ttu-id="3f704-130">Ad alanı diğer adı niteleyicisi `::`</span><span class="sxs-lookup"><span data-stu-id="3f704-130">Namespace alias qualifier `::`</span></span>](../operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="3f704-131">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="3f704-131">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
