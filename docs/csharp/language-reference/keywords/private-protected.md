---
title: özel korumalı - C# Referans
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 01a8b716ce87a63a50a92a25b2842f7bb12d4c9f
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134358"
---
# <a name="private-protected-c-reference"></a><span data-ttu-id="f309e-102">özel korumalı (C# Reference)</span><span class="sxs-lookup"><span data-stu-id="f309e-102">private protected (C# Reference)</span></span>

<span data-ttu-id="f309e-103">`private protected` Anahtar kelime birleşimi bir üye erişim değiştiricidir.</span><span class="sxs-lookup"><span data-stu-id="f309e-103">The `private protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="f309e-104">Özel korumalı bir üye, içerdiği sınıftan türetilen türlere, ancak yalnızca kendi içderlemesi içinde erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="f309e-104">A private protected member is accessible by types derived from the containing class, but only within its containing assembly.</span></span> <span data-ttu-id="f309e-105">Diğer erişim `private protected` değiştiriciler ile karşılaştırma için [Erişilebilirlik Düzeyleri'ne](accessibility-levels.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="f309e-105">For a comparison of `private protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

> [!NOTE]
> <span data-ttu-id="f309e-106">Erişim `private protected` değiştirici C# sürüm 7.2 ve sonraki sürümlerinde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f309e-106">The `private protected` access modifier is valid in C# version 7.2 and later.</span></span>

## <a name="example"></a><span data-ttu-id="f309e-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="f309e-107">Example</span></span>

<span data-ttu-id="f309e-108">Taban sınıfın özel korumalı üyesine, yalnızca değişkenin statik türü türetilmiş sınıf türüyse, içerdiği derlemedeki türetilmiş türlerden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="f309e-108">A private protected member of a base class is accessible from derived types in its containing assembly only if the static type of the variable is the derived class type.</span></span> <span data-ttu-id="f309e-109">Örneğin, aşağıdaki kod kesimini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="f309e-109">For example, consider the following code segment:</span></span>  

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

<span data-ttu-id="f309e-110">Bu örnekte iki `Assembly1.cs` `Assembly2.cs`dosya ve .</span><span class="sxs-lookup"><span data-stu-id="f309e-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="f309e-111">İlk dosya, ortak taban `BaseClass`sınıf ve ondan türetilen `DerivedClass1`bir tür içerir.</span><span class="sxs-lookup"><span data-stu-id="f309e-111">The first file contains a public base class, `BaseClass`, and a type derived from it, `DerivedClass1`.</span></span> <span data-ttu-id="f309e-112">`BaseClass`iki şekilde erişmeye `myValue`çalışan `DerivedClass1` özel bir korumalı üyesi ne sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f309e-112">`BaseClass` owns a private protected member, `myValue`, which `DerivedClass1` tries to access in two ways.</span></span> <span data-ttu-id="f309e-113">Bir örnek üzerinden `myValue` erişmek için `BaseClass` ilk girişimi bir hata üretecek.</span><span class="sxs-lookup"><span data-stu-id="f309e-113">The first attempt to access `myValue` through an instance of `BaseClass` will produce an error.</span></span> <span data-ttu-id="f309e-114">Ancak, kalıtsal bir üye olarak kullanma `DerivedClass1` girişimi başarılı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="f309e-114">However, the attempt to use it as an inherited member in `DerivedClass1` will succeed.</span></span>
<span data-ttu-id="f309e-115">İkinci dosyada, devralınan `myValue` bir üye `DerivedClass2` olarak erişme girişimi, yalnızca Derleme1'de türetilen türler tarafından erişilebilir olduğundan bir hata üretir.</span><span class="sxs-lookup"><span data-stu-id="f309e-115">In the second file, an attempt to access `myValue` as an inherited member of `DerivedClass2` will produce an error, as it is only accessible by derived types in Assembly1.</span></span>

<span data-ttu-id="f309e-116">Yapı üyeleri, yapının devralınamayacağı için olamaz. `private protected`</span><span class="sxs-lookup"><span data-stu-id="f309e-116">Struct members cannot be `private protected` because the struct cannot be inherited.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="f309e-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="f309e-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a><span data-ttu-id="f309e-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f309e-118">See also</span></span>

- [<span data-ttu-id="f309e-119">C# Referans</span><span class="sxs-lookup"><span data-stu-id="f309e-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f309e-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f309e-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f309e-121">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="f309e-121">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f309e-122">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="f309e-122">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="f309e-123">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="f309e-123">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="f309e-124">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="f309e-124">Modifiers</span></span>](index.md)
- [<span data-ttu-id="f309e-125">Kamu</span><span class="sxs-lookup"><span data-stu-id="f309e-125">public</span></span>](public.md)
- [<span data-ttu-id="f309e-126">Özel</span><span class="sxs-lookup"><span data-stu-id="f309e-126">private</span></span>](private.md)
- [<span data-ttu-id="f309e-127">Iç</span><span class="sxs-lookup"><span data-stu-id="f309e-127">internal</span></span>](internal.md)
- <span data-ttu-id="f309e-128">[Dahili sanal anahtar kelimeler için güvenlik endişeleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f309e-128">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
