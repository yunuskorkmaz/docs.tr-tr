---
title: LINQ'i Destekleyen C# Özellikleri
description: LINQ sorgularıyla ve diğer bağlamlarda kullanılacak C# özellikleri hakkında bilgi edinin. Bu dil yapıları C# 3,0 ' de tanıtılmıştır.
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
ms.openlocfilehash: 13254c69193e04ffcf11e3e23f1deb460063a6c1
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063698"
---
# <a name="c-features-that-support-linq"></a>LINQ'i Destekleyen C# Özellikleri

Aşağıdaki bölümde C# 3,0 ' de tanıtılan yeni dil yapıları tanıtılmaktadır. Bu yeni özelliklerin tümü LINQ sorgularıyla bir dereceye kadar kullanılsa da, LINQ ile sınırlı değildir ve yararlı bulduğunuz herhangi bir bağlamda kullanılabilir.

## <a name="query-expressions"></a>Sorgu İfadeleri

Sorgu ifadeleri, IEnumerable koleksiyonlarını sorgulamak için SQL veya XQuery ile benzer bir bildirime dayalı sözdizimi kullanır. Derleme zamanı sorgu söz dizimi, bir LINQ sağlayıcısının standart sorgu işleci genişletme yöntemlerinin uygulamasına yönelik yöntem çağrılarına dönüştürülür. Uygulamalar, uygun ad alanını bir yönergeyle belirterek kapsamdaki standart sorgu işleçlerini denetler `using` . Aşağıdaki sorgu ifadesi bir dize dizisi alır, bunları dizedeki ilk karaktere göre gruplandırır ve grupları sıralar.

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

Olarak belirtilen değişkenler `var` , türü açıkça belirttiğiniz değişkenler olarak kesin şekilde türdedir. Öğesinin kullanımı `var` anonim türler oluşturmayı mümkün kılar, ancak yalnızca yerel değişkenler için kullanılabilir. Diziler, örtük yazma ile de bildirilemez.

Daha fazla bilgi için bkz. [örtülü olarak yazılan yerel değişkenler](../../classes-and-structs/implicitly-typed-local-variables.md).

## <a name="object-and-collection-initializers"></a>Nesne ve Koleksiyon Başlatıcıları

Nesne ve koleksiyon başlatıcıları nesne için bir oluşturucu açıkça çağrılmadan nesneleri başlatmayı mümkün hale getirir. Başlatıcılar, genellikle, kaynak verileri yeni bir veri türüne proje yaparken sorgu ifadelerinde kullanılır. Public ve Properties ile adlandırılmış bir sınıf varsayıldığında `Customer` `Name` `Phone` , nesne Başlatıcısı aşağıdaki kodda olduğu gibi kullanılabilir:

```csharp
var cust = new Customer { Name = "Mike", Phone = "555-1212" };
```

Sınıfımızla devam ederek, `Customer` adlı bir veri kaynağı olduğunu `IncomingOrders` ve her sıra büyük bir sipariş için bu `OrderSize` sırada yeni bir temel oluşturmak istiyoruz `Customer` . Bir LINQ sorgusu bu veri kaynağında yürütülebilir ve bir koleksiyonu doldurarak nesne başlatma işlemi kullanılabilir:

```csharp
var newLargeOrderCustomers = from o in IncomingOrders
                            where o.OrderSize > 5
                            select new Customer { Name = o.Name, Phone = o.Phone };
```

Veri kaynağı, gibi bir sınıftan çok daha fazla özelliğe sahip olabilir `Customer` `OrderSize` , ancak nesne başlatma ile sorgudan döndürülen veriler istenen veri türüne kopyalanır; sınıfımızla ilgili verileri seçiyoruz. Sonuç olarak, şimdi `IEnumerable` `Customer` yaptığımız yeni s 'leri doldurduk. Yukarıdaki, LINQ yöntem sözdiziminde de yazılabilir:

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

Uzantı yöntemi, bir tür ile ilişkilendirilebilen statik bir yöntemdir ve bu sayede tür üzerinde bir örnek yöntemi gibi çağrılabilir. Bu özellik, etkin bir şekilde, var olan türlere "Ekle" gibi yeni yöntemler eklemenizi sağlar. Standart sorgu işleçleri, uygulayan herhangi bir tür için LINQ sorgu işlevselliği sağlayan bir genişletme yöntemleri kümesidir <xref:System.Collections.Generic.IEnumerable%601> .

Daha fazla bilgi için bkz. [Uzantı yöntemleri](../../classes-and-structs/extension-methods.md).

## <a name="lambda-expressions"></a>Lambda İfadeleri

Lambda ifadesi, işlev gövdesinden giriş parametrelerini ayırmak için => işlecini kullanan ve derleme zamanında bir temsilciye veya bir ifade ağacına dönüştürülebilen bir satır içi işlevdir. LINQ programlamada, standart sorgu işleçleri için doğrudan Yöntem çağrıları yaptığınızda lambda ifadeleriyle karşılaşacaksınız.

Daha fazla bilgi için bkz.

- [Anonim Işlevler](../../statements-expressions-operators/anonymous-functions.md)

- [Lambda Ifadeleri](../../../language-reference/operators/lambda-expressions.md)

- [İfade ağaçları (C#)](../expression-trees/index.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Dil ile tümleşik sorgu (LINQ) (C#)](./index.md)
