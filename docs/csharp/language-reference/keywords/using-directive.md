---
title: yönergeyi kullanarak - C# Referans
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: 4f7ddad8c3dc12391ef6bf345a73ebb384400b38
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093155"
---
# <a name="using-directive-c-reference"></a><span data-ttu-id="f5646-102">yönergeyi kullanma (C# Reference)</span><span class="sxs-lookup"><span data-stu-id="f5646-102">using directive (C# Reference)</span></span>

<span data-ttu-id="f5646-103">`using` Yönergeüç kullanıma sahiptir:</span><span class="sxs-lookup"><span data-stu-id="f5646-103">The `using` directive has three uses:</span></span>

- <span data-ttu-id="f5646-104">Bu ad alanında bir tür kullanımını hak kazanmak zorunda kalmamak için bir ad alanında türlerin kullanımına izin vermek için:</span><span class="sxs-lookup"><span data-stu-id="f5646-104">To allow the use of types in a namespace so that you do not have to qualify the use of a type in that namespace:</span></span>

    ```csharp
    using System.Text;
    ```

- <span data-ttu-id="f5646-105">Erişimi tür adıyla nitelemek zorunda kalmadan statik üyelere ve iç içe geçmiş türtürlerine erişmenize izin vermek için.</span><span class="sxs-lookup"><span data-stu-id="f5646-105">To allow you to access static members and nested types of a type without having to qualify the access with the type name.</span></span>

    ```csharp
    using static System.Math;
    ```

    <span data-ttu-id="f5646-106">Daha fazla bilgi için statik [yönergeleri kullanarak](using-static.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="f5646-106">For more information, see the [using static directive](using-static.md).</span></span>

- <span data-ttu-id="f5646-107">Ad alanı veya tür için takma ad oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="f5646-107">To create an alias for a namespace or a type.</span></span> <span data-ttu-id="f5646-108">Buna kullanma *diğer adı yönergesi*denir.</span><span class="sxs-lookup"><span data-stu-id="f5646-108">This is called a *using alias directive*.</span></span>

    ```csharp
    using Project = PC.MyCompany.Project;
    ```

<span data-ttu-id="f5646-109">Anahtar kelime, dosya ve yazı tipleri gibi <xref:System.IDisposable> nesnelerin doğru şekilde işlenmesini sağlamaya yardımcı olan ifadeleri kullanarak oluşturmak için de kullanılır. *using statements* `using`</span><span class="sxs-lookup"><span data-stu-id="f5646-109">The `using` keyword is also used to create *using statements*, which help ensure that <xref:System.IDisposable> objects such as files and fonts are handled correctly.</span></span> <span data-ttu-id="f5646-110">Daha fazla bilgi için [Bildirim'i kullanma](using-statement.md) bilgisine bakın.</span><span class="sxs-lookup"><span data-stu-id="f5646-110">See [using Statement](using-statement.md) for more information.</span></span>

## <a name="using-static-type"></a><span data-ttu-id="f5646-111">Statik türü kullanma</span><span class="sxs-lookup"><span data-stu-id="f5646-111">Using static type</span></span>

<span data-ttu-id="f5646-112">Erişimi tür adıyla nitelemek zorunda kalmadan bir türün statik üyelerine erişebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f5646-112">You can access static members of a type without having to qualify the access with the type name:</span></span>

```csharp
using static System.Console;
using static System.Math;
class Program
{
    static void Main()
    {
        WriteLine(Sqrt(3*3 + 4*4));
    }
}
```

## <a name="remarks"></a><span data-ttu-id="f5646-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f5646-113">Remarks</span></span>

<span data-ttu-id="f5646-114">Bir `using` yönergenin kapsamı, görüntülendiği dosyayla sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="f5646-114">The scope of a `using` directive is limited to the file in which it appears.</span></span>

<span data-ttu-id="f5646-115">Yönerge `using` şu şekilde görünebilir:</span><span class="sxs-lookup"><span data-stu-id="f5646-115">The `using` directive can appear:</span></span>

- <span data-ttu-id="f5646-116">Kaynak kodu dosyasının başında, herhangi bir ad alanı veya tür tanımlarından önce.</span><span class="sxs-lookup"><span data-stu-id="f5646-116">At the beginning of a source code file, before any namespace or type definitions.</span></span>
- <span data-ttu-id="f5646-117">Herhangi bir ad alanında, ancak bu ad alanında bildirilen herhangi bir ad alanı veya türleri önce.</span><span class="sxs-lookup"><span data-stu-id="f5646-117">In any namespace, but before any namespace or types declared in this namespace.</span></span>

<span data-ttu-id="f5646-118">Aksi takdirde, derleyici hatası [CS1529](../../misc/cs1529.md) oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f5646-118">Otherwise, compiler error [CS1529](../../misc/cs1529.md) is generated.</span></span>

<span data-ttu-id="f5646-119">Bir `using` tanımlayıcıyı bir ad alanı veya türe hak kazanmak için bir takma ad yönergesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f5646-119">Create a `using` alias directive to make it easier to qualify an identifier to a namespace or type.</span></span> <span data-ttu-id="f5646-120">Herhangi `using` bir yönergede, tam nitelikli ad alanı veya `using` türü, ondan önce gelen yönergelerden bağımsız olarak kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f5646-120">In any `using` directive, the fully-qualified namespace or type must be used regardless of the `using` directives that come before it.</span></span> <span data-ttu-id="f5646-121">Bir yönerge bildiriminde başka `using` bir ad kullanılamaz. `using`</span><span class="sxs-lookup"><span data-stu-id="f5646-121">No `using` alias can be used in the declaration of a `using` directive.</span></span> <span data-ttu-id="f5646-122">Örneğin, aşağıdaki derleyici hatası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="f5646-122">For example, the following generates a compiler error:</span></span>

```csharp
using s = System.Text;
using s.RegularExpressions; // Generates a compiler error.
```

<span data-ttu-id="f5646-123">Ad `using` alanını belirtmek zorunda kalmadan, türleri ad alanında kullanmak için bir yönerge oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f5646-123">Create a `using` directive to use the types in a namespace without having to specify the namespace.</span></span> <span data-ttu-id="f5646-124">Yönerge, `using` belirttiğiniz ad alanında iç içe olan ad alanlarına erişmenizi sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="f5646-124">A `using` directive does not give you access to any namespaces that are nested in the namespace you specify.</span></span>

<span data-ttu-id="f5646-125">Ad alanları iki kategoride gelir: kullanıcı tanımlı ve sistem tanımlı.</span><span class="sxs-lookup"><span data-stu-id="f5646-125">Namespaces come in two categories: user-defined and system-defined.</span></span> <span data-ttu-id="f5646-126">Kullanıcı tanımlı ad alanları, kodunuzda tanımlanan ad alanlarıdır.</span><span class="sxs-lookup"><span data-stu-id="f5646-126">User-defined namespaces are namespaces defined in your code.</span></span> <span data-ttu-id="f5646-127">Sistem tanımlı ad alanlarının listesi [için](../../../../api/index.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="f5646-127">For a list of the system-defined namespaces, see [.NET API Browser](../../../../api/index.md).</span></span>

## <a name="example-1"></a><span data-ttu-id="f5646-128">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="f5646-128">Example 1</span></span>

<span data-ttu-id="f5646-129">Aşağıdaki örnek, ad alanı için `using` takma adınasıl tanımlanırken kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="f5646-129">The following example shows how to define and use a `using` alias for a namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#8)]

<span data-ttu-id="f5646-130">Bir diğer ad yönergesi sağ tarafta açık bir genel türü olamaz.</span><span class="sxs-lookup"><span data-stu-id="f5646-130">A using alias directive cannot have an open generic type on the right hand side.</span></span> <span data-ttu-id="f5646-131">Örneğin, bir `List<T>`, bir için bir ' için bir `List<int>`', bir ' için bir ' için bir ' sözcük oluşturamazsınız.</span><span class="sxs-lookup"><span data-stu-id="f5646-131">For example, you cannot create a using alias for a `List<T>`, but you can create one for a `List<int>`.</span></span>

## <a name="example-2"></a><span data-ttu-id="f5646-132">Örnek 2</span><span class="sxs-lookup"><span data-stu-id="f5646-132">Example 2</span></span>

<span data-ttu-id="f5646-133">Aşağıdaki örnek, bir sınıf `using` için `using` bir yönerge ve diğer adnasıl tanımlanabildiğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="f5646-133">The following example shows how to define a `using` directive and a `using` alias for a class:</span></span>

[!code-csharp[csrefKeywordsNamespace#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="f5646-134">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="f5646-134">C# language specification</span></span>

<span data-ttu-id="f5646-135">Daha fazla bilgi için Bkz. [C# Dil Belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [yönergeleri kullanma.](~/_csharplang/spec/namespaces.md#using-directives)</span><span class="sxs-lookup"><span data-stu-id="f5646-135">For more information, see [Using directives](~/_csharplang/spec/namespaces.md#using-directives) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="f5646-136">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="f5646-136">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="f5646-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5646-137">See also</span></span>

- [<span data-ttu-id="f5646-138">C# Referans</span><span class="sxs-lookup"><span data-stu-id="f5646-138">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f5646-139">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f5646-139">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f5646-140">Ad Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="f5646-140">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
- [<span data-ttu-id="f5646-141">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="f5646-141">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f5646-142">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="f5646-142">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
- [<span data-ttu-id="f5646-143">Ekstresi'ni kullanma</span><span class="sxs-lookup"><span data-stu-id="f5646-143">using Statement</span></span>](using-statement.md)
