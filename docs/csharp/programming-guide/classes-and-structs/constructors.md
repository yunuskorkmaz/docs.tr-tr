---
title: "Oluşturucular (C# Programlama Kılavuzu)"
ms.date: 05/05/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 65c50311548667ab5fdc685b70b6ab9e88376067
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="constructors-c-programming-guide"></a><span data-ttu-id="ac63e-102">Oluşturucular (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="ac63e-102">Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="ac63e-103">Her bir [sınıfı](../../../csharp/language-reference/keywords/class.md) veya [yapısı](../../../csharp/language-reference/keywords/struct.md) olan oluşturulan kurucusu çağrılır.</span><span class="sxs-lookup"><span data-stu-id="ac63e-103">Whenever a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="ac63e-104">Sınıfta veya yapı farklı bağımsız değişkenler almayan birden çok oluşturucular olabilir.</span><span class="sxs-lookup"><span data-stu-id="ac63e-104">A class or struct may have multiple constructors that take different arguments.</span></span> <span data-ttu-id="ac63e-105">Oluşturucular örneklemesi sınırlamak ve esnek ve kolay okumak kod yazma varsayılan değerlerini ayarlamak Programcı etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="ac63e-105">Constructors enable the programmer to set default values, limit instantiation, and write code that is flexible and easy to read.</span></span> <span data-ttu-id="ac63e-106">Daha fazla bilgi ve örnekler için bkz: [kullanarak oluşturucular](../../../csharp/programming-guide/classes-and-structs/using-constructors.md) ve [örnek oluşturucuları](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="ac63e-106">For more information and examples, see [Using Constructors](../../../csharp/programming-guide/classes-and-structs/using-constructors.md) and [Instance Constructors](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span></span>  

## <a name="default-constructors"></a><span data-ttu-id="ac63e-107">Varsayılan Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="ac63e-107">Default constructors</span></span>
  
<span data-ttu-id="ac63e-108">Sınıfı için bir oluşturucu sağlamazsanız, C# bir nesne oluşturur ve üye değişkenleri için varsayılan değerleri içinde listelenen ayarlar varsayılan olarak oluşturur [varsayılan değerler tablosu](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="ac63e-108">If you don't provide a constructor for your class, C# creates one by default that instantiates the object and sets member variables to the default values as listed in the [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="ac63e-109">Yapı için bir oluşturucu sağlamazsanız, C# dayanan bir *örtük varsayılan oluşturucu* içinde listelenen her bir alan bir değer türü için varsayılan değer otomatik olarak başlatmak için [varsayılan değerler tablosu](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="ac63e-109">If you don't provide a constructor for your struct, C# relies on an *implicit default constructor* to automatically initialize each field of a value type to its default value as listed in the [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="ac63e-110">Daha fazla bilgi ve örnekler için bkz: [örnek oluşturucuları](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="ac63e-110">For more information and examples, see [Instance Constructors](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span></span>  

## <a name="constructor-syntax"></a><span data-ttu-id="ac63e-111">Oluşturucu sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ac63e-111">Constructor syntax</span></span>

<span data-ttu-id="ac63e-112">Bir oluşturucu kendi türünün adı ile aynı adı olan bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="ac63e-112">A constructor is a method whose name is the same as the name of its type.</span></span> <span data-ttu-id="ac63e-113">Yöntem imzası yalnızca yöntemi adı ve parametre listesi içerir; dönüş türü içermez.</span><span class="sxs-lookup"><span data-stu-id="ac63e-113">Its method signature includes only the method name and its parameter list; it does not include a return type.</span></span> <span data-ttu-id="ac63e-114">Aşağıdaki örnek adlı bir sınıf oluşturucusu gösterir `Person`.</span><span class="sxs-lookup"><span data-stu-id="ac63e-114">The following example shows the constructor for a class named `Person`.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

<span data-ttu-id="ac63e-115">Bir oluşturucu tek bir deyimde uygulanabilir, kullanabileceğiniz bir [ifade gövdesi tanımı](../statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="ac63e-115">If a constructor can be implemented as a single statement, you can use an [expression body definition](../statements-expressions-operators/expression-bodied-members.md).</span></span> <span data-ttu-id="ac63e-116">Aşağıdaki örnek tanımlayan bir `Location` sınıfı, bir oluşturucuya sahip tek bir dize adlı parametre *adı*.</span><span class="sxs-lookup"><span data-stu-id="ac63e-116">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="ac63e-117">Bağımsız değişkeni ifadesi gövde tanımı atar `locationName` alan.</span><span class="sxs-lookup"><span data-stu-id="ac63e-117">The expression body definition assigns the argument to the `locationName` field.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a><span data-ttu-id="ac63e-118">Statik oluşturucular</span><span class="sxs-lookup"><span data-stu-id="ac63e-118">Static constructors</span></span>

<span data-ttu-id="ac63e-119">Önceki örneklerde, yeni nesne oluşturma tüm gösterilen örnek oluşturucuları vardır.</span><span class="sxs-lookup"><span data-stu-id="ac63e-119">The previous examples have all shown instance constructors, which create a new object.</span></span> <span data-ttu-id="ac63e-120">Ayrıca bir sınıf veya yapı türün statik üyeleri başlatır statik Oluşturucu olabilir.</span><span class="sxs-lookup"><span data-stu-id="ac63e-120">A class or struct can also have a static constructor, which initializes static members of the type.</span></span>  <span data-ttu-id="ac63e-121">Statik oluşturucular parametresiz.</span><span class="sxs-lookup"><span data-stu-id="ac63e-121">Static constructors are parameterless.</span></span> <span data-ttu-id="ac63e-122">Statik alanları başlatmak için statik bir oluşturucu sağlamazsanız, C# Derleyici içinde listelenen statik alanları varsayılan değerlerine başlatır varsayılan statik Oluşturucu sağlayacak [varsayılan değerler tablosu](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="ac63e-122">If you don't provide a static constructor to initialize static fields, the C# compiler will supply a default static constructor that initializes static fields to their default value as listed in the [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> 

<span data-ttu-id="ac63e-123">Aşağıdaki örnek, statik bir alanı başlatmak için bir statik oluşturucusunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="ac63e-123">The following example uses a static constructor to initialize a static field.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]  

<span data-ttu-id="ac63e-124">Ayrıca aşağıdaki örnekte gösterildiği gibi bir ifade gövdesi tanımı statik bir oluşturucu tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac63e-124">You can also define a static constructor with an expression body definition, as the following example shows.</span></span> 

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]  

<span data-ttu-id="ac63e-125">Daha fazla bilgi ve örnekler için bkz: [statik oluşturucular](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="ac63e-125">For more information and examples, see [Static Constructors](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ac63e-126">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ac63e-126">In This Section</span></span>  
 [<span data-ttu-id="ac63e-127">Oluşturucular Kullanma</span><span class="sxs-lookup"><span data-stu-id="ac63e-127">Using Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)  
  
 [<span data-ttu-id="ac63e-128">Örnek oluşturucuları</span><span class="sxs-lookup"><span data-stu-id="ac63e-128">Instance Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)  
  
 [<span data-ttu-id="ac63e-129">Özel oluşturucular</span><span class="sxs-lookup"><span data-stu-id="ac63e-129">Private Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/private-constructors.md)  
  
 [<span data-ttu-id="ac63e-130">Statik oluşturucular</span><span class="sxs-lookup"><span data-stu-id="ac63e-130">Static Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)  
  
 [<span data-ttu-id="ac63e-131">Nasıl yapılır: kopya Oluşturucu yazma</span><span class="sxs-lookup"><span data-stu-id="ac63e-131">How to: Write a Copy Constructor</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a><span data-ttu-id="ac63e-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ac63e-132">See Also</span></span>  
 [<span data-ttu-id="ac63e-133">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ac63e-133">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ac63e-134">Sınıflar ve yapılar</span><span class="sxs-lookup"><span data-stu-id="ac63e-134">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="ac63e-135">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="ac63e-135">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
 [<span data-ttu-id="ac63e-136">statik</span><span class="sxs-lookup"><span data-stu-id="ac63e-136">static</span></span>](../../../csharp/language-reference/keywords/static.md)  
 [<span data-ttu-id="ac63e-137">Başlatıcılar neden oluşturucular ters sırada çalışır? Bölüm bir</span><span class="sxs-lookup"><span data-stu-id="ac63e-137">Why Do Initializers Run In The Opposite Order As Constructors? Part One</span></span>](http://go.microsoft.com/fwlink/?LinkId=112374)
