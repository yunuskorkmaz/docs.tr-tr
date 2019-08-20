---
title: Özellikler
description: Doğrulama, C# hesaplanan değerler, geç değerlendirme ve özellik değiştirilen bildirimler için özellikler içeren özellikler hakkında bilgi edinin.
ms.date: 04/25/2018
ms.openlocfilehash: 6638ae74516d7546882c8a380eed9b03ff3d18e9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587410"
---
# <a name="properties"></a>Özellikler

Özellikler ilk sınıf vatandaşları ' C#dir. Dil, geliştiricilerin tasarım amacını doğru şekilde ifade eden kod yazmasını sağlayan sözdizimini tanımlar.

Özellikler erişilen alanlar gibi davranır.
Ancak, alanların aksine özellikler, bir özelliğe erişildiğinde veya atandığında yürütülen deyimleri tanımlayan Erişimcilerde uygulanır.

## <a name="property-syntax"></a>Özellik sözdizimi

Özellikler için sözdizimi, alanlar için doğal bir uzantıdır. Bir alan, depolama konumunu tanımlar:

[!code-csharp[Person class with public fields](../../samples/snippets/csharp/properties/Person.cs#1)]

Bir özellik tanımı, bu özelliğin değerini `get` alan `set` ve atayan bir ve erişimcisi için bildirimleri içerir:

[!code-csharp[Person class with public properties](../../samples/snippets/csharp/properties/Person.cs#2)]

Yukarıda gösterilen sözdizimi *Auto özelliği* sözdizimidir. Derleyici, özelliği yedekleyen alan için depolama konumu oluşturur. Derleyici Ayrıca `get` ve `set` erişimcilerinin gövdesini de uygular.

Bazen bir özelliği, türü için varsayılan değer dışında bir değere başlatmalısınız.  C#özelliği için kapanış ayracından sonra bir değer ayarlayarak bunu yapmanızı mümkün. `FirstName` Özelliğin başlangıç değerini, `null`yerine boş dize olacak şekilde tercih edebilirsiniz. Aşağıda gösterildiği gibi belirtmeniz gerekir:

[!code-csharp[Person class with properties and initializer](../../samples/snippets/csharp/properties/Person.cs#3)]

Bu makalede daha sonra göreceğiniz gibi, belirli bir başlatma, salt okuma özellikleri için en yararlı seçenektir.

Depolamayı aşağıda gösterildiği gibi kendiniz de tanımlayabilirsiniz:

[!code-csharp[Person class with properties and backing field](../../samples/snippets/csharp/properties/Person.cs#4)]

Bir özellik uygulamasının tek bir ifade olması halinde, alıcı veya ayarlayıcı için *ifade-Bodied Üyeler* kullanabilirsiniz:

[!code-csharp[Person class with properties and expression bodied getters and setters](../../samples/snippets/csharp/properties/Person.cs#5)]

Bu basitleştirilmiş söz dizimi, bu makale boyunca geçerli olan yerlerde kullanılacaktır.

Yukarıda gösterilen özellik tanımı bir okuma-yazma özelliğidir. Set erişimcisindeki `value` anahtar sözcüğe dikkat edin. Erişimcinin her zaman adlı `value`tek bir parametresi vardır. `set` Erişimcinin, özelliğin türüne dönüştürülebilir bir değer döndürmesi gerekir (`string` Bu örnekte). `get`

Söz dizimi temel bilgileri. Çeşitli farklı tasarım deyimlerini destekleyen birçok farklı çeşitliliğe sahiptir. İnceleyelim ve her biri için sözdizimi seçeneklerini öğrenelim.

## <a name="scenarios"></a>Senaryolar

Yukarıdaki örneklerde, özellik tanımının en basit durumlardan biri gösterildi: doğrulama içermeyen bir okuma-yazma özelliği. `get` Ve`set` Erişimcilerde istediğiniz kodu yazarak birçok farklı senaryo oluşturabilirsiniz.

### <a name="validation"></a>Doğrulama

Bir özellik tarafından temsil edilen değerlerin `set` her zaman geçerli olduğundan emin olmak için erişimciye kod yazabilirsiniz. Örneğin, `Person` sınıf için bir kural, adın boş veya boşluk olamaz. Şöyle yazın:

[!code-csharp[Validating property setters](../../samples/snippets/csharp/properties/Person.cs#6)]

Önceki örnek, Özellik ayarlayıcısı doğrulamasının bir parçası olarak`throw` bir ifade kullanılarak basitleştirilebilir:

[!code-csharp[Validating property setters](../../samples/snippets/csharp/properties/Person.cs#7)]

Yukarıdaki örnekte, ilk adın boş veya boşluk olmaması gerekir kuralını zorlar. Bir geliştirici yazıyorsa

```csharp
hero.FirstName = "";
```

Bu atama bir `ArgumentException`oluşturur. Bir özellik kümesi erişimcisinin void dönüş türüne sahip olması gerektiğinden, özel durum oluşturarak set erişimcisinde hataları raporlayabilir.

Bu söz dizimini, senaryonuza gereken her şeye genişletebilirsiniz. Farklı özellikler arasındaki ilişkileri denetleyebilir veya herhangi bir dış koşula göre doğrulayabilirsiniz. Bir özellik C# erişimcisinde geçerli deyimler geçerlidir.

### <a name="read-only"></a>Salt okunurdur

Bu noktaya kadar, gördüğünüze olan tüm özellik tanımlarının ortak erişimcilere sahip okuma/yazma özellikleri vardır. Bu, özellikler için tek geçerli erişilebilirlik değildir.
Salt okunurdur özellikler oluşturabilir veya set ve Get erişimcilerine farklı erişilebilirlik sağlayabilirsiniz. `Person` Sınıfınızın yalnızca `FirstName` özelliğin değerini bu sınıftaki diğer yöntemlerle değiştirmesini öneririz. Bunun yerine set accessor `private` erişilebilirliği verebilirsiniz: `public`

[!code-csharp[Using a private setter for a publicly readonly property](../../samples/snippets/csharp/properties/Person.cs#8)]

Artık, `FirstName` özelliğe herhangi bir koddan erişilebilir, ancak yalnızca `Person` sınıftaki diğer koddan atanabilir.

Küme veya Get erişimcilerine herhangi bir kısıtlayıcı erişim değiştiricisi ekleyebilirsiniz. Bireysel erişimciye yerleştirdiğiniz herhangi bir erişim değiştiricisi, özellik tanımındaki erişim değiştiricisinden daha sınırlı olmalıdır. `FirstName` , Özelliğiolduğu`private`,ancakset erişimcisi olduğu için geçerlidir. `public` `private` Bir`public` erişimcisi olan bir özellik bildiremezsiniz. Özellik bildirimleri de,,, `protected`veya `internal` `private`de `protected internal`olarak bildirilemez.

`get` Erişimciye daha kısıtlayıcı değiştirici yerleştirmek de geçerlidir. Örneğin, bir `public` özelliğine sahip olabilirsiniz, ancak `get` erişimciyi olarak `private`kısıtlayabilirsiniz. Bu senaryo uygulamada nadiren yapılır.

Ayrıca, bir özellik üzerinde yapılan değişiklikleri yalnızca bir oluşturucuda veya özellik başlatıcısında ayarlanabilmesi için kısıtlayabilirsiniz. `Person` Sınıfı şu şekilde değiştirebilirsiniz:

[!code-csharp[A readonly auto implemented property](../../samples/snippets/csharp/properties/Person.cs#9)]

Bu özellik, en yaygın olarak salt okunurdur özellikler olarak sunulan koleksiyonları başlatmak için kullanılır:

```csharp
public class Measurements
{
    public ICollection<DataPoint> points { get; } = new List<DataPoint>();
}
```

### <a name="computed-properties"></a>Hesaplanan özellikler

Bir özelliğin yalnızca bir üye alanının değerini döndürmesi gerekmez. Hesaplanan bir değer döndüren özellikler oluşturabilirsiniz. İlk ve soyadlarını `Person` birleştirerek hesaplanan tam adı döndürmek için nesneyi genişletelim:

[!code-csharp[A computed property](../../samples/snippets/csharp/properties/Person.cs#10)]

Yukarıdaki örnek, tam ad için biçimlendirilen dizeyi oluşturmak üzere [dize ilişkilendirme](./language-reference/tokens/interpolated.md) özelliğini kullanır.

Ayrıca, hesaplanan `FullName` özelliği oluşturmak için daha kısa bir yol sağlayan *Expression-Bodied üyesini*de kullanabilirsiniz:

[!code-csharp[A computed property using an expression bodied member](../../samples/snippets/csharp/properties/Person.cs#11)]

*İfade-Bodied Üyeler* , tek bir ifade içeren yöntemleri tanımlamak için *lambda ifadesi* sözdizimini kullanır. Burada, bu ifade kişi nesnesinin tam adını döndürür.

### <a name="cached-evaluated-properties"></a>Önbelleğe alınan değerlendirilen Özellikler

Hesaplanan bir özellik kavramını depolama ile karıştırabilir ve *önbelleğe alınmış bir değerlendirilen Özellik*oluşturabilirsiniz.  Örneğin, `FullName` özelliği yalnızca ilk kez erişildiği zaman dize biçimlendirmesi olacak şekilde güncelleştirebilirsiniz:

[!code-csharp[Caching the value of a computed property](../../samples/snippets/csharp/properties/Person.cs#12)]

Yukarıdaki kod bir hata içeriyor. Kod, `FirstName` ya `LastName` da özelliğinin değerini güncelleştiriyorsa, önceden değerlendirilen `fullName` alan geçersiz olur. `FirstName` Ve özelliğininerişimcilerialanınıyeniden`set`hesaplanacak şekildedeğiştirirsiniz:`LastName` `fullName`

[!code-csharp[Invalidating the cache correctly](../../samples/snippets/csharp/properties/Person.cs#13)]

Bu son sürüm, `FullName` özelliği yalnızca gerektiğinde değerlendirir.
Daha önce hesaplanan sürüm geçerliyse, kullanılır. Başka bir durum değişikliği önceden hesaplanan sürümü geçersiz kılar, yeniden hesaplanır. Bu sınıfı kullanan geliştiricilerin uygulamanın ayrıntılarını bilmeleri gerekmez. Bu iç değişikliklerden hiçbiri kişi nesnesinin kullanımını etkilemez. Bu, bir nesnenin veri üyelerini açığa çıkarmak için özellikleri kullanmanın temel nedenidir.

### <a name="attaching-attributes-to-auto-implemented-properties"></a>Öznitelikleri otomatik uygulanan özelliklere iliştirme

7,3 ile C# başlayarak, alan öznitelikleri otomatik uygulanan özelliklerde derleyicinin ürettiği yedekleme alanına iliştirilebilir. Örneğin, benzersiz bir tamsayı `Person` `Id` özelliği ekleyen sınıfa bir düzeltme düşünün.
`Id` Özelliği otomatik uygulanan bir özellik kullanarak yazarsınız, ancak tasarımınız `Id` özelliği kalıcı hale getirmeyi çağırmaz. , <xref:System.NonSerializedAttribute> Yalnızca alanlara eklenebilir, ancak özelliklere eklenebilir. Aşağıdaki örnekte gösterildiği gibi <xref:System.NonSerializedAttribute> , özniteliğinde `field:` tanımlayıcısını kullanarak `Id` özelliği için yedekleme alanına ekleyebilirsiniz:

[!code-csharp[Attaching attributes to a backing field](../../samples/snippets/csharp/properties/Person.cs#14)]

Bu teknik, otomatik uygulanan özelliğindeki yedekleme alanına eklediğiniz tüm öznitelikler için geçerlidir.

### <a name="implementing-inotifypropertychanged"></a>INotifyPropertyChanged uygulama

Özellik erişimcisine kod yazmanız gereken son senaryo, veri bağlama istemcilerine bir değerin değiştiğini bildirmek için <xref:System.ComponentModel.INotifyPropertyChanged> kullanılan arabirimi desteklemedir. Bir özelliğin değeri değiştiğinde, nesne değişikliği belirtmek için <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged?displayProperty=nameWithType> olayı harekete geçirir. Veri bağlama kitaplıkları, sırasıyla, bu değişikliğe göre görüntüleme öğelerini güncelleştirir. Aşağıdaki kod, bu kişi sınıfının `INotifyPropertyChanged` `FirstName` özelliği için nasıl uygulanacağını gösterir.

[!code-csharp[invalidating the cache correctly](../../samples/snippets/csharp/properties/Person.cs#15)]

İşleci null koşullu işleç olarak adlandırılır. `?.` İşlecin sağ tarafını değerlendirmeden önce null başvurusunu denetler. Nihai sonuç, `PropertyChanged` olay üzerinde abone olmadığında, olayı yürütmek için kodun yürütülmeyeceğini unutmayın. Bu durumda bu onay `NullReferenceException` olmadan bir oluşturur. Daha fazla bilgi için bkz. [`events`](events-overview.md). Bu örnek ayrıca Özellik adı sembolünden metin gösterimine dönüştürmek için New `nameof` işlecini de kullanır.
Kullanmak `nameof` , özelliğin adını yanlış yazmış olduğunuz hataları azaltabilir.

Bu durumda, <xref:System.ComponentModel.INotifyPropertyChanged> uygulamanız gereken senaryoları desteklemek için Erişimcilerde kod yazabileceğiniz bir örnek örneğidir.

## <a name="summing-up"></a>Toplam

Özellikler, bir sınıf veya nesne içindeki akıllı alanların bir biçimidir. Nesnenin dışından, nesne içindeki alanlar gibi görünürler. Ancak, özellikler tam C# işlevsellik paleti kullanılarak uygulanabilir.
Doğrulama, farklı erişilebilirlik, geç değerlendirme ya da senaryolarınızın ihtiyaç duyduğu herhangi bir gereksinim sağlayabilirsiniz.
