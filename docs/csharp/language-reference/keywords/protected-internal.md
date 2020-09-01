---
description: Protected Internal-C# başvurusu
title: Protected Internal-C# başvurusu
ms.date: 11/15/2017
f1_keywords:
- protectedinternal_CSharpKeyword
author: sputier
ms.openlocfilehash: a7537fba93c0d7145f04c6236d15c11b70f8bf98
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139443"
---
# <a name="protected-internal-c-reference"></a><span data-ttu-id="a4a12-103">korumalı iç (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a4a12-103">protected internal (C# Reference)</span></span>

<span data-ttu-id="a4a12-104">`protected internal`Anahtar sözcük birleşimi bir üye erişim değiştiricisidir.</span><span class="sxs-lookup"><span data-stu-id="a4a12-104">The `protected internal` keyword combination is a member access modifier.</span></span> <span data-ttu-id="a4a12-105">Korunan bir iç üyeye geçerli derlemeden veya kapsayan sınıftan türetilmiş türlerden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="a4a12-105">A protected internal member is accessible from the current assembly or from types that are derived from the containing class.</span></span> <span data-ttu-id="a4a12-106">`protected internal`Diğer erişim değiştiricilerine ilişkin bir karşılaştırma için bkz. [Erişilebilirlik düzeyleri](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="a4a12-106">For a comparison of `protected internal` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="a4a12-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="a4a12-107">Example</span></span>

<span data-ttu-id="a4a12-108">Bir temel sınıfın korunan iç üyesine, kendisini içeren derleme içindeki herhangi bir türden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="a4a12-108">A protected internal member of a base class is accessible from any type within its containing assembly.</span></span> <span data-ttu-id="a4a12-109">Ayrıca, başka bir derlemede bulunan türetilmiş bir sınıfta, yalnızca erişim türetilmiş sınıf türünün bir değişkeniyle gerçekleşirse erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="a4a12-109">It is also accessible in a derived class located in another assembly only if the access occurs through a variable of the derived class type.</span></span> <span data-ttu-id="a4a12-110">Örneğin, aşağıdaki kod kesimini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="a4a12-110">For example, consider the following code segment:</span></span>

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

<span data-ttu-id="a4a12-111">Bu örnek, ve olmak üzere iki dosya içerir `Assembly1.cs` `Assembly2.cs` .</span><span class="sxs-lookup"><span data-stu-id="a4a12-111">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="a4a12-112">İlk dosya bir ortak temel sınıf, `BaseClass` ve başka bir sınıf içerir `TestAccess` .</span><span class="sxs-lookup"><span data-stu-id="a4a12-112">The first file contains a public base class, `BaseClass`, and another class, `TestAccess`.</span></span> <span data-ttu-id="a4a12-113">`BaseClass` , türü tarafından erişilen korumalı bir iç üyeye sahip `myValue` `TestAccess` .</span><span class="sxs-lookup"><span data-stu-id="a4a12-113">`BaseClass` owns a protected internal member, `myValue`, which is accessed by the `TestAccess` type.</span></span>
<span data-ttu-id="a4a12-114">İkinci dosyada, `myValue` bir örneği üzerinden erişim girişimi `BaseClass` bir hata üretir, bu üyeye türetilmiş bir sınıf örneği aracılığıyla erişim `DerivedClass` başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="a4a12-114">In the second file, an attempt to access `myValue` through an instance of `BaseClass` will produce an error, while an access to this member through an instance of a derived class, `DerivedClass` will succeed.</span></span>

<span data-ttu-id="a4a12-115">Struct üye olamaz `protected internal` çünkü yapı devralınamaz.</span><span class="sxs-lookup"><span data-stu-id="a4a12-115">Struct members cannot be `protected internal` because the struct cannot be inherited.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a4a12-116">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="a4a12-116">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="a4a12-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4a12-117">See also</span></span>

- [<span data-ttu-id="a4a12-118">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="a4a12-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a4a12-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a4a12-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a4a12-120">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="a4a12-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="a4a12-121">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="a4a12-121">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="a4a12-122">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="a4a12-122">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="a4a12-123">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="a4a12-123">Modifiers</span></span>](index.md)
- [<span data-ttu-id="a4a12-124">genel</span><span class="sxs-lookup"><span data-stu-id="a4a12-124">public</span></span>](public.md)
- [<span data-ttu-id="a4a12-125">private</span><span class="sxs-lookup"><span data-stu-id="a4a12-125">private</span></span>](private.md)
- [<span data-ttu-id="a4a12-126">internal</span><span class="sxs-lookup"><span data-stu-id="a4a12-126">internal</span></span>](internal.md)
- <span data-ttu-id="a4a12-127">[İç sanal anahtar sözcüklere yönelik güvenlik sorunları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a4a12-127">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
