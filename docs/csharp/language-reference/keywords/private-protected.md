---
description: özel korumalı-C# başvurusu
title: özel korumalı-C# başvurusu
ms.date: 11/15/2017
f1_keywords:
- privateprotected_CSharpKeyword
author: sputier
ms.openlocfilehash: e7ef6d691b43abd3d07321adfc0c166629ce9098
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537307"
---
# <a name="private-protected-c-reference"></a><span data-ttu-id="031db-103">özel korumalı (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="031db-103">private protected (C# Reference)</span></span>

<span data-ttu-id="031db-104">`private protected`Anahtar sözcük birleşimi bir üye erişim değiştiricisidir.</span><span class="sxs-lookup"><span data-stu-id="031db-104">The `private protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="031db-105">Özel korumalı bir üyeye, kapsayan sınıftan türetilmiş türler tarafından erişilebilir, ancak yalnızca kendi kapsayıcı bütünleştirilmiş kodu içinde erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="031db-105">A private protected member is accessible by types derived from the containing class, but only within its containing assembly.</span></span> <span data-ttu-id="031db-106">`private protected`Diğer erişim değiştiricilerine ilişkin bir karşılaştırma için bkz. [Erişilebilirlik düzeyleri](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="031db-106">For a comparison of `private protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

> [!NOTE]
> <span data-ttu-id="031db-107">`private protected`Access Modifier, C# sürüm 7,2 ve üzeri sürümlerde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="031db-107">The `private protected` access modifier is valid in C# version 7.2 and later.</span></span>

## <a name="example"></a><span data-ttu-id="031db-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="031db-108">Example</span></span>

<span data-ttu-id="031db-109">Bir temel sınıfın özel korumalı bir üyesine, yalnızca değişkenin statik türü türetilmiş sınıf türü ise, kendisini kapsayan derlemede bulunan türetilmiş türlerden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="031db-109">A private protected member of a base class is accessible from derived types in its containing assembly only if the static type of the variable is the derived class type.</span></span> <span data-ttu-id="031db-110">Örneğin, aşağıdaki kod kesimini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="031db-110">For example, consider the following code segment:</span></span>

```csharp
public class BaseClass
{
    private protected int myValue = 0;
}

public class DerivedClass1 : BaseClass
{
    void Access()
    {
        var baseObject = new BaseClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 5;

        // OK, accessed through the current derived class instance
        myValue = 5;
    }
}
```

```csharp
// Assembly2.cs
// Compile with: /reference:Assembly1.dll
class DerivedClass2 : BaseClass
{
    void Access()
    {
        // Error CS0122, because myValue can only be
        // accessed by types in Assembly1
        // myValue = 10;
    }
}
```

<span data-ttu-id="031db-111">Bu örnek, ve olmak üzere iki dosya içerir `Assembly1.cs` `Assembly2.cs` .</span><span class="sxs-lookup"><span data-stu-id="031db-111">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="031db-112">İlk dosya, bir ortak temel sınıf, `BaseClass` ve ondan türetilmiş bir tür içerir `DerivedClass1` .</span><span class="sxs-lookup"><span data-stu-id="031db-112">The first file contains a public base class, `BaseClass`, and a type derived from it, `DerivedClass1`.</span></span> <span data-ttu-id="031db-113">`BaseClass` , `myValue` iki şekilde erişmeye çalışan özel korumalı bir üyenin sahibidir `DerivedClass1` .</span><span class="sxs-lookup"><span data-stu-id="031db-113">`BaseClass` owns a private protected member, `myValue`, which `DerivedClass1` tries to access in two ways.</span></span> <span data-ttu-id="031db-114">Bir örneğinden ilk erişme girişimi `myValue` `BaseClass` bir hata üretir.</span><span class="sxs-lookup"><span data-stu-id="031db-114">The first attempt to access `myValue` through an instance of `BaseClass` will produce an error.</span></span> <span data-ttu-id="031db-115">Ancak, bunu devralınmış bir üye olarak kullanma girişimi `DerivedClass1` başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="031db-115">However, the attempt to use it as an inherited member in `DerivedClass1` will succeed.</span></span>

<span data-ttu-id="031db-116">İkinci dosyada, devralınan bir üye olarak erişim girişimi `myValue` `DerivedClass2` yalnızca Assembly1 içindeki türetilmiş türler tarafından erişilebilen bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="031db-116">In the second file, an attempt to access `myValue` as an inherited member of `DerivedClass2` will produce an error, as it is only accessible by derived types in Assembly1.</span></span>

<span data-ttu-id="031db-117">`Assembly1.cs` <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Bu adları içeriyorsa `Assembly2` , türetilmiş sınıfın `DerivedClass1` `private protected` içinde belirtilen üyelere erişimi olur `BaseClass` .</span><span class="sxs-lookup"><span data-stu-id="031db-117">If `Assembly1.cs` contains an <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> that names `Assembly2`, the derived class `DerivedClass1` will have access to `private protected` members declared in `BaseClass`.</span></span> <span data-ttu-id="031db-118">`InternalsVisibleTo``private protected`üyeleri diğer derlemelerdeki türetilmiş sınıflara görünür hale getirir.</span><span class="sxs-lookup"><span data-stu-id="031db-118">`InternalsVisibleTo` makes `private protected` members visible to derived classes in other assemblies.</span></span>

<span data-ttu-id="031db-119">Struct üye olamaz `private protected` çünkü yapı devralınamaz.</span><span class="sxs-lookup"><span data-stu-id="031db-119">Struct members cannot be `private protected` because the struct cannot be inherited.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="031db-120">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="031db-120">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="031db-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="031db-121">See also</span></span>

- [<span data-ttu-id="031db-122">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="031db-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="031db-123">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="031db-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="031db-124">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="031db-124">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="031db-125">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="031db-125">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="031db-126">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="031db-126">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="031db-127">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="031db-127">Modifiers</span></span>](index.md)
- [<span data-ttu-id="031db-128">genel</span><span class="sxs-lookup"><span data-stu-id="031db-128">public</span></span>](public.md)
- [<span data-ttu-id="031db-129">private</span><span class="sxs-lookup"><span data-stu-id="031db-129">private</span></span>](private.md)
- [<span data-ttu-id="031db-130">internal</span><span class="sxs-lookup"><span data-stu-id="031db-130">internal</span></span>](internal.md)
- <span data-ttu-id="031db-131">[İç sanal anahtar sözcüklere yönelik güvenlik sorunları](/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="031db-131">[Security concerns for internal virtual keywords](/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
