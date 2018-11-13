---
title: protected anahtar sözcüğü (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: 6e3f72226d10910152f7a2139a5a1be35e681ec7
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2018
ms.locfileid: "50183184"
---
# <a name="protected-c-reference"></a><span data-ttu-id="bfb64-102">protected (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="bfb64-102">protected (C# Reference)</span></span>

<span data-ttu-id="bfb64-103">`protected` Anahtar sözcüğü, bir üye erişim değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="bfb64-103">The `protected` keyword is a member access modifier.</span></span>

 > <span data-ttu-id="bfb64-104">Bu sayfa kapsayan `protected` erişim.</span><span class="sxs-lookup"><span data-stu-id="bfb64-104">This page covers `protected` access.</span></span> <span data-ttu-id="bfb64-105">`protected` Anahtar sözcüğü, ayrıca parçası [ `protected internal` ](protected-internal.md) ve [ `private protected` ](private-protected.md) erişim değiştiricileri.</span><span class="sxs-lookup"><span data-stu-id="bfb64-105">The `protected` keyword is also part of the [`protected internal`](protected-internal.md) and [`private protected`](private-protected.md) access modifiers.</span></span>

<span data-ttu-id="bfb64-106">Korumalı üye sınıfı içinde ve türetilen sınıf örnekleri tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="bfb64-106">A protected member is accessible within its class and by derived class instances.</span></span>

<span data-ttu-id="bfb64-107">Bir karşılaştırması `protected` diğer erişim değiştiricileri ile bkz [erişilebilirlik düzeyleri](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="bfb64-107">For a comparison of `protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="bfb64-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="bfb64-108">Example</span></span>

<span data-ttu-id="bfb64-109">Yalnızca türetilmiş sınıf türü erişim ortaya çıkarsa, bir taban sınıfın korumalı bir üye türetilen bir sınıfta erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="bfb64-109">A protected member of a base class is accessible in a derived class only if the access occurs through the derived class type.</span></span> <span data-ttu-id="bfb64-110">Örneğin, aşağıdaki kod kesimi göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="bfb64-110">For example, consider the following code segment:</span></span>

[!code-csharp[csrefKeywordsModifiers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#11)]

<span data-ttu-id="bfb64-111">Deyim `a.x = 10` ana statik yöntem içinde yapılır ve örneği değil, sınıf b olduğundan bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bfb64-111">The statement `a.x = 10` generates an error because it is made within the static method Main, and not an instance of class B.</span></span>

<span data-ttu-id="bfb64-112">Yapı üyeleri struct devralınamaz korunamaz.</span><span class="sxs-lookup"><span data-stu-id="bfb64-112">Struct members cannot be protected because the struct cannot be inherited.</span></span>

## <a name="example"></a><span data-ttu-id="bfb64-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="bfb64-113">Example</span></span>

<span data-ttu-id="bfb64-114">Bu örnekte, sınıf `DerivedPoint` türetilir `Point`.</span><span class="sxs-lookup"><span data-stu-id="bfb64-114">In this example, the class `DerivedPoint` is derived from `Point`.</span></span> <span data-ttu-id="bfb64-115">Bu nedenle, temel sınıfın korumalı üyeler türetilmiş sınıftan doğrudan erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bfb64-115">Therefore, you can access the protected members of the base class directly from the derived class.</span></span>

[!code-csharp[csrefKeywordsModifiers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#12)]  

<span data-ttu-id="bfb64-116">Erişim düzeyleri değiştirirseniz `x` ve `y` için [özel](private.md), derleyici hata iletilerini verir:</span><span class="sxs-lookup"><span data-stu-id="bfb64-116">If you change the access levels of `x` and `y` to [private](private.md), the compiler will issue the error messages:</span></span>

`'Point.y' is inaccessible due to its protection level.`

`'Point.x' is inaccessible due to its protection level.`

## <a name="c-language-specification"></a><span data-ttu-id="bfb64-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="bfb64-117">C# language specification</span></span>  

<span data-ttu-id="bfb64-118">Daha fazla bilgi için [erişilebilirlik bildirilen](~/_csharplang/spec/basic-concepts.md#declared-accessibility) içinde [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="bfb64-118">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="bfb64-119">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="bfb64-119">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="bfb64-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bfb64-120">See also</span></span>

- [<span data-ttu-id="bfb64-121">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="bfb64-121">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="bfb64-122">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="bfb64-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="bfb64-123">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="bfb64-123">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="bfb64-124">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="bfb64-124">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="bfb64-125">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="bfb64-125">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="bfb64-126">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="bfb64-126">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="bfb64-127">public</span><span class="sxs-lookup"><span data-stu-id="bfb64-127">public</span></span>](public.md)
- [<span data-ttu-id="bfb64-128">private</span><span class="sxs-lookup"><span data-stu-id="bfb64-128">private</span></span>](private.md)
- [<span data-ttu-id="bfb64-129">internal</span><span class="sxs-lookup"><span data-stu-id="bfb64-129">internal</span></span>](internal.md)
- <span data-ttu-id="bfb64-130">[İç sanal anahtar sözcükleri ile ilgili güvenlik konuları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="bfb64-130">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>