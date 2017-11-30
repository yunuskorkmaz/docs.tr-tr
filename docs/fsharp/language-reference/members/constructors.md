---
title: "Oluşturucular (F#)"
description: "Tanımlayın ve oluşturucular F #'ta oluşturmak ve sınıf ve yapısı nesneleri başlatmak için nasıl kullanılacağını öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e0da2250-29de-4145-a1be-e5faff080759
ms.openlocfilehash: 60ed93f1c1dc15e99465d969c9e4fd3e61c28ffa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="constructors"></a><span data-ttu-id="9530e-104">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="9530e-104">Constructors</span></span>

<span data-ttu-id="9530e-105">Bu konu, tanımlama ve oluşturma ve sınıf ve yapısı nesneleri başlatma için oluşturucular kullanma açıklar.</span><span class="sxs-lookup"><span data-stu-id="9530e-105">This topic describes how to define and use constructors to create and initialize class and structure objects.</span></span>


## <a name="construction-of-class-objects"></a><span data-ttu-id="9530e-106">Sınıf nesnelerine yapımı</span><span class="sxs-lookup"><span data-stu-id="9530e-106">Construction of Class Objects</span></span>
<span data-ttu-id="9530e-107">Sınıf türleri nesnelerin oluşturucular vardır.</span><span class="sxs-lookup"><span data-stu-id="9530e-107">Objects of class types have constructors.</span></span> <span data-ttu-id="9530e-108">Oluşturucular iki tür vardır.</span><span class="sxs-lookup"><span data-stu-id="9530e-108">There are two kinds of constructors.</span></span> <span data-ttu-id="9530e-109">Parametreleri yalnızca tür adından sonra parantez içinde görünür birincil Oluşturucusu biridir.</span><span class="sxs-lookup"><span data-stu-id="9530e-109">One is the primary constructor, whose parameters appear in parentheses just after the type name.</span></span> <span data-ttu-id="9530e-110">Diğer, isteğe bağlı ek oluşturucuları kullanarak belirttiğiniz `new` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="9530e-110">You specify other, optional additional constructors by using the `new` keyword.</span></span> <span data-ttu-id="9530e-111">Böyle bir ek oluşturucular birincil Oluşturucusu çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9530e-111">Any such additional constructors must call the primary constructor.</span></span>

