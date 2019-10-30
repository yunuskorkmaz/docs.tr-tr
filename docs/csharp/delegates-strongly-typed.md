---
title: Kesin Tür Belirtilmiş Temsilciler
description: Temsilci gerektiren bir özellik oluştururken özel türler bildirmek için genel temsilci türlerini nasıl kullanacağınızı öğrenin.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 564a683d-352b-4e57-8bac-b466529daf6b
ms.openlocfilehash: efdbef39d0e6bf2f07cde2c9621cec173e921752
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037356"
---
# <a name="strongly-typed-delegates"></a>Kesin Tür Belirtilmiş Temsilciler

[Öncekini](delegate-class.md)

Önceki makalede, `delegate` anahtar sözcüğünü kullanarak belirli temsilci türleri oluşturduğunuz gördünüz. 

Soyut temsilci sınıfı, gevşek bağlantısı ve çağırma için altyapıyı sağlar. Somut temsilci türleri, bir temsilci nesnesi için çağırma listesine eklenen yöntemler için tür güvenliğini benimseme ve zorlama açısından çok daha yararlı hale gelir. `delegate` anahtar sözcüğünü kullandığınızda ve somut bir temsilci türü tanımladığınızda, derleyici bu yöntemleri oluşturur.

Uygulamada, bu, farklı bir yöntem imzasına ihtiyacınız olduğunda yeni temsilci türleri oluşturulmasına neden olur. Bu iş bir süre sonra sıkıcı olabilir. Her yeni özellik yeni temsilci türleri gerektirir.

Ktam, bu gerekli değildir. .NET Core Framework, temsilci türlerine ihtiyacınız olduğunda yeniden kullanabileceğiniz çeşitli türler içerir. Bunlar, yeni yöntem bildirimlerine ihtiyacınız olduğunda özelleştirmeler bildirebilmeniz için [genel](programming-guide/generics/index.md) tanımlardır. 

Bu türlerin ilki <xref:System.Action> türüdür ve çeşitli çeşitlerdir:

```csharp
public delegate void Action();
public delegate void Action<in T>(T arg);
public delegate void Action<in T1, in T2>(T1 arg1, T2 arg2);
// Other variations removed for brevity.
```

Genel tür bağımsız değişkeninde `in` değiştirici, Kovaryans hakkındaki makalede ele alınmıştır.

<xref:System.Action%6016>gibi 16 ' ya kadar bağımsız değişken içeren `Action` temsilcisinin çeşitlemeleri vardır.
Bu tanımların her bir temsilci bağımsız değişkeni için farklı genel bağımsız değişkenler kullanması önemlidir: Bu, size en fazla esneklik sağlar. Yöntem bağımsız değişkenlerinin aynı olması gerekir, ancak aynı türde olabilir.

Void dönüş türüne sahip herhangi bir temsilci türü için `Action` türlerinden birini kullanın.

Framework Ayrıca değer döndüren temsilci türleri için kullanabileceğiniz çeşitli genel temsilci türleri içerir:

```csharp
public delegate TResult Func<out TResult>();
public delegate TResult Func<in T1, out TResult>(T1 arg);
public delegate TResult Func<in T1, in T2, out TResult>(T1 arg1, T2 arg2);
// Other variations removed for brevity
```

Sonuç genel tür bağımsız değişkeninde `out` değiştirici, Kovaryans hakkındaki makalede ele alınmıştır.

<xref:System.Func%6017>gibi 16 ' ya kadar giriş bağımsız değişkeni olan `Func` temsilcisinin çeşitlemeleri vardır.
Sonucun türü her zaman kuralına göre tüm `Func` bildirimlerinde son tür parametresidir.

Bir değer döndüren herhangi bir temsilci türü için `Func` türlerinden birini kullanın.

Ayrıca özelleştirilmiş bir <xref:System.Predicate%601> 
tek bir değer üzerinde bir test döndüren temsilcinin türü:

```csharp
public delegate bool Predicate<in T>(T obj);
```

Herhangi bir `Predicate` türü için yapısal olarak eşdeğer `Func` türünün var olduğunu fark edebilirsiniz:

```csharp
Func<string, bool> TestForString;
Predicate<string> AnotherTestForString;
```

Bu iki tür denk olduğunu düşünebilirsiniz. Bunlar değildir.
Bu iki değişken birbirlerinin yerine kullanılamaz. Bir tür değişkenine diğer tür atanamaz. C# Tür sistemi, yapıyı değil, tanımlı türlerin adlarını kullanır.

.NET Core kitaplığındaki tüm bu temsilci türü tanımları, oluşturduğunuz ve temsilci gerektiren yeni bir özellik için yeni bir temsilci türü tanımlamanız gerekmeyen anlamına gelir. Bu genel tanımlar çoğu durumda ihtiyacınız olan tüm temsilci türlerini sağlamalıdır. Gerekli tür parametreleriyle bu türlerden birini basitçe örnekleyebilirsiniz. Genel hale getirilebilir algoritmalar söz konusu olduğunda, bu Temsilciler genel türler olarak kullanılabilir. 

Bu süre zamandan tasarruf etmelidir ve temsilcilerle çalışmak için oluşturmanız gereken yeni tür sayısını en aza indirir.

Sonraki makalede, uygulama ortamında temsilcilerle çalışmaya yönelik birkaç ortak desen görürsünüz.

[Next](delegates-patterns.md)
