---
title: Oluşturucular-C# Programlama Kılavuzu
description: Bir sınıf veya yapı oluşturulduğunda C# içindeki bir Oluşturucu çağırılır. Varsayılan değerleri ayarlamak için oluşturucuları kullanın, örnek oluşturmayı sınırlayın ve esnek, okunması kolay bir kod yazın.
ms.date: 05/05/2017
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
ms.openlocfilehash: e8758d7322d7fde45ccbd9eaf9248a3168980bd3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555347"
---
# <a name="constructors-c-programming-guide"></a><span data-ttu-id="dba24-104">Oluşturucular (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="dba24-104">Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="dba24-105">Bir [sınıf](../../language-reference/keywords/class.md) veya [Yapı](../../language-reference/builtin-types/struct.md) oluşturulduğunda, Oluşturucusu çağırılır.</span><span class="sxs-lookup"><span data-stu-id="dba24-105">Whenever a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/builtin-types/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="dba24-106">Bir sınıf veya yapının farklı bağımsız değişkenler alan birden çok Oluşturucusu olabilir.</span><span class="sxs-lookup"><span data-stu-id="dba24-106">A class or struct may have multiple constructors that take different arguments.</span></span> <span data-ttu-id="dba24-107">Oluşturucular, programcının varsayılan değerleri ayarlama, örnek oluşturmayı sınırlandırma ve esnek ve okunması kolay bir kod yazma olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="dba24-107">Constructors enable the programmer to set default values, limit instantiation, and write code that is flexible and easy to read.</span></span> <span data-ttu-id="dba24-108">Daha fazla bilgi ve örnek için bkz. oluşturucular ve [örnek oluşturucular](./instance-constructors.md) [kullanma](./using-constructors.md) .</span><span class="sxs-lookup"><span data-stu-id="dba24-108">For more information and examples, see [Using Constructors](./using-constructors.md) and [Instance Constructors](./instance-constructors.md).</span></span>  

## <a name="parameterless-constructors"></a><span data-ttu-id="dba24-109">Parametresiz oluşturucular</span><span class="sxs-lookup"><span data-stu-id="dba24-109">Parameterless constructors</span></span>
  
<span data-ttu-id="dba24-110">Sınıfınız için bir Oluşturucu sağlamazsanız, C#, nesneyi örnekleyen ve varsayılan olarak [C# Types](../../language-reference/builtin-types/default-values.md) makalesinde listelenen üye değişkenlerini varsayılan değerlere ayarlayan bir varsayılan olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dba24-110">If you don't provide a constructor for your class, C# creates one by default that instantiates the object and sets member variables to the default values as listed in the [Default values of C# types](../../language-reference/builtin-types/default-values.md) article.</span></span> <span data-ttu-id="dba24-111">Struct için bir Oluşturucu sağlamazsanız, C# her bir alanı varsayılan değerine otomatik olarak başlatmak için *örtük parametresiz bir oluşturucuya* dayanır.</span><span class="sxs-lookup"><span data-stu-id="dba24-111">If you don't provide a constructor for your struct, C# relies on an *implicit parameterless constructor* to automatically initialize each field to its default value.</span></span> <span data-ttu-id="dba24-112">Daha fazla bilgi ve örnek için bkz. [örnek oluşturucular](instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="dba24-112">For more information and examples, see [Instance constructors](instance-constructors.md).</span></span>  

## <a name="constructor-syntax"></a><span data-ttu-id="dba24-113">Oluşturucu sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dba24-113">Constructor syntax</span></span>

<span data-ttu-id="dba24-114">Oluşturucu, adı türünün adı ile aynı olan bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="dba24-114">A constructor is a method whose name is the same as the name of its type.</span></span> <span data-ttu-id="dba24-115">Yöntemi imzasında yalnızca Yöntem adı ve parametre listesi bulunur; dönüş türü içermez.</span><span class="sxs-lookup"><span data-stu-id="dba24-115">Its method signature includes only the method name and its parameter list; it does not include a return type.</span></span> <span data-ttu-id="dba24-116">Aşağıdaki örnek adlı bir sınıf için oluşturucuyu gösterir `Person` .</span><span class="sxs-lookup"><span data-stu-id="dba24-116">The following example shows the constructor for a class named `Person`.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

