---
title: Kesin Tür Belirtilmiş Temsilciler
description: Temsilci gerektiren bir özellik oluştururken özel türleri bildirmek için genel temsilci türlerini nasıl kullanacağınızı öğrenin.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 564a683d-352b-4e57-8bac-b466529daf6b
ms.openlocfilehash: 798e8b597389bc99d10e587ec417a4e717f28abc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146209"
---
# <a name="strongly-typed-delegates"></a>Kesin Tür Belirtilmiş Temsilciler

[Önceki](delegate-class.md)

Önceki makalede, anahtar kelimeyi kullanarak belirli temsilci `delegate` türleri oluşturduğunuzu gördünuz.

Soyut Temsilci sınıfı gevşek bağlantı ve çağırma için altyapı sağlar. Somut Temsilci türleri, bir temsilci nesnesi için çağırma listesine eklenen yöntemler için tür güvenliğini kucaklayarak ve uygulayarak çok daha kullanışlı hale gelir. Anahtar sözcüğü `delegate` kullandığınızda ve somut bir temsilci türü tanımladığınızda, derleyici bu yöntemleri oluşturur.

Uygulamada, bu farklı bir yöntem imzası gerektiğinde yeni temsilci türleri oluşturmaya yol açar. Bu iş bir süre sonra sıkıcı olabilir. Her yeni özellik yeni temsilci türleri gerektirir.

Neyse ki buna gerek yok. .NET Core çerçevesi, temsilci türlerine ihtiyacınız olduğunda yeniden kullanabileceğiniz birkaç tür içerir. Bunlar [genel](programming-guide/generics/index.md) tanımlardır, böylece yeni yöntem bildirimlerine ihtiyaç duyduğunuzda özelleştirmeleri bildirebilirsiniz.

Bu türlerden <xref:System.Action> ilki tür ve çeşitli varyasyonları:

```csharp
public delegate void Action();
public delegate void Action<in T>(T arg);
public delegate void Action<in T1, in T2>(T1 arg1, T2 arg2);
// Other variations removed for brevity.
```

Genel `in` tür bağımsız değişkeninde değiştirici covariance makalede ele alınmıştır.

Temsilcinin `Action` 16'ya kadar bağımsız değişken içeren <xref:System.Action%6016>varyasyonları vardır.
Bu tanımların her bir temsilci bağımsız değişkeni için farklı genel bağımsız değişkenler kullanması önemlidir: Bu size maksimum esneklik sağlar. Yöntem bağımsız değişkenleri gerek meç, ancak olabilir, aynı türde.

Geçersiz dönüş `Action` türü olan herhangi bir temsilci türü için türlerden birini kullanın.

Çerçeve, değerleri döndüren temsilci türleri için kullanabileceğiniz birkaç genel temsilci türü de içerir:

```csharp
public delegate TResult Func<out TResult>();
public delegate TResult Func<in T1, out TResult>(T1 arg);
public delegate TResult Func<in T1, in T2, out TResult>(T1 arg1, T2 arg2);
// Other variations removed for brevity
```

Sonuç `out` genel türü bağımsız değişkeninde değiştirici, tutarlılık makalesinde ele alınmıştır.

`Func` 'ye kadar 16 giriş bağımsız değişkeni olan <xref:System.Func%6017>temsilcinin varyasyonları vardır.
Sonucun türü, tüm `Func` bildirimlerdeki son tür parametresi, konvansiyona göre her zaman dır.

Bir değer `Func` döndüren herhangi bir temsilci türü için türlerden birini kullanın.

Ayrıca özel bir<xref:System.Predicate%601>
tek bir değer üzerinde bir test döndüren bir temsilci için yazın:

```csharp
public delegate bool Predicate<in T>(T obj);
```

Herhangi bir `Predicate` tür için, yapısal olarak `Func` eşdeğer bir tür örneğin var fark edebilirsiniz:

```csharp
Func<string, bool> TestForString;
Predicate<string> AnotherTestForString;
```

Bu iki tür eşdeğer olduğunu düşünebilirsiniz. Değiller.
Bu iki değişken birbirinin yerine kullanılamaz. Bir türden bir değişken diğer türe atanamaz. C# türü sistem, yapıyı değil, tanımlanan türlerin adlarını kullanır.

.NET Core Kitaplığı'ndaki tüm bu temsilci türü tanımları, oluşturduğunuz herhangi bir yeni özellik için temsilci gerektiren yeni bir temsilci türü tanımlamanız gerekolmadığı anlamına gelir. Bu genel tanımlar, çoğu durumda gereksinim duyduğunuz tüm temsilci türlerini sağlamalıdır. Bu türlerden birini gerekli tür parametreleri ile anında kolayca anlayabilirsiniz. Genel yapIlebilen algoritmalar söz konusu olduğunda, bu temsilciler genel türler olarak kullanılabilir.

Bu, zamandan tasarruf etmeli ve temsilcilerle çalışmak için oluşturmanız gereken yeni türlerin sayısını en aza indirir.

Sonraki makalede, uygulamada temsilcilerle çalışmak için çeşitli ortak desenler görürsünüz.

[Sonraki](delegates-patterns.md)
