---
title: Oluşturucular - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 05/05/2017
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
ms.openlocfilehash: e88cc9b36f64a559105620359f4c163978cf9d8c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54692265"
---
# <a name="constructors-c-programming-guide"></a><span data-ttu-id="f86fe-102">Oluşturucular (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="f86fe-102">Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="f86fe-103">Her bir [sınıfı](../../../csharp/language-reference/keywords/class.md) veya [yapı](../../../csharp/language-reference/keywords/struct.md) olan oluşturulan, kendi Oluşturucu çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f86fe-103">Whenever a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="f86fe-104">Farklı bağımsız değişkenler almayan birden çok Oluşturucu, bir sınıf veya yapı olabilir.</span><span class="sxs-lookup"><span data-stu-id="f86fe-104">A class or struct may have multiple constructors that take different arguments.</span></span> <span data-ttu-id="f86fe-105">Oluşturucular, esnek ve kolay okunur kod yazma, örnekleme sınırlandırmak ve varsayılan değerlerini ayarlamak Programcı etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="f86fe-105">Constructors enable the programmer to set default values, limit instantiation, and write code that is flexible and easy to read.</span></span> <span data-ttu-id="f86fe-106">Daha fazla bilgi ve örnekler için bkz. [oluşturucuları kullanarak](../../../csharp/programming-guide/classes-and-structs/using-constructors.md) ve [örnek oluşturucuları](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="f86fe-106">For more information and examples, see [Using Constructors](../../../csharp/programming-guide/classes-and-structs/using-constructors.md) and [Instance Constructors](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span></span>  

## <a name="default-constructors"></a><span data-ttu-id="f86fe-107">Varsayılan Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="f86fe-107">Default constructors</span></span>
  
<span data-ttu-id="f86fe-108">Sınıfınız için bir oluşturucu sağlamazsanız, C# nesnesini başlatır ve üye değişkenleri için varsayılan değerleri, bağlantısında listelendiği gibi ayarlar. varsayılan olarak bir tane oluşturur [varsayılan değerler tablosu](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="f86fe-108">If you don't provide a constructor for your class, C# creates one by default that instantiates the object and sets member variables to the default values as listed in the [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="f86fe-109">Yapınızı için bir oluşturucu sağlamazsanız, C# dayanan bir *örtülü varsayılan bir oluşturucuya* listelenen her alanda bir değer türü varsayılan değerine otomatik olarak başlatmak için [varsayılan değerler tablosu](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="f86fe-109">If you don't provide a constructor for your struct, C# relies on an *implicit default constructor* to automatically initialize each field of a value type to its default value as listed in the [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="f86fe-110">Daha fazla bilgi ve örnekler için bkz. [örnek oluşturucuları](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="f86fe-110">For more information and examples, see [Instance Constructors](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span></span>  

## <a name="constructor-syntax"></a><span data-ttu-id="f86fe-111">Oluşturucu sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f86fe-111">Constructor syntax</span></span>

<span data-ttu-id="f86fe-112">Bir oluşturucu kendi türünün adı ile aynı adı olan bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="f86fe-112">A constructor is a method whose name is the same as the name of its type.</span></span> <span data-ttu-id="f86fe-113">Yöntem imzası yöntem adı ve kendi parametre listesi ' dönüş türü içermez.</span><span class="sxs-lookup"><span data-stu-id="f86fe-113">Its method signature includes only the method name and its parameter list; it does not include a return type.</span></span> <span data-ttu-id="f86fe-114">Aşağıdaki örnekte adlı bir sınıf için oluşturucu `Person`.</span><span class="sxs-lookup"><span data-stu-id="f86fe-114">The following example shows the constructor for a class named `Person`.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

