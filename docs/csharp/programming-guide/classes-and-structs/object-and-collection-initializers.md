---
title: Nesne ve koleksiyon başlatıcıları- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 12/19/2018
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
ms.openlocfilehash: f6977fa6c5a8909d6108a5ccfc140b89a4fdd5a4
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596570"
---
# <a name="object-and-collection-initializers-c-programming-guide"></a>Nesne ve Koleksiyon Başlatıcıları (C# Programlama Kılavuzu)

C#bir nesne veya koleksiyon örneklemenizi ve tek bir ifadede üye atamaları gerçekleştirmenizi sağlar.

## <a name="object-initializers"></a>Nesne başlatıcıları

Nesne başlatıcıları, oluşturma zamanında ardından atama deyimleri satırları gelecek şekilde bir oluşturucu çağırmak zorunda kalmadan, bir nesnenin istediğiniz erişilebilir alanlarına veya özelliklerine değerler atamanıza olanak tanır. Nesne başlatıcı sözdizimi, bir oluşturucu için bağımsız değişkenler belirtmenize veya bağımsız değişkenleri (ve parantez sözdizimini) atmanıza olanak tanır.  Aşağıdaki örnek, `Cat` bir nesne başlatıcısının adlandırılmış bir tür ile nasıl kullanılacağını ve parametresiz oluşturucunun nasıl çağırılacağını gösterir. `Cat` Sınıfında otomatik uygulanan özelliklerin kullanımını göz önünde edin. Daha fazla bilgi için bkz. [Otomatik uygulanan özellikler](auto-implemented-properties.md).  
  
