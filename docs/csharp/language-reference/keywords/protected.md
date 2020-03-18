---
title: korumalı anahtar kelime - C# Başvuru
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: bec619d4f49bd26daa742c18c830909c14948adf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713189"
---
# <a name="protected-c-reference"></a><span data-ttu-id="5f41e-102">protected (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5f41e-102">protected (C# Reference)</span></span>

<span data-ttu-id="5f41e-103">Anahtar `protected` kelime bir üye erişim değiştiricidir.</span><span class="sxs-lookup"><span data-stu-id="5f41e-103">The `protected` keyword is a member access modifier.</span></span>

 > <span data-ttu-id="5f41e-104">Bu sayfa `protected` erişimi kapsar.</span><span class="sxs-lookup"><span data-stu-id="5f41e-104">This page covers `protected` access.</span></span> <span data-ttu-id="5f41e-105">Anahtar `protected` kelime de [`protected internal`](protected-internal.md) bir parçasıdır [`private protected`](private-protected.md) ve erişim değiştiriciler.</span><span class="sxs-lookup"><span data-stu-id="5f41e-105">The `protected` keyword is also part of the [`protected internal`](protected-internal.md) and [`private protected`](private-protected.md) access modifiers.</span></span>

<span data-ttu-id="5f41e-106">Korumalı bir üyeye kendi sınıfında ve türetilmiş sınıf örnekleri ne göre erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="5f41e-106">A protected member is accessible within its class and by derived class instances.</span></span>

<span data-ttu-id="5f41e-107">Diğer erişim `protected` değiştiriciler ile karşılaştırma için [Erişilebilirlik Düzeyleri'ne](accessibility-levels.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="5f41e-107">For a comparison of `protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="5f41e-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="5f41e-108">Example</span></span>

<span data-ttu-id="5f41e-109">Taban sınıfın korumalı üyesine, yalnızca türetilmiş sınıf türü nden erişim oluşursa, türetilmiş bir sınıfta erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="5f41e-109">A protected member of a base class is accessible in a derived class only if the access occurs through the derived class type.</span></span> <span data-ttu-id="5f41e-110">Örneğin, aşağıdaki kod kesimini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="5f41e-110">For example, consider the following code segment:</span></span>

[!code-csharp[csrefKeywordsModifiers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#11)]

<span data-ttu-id="5f41e-111">İfade, `a.x = 10` B sınıfının bir örneği değil, main statik yöntemi içinde yapıldığından bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5f41e-111">The statement `a.x = 10` generates an error because it is made within the static method Main, and not an instance of class B.</span></span>

<span data-ttu-id="5f41e-112">Yapı kalıtsal olamaz, çünkü yapı üyeleri korunamaz.</span><span class="sxs-lookup"><span data-stu-id="5f41e-112">Struct members cannot be protected because the struct cannot be inherited.</span></span>

## <a name="example"></a><span data-ttu-id="5f41e-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="5f41e-113">Example</span></span>

<span data-ttu-id="5f41e-114">Bu örnekte, `DerivedPoint` `Point`sınıf.</span><span class="sxs-lookup"><span data-stu-id="5f41e-114">In this example, the class `DerivedPoint` is derived from `Point`.</span></span> <span data-ttu-id="5f41e-115">Bu nedenle, taban sınıfın korumalı üyelerine doğrudan türemiş sınıftan erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5f41e-115">Therefore, you can access the protected members of the base class directly from the derived class.</span></span>

[!code-csharp[csrefKeywordsModifiers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#12)]  

<span data-ttu-id="5f41e-116">Erişim düzeylerini `x` `y` ve [özel](private.md)düzeylerini değiştirirseniz, derleyici hata iletilerini verecektir:</span><span class="sxs-lookup"><span data-stu-id="5f41e-116">If you change the access levels of `x` and `y` to [private](private.md), the compiler will issue the error messages:</span></span>

`'Point.y' is inaccessible due to its protection level.`

`'Point.x' is inaccessible due to its protection level.`

## <a name="c-language-specification"></a><span data-ttu-id="5f41e-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="5f41e-117">C# language specification</span></span>  

<span data-ttu-id="5f41e-118">Daha fazla bilgi için [C# Dil Belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Bildirilen Erişilebilirlik'e](~/_csharplang/spec/basic-concepts.md#declared-accessibility) bakın.</span><span class="sxs-lookup"><span data-stu-id="5f41e-118">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="5f41e-119">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="5f41e-119">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="5f41e-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f41e-120">See also</span></span>

- [<span data-ttu-id="5f41e-121">C# Referans</span><span class="sxs-lookup"><span data-stu-id="5f41e-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5f41e-122">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5f41e-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5f41e-123">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="5f41e-123">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="5f41e-124">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="5f41e-124">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="5f41e-125">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="5f41e-125">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="5f41e-126">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="5f41e-126">Modifiers</span></span>](index.md)
- [<span data-ttu-id="5f41e-127">Kamu</span><span class="sxs-lookup"><span data-stu-id="5f41e-127">public</span></span>](public.md)
- [<span data-ttu-id="5f41e-128">Özel</span><span class="sxs-lookup"><span data-stu-id="5f41e-128">private</span></span>](private.md)
- [<span data-ttu-id="5f41e-129">Iç</span><span class="sxs-lookup"><span data-stu-id="5f41e-129">internal</span></span>](internal.md)
- <span data-ttu-id="5f41e-130">[Dahili sanal anahtar kelimeler için güvenlik endişeleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5f41e-130">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
