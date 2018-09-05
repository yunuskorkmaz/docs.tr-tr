---
title: LINQ'i Destekleyen C# Özellikleri
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
ms.openlocfilehash: c617b2d7b56618867fe92cbe1d9ee04aa4c3ab64
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43661288"
---
# <a name="c-features-that-support-linq"></a><span data-ttu-id="62e62-102">LINQ'i Destekleyen C# Özellikleri</span><span class="sxs-lookup"><span data-stu-id="62e62-102">C# Features That Support LINQ</span></span>
<span data-ttu-id="62e62-103">Aşağıdaki bölümde, C# 3.0 sürümünde sunulan yeni dil yapıları sunar.</span><span class="sxs-lookup"><span data-stu-id="62e62-103">The following section introduces new language constructs introduced in C# 3.0.</span></span> <span data-ttu-id="62e62-104">Bu yeni özelliklerin tümünü bir dereceye kullanılsa [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgular olmadıkları için sınırlı [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] ve burada, bunları kullanışlı her bağlamda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="62e62-104">Although these new features are all used to a degree with [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, they are not limited to [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] and can be used in any context where you find them useful.</span></span>  
  
## <a name="query-expressions"></a><span data-ttu-id="62e62-105">Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="62e62-105">Query Expressions</span></span>  
 <span data-ttu-id="62e62-106">Sorgu ifadeleri IEnumerable koleksiyonları sorgulamak için SQL veya XQuery benzer bir tanımlayıcı sözdizimi kullanın.</span><span class="sxs-lookup"><span data-stu-id="62e62-106">Query expressions use a declarative syntax similar to SQL or XQuery to query over IEnumerable collections.</span></span> <span data-ttu-id="62e62-107">Derleme zamanı sorgu sözdizimi yöntem çağrıları için dönüştürülür bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sağlayıcısının uygulaması standart sorgu işleci genişletme yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="62e62-107">At compile time query syntax is converted to method calls to a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provider's implementation of the standard query operator extension methods.</span></span> <span data-ttu-id="62e62-108">Uygulama Denetim uygun ad belirterek kapsamındaki standart sorgu işleçleri bir `using` yönergesi.</span><span class="sxs-lookup"><span data-stu-id="62e62-108">Applications control the standard query operators that are in scope by specifying the appropriate namespace with a `using` directive.</span></span> <span data-ttu-id="62e62-109">Aşağıdaki sorgu ifadesi dizisini alır, bunları dizedeki ilk karakter göre gruplandırır ve grupları sıralar.</span><span class="sxs-lookup"><span data-stu-id="62e62-109">The following query expression takes an array of strings, groups them according to the first character in the string, and orders the groups.</span></span>  
  
```csharp  
var query = from str in stringArray  
            group str by str[0] into stringGroup  
            orderby stringGroup.Key  
            select stringGroup;  
```  
  
 <span data-ttu-id="62e62-110">Daha fazla bilgi için [LINQ Sorgu ifadeleri](../../../../csharp/programming-guide/linq-query-expressions/index.md).</span><span class="sxs-lookup"><span data-stu-id="62e62-110">For more information, see [LINQ Query Expressions](../../../../csharp/programming-guide/linq-query-expressions/index.md).</span></span>  
  
## <a name="implicitly-typed-variables-var"></a><span data-ttu-id="62e62-111">Örtük olarak yazılan değişkenler (var)</span><span class="sxs-lookup"><span data-stu-id="62e62-111">Implicitly Typed Variables (var)</span></span>  
 <span data-ttu-id="62e62-112">Kullanabileceğiniz bildirme ve bir değişkeni başlatarak, açıkça bir tür belirtmek yerine, [var](../../../../csharp/language-reference/keywords/var.md) çıkarır ve atamak için burada gösterildiği gibi derleyicisinin değiştiricisi:</span><span class="sxs-lookup"><span data-stu-id="62e62-112">Instead of explicitly specifying a type when you declare and initialize a variable, you can use the [var](../../../../csharp/language-reference/keywords/var.md) modifier to instruct the compiler to infer and assign the type, as shown here:</span></span>  
  