[!code-csharp[ObjectInitializer1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#CatDeclaration)]  
[!code-csharp[ObjectInitializer1a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ObjectPropertyInitialization)]  
 
Nesne başlatıcıları sözdizimi, bir örnek oluşturmanıza olanak sağlar ve sonra, atanan özelliklerine sahip yeni oluşturulan nesneyi atamadaki değişkene atar.

C# 6 ' dan itibaren, nesne başlatıcıları alanları ve özellikleri atamaya ek olarak Dizin oluşturucular ayarlayabilir. Bu temel `Matrix` sınıfı göz önünde bulundurun:

[!code-csharp[ObjectInitializer2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixDeclaration)]  

Kimlik matrisini aşağıdaki kodla başlatabilirsiniz:

[!code-csharp[ObjectInitializer2a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixInitialization)]  

Erişilebilir bir ayarlayıcı içeren erişilebilir Dizin Oluşturucu, bağımsız değişkenlerin sayısı veya türleri ne olursa olsun, nesne başlatıcısındaki ifadelerden biri olarak kullanılabilir. Dizin bağımsız değişkenleri atamanın sol tarafını oluşturur ve değer ifadenin sağ tarafındadır.  Örneğin, uygun dizin oluşturucular varsa `IndexersExample` bunların hepsi geçerlidir:

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

Önceki kodun derlenmesi için, `IndexersExample` türün aşağıdaki üyelere sahip olması gerekir:

```csharp
public string name;
public double Size { set { ... }; }
public char this[int i] { set { ... }; }
public string this[char c, int i] {  set { ... }; }
```

## <a name="object-initializers-with-anonymous-types"></a>Anonim türlerde Nesne Başlatıcıları

Nesne başlatıcıları herhangi bir bağlamda kullanılabilse de, [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadelerinde özellikle faydalıdır. Sorgu ifadeleri, aşağıdaki bildirimde gösterildiği gibi, yalnızca bir nesne Başlatıcısı kullanılarak başlatılan [anonim türler](./anonymous-types.md)için sık kullanılan kullanımı kolaylaştırır.  

```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```

Anonim türler, bir `select` sorgu ifadesindeki yan [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] tümcesini, değer ve şekli orijinalden farklı olabilecek nesneler içine dönüştürmek için bir sorgu ifadesinde etkinleştirir. Bir sıradaki her bir nesneden elde edilen bilgilerin yalnızca bir kısmını depolamak isterseniz, bu kullanışlıdır. Aşağıdaki örnekte, bir ürün nesnesinin (`p`) birçok alanı ve yöntemi içerdiğini ve yalnızca ürün adını ve birim fiyatını içeren bir nesne dizisi oluşturmak istediğinizi varsayalım.  
  
[!code-csharp[ObjectInitializer3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#AnonymousUse)]  

Bu sorgu yürütüldüğünde, `productInfos` değişken, bu örnekte gösterildiği gibi bir `foreach` bildirimde erişilebilen nesne dizisine sahip olur:  

```csharp
foreach(var p in productInfos){...}  
```

Yeni anonim türdeki her nesnenin, özgün nesnedeki özellikler veya alanlarla aynı adları alan iki ortak özelliği vardır. Ayrıca, anonim bir tür oluştururken bir alanı yeniden adlandırabilirsiniz; Aşağıdaki örnek, `UnitPrice` alanını olarak `Price`yeniden adlandırır.  

```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```

## <a name="collection-initializers"></a>Koleksiyon başlatıcıları

Koleksiyon Başlatıcıları bir veya daha fazla öğe başlatıcısını, bir örnek yöntemi veya bir genişletme yöntemi olarak <xref:System.Collections.IEnumerable> uygun imzaya `Add` sahip ve uygulayan bir koleksiyon türü başlattığınızda belirtmenize olanak tanır. Öğe başlatıcıları basit bir değer, bir ifade veya nesne Başlatıcısı olabilir. Bir koleksiyon başlatıcısı kullanarak birden çok çağrı belirtmeniz gerekmez; Derleyici çağrıları otomatik olarak ekler.  
  
Aşağıdaki örnekte iki basit koleksiyon başlatıcıları gösterilmektedir:  

```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```

Aşağıdaki koleksiyon başlatıcısı, önceki örnekte tanımlanan `Cat` sınıfın nesnelerini başlatmak için nesne başlatıcıları kullanır. Nesne başlatıcıların tek tek küme ayraçları içine alındığına ve virgüllerle ayrıldığına dikkat edin.  
  
[!code-csharp[ListInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitializer)]  
  
Koleksiyonun`Add` yöntemi izin veriyorsa, koleksiyon başlatıcısında bir öğe olarak [null](../../language-reference/keywords/null.md) belirtebilirsiniz.  
  
[!code-csharp[ListInitializerNull](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitialerWithNull)]  
  
 Koleksiyon okuma/yazma dizinlemeyi destekliyorsa, dizinli öğeleri belirtebilirsiniz.
  
[!code-csharp[DictionaryInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryIndexerInitializer)]  

Yukarıdaki örnek, <xref:System.Collections.Generic.Dictionary%602.Item(%600)> değerlerini ayarlamak için öğesini çağıran kodu oluşturur. C# 6 ' dan başlayarak, aşağıdaki sözdizimini kullanarak sözlükleri ve diğer İlişkilendirilebilir kapsayıcıları başlatabilirsiniz. Dizin Oluşturucu sözdizimi yerine parantez ve atama ile birden çok değerli bir nesne kullandığını fark edin:

[!code-csharp[DictionaryAddInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryAddInitializer)]  

Bu başlatıcı örneği, <xref:System.Collections.Generic.Dictionary%602.Add(%600,%601)> sözlüğe üç öğe eklemek için çağırır. İlişkilendirilebilir koleksiyonları başlatmanın bu iki farklı yolu, derleyicinin oluşturduğu Yöntem çağrıları nedeniyle biraz farklı davranışa sahiptir. Her iki çeşit de `Dictionary` sınıfla çalışır. Diğer türler, genel API 'lerine göre yalnızca bir veya diğerini destekleyebilir.

## <a name="examples"></a>Örnekler

Aşağıdaki örnek, nesne ve koleksiyon başlatıcıları kavramlarını birleştirir.

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullExample)]  

Aşağıdaki örnek, uygulayan <xref:System.Collections.IEnumerable> ve birden çok parametreli bir `Add` yöntemi içeren bir nesnesi gösterir, bu, `Add`biröğeiçinbiröğebaşınabirdençoköğeiçerenbirkoleksiyonbaşlatıcısıkullanıryöntemi.

[!code-csharp[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullListExample)]  

`Add`Yöntemler `params` anahtar sözcüğünü, aşağıdaki örnekte gösterildiği gibi değişken sayıda bağımsız değişken almak için kullanabilir. Bu örnek ayrıca dizin kullanarak bir koleksiyonu başlatmak için bir dizin oluşturucunun özel uygulamasını gösterir.

[!code-csharp[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullDictionaryInitializer)]  

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [LINQ sorgu Ifadeleri](../linq-query-expressions/index.md)
- [Anonim Tipler](anonymous-types.md)
