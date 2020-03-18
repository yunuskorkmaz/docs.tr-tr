---
title: Nesne Yönelimli Programlama (C#)
ms.date: 02/08/2020
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: 01d6f55bf0752f902f351675c4596abbb8ac85c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77627896"
---
# <a name="object-oriented-programming-c"></a>Nesne Yönelimli programlama (C#)

C#, kapsülleme, kalıtım ve çok biçimlilik gibi nesne yönelimli programlama için tam destek sağlar.

- *Kapsülleme,* ilgili özellikler, yöntemler ve diğer üyelerden oluşan bir grubun tek bir birim veya nesne olarak kabul edilsi anlamına gelir.
- *Devralma,* varolan bir sınıfa dayalı yeni sınıflar oluşturma yeteneğini açıklar.
- *Çok biçimlilik,* her sınıf aynı özellikleri veya yöntemleri farklı şekillerde uygulasa bile, birbirinin yerine kullanılabilecek birden çok sınıfa sahip olabileceğiniz anlamına gelir.

## <a name="classes-and-objects"></a>Sınıflar ve nesneler

Terim *sınıf* ve *nesne,* sırasıyla nesnelerin *türünü* ve sınıf *örneklerini* açıklar. Yani, bir nesne oluşturma eylemine *anlık hareket*denir. Plan benzetmesini kullanarak, sınıf bir plandır ve bir nesne de bu plandan yapılmış bir binadır.

Bir sınıfı tanımlamak için:

```csharp
class SampleClass
{
}
```

C# ayrıca kalıtım veya çok biçimlilik için desteğe ihtiyacınız olmadığında yararlı olan *yapılar* olarak adlandırılan türleri de sağlar.

Bir yapıtanımlamak için:

```csharp
struct SampleStruct
{
}
```

Daha fazla bilgi için [sınıf](../../language-reference/keywords/class.md) ve [yapı](../../language-reference/builtin-types/struct.md) anahtar kelimeleri hakkındaki makalelere bakın.

### <a name="class-members"></a>Sınıf üyeleri

Her *sınıfın,* sınıf verilerini açıklayan özellikleri, sınıf davranışını tanımlayan yöntemleri ve farklı sınıflar ve nesneler arasında iletişim sağlayan olayları içeren farklı sınıf üyeleri olabilir.

#### <a name="properties-and-fields"></a>Özellikler ve alanlar

Alanlar ve özellikler, nesnenin içerdiği bilgileri temsil ediyor. Alanlar, uygulanabilir erişim değiştiricilere tabi olarak doğrudan okunabildikleri veya ayarlanabildikleri için değişkenler gibidir.

Sınıfın örnekleri içinden erişilebilen bir alanı tanımlamak için:

```csharp
public class SampleClass
{
    string sampleField;
}
```

Özelliklerin `get` `set` ve erişime sahip olan ve değerlerin nasıl ayarlandığı veya döndürüldek hakkında daha fazla denetim sağlayan.

C# özellik değerini depolamak için özel bir alan oluşturmanıza veya bu alanı otomatik olarak arka planda oluşturan otomatik olarak uygulanan özellikleri kullanmanıza ve özellik yordamları için temel mantığı sağlamanıza olanak tanır.

Otomatik olarak uygulanan bir özelliği tanımlamak için:

```csharp
class SampleClass
{
    public int SampleProperty { get; set; }
}
```

Özellik değerini okumak ve yazmak için bazı ek işlemler gerçekleştirmeniz gerekiyorsa, özellik değerini depolamak için bir alan tanımlayın ve depolamak ve almak için temel mantığı sağlayın:

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

Çoğu özelliğin hem ayarlayıp hem de özellik değerini almak için yöntemleri veya yordamları vardır. Ancak, değiştirilmelerini veya okunmasını kısıtlamak için salt okunur veya yalnızca yazma özellikleri oluşturabilirsiniz. C#'da, özelliği veya `get` `set` özelliği yöntemini atlayabilirsiniz. Ancak, otomatik olarak uygulanan özellikler yalnızca yazılamaz. Yalnızca okunan otomatik uygulanan özellikler, içeren sınıfın oluşturucularında ayarlanabilir.

Daha fazla bilgi için bkz.

- [get](../../language-reference/keywords/get.md)

- [Ayarlamak](../../language-reference/keywords/set.md)

#### <a name="methods"></a>Yöntemler

*Yöntem,* bir nesnenin gerçekleştirebileceği bir eylemdir.

Bir sınıfın yöntemini tanımlamak için:

```csharp
class SampleClass
{
    public int sampleMethod(string sampleParam)
    {
        // Insert code here
    }
}
```

Bir sınıfın, parametre veya parametre türlerinin sayısında farklılık gösteren aynı yöntemin birkaç uygulaması veya *aşırı yüklemesi*olabilir.

Bir yöntemi aşırı yüklemek için:

```csharp
public int sampleMethod(string sampleParam) {}
public int sampleMethod(int sampleParam) {}
```

Çoğu durumda bir sınıf tanımı içinde bir yöntem bildirirsiniz. Ancak C# ayrıca, sınıfın gerçek tanımı dışında varolan bir sınıfa yöntem eklemenize olanak tanıyan *uzantı yöntemlerini* de destekler.

Daha fazla bilgi için bkz.

- [Yöntemler](../classes-and-structs/methods.md)
- [Genişletme Yöntemleri](../classes-and-structs/extension-methods.md)

#### <a name="constructors"></a>Oluşturucular

Oluşturucular, belirli bir türdeki bir nesne oluşturulduğunda otomatik olarak yürütülen sınıf yöntemleridir. Oluşturucular genellikle yeni nesnenin veri üyelerini başlangıç olarak karşılarlar. Bir oluşturucu, bir sınıf oluşturulduğunda yalnızca bir kez çalıştırılabilir. Ayrıca, oluşturucudaki kod her zaman bir sınıftaki başka bir koddan önce çalışır. Ancak, birden çok oluşturucu başka bir yöntemle aynı şekilde aşırı yüklemeler oluşturabilirsiniz.

Bir sınıf için bir oluşturucu tanımlamak için:

```csharp
public class SampleClass
{
    public SampleClass()
    {
        // Add code here
    }
}
```

Daha fazla bilgi için [Constructors'a](../classes-and-structs/constructors.md)bakın.

#### <a name="finalizers"></a>Sonlandırıcılar

Sonlandırıcılar sınıfların örneklerini yok etmek için kullanılır. .NET Framework'de, çöp toplayıcı, uygulamanızdaki yönetilen nesneler için bellek tahsisini ve serbest bırakılmasını otomatik olarak yönetir. Ancak, uygulamanızın oluşturduğu yönetilmeyen kaynakları temizlemek için yine de sonlandırıcılara ihtiyacınız olabilir. Bir ders için sadece bir finalizatör olabilir.

.NET Framework'de sonlandırıcılar ve çöp toplama hakkında daha fazla bilgi için [Bkz.](../../../standard/garbage-collection/index.md)

#### <a name="events"></a>Olaylar

Olaylar, ilgi çekici bir şey oluştuğunda bir sınıfın veya nesnenin diğer sınıfları veya nesneleri bildirmesini sağlar. Olayı gönderen (veya yükselten) sınıfa *yayımcı,* olayı alan (veya işleyen) sınıflara *abone*denir. Olaylar hakkında daha fazla bilgi için, bunların nasıl yükseltildiği ve işlendiği [hakkında](../../../standard/events/index.md)bkz.

- Bir sınıfta olay bildirmek için [olay](../../language-reference/keywords/event.md) anahtar sözcük'ünden yararlanın.

- Bir olayı yükseltmek için olay temsilcisini çağırın.

- Bir etkinliğe abone olmak `+=` için operatörü kullanın; bir etkinlikten aboneliğinizi iptal `-=` etmek için işleci kullanın.

#### <a name="nested-classes"></a>İç içe sınıflar

Başka bir sınıf içinde tanımlanan bir sınıf *iç içe*denir. Varsayılan olarak, iç içe sınıf özeldir.

```csharp
class Container
{
    class Nested
    {
        // Add code here.
    }
}
```

İç içe sınıf bir örnek oluşturmak için, nokta ardından kapsayıcı sınıfın adını ve ardından iç içe sınıf adını kullanın:

```csharp
Container.Nested nestedInstance = new Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a>Değiştiricilere ve erişim düzeylerine erişin

Tüm sınıflar ve sınıf *üyeleri, erişim değiştiriciler*kullanarak diğer sınıflara hangi erişim düzeyini sağladıklarını belirtebilir.

Aşağıdaki erişim değiştiriciler kullanılabilir:

|C# Değiştirici|Tanım|
|------------------|----------------|
|[Kamu](../../language-reference/keywords/public.md)|Türe veya üyeye, aynı derlemedeki veya ona başvuran başka bir derlemedeki başka bir kod erişebilir.|
|[Özel](../../language-reference/keywords/private.md)|Türe veya üyeye yalnızca aynı sınıftaki kodla erişilebilir.|
|[protected](../../language-reference/keywords/protected.md)|Türe veya üyeye yalnızca aynı sınıftaveya türemiş bir sınıfta kodla erişilebilir.|
|[Iç](../../language-reference/keywords/internal.md)|Türe veya üyeye aynı derlemedeki herhangi bir kod erişebilir, ancak başka bir derlemeden erişilemez.|
|[protected internal](../../language-reference/keywords/protected-internal.md)|Türe veya üyeye aynı derlemedeki herhangi bir kod veya başka bir derlemedeki herhangi bir türemiş sınıf erişebilir.|
|[özel korumalı](../../language-reference/keywords/private-protected.md)|Türe veya üyeye aynı sınıftaki kodla veya taban sınıf derlemesi içinde türetilmiş bir sınıfta erişilebilir.|

Daha fazla bilgi için [Erişim Değiştiriciler'e](../classes-and-structs/access-modifiers.md)bakın.

### <a name="instantiating-classes"></a>Anında sınıflar

Bir nesne oluşturmak için, bir sınıfı anında oluşturmanız veya bir sınıf örneği oluşturmanız gerekir.

```csharp
SampleClass sampleObject = new SampleClass();
```

Bir sınıfı anında yaptıktan sonra, örnek özelliklerine ve alanlarına değerler atayabilir ve sınıf yöntemlerini çağırabilirsiniz.

```csharp
// Set a property value.
sampleObject.sampleProperty = "Sample String";
// Call a method.
sampleObject.sampleMethod();
```

Sınıf anlık işlem sırasında özelliklerine değer atamak için nesne baş harflerini kullanın:

```csharp
// Set a property value.
SampleClass sampleObject = new SampleClass
    { FirstProperty = "A", SecondProperty = "B" };
```

Daha fazla bilgi için bkz.

- [new İşleci](../../language-reference/operators/new-operator.md)
- [Nesne ve Koleksiyon Başlatıcıları](../classes-and-structs/object-and-collection-initializers.md)

### <a name="static-classes-and-members"></a>Statik Sınıflar ve Üyeler

Sınıfın statik bir üyesi, sınıfın tüm örnekleri tarafından paylaşılan bir özellik, yordam veya alandır.

Statik bir üye tanımlamak için:

```csharp
static class SampleClass
{
    public static string SampleString = "Sample String";
}
```

Statik üyeye erişmek için, bu sınıfın bir nesnesini oluşturmadan sınıfın adını kullanın:

```csharp
Console.WriteLine(SampleClass.SampleString);
```

C#'daki statik sınıflar yalnızca statik üyelere sahiptir ve anında alınamaz. Statik üyeler de statik olmayan özelliklere, alanlara veya yöntemlere erişemez

Daha fazla bilgi için bkz: [statik](../../language-reference/keywords/static.md).

### <a name="anonymous-types"></a>Anonim türleri

Anonim türler, veri türü için sınıf tanımı yazmadan nesneler oluşturmanıza olanak tanır. Bunun yerine, derleyici sizin için bir sınıf oluşturur. Sınıfın kullanılabilir bir adı yoktur ve nesneyi bildirirken belirttiğiniz özellikleri içerir.

Anonim bir tür örneği oluşturmak için:

```csharp
// sampleObject is an instance of a simple anonymous type.
var sampleObject =
    new { FirstProperty = "A", SecondProperty = "B" };
```

Daha fazla bilgi için bkz: [Anonim Türleri](../classes-and-structs/anonymous-types.md).

## <a name="inheritance"></a>Devralma

Devralma, başka bir sınıfta tanımlanan davranışı yeniden kullanan, genişleten ve değiştiren yeni bir sınıf oluşturmanıza olanak tanır. Üyeleri devralınan *sınıfa taban sınıf,* bu üyeleri devralan sınıfa *ise türemiş sınıf*denir. Ancak, C#'daki tüm sınıflar <xref:System.Object> ,.NET sınıf hiyerarşisini destekleyen ve tüm sınıflara düşük düzeyli hizmetler sağlayan sınıftan örtülü olarak devralır.

> [!NOTE]
> C# birden fazla mirası desteklemez. Diğer bir tanesi, türemiş bir sınıf için yalnızca bir taban sınıf belirtebilirsiniz.

Taban sınıftan devralmak için:

```csharp
class DerivedClass:BaseClass {}
```

Varsayılan olarak tüm sınıflar devralınabilir. Ancak, bir sınıfın taban sınıf olarak kullanılmaması mı yoksa yalnızca taban sınıf olarak kullanılabilecek bir sınıf oluşturup oluşturmayacağını belirtebilirsiniz.

Bir sınıfın taban sınıf olarak kullanılamayacağını belirtmek için:

```csharp
public sealed class A { }
```

Bir sınıfın yalnızca taban sınıf olarak kullanılabileceğini ve anında kullanılamayacağını belirtmek için:

```csharp
public abstract class B { }
```

Daha fazla bilgi için bkz.

- [sealed](../../language-reference/keywords/sealed.md)

- [Soyut](../../language-reference/keywords/abstract.md)

### <a name="overriding-members"></a>Üyeleri Geçersiz Kılma

Varsayılan olarak, türetilmiş bir sınıf tüm üyeleri taban sınıfından devralır. Devralınan üyenin davranışını değiştirmek istiyorsanız, bunu geçersiz kılmanız gerekir. Diğer bir deyişle, türemiş sınıfta yöntem, özellik veya olay yeni bir uygulama tanımlayabilirsiniz.

Aşağıdaki değiştiriciler özelliklerin ve yöntemlerin nasıl geçersiz kılındığını denetlemek için kullanılır:

|C# Değiştirici|Tanım|
|------------------|----------------|
|[virtual](../../language-reference/keywords/virtual.md)|Bir sınıf üyesinin türetilmiş bir sınıfta geçersiz kılınmasına izin verir.|
|[Geçersiz kılma](../../language-reference/keywords/override.md)|Taban sınıfta tanımlanan sanal (geçersiz kılınabilir) bir üyeyi geçersiz kılar.|
|[Soyut](../../language-reference/keywords/abstract.md)|Bir sınıf üyesinin türemiş sınıfta geçersiz kılınmasını gerektirir.|
|[new Değiştiricisi](../../language-reference/keywords/new-modifier.md)|Taban sınıftan devralınan bir üyeyi gizler|

## <a name="interfaces"></a>Arabirimler

Arabirimler, sınıflar gibi, özellikler, yöntemler ve olaylar kümesi tanımlar. Ancak sınıfların aksine, arabirimler uygulama sağlamaz. Sınıflar tarafından uygulanır ve sınıflardan ayrı varlıklar olarak tanımlanır. Arabirim, arabirimi uygulayan bir sınıfın bu arabirimin her yönünü tam olarak tanımlandığı şekilde uygulaması gerektiğinden, bir sözleşmeyi temsil eder.

Arabirimi tanımlamak için:

```csharp
interface ISampleInterface
{
    void doSomething();
}
```

Bir sınıfta arabirim uygulamak için:

```csharp
class SampleClass : ISampleInterface
{
    void ISampleInterface.doSomething()
    {
        // Method implementation.
    }
}
```

Daha fazla bilgi [için, Arabirimler](../interfaces/index.md) ve [arayüz](../../language-reference/keywords/interface.md) anahtar kelimesi ndeki dil başvuru makalesi hakkındaki programlama kılavuzu makalesine bakın.

## <a name="generics"></a>Genel Türler

.NET Framework'deki sınıflar, yapılar, arabirimler ve yöntemler, depolayabildikleri veya kullanabilecekleri nesne türlerini tanımlayan *tür parametreleri* içerebilir. Jeneriklerin en yaygın örneği, koleksiyonda depolanacak nesnelerin türünü belirtebileceğiniz bir koleksiyondur.

Genel bir sınıf tanımlamak için:

```csharp
public class SampleGeneric<T>
{
    public T Field;
}
```

Genel bir sınıfın örneğini oluşturmak için:

```csharp
SampleGeneric<string> sampleObject = new SampleGeneric<string>();
sampleObject.Field = "Sample string";
```

Daha fazla bilgi için bkz.

- [Genel Türler](../../../standard/generics/index.md)

- [Genel Türler](../generics/index.md)

## <a name="delegates"></a>Temsilciler

*Temsilci,* yöntem imzasını tanımlayan ve uyumlu imzası olan herhangi bir yönteme başvuru sağlayan bir türdür. Temsilci aracılığıyla yöntemi çağırabilir (veya çağırabilirsiniz). Temsilciler, yöntemleri bağımsız değişkenler olarak diğer yöntemlere geçirmek için kullanılır.

> [!NOTE]
> Olay işleyicileri, temsilciler aracılığıyla çağrılan yöntemlerden başka bir şey değildir. Etkinlik işlemede temsilci kullanma hakkında daha fazla bilgi için [Etkinlikler'e](../../../standard/events/index.md)bakın.

Bir temsilci oluşturmak için:

```csharp
public delegate void SampleDelegate(string str);
```

Temsilci tarafından belirtilen imzayla eşleşen bir yönteme başvuru oluşturmak için:

```csharp
class SampleClass
{
    // Method that matches the SampleDelegate signature.
    public static void sampleMethod(string message)
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

Daha fazla bilgi [için, Temsilciler](../delegates/index.md) hakkındaki programlama kılavuzu makalesine ve [temsilci](../../language-reference/builtin-types/reference-types.md) anahtar kelimesindeki dil başvuru makalesine bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
