---
title: Oluşturucular- C# Programlama Kılavuzu
ms.date: 05/05/2017
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
ms.openlocfilehash: 465dbb9120e6e81e5ef216c34dc6a92283956033
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964669"
---
# <a name="constructors-c-programming-guide"></a><span data-ttu-id="9ef65-102">Oluşturucular (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="9ef65-102">Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="9ef65-103">Bir [sınıf](../../language-reference/keywords/class.md) veya [Yapı](../../language-reference/keywords/struct.md) oluşturulduğunda, Oluşturucusu çağırılır.</span><span class="sxs-lookup"><span data-stu-id="9ef65-103">Whenever a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/keywords/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="9ef65-104">Bir sınıf veya yapının farklı bağımsız değişkenler alan birden çok Oluşturucusu olabilir.</span><span class="sxs-lookup"><span data-stu-id="9ef65-104">A class or struct may have multiple constructors that take different arguments.</span></span> <span data-ttu-id="9ef65-105">Oluşturucular, programcının varsayılan değerleri ayarlama, örnek oluşturmayı sınırlandırma ve esnek ve okunması kolay bir kod yazma olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="9ef65-105">Constructors enable the programmer to set default values, limit instantiation, and write code that is flexible and easy to read.</span></span> <span data-ttu-id="9ef65-106">Daha fazla bilgi ve örnek için bkz. oluşturucular ve [örnek oluşturucular](./instance-constructors.md) [kullanma](./using-constructors.md) .</span><span class="sxs-lookup"><span data-stu-id="9ef65-106">For more information and examples, see [Using Constructors](./using-constructors.md) and [Instance Constructors](./instance-constructors.md).</span></span>  

## <a name="parameterless-constructors"></a><span data-ttu-id="9ef65-107">Parametresiz oluşturucular</span><span class="sxs-lookup"><span data-stu-id="9ef65-107">Parameterless constructors</span></span>
  
<span data-ttu-id="9ef65-108">Sınıfınız için bir Oluşturucu sağlamazsanız, C# varsayılan olarak, nesneyi örnekleyen ve üye değişkenlerini varsayılan değerlere ayarlar, örneğin [varsayılan C# ](../../language-reference/builtin-types/default-values.md) değerleri makalede listelendiği şekilde oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9ef65-108">If you don't provide a constructor for your class, C# creates one by default that instantiates the object and sets member variables to the default values as listed in the [Default values of C# types](../../language-reference/builtin-types/default-values.md) article.</span></span> <span data-ttu-id="9ef65-109">Yapı aboneliğiniz için bir Oluşturucu sağlamazsanız, C# her bir alanı varsayılan değerine otomatik olarak başlatmak için örtük olarak parametresiz bir *oluşturucuya* bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="9ef65-109">If you don't provide a constructor for your struct, C# relies on an *implicit parameterless constructor* to automatically initialize each field to its default value.</span></span> <span data-ttu-id="9ef65-110">Daha fazla bilgi ve örnek için bkz. [örnek oluşturucular](instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="9ef65-110">For more information and examples, see [Instance constructors](instance-constructors.md).</span></span>  

## <a name="constructor-syntax"></a><span data-ttu-id="9ef65-111">Oluşturucu sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9ef65-111">Constructor syntax</span></span>

<span data-ttu-id="9ef65-112">Oluşturucu, adı türünün adı ile aynı olan bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="9ef65-112">A constructor is a method whose name is the same as the name of its type.</span></span> <span data-ttu-id="9ef65-113">Yöntemi imzasında yalnızca Yöntem adı ve parametre listesi bulunur; dönüş türü içermez.</span><span class="sxs-lookup"><span data-stu-id="9ef65-113">Its method signature includes only the method name and its parameter list; it does not include a return type.</span></span> <span data-ttu-id="9ef65-114">Aşağıdaki örnek, `Person`adlı bir sınıf için oluşturucuyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9ef65-114">The following example shows the constructor for a class named `Person`.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

