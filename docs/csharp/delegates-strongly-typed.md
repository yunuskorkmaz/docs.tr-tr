---
title: Kesin türü belirtilmiş temsilciler
description: Genel temsilci türleri temsilciler gerektiren bir özellik oluştururken, özel türler bildirmek için nasıl kullanılacağını öğrenin.
ms.date: 06/20/2016
ms.assetid: 564a683d-352b-4e57-8bac-b466529daf6b
ms.openlocfilehash: 2e4cc1c7bfa0aaa90f3aaefa0da64c5486a9d10f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215170"
---
# <a name="strongly-typed-delegates"></a>Kesin türü belirtilmiş temsilciler

[Önceki](delegate-class.md)

Önceki makalede belirli temsilci kullanarak türleri oluşturmak gördüğünüz `delegate` anahtar sözcüğü. 

Özet temsilci sınıf gevşek bağlantı ve çağırma için altyapı sağlar. Somut temsilci türleri kucaklamakta ve tür güvenliği için temsilci nesnesini çağırma listesine eklenen yöntemleri için zorlamayı göre çok daha yararlı olur. Kullandığınızda `delegate` anahtar sözcüğü ve somut temsilci türünü tanımlayın, bu yöntemleri derleyici oluşturur.

Uygulamada, bu farklı yöntem imzası gereksinim duyduğunuzda, yeni temsilci türleri oluşturmak için yol açar. Bir süre sonra bu işi sıkıcı. Her yeni özellik, yeni temsilci türleri gerektirir.

Thankfully, bu gerekli değildir. .NET Core framework türleri temsilci olduğunda yeniden kullanabilir birkaç türlerini içerir. Bunlar [genel](programming-guide/generics/index.md) yeni yöntem bildirimleri gerektiğinde özelleştirmeleri bildirebilir şekilde tanımlar. 

Bu tür ilk <xref:System.Action> türü ve birkaç Çeşitlemeler:

```csharp
public delegate void Action();
public delegate void Action<in T>(T arg);
public delegate void Action<in T1, in T2>(T1 arg1, T2 arg2);
// Other variations removed for brevity.
```

`in` Genel tür bağımsız değişkeni değiştiricisi Kovaryans makalede ele alınan.

Çeşidi vardır `Action` en fazla 16 bağımsız değişkenler gibi içeren temsilci <xref:System.Action%6016>.
Bu tanımları farklı genel değişkenleri temsilci değişkenin her biri için kullanın önemli: Bu, en büyük esnekliği sağlar. Yöntem bağımsız değişkenleri olmaması, ancak olabilir, aynı türde.

Aşağıdakilerden birini kullanmak `Action` türleri için geçersiz bir dönüş türüne sahip herhangi bir temsilci türü.

Framework de dönüş değerleri temsilci türleri için kullanabileceğiniz birkaç genel temsilci türleri içerir:

```csharp
public delegate TResult Func<out TResult>();
public delegate TResult Func<in T1, out TResult>(T1 arg);
public delegate TResult Func<in T1, in T2, out TResult>(T1 arg1, T2 arg2);
// Other variations removed for brevity
```

`out` Sonuç genel tür bağımsız değişkeni değiştiricisi Kovaryans makalede ele alınan.

Çeşidi vardır `Func` en fazla 16 giriş bağımsız değişkeni ile gibi temsilci <xref:System.Func%6017>.
Sonuç türü her zaman son türü tüm parametredir `Func` kural tarafından bildirimleri.

Aşağıdakilerden birini kullanmak `Func` türleri için bir değer döndürür herhangi bir temsilci türü.

Yoktur ayrıca özel <xref:System.Predicate%601> türü bir test üzerinde tek bir değer döndüren bir temsilci için:

```csharp
public delegate bool Predicate<in T>(T obj);
```

Sizin için değiştiğini görebilirsiniz `Predicate` türü, yapısal olarak eşdeğer `Func` türü mevcut örneğin:

```csharp
Func<string, bool> TestForString;
Predicate<string> AnotherTestForString;
```

Bu iki tür eşdeğer düşünebilirsiniz. Bunlar değildir.
Bu iki değişken birbirinin yerine kullanılamaz. Bir türde bir değişken diğer tür atanamaz. C# tür sistemi yapısı tanımlı türlerinin adlarını kullanır.

.NET Core kitaplığı tanımlarında herhangi bir yeni özellik için yeni bir temsilci türü tanımlamanız gerekmez anlamına Bu temsilci türü temsilciler gerektiren oluşturun. Bu genel tanımları tüm temsilci altında çoğu durumlar gereken türleri sağlamalıdır. Yalnızca gerekli tür parametreleri ile şu türlerden birine örneğini oluşturabilirsiniz. Genel hale getirilebilir algoritmaları söz konusu olduğunda, bu temsilciler genel türleri olarak kullanılabilir. 

Bu zamandan tasarruf ve temsilciler ile çalışması için oluşturmanıza gerek yeni türleri sayısını en aza indirin.

Sonraki makalede temsilciler uygulamada çalışmak için birkaç ortak desenler görürsünüz.

[Next](delegates-patterns.md)
