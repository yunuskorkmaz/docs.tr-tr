---
title: LINQ'i Destekleyen C# Özellikleri
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
ms.openlocfilehash: d0b35bec3bbc30f411a705220c468fa8961b83cb
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58186032"
---
# <a name="c-features-that-support-linq"></a>LINQ'i Destekleyen C# Özellikleri

Aşağıdaki bölümde, C# 3.0 sürümünde sunulan yeni dil yapıları sunar. Bu yeni özelliklerin tümünü bir dereceye kullanılsa [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgular olmadıkları için sınırlı [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] ve burada, bunları kullanışlı her bağlamda kullanılabilir.

## <a name="query-expressions"></a>Sorgu İfadeleri

Sorgu ifadeleri IEnumerable koleksiyonları sorgulamak için SQL veya XQuery benzer bir tanımlayıcı sözdizimi kullanın. Derleme zamanı sorgu sözdizimi yöntem çağrıları için dönüştürülür bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sağlayıcısının uygulaması standart sorgu işleci genişletme yöntemleri. Uygulama Denetim uygun ad belirterek kapsamındaki standart sorgu işleçleri bir `using` yönergesi. Aşağıdaki sorgu ifadesi dizisini alır, bunları dizedeki ilk karakter göre gruplandırır ve grupları sıralar.

```csharp
var query = from str in stringArray
            group str by str[0] into stringGroup
            orderby stringGroup.Key
            select stringGroup;
```

Daha fazla bilgi için [LINQ Sorgu ifadeleri](../../../../csharp/programming-guide/linq-query-expressions/index.md).

## <a name="implicitly-typed-variables-var"></a>Örtük olarak yazılan değişkenler (var)

Kullanabileceğiniz bildirme ve bir değişkeni başlatarak, açıkça bir tür belirtmek yerine, [var](../../../../csharp/language-reference/keywords/var.md) çıkarır ve atamak için burada gösterildiği gibi derleyicisinin değiştiricisi:

```csharp
var number = 5;
var name = "Virginia";
var query = from str in stringArray
            where str[0] == 'm'
            select str;
```

Olarak bildirilen değişkenler `var` yalnızca olarak türünü açıkça belirtmeniz değişkenleri olarak kesin olan. Kullanımını `var` anonim türler, ancak oluşturmak mümkün kullanılabileceği için yalnızca yerel değişkenler yapar. Diziler de örtülü yazma ile bildirilebilir.

Daha fazla bilgi için [örtük olarak yazılan yerel değişkenler](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).

## <a name="object-and-collection-initializers"></a>Nesne ve Koleksiyon Başlatıcıları

Nesne ve koleksiyon başlatıcıları nesne için açıkça bir oluşturucu çağırmaya gerek kalmadan nesneleri başlatmak mümkün kılar. Bunlar kaynak verileri yeni bir veri türüne projenizin başlatıcılar genellikle sorgu ifadelerinde kullanılır. Adlı bir sınıf varsayılarak `Customer` ortak `Name` ve `Phone` nesne Başlatıcı özellikleri, aşağıdaki kodda gösterildiği gibi kullanılabilir:

```csharp
Customer cust = new Customer { Name = "Mike", Phone = "555-1212" };
```

Devam etmeden bizim `Customer` sınıfı, adlandırılan bir veri kaynağı olduğunu varsayın `IncomingOrders`ve her sipariş büyük ile ilgili `OrderSize`, yeni bir istiyoruz `Customer` dışına o sırada temel. LINQ sorgusu, bu veri kaynağında yürütülen ve bir koleksiyonu doldurmak için nesne başlatmayı kullanın:

```csharp
var newLargeOrderCustomers = from o in IncomingOrders
                            where o.OrderSize > 5
                            select new Customer { Name = o.Name, Phone = o.Phone };
```

Veri kaynağını daha fazla özellik dizinimizin duran olabilir `Customer` gibi sınıf `OrderSize`, ancak ile nesne başlatmayı, istenen veri türüne sorgudan döndürülen verileri ekleme; biz bizim sınıfına ilgili verileri seçin. Sonuç olarak, artık sahip olduğumuz bir `IEnumerable` yeni doldurulmuş `Customer`s istedik. Yukarıdaki, ayrıca LINQ'ın yöntemi sözdiziminde yazılabilir:

```csharp
var newLargeOrderCustomers = IncomingOrders.Where(x => x.OrderSize > 5).Select(y => new Customer { Name = y.Name, Phone = y.Phone });
```

Daha fazla bilgi için bkz.:

- [Nesne ve Koleksiyon Başlatıcıları](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)

- [Standart Sorgu İşleçleri için Sorgu İfade Sözdizimi](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)

## <a name="anonymous-types"></a>Anonim Türler

Anonim bir tür derleyici tarafından oluşturulmuş olan ve yalnızca tür adı derleyici için kullanılabilir. Anonim türler bir sorgu sonucu özelliklerinde geçici olarak bir dizi türü adlı ayrı bir tanımlamak zorunda kalmadan gruplandırmak için kullanışlı bir yol sağlar. Anonim türler, burada gösterildiği gibi bir new ifadesi ve bir nesne Başlatıcı ile başlatılır:

```csharp
select new {name = cust.Name, phone = cust.Phone};
```

Daha fazla bilgi için [anonim türler](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).

## <a name="extension-methods"></a>Genişletme Yöntemleri

Böylece türünde bir örnek yöntemi gibi çağrılabilen bir genişletme yöntemi, bir tür ile ilişkilendirilebilir bir statik yöntemidir. Bu özellik, aslında "yeni yöntemler varolan türleri için bunları gerçekten değiştirmeden eklemek," sağlar. Standart sorgu işleçleri sağlayan genişletme yöntemleri kümesidir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] işlevselliğini uygulayan herhangi bir türü için sorgu <xref:System.Collections.Generic.IEnumerable%601>.

Daha fazla bilgi için [genişletme yöntemleri](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).

## <a name="lambda-expressions"></a>Lambda İfadeleri

Bir lambda ifadesi = kullanan bir satır içi işlevdir > işleci ayırmak için giriş parametreleri işlevi gövdesinden ve derleme zamanında bir temsilci veya ifade ağacı dönüştürülebilir. İçinde [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] standart sorgu işleçleri için doğrudan yöntem çağrıları yaptığınızda programlama, lambda ifadeleri karşılaşırsınız.

Daha fazla bilgi için bkz.:

- [Anonim İşlevler](../../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)

- [Lambda İfadeleri](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)

- [İfade ağaçları (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Dil ile tümleşik sorgu (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)
