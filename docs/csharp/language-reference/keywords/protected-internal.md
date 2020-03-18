---
title: korumalı dahili - C# Referans
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 877df74b51fb859043171619f5687ecddb8409d1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713202"
---
# <a name="protected-internal-c-reference"></a><span data-ttu-id="a3a45-102">korumalı dahili (C# Reference)</span><span class="sxs-lookup"><span data-stu-id="a3a45-102">protected internal (C# Reference)</span></span>

<span data-ttu-id="a3a45-103">`protected internal` Anahtar kelime birleşimi bir üye erişim değiştiricidir.</span><span class="sxs-lookup"><span data-stu-id="a3a45-103">The `protected internal` keyword combination is a member access modifier.</span></span> <span data-ttu-id="a3a45-104">Korumalı bir iç üyeye geçerli derlemeden veya içeren sınıftan türetilen türlerden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="a3a45-104">A protected internal member is accessible from the current assembly or from types that are derived from the containing class.</span></span> <span data-ttu-id="a3a45-105">Diğer erişim `protected internal` değiştiriciler ile karşılaştırma için [Erişilebilirlik Düzeyleri'ne](accessibility-levels.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="a3a45-105">For a comparison of `protected internal` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="a3a45-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="a3a45-106">Example</span></span>

<span data-ttu-id="a3a45-107">Taban sınıfın korumalı bir iç üyesine, içerdiği derlemedeki herhangi bir türden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="a3a45-107">A protected internal member of a base class is accessible from any type within its containing assembly.</span></span> <span data-ttu-id="a3a45-108">Erişim türemiş sınıf türünden bir değişken aracılığıyla oluşursa, başka bir derlemede bulunan türemiş bir sınıfta da erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="a3a45-108">It is also accessible in a derived class located in another assembly only if the access occurs through a variable of the derived class type.</span></span> <span data-ttu-id="a3a45-109">Örneğin, aşağıdaki kod kesimini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="a3a45-109">For example, consider the following code segment:</span></span>

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

<span data-ttu-id="a3a45-110">Bu örnekte iki `Assembly1.cs` `Assembly2.cs`dosya ve .</span><span class="sxs-lookup"><span data-stu-id="a3a45-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="a3a45-111">İlk dosya, ortak taban `BaseClass`sınıf ve başka `TestAccess`bir sınıf içerir.</span><span class="sxs-lookup"><span data-stu-id="a3a45-111">The first file contains a public base class, `BaseClass`, and another class, `TestAccess`.</span></span> <span data-ttu-id="a3a45-112">`BaseClass`türüne göre erişilen korumalı bir `TestAccess` dahili üyeye `myValue`sahip.</span><span class="sxs-lookup"><span data-stu-id="a3a45-112">`BaseClass` owns a protected internal member, `myValue`, which is accessed by the `TestAccess` type.</span></span>
<span data-ttu-id="a3a45-113">İkinci dosyada, bir hata `myValue` örneği `BaseClass` üzerinden erişim girişimi bir hata üretirken, türetilmiş bir `DerivedClass` sınıfın bir örneği aracılığıyla bu üyeye erişim başarılı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a3a45-113">In the second file, an attempt to access `myValue` through an instance of `BaseClass` will produce an error, while an access to this member through an instance of a derived class, `DerivedClass` will succeed.</span></span>

<span data-ttu-id="a3a45-114">Yapı üyeleri, yapının devralınamayacağı için olamaz. `protected internal`</span><span class="sxs-lookup"><span data-stu-id="a3a45-114">Struct members cannot be `protected internal` because the struct cannot be inherited.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a3a45-115">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="a3a45-115">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="a3a45-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3a45-116">See also</span></span>

- [<span data-ttu-id="a3a45-117">C# Referans</span><span class="sxs-lookup"><span data-stu-id="a3a45-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a3a45-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a3a45-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a3a45-119">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="a3a45-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="a3a45-120">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="a3a45-120">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="a3a45-121">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="a3a45-121">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="a3a45-122">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="a3a45-122">Modifiers</span></span>](index.md)
- [<span data-ttu-id="a3a45-123">Kamu</span><span class="sxs-lookup"><span data-stu-id="a3a45-123">public</span></span>](public.md)
- [<span data-ttu-id="a3a45-124">Özel</span><span class="sxs-lookup"><span data-stu-id="a3a45-124">private</span></span>](private.md)
- [<span data-ttu-id="a3a45-125">Iç</span><span class="sxs-lookup"><span data-stu-id="a3a45-125">internal</span></span>](internal.md)
- <span data-ttu-id="a3a45-126">[Dahili sanal anahtar kelimeler için güvenlik endişeleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a3a45-126">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
