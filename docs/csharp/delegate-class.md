---
title: System.Delegate ve `delegate` anahtar kelime
description: .NET'te delegeleri destekleyen sınıflar ve bu ların 'temsilci' anahtar kelimesine nasıl eşleneceği hakkında bilgi edinin.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: f3742fda-13c2-4283-8966-9e21c2674393
ms.openlocfilehash: 87fdf19c4ea810c5ac4409fe16c3cba9d5fc6574
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146287"
---
# <a name="systemdelegate-and-the-delegate-keyword"></a>System.Delegate ve `delegate` anahtar kelime

[Önceki](delegates-overview.md)

Bu makalede, .NET'te delegeleri destekleyen sınıfları ve `delegate` bu eşin anahtar kelimeye nasıl eşlenebildiğini kapsar.

## <a name="define-delegate-types"></a>Temsilci türlerini tanımlama

'Temsilci' anahtar kelimesi ile başlayalım, çünkü öncelikle temsilcilerle çalışırken kullanacağınız şey budur. `delegate` Anahtar kelimeyi kullandığınızda derleyicinin oluşturduğu kod, ve <xref:System.Delegate> <xref:System.MulticastDelegate> sınıfların üyelerini çağıran çağrıları yöntemle eşler.

Yöntem imzasını tanımlamaya benzer sözdizimini kullanarak bir temsilci türü tanımlarsınız. Sadece tanım `delegate` için anahtar kelime ekleyin.

Liste.Sıralama() yöntemini örneğimiz olarak kullanmaya devam edelim. İlk adım, karşılaştırma temsilcisi için bir tür oluşturmaktır:

```csharp
// From the .NET Core library

// Define the delegate type:
public delegate int Comparison<in T>(T left, T right);
```

Derleyici, `System.Delegate` kullanılan imzayla eşleşen bir sınıf oluşturur (bu durumda, bir tamsayı döndüren ve iki bağımsız değişkeni olan bir yöntem). Bu temsilcinin `Comparison`türü. Temsilci `Comparison` türü genel bir türüdür. Jenerik hakkında ayrıntılı bilgi için [buraya](programming-guide/generics/index.md)bakın.

Sözdiziminin bir değişken beyan ediyormuş gibi görünebileceğine, ancak aslında bir *tür*beyan ettiğine dikkat edin. Sınıflar içinde, doğrudan ad alanları içinde ve hatta genel ad alanında temsilci türlerini tanımlayabilirsiniz.

> [!NOTE]
> Temsilci türlerinin (veya diğer türlerin) doğrudan genel ad alanında beyan olması önerilmez.

Derleyici ayrıca, bu sınıfın istemcilerinin bir örneğin çağrı listesinden yöntem ekleyip kaldırabilmesi için bu yeni tür için işleyiciler ekleme ve kaldırma oluşturur. Derleyici, eklenen veya kaldırılan yöntemin imzasının yöntemi bildirirken kullanılan imzayla eşleştiğini zorlar.

## <a name="declare-instances-of-delegates"></a>Temsilci örneklerini bildir

Temsilciyi tanımladıktan sonra, bu tür bir örnek oluşturabilirsiniz.
C#'daki tüm değişkenler gibi, temsilci örneklerini doğrudan bir ad alanında veya genel ad alanında bildiremezsiniz.

```csharp
// inside a class definition:

// Declare an instance of that type:
public Comparison<T> comparator;
```

Değişkenin `Comparison<T>`türü, daha önce tanımlanan temsilci türüdür. Değişkenin adı `comparator`.

 Yukarıdaki kod parçacığı bir sınıf içinde bir üye değişken içinde ilan etti. Yerel değişkenler veya bağımsız değişkenler olan temsilci değişkenlerini yöntemlere de bildirebilirsiniz.

## <a name="invoke-delegates"></a>Delegeleri çağırma

