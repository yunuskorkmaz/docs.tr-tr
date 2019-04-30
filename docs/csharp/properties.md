---
title: Özellikler
description: Hakkında bilgi edinin C# hesaplanan değerler, geç değerlendirme doğrulama özellikleri içeren, özellikler, ve özellik bildirimleri değiştirildi.
ms.date: 04/25/2018
ms.openlocfilehash: d4fa7b6117bec63c41318dd4bcc3850ce55a5907
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675786"
---
# <a name="properties"></a>Özellikler

Birinci sınıf vatandaşlar özelliklerdir C#. Geliştiricilerin, bunların tasarım amacı doğru bir şekilde ifade kod yazmanızı sağlayan sözdizimi dil tanımlar.

Bunlar erişildiğinde özellikleri alanlar gibi davranır.
Ancak, alanları özellikleri bir özellik erişilen veya atandığında, yürütülen deyimleri tanımlayan erişimcileri ile uygulanır.

## <a name="property-syntax"></a>Özellik sözdizimi

Özelliklerinin sözdizimi, alanlar için doğal bir uzantısıdır. Bir alan bir depolama konumu tanımlar:

[!code-csharp[Person class with public fields](../../samples/snippets/csharp/properties/Person.cs#1)]

Bir özellik tanımı bildirimlerini içeren bir `get` ve `set` erişimci alır ve bu özelliğin değeri atar:

[!code-csharp[Person class with public properties](../../samples/snippets/csharp/properties/Person.cs#2)]

Yukarıda gösterilen sözdizimi *otomatik özellik* söz dizimi. Derleyici özelliği yedekleyen alanı için depolama konumu oluşturur. Derleyici ayrıca gövdesinin uygulayan `get` ve `set` erişimcileri.

Bazen, bir tür için varsayılan dışında bir değer özelliğini başlatmak gerekebilir.  C#Bu özellik için kapatma küme ayracından sonra bir değer ayarlayarak sağlar. İlk değeri tercih edebilirsiniz `FirstName` boş bir dize özelliğini yerine `null`. Aşağıda gösterildiği gibi belirtmeniz gerekir:

[!code-csharp[Person class with properties and initializer](../../samples/snippets/csharp/properties/Person.cs#3)]

Bu makalenin sonraki bölümlerinde anlatıldığı gibi belirli başlatma salt okunur özellikler için en kullanışlıdır.

Aşağıda gösterildiği gibi depolama kendiniz de tanımlayabilirsiniz:

[!code-csharp[Person class with properties and backing field](../../samples/snippets/csharp/properties/Person.cs#4)]

Bir özellik uygulama tek bir ifade olduğunda kullanabileceğiniz *ifade gövdeli üyeler* alıcı veya ayarlayıcı için:

[!code-csharp[Person class with properties and expression bodied getters and setters](../../samples/snippets/csharp/properties/Person.cs#5)]

Bu Basitleştirilmiş söz dizimi, bu makalenin tamamında uygun olduğunda kullanılır.

Yukarıda gösterilen özellik tanımı, bir okuma-yazma özelliğidir. Anahtar sözcüğü fark `value` set erişimcisine içinde. `set` Erişimci her zaman adlı tek bir parametreye sahip `value`. `get` Erişimci özelliğin türüne dönüştürülebilen bir değer döndürmesi gerekir (`string` Bu örnekte).

Söz dizimi temelleri olmasıdır. Farklı tasarım deyimleri çeşitli destek pek çok farklı Çeşitleme vardır. Şimdi keşfedin ve her söz dizimi seçenek öğrenin.

## <a name="scenarios"></a>Senaryolar

Yukarıdaki örneklerde gösterilen özellik tanımının en basit durumlarından biri: doğrulama bir okuma-yazma özelliği. Kod yazarak istediğiniz `get` ve `set` erişimcileri, birçok farklı senaryo oluşturabilirsiniz.

### <a name="validation"></a>Doğrulama

Kod yazabileceğiniz `set` erişimci özelliği tarafından temsil edilen değerler her zaman geçerli olduğundan emin olmak için. Örneğin, bir kural için varsayalım `Person` sınıfı, adı boş veya boşluk olamaz. Aşağıdaki gibi yazmalısınız:

[!code-csharp[Validating property setters](../../samples/snippets/csharp/properties/Person.cs#6)]

Önceki örnekte kullanarak basit hale getirilebilir bir`throw` özellik ayarlayıcı doğrulama bir parçası olarak ifade:

[!code-csharp[Validating property setters](../../samples/snippets/csharp/properties/Person.cs#7)]

Yukarıdaki örnekte kural adı boş olmamalı veya boşluk zorlar. Bir geliştirici yazma

```csharp
hero.FirstName = "";
```

Bu atamayı oluşturur bir `ArgumentException`. Bir özellik kümesi erişimcisi, dönüş türü void olmalıdır çünkü bir özel durum tarafından set erişimcisine hataları bildirin.

Senaryonuzda gereken her şeyi aynı bu söz dizimini genişletebilirsiniz. Farklı özellikler arasındaki ilişkileri denetleyin veya dış koşulları karşı doğrulayın. Herhangi bir geçerli C# deyimleri bir özellik erişimcisi geçerlidir.

### <a name="read-only"></a>salt okunur

Bu noktaya kadar açtığınız tüm özellik tanımları ile ortak erişimciler okuma/yazma özellikleri ' dir. Yalnızca geçerli erişilebilirlik özellikleri için değil.
Salt okunur özelliklerini oluşturun veya farklı erişilebilirliğe kümesine vermek ve get erişimcileri. Varsayın, `Person` sınıfı, değerinin değiştirilmesi yalnızca etkinleştirmelisiniz `FirstName` o sınıftaki diğer yöntemleri özelliği. Set erişimcisine müdürün `private` erişilebilirlik yerine `public`:

[!code-csharp[Using a private setter for a publicly readonly property](../../samples/snippets/csharp/properties/Person.cs#8)]

Şimdi, `FirstName` özelliği herhangi bir koddan erişilebilir, ancak diğer koddan yalnızca atanabilir `Person` sınıfı.

Herhangi bir kısıtlayıcı erişim değiştiricisi kümesi ya da ekleyebilir veya get erişimcileri. Tek tek erişimcisine yerleştirdiğiniz herhangi erişim değiştiricisi özellik tanımı erişim değiştiricisi daha sınırlı olmalıdır. Yukarıdaki yasal çünkü `FirstName` özelliği `public`, ancak set erişimcisine `private`. Değil bildirip bir `private` özelliğiyle bir `public` erişimcisi. Özellik bildirimleri de bildirilebilir `protected`, `internal`, `protected internal`, veya hatta `private`.

Ayrıca daha kısıtlayıcı değiştiricisi yerleştirmek için yasal `get` erişimcisi. Örneğin, olabilir bir `public` özelliği, ancak kısıtlama `get` için erişimci `private`. Bu senaryo, uygulamada nadiren gerçekleştirilir.

Böylece bir oluşturucu veya bir özellik başlatıcısının içinde yalnızca ayarlanabilir da bir özellik değişiklikleri kısıtlayabilirsiniz. Değiştirebileceğiniz `Person` bunu aşağıdaki gibi sınıf:

[!code-csharp[A readonly auto implemented property](../../samples/snippets/csharp/properties/Person.cs#9)]

Bu özellik salt okunur özellikler olarak sunulan koleksiyonlar başlatmak için en yaygın olarak kullanılır:

```csharp
public class Measurements
{
    public ICollection<DataPoint> points { get; } = new List<DataPoint>();
}
```

### <a name="computed-properties"></a>Hesaplanan Özellikler

Yalnızca bir üye alanın değerini döndürmek bir özellik gerekmez. Hesaplanan değeri döndüren özellikler oluşturabilirsiniz. Şimdi genişletin `Person` ilk ve son adları birleştirerek hesaplanan tam adı döndürülecek nesne:

[!code-csharp[A computed property](../../samples/snippets/csharp/properties/Person.cs#10)]

Kullanan yukarıdaki örnekte [dize ilişkilendirme](../csharp/language-reference/tokens/interpolated.md) tam adı için biçimlendirilmiş dize oluşturmak için özellik.

Ayrıca bir *ifade gövdeli üye*, hesaplanan oluşturmak için daha birleştiren bir yöntem sunan `FullName` özelliği:

[!code-csharp[A computed property using an expression bodied member](../../samples/snippets/csharp/properties/Person.cs#11)]

*İfade gövdeli üyeler* kullanın *lambda ifadesi* tek bir ifade içeren yöntemleri tanımlamak için söz dizimi. Burada, bu ifade, kişi nesnesinin tam adını döndürür.

### <a name="cached-evaluated-properties"></a>Önbelleğe alınan değerlendirilen Özellikler

Hesaplanan bir özellik kavramını depolama ile karışık ve oluşturma bir *hesaplanan özellik önbelleğe*.  Örneğin, güncelleştiremedi `FullName` özelliği böylece biçimlendirme dizesi yalnızca ilk kez erişildi, oldu:

[!code-csharp[Caching the value of a computed property](../../samples/snippets/csharp/properties/Person.cs#12)]

Yukarıdaki kod, ancak bir hata içeriyor. Kod ya da değerini güncelleştiriyorsa `FirstName` veya `LastName` özelliği, daha önce değerlendirilmesini `fullName` alanı geçersiz. Değişiklik `set` erişicilerini `FirstName` ve `LastName` özelliği böylece `fullName` alan yeniden hesaplanır:

[!code-csharp[Invalidating the cache correctly](../../samples/snippets/csharp/properties/Person.cs#13)]

Bu son sürümü değerlendirir `FullName` yalnızca gerektiğinde özelliği.
Önceden hesaplanmış sürüm geçerli ise kullanılır. Önceden hesaplanmış sürüm başka bir durum değişikliği geçersiz kılar, hesaplanır. Bu sınıfı kullanan geliştiriciler, uygulama ayrıntılarını bilmeniz gerekmez. İç değişikliklerin hiçbiri kişi nesnesinin kullanımını etkiler. Bir nesnenin üyelerine verileri göstermek için özellikleri kullanmak için anahtar neden olmasıdır.

### <a name="attaching-attributes-to-auto-implemented-properties"></a>Otomatik uygulanan özellikler için öznitelikleri ekleme

İle başlayarak C# 7.3, alan öznitelikleri eklenebilir derleyicinin ürettiği yedekleme alanını otomatik olarak uygulanan özellikler için. Örneğin, bir düzeltmeyi düşünün `Person` benzersiz bir tamsayı ekler sınıfı `Id` özelliği.
Yazdığınız`Id` otomatik uygulanan bir özellik, ancak tasarımınızı kullanan özellik kalıcı hale getirilmesine yönelik çağırmaz `Id` özelliği. <xref:System.NonSerializedAttribute> Alanları, özellikleri yalnızca eklenebilir. İliştirebilirsiniz <xref:System.NonSerializedAttribute> yedekleme alanına `Id` özelliğini kullanarak `field:` belirticisi özniteliği aşağıdaki örnekte gösterildiği gibi üzerinde:

[!code-csharp[Attaching attributes to a backing field](../../samples/snippets/csharp/properties/Person.cs#14)]

Bu teknik yedekleme alanını otomatik uygulanan özellik için eklediğiniz herhangi bir öznitelik için geçerlidir.

### <a name="implementing-inotifypropertychanged"></a>INotifyPropertyChanged uygulama

Gerek duyduğunuz özellik erişimcisinde kod yazmak için son bir senaryo desteklemektir <xref:System.ComponentModel.INotifyPropertyChanged> bir değer değiştikten veri bağlama istemcilerine bildirmek için kullanılan arabirim. Bir özelliğin değeri değiştiğinde, nesneyi başlatır <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged?displayProperty=nameWithType> olay değişikliği göstermek için. Veri bağlama kitaplıkları, sırasıyla görüntüleme öğeleri üzerinde bu değişikliği göre güncelleştirin. Aşağıdaki kod nasıl uygulamak gösterir `INotifyPropertyChanged` için `FirstName` bu kişi sınıfın özelliği.

[!code-csharp[invalidating the cache correctly](../../samples/snippets/csharp/properties/Person.cs#15)]

`?.` İşleci çağrıldığında *null koşullu işleci*. İşlecin sağ tarafındaki değerlendirmeden önce bir null başvuru için denetler. Hiçbir abonelere varsa olan sonuç `PropertyChanged` değil olay, olayı için kodu yürütün. Throw bir `NullReferenceException` bu durumda bu olmadan denetleyin. Daha fazla bilgi için bkz. [`events`](delegates-events.md). Bu örnek ayrıca yeni kullanır `nameof` özelliği adı sembolünden kendi metin gösterimine dönüştürmek için işleci.
Kullanarak `nameof` Burada, yanlış yazmış özelliğin adını hataları azaltabilir.

Uygulama yeniden <xref:System.ComponentModel.INotifyPropertyChanged> nerede yazabilirsiniz kod ihtiyacınız senaryolarını desteklemek üzere erişenler bir servis talebi örneğidir.

## <a name="summing-up"></a>Özetle

Özellikleri, bir sınıf veya nesne akıllı alanların bir biçimidir. Gelen nesne nesne alanları gibi görünürler. Ancak, özellikleri tam paletini kullanarak uygulanabilir C# işlevselliği.
Doğrulama, farklı erişilebilirlik, geç değerlendirme veya senaryolarınızı gereken herhangi bir gereksinim sağlayabilir.
