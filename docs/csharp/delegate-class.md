---
title: System. Delegate ve `delegate` anahtar sözcüğü
description: Temsilcileri destekleyen ve bunların ' Delegate ' anahtar sözcüğüyle nasıl eşlendikleri .NET sınıfları hakkında bilgi edinin.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: f3742fda-13c2-4283-8966-9e21c2674393
ms.openlocfilehash: 9df8ad68f6bfa62863ee047875b6419fc81ad779
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062476"
---
# <a name="systemdelegate-and-the-delegate-keyword"></a>System. Delegate ve `delegate` anahtar sözcüğü

[Önceki](delegates-overview.md)

Bu makalede temsilcileri destekleyen .NET sınıfları ve bunların anahtar kelimesiyle nasıl eşlendikleri ele alınmaktadır `delegate` .

## <a name="define-delegate-types"></a>Temsilci türlerini tanımlama

' Delegate ' anahtar sözcüğüyle başlayalım, çünkü bu aslında temsilcilerle çalışırken kullanacağınız şeydir. Anahtar sözcüğünü kullandığınızda derleyicinin ürettiği kod, `delegate` ve sınıflarının üyelerini çağıran yöntem çağrılarına eşlenir <xref:System.Delegate> <xref:System.MulticastDelegate> .

Yöntem imzasını tanımlamaya benzer bir sözdizimi kullanarak bir temsilci türü tanımlarsınız. `delegate`Anahtar sözcüğünü yalnızca tanımına eklersiniz.

Bizim örneğimizde List. Sort () yöntemini kullanmaya devam edelim. İlk adım, karşılaştırma temsilcisi için bir tür oluşturmaktır:

```csharp
// From the .NET Core library

// Define the delegate type:
public delegate int Comparison<in T>(T left, T right);
```

Derleyici, kullanılan imzayla eşleşen bir sınıf oluşturur `System.Delegate` (Bu durumda, bir tamsayı döndüren ve iki bağımsız değişkeni olan bir yöntem). Bu temsilcinin türü `Comparison` . `Comparison`Temsilci türü genel bir tür. Genel türler hakkında daha fazla bilgi için [buraya](programming-guide/generics/index.md)bakın.

Sözdiziminin bir değişken bildirmiş gibi görünebileceğini ancak gerçekten bir *tür*bildirdiğine dikkat edin. Sınıf içinde doğrudan ad alanları içinde veya genel ad alanında temsilci türleri tanımlayabilirsiniz.

> [!NOTE]
> Temsilci türlerinin (veya diğer türlerin) doğrudan genel ad alanında bildirilmesi önerilmez.

Derleyici Ayrıca bu yeni tür için ekleme ve kaldırma işleyicileri üretir. bu sayede, bu sınıfın istemcileri bir örneğin çağrı listesinden Yöntem ekleyebilir ve kaldırabilir. Derleyici, eklenen veya kaldırılan yöntemin imzasının, yöntemi bildirirken kullanılan imza ile eşleştiğinden zorlanır.

## <a name="declare-instances-of-delegates"></a>Temsilcilerin örneklerini bildirme

Temsilciyi tanımladıktan sonra, bu türün bir örneğini oluşturabilirsiniz.
C# ' deki tüm değişkenler gibi, temsilci örneklerini doğrudan bir ad alanında veya genel ad alanında bildiremezsiniz.

```csharp
// inside a class definition:

// Declare an instance of that type:
public Comparison<T> comparator;
```

Değişkenin türü `Comparison<T>` , daha önce tanımlanan temsilci türüdür. Değişkenin adı `comparator` .

 Yukarıdaki kod parçacığı, bir sınıf içinde bir üye değişkeni bildirdi. Yerel değişkenler veya yöntemler için bağımsız değişkenler olan temsilci değişkenlerini de bildirebilirsiniz.

## <a name="invoke-delegates"></a>Temsilcileri çağır