<span data-ttu-id="9ef65-115">Bir Oluşturucu tek bir deyim olarak uygulan, bir [ifade gövdesi tanımı](../statements-expressions-operators/expression-bodied-members.md)kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ef65-115">If a constructor can be implemented as a single statement, you can use an [expression body definition](../statements-expressions-operators/expression-bodied-members.md).</span></span> <span data-ttu-id="9ef65-116">Aşağıdaki örnek, oluşturucusunun *adı*adlı tek bir dize parametresine sahip bir `Location` sınıfını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9ef65-116">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="9ef65-117">İfade gövdesi tanımı, `locationName` alanına bağımsız değişkenini atar.</span><span class="sxs-lookup"><span data-stu-id="9ef65-117">The expression body definition assigns the argument to the `locationName` field.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a><span data-ttu-id="9ef65-118">Statik oluşturucular</span><span class="sxs-lookup"><span data-stu-id="9ef65-118">Static constructors</span></span>

<span data-ttu-id="9ef65-119">Önceki örneklerde, yeni bir nesne oluşturan tüm gösterilen örnek oluşturucuları vardır.</span><span class="sxs-lookup"><span data-stu-id="9ef65-119">The previous examples have all shown instance constructors, which create a new object.</span></span> <span data-ttu-id="9ef65-120">Bir sınıf veya yapı, türün statik üyelerini Başlatan statik bir oluşturucuya de sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="9ef65-120">A class or struct can also have a static constructor, which initializes static members of the type.</span></span>  <span data-ttu-id="9ef65-121">Statik oluşturucular parametresiz.</span><span class="sxs-lookup"><span data-stu-id="9ef65-121">Static constructors are parameterless.</span></span> <span data-ttu-id="9ef65-122">Statik alanları başlatmak için statik bir Oluşturucu sağlamazsanız, C# derleyici varsayılan değer [ C# türleri](../../language-reference/builtin-types/default-values.md) makalesinde listelenen statik alanları varsayılan değerlerine başlatır.</span><span class="sxs-lookup"><span data-stu-id="9ef65-122">If you don't provide a static constructor to initialize static fields, the C# compiler initializes static fields to their default value as listed in the [Default values of C# types](../../language-reference/builtin-types/default-values.md) article.</span></span>

<span data-ttu-id="9ef65-123">Aşağıdaki örnek, statik bir alanı başlatmak için statik bir Oluşturucu kullanır.</span><span class="sxs-lookup"><span data-stu-id="9ef65-123">The following example uses a static constructor to initialize a static field.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]  

<span data-ttu-id="9ef65-124">Aşağıdaki örnekte gösterildiği gibi, bir ifade gövdesi tanımıyla bir statik oluşturucu da tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ef65-124">You can also define a static constructor with an expression body definition, as the following example shows.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]  

<span data-ttu-id="9ef65-125">Daha fazla bilgi ve örnek için bkz. [statik oluşturucular](./static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="9ef65-125">For more information and examples, see [Static Constructors](./static-constructors.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9ef65-126">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="9ef65-126">In This Section</span></span>  
 [<span data-ttu-id="9ef65-127">Oluşturucuları Kullanma</span><span class="sxs-lookup"><span data-stu-id="9ef65-127">Using Constructors</span></span>](./using-constructors.md)  
  
 [<span data-ttu-id="9ef65-128">Örnek Oluşturucuları</span><span class="sxs-lookup"><span data-stu-id="9ef65-128">Instance Constructors</span></span>](./instance-constructors.md)  
  
 [<span data-ttu-id="9ef65-129">Özel Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="9ef65-129">Private Constructors</span></span>](./private-constructors.md)  
  
 [<span data-ttu-id="9ef65-130">Statik Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="9ef65-130">Static Constructors</span></span>](./static-constructors.md)  
  
 [<span data-ttu-id="9ef65-131">Kopya Oluşturucu yazma</span><span class="sxs-lookup"><span data-stu-id="9ef65-131">How to write a copy constructor</span></span>](./how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a><span data-ttu-id="9ef65-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ef65-132">See also</span></span>

- [<span data-ttu-id="9ef65-133">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9ef65-133">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9ef65-134">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="9ef65-134">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="9ef65-135">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="9ef65-135">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="9ef65-136">static</span><span class="sxs-lookup"><span data-stu-id="9ef65-136">static</span></span>](../../language-reference/keywords/static.md)
- [<span data-ttu-id="9ef65-137">Başlatıcılar neden oluşturucular olarak ters sırada çalışıyor? Birinci bölüm</span><span class="sxs-lookup"><span data-stu-id="9ef65-137">Why Do Initializers Run In The Opposite Order As Constructors? Part One</span></span>](https://docs.microsoft.com/archive/blogs/ericlippert/why-do-initializers-run-in-the-opposite-order-as-constructors-part-one)
