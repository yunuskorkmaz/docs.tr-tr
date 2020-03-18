---
title: Özellikler
description: Doğrulama, hesaplanan değerler, tembel değerlendirme ve özellik değiştirilen bildirimler için özellikler içeren C# özellikleri hakkında bilgi edinin.
ms.technology: csharp-fundamentals
ms.date: 04/25/2018
ms.openlocfilehash: bda8a4f58f71b57248296dd4ba9f9bf4cbed40d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399415"
---
# <a name="properties"></a>Özellikler

Mülkler C#'daki birinci sınıf vatandaşlardır. Dil, geliştiricilerin tasarım amaçlarını doğru bir şekilde ifade eden kod yazmalarını sağlayan sözdizimini tanımlar.

Özellikler erişildiğinde alanlar gibi olur.
Ancak, alanların aksine, özellikler, bir özelliğe erişildiğinde veya atandığında yürütülen deyimleri tanımlayan erişimcilerle birlikte uygulanır.

## <a name="property-syntax"></a>Özellik sözdizimi

Özellikler için sözdizimi alanlara doğal bir uzantısıdır. Alan bir depolama konumunu tanımlar:

[!code-csharp[Person class with public fields](../../samples/snippets/csharp/properties/Person.cs#1)]

Özellik tanımı, bu özelliğin değerini alan ve atayan bir `get` ve `set` erişimcinin bildirimlerini içerir:

[!code-csharp[Person class with public properties](../../samples/snippets/csharp/properties/Person.cs#2)]

Yukarıda gösterilen sözdizimi *otomatik özellik* sözdizimidir. Derleyici, özelliği destekleyen alanın depolama konumunu oluşturur. Derleyici aynı zamanda ve `get` `set` erişenelerin gövdesini de uygular.

Bazen, bir özelliği türü için varsayılan değer den başka bir değere başlatmanız gerekir.  C# özelliği için kapanış ayraç sonra bir değer ayarlayarak sağlar. `FirstName` Özelliğin ilk değerinin `null`boş dize yerine boş dize olmasını tercih edebilirsiniz. Aşağıda gösterildiği gibi belirtebilirsiniz:

[!code-csharp[Person class with properties and initializer](../../samples/snippets/csharp/properties/Person.cs#3)]

Bu makalede daha sonra göreceğiniz gibi, özel başlatma en çok salt okunur özellikler için yararlıdır.

Ayrıca, aşağıda gösterildiği gibi depolama yı kendiniz de tanımlayabilirsiniz:

[!code-csharp[Person class with properties and backing field](../../samples/snippets/csharp/properties/Person.cs#4)]

Özellik uygulaması tek bir ifade olduğunda, gelen veya ayarlayıcı için *ifade gövdeli üyeleri* kullanabilirsiniz:

[!code-csharp[Person class with properties and expression bodied getters and setters](../../samples/snippets/csharp/properties/Person.cs#5)]

Bu basitleştirilmiş sözdizimi, bu makale boyunca geçerli olduğu durumlarda kullanılacaktır.

Yukarıda gösterilen özellik tanımı bir okuma-yazma özelliğidir. Ayarlanan erişimdeki anahtar kelimeye `value` dikkat edin. Erişimcinin `set` her zaman adı `value`tek bir parametre vardır. Erişimci, `get` özelliğin türüne dönüştürülebilir bir değer döndürmelidir (bu`string` örnekte).

Sözdiziminin temelleri bu. Farklı tasarım deyimleri çeşitli destekleyen birçok farklı varyasyonları vardır. Her biri için sözdizimi seçeneklerini inceleyelim ve öğrenelim.

## <a name="scenarios"></a>Senaryolar

Yukarıdaki örnekler özellik tanımının en basit örneklerinden birini gösterdi: doğrulama olmayan bir okuma-yazma özelliği. İstediğiniz kodu `get` ve `set` erişimcileri yazarak, birçok farklı senaryo oluşturabilirsiniz.

### <a name="validation"></a>Doğrulama

Bir özellik tarafından `set` temsil edilen değerlerin her zaman geçerli olduğundan emin olmak için erişime erişime kod yazabilirsiniz. Örneğin, `Person` sınıf için bir kural, adın boş veya beyaz boşluk olamaz olduğunu varsayalım. Bunu şöyle yazacaktın:

[!code-csharp[Validating property setters](../../samples/snippets/csharp/properties/Person.cs#6)]

Önceki örnek, özellik ayarlayıcı doğrulamasının bir parçası olarak bir`throw` ifade kullanılarak basitleştirilmiş olabilir:

[!code-csharp[Validating property setters](../../samples/snippets/csharp/properties/Person.cs#7)]

Yukarıdaki örnek, ilk adın boş veya beyaz boşluk olmaması gerektiği kuralını zorlar. Bir geliştirici yazarsa

```csharp
hero.FirstName = "";
```

Bu atama bir `ArgumentException`. Özellik kümesi aksesuarı geçersiz bir iade türüne sahip olduğundan, bir özel durum oluşturarak ayarlanan erişimcideki hataları bildirirsiniz.

Aynı sözdizimini senaryonuzda gereken her şeye genişletebilirsiniz. Farklı özellikler arasındaki ilişkileri denetleyebilir veya dış koşullara karşı doğrulayabilirsiniz. Geçerli C# ifadeleri bir özellik aksesuarında geçerlidir.

### <a name="read-only"></a>Salt okunur

Bu noktaya kadar, gördüğünüz tüm özellik tanımları ortak erişime sahip okuma/yazma özellikleridir. Özellikler için tek geçerli erişilebilirlik bu değildir.
Salt okunur özellikler oluşturabilir veya kümeye farklı erişilebilirlik verebilir ve erişimsağlayanlar elde edebilirsiniz. Sınıfınızın `Person` yalnızca `FirstName` özelliğin değerini o sınıftaki diğer yöntemlerden değiştirmeyi etkinleştirmesi gerektiğini varsayalım. Aşağıdakiler yerine ayarlanan `private` erişime erişim `public`sağlayabilirsiniz:

[!code-csharp[Using a private setter for a publicly readonly property](../../samples/snippets/csharp/properties/Person.cs#8)]

Şimdi, `FirstName` özellik herhangi bir koddan erişilebilir, ancak yalnızca sınıftaki `Person` diğer kodlardan atanabilir.

Herhangi bir kısıtlayıcı erişim değiştiricisini kümeye ekleyebilir veya erişimcilere ulaşabilirsiniz. Tek tek erişime yerleştirdiğiniz herhangi bir erişim değiştirici, özellik tanımındaki erişim değiştiricisinden daha sınırlı olmalıdır. Özellik olduğu `FirstName` `public`için yukarıdaki yasal , ancak ayarlanan erişimci . `private` Bir aksesuarı `private` olan bir `public` mülkü bildiremediniz. Özellik beyanları da `protected`ilan `internal` `protected internal`edilebilir , `private`, , , hatta .

`get` Ayrıca, daha kısıtlayıcı değiştiricinin aksesuara yerlefı yapmak da yasaldır. Örneğin, bir `public` özelliğiniz olabilir, ancak `get` erişime `private`gireni . Bu senaryo pratikte nadiren yapılır.

Bir özellik için yapılan değişiklikleri, yalnızca bir oluşturucu veya özellik başlatılmasında ayarlanabilmesi için de kısıtlayabilirsiniz. `Person` Sınıfı aşağıdaki şekilde değiştirebilirsiniz:

[!code-csharp[A readonly auto implemented property](../../samples/snippets/csharp/properties/Person.cs#9)]

Bu özellik en sık salt okunur özellikleri olarak ortaya çıkarılan koleksiyonları n için başlatmaiçin kullanılır:

```csharp
public class Measurements
{
    public ICollection<DataPoint> points { get; } = new List<DataPoint>();
}
```

### <a name="computed-properties"></a>Hesaplanmış özellikler

Bir özelliğin yalnızca üye alanın değerini döndürmesi gerekmez. Hesaplanan bir değer döndüren özellikler oluşturabilirsiniz. Nesneyi, `Person` ad ve soyadlarını biraraya getirerek hesaplanan tam adı döndürmek için genişletelim:

[!code-csharp[A computed property](../../samples/snippets/csharp/properties/Person.cs#10)]

Yukarıdaki örnekte, tam ad için biçimlendirilmiş dize oluşturmak için [dize enterpolasyon](./language-reference/tokens/interpolated.md) özelliği ni kullanır.

Ayrıca, hesaplanan `FullName` özelliği oluşturmak için daha kısa bir yol sağlayan *ifade gövdeli*bir üye de kullanabilirsiniz:

[!code-csharp[A computed property using an expression bodied member](../../samples/snippets/csharp/properties/Person.cs#11)]

*İfade gövdeli üyeler,* tek bir ifade içeren yöntemleri tanımlamak için *lambda ifade* sözdizimini kullanırlar. Burada, bu ifade kişi nesnesinin tam adını döndürür.

### <a name="cached-evaluated-properties"></a>Önbelleğe alınmış değerlendirilen özellikler

Hesaplanmış bir özellik kavramını depolama yla karıştırabilir ve *önbelleğe alınmış bir özellik*oluşturabilirsiniz.  Örneğin, `FullName` özelliği, dize biçimlendirmesinin yalnızca ilk erişilen de olması için güncelleştirebilirsiniz:

[!code-csharp[Caching the value of a computed property](../../samples/snippets/csharp/properties/Person.cs#12)]

Yukarıdaki kod olsa bir hata içerir. Kod, özelliğin `FirstName` veya `LastName` özelliğin değerini güncelleştirirse, daha önce değerlendirilen `fullName` alan geçersizdir. Alanın yeniden `set` hesaplanacak şekilde `FirstName` `LastName` erişimci lerini ve özelliğini değiştirirsiniz: `fullName`

[!code-csharp[Invalidating the cache correctly](../../samples/snippets/csharp/properties/Person.cs#13)]

Bu son sürüm `FullName` özelliği yalnızca gerektiğinde değerlendirir.
Önceden hesaplanan sürüm geçerliyse, kullanılır. Başka bir durum değişikliği önceden hesaplanan sürümü geçersiz kılınıyorsa, yeniden hesaplanır. Bu sınıfı kullanan geliştiricilerin uygulamanın ayrıntılarını bilmesi gerekmez. Bu iç değişikliklerin hiçbiri Kişi nesnesinin kullanımını etkilemez. Bir nesnenin veri üyelerini ortaya çıkarmak için Özellikler'i kullanmanın temel nedeni budur.

### <a name="attaching-attributes-to-auto-implemented-properties"></a>Öznitelikleri otomatik olarak uygulanan özelliklere ekleme

C# 7.3 ile başlayarak, alan öznitelikleri otomatik uygulanan özelliklerde derleyici oluşturulan destek alanına eklenebilir. Örneğin, benzersiz bir tamsayı `Person` `Id` özelliği ekleyen sınıfa bir düzeltme düşünün.
`Id` Özelliği otomatik olarak uygulanan bir özelliği kullanarak yazarsınız, ancak tasarımınız `Id` özelliğin kalıcı olarak kullanılmasını gerektirmez. Yalnızca <xref:System.NonSerializedAttribute> alanlara bağlanabilir, özelliklere değil. Aşağıdaki örnekte <xref:System.NonSerializedAttribute> gösterildiği gibi, `Id` öznitelik üzerinde `field:` belirtici kullanarak özelliğin destek alanına ekleyebilirsiniz:

[!code-csharp[Attaching attributes to a backing field](../../samples/snippets/csharp/properties/Person.cs#14)]

Bu teknik, otomatik olarak uygulanan özellik üzerinde destek alanına eklediğiniz herhangi bir öznitelik için çalışır.

### <a name="implementing-inotifypropertychanged"></a>INotifyPropertyChanged uygulanması

Bir özellik erişimcisine kod yazmanız gereken son senaryo, veri bağlama istemcilerine bir değerin değiştiğini bildirmek için kullanılan <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi desteklemektir. Bir özelliğin değeri değiştiğinde, nesne <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged?displayProperty=nameWithType> değişikliği göstermek için olayı yükseltir. Veri bağlama kitaplıkları, sırayla, bu değişikliği temel alan görüntü öğelerini günceller. Aşağıdaki kod, bu kişi `INotifyPropertyChanged` sınıfının `FirstName` özelliği için nasıl uygulayacağınızı gösterir.

[!code-csharp[invalidating the cache correctly](../../samples/snippets/csharp/properties/Person.cs#15)]

İşleç `?.` *null koşullu işleci*denir. Operatörün sağ tarafını değerlendirmeden önce null başvurusu kontrol eder. Sonuç olarak, `PropertyChanged` olaya abone yoksa, olayı yükseltmek için kod yürütülmüyor. Bu durumda `NullReferenceException` bu çek olmadan bir atmak olacaktır. Daha fazla bilgi [`events`](events-overview.md)için bkz. Bu örnek, özellik `nameof` adı simgesinden metin gösterimine dönüştürmek için yeni işleci de kullanır.
Kullanma `nameof` özelliğinin adını yanlış yazdığınız hataları azaltabilir.

Yine, uygulama, <xref:System.ComponentModel.INotifyPropertyChanged> ihtiyacınız olan senaryoları desteklemek için erişime girenlere kod yazabileceğiniz bir örnektir.

## <a name="summing-up"></a>Özetleme

Özellikler, bir sınıf veya nesnedeki akıllı alanların biçimidir. Nesnenin dışından, nesnedeki alanlar gibi görünürler. Ancak, özellikler C# işlevselliğinin tam paleti kullanılarak uygulanabilir.
Doğrulama, farklı erişilebilirlik, tembel değerlendirme veya senaryolarınızın gereksinim duyduğu gereksinimleri sağlayabilirsiniz.
