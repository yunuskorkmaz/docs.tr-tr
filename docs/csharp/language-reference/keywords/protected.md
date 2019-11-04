---
title: protected anahtar sözcüğü C# -başvuru
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: f54c3f36e5aeb428815d1c49cd797e559d156ea7
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422572"
---
# <a name="protected-c-reference"></a><span data-ttu-id="46a95-102">protected (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="46a95-102">protected (C# Reference)</span></span>

<span data-ttu-id="46a95-103">`protected` anahtar sözcüğü bir üye erişim değiştiricisidir.</span><span class="sxs-lookup"><span data-stu-id="46a95-103">The `protected` keyword is a member access modifier.</span></span>

 > <span data-ttu-id="46a95-104">Bu sayfa `protected` erişimi içerir.</span><span class="sxs-lookup"><span data-stu-id="46a95-104">This page covers `protected` access.</span></span> <span data-ttu-id="46a95-105">`protected` anahtar sözcüğü ayrıca [`protected internal`](protected-internal.md) ve [`private protected`](private-protected.md) erişim değiştiricilerinden de bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="46a95-105">The `protected` keyword is also part of the [`protected internal`](protected-internal.md) and [`private protected`](private-protected.md) access modifiers.</span></span>

<span data-ttu-id="46a95-106">Korunan bir üyeye kendi sınıfı içinde ve türetilmiş sınıf örnekleri tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="46a95-106">A protected member is accessible within its class and by derived class instances.</span></span>

<span data-ttu-id="46a95-107">Diğer erişim değiştiricilerine sahip `protected` bir karşılaştırması için bkz. [Erişilebilirlik düzeyleri](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="46a95-107">For a comparison of `protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="46a95-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="46a95-108">Example</span></span>

<span data-ttu-id="46a95-109">Bir temel sınıfın korunan üyesine, yalnızca erişim türetilmiş sınıf türü aracılığıyla gerçekleşirse türetilmiş bir sınıfta erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="46a95-109">A protected member of a base class is accessible in a derived class only if the access occurs through the derived class type.</span></span> <span data-ttu-id="46a95-110">Örneğin, aşağıdaki kod kesimini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="46a95-110">For example, consider the following code segment:</span></span>

[!code-csharp[csrefKeywordsModifiers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#11)]

<span data-ttu-id="46a95-111">`a.x = 10` ifade, B sınıfının bir örneği değil, Main yöntemi içinde yapıldığından bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="46a95-111">The statement `a.x = 10` generates an error because it is made within the static method Main, and not an instance of class B.</span></span>

<span data-ttu-id="46a95-112">Struct devralınamadığı için yapı üyeleri korunamaz.</span><span class="sxs-lookup"><span data-stu-id="46a95-112">Struct members cannot be protected because the struct cannot be inherited.</span></span>

## <a name="example"></a><span data-ttu-id="46a95-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="46a95-113">Example</span></span>

<span data-ttu-id="46a95-114">Bu örnekte, `DerivedPoint` sınıfı `Point`türetilir.</span><span class="sxs-lookup"><span data-stu-id="46a95-114">In this example, the class `DerivedPoint` is derived from `Point`.</span></span> <span data-ttu-id="46a95-115">Bu nedenle, doğrudan türetilmiş sınıftan temel sınıfın korunan üyelerine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46a95-115">Therefore, you can access the protected members of the base class directly from the derived class.</span></span>

[!code-csharp[csrefKeywordsModifiers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#12)]  

<span data-ttu-id="46a95-116">`x` ve `y` erişim düzeylerini [özel](private.md)olarak değiştirirseniz, derleyici hata iletilerini verebilir:</span><span class="sxs-lookup"><span data-stu-id="46a95-116">If you change the access levels of `x` and `y` to [private](private.md), the compiler will issue the error messages:</span></span>

`'Point.y' is inaccessible due to its protection level.`

`'Point.x' is inaccessible due to its protection level.`

## <a name="c-language-specification"></a><span data-ttu-id="46a95-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="46a95-117">C# language specification</span></span>  

<span data-ttu-id="46a95-118">Daha fazla bilgi için bkz. [ C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Erişilebilirlik bildirimi](~/_csharplang/spec/basic-concepts.md#declared-accessibility) .</span><span class="sxs-lookup"><span data-stu-id="46a95-118">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="46a95-119">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="46a95-119">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="46a95-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46a95-120">See also</span></span>

- [<span data-ttu-id="46a95-121">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="46a95-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="46a95-122">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="46a95-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="46a95-123">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="46a95-123">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="46a95-124">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="46a95-124">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="46a95-125">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="46a95-125">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="46a95-126">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="46a95-126">Modifiers</span></span>](index.md)
- [<span data-ttu-id="46a95-127">public</span><span class="sxs-lookup"><span data-stu-id="46a95-127">public</span></span>](public.md)
- [<span data-ttu-id="46a95-128">private</span><span class="sxs-lookup"><span data-stu-id="46a95-128">private</span></span>](private.md)
- [<span data-ttu-id="46a95-129">internal</span><span class="sxs-lookup"><span data-stu-id="46a95-129">internal</span></span>](internal.md)
- <span data-ttu-id="46a95-130">[İç sanal anahtar sözcüklere yönelik güvenlik sorunları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="46a95-130">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