Bu temsilciyi çağırarak bir temsilcinin çağırma listesindeki yöntemleri çağırabilirsiniz. Yöntemi içinde `Sort()` , kod, nesnelerin yerleştirileceği sırayı belirleyen karşılaştırma yöntemini çağırır:

```csharp
int result = comparator(left, right);
```

Yukarıdaki satırda kod, temsilciye iliştirilmiş yöntemi *çağırır* .
Değişkeni bir yöntem adı olarak değerlendirir ve normal Yöntem çağrısı söz dizimini kullanarak çağırılır.

Bu kod satırı güvenli olmayan bir varsayımına neden olur: temsilciye bir hedefin eklendiğinden emin olmaz. Hiçbir hedef iliştirilmişse yukarıdaki satır bir oluşturulmasına neden olur `NullReferenceException` . Bu sorunu gidermek için kullanılan ıoms, basit bir null denetiminden daha karmaşıktır ve bu [serinin](delegates-patterns.md)ilerleyen kısımlarında ele alınmıştır.

## <a name="assign-add-and-remove-invocation-targets"></a>Çağırma hedeflerini atama, ekleme ve kaldırma

Temsilci türünün tanımlanması ve temsilci örneklerinin nasıl bildirildiği ve çağrıldığı.

Yöntemini kullanmak isteyen geliştiriciler, `List.Sort()` imzası temsilci türü tanımıyla eşleşen bir yöntem tanımlamak ve bunu sıralama yöntemi tarafından kullanılan temsilciye atamalıdır. Bu atama, yöntemi bu temsilci nesnesinin çağırma listesine ekler.

Dizelerin bir listesini uzunluğuna göre sıralamak istediğinizi varsayalım. Karşılaştırma işleviniz aşağıdaki gibi olabilir:

```csharp
private static int CompareLength(string left, string right) =>
    left.Length.CompareTo(right.Length);
```

Yöntemi özel bir yöntem olarak bildirilmiştir. Bu çok güzel. Bu yöntemin ortak arayüzün bir parçası olmasını istemeyebilirsiniz. Bir temsilciye eklendiğinde karşılaştırma yöntemi olarak yine de kullanılabilir. Çağıran kod bu yöntemi temsilci nesnesinin hedef listesine iliştirilir ve bu temsilci aracılığıyla erişebilir.

Yöntemi yöntemine geçirerek bu ilişkiyi oluşturursunuz `List.Sort()` :

```csharp
phrases.Sort(CompareLength);
```

Yöntem adının parantez olmadan kullanıldığına dikkat edin. Yöntemin bağımsız değişken olarak kullanılması, derleyicinin Yöntem başvurusunu temsilci çağırma hedefi olarak kullanılabilecek bir başvuruya dönüştürmesini ve bu yöntemi bir çağırma hedefi olarak iliştirmesine söyler.

Ayrıca, türünde bir değişken bildirerek ve ödev yaparak da açık olabilirsiniz `Comparison<string>` :

```csharp
Comparison<string> comparer = CompareLength;
phrases.Sort(comparer);
```

' De, bir temsilci hedefi olarak kullanılan yöntemin küçük bir yöntem olduğu durumlarda, atamayı gerçekleştirmek için [lambda ifadesi](language-reference/operators/lambda-expressions.md) sözdizimini kullanmak yaygındır:

```csharp
Comparison<string> comparer = (left, right) => left.Length.CompareTo(right.Length);
phrases.Sort(comparer);
```

Temsilci hedefleri için lambda ifadelerinin kullanılması, [sonraki bölümde](delegates-patterns.md)daha fazla ele alınmıştır.

Sort () örneği genellikle temsilciye tek bir hedef yöntemi iliştirir. Ancak, temsilci nesneleri, temsilci nesnesine eklenmiş birden çok Target yöntemi olan çağrı listelerini destekler.

## <a name="delegate-and-multicastdelegate-classes"></a>Temsilci ve MulticastDelegate sınıfları

