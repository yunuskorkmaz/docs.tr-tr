---
title: Nesne ve koleksiyon başlatıcıları-C# Programlama Kılavuzu
description: C# ' deki nesne başlatıcıları, bir oluşturucuyu çağırdıktan sonra oluşturma sırasında bir nesnenin erişilebilir alanlara veya özelliklerine değerler atar.
ms.date: 12/19/2018
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
ms.openlocfilehash: 81deed8a21bff10364524c3e0784c562d4e727e6
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864780"
---
# <a name="object-and-collection-initializers-c-programming-guide"></a><span data-ttu-id="70754-103">Nesne ve Koleksiyon Başlatıcıları (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="70754-103">Object and Collection Initializers (C# Programming Guide)</span></span>

<span data-ttu-id="70754-104">C# bir nesne veya koleksiyon örneklemenizi ve tek bir ifadede üye atamaları gerçekleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="70754-104">C# lets you instantiate an object or collection and perform member assignments in a single statement.</span></span>

## <a name="object-initializers"></a><span data-ttu-id="70754-105">Nesne başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="70754-105">Object initializers</span></span>

<span data-ttu-id="70754-106">Nesne başlatıcıları, oluşturma zamanında ardından atama deyimleri satırları gelecek şekilde bir oluşturucu çağırmak zorunda kalmadan, bir nesnenin istediğiniz erişilebilir alanlarına veya özelliklerine değerler atamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="70754-106">Object initializers let you assign values to any accessible fields or properties of an object at creation time without having to invoke a constructor followed by lines of assignment statements.</span></span> <span data-ttu-id="70754-107">Nesne başlatıcı sözdizimi, bir oluşturucu için bağımsız değişkenler belirtmenize veya bağımsız değişkenleri (ve parantez sözdizimini) atmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="70754-107">The object initializer syntax enables you to specify arguments for a constructor or omit the arguments (and parentheses syntax).</span></span>  <span data-ttu-id="70754-108">Aşağıdaki örnek, bir nesne başlatıcısının adlandırılmış bir tür ile nasıl kullanılacağını `Cat` ve parametresiz oluşturucunun nasıl çağırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="70754-108">The following example shows how to use an object initializer with a named type, `Cat` and how to invoke the parameterless constructor.</span></span> <span data-ttu-id="70754-109">Sınıfında otomatik uygulanan özelliklerin kullanımını göz önünde edin `Cat` .</span><span class="sxs-lookup"><span data-stu-id="70754-109">Note the use of auto-implemented properties in the `Cat` class.</span></span> <span data-ttu-id="70754-110">Daha fazla bilgi için bkz. [Otomatik uygulanan özellikler](auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="70754-110">For more information, see [Auto-Implemented Properties](auto-implemented-properties.md).</span></span>  
  
[!code-csharp[ObjectInitializer1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#CatDeclaration)]  
[!code-csharp[ObjectInitializer1a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ObjectPropertyInitialization)]  

<span data-ttu-id="70754-111">Nesne başlatıcıları sözdizimi, bir örnek oluşturmanıza olanak sağlar ve sonra, atanan özelliklerine sahip yeni oluşturulan nesneyi atamadaki değişkene atar.</span><span class="sxs-lookup"><span data-stu-id="70754-111">The object initializers syntax allows you to create an instance, and after that it assigns the newly created object, with its assigned properties, to the variable in the assignment.</span></span>

<span data-ttu-id="70754-112">C# 6 ' dan itibaren, nesne başlatıcıları alanları ve özellikleri atamaya ek olarak Dizin oluşturucular ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="70754-112">Starting with C# 6, object initializers can set indexers, in addition to assigning fields and properties.</span></span> <span data-ttu-id="70754-113">Bu temel sınıfı göz önünde bulundurun `Matrix` :</span><span class="sxs-lookup"><span data-stu-id="70754-113">Consider this basic `Matrix` class:</span></span>

[!code-csharp[ObjectInitializer2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixDeclaration)]  

<span data-ttu-id="70754-114">Kimlik matrisini aşağıdaki kodla başlatabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="70754-114">You could initialize the identity matrix with the following code:</span></span>

[!code-csharp[ObjectInitializer2a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixInitialization)]  

<span data-ttu-id="70754-115">Erişilebilir bir ayarlayıcı içeren erişilebilir Dizin Oluşturucu, bağımsız değişkenlerin sayısı veya türleri ne olursa olsun, nesne başlatıcısındaki ifadelerden biri olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="70754-115">Any accessible indexer that contains an accessible setter can be used as one of the expressions in an object initializer, regardless of the number or types of arguments.</span></span> <span data-ttu-id="70754-116">Dizin bağımsız değişkenleri atamanın sol tarafını oluşturur ve değer ifadenin sağ tarafındadır.</span><span class="sxs-lookup"><span data-stu-id="70754-116">The index arguments form the left side of the assignment, and the value is the right side of the expression.</span></span>  <span data-ttu-id="70754-117">Örneğin, uygun dizin oluşturucular varsa bunların hepsi geçerlidir `IndexersExample` :</span><span class="sxs-lookup"><span data-stu-id="70754-117">For example, these are all valid if `IndexersExample` has the appropriate indexers:</span></span>

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

<span data-ttu-id="70754-118">Önceki kodun derlenmesi için, `IndexersExample` türün aşağıdaki üyelere sahip olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="70754-118">For the preceding code to compile, the `IndexersExample` type must have the following members:</span></span>

```csharp
public string name;
public double Size { set { ... }; }
public char this[int i] { set { ... }; }
public string this[char c, int i] {  set { ... }; }
```

## <a name="object-initializers-with-anonymous-types"></a><span data-ttu-id="70754-119">Anonim türlerde Nesne Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="70754-119">Object Initializers with anonymous types</span></span>

<span data-ttu-id="70754-120">Nesne başlatıcıları herhangi bir bağlamda kullanılabilse de, LINQ sorgu ifadelerinde özellikle faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="70754-120">Although object initializers can be used in any context, they are especially useful in LINQ query expressions.</span></span> <span data-ttu-id="70754-121">Sorgu ifadeleri, aşağıdaki bildirimde gösterildiği gibi, yalnızca bir nesne Başlatıcısı kullanılarak başlatılan [anonim türler](./anonymous-types.md)için sık kullanılan kullanımı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="70754-121">Query expressions make frequent use of [anonymous types](./anonymous-types.md), which can only be initialized by using an object initializer, as shown in the following declaration.</span></span>  

```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```

<span data-ttu-id="70754-122">Anonim türler, `select` BIR LINQ sorgu ifadesindeki yan tümceyi, özgün dizinin nesnelerini değeri ve şekli orijinalden farklı olabilecek nesnelere dönüştürmek üzere etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="70754-122">Anonymous types enable the `select` clause in a LINQ query expression to transform objects of the original sequence into objects whose value and shape may differ from the original.</span></span> <span data-ttu-id="70754-123">Bir sıradaki her bir nesneden elde edilen bilgilerin yalnızca bir kısmını depolamak isterseniz, bu kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="70754-123">This is useful if you want to store only a part of the information from each object in a sequence.</span></span> <span data-ttu-id="70754-124">Aşağıdaki örnekte, bir ürün nesnesinin ( `p` ) birçok alanı ve yöntemi içerdiğini ve yalnızca ürün adını ve birim fiyatını içeren bir nesne dizisi oluşturmak istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="70754-124">In the following example, assume that a product object (`p`) contains many fields and methods, and that you are only interested in creating a sequence of objects that contain the product name and the unit price.</span></span>  
  
[!code-csharp[ObjectInitializer3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#AnonymousUse)]  

<span data-ttu-id="70754-125">Bu sorgu yürütüldüğünde, `productInfos` değişken, `foreach` Bu örnekte gösterildiği gibi bir bildirimde erişilebilen nesne dizisine sahip olur:</span><span class="sxs-lookup"><span data-stu-id="70754-125">When this query is executed, the `productInfos` variable will contain a sequence of objects that can be accessed in a `foreach` statement as shown in this example:</span></span>  

```csharp
foreach(var p in productInfos){...}  
```

<span data-ttu-id="70754-126">Yeni anonim türdeki her nesnenin, özgün nesnedeki özellikler veya alanlarla aynı adları alan iki ortak özelliği vardır.</span><span class="sxs-lookup"><span data-stu-id="70754-126">Each object in the new anonymous type has two public properties that receive the same names as the properties or fields in the original object.</span></span> <span data-ttu-id="70754-127">Ayrıca, anonim bir tür oluştururken bir alanı yeniden adlandırabilirsiniz; Aşağıdaki örnek, `UnitPrice` alanını olarak yeniden adlandırır `Price` .</span><span class="sxs-lookup"><span data-stu-id="70754-127">You can also rename a field when you are creating an anonymous type; the following example renames the `UnitPrice` field to `Price`.</span></span>  

```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```

## <a name="collection-initializers"></a><span data-ttu-id="70754-128">Koleksiyon başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="70754-128">Collection initializers</span></span>

<span data-ttu-id="70754-129">Koleksiyon Başlatıcıları bir veya daha fazla öğe başlatıcısını, <xref:System.Collections.IEnumerable> `Add` bir örnek yöntemi veya bir genişletme yöntemi olarak uygun imzaya sahip ve uygulayan bir koleksiyon türü başlattığınızda belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="70754-129">Collection initializers let you specify one or more element initializers when you initialize a collection type that implements <xref:System.Collections.IEnumerable> and has `Add` with the appropriate signature as an instance method or an extension method.</span></span> <span data-ttu-id="70754-130">Öğe başlatıcıları basit bir değer, bir ifade veya nesne Başlatıcısı olabilir.</span><span class="sxs-lookup"><span data-stu-id="70754-130">The element initializers can be a simple value, an expression, or an object initializer.</span></span> <span data-ttu-id="70754-131">Bir koleksiyon başlatıcısı kullanarak birden çok çağrı belirtmeniz gerekmez; Derleyici çağrıları otomatik olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="70754-131">By using a collection initializer, you do not have to specify multiple calls; the compiler adds the calls automatically.</span></span>  
  
<span data-ttu-id="70754-132">Aşağıdaki örnekte iki basit koleksiyon başlatıcıları gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="70754-132">The following example shows two simple collection initializers:</span></span>  

```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```

<span data-ttu-id="70754-133">Aşağıdaki koleksiyon başlatıcısı, `Cat` Önceki örnekte tanımlanan sınıfın nesnelerini başlatmak için nesne başlatıcıları kullanır.</span><span class="sxs-lookup"><span data-stu-id="70754-133">The following collection initializer uses object initializers to initialize objects of the `Cat` class defined in a previous example.</span></span> <span data-ttu-id="70754-134">Nesne başlatıcıların tek tek küme ayraçları içine alındığına ve virgüllerle ayrıldığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="70754-134">Note that the individual object initializers are enclosed in braces and separated by commas.</span></span>  
  
[!code-csharp[ListInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitializer)]  
  
<span data-ttu-id="70754-135">Koleksiyonun yöntemi izin veriyorsa, koleksiyon başlatıcısında bir öğe olarak [null](../../language-reference/keywords/null.md) belirtebilirsiniz `Add` .</span><span class="sxs-lookup"><span data-stu-id="70754-135">You can specify [null](../../language-reference/keywords/null.md) as an element in a collection initializer if the collection's `Add` method allows it.</span></span>  
  
[!code-csharp[ListInitializerNull](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitialerWithNull)]  
  
 <span data-ttu-id="70754-136">Koleksiyon okuma/yazma dizinlemeyi destekliyorsa, dizinli öğeleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70754-136">You can specify indexed elements if the collection supports read / write indexing.</span></span>
  
[!code-csharp[DictionaryInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryIndexerInitializer)]  

<span data-ttu-id="70754-137">Yukarıdaki örnek, değerlerini ayarlamak için öğesini çağıran kodu oluşturur <xref:System.Collections.Generic.Dictionary%602.Item(%600)> .</span><span class="sxs-lookup"><span data-stu-id="70754-137">The preceding sample generates code that calls the <xref:System.Collections.Generic.Dictionary%602.Item(%600)> to set the values.</span></span> <span data-ttu-id="70754-138">C# 6 ' dan önce, aşağıdaki sözdizimini kullanarak sözlükleri ve diğer İlişkilendirilebilir kapsayıcıları başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70754-138">Before C# 6, you could initialize dictionaries and other associative containers using the following syntax.</span></span> <span data-ttu-id="70754-139">Dizin Oluşturucu sözdizimi yerine parantez ve atama ile birden çok değerli bir nesne kullandığını fark edin:</span><span class="sxs-lookup"><span data-stu-id="70754-139">Notice that instead of indexer syntax, with parentheses and an assignment, it uses an object with multiple values:</span></span>

[!code-csharp[DictionaryAddInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryAddInitializer)]  

<span data-ttu-id="70754-140">Bu başlatıcı örneği, <xref:System.Collections.Generic.Dictionary%602.Add(%600,%601)> sözlüğe üç öğe eklemek için çağırır.</span><span class="sxs-lookup"><span data-stu-id="70754-140">This initializer example calls <xref:System.Collections.Generic.Dictionary%602.Add(%600,%601)> to add the three items into the dictionary.</span></span> <span data-ttu-id="70754-141">İlişkilendirilebilir koleksiyonları başlatmanın bu iki farklı yolu, derleyicinin oluşturduğu Yöntem çağrıları nedeniyle biraz farklı davranışa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="70754-141">These two different ways to initialize associative collections have slightly different behavior because of the method calls the compiler generates.</span></span> <span data-ttu-id="70754-142">Her iki çeşit de `Dictionary` sınıfla çalışır.</span><span class="sxs-lookup"><span data-stu-id="70754-142">Both variants work with the `Dictionary` class.</span></span> <span data-ttu-id="70754-143">Diğer türler, genel API 'lerine göre yalnızca bir veya diğerini destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="70754-143">Other types may only support one or the other based on their public API.</span></span>

## <a name="examples"></a><span data-ttu-id="70754-144">Örnekler</span><span class="sxs-lookup"><span data-stu-id="70754-144">Examples</span></span>

<span data-ttu-id="70754-145">Aşağıdaki örnek, nesne ve koleksiyon başlatıcıları kavramlarını birleştirir.</span><span class="sxs-lookup"><span data-stu-id="70754-145">The following example combines the concepts of object and collection initializers.</span></span>

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullExample)]  

<span data-ttu-id="70754-146">Aşağıdaki örnek, uygulayan <xref:System.Collections.IEnumerable> ve birden çok parametreli bir yöntemi içeren bir nesnesi gösterir `Add` , bu, yönteminin imzasına karşılık gelen listede öğe başına birden çok öğe içeren bir koleksiyon başlatıcısı kullanır `Add` .</span><span class="sxs-lookup"><span data-stu-id="70754-146">The following example shows an object that implements <xref:System.Collections.IEnumerable> and contains an `Add` method with multiple parameters, It uses a collection initializer with multiple elements per item in the list that correspond to the signature of the `Add` method.</span></span>

[!code-csharp[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullListExample)]  

<span data-ttu-id="70754-147">`Add`Yöntemler `params` anahtar sözcüğünü, aşağıdaki örnekte gösterildiği gibi değişken sayıda bağımsız değişken almak için kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="70754-147">`Add` methods can use the `params` keyword to take a variable number of arguments, as shown in the following example.</span></span> <span data-ttu-id="70754-148">Bu örnek ayrıca dizin kullanarak bir koleksiyonu başlatmak için bir dizin oluşturucunun özel uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="70754-148">This example also demonstrates the custom implementation of an indexer to initialize a collection using indexes.</span></span>

[!code-csharp[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullDictionaryInitializer)]  

## <a name="see-also"></a><span data-ttu-id="70754-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70754-149">See also</span></span>

- [<span data-ttu-id="70754-150">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="70754-150">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="70754-151">C# üzerinde LINQ</span><span class="sxs-lookup"><span data-stu-id="70754-151">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="70754-152">Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="70754-152">Anonymous Types</span></span>](anonymous-types.md)
