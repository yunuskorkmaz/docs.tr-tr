---
title: Nesne odaklı programlama (C#)
description: C#; soyutlama, kapsülleme, devralma ve çok biçimlilik dahil olmak üzere nesne odaklı programlama için tam destek sağlar.
ms.date: 05/13/2020
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: 0c5495aefad73a2916ad6e2bd2bf3701d0868f24
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302821"
---
# <a name="object-oriented-programming-c"></a>Nesne odaklı programlama (C#)

C#; soyutlama, kapsülleme, devralma ve çok biçimlilik dahil olmak üzere nesne odaklı programlama için tam destek sağlar.

- *Soyutlama* , tür tüketicilerden gereksiz ayrıntıların gizlenmesi anlamına gelir.
- *Kapsülleme* , ilişkili özellikler, Yöntemler ve diğer üyelerin bir grubunun tek bir birim veya nesne olarak kabul edildiği anlamına gelir.
- *Devralma* , mevcut bir sınıfı temel alan yeni sınıflar oluşturma özelliğini açıklar.
- Çok *biçimlilik* , her bir sınıf farklı yollarla aynı özellikleri veya yöntemleri uyguladığından bile, birbirinin yerine kullanılabilecek birden fazla sınıfa sahip olabileceği anlamına gelir.

## <a name="classes-and-objects"></a>Sınıflar ve nesneler

Terimleri, sırasıyla nesnelerin *türünü* ve sınıfların *örneklerini* betimleyen *sınıf* ve *nesne* . Bu nedenle, bir nesne oluşturma konusuna *örnek*oluşturma denir. Şema benzerleme vurguladı kullanarak bir sınıf şeması bir şema, bir nesne ise bu şema tarafından oluşturulan bir derleme.

Bir sınıf tanımlamak için:

```csharp
class SampleClass
{
}
```

C# Ayrıca, devralma veya çok biçimlilik için desteğe ihtiyacınız olmadığında yararlı olan *yapılar* olarak adlandırılan türler de sağlar. Daha fazla bilgi için bkz. [sınıf ve yapı arasında seçim yapma](../../../standard/design-guidelines/choosing-between-class-and-struct.md).

Bir yapı tanımlamak için:

```csharp
struct SampleStruct
{
}
```

Daha fazla bilgi için [sınıf](../../language-reference/keywords/class.md) ve [Yapı](../../language-reference/builtin-types/struct.md) anahtar kelimeleri makalesine bakın.

### <a name="class-members"></a>Sınıf üyeleri

Her sınıf, sınıf verilerini tanımlayan özellikleri, sınıf davranışını tanımlayan yöntemleri ve farklı sınıflar ve nesneler arasında iletişim sağlayan olayları içeren farklı *sınıf üyelerine* sahip olabilir.

#### <a name="properties-and-fields"></a>Özellikler ve alanlar

Alanlar ve özellikler bir nesnenin içerdiği bilgileri temsil eder. Alanlar, uygun erişim değiştiricilerine bağlı olarak doğrudan okunabildikleri veya ayarlanabileceğinden değişkenlere benzer.

Sınıfın örnekleri içinden erişilebilen bir alan tanımlamak için:

```csharp
public class SampleClass
{
    string sampleField;
}
```

Özellikler `get` ve `set` erişimcileri, değerlerin nasıl ayarlandığı veya döndürüldüğü üzerinde daha fazla denetim sağlar.

C#, özellik değerini depolamak için özel bir alan oluşturmanıza ya da bu alanı arka planda otomatik olarak oluşturan otomatik uygulanan özellikleri ve özellik yordamları için temel mantığı kullanmayı sağlar.

Otomatik uygulanan bir özellik tanımlamak için:

```csharp
class SampleClass
{
    public int SampleProperty { get; set; }
}
```

Özellik değerini okumak ve yazmak için bazı ek işlemler gerçekleştirmeniz gerekiyorsa, özellik değerini depolamak için bir alan tanımlayın ve bunu depolamak ve almak için temel mantığı sağlayın:

```csharp
class SampleClass
{
    private int _sample;
    public int Sample
    {
        // Return the value stored in a field.
        get => _sample;
        // Store the value in the field.
        set =>  _sample = value;
    }
}
```

Çoğu özelliğin, özellik değerini ayarlamak ve almak için yöntemleri ya da yordamları vardır. Ancak, bunları değiştirilmesini veya okumayı kısıtlamak için salt okunurdur veya salt yazılır özellikler oluşturabilirsiniz. C# ' de, `get` veya `set` özellik yöntemini atlayabilirsiniz. Ancak otomatik uygulanan özellikler salt yazılır olamaz. Salt okuma otomatik uygulanmış özellikler, kapsayan sınıfın oluşturucuları içinde ayarlanabilir.

Daha fazla bilgi için bkz.

- [Al](../../language-reference/keywords/get.md)
- [kurmak](../../language-reference/keywords/set.md)

#### <a name="methods"></a>Yöntemler

Bir *Yöntem* , bir nesnenin gerçekleştirebileceği bir eylemdir.

Bir sınıfın yöntemini tanımlamak için:

```csharp
class SampleClass
{
    public int SampleMethod(string sampleParam)
    {
        // Insert code here
    }
}
```

Bir sınıf, parametrelerin veya parametre türlerinin sayısında farklı olan aynı yöntemin çeşitli uygulamalarına veya *aşırı*yüküne sahip olabilir.

Bir yöntemi aşırı yüklemek için:

```csharp
public int SampleMethod(string sampleParam) { }
public int SampleMethod(int sampleParam) { }
```

Çoğu durumda, bir sınıf tanımı içinde bir yöntemi bildirirsiniz. Ancak C#, sınıfın gerçek tanımının dışında mevcut bir sınıfa Yöntemler eklemenize olanak tanıyan *genişletme yöntemlerini* de destekler.

Daha fazla bilgi için bkz.

- [Yöntemler](../classes-and-structs/methods.md)
- [Uzantı Metotları](../classes-and-structs/extension-methods.md)

#### <a name="constructors"></a>Oluşturucular

Oluşturucular, belirli bir türden bir nesne oluşturulduğunda otomatik olarak yürütülen sınıf yöntemleridir. Oluşturucular genellikle yeni nesnenin veri üyelerini başlatır. Bir Oluşturucu, bir sınıf oluşturulduğunda yalnızca bir kez çalıştırılabilir. Ayrıca, kurucudaki kod her zaman bir sınıftaki diğer koddan önce çalışır. Ancak, başka bir yöntemle aynı şekilde birden çok Oluşturucu aşırı yüklemesi oluşturabilirsiniz.

Bir sınıf için bir Oluşturucu tanımlamak için:

```csharp
public class SampleClass
{
    public SampleClass()
    {
        // Add code here
    }
}
```

Daha fazla bilgi için bkz. [oluşturucular](../classes-and-structs/constructors.md).

#### <a name="finalizers"></a>Sonlandırıcılar

Sonlandırıcı, sınıf örneklerinin çıkarılması için kullanılır. .NET sürümünde çöp toplayıcı, uygulamanızdaki yönetilen nesneler için bellek ayırmayı ve serbest bırakma işlemini otomatik olarak yönetir. Ancak, uygulamanızın oluşturduğu yönetilmeyen kaynakları temizlemek için sonlandırıcılardan yine de ihtiyacınız olabilir. Bir sınıf için yalnızca bir Sonlandırıcı olabilir.

.NET 'teki sonlandırıcılar ve çöp toplama hakkında daha fazla bilgi için bkz. [çöp toplama](../../../standard/garbage-collection/index.md).

#### <a name="events"></a>Olaylar

Olaylar, bir sınıf ya da nesnenin, ilgi çekici bir şeyler gerçekleştiğinde diğer sınıflara veya nesnelere bildirilmesini sağlar. Olayı gönderen (veya Başlatan) sınıf *Yayımcı* olarak adlandırılır ve olayı alan (veya işleyen) sınıflar *aboneler*olarak adlandırılır. Olaylar, nasıl oluşturulur ve işlenir hakkında daha fazla bilgi için bkz. [Olaylar](../../../standard/events/index.md).

- Bir sınıfında bir olay bildirmek için [Event](../../language-reference/keywords/event.md) anahtar sözcüğünü kullanın.
- Bir olayı yükseltmek için olay temsilcisini çağırın.
- Bir olaya abone olmak için `+=` işlecini kullanın; bir olayın aboneliğini kaldırmak için `-=` işlecini kullanın.

#### <a name="nested-classes"></a>İç içe geçmiş sınıflar

Başka bir sınıf içinde tanımlı bir sınıf *iç içe*çağırılır. Varsayılan olarak, iç içe yerleştirilmiş sınıf özeldir.

```csharp
class Container
{
    class Nested
    {
        // Add code here.
    }
}
```

İç içe yerleştirilmiş sınıfın bir örneğini oluşturmak için, container sınıfının adını ve ardından nokta ve ardından iç içe geçmiş sınıfın adını kullanın:

```csharp
Container.Nested nestedInstance = new Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a>Erişim değiştiricileri ve erişim düzeyleri

Tüm sınıflar ve sınıf üyeleri, *erişim değiştiricilerini*kullanarak diğer sınıflara hangi erişim düzeyini sundukları belirler.

Aşağıdaki erişim değiştiriciler kullanılabilir:

| C# değiştiricisi | Tanım |
|--|--|
| [genel](../../language-reference/keywords/public.md) | Türe veya üyeye aynı derlemedeki veya buna başvuran başka bir derlemede bir veya daha fazla kod tarafından erişilebilir. |
| [özelleştirme](../../language-reference/keywords/private.md) | Türe veya üyeye yalnızca aynı sınıftaki kodla erişilebilir. |
| [protected](../../language-reference/keywords/protected.md) | Türe veya üyeye yalnızca aynı sınıftaki veya türetilmiş bir sınıftaki kodla erişilebilir. |
| [internal](../../language-reference/keywords/internal.md) | Türe veya üyeye aynı derlemedeki kod tarafından erişilebilir, ancak başka bir derlemeden erişilebilir. |
| [protected internal](../../language-reference/keywords/protected-internal.md) | Türe veya üyeye aynı derlemedeki herhangi bir kod ya da başka bir derlemedeki türetilmiş bir sınıf tarafından erişilebilir. |
| [private protected](../../language-reference/keywords/private-protected.md) | Türe veya üyeye aynı sınıftaki veya temel sınıf derlemesi içindeki türetilmiş bir sınıftaki kodla erişilebilir. |

Daha fazla bilgi için bkz. [erişim değiştiricileri](../classes-and-structs/access-modifiers.md).

### <a name="instantiating-classes"></a>Sınıfları örnekleme

Bir nesne oluşturmak için bir sınıf örneği oluşturmanız veya bir sınıf örneği oluşturmanız gerekir.

```csharp
SampleClass sampleObject = new SampleClass();
```

Bir sınıfı örnekledikten sonra, örneğin özelliklerine ve alanlarına değerler atayabilir ve sınıf yöntemlerini çağırabilirsiniz.

```csharp
// Set a property value.
sampleObject.sampleProperty = "Sample String";
// Call a method.
sampleObject.SampleMethod();
```

Sınıf örnek oluşturma işlemi sırasında özelliklere değer atamak için, nesne başlatıcıları kullanın:

```csharp
// Set a property value.
var sampleObject = new SampleClass
{
    FirstProperty = "A",
    SecondProperty = "B"
};
```

Daha fazla bilgi için bkz.

- [New Işleci](../../language-reference/operators/new-operator.md)
- [Nesne ve Koleksiyon Başlatıcıları](../classes-and-structs/object-and-collection-initializers.md)

### <a name="static-classes-and-members"></a>Statik sınıflar ve Üyeler

Sınıfının statik üyesi, bir sınıfın tüm örnekleri tarafından paylaşılan bir özellik, yordam veya alandır.

Statik üye tanımlamak için:

```csharp
static class SampleClass
{
    public static string SampleString = "Sample String";
}
```

Statik üyeye erişmek için, sınıfın adını bu sınıfın bir nesnesi oluşturmadan kullanın:

```csharp
Console.WriteLine(SampleClass.SampleString);
```

C# içindeki statik sınıflar yalnızca statik üyelere sahiptir ve örneklenemez. Statik Üyeler ayrıca statik olmayan özelliklere, alanlara veya yöntemlere erişemez

Daha fazla bilgi için bkz: [static](../../language-reference/keywords/static.md).

### <a name="anonymous-types"></a>Anonim türler

Anonim türler, veri türü için bir sınıf tanımı yazmadan nesneler oluşturmanızı sağlar. Bunun yerine, derleyici sizin için bir sınıf oluşturur. Sınıfın kullanılabilir adı yok ve nesneyi bildirirken belirttiğiniz özellikleri içerir.

Anonim türün bir örneğini oluşturmak için:

```csharp
// sampleObject is an instance of a simple anonymous type.
var sampleObject = new
{
    FirstProperty = "A",
    SecondProperty = "B"
};
```

Daha fazla bilgi için bkz: [anonim türler](../classes-and-structs/anonymous-types.md).

## <a name="inheritance"></a>Devralma

Devralma, başka bir sınıfta tanımlanan davranışı yeniden kullanan, genişleten ve değiştiren yeni bir sınıf oluşturmanıza olanak sağlar. Üyeleri devralınmış olan sınıfa *temel sınıf*denir ve bu üyeleri devralan sınıfa *türetilmiş sınıf*denir. Ancak, C# ' deki tüm sınıflar dolaylı olarak <xref:System.Object> .NET sınıf hiyerarşisini destekleyen sınıftan devralınır ve tüm sınıflara alt düzey hizmetler sağlar.

> [!NOTE]
> C# birden fazla devralmayı desteklemez. Diğer bir deyişle, türetilmiş bir sınıf için yalnızca bir temel sınıf belirtebilirsiniz.

Temel sınıftan devralması için:

```csharp
class DerivedClass:BaseClass { }
```

Varsayılan olarak, tüm sınıflar devralınabilir. Ancak, bir sınıfın temel sınıf olarak kullanılması gerekip gerekmediğini belirtebilir veya yalnızca temel sınıf olarak kullanılabilecek bir sınıf oluşturmanız gerekir.

Bir sınıfın temel sınıf olarak kullanılamayacağını belirtmek için:

```csharp
public sealed class A { }
```

Bir sınıfın yalnızca temel sınıf olarak kullanılabileceğini ve örneklenemez olduğunu belirtmek için:

```csharp
public abstract class B { }
```

Daha fazla bilgi için bkz.

- [sealed](../../language-reference/keywords/sealed.md)
- [Soyut](../../language-reference/keywords/abstract.md)

### <a name="overriding-members"></a>Üyeleri geçersiz kılma

Varsayılan olarak, türetilmiş bir sınıf kendi temel sınıfından tüm üyeleri devralır. Devralınan üyenin davranışını değiştirmek istiyorsanız, onu geçersiz kılmanız gerekir. Diğer bir deyişle, türetilmiş sınıfta yöntemin, özelliğin veya olayın yeni bir uygulamasını tanımlayabilirsiniz.

Özelliklerin ve yöntemlerin nasıl geçersiz kılınabileceğini denetlemek için aşağıdaki değiştiriciler kullanılır:

| C# değiştiricisi | Tanım |
|--|--|
| [sanal](../../language-reference/keywords/virtual.md) | Bir sınıf üyesinin türetilmiş bir sınıfta geçersiz kılınmasına izin verir. |
| [override](../../language-reference/keywords/override.md) | Temel sınıfta tanımlanan bir sanal (geçersiz kılınabilir) üyeyi geçersiz kılar. |
| [Soyut](../../language-reference/keywords/abstract.md) | Türetilmiş sınıfta bir sınıf üyesinin geçersiz kılınmasını gerektirir. |
| [new Değiştiricisi](../../language-reference/keywords/new-modifier.md) | Temel sınıftan devralınan bir üyeyi gizler |

## <a name="interfaces"></a>Arabirimler

Sınıflar gibi arabirimler, özellikler, Yöntemler ve olaylar kümesi tanımlar. Ancak sınıfların aksine arabirimler uygulama sağlamaz. Sınıflar tarafından uygulanır ve sınıflardan ayrı varlıklar olarak tanımlanır. Arabirim, bir arabirimi uygulayan bir sınıfın, bu arabirimin her yönünü tam olarak tanımlandığı gibi uygulaması gerektiğini belirten bir sözleşmeyi temsil eder.

Bir arabirim tanımlamak için:

```csharp
interface ISampleInterface
{
    void DoSomething();
}
```

Bir sınıfa bir arabirim uygulamak için:

```csharp
class SampleClass : ISampleInterface
{
    void ISampleInterface.DoSomething()
    {
        // Method implementation.
    }
}
```

Daha fazla bilgi için [arabirim](../../language-reference/keywords/interface.md) anahtar sözcüğünün [arabirimler](../interfaces/index.md) ve dil başvurusu makalesindeki Programlama Kılavuzu makalesine bakın.

## <a name="generics"></a>Genel Türler

.NET 'teki sınıflar, yapılar, arabirimler ve Yöntemler, depolayabilecekleri veya kullanabileceği nesne türlerini tanımlayan *tür parametreleri* içerebilir. En yaygın genel türler örneği, bir koleksiyonda depolanacak nesne türlerini belirtebileceğiniz bir koleksiyondur.

Genel bir sınıf tanımlamak için:

```csharp
public class SampleGeneric<T>
{
    public T Field;
}
```

Genel sınıfın bir örneğini oluşturmak için:

```csharp
var sampleObject = new SampleGeneric<string>();
sampleObject.Field = "Sample string";
```

Daha fazla bilgi için bkz.

- [.NET içindeki Genel Türler](../../../standard/generics/index.md)
- [Genel türler-C# Programlama Kılavuzu](../generics/index.md)

## <a name="delegates"></a>Temsilciler

*Temsilci* , yöntem imzasını tanımlayan bir türdür ve uyumlu imzaya sahip herhangi bir yönteme başvuru sağlayabilir. Yöntemi temsilci aracılığıyla çağırabilir (veya çağırabilirsiniz). Temsilciler, yöntemleri bağımsız değişkenler olarak diğer yöntemlere geçirmek için kullanılır.

> [!NOTE]
> Olay işleyicileri, temsilciler aracılığıyla çağrılan yöntemlerden başka bir şey değildir. Olay İşlemede temsilciler kullanma hakkında daha fazla bilgi için bkz. [Olaylar](../../../standard/events/index.md).

Bir temsilci oluşturmak için:

```csharp
public delegate void SampleDelegate(string str);
```

Temsilci tarafından belirtilen imzayla eşleşen bir yönteme başvuru oluşturmak için:

```csharp
class SampleClass
{
    // Method that matches the SampleDelegate signature.
    public static void SampleMethod(string message)
    {
        // Add code here.
    }

    // Method that instantiates the delegate.
    void SampleDelegate()
    {
        SampleDelegate sd = sampleMethod;
        sd("Sample string");
    }
}
```

Daha fazla bilgi için [temsilci](../../language-reference/builtin-types/reference-types.md) anahtar kelimesiyle ilgili [Temsilciler](../delegates/index.md) ve dil başvurusu makalesindeki Programlama Kılavuzu makalesine bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
