---
title: özel korumalı - C# Referans
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 03fa90582d096919f2e6546fae2fde28e486fe41
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463050"
---
# <a name="private-protected-c-reference"></a><span data-ttu-id="16359-102">özel korumalı (C# Reference)</span><span class="sxs-lookup"><span data-stu-id="16359-102">private protected (C# Reference)</span></span>

<span data-ttu-id="16359-103">`private protected` Anahtar kelime birleşimi bir üye erişim değiştiricidir.</span><span class="sxs-lookup"><span data-stu-id="16359-103">The `private protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="16359-104">Özel korumalı bir üye, içerdiği sınıftan türetilen türlere, ancak yalnızca kendi içderlemesi içinde erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="16359-104">A private protected member is accessible by types derived from the containing class, but only within its containing assembly.</span></span> <span data-ttu-id="16359-105">Diğer erişim `private protected` değiştiriciler ile karşılaştırma için [Erişilebilirlik Düzeyleri'ne](accessibility-levels.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="16359-105">For a comparison of `private protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

> [!NOTE]
> <span data-ttu-id="16359-106">Erişim `private protected` değiştirici C# sürüm 7.2 ve sonraki sürümlerinde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="16359-106">The `private protected` access modifier is valid in C# version 7.2 and later.</span></span>

## <a name="example"></a><span data-ttu-id="16359-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="16359-107">Example</span></span>

<span data-ttu-id="16359-108">Taban sınıfın özel korumalı üyesine, yalnızca değişkenin statik türü türetilmiş sınıf türüyse, içerdiği derlemedeki türetilmiş türlerden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="16359-108">A private protected member of a base class is accessible from derived types in its containing assembly only if the static type of the variable is the derived class type.</span></span> <span data-ttu-id="16359-109">Örneğin, aşağıdaki kod kesimini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="16359-109">For example, consider the following code segment:</span></span>

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

<span data-ttu-id="16359-110">Bu örnekte iki `Assembly1.cs` `Assembly2.cs`dosya ve .</span><span class="sxs-lookup"><span data-stu-id="16359-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="16359-111">İlk dosya, ortak taban `BaseClass`sınıf ve ondan türetilen `DerivedClass1`bir tür içerir.</span><span class="sxs-lookup"><span data-stu-id="16359-111">The first file contains a public base class, `BaseClass`, and a type derived from it, `DerivedClass1`.</span></span> <span data-ttu-id="16359-112">`BaseClass`iki şekilde erişmeye `myValue`çalışan `DerivedClass1` özel bir korumalı üyesi ne sahiptir.</span><span class="sxs-lookup"><span data-stu-id="16359-112">`BaseClass` owns a private protected member, `myValue`, which `DerivedClass1` tries to access in two ways.</span></span> <span data-ttu-id="16359-113">Bir örnek üzerinden `myValue` erişmek için `BaseClass` ilk girişimi bir hata üretecek.</span><span class="sxs-lookup"><span data-stu-id="16359-113">The first attempt to access `myValue` through an instance of `BaseClass` will produce an error.</span></span> <span data-ttu-id="16359-114">Ancak, kalıtsal bir üye olarak kullanma `DerivedClass1` girişimi başarılı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="16359-114">However, the attempt to use it as an inherited member in `DerivedClass1` will succeed.</span></span>

<span data-ttu-id="16359-115">İkinci dosyada, devralınan `myValue` bir üye `DerivedClass2` olarak erişme girişimi, yalnızca Derleme1'de türetilen türler tarafından erişilebilir olduğundan bir hata üretir.</span><span class="sxs-lookup"><span data-stu-id="16359-115">In the second file, an attempt to access `myValue` as an inherited member of `DerivedClass2` will produce an error, as it is only accessible by derived types in Assembly1.</span></span>

<span data-ttu-id="16359-116">Bir `Assembly1.cs` ad <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> `Assembly2`içeriyorsa, `DerivedClass1` türemiş `private protected` sınıfın ' `BaseClass`da bildirilen üyelere erişimi olacak.</span><span class="sxs-lookup"><span data-stu-id="16359-116">If `Assembly1.cs` contains an <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> that names `Assembly2`, the derived class `DerivedClass1` will have access to `private protected` members declared in `BaseClass`.</span></span> <span data-ttu-id="16359-117">`InternalsVisibleTo`üyeleri `private protected` diğer derlemelerde türetilmiş sınıflara görünür kılar.</span><span class="sxs-lookup"><span data-stu-id="16359-117">`InternalsVisibleTo` makes `private protected` members visible to derived classes in other assemblies.</span></span>

<span data-ttu-id="16359-118">Yapı üyeleri, yapının devralınamayacağı için olamaz. `private protected`</span><span class="sxs-lookup"><span data-stu-id="16359-118">Struct members cannot be `private protected` because the struct cannot be inherited.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="16359-119">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="16359-119">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="16359-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16359-120">See also</span></span>

- [<span data-ttu-id="16359-121">C# Referans</span><span class="sxs-lookup"><span data-stu-id="16359-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="16359-122">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="16359-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="16359-123">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="16359-123">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="16359-124">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="16359-124">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="16359-125">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="16359-125">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="16359-126">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="16359-126">Modifiers</span></span>](index.md)
- [<span data-ttu-id="16359-127">public</span><span class="sxs-lookup"><span data-stu-id="16359-127">public</span></span>](public.md)
- [<span data-ttu-id="16359-128">private</span><span class="sxs-lookup"><span data-stu-id="16359-128">private</span></span>](private.md)
- [<span data-ttu-id="16359-129">internal</span><span class="sxs-lookup"><span data-stu-id="16359-129">internal</span></span>](internal.md)
- <span data-ttu-id="16359-130">[Dahili sanal anahtar kelimeler için güvenlik endişeleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="16359-130">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