```csharp  
var number = 5;  
var name = "Virginia";  
var query = from str in stringArray  
            where str[0] == 'm'  
            select str;  
```  
  
 <span data-ttu-id="62e62-113">Olarak bildirilen değişkenler `var` yalnızca olarak türünü açıkça belirtmeniz değişkenleri olarak kesin olan.</span><span class="sxs-lookup"><span data-stu-id="62e62-113">Variables declared as `var` are just as strongly-typed as variables whose type you specify explicitly.</span></span> <span data-ttu-id="62e62-114">Kullanımını `var` anonim türler, ancak oluşturmak mümkün kullanılabileceği için yalnızca yerel değişkenler yapar.</span><span class="sxs-lookup"><span data-stu-id="62e62-114">The use of `var` makes it possible to create anonymous types, but it can be used only for local variables.</span></span> <span data-ttu-id="62e62-115">Diziler de örtülü yazma ile bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="62e62-115">Arrays can also be declared with implicit typing.</span></span>  
  
 <span data-ttu-id="62e62-116">Daha fazla bilgi için [örtük olarak yazılan yerel değişkenler](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="62e62-116">For more information, see [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
## <a name="object-and-collection-initializers"></a><span data-ttu-id="62e62-117">Nesne ve Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="62e62-117">Object and Collection Initializers</span></span>  
 <span data-ttu-id="62e62-118">Nesne ve koleksiyon başlatıcıları nesne için açıkça bir oluşturucu çağırmaya gerek kalmadan nesneleri başlatmak mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="62e62-118">Object and collection initializers make it possible to initialize objects without explicitly calling a constructor for the object.</span></span> <span data-ttu-id="62e62-119">Bunlar kaynak verileri yeni bir veri türüne projenizin başlatıcılar genellikle sorgu ifadelerinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="62e62-119">Initializers are typically used in query expressions when they project the source data into a new data type.</span></span> <span data-ttu-id="62e62-120">Adlı bir sınıf varsayılarak `Customer` ortak `Name` ve `Phone` nesne Başlatıcı özellikleri, aşağıdaki kodda gösterildiği gibi kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="62e62-120">Assuming a class named `Customer` with public `Name` and `Phone` properties, the object initializer can be used as in the following code:</span></span>  
  
```csharp  
Customer cust = new Customer { Name = "Mike", Phone = "555-1212" };  
```  
  
 <span data-ttu-id="62e62-121">Daha fazla bilgi için [nesne ve koleksiyon başlatıcıları](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="62e62-121">For more information, see [Object and Collection Initializers](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
## <a name="anonymous-types"></a><span data-ttu-id="62e62-122">Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="62e62-122">Anonymous Types</span></span>  
 <span data-ttu-id="62e62-123">Anonim bir tür derleyici tarafından oluşturulmuş olan ve yalnızca tür adı derleyici için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="62e62-123">An anonymous type is constructed by the compiler and the type name is only available to the compiler.</span></span> <span data-ttu-id="62e62-124">Anonim türler bir sorgu sonucu özelliklerinde geçici olarak bir dizi türü adlı ayrı bir tanımlamak zorunda kalmadan gruplandırmak için kullanışlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="62e62-124">Anonymous types provide a convenient way to group a set of properties temporarily in a query result without having to define a separate named type.</span></span> <span data-ttu-id="62e62-125">Anonim türler, burada gösterildiği gibi bir new ifadesi ve bir nesne Başlatıcı ile başlatılır:</span><span class="sxs-lookup"><span data-stu-id="62e62-125">Anonymous types are initialized with a new expression and an object initializer, as shown here:</span></span>  
  
```  
select new {name = cust.Name, phone = cust.Phone};  
```  
  
 <span data-ttu-id="62e62-126">Daha fazla bilgi için [anonim türler](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="62e62-126">For more information, see [Anonymous Types](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
## <a name="extension-methods"></a><span data-ttu-id="62e62-127">Uzantı Metotları</span><span class="sxs-lookup"><span data-stu-id="62e62-127">Extension Methods</span></span>  
 <span data-ttu-id="62e62-128">Böylece türünde bir örnek yöntemi gibi çağrılabilen bir genişletme yöntemi, bir tür ile ilişkilendirilebilir bir statik yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="62e62-128">An extension method is a static method that can be associated with a type, so that it can be called as if it were an instance method on the type.</span></span> <span data-ttu-id="62e62-129">Bu özellik, aslında "yeni yöntemler varolan türleri için bunları gerçekten değiştirmeden eklemek," sağlar.</span><span class="sxs-lookup"><span data-stu-id="62e62-129">This feature enables you to, in effect, "add" new methods to existing types without actually modifying them.</span></span> <span data-ttu-id="62e62-130">Standart sorgu işleçleri sağlayan genişletme yöntemleri kümesidir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] işlevselliğini uygulayan herhangi bir türü için sorgu <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="62e62-130">The standard query operators are a set of extension methods that provide [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query functionality for any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
 <span data-ttu-id="62e62-131">Daha fazla bilgi için [genişletme yöntemleri](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="62e62-131">For more information, see [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>  
  
## <a name="lambda-expressions"></a><span data-ttu-id="62e62-132">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="62e62-132">Lambda Expressions</span></span>  
 <span data-ttu-id="62e62-133">Bir lambda ifadesi = kullanan bir satır içi işlevdir > işleci ayırmak için giriş parametreleri işlevi gövdesinden ve derleme zamanında bir temsilci veya ifade ağacı dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="62e62-133">A lambda expression is an inline function that uses the => operator to separate input parameters from the function body and can be converted at compile time to a delegate or an expression tree.</span></span> <span data-ttu-id="62e62-134">İçinde [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] standart sorgu işleçleri için doğrudan yöntem çağrıları yaptığınızda programlama, lambda ifadeleri karşılaşırsınız.</span><span class="sxs-lookup"><span data-stu-id="62e62-134">In [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] programming, you will encounter lambda expressions when you make direct method calls to the standard query operators.</span></span>  
  
 <span data-ttu-id="62e62-135">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="62e62-135">For more information, see:</span></span>  
  
-   [<span data-ttu-id="62e62-136">Anonim İşlevler</span><span class="sxs-lookup"><span data-stu-id="62e62-136">Anonymous Functions</span></span>](../../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)  
  
-   [<span data-ttu-id="62e62-137">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="62e62-137">Lambda Expressions</span></span>](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
  
-   [<span data-ttu-id="62e62-138">İfade ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="62e62-138">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
  
## <a name="auto-implemented-properties"></a><span data-ttu-id="62e62-139">Otomatik Uygulanan Özellikler</span><span class="sxs-lookup"><span data-stu-id="62e62-139">Auto-Implemented Properties</span></span>  
 <span data-ttu-id="62e62-140">Otomatik uygulanan özellikler özellik bildirimini daha kısa yapın.</span><span class="sxs-lookup"><span data-stu-id="62e62-140">Auto-implemented properties make property-declaration more concise.</span></span> <span data-ttu-id="62e62-141">Aşağıdaki örnekte gösterildiği gibi bir özellik bildirdiğinizde, derleyici özellik alıcı ve ayarlayıcı erişilemeyen dışında özel, anonim destek alanı oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="62e62-141">When you declare a property as shown in the following example, the compiler will create a private, anonymous backing field that is not accessible except through the property getter and setter.</span></span>  
  
```csharp  
public string Name {get; set;}  
```  
  
 <span data-ttu-id="62e62-142">Daha fazla bilgi için [Implemented Properties](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="62e62-142">For more information, see [Auto-Implemented Properties](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62e62-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="62e62-143">See Also</span></span>

- [<span data-ttu-id="62e62-144">Dil ile tümleşik sorgu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="62e62-144">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)
