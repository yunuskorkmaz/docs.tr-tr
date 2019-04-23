---
title: Nesne ve koleksiyon başlatıcıları - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 12/19/2018
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
ms.openlocfilehash: 6c713072e120f2b5a6740add296c957d499c93c7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59978659"
---
# <a name="object-and-collection-initializers-c-programming-guide"></a>Nesne ve Koleksiyon Başlatıcıları (C# Programlama Kılavuzu)

C#bir nesnede veya koleksiyonda örneklemek ve tek bir deyimde üye atamalar gerçekleştirmek olanak sağlar.

## <a name="object-initializers"></a>Nesne başlatıcıları

Nesne başlatıcıları, oluşturma zamanında ardından atama deyimleri satırları gelecek şekilde bir oluşturucu çağırmak zorunda kalmadan, bir nesnenin istediğiniz erişilebilir alanlarına veya özelliklerine değerler atamanıza olanak tanır. Nesne başlatıcı sözdizimi, bir oluşturucu için bağımsız değişkenler belirtmenize veya bağımsız değişkenleri (ve parantez sözdizimini) atmanıza olanak tanır.  Aşağıdaki örnek, adlandırılmış bir türü ile bir nesne Başlatıcı kullanma işlemi gösterilmektedir `Cat` ve parametresiz bir oluşturucu çağırmak. Otomatik uygulanan özelliklerin kullanımına dikkat edin `Cat` sınıfı. Daha fazla bilgi için [Implemented Properties](auto-implemented-properties.md).  
  