<span data-ttu-id="dba24-117">Bir Oluşturucu tek bir deyim olarak uygulan, bir [ifade gövdesi tanımı](../statements-expressions-operators/expression-bodied-members.md)kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dba24-117">If a constructor can be implemented as a single statement, you can use an [expression body definition](../statements-expressions-operators/expression-bodied-members.md).</span></span> <span data-ttu-id="dba24-118">Aşağıdaki örnek, `Location` oluşturucusunun *adı*adlı tek bir dize parametresine sahip olan bir sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dba24-118">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="dba24-119">İfade gövdesi tanımı, bağımsız değişkenini `locationName` alana atar.</span><span class="sxs-lookup"><span data-stu-id="dba24-119">The expression body definition assigns the argument to the `locationName` field.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a><span data-ttu-id="dba24-120">Statik oluşturucular</span><span class="sxs-lookup"><span data-stu-id="dba24-120">Static constructors</span></span>

<span data-ttu-id="dba24-121">Önceki örneklerde, yeni bir nesne oluşturan tüm gösterilen örnek oluşturucuları vardır.</span><span class="sxs-lookup"><span data-stu-id="dba24-121">The previous examples have all shown instance constructors, which create a new object.</span></span> <span data-ttu-id="dba24-122">Bir sınıf veya yapı, türün statik üyelerini Başlatan statik bir oluşturucuya de sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="dba24-122">A class or struct can also have a static constructor, which initializes static members of the type.</span></span>  <span data-ttu-id="dba24-123">Statik oluşturucular parametresiz.</span><span class="sxs-lookup"><span data-stu-id="dba24-123">Static constructors are parameterless.</span></span> <span data-ttu-id="dba24-124">Statik alanları başlatmak için statik bir Oluşturucu sağlamazsanız, C# derleyicisi statik alanları varsayılan değer [olan C# Types](../../language-reference/builtin-types/default-values.md) makalesinde listelendiği gibi varsayılan değerlerine başlatır.</span><span class="sxs-lookup"><span data-stu-id="dba24-124">If you don't provide a static constructor to initialize static fields, the C# compiler initializes static fields to their default value as listed in the [Default values of C# types](../../language-reference/builtin-types/default-values.md) article.</span></span>

<span data-ttu-id="dba24-125">Aşağıdaki örnek, statik bir alanı başlatmak için statik bir Oluşturucu kullanır.</span><span class="sxs-lookup"><span data-stu-id="dba24-125">The following example uses a static constructor to initialize a static field.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]  

<span data-ttu-id="dba24-126">Aşağıdaki örnekte gösterildiği gibi, bir ifade gövdesi tanımıyla bir statik oluşturucu da tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dba24-126">You can also define a static constructor with an expression body definition, as the following example shows.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]  

<span data-ttu-id="dba24-127">Daha fazla bilgi ve örnek için bkz. [statik oluşturucular](./static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="dba24-127">For more information and examples, see [Static Constructors](./static-constructors.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dba24-128">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="dba24-128">In This Section</span></span>  
 [<span data-ttu-id="dba24-129">Oluşturucular Kullanma</span><span class="sxs-lookup"><span data-stu-id="dba24-129">Using Constructors</span></span>](./using-constructors.md)  
  
 [<span data-ttu-id="dba24-130">Örnek Oluşturucuları</span><span class="sxs-lookup"><span data-stu-id="dba24-130">Instance Constructors</span></span>](./instance-constructors.md)  
  
 [<span data-ttu-id="dba24-131">Özel Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="dba24-131">Private Constructors</span></span>](./private-constructors.md)  
  
 [<span data-ttu-id="dba24-132">Statik Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="dba24-132">Static Constructors</span></span>](./static-constructors.md)  
  
 [<span data-ttu-id="dba24-133">Kopya oluşturucu yazma</span><span class="sxs-lookup"><span data-stu-id="dba24-133">How to write a copy constructor</span></span>](./how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a><span data-ttu-id="dba24-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dba24-134">See also</span></span>

- [<span data-ttu-id="dba24-135">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="dba24-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="dba24-136">Sınıflar ve yapılar</span><span class="sxs-lookup"><span data-stu-id="dba24-136">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="dba24-137">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="dba24-137">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="dba24-138">static</span><span class="sxs-lookup"><span data-stu-id="dba24-138">static</span></span>](../../language-reference/keywords/static.md)
- [<span data-ttu-id="dba24-139">Başlatıcılar neden oluşturucular olarak ters sırada çalışıyor? Birinci bölüm</span><span class="sxs-lookup"><span data-stu-id="dba24-139">Why Do Initializers Run In The Opposite Order As Constructors? Part One</span></span>](/archive/blogs/ericlippert/why-do-initializers-run-in-the-opposite-order-as-constructors-part-one)
