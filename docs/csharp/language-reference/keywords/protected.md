---
title: protected anahtar sözcüğü C# -başvuru
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: bec619d4f49bd26daa742c18c830909c14948adf
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713189"
---
# <a name="protected-c-reference"></a><span data-ttu-id="e48a0-102">protected (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e48a0-102">protected (C# Reference)</span></span>

<span data-ttu-id="e48a0-103">`protected` anahtar sözcüğü bir üye erişim değiştiricisidir.</span><span class="sxs-lookup"><span data-stu-id="e48a0-103">The `protected` keyword is a member access modifier.</span></span>

 > <span data-ttu-id="e48a0-104">Bu sayfa `protected` erişimi içerir.</span><span class="sxs-lookup"><span data-stu-id="e48a0-104">This page covers `protected` access.</span></span> <span data-ttu-id="e48a0-105">`protected` anahtar sözcüğü ayrıca [`protected internal`](protected-internal.md) ve [`private protected`](private-protected.md) erişim değiştiricilerinden de bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="e48a0-105">The `protected` keyword is also part of the [`protected internal`](protected-internal.md) and [`private protected`](private-protected.md) access modifiers.</span></span>

<span data-ttu-id="e48a0-106">Korunan bir üyeye kendi sınıfı içinde ve türetilmiş sınıf örnekleri tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="e48a0-106">A protected member is accessible within its class and by derived class instances.</span></span>

<span data-ttu-id="e48a0-107">Diğer erişim değiştiricilerine sahip `protected` bir karşılaştırması için bkz. [Erişilebilirlik düzeyleri](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="e48a0-107">For a comparison of `protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="e48a0-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="e48a0-108">Example</span></span>

<span data-ttu-id="e48a0-109">Bir temel sınıfın korunan üyesine, yalnızca erişim türetilmiş sınıf türü aracılığıyla gerçekleşirse türetilmiş bir sınıfta erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="e48a0-109">A protected member of a base class is accessible in a derived class only if the access occurs through the derived class type.</span></span> <span data-ttu-id="e48a0-110">Örneğin, aşağıdaki kod kesimini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="e48a0-110">For example, consider the following code segment:</span></span>

[!code-csharp[csrefKeywordsModifiers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#11)]

<span data-ttu-id="e48a0-111">`a.x = 10` ifade, B sınıfının bir örneği değil, Main yöntemi içinde yapıldığından bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e48a0-111">The statement `a.x = 10` generates an error because it is made within the static method Main, and not an instance of class B.</span></span>

<span data-ttu-id="e48a0-112">Struct devralınamadığı için yapı üyeleri korunamaz.</span><span class="sxs-lookup"><span data-stu-id="e48a0-112">Struct members cannot be protected because the struct cannot be inherited.</span></span>

## <a name="example"></a><span data-ttu-id="e48a0-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="e48a0-113">Example</span></span>

<span data-ttu-id="e48a0-114">Bu örnekte, `DerivedPoint` sınıfı `Point`türetilir.</span><span class="sxs-lookup"><span data-stu-id="e48a0-114">In this example, the class `DerivedPoint` is derived from `Point`.</span></span> <span data-ttu-id="e48a0-115">Bu nedenle, doğrudan türetilmiş sınıftan temel sınıfın korunan üyelerine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e48a0-115">Therefore, you can access the protected members of the base class directly from the derived class.</span></span>

[!code-csharp[csrefKeywordsModifiers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#12)]  

<span data-ttu-id="e48a0-116">`x` ve `y` erişim düzeylerini [özel](private.md)olarak değiştirirseniz, derleyici hata iletilerini verebilir:</span><span class="sxs-lookup"><span data-stu-id="e48a0-116">If you change the access levels of `x` and `y` to [private](private.md), the compiler will issue the error messages:</span></span>

`'Point.y' is inaccessible due to its protection level.`

`'Point.x' is inaccessible due to its protection level.`

## <a name="c-language-specification"></a><span data-ttu-id="e48a0-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="e48a0-117">C# language specification</span></span>  

<span data-ttu-id="e48a0-118">Daha fazla bilgi için bkz. [ C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Erişilebilirlik bildirimi](~/_csharplang/spec/basic-concepts.md#declared-accessibility) .</span><span class="sxs-lookup"><span data-stu-id="e48a0-118">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="e48a0-119">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="e48a0-119">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="e48a0-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e48a0-120">See also</span></span>

- [<span data-ttu-id="e48a0-121">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="e48a0-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e48a0-122">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e48a0-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e48a0-123">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="e48a0-123">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="e48a0-124">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="e48a0-124">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="e48a0-125">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="e48a0-125">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="e48a0-126">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="e48a0-126">Modifiers</span></span>](index.md)
- [<span data-ttu-id="e48a0-127">public</span><span class="sxs-lookup"><span data-stu-id="e48a0-127">public</span></span>](public.md)
- [<span data-ttu-id="e48a0-128">private</span><span class="sxs-lookup"><span data-stu-id="e48a0-128">private</span></span>](private.md)
- [<span data-ttu-id="e48a0-129">internal</span><span class="sxs-lookup"><span data-stu-id="e48a0-129">internal</span></span>](internal.md)
- <span data-ttu-id="e48a0-130">[İç sanal anahtar sözcüklere yönelik güvenlik sorunları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e48a0-130">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
