---
title: using yönergesi- C# başvuru
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: d6e3667861c2b1ac9a84ca7b4e2cabb5784d793d
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970051"
---
# <a name="using-directive-c-reference"></a><span data-ttu-id="6f1fb-102">using yönergesi (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="6f1fb-102">using directive (C# Reference)</span></span>

<span data-ttu-id="6f1fb-103">`using` Yönergesinin üç kullanımı vardır:</span><span class="sxs-lookup"><span data-stu-id="6f1fb-103">The `using` directive has three uses:</span></span>

- <span data-ttu-id="6f1fb-104">Bir ad alanında türlerin kullanılmasına izin vermek için, bu ad alanında bir tür kullanımını nitelendirmeniz gerekmez:</span><span class="sxs-lookup"><span data-stu-id="6f1fb-104">To allow the use of types in a namespace so that you do not have to qualify the use of a type in that namespace:</span></span>

    ```csharp
    using System.Text;
    ```

- <span data-ttu-id="6f1fb-105">Tür adıyla erişimi nitelemek zorunda kalmadan statik üyelere ve bir tür iç içe türlerine erişmenize izin vermek için.</span><span class="sxs-lookup"><span data-stu-id="6f1fb-105">To allow you to access static members and nested types of a type without having to qualify the access with the type name.</span></span>

    ```csharp
    using static System.Math;
    ```

    <span data-ttu-id="6f1fb-106">Daha fazla bilgi için bkz. [using static yönergesi](using-static.md).</span><span class="sxs-lookup"><span data-stu-id="6f1fb-106">For more information, see the [using static directive](using-static.md).</span></span>

- <span data-ttu-id="6f1fb-107">Bir ad alanı veya tür için bir diğer ad oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="6f1fb-107">To create an alias for a namespace or a type.</span></span> <span data-ttu-id="6f1fb-108">Bu, *Using alias yönergesi*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="6f1fb-108">This is called a *using alias directive*.</span></span>

    ```csharp
    using Project = PC.MyCompany.Project;
    ```

