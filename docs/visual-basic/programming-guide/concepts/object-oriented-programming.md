---
title: "Nesne odaklı programlama (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 49794de4-64c3-473c-b8ed-fe98835df69c
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 950f080949dce0fc1a2834825d2f7c945007fb7b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="object-oriented-programming-visual-basic"></a>Nesne odaklı programlama (Visual Basic)
Visual Basic kapsülleme, devralma ve çok biçimlilik dahil nesne odaklı programlama için tam destek sağlar.  
  
 *Kapsülleme* ilgili özellikleri, yöntemleri ve diğer üyeleri bir grup kabul edilir olduğunu tek bir birim veya nesne olarak anlamına gelir.  
  
 *Devralma* var olan bir sınıfına dayalı yeni sınıflar oluşturma olanağı açıklar.  
  
 *Çok biçimlilik* farklı yollarla aynı özelliklerinin veya yöntemlerin her sınıf uygulayan olsa bile, birbirinin yerine, kullanılabilir birden çok sınıf olabilir anlamına gelir.  
  
 Bu bölümde aşağıdaki kavramlar açıklanmaktadır:  
  
-   [Sınıflar ve nesneler](#classes-and-objects)  
  
    -   [Sınıf üyeleri](#members)  
  
         [Özellikleri ve alanları](#properties-and-fields)  
  
         [Yöntemleri](#methods)  
  
         [Oluşturucular](#constructors)  
  
         [Yıkıcılar](#destructors)  
  
         [Olayları](#events)  
  
         [İç içe geçmiş sınıflar](#nested-classes)  
  
    -   [Erişim değiştiricileri ve erişim düzeylerini](#access-modifiers-and-access-levels)  
  
    -   [Örnek oluşturma sınıfları](#instantiating-classes)  
  
    -   [Paylaşılan sınıflar ve üyeleri](#shared-classes-and-members)  
  
    -   [Anonim türler](#anonymous-types)  
  
-   [Devralma](#inheritance)  
  
    -   [Üyeleri geçersiz kılma](#overriding-members)  
  
-   [Arabirimleri](#interfaces)  
  
-   [Genel türler](#generics)  
  
-   [Temsilciler](#delegates)  
  
## <a name="classes-and-objects"></a>Sınıflar ve nesneler  
Koşulları *sınıfı* ve *nesne* bazen birbirinin yerine, ancak aslında, sınıfları açıklar kullanılan *türü* nesnelerin nesneleri kullanılabilir durumdayken  *örnekleri* sınıfların. Bu nedenle, bir nesne oluşturma işlemi adlı *örneklemesi*. Şeması benzerleme kullanarak şeması sınıftır ve o şeması yapılan bir yapı bir nesnedir.

Bir sınıf tanımlamak için:

```vb  
Class SampleClass
End Class
```

Visual Basic adlı sınıflar açık bir sürümünü de sağlar *yapıları* büyük nesneler dizisi oluşturmak ve gerektiğinde faydalı olan çok fazla bellek için kullanmak istediğiniz değil.

Bir yapı tanımlamak için:  

```vb
Structure SampleStructure
End Structure
```

Daha fazla bilgi için bkz.:

- [Class deyimi](../../../visual-basic/language-reference/statements/class-statement.md)

- [Structure deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)

### <a name="class-members"></a>Sınıf üyeleri
Her sınıf farklı olabilir *sınıfı üyeleri* sınıfı verileri, sınıf davranışını tanımlayan yöntemleri ve farklı sınıflar ve nesneler arasındaki iletişimi sağlamak olayları tanımlayan özelliği içerir.

#### <a name="properties-and-fields"></a>Özellikleri ve alanları
Alanları ve özellikleri bir nesne içeren bilgileri temsil eder. Bunlar okunabilir veya doğrudan ayarlamak için alanları gibi değişkenlerdir.

Bir alan tanımlamak için:

```vb
Class SampleClass
    Public SampleField As String
End Class
```

Özelliklerin get ve değerleri nasıl ayarlayın veya döndürülen üzerinde daha fazla denetim sağlamak yordamları ayarlayın.

Visual Basic, özellik değeri depolamak için özel bir alan oluşturun veya bu alan otomatik olarak arka planda oluşturun ve özellik yordamlar için temel mantığın sözde ve otomatik uygulanan özellikler kullanmak üzere sağlar.

Otomatik uygulanan bir özellik tanımlamak için:

```vb
Class SampleClass
    Public Property SampleProperty as String
End Class
```

Özellik değeri depolamak için bir alan tanımlayın ve depolamak ve bunu alma için temel mantığı sağlar özellik değeri yazılırken okuma için bazı ek işlemler gerçekleştirmek ve gerekirse:

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

Çoğu özellikleri yöntemleri ya da hem ayarlamak ve özellik değerini almak için yordamlar vardır. Ancak, okuma veya değiştirilmesini kısıtlamak için salt okunur veya salt yazılır özellikler oluşturabilirsiniz. Visual Basic'te kullandığınız `ReadOnly` ve `WriteOnly` anahtar sözcükler. Ancak, otomatik uygulanan özellikler salt okunur veya sadece yazılabilir olamaz.

Daha fazla bilgi için bkz.:
  
-   [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Get deyimi](../../../visual-basic/language-reference/statements/get-statement.md)  
  
-   [Set deyimi](../../../visual-basic/language-reference/statements/set-statement.md)  
  
-   [Salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md)  
  
-   [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)  
  
#### <a name="methods"></a>Yöntemler  
 A *yöntemi* bir nesne gerçekleştirebileceğiniz bir eylemdir.  

> [!NOTE]
>  Visual Basic'te bir yöntem oluşturmanın iki yolu vardır: `Sub` yöntemi bir değer; döndürmezse deyimi kullanılan `Function` deyimi bir yöntemi bir değer döndürürse kullanılır.

Bir sınıfın bir yöntemi tanımlamak için:

```vb
Class SampleClass
    Public Function SampleFunc(ByVal SampleParam As String)
        ' Add code here
    End Function
End Class
```

Bir sınıf çeşitli uygulamalarını olabilir veya *aşırı*, aynı yönteminin parametreleri veya parametre türleri sayısında farklılık gösterir.

Bir yöntem aşırı yükleme için:

```vb
Overloads Sub Display(ByVal theChar As Char)
    ' Add code that displays Char data.
End Sub
Overloads Sub Display(ByVal theInteger As Integer)
    ' Add code that displays Integer data.
End Sub
```

Çoğu durumda bir sınıf tanımı içinde bir yöntem bildirin. Ancak, Visual Basic de destekler *genişletme yöntemleri* sınıfının gerçek tanımının dışında varolan bir sınıfı yöntemleri eklemek izin verir.

Daha fazla bilgi için bkz.:

- [Function deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  

- [Sub deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  

- [Aşırı yüklemeler](../../../visual-basic/language-reference/modifiers/overloads.md)  

- [Genişletme yöntemleri](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  

#### <a name="constructors"></a>Oluşturucular  
Oluşturucular belirli bir türde bir nesne oluşturulduğunda, otomatik olarak yürütülen sınıfı yöntemleridir. Oluşturucular genellikle yeni nesnenin veri üyeleri başlatır. Yalnızca bir sınıf oluşturulduğunda sonra bir oluşturucu çalıştırabilirsiniz. Ayrıca, Oluşturucusu kodda, başka bir kod sınıfında önce her zaman çalışır. Ancak, başka bir yöntem için olduğu gibi aynı şekilde, birden çok Oluşturucusu aşırı oluşturabilirsiniz.

Bir sınıf için bir oluşturucu tanımlamak için:

```vb
Class SampleClass
    Sub New(ByVal s As String)
        // Add code here.
    End Sub
End Class 
```

Daha fazla bilgi için bkz: [nesne ömrü: nesneleri oluşturma ve Destroyed şeklini](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).

#### <a name="destructors"></a>Yıkıcılar
Yıkıcılar sınıfların örneklerini destruct için kullanılır. .NET Framework Atık toplayıcısının ayırma ve uygulamanızda yönetilen nesneler için bellek sürümü otomatik olarak yönetir. Ancak, uygulamanızın oluşturduğu herhangi yönetilmeyen kaynakları temizlemek için Yıkıcılar hala gerekebilir. Bir sınıf için yalnızca bir yıkıcı olabilir.

Yok ediciler ve .NET Framework atık toplama hakkında daha fazla bilgi için bkz: [çöp toplama](../../../standard/garbage-collection/index.md).

#### <a name="events"></a>Olaylar
Bir sınıf olayları etkinleştirin veya diğer sınıflar bildirmek için nesne veya nesnelerin çeken bir şey olduğunda oluşur. Olay gönderir (veya oluşturur) sınıf adlı *yayımcı* ve olay alın (veya ele) sınıfları adlı *aboneleri*. Olaylar hakkında daha fazla bilgi için nasıl oluşturulur ve işlenmiş, bkz: [olayları](../../../standard/events/index.md).

- Olayları bildirme için kullanmak [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).

- Olayları yükseltmek için kullanmak [RaiseEvent deyimi](../../../visual-basic/language-reference/statements/raiseevent-statement.md).

- Olay işleyicileri bildirim temelli bir yolunu kullanarak belirtmek için kullanın [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) deyimi ve [işler](../../../visual-basic/language-reference/statements/handles-clause.md) yan tümcesi.

- Dinamik olarak eklemek, kaldırmak ve olayla ilişkili olay işleyicisini değiştirin yapabiliyor olmanız için kullanmak [AddHandler deyimi](../../../visual-basic/language-reference/statements/addhandler-statement.md) ve [RemoveHandler deyimi](../../../visual-basic/language-reference/statements/removehandler-statement.md) ile birlikte [AddressOf İşleç](../../../visual-basic/language-reference/operators/addressof-operator.md).

#### <a name="nested-classes"></a>İç içe geçmiş sınıflar  
Başka bir sınıfın içinde tanımlanmış bir sınıf olarak adlandırılan *iç içe geçmiş*. Varsayılan olarak, iç içe geçmiş sınıf özeldir.

```vb
Class Container
    Class Nested
    ' Add code here.
    End Class
End Class
```

İç içe geçmiş sınıf örneği oluşturmak için nokta tarafından takip ve iç içe geçmiş sınıf adına göre ve ardından kapsayıcı sınıfın adını kullanın:

```vb
Dim nestedInstance As Container.Nested = New Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a>Erişim değiştiricileri ve erişim düzeylerini  
Tüm sınıflar ve sınıf üyeleri sağladıkları diğer sınıflara kullanarak hangi erişim düzeyi belirtebilirsiniz *erişim değiştiricileri*.

Aşağıdaki erişim değiştiricileri kullanılabilir:

|Visual Basic değiştiricisi|Tanım|
|---------------------------|----------------|
|[Ortak](../../../visual-basic/language-reference/modifiers/public.md)|Tür veya üye, başka bir kod aynı bütünleştirilmiş kodda ya da başvurduğu başka bir derleme tarafından erişilebilir.|
|[Özel](../../../visual-basic/language-reference/modifiers/private.md)|Tür veya üye yalnızca aynı sınıfta kodu tarafından erişilebilir.|
|[Korumalı](../../../visual-basic/language-reference/modifiers/protected.md)|Tür veya üye yalnızca kodu aynı sınıfın veya türetilmiş bir sınıf tarafından erişilebilir.|
|[Arkadaş](../../../visual-basic/language-reference/modifiers/friend.md)|Tür veya üye, herhangi bir kod aynı bütünleştirilmiş kodda değiştirebilir, ancak başka bir derleme tarafından erişilebilir.|
|`Protected Friend`|Tür veya üye aynı bütünleştirilmiş kod veya başka bir derlemede herhangi bir türetilmiş sınıf tarafından erişilebilir.|

Daha fazla bilgi için bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

### <a name="instantiating-classes"></a>Örnek oluşturma sınıfları  
Nesne oluşturmak için bir sınıf örneği veya bir sınıf örneği oluşturmak gerekir.

```vb
Dim sampleObject as New SampleClass()
```

Bir sınıf örneği sonra değerleri örneğin özellikleri ve alanları atayın ve sınıf yöntemlerini çağırın.

```vb
' Set a property value.
sampleObject.SampleProperty = "Sample String"
' Call a method.
sampleObject.SampleMethod()
```

Sınıf örnek oluşturma işlemi sırasında özellikleri değerleri atamak için nesne başlatıcıları kullanın:

```vb
Dim sampleObject = New SampleClass With
    {.FirstProperty = "A", .SecondProperty = "B"}
```

Daha fazla bilgi için bkz.:

- [New işleci](../../../visual-basic/language-reference/operators/new-operator.md)

- [Nesne başlatıcıları: Adlandırılmış ve anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)

###  <a name="Static"></a>Paylaşılan sınıflar ve üyeleri  
 Bir paylaşılan sınıfı bir özellik, yordam veya bir sınıfın tüm örnekleri tarafından paylaşılan alan üyesidir.  
  
 Paylaşılan bir üyeye tanımlamak için:  
  
```vb  
Class SampleClass  
    Public Shared SampleString As String = "Sample String"  
End Class  
```  
  
 Paylaşılan üyeye erişmek için bu sınıfın bir nesnesi oluşturmadan sınıfın adını kullanın:  
  
```vb  
MsgBox(SampleClass.SampleString)  
```  
  
 Visual Basic'te paylaşılan modülleri üyeleri yalnızca paylaşılan ve örneği oluşturulamıyor. Paylaşılan üyeler da paylaşılmayan özellikleri, alan veya yöntem erişemiyor  
  
 Daha fazla bilgi için bkz.:  
  
-   [Paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md)  
  
-   [Module deyimi](../../../visual-basic/language-reference/statements/module-statement.md)  
  
### <a name="anonymous-types"></a>Anonim türler  
Anonim türler veri türü için bir sınıf tanımı yazmadan nesneleri oluşturmak etkinleştirin. Bunun yerine, derleyici bir sınıf sizin için oluşturur. Sınıf kullanılabilir adı yok ve nesne bildirme belirttiğiniz özellikler içerir.

Anonim bir türün bir örneğini oluşturmak için:

```vb
' sampleObject is an instance of a simple anonymous type.
Dim sampleObject =
    New With {Key .FirstProperty = "A", .SecondProperty = "B"}
```

Daha fazla bilgi için bkz: [anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).

## <a name="inheritance"></a>Devralma
Devralma yeniden kullanır, genişletir ve başka bir sınıf içinde tanımlanan davranışını değiştiren yeni bir sınıf oluşturmanıza olanak sağlar. Üyeleri devralındığı sınıfı adlı *temel sınıfı*, bu üyeler devralan sınıf adı verilen ve *türetilmiş sınıf*. Ancak, Visual Basic'te tüm sınıflar örtük olarak devralınmalıdır <xref:System.Object> .NET sınıf hiyerarşisi destekleyen ve tüm sınıfları için alt düzey hizmetleri sağlayan sınıf.

> [!NOTE]
>  Visual Basic birden çok devralma desteklemiyor. Diğer bir deyişle, türetilmiş bir sınıf için yalnızca bir temel sınıf belirtebilirsiniz.

Bir taban sınıftan devralın için:

```vb
Class DerivedClass
    Inherits BaseClass
End Class
```

Varsayılan olarak tüm sınıflar devralınabilir. Ancak, bir sınıfın temel sınıf olarak kullanılmamalıdır veya yalnızca bir temel sınıf olarak kullanılan bir sınıf oluşturun olup olmadığını belirtebilirsiniz.

Bir sınıfın temel sınıf olarak kullanılan belirtmek için:

```vb
NotInheritable Class SampleClass
End Class
```

Sınıfı yalnızca bir temel sınıf olarak kullanılabilir ve başlatılamaz belirtmek için:

```vb
MustInherit Class BaseClass
End Class
```

Daha fazla bilgi için bkz.:

- [Inherits deyimi](../../../visual-basic/language-reference/statements/inherits-statement.md)

- [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)

- [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)

### <a name="overriding-members"></a>Üyeleri geçersiz kılma
Varsayılan olarak, türetilmiş bir sınıf tüm üyelerin kendi taban sınıfından devralıyor. Devralınan üye davranışını değiştirmek istiyorsanız, bunu geçersiz kılmanız gerekir. Diğer bir deyişle, yeni bir uygulama yöntemi, özelliği veya olay türetilen sınıfta tanımlayabilirsiniz.

Aşağıdaki değiştiricileri özellikleri ve yöntemleri nasıl geçersiz kılınır denetlemek için kullanılır:

|Visual Basic değiştiricisi|Tanım|
|---------------------------|----------------|
|[Geçersiz kılınabilir](../../../visual-basic/language-reference/modifiers/overridable.md)|Türetilen bir sınıfta geçersiz kılınmak üzere sınıf üyesine sağlar.|
|[Geçersiz kılmaları](../../../visual-basic/language-reference/modifiers/overrides.md)|Taban sınıf içinde tanımlı sanal (geçersiz kılınabilir) üyesi geçersiz kılar.|
|[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)|Türetilen bir sınıfta geçersiz üye engeller.|
|[MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)|Gerektiren türetilen bir sınıfta geçersiz kılınmak üzere bir sınıf üyesi.|
|[Gölgeleri](../../../visual-basic/language-reference/modifiers/shadows.md)|Bir taban sınıftan devralınan üye gizler|

## <a name="interfaces"></a>Arabirimler
Sınıfları gibi arabirimler özellikleri, yöntemleri ve olayları kümesini tanımlar. Ancak sınıflarından farklı olarak, uygulama arabirimleri sağlamaz. Bunlar sınıfları tarafından uygulanan ve sınıflardan ayrı varlıklar olarak tanımlanır. Tam olarak tanımlandığı şekilde bir arabirimini uygulayan bir sınıf her açıdan bu arabirimi uygulamalıdır içeren bir sözleşme bir arabirimi temsil eder.

Bir arabirim tanımlamak için:

```vb
Public Interface ISampleInterface
    Sub DoSomething()
End Interface
```

Bir sınıfta bir arabirim uygulamak için:

```vb
Class SampleClass
    Implements ISampleInterface
    Sub DoSomething
        ' Method implementation.
    End Sub
End Class
```

Daha fazla bilgi için bkz.:

- [Arabirimleri](../../../visual-basic/programming-guide/language-features/interfaces/index.md)  

- [Interface deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)  

- [Implements deyimi](../../../visual-basic/language-reference/statements/implements-statement.md)  

## <a name="generics"></a>Genel Türler
Sınıflar, yapılar, arabirimler ve .NET yöntemleri dahil edebileceğiniz *tür parametrelerindeki* kullanan depolamak veya nesne türlerini tanımlar. Genel türler en yaygın örneği, bir koleksiyonda depolanan nesnelerin türü belirtebileceğiniz koleksiyonudur.  

Genel bir sınıf tanımlamak için:

```vb
Class SampleGeneric(Of T)
    Public Field As T
End Class
```

Genel bir sınıf örneği oluşturmak için:

```vb
Dim sampleObject As New SampleGeneric(Of String)
sampleObject.Field = "Sample string"
```

Daha fazla bilgi için bkz.:

- [Genel türler](~/docs/standard/generics/index.md)

- [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)

## <a name="delegates"></a>Temsilciler
 A *temsilci* yöntem imzası tanımlar türüdür ve herhangi bir yöntem başvuru ile uyumlu bir imzası sağlayabilir. Çağırma (çağrı yöntemi temsilci aracılığıyla veya). Temsilciler, yöntemleri bağımsız değişkenler olarak diğer yöntemlere geçirmek için kullanılır.

> [!NOTE]
>  Olay işleyicileri, temsilciler aracılığıyla çağrılan yöntemlerden başka bir şey değildir. Olay işlemede kullanma hakkında daha fazla bilgi için bkz: [olayları](../../../standard/events/index.md).

Bir temsilciyi oluşturmak için:

```vb
Delegate Sub SampleDelegate(ByVal str As String)
```

Temsilci tarafından belirtilen imza eşleşen bir yöntem başvuru oluşturmak için:

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

- [Delegate deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md)

- [AddressOf işleci](../../../visual-basic/language-reference/operators/addressof-operator.md)

## <a name="see-also"></a>Ayrıca bkz.
 [Visual Basic programlama kılavuzu](../../../visual-basic/programming-guide/index.md)
