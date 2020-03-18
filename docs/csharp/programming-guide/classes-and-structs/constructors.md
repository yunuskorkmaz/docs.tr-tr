---
title: Constructors - C# Programlama Kılavuzu
ms.date: 05/05/2017
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
ms.openlocfilehash: 8eedfaed111f01cc2ec55a2f42df66d4588bd42f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399793"
---
# <a name="constructors-c-programming-guide"></a><span data-ttu-id="fdd64-102">Oluşturucular (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="fdd64-102">Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="fdd64-103">Bir [sınıf](../../language-reference/keywords/class.md) veya [yapı](../../language-reference/builtin-types/struct.md) oluşturulduğunda, oluşturucusu çağrılır.</span><span class="sxs-lookup"><span data-stu-id="fdd64-103">Whenever a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/builtin-types/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="fdd64-104">Bir sınıf veya yapı, farklı bağımsız değişkenler alan birden çok oluşturucuya sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="fdd64-104">A class or struct may have multiple constructors that take different arguments.</span></span> <span data-ttu-id="fdd64-105">Oluşturucular, programcının varsayılan değerleri ayarlamasını, anlık değeri sınırlamasını ve esnek ve okunması kolay kod yazmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="fdd64-105">Constructors enable the programmer to set default values, limit instantiation, and write code that is flexible and easy to read.</span></span> <span data-ttu-id="fdd64-106">Daha fazla bilgi ve örnekler için, Yapı [oluşturucuları](./using-constructors.md) ve Örnek [Oluşturucuları](./instance-constructors.md)Kullanma'ya bakın.</span><span class="sxs-lookup"><span data-stu-id="fdd64-106">For more information and examples, see [Using Constructors](./using-constructors.md) and [Instance Constructors](./instance-constructors.md).</span></span>  

## <a name="parameterless-constructors"></a><span data-ttu-id="fdd64-107">Parametresiz yapıcılar</span><span class="sxs-lookup"><span data-stu-id="fdd64-107">Parameterless constructors</span></span>
  
<span data-ttu-id="fdd64-108">Sınıfınız için bir oluşturucu sağlamazsanız, C# varsayılan olarak nesneyi anında belirleyen ve üye değişkenleri [C# türlerinin varsayılan değerlerinde](../../language-reference/builtin-types/default-values.md) listelenen varsayılan değerlere ayarlayan bir tane oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fdd64-108">If you don't provide a constructor for your class, C# creates one by default that instantiates the object and sets member variables to the default values as listed in the [Default values of C# types](../../language-reference/builtin-types/default-values.md) article.</span></span> <span data-ttu-id="fdd64-109">Yapınız için bir oluşturucu sağlamazsanız, C# her alanı varsayılan değerine otomatik olarak başlatması için *örtük bir parametresiz oluşturucuya* güvenir.</span><span class="sxs-lookup"><span data-stu-id="fdd64-109">If you don't provide a constructor for your struct, C# relies on an *implicit parameterless constructor* to automatically initialize each field to its default value.</span></span> <span data-ttu-id="fdd64-110">Daha fazla bilgi ve örnekler için [Bkz. Örnek oluşturucular.](instance-constructors.md)</span><span class="sxs-lookup"><span data-stu-id="fdd64-110">For more information and examples, see [Instance constructors](instance-constructors.md).</span></span>  

## <a name="constructor-syntax"></a><span data-ttu-id="fdd64-111">Yapıcı sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fdd64-111">Constructor syntax</span></span>

<span data-ttu-id="fdd64-112">Oluşturucu, adı türünün adıile aynı olan bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="fdd64-112">A constructor is a method whose name is the same as the name of its type.</span></span> <span data-ttu-id="fdd64-113">Yöntem imzası yalnızca yöntem adını ve parametre listesini içerir; bir iade türü içermez.</span><span class="sxs-lookup"><span data-stu-id="fdd64-113">Its method signature includes only the method name and its parameter list; it does not include a return type.</span></span> <span data-ttu-id="fdd64-114">Aşağıdaki örnek, adlı bir sınıfın `Person`oluşturucusu gösterir.</span><span class="sxs-lookup"><span data-stu-id="fdd64-114">The following example shows the constructor for a class named `Person`.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

