---
title: anahtar sözcüğü - korumalı C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: 55fbcf6fbc5148143e2d559ab8192e3ea10ab43c
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633305"
---
# <a name="protected-c-reference"></a><span data-ttu-id="4466a-102">protected (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="4466a-102">protected (C# Reference)</span></span>

<span data-ttu-id="4466a-103">`protected` Anahtar sözcüğü, bir üye erişim değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="4466a-103">The `protected` keyword is a member access modifier.</span></span>

 > <span data-ttu-id="4466a-104">Bu sayfa kapsayan `protected` erişim.</span><span class="sxs-lookup"><span data-stu-id="4466a-104">This page covers `protected` access.</span></span> <span data-ttu-id="4466a-105">`protected` Anahtar sözcüğü, ayrıca parçası [ `protected internal` ](protected-internal.md) ve [ `private protected` ](private-protected.md) erişim değiştiricileri.</span><span class="sxs-lookup"><span data-stu-id="4466a-105">The `protected` keyword is also part of the [`protected internal`](protected-internal.md) and [`private protected`](private-protected.md) access modifiers.</span></span>

<span data-ttu-id="4466a-106">Korumalı üye sınıfı içinde ve türetilen sınıf örnekleri tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="4466a-106">A protected member is accessible within its class and by derived class instances.</span></span>

<span data-ttu-id="4466a-107">Bir karşılaştırması `protected` diğer erişim değiştiricileri ile bkz [erişilebilirlik düzeyleri](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="4466a-107">For a comparison of `protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="4466a-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="4466a-108">Example</span></span>

<span data-ttu-id="4466a-109">Yalnızca türetilmiş sınıf türü erişim ortaya çıkarsa, bir taban sınıfın korumalı bir üye türetilen bir sınıfta erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="4466a-109">A protected member of a base class is accessible in a derived class only if the access occurs through the derived class type.</span></span> <span data-ttu-id="4466a-110">Örneğin, aşağıdaki kod kesimi göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="4466a-110">For example, consider the following code segment:</span></span>

[!code-csharp[csrefKeywordsModifiers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#11)]

<span data-ttu-id="4466a-111">Deyim `a.x = 10` ana statik yöntem içinde yapılır ve örneği değil, sınıf b olduğundan bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4466a-111">The statement `a.x = 10` generates an error because it is made within the static method Main, and not an instance of class B.</span></span>

<span data-ttu-id="4466a-112">Yapı üyeleri struct devralınamaz korunamaz.</span><span class="sxs-lookup"><span data-stu-id="4466a-112">Struct members cannot be protected because the struct cannot be inherited.</span></span>

## <a name="example"></a><span data-ttu-id="4466a-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="4466a-113">Example</span></span>

<span data-ttu-id="4466a-114">Bu örnekte, sınıf `DerivedPoint` türetilir `Point`.</span><span class="sxs-lookup"><span data-stu-id="4466a-114">In this example, the class `DerivedPoint` is derived from `Point`.</span></span> <span data-ttu-id="4466a-115">Bu nedenle, temel sınıfın korumalı üyeler türetilmiş sınıftan doğrudan erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4466a-115">Therefore, you can access the protected members of the base class directly from the derived class.</span></span>

[!code-csharp[csrefKeywordsModifiers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#12)]  

<span data-ttu-id="4466a-116">Erişim düzeyleri değiştirirseniz `x` ve `y` için [özel](private.md), derleyici hata iletilerini verir:</span><span class="sxs-lookup"><span data-stu-id="4466a-116">If you change the access levels of `x` and `y` to [private](private.md), the compiler will issue the error messages:</span></span>

`'Point.y' is inaccessible due to its protection level.`

`'Point.x' is inaccessible due to its protection level.`

## <a name="c-language-specification"></a><span data-ttu-id="4466a-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="4466a-117">C# language specification</span></span>  

<span data-ttu-id="4466a-118">Daha fazla bilgi için [erişilebilirlik bildirilen](~/_csharplang/spec/basic-concepts.md#declared-accessibility) içinde [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="4466a-118">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="4466a-119">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="4466a-119">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="4466a-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4466a-120">See also</span></span>

- [<span data-ttu-id="4466a-121">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="4466a-121">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="4466a-122">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4466a-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="4466a-123">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="4466a-123">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="4466a-124">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="4466a-124">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="4466a-125">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="4466a-125">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="4466a-126">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="4466a-126">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="4466a-127">public</span><span class="sxs-lookup"><span data-stu-id="4466a-127">public</span></span>](public.md)
- [<span data-ttu-id="4466a-128">private</span><span class="sxs-lookup"><span data-stu-id="4466a-128">private</span></span>](private.md)
- [<span data-ttu-id="4466a-129">internal</span><span class="sxs-lookup"><span data-stu-id="4466a-129">internal</span></span>](internal.md)
- <span data-ttu-id="4466a-130">[İç sanal anahtar sözcükleri ile ilgili güvenlik konuları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4466a-130">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
