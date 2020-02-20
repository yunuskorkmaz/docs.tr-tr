---
title: System. Delegate ve `delegate` anahtar sözcüğü
description: Temsilcileri destekleyen ve bunların ' Delegate ' anahtar sözcüğüyle nasıl eşlendikleri .NET sınıfları hakkında bilgi edinin.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: f3742fda-13c2-4283-8966-9e21c2674393
ms.openlocfilehash: 3cfc9925be0f191dc3fc93c02f4a8f9a40b71895
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77450927"
---
# <a name="systemdelegate-and-the-delegate-keyword"></a>System. Delegate ve `delegate` anahtar sözcüğü

[Öncekini](delegates-overview.md)

Bu makalede temsilcileri destekleyen .NET sınıfları ve bunların `delegate` anahtar kelimesiyle nasıl eşlendikleri ele alınmaktadır.

## <a name="define-delegate-types"></a>Temsilci türlerini tanımlama

' Delegate ' anahtar sözcüğüyle başlayalım, çünkü bu aslında temsilcilerle çalışırken kullanacağınız şeydir. `delegate` anahtar sözcüğünü kullandığınızda derleyicinin oluşturduğu kod, <xref:System.Delegate> ve <xref:System.MulticastDelegate> sınıflarının üyelerini çağıran yöntem çağrılarına eşlenir. 

Yöntem imzasını tanımlamaya benzer bir sözdizimi kullanarak bir temsilci türü tanımlarsınız. Yalnızca `delegate` anahtar sözcüğünü tanımına eklersiniz.

Bizim örneğimizde List. Sort () yöntemini kullanmaya devam edelim. İlk adım, karşılaştırma temsilcisi için bir tür oluşturmaktır:

```csharp
// From the .NET Core library

// Define the delegate type:
public delegate int Comparison<in T>(T left, T right);
```

Derleyici, kullanılan imzayla eşleşen `System.Delegate` türetilen bir sınıf oluşturur (Bu durumda, bir tamsayı döndüren ve iki bağımsız değişkeni olan bir yöntem). Bu temsilcinin türü `Comparison`. `Comparison` temsilci türü genel bir tür. Genel türler hakkında daha fazla bilgi için [buraya](programming-guide/generics/index.md)bakın.

Sözdiziminin bir değişken bildirmiş gibi görünebileceğini ancak gerçekten bir *tür*bildirdiğine dikkat edin. Sınıf içinde doğrudan ad alanları içinde veya genel ad alanında temsilci türleri tanımlayabilirsiniz.

> [!NOTE]
> Temsilci türlerinin (veya diğer türlerin) doğrudan genel ad alanında bildirilmesi önerilmez. 

Derleyici Ayrıca bu yeni tür için ekleme ve kaldırma işleyicileri üretir. bu sayede, bu sınıfın istemcileri bir örneğin çağrı listesinden Yöntem ekleyebilir ve kaldırabilir. Derleyici, eklenen veya kaldırılan yöntemin imzasının, yöntemi bildirirken kullanılan imza ile eşleştiğinden zorlanır. 

## <a name="declare-instances-of-delegates"></a>Temsilcilerin örneklerini bildirme

Temsilciyi tanımladıktan sonra, bu türün bir örneğini oluşturabilirsiniz.
İçindeki C#tüm değişkenler gibi, temsilci örneklerini doğrudan bir ad alanında veya genel ad alanında bildiremezsiniz.

```csharp
// inside a class definition:

// Declare an instance of that type:
public Comparison<T> comparator;
```

Değişkenin türü, daha önce tanımlanan temsilci türü `Comparison<T>`. Değişkenin adı `comparator`.
 
 Yukarıdaki kod parçacığı, bir sınıf içinde bir üye değişkeni bildirdi. Yerel değişkenler veya yöntemler için bağımsız değişkenler olan temsilci değişkenlerini de bildirebilirsiniz.

