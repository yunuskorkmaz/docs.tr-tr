---
title: "LINQ'i Destekleyen C# Özellikleri"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2f5accb188e54e0d3e2b941832637ec33afc26b2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="c-features-that-support-linq"></a><span data-ttu-id="ada74-102">LINQ'i Destekleyen C# Özellikleri</span><span class="sxs-lookup"><span data-stu-id="ada74-102">C# Features That Support LINQ</span></span>
<span data-ttu-id="ada74-103">Aşağıdaki bölümde, C# 3.0 sürümünde sunulan yeni dil yapıları tanıtır.</span><span class="sxs-lookup"><span data-stu-id="ada74-103">The following section introduces new language constructs introduced in C# 3.0.</span></span> <span data-ttu-id="ada74-104">Bu yeni özellikleri tüm ile bir dereceye kullanılsa [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorguları, bunlar için sınırlı değildir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] ve bunları yararlı bulabileceğiniz bir bağlamda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ada74-104">Although these new features are all used to a degree with [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, they are not limited to [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] and can be used in any context where you find them useful.</span></span>  
  
## <a name="query-expressions"></a><span data-ttu-id="ada74-105">Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="ada74-105">Query Expressions</span></span>  
 <span data-ttu-id="ada74-106">Sorgu ifadeleri sorguya SQL ya da XQuery benzer bir tanımlayıcı sözdizimi IEnumerable koleksiyonları kullanın.</span><span class="sxs-lookup"><span data-stu-id="ada74-106">Queries expressions use a declarative syntax similar to SQL or XQuery to query over IEnumerable collections.</span></span> <span data-ttu-id="ada74-107">Derleme zamanı sorgu sözdizimi yöntem çağrılarını dönüştürülür bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] standart sorgu işleci genişletme yöntemleri sağlayıcının uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="ada74-107">At compile time query syntax is converted to method calls to a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provider's implementation of the standard query operator extension methods.</span></span> <span data-ttu-id="ada74-108">Uygulamaları denetim uygun ad belirterek kapsamındaki standart sorgu işleçleri bir `using` yönergesi.</span><span class="sxs-lookup"><span data-stu-id="ada74-108">Applications control the standard query operators that are in scope by specifying the appropriate namespace with a `using` directive.</span></span> <span data-ttu-id="ada74-109">Aşağıdaki sorgu ifadesi dizisini alır, bunları dizedeki ilk karakter göre gruplandırır ve grupları sıralar.</span><span class="sxs-lookup"><span data-stu-id="ada74-109">The following query expression takes an array of strings, groups them according to the first character in the string, and orders the groups.</span></span>  
  
```  
var query = from str in stringArray  
            group str by str[0] into stringGroup  
            orderby stringGroup.Key  
            select stringGroup;  
```  
  
 <span data-ttu-id="ada74-110">Daha fazla bilgi için bkz: [LINQ Sorgu ifadeleri](../../../../csharp/programming-guide/linq-query-expressions/index.md).</span><span class="sxs-lookup"><span data-stu-id="ada74-110">For more information, see [LINQ Query Expressions](../../../../csharp/programming-guide/linq-query-expressions/index.md).</span></span>  
  
## <a name="implicitly-typed-variables-var"></a><span data-ttu-id="ada74-111">Örtük olarak yazılan değişkenler (var)</span><span class="sxs-lookup"><span data-stu-id="ada74-111">Implicitly Typed Variables (var)</span></span>  
 <span data-ttu-id="ada74-112">Kullanabileceğiniz bildirme ve bir değişkeni başlatma zaman açıkça bir tür belirtmek yerine, [var](../../../../csharp/language-reference/keywords/var.md) Infer ve türünü atamak için aşağıda gösterildiği gibi görevlendirin değiştiricisi:</span><span class="sxs-lookup"><span data-stu-id="ada74-112">Instead of explicitly specifying a type when you declare and initialize a variable, you can use the [var](../../../../csharp/language-reference/keywords/var.md) modifier to instruct the compiler to infer and assign the type, as shown here:</span></span>  
  