Yukarıda açıklanan dil desteği, genellikle temsilcilerle çalışmanız gereken özellikleri ve desteği sağlar. Bu özellikler .NET Core Framework 'te iki sınıf üzerine kurulmuştur: <xref:System.Delegate> ve <xref:System.MulticastDelegate> .

`System.Delegate`Sınıfı ve tek bir doğrudan alt sınıfı olan, `System.MulticastDelegate` Temsilciler oluşturmak, yöntemleri temsilci hedefleri olarak kaydetmek ve temsilci hedefi olarak kaydedilen tüm yöntemleri çağırmak için çerçeve desteği sağlar.

Intergelme, `System.Delegate` ve `System.MulticastDelegate` sınıfları kendilerine temsilci türleri değil. Bunlar, tüm özel temsilci türleri için temel sağlar. Aynı dil tasarım süreci, veya ' den türetilen bir sınıfı bildiremezsiniz `Delegate` `MulticastDelegate` . C# dil kuralları bunu yasaklar.

Bunun yerine, C# derleyicisi `MulticastDelegate` temsilci türlerini bildirmek Için C# Language anahtar sözcüğünü kullandığınızda öğesinden türetilmiş bir sınıfın örneklerini oluşturur.

Bu tasarımın ilk C# ve .NET sürümünde köklerine sahiptir. Tasarım ekibi için bir hedef, temsilci kullanılırken dilin tür güvenliğini zorlamasını sağlamaktır. Bu, temsilcilerin doğru tür ve bağımsız değişken sayısıyla çağrılmasını sağlamaktır. Ve herhangi bir dönüş türü, derleme zamanında doğru şekilde belirtilmiştir. Temsilciler, genel türler 'den önce olan 1,0 .NET sürümünün bir parçası idi.

Bu tür güvenliğini zorlamak için en iyi yol, derleyicinin kullanılan yöntem imzasını temsil eden somut temsilci sınıfları oluşturmasına yöneliktir.

Türetilmiş sınıfları doğrudan oluşturamasanız bile, bu sınıflarda tanımlanan yöntemleri kullanacaksınız. Temsilcilerle çalışırken kullanacağınız en yaygın yöntemlerle başlayalım.

Anımsanması gereken ilk, en önemli olgu, ile birlikte çalıştığınız her temsilcinin türetiliyor `MulticastDelegate` . Çok noktaya yayın temsilcisi, bir temsilci aracılığıyla çağrıldığında birden fazla yöntem hedefinin çağrılabileceği anlamına gelir. Özgün tasarım, yalnızca bir hedef yöntemin iliştirilebileceği ve çağrılabildiği temsilciler arasında ayrım yapmayı ve birden çok hedef metodun iliştirilebileceği ve çağrılabileceği temsilcileri arasında ayrım yapmayı düşünüder. Bu ayrım, ilk düşünmeden uygulamada daha az yararlı olacaktır. İki farklı sınıf zaten oluşturuldu ve ilk genel sürümünden bu yana çerçevede vardı.

Temsilcilerle en çok kullanacağınız Yöntemler `Invoke()` ve ' dir `BeginInvoke()`  /  `EndInvoke()` . `Invoke()`, belirli bir temsilci örneğine eklenmiş olan tüm yöntemleri çağırır. Yukarıda gördüğünüz gibi genellikle temsilci değişkeninde Yöntem çağrısı söz dizimini kullanarak temsilciler çağırılır. [Bu serinin ilerleyen kısımlarında](delegates-patterns.md)göreceğiniz gibi, bu yöntemlerle doğrudan çalışan desenler vardır.

Artık dil sözdizimini ve temsilcileri destekleyen sınıfları gördüğünüze göre, türü kesin belirlenmiş temsilcilerin ne kullanıldığını, oluşturulduğunu ve çağrılmasını incelim.

[Sonraki](delegates-strongly-typed.md)