## <a name="invoke-delegates"></a>Temsilcileri çağır

Bu temsilciyi çağırarak bir temsilcinin çağırma listesindeki yöntemleri çağırabilirsiniz. `Sort()` yönteminin içinde, hangi nesnelerin yerleştirileceği sırayı belirleyen kod karşılaştırma yöntemini çağırır:

```csharp
int result = comparator(left, right);
```

Yukarıdaki satırda kod, temsilciye iliştirilmiş yöntemi *çağırır* .
Değişkeni bir yöntem adı olarak değerlendirir ve normal Yöntem çağrısı söz dizimini kullanarak çağırılır.

Bu kod satırı güvenli olmayan bir varsayımına neden olur: temsilciye bir hedefin eklendiğinden emin olmaz. Hiçbir hedef iliştirilmişse, yukarıdaki satır `NullReferenceException` oluşturulmasına neden olur. Bu sorunu gidermek için kullanılan ıoms, basit bir null denetiminden daha karmaşıktır ve bu [serinin](delegates-patterns.md)ilerleyen kısımlarında ele alınmıştır.

## <a name="assign-add-and-remove-invocation-targets"></a>Çağırma hedeflerini atama, ekleme ve kaldırma

Temsilci türünün tanımlanması ve temsilci örneklerinin nasıl bildirildiği ve çağrıldığı.

`List.Sort()` yöntemini kullanmak isteyen geliştiricilerin imza, temsilci türü tanımıyla eşleşen bir yöntem tanımlaması gerekir ve bunu sıralama yöntemi tarafından kullanılan temsilciye atar. Bu atama, yöntemi bu temsilci nesnesinin çağırma listesine ekler.

Dizelerin bir listesini uzunluğuna göre sıralamak istediğinizi varsayalım. Karşılaştırma işleviniz aşağıdaki gibi olabilir:

```csharp
private static int CompareLength(string left, string right) =>
    left.Length.CompareTo(right.Length);
```

Yöntemi özel bir yöntem olarak bildirilmiştir. Bu çok güzel. Bu yöntemin ortak arayüzün bir parçası olmasını istemeyebilirsiniz. Bir temsilciye eklendiğinde karşılaştırma yöntemi olarak yine de kullanılabilir. Çağıran kod bu yöntemi temsilci nesnesinin hedef listesine iliştirilir ve bu temsilci aracılığıyla erişebilir.

Bu ilişkiyi, `List.Sort()` yöntemine geçirerek oluşturursunuz:

```csharp
phrases.Sort(CompareLength);
```

Yöntem adının parantez olmadan kullanıldığına dikkat edin. Yöntemin bağımsız değişken olarak kullanılması, derleyicinin Yöntem başvurusunu temsilci çağırma hedefi olarak kullanılabilecek bir başvuruya dönüştürmesini ve bu yöntemi bir çağırma hedefi olarak iliştirmesine söyler.

Ayrıca, `Comparison<string>` türünde bir değişken bildirerek ve ödev yaparak da açık olabilirsiniz:

```csharp
Comparison<string> comparer = CompareLength;
phrases.Sort(comparer);
```

' De, bir temsilci hedefi olarak kullanılan yöntemin küçük bir yöntem olduğu durumlarda, atamayı gerçekleştirmek için [lambda ifadesi](./programming-guide/statements-expressions-operators/lambda-expressions.md) sözdizimini kullanmak yaygındır:

```csharp
Comparison<string> comparer = (left, right) => left.Length.CompareTo(right.Length);
phrases.Sort(comparer);
```

Temsilci hedefleri için lambda ifadelerinin kullanılması, [sonraki bölümde](delegates-patterns.md)daha fazla ele alınmıştır.

Sort () örneği genellikle temsilciye tek bir hedef yöntemi iliştirir. Ancak, temsilci nesneleri, temsilci nesnesine eklenmiş birden çok Target yöntemi olan çağrı listelerini destekler.

