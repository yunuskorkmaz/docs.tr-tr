---
title: Nesne ve Toplama Başlangıç - C# Programlama Kılavuzu
ms.date: 12/19/2018
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
ms.openlocfilehash: ae8741e2f29db0a470ad8d3b121375fbdeaff0d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170201"
---
# <a name="object-and-collection-initializers-c-programming-guide"></a><span data-ttu-id="7527f-102">Nesne ve Koleksiyon Başlatıcıları (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="7527f-102">Object and Collection Initializers (C# Programming Guide)</span></span>

<span data-ttu-id="7527f-103">C# bir nesneyi veya koleksiyonu anında gerçekleştirmenizi ve üye atamaları tek bir deyimde gerçekleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7527f-103">C# lets you instantiate an object or collection and perform member assignments in a single statement.</span></span>

## <a name="object-initializers"></a><span data-ttu-id="7527f-104">Nesne başharfleri</span><span class="sxs-lookup"><span data-stu-id="7527f-104">Object initializers</span></span>

<span data-ttu-id="7527f-105">Nesne başlatıcıları, oluşturma zamanında ardından atama deyimleri satırları gelecek şekilde bir oluşturucu çağırmak zorunda kalmadan, bir nesnenin istediğiniz erişilebilir alanlarına veya özelliklerine değerler atamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="7527f-105">Object initializers let you assign values to any accessible fields or properties of an object at creation time without having to invoke a constructor followed by lines of assignment statements.</span></span> <span data-ttu-id="7527f-106">Nesne başlatıcı sözdizimi, bir oluşturucu için bağımsız değişkenler belirtmenize veya bağımsız değişkenleri (ve parantez sözdizimini) atmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="7527f-106">The object initializer syntax enables you to specify arguments for a constructor or omit the arguments (and parentheses syntax).</span></span>  <span data-ttu-id="7527f-107">Aşağıdaki örnek, adlandırılmış bir türe sahip bir `Cat` nesne başlatıcısının nasıl kullanılacağını ve parametresiz oluşturucuyu nasıl çağırılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7527f-107">The following example shows how to use an object initializer with a named type, `Cat` and how to invoke the parameterless constructor.</span></span> <span data-ttu-id="7527f-108">Sınıfta otomatik olarak uygulanan özelliklerin `Cat` kullanımına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="7527f-108">Note the use of auto-implemented properties in the `Cat` class.</span></span> <span data-ttu-id="7527f-109">Daha fazla bilgi için otomatik [olarak uygulanan özellikler'e](auto-implemented-properties.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="7527f-109">For more information, see [Auto-Implemented Properties](auto-implemented-properties.md).</span></span>  
  
