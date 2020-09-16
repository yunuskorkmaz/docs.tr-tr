---
description: Protected Internal-C# başvurusu
title: Protected Internal-C# başvurusu
ms.date: 11/15/2017
f1_keywords:
- protectedinternal_CSharpKeyword
author: sputier
ms.openlocfilehash: f22de104154df74f02c048b1209eeac754a03e64
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90536814"
---
# <a name="protected-internal-c-reference"></a><span data-ttu-id="90897-103">korumalı iç (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="90897-103">protected internal (C# Reference)</span></span>

<span data-ttu-id="90897-104">`protected internal`Anahtar sözcük birleşimi bir üye erişim değiştiricisidir.</span><span class="sxs-lookup"><span data-stu-id="90897-104">The `protected internal` keyword combination is a member access modifier.</span></span> <span data-ttu-id="90897-105">Korunan bir iç üyeye geçerli derlemeden veya kapsayan sınıftan türetilmiş türlerden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="90897-105">A protected internal member is accessible from the current assembly or from types that are derived from the containing class.</span></span> <span data-ttu-id="90897-106">`protected internal`Diğer erişim değiştiricilerine ilişkin bir karşılaştırma için bkz. [Erişilebilirlik düzeyleri](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="90897-106">For a comparison of `protected internal` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="90897-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="90897-107">Example</span></span>

<span data-ttu-id="90897-108">Bir temel sınıfın korunan iç üyesine, kendisini içeren derleme içindeki herhangi bir türden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="90897-108">A protected internal member of a base class is accessible from any type within its containing assembly.</span></span> <span data-ttu-id="90897-109">Ayrıca, başka bir derlemede bulunan türetilmiş bir sınıfta, yalnızca erişim türetilmiş sınıf türünün bir değişkeniyle gerçekleşirse erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="90897-109">It is also accessible in a derived class located in another assembly only if the access occurs through a variable of the derived class type.</span></span> <span data-ttu-id="90897-110">Örneğin, aşağıdaki kod kesimini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="90897-110">For example, consider the following code segment:</span></span>

```csharp
// Assembly1.cs
// Compile with: /target:library
public class BaseClass
{
   protected internal int myValue = 0;
}

class TestAccess
{
    void Access()
    {
        var baseObject = new BaseClass();
        baseObject.myValue = 5;
    }
}
```

```csharp
// Assembly2.cs
// Compile with: /reference:Assembly1.dll
class DerivedClass : BaseClass
{
    static void Main()
    {
        var baseObject = new BaseClass();
        var derivedObject = new DerivedClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 10;

        // OK, because this class derives from BaseClass.
        derivedObject.myValue = 10;
    }
}
```

<span data-ttu-id="90897-111">Bu örnek, ve olmak üzere iki dosya içerir `Assembly1.cs` `Assembly2.cs` .</span><span class="sxs-lookup"><span data-stu-id="90897-111">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="90897-112">İlk dosya bir ortak temel sınıf, `BaseClass` ve başka bir sınıf içerir `TestAccess` .</span><span class="sxs-lookup"><span data-stu-id="90897-112">The first file contains a public base class, `BaseClass`, and another class, `TestAccess`.</span></span> <span data-ttu-id="90897-113">`BaseClass` , türü tarafından erişilen korumalı bir iç üyeye sahip `myValue` `TestAccess` .</span><span class="sxs-lookup"><span data-stu-id="90897-113">`BaseClass` owns a protected internal member, `myValue`, which is accessed by the `TestAccess` type.</span></span>
<span data-ttu-id="90897-114">İkinci dosyada, `myValue` bir örneği üzerinden erişim girişimi `BaseClass` bir hata üretir, bu üyeye türetilmiş bir sınıf örneği aracılığıyla erişim `DerivedClass` başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="90897-114">In the second file, an attempt to access `myValue` through an instance of `BaseClass` will produce an error, while an access to this member through an instance of a derived class, `DerivedClass` will succeed.</span></span>

<span data-ttu-id="90897-115">Struct üye olamaz `protected internal` çünkü yapı devralınamaz.</span><span class="sxs-lookup"><span data-stu-id="90897-115">Struct members cannot be `protected internal` because the struct cannot be inherited.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="90897-116">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="90897-116">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="90897-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="90897-117">See also</span></span>

- [<span data-ttu-id="90897-118">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="90897-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="90897-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="90897-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="90897-120">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="90897-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="90897-121">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="90897-121">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="90897-122">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="90897-122">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="90897-123">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="90897-123">Modifiers</span></span>](index.md)
- [<span data-ttu-id="90897-124">genel</span><span class="sxs-lookup"><span data-stu-id="90897-124">public</span></span>](public.md)
- [<span data-ttu-id="90897-125">private</span><span class="sxs-lookup"><span data-stu-id="90897-125">private</span></span>](private.md)
- [<span data-ttu-id="90897-126">internal</span><span class="sxs-lookup"><span data-stu-id="90897-126">internal</span></span>](internal.md)
- <span data-ttu-id="90897-127">[İç sanal anahtar sözcüklere yönelik güvenlik sorunları](/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="90897-127">[Security concerns for internal virtual keywords](/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
