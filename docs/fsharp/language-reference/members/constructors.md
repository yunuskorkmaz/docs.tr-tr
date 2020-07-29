---
title: Oluşturucular
description: "F # ' da sınıf ve yapı nesneleri oluşturmak ve başlatmak için oluşturucuları tanımlama ve kullanma hakkında bilgi edinin."
ms.date: 05/16/2016
ms.openlocfilehash: be8fc3f1d82a9a7c778a6d094139f14150a28813
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303445"
---
# <a name="constructors"></a><span data-ttu-id="73e95-103">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="73e95-103">Constructors</span></span>

<span data-ttu-id="73e95-104">Bu makalede, sınıf ve yapı nesneleri oluşturmak ve başlatmak için oluşturucuların nasıl tanımlanacağı ve kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="73e95-104">This article describes how to define and use constructors to create and initialize class and structure objects.</span></span>

## <a name="construction-of-class-objects"></a><span data-ttu-id="73e95-105">Sınıf nesnelerinin oluşturulması</span><span class="sxs-lookup"><span data-stu-id="73e95-105">Construction of class objects</span></span>

<span data-ttu-id="73e95-106">Sınıf türündeki nesnelerin oluşturucuları vardır.</span><span class="sxs-lookup"><span data-stu-id="73e95-106">Objects of class types have constructors.</span></span> <span data-ttu-id="73e95-107">İki tür Oluşturucu vardır.</span><span class="sxs-lookup"><span data-stu-id="73e95-107">There are two kinds of constructors.</span></span> <span data-ttu-id="73e95-108">Bunlardan biri, tür adından hemen sonra, parametreleri parantez içinde görüntülenen birincil oluşturucudur.</span><span class="sxs-lookup"><span data-stu-id="73e95-108">One is the primary constructor, whose parameters appear in parentheses just after the type name.</span></span> <span data-ttu-id="73e95-109">Anahtar sözcüğünü kullanarak diğer, isteğe bağlı ek oluşturucular belirtirsiniz `new` .</span><span class="sxs-lookup"><span data-stu-id="73e95-109">You specify other, optional additional constructors by using the `new` keyword.</span></span> <span data-ttu-id="73e95-110">Bu tür ek oluşturucuların birincil oluşturucuyu çağırması gerekir.</span><span class="sxs-lookup"><span data-stu-id="73e95-110">Any such additional constructors must call the primary constructor.</span></span>