[!code-csharp[ObjectInitializer1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#CatDeclaration)]  
[!code-csharp[ObjectInitializer1a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ObjectPropertyInitialization)]  
 
Nesne Başlatıcı sözdizimi örneği oluşturmanıza olanak sağlar ve sonra kendi atanan özelliklere sahip yeni oluşturulan nesne değişkeni ataması atar.

İle başlayarak C# 6, nesne başlatıcıları, Dizinleyicileri, alanlar ve Özellikler atama ek olarak ayarlayabilirsiniz. Bu temel göz önünde bulundurun `Matrix` sınıfı:

[!code-csharp[ObjectInitializer2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixDeclaration)]  

Aşağıdaki kod ile kimlik matrisi başlatabilir:

[!code-csharp[ObjectInitializer2a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixInitialization)]  

Erişilebilir bir Ayarlayıcısı içeren tüm erişilebilir bir dizin oluşturucu bağımsız değişkenlerinin türlerine ve sayı bağımsız olarak nesne Başlatıcı ifadelerinde biri olarak kullanılabilir. Dizin bağımsız değişkenler atamanın sol tarafındaki form ve ifadesinin sağ tarafı değerdir.  Örneğin, tüm geçerli ise bunlar `IndexersExample` uygun dizin oluşturucular sahiptir:

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

Derlemek, yukarıdaki kod için `IndexersExample` türü aşağıdaki üyeleri olması gerekir:

```csharp
public string name;
public double Size { set { ... }; }
public char this[int i] { set { ... }; }
public string this[char c, int i] {  set { ... }; }
}
```

## <a name="object-initializers-with-anonymous-types"></a>Anonim türlerde Nesne Başlatıcıları

Nesne başlatıcıları her bağlamda kullanılabilir olsa da, bunlar özellikle kullanışlı [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadelerinde. Sorgu ifadeleri, sık sık kullanırlar [anonim türler](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), hangi yalnızca başlatılabilir bir nesne Başlatıcı kullanarak aşağıdaki bildirimde gösterildiği gibi.  

```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```

Anonim türler etkinleştirme `select` yan tümcesinde bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu deyimi orijinal sıranın nesnelerini değeri ve şekli orijinalden farklı olabilir nesneleri dönüştürün. Bir sıradaki her bir nesneden elde edilen bilgilerin yalnızca bir kısmını depolamak isterseniz, bu kullanışlıdır. Aşağıdaki örnekte, varsayımında bir ürün nesnesinin (`p`) birçok alan ve yöntem içerir ve, yalnızca sırası oluşturmakla ilgili bilgi sahibi olduğunuz ürün adını ve birim fiyatı içerir.  
  
[!code-csharp[ObjectInitializer3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#AnonymousUse)]  

Bu sorgu yürütüldüğünde `productInfos` değişkeni erişilebilen bir nesne sırası içerecektir bir `foreach` Bu örnekte gösterildiği gibi deyimi:  

```csharp
foreach(var p in productInfos){...}  
```

Yeni anonim türdeki her bir nesnenin orijinal nesnedeki özelliklerle veya alanlarla aynı adları alan iki genel özelliği vardır. Ayrıca, anonim bir tür oluştururken bir alanı yeniden adlandırabilirsiniz; Aşağıdaki örnek yeniden adlandırır `UnitPrice` alanı `Price`.  

```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```

## <a name="collection-initializers"></a>Koleksiyon başlatıcıları

Koleksiyon başlatıcıları bir belirtmenize olanak tanır veya daha fazla öğe başlatıcıları bir koleksiyon başlattığınızda uygulayan türü <xref:System.Collections.IEnumerable> ve `Add` uygun imzalı bir örnek yöntemi veya bir genişletme yöntemi olarak. Öğe başlatıcıları basit bir değer, bir ifade veya bir nesne Başlatıcı olabilir. Koleksiyon Başlatıcısı kullanarak, birden çok çağrı belirtmeniz gerekmez; Derleyici çağrıları otomatik olarak ekler.  
  
Aşağıdaki örnek, iki basit koleksiyon başlatıcısını gösterir:  

```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```

Aşağıdaki koleksiyon Başlatıcısı nesnelerini başlatmak için nesne başlatıcıları kullanır `Cat` önceki bir örnekte tanımlanan sınıfı. Nesne başlatıcıların tek tek küme ayraçları içine alındığına ve virgüllerle ayrıldığına dikkat edin.  
  
[!code-csharp[ListInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitializer)]  
  
Belirtebileceğiniz [null](../../language-reference/keywords/null.md) bir koleksiyon başlatıcısında bir öğe olarak varsa koleksiyonun `Add` yöntemi sağlar.  
  
[!code-csharp[ListInitializerNull](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitialerWithNull)]  
  
 Dizinli öğeleri koleksiyonu destekleyen okuma / yazma dizin belirtebilirsiniz.
  
[!code-csharp[DictionaryInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryIndexerInitializer)]  

Önceki örnekte çağıran kodu üretir <xref:System.Collections.Generic.Dictionary%602.Item(%600)> değerleri ayarlamak için. İle başlayarak C# 6 başlatır sözlükleri ve diğer ilişkisel kapsayıcılar aşağıdaki söz dizimini kullanarak. Dizin Oluşturucu sözdizimi yerine parantez ve bir atama ile birden çok değer içeren bir nesne kullandığına dikkat edin:

[!code-csharp[DictionaryAddInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryAddInitializer)]  

Bu Başlatıcı örnek <xref:System.Collections.Generic.Dictionary%602.Add(%600,%601)> sözlüğe üç öğe eklemek için. İlişkili koleksiyonlar başlatmak için bu iki farklı şekilde derleyici oluşturur yöntem çağrıları nedeniyle biraz farklı davranışa sahip. Her iki çeşitleri çalışmak `Dictionary` sınıfı. Diğer türleri yalnızca bir diğer bağlı veya kendi genel API'sini destekleyebilir.

## <a name="examples"></a>Örnekler

Aşağıdaki örnek, nesne ve koleksiyon başlatıcıları kavramlarını birleştirir.

[!code-csharp-interactive[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullExample)]  

Uygulayan bir nesne aşağıdaki örnekte <xref:System.Collections.IEnumerable> ve içeren bir `Add` yöntemi ile birden çok parametre listedeki bir öğe başına imzasıiçinkarşılıkgelenbirdençoköğeiçerenbirkoleksiyonBaşlatıcısıkullanır,`Add`yöntemi.

[!code-csharp-interactive[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullListExample)]  

`Add` yöntemleri kullanabilir `params` anahtar sözcüğü bir değişken sayıda bağımsız değişken, aşağıdaki örnekte gösterildiği gibi gerçekleştirilecek. Bu örnekte ayrıca dizinleri kullanarak bir koleksiyonu başlatmak için bir dizin oluşturucu özel uygulanışı gösterilmektedir.

[!code-csharp-interactive[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullDictionaryInitializer)]  

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [LINQ Sorgu ifadeleri](../linq-query-expressions/index.md)
- [Anonim Tipler](anonymous-types.md)
