---
title: Özellikler
description: Bilgi C# hakkında değerleri, geç değerlendirme doğrulama için özellikler, Özellikler hesaplanır ve özelliği bildirimleri değiştirildi.
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 04/03/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 6950d25a-bba1-4744-b7c7-a3cc90438c55
ms.openlocfilehash: 2a25919048f94211b1696ac8c8471a14ce6e15c5
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2018
---
# <a name="properties"></a>Özellikler

C# birinci sınıf kullanıcılarının özelliklerdir. Dil kendi tasarım hedefi doğru şekilde ifade kod yazmaya geliştiricilerinin sözdizimi tanımlar.

Bunlar erişildiğinde özellikleri alanlar gibi davranır.
Ancak, alanları, bir özellik erişilen veya atandığında, yürütülen deyimleri tanımlayan erişimciler ile özellikleri uygulanır.

## <a name="property-syntax"></a>Özellik sözdizimi

Özellikleri için sözdizimi, alanlar için doğal bir uzantıdır. Bir alan bir depolama konumu tanımlar:

```csharp
public class Person
{
    public string FirstName;
    // remaining implementation removed from listing
}
```

Bildirimler için bir özellik tanımını içeren bir `get` ve `set` alır ve bu özelliğin değeri atayan erişimcisi:

```csharp
public class Person
{
    public string FirstName { get; set; }

    // remaining implementation removed from listing
}
```

Yukarıda gösterilen sözdizimi *otomatik özelliği* sözdizimi. Derleyici özelliği yedekler alanı için depolama konumu oluşturur. Derleyici de gövdesini uygulayan `get` ve `set` erişimciler.

Bazı durumlarda, bir özellik türü için varsayılan farklı bir değere başlatmak için gerekir.  C#, sonra kapanış ayracı özelliği için bir değer ayarlanarak sağlar. İlk değeri tercih edebilirsiniz `FirstName` boş dize özelliğini yerine `null`. Aşağıda gösterildiği gibi belirtmeniz gerekir:

```csharp
public class Person
{
    public string FirstName { get; set; } = string.Empty;

    // remaining implementation removed from listing
}
```

Bu konunun ilerleyen bölümlerinde anlatıldığı gibi bu salt okunur özellikler için kullanışlıdır.

Aşağıda gösterildiği gibi depolama kendiniz de tanımlayabilirsiniz:

