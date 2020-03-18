---
title: LINQ'i Destekleyen C# Özellikleri
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
ms.openlocfilehash: 9fc8adaa49d02f8b69c2db6e94a28b9fab36b3b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635801"
---
# <a name="c-features-that-support-linq"></a>LINQ'i Destekleyen C# Özellikleri

Aşağıdaki bölümde C# 3.0'da tanıtılan yeni dil yapıları tanıtılır. Bu yeni özelliklerin tümü LINQ sorgularında bir dereceye kadar kullanılsa da, linq ile sınırlı değildir ve bunları yararlı bulduğunuz herhangi bir bağlamda kullanılabilir.

## <a name="query-expressions"></a>Sorgu İfadeleri

Sorgu ifadeleri, Tamamlanamayan koleksiyonlar üzerinde sorgulamak için SQL veya XQuery'ye benzer bir bildirim sözdizimi kullanır. Derleme zaman sorgu sözdizimi, bir LINQ sağlayıcısının standart sorgu işleci uzantısı yöntemlerini uygulamasına yöntem çağrılarına dönüştürülür. Uygulamalar, bir `using` yönergeyle uygun ad alanını belirterek kapsamda olan standart sorgu işleçlerini denetler. Aşağıdaki sorgu ifadesi bir dizi dize alır, dizedeki ilk karaktere göre gruplanır ve grupları emreder.

```csharp
var query = from str in stringArray
            group str by str[0] into stringGroup
            orderby stringGroup.Key
            select stringGroup;
```

Daha fazla bilgi için [LINQ Sorgu İfadeleri'ne](../../../linq/index.md)bakın.

## <a name="implicitly-typed-variables-var"></a>Örtülü Olarak Yazılan Değişkenler (var)

Bir değişkeni beyan ve başharfe çevirirken bir türü açıkça belirtmek yerine, burada gösterildiği gibi derleyiciye türü çıkartmasını ve atamasını bildirmek için [var](../../../language-reference/keywords/var.md) değiştiricisini kullanabilirsiniz:

```csharp
var number = 5;
var name = "Virginia";
var query = from str in stringArray
            where str[0] == 'm'
            select str;
```

Olarak `var` bildirilen değişkenler, türünü açıkça belirttiğiniz değişkenler kadar güçlü bir şekilde yazılır. Kullanımı, `var` anonim türleri oluşturmayı mümkün kılar, ancak yalnızca yerel değişkenler için kullanılabilir. Diziler de örtülü yazarak ilan edilebilir.

Daha fazla bilgi için [bkz.](../../classes-and-structs/implicitly-typed-local-variables.md)

## <a name="object-and-collection-initializers"></a>Nesne ve Koleksiyon Başlatıcıları

Nesne ve koleksiyon başharfleri, nesne için açıkça bir oluşturucu çağırmadan nesneleri başlatmayı mümkün kılar. Başlangıç layıcılar genellikle kaynak verileri yeni bir veri türüne yansıttığında sorgu ifadelerinde kullanılır. Ortak `Name` ve `Phone` `Customer` özellikleri ile adlı bir sınıf varsayarsak, nesne baş harfizer aşağıdaki kod olarak kullanılabilir:

```csharp
var cust = new Customer { Name = "Mike", Phone = "555-1212" };
```

Sınıfımıza `Customer` devam ederek, "büyük" adlı `IncomingOrders`bir veri kaynağı olduğunu ve `OrderSize`her sipariş için bu `Customer` siparişten yeni bir tabanlı oluşturmak istediğimizi varsayalım. Bir LINQ sorgusu bu veri kaynağında yürütülebilir ve bir koleksiyonu doldurmak için nesne başlatmayı kullanabilir:

```csharp
var newLargeOrderCustomers = from o in IncomingOrders
                            where o.OrderSize > 5
                            select new Customer { Name = o.Name, Phone = o.Phone };
```

Veri kaynağı, başlık `Customer` altında sınıf , `OrderSize`ancak nesne başlatma ile, sorgudan döndürülen veri istenilen veri türüne kalıplanmış daha fazla özelliklere sahip olabilir; sınıfımızla ilgili verileri seçeriz. Sonuç olarak, şimdi istediğimiz `IEnumerable` yeni `Customer`s ile dolu bir var. Yukarıdaki ler LINQ'nin yöntem sözdiziminde de yazılabilir:

```csharp
var newLargeOrderCustomers = IncomingOrders.Where(x => x.OrderSize > 5).Select(y => new Customer { Name = y.Name, Phone = y.Phone });
```

Daha fazla bilgi için bkz.

- [Nesne ve Koleksiyon Başlatıcıları](../../classes-and-structs/object-and-collection-initializers.md)

- [Standart Sorgu İşleçleri için Sorgu İfade Sözdizimi](./query-expression-syntax-for-standard-query-operators.md)

## <a name="anonymous-types"></a>Anonim Türler

Anonim bir tür derleyici tarafından oluşturulur ve tür adı yalnızca derleyici için kullanılabilir. Adsız türler, ayrı bir adlandırılmış tür tanımlamak zorunda kalmadan, bir dizi özelliği geçici olarak sorgu sonucuna gruplandırmak için kullanışlı bir yol sağlar. Anonim türleri burada gösterildiği gibi, yeni bir ifade ve bir nesne baş harfi ile baş harfe

```csharp
select new {name = cust.Name, phone = cust.Phone};
```

Daha fazla bilgi için [Bkz. Anonim Türler.](../../classes-and-structs/anonymous-types.md)

## <a name="extension-methods"></a>Genişletme Yöntemleri

Uzantı yöntemi, bir türle ilişkilendirilebilen statik bir yöntemdir, böylece türüzerinde bir örnek yöntemi yatılabilir. Bu özellik, gerçekte, gerçekte bunları değiştirmeden varolan türlere yeni yöntemler "eklemek" sağlar. Standart sorgu işleçleri, linq sorgusu işlevselliği sağlayan bir uzantı yöntemi kümesidir. <xref:System.Collections.Generic.IEnumerable%601>

Daha fazla bilgi için [Uzantı Yöntemleri'ne](../../classes-and-structs/extension-methods.md)bakın.

## <a name="lambda-expressions"></a>Lambda İfadeleri

Lambda ifadesi, giriş parametrelerini işlev gövdesinden ayırmak için => işleci kullanan ve derleme zamanında bir temsilciye veya bir ifade ağacına dönüştürülebilen bir satır dışı işlevdir. LINQ programlamada, standart sorgu işleçlerine doğrudan yöntem aramaları yaptığınızda lambda ifadelerle karşılaşırsınız.

Daha fazla bilgi için bkz.

- [Anonim Fonksiyonlar](../../statements-expressions-operators/anonymous-functions.md)

- [Lambda İfadeler](../../statements-expressions-operators/lambda-expressions.md)

- [İfade Ağaçları (C#)](../expression-trees/index.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Dil-Tümleşik Sorgu (LINQ) (C#)](./index.md)
