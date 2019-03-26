---
title: System.Delegate ve `delegate` anahtar sözcüğü
description: .NET Framework'teki temsilcileri ve bu 'temsilci' anahtar sözcüğü nasıl eşleştiği destekleyen sınıfları hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: f3742fda-13c2-4283-8966-9e21c2674393
ms.openlocfilehash: 4cf2b113fc9e2c6621f648af7ecb272a42b1f056
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2019
ms.locfileid: "58465782"
---
# <a name="systemdelegate-and-the-delegate-keyword"></a>System.Delegate ve `delegate` anahtar sözcüğü

[Önceki](delegates-overview.md)

Bu makalede, temsilciler ve bu'nasıl eşleştiğini destekleyen sınıfları .NET Framework'teki kapsar `delegate` anahtar sözcüğü.

## <a name="defining-delegate-types"></a>Temsilci türleri tanımlama

Temsilciler ile çalışırken kullandığınız, öncelikle olduğu için 'temsilci' anahtar sözcüğü ile başlayalım. Kullandığınızda, derleyici oluşturan kod `delegate` anahtar sözcüğü, üyelerini çağırmak için yöntem çağrıları eşleme <xref:System.Delegate> ve <xref:System.MulticastDelegate> sınıfları. 

Bir yöntem imzasını tanımlayan benzer söz dizimini kullanarak bir temsilci türü tanımlarsınız. Yalnızca eklediğiniz `delegate` tanımına anahtar sözcüğü.

Bizim örnek olarak List.Sort() yöntemi kullanmak üzere devam edelim. İlk adım, bir tür karşılaştırma temsilcisi oluşturmaktır:

```csharp
// From the .NET Core library

// Define the delegate type:
public delegate int Comparison<in T>(T left, T right);
```

Derleyici, türetilen bir sınıf oluşturur `System.Delegate` eşleştiren (Bu durumda bir tamsayı döndürür ve iki bağımsız değişkeni olan bir yöntem) kullanılır. Bu temsilci türü `Comparison`. `Comparison` Temsilci türü olan genel bir tür. Genel türler hakkında ayrıntılar için bkz. [burada](generics.md).

Sözdizimi, bir değişken bildiriyor, ancak gerçekte bildirme gibi sorgulamanıza görünebilir bildirimi bir *türü*. Temsilci türleri sınıflar, ad alanları doğrudan içinde veya hatta genel ad içinde tanımlayabilirsiniz.

> [!NOTE]
> Doğrudan genel ad alanında temsilci türleri (veya diğer türleri) bildirme önerilmez. 

Derleyici ayrıca oluşturur ekleyin ve böylece istemciler bu sınıfın ekleyebilir ve yöntemleri bir örneğin çağırma listesinden kaldırmak için bu yeni türü işleyicilerini kaldırmak. Derleyici, eklendiğinde veya kaldırıldığında metodun imzası yöntem bildirirken kullanılan imzayla eşleşen zorlar. 

## <a name="declaring-instances-of-delegates"></a>Temsilci örneklerini bildirme

Temsilci tanımladıktan sonra bu türün bir örneği oluşturabilirsiniz.
Tüm değişkenler gibi C#, doğrudan bir ad alanında ya da genel ad alanında temsilci örneklerini bildiremezsiniz.

```csharp
// inside a class definition:

// Declare an instance of that type:
public Comparison<T> comparator;
```

Değişken türü `Comparison<T>`, daha önce tanımlanan temsilci türü. Değişken adı `comparator`.
 
 Yukarıdaki Bu kod parçacığında, bir sınıf içinde bir üye değişkeni bildirildi. Ayrıca, yerel değişkenler veya yöntemlerinin bağımsız değişkenleri temsilci değişkenleri bildirebilirsiniz.

## <a name="invoking-delegates"></a>Çağrılıyor temsilciler

Bu temsilciyi çağırarak bir temsilci çağırma listesinde yöntemleri çağırır. İçinde `Sort()` yöntemi, kod nesneleri yerleştirmek için sırasını belirlemek için karşılaştırma metodu çağıracaktır:

```csharp
int result = comparator(left, right);
```

Yukarıdaki kod satırında *çağırır* yöntem temsilciye bağlı.
Değişkeni bir yöntem adı kabul et ve normal yöntem çağrı sözdizimini kullanarak çağırma.

Bu kod satırı, güvenli olmayan bir varsayım yapmaz: Bir hedef temsilciye eklendiğini garantisi yoktur. Hiçbir hedef bağlı değilse, yukarıdaki satırı neden bir `NullReferenceException` oluşturulması için. Bu sorunu gidermek için kullanılan deyimleri basit bir null denetimi daha karmaşıktır ve daha sonra bu konuda ele alınmaktadır [serisi](delegates-patterns.md).

## <a name="assigning-adding-and-removing-invocation-targets"></a>Atama, ekleme ve kaldırma çağırma hedefleri

Bir temsilci türü nasıl tanımlandığını ve temsilci örneklerini nasıl bildirildi ve çağrılan olmasıdır.

Kullanmak istediğiniz geliştiriciler `List.Sort()` imzası olan, temsilci türü tanımı eşleşen bir yöntemi tanımlamak ve sıralama yöntemi tarafından kullanılan temsilci atamak yöntem gerekir. Bu atama yöntemi, temsilci nesnesini çağırma listesine ekler.

Bir dize listesi kendi uzunluğa göre sıralamak istediğinizi varsayalım. Karşılaştırma işlevinizi aşağıdakiler olabilir:

```csharp
private static int CompareLength(string left, string right) =>
    left.Length.CompareTo(right.Length);
```

