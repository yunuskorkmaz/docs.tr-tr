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
# <a name="object-and-collection-initializers-c-programming-guide"></a>Nesne ve Koleksiyon Başlatıcıları (C# Programlama Kılavuzu)

C# bir nesneyi veya koleksiyonu anında gerçekleştirmenizi ve üye atamaları tek bir deyimde gerçekleştirmenizi sağlar.

## <a name="object-initializers"></a>Nesne başharfleri

Nesne başlatıcıları, oluşturma zamanında ardından atama deyimleri satırları gelecek şekilde bir oluşturucu çağırmak zorunda kalmadan, bir nesnenin istediğiniz erişilebilir alanlarına veya özelliklerine değerler atamanıza olanak tanır. Nesne başlatıcı sözdizimi, bir oluşturucu için bağımsız değişkenler belirtmenize veya bağımsız değişkenleri (ve parantez sözdizimini) atmanıza olanak tanır.  Aşağıdaki örnek, adlandırılmış bir türe sahip bir `Cat` nesne başlatıcısının nasıl kullanılacağını ve parametresiz oluşturucuyu nasıl çağırılabildiğini gösterir. Sınıfta otomatik olarak uygulanan özelliklerin `Cat` kullanımına dikkat edin. Daha fazla bilgi için otomatik [olarak uygulanan özellikler'e](auto-implemented-properties.md)bakın.  
  
[!code-csharp[ObjectInitializer1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#CatDeclaration)]  
[!code-csharp[ObjectInitializer1a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ObjectPropertyInitialization)]  

Nesne baş harfleri sözdizimi bir örnek oluşturmanıza olanak sağlar ve bundan sonra yeni oluşturulan nesneyi atanan özellikleriyle atamadaki değişkene atar.

C# 6 ile başlayarak, nesne başlatıcıları alanları ve özellikleri atamaya ek olarak dizin leyiciler ayarlayabilir. Bu temel `Matrix` sınıfı göz önünde bulundurun:

[!code-csharp[ObjectInitializer2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixDeclaration)]  

Kimlik matrisini aşağıdaki kodla başharfe alabilirsiniz:

[!code-csharp[ObjectInitializer2a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixInitialization)]  

Erişilebilir bir ayarlayıcı içeren erişilebilir dizinleyici, bağımsız değişken sayısı veya türüne bakılmaksızın nesne baş harferindeki ifadelerden biri olarak kullanılabilir. Dizin bağımsız değişkenleri atamanın sol tarafını oluşturur ve değer ifadenin sağ tarafıdır.  Örneğin, uygun dizinleyicileri varsa `IndexersExample` bunların tümü geçerlidir:

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

Önceki kodun derlemesi için, `IndexersExample` tür aşağıdaki üyelere sahip olmalıdır:

```csharp
public string name;
public double Size { set { ... }; }
public char this[int i] { set { ... }; }
public string this[char c, int i] {  set { ... }; }
```

## <a name="object-initializers-with-anonymous-types"></a>Anonim türlerde Nesne Başlatıcıları

Nesne baş harfleri herhangi bir bağlamda kullanılabilse de, özellikle LINQ sorgu ifadelerinde yararlıdır. Sorgu ifadeleri, aşağıdaki bildirimde gösterildiği gibi, yalnızca bir nesne baş harfer kullanılarak başharfe bünyebilen [anonim türleri](./anonymous-types.md)sık sık kullanır.  

```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```

Adsız türler, linq sorgu ifadesindeki `select` yan tümcenin, özgün dizinin nesnelerini değeri ve şekli orijinalden farklı olabilecek nesnelere dönüştürmesini sağlar. Bir sıradaki her bir nesneden elde edilen bilgilerin yalnızca bir kısmını depolamak isterseniz, bu kullanışlıdır. Aşağıdaki örnekte, bir ürün nesnesinin (`p`) birçok alan ve yöntem içerdiğini ve yalnızca ürün adını ve birim fiyatı içeren bir nesne dizisi oluşturmakla ilgilendiğinizi varsayalım.  
  
[!code-csharp[ObjectInitializer3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#AnonymousUse)]  

Bu sorgu yürütüldüğünde, `productInfos` değişken bu örnekte gösterildiği gibi bir `foreach` deyimde erişilebilen bir nesne dizisi içerir:  

```csharp
foreach(var p in productInfos){...}  
```

Yeni adsız türdeki her nesnenin, özgün nesnedeki özellikler veya alanlar la aynı adları alan iki ortak özelliği vardır. Anonim bir tür oluştururken alanı yeniden adlandırabilirsiniz; aşağıdaki örnek alanı `UnitPrice` . `Price`  

```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```

## <a name="collection-initializers"></a>Koleksiyon başlatıcıları

Koleksiyon başlatılması, bir örnek yöntemi veya uzantı yöntemi olarak uygun imzayı <xref:System.Collections.IEnumerable> uygulayan `Add` ve sahip olan bir koleksiyon türünü başharfe aldığınızda bir veya daha fazla öğe başlatılmasını belirtmenize izin verirken. Öğe initializaları basit bir değer, bir ifade veya nesne baş harfer olabilir. Bir koleksiyon başlatma kullanarak, birden çok çağrı belirtmeniz gerekmez; derleyici aramaları otomatik olarak ekler.  
  
Aşağıdaki örnekte iki basit koleksiyon başharfleri gösterilmektedir:  

```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```

Aşağıdaki koleksiyon başharfleri, önceki örnekte tanımlanan `Cat` sınıfın nesnelerini başlatmak için nesne başharfleri kullanır. Nesne başlatıcıların tek tek küme ayraçları içine alındığına ve virgüllerle ayrıldığına dikkat edin.  
  
[!code-csharp[ListInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitializer)]  
  
Koleksiyonun [null](../../language-reference/keywords/null.md) `Add` yöntemi izin veriyorsa, koleksiyon başlatılmasında bir öğe olarak null belirtebilirsiniz.  
  
[!code-csharp[ListInitializerNull](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitialerWithNull)]  
  
 Koleksiyon okuma /yazma dizini oluşturmayı destekliyorsa dizinlenmiş öğeleri belirtebilirsiniz.
  
[!code-csharp[DictionaryInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryIndexerInitializer)]  

Önceki örnek değerleri ayarlamak <xref:System.Collections.Generic.Dictionary%602.Item(%600)> için çağıran kod oluşturur. C# 6'dan önce, aşağıdaki sözdizimini kullanarak sözlükleri ve diğer bağdaştırıcı kapları başharfe dönüştürebilirsiniz. Dizinleyici sözdizimi yerine, parantez ve atama ile, birden çok değere sahip bir nesne kullanır:

[!code-csharp[DictionaryAddInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryAddInitializer)]  

Bu baş harförneği, üç öğeyi sözlüğün içine eklemek için çağırır. <xref:System.Collections.Generic.Dictionary%602.Add(%600,%601)> Bu iki farklı şekilde bağdaştırıcı koleksiyonları başlatmanın, derleyicinin oluşturduğu yöntem nedeniyle biraz farklı davranışlara sahiptir. Her iki varyant `Dictionary` da sınıfla çalışır. Diğer türler, genel API'lerine göre yalnızca birini veya diğerini destekleyebilir.

## <a name="examples"></a>Örnekler

Aşağıdaki örnek, nesne ve koleksiyon başharfleri kavramlarını birleştirir.

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullExample)]  

Aşağıdaki örnek, birden çok <xref:System.Collections.IEnumerable> parametreiçeren `Add` bir yöntem uygulayan ve içeren bir nesneyi gösterir, Bu `Add` yöntemin imzasına karşılık gelen listede öğe başına birden çok öğe içeren bir koleksiyon başlatılması kullanır.

[!code-csharp[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullListExample)]  

`Add`yöntemler, aşağıdaki `params` örnekte gösterildiği gibi değişken sayıda bağımsız değişken almak için anahtar sözcüğü kullanabilir. Bu örnek, dizinleri kullanarak bir koleksiyon başlatılması için bir dizinleyici özel uygulamasını da gösterir.

[!code-csharp[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullDictionaryInitializer)]  

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [C# üzerinde LINQ](../../linq/index.md)
- [Anonim Türler](anonymous-types.md)
