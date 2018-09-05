---
title: Erişim Denetimi (F#)
description: 'Türlerin, yöntemlerin ve İşlevler, F # programlama dili gibi programlama öğelerine erişimi denetlemeyi öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 6b13ac03d2a4a6c53b53d4c790760f5d51b334ee
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43540442"
---
# <a name="access-control"></a><span data-ttu-id="95836-103">Erişim Denetimi</span><span class="sxs-lookup"><span data-stu-id="95836-103">Access Control</span></span>

<span data-ttu-id="95836-104">*Erişim denetimi* hangi istemcilerin türleri, yöntemleri ve işlevleri gibi belirli program öğelerini kullanabilirsiniz bildirmek için ifade eder.</span><span class="sxs-lookup"><span data-stu-id="95836-104">*Access control* refers to declaring which clients can use certain program elements, such as types, methods, and functions.</span></span>

## <a name="basics-of-access-control"></a><span data-ttu-id="95836-105">Erişim denetimi ile ilgili temel bilgiler</span><span class="sxs-lookup"><span data-stu-id="95836-105">Basics of Access Control</span></span>
<span data-ttu-id="95836-106">F #'ta erişimi denetleme tanımlayıcıları `public`, `internal`, ve `private` modülleri, türleri, yöntemleri, değer tanımları, işlevleri, özellikleri ve açık alanlar için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="95836-106">In F#, the access control specifiers `public`, `internal`, and `private` can be applied to modules, types, methods, value definitions, functions, properties, and explicit fields.</span></span>

- <span data-ttu-id="95836-107">`public` varlığın tüm çağıranlar tarafından erişilebilir olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="95836-107">`public` indicates that the entity can be accessed by all callers.</span></span>

- <span data-ttu-id="95836-108">`internal` varlık yalnızca aynı bütünleştirilmiş koddan erişilebilir olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="95836-108">`internal` indicates that the entity can be accessed only from the same assembly.</span></span>

- <span data-ttu-id="95836-109">`private` varlık yalnızca kapsayan tür veya modülünden erişilebilir olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="95836-109">`private` indicates that the entity can be accessed only from the enclosing type or module.</span></span>

>[!NOTE] 
<span data-ttu-id="95836-110">Erişim belirticisi `protected` destekleyen dillerde yazılan türleri kullanıyorsanız, kabul edilebilir olmasına rağmen F # kullanılmayan `protected` erişim.</span><span class="sxs-lookup"><span data-stu-id="95836-110">The access specifier `protected` is not used in F#, although it is acceptable if you are using types authored in languages that do support `protected` access.</span></span> <span data-ttu-id="95836-111">Bu nedenle, korunan bir yöntemi geçersiz kılarsanız, yöntemi yalnızca sınıf ve onun alt öğelerine içinde erişilebilir kalır.</span><span class="sxs-lookup"><span data-stu-id="95836-111">Therefore, if you override a protected method, your method remains accessible only within the class and its descendents.</span></span>

<span data-ttu-id="95836-112">Genel olarak, aşağıdakiler haricinde varlığın adını önünde tanımlayıcısı put bir `mutable` veya `inline` belirticisi kullanıldığında, erişim denetimi belirticisinden sonra görünen.</span><span class="sxs-lookup"><span data-stu-id="95836-112">In general, the specifier is put in front of the name of the entity, except when a `mutable` or `inline` specifier is used, which appear after the access control specifier.</span></span>

<span data-ttu-id="95836-113">Hiçbir erişim belirticisi kullanıldığında varsayılandır `public`, dışında `let` her zaman bir türdeki bağlamaları `private` türü.</span><span class="sxs-lookup"><span data-stu-id="95836-113">If no access specifier is used, the default is `public`, except for `let` bindings in a type, which are always `private` to the type.</span></span>

<span data-ttu-id="95836-114">İmzalarını F #, F # program öğelerine erişimi denetlemek için başka bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="95836-114">Signatures in F# provide another mechanism for controlling access to F# program elements.</span></span> <span data-ttu-id="95836-115">İmzalar için erişim denetimi gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="95836-115">Signatures are not required for access control.</span></span> <span data-ttu-id="95836-116">Daha fazla bilgi için [imzaları](signatures.md).</span><span class="sxs-lookup"><span data-stu-id="95836-116">For more information, see [Signatures](signatures.md).</span></span>

## <a name="rules-for-access-control"></a><span data-ttu-id="95836-117">Erişim denetim için kuralları</span><span class="sxs-lookup"><span data-stu-id="95836-117">Rules for Access Control</span></span>
<span data-ttu-id="95836-118">Erişim denetimi aşağıdaki kurallarına tabidir şöyledir:</span><span class="sxs-lookup"><span data-stu-id="95836-118">Access control is subject to the following rules:</span></span>

- <span data-ttu-id="95836-119">Devralma bildirimleri (diğer bir deyişle, kullanımını `inherit` bir sınıf için temel sınıf belirtmek için), arabirim (bir sınıf bir arabirim uyguladığını belirterek olduğu gibi) bildirimleri ve soyut üyeleri, her zaman aynı erişilebilirliği kapsayan tür olarak sahiptir.</span><span class="sxs-lookup"><span data-stu-id="95836-119">Inheritance declarations (that is, the use of `inherit` to specify a base class for a class), interface declarations (that is, specifying that a class implements an interface), and abstract members always have the same accessibility as the enclosing type.</span></span> <span data-ttu-id="95836-120">Bu nedenle, erişim denetimi belirticisinin bu yapıları üzerinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="95836-120">Therefore, an access control specifier cannot be used on these constructs.</span></span>

- <span data-ttu-id="95836-121">Erişilebilirlik için ayrılmış bir birleşim bireysel durumlarda, ayrılmış birleşim erişilebilirliğini tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="95836-121">Accessibility for individual cases in a discriminated union is determined by the accessibility of the discriminated union itself.</span></span> <span data-ttu-id="95836-122">Diğer bir deyişle, belirli bir birleşim durumu birleşim bundan daha az erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="95836-122">That is, a particular union case is no less accessible than the union itself.</span></span>

- <span data-ttu-id="95836-123">Bir kayıt türünün her bir alanı olamaz için erişilebilirlik kaydın kendisini erişilebilirliğini tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="95836-123">Accessibility for individual fields of a record type cannot is determined by the accessibility of the record itself.</span></span> <span data-ttu-id="95836-124">Diğer bir deyişle, belirli kayıt etiket kaydı bundan daha az erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="95836-124">That is, a particular record label is no less accessible than the record itself.</span></span>

## <a name="example"></a><span data-ttu-id="95836-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="95836-125">Example</span></span>
<span data-ttu-id="95836-126">Aşağıdaki kod, erişim denetimi tanımlayıcıları kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="95836-126">The following code illustrates the use of access control specifiers.</span></span> <span data-ttu-id="95836-127">Projenin başında iki dosya vardır `Module1.fs` ve `Module2.fs`.</span><span class="sxs-lookup"><span data-stu-id="95836-127">There are two files in the project, `Module1.fs` and `Module2.fs`.</span></span> <span data-ttu-id="95836-128">Her dosya örtük olarak bir modüldür.</span><span class="sxs-lookup"><span data-stu-id="95836-128">Each file is implicitly a module.</span></span> <span data-ttu-id="95836-129">Bu nedenle, iki modül vardır `Module1` ve `Module2`.</span><span class="sxs-lookup"><span data-stu-id="95836-129">Therefore, there are two modules, `Module1` and `Module2`.</span></span> <span data-ttu-id="95836-130">Özel bir tür ile iç tür tanımlanan `Module1`.</span><span class="sxs-lookup"><span data-stu-id="95836-130">A private type and an internal type are defined in `Module1`.</span></span> <span data-ttu-id="95836-131">Özel tür erişilemez `Module2`, ancak iç türü.</span><span class="sxs-lookup"><span data-stu-id="95836-131">The private type cannot be accessed from `Module2`, but the internal type can.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet1.fs)]
    
<span data-ttu-id="95836-132">Aşağıdaki kod içinde oluşturulan türleri erişilebilirliğini test `Module1.fs`.</span><span class="sxs-lookup"><span data-stu-id="95836-132">The following code tests the accessibility of the types created in `Module1.fs`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet2.fs)]
    
## <a name="see-also"></a><span data-ttu-id="95836-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="95836-133">See Also</span></span>
[<span data-ttu-id="95836-134">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="95836-134">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="95836-135">İmzalar</span><span class="sxs-lookup"><span data-stu-id="95836-135">Signatures</span></span>](signatures.md)