Bu temsilciyi çağırarak bir temsilcinin çağırma listesinde bulunan yöntemleri çağırırsınız. Yöntemin `Sort()` içinde, kod nesneleri yerleştirmek için hangi sırayı belirlemek için karşılaştırma yöntemi çağırır:

```csharp
int result = comparator(left, right);
```

Yukarıdaki satırda, kod temsilciye eklenen yöntemi *çağırır.*
Değişkeni bir yöntem adı olarak ele alıp, normal yöntem çağrı sözdizimini kullanarak çağırırsınız.

Bu kod satırı güvenli olmayan bir varsayım yapar: Temsilciye bir hedefekildiğinin garantisi yoktur. Hiçbir hedef eklenmediyse, yukarıdaki satır `NullReferenceException` a'nın atılmasına neden olur. Bu sorunu gidermek için kullanılan deyimler basit bir null-check daha karmaşık, ve daha sonra bu serinin ele [alınmıştır.](delegates-patterns.md)

## <a name="assign-add-and-remove-invocation-targets"></a>Çağırma hedeflerini atama, ekleme ve kaldırma

Temsilci türü bu şekilde tanımlanır ve temsilci örnekleri nasıl bildirilir ve çağrılır.

`List.Sort()` Yöntemi kullanmak isteyen geliştiricilerin, imzası temsilci türü tanımıyla eşleşen bir yöntem tanımlaması ve sıralama yöntemi tarafından kullanılan temsilciye ataması gerekir. Bu atama, bu temsilci nesnesinin çağırma listesine yöntemi ekler.

Dizeleri uzunluklarına göre sıralamak istediğinizi varsayalım. Karşılaştırma işleviniz aşağıdakiler olabilir:

```csharp
private static int CompareLength(string left, string right) =>
    left.Length.CompareTo(right.Length);
```

Yöntem özel bir yöntem olarak bildirilir. Sorun değil. Bu yöntemin ortak arabiriminizin bir parçası olmasını istemeyebilirsiniz. Yine de bir temsilciye eklendiğinde karşılaştırma yöntemi olarak kullanılabilir. Arama kodu bu yöntemi temsilci nesnesinin hedef listesine iliştirecek ve bu temsilci aracılığıyla erişebilirsiniz.

Bu yöntemi yönteme geçirerek `List.Sort()` bu ilişkiyi oluşturursunuz:

```csharp
phrases.Sort(CompareLength);
```

Yöntem adının parantez olmadan kullanıldığına dikkat edin. Yöntemi bağımsız değişken olarak kullanmak, derleyiciye yöntem başvurularını temsilci çağırma hedefi olarak kullanılabilecek bir başvuruya dönüştürmesini ve bu yöntemi bir çağırma hedefi olarak eklemesini söyler.

Ayrıca, bir tür `Comparison<string>` değişkeni beyan ederek ve bir atama yaparak da açık olabilirsiniz:

```csharp
Comparison<string> comparer = CompareLength;
phrases.Sort(comparer);
```

Temsilci hedefi olarak kullanılan yöntemin küçük bir yöntem olduğu kullanımlarda, atamayı gerçekleştirmek için [lambda ifade](./programming-guide/statements-expressions-operators/lambda-expressions.md) sözdizimini kullanmak yaygındır:

```csharp
Comparison<string> comparer = (left, right) => left.Length.CompareTo(right.Length);
phrases.Sort(comparer);
```

Temsilci hedefleri için lambda ifadeleri kullanarak [daha sonraki](delegates-patterns.md)bir bölümde daha fazla ele alınmıştır.

Sıralama() örneği genellikle temsilciye tek bir hedef yöntemi bağlar. Ancak, temsilci nesneleri, bir temsilci nesnesine bağlı birden çok hedef yöntemi olan çağrı listelerini destekler.

## <a name="delegate-and-multicastdelegate-classes"></a>Temsilci ve Çok Noktaya Yayın sınıfları