```csharp
public class Person
{
    public string FirstName
    {
        get { return firstName; }
        set { firstName = value; }
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

Bir özellik uygulama tek bir ifade olduğunda kullanabileceğiniz *ifade bodied üyeleri* alıcı veya ayarlayıcı için:

```csharp
public class Person
{
    public string FirstName
    {
        get => firstName;
        set => firstName = value;
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

Bu Basitleştirilmiş söz dizimi, bu konuda boyunca uygunsa kullanılır.

Yukarıda gösterilen özellik tanımı bir okuma-yazma özelliğidir. Anahtar sözcüğü fark `value` set erişimcisi içinde. `set` Erişimcisine sahip her zaman adlı tek bir parametre `value`. `get` Erişimci özelliği türüne dönüştürülebilir olan bir değer döndürmesi gerekir (`string` Bu örnekte).
 
Sözdizimi temelleri olmasıdır. Farklı tasarım deyimleri çeşitli destek pek çok farklı Çeşitleme vardır. Şimdi bu keşfedin ve her sözdizimi seçenekleri öğrenin.

## <a name="scenarios"></a>Senaryolar

Yukarıdaki örneklerde gösterilen özellik tanımı, basit bir durumda birini: hiçbir doğrulama okuma-yazma özelliğiyle. Kod yazarak istediğiniz `get` ve `set` erişimciler, birçok farklı senaryolar oluşturabilirsiniz.

### <a name="validation"></a>Doğrulama

Kod yazabilirsiniz `set` erişimci özelliği tarafından temsil edilen değerler her zaman geçerli olduğundan emin olun. Örneğin, bir kural için varsayalım `Person` sınıftır adı boş veya boşluk olamaz. Aşağıdaki gibi yazarsınız:

```csharp
public class Person
{
    public string FirstName
    {
        get => firstName;
        set
        {
            if (string.IsNullOrWhiteSpace(value))
                throw new ArgumentException("First name must not be blank");
            firstName = value;
        }
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

Yukarıdaki örnek adı boş veya boşluk olmamalıdır kural zorlar. Bir geliştirici yazıyorsa

```csharp
hero.FirstName = "";
```

Bu atama oluşturur bir `ArgumentException`. Dönüş türü void özellik bir set erişimcisine sahip olması gerektiğinden, bir özel durum atma tarafından set erişimcisine hataları rapor.

Bu, doğrulama basit bir durumdur. Bu aynı sözdizimini senaryonuzda gereken herhangi bir şeye genişletebilirsiniz. Farklı özellikler arasındaki ilişkileri denetleyin veya karşı dış koşulları doğrulayın. Geçerli bir C# ifadelerinin içinde bir özellik erişimcisini geçerli değil.

### <a name="read-only"></a>Salt okunur

Bu noktaya kadar açtığınız tüm özellik tanımları ortak erişimciler ile okuma/yazma özelliklerdir. Bu özellikler için geçerli tek erişilebilirlik değil.
Salt okunur özellikler oluşturun veya farklı erişilebilirlik kümesine verin ve erişimciler alın. Varsayın, `Person` sınıfı, değerinin değiştirilmesi yalnızca etkinleştirmelisiniz `FirstName` o sınıfın diğer yöntemlerle özelliğinden. Set erişimcisine sunabilir `private` yerine erişilebilirlik `public`:

```csharp
public class Person
{
    public string FirstName { get; private set; }

    // remaining implementation removed from listing
}
```

Şimdi, `FirstName` özelliği herhangi bir kodda erişilebilir, ancak diğer koddan yalnızca atanabilir `Person` sınıfı.

Herhangi bir kısıtlayıcı erişim değiştiricisi ya da kümesi ekleyin veya erişimciler alın. Tek tek erişimcisine yerleştirin herhangi bir erişim değiştiricisi özellik tanımı üzerinde erişim değiştiricisi daha kısıtlı olması gerekir. Yukarıdaki yasal olduğundan `FirstName` özelliği `public`, ancak set erişimcisine `private`. Değil bildirebilirsiniz bir `private` özelliği ile bir `public` erişimcisi. Özellik bildirimleri de bildirilebilir `protected`, `internal`, `protected internal`, `private protected` ve hatta `private`.   

Daha kısıtlayıcı değiştiricisi yerleştirmek için uygundur `get` erişimcisi. Örneğin, olabilir bir `public` özelliği, ancak kısıtlamak `get` erişimcisi için `private`. Bu senaryo, uygulamada nadiren yapılır.

Böylece bir oluşturucu veya özellik başlatıcı yalnızca ayarlanabilir bir özellik değişiklikler de kısıtlayabilirsiniz. Değiştirebileceğiniz `Person` bunu aşağıdaki gibi sınıfı:

```csharp
public class Person
{
    public Person(string firstName)
    {
        this.FirstName = firstName;
    }

    public string FirstName { get; }

    // remaining implementation removed from listing
}
```

Bu özellik salt okunur özellikler olarak sunulan koleksiyonları başlatmak için en yaygın olarak kullanılır:

```csharp
public class Measurements
{
    public ICollection<DataPoint> points { get; } = new List<DataPoint>();
}
```

### <a name="computed-properties"></a>Hesaplanan özellikleri

Bir özelliği yalnızca bir üye alanın değerini döndürmek gerekmez. Hesaplanan değeri döndüren özellikleri oluşturabilirsiniz. Şimdi genişletin `Person` nesne adları ve soyadları birleştirerek hesaplanan tam adını döndürmek için:

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    public string FullName { get { return $"{FirstName} {LastName}"; } }
}
```

Kullandığı Yukarıdaki örnek [dize ilişkilendirme](../csharp/language-reference/tokens/interpolated.md) biçimlendirilmiş dize tam adı oluşturmak için özellik.

De kullanabilirsiniz *ifade bodied üyeleri*, hesaplanan oluşturmak için daha kısa bir yol sağlayan `FullName` özelliği:

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    public string FullName =>  $"{FirstName} {LastName}";
}
```
 
*İfade bodied üyeleri* kullanmak *lambda ifadesi* tek bir ifade içeren bir yöntemi tanımlamak için sözdizimi. Burada, bu ifade kişi nesnesi tam adını döndürür.

### <a name="lazy-evaluated-properties"></a>Yavaş değerlendirilen Özellikler

Hesaplanan bir özellik kavramı depolama ile karıştırmak ve oluşturma bir *yavaş hesaplanan özelliği*.  Örneğin, güncelleştirebilir `FullName` özelliği böylece biçimlendirme dizesi yalnızca erişilen ilk kez oluştu:

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    private string fullName;
    public string FullName
    {
        get
        {
            if (fullName == null)
                fullName = $"{FirstName} {LastName}";
            return fullName;
        }
    }
}
```

Yukarıdaki kod, ancak bir hata içeriyor. Kod ya da değeri güncelleştirmeleri olursa `FirstName` veya `LastName` özelliği, daha önce değerlendirilen `fullName` alanı geçersiz. Güncelleştirmek gereken `set` erişimci `FirstName` ve `LastName` özelliği böylece `fullName` alan yeniden hesaplanır:

```csharp
public class Person
{
    private string firstName;
    public string FirstName
    {
        get => firstName;
        set
        {
            firstName = value;
            fullName = null;
        }
    }

    private string lastName;
    public string LastName
    {
        get => lastName;
        set
        {
            lastName = value;
            fullName = null;
        }
    }

    private string fullName;
    public string FullName
    {
        get
        {
            if (fullName == null)
                fullName = $"{FirstName} {LastName}";
            return fullName;
        }
    }
}
```

Bu son sürümü değerlendirir `FullName` yalnızca gerekli olduğunda özelliği.
Önceden hesaplanmış sürümü geçerli ise kullanılır. Başka bir durum değişikliği önceden hesaplanmış sürümü geçersiz kılar, hesaplanır. Bu sınıf kullanan geliştiriciler uygulama ayrıntılarını bilmeniz gerek yoktur. İç değişikliklerin hiçbiri kişi nesnesinin kullanımını etkiler. Veri üyeleri bir nesnenin kullanıma sunmak için özelliklerini kullanarak anahtar nedenini olmasıdır.
 
### <a name="inotifypropertychanged"></a>INotifyPropertyChanged

Bir özellik erişimcisini kod yazmanız gereken son bir senaryo desteklemektir `INotifyPropertyChanged` bir değer değiştikten veri bağlama istemcilerine bildirmek için kullanılan arabirim. Bir özellik değeri değiştiğinde, nesneyi başlatır `PropertyChanged` değişikliği göstermek için olay. Veri kitaplıkları, bağlama sırayla, bu değişiklik temel görüntü öğeleri güncelleştirin. Aşağıdaki kod, nasıl uygulayacağınıza gösterir `INotifyPropertyChanged` için `FirstName` bu kişinin sınıfının özelliği.

```csharp
public class Person : INotifyPropertyChanged
{
    public string FirstName
    {
        get => firstName;
        set
        {
            if (string.IsNullOrWhiteSpace(value))
                throw new ArgumentException("First name must not be blank");
            if (value != firstName)
            {
                PropertyChanged?.Invoke(this, 
                    new PropertyChangedEventArgs(nameof(FirstName)));
            }
            firstName = value;
        }
    }
    private string firstName;

    public event PropertyChangedEventHandler PropertyChanged;
    // remaining implementation removed from listing
}
```

`?.` İşleci çağrılır *null koşullu işleç*. Bir null başvuru için işlecinin sağ tarafında değerlendirmeden önce denetler. Hiçbir abonelere varsa olan sonuç `PropertyChanged` değil olay, olayı için kodu yürütün. Throw bir `NullReferenceException` bu durumda bu olmadan denetleyin. Sayfasına bakın [ `events` ](delegates-events.md) daha fazla ayrıntı için. Bu örnek ayrıca yeni `nameof` kendi metin gösterimi olan özellik adı simgesini dönüştürmek için işleci.
Kullanarak `nameof` Burada, yanlış yazmış özelliğinin adı hataları azaltabilir.

Yeniden, bu nerede gereksinim duyduğunuz senaryoları desteklemek için erişimcileri kod yazabilirsiniz servis talebi örneğidir.

## <a name="summing-up"></a>Özetle

Özellikler, bir sınıf veya nesne akıllı alanları biçimidir. Gelen dışında nesne, nesne alanları gibi görünürler. Ancak, özellikler, C# işlevlerin tam paleti kullanarak uygulanabilir.
Doğrulama, farklı erişilebilirlik, geç değerlendirme veya senaryolarınızı gereken herhangi bir gereksinimi sağlayabilir.