<span data-ttu-id="6f1fb-109">Anahtar sözcüğü Ayrıca, dosyalar ve yazı tipleri gibi <xref:System.IDisposable> nesnelerin doğru şekilde işlenmesini sağlamaya yardımcı olan *using deyimleri*oluşturmak için de kullanılır. `using`</span><span class="sxs-lookup"><span data-stu-id="6f1fb-109">The `using` keyword is also used to create *using statements*, which help ensure that <xref:System.IDisposable> objects such as files and fonts are handled correctly.</span></span> <span data-ttu-id="6f1fb-110">Daha fazla bilgi için bkz. [using deyimleri](using-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="6f1fb-110">See [using Statement](using-statement.md) for more information.</span></span>

## <a name="using-static-type"></a><span data-ttu-id="6f1fb-111">Statik tür kullanma</span><span class="sxs-lookup"><span data-stu-id="6f1fb-111">Using static type</span></span>

<span data-ttu-id="6f1fb-112">Tür adıyla erişimi nitelemek zorunda kalmadan, bir türün statik üyelerine erişebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6f1fb-112">You can access static members of a type without having to qualify the access with the type name:</span></span>

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

## <a name="remarks"></a><span data-ttu-id="6f1fb-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6f1fb-113">Remarks</span></span>

<span data-ttu-id="6f1fb-114">Bir `using` yönergenin kapsamı göründüğü dosyayla sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="6f1fb-114">The scope of a `using` directive is limited to the file in which it appears.</span></span>

<span data-ttu-id="6f1fb-115">`using` Yönerge şu şekilde görünebilir:</span><span class="sxs-lookup"><span data-stu-id="6f1fb-115">The `using` directive can appear:</span></span>

- <span data-ttu-id="6f1fb-116">Bir kaynak kodu dosyasının başlangıcında, herhangi bir ad alanı veya tür tanımlarından önce.</span><span class="sxs-lookup"><span data-stu-id="6f1fb-116">At the beginning of a source code file, before any namespace or type definitions.</span></span>
- <span data-ttu-id="6f1fb-117">Herhangi bir ad alanında, bu ad alanında bildirilmeyen herhangi bir ad alanı veya türden önce.</span><span class="sxs-lookup"><span data-stu-id="6f1fb-117">In any namespace, but before any namespace or types declared in this namespace.</span></span>

<span data-ttu-id="6f1fb-118">Aksi halde, derleyici hatası [CS1529](../../misc/cs1529.md) oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6f1fb-118">Otherwise, compiler error [CS1529](../../misc/cs1529.md) is generated.</span></span>

<span data-ttu-id="6f1fb-119">Bir tanımlayıcıyı `using` bir ad alanına veya türe göre bulmayı kolaylaştırmak için bir diğer ad yönergesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6f1fb-119">Create a `using` alias directive to make it easier to qualify an identifier to a namespace or type.</span></span> <span data-ttu-id="6f1fb-120">Herhangi bir `using` yönergede, daha önce gelen `using` yönergelerden bağımsız olarak tam nitelikli ad alanı veya tür kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6f1fb-120">In any `using` directive, the fully-qualified namespace or type must be used regardless of the `using` directives that come before it.</span></span> <span data-ttu-id="6f1fb-121">`using` Bir`using` yönergenin bildiriminde diğer ad kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6f1fb-121">No `using` alias can be used in the declaration of a `using` directive.</span></span> <span data-ttu-id="6f1fb-122">Örneğin, aşağıdakiler bir derleyici hatası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="6f1fb-122">For example, the following generates a compiler error:</span></span>

```csharp
using s = System.Text;
using s.RegularExpressions;
```

<span data-ttu-id="6f1fb-123">Ad alanını `using` belirtmek zorunda kalmadan bir ad alanındaki türleri kullanmak için bir yönerge oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6f1fb-123">Create a `using` directive to use the types in a namespace without having to specify the namespace.</span></span> <span data-ttu-id="6f1fb-124">Bir `using` yönerge, belirttiğiniz ad alanında iç içe yerleştirilmiş herhangi bir ad alanı için erişim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="6f1fb-124">A `using` directive does not give you access to any namespaces that are nested in the namespace you specify.</span></span>

<span data-ttu-id="6f1fb-125">Ad alanları iki kategoride gelir: Kullanıcı tanımlı ve sistem tanımlı.</span><span class="sxs-lookup"><span data-stu-id="6f1fb-125">Namespaces come in two categories: user-defined and system-defined.</span></span> <span data-ttu-id="6f1fb-126">Kullanıcı tanımlı ad alanları kodunuzda tanımlı ad uzaylardır.</span><span class="sxs-lookup"><span data-stu-id="6f1fb-126">User-defined namespaces are namespaces defined in your code.</span></span> <span data-ttu-id="6f1fb-127">Sistem tanımlı ad alanlarının listesi için bkz. [.NET API Browser](../../../../api/index.md).</span><span class="sxs-lookup"><span data-stu-id="6f1fb-127">For a list of the system-defined namespaces, see [.NET API Browser](../../../../api/index.md).</span></span>

## <a name="example-1"></a><span data-ttu-id="6f1fb-128">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="6f1fb-128">Example 1</span></span>

<span data-ttu-id="6f1fb-129">Aşağıdaki örnek, bir ad alanı için bir `using` diğer ad tanımlama ve kullanmayı gösterir:</span><span class="sxs-lookup"><span data-stu-id="6f1fb-129">The following example shows how to define and use a `using` alias for a namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#8)]

<span data-ttu-id="6f1fb-130">Using takma ad yönergesinin sağ tarafta açık genel bir türü olamaz.</span><span class="sxs-lookup"><span data-stu-id="6f1fb-130">A using alias directive cannot have an open generic type on the right hand side.</span></span> <span data-ttu-id="6f1fb-131">Örneğin, için `List<T>`bir using diğer adı oluşturamazsınız, ancak bir `List<int>`için bir tane oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f1fb-131">For example, you cannot create a using alias for a `List<T>`, but you can create one for a `List<int>`.</span></span>

## <a name="example-2"></a><span data-ttu-id="6f1fb-132">Örnek 2</span><span class="sxs-lookup"><span data-stu-id="6f1fb-132">Example 2</span></span>

<span data-ttu-id="6f1fb-133">Aşağıdaki örnek bir sınıfın bir `using` yönergesinin `using` ve diğer adının nasıl tanımlanacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="6f1fb-133">The following example shows how to define a `using` directive and a `using` alias for a class:</span></span>

[!code-csharp[csrefKeywordsNamespace#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="6f1fb-134">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="6f1fb-134">C# language specification</span></span>

<span data-ttu-id="6f1fb-135">Daha fazla bilgi için bkz. [ C# dil belirtiminde](../language-specification/index.md) [yönergeleri kullanma](~/_csharplang/spec/namespaces.md#using-directives) .</span><span class="sxs-lookup"><span data-stu-id="6f1fb-135">For more information, see [Using directives](~/_csharplang/spec/namespaces.md#using-directives) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="6f1fb-136">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="6f1fb-136">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="6f1fb-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f1fb-137">See also</span></span>

- [<span data-ttu-id="6f1fb-138">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="6f1fb-138">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6f1fb-139">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6f1fb-139">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6f1fb-140">Ad Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="6f1fb-140">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
- [<span data-ttu-id="6f1fb-141">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="6f1fb-141">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="6f1fb-142">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="6f1fb-142">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
- [<span data-ttu-id="6f1fb-143">using Deyimi</span><span class="sxs-lookup"><span data-stu-id="6f1fb-143">using Statement</span></span>](using-statement.md)
