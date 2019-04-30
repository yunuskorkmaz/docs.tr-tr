---
title: Kesin tür belirtilmiş temsilciler
description: Özel türler temsilciler gerektiren bir özellik oluştururken bildirmek için genel temsilci türleriyle kullanmayı öğrenin.
ms.date: 06/20/2016
ms.assetid: 564a683d-352b-4e57-8bac-b466529daf6b
ms.openlocfilehash: 2e4cc1c7bfa0aaa90f3aaefa0da64c5486a9d10f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646666"
---
# <a name="strongly-typed-delegates"></a>Kesin tür belirtilmiş temsilciler

[Önceki](delegate-class.md)

Önceki makalede türleri kullanarak belirli bir temsilci oluşturmak, gördüğünüz `delegate` anahtar sözcüğü. 

Soyut temsilci sınıfı gevşek eşleştirme ve çağırma için altyapı sağlar. Somut temsilci türleri benimsemenin ve tür güvenliği için bir temsilci nesnesini çağırma listesine eklenen yöntemleri için zorlama göre çok daha kullanışlı olur. Kullanırken `delegate` anahtar sözcüğü ve bir somut bir temsilci türü tanımlamak, derleyici bu yöntemleri oluşturur.

Uygulamada, bu farklı yöntem imzası ihtiyaç duyduğunuzda, yeni temsilci türlerini oluşturmak için yol açar. Bir süre sonra bu iş sıkıcı. Her yeni özellik, yeni temsilci türleri gerektirir.

Ne bu gerekli değildir. .NET Core framework temsilci türleri olduğunda yeniden kullanabileceğiniz çeşitli türleri içerir. Bunlar [genel](programming-guide/generics/index.md) yeni yöntem bildirimleri gerektiğinde özelleştirmeleri bildirebilirsiniz şekilde tanımlar. 

Bu türlerinin ilki <xref:System.Action> türü ve çeşitli kullanımları tercih edilebilir:

```csharp
public delegate void Action();
public delegate void Action<in T>(T arg);
public delegate void Action<in T1, in T2>(T1 arg1, T2 arg2);
// Other variations removed for brevity.
```

`in` Makalede Kovaryans genel tür bağımsız değişkeni değiştiricisi alınmıştır.

Çeşidi vardır `Action` gibi en fazla 16 bağımsız değişkenleri içeren bir temsilci <xref:System.Action%6016>.
Bu tanımları temsilci değişkenin her biri için farklı genel bağımsız değişkenleri kullanmak önemlidir: Bu, en yüksek esnekliği sağlar. Yöntem bağımsız değişkenleri olmaması, ancak olabilir, aynı türde.

Birini `Action` türleri için dönüş türü void olan herhangi bir temsilci türü.

Framework, dönüş değerleri temsilci türleri için kullanabileceğiniz çeşitli genel temsilci türleriyle de içerir:

```csharp
public delegate TResult Func<out TResult>();
public delegate TResult Func<in T1, out TResult>(T1 arg);
public delegate TResult Func<in T1, in T2, out TResult>(T1 arg1, T2 arg2);
// Other variations removed for brevity
```

`out` Sonucu genel tür bağımsız değişkeni değiştiricisi Kovaryans makalede ele alınmaktadır.

Çeşidi vardır `Func` gibi en fazla 16 giriş bağımsız değişkeni ile temsilci <xref:System.Func%6017>.
Sonuç türü her zaman son tür parametresinde tüm olan `Func` bildirimleri, kural tarafından.

Birini `Func` türleri için bir değer döndüren bir temsilci türü.

Var. Ayrıca özelleştirilmiş <xref:System.Predicate%601> 
bir test üzerinde tek bir değer döndüren bir temsilci için şunu yazın:

```csharp
public delegate bool Predicate<in T>(T obj);
```

Sizin için değiştiğini görebilirsiniz `Predicate` türü, yapısal olarak eşdeğer `Func` türü mevcut örneğin:

```csharp
Func<string, bool> TestForString;
Predicate<string> AnotherTestForString;
```

Bu iki tür eşdeğerdir düşünebilirsiniz. Değiller.
Bu iki değişken birbirinin yerine kullanılamaz. Bir değişken, bir tür diğer türden atanamaz. C# Tür sistemi yapısı tanımlanmış türlerinin adlarını kullanır.

.NET Core kitaplığı'nda tanımları herhangi bir yeni özellik için yeni bir temsilci türü tanımlayan gerekmez anlamına Bu temsilci türü temsilciler gerektiren oluşturun. Bu genel tanımları tüm temsilci türleri çoğu durumlarda ihtiyacınız sağlamanız gerekir. Yalnızca gerekli tür parametreleri ile şu türlerden birinde örneği oluşturabilir. Genel hale getirilebilir algoritmaları söz konusu olduğunda, bu temsilcileri genel türleri olarak kullanılabilir. 

Bu zamandan tasarruf edin ve temsilciler ile çalışmak için oluşturmanız gereken yeni türleri sayısını en aza indirin.

Sonraki makalede, temsilciler uygulamada çalışmaya yönelik birçok ortak deseni görürsünüz.

[Next](delegates-patterns.md)