[!code-csharp[ObjectInitializer1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#CatDeclaration)]  
[!code-csharp[ObjectInitializer1a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ObjectPropertyInitialization)]  

<span data-ttu-id="7527f-110">Nesne baş harfleri sözdizimi bir örnek oluşturmanıza olanak sağlar ve bundan sonra yeni oluşturulan nesneyi atanan özellikleriyle atamadaki değişkene atar.</span><span class="sxs-lookup"><span data-stu-id="7527f-110">The object initializers syntax allows you to create an instance, and after that it assigns the newly created object, with its assigned properties, to the variable in the assignment.</span></span>

<span data-ttu-id="7527f-111">C# 6 ile başlayarak, nesne başlatıcıları alanları ve özellikleri atamaya ek olarak dizin leyiciler ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="7527f-111">Starting with C# 6, object initializers can set indexers, in addition to assigning fields and properties.</span></span> <span data-ttu-id="7527f-112">Bu temel `Matrix` sınıfı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="7527f-112">Consider this basic `Matrix` class:</span></span>

[!code-csharp[ObjectInitializer2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixDeclaration)]  

<span data-ttu-id="7527f-113">Kimlik matrisini aşağıdaki kodla başharfe alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7527f-113">You could initialize the identity matrix with the following code:</span></span>

[!code-csharp[ObjectInitializer2a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixInitialization)]  

<span data-ttu-id="7527f-114">Erişilebilir bir ayarlayıcı içeren erişilebilir dizinleyici, bağımsız değişken sayısı veya türüne bakılmaksızın nesne baş harferindeki ifadelerden biri olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7527f-114">Any accessible indexer that contains an accessible setter can be used as one of the expressions in an object initializer, regardless of the number or types of arguments.</span></span> <span data-ttu-id="7527f-115">Dizin bağımsız değişkenleri atamanın sol tarafını oluşturur ve değer ifadenin sağ tarafıdır.</span><span class="sxs-lookup"><span data-stu-id="7527f-115">The index arguments form the left side of the assignment, and the value is the right side of the expression.</span></span>  <span data-ttu-id="7527f-116">Örneğin, uygun dizinleyicileri varsa `IndexersExample` bunların tümü geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="7527f-116">For example, these are all valid if `IndexersExample` has the appropriate indexers:</span></span>

```csharp
var thing = new IndexersExample {
    name = "object one",
    [1] = '1',
    [2] = '4',
    [3] = '9',
    Size = Math.PI,
    ['C',4] = "Middle C"
}
```

<span data-ttu-id="7527f-117">Önceki kodun derlemesi için, `IndexersExample` tür aşağıdaki üyelere sahip olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="7527f-117">For the preceding code to compile, the `IndexersExample` type must have the following members:</span></span>

```csharp
public string name;
public double Size { set { ... }; }
public char this[int i] { set { ... }; }
public string this[char c, int i] {  set { ... }; }
```

## <a name="object-initializers-with-anonymous-types"></a><span data-ttu-id="7527f-118">Anonim türlerde Nesne Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="7527f-118">Object Initializers with anonymous types</span></span>

<span data-ttu-id="7527f-119">Nesne baş harfleri herhangi bir bağlamda kullanılabilse de, özellikle LINQ sorgu ifadelerinde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="7527f-119">Although object initializers can be used in any context, they are especially useful in LINQ query expressions.</span></span> <span data-ttu-id="7527f-120">Sorgu ifadeleri, aşağıdaki bildirimde gösterildiği gibi, yalnızca bir nesne baş harfer kullanılarak başharfe bünyebilen [anonim türleri](./anonymous-types.md)sık sık kullanır.</span><span class="sxs-lookup"><span data-stu-id="7527f-120">Query expressions make frequent use of [anonymous types](./anonymous-types.md), which can only be initialized by using an object initializer, as shown in the following declaration.</span></span>  

```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```

<span data-ttu-id="7527f-121">Adsız türler, linq sorgu ifadesindeki `select` yan tümcenin, özgün dizinin nesnelerini değeri ve şekli orijinalden farklı olabilecek nesnelere dönüştürmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="7527f-121">Anonymous types enable the `select` clause in a LINQ query expression to transform objects of the original sequence into objects whose value and shape may differ from the original.</span></span> <span data-ttu-id="7527f-122">Bir sıradaki her bir nesneden elde edilen bilgilerin yalnızca bir kısmını depolamak isterseniz, bu kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="7527f-122">This is useful if you want to store only a part of the information from each object in a sequence.</span></span> <span data-ttu-id="7527f-123">Aşağıdaki örnekte, bir ürün nesnesinin (`p`) birçok alan ve yöntem içerdiğini ve yalnızca ürün adını ve birim fiyatı içeren bir nesne dizisi oluşturmakla ilgilendiğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="7527f-123">In the following example, assume that a product object (`p`) contains many fields and methods, and that you are only interested in creating a sequence of objects that contain the product name and the unit price.</span></span>  
  
[!code-csharp[ObjectInitializer3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#AnonymousUse)]  

<span data-ttu-id="7527f-124">Bu sorgu yürütüldüğünde, `productInfos` değişken bu örnekte gösterildiği gibi bir `foreach` deyimde erişilebilen bir nesne dizisi içerir:</span><span class="sxs-lookup"><span data-stu-id="7527f-124">When this query is executed, the `productInfos` variable will contain a sequence of objects that can be accessed in a `foreach` statement as shown in this example:</span></span>  

```csharp
foreach(var p in productInfos){...}  
```

<span data-ttu-id="7527f-125">Yeni adsız türdeki her nesnenin, özgün nesnedeki özellikler veya alanlar la aynı adları alan iki ortak özelliği vardır.</span><span class="sxs-lookup"><span data-stu-id="7527f-125">Each object in the new anonymous type has two public properties that receive the same names as the properties or fields in the original object.</span></span> <span data-ttu-id="7527f-126">Anonim bir tür oluştururken alanı yeniden adlandırabilirsiniz; aşağıdaki örnek alanı `UnitPrice` . `Price`</span><span class="sxs-lookup"><span data-stu-id="7527f-126">You can also rename a field when you are creating an anonymous type; the following example renames the `UnitPrice` field to `Price`.</span></span>  

```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```

## <a name="collection-initializers"></a><span data-ttu-id="7527f-127">Koleksiyon başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="7527f-127">Collection initializers</span></span>

<span data-ttu-id="7527f-128">Koleksiyon başlatılması, bir örnek yöntemi veya uzantı yöntemi olarak uygun imzayı <xref:System.Collections.IEnumerable> uygulayan `Add` ve sahip olan bir koleksiyon türünü başharfe aldığınızda bir veya daha fazla öğe başlatılmasını belirtmenize izin verirken.</span><span class="sxs-lookup"><span data-stu-id="7527f-128">Collection initializers let you specify one or more element initializers when you initialize a collection type that implements <xref:System.Collections.IEnumerable> and has `Add` with the appropriate signature as an instance method or an extension method.</span></span> <span data-ttu-id="7527f-129">Öğe initializaları basit bir değer, bir ifade veya nesne baş harfer olabilir.</span><span class="sxs-lookup"><span data-stu-id="7527f-129">The element initializers can be a simple value, an expression, or an object initializer.</span></span> <span data-ttu-id="7527f-130">Bir koleksiyon başlatma kullanarak, birden çok çağrı belirtmeniz gerekmez; derleyici aramaları otomatik olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="7527f-130">By using a collection initializer, you do not have to specify multiple calls; the compiler adds the calls automatically.</span></span>  
  
<span data-ttu-id="7527f-131">Aşağıdaki örnekte iki basit koleksiyon başharfleri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7527f-131">The following example shows two simple collection initializers:</span></span>  

```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```

<span data-ttu-id="7527f-132">Aşağıdaki koleksiyon başharfleri, önceki örnekte tanımlanan `Cat` sınıfın nesnelerini başlatmak için nesne başharfleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="7527f-132">The following collection initializer uses object initializers to initialize objects of the `Cat` class defined in a previous example.</span></span> <span data-ttu-id="7527f-133">Nesne başlatıcıların tek tek küme ayraçları içine alındığına ve virgüllerle ayrıldığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="7527f-133">Note that the individual object initializers are enclosed in braces and separated by commas.</span></span>  
  
[!code-csharp[ListInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitializer)]  
  
<span data-ttu-id="7527f-134">Koleksiyonun [null](../../language-reference/keywords/null.md) `Add` yöntemi izin veriyorsa, koleksiyon başlatılmasında bir öğe olarak null belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7527f-134">You can specify [null](../../language-reference/keywords/null.md) as an element in a collection initializer if the collection's `Add` method allows it.</span></span>  
  
[!code-csharp[ListInitializerNull](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitialerWithNull)]  
  
 <span data-ttu-id="7527f-135">Koleksiyon okuma /yazma dizini oluşturmayı destekliyorsa dizinlenmiş öğeleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7527f-135">You can specify indexed elements if the collection supports read / write indexing.</span></span>
  
[!code-csharp[DictionaryInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryIndexerInitializer)]  

<span data-ttu-id="7527f-136">Önceki örnek değerleri ayarlamak <xref:System.Collections.Generic.Dictionary%602.Item(%600)> için çağıran kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7527f-136">The preceding sample generates code that calls the <xref:System.Collections.Generic.Dictionary%602.Item(%600)> to set the values.</span></span> <span data-ttu-id="7527f-137">C# 6'dan önce, aşağıdaki sözdizimini kullanarak sözlükleri ve diğer bağdaştırıcı kapları başharfe dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7527f-137">Before C# 6, you could initialize dictionaries and other associative containers using the following syntax.</span></span> <span data-ttu-id="7527f-138">Dizinleyici sözdizimi yerine, parantez ve atama ile, birden çok değere sahip bir nesne kullanır:</span><span class="sxs-lookup"><span data-stu-id="7527f-138">Notice that instead of indexer syntax, with parentheses and an assignment, it uses an object with multiple values:</span></span>

[!code-csharp[DictionaryAddInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryAddInitializer)]  

<span data-ttu-id="7527f-139">Bu baş harförneği, üç öğeyi sözlüğün içine eklemek için çağırır. <xref:System.Collections.Generic.Dictionary%602.Add(%600,%601)></span><span class="sxs-lookup"><span data-stu-id="7527f-139">This initializer example calls <xref:System.Collections.Generic.Dictionary%602.Add(%600,%601)> to add the three items into the dictionary.</span></span> <span data-ttu-id="7527f-140">Bu iki farklı şekilde bağdaştırıcı koleksiyonları başlatmanın, derleyicinin oluşturduğu yöntem nedeniyle biraz farklı davranışlara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="7527f-140">These two different ways to initialize associative collections have slightly different behavior because of the method calls the compiler generates.</span></span> <span data-ttu-id="7527f-141">Her iki varyant `Dictionary` da sınıfla çalışır.</span><span class="sxs-lookup"><span data-stu-id="7527f-141">Both variants work with the `Dictionary` class.</span></span> <span data-ttu-id="7527f-142">Diğer türler, genel API'lerine göre yalnızca birini veya diğerini destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="7527f-142">Other types may only support one or the other based on their public API.</span></span>

## <a name="examples"></a><span data-ttu-id="7527f-143">Örnekler</span><span class="sxs-lookup"><span data-stu-id="7527f-143">Examples</span></span>

<span data-ttu-id="7527f-144">Aşağıdaki örnek, nesne ve koleksiyon başharfleri kavramlarını birleştirir.</span><span class="sxs-lookup"><span data-stu-id="7527f-144">The following example combines the concepts of object and collection initializers.</span></span>

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullExample)]  

<span data-ttu-id="7527f-145">Aşağıdaki örnek, birden çok <xref:System.Collections.IEnumerable> parametreiçeren `Add` bir yöntem uygulayan ve içeren bir nesneyi gösterir, Bu `Add` yöntemin imzasına karşılık gelen listede öğe başına birden çok öğe içeren bir koleksiyon başlatılması kullanır.</span><span class="sxs-lookup"><span data-stu-id="7527f-145">The following example shows an object that implements <xref:System.Collections.IEnumerable> and contains an `Add` method with multiple parameters, It uses a collection initializer with multiple elements per item in the list that correspond to the signature of the `Add` method.</span></span>

[!code-csharp[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullListExample)]  

<span data-ttu-id="7527f-146">`Add`yöntemler, aşağıdaki `params` örnekte gösterildiği gibi değişken sayıda bağımsız değişken almak için anahtar sözcüğü kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="7527f-146">`Add` methods can use the `params` keyword to take a variable number of arguments, as shown in the following example.</span></span> <span data-ttu-id="7527f-147">Bu örnek, dizinleri kullanarak bir koleksiyon başlatılması için bir dizinleyici özel uygulamasını da gösterir.</span><span class="sxs-lookup"><span data-stu-id="7527f-147">This example also demonstrates the custom implementation of an indexer to initialize a collection using indexes.</span></span>

[!code-csharp[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullDictionaryInitializer)]  

## <a name="see-also"></a><span data-ttu-id="7527f-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7527f-148">See also</span></span>

- [<span data-ttu-id="7527f-149">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7527f-149">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7527f-150">C# üzerinde LINQ</span><span class="sxs-lookup"><span data-stu-id="7527f-150">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="7527f-151">Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="7527f-151">Anonymous Types</span></span>](anonymous-types.md)