## <a name="delegate-and-multicastdelegate-classes"></a>Temsilci ve MulticastDelegate sınıfları

Yukarıda açıklanan dil desteği, genellikle temsilcilerle çalışmanız gereken özellikleri ve desteği sağlar. Bu özellikler .NET Core Framework 'te iki sınıf üzerine kurulmuştur: <xref:System.Delegate> ve <xref:System.MulticastDelegate>.

`System.Delegate` sınıfı ve tek bir doğrudan alt sınıfı olan `System.MulticastDelegate`, temsilciler oluşturmak, yöntemleri temsilci hedefleri olarak kaydetmek ve temsilci hedefi olarak kaydedilen tüm yöntemleri çağırmak için çerçeve desteği sağlar. 

Her ne kadar `System.Delegate` ve `System.MulticastDelegate` sınıfları kendilerine temsilci türleri değildir. Bunlar, tüm özel temsilci türleri için temel sağlar. Aynı dil tasarım süreci, `Delegate` veya `MulticastDelegate`türetilen bir sınıfı bildiremezsiniz. C# Dil kuralları bunu yasaklar.
 
Bunun yerine, C# derleyici, temsilci türlerini bildirmek için C# language anahtar sözcüğünü kullandığınızda `MulticastDelegate` türetilen bir sınıfın örneklerini oluşturur.

Bu tasarım, C# ve .net ilk sürümünde köklerine sahiptir. Tasarım ekibi için bir hedef, temsilci kullanılırken dilin tür güvenliğini zorlamasını sağlamaktır. Bu, temsilcilerin doğru tür ve bağımsız değişken sayısıyla çağrılmasını sağlamaktır. Ve herhangi bir dönüş türü, derleme zamanında doğru şekilde belirtilmiştir. Temsilciler, genel türler 'den önce olan 1,0 .NET sürümünün bir parçası idi.

Bu tür güvenliğini zorlamak için en iyi yol, derleyicinin kullanılan yöntem imzasını temsil eden somut temsilci sınıfları oluşturmasına yöneliktir.

Türetilmiş sınıfları doğrudan oluşturamasanız bile, bu sınıflarda tanımlanan yöntemleri kullanacaksınız. Temsilcilerle çalışırken kullanacağınız en yaygın yöntemlerle başlayalım.

Anımsanması gereken ilk, en önemli olgu, birlikte çalıştığınız her temsilcinin `MulticastDelegate`türetilir. Çok noktaya yayın temsilcisi, bir temsilci aracılığıyla çağrıldığında birden fazla yöntem hedefinin çağrılabileceği anlamına gelir. Özgün tasarım, yalnızca bir hedef yöntemin iliştirilebileceği ve çağrılabildiği temsilciler arasında ayrım yapmayı ve birden çok hedef metodun iliştirilebileceği ve çağrılabileceği temsilcileri arasında ayrım yapmayı düşünüder. Bu ayrım, ilk düşünmeden uygulamada daha az yararlı olacaktır. İki farklı sınıf zaten oluşturuldu ve ilk genel sürümünden bu yana çerçevede vardı.

Temsilcilerle en iyi şekilde kullanacağınız Yöntemler `Invoke()` ve  / `EndInvoke()``BeginInvoke()`. `Invoke()`, belirli bir temsilci örneğine eklenmiş olan tüm yöntemleri çağırır. Yukarıda gördüğünüz gibi genellikle temsilci değişkeninde Yöntem çağrısı söz dizimini kullanarak temsilciler çağırılır. [Bu serinin ilerleyen kısımlarında](delegates-patterns.md)göreceğiniz gibi, bu yöntemlerle doğrudan çalışan desenler vardır.

Artık dil sözdizimini ve temsilcileri destekleyen sınıfları gördüğünüze göre, türü kesin belirlenmiş temsilcilerin ne kullanıldığını, oluşturulduğunu ve çağrılmasını incelim.

[Next](delegates-strongly-typed.md)
