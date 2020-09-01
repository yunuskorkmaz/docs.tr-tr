---
description: using yönergesi-C# başvurusu
title: using yönergesi-C# başvurusu
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: f22a67348b19b8c97513ca685b2b10b34b1fd6fd
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141952"
---
# <a name="using-directive-c-reference"></a><span data-ttu-id="16729-103">using yönergesi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="16729-103">using directive (C# Reference)</span></span>

<span data-ttu-id="16729-104">`using`Yönergesinin üç kullanımı vardır:</span><span class="sxs-lookup"><span data-stu-id="16729-104">The `using` directive has three uses:</span></span>

- <span data-ttu-id="16729-105">Bir ad alanında türlerin kullanılmasına izin vermek için, bu ad alanında bir tür kullanımını nitelendirmeniz gerekmez:</span><span class="sxs-lookup"><span data-stu-id="16729-105">To allow the use of types in a namespace so that you do not have to qualify the use of a type in that namespace:</span></span>

    ```csharp
    using System.Text;
    ```

- <span data-ttu-id="16729-106">Tür adıyla erişimi nitelemek zorunda kalmadan statik üyelere ve bir tür iç içe türlerine erişmenize izin vermek için.</span><span class="sxs-lookup"><span data-stu-id="16729-106">To allow you to access static members and nested types of a type without having to qualify the access with the type name.</span></span>

    ```csharp
    using static System.Math;
    ```

    <span data-ttu-id="16729-107">Daha fazla bilgi için bkz. [using static yönergesi](using-static.md).</span><span class="sxs-lookup"><span data-stu-id="16729-107">For more information, see the [using static directive](using-static.md).</span></span>

- <span data-ttu-id="16729-108">Bir ad alanı veya tür için bir diğer ad oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="16729-108">To create an alias for a namespace or a type.</span></span> <span data-ttu-id="16729-109">Bu, *Using alias yönergesi*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="16729-109">This is called a *using alias directive*.</span></span>

    ```csharp
    using Project = PC.MyCompany.Project;
    ```

