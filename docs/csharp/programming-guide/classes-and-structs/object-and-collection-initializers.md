---
title: Nesne ve koleksiyon başlatıcıları - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 12/19/2018
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
ms.openlocfilehash: 1dc28ac218eb0325095641840834b40594ad67ab
ms.sourcegitcommit: d09c77414e9e4fc72c79b04deee7a756a120674e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54084868"
---
# <a name="object-and-collection-initializers-c-programming-guide"></a><span data-ttu-id="370d6-102">Nesne ve Koleksiyon Başlatıcıları (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="370d6-102">Object and Collection Initializers (C# Programming Guide)</span></span>

<span data-ttu-id="370d6-103">C#bir nesnede veya koleksiyonda örneklemek ve tek bir deyimde üye atamalar gerçekleştirmek olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="370d6-103">C# lets you instantiate an object or collection and perform member assignments in a single statement.</span></span>

## <a name="object-initializers"></a><span data-ttu-id="370d6-104">Nesne başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="370d6-104">Object initializers</span></span>

<span data-ttu-id="370d6-105">Nesne başlatıcıları, oluşturma zamanında ardından atama deyimleri satırları gelecek şekilde bir oluşturucu çağırmak zorunda kalmadan, bir nesnenin istediğiniz erişilebilir alanlarına veya özelliklerine değerler atamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="370d6-105">Object initializers let you assign values to any accessible fields or properties of an object at creation time without having to invoke a constructor followed by lines of assignment statements.</span></span> <span data-ttu-id="370d6-106">Nesne başlatıcı sözdizimi, bir oluşturucu için bağımsız değişkenler belirtmenize veya bağımsız değişkenleri (ve parantez sözdizimini) atmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="370d6-106">The object initializer syntax enables you to specify arguments for a constructor or omit the arguments (and parentheses syntax).</span></span>  <span data-ttu-id="370d6-107">Aşağıdaki örnek, adlandırılmış bir türü ile bir nesne Başlatıcı kullanma işlemi gösterilmektedir `Cat` ve varsayılan oluşturucunun nasıl çağrılacağını.</span><span class="sxs-lookup"><span data-stu-id="370d6-107">The following example shows how to use an object initializer with a named type, `Cat` and how to invoke the default constructor.</span></span> <span data-ttu-id="370d6-108">Otomatik uygulanan özelliklerin kullanımına dikkat edin `Cat` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="370d6-108">Note the use of auto-implemented properties in the `Cat` class.</span></span> <span data-ttu-id="370d6-109">Daha fazla bilgi için [Implemented Properties](auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="370d6-109">For more information, see [Auto-Implemented Properties](auto-implemented-properties.md).</span></span>  
  
[!code-csharp[ObjectInitializer1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#CatDeclaration)]  
[!code-csharp[ObjectInitializer1a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ObjectPropertyInitialization)]  
 
<span data-ttu-id="370d6-110">Nesne Başlatıcı sözdizimi örneği oluşturmanıza olanak sağlar ve sonra kendi atanan özelliklere sahip yeni oluşturulan nesne değişkeni ataması atar.</span><span class="sxs-lookup"><span data-stu-id="370d6-110">The object initializers syntax allows you to create an instance, and after that it assigns the newly created object, with its assigned properties, to the variable in the assignment.</span></span>

<span data-ttu-id="370d6-111">İle başlayarak C# 6, nesne başlatıcıları, Dizinleyicileri, alanlar ve Özellikler atama ek olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="370d6-111">Starting with C# 6, object initializers can set indexers, in addition to assigning fields and properties.</span></span> <span data-ttu-id="370d6-112">Bu temel göz önünde bulundurun `Matrix` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="370d6-112">Consider this basic `Matrix` class:</span></span>

[!code-csharp[ObjectInitializer2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixDeclaration)]  

<span data-ttu-id="370d6-113">Aşağıdaki kod ile kimlik matrisi başlatabilir:</span><span class="sxs-lookup"><span data-stu-id="370d6-113">You could initialize the identity matrix with the following code:</span></span>

[!code-csharp[ObjectInitializer2a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixInitialization)]  

<span data-ttu-id="370d6-114">Erişilebilir bir Ayarlayıcısı içeren tüm erişilebilir bir dizin oluşturucu bağımsız değişkenlerinin türlerine ve sayı bağımsız olarak nesne Başlatıcı ifadelerinde biri olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="370d6-114">Any accessible indexer that contains an accessible setter can be used as one of the expressions in an object initializer, regardless of the number or types of arguments.</span></span> <span data-ttu-id="370d6-115">Dizin bağımsız değişkenler atamanın sol tarafındaki form ve ifadesinin sağ tarafı değerdir.</span><span class="sxs-lookup"><span data-stu-id="370d6-115">The index arguments form the left side of the assignment, and the value is the right side of the expression.</span></span>  <span data-ttu-id="370d6-116">Örneğin, tüm geçerli ise bunlar `IndexersExample` uygun dizin oluşturucular sahiptir:</span><span class="sxs-lookup"><span data-stu-id="370d6-116">For example, these are all valid if `IndexersExample` has the appropriate indexers:</span></span>

```csharp
var thing = new IndexersExample {
    name = "object one",
    [1] = '1',
    [2] = '4',
    [3] = '9',
    Baz = Math.PI,
    ['C',4] = "Middle C"
}
```

<span data-ttu-id="370d6-117">Derlemek, yukarıdaki kod için `IndexersExample` türü aşağıdaki üyeleri olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="370d6-117">For the preceding code to compile, the `IndexersExample` type must have the following members:</span></span>

```csharp
public string name;
public double Size { set { ... }; }
public char this[int i] { set { ... }; }
public string this[char c, int i] {  set { ... }; }
}
```

## <a name="object-initializers-with-anonymous-types"></a><span data-ttu-id="370d6-118">Anonim türlerde Nesne Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="370d6-118">Object Initializers with anonymous types</span></span>

<span data-ttu-id="370d6-119">Nesne başlatıcıları her bağlamda kullanılabilir olsa da, bunlar özellikle kullanışlı [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadelerinde.</span><span class="sxs-lookup"><span data-stu-id="370d6-119">Although object initializers can be used in any context, they are especially useful in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="370d6-120">Sorgu ifadeleri, sık sık kullanırlar [anonim türler](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), hangi yalnızca başlatılabilir bir nesne Başlatıcı kullanarak aşağıdaki bildirimde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="370d6-120">Query expressions make frequent use of [anonymous types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), which can only be initialized by using an object initializer, as shown in the following declaration.</span></span>  

```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```

<span data-ttu-id="370d6-121">Anonim türler etkinleştirme `select` yan tümcesinde bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu deyimi orijinal sıranın nesnelerini değeri ve şekli orijinalden farklı olabilir nesneleri dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="370d6-121">Anonymous types enable the `select` clause in a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression to transform objects of the original sequence into objects whose value and shape may differ from the original.</span></span> <span data-ttu-id="370d6-122">Bir sıradaki her bir nesneden elde edilen bilgilerin yalnızca bir kısmını depolamak isterseniz, bu kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="370d6-122">This is useful if you want to store only a part of the information from each object in a sequence.</span></span> <span data-ttu-id="370d6-123">Aşağıdaki örnekte, varsayımında bir ürün nesnesinin (`p`) birçok alan ve yöntem içerir ve, yalnızca sırası oluşturmakla ilgili bilgi sahibi olduğunuz ürün adını ve birim fiyatı içerir.</span><span class="sxs-lookup"><span data-stu-id="370d6-123">In the following example, assume that a product object (`p`) contains many fields and methods, and that you are only interested in creating a sequence of objects that contain the product name and the unit price.</span></span>  
  
[!code-csharp[ObjectInitializer3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#AnonymousUse)]  

<span data-ttu-id="370d6-124">Bu sorgu yürütüldüğünde `productInfos` değişkeni erişilebilen bir nesne sırası içerecektir bir `foreach` Bu örnekte gösterildiği gibi deyimi:</span><span class="sxs-lookup"><span data-stu-id="370d6-124">When this query is executed, the `productInfos` variable will contain a sequence of objects that can be accessed in a `foreach` statement as shown in this example:</span></span>  

```csharp
foreach(var p in productInfos){...}  
```

<span data-ttu-id="370d6-125">Yeni anonim türdeki her bir nesnenin orijinal nesnedeki özelliklerle veya alanlarla aynı adları alan iki genel özelliği vardır.</span><span class="sxs-lookup"><span data-stu-id="370d6-125">Each object in the new anonymous type has two public properties that receive the same names as the properties or fields in the original object.</span></span> <span data-ttu-id="370d6-126">Ayrıca, anonim bir tür oluştururken bir alanı yeniden adlandırabilirsiniz; Aşağıdaki örnek yeniden adlandırır `UnitPrice` alanı `Price`.</span><span class="sxs-lookup"><span data-stu-id="370d6-126">You can also rename a field when you are creating an anonymous type; the following example renames the `UnitPrice` field to `Price`.</span></span>  

```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```

## <a name="collection-initializers"></a><span data-ttu-id="370d6-127">Koleksiyon başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="370d6-127">Collection initializers</span></span>

<span data-ttu-id="370d6-128">Koleksiyon başlatıcıları bir belirtmenize olanak tanır veya daha fazla öğe başlatıcıları bir koleksiyon başlattığınızda uygulayan türü <xref:System.Collections.IEnumerable> ve `Add` uygun imzalı bir örnek yöntemi veya bir genişletme yöntemi olarak.</span><span class="sxs-lookup"><span data-stu-id="370d6-128">Collection initializers let you specify one or more element initializers when you initialize a collection type that implements <xref:System.Collections.IEnumerable> and has `Add` with the appropriate signature as an instance method or an extension method.</span></span> <span data-ttu-id="370d6-129">Öğe başlatıcıları basit bir değer, bir ifade veya bir nesne Başlatıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="370d6-129">The element initializers can be a simple value, an expression, or an object initializer.</span></span> <span data-ttu-id="370d6-130">Koleksiyon Başlatıcısı kullanarak, birden çok çağrı belirtmeniz gerekmez; Derleyici çağrıları otomatik olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="370d6-130">By using a collection initializer, you do not have to specify multiple calls; the compiler adds the calls automatically.</span></span>  
  
<span data-ttu-id="370d6-131">Aşağıdaki örnek, iki basit koleksiyon başlatıcısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="370d6-131">The following example shows two simple collection initializers:</span></span>  

```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```

<span data-ttu-id="370d6-132">Aşağıdaki koleksiyon Başlatıcısı nesnelerini başlatmak için nesne başlatıcıları kullanır `Cat` önceki bir örnekte tanımlanan sınıfı.</span><span class="sxs-lookup"><span data-stu-id="370d6-132">The following collection initializer uses object initializers to initialize objects of the `Cat` class defined in a previous example.</span></span> <span data-ttu-id="370d6-133">Nesne başlatıcıların tek tek küme ayraçları içine alındığına ve virgüllerle ayrıldığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="370d6-133">Note that the individual object initializers are enclosed in braces and separated by commas.</span></span>  
  
[!code-csharp[ListInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitializer)]  
  
<span data-ttu-id="370d6-134">Belirtebileceğiniz [null](../../language-reference/keywords/null.md) bir koleksiyon başlatıcısında bir öğe olarak varsa koleksiyonun `Add` yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="370d6-134">You can specify [null](../../language-reference/keywords/null.md) as an element in a collection initializer if the collection's `Add` method allows it.</span></span>  
  
[!code-csharp[ListInitializerNull](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitialerWithNull)]  
  
 <span data-ttu-id="370d6-135">Dizinli öğeleri koleksiyonu destekleyen okuma / yazma dizin belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="370d6-135">You can specify indexed elements if the collection supports read / write indexing.</span></span>
  
[!code-csharp[DictionaryInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryIndexerInitializer)]  

<span data-ttu-id="370d6-136">Önceki örnekte çağıran kodu üretir <xref:System.Collections.Generic.Dictionary%602.Item(%600)> değerleri ayarlamak için.</span><span class="sxs-lookup"><span data-stu-id="370d6-136">The preceding sample generates code that calls the <xref:System.Collections.Generic.Dictionary%602.Item(%600)> to set the values.</span></span> <span data-ttu-id="370d6-137">İle başlayarak C# 6 başlatır sözlükleri ve diğer ilişkisel kapsayıcılar aşağıdaki söz dizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="370d6-137">Beginning with C# 6, you can initialize dictionaries and other associative containers using the following syntax.</span></span> <span data-ttu-id="370d6-138">Dizin Oluşturucu sözdizimi yerine parantez ve bir atama ile birden çok değer içeren bir nesne kullandığına dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="370d6-138">Notice that instead of indexer syntax, with parentheses and an assignment, it uses an object with multiple values:</span></span>

[!code-csharp[DictionaryAddInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryAddInitializer)]  

<span data-ttu-id="370d6-139">Bu Başlatıcı örnek <xref:System.Collections.Generic.Dictionary%602.Add(%600,%601)> sözlüğe üç öğe eklemek için.</span><span class="sxs-lookup"><span data-stu-id="370d6-139">This initializer example calls <xref:System.Collections.Generic.Dictionary%602.Add(%600,%601)> to add the three items into the dictionary.</span></span> <span data-ttu-id="370d6-140">İlişkili koleksiyonlar başlatmak için bu iki farklı şekilde derleyici oluşturur yöntem çağrıları nedeniyle biraz farklı davranışa sahip.</span><span class="sxs-lookup"><span data-stu-id="370d6-140">These two different ways to initialize associative collections have slightly different behavior because of the method calls the compiler generates.</span></span> <span data-ttu-id="370d6-141">Her iki çeşitleri çalışmak `Dictionary` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="370d6-141">Both variants work with the `Dictionary` class.</span></span> <span data-ttu-id="370d6-142">Diğer türleri yalnızca bir diğer bağlı veya kendi genel API'sini destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="370d6-142">Other types may only support one or the other based on their public API.</span></span>

## <a name="examples"></a><span data-ttu-id="370d6-143">Örnekler</span><span class="sxs-lookup"><span data-stu-id="370d6-143">Examples</span></span>

<span data-ttu-id="370d6-144">Aşağıdaki örnek, nesne ve koleksiyon başlatıcıları kavramlarını birleştirir.</span><span class="sxs-lookup"><span data-stu-id="370d6-144">The following example combines the concepts of object and collection initializers.</span></span>

[!code-csharp-interactive[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullExample)]  

<span data-ttu-id="370d6-145">Uygulayan bir nesne aşağıdaki örnekte <xref:System.Collections.IEnumerable> ve içeren bir `Add` yöntemi ile birden çok parametre listedeki bir öğe başına imzasıiçinkarşılıkgelenbirdençoköğeiçerenbirkoleksiyonBaşlatıcısıkullanır,`Add`yöntemi.</span><span class="sxs-lookup"><span data-stu-id="370d6-145">The following example shows an object that implements <xref:System.Collections.IEnumerable> and contains an `Add` method with multiple parameters, It uses a collection initializer with multiple elements per item in the list that correspond to the signature of the `Add` method.</span></span>

[!code-csharp-interactive[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullListExample)]  

<span data-ttu-id="370d6-146">`Add` yöntemleri kullanabilir `params` anahtar sözcüğü bir değişken sayıda bağımsız değişken, aşağıdaki örnekte gösterildiği gibi gerçekleştirilecek.</span><span class="sxs-lookup"><span data-stu-id="370d6-146">`Add` methods can use the `params` keyword to take a variable number of arguments, as shown in the following example.</span></span> <span data-ttu-id="370d6-147">Bu örnekte ayrıca dizinleri kullanarak bir koleksiyonu başlatmak için bir dizin oluşturucu özel uygulanışı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="370d6-147">This example also demonstrates the custom implementation of an indexer to initialize a collection using indexes.</span></span>

[!code-csharp-interactive[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullDictionaryInitializer)]  

## <a name="see-also"></a><span data-ttu-id="370d6-148">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="370d6-148">See Also</span></span>

- [<span data-ttu-id="370d6-149">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="370d6-149">C# Programming Guide</span></span>](../index.md)  
- [<span data-ttu-id="370d6-150">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="370d6-150">LINQ Query Expressions</span></span>](../linq-query-expressions/index.md)  
- [<span data-ttu-id="370d6-151">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="370d6-151">Anonymous Types</span></span>](anonymous-types.md)
