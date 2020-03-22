---
title: Nesne yönelimli programlama
ms.date: 07/20/2015
ms.assetid: 49794de4-64c3-473c-b8ed-fe98835df69c
ms.openlocfilehash: 3739919273f4cdd285d519c414c542f1a82a16d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400689"
---
# <a name="object-oriented-programming-visual-basic"></a>Nesne yönelimli programlama (Visual Basic)

Visual Basic kapsülleme, kalıtım ve çok biçimlilik gibi nesne yönelimli programlama için tam destek sağlar.

 *Kapsülleme,* ilgili özellikler, yöntemler ve diğer üyelerden oluşan bir grubun tek bir birim veya nesne olarak kabul edilsi anlamına gelir.

 *Devralma,* varolan bir sınıfa dayalı yeni sınıflar oluşturma yeteneğini açıklar.

 *Çok biçimlilik,* her sınıf aynı özellikleri veya yöntemleri farklı şekillerde uygulasa bile, birbirinin yerine kullanılabilecek birden çok sınıfa sahip olabileceğiniz anlamına gelir.

 Bu bölümde aşağıdaki kavramlar açıklanmaktadır:

- [Sınıflar ve nesneler](#classes-and-objects)
  - [Sınıf üyeleri](#class-members)
    - [Özellikler ve alanlar](#properties-and-fields)
    - [Yöntemler](#methods)
    - [Oluşturucular](#constructors)
    - [Yıkıcılar](#destructors)
    - [Olaylar](#events)
    - [İç içe sınıflar](#nested-classes)
  - [Değiştiricilere ve erişim düzeylerine erişin](#access-modifiers-and-access-levels)
    - [Anında sınıflar](#instantiating-classes)
    - [Paylaşılan sınıflar ve üyeler](#shared-classes-and-members)
    - [Anonim türleri](#anonymous-types)
- [Devralma](#inheritance)
  - [Üyeleri geçersiz kılma](#overriding-members)
- [Arabirimler](#interfaces)
- [Genel Türler](#generics)
- [Temsilciler](#delegates)

## <a name="classes-and-objects"></a>Sınıflar ve nesneler

*Sınıf* ve *nesne* terimleri bazen birbirinin yerine kullanılır, ancak aslında sınıflar nesnelerin *türünü* açıklarken, nesneler kullanılabilir sınıf *örnekleridir.* Yani, bir nesne oluşturma eylemine *anlık hareket*denir. Plan benzetmesini kullanarak, sınıf bir plandır ve bir nesne de bu plandan yapılmış bir binadır.

Bir sınıfı tanımlamak için:

```vb
Class SampleClass
End Class
```

Visual Basic ayrıca, büyük bir nesne dizisi oluşturmanız gerektiğinde yararlı olan ve bunun için çok fazla bellek tüketmek istemediğinde yararlı olan *yapılar* adı verilen sınıfların hafif bir sürümünü de sağlar.

Bir yapıtanımlamak için:

```vb
Structure SampleStructure
End Structure
```

Daha fazla bilgi için bkz.

- [Class Deyimi](../../../visual-basic/language-reference/statements/class-statement.md)
- [Structure Deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)

### <a name="class-members"></a>Sınıf üyeleri

Her *sınıfın,* sınıf verilerini açıklayan özellikleri, sınıf davranışını tanımlayan yöntemleri ve farklı sınıflar ve nesneler arasında iletişim sağlayan olayları içeren farklı sınıf üyeleri olabilir.

#### <a name="properties-and-fields"></a>Özellikler ve alanlar

Alanlar ve özellikler, nesnenin içerdiği bilgileri temsil ediyor. Alanlar, doğrudan okunabildikleri veya ayarlanabildikleri için değişkenler gibidir.

Bir alanı tanımlamak için:

```vb
Class SampleClass
    Public SampleField As String
End Class
```

Özellikler, değerlerin nasıl ayarlandığı veya döndürüldüğü konusunda daha fazla denetim sağlayan yordamları alırıp ayarla

Visual Basic, özellik değerini depolamak için özel bir alan oluşturmanıza veya bu alanı otomatik olarak arka planda oluşturan ve özellik yordamları için temel mantığı sağlayan otomatik olarak uygulanan özellikleri kullanmanıza olanak tanır.

Otomatik olarak uygulanan bir özelliği tanımlamak için:

```vb
Class SampleClass
    Public Property SampleProperty as String
End Class
```

Özellik değerini okumak ve yazmak için bazı ek işlemler gerçekleştirmeniz gerekiyorsa, özellik değerini depolamak için bir alan tanımlayın ve depolamak ve almak için temel mantığı sağlayın:

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

Çoğu özelliğin hem ayarlayıp hem de özellik değerini almak için yöntemleri veya yordamları vardır. Ancak, değiştirilmelerini veya okunmasını kısıtlamak için salt okunur veya yalnızca yazma özellikleri oluşturabilirsiniz. Visual Basic'te `ReadOnly` anahtar `WriteOnly` kelimeleri ve anahtar kelimeleri kullanabilirsiniz. Ancak, otomatik olarak uygulanan özellikler salt okunur veya yalnızca yazılamaz.

Daha fazla bilgi için bkz.

- [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)
- [Get Deyimi](../../../visual-basic/language-reference/statements/get-statement.md)
- [Set Deyimi](../../../visual-basic/language-reference/statements/set-statement.md)
- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)

#### <a name="methods"></a>Yöntemler

 *Yöntem,* bir nesnenin gerçekleştirebileceği bir eylemdir.

> [!NOTE]
> Visual Basic'te bir yöntem oluşturmanın iki `Sub` yolu vardır: yöntem bir değer döndürmüyorsa deyim kullanılır; `Function` bir yöntem bir değer döndürürse deyim kullanılır.

Bir sınıfın yöntemini tanımlamak için:

```vb
Class SampleClass
    Public Function SampleFunc(ByVal SampleParam As String)
        ' Add code here
    End Function
End Class
```

Bir sınıfın, parametre veya parametre türlerinin sayısında farklılık gösteren aynı yöntemin birkaç uygulaması veya *aşırı yüklemesi*olabilir.

Bir yöntemi aşırı yüklemek için:

```vb
Overloads Sub Display(ByVal theChar As Char)
    ' Add code that displays Char data.
End Sub
Overloads Sub Display(ByVal theInteger As Integer)
    ' Add code that displays Integer data.
End Sub
```

Çoğu durumda bir sınıf tanımı içinde bir yöntem bildirirsiniz. Ancak, Visual Basic, sınıfın gerçek tanımı dışında varolan bir sınıfa yöntem eklemenize olanak tanıyan *uzantı yöntemlerini* de destekler.

Daha fazla bilgi için bkz.

- [Fonksiyon Bildirimi](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Aşırı Yüklemeler](../../../visual-basic/language-reference/modifiers/overloads.md)
- [Genişletme Yöntemleri](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)

#### <a name="constructors"></a>Oluşturucular

Oluşturucular, belirli bir türdeki bir nesne oluşturulduğunda otomatik olarak yürütülen sınıf yöntemleridir. Oluşturucular genellikle yeni nesnenin veri üyelerini başlangıç olarak karşılarlar. Bir oluşturucu, bir sınıf oluşturulduğunda yalnızca bir kez çalıştırılabilir. Ayrıca, oluşturucudaki kod her zaman bir sınıftaki başka bir koddan önce çalışır. Ancak, birden çok oluşturucu başka bir yöntemle aynı şekilde aşırı yüklemeler oluşturabilirsiniz.

Bir sınıf için bir oluşturucu tanımlamak için:

```vb
Class SampleClass
    Sub New(ByVal s As String)
        // Add code here.
    End Sub
End Class
```

Daha fazla bilgi için bkz: [Nesne Yaşam Süresi: Nesneler Nasıl Oluşturulur ve Yok Edilir.](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)

#### <a name="destructors"></a>Yıkıcılar

Yıkıcılar sınıfların örneklerini yok etmek için kullanılır. .NET Framework'de, çöp toplayıcı, uygulamanızdaki yönetilen nesneler için bellek tahsisini ve serbest bırakılmasını otomatik olarak yönetir. Ancak, uygulamanızın oluşturduğu yönetilmeyen kaynakları temizlemek için yine de yıkıcılara ihtiyacınız olabilir. Bir sınıf için sadece bir yıkıcı olabilir.

.NET Framework'de yıkıcılar ve çöp toplama hakkında daha fazla bilgi için [Bkz.](../../../standard/garbage-collection/index.md)

#### <a name="events"></a>Olaylar

Olaylar, ilgi çekici bir şey oluştuğunda bir sınıfın veya nesnenin diğer sınıfları veya nesneleri bildirmesini sağlar. Olayı gönderen (veya yükselten) sınıfa *yayımcı,* olayı alan (veya işleyen) sınıflara *abone*denir. Olaylar hakkında daha fazla bilgi için, bunların nasıl yükseltildiği ve işlendiği [hakkında](../../../standard/events/index.md)bkz.

- Olayları bildirmek için [Olay Bildirimi'ni](../../../visual-basic/language-reference/statements/event-statement.md)kullanın.

- Olayları yükseltmek için [RaiseEvent Bildirimi'ni](../../../visual-basic/language-reference/statements/raiseevent-statement.md)kullanın.

- Olay işleyicilerini bildirimsel bir yol kullanarak belirtmek [için, WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) deyimini ve [İşleştiler](../../../visual-basic/language-reference/statements/handles-clause.md) yan tümcesini kullanın.

- Bir olayla ilişkili olay işleyicisini dinamik olarak ekleyebilmek, kaldırabilmek ve değiştirebilmek için, [İşleç'in Adresi](../../../visual-basic/language-reference/operators/addressof-operator.md)ile birlikte AddHandler Bildirimi ni ve [RemoveHandler Bildirimini](../../../visual-basic/language-reference/statements/addhandler-statement.md) kullanın. [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md)

#### <a name="nested-classes"></a>İç içe sınıflar

Başka bir sınıf içinde tanımlanan bir sınıf *iç içe*denir. Varsayılan olarak, iç içe sınıf özeldir.

```vb
Class Container
    Class Nested
    ' Add code here.
    End Class
End Class
```

İç içe sınıf bir örnek oluşturmak için, nokta ardından kapsayıcı sınıfın adını ve ardından iç içe sınıf adını kullanın:

```vb
Dim nestedInstance As Container.Nested = New Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a>Değiştiricilere ve erişim düzeylerine erişin

Tüm sınıflar ve sınıf *üyeleri, erişim değiştiriciler*kullanarak diğer sınıflara hangi erişim düzeyini sağladıklarını belirtebilir.

Aşağıdaki erişim değiştiriciler kullanılabilir:

|Görsel Temel Değiştirici|Tanım|
|---------------------------|----------------|
|[Genel](../../../visual-basic/language-reference/modifiers/public.md)|Türe veya üyeye, aynı derlemedeki veya ona başvuran başka bir derlemedeki başka bir kod erişebilir.|
|[Özel](../../../visual-basic/language-reference/modifiers/private.md)|Türe veya üyeye yalnızca aynı sınıftaki kodla erişilebilir.|
|[Korumalı](../../../visual-basic/language-reference/modifiers/protected.md)|Türe veya üyeye yalnızca aynı sınıftaveya türemiş bir sınıfta kodla erişilebilir.|
|[Arkadaş](../../../visual-basic/language-reference/modifiers/friend.md)|Türe veya üyeye aynı derlemedeki herhangi bir kod erişebilir, ancak başka bir derlemeden erişilemez.|
|`Protected Friend`|Türe veya üyeye aynı derlemedeki herhangi bir kod veya başka bir derlemedeki herhangi bir türemiş sınıf erişebilir.|

Daha fazla bilgi için [Visual Basic'teki Access düzeylerine](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)bakın.

### <a name="instantiating-classes"></a>Anında sınıflar

Bir nesne oluşturmak için, bir sınıfı anında oluşturmanız veya bir sınıf örneği oluşturmanız gerekir.

```vb
Dim sampleObject as New SampleClass()
```

Bir sınıfı anında yaptıktan sonra, örnek özelliklerine ve alanlarına değerler atayabilir ve sınıf yöntemlerini çağırabilirsiniz.

```vb
' Set a property value.
sampleObject.SampleProperty = "Sample String"
' Call a method.
sampleObject.SampleMethod()
```

Sınıf anlık işlem sırasında özelliklerine değer atamak için nesne baş harflerini kullanın:

```vb
Dim sampleObject = New SampleClass With
    {.FirstProperty = "A", .SecondProperty = "B"}
```

Daha fazla bilgi için bkz.

- [Yeni Operatör](../../../visual-basic/language-reference/operators/new-operator.md)
- [Nesne Başlatıcıları: Adlandırılmış ve Anonim Türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)

### <a name="shared-classes-and-members"></a>Paylaşılan sınıflar ve üyeler

 Sınıfın paylaşılan bir üyesi, sınıfın tüm örnekleri tarafından paylaşılan bir özellik, yordam veya alandır.

 Paylaşılan bir üyeyi tanımlamak için:

```vb
Class SampleClass
    Public Shared SampleString As String = "Sample String"
End Class
```

 Paylaşılan üyeye erişmek için, bu sınıfın bir nesnesini oluşturmadan sınıfın adını kullanın:

```vb
MsgBox(SampleClass.SampleString)
```

 Visual Basic'teki paylaşılan modüller yalnızca üyeleri paylaştı ve anlık olarak paylaşılamaz. Paylaşılan üyeler ayrıca paylaşılmayan özelliklere, alanlara veya yöntemlere erişemez

 Daha fazla bilgi için bkz.

- [Paylaşımlı](../../../visual-basic/language-reference/modifiers/shared.md)
- [Module Deyimi](../../../visual-basic/language-reference/statements/module-statement.md)

### <a name="anonymous-types"></a>Anonim türleri

Anonim türler, veri türü için sınıf tanımı yazmadan nesneler oluşturmanıza olanak tanır. Bunun yerine, derleyici sizin için bir sınıf oluşturur. Sınıfın kullanılabilir bir adı yoktur ve nesneyi bildirirken belirttiğiniz özellikleri içerir.

Anonim bir tür örneği oluşturmak için:

```vb
' sampleObject is an instance of a simple anonymous type.
Dim sampleObject =
    New With {Key .FirstProperty = "A", .SecondProperty = "B"}
```

Daha fazla bilgi için bkz: [Anonim Türleri](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).

## <a name="inheritance"></a>Devralma

Devralma, başka bir sınıfta tanımlanan davranışı yeniden kullanan, genişleten ve değiştiren yeni bir sınıf oluşturmanıza olanak tanır. Üyeleri devralınan *sınıfa taban sınıf,* bu üyeleri devralan sınıfa *ise türemiş sınıf*denir. Ancak, Visual Basic'teki tüm sınıflar <xref:System.Object> ,.NET sınıf hiyerarşisini destekleyen ve tüm sınıflara düşük düzeyli hizmetler sağlayan sınıftan örtülü olarak devralır.

> [!NOTE]
> Visual Basic birden çok devralmayı desteklemez. Diğer bir tanesi, türemiş bir sınıf için yalnızca bir taban sınıf belirtebilirsiniz.

Taban sınıftan devralmak için:

```vb
Class DerivedClass
    Inherits BaseClass
End Class
```

Varsayılan olarak tüm sınıflar devralınabilir. Ancak, bir sınıfın taban sınıf olarak kullanılmaması mı yoksa yalnızca taban sınıf olarak kullanılabilecek bir sınıf oluşturup oluşturmayacağını belirtebilirsiniz.

Bir sınıfın taban sınıf olarak kullanılamayacağını belirtmek için:

```vb
NotInheritable Class SampleClass
End Class
```

Bir sınıfın yalnızca taban sınıf olarak kullanılabileceğini ve anında kullanılamayacağını belirtmek için:

```vb
MustInherit Class BaseClass
End Class
```

Daha fazla bilgi için bkz.

- [Inherits Deyimi](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)

### <a name="overriding-members"></a>Üyeleri geçersiz kılma

Varsayılan olarak, türetilmiş bir sınıf tüm üyeleri taban sınıfından devralır. Devralınan üyenin davranışını değiştirmek istiyorsanız, bunu geçersiz kılmanız gerekir. Diğer bir deyişle, türemiş sınıfta yöntem, özellik veya olay yeni bir uygulama tanımlayabilirsiniz.

Aşağıdaki değiştiriciler özelliklerin ve yöntemlerin nasıl geçersiz kılındığını denetlemek için kullanılır:

|Görsel Temel Değiştirici|Tanım|
|---------------------------|----------------|
|[Geçersiz Kılınabilir](../../../visual-basic/language-reference/modifiers/overridable.md)|Bir sınıf üyesinin türetilmiş bir sınıfta geçersiz kılınmasına izin verir.|
|[Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)|Taban sınıfta tanımlanan sanal (geçersiz kılınabilir) bir üyeyi geçersiz kılar.|
|[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)|Bir üyenin devralan bir sınıfta geçersiz kılınmasını önler.|
|[MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)|Bir sınıf üyesinin türemiş sınıfta geçersiz kılınmasını gerektirir.|
|[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)|Taban sınıftan devralınan bir üyeyi gizler|

## <a name="interfaces"></a>Arabirimler

Arabirimler, sınıflar gibi, özellikler, yöntemler ve olaylar kümesi tanımlar. Ancak sınıfların aksine, arabirimler uygulama sağlamaz. Sınıflar tarafından uygulanır ve sınıflardan ayrı varlıklar olarak tanımlanır. Arabirim, arabirimi uygulayan bir sınıfın bu arabirimin her yönünü tam olarak tanımlandığı şekilde uygulaması gerektiğinden, bir sözleşmeyi temsil eder.

Arabirimi tanımlamak için:

```vb
Public Interface ISampleInterface
    Sub DoSomething()
End Interface
```

Bir sınıfta arabirim uygulamak için:

```vb
Class SampleClass
    Implements ISampleInterface
    Sub DoSomething
        ' Method implementation.
    End Sub
End Class
```

Daha fazla bilgi için bkz.

- [Arabirimler](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [Interface Deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Implements Deyimi](../../../visual-basic/language-reference/statements/implements-statement.md)

## <a name="generics"></a>Genel Türler

.NET'teki sınıflar, yapılar, arabirimler ve yöntemler, depolayabildikleri veya kullanabilecekleri nesne türlerini tanımlayan *tür parametreleri* içerebilir. Jeneriklerin en yaygın örneği, koleksiyonda depolanacak nesnelerin türünü belirtebileceğiniz bir koleksiyondur.

Genel bir sınıf tanımlamak için:

```vb
Class SampleGeneric(Of T)
    Public Field As T
End Class
```

Genel bir sınıfın örneğini oluşturmak için:

```vb
Dim sampleObject As New SampleGeneric(Of String)
sampleObject.Field = "Sample string"
```

Daha fazla bilgi için bkz.

- [Genel Türler](../../../standard/generics/index.md)
- [Visual Basic'te Genel Türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)

## <a name="delegates"></a>Temsilciler

 *Temsilci,* yöntem imzasını tanımlayan ve uyumlu imzası olan herhangi bir yönteme başvuru sağlayan bir türdür. Temsilci aracılığıyla yöntemi çağırabilir (veya çağırabilirsiniz). Temsilciler, yöntemleri bağımsız değişkenler olarak diğer yöntemlere geçirmek için kullanılır.

> [!NOTE]
> Olay işleyicileri, temsilciler aracılığıyla çağrılan yöntemlerden başka bir şey değildir. Etkinlik işlemede temsilci kullanma hakkında daha fazla bilgi için [Etkinlikler'e](../../../standard/events/index.md)bakın.

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

- [Temsilciler](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Delegate Deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [AddressOf İşleci](../../../visual-basic/language-reference/operators/addressof-operator.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic Programlama Kılavuzu](../../../visual-basic/programming-guide/index.md)