<span data-ttu-id="16729-110">`using`Anahtar sözcüğü Ayrıca, dosyalar ve yazı tipleri gibi nesnelerin doğru şekilde işlenmesini sağlamaya yardımcı olan *using deyimleri*oluşturmak için de kullanılır <xref:System.IDisposable> .</span><span class="sxs-lookup"><span data-stu-id="16729-110">The `using` keyword is also used to create *using statements*, which help ensure that <xref:System.IDisposable> objects such as files and fonts are handled correctly.</span></span> <span data-ttu-id="16729-111">Daha fazla bilgi için bkz. [using deyimleri](using-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="16729-111">See [using Statement](using-statement.md) for more information.</span></span>

## <a name="using-static-type"></a><span data-ttu-id="16729-112">Statik tür kullanma</span><span class="sxs-lookup"><span data-stu-id="16729-112">Using static type</span></span>

<span data-ttu-id="16729-113">Tür adıyla erişimi nitelemek zorunda kalmadan, bir türün statik üyelerine erişebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="16729-113">You can access static members of a type without having to qualify the access with the type name:</span></span>

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

## <a name="remarks"></a><span data-ttu-id="16729-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16729-114">Remarks</span></span>

<span data-ttu-id="16729-115">Bir `using` yönergenin kapsamı göründüğü dosyayla sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="16729-115">The scope of a `using` directive is limited to the file in which it appears.</span></span>

<span data-ttu-id="16729-116">`using`Yönerge şu şekilde görünebilir:</span><span class="sxs-lookup"><span data-stu-id="16729-116">The `using` directive can appear:</span></span>

- <span data-ttu-id="16729-117">Bir kaynak kodu dosyasının başlangıcında, herhangi bir ad alanı veya tür tanımlarından önce.</span><span class="sxs-lookup"><span data-stu-id="16729-117">At the beginning of a source code file, before any namespace or type definitions.</span></span>
- <span data-ttu-id="16729-118">Herhangi bir ad alanında, bu ad alanında bildirilmeyen herhangi bir ad alanı veya türden önce.</span><span class="sxs-lookup"><span data-stu-id="16729-118">In any namespace, but before any namespace or types declared in this namespace.</span></span>

<span data-ttu-id="16729-119">Aksi halde, derleyici hatası [CS1529](../../misc/cs1529.md) oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="16729-119">Otherwise, compiler error [CS1529](../../misc/cs1529.md) is generated.</span></span>

<span data-ttu-id="16729-120">Bir `using` tanımlayıcıyı bir ad alanına veya türe göre bulmayı kolaylaştırmak için bir diğer ad yönergesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="16729-120">Create a `using` alias directive to make it easier to qualify an identifier to a namespace or type.</span></span> <span data-ttu-id="16729-121">Herhangi bir `using` yönergede, daha `using` önce gelen yönergelerden bağımsız olarak tam nitelikli ad alanı veya tür kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="16729-121">In any `using` directive, the fully-qualified namespace or type must be used regardless of the `using` directives that come before it.</span></span> <span data-ttu-id="16729-122">`using`Bir yönergenin bildiriminde diğer ad kullanılamaz `using` .</span><span class="sxs-lookup"><span data-stu-id="16729-122">No `using` alias can be used in the declaration of a `using` directive.</span></span> <span data-ttu-id="16729-123">Örneğin, aşağıdakiler bir derleyici hatası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="16729-123">For example, the following generates a compiler error:</span></span>

```csharp
using s = System.Text;
using s.RegularExpressions; // Generates a compiler error.
```

<span data-ttu-id="16729-124">Ad `using` alanını belirtmek zorunda kalmadan bir ad alanındaki türleri kullanmak için bir yönerge oluşturun.</span><span class="sxs-lookup"><span data-stu-id="16729-124">Create a `using` directive to use the types in a namespace without having to specify the namespace.</span></span> <span data-ttu-id="16729-125">Bir `using` yönerge, belirttiğiniz ad alanında iç içe yerleştirilmiş herhangi bir ad alanı için erişim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="16729-125">A `using` directive does not give you access to any namespaces that are nested in the namespace you specify.</span></span>

<span data-ttu-id="16729-126">Ad alanları iki kategoride gelir: Kullanıcı tanımlı ve sistem tanımlı.</span><span class="sxs-lookup"><span data-stu-id="16729-126">Namespaces come in two categories: user-defined and system-defined.</span></span> <span data-ttu-id="16729-127">Kullanıcı tanımlı ad alanları kodunuzda tanımlı ad uzaylardır.</span><span class="sxs-lookup"><span data-stu-id="16729-127">User-defined namespaces are namespaces defined in your code.</span></span> <span data-ttu-id="16729-128">Sistem tanımlı ad alanlarının listesi için bkz. [.NET API Browser](../../../../api/index.md).</span><span class="sxs-lookup"><span data-stu-id="16729-128">For a list of the system-defined namespaces, see [.NET API Browser](../../../../api/index.md).</span></span>

## <a name="example-1"></a><span data-ttu-id="16729-129">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="16729-129">Example 1</span></span>

<span data-ttu-id="16729-130">Aşağıdaki örnek, `using` bir ad alanı için bir diğer ad tanımlama ve kullanmayı gösterir:</span><span class="sxs-lookup"><span data-stu-id="16729-130">The following example shows how to define and use a `using` alias for a namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#8)]

<span data-ttu-id="16729-131">Using takma ad yönergesinin sağ tarafta açık genel bir türü olamaz.</span><span class="sxs-lookup"><span data-stu-id="16729-131">A using alias directive cannot have an open generic type on the right hand side.</span></span> <span data-ttu-id="16729-132">Örneğin, için bir using diğer adı oluşturamazsınız `List<T>` , ancak bir için bir tane oluşturabilirsiniz `List<int>` .</span><span class="sxs-lookup"><span data-stu-id="16729-132">For example, you cannot create a using alias for a `List<T>`, but you can create one for a `List<int>`.</span></span>

## <a name="example-2"></a><span data-ttu-id="16729-133">Örnek 2</span><span class="sxs-lookup"><span data-stu-id="16729-133">Example 2</span></span>

<span data-ttu-id="16729-134">Aşağıdaki örnek bir `using` sınıfın bir yönergesinin ve diğer adının nasıl tanımlanacağını göstermektedir `using` :</span><span class="sxs-lookup"><span data-stu-id="16729-134">The following example shows how to define a `using` directive and a `using` alias for a class:</span></span>

[!code-csharp[csrefKeywordsNamespace#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="16729-135">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="16729-135">C# language specification</span></span>

<span data-ttu-id="16729-136">Daha fazla bilgi için bkz. [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [yönergeleri kullanma](~/_csharplang/spec/namespaces.md#using-directives) .</span><span class="sxs-lookup"><span data-stu-id="16729-136">For more information, see [Using directives](~/_csharplang/spec/namespaces.md#using-directives) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="16729-137">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="16729-137">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="16729-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16729-138">See also</span></span>

- [<span data-ttu-id="16729-139">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="16729-139">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="16729-140">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="16729-140">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="16729-141">Ad alanlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="16729-141">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
- [<span data-ttu-id="16729-142">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="16729-142">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="16729-143">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="16729-143">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
- [<span data-ttu-id="16729-144">using Deyimi</span><span class="sxs-lookup"><span data-stu-id="16729-144">using Statement</span></span>](using-statement.md)