<span data-ttu-id="73e95-111">Birincil Oluşturucu, `let` `do` sınıf tanımının başlangıcında görüntülenen bağlamaları ve içerir.</span><span class="sxs-lookup"><span data-stu-id="73e95-111">The primary constructor contains `let` and `do` bindings that appear at the start of the class definition.</span></span> <span data-ttu-id="73e95-112">`let`Bağlama, sınıfın özel alanlarını ve yöntemlerini bildirir; bir `do` bağlama kodu yürütür.</span><span class="sxs-lookup"><span data-stu-id="73e95-112">A `let` binding declares private fields and methods of the class; a `do` binding executes code.</span></span> <span data-ttu-id="73e95-113">Sınıf oluşturucularında bağlamalar hakkında daha fazla bilgi için `let` bkz. [ `let` sınıflarda bağlamalar](let-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="73e95-113">For more information about `let` bindings in class constructors, see [`let` Bindings in Classes](let-bindings-in-classes.md).</span></span> <span data-ttu-id="73e95-114">Oluşturuculardaki bağlamalar hakkında daha fazla bilgi için `do` bkz. [ `do` sınıflarda bağlamalar](do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="73e95-114">For more information about `do` bindings in constructors, see [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

<span data-ttu-id="73e95-115">Çağırmak istediğiniz oluşturucunun birincil Oluşturucu mı yoksa ek bir Oluşturucu mı olduğuna bakılmaksızın, `new` isteğe bağlı anahtar sözcüğü ile veya olmadan bir ifadesi kullanarak nesneler oluşturabilirsiniz `new` .</span><span class="sxs-lookup"><span data-stu-id="73e95-115">Regardless of whether the constructor you want to call is a primary constructor or an additional constructor, you can create objects by using a `new` expression, with or without the optional `new` keyword.</span></span> <span data-ttu-id="73e95-116">Bağımsız değişkenleri sırayla listeleyerek ve virgülle ayırarak ya da parantez içinde adlandırılmış bağımsız değişkenleri ve değerleri kullanarak, nesnelerinizi Oluşturucu bağımsız değişkenlerle birlikte başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73e95-116">You initialize your objects together with constructor arguments, either by listing the arguments in order and separated by commas and enclosed in parentheses, or by using named arguments and values in parentheses.</span></span> <span data-ttu-id="73e95-117">Ayrıca, özellik adlarını kullanarak ve yalnızca adlandırılmış Oluşturucu bağımsız değişkenleri kullandığınız gibi değer atayarak nesne oluşturma sırasında nesne üzerinde özellikler ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73e95-117">You can also set properties on an object during the construction of the object by using the property names and assigning values just as you use named constructor arguments.</span></span>

<span data-ttu-id="73e95-118">Aşağıdaki kod, Oluşturucusu olan bir sınıfı ve nesne oluşturmanın çeşitli yollarını gösterir:</span><span class="sxs-lookup"><span data-stu-id="73e95-118">The following code illustrates a class that has a constructor and various ways of creating objects:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

<span data-ttu-id="73e95-119">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="73e95-119">The output is as follows:</span></span>

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a><span data-ttu-id="73e95-120">Yapıların oluşturulması</span><span class="sxs-lookup"><span data-stu-id="73e95-120">Construction of structures</span></span>

<span data-ttu-id="73e95-121">Yapılar sınıfların tüm kurallarını izler.</span><span class="sxs-lookup"><span data-stu-id="73e95-121">Structures follow all the rules of classes.</span></span> <span data-ttu-id="73e95-122">Bu nedenle, bir birincil oluşturucuya sahip olabilirsiniz ve kullanarak ek oluşturucular sağlayabilirsiniz `new` .</span><span class="sxs-lookup"><span data-stu-id="73e95-122">Therefore, you can have a primary constructor, and you can provide additional constructors by using `new`.</span></span> <span data-ttu-id="73e95-123">Ancak, yapılar ve sınıflar arasında önemli bir farklılık vardır: yapılar, hiçbir birincil Oluşturucu tanımlanmasa bile parametresiz bir oluşturucuya (bağımsız değişken içermeyen bir) sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="73e95-123">However, there is one important difference between structures and classes: structures can have a parameterless constructor (that is, one with no arguments) even if no primary constructor is defined.</span></span> <span data-ttu-id="73e95-124">Parametresiz Oluşturucu, tüm alanları bu tür için varsayılan değere (genellikle sıfır veya eşdeğeri) başlatır.</span><span class="sxs-lookup"><span data-stu-id="73e95-124">The parameterless constructor initializes all the fields to the default value for that type, usually zero or its equivalent.</span></span> <span data-ttu-id="73e95-125">Yapılar için tanımladığınız tüm oluşturucular, parametresiz oluşturucuyla çakışmayacak şekilde en az bir bağımsız değişkene sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="73e95-125">Any constructors that you define for structures must have at least one argument so that they do not conflict with the parameterless constructor.</span></span>

<span data-ttu-id="73e95-126">Ayrıca, yapılar genellikle anahtar sözcüğü kullanılarak oluşturulan alanlara sahiptir `val` ; sınıflar da bu alanları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="73e95-126">Also, structures often have fields that are created by using the `val` keyword; classes can also have these fields.</span></span> <span data-ttu-id="73e95-127">Anahtar sözcüğü kullanılarak tanımlanmış olan yapılar ve sınıflar `val` , aşağıdaki kodda gösterildiği gibi, kayıt ifadeleri kullanılarak ek oluşturuculara de başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="73e95-127">Structures and classes that have fields defined by using the `val` keyword can also be initialized in additional constructors by using record expressions, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

<span data-ttu-id="73e95-128">Daha fazla bilgi için bkz. [açık alanlar: `val` anahtar sözcük](explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="73e95-128">For more information, see [Explicit Fields: The `val` Keyword](explicit-fields-the-val-keyword.md).</span></span>

## <a name="executing-side-effects-in-constructors"></a><span data-ttu-id="73e95-129">Oluşturucularda yan etkileri yürütme</span><span class="sxs-lookup"><span data-stu-id="73e95-129">Executing side effects in constructors</span></span>

<span data-ttu-id="73e95-130">Bir sınıftaki birincil Oluşturucu, bir `do` bağlamadaki kodu yürütebilir.</span><span class="sxs-lookup"><span data-stu-id="73e95-130">A primary constructor in a class can execute code in a `do` binding.</span></span> <span data-ttu-id="73e95-131">Ancak, bir bağlama olmadan kodu ek bir oluşturucuda yürütmeniz gerekiyorsa ne yapmanız gerekir `do` ?</span><span class="sxs-lookup"><span data-stu-id="73e95-131">However, what if you have to execute code in an additional constructor, without a `do` binding?</span></span> <span data-ttu-id="73e95-132">Bunu yapmak için `then` anahtar sözcüğünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="73e95-132">To do this, you use the `then` keyword.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

<span data-ttu-id="73e95-133">Birincil oluşturucunun yan etkileri hala yürütülür.</span><span class="sxs-lookup"><span data-stu-id="73e95-133">The side effects of the primary constructor still execute.</span></span> <span data-ttu-id="73e95-134">Bu nedenle, çıkış aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="73e95-134">Therefore, the output is as follows:</span></span>

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

<span data-ttu-id="73e95-135">Bunun yerine neden gerekli olmasının nedeni, `then` `do` `do` anahtar sözcüğünün, `unit` ek bir oluşturucunun gövdesinde mevcut olduğunda, bir döndüren ifadenin standart anlamı vardır.</span><span class="sxs-lookup"><span data-stu-id="73e95-135">The reason why `then` is required instead of another `do` is that the `do` keyword has its standard meaning of delimiting a `unit`-returning expression when present in the body of an additional constructor.</span></span> <span data-ttu-id="73e95-136">Birincil oluşturucuların bağlamında yalnızca özel anlamı vardır.</span><span class="sxs-lookup"><span data-stu-id="73e95-136">It only has special meaning in the context of primary constructors.</span></span>

## <a name="self-identifiers-in-constructors"></a><span data-ttu-id="73e95-137">Oluşturucularda kendi tanımlayıcıları</span><span class="sxs-lookup"><span data-stu-id="73e95-137">Self identifiers in constructors</span></span>

<span data-ttu-id="73e95-138">Diğer üyelerde, her üyenin tanımında geçerli nesne için bir ad sağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="73e95-138">In other members, you provide a name for the current object in the definition of each member.</span></span> <span data-ttu-id="73e95-139">Ayrıca, `as` Oluşturucu parametrelerinin hemen ardından gelen anahtar sözcüğünü kullanarak sınıf tanımının ilk satırına kendi tanımlayıcısını koyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73e95-139">You can also put the self identifier on the first line of the class definition by using the `as` keyword immediately following the constructor parameters.</span></span> <span data-ttu-id="73e95-140">Aşağıdaki örnekte bu söz dizimi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="73e95-140">The following example illustrates this syntax.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

<span data-ttu-id="73e95-141">Ek oluşturucularda, `as` yan tümcesini Oluşturucu parametrelerinden sonra koyarak kendi kendine tanımlayıcıyı da tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73e95-141">In additional constructors, you can also define a self identifier by putting the `as` clause right after the constructor parameters.</span></span> <span data-ttu-id="73e95-142">Aşağıdaki örnekte bu söz dizimi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="73e95-142">The following example illustrates this syntax:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

<span data-ttu-id="73e95-143">Bir nesne, tam olarak tanımlanmadan önce kullanmaya çalıştığınızda sorunlar oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="73e95-143">Problems can occur when you try to use an object before it is fully defined.</span></span> <span data-ttu-id="73e95-144">Bu nedenle, kendi kendine tanımlayıcı kullanımları derleyicinin bir uyarı yaymasına ve nesne başlatılmadan önce bir nesnenin üyelerine erişilmemesini sağlamak için ek denetimler eklemesine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="73e95-144">Therefore, uses of the self identifier can cause the compiler to emit a warning and insert additional checks to ensure the members of an object are not accessed before the object is initialized.</span></span> <span data-ttu-id="73e95-145">Self tanımlayıcıyı yalnızca `do` birincil oluşturucunun bağlamalarında veya `then` ek oluşturuculardaki anahtar sözcükten sonra kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="73e95-145">You should only use the self identifier in the `do` bindings of the primary constructor, or after the `then` keyword in additional constructors.</span></span>

<span data-ttu-id="73e95-146">Kendi tanımlayıcısının adının olması gerekmez `this` .</span><span class="sxs-lookup"><span data-stu-id="73e95-146">The name of the self identifier does not have to be `this`.</span></span> <span data-ttu-id="73e95-147">Geçerli bir tanımlayıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="73e95-147">It can be any valid identifier.</span></span>

## <a name="assigning-values-to-properties-at-initialization"></a><span data-ttu-id="73e95-148">Başlatma sırasında özelliklere değerler atama</span><span class="sxs-lookup"><span data-stu-id="73e95-148">Assigning values to properties at initialization</span></span>

<span data-ttu-id="73e95-149">Bir oluşturucunun bağımsız değişken listesine form atamalarının bir listesini ekleyerek başlatma kodundaki bir sınıf nesnesinin özelliklerine değerler atayabilirsiniz `property = value` .</span><span class="sxs-lookup"><span data-stu-id="73e95-149">You can assign values to the properties of a class object in the initialization code by appending a list of assignments of the form `property = value` to the argument list for a constructor.</span></span> <span data-ttu-id="73e95-150">Bu, aşağıdaki kod örneğinde gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="73e95-150">This is shown in the following code example:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="73e95-151">Önceki kodun aşağıdaki sürümü, tek bir Oluşturucu çağrısında sıradan bağımsız değişkenlerin, isteğe bağlı bağımsız değişkenlerin ve özellik ayarlarının birleşimini gösterir:</span><span class="sxs-lookup"><span data-stu-id="73e95-151">The following version of the previous code illustrates the combination of ordinary arguments, optional arguments, and property settings in one constructor call:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]

## <a name="constructors-in-inherited-class"></a><span data-ttu-id="73e95-152">Devralınan sınıftaki oluşturucular</span><span class="sxs-lookup"><span data-stu-id="73e95-152">Constructors in inherited class</span></span>

<span data-ttu-id="73e95-153">Oluşturucusu olan bir taban sınıftan devralınırken, devralma yan tümcesinde bağımsız değişkenlerini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="73e95-153">When inheriting from a base class that has a constructor, you must specify its arguments in the inherit clause.</span></span> <span data-ttu-id="73e95-154">Daha fazla bilgi için bkz. [oluşturucular ve devralma](../inheritance.md#constructors-and-inheritance).</span><span class="sxs-lookup"><span data-stu-id="73e95-154">For more information, see [Constructors and inheritance](../inheritance.md#constructors-and-inheritance).</span></span>

## <a name="static-constructors-or-type-constructors"></a><span data-ttu-id="73e95-155">Statik oluşturucular veya tür oluşturucuları</span><span class="sxs-lookup"><span data-stu-id="73e95-155">Static constructors or type constructors</span></span>

<span data-ttu-id="73e95-156">Nesne oluşturmaya yönelik kodu belirtmenin yanı sıra, statik `let` ve `do` bağlamalar tür düzeyinde başlatma gerçekleştirmek için önce yürütülen sınıf türlerinde yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="73e95-156">In addition to specifying code for creating objects, static `let` and `do` bindings can be authored in class types that execute before the type is first used to perform initialization at the type level.</span></span> <span data-ttu-id="73e95-157">Daha fazla bilgi için bkz. sınıflardaki [ `let` sınıflarda ve bağlamalardaki bağlamalar](let-bindings-in-classes.md) . [ `do` ](do-bindings-in-classes.md)</span><span class="sxs-lookup"><span data-stu-id="73e95-157">For more information, see [`let` Bindings in Classes](let-bindings-in-classes.md) and [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="73e95-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73e95-158">See also</span></span>

- [<span data-ttu-id="73e95-159">Üyeler</span><span class="sxs-lookup"><span data-stu-id="73e95-159">Members</span></span>](index.md)
