---
title: Erişim Denetimi (F#)
description: 'Türleri, yöntemleri ve İşlevler, F # programlama dili gibi programlama öğeleri erişimi denetlemek öğrenin.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: fee5f719904b61c3082d56f73448defdea39f472
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="access-control"></a><span data-ttu-id="9e300-103">Erişim Denetimi</span><span class="sxs-lookup"><span data-stu-id="9e300-103">Access Control</span></span>

<span data-ttu-id="9e300-104">*Erişim denetimi* hangi istemcilerin türleri, yöntemleri ve işlevleri gibi bazı program öğeleri kullanabilirsiniz bildirmek için başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="9e300-104">*Access control* refers to declaring which clients can use certain program elements, such as types, methods, and functions.</span></span>


## <a name="basics-of-access-control"></a><span data-ttu-id="9e300-105">Erişim denetimi ile ilgili temel bilgiler</span><span class="sxs-lookup"><span data-stu-id="9e300-105">Basics of Access Control</span></span>
<span data-ttu-id="9e300-106">F #'ta erişimi denetleyen tanımlayıcıları `public`, `internal`, ve `private` modülleri, türleri, yöntemleri, değer tanımları, İşlevler, özellikleri ve açık alanlar için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="9e300-106">In F#, the access control specifiers `public`, `internal`, and `private` can be applied to modules, types, methods, value definitions, functions, properties, and explicit fields.</span></span>


- <span data-ttu-id="9e300-107">`public` Varlık tüm arayanlar tarafından erişilebilir gösterir.</span><span class="sxs-lookup"><span data-stu-id="9e300-107">`public` indicates that the entity can be accessed by all callers.</span></span>

- <span data-ttu-id="9e300-108">`internal` varlık yalnızca aynı derlemesinden erişilebilir gösterir.</span><span class="sxs-lookup"><span data-stu-id="9e300-108">`internal` indicates that the entity can be accessed only from the same assembly.</span></span>

- <span data-ttu-id="9e300-109">`private` varlık yalnızca kapsayan türü veya modülünden erişilebilir gösterir.</span><span class="sxs-lookup"><span data-stu-id="9e300-109">`private` indicates that the entity can be accessed only from the enclosing type or module.</span></span>


>[!NOTE] 
<span data-ttu-id="9e300-110">Erişim belirteci `protected` destek dillerde yazılmış türleri kullanıyorsanız, kabul edilebilir olmasına rağmen F #'ta kullanılmaz `protected` erişim.</span><span class="sxs-lookup"><span data-stu-id="9e300-110">The access specifier `protected` is not used in F#, although it is acceptable if you are using types authored in languages that do support `protected` access.</span></span> <span data-ttu-id="9e300-111">Bu nedenle, bir korumalı yöntemi geçersiz kılarsanız yönteminizi yalnızca sınıfı ve alt öğelerinden içinde erişilebilir kalır.</span><span class="sxs-lookup"><span data-stu-id="9e300-111">Therefore, if you override a protected method, your method remains accessible only within the class and its descendents.</span></span>

<span data-ttu-id="9e300-112">Genel olarak, ne zaman dışında varlık adı önünde belirleyici put bir `mutable` veya `inline` belirticisi kullanılır, erişim denetimi belirticisi sonra görünen.</span><span class="sxs-lookup"><span data-stu-id="9e300-112">In general, the specifier is put in front of the name of the entity, except when a `mutable` or `inline` specifier is used, which appear after the access control specifier.</span></span>

<span data-ttu-id="9e300-113">Hiçbir erişim belirticisi kullanılırsa, varsayılan değer `public`, dışında `let` bir türdeki her zaman bağlamaları `private` türü.</span><span class="sxs-lookup"><span data-stu-id="9e300-113">If no access specifier is used, the default is `public`, except for `let` bindings in a type, which are always `private` to the type.</span></span>

<span data-ttu-id="9e300-114">İmzaları F #, F # programı öğelere erişimi denetlemek için başka bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e300-114">Signatures in F# provide another mechanism for controlling access to F# program elements.</span></span> <span data-ttu-id="9e300-115">İmzalar için erişim denetimi gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="9e300-115">Signatures are not required for access control.</span></span> <span data-ttu-id="9e300-116">Daha fazla bilgi için bkz: [imzalar](signatures.md).</span><span class="sxs-lookup"><span data-stu-id="9e300-116">For more information, see [Signatures](signatures.md).</span></span>


## <a name="rules-for-access-control"></a><span data-ttu-id="9e300-117">Erişim denetimi için kuralları</span><span class="sxs-lookup"><span data-stu-id="9e300-117">Rules for Access Control</span></span>
<span data-ttu-id="9e300-118">Erişim denetimi aşağıdaki kuralları tabi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="9e300-118">Access control is subject to the following rules:</span></span>


- <span data-ttu-id="9e300-119">Devralma bildirimleri (diğer bir deyişle, kullanımını `inherit` bir sınıf için temel sınıf belirtmek için), arabirim (bir sınıf bir arabirimini uygulayan belirterek olan) bildirimleri ve soyut üyeleri her zaman kendilerini kapsayan türle aynı erişilebilirlik sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9e300-119">Inheritance declarations (that is, the use of `inherit` to specify a base class for a class), interface declarations (that is, specifying that a class implements an interface), and abstract members always have the same accessibility as the enclosing type.</span></span> <span data-ttu-id="9e300-120">Bu nedenle, bir erişim denetimi belirticisi bu yapıları üzerinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9e300-120">Therefore, an access control specifier cannot be used on these constructs.</span></span>

- <span data-ttu-id="9e300-121">Ayrılmış birleşim tek tek durumlarda birleşim türü ayrı kendi erişim denetimi değiştiricileri sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="9e300-121">Individual cases in a discriminated union cannot have their own access control modifiers separate from the union type.</span></span>

- <span data-ttu-id="9e300-122">Bir kayıt türü tek tek alanların kayıt türünden ayrı kendi erişim denetimi değiştiricileri sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="9e300-122">Individual fields of a record type cannot have their own access control modifiers separate from the record type.</span></span>


## <a name="example"></a><span data-ttu-id="9e300-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="9e300-123">Example</span></span>
<span data-ttu-id="9e300-124">Aşağıdaki kod, erişim denetimi belirticileri kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9e300-124">The following code illustrates the use of access control specifiers.</span></span> <span data-ttu-id="9e300-125">Projede iki dosya vardır `Module1.fs` ve `Module2.fs`.</span><span class="sxs-lookup"><span data-stu-id="9e300-125">There are two files in the project, `Module1.fs` and `Module2.fs`.</span></span> <span data-ttu-id="9e300-126">Her dosya örtük olarak bir modüldür.</span><span class="sxs-lookup"><span data-stu-id="9e300-126">Each file is implicitly a module.</span></span> <span data-ttu-id="9e300-127">Bu nedenle, iki modülleri vardır `Module1` ve `Module2`.</span><span class="sxs-lookup"><span data-stu-id="9e300-127">Therefore, there are two modules, `Module1` and `Module2`.</span></span> <span data-ttu-id="9e300-128">Özel bir türü ve iç tür tanımlanan `Module1`.</span><span class="sxs-lookup"><span data-stu-id="9e300-128">A private type and an internal type are defined in `Module1`.</span></span> <span data-ttu-id="9e300-129">Özel tür erişim sağlanamaz `Module2`, ancak iç türü.</span><span class="sxs-lookup"><span data-stu-id="9e300-129">The private type cannot be accessed from `Module2`, but the internal type can.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet1.fs)]
    
<span data-ttu-id="9e300-130">Aşağıdaki kod içinde oluşturulan türleri erişilebilirliğini testleri `Module1.fs`.</span><span class="sxs-lookup"><span data-stu-id="9e300-130">The following code tests the accessibility of the types created in `Module1.fs`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet2.fs)]
    
## <a name="see-also"></a><span data-ttu-id="9e300-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9e300-131">See Also</span></span>
[<span data-ttu-id="9e300-132">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="9e300-132">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="9e300-133">İmzalar</span><span class="sxs-lookup"><span data-stu-id="9e300-133">Signatures</span></span>](signatures.md)
