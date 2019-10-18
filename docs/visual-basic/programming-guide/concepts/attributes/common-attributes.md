---
title: Ortak öznitelikler (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 11fe4894-1bf9-4525-a36b-cddcd3a5d22b
ms.openlocfilehash: 5bc568279a6952fdc5e0a000b1208cd7f9cfd6e7
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524287"
---
# <a name="common-attributes-visual-basic"></a>Ortak öznitelikler (Visual Basic)

Bu konuda Visual Basic programlarında en yaygın olarak kullanılan öznitelikler açıklanmaktadır.

- [Genel öznitelikler](#Global)

- [Kullanımdan kaldırılmış öznitelik](#Obsolete)

- [Koşullu öznitelik](#Conditional)

- [Arayan bilgileri öznitelikleri](#CallerInfo)

- [Visual Basic öznitelikleri](#VB)

## <a name="Global"></a>Genel öznitelikler

Çoğu öznitelik sınıflar veya yöntemler gibi belirli dil öğelerine uygulanır; Ancak, bazı öznitelikler geneldir, tüm derleme veya modül için geçerlidir. Örneğin, <xref:System.Reflection.AssemblyVersionAttribute> özniteliği aşağıdaki gibi bir derlemeye sürüm bilgilerini eklemek için kullanılabilir:

```vb
<Assembly: AssemblyVersion("1.0.0.0")>
```

Genel öznitelikler, herhangi bir üst düzey `Imports` deyimden sonra ve herhangi bir tür, modül veya ad alanı bildirimlerinden sonra kaynak kodunda görünür. Genel öznitelikler birden çok kaynak dosyasında görünebilir, ancak dosyaların tek bir derleme geçişinde derlenmesi gerekir. Visual Basic projeler için genel öznitelikler genellikle AssemblyInfo. vb dosyasına konur (Visual Studio 'da bir proje oluşturduğunuzda dosya otomatik olarak oluşturulur).

Derleme öznitelikleri, bir derleme hakkında bilgi sağlayan değerlerdir. Bunlar aşağıdaki kategorilere ayrılır:

- Bütünleştirilmiş kod kimliği öznitelikleri

- Bilgilendirici öznitelikler

- Bütünleştirilmiş kod bildirim öznitelikleri

### <a name="assembly-identity-attributes"></a>Bütünleştirilmiş kod kimliği öznitelikleri

Üç öznitelik (varsa, güçlü bir ad varsa) bir derlemenin kimliğini belirleme: ad, sürüm ve kültür. Bu öznitelikler, derlemenin tam adını oluşturur ve kodda başvuru yaptığınızda gereklidir. Öznitelikleri kullanarak bir derlemenin sürümünü ve kültürünü ayarlayabilirsiniz. Bununla birlikte, ad değeri derleyici tarafından, derleme [bilgileri Iletişim kutusunda](/visualstudio/ide/reference/assembly-information-dialog-box)VISUAL Studio IDE veya derleme oluşturulduğunda derleme Bağlayıcısı (al. exe) tarafından ayarlanır. @No__t_0 özniteliği, derlemenin birden çok kopyasının birlikte kullanılıp kullanılamayacağını belirtir.

Aşağıdaki tabloda kimlik öznitelikleri gösterilmektedir.

|Öznitelik|Amaç|
|---------------|-------------|
|<xref:System.Reflection.AssemblyName>|Bir derlemenin kimliğini tam olarak açıklar.|
|<xref:System.Reflection.AssemblyVersionAttribute>|Bir derlemenin sürümünü belirtir.|
|<xref:System.Reflection.AssemblyCultureAttribute>|Derlemenin desteklediği kültürü belirtir.|
|<xref:System.Reflection.AssemblyFlagsAttribute>|Bir derlemenin aynı bilgisayarda, aynı işlemde veya aynı uygulama etki alanında yan yana yürütmeyi destekleyip desteklemediğini belirtir.|

### <a name="informational-attributes"></a>Bilgilendirici öznitelikler

Bir derlemeye ek şirket veya ürün bilgileri sağlamak için bilgilendirici öznitelikleri kullanabilirsiniz. Aşağıdaki tabloda <xref:System.Reflection?displayProperty=nameWithType> ad alanında tanımlanan bilgilendirici öznitelikler gösterilmektedir.

|Öznitelik|Amaç|
|---------------|-------------|
|<xref:System.Reflection.AssemblyProductAttribute>|Bir derleme bildirimi için bir ürün adı belirten özel bir özniteliği tanımlar.|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|Bir derleme bildirimi için ticari marka belirten özel bir özniteliği tanımlar.|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|Bir derleme bildirimi için bilgilendirici bir sürüm belirten özel bir özniteliği tanımlar.|
|<xref:System.Reflection.AssemblyCompanyAttribute>|Bir derleme bildirimi için bir şirket adı belirten özel bir özniteliği tanımlar.|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|Bir derleme bildirimi için bir telif hakkı belirten özel bir özniteliği tanımlar.|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|Derleyiciye Win32 dosya sürümü kaynağı için belirli bir sürüm numarası kullanmasını söyler.|
|<xref:System.CLSCompliantAttribute>|Derlemenin ortak dil belirtimi (CLS) ile uyumlu olup olmadığını gösterir.|

### <a name="assembly-manifest-attributes"></a>Bütünleştirilmiş kod bildirim öznitelikleri

Derleme bildiriminde bilgi sağlamak için bütünleştirilmiş kod bildirim özniteliklerini kullanabilirsiniz. Buna Başlık, açıklama, varsayılan diğer ad ve yapılandırma dahildir. Aşağıdaki tabloda <xref:System.Reflection?displayProperty=nameWithType> ad alanında tanımlanan derleme bildirimi öznitelikleri gösterilmektedir.

|Öznitelik|Amaç|
|---------------|-------------|
|<xref:System.Reflection.AssemblyTitleAttribute>|Bir derleme bildirimi için derleme başlığını belirten özel bir özniteliği tanımlar.|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|Bir derleme bildirimi için derleme açıklamasını belirten özel bir özniteliği tanımlar.|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|Derleme bildirimi için bir derleme yapılandırması (perakende veya hata ayıklama) belirten özel bir öznitelik tanımlar.|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|Bir derleme bildirimi için kolay bir varsayılan diğer ad tanımlar|

## <a name="Obsolete"></a>Kullanımdan kaldırılmış öznitelik

@No__t_0 özniteliği, bir program varlığını artık kullanım için önerilmeyen bir şekilde işaretler. Kullanımdan kalktı olarak işaretlenen bir varlığın her kullanımı, özniteliğin nasıl yapılandırıldığına bağlı olarak bir uyarı veya hata oluşturur. Örneğin:

```vb
<System.Obsolete("use class B")>
Class A
    Sub Method()
    End Sub
End Class

Class B
    <System.Obsolete("use NewMethod", True)>
    Sub OldMethod()
    End Sub

    Sub NewMethod()
    End Sub
End Class
```

Bu örnekte `Obsolete` özniteliği sınıf `A` ve yönteme `B.OldMethod` uygulanır. @No__t_0 uygulanan öznitelik oluşturucusunun ikinci bağımsız değişkeni `true` olarak ayarlandığı için, bu yöntem bir derleyici hatasına neden olur, ancak sınıf `A` kullanılması yalnızca bir uyarı oluşturur. Ancak `B.NewMethod` çağırmak, hiçbir uyarı veya hata üretir.

Öznitelik oluşturucusuna ilk bağımsız değişken olarak girilen dize, uyarının veya hatanın bir parçası olarak görüntülenir. Örneğin, önceki tanımlarla birlikte kullandığınızda, aşağıdaki kod iki uyarı ve bir hata oluşturur:

```vb
' Generates 2 warnings:
' Dim a As New A
' Generate no errors or warnings:

Dim b As New B
b.NewMethod()

' Generates an error, terminating compilation:
' b.OldMethod()
```

Sınıf `A` için iki uyarı oluşturulur: biri sınıf başvurusunun bildirimi ve diğeri sınıf oluşturucusu içindir.

@No__t_0 özniteliği bağımsız değişkenler olmadan kullanılabilir, ancak öğenin neden kullanımdan kalkdığına ve bunun yerine ne tür bir açıklama dahil edilmesi önerilir.

@No__t_0 özniteliği tek kullanım özniteliğidir ve özniteliklere izin veren herhangi bir varlığa uygulanabilir. `Obsolete`, <xref:System.ObsoleteAttribute> için bir diğer addır.

## <a name="Conditional"></a>Koşullu öznitelik

@No__t_0 özniteliği, bir yöntemi ön işleme tanımlayıcısına bağımlı hale getirir. @No__t_0 özniteliği <xref:System.Diagnostics.ConditionalAttribute> için bir diğer addır ve bir yönteme veya öznitelik sınıfına uygulanabilir.

Bu örnekte, programa özgü tanılama bilgilerinin görüntülenmesini etkinleştirmek veya devre dışı bırakmak için bir yönteme `Conditional` uygulanır:

```vb
#Const TRACE_ON = True
Imports System
Imports System.Diagnostics
Module TestConditionalAttribute
    Public Class Trace
        <Conditional("TRACE_ON")>
        Public Shared Sub Msg(ByVal msg As String)
            Console.WriteLine(msg)
        End Sub

    End Class

    Sub Main()
        Trace.Msg("Now in Main...")
        Console.WriteLine("Done.")
    End Sub
End Module
```

@No__t_0 tanımlayıcı tanımlanmamışsa, izleme çıktısı görüntülenmez.

@No__t_0 özniteliği genellikle hata ayıklama derlemeleri için izleme ve günlüğe kaydetme özelliklerini etkinleştirmek üzere `DEBUG` tanımlayıcısı ile kullanılır, ancak bunun gibi sürüm yapılarında desteklenmez:

```vb
<Conditional("DEBUG")>
Shared Sub DebugMethod()

End Sub
```

Koşullu olarak işaretlenen bir yöntem çağrıldığında, belirtilen ön işleme simgesinin varlığı veya yokluğu, çağrının eklenip eklenmeyeceğini veya atlanmadığını belirler. Sembol tanımlanmışsa, çağrı dahil edilir; Aksi takdirde, çağrı atlanır. @No__t_0 kullanmak, bir temizleyici, daha zarif ve `#if…#endif` bloklar içindeki yöntemlere benzer bir diğer hataya açık bir alternatiftir:

```vb
#If DEBUG Then
    Sub ConditionalMethod()
    End Sub
#End If
```

Koşullu Yöntem bir sınıf veya yapı bildiriminde bir yöntem olmalıdır ve dönüş değeri içermemelidir.

### <a name="using-multiple-identifiers"></a>Birden çok tanımlayıcı kullanma

Bir yöntemde birden çok `Conditional` özniteliği varsa, koşullu simgelerden en az biri tanımlanmışsa yönteme bir çağrı dahil edilir (başka bir deyişle, semboller OR işleci kullanılarak mantıksal olarak birbirlerine bağlanır). Bu örnekte, `A` ya da `B` varlığı bir yöntem çağrısına neden olur:

```vb
<Conditional("A"), Conditional("B")>
Shared Sub DoIfAorB()

End Sub
```

VE işlecini kullanarak sembolleri mantıksal olarak bağlama etkisini elde etmek için, seri koşullu yöntemleri tanımlayabilirsiniz. Örneğin, aşağıdaki ikinci yöntem yalnızca `A` ve `B` tanımlanmışsa yürütülür:

```vb
<Conditional("A")>
Shared Sub DoIfA()
    DoIfAandB()
End Sub

<Conditional("B")>
Shared Sub DoIfAandB()
    ' Code to execute when both A and B are defined...
End Sub
```

### <a name="using-conditional-with-attribute-classes"></a>Öznitelik sınıfları ile koşullu kullanma

@No__t_0 özniteliği bir öznitelik sınıfı tanımına da uygulanabilir. Bu örnekte, özel öznitelik `Documentation` yalnızca hata ayıklama tanımlanmışsa meta verilere bilgi ekler.

```vb
<Conditional("DEBUG")>
Public Class Documentation
    Inherits System.Attribute
    Private text As String
    Sub New(ByVal doc_text As String)
        text = doc_text
    End Sub
End Class

Class SampleClass
    ' This attribute will only be included if DEBUG is defined.
    <Documentation("This method displays an integer.")>
    Shared Sub DoWork(ByVal i As Integer)
        System.Console.WriteLine(i)
    End Sub
End Class
```

## <a name="CallerInfo"></a>Arayan bilgileri öznitelikleri

Arayan Bilgisi özniteliklerini kullanarak bir yöntemin arayanı hakkında bilgi edinebilirsiniz. Kaynak kodun dosya yolunu, kaynak kodundaki satır numarasını ve arayanın üye adını elde edebilirsiniz.

Üye çağıran bilgilerini almak için, isteğe bağlı parametrelere uygulanan öznitelikleri kullanırsınız. Her isteğe bağlı parametre varsayılan bir değer belirtir. Aşağıdaki tabloda <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> ad alanında tanımlanan çağıran bilgi öznitelikleri listelenmektedir:

|Öznitelik|Açıklama|Tür|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Kaynak dosyasının arayanı içeren tam yolu. Bu, derleme zamanının yoludur.|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Yöntemin çağrıldığı kaynak dosyadaki satır numarası.|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Çağıranın Yöntem adı veya özellik adı. Daha fazla bilgi için bkz. [arayan bilgileri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).|`String`|

Arayan bilgileri öznitelikleri hakkında daha fazla bilgi için bkz. [arayan bilgileri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).

## <a name="VB"></a>Visual Basic öznitelikleri

Aşağıdaki tablo Visual Basic özgü öznitelikleri listeler.

|Öznitelik|Amaç|
|---------------|-------------|
|<xref:Microsoft.VisualBasic.ComClassAttribute>|Derleyicinin sınıfın bir COM nesnesi olarak kullanıma sunulduğunu belirtir.|
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute>|Modül üyelerine yalnızca modül için gereken nitelik kullanılarak erişilmesine izin verir.|
|<xref:Microsoft.VisualBasic.VBFixedStringAttribute>|Dosya girişi ve çıkış işlevleriyle kullanılmak üzere bir yapıda sabit uzunluklu dizenin boyutunu belirtir.|
|<xref:Microsoft.VisualBasic.VBFixedArrayAttribute>|Dosya girişi ve çıkış işlevleriyle kullanılmak üzere bir yapıda sabit bir dizinin boyutunu belirtir.|

### <a name="comclassattribute"></a>COMClassAttribute

Visual Basic COM bileşenleri oluşturma işlemini basitleştirmek için `COMClassAttribute` kullanın. COM nesneleri .NET Framework derlemelerinden oldukça farklıdır ve `COMClassAttribute` olmadan Visual Basic bir COM nesnesi oluşturmak için birkaç adımı izlemeniz gerekir. @No__t_0 ile işaretlenmiş sınıflar için, derleyici bu adımların çoğunu otomatik olarak gerçekleştirir.

### <a name="hidemodulenameattribute"></a>HideModuleNameAttribute

Modül üyelerine yalnızca modül için gereken nitelik kullanılarak erişilmesine izin vermek için `HideModuleNameAttribute` kullanın.

### <a name="vbfixedstringattribute"></a>VBFixedStringAttribute

Visual Basic sabit uzunluklu bir dize oluşturmaya zorlamak için `VBFixedStringAttribute` kullanın. Dizeler varsayılan olarak değişken uzunluktadır ve bu öznitelik, dizeleri dosyalara depolarken yararlı olur. Aşağıdaki kod bunu gösterir:

```vb
Structure Worker
    ' The runtime uses VBFixedString to determine
    ' if the field should be written out as a fixed size.
    <VBFixedString(10)> Public LastName As String
    <VBFixedString(7)> Public Title As String
    <VBFixedString(2)> Public Rank As String
End Structure
```

### <a name="vbfixedarrayattribute"></a>VBFixedArrayAttribute

Boyut olarak düzeltilen dizileri bildirmek için `VBFixedArrayAttribute` kullanın. Visual Basic dizeleri gibi diziler, varsayılan olarak değişken uzunluktadır. Bu öznitelik, dosyalara veri serileştirilirken veya verileri yazarken faydalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Visual Basic programlama kılavuzu](../../../../visual-basic/programming-guide/index.md)
- [Öznitelikler](../../../../standard/attributes/index.md)
- [Yansıma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [Yansıma kullanarak özniteliklere erişme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
