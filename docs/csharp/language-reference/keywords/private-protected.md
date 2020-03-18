---
title: özel korumalı - C# Referans
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: a73d61712075cf24d2b94c505104df1fade629e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713215"
---
# <a name="private-protected-c-reference"></a><span data-ttu-id="e357d-102">özel korumalı (C# Reference)</span><span class="sxs-lookup"><span data-stu-id="e357d-102">private protected (C# Reference)</span></span>

<span data-ttu-id="e357d-103">`private protected` Anahtar kelime birleşimi bir üye erişim değiştiricidir.</span><span class="sxs-lookup"><span data-stu-id="e357d-103">The `private protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="e357d-104">Özel korumalı bir üye, içerdiği sınıftan türetilen türlere, ancak yalnızca kendi içderlemesi içinde erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="e357d-104">A private protected member is accessible by types derived from the containing class, but only within its containing assembly.</span></span> <span data-ttu-id="e357d-105">Diğer erişim `private protected` değiştiriciler ile karşılaştırma için [Erişilebilirlik Düzeyleri'ne](accessibility-levels.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="e357d-105">For a comparison of `private protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

> [!NOTE]
> <span data-ttu-id="e357d-106">Erişim `private protected` değiştirici C# sürüm 7.2 ve sonraki sürümlerinde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e357d-106">The `private protected` access modifier is valid in C# version 7.2 and later.</span></span>

## <a name="example"></a><span data-ttu-id="e357d-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="e357d-107">Example</span></span>

<span data-ttu-id="e357d-108">Taban sınıfın özel korumalı üyesine, yalnızca değişkenin statik türü türetilmiş sınıf türüyse, içerdiği derlemedeki türetilmiş türlerden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="e357d-108">A private protected member of a base class is accessible from derived types in its containing assembly only if the static type of the variable is the derived class type.</span></span> <span data-ttu-id="e357d-109">Örneğin, aşağıdaki kod kesimini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="e357d-109">For example, consider the following code segment:</span></span>  

```csharp
// Assembly1.cs  
// Compile with: /target:library  
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

<span data-ttu-id="e357d-110">Bu örnekte iki `Assembly1.cs` `Assembly2.cs`dosya ve .</span><span class="sxs-lookup"><span data-stu-id="e357d-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="e357d-111">İlk dosya, ortak taban `BaseClass`sınıf ve ondan türetilen `DerivedClass1`bir tür içerir.</span><span class="sxs-lookup"><span data-stu-id="e357d-111">The first file contains a public base class, `BaseClass`, and a type derived from it, `DerivedClass1`.</span></span> <span data-ttu-id="e357d-112">`BaseClass`iki şekilde erişmeye `myValue`çalışan `DerivedClass1` özel bir korumalı üyesi ne sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e357d-112">`BaseClass` owns a private protected member, `myValue`, which `DerivedClass1` tries to access in two ways.</span></span> <span data-ttu-id="e357d-113">Bir örnek üzerinden `myValue` erişmek için `BaseClass` ilk girişimi bir hata üretecek.</span><span class="sxs-lookup"><span data-stu-id="e357d-113">The first attempt to access `myValue` through an instance of `BaseClass` will produce an error.</span></span> <span data-ttu-id="e357d-114">Ancak, kalıtsal bir üye olarak kullanma `DerivedClass1` girişimi başarılı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e357d-114">However, the attempt to use it as an inherited member in `DerivedClass1` will succeed.</span></span>
<span data-ttu-id="e357d-115">İkinci dosyada, devralınan `myValue` bir üye `DerivedClass2` olarak erişme girişimi, yalnızca Derleme1'de türetilen türler tarafından erişilebilir olduğundan bir hata üretir.</span><span class="sxs-lookup"><span data-stu-id="e357d-115">In the second file, an attempt to access `myValue` as an inherited member of `DerivedClass2` will produce an error, as it is only accessible by derived types in Assembly1.</span></span>

<span data-ttu-id="e357d-116">Yapı üyeleri, yapının devralınamayacağı için olamaz. `private protected`</span><span class="sxs-lookup"><span data-stu-id="e357d-116">Struct members cannot be `private protected` because the struct cannot be inherited.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="e357d-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="e357d-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a><span data-ttu-id="e357d-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e357d-118">See also</span></span>

- [<span data-ttu-id="e357d-119">C# Referans</span><span class="sxs-lookup"><span data-stu-id="e357d-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e357d-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e357d-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e357d-121">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="e357d-121">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="e357d-122">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="e357d-122">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="e357d-123">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="e357d-123">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="e357d-124">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="e357d-124">Modifiers</span></span>](index.md)
- [<span data-ttu-id="e357d-125">Kamu</span><span class="sxs-lookup"><span data-stu-id="e357d-125">public</span></span>](public.md)
- [<span data-ttu-id="e357d-126">Özel</span><span class="sxs-lookup"><span data-stu-id="e357d-126">private</span></span>](private.md)
- [<span data-ttu-id="e357d-127">Iç</span><span class="sxs-lookup"><span data-stu-id="e357d-127">internal</span></span>](internal.md)
- <span data-ttu-id="e357d-128">[Dahili sanal anahtar kelimeler için güvenlik endişeleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e357d-128">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
