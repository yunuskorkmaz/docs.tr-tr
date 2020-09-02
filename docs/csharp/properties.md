---
title: Özellikler
description: Doğrulama, hesaplanan değerler, yavaş değerlendirme ve özellik değiştirilen bildirimler için özellikler içeren C# özellikleri hakkında bilgi edinin.
ms.technology: csharp-fundamentals
ms.date: 04/25/2018
ms.openlocfilehash: 28050a77e1f7b0ac148bba6112aa79ef4d46b710
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89358914"
---
# <a name="properties"></a>Özellikler

Özellikler C# içinde ilk sınıf vatandaşları. Dil, geliştiricilerin tasarım amacını doğru şekilde ifade eden kod yazmasını sağlayan sözdizimini tanımlar.

Özellikler erişilen alanlar gibi davranır.
Ancak, alanların aksine özellikler, bir özelliğe erişildiğinde veya atandığında yürütülen deyimleri tanımlayan Erişimcilerde uygulanır.

## <a name="property-syntax"></a>Özellik sözdizimi

Özellikler için sözdizimi, alanlar için doğal bir uzantıdır. Bir alan, depolama konumunu tanımlar:

[!code-csharp[Person class with public fields](../../samples/snippets/csharp/properties/Person.cs#1)]

Bir özellik tanımı `get` `set` , bu özelliğin değerini alan ve atayan bir ve erişimcisi için bildirimleri içerir:

[!code-csharp[Person class with public properties](../../samples/snippets/csharp/properties/Person.cs#2)]

Yukarıda gösterilen sözdizimi *Auto özelliği* sözdizimidir. Derleyici, özelliği yedekleyen alan için depolama konumu oluşturur. Derleyici Ayrıca `get` ve erişimcilerinin gövdesini de uygular `set` .

Bazen bir özelliği, türü için varsayılan değer dışında bir değere başlatmalısınız.  C#, özelliğin kapanış ayracından sonra bir değer ayarlayarak bunu yapmanızı mümkün. Özelliğin başlangıç değerini, `FirstName` yerine boş dize olacak şekilde tercih edebilirsiniz `null` . Aşağıda gösterildiği gibi belirtmeniz gerekir:

[!code-csharp[Person class with properties and initializer](../../samples/snippets/csharp/properties/Person.cs#3)]

Bu makalede daha sonra göreceğiniz gibi, belirli bir başlatma, salt okuma özellikleri için en yararlı seçenektir.

Depolamayı aşağıda gösterildiği gibi kendiniz de tanımlayabilirsiniz:

[!code-csharp[Person class with properties and backing field](../../samples/snippets/csharp/properties/Person.cs#4)]

Bir özellik uygulamasının tek bir ifade olması halinde, alıcı veya ayarlayıcı için *ifade-Bodied Üyeler* kullanabilirsiniz:

[!code-csharp[Person class with properties and expression bodied getters and setters](../../samples/snippets/csharp/properties/Person.cs#5)]

Bu basitleştirilmiş söz dizimi, bu makale boyunca geçerli olan yerlerde kullanılacaktır.

Yukarıda gösterilen özellik tanımı bir okuma-yazma özelliğidir. Set erişimcisindeki anahtar sözcüğe dikkat edin `value` . `set`Erişimcinin her zaman adlı tek bir parametresi vardır `value` . `get`Erişimcinin, özelliğin türüne dönüştürülebilir bir değer döndürmesi gerekir ( `string` Bu örnekte).

Söz dizimi temel bilgileri. Çeşitli farklı tasarım deyimlerini destekleyen birçok farklı çeşitliliğe sahiptir. İnceleyelim ve her biri için sözdizimi seçeneklerini öğrenelim.

## <a name="scenarios"></a>Senaryolar

Yukarıdaki örneklerde, özellik tanımının en basit durumlardan biri gösterildi: doğrulama içermeyen bir okuma-yazma özelliği. `get`Ve Erişimcilerde istediğiniz kodu yazarak `set` birçok farklı senaryo oluşturabilirsiniz.

### <a name="validation"></a>Doğrulama

`set`Bir özellik tarafından temsil edilen değerlerin her zaman geçerli olduğundan emin olmak için erişimciye kod yazabilirsiniz. Örneğin, sınıf için bir kural, `Person` adın boş veya boşluk olamaz. Şöyle yazın:

[!code-csharp[Validating property setters](../../samples/snippets/csharp/properties/Person.cs#6)]

Önceki örnek, `throw` Özellik ayarlayıcısı doğrulamasının bir parçası olarak bir ifade kullanılarak basitleştirilebilir:

[!code-csharp[Validating property setters](../../samples/snippets/csharp/properties/Person.cs#7)]

Yukarıdaki örnekte, ilk adın boş veya boşluk olmaması gerekir kuralını zorlar. Bir geliştirici yazıyorsa

```csharp
hero.FirstName = "";
```

Bu atama bir oluşturur `ArgumentException` . Bir özellik kümesi erişimcisinin void dönüş türüne sahip olması gerektiğinden, özel durum oluşturarak set erişimcisinde hataları raporlayabilir.

Bu söz dizimini, senaryonuza gereken her şeye genişletebilirsiniz. Farklı özellikler arasındaki ilişkileri denetleyebilir veya herhangi bir dış koşula göre doğrulayabilirsiniz. Geçerli C# deyimleri bir özellik erişimcisinde geçerlidir.

### <a name="read-only"></a>Salt okunur

Bu noktaya kadar, gördüğünüze olan tüm özellik tanımlarının ortak erişimcilere sahip okuma/yazma özellikleri vardır. Bu, özellikler için tek geçerli erişilebilirlik değildir.
Salt okunurdur özellikler oluşturabilir veya set ve Get erişimcilerine farklı erişilebilirlik sağlayabilirsiniz. `Person`Sınıfınızın yalnızca `FirstName` özelliğin değerini bu sınıftaki diğer yöntemlerle değiştirmesini öneririz. Bunun yerine set accessor erişilebilirliği verebilirsiniz `private` `public` :

[!code-csharp[Using a private setter for a publicly readonly property](../../samples/snippets/csharp/properties/Person.cs#8)]

Artık, `FirstName` özelliğe herhangi bir koddan erişilebilir, ancak yalnızca sınıftaki diğer koddan atanabilir `Person` .

Küme veya Get erişimcilerine herhangi bir kısıtlayıcı erişim değiştiricisi ekleyebilirsiniz. Bireysel erişimciye yerleştirdiğiniz herhangi bir erişim değiştiricisi, özellik tanımındaki erişim değiştiricisinden daha sınırlı olmalıdır. , `FirstName` Özelliği olduğu `public` , ancak set erişimcisi olduğu için geçerlidir `private` . `private`Bir erişimcisi olan bir özellik bildiremezsiniz `public` . Özellik bildirimleri de,,, veya de olarak bildirilemez `protected` `internal` `protected internal` `private` .

Erişimciye daha kısıtlayıcı değiştirici yerleştirmek de geçerlidir `get` . Örneğin, bir özelliğine sahip olabilirsiniz `public` , ancak `get` erişimciyi olarak kısıtlayabilirsiniz `private` . Bu senaryo uygulamada nadiren yapılır.

Ayrıca, bir özellik üzerinde yapılan değişiklikleri yalnızca bir oluşturucuda veya özellik başlatıcısında ayarlanabilmesi için kısıtlayabilirsiniz. `Person`Sınıfı şu şekilde değiştirebilirsiniz:

[!code-csharp[A readonly auto implemented property](../../samples/snippets/csharp/properties/Person.cs#9)]

Bu özellik, en yaygın olarak salt okunurdur özellikler olarak sunulan koleksiyonları başlatmak için kullanılır:

```csharp
public class Measurements
{
    public ICollection<DataPoint> points { get; } = new List<DataPoint>();
}
```

### <a name="computed-properties"></a>Hesaplanan özellikler

Bir özelliğin yalnızca bir üye alanının değerini döndürmesi gerekmez. Hesaplanan bir değer döndüren özellikler oluşturabilirsiniz. `Person`İlk ve soyadlarını birleştirerek hesaplanan tam adı döndürmek için nesneyi genişletelim:

[!code-csharp[A computed property](../../samples/snippets/csharp/properties/Person.cs#10)]

Yukarıdaki örnek, tam ad için biçimlendirilen dizeyi oluşturmak üzere [dize ilişkilendirme](./language-reference/tokens/interpolated.md) özelliğini kullanır.

Ayrıca, hesaplanan özelliği oluşturmak için daha kısa bir yol sağlayan *Expression-Bodied üyesini*de kullanabilirsiniz `FullName` :

[!code-csharp[A computed property using an expression bodied member](../../samples/snippets/csharp/properties/Person.cs#11)]

*İfade-Bodied Üyeler* , tek bir ifade içeren yöntemleri tanımlamak için *lambda ifadesi* sözdizimini kullanır. Burada, bu ifade kişi nesnesinin tam adını döndürür.

### <a name="cached-evaluated-properties"></a>Önbelleğe alınan değerlendirilen Özellikler

Hesaplanan bir özellik kavramını depolama ile karıştırabilir ve *önbelleğe alınmış bir değerlendirilen Özellik*oluşturabilirsiniz.  Örneğin, `FullName` özelliği yalnızca ilk kez erişildiği zaman dize biçimlendirmesi olacak şekilde güncelleştirebilirsiniz:

[!code-csharp[Caching the value of a computed property](../../samples/snippets/csharp/properties/Person.cs#12)]

Yukarıdaki kod bir hata içeriyor. Kod, ya da özelliğinin değerini güncelleştiriyorsa `FirstName` `LastName` , önceden değerlendirilen `fullName` alan geçersiz olur. `set` `FirstName` Ve `LastName` özelliğinin erişimcileri `fullName` alanını yeniden hesaplanacak şekilde değiştirirsiniz:

[!code-csharp[Invalidating the cache correctly](../../samples/snippets/csharp/properties/Person.cs#13)]

Bu son sürüm, `FullName` özelliği yalnızca gerektiğinde değerlendirir.
Daha önce hesaplanan sürüm geçerliyse, kullanılır. Başka bir durum değişikliği önceden hesaplanan sürümü geçersiz kılar, yeniden hesaplanır. Bu sınıfı kullanan geliştiricilerin uygulamanın ayrıntılarını bilmeleri gerekmez. Bu iç değişikliklerden hiçbiri kişi nesnesinin kullanımını etkilemez. Bu, bir nesnenin veri üyelerini açığa çıkarmak için özellikleri kullanmanın temel nedenidir.

### <a name="attaching-attributes-to-auto-implemented-properties"></a>Öznitelikleri otomatik uygulanan özelliklere iliştirme

C# 7,3 ile başlayarak, alan öznitelikleri otomatik uygulanan özelliklerde derleyicinin ürettiği yedekleme alanına iliştirilebilir. Örneğin, `Person` benzersiz bir tamsayı özelliği ekleyen sınıfa bir düzeltme düşünün `Id` .
`Id`Özelliği otomatik uygulanan bir özellik kullanarak yazarsınız, ancak tasarımınız özelliği kalıcı hale getirmeyi çağırmaz `Id` . , <xref:System.NonSerializedAttribute> Yalnızca alanlara eklenebilir, ancak özelliklere eklenebilir. <xref:System.NonSerializedAttribute> `Id` `field:` Aşağıdaki örnekte gösterildiği gibi, özniteliğinde tanımlayıcısını kullanarak özelliği için yedekleme alanına ekleyebilirsiniz:

[!code-csharp[Attaching attributes to a backing field](../../samples/snippets/csharp/properties/Person.cs#14)]

Bu teknik, otomatik uygulanan özelliğindeki yedekleme alanına eklediğiniz tüm öznitelikler için geçerlidir.

### <a name="implementing-inotifypropertychanged"></a>INotifyPropertyChanged uygulama

Özellik erişimcisine kod yazmanız gereken son senaryo, <xref:System.ComponentModel.INotifyPropertyChanged> veri bağlama istemcilerine bir değerin değiştiğini bildirmek için kullanılan arabirimi desteklemedir. Bir özelliğin değeri değiştiğinde, nesne <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged?displayProperty=nameWithType> değişikliği belirtmek için olayı harekete geçirir. Veri bağlama kitaplıkları, sırasıyla, bu değişikliğe göre görüntüleme öğelerini güncelleştirir. Aşağıdaki kod, `INotifyPropertyChanged` `FirstName` Bu kişi sınıfının özelliği için nasıl uygulanacağını gösterir.

[!code-csharp[invalidating the cache correctly](../../samples/snippets/csharp/properties/Person.cs#15)]

`?.`İşleci *null koşullu işleç*olarak adlandırılır. İşlecin sağ tarafını değerlendirmeden önce null başvurusunu denetler. Nihai sonuç, olay üzerinde abone olmadığında `PropertyChanged` , olayı yürütmek için kodun yürütülmeyeceğini unutmayın. `NullReferenceException`Bu durumda bu onay olmadan bir oluşturur. Daha fazla bilgi için bkz. [`events`](events-overview.md). Bu örnek ayrıca `nameof` özellik adı sembolünden metin gösterimine dönüştürmek için New işlecini de kullanır.
Kullanmak `nameof` , özelliğin adını yanlış yazmış olduğunuz hataları azaltabilir.

Bu durumda, <xref:System.ComponentModel.INotifyPropertyChanged> uygulamanız gereken senaryoları desteklemek için Erişimcilerde kod yazabileceğiniz bir örnek örneğidir.

## <a name="summing-up"></a>Toplam

Özellikler, bir sınıf veya nesne içindeki akıllı alanların bir biçimidir. Nesnenin dışından, nesne içindeki alanlar gibi görünürler. Ancak, Özellikler C# işlevselliğinin tam paleti kullanılarak uygulanabilir.
Doğrulama, farklı erişilebilirlik, geç değerlendirme ya da senaryolarınızın ihtiyaç duyduğu herhangi bir gereksinim sağlayabilirsiniz.
