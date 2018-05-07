---
title: System.Delegate ve `delegate` anahtar sözcüğü
description: .NET Framework'teki temsilcileri ve nasıl olanlar 'temsilci' anahtar sözcüğü eşleme desteği sınıfları hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: f3742fda-13c2-4283-8966-9e21c2674393
ms.openlocfilehash: 2265d081b884a19cda6fc9d80a0f621a30c87e2a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="systemdelegate-and-the-delegate-keyword"></a>System.Delegate ve `delegate` anahtar sözcüğü

[Önceki](delegates-overview.md)

Bu makalede Temsilciler ve nasıl olanlar için eşleme destekleyen sınıfları .NET Framework'teki ele alınacaktır `delegate` anahtar sözcüğü.

## <a name="defining-delegate-types"></a>Temsilci türleri tanımlama

Temsilciler ile çalışırken ne kullanır, öncelikle olduğu için 'temsilci' anahtar sözcüğüyle başlayalım. Derleyici kullandığınızda oluşturduğu kodu `delegate` anahtar sözcüğü üyeleri çağırma yöntem çağrıları eşleme <xref:System.Delegate> ve <xref:System.MulticastDelegate> sınıfları. 

Bir yöntem imzası tanımlamak için benzer sözdizimini kullanarak bir temsilci türü tanımlayın. Yalnızca Ekle `delegate` tanımına anahtar sözcüğü.

Şimdi List.Sort() yöntemi bizim örnek olarak kullanmaya devam edin. İlk adım, bir tür için karşılaştırma temsilci oluşturmaktır:

```csharp
// From the .NET Core library

// Define the delegate type:
public delegate int Comparison<in T>(T left, T right);
```

Derleyici türetilmiş bir sınıf oluşturur `System.Delegate` (Bu durumda, bir tamsayı döndürür ve iki bağımsız olan bir yöntem) kullanılan imzayı eşleşir. Bu temsilci türü `Comparison`. `Comparison` Temsilci türüdür genel bir tür. Genel türler hakkında ayrıntılar için bkz: [burada](generics.md).

Sözdizimi değişken bildirme, ancak gerçekte bildirme gibi sorgulamanıza görünebilir bildirimi bir *türü*. Sınıfları, ad alanları doğrudan içinde ya da hatta genel ad alanında temsilci türlerinde tanımlayabilirsiniz.

> [!NOTE]
> Doğrudan genel ad alanında temsilci türleri (veya diğer türleri) bildirme önerilmez. 

Derleyici de oluşturur ekleyin ve böylece istemciler, bu sınıfın ekleyin ve yöntemleri bir örneğinin çağırma listesinden kaldırmak bu yeni tür için işleyiciler kaldırın. Derleyici eklendiğinde veya kaldırıldığında yöntemi imzası yöntemi bildirirken kullanılan imzayı eşleştiğini zorlar. 

## <a name="declaring-instances-of-delegates"></a>Temsilciler örneklerini bildirme

Temsilci tanımladıktan sonra o türünün bir örneğini oluşturabilirsiniz.
C# tüm değişkenler gibi bir ad alanındaki doğrudan ya da genel ad alanında temsilci örneklerinin bildiremezsiniz.

```csharp
// inside a class definition:

// Declare an instance of that type:
public Comparison<T> comparator;
```

Değişken türü `Comparison<T>`, daha önce tanımlanan temsilci türü. Değişken adı `comparator`.
 
 Yukarıdaki kod parçacığında, bir üye değişkenine bir sınıf içinde bildirildi. Yerel değişkenler ya da bağımsız değişkenleri yöntemleri için temsilci değişkenleri de bildirebilirsiniz.

## <a name="invoking-delegates"></a>Çağıran temsilciler

Bu temsilci çağırarak bir temsilci çağırma listesi yöntemleri çağırır. İçinde `Sort()` yöntemi, kodun hangi sırada yerleştirmek için nesneleri belirlemek için karşılaştırma yöntemi çağıracaktır:

```csharp
int result = comparator(left, right);
```

Yukarıdaki kod satırına *çağırır* yöntemi temsilciye bağlı.
Değişken bir yöntem adı kabul eder ve normal yöntemi çağrı sözdizimini kullanarak çağırma.

Bu kod satırı güvenli olmayan bir varsayım yapmaz: hedef temsilciye eklendi garantisi yoktur. Hiçbir hedef eklediyseniz, yukarıdaki satır neden olacağından bir `NullReferenceException` oluşturulmasına. Bu sorunu gidermek için kullanılan deyimleri basit bir null denetimi daha karmaşıktır ve daha sonra bu konuda ele alınmıştır [serisi](delegates-patterns.md).

## <a name="assigning-adding-and-removing-invocation-targets"></a>Atama, ekleme ve çağırma hedeflerini kaldırma

Bir temsilci türü nasıl tanımlanır ve temsilci örneklerinin nasıl bildirilir ve çağrılan olmasıdır.

Kullanmak istediğiniz geliştiriciler `List.Sort()` yöntemi ihtiyacınız olan imza temsilci türü tanımı eşleşen bir yöntemi tanımlamak ve sıralama yöntemi tarafından kullanılan temsilci atamak. Bu atama yöntemi temsilci nesnenin çağırma listesine ekler.

Dizeleri listesini kendi uzunluğa göre sıralamak istediğinizi varsayalım. Karşılaştırma işlevinizi şöyle olabilir:

```csharp
private static int CompareLength(string left, string right)
{
    return left.Length.CompareTo(right.Length);
}
```

