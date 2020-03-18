---
title: namespace anahtar kelime - C# Başvuru
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: b35f0a2a5cc0b2895b491d4ee24f89955f4b8fed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77625806"
---
# <a name="namespace-c-reference"></a><span data-ttu-id="40d80-102">namespace (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="40d80-102">namespace (C# Reference)</span></span>

<span data-ttu-id="40d80-103">Anahtar `namespace` kelime, ilgili nesneler kümesini içeren bir kapsamı bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="40d80-103">The `namespace` keyword is used to declare a scope that contains a set of related objects.</span></span> <span data-ttu-id="40d80-104">Kod öğelerini düzenlemek ve genel olarak benzersiz türler oluşturmak için bir ad alanı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40d80-104">You can use a namespace to organize code elements and to create globally unique types.</span></span>

[!code-csharp[csrefKeywordsNamespace#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#1)]

## <a name="remarks"></a><span data-ttu-id="40d80-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="40d80-105">Remarks</span></span>

<span data-ttu-id="40d80-106">Ad alanı içinde, aşağıdaki türlerden sıfır veya daha fazlasını bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="40d80-106">Within a namespace, you can declare zero or more of the following types:</span></span>

- <span data-ttu-id="40d80-107">başka bir ad alanı</span><span class="sxs-lookup"><span data-stu-id="40d80-107">another namespace</span></span>

- [<span data-ttu-id="40d80-108">Sınıfı</span><span class="sxs-lookup"><span data-stu-id="40d80-108">class</span></span>](class.md)

- [<span data-ttu-id="40d80-109">Arabirim</span><span class="sxs-lookup"><span data-stu-id="40d80-109">interface</span></span>](interface.md)

- [<span data-ttu-id="40d80-110">Yapı</span><span class="sxs-lookup"><span data-stu-id="40d80-110">struct</span></span>](../builtin-types/struct.md)

- [<span data-ttu-id="40d80-111">Enum</span><span class="sxs-lookup"><span data-stu-id="40d80-111">enum</span></span>](../builtin-types/enum.md)

- [<span data-ttu-id="40d80-112">temsilci</span><span class="sxs-lookup"><span data-stu-id="40d80-112">delegate</span></span>](../builtin-types/reference-types.md#the-delegate-type)

<span data-ttu-id="40d80-113">C# kaynak dosyasında bir ad alanını açıkça beyan edin veya bildirmeseniz de, derleyici varsayılan bir ad alanı ekler.</span><span class="sxs-lookup"><span data-stu-id="40d80-113">Whether or not you explicitly declare a namespace in a C# source file, the compiler adds a default namespace.</span></span> <span data-ttu-id="40d80-114">Bu adsız ad alanı, bazen genel ad alanı olarak da adlandırılır, her dosyada bulunur.</span><span class="sxs-lookup"><span data-stu-id="40d80-114">This unnamed namespace, sometimes referred to as the global namespace, is present in every file.</span></span> <span data-ttu-id="40d80-115">Genel ad alanındaki herhangi bir tanımlayıcı adlandırılmış bir ad alanında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="40d80-115">Any identifier in the global namespace is available for use in a named namespace.</span></span>

<span data-ttu-id="40d80-116">Ad alanları örtülü olarak genel erişime sahiptir ve bu değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="40d80-116">Namespaces implicitly have public access and this is not modifiable.</span></span> <span data-ttu-id="40d80-117">Erişim değiştiriciler bir tartışma için bir ad alanı öğeleri atayabilirsiniz, [Erişim Değiştiriciler](access-modifiers.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="40d80-117">For a discussion of the access modifiers you can assign to elements in a namespace, see [Access Modifiers](access-modifiers.md).</span></span>

<span data-ttu-id="40d80-118">İki veya daha fazla bildirimde bir ad alanı tanımlamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="40d80-118">It is possible to define a namespace in two or more declarations.</span></span> <span data-ttu-id="40d80-119">Örneğin, aşağıdaki örnek, iki sınıfı ad `MyCompany` alanının bir parçası olarak tanımlar:</span><span class="sxs-lookup"><span data-stu-id="40d80-119">For example, the following example defines two classes as part of the `MyCompany` namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#2)]

## <a name="example"></a><span data-ttu-id="40d80-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="40d80-120">Example</span></span>

<span data-ttu-id="40d80-121">Aşağıdaki örnek, iç içe geçmiş bir ad alanında statik bir yöntemin nasıl çağrılmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="40d80-121">The following example shows how to call a static method in a nested namespace.</span></span>

[!code-csharp[csrefKeywordsNamespace#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="40d80-122">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="40d80-122">C# language specification</span></span>

<span data-ttu-id="40d80-123">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Ad Alanları](~/_csharplang/spec/namespaces.md) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="40d80-123">For more information, see the [Namespaces](~/_csharplang/spec/namespaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="40d80-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40d80-124">See also</span></span>

- [<span data-ttu-id="40d80-125">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="40d80-125">C# reference</span></span>](../index.md)
- [<span data-ttu-id="40d80-126">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="40d80-126">C# keywords</span></span>](index.md)
- [<span data-ttu-id="40d80-127">Kullan -arak</span><span class="sxs-lookup"><span data-stu-id="40d80-127">using</span></span>](using-directive.md)
- [<span data-ttu-id="40d80-128">statik kullanarak</span><span class="sxs-lookup"><span data-stu-id="40d80-128">using static</span></span>](using-static.md)
- [<span data-ttu-id="40d80-129">Ad alanı diğer ad niteleyici`::`</span><span class="sxs-lookup"><span data-stu-id="40d80-129">Namespace alias qualifier `::`</span></span>](../operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="40d80-130">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="40d80-130">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