<span data-ttu-id="9530e-112">Birincil Oluşturucuyu içeren `let` ve `do` sınıf tanımını başlangıcında görünür bağlar.</span><span class="sxs-lookup"><span data-stu-id="9530e-112">The primary constructor contains `let` and `do` bindings that appear at the start of the class definition.</span></span> <span data-ttu-id="9530e-113">A `let` bağlama bildirir özel alanlar ve; sınıfı yöntemlerinin bir `do` bağlama kodu yürütür.</span><span class="sxs-lookup"><span data-stu-id="9530e-113">A `let` binding declares private fields and methods of the class; a `do` binding executes code.</span></span> <span data-ttu-id="9530e-114">Hakkında daha fazla bilgi için `let` sınıfı Yapıcılardaki bağlamaları bkz [ `let` sınıflardaki bağlamaları](let-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="9530e-114">For more information about `let` bindings in class constructors, see [`let` Bindings in Classes](let-bindings-in-classes.md).</span></span> <span data-ttu-id="9530e-115">Hakkında daha fazla bilgi için `do` Oluşturucular, bağlama bkz [ `do` sınıflardaki bağlamaları](do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="9530e-115">For more information about `do` bindings in constructors, see [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

<span data-ttu-id="9530e-116">Çağrı istediğiniz Oluşturucusu birincil oluşturucu veya ek bir oluşturucu olup olmadığına bakılmaksızın, nesneleri kullanarak oluşturabileceğiniz bir `new` ifadesi, ile veya isteğe bağlı olmadan `new` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="9530e-116">Regardless of whether the constructor you want to call is a primary constructor or an additional constructor, you can create objects by using a `new` expression, with or without the optional `new` keyword.</span></span> <span data-ttu-id="9530e-117">Virgülle ayrılmış nesnelerinizi oluşturucu bağımsız değişkenleri, sipariş değişkenlerinde listesi ile birlikte başlatmak ve parantez içinde ya da parantez içinde adlandırılmış bağımsız değişkenler ve değerleri kullanarak içine alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9530e-117">You initialize your objects together with constructor arguments, either by listing the arguments in order and separated by commas and enclosed in parentheses, or by using named arguments and values in parentheses.</span></span> <span data-ttu-id="9530e-118">Ayrıca özellikleri bir nesne üzerinde nesne oluşturma sırasında özellik adlarını kullanarak ayarlayabilirsiniz ve yalnızca kullandığınız gibi değerler atama adlı oluşturucu bağımsız değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="9530e-118">You can also set properties on an object during the construction of the object by using the property names and assigning values just as you use named constructor arguments.</span></span>

<span data-ttu-id="9530e-119">Aşağıdaki kod bir oluşturucu ve nesneleri oluşturma çeşitli şekillerde olan bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="9530e-119">The following code illustrates a class that has a constructor and various ways of creating objects.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

<span data-ttu-id="9530e-120">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="9530e-120">The output is as follows.</span></span>

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a><span data-ttu-id="9530e-121">Yapıları yapımı</span><span class="sxs-lookup"><span data-stu-id="9530e-121">Construction of Structures</span></span>
<span data-ttu-id="9530e-122">Yapıları sınıflarının tüm kuralları izleyin.</span><span class="sxs-lookup"><span data-stu-id="9530e-122">Structures follow all the rules of classes.</span></span> <span data-ttu-id="9530e-123">Bu nedenle, birincil bir oluşturucuya sahip olabilir ve kullanarak ek oluşturucular sağlayabilirsiniz `new`.</span><span class="sxs-lookup"><span data-stu-id="9530e-123">Therefore, you can have a primary constructor, and you can provide additional constructors by using `new`.</span></span> <span data-ttu-id="9530e-124">Ancak, yapılar ve sınıflar arasında önemli bir fark yoktur: birincil bir oluşturucu yok tanımlanan olsa bile, yapıları varsayılan bir oluşturucu (diğer bir deyişle, bir bağımsız değişken içermeyen) sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="9530e-124">However, there is one important difference between structures and classes: structures can have a default constructor (that is, one with no arguments) even if no primary constructor is defined.</span></span> <span data-ttu-id="9530e-125">Varsayılan Oluşturucu tüm alanları varsayılan değer türü, genellikle sıfır veya eşdeğer başlatır.</span><span class="sxs-lookup"><span data-stu-id="9530e-125">The default constructor initializes all the fields to the default value for that type, usually zero or its equivalent.</span></span> <span data-ttu-id="9530e-126">Varsayılan Oluşturucu ile çakışmadığından emin yapıları için tanımladığınız oluşturucular en az bir değişken olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9530e-126">Any constructors that you define for structures must have at least one argument so that they do not conflict with the default constructor.</span></span>

<span data-ttu-id="9530e-127">Ayrıca, yapıları kullanılarak oluşturulan alanları genellikle sahip `val` anahtar sözcüğü; sınıfları Ayrıca bu alanlar vardır.</span><span class="sxs-lookup"><span data-stu-id="9530e-127">Also, structures often have fields that are created by using the `val` keyword; classes can also have these fields.</span></span> <span data-ttu-id="9530e-128">Yapılar ve alanlar kullanılarak tanımlanmış sınıfları `val` anahtar sözcüğü de başlatılabilir ek kurucularda kayıt ifadeler kullanarak aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="9530e-128">Structures and classes that have fields defined by using the `val` keyword can also be initialized in additional constructors by using record expressions, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

<span data-ttu-id="9530e-129">Daha fazla bilgi için bkz: [açık alanlar: `val` anahtar sözcüğü](explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="9530e-129">For more information, see [Explicit Fields: The `val` Keyword](explicit-fields-the-val-keyword.md).</span></span>


## <a name="executing-side-effects-in-constructors"></a><span data-ttu-id="9530e-130">Oluşturucularda yan etkileri yürütme</span><span class="sxs-lookup"><span data-stu-id="9530e-130">Executing Side Effects in Constructors</span></span>
<span data-ttu-id="9530e-131">Bir sınıf birincil oluşturucuda kod yürütebilir bir `do` bağlama.</span><span class="sxs-lookup"><span data-stu-id="9530e-131">A primary constructor in a class can execute code in a `do` binding.</span></span> <span data-ttu-id="9530e-132">Ancak, yoksa ne kod ek bir oluşturucu olmadan yürütmek bir `do` bağlama?</span><span class="sxs-lookup"><span data-stu-id="9530e-132">However, what if you have to execute code in an additional constructor, without a `do` binding?</span></span> <span data-ttu-id="9530e-133">Bunu yapmak için kullandığınız `then` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="9530e-133">To do this, you use the `then` keyword.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

<span data-ttu-id="9530e-134">Birincil Oluşturucusu yan etkileri hala yürütün.</span><span class="sxs-lookup"><span data-stu-id="9530e-134">The side effects of the primary constructor still execute.</span></span> <span data-ttu-id="9530e-135">Bu nedenle, çıktı şu şekildedir.</span><span class="sxs-lookup"><span data-stu-id="9530e-135">Therefore, the output is as follows.</span></span>

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

## <a name="self-identifiers-in-constructors"></a><span data-ttu-id="9530e-136">Yapıcılardaki kendine yönelik tanımlayıcılar</span><span class="sxs-lookup"><span data-stu-id="9530e-136">Self Identifiers in Constructors</span></span>
<span data-ttu-id="9530e-137">Diğer üyeler her üye tanımı geçerli nesne için bir ad sağlayın.</span><span class="sxs-lookup"><span data-stu-id="9530e-137">In other members, you provide a name for the current object in the definition of each member.</span></span> <span data-ttu-id="9530e-138">Kullanarak sınıf tanımının ilk satırda kendini tanımlayıcı koyabilirsiniz `as` hemen Oluşturucu parametreleri aşağıdaki anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="9530e-138">You can also put the self identifier on the first line of the class definition by using the `as` keyword immediately following the constructor parameters.</span></span> <span data-ttu-id="9530e-139">Aşağıdaki örnekte bu söz dizimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9530e-139">The following example illustrates this syntax.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

<span data-ttu-id="9530e-140">Ek kurucularda da kendi kendine tanımlayıcı koyarak tanımlayabilirsiniz `as` Oluşturucu parametreleri hemen sonra yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="9530e-140">In additional constructors, you can also define a self identifier by putting the `as` clause right after the constructor parameters.</span></span> <span data-ttu-id="9530e-141">Aşağıdaki örnekte bu söz dizimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9530e-141">The following example illustrates this syntax.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

<span data-ttu-id="9530e-142">Tam olarak tanımlanmadan önce bir nesne kullanmaya çalıştığınızda sorunları ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="9530e-142">Problems can occur when you try to use an object before it is fully defined.</span></span> <span data-ttu-id="9530e-143">Bu nedenle, kendini tanımlayıcı kullanımlarını bir uyarı yayma ve nesne başlatılmadan önce bir nesnenin üyelerine erişilemeyen emin olmak için ek denetimler eklemek derleyici neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="9530e-143">Therefore, uses of the self identifier can cause the compiler to emit a warning and insert additional checks to ensure the members of an object are not accessed before the object is initialized.</span></span> <span data-ttu-id="9530e-144">Yalnızca kendi kendine tanımlayıcıda kullanması gereken `do` bağlamaları birincil oluşturucunun ya da sonra `then` ek oluşturucular anahtar sözcük.</span><span class="sxs-lookup"><span data-stu-id="9530e-144">You should only use the self identifier in the `do` bindings of the primary constructor, or after the `then` keyword in additional constructors.</span></span>

<span data-ttu-id="9530e-145">Kendi kendine tanımlayıcı adı olması gerekmez `this`.</span><span class="sxs-lookup"><span data-stu-id="9530e-145">The name of the self identifier does not have to be `this`.</span></span> <span data-ttu-id="9530e-146">Geçerli bir tanımlayıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="9530e-146">It can be any valid identifier.</span></span>


## <a name="assigning-values-to-properties-at-initialization"></a><span data-ttu-id="9530e-147">Başlatma sırasında özelliklerine değerler atama</span><span class="sxs-lookup"><span data-stu-id="9530e-147">Assigning Values to Properties at Initialization</span></span>
<span data-ttu-id="9530e-148">Formun atamaları listesini ekleyerek başlatma kodda bir sınıf nesnesinin özellikleri için değer atayabilirsiniz `property = value` bir oluşturucu bağımsız değişken listesi.</span><span class="sxs-lookup"><span data-stu-id="9530e-148">You can assign values to the properties of a class object in the initialization code by appending a list of assignments of the form `property = value` to the argument list for a constructor.</span></span> <span data-ttu-id="9530e-149">Bu, aşağıdaki kod örneğinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="9530e-149">This is shown in the following code example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="9530e-150">Önceki kod aşağıdaki sürümü sıradan bağımsız değişkenler, isteğe bağlı bağımsız değişkenler ve bir oluşturucu çağrısı özelliği ayarlarında birleşimi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9530e-150">The following version of the previous code illustrates the combination of ordinary arguments, optional arguments, and property settings in one constructor call.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]
    
## <a name="constructors-in-inherited-class"></a><span data-ttu-id="9530e-151">Devralınan bir sınıf oluşturucuları</span><span class="sxs-lookup"><span data-stu-id="9530e-151">Constructors in inherited class</span></span>
<span data-ttu-id="9530e-152">Bir oluşturucuya sahip bir taban sınıftan devralınırken devral yan tümcesinde bağımsız değişkenleri belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9530e-152">When inheriting from a base class that has a constructor, you must specify its arguments in the inherit clause.</span></span> <span data-ttu-id="9530e-153">Daha fazla bilgi için bkz: [oluşturucular ve devralma](../inheritance.md#constructors-and-inheritance).</span><span class="sxs-lookup"><span data-stu-id="9530e-153">For more information, see [Constructors and inheritance](../inheritance.md#constructors-and-inheritance).</span></span>

## <a name="static-constructors-or-type-constructors"></a><span data-ttu-id="9530e-154">Statik oluşturucular veya türü oluşturucuları</span><span class="sxs-lookup"><span data-stu-id="9530e-154">Static Constructors or Type Constructors</span></span>
<span data-ttu-id="9530e-155">Nesneleri, statik oluşturmak için kodu belirtme yanı sıra `let` ve `do` bağlamaları yazılan türü ilk başlatma türü düzeyinde gerçekleştirmek için kullanılmadan önce yürütme sınıfı türlerinde.</span><span class="sxs-lookup"><span data-stu-id="9530e-155">In addition to specifying code for creating objects, static `let` and `do` bindings can be authored in class types that execute before the type is first used to perform initialization at the type level.</span></span> <span data-ttu-id="9530e-156">Daha fazla bilgi için bkz: [ `let` sınıflardaki bağlamaları](let-bindings-in-classes.md) ve [ `do` sınıflardaki bağlamaları](do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="9530e-156">For more information, see [`let` Bindings in Classes](let-bindings-in-classes.md) and [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9530e-157">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9530e-157">See Also</span></span>
[<span data-ttu-id="9530e-158">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="9530e-158">Members</span></span>](index.md)