Yöntemi, özel bir yöntem olarak bildirilir. Bu sorun yoktur. Ortak arabirimi bir parçası olması için bu yöntemi istemeyebilirsiniz. Bir temsilciye eklendiğinde karşılaştırma yöntemi olarak hala kullanılabilir. Çağrıyı yapan kod temsilci nesnesini hedef listeye eklenen bu yöntem sahip olur ve bu temsilciyi erişebilir.

Bu yönteme geçirerek bu ilişki oluşturmak `List.Sort()` yöntemi:

```csharp
phrases.Sort(CompareLength);
```

Yöntem adı, parantez olmadan kullanılmıştır. Yöntemin bağımsız değişken olarak kullanarak, bu yöntem çağırma hedefi olarak eklemek ve temsilci çağırma hedef olarak kullanılabilir bir başvuru yöntemi başvuru dönüştürmek için derleyici söyler.

Ayrıca türünde bir değişken bildirerek açık atanmış olmanız ' karşılaştırma<string>' ve bir ataması yapıyor:

```csharp
Comparison<string> comparer = CompareLength;
phrases.Sort(comparer);
```

Bir temsilci hedef küçük bir yöntem olarak kullanılmakta olan yöntemin olduğu kullanmak için yaygın kullanımları içinde [Lambda ifadesi](lambda-expressions.md) ataması gerçekleştirmek için söz dizimi:

```csharp
Comparison<string> comparer = (left, right) => left.Length.CompareTo(right.Length);
phrases.Sort(comparer);
```

Lambda ifadeleri için temsilci hedefleri kullanarak kapsanan daha içinde bir [daha sonra bölüm](delegates-patterns.md).

Sort() örnek, bir tek hedef yöntemi temsilciye genellikle iliştirir. Ancak, temsilci nesneleri bir temsilci nesnesine bağlı birden çok hedef yöntemleri çağırma listelerini destekler.

## <a name="delegate-and-multicastdelegate-classes"></a>Temsilci ve MulticastDelegate sınıfları

Yukarıda açıklanan dil desteği, özellikleri ve genellikle temsilciler ile çalışması gerekir desteği sağlar. Bu özellikler iki sınıf .NET Core Framework üzerine kurulu: <xref:System.Delegate> ve <xref:System.MulticastDelegate>.

`System.Delegate` Sınıfı ve onun tek doğrudan alt sınıfını `System.MulticastDelegate`, temsilci oluşturmak, yöntemleri temsilci hedefleri olarak kaydetme ve temsilci hedef olarak kayıtlı olan tüm yöntemleri çağırma framework desteği sağlar. 

İlginçtir ki, `System.Delegate` ve `System.MulticastDelegate` sınıfları kendilerini olmayan temsilci türleri. Bunlar, tüm özel temsilci türleri için temel sağlar. İşlem zorunlu bir sınıfı bildiremezsiniz aynı dil tasarımında, türetilen olduğunu `Delegate` veya `MulticastDelegate`. C# dil kurallarına yasaklayabilmek.
 
Bunun yerine, C# derleyici türetilmiş bir sınıf örneklerini oluşturur `MulticastDelegate` temsilci türleri bildirmek için C# dil anahtar sözcüğünü kullandığınızda.

Bu tasarım, kökleri ve C# .NET ilk sürümünde sahiptir. Dil temsilciler kullanırken tür güvenliği uygulanmasını sağlamak için bir hedef Tasarım ekibi için oluştu. Temsilciler sağ türü ve bağımsız değişken sayısı ile çağrıldı emin olma anlamına gelir. Derleme zamanı ve herhangi bir dönüş türü en doğru belirtildi. Temsilciler önce genel türler edildi 1.0 .NET sürüm parçası olan.

Bu tür güvenliği zorlamak için en iyi yolu derleyici somut temsilci kullanılan yöntem imzası temsil sınıfları oluşturmak oluştu.

Türetilen sınıflar doğrudan oluşturamaz olsa da, bu sınıflara tanımlanan yöntemler kullanır. Temsilciler ile çalışırken kullanacağınız en yaygın yöntemleri aracılığıyla edelim.

Anımsaması ilk ve en önemli ile çalışırsınız her temsilci türetilmiş gerçeğidir `MulticastDelegate`. Çok noktaya yayın temsilci bir temsilci çağrılırken, birden fazla yöntem hedef çağrılabilir anlamına gelir. Özgün Tasarım olarak kabul burada yalnızca bir hedef yönteme bağlı çağrılır ve yüklenemedi Temsilciler ve burada birden çok hedef yöntemi bağlı çağrılır ve yüklenemedi temsilciler arasında ayrım yapma. Bu ayrım başlangıçta zorlayıcı daha uygulamada daha az kullanışlı olması için oluyor uygulamasına yol açıyordu. Farklı iki sınıf zaten oluşturulmuş ve framework ilk sürülmeden itibaren kapatıldı.

En temsilciler ile kullanacağınız yöntemler `Invoke()` ve `BeginInvoke()`  /  `EndInvoke()`. `Invoke()` belirli temsilci örneğine bağlı tüm yöntemleri çağırır. Yukarıda gördüğünüz gibi genellikle temsilcileri temsilci değişkeni yöntemi çağrı sözdizimini kullanarak çağırır. Gördüğünüz gibi [bu serideki sonraki](delegates-patterns.md), doğrudan bu yöntemlerle iş desenleri vardır.

Dili sözdizimi ve temsilciler destekleyen sınıfları gördüğünüze göre nasıl kesin türü belirtilmiş temsilciler inceleyelim, oluşturulan çağrılır ve kullanıldığını.

[Next](delegates-strongly-typed.md)