Yukarıda açıklanan dil desteği, genellikle temsilcilerle çalışmak için ihtiyaç duyduğunuz özellikleri ve desteği sağlar. Bu özellikler .NET Core çerçevesinde iki sınıf <xref:System.Delegate> <xref:System.MulticastDelegate>üzerine kurulmuştur: ve .

Sınıf `System.Delegate` ve onun tek doğrudan `System.MulticastDelegate`alt sınıfı, temsilci oluşturmak, yöntemleri temsilci hedefleri olarak kaydetmek ve temsilci hedefi olarak kaydedilmiş tüm yöntemleri çağırmak için çerçeve desteği sağlar.

İlginçtir, `System.Delegate` ve `System.MulticastDelegate` sınıflar kendilerini temsilci türleri değildir. Bunlar, tüm belirli temsilci türleri için temel sağlar. Aynı dil tasarımı işlemi, türeyen `Delegate` bir sınıfı veya `MulticastDelegate`. C# dil kuralları bunu yasaklıyor.

Bunun yerine, C# derleyicisi, temsilci `MulticastDelegate` türlerini bildirmek için C# dil anahtar sözcüklerini kullandığınızda türetilen bir sınıfın örneklerini oluşturur.

Bu tasarımın kökleri C# ve .NET'in ilk sürümünde dir. Tasarım ekibinin amaçlarından biri, temsilcilerini kullanırken dilin tür güvenliğini zorunlu kıldığından emin olmaktı. Bu, delegelerin doğru argüman türü ve sayısıyla çağrılmasını sağlamak anlamına geliyordu. Ve, herhangi bir dönüş türü doğru derleme zamanda belirtilmiştir. Delegeler, jeneriklerden önce yapılan 1.0 .NET sürümünde yer alıyordu.

Bu tür güvenliğini zorlamanın en iyi yolu, derleyicinin kullanılan yöntem imzasını temsil eden somut temsilci sınıfları oluşturmasıydı.

Türemiş sınıfları doğrudan oluşturamasanız da, bu sınıflarda tanımlanan yöntemleri kullanırsınız. Temsilcilerle çalışırken kullanacağınız en yaygın yöntemleri gözden geçirelim.

Hatırlanması gereken ilk ve en önemli gerçek, çalıştığınız `MulticastDelegate`her temsilcinin.'den türetilmiş olmasıdır. Çok noktaya yayın temsilcisi, bir temsilci aracılığıyla çağrılırken birden fazla yöntem hedefinin çağrılabileceği anlamına gelir. Özgün tasarım, yalnızca bir hedef yöntemin eklenebileceği ve çağrılabildiği temsilciler ile birden çok hedef yöntemin eklenebileceği ve çağrılabileceği temsilciler arasında ayrım yapmayı kabul eder. Bu ayrım pratikte başlangıçta düşünülenden daha az yararlı olduğunu kanıtladı. İki farklı sınıf zaten oluşturuldu ve ilk kamuoyuna açıklanmasından bu yana çerçeve içinde olmuştur.

Temsilcilerle en çok kullanacağınız yöntemler `Invoke()` ve `BeginInvoke()`  /  `EndInvoke()`. `Invoke()`belirli bir temsilci örneğine eklenen tüm yöntemleri çağırır. Yukarıda gördüğünüz gibi, genellikle temsilci değişkeninde sözdizimi arama yöntemini kullanarak temsilci çağırırsınız. [Daha sonra bu seride](delegates-patterns.md)göreceğiniz gibi, bu yöntemlerle doğrudan çalışan desenler vardır.

Artık dil sözdizimini ve temsilcileri destekleyen sınıfları gördüğünüze göre, ne kadar güçlü bir şekilde yazılan temsilcilerin kullanıldığını, oluşturulduğunu ve çağrıldığını inceleyelim.

[Sonraki](delegates-strongly-typed.md)
