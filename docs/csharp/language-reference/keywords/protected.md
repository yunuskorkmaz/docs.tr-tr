---
description: protected anahtar sözcüğü-C# başvurusu
title: protected anahtar sözcüğü-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: af0c7ab5ebb6980bb0381e46fd38e9470f3a2152
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90536762"
---
# <a name="protected-c-reference"></a><span data-ttu-id="eee4a-103">protected (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="eee4a-103">protected (C# Reference)</span></span>

<span data-ttu-id="eee4a-104">`protected`Anahtar sözcüğü bir üye erişim değiştiricisidir.</span><span class="sxs-lookup"><span data-stu-id="eee4a-104">The `protected` keyword is a member access modifier.</span></span>

 > <span data-ttu-id="eee4a-105">Bu sayfa `protected` erişimi içerir.</span><span class="sxs-lookup"><span data-stu-id="eee4a-105">This page covers `protected` access.</span></span> <span data-ttu-id="eee4a-106">`protected`Anahtar sözcüğü ayrıca [`protected internal`](protected-internal.md) ve [`private protected`](private-protected.md) erişim değiştiricilerin bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="eee4a-106">The `protected` keyword is also part of the [`protected internal`](protected-internal.md) and [`private protected`](private-protected.md) access modifiers.</span></span>

<span data-ttu-id="eee4a-107">Korunan bir üyeye kendi sınıfı içinde ve türetilmiş sınıf örnekleri tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="eee4a-107">A protected member is accessible within its class and by derived class instances.</span></span>

<span data-ttu-id="eee4a-108">`protected`Diğer erişim değiştiricilerine ilişkin bir karşılaştırma için bkz. [Erişilebilirlik düzeyleri](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="eee4a-108">For a comparison of `protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="eee4a-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="eee4a-109">Example</span></span>

<span data-ttu-id="eee4a-110">Bir temel sınıfın korunan üyesine, yalnızca erişim türetilmiş sınıf türü aracılığıyla gerçekleşirse türetilmiş bir sınıfta erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="eee4a-110">A protected member of a base class is accessible in a derived class only if the access occurs through the derived class type.</span></span> <span data-ttu-id="eee4a-111">Örneğin, aşağıdaki kod kesimini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="eee4a-111">For example, consider the following code segment:</span></span>

[!code-csharp[csrefKeywordsModifiers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#11)]

<span data-ttu-id="eee4a-112">İfade, `a.x = 10` B sınıfının bir örneği değil ana static yöntemi içinde yapıldığından bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="eee4a-112">The statement `a.x = 10` generates an error because it is made within the static method Main, and not an instance of class B.</span></span>

<span data-ttu-id="eee4a-113">Struct devralınamadığı için yapı üyeleri korunamaz.</span><span class="sxs-lookup"><span data-stu-id="eee4a-113">Struct members cannot be protected because the struct cannot be inherited.</span></span>

## <a name="example"></a><span data-ttu-id="eee4a-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="eee4a-114">Example</span></span>

<span data-ttu-id="eee4a-115">Bu örnekte, sınıfı `DerivedPoint` öğesinden türetilir `Point` .</span><span class="sxs-lookup"><span data-stu-id="eee4a-115">In this example, the class `DerivedPoint` is derived from `Point`.</span></span> <span data-ttu-id="eee4a-116">Bu nedenle, doğrudan türetilmiş sınıftan temel sınıfın korunan üyelerine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eee4a-116">Therefore, you can access the protected members of the base class directly from the derived class.</span></span>

[!code-csharp[csrefKeywordsModifiers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#12)]  

<span data-ttu-id="eee4a-117">Ve erişim düzeylerini `x` `y` [özel](private.md)olarak değiştirirseniz, derleyici hata iletilerini de verebilir:</span><span class="sxs-lookup"><span data-stu-id="eee4a-117">If you change the access levels of `x` and `y` to [private](private.md), the compiler will issue the error messages:</span></span>

`'Point.y' is inaccessible due to its protection level.`

`'Point.x' is inaccessible due to its protection level.`

## <a name="c-language-specification"></a><span data-ttu-id="eee4a-118">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="eee4a-118">C# language specification</span></span>  

<span data-ttu-id="eee4a-119">Daha fazla bilgi için bkz. [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Erişilebilirlik bildirimi](~/_csharplang/spec/basic-concepts.md#declared-accessibility) .</span><span class="sxs-lookup"><span data-stu-id="eee4a-119">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="eee4a-120">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="eee4a-120">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="eee4a-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eee4a-121">See also</span></span>

- [<span data-ttu-id="eee4a-122">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="eee4a-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="eee4a-123">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="eee4a-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="eee4a-124">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="eee4a-124">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="eee4a-125">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="eee4a-125">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="eee4a-126">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="eee4a-126">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="eee4a-127">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="eee4a-127">Modifiers</span></span>](index.md)
- [<span data-ttu-id="eee4a-128">genel</span><span class="sxs-lookup"><span data-stu-id="eee4a-128">public</span></span>](public.md)
- [<span data-ttu-id="eee4a-129">private</span><span class="sxs-lookup"><span data-stu-id="eee4a-129">private</span></span>](private.md)
- [<span data-ttu-id="eee4a-130">internal</span><span class="sxs-lookup"><span data-stu-id="eee4a-130">internal</span></span>](internal.md)
- <span data-ttu-id="eee4a-131">[İç sanal anahtar sözcüklere yönelik güvenlik sorunları](/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="eee4a-131">[Security concerns for internal virtual keywords](/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