<span data-ttu-id="f86fe-115">Tek bir deyimde bir oluşturucu uygulanabilir, kullanabileceğiniz bir [ifade gövdesi tanımına](../statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="f86fe-115">If a constructor can be implemented as a single statement, you can use an [expression body definition](../statements-expressions-operators/expression-bodied-members.md).</span></span> <span data-ttu-id="f86fe-116">Aşağıdaki örnekte tanımlayan bir `Location` sınıfı, Oluşturucusu olan tek bir dize parametresi adlı *adı*.</span><span class="sxs-lookup"><span data-stu-id="f86fe-116">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="f86fe-117">Bağımsız değişkeni için ifade gövdesi tanımına atar `locationName` alan.</span><span class="sxs-lookup"><span data-stu-id="f86fe-117">The expression body definition assigns the argument to the `locationName` field.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a><span data-ttu-id="f86fe-118">Statik oluşturucular</span><span class="sxs-lookup"><span data-stu-id="f86fe-118">Static constructors</span></span>

<span data-ttu-id="f86fe-119">Önceki örneklerde, yeni nesne oluşturma tüm gösterilen örnek oluşturucuları vardır.</span><span class="sxs-lookup"><span data-stu-id="f86fe-119">The previous examples have all shown instance constructors, which create a new object.</span></span> <span data-ttu-id="f86fe-120">Bir sınıf veya yapı, türün statik üyeleri başlatan bir statik Oluşturucu da olabilir.</span><span class="sxs-lookup"><span data-stu-id="f86fe-120">A class or struct can also have a static constructor, which initializes static members of the type.</span></span>  <span data-ttu-id="f86fe-121">Statik oluşturucular parametresiz.</span><span class="sxs-lookup"><span data-stu-id="f86fe-121">Static constructors are parameterless.</span></span> <span data-ttu-id="f86fe-122">Statik alanları başlatmak için bir statik Oluşturucu sağlamazsanız, C# derleyicisi bağlantısında listelendiği gibi statik alanları varsayılan değerlerine başlatır varsayılan statik Oluşturucu sağlayacak [varsayılan değerler tablosu](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="f86fe-122">If you don't provide a static constructor to initialize static fields, the C# compiler will supply a default static constructor that initializes static fields to their default value as listed in the [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> 

<span data-ttu-id="f86fe-123">Aşağıdaki örnek, statik bir alanı başlatmak için bir statik Oluşturucu kullanır.</span><span class="sxs-lookup"><span data-stu-id="f86fe-123">The following example uses a static constructor to initialize a static field.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]  

<span data-ttu-id="f86fe-124">Aşağıdaki örnekte gösterildiği gibi bir statik Oluşturucu bir ifade gövdesi tanımıyla de tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f86fe-124">You can also define a static constructor with an expression body definition, as the following example shows.</span></span> 

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]  

<span data-ttu-id="f86fe-125">Daha fazla bilgi ve örnekler için bkz. [statik oluşturucular](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="f86fe-125">For more information and examples, see [Static Constructors](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f86fe-126">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f86fe-126">In This Section</span></span>  
 [<span data-ttu-id="f86fe-127">Oluşturucuları Kullanma</span><span class="sxs-lookup"><span data-stu-id="f86fe-127">Using Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)  
  
 [<span data-ttu-id="f86fe-128">Örnek Oluşturucuları</span><span class="sxs-lookup"><span data-stu-id="f86fe-128">Instance Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)  
  
 [<span data-ttu-id="f86fe-129">Özel Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="f86fe-129">Private Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/private-constructors.md)  
  
 [<span data-ttu-id="f86fe-130">Statik Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="f86fe-130">Static Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)  
  
 [<span data-ttu-id="f86fe-131">Nasıl yapılır: Kopya Oluşturucu yazma</span><span class="sxs-lookup"><span data-stu-id="f86fe-131">How to: Write a Copy Constructor</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a><span data-ttu-id="f86fe-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f86fe-132">See also</span></span>

- [<span data-ttu-id="f86fe-133">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f86fe-133">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="f86fe-134">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="f86fe-134">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="f86fe-135">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="f86fe-135">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
- [<span data-ttu-id="f86fe-136">static</span><span class="sxs-lookup"><span data-stu-id="f86fe-136">static</span></span>](../../../csharp/language-reference/keywords/static.md)
- [<span data-ttu-id="f86fe-137">Başlatıcılar neden olarak oluşturucular ters sırada çalıştırılır? Bölüm bir</span><span class="sxs-lookup"><span data-stu-id="f86fe-137">Why Do Initializers Run In The Opposite Order As Constructors? Part One</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2008/02/15/why-do-initializers-run-in-the-opposite-order-as-constructors-part-one)
