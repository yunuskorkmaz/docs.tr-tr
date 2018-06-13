---
title: Nesne ve Koleksiyon Başlatıcıları (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
ms.openlocfilehash: ad8127bfdd7178051077e6f3fe75c777acf5d345
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33321954"
---
# <a name="object-and-collection-initializers-c-programming-guide"></a><span data-ttu-id="722cb-102">Nesne ve Koleksiyon Başlatıcıları (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="722cb-102">Object and Collection Initializers (C# Programming Guide)</span></span>
<span data-ttu-id="722cb-103">Nesne başlatıcıları, oluşturma zamanında ardından atama deyimleri satırları gelecek şekilde bir oluşturucu çağırmak zorunda kalmadan, bir nesnenin istediğiniz erişilebilir alanlarına veya özelliklerine değerler atamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="722cb-103">Object initializers let you assign values to any accessible fields or properties of an object at creation time without having to invoke a constructor followed by lines of assignment statements.</span></span> <span data-ttu-id="722cb-104">Nesne başlatıcı sözdizimi, bir oluşturucu için bağımsız değişkenler belirtmenize veya bağımsız değişkenleri (ve parantez sözdizimini) atmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="722cb-104">The object initializer syntax enables you to specify arguments for a constructor or omit the arguments (and parentheses syntax).</span></span>  <span data-ttu-id="722cb-105">Aşağıdaki örnekte bir adlandırılmış türüyle nesne Başlatıcı kullanmayı gösterir `Cat` ve varsayılan oluşturucu çağırmak nasıl.</span><span class="sxs-lookup"><span data-stu-id="722cb-105">The following example shows how to use an object initializer with a named type, `Cat` and how to invoke the default constructor.</span></span> <span data-ttu-id="722cb-106">Otomatik uygulanan özellikler kullanımına dikkat edin `Cat` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="722cb-106">Note the use of auto-implemented properties in the `Cat` class.</span></span> <span data-ttu-id="722cb-107">Daha fazla bilgi için bkz: [Auto-Implemented özellikleri](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="722cb-107">For more information, see [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>  
  
 [!code-csharp[csProgGuideLINQ#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_1.cs)]  
  
 [!code-csharp[csProgGuideLINQ#45](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_2.cs)] 
 
<span data-ttu-id="722cb-108">Nesne başlatıcıları sözdizimi örneği oluşturmanıza olanak tanır ve bundan sonra değişken ataması atanan özelliklerini ile yeni oluşturulan nesnenin atar.</span><span class="sxs-lookup"><span data-stu-id="722cb-108">The object initializers syntax allows you to create an instance, and after that it assigns the newly created object, with its assigned properties, to the variable in the assignment.</span></span>
  
## <a name="object-initializers-with-anonymous-types"></a><span data-ttu-id="722cb-109">Anonim türlerde Nesne Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="722cb-109">Object Initializers with anonymous types</span></span>  
 <span data-ttu-id="722cb-110">Nesne başlatıcıları herhangi bir bağlamda kullanılır ancak bunlar özellikle kullanışlı [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadeleri.</span><span class="sxs-lookup"><span data-stu-id="722cb-110">Although object initializers can be used in any context, they are especially useful in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="722cb-111">Sorgu ifadeleri olun, sık kullanılan [anonim türler](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), hangi yalnızca başlatılabilir nesne Başlatıcı kullanarak aşağıdaki bildiriminde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="722cb-111">Query expressions make frequent use of [anonymous types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), which can only be initialized by using an object initializer, as shown in the following declaration.</span></span>  
  
```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```  
  
 <span data-ttu-id="722cb-112">Anonim türler etkinleştirmek `select` yan tümcesinde bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadesi, değer ve şekli özgün değişebilir nesneler özgün sırasının nesnelerini dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="722cb-112">Anonymous types enable the `select` clause in a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression to transform objects of the original sequence into objects whose value and shape may differ from the original.</span></span> <span data-ttu-id="722cb-113">Bir sıradaki her bir nesneden elde edilen bilgilerin yalnızca bir kısmını depolamak isterseniz, bu kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="722cb-113">This is useful if you want to store only a part of the information from each object in a sequence.</span></span> <span data-ttu-id="722cb-114">Aşağıdaki örnekte, varsayımında bir product nesnesi (`p`) birçok alanları ve yöntemleri içerir ve, yalnızca nesnelerinin bir dizisi oluşturmada ilgilendiğiniz ürün adı ve birim fiyat içerebilir.</span><span class="sxs-lookup"><span data-stu-id="722cb-114">In the following example, assume that a product object (`p`) contains many fields and methods, and that you are only interested in creating a sequence of objects that contain the product name and the unit price.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_3.cs)]  
  
 <span data-ttu-id="722cb-115">Bu sorgunun yürütüldüğü zaman `productInfos` değişkeni erişilebilen nesnelerinin bir dizisi içerecek bir `foreach` Bu örnekte gösterildiği gibi deyimi:</span><span class="sxs-lookup"><span data-stu-id="722cb-115">When this query is executed, the `productInfos` variable will contain a sequence of objects that can be accessed in a `foreach` statement as shown in this example:</span></span>  
  
```csharp
foreach(var p in productInfos){...}  
```  
  
 <span data-ttu-id="722cb-116">Yeni anonim türdeki her bir nesnenin, orijinal nesnedeki özelliklerle veya alanlarla aynı adları alan iki genel özelliği vardır.</span><span class="sxs-lookup"><span data-stu-id="722cb-116">Each object in the new anonymous type has two public properties which receive the same names as the properties or fields in the original object.</span></span> <span data-ttu-id="722cb-117">Anonim bir tür oluştururken bir alanı de yeniden adlandırabilirsiniz; Aşağıdaki örnekte yeniden adlandırır `UnitPrice` alanı `Price`.</span><span class="sxs-lookup"><span data-stu-id="722cb-117">You can also rename a field when you are creating an anonymous type; the following example renames the `UnitPrice` field to `Price`.</span></span>  
  
```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```  
  
## <a name="object-initializers-with-nullable-types"></a><span data-ttu-id="722cb-118">Boş değer atanabilir tiplerde Nesne Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="722cb-118">Object initializers with nullable types</span></span>  
 <span data-ttu-id="722cb-119">Bir nesne başlatıcısını null yapılabilir bir yapıyla birlikte kullanmak bir derleme zamanı hatasıdır.</span><span class="sxs-lookup"><span data-stu-id="722cb-119">It is a compile-time error to use an object initializer with a nullable struct.</span></span>  
  
## <a name="collection-initializers"></a><span data-ttu-id="722cb-120">Koleksiyon başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="722cb-120">Collection initializers</span></span>  
 <span data-ttu-id="722cb-121">Koleksiyon başlatıcıları birini belirtmenize olanak tanır veya bu uygulayan bir koleksiyon başlattığınızda daha fazla öğesi başlatıcıları yazın <xref:System.Collections.IEnumerable> ve `Add` uygun imzalı bir örnek yöntemi veya bir genişletme yöntemi olarak.</span><span class="sxs-lookup"><span data-stu-id="722cb-121">Collection initializers let you specify one or more element initializers when you initialize a collection type that implements <xref:System.Collections.IEnumerable> and has `Add` with the appropriate signature as an instance method or an extension method.</span></span> <span data-ttu-id="722cb-122">Öğe başlatıcıları basit bir değer, bir ifade veya bir nesne başlatıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="722cb-122">The element initializers can be a simple value, an expression or an object initializer.</span></span> <span data-ttu-id="722cb-123">Koleksiyon Başlatıcısı kullanarak, birden fazla çağrı belirtmek zorunda değilsiniz `Add` kaynak kodunuzu; sınıfının yöntemi çağrıları derleyici ekler.</span><span class="sxs-lookup"><span data-stu-id="722cb-123">By using a collection initializer you do not have to specify multiple calls to the `Add` method of the class in your source code; the compiler adds the calls.</span></span>  
  
 <span data-ttu-id="722cb-124">Aşağıdaki örnekler, iki basit koleksiyon başlatıcısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="722cb-124">The following examples shows two simple collection initializers:</span></span>  
  
```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```  
  
 <span data-ttu-id="722cb-125">Aşağıdaki koleksiyon Başlatıcısı nesnelerin başlatmak için nesne başlatıcıları kullanan `Cat` bir önceki örnekte tanımlanan sınıfı.</span><span class="sxs-lookup"><span data-stu-id="722cb-125">The following collection initializer uses object initializers to initialize objects of the `Cat` class defined in a previous example.</span></span> <span data-ttu-id="722cb-126">Nesne başlatıcıların tek tek küme ayraçları içine alındığına ve virgüllerle ayrıldığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="722cb-126">Note that the individual object initializers are enclosed in braces and separated by commas.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_4.cs)]  
  
 <span data-ttu-id="722cb-127">Belirleyebileceğiniz [null](../../../csharp/language-reference/keywords/null.md) koleksiyon başlatıcısı bir öğe olarak durumunda koleksiyonun `Add` yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="722cb-127">You can specify [null](../../../csharp/language-reference/keywords/null.md) as an element in a collection initializer if the collection's `Add` method allows it.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_5.cs)]  
  
 <span data-ttu-id="722cb-128">Toplama dizin oluşturmayı destekliyorsa öğeleri dizine belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="722cb-128">You can specify indexed elements if the collection supports indexing.</span></span>  
  
```csharp
var numbers = new Dictionary<int, string> {   
    [7] = "seven",   
    [9] = "nine",   
    [13] = "thirteen"   
};  
```  
  
## <a name="examples"></a><span data-ttu-id="722cb-129">Örnekler</span><span class="sxs-lookup"><span data-stu-id="722cb-129">Examples</span></span>

 <span data-ttu-id="722cb-130">Aşağıdaki örnek, nesne ve koleksiyon başlatıcıları kavramlarını birleştirir.</span><span class="sxs-lookup"><span data-stu-id="722cb-130">The following example combines the concepts of object and collection initializers.</span></span>

 [!code-csharp[csProgGuideLINQ#46](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_6.cs)]  
 
 <span data-ttu-id="722cb-131">Aşağıdaki örnekte, uygulayan bir nesne gösterilen <xref:System.Collections.IEnumerable> içeren bir `Add` koleksiyon başlatıcıları imzaiçinkarşılıkgelenlistedekiöğebaşınabirdençoköğeilebirdençokparametreyöntemiylesağlar`Add` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="722cb-131">Shown in the following example, an object which implements <xref:System.Collections.IEnumerable> containing an `Add` method with multiple parameters allows for collection initializers with multiple elements per item in the list corresponding to the signature of the `Add` method.</span></span> 
 
 [!code-csharp[csProgGuideLINQ#84](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_7.cs)]
 
 <span data-ttu-id="722cb-132">`Add` yöntemleri kullanabilir `params` değişken sayıda bağımsız değişken aşağıdaki örnekte gösterildiği gibi olabilmesi için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="722cb-132">`Add` methods can use the `params` keyword to take a variable number of arguments as shown in the following example.</span></span> <span data-ttu-id="722cb-133">Bu örnek özel uygulama dizinler kullanılarak bir koleksiyonu başlatmak için bir dizin oluşturucu de ortaya koyar.</span><span class="sxs-lookup"><span data-stu-id="722cb-133">This example demonstrates the custom implementation of an indexer as well to initialize a collection using indexes.</span></span>
 
 [!code-csharp[csProgGuideLINQ#85](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_8.cs)]
 
## <a name="see-also"></a><span data-ttu-id="722cb-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="722cb-134">See Also</span></span>  
 [<span data-ttu-id="722cb-135">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="722cb-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="722cb-136">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="722cb-136">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="722cb-137">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="722cb-137">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
