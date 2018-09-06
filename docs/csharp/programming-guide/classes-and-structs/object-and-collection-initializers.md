---
title: Nesne ve Koleksiyon Başlatıcıları (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
ms.openlocfilehash: def33041c4202c80aad9f08d1ff8d9dbbc477061
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43892434"
---
# <a name="object-and-collection-initializers-c-programming-guide"></a><span data-ttu-id="5e0ad-102">Nesne ve Koleksiyon Başlatıcıları (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="5e0ad-102">Object and Collection Initializers (C# Programming Guide)</span></span>
<span data-ttu-id="5e0ad-103">Nesne başlatıcıları, oluşturma zamanında ardından atama deyimleri satırları gelecek şekilde bir oluşturucu çağırmak zorunda kalmadan, bir nesnenin istediğiniz erişilebilir alanlarına veya özelliklerine değerler atamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="5e0ad-103">Object initializers let you assign values to any accessible fields or properties of an object at creation time without having to invoke a constructor followed by lines of assignment statements.</span></span> <span data-ttu-id="5e0ad-104">Nesne başlatıcı sözdizimi, bir oluşturucu için bağımsız değişkenler belirtmenize veya bağımsız değişkenleri (ve parantez sözdizimini) atmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="5e0ad-104">The object initializer syntax enables you to specify arguments for a constructor or omit the arguments (and parentheses syntax).</span></span>  <span data-ttu-id="5e0ad-105">Aşağıdaki örnek, adlandırılmış bir türü ile bir nesne Başlatıcı kullanma işlemi gösterilmektedir `Cat` ve varsayılan oluşturucunun nasıl çağrılacağını.</span><span class="sxs-lookup"><span data-stu-id="5e0ad-105">The following example shows how to use an object initializer with a named type, `Cat` and how to invoke the default constructor.</span></span> <span data-ttu-id="5e0ad-106">Otomatik uygulanan özelliklerin kullanımına dikkat edin `Cat` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5e0ad-106">Note the use of auto-implemented properties in the `Cat` class.</span></span> <span data-ttu-id="5e0ad-107">Daha fazla bilgi için [Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="5e0ad-107">For more information, see [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>  
  
 [!code-csharp[csProgGuideLINQ#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_1.cs)]  
  
 [!code-csharp[csProgGuideLINQ#45](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_2.cs)] 
 
<span data-ttu-id="5e0ad-108">Nesne Başlatıcı sözdizimi örneği oluşturmanıza olanak sağlar ve sonra kendi atanan özelliklere sahip yeni oluşturulan nesne değişkeni ataması atar.</span><span class="sxs-lookup"><span data-stu-id="5e0ad-108">The object initializers syntax allows you to create an instance, and after that it assigns the newly created object, with its assigned properties, to the variable in the assignment.</span></span>
  
## <a name="object-initializers-with-anonymous-types"></a><span data-ttu-id="5e0ad-109">Anonim türlerde Nesne Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="5e0ad-109">Object Initializers with anonymous types</span></span>  
 <span data-ttu-id="5e0ad-110">Nesne başlatıcıları her bağlamda kullanılabilir olsa da, bunlar özellikle kullanışlı [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadelerinde.</span><span class="sxs-lookup"><span data-stu-id="5e0ad-110">Although object initializers can be used in any context, they are especially useful in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="5e0ad-111">Sorgu ifadeleri, sık sık kullanırlar [anonim türler](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), hangi yalnızca başlatılabilir bir nesne Başlatıcı kullanarak aşağıdaki bildirimde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="5e0ad-111">Query expressions make frequent use of [anonymous types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), which can only be initialized by using an object initializer, as shown in the following declaration.</span></span>  
  
```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```  
  
 <span data-ttu-id="5e0ad-112">Anonim türler etkinleştirme `select` yan tümcesinde bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu deyimi orijinal sıranın nesnelerini değeri ve şekli orijinalden farklı olabilir nesneleri dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="5e0ad-112">Anonymous types enable the `select` clause in a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression to transform objects of the original sequence into objects whose value and shape may differ from the original.</span></span> <span data-ttu-id="5e0ad-113">Bir sıradaki her bir nesneden elde edilen bilgilerin yalnızca bir kısmını depolamak isterseniz, bu kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="5e0ad-113">This is useful if you want to store only a part of the information from each object in a sequence.</span></span> <span data-ttu-id="5e0ad-114">Aşağıdaki örnekte, varsayımında bir ürün nesnesinin (`p`) birçok alan ve yöntem içerir ve, yalnızca sırası oluşturmakla ilgili bilgi sahibi olduğunuz ürün adını ve birim fiyatı içerir.</span><span class="sxs-lookup"><span data-stu-id="5e0ad-114">In the following example, assume that a product object (`p`) contains many fields and methods, and that you are only interested in creating a sequence of objects that contain the product name and the unit price.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_3.cs)]  
  
 <span data-ttu-id="5e0ad-115">Bu sorgu yürütüldüğünde `productInfos` değişkeni erişilebilen bir nesne sırası içerecektir bir `foreach` Bu örnekte gösterildiği gibi deyimi:</span><span class="sxs-lookup"><span data-stu-id="5e0ad-115">When this query is executed, the `productInfos` variable will contain a sequence of objects that can be accessed in a `foreach` statement as shown in this example:</span></span>  
  
```csharp
foreach(var p in productInfos){...}  
```  
  
 <span data-ttu-id="5e0ad-116">Yeni anonim türdeki her bir nesnenin, orijinal nesnedeki özelliklerle veya alanlarla aynı adları alan iki genel özelliği vardır.</span><span class="sxs-lookup"><span data-stu-id="5e0ad-116">Each object in the new anonymous type has two public properties which receive the same names as the properties or fields in the original object.</span></span> <span data-ttu-id="5e0ad-117">Ayrıca, anonim bir tür oluştururken bir alanı yeniden adlandırabilirsiniz; Aşağıdaki örnek yeniden adlandırır `UnitPrice` alanı `Price`.</span><span class="sxs-lookup"><span data-stu-id="5e0ad-117">You can also rename a field when you are creating an anonymous type; the following example renames the `UnitPrice` field to `Price`.</span></span>  
  
```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```  
  
## <a name="collection-initializers"></a><span data-ttu-id="5e0ad-118">Koleksiyon başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="5e0ad-118">Collection initializers</span></span>  
 <span data-ttu-id="5e0ad-119">Koleksiyon başlatıcıları bir belirtmenize olanak tanır veya daha fazla öğe başlatıcıları bir koleksiyon başlattığınızda uygulayan türü <xref:System.Collections.IEnumerable> ve `Add` uygun imzalı bir örnek yöntemi veya bir genişletme yöntemi olarak.</span><span class="sxs-lookup"><span data-stu-id="5e0ad-119">Collection initializers let you specify one or more element initializers when you initialize a collection type that implements <xref:System.Collections.IEnumerable> and has `Add` with the appropriate signature as an instance method or an extension method.</span></span> <span data-ttu-id="5e0ad-120">Öğe başlatıcıları basit bir değer, bir ifade veya bir nesne başlatıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="5e0ad-120">The element initializers can be a simple value, an expression or an object initializer.</span></span> <span data-ttu-id="5e0ad-121">Koleksiyon Başlatıcısı kullanarak, birden çok çağrı belirtmeniz gerekmez `Add` ; kaynak kodunuzdaki sınıfın yöntemi derleyici çağrıları ekler.</span><span class="sxs-lookup"><span data-stu-id="5e0ad-121">By using a collection initializer you do not have to specify multiple calls to the `Add` method of the class in your source code; the compiler adds the calls.</span></span>  
  
 <span data-ttu-id="5e0ad-122">Aşağıdaki örnekler, iki basit koleksiyon başlatıcısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="5e0ad-122">The following examples shows two simple collection initializers:</span></span>  
  
```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```  
  
 <span data-ttu-id="5e0ad-123">Aşağıdaki koleksiyon Başlatıcısı nesnelerini başlatmak için nesne başlatıcıları kullanır `Cat` önceki bir örnekte tanımlanan sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5e0ad-123">The following collection initializer uses object initializers to initialize objects of the `Cat` class defined in a previous example.</span></span> <span data-ttu-id="5e0ad-124">Nesne başlatıcıların tek tek küme ayraçları içine alındığına ve virgüllerle ayrıldığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="5e0ad-124">Note that the individual object initializers are enclosed in braces and separated by commas.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_4.cs)]  
  
 <span data-ttu-id="5e0ad-125">Belirtebileceğiniz [null](../../../csharp/language-reference/keywords/null.md) bir koleksiyon başlatıcısında bir öğe olarak varsa koleksiyonun `Add` yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e0ad-125">You can specify [null](../../../csharp/language-reference/keywords/null.md) as an element in a collection initializer if the collection's `Add` method allows it.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_5.cs)]  
  
 <span data-ttu-id="5e0ad-126">Koleksiyon dizin oluşturma destekliyorsa öğeleri dizine belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e0ad-126">You can specify indexed elements if the collection supports indexing.</span></span>  
  
```csharp
var numbers = new Dictionary<int, string> {   
    [7] = "seven",   
    [9] = "nine",   
    [13] = "thirteen"   
};  
```  
  
## <a name="examples"></a><span data-ttu-id="5e0ad-127">Örnekler</span><span class="sxs-lookup"><span data-stu-id="5e0ad-127">Examples</span></span>

 <span data-ttu-id="5e0ad-128">Aşağıdaki örnek, nesne ve koleksiyon başlatıcıları kavramlarını birleştirir.</span><span class="sxs-lookup"><span data-stu-id="5e0ad-128">The following example combines the concepts of object and collection initializers.</span></span>

 [!code-csharp[csProgGuideLINQ#46](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_6.cs)]  
 
 <span data-ttu-id="5e0ad-129">Uygulayan bir nesne aşağıdaki örnekte gösterilen <xref:System.Collections.IEnumerable> içeren bir `Add` imzasıiçinkarşılıkgelenöğebaşınabirdençoköğeiçerenkoleksiyonbaşlatıcılarıyöntemiilebirdençokparametresağlar`Add` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5e0ad-129">Shown in the following example, an object which implements <xref:System.Collections.IEnumerable> containing an `Add` method with multiple parameters allows for collection initializers with multiple elements per item in the list corresponding to the signature of the `Add` method.</span></span> 
 
 [!code-csharp[csProgGuideLINQ#84](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_7.cs)]
 
 <span data-ttu-id="5e0ad-130">`Add` yöntemleri kullanabilir `params` aşağıdaki örnekte gösterildiği gibi değişken sayıda bağımsız değişken almak için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="5e0ad-130">`Add` methods can use the `params` keyword to take a variable number of arguments as shown in the following example.</span></span> <span data-ttu-id="5e0ad-131">Bu örnekte, dizinleri kullanarak bir koleksiyonu başlatmak için bir dizin oluşturucu de özel uygulanışı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5e0ad-131">This example demonstrates the custom implementation of an indexer as well to initialize a collection using indexes.</span></span>
 
 [!code-csharp[csProgGuideLINQ#85](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_8.cs)]
 
## <a name="see-also"></a><span data-ttu-id="5e0ad-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5e0ad-132">See Also</span></span>

- [<span data-ttu-id="5e0ad-133">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5e0ad-133">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="5e0ad-134">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="5e0ad-134">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
- [<span data-ttu-id="5e0ad-135">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="5e0ad-135">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
