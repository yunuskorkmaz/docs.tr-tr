---
title: Nesne odaklı programlama
ms.date: 07/20/2015
ms.assetid: 49794de4-64c3-473c-b8ed-fe98835df69c
ms.openlocfilehash: f7e222cde8ce80d4c52cc8b4b111c576eb4041b9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413199"
---
# <a name="object-oriented-programming-visual-basic"></a>Nesne odaklı programlama (Visual Basic)

Visual Basic, kapsülleme, devralma ve çok biçimlilik dahil olmak üzere nesne odaklı programlama için tam destek sağlar.

 *Kapsülleme* , ilişkili özellikler, Yöntemler ve diğer üyelerin bir grubunun tek bir birim veya nesne olarak kabul edildiği anlamına gelir.

 *Devralma* , mevcut bir sınıfı temel alan yeni sınıflar oluşturma özelliğini açıklar.

 Çok *biçimlilik* , her bir sınıf farklı yollarla aynı özellikleri veya yöntemleri uyguladığından bile, birbirinin yerine kullanılabilecek birden fazla sınıfa sahip olabileceği anlamına gelir.

 Bu bölümde aşağıdaki kavramlar açıklanmaktadır:

- [Sınıflar ve nesneler](#classes-and-objects)
  - [Sınıf üyeleri](#class-members)
    - [Özellikler ve alanlar](#properties-and-fields)
    - [Yöntemler](#methods)
    - [Oluşturucular](#constructors)
    - [Yıkıcılar](#destructors)
    - [Olaylar](#events)
    - [İç içe geçmiş sınıflar](#nested-classes)
  - [Erişim değiştiricileri ve erişim düzeyleri](#access-modifiers-and-access-levels)
    - [Sınıfları örnekleme](#instantiating-classes)
    - [Paylaşılan sınıflar ve Üyeler](#shared-classes-and-members)
    - [Anonim türler](#anonymous-types)
- [Devralma](#inheritance)
  - [Üyeleri geçersiz kılma](#overriding-members)
- [Arabirimler](#interfaces)
- [Genel Türler](#generics)
- [Temsilciler](#delegates)

## <a name="classes-and-objects"></a>Sınıflar ve nesneler

Terimler *sınıfı* ve *nesne* bazen birbirinin yerine kullanılır, ancak aslında nesneler sınıfların kullanılabilir *örnekleri* olduğunda sınıflar nesne *türünü* betimler. Bu nedenle, bir nesne oluşturma konusuna *örnek*oluşturma denir. Şema benzerleme vurguladı kullanarak bir sınıf şeması bir şema, bir nesne ise bu şema tarafından oluşturulan bir derleme.

Bir sınıf tanımlamak için:

```vb
Class SampleClass
End Class
```

Visual Basic Ayrıca, büyük bir nesne dizisi oluşturmanız gerektiğinde ve bunun için çok fazla bellek kullanmak istemediğinizde yararlı olan *yapılar* adlı sınıfların hafif bir sürümünü sağlar.

Bir yapı tanımlamak için:

```vb
Structure SampleStructure
End Structure
```

Daha fazla bilgi için bkz.

- [Class Deyimi](../../language-reference/statements/class-statement.md)
- [Structure Yapısı](../../language-reference/statements/structure-statement.md)

### <a name="class-members"></a>Sınıf üyeleri

Her sınıf, sınıf verilerini tanımlayan özellikleri, sınıf davranışını tanımlayan yöntemleri ve farklı sınıflar ve nesneler arasında iletişim sağlayan olayları içeren farklı *sınıf üyelerine* sahip olabilir.

#### <a name="properties-and-fields"></a>Özellikler ve alanlar

Alanlar ve özellikler bir nesnenin içerdiği bilgileri temsil eder. Alanlar, okunabilir veya doğrudan ayarlanabileceğinden, değişkenlere benzer.

Bir alan tanımlamak için:

```vb
Class SampleClass
    Public SampleField As String
End Class
```

Özellikler, değerlerin nasıl ayarlandığı veya döndürüldüğü hakkında daha fazla denetim sağlayan alma ve ayarlama yordamlarına sahiptir.

Visual Basic, özellik değerini depolamak için özel bir alan oluşturmanıza veya bu alanı arka planda otomatik olarak oluşturan ve özellik yordamları için temel mantığı sağlayan, otomatik olarak uygulanan özelliklerin kullanılmasına izin verir.

Otomatik uygulanan bir özellik tanımlamak için:

```vb
Class SampleClass
    Public Property SampleProperty as String
End Class
```

Özellik değerini okumak ve yazmak için bazı ek işlemler gerçekleştirmeniz gerekiyorsa, özellik değerini depolamak için bir alan tanımlayın ve bunu depolamak ve almak için temel mantığı sağlayın:

```vb
Class SampleClass
    Private m_Sample As String
    Public Property Sample() As String
        Get
            ' Return the value stored in the field.
            Return m_Sample
        End Get
        Set(ByVal Value As String)
            ' Store the value in the field.
            m_Sample = Value
        End Set
    End Property
End Class
```

Çoğu özelliğin, özellik değerini ayarlamak ve almak için yöntemleri ya da yordamları vardır. Ancak, bunları değiştirilmesini veya okumayı kısıtlamak için salt okunurdur veya salt yazılır özellikler oluşturabilirsiniz. Visual Basic, `ReadOnly` ve `WriteOnly` anahtar sözcüklerini kullanabilirsiniz. Ancak otomatik olarak uygulanan özellikler salt okunurdur veya salt yazılır olamaz.

Daha fazla bilgi için bkz.

- [Property Deyimi](../../language-reference/statements/property-statement.md)
- [Get Deyimi](../../language-reference/statements/get-statement.md)
- [Set deyimleri](../../language-reference/statements/set-statement.md)
- [Özelliğinin](../../language-reference/modifiers/readonly.md)
- [WriteOnly](../../language-reference/modifiers/writeonly.md)

#### <a name="methods"></a>Yöntemler

 Bir *Yöntem* , bir nesnenin gerçekleştirebileceği bir eylemdir.

> [!NOTE]
> Visual Basic, bir yöntem oluşturmanın iki yolu vardır: `Sub` Yöntem bir değer döndürmezse ifade kullanılır; `Function` bir yöntem bir değer döndürürse, ifade kullanılır.

Bir sınıfın yöntemini tanımlamak için:

```vb
Class SampleClass
    Public Function SampleFunc(ByVal SampleParam As String)
        ' Add code here
    End Function
End Class
```

Bir sınıf, parametrelerin veya parametre türlerinin sayısında farklı olan aynı yöntemin çeşitli uygulamalarına veya *aşırı*yüküne sahip olabilir.

Bir yöntemi aşırı yüklemek için:

```vb
Overloads Sub Display(ByVal theChar As Char)
    ' Add code that displays Char data.
End Sub
Overloads Sub Display(ByVal theInteger As Integer)
    ' Add code that displays Integer data.
End Sub
```

Çoğu durumda, bir sınıf tanımı içinde bir yöntemi bildirirsiniz. Ancak Visual Basic Ayrıca, sınıfının gerçek tanımının dışında mevcut bir sınıfa Yöntemler eklemenize olanak tanıyan *genişletme yöntemlerini* destekler.

Daha fazla bilgi için bkz.

- [Function Deyimi](../../language-reference/statements/function-statement.md)
- [Sub Deyimi](../../language-reference/statements/sub-statement.md)
- [Aşırı Yüklemeler](../../language-reference/modifiers/overloads.md)
- [Uzantı yöntemleri](../language-features/procedures/extension-methods.md)

#### <a name="constructors"></a>Oluşturucular

Oluşturucular, belirli bir türden bir nesne oluşturulduğunda otomatik olarak yürütülen sınıf yöntemleridir. Oluşturucular genellikle yeni nesnenin veri üyelerini başlatır. Bir Oluşturucu, bir sınıf oluşturulduğunda yalnızca bir kez çalıştırılabilir. Ayrıca, kurucudaki kod her zaman bir sınıftaki diğer koddan önce çalışır. Ancak, başka bir yöntemle aynı şekilde birden çok Oluşturucu aşırı yüklemesi oluşturabilirsiniz.

Bir sınıf için bir Oluşturucu tanımlamak için:

```vb
Class SampleClass
    Sub New(ByVal s As String)
        // Add code here.
    End Sub
End Class
```

Daha fazla bilgi için bkz. [nesne ömrü: nesneleri oluşturma ve yok etme](../language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).

#### <a name="destructors"></a>Yıkıcılar

Yok ediciler sınıfların örneklerini deketmek için kullanılır. .NET Framework, çöp toplayıcı uygulamanızdaki yönetilen nesneler için bellek ayırmayı ve serbest bırakma işlemini otomatik olarak yönetir. Ancak, uygulamanızın oluşturduğu yönetilmeyen kaynakları temizlemek için yine de yıkıcı gerekebilir. Bir sınıf için yalnızca bir yıkıcı olabilir.

.NET Framework Yıkıcılar ve çöp toplama hakkında daha fazla bilgi için bkz. [çöp toplama](../../../standard/garbage-collection/index.md).

#### <a name="events"></a>Olaylar

Olaylar, bir sınıf ya da nesnenin, ilgi çekici bir şeyler gerçekleştiğinde diğer sınıflara veya nesnelere bildirilmesini sağlar. Olayı gönderen (veya Başlatan) sınıf *Yayımcı* olarak adlandırılır ve olayı alan (veya işleyen) sınıflar *aboneler*olarak adlandırılır. Olaylar, nasıl oluşturulur ve işlenir hakkında daha fazla bilgi için bkz. [Olaylar](../../../standard/events/index.md).

- Olayları bildirmek için [Event ifadesini](../../language-reference/statements/event-statement.md)kullanın.

- Olay yükseltmek için [RaiseEvent ifadesini](../../language-reference/statements/raiseevent-statement.md)kullanın.

- Bildirim temelli bir yöntem kullanarak olay işleyicileri belirtmek için [WithEvents](../../language-reference/modifiers/withevents.md) deyimi ve [Handles](../../language-reference/statements/handles-clause.md) yan tümcesini kullanın.

- Bir olayla ilişkili olay işleyicisini dinamik olarak eklemek, kaldırmak ve değiştirmek için, [AddressOf işleci](../../language-reference/operators/addressof-operator.md)Ile birlikte [AddHandler](../../language-reference/statements/addhandler-statement.md) ifadesini ve [RemoveHandler ifadesini](../../language-reference/statements/removehandler-statement.md) kullanın.

#### <a name="nested-classes"></a>İç içe geçmiş sınıflar

Başka bir sınıf içinde tanımlı bir sınıf *iç içe*çağırılır. Varsayılan olarak, iç içe yerleştirilmiş sınıf özeldir.

```vb
Class Container
    Class Nested
    ' Add code here.
    End Class
End Class
```

İç içe yerleştirilmiş sınıfın bir örneğini oluşturmak için, container sınıfının adını ve ardından nokta ve ardından iç içe geçmiş sınıfın adını kullanın:

```vb
Dim nestedInstance As Container.Nested = New Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a>Erişim değiştiricileri ve erişim düzeyleri

Tüm sınıflar ve sınıf üyeleri, *erişim değiştiricilerini*kullanarak diğer sınıflara hangi erişim düzeyini sundukları belirler.

Aşağıdaki erişim değiştiriciler kullanılabilir:

|Visual Basic değiştirici|Tanım|
|---------------------------|----------------|
|[Geneldir](../../language-reference/modifiers/public.md)|Türe veya üyeye aynı derlemedeki veya buna başvuran başka bir derlemede bir veya daha fazla kod tarafından erişilebilir.|
|[Özelleştirme](../../language-reference/modifiers/private.md)|Türe veya üyeye yalnızca aynı sınıftaki kodla erişilebilir.|
|[Korunamadı](../../language-reference/modifiers/protected.md)|Türe veya üyeye yalnızca aynı sınıftaki veya türetilmiş bir sınıftaki kodla erişilebilir.|
|[Dost](../../language-reference/modifiers/friend.md)|Türe veya üyeye aynı derlemedeki kod tarafından erişilebilir, ancak başka bir derlemeden erişilebilir.|
|`Protected Friend`|Türe veya üyeye aynı derlemedeki herhangi bir kod ya da başka bir derlemedeki türetilmiş bir sınıf tarafından erişilebilir.|

Daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](../language-features/declared-elements/access-levels.md).

### <a name="instantiating-classes"></a>Sınıfları örnekleme

Bir nesne oluşturmak için bir sınıf örneği oluşturmanız veya bir sınıf örneği oluşturmanız gerekir.

```vb
Dim sampleObject as New SampleClass()
```

Bir sınıfı örnekledikten sonra, örneğin özelliklerine ve alanlarına değerler atayabilir ve sınıf yöntemlerini çağırabilirsiniz.

```vb
' Set a property value.
sampleObject.SampleProperty = "Sample String"
' Call a method.
sampleObject.SampleMethod()
```

Sınıf örnek oluşturma işlemi sırasında özelliklere değer atamak için, nesne başlatıcıları kullanın:

```vb
Dim sampleObject = New SampleClass With
    {.FirstProperty = "A", .SecondProperty = "B"}
```

Daha fazla bilgi için bkz.

- [New Işleci](../../language-reference/operators/new-operator.md)
- [Nesne Başlatıcıları: Adlandırılmış ve Anonim Türler](../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)

### <a name="shared-classes-and-members"></a>Paylaşılan sınıflar ve Üyeler

 Sınıfın paylaşılan bir üyesi bir sınıfın tüm örnekleri tarafından paylaşılan bir özellik, yordam veya alandır.

 Paylaşılan bir üye tanımlamak için:

```vb
Class SampleClass
    Public Shared SampleString As String = "Sample String"
End Class
```

 Paylaşılan üyeye erişmek için sınıfın adını bu sınıfın bir nesnesi oluşturmadan kullanın:

```vb
MsgBox(SampleClass.SampleString)
```

 Visual Basic paylaşılan modüller yalnızca paylaşılan üyelere sahiptir ve örneklenemez. Paylaşılan Üyeler ayrıca paylaşılmayan özelliklere, alanlara veya yöntemlere erişemez

 Daha fazla bilgi için bkz.

- [Shared](../../language-reference/modifiers/shared.md)
- [Module Deyimi](../../language-reference/statements/module-statement.md)

### <a name="anonymous-types"></a>Anonim türler

Anonim türler, veri türü için bir sınıf tanımı yazmadan nesneler oluşturmanızı sağlar. Bunun yerine, derleyici sizin için bir sınıf oluşturur. Sınıfın kullanılabilir adı yok ve nesneyi bildirirken belirttiğiniz özellikleri içerir.

Anonim türün bir örneğini oluşturmak için:

```vb
' sampleObject is an instance of a simple anonymous type.
Dim sampleObject =
    New With {Key .FirstProperty = "A", .SecondProperty = "B"}
```

Daha fazla bilgi için bkz: [anonim türler](../language-features/objects-and-classes/anonymous-types.md).

## <a name="inheritance"></a>Devralma

Devralma, başka bir sınıfta tanımlanan davranışı yeniden kullanan, genişleten ve değiştiren yeni bir sınıf oluşturmanıza olanak sağlar. Üyeleri devralınmış olan sınıfa *temel sınıf*denir ve bu üyeleri devralan sınıfa *türetilmiş sınıf*denir. Ancak Visual Basic içindeki tüm sınıflar, <xref:System.Object> .NET sınıf hiyerarşisini destekleyen sınıftan dolaylı olarak devralınır ve tüm sınıflara alt düzey hizmetler sağlar.

> [!NOTE]
> Visual Basic birden çok devralmayı desteklemez. Diğer bir deyişle, türetilmiş bir sınıf için yalnızca bir temel sınıf belirtebilirsiniz.

Temel sınıftan devralması için:

```vb
Class DerivedClass
    Inherits BaseClass
End Class
```

Varsayılan olarak, tüm sınıflar devralınabilir. Ancak, bir sınıfın temel sınıf olarak kullanılması gerekip gerekmediğini belirtebilir veya yalnızca temel sınıf olarak kullanılabilecek bir sınıf oluşturmanız gerekir.

Bir sınıfın temel sınıf olarak kullanılamayacağını belirtmek için:

```vb
NotInheritable Class SampleClass
End Class
```

Bir sınıfın yalnızca temel sınıf olarak kullanılabileceğini ve örneklenemez olduğunu belirtmek için:

```vb
MustInherit Class BaseClass
End Class
```

Daha fazla bilgi için bkz.

- [Inherits Deyimi](../../language-reference/statements/inherits-statement.md)
- [NotInheritable](../../language-reference/modifiers/notinheritable.md)
- [MustInherit](../../language-reference/modifiers/mustinherit.md)

### <a name="overriding-members"></a>Üyeleri geçersiz kılma

Varsayılan olarak, türetilmiş bir sınıf kendi temel sınıfından tüm üyeleri devralır. Devralınan üyenin davranışını değiştirmek istiyorsanız, onu geçersiz kılmanız gerekir. Diğer bir deyişle, türetilmiş sınıfta yöntemin, özelliğin veya olayın yeni bir uygulamasını tanımlayabilirsiniz.

Özelliklerin ve yöntemlerin nasıl geçersiz kılınabileceğini denetlemek için aşağıdaki değiştiriciler kullanılır:

|Visual Basic değiştirici|Tanım|
|---------------------------|----------------|
|[Overridable](../../language-reference/modifiers/overridable.md)|Bir sınıf üyesinin türetilmiş bir sınıfta geçersiz kılınmasına izin verir.|
|[Geçersiz Kılmalar](../../language-reference/modifiers/overrides.md)|Temel sınıfta tanımlanan bir sanal (geçersiz kılınabilir) üyeyi geçersiz kılar.|
|[NotOverridable](../../language-reference/modifiers/notoverridable.md)|Devralan bir sınıfta üyenin geçersiz kılınmasını önler.|
|[MustOverride](../../language-reference/modifiers/mustoverride.md)|Türetilmiş sınıfta bir sınıf üyesinin geçersiz kılınmasını gerektirir.|
|[Shadows](../../language-reference/modifiers/shadows.md)|Temel sınıftan devralınan bir üyeyi gizler|

## <a name="interfaces"></a>Arabirimler

Sınıflar gibi arabirimler, özellikler, Yöntemler ve olaylar kümesi tanımlar. Ancak sınıfların aksine arabirimler uygulama sağlamaz. Sınıflar tarafından uygulanır ve sınıflardan ayrı varlıklar olarak tanımlanır. Arabirim, bir arabirimi uygulayan bir sınıfın, bu arabirimin her yönünü tam olarak tanımlandığı gibi uygulaması gerektiğini belirten bir sözleşmeyi temsil eder.

Bir arabirim tanımlamak için:

```vb
Public Interface ISampleInterface
    Sub DoSomething()
End Interface
```

Bir sınıfa bir arabirim uygulamak için:

```vb
Class SampleClass
    Implements ISampleInterface
    Sub DoSomething
        ' Method implementation.
    End Sub
End Class
```

Daha fazla bilgi için bkz.

- [Arabirimler](../language-features/interfaces/index.md)
- [Interface Deyimi](../../language-reference/statements/interface-statement.md)
- [Implements Deyimi](../../language-reference/statements/implements-statement.md)

## <a name="generics"></a>Genel Türler

.NET 'teki sınıflar, yapılar, arabirimler ve Yöntemler, depolayabilecekleri veya kullanabileceği nesne türlerini tanımlayan *tür parametreleri* içerebilir. En yaygın genel türler örneği, bir koleksiyonda depolanacak nesne türlerini belirtebileceğiniz bir koleksiyondur.

Genel bir sınıf tanımlamak için:

```vb
Class SampleGeneric(Of T)
    Public Field As T
End Class
```

Genel sınıfın bir örneğini oluşturmak için:

```vb
Dim sampleObject As New SampleGeneric(Of String)
sampleObject.Field = "Sample string"
```

Daha fazla bilgi için bkz.

- [Genel Türler](../../../standard/generics/index.md)
- [Visual Basic genel türler](../language-features/data-types/generic-types.md)

## <a name="delegates"></a>Temsilciler

 *Temsilci* , yöntem imzasını tanımlayan bir türdür ve uyumlu imzaya sahip herhangi bir yönteme başvuru sağlayabilir. Yöntemi temsilci aracılığıyla çağırabilir (veya çağırabilirsiniz). Temsilciler, yöntemleri bağımsız değişkenler olarak diğer yöntemlere geçirmek için kullanılır.

> [!NOTE]
> Olay işleyicileri, temsilciler aracılığıyla çağrılan yöntemlerden başka bir şey değildir. Olay İşlemede temsilciler kullanma hakkında daha fazla bilgi için bkz. [Olaylar](../../../standard/events/index.md).

Bir temsilci oluşturmak için:

```vb
Delegate Sub SampleDelegate(ByVal str As String)
```

Temsilci tarafından belirtilen imzayla eşleşen bir yönteme başvuru oluşturmak için:

```vb
Class SampleClass
    ' Method that matches the SampleDelegate signature.
    Sub SampleSub(ByVal str As String)
        ' Add code here.
    End Sub
    ' Method that instantiates the delegate.
    Sub SampleDelegateSub()
        Dim sd As SampleDelegate = AddressOf SampleSub
        sd("Sample string")
    End Sub
End Class
```

Daha fazla bilgi için bkz.

- [Temsilciler](../language-features/delegates/index.md)
- [Delegate Deyimi](../../language-reference/statements/delegate-statement.md)
- [AddressOf İşleci](../../language-reference/operators/addressof-operator.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic Programlama Kılavuzu](../index.md)