```  
var number = 5;  
var name = "Virginia";  
var query = from str in stringArray  
            where str[0] == 'm'  
            select str;  
```  
  
 <span data-ttu-id="ada74-113">Olarak bildirilen değişkenlerin `var` yalnızca olarak kesin türü türünü açıkça belirtmek değişkenleri olarak belirtilmiş olan.</span><span class="sxs-lookup"><span data-stu-id="ada74-113">Variables declared as `var` are just as strongly-typed as variables whose type you specify explicitly.</span></span> <span data-ttu-id="ada74-114">Kullanımını `var` anonim türler, ancak oluşturmak mümkün kullanılabilir herhangi bir yerel değişken için yapar.</span><span class="sxs-lookup"><span data-stu-id="ada74-114">The use of `var` makes it possible to create anonymous types, but it can be used for any local variable.</span></span> <span data-ttu-id="ada74-115">Diziler de örtülü yazma ile bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ada74-115">Arrays can also be declared with implicit typing.</span></span>  
  
 <span data-ttu-id="ada74-116">Daha fazla bilgi için bkz: [örtük olarak yazılan yerel değişkenler](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="ada74-116">For more information, see [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
## <a name="object-and-collection-initializers"></a><span data-ttu-id="ada74-117">Nesne ve Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="ada74-117">Object and Collection Initializers</span></span>  
 <span data-ttu-id="ada74-118">Nesne ve koleksiyon başlatıcıları nesne için açıkça bir oluşturucu çağırmadan nesneleri başlatmak mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="ada74-118">Object and collection initializers make it possible to initialize objects without explicitly calling a constructor for the object.</span></span> <span data-ttu-id="ada74-119">Bunlar veri kaynağını yeni bir veri türüne projenizin başlatıcıları genellikle sorgu ifadelerinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ada74-119">Initializers are typically used in query expressions when they project the source data into a new data type.</span></span> <span data-ttu-id="ada74-120">Adlı bir sınıf varsayılarak `Customer` ortak `Name` ve `Phone` özellikleri, nesne Başlatıcı olduğu gibi aşağıdaki kodu kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="ada74-120">Assuming a class named `Customer` with public `Name` and `Phone` properties, the object initializer can be used as in the following code:</span></span>  
  
```  
Customer cust = new Customer { Name = "Mike", Phone = "555-1212" };  
```  
  
 <span data-ttu-id="ada74-121">Daha fazla bilgi için bkz: [nesne ve koleksiyon başlatıcıları](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="ada74-121">For more information, see [Object and Collection Initializers](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
## <a name="anonymous-types"></a><span data-ttu-id="ada74-122">Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="ada74-122">Anonymous Types</span></span>  
 <span data-ttu-id="ada74-123">Anonim bir tür derleyici tarafından oluşturulan ve tür adı yalnızca derleyiciye kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ada74-123">An anonymous type is constructed by the compiler and the type name is only available to the compiler.</span></span> <span data-ttu-id="ada74-124">Anonim türler türü adlı ayrı bir tanımlamak zorunda kalmadan sorgu sonucu geçici olarak özelliklerinde kümesini gruplamak için kolay bir yol sağlamak.</span><span class="sxs-lookup"><span data-stu-id="ada74-124">Anonymous types provide a convenient way to group a set of properties temporarily in a query result without having to define a separate named type.</span></span> <span data-ttu-id="ada74-125">Anonim türler, aşağıda gösterildiği gibi yeni bir ifade ve nesne Başlatıcı başlatılır:</span><span class="sxs-lookup"><span data-stu-id="ada74-125">Anonymous types are initialized with a new expression and an object initializer, as shown here:</span></span>  
  
```  
select new {name = cust.Name, phone = cust.Phone};  
```  
  
 <span data-ttu-id="ada74-126">Daha fazla bilgi için bkz: [anonim türler](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="ada74-126">For more information, see [Anonymous Types](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
## <a name="extension-methods"></a><span data-ttu-id="ada74-127">Uzantı Metotları</span><span class="sxs-lookup"><span data-stu-id="ada74-127">Extension Methods</span></span>  
 <span data-ttu-id="ada74-128">Bir genişletme yöntemi türü ile ilişkilendirilebilir bir statik yöntem, böylelikle türü üzerinde örnek yöntemi değilmiş gibi çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="ada74-128">An extension method is a static method that can be associated with a type, so that it can be called as if it were an instance method on the type.</span></span> <span data-ttu-id="ada74-129">Bu özellik, etkin, "yeni yöntemi var olan türlere bunları gerçekte değiştirmeden eklemek," sağlar.</span><span class="sxs-lookup"><span data-stu-id="ada74-129">This feature enables you to, in effect, "add" new methods to existing types without actually modifying them.</span></span> <span data-ttu-id="ada74-130">Standart sorgu işleçleri sağlamak genişletme yöntemleri kümesidir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] işlevselliği uygulayan herhangi bir türü için sorgu <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="ada74-130">The standard query operators are a set of extension methods that provide [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query functionality for any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
 <span data-ttu-id="ada74-131">Daha fazla bilgi için bkz: [genişletme yöntemleri](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="ada74-131">For more information, see [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>  
  
## <a name="lambda-expressions"></a><span data-ttu-id="ada74-132">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="ada74-132">Lambda Expressions</span></span>  
 <span data-ttu-id="ada74-133">Lambda ifadesi = kullanan bir satır içi işlevidir > ayırmak için işleci giriş parametreleri işlevi gövdesinden ve temsilci ya da bir ifade ağacına derleme zamanında dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="ada74-133">A lambda expression is an inline function that uses the => operator to separate input parameters from the function body and can be converted at compile time to a delegate or an expression tree.</span></span> <span data-ttu-id="ada74-134">İçinde [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] doğrudan yöntem çağrılarını standart sorgu işleçleri için yaptığınızda programlama, lambda ifadeleri karşılaşırsınız.</span><span class="sxs-lookup"><span data-stu-id="ada74-134">In [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] programming, you will encounter lambda expressions when you make direct method calls to the standard query operators.</span></span>  
  
 <span data-ttu-id="ada74-135">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="ada74-135">For more information, see:</span></span>  
  
-   [<span data-ttu-id="ada74-136">Anonim İşlevler</span><span class="sxs-lookup"><span data-stu-id="ada74-136">Anonymous Functions</span></span>](../../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)  
  
-   [<span data-ttu-id="ada74-137">Lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="ada74-137">Lambda Expressions</span></span>](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
  
-   [<span data-ttu-id="ada74-138">İfade ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="ada74-138">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
  
## <a name="auto-implemented-properties"></a><span data-ttu-id="ada74-139">Otomatik Uygulanan Özellikler</span><span class="sxs-lookup"><span data-stu-id="ada74-139">Auto-Implemented Properties</span></span>  
 <span data-ttu-id="ada74-140">Otomatik uygulanan özellikler özellik bildirimi daha kısa hale getirir.</span><span class="sxs-lookup"><span data-stu-id="ada74-140">Auto-implemented properties make property-declaration more concise.</span></span> <span data-ttu-id="ada74-141">Aşağıdaki örnekte gösterildiği gibi bir özelliği bildirme, derleyici özellik Set'yordamı erişilemez dışında bir özel, anonim yedekleme alanını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ada74-141">When you declare a property as shown in the following example, the compiler will create a private, anonymous backing field that is not accessible except through the property getter and setter.</span></span>  
  
```  
public string Name {get; set;}  
```  
  
 <span data-ttu-id="ada74-142">Daha fazla bilgi için bkz: [Auto-Implemented özellikleri](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="ada74-142">For more information, see [Auto-Implemented Properties](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ada74-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ada74-143">See Also</span></span>  
 [<span data-ttu-id="ada74-144">Dil ile tümleşik sorgu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="ada74-144">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)
