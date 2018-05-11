---
title: Özellikler
description: Bilgi C# hakkında değerleri, geç değerlendirme doğrulama için özellikler, Özellikler hesaplanır ve özelliği bildirimleri değiştirildi.
ms.date: 04/25/2018
ms.openlocfilehash: d4fa7b6117bec63c41318dd4bcc3850ce55a5907
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
---
# <a name="properties"></a>Özellikler

C# birinci sınıf kullanıcılarının özelliklerdir. Dil kendi tasarım hedefi doğru şekilde ifade kod yazmaya geliştiricilerinin sözdizimi tanımlar.

Bunlar erişildiğinde özellikleri alanlar gibi davranır.
Ancak, alanları, bir özellik erişilen veya atandığında, yürütülen deyimleri tanımlayan erişimciler ile özellikleri uygulanır.

## <a name="property-syntax"></a>Özellik sözdizimi

Özellikleri için sözdizimi, alanlar için doğal bir uzantıdır. Bir alan bir depolama konumu tanımlar:

[!code-csharp[Person class with public fields](../../samples/snippets/csharp/properties/Person.cs#1)]

Bildirimler için bir özellik tanımını içeren bir `get` ve `set` alır ve bu özelliğin değeri atayan erişimcisi:

[!code-csharp[Person class with public properties](../../samples/snippets/csharp/properties/Person.cs#2)]

Yukarıda gösterilen sözdizimi *otomatik özelliği* sözdizimi. Derleyici özelliği yedekler alanı için depolama konumu oluşturur. Derleyici de gövdesini uygulayan `get` ve `set` erişimciler.

Bazı durumlarda, bir özellik türü için varsayılan farklı bir değere başlatmak için gerekir.  C#, sonra kapanış ayracı özelliği için bir değer ayarlanarak sağlar. İlk değeri tercih edebilirsiniz `FirstName` boş dize özelliğini yerine `null`. Aşağıda gösterildiği gibi belirtmeniz gerekir:

[!code-csharp[Person class with properties and initializer](../../samples/snippets/csharp/properties/Person.cs#3)]

Daha sonra bu makalede anlatıldığı gibi belirli başlatma salt okunur özellikler için kullanışlıdır.

Aşağıda gösterildiği gibi depolama kendiniz de tanımlayabilirsiniz:

[!code-csharp[Person class with properties and backing field](../../samples/snippets/csharp/properties/Person.cs#4)]

Bir özellik uygulama tek bir ifade olduğunda kullanabileceğiniz *ifade bodied üyeleri* alıcı veya ayarlayıcı için:

[!code-csharp[Person class with properties and expression bodied getters and setters](../../samples/snippets/csharp/properties/Person.cs#5)]

Bu Basitleştirilmiş söz dizimi geçerli olduğunda bu makale boyunca kullanılır.

Yukarıda gösterilen özellik tanımı bir okuma-yazma özelliğidir. Anahtar sözcüğü fark `value` set erişimcisi içinde. `set` Erişimcisine sahip her zaman adlı tek bir parametre `value`. `get` Erişimci özelliği türüne dönüştürülebilir olan bir değer döndürmesi gerekir (`string` Bu örnekte).

Sözdizimi temelleri olmasıdır. Farklı tasarım deyimleri çeşitli destek pek çok farklı Çeşitleme vardır. Şimdi keşfedin ve her sözdizimi seçenekleri öğrenin.

## <a name="scenarios"></a>Senaryolar

Yukarıdaki örneklerde gösterilen özellik tanımı, basit bir durumda birini: hiçbir doğrulama okuma-yazma özelliğiyle. Kod yazarak istediğiniz `get` ve `set` erişimciler, birçok farklı senaryolar oluşturabilirsiniz.

### <a name="validation"></a>Doğrulama

Kod yazabilirsiniz `set` erişimci özelliği tarafından temsil edilen değerler her zaman geçerli olduğundan emin olun. Örneğin, bir kural için varsayalım `Person` sınıftır adı boş veya boşluk olamaz. Aşağıdaki gibi yazarsınız:

[!code-csharp[Validating property setters](../../samples/snippets/csharp/properties/Person.cs#6)]

Önceki örnekte kullanarak basit hale getirilebilir bir`throw` özellik ayarlayıcı doğrulama bir parçası olarak ifade:

[!code-csharp[Validating property setters](../../samples/snippets/csharp/properties/Person.cs#7)]

Yukarıdaki örnekte kuralı adı boş olmamalı veya boşluk zorlar. Bir geliştirici yazıyorsa

```csharp
hero.FirstName = "";
```

Bu atama oluşturur bir `ArgumentException`. Dönüş türü void özellik bir set erişimcisine sahip olması gerektiğinden, bir özel durum atma tarafından set erişimcisine hataları rapor.

Bu aynı sözdizimini senaryonuzda gereken herhangi bir şeye genişletebilirsiniz. Farklı özellikler arasındaki ilişkileri denetleyin veya karşı dış koşulları doğrulayın. Geçerli bir C# ifadelerinin içinde bir özellik erişimcisini geçerli değil.

### <a name="read-only"></a>Salt okunur

Bu noktaya kadar açtığınız tüm özellik tanımları ortak erişimciler ile okuma/yazma özelliklerdir. Bu özellikler için geçerli tek erişilebilirlik değil.
Salt okunur özellikler oluşturun veya farklı erişilebilirlik kümesine verin ve erişimciler alın. Varsayın, `Person` sınıfı, değerinin değiştirilmesi yalnızca etkinleştirmelisiniz `FirstName` o sınıfın diğer yöntemlerle özelliğinden. Set erişimcisine sunabilir `private` yerine erişilebilirlik `public`:

[!code-csharp[Using a private setter for a publicly readonly property](../../samples/snippets/csharp/properties/Person.cs#8)]

Şimdi, `FirstName` özelliği herhangi bir kodda erişilebilir, ancak diğer koddan yalnızca atanabilir `Person` sınıfı.

Herhangi bir kısıtlayıcı erişim değiştiricisi ya da kümesi ekleyin veya erişimciler alın. Tek tek erişimcisine yerleştirin herhangi bir erişim değiştiricisi özellik tanımı üzerinde erişim değiştiricisi daha kısıtlı olması gerekir. Yukarıdaki yasal olduğundan `FirstName` özelliği `public`, ancak set erişimcisine `private`. Değil bildirebilirsiniz bir `private` özelliği ile bir `public` erişimcisi. Özellik bildirimleri de bildirilebilir `protected`, `internal`, `protected internal`, ve hatta `private`.

Daha kısıtlayıcı değiştiricisi yerleştirmek için uygundur `get` erişimcisi. Örneğin, olabilir bir `public` özelliği, ancak kısıtlamak `get` erişimcisi için `private`. Bu senaryo, uygulamada nadiren yapılır.

Böylece bir oluşturucu veya özellik başlatıcı yalnızca ayarlanabilir bir özellik değişiklikler de kısıtlayabilirsiniz. Değiştirebileceğiniz `Person` bunu aşağıdaki gibi sınıfı:

[!code-csharp[A readonly auto implemented property](../../samples/snippets/csharp/properties/Person.cs#9)]

Bu özellik salt okunur özellikler olarak sunulan koleksiyonları başlatmak için en yaygın olarak kullanılır:

```csharp
public class Measurements
{
    public ICollection<DataPoint> points { get; } = new List<DataPoint>();
}
```

### <a name="computed-properties"></a>Hesaplanan özellikleri

Bir özelliği yalnızca bir üye alanın değerini döndürmek gerekmez. Hesaplanan değeri döndüren özellikleri oluşturabilirsiniz. Şimdi genişletin `Person` nesne adları ve soyadları birleştirerek hesaplanan tam adını döndürmek için:

[!code-csharp[A computed property](../../samples/snippets/csharp/properties/Person.cs#10)]

Kullandığı Yukarıdaki örnek [dize ilişkilendirme](../csharp/language-reference/tokens/interpolated.md) biçimlendirilmiş dize tam adı oluşturmak için özellik.

Aynı zamanda bir *ifade bodied üye*, hesaplanan oluşturmak için daha kısa bir yol sağlar `FullName` özelliği:

[!code-csharp[A computed property using an expression bodied member](../../samples/snippets/csharp/properties/Person.cs#11)]

*İfade bodied üyeleri* kullanmak *lambda ifadesi* sözdizimi tek bir ifade içeren yöntemleri tanımlar. Burada, bu ifade kişi nesnesi tam adını döndürür.

### <a name="cached-evaluated-properties"></a>Önbelleğe alınan değerlendirilen özellikleri

Hesaplanan bir özellik kavramı depolama ile karıştırmak ve oluşturma bir *değerlendirilen özellik önbelleğe*.  Örneğin, güncelleştirebilir `FullName` özelliği böylece biçimlendirme dizesi yalnızca erişilen ilk kez oluştu:

[!code-csharp[Caching the value of a computed property](../../samples/snippets/csharp/properties/Person.cs#12)]

Yukarıdaki kod, ancak bir hata içeriyor. Kod ya da değeri güncelleştirmeleri olursa `FirstName` veya `LastName` özelliği, daha önce değerlendirilen `fullName` alanı geçersiz. Değiştirmeniz `set` erişimci `FirstName` ve `LastName` özelliği böylece `fullName` alan yeniden hesaplanır:

[!code-csharp[Invalidating the cache correctly](../../samples/snippets/csharp/properties/Person.cs#13)]

Bu son sürümü değerlendirir `FullName` yalnızca gerekli olduğunda özelliği.
Önceden hesaplanmış sürümü geçerli ise kullanılır. Başka bir durum değişikliği önceden hesaplanmış sürümü geçersiz kılar, hesaplanır. Bu sınıf kullanan geliştiriciler uygulama ayrıntılarını bilmeniz gerek yoktur. İç değişikliklerin hiçbiri kişi nesnesinin kullanımını etkiler. Veri üyeleri bir nesnenin kullanıma sunmak için özelliklerini kullanarak anahtar nedenini olmasıdır.

### <a name="attaching-attributes-to-auto-implemented-properties"></a>Otomatik uygulanan özellikler öznitelikleri ekleme

C# 7.3 ile başlayarak, alan öznitelikleri otomatik uygulanan özellikler derleyici oluşturulan yedekleme alanına eklenebilir. Örneğin, bir düzeltme için göz önünde bulundurun `Person` benzersiz bir tamsayı ekler sınıfı `Id` özelliği.
Yazdığınız`Id` otomatik uygulanan bir özellik, ancak tasarımınızı kullanan özellik sürdürmek için çağırmaz `Id` özelliği. <xref:System.NonSerializedAttribute> Alanları, özellikleri yalnızca bağlanabilir. Ekleyebilir miyim <xref:System.NonSerializedAttribute> için yedekleme alanına `Id` kullanarak özellik `field:` aşağıdaki örnekte gösterildiği gibi öznitelikte tanımlayıcısı:

[!code-csharp[Attaching attributes to a backing field](../../samples/snippets/csharp/properties/Person.cs#14)]

Otomatik uygulanan özellikte yedekleme alanını ekleme herhangi bir öznitelik için bu tekniği çalışır.

### <a name="implementing-inotifypropertychanged"></a>INotifyPropertyChanged uygulama

Bir özellik erişimcisini kod yazmanız gereken son bir senaryo desteklemektir <xref:System.ComponentModel.INotifyPropertyChanged> bir değer değiştikten veri bağlama istemcilerine bildirmek için kullanılan arabirim. Bir özellik değeri değiştiğinde, nesneyi başlatır <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged?displayProperty=nameWithType> değişikliği göstermek için olay. Veri kitaplıkları, bağlama sırayla, bu değişiklik temel görüntü öğeleri güncelleştirin. Aşağıdaki kod, nasıl uygulayacağınıza gösterir `INotifyPropertyChanged` için `FirstName` bu kişinin sınıfının özelliği.

[!code-csharp[invalidating the cache correctly](../../samples/snippets/csharp/properties/Person.cs#15)]

`?.` İşleci çağrılır *null koşullu işleç*. Bir null başvuru için işlecinin sağ tarafında değerlendirmeden önce denetler. Hiçbir abonelere varsa olan sonuç `PropertyChanged` değil olay, olayı için kodu yürütün. Throw bir `NullReferenceException` bu durumda bu olmadan denetleyin. Daha fazla bilgi için bkz. [`events`](delegates-events.md). Bu örnek ayrıca yeni `nameof` kendi metin gösterimi olan özellik adı simgesini dönüştürmek için işleci.
Kullanarak `nameof` Burada, yanlış yazmış özelliğinin adı hataları azaltabilir.

Yeniden uygulama <xref:System.ComponentModel.INotifyPropertyChanged> burada yazabilirsiniz kod ihtiyacınız senaryoları desteklemek için erişimcileri içinde bir durumu bir örnektir.

## <a name="summing-up"></a>Özetle

Özellikler, bir sınıf veya nesne akıllı alanları biçimidir. Gelen dışında nesne, nesne alanları gibi görünürler. Ancak, özellikler, C# işlevlerin tam paleti kullanarak uygulanabilir.
Doğrulama, farklı erişilebilirlik, geç değerlendirme veya senaryolarınızı gereken herhangi bir gereksinimi sağlayabilir.