Yöntemi, özel bir yöntem bildirilir. İyi olur. Bu yöntem, genel arabiriminin bir parçası olmasını istemeyebilirsiniz. Bir temsilciye eklendiğinde karşılaştırma yöntemi olarak hala kullanılabilir. Çağıran kod bu yöntem hedef temsilci nesne listesine bağlı olacaktır ve bu temsilci erişebilirsiniz.

Bu yönteme geçirerek bu ilişki oluşturma `List.Sort()` yöntemi:

```csharp
phrases.Sort(CompareLength);
```

Yöntem adı, parantez olmadan kullanıldığına dikkat edin. Bağımsız değişken olarak yöntemi kullanarak, bir temsilci çağırma hedefi olarak kullanılabilir ve bu yöntem bir çağırma hedefi olarak ekleme başvuru yöntemi başvuru dönüştürmek için derleyiciye bildirir.

Ayrıca türünün bir değişkeni bildirerek açık atanmış `Comparison<string>` ve atama:

```csharp
Comparison<string> comparer = CompareLength;
phrases.Sort(comparer);
```

Small yöntemi temsilci hedefi olarak kullanılan yöntemin olduğu kullanmak yaygın kullanır [lambda ifadesi](./programming-guide/statements-expressions-operators/lambda-expressions.md) ataması gerçekleştirmek için söz dizimi:

```csharp
Comparison<string> comparer = (left, right) => left.Length.CompareTo(right.Length);
phrases.Sort(comparer);
```

Lambda ifadeleri için temsilci hedefleri kullanarak kapsanan daha bir [daha sonra bölüm](delegates-patterns.md).

Sort() örnek bir tek hedef yöntem temsilciye genellikle ekler. Ancak, temsilci nesneleri birden çok hedef yöntem bir temsilci nesnesine ekli olan çağırma listelerini destekler.

## <a name="delegate-and-multicastdelegate-classes"></a>Temsilci ve MulticastDelegate sınıfları

Yukarıda açıklanan dil desteği, destek temsilcileri ile çalışmak için genellikle gerekir ve özellikleri sağlar. Bu özelliklerin .NET Core Framework iki sınıf temel alır: <xref:System.Delegate> ve <xref:System.MulticastDelegate>.

`System.Delegate` Sınıfı ve onun tek doğrudan alt sınıfını `System.MulticastDelegate`, temsilciler oluşturma yöntemleri temsilci hedefler olarak kaydetme ve temsilci hedef olarak kayıtlı olan tüm yöntemlerini çağırmaktan framework desteği sağlayın. 

İlginçtir ki, `System.Delegate` ve `System.MulticastDelegate` sınıfları kendilerini olmayan temsilci türleri. Bunlar, tüm özel temsilci türleri için temel sağlar. Aynı dil tasarım işlemi uygulanan bir sınıfı bildiremez öğesinden türetilen `Delegate` veya `MulticastDelegate`. C# Dil kuralları yasaklar.
 
Bunun yerine, C# derleyici türetilmiş bir sınıfın örneklerini oluşturur `MulticastDelegate` kullandığınızda C# temsilci türleri bildirmek için dil anahtar sözcüğü.

Bu tasarım, ilk sürümünde, kökleri sahip C# ve .NET. Temsilcileri kullanarak zaman dil tür güvenliği zorunlu emin olmak için Tasarım ekibi için bir hedef oluştu. Bu temsilciler doğru tür ve sayıda bağımsız değişken ile çağrılan sağlama geliyordu. Derleme zamanı ve herhangi bir dönüş türü, doğru şekilde belirtildi. Temsilciler genel türler önce olan 1.0 .NET sürümünün bir parçası olan.

En iyi yolu, bu tür güvenliği zorlamak için kullanılan yöntem imzası temsil sınıflar somut temsilci oluşturmak derleyicinin için oluştu.

Türetilmiş sınıflar doğrudan oluşturamazsınız olsa da, bu sınıflarında tanımlanan yöntemler kullanır. Temsilciler ile çalışırken kullanacağınız en yaygın yöntemleri aracılığıyla Bahsedelim.

Anımsanması ilk ve en önemli iş her temsilci türetilir gerçeğidir `MulticastDelegate`. Çok noktaya yayın temsilci, bir temsilci çağrılırken birden fazla yöntem hedef çağrılabilir anlamına gelir. Yalnızca bir hedef yöntemi burada bağlı ve çağrılan Temsilciler ve birden çok hedef yöntem nereye eklenmiş ve çağrılan temsilcileri arasında bir ayrım yapma özgün tasarımda dikkate. İlk olarak düşünülebilir daha uygulamada daha az kullanışlı olması için Bu ayrım kanıtladılar. Farklı iki sınıf zaten oluşturulduğunu ve framework ilk genel sürümünden sonra olmuştur.

En iyi temsilcilerinden kullanacağınız yöntemler `Invoke()` ve `BeginInvoke()`  /  `EndInvoke()`. `Invoke()` belirli bir temsilci örneğine eklenmiş olan tüm yöntemleri çağırır. Yukarıda anlatıldığı gibi genellikle temsilcileri yöntemi çağrı sözdizimini kullanarak temsilci değişkeni çağırır. Gördüğünüz gibi [bu serideki sonraki](delegates-patterns.md), doğrudan bu yöntemlerle iş desenleri vardır.

Dilinin sözdizimi ve temsilcileri destekleyen sınıfları gördüğünüze göre şimdi nasıl kesin tür belirtilmiş temsilciler inceleyin, oluşturulan çağrılır ve kullanıldığını.

[Next](delegates-strongly-typed.md)