<span data-ttu-id="fdd64-115">Bir oluşturucu tek bir deyim olarak uygulanabilirse, bir [ifade gövdesi tanımı](../statements-expressions-operators/expression-bodied-members.md)kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fdd64-115">If a constructor can be implemented as a single statement, you can use an [expression body definition](../statements-expressions-operators/expression-bodied-members.md).</span></span> <span data-ttu-id="fdd64-116">Aşağıdaki örnek, oluşturucu `Location` *adı*adlı tek bir dize parametresi olan bir sınıf tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fdd64-116">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="fdd64-117">İfade gövdesi tanımı bağımsız değişkeni `locationName` alana atar.</span><span class="sxs-lookup"><span data-stu-id="fdd64-117">The expression body definition assigns the argument to the `locationName` field.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a><span data-ttu-id="fdd64-118">Statik yapıcılar</span><span class="sxs-lookup"><span data-stu-id="fdd64-118">Static constructors</span></span>

<span data-ttu-id="fdd64-119">Önceki örneklerin tümü, yeni bir nesne oluşturan örnek oluşturucuları göstermiştir.</span><span class="sxs-lookup"><span data-stu-id="fdd64-119">The previous examples have all shown instance constructors, which create a new object.</span></span> <span data-ttu-id="fdd64-120">Bir sınıf veya yapı, türün statik üyelerini baş harfe çeken statik bir oluşturucuya da sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="fdd64-120">A class or struct can also have a static constructor, which initializes static members of the type.</span></span>  <span data-ttu-id="fdd64-121">Statik yapıcılar parametresizdir.</span><span class="sxs-lookup"><span data-stu-id="fdd64-121">Static constructors are parameterless.</span></span> <span data-ttu-id="fdd64-122">Statik alanları başlatmak için statik bir oluşturucu sağlamazsanız, C# derleyicisi statik alanları [C# türleri makalesinin Varsayılan değerlerinde](../../language-reference/builtin-types/default-values.md) listelenen varsayılan değerlerine amerler.</span><span class="sxs-lookup"><span data-stu-id="fdd64-122">If you don't provide a static constructor to initialize static fields, the C# compiler initializes static fields to their default value as listed in the [Default values of C# types](../../language-reference/builtin-types/default-values.md) article.</span></span>

<span data-ttu-id="fdd64-123">Aşağıdaki örnek, statik bir alanı başlatmak için statik bir oluşturucu kullanır.</span><span class="sxs-lookup"><span data-stu-id="fdd64-123">The following example uses a static constructor to initialize a static field.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]  

<span data-ttu-id="fdd64-124">Aşağıdaki örnekte görüldüğü gibi, ifade gövdesi tanımına sahip statik bir oluşturucu da tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fdd64-124">You can also define a static constructor with an expression body definition, as the following example shows.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]  

<span data-ttu-id="fdd64-125">Daha fazla bilgi ve örnekler için [Statik Oluşturucular'a](./static-constructors.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="fdd64-125">For more information and examples, see [Static Constructors](./static-constructors.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fdd64-126">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="fdd64-126">In This Section</span></span>  
 [<span data-ttu-id="fdd64-127">Oluşturucuları Kullanma</span><span class="sxs-lookup"><span data-stu-id="fdd64-127">Using Constructors</span></span>](./using-constructors.md)  
  
 [<span data-ttu-id="fdd64-128">Örnek Oluşturucuları</span><span class="sxs-lookup"><span data-stu-id="fdd64-128">Instance Constructors</span></span>](./instance-constructors.md)  
  
 [<span data-ttu-id="fdd64-129">Özel Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="fdd64-129">Private Constructors</span></span>](./private-constructors.md)  
  
 [<span data-ttu-id="fdd64-130">Statik Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="fdd64-130">Static Constructors</span></span>](./static-constructors.md)  
  
 [<span data-ttu-id="fdd64-131">Kopya oluşturucu nasıl yazılır?</span><span class="sxs-lookup"><span data-stu-id="fdd64-131">How to write a copy constructor</span></span>](./how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a><span data-ttu-id="fdd64-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fdd64-132">See also</span></span>

- [<span data-ttu-id="fdd64-133">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="fdd64-133">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="fdd64-134">Sınıflar ve Structs</span><span class="sxs-lookup"><span data-stu-id="fdd64-134">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="fdd64-135">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="fdd64-135">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="fdd64-136">Statik</span><span class="sxs-lookup"><span data-stu-id="fdd64-136">static</span></span>](../../language-reference/keywords/static.md)
- [<span data-ttu-id="fdd64-137">Neden Başharfler yapıcılar olarak Ters Sırada Çalışır? Birinci Bölüm</span><span class="sxs-lookup"><span data-stu-id="fdd64-137">Why Do Initializers Run In The Opposite Order As Constructors? Part One</span></span>](https://docs.microsoft.com/archive/blogs/ericlippert/why-do-initializers-run-in-the-opposite-order-as-constructors-part-one)
