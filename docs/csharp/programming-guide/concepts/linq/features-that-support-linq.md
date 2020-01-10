---
title: LINQ'i Destekleyen C# Özellikleri
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
ms.openlocfilehash: 9fc8adaa49d02f8b69c2db6e94a28b9fab36b3b0
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635801"
---
# <a name="c-features-that-support-linq"></a>LINQ'i Destekleyen C# Özellikleri

Aşağıdaki bölümde 3,0 sürümünde C# tanıtılan yeni dil yapıları tanıtılmaktadır. Bu yeni özelliklerin tümü LINQ sorgularıyla bir dereceye kadar kullanılsa da, LINQ ile sınırlı değildir ve yararlı bulduğunuz herhangi bir bağlamda kullanılabilir.

## <a name="query-expressions"></a>Sorgu İfadeleri

Sorgu ifadeleri, IEnumerable koleksiyonlarını sorgulamak için SQL veya XQuery ile benzer bir bildirime dayalı sözdizimi kullanır. Derleme zamanı sorgu söz dizimi, bir LINQ sağlayıcısının standart sorgu işleci genişletme yöntemlerinin uygulamasına yönelik yöntem çağrılarına dönüştürülür. Uygulamalar, `using` yönergesi ile uygun ad alanını belirterek kapsamdaki standart sorgu işleçlerini denetler. Aşağıdaki sorgu ifadesi bir dize dizisi alır, bunları dizedeki ilk karaktere göre gruplandırır ve grupları sıralar.

```csharp
var query = from str in stringArray
            group str by str[0] into stringGroup
            orderby stringGroup.Key
            select stringGroup;
```

Daha fazla bilgi için bkz. [LINQ sorgu ifadeleri](../../../linq/index.md).

## <a name="implicitly-typed-variables-var"></a>Örtük olarak yazılan değişkenler (var)

Bir değişkeni bildirdiğinizde ve başlattığınızda açıkça bir tür belirtmek yerine, derleyicinin türü çıkarması ve atamasını bildirmek için, burada gösterildiği gibi [var](../../../language-reference/keywords/var.md) değiştiricisini kullanabilirsiniz:

```csharp
var number = 5;
var name = "Virginia";
var query = from str in stringArray
            where str[0] == 'm'
            select str;
```

`var` olarak belirtilen değişkenler, türü açıkça belirttiğiniz değişkenler olarak kesin olarak türdedir. `var` kullanımı anonim türler oluşturmayı mümkün kılar, ancak yalnızca yerel değişkenler için kullanılabilir. Diziler, örtük yazma ile de bildirilemez.

Daha fazla bilgi için bkz. [örtülü olarak yazılan yerel değişkenler](../../classes-and-structs/implicitly-typed-local-variables.md).

## <a name="object-and-collection-initializers"></a>Nesne ve Koleksiyon Başlatıcıları

Nesne ve koleksiyon başlatıcıları nesne için bir oluşturucu açıkça çağrılmadan nesneleri başlatmayı mümkün hale getirir. Başlatıcılar, genellikle, kaynak verileri yeni bir veri türüne proje yaparken sorgu ifadelerinde kullanılır. Ortak `Name` ve `Phone` özellikleriyle `Customer` adlı bir sınıf kabul edildiğinde, nesne Başlatıcısı aşağıdaki kodda olduğu gibi kullanılabilir:

```csharp
var cust = new Customer { Name = "Mike", Phone = "555-1212" };
```

`Customer` sınıfınız ile devam ederek, `IncomingOrders`adlı bir veri kaynağı olduğunu ve her bir sipariş için büyük bir `OrderSize`olan her sıra için bu siparişi temel alan yeni bir `Customer` oluşturmak istediğinizi varsayalım. Bir LINQ sorgusu bu veri kaynağında yürütülebilir ve bir koleksiyonu doldurarak nesne başlatma işlemi kullanılabilir:

```csharp
var newLargeOrderCustomers = from o in IncomingOrders
                            where o.OrderSize > 5
                            select new Customer { Name = o.Name, Phone = o.Phone };
```

Veri kaynağı, `OrderSize`gibi `Customer` sınıftan çok daha fazla özelliğe sahip olabilir, ancak nesne başlatma ile, sorgudan döndürülen veriler istenen veri türüne kopyalanır; sınıfımızla ilgili verileri seçtik. Sonuç olarak, şimdi yaptığımız yeni `Customer`s `IEnumerable`. Yukarıdaki, LINQ yöntem sözdiziminde de yazılabilir:

```csharp
var newLargeOrderCustomers = IncomingOrders.Where(x => x.OrderSize > 5).Select(y => new Customer { Name = y.Name, Phone = y.Phone });
```

Daha fazla bilgi için bkz.

- [Nesne ve Koleksiyon Başlatıcıları](../../classes-and-structs/object-and-collection-initializers.md)

- [Standart Sorgu İşleçleri için Sorgu İfade Sözdizimi](./query-expression-syntax-for-standard-query-operators.md)

## <a name="anonymous-types"></a>Anonim Türler

Anonim bir tür derleyici tarafından oluşturulur ve tür adı yalnızca derleyici tarafından kullanılabilir. Anonim türler, farklı bir adlandırılmış tür tanımlamak zorunda kalmadan bir özellik kümesini geçici olarak bir sorgu sonucuyla gruplamak için kullanışlı bir yol sağlar. Anonim türler aşağıda gösterildiği gibi yeni bir ifadeyle ve bir nesne başlatıcısıyla başlatılır:

```csharp
select new {name = cust.Name, phone = cust.Phone};
```

Daha fazla bilgi için bkz. [anonim türler](../../classes-and-structs/anonymous-types.md).

## <a name="extension-methods"></a>Genişletme Yöntemleri

Uzantı yöntemi, bir tür ile ilişkilendirilebilen statik bir yöntemdir ve bu sayede tür üzerinde bir örnek yöntemi gibi çağrılabilir. Bu özellik, etkin bir şekilde, var olan türlere "Ekle" gibi yeni yöntemler eklemenizi sağlar. Standart sorgu işleçleri, <xref:System.Collections.Generic.IEnumerable%601>uygulayan herhangi bir tür için LINQ sorgu işlevselliği sağlayan bir genişletme yöntemleri kümesidir.

Daha fazla bilgi için bkz. [Uzantı yöntemleri](../../classes-and-structs/extension-methods.md).

## <a name="lambda-expressions"></a>Lambda İfadeleri

Lambda ifadesi, işlev gövdesinden giriş parametrelerini ayırmak için = > işlecini kullanan ve derleme zamanında bir temsilciye veya bir ifade ağacına dönüştürülebilen bir satır içi işlevdir. LINQ programlamada, standart sorgu işleçleri için doğrudan Yöntem çağrıları yaptığınızda lambda ifadeleriyle karşılaşacaksınız.

Daha fazla bilgi için bkz.

- [Anonim İşlevler](../../statements-expressions-operators/anonymous-functions.md)

- [Lambda İfadeleri](../../statements-expressions-operators/lambda-expressions.md)

- [İfade ağaçları (C#)](../expression-trees/index.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Dil ile tümleşik sorgu (LINQ) (C#)](./index.md)
