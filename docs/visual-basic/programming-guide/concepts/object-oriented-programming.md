---
title: Nesne odaklı programlama (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 49794de4-64c3-473c-b8ed-fe98835df69c
ms.openlocfilehash: 058d8b932e50f784d4a5cefa9fadfb31953687f0
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153936"
---
# <a name="object-oriented-programming-visual-basic"></a>Nesne odaklı programlama (Visual Basic)

Visual Basic kapsülleme, devralma ve çok biçimlilik dahil olmak üzere nesne yönelimli programlama için tam destek sağlar.

 *Kapsülleme* ilgili özellikleri, yöntemleri ve diğer üyeleri bir grup işlem tek bir birim veya nesne anlamına gelir.

 *Devralma* mevcut bir sınıfı temel alan yeni sınıflar oluşturma becerisidir.

 *Çok biçimlilik* her sınıf aynı özellikleri veya yöntemleri farklı şekilde uygular olsa da birbirinin yerine kullanılabilen birden fazla sınıfınız olabileceği anlamına gelir.

 Bu bölüm aşağıdaki kavramları açıklar:

- [Sınıflar ve nesneler](#classes-and-objects)
  - [Sınıf üyeleri](#class-members)
    - [Özellikler ve alanları](#properties-and-fields)
    - [Yöntemler](#methods)
    - [Oluşturucular](#constructors)
    - [Yıkıcılar](#destructors)
    - [Olaylar](#events)
    - [İç içe geçmiş sınıflar](#nested-classes)
  - [Erişim değiştiricileri ve erişim düzeyleri](#access-modifiers-and-access-levels)
    - [Sınıf oluşturma](#instantiating-classes)
    - [Paylaşılan sınıflar ve Üyeler](#shared-classes-and-members)
    - [Anonim türler](#anonymous-types)
- [Devralma](#inheritance)
  - [Üyeleri geçersiz kılma](#overriding-members)
- [Arabirimler](#interfaces)
- [Genel Türler](#generics)
- [Temsilciler](#delegates)

## <a name="classes-and-objects"></a>Sınıflar ve nesneler

Koşulları *sınıfı* ve *nesne* bazen birbirlerinin yerine, ancak aslında sınıfları açıklar kullanılan *türü* nesnelerin nesneleri iken  *örnekleri* sınıf. Bu nedenle, bir nesne oluşturma işlemi olarak da adlandırılır *oluşturmada*. Blueprint benzerliği kullanarak bir sınıf plandır ve nesne bu yapılan bir binadır.

Bir sınıf tanımlamak için:

```vb
Class SampleClass
End Class
```

Visual Basic, hafif bir sınıflar adlandırılan sürümünü de sağlar *yapıları* yapın ve büyük nesneler dizisi oluşturmanız gerektiğinde yararlı olan çok fazla bellek için kullanmak istemiyorsanız.

Yapı tanımlamak için:

```vb
Structure SampleStructure
End Structure
```

Daha fazla bilgi için bkz.:

- [Class Deyimi](../../../visual-basic/language-reference/statements/class-statement.md)
- [Structure Deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)

### <a name="class-members"></a>Sınıf üyeleri

Her sınıf farklı olabilir *sınıf üyeleri* sınıf verilerini, sınıf davranışını tanımlayan yöntemleri ve farklı sınıflar ve nesneler arasındaki iletişimi sağlayan olayları tanımlayan özellikler içerir.

#### <a name="properties-and-fields"></a>Özellikler ve alanları

Alanlar ve özellikler bir nesnenin içerdiği bilgileri temsil eder. Bunlar okunabilir ve doğrudan ayarlamak için alanları gibi değişkenlerdir.

Bir alanı tanımlamak için:

```vb
Class SampleClass
    Public SampleField As String
End Class
```

Özellik get ve set yordamları, değerlerin nasıl ayarlanacağı veya döndürüleceği hakkında daha fazla denetim sağlar.

Visual Basic ya da özellik değerini depolamak için özel bir alan oluşturabilir veya bu alanı arka planda otomatik olarak oluşturmak ve özellik yordamları için temel mantığı sağlayan sözde ve otomatik olarak uygulanan özellikler sağlar.

Otomatik uygulanan bir özellik tanımlamak için:

```vb
Class SampleClass
    Public Property SampleProperty as String
End Class
```

Okuma için bazı ek işlemler gerçekleştirebilir ve yazma özellik değeri özellik değerini depolamak için bir alan tanımlayın ve depolanması ve alınması için temel mantığı sağlayan gerekiyorsa:

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

Çoğu özellikleri, yöntemleri ya da yordamlar hem ayarlamak ve özellik değerini almak için vardır. Ancak, değiştiren veya okunmalarını kısıtlamak için salt okunur veya salt yazılır özellikler oluşturabilirsiniz. Visual Basic'te kullanabileceğiniz `ReadOnly` ve `WriteOnly` anahtar sözcükleri. Ancak, otomatik uygulanan özellikler salt okunur veya salt yazılır olamaz.

Daha fazla bilgi için bkz.:

- [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)
- [Get Deyimi](../../../visual-basic/language-reference/statements/get-statement.md)
- [Set Deyimi](../../../visual-basic/language-reference/statements/set-statement.md)
- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)

#### <a name="methods"></a>Yöntemler

 A *yöntemi* , nesnenin gerçekleştirebileceği bir eylemdir.

> [!NOTE]
> Visual Basic'te, bir yöntem oluşturmanın iki yolu vardır: `Sub` deyimi kullanılır; değer döndürmezse `Function` bir yöntem bir değer döndürüyorsa deyimi kullanılır.

Bir sınıfın yöntemini tanımlamak için:

```vb
Class SampleClass
    Public Function SampleFunc(ByVal SampleParam As String)
        ' Add code here
    End Function
End Class
```

Bir sınıfta çeşitli uygulamalar olabilir veya *aşırı*, parametre sayıları veya parametre türleri içinde farklı aynı yöntemin.

Bir yöntemi aşırı yüklemek için:

```vb
Overloads Sub Display(ByVal theChar As Char)
    ' Add code that displays Char data.
End Sub
Overloads Sub Display(ByVal theInteger As Integer)
    ' Add code that displays Integer data.
End Sub
```

Çoğu durumda, sınıf tanımında bir yöntem bildirin. Ancak, Visual Basic de destekler *genişletme yöntemleri* mevcut sınıfa sınıfın gerçek tanımı dışında yöntemler eklemenize olanak tanıyan.

Daha fazla bilgi için bkz.:

- [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)
- [Genişletme Yöntemleri](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)

#### <a name="constructors"></a>Oluşturucular

Oluşturucular, belirli bir türde bir nesne oluşturulduğunda, otomatik olarak yürütülen sınıf yöntemleridir. Kurucular genellikle yeni nesnenin veri üyeleri başlatın. Sonra yalnızca bir sınıf oluşturulduğunda Oluşturucu çalıştırabilirsiniz. Ayrıca, Oluşturucudaki kod her zaman bir sınıftaki herhangi bir kod önce çalışır. Ancak, başka bir yöntem olduğu gibi birden çok oluşturucu aşırı yüklemeleri oluşturabilirsiniz.

Bir sınıf için bir kurucu tanımlamak için:

```vb
Class SampleClass
    Sub New(ByVal s As String)
        // Add code here.
    End Sub
End Class
```

Daha fazla bilgi için bkz.: [Nesne ömrü: Nesneler nasıl oluşturulur ve imha](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).

#### <a name="destructors"></a>Yıkıcılar

Yıkıcılar, sınıfların örneklerini yok etmek üzere kullanılır. .NET Framework, atık toplayıcı sağlanmasını ve ayrılmasını uygulamanızda yönetilen nesneler için bellek otomatik olarak yönetir. Ancak, Yıkıcılar uygulamanızın oluşturduğu herhangi yönetilmeyen kaynakları temizlemek için yine de gerekebilir. Bir sınıf için yalnızca bir yıkıcı olabilir.

Yok ediciler ve çöp toplama .NET Framework'teki hakkında daha fazla bilgi için bkz: [çöp toplama](../../../standard/garbage-collection/index.md).

#### <a name="events"></a>Olaylar

Bir sınıf olayları etkinleştirin veya nesneyi diğer sınıfları veya nesneleri ilgilendiğiniz bir şeyler olduğunda gerçekleşir. Olay gönderir (veya harekete geçiren) sınıf adlı *yayımcı* ve olay alma (veya tanıtıcı) sınıflar adlandırılan *aboneleri*. Olaylar hakkında daha fazla bilgi için nasıl oluştukları ve işlendikleri bkz [olayları](../../../standard/events/index.md).

- Olayları bildirmek için kullanın [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).

- Olayları yükseltmek için kullanmak [RaiseEvent deyimi](../../../visual-basic/language-reference/statements/raiseevent-statement.md).

- Bildirim temelli bir yöntemini kullanarak olay işleyicileri belirtmek için kullanın [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) deyimi ve [işleme](../../../visual-basic/language-reference/statements/handles-clause.md) yan tümcesi.

- Dinamik olarak ekleme, kaldırma ve bir olay ile ilişkili olay işleyicisini değiştirme yapabilmek için kullanmak [AddHandler deyimi](../../../visual-basic/language-reference/statements/addhandler-statement.md) ve [RemoveHandler deyimi](../../../visual-basic/language-reference/statements/removehandler-statement.md) ile birlikte [AddressOf İşleç](../../../visual-basic/language-reference/operators/addressof-operator.md).

#### <a name="nested-classes"></a>İç içe geçmiş sınıflar

Başka bir sınıfın içinde tanımlanan bir sınıfa *iç içe geçmiş*. Varsayılan olarak, iç içe geçmiş özel sınıftır.

```vb
Class Container
    Class Nested
    ' Add code here.
    End Class
End Class
```

İç içe geçmiş sınıfının bir örneğini oluşturmak için kapsayıcı sınıfının arkasına bir nokta koyun ve sonra ardından iç içe geçmiş sınıf adı adını kullanın:

```vb
Dim nestedInstance As Container.Nested = New Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a>Erişim değiştiricileri ve erişim düzeyleri

Tüm sınıflar ve sınıf üyeleri sağlamaları için diğer sınıflar kullanılarak hangi erişim düzeyini belirtebilirsiniz *erişim değiştiricilerine*.

Aşağıdaki erişim değiştiriciler kullanılabilir:

|Visual Basic değiştiricisi|Tanım|
|---------------------------|----------------|
|[Public](../../../visual-basic/language-reference/modifiers/public.md)|Türe veya üyeye aynı derlemenin veya ona başvuran başka bir derleme içindeki diğer kodlardan tarafından erişilebilir.|
|[Private](../../../visual-basic/language-reference/modifiers/private.md)|Türe veya üyeye aynı sınıftaki kod tarafından yalnızca erişilebilir.|
|[Protected](../../../visual-basic/language-reference/modifiers/protected.md)|Türe veya üyeye aynı sınıftaki veya türetilmiş bir sınıf içinde kod tarafından yalnızca erişilebilir.|
|[Friend](../../../visual-basic/language-reference/modifiers/friend.md)|Türe veya üyeye aynı derlemedeki ancak farklı derlemeyle herhangi bir kod tarafından erişilebilir.|
|`Protected Friend`|Türe veya üyeye aynı derlemedeki kod ile veya başka bir derlemedeki türetilmiş sınıfla erişilebilir.|

Daha fazla bilgi için [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

### <a name="instantiating-classes"></a>Sınıf oluşturma

Bir nesne oluşturmak için bir sınıf örneği başlatmanız veya sınıf örneği oluşturmanız gerekir.

```vb
Dim sampleObject as New SampleClass()
```

Bir sınıf başlatıldıktan sonra Örneğin özelliklerine ve alanlarına değerler atayın ve sınıf yöntemini çağırabilirsiniz.

```vb
' Set a property value.
sampleObject.SampleProperty = "Sample String"
' Call a method.
sampleObject.SampleMethod()
```

Sınıf örnekleme işlemi sırasında özellikleri değerleri atamak için nesne başlatıcıları kullanın:

```vb
Dim sampleObject = New SampleClass With
    {.FirstProperty = "A", .SecondProperty = "B"}
```

Daha fazla bilgi için bkz.:

- [New İşleci](../../../visual-basic/language-reference/operators/new-operator.md)
- [Nesne başlatıcıları: Adlandırılmış ve anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)

### <a name="shared-classes-and-members"></a>Paylaşılan sınıflar ve Üyeler

 Paylaşılan bir sınıfın üyesi bir özellik, yordam veya bir sınıfın tüm örnekleri tarafından paylaşıldığını alan var.

 Paylaşılan bir üye tanımlamak için:

```vb
Class SampleClass
    Public Shared SampleString As String = "Sample String"
End Class
```

 Paylaşılan üyeye erişmek için sınıfın adını, bu sınıfın bir nesnesi oluşturmadan kullanın:

```vb
MsgBox(SampleClass.SampleString)
```

 Visual Basic'te paylaşılan modülleri, üyeleri yalnızca paylaşılan ve örnekleri oluşturulamaz. Paylaşılan üyeleri ayrıca paylaşılmayan özellikleri, alanlara veya yöntemlere erişemez

 Daha fazla bilgi için bkz.:

- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Module Deyimi](../../../visual-basic/language-reference/statements/module-statement.md)

### <a name="anonymous-types"></a>Anonim türler

Anonim türler nesne veri türü için bir sınıf tanımı yazmaya gerek kalmadan oluşturmanıza olanak sağlar. Bunun yerine, derleyici bir sınıf sizin için oluşturur. Sınıfın kullanılabilir adı yok ve nesneyi bildirirken belirttiğiniz özellikleri içeriyor.

Anonim bir türün bir örneğini oluşturmak için:

```vb
' sampleObject is an instance of a simple anonymous type.
Dim sampleObject =
    New With {Key .FirstProperty = "A", .SecondProperty = "B"}
```

Daha fazla bilgi için bkz.: [Anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).

## <a name="inheritance"></a>Devralma

Devralma, başka bir sınıfta tanımlanan davranışı değiştirir kullanır ve genişleten yeni bir sınıf oluşturmanıza olanak sağlar. Üyeleri devralınan sınıf *temel sınıfı*, ve bu üyeleri devralan sınıf *türetilmiş sınıf*. Ancak, Visual Basic'te tüm sınıflar örtük olarak devralınacak <xref:System.Object> .NET sınıf hiyerarşisini destekleyen ve tüm sınıflara alt düzey hizmetler sağlayan sınıf.

> [!NOTE]
> Visual Basic, birden çok devralmayı desteklemez. Diğer bir deyişle, türetilmiş bir sınıf için yalnızca bir temel sınıf belirtebilirsiniz.

Temel sınıfından devralmak için:

```vb
Class DerivedClass
    Inherits BaseClass
End Class
```

Varsayılan olarak, tüm sınıflar devralınabilir. Ancak, bir sınıfın temel sınıf olarak kullanılmamalıdır veya yalnızca temel sınıf olarak kullanılan bir sınıf oluşturmak olup olmadığını belirtebilirsiniz.

Bir sınıfın temel sınıf olarak kullanılamayacağını belirtmek için:

```vb
NotInheritable Class SampleClass
End Class
```

Bir sınıf yalnızca temel sınıf olarak kullanılabilecek ve başlatılamayacak belirtmek için:

```vb
MustInherit Class BaseClass
End Class
```

Daha fazla bilgi için bkz.:

- [Inherits Deyimi](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)

### <a name="overriding-members"></a>Üyeleri geçersiz kılma

Varsayılan olarak, türetilmiş bir sınıf tüm üyelerini kendi temel sınıfından devralır. Devralınan üye davranışını değiştirmek istiyorsanız, onu geçersiz kılmanız gerekir. Diğer bir deyişle, türetilmiş bir sınıf içindeki yöntemin, özelliğin veya olayın yeni bir uygulamasını tanımlayabilirsiniz.

Özellikleri ve yöntemleri nasıl geçersiz kılınacağını denetlemek için aşağıdaki değiştiriciler kullanılır:

|Visual Basic değiştiricisi|Tanım|
|---------------------------|----------------|
|[Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)|Bir sınıf üyesinin türetilmiş bir sınıfta geçersiz kılınmasına izin verir.|
|[Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)|Temel sınıfta tanımlanan sanal bir (geçersiz kılınabilir) üyeyi geçersiz kılar.|
|[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)|Üye devralınan bir sınıfta kılınmasını önler.|
|[MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)|Gerektiren bir sınıf üyesinin derlenen sınıfta geçersiz kılınacak.|
|[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)|Bir temel sınıftan devralınan üyeyi gizler|

## <a name="interfaces"></a>Arabirimler

Sınıflar gibi arabirimler, özellikleri, yöntemleri ve olayları kümesi tanımlarsınız. Ancak, sınıflardan farklı olarak, arabirimler uygulama sağlamaz. Bunlar sınıfları tarafından uygulanır ve sınıflardan ayrı varlıklar olarak tanımlanır. Tam olarak tanımlandığı şekilde bir arabirimi uygulayan bir sınıf, o arabirimi her yönüyle uygulamalıdır bir arabirim bir sözleşmeyi temsil eder.

Arabirim tanımlamak için:

```vb
Public Interface ISampleInterface
    Sub DoSomething()
End Interface
```

Bir sınıf içinde arabirim uygulamak için:

```vb
Class SampleClass
    Implements ISampleInterface
    Sub DoSomething
        ' Method implementation.
    End Sub
End Class
```

Daha fazla bilgi için bkz.:

- [Arabirimler](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [Interface Deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Implements Deyimi](../../../visual-basic/language-reference/statements/implements-statement.md)

## <a name="generics"></a>Genel Türler

Sınıflar, yapılar, arabirimler ve yöntemler .NET içerebilir *tür parametrelerindeki* bunlar depolayabildikleri veya kullanabildikleri nesnelerin türlerini tanımlayan. Genel türlerin yararları en yaygın örnek, bir koleksiyonda depolanacak nesnelerin türünü belirleyebileceğiniz koleksiyonudur.

Genel bir sınıf tanımlamak için:

```vb
Class SampleGeneric(Of T)
    Public Field As T
End Class
```

Bir genel sınıfın bir örneğini oluşturmak için:

```vb
Dim sampleObject As New SampleGeneric(Of String)
sampleObject.Field = "Sample string"
```

Daha fazla bilgi için bkz.:

- [Genel Türler](../../../standard/generics/index.md)
- [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)

## <a name="delegates"></a>Temsilciler

 A *temsilci* , yöntem imzasını tanımlayan bir türdür ve uyumlu bir imza ile herhangi bir yönteme başvuru sağlayabilir. Çağırma (çağrı yöntemi temsilci aracılığıyla veya). Temsilciler, yöntemleri bağımsız değişkenler olarak diğer yöntemlere geçirmek için kullanılır.

> [!NOTE]
> Olay işleyicileri, temsilciler aracılığıyla çağrılan yöntemlerden başka bir şey değildir. Temsilcileri olay işlemede kullanma hakkında daha fazla bilgi için bkz. [olayları](../../../standard/events/index.md).

Temsilci oluşturmak için:

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

Daha fazla bilgi için bkz.:

- [Temsilciler](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Delegate Deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [AddressOf İşleci](../../../visual-basic/language-reference/operators/addressof-operator.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic programlama kılavuzu](../../../visual-basic/programming-guide/index.md)
