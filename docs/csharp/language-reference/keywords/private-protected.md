---
title: özel korumalı C# başvuru
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: a73d61712075cf24d2b94c505104df1fade629e9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713215"
---
# <a name="private-protected-c-reference"></a><span data-ttu-id="51d27-102">özel korumalı (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="51d27-102">private protected (C# Reference)</span></span>

<span data-ttu-id="51d27-103">`private protected` anahtar sözcük birleşimi bir üye erişim değiştiricisidir.</span><span class="sxs-lookup"><span data-stu-id="51d27-103">The `private protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="51d27-104">Özel korumalı bir üyeye, kapsayan sınıftan türetilmiş türler tarafından erişilebilir, ancak yalnızca kendi kapsayıcı bütünleştirilmiş kodu içinde erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="51d27-104">A private protected member is accessible by types derived from the containing class, but only within its containing assembly.</span></span> <span data-ttu-id="51d27-105">Diğer erişim değiştiricilerine sahip `private protected` bir karşılaştırması için bkz. [Erişilebilirlik düzeyleri](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="51d27-105">For a comparison of `private protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

> [!NOTE]
> <span data-ttu-id="51d27-106">`private protected` erişim değiştiricisi C# sürüm 7,2 ve üzeri sürümlerde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="51d27-106">The `private protected` access modifier is valid in C# version 7.2 and later.</span></span>

## <a name="example"></a><span data-ttu-id="51d27-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="51d27-107">Example</span></span>

<span data-ttu-id="51d27-108">Bir temel sınıfın özel korumalı bir üyesine, yalnızca değişkenin statik türü türetilmiş sınıf türü ise, kendisini kapsayan derlemede bulunan türetilmiş türlerden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="51d27-108">A private protected member of a base class is accessible from derived types in its containing assembly only if the static type of the variable is the derived class type.</span></span> <span data-ttu-id="51d27-109">Örneğin, aşağıdaki kod kesimini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="51d27-109">For example, consider the following code segment:</span></span>  

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

<span data-ttu-id="51d27-110">Bu örnek, `Assembly1.cs` ve `Assembly2.cs`iki dosya içerir.</span><span class="sxs-lookup"><span data-stu-id="51d27-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="51d27-111">İlk dosya, bir ortak temel sınıf, `BaseClass`ve ondan türetilmiş bir tür içerir, `DerivedClass1`.</span><span class="sxs-lookup"><span data-stu-id="51d27-111">The first file contains a public base class, `BaseClass`, and a type derived from it, `DerivedClass1`.</span></span> <span data-ttu-id="51d27-112">`BaseClass`, `myValue``DerivedClass1` iki şekilde erişmeye çalıştığı özel korumalı bir üyeye sahip.</span><span class="sxs-lookup"><span data-stu-id="51d27-112">`BaseClass` owns a private protected member, `myValue`, which `DerivedClass1` tries to access in two ways.</span></span> <span data-ttu-id="51d27-113">Bir `BaseClass` örneği üzerinden `myValue` ilk kez erişme girişimi bir hata üretir.</span><span class="sxs-lookup"><span data-stu-id="51d27-113">The first attempt to access `myValue` through an instance of `BaseClass` will produce an error.</span></span> <span data-ttu-id="51d27-114">Ancak, bunu `DerivedClass1` devralınmış üye olarak kullanma girişimi başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="51d27-114">However, the attempt to use it as an inherited member in `DerivedClass1` will succeed.</span></span>
<span data-ttu-id="51d27-115">İkinci dosyada, `DerivedClass2` devralınmış bir `myValue` erişme girişimi yalnızca Assembly1 içindeki türetilmiş türler tarafından erişilebilir olduğundan bir hata üretir.</span><span class="sxs-lookup"><span data-stu-id="51d27-115">In the second file, an attempt to access `myValue` as an inherited member of `DerivedClass2` will produce an error, as it is only accessible by derived types in Assembly1.</span></span>

<span data-ttu-id="51d27-116">Struct devralınamadığı için yapı üyeleri `private protected` olamaz.</span><span class="sxs-lookup"><span data-stu-id="51d27-116">Struct members cannot be `private protected` because the struct cannot be inherited.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="51d27-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="51d27-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a><span data-ttu-id="51d27-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51d27-118">See also</span></span>

- [<span data-ttu-id="51d27-119">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="51d27-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="51d27-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="51d27-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="51d27-121">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="51d27-121">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="51d27-122">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="51d27-122">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="51d27-123">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="51d27-123">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="51d27-124">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="51d27-124">Modifiers</span></span>](index.md)
- [<span data-ttu-id="51d27-125">public</span><span class="sxs-lookup"><span data-stu-id="51d27-125">public</span></span>](public.md)
- [<span data-ttu-id="51d27-126">private</span><span class="sxs-lookup"><span data-stu-id="51d27-126">private</span></span>](private.md)
- [<span data-ttu-id="51d27-127">internal</span><span class="sxs-lookup"><span data-stu-id="51d27-127">internal</span></span>](internal.md)
- <span data-ttu-id="51d27-128">[İç sanal anahtar sözcüklere yönelik güvenlik sorunları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="51d27-128">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
