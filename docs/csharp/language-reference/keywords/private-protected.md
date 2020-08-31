---
description: özel korumalı-C# başvurusu
title: özel korumalı-C# başvurusu
ms.date: 11/15/2017
f1_keywords:
- privateprotected_CSharpKeyword
author: sputier
ms.openlocfilehash: d83fd2a570b735a029bd2a79ad24e30d235dc5fb
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89117967"
---
# <a name="private-protected-c-reference"></a><span data-ttu-id="475c7-103">özel korumalı (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="475c7-103">private protected (C# Reference)</span></span>

<span data-ttu-id="475c7-104">`private protected`Anahtar sözcük birleşimi bir üye erişim değiştiricisidir.</span><span class="sxs-lookup"><span data-stu-id="475c7-104">The `private protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="475c7-105">Özel korumalı bir üyeye, kapsayan sınıftan türetilmiş türler tarafından erişilebilir, ancak yalnızca kendi kapsayıcı bütünleştirilmiş kodu içinde erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="475c7-105">A private protected member is accessible by types derived from the containing class, but only within its containing assembly.</span></span> <span data-ttu-id="475c7-106">`private protected`Diğer erişim değiştiricilerine ilişkin bir karşılaştırma için bkz. [Erişilebilirlik düzeyleri](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="475c7-106">For a comparison of `private protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

> [!NOTE]
> <span data-ttu-id="475c7-107">`private protected`Access Modifier, C# sürüm 7,2 ve üzeri sürümlerde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="475c7-107">The `private protected` access modifier is valid in C# version 7.2 and later.</span></span>

## <a name="example"></a><span data-ttu-id="475c7-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="475c7-108">Example</span></span>

<span data-ttu-id="475c7-109">Bir temel sınıfın özel korumalı bir üyesine, yalnızca değişkenin statik türü türetilmiş sınıf türü ise, kendisini kapsayan derlemede bulunan türetilmiş türlerden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="475c7-109">A private protected member of a base class is accessible from derived types in its containing assembly only if the static type of the variable is the derived class type.</span></span> <span data-ttu-id="475c7-110">Örneğin, aşağıdaki kod kesimini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="475c7-110">For example, consider the following code segment:</span></span>

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

<span data-ttu-id="475c7-111">Bu örnek, ve olmak üzere iki dosya içerir `Assembly1.cs` `Assembly2.cs` .</span><span class="sxs-lookup"><span data-stu-id="475c7-111">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="475c7-112">İlk dosya, bir ortak temel sınıf, `BaseClass` ve ondan türetilmiş bir tür içerir `DerivedClass1` .</span><span class="sxs-lookup"><span data-stu-id="475c7-112">The first file contains a public base class, `BaseClass`, and a type derived from it, `DerivedClass1`.</span></span> <span data-ttu-id="475c7-113">`BaseClass` , `myValue` iki şekilde erişmeye çalışan özel korumalı bir üyenin sahibidir `DerivedClass1` .</span><span class="sxs-lookup"><span data-stu-id="475c7-113">`BaseClass` owns a private protected member, `myValue`, which `DerivedClass1` tries to access in two ways.</span></span> <span data-ttu-id="475c7-114">Bir örneğinden ilk erişme girişimi `myValue` `BaseClass` bir hata üretir.</span><span class="sxs-lookup"><span data-stu-id="475c7-114">The first attempt to access `myValue` through an instance of `BaseClass` will produce an error.</span></span> <span data-ttu-id="475c7-115">Ancak, bunu devralınmış bir üye olarak kullanma girişimi `DerivedClass1` başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="475c7-115">However, the attempt to use it as an inherited member in `DerivedClass1` will succeed.</span></span>

<span data-ttu-id="475c7-116">İkinci dosyada, devralınan bir üye olarak erişim girişimi `myValue` `DerivedClass2` yalnızca Assembly1 içindeki türetilmiş türler tarafından erişilebilen bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="475c7-116">In the second file, an attempt to access `myValue` as an inherited member of `DerivedClass2` will produce an error, as it is only accessible by derived types in Assembly1.</span></span>

<span data-ttu-id="475c7-117">`Assembly1.cs` <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Bu adları içeriyorsa `Assembly2` , türetilmiş sınıfın `DerivedClass1` `private protected` içinde belirtilen üyelere erişimi olur `BaseClass` .</span><span class="sxs-lookup"><span data-stu-id="475c7-117">If `Assembly1.cs` contains an <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> that names `Assembly2`, the derived class `DerivedClass1` will have access to `private protected` members declared in `BaseClass`.</span></span> <span data-ttu-id="475c7-118">`InternalsVisibleTo``private protected`üyeleri diğer derlemelerdeki türetilmiş sınıflara görünür hale getirir.</span><span class="sxs-lookup"><span data-stu-id="475c7-118">`InternalsVisibleTo` makes `private protected` members visible to derived classes in other assemblies.</span></span>

<span data-ttu-id="475c7-119">Struct üye olamaz `private protected` çünkü yapı devralınamaz.</span><span class="sxs-lookup"><span data-stu-id="475c7-119">Struct members cannot be `private protected` because the struct cannot be inherited.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="475c7-120">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="475c7-120">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="475c7-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="475c7-121">See also</span></span>

- [<span data-ttu-id="475c7-122">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="475c7-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="475c7-123">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="475c7-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="475c7-124">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="475c7-124">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="475c7-125">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="475c7-125">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="475c7-126">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="475c7-126">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="475c7-127">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="475c7-127">Modifiers</span></span>](index.md)
- [<span data-ttu-id="475c7-128">genel</span><span class="sxs-lookup"><span data-stu-id="475c7-128">public</span></span>](public.md)
- [<span data-ttu-id="475c7-129">private</span><span class="sxs-lookup"><span data-stu-id="475c7-129">private</span></span>](private.md)
- [<span data-ttu-id="475c7-130">internal</span><span class="sxs-lookup"><span data-stu-id="475c7-130">internal</span></span>](internal.md)
- <span data-ttu-id="475c7-131">[İç sanal anahtar sözcüklere yönelik güvenlik sorunları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="475c7-131">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
