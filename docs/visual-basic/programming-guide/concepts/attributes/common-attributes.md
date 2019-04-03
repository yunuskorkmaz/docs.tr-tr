---
title: Ortak öznitelikler (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 11fe4894-1bf9-4525-a36b-cddcd3a5d22b
ms.openlocfilehash: e001c9a637d2e5e34e77158704e4ad81d6973a50
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834554"
---
# <a name="common-attributes-visual-basic"></a>Ortak öznitelikler (Visual Basic)
Bu konuda, Visual Basic programlarında en çok kullanılan öznitelikler açıklanmaktadır.  
  
-   [Genel Öznitelikler](#Global)  
  
-   [Geçersiz öznitelik](#Obsolete)  
  
-   [Conditional özniteliği](#Conditional)  
  
-   [Arayan bilgileri öznitelikleri](#CallerInfo)  
  
-   [Visual Basic öznitelikleri](#VB)  
  
## <a name="Global"></a> Genel Öznitelikler  
 Çoğu öznitelik sınıfları veya yöntemleri gibi belirli dil öğelerini uygulanır; Ancak, bazı öznitelikler genel — bir tüm derleme veya modül için geçerlidir. Örneğin, <xref:System.Reflection.AssemblyVersionAttribute> özniteliği, böyle bir derleme içinde sürüm bilgileri ekleme için kullanılabilir:  
  
```vb  
<Assembly: AssemblyVersion("1.0.0.0")>  
```  
  
 Genel Öznitelikler görünen kaynak kodunda herhangi sonra en üst düzey `Imports` deyimleri ve herhangi bir tür, modül veya ad alanı bildirimleri önce. Genel Öznitelikler birden çok kaynak dosyalarında görünebilir, ancak dosyalar tek bir derleme pass derlenmelidir. Visual Basic projeleri için genel özniteliklerle (Visual Studio'da bir proje oluşturduğunuzda, dosyayı otomatik olarak oluşturulur) AssemblyInfo.vb dosyasında genellikle yerleştirin.  
  
 Derleme özniteliklerinin bir derlemeyle ilgili bilgi sağlayan değerlerdir. Bunlar, aşağıdaki kategorilere ayrılır:  
  
-   Derleme kimliği öznitelikleri  
  
-   Bilgilendirme özniteliklerini  
  
-   Derleme bildirimi öznitelikleri  
  
### <a name="assembly-identity-attributes"></a>Derleme kimliği öznitelikleri  
 Üç öznitelikler (katı bir adla, eğer varsa) bir derlemenin kimliğini belirler: ad, sürüm ve kültür. Bu öznitelikler, bütünleştirilmiş kodun tam adı oluşturur ve kodda başvurduğunuzda gereklidir. Bir derlemenin sürüm ve kültür öznitelikleri kullanarak ayarlayabilirsiniz. Ancak, Visual Studio IDE'de derleyici tarafından adı değeri ayarlanır [derleme bilgileri iletişim kutusu](/visualstudio/ide/reference/assembly-information-dialog-box), veya Assembly Linker (Al.exe) derleme oluşturulduğunda derleme bildirimi içeren dosyada. <xref:System.Reflection.AssemblyFlagsAttribute> Özniteliği, derlemenin birden fazla kopyası bulunabilir olup olmadığını belirtir.  
  
 Aşağıdaki tabloda, kimlik öznitelikleri gösterir.  
  
|Öznitelik|Amaç|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|Tam olarak bir derleme kimliğini açıklar.|  
|<xref:System.Reflection.AssemblyVersionAttribute>|Bir derleme sürümünü belirtir.|  
|<xref:System.Reflection.AssemblyCultureAttribute>|Bu derlemenin desteklediği kültür belirtir.|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|Bir derlemeyi aynı işlemde ya da aynı uygulama etki alanında aynı bilgisayarda yan yana yürütme destekleyip desteklemediğini belirtir.|  
  
### <a name="informational-attributes"></a>Bilgilendirme özniteliklerini  
 Diğer şirket ya da bir derleme için ürün bilgi sağlamak için bilgilendirme özniteliklerini kullanabilirsiniz. Aşağıdaki tabloda tanımlanan bilgilendirme özniteliklerini gösterir <xref:System.Reflection?displayProperty=nameWithType> ad alanı.  
  
|Öznitelik|Amaç|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute>|Bir derleme bildirimi için ürün adını belirten özel bir öznitelik tanımlar.|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|Bir derleme bildirimi için bir ticari marka belirten özel bir öznitelik tanımlar.|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|Bir derleme bildirimi için Bilgilendirme sürümü belirten özel bir öznitelik tanımlar.|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|Bir derleme bildirimi için bir şirket adı belirten özel bir öznitelik tanımlar.|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|Bir derleme bildirimi için telif hakkı belirten özel bir öznitelik tanımlar.|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|Belirli bir sürüm numarasını için Win32 dosya sürüm kaynağının kullanılacağını derleyiciye.|  
|<xref:System.CLSCompliantAttribute>|Derleme ortak dil belirtimi (CLS) ile uyumlu olup olmadığını belirtir.|  
  
### <a name="assembly-manifest-attributes"></a>Derleme bildirimi öznitelikleri  
 Derleme bildirimi bilgilerini sağlamak için derleme bildirimi özniteliklerini kullanabilirsiniz. Bu başlık, açıklama, varsayılan diğer ad ve yapılandırması içerir. Aşağıdaki tabloda tanımlanan derleme bildirimi öznitelikleri gösterir <xref:System.Reflection?displayProperty=nameWithType> ad alanı.  
  
|Öznitelik|Amaç|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|Bir derleme bildirimi derleme başlığını belirtir, özel bir öznitelik tanımlar.|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|Bir derleme bildirimi için bir derleme tanımı belirten özel bir öznitelik tanımlar.|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|Bir derleme yapılandırmasını (örneğin, perakende veya hata ayıklama) belirten bir özel özniteliği için bir derleme bildirimi tanımlar.|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|Bir derleme bildirimi bir kolay varsayılan ad tanımlar|  
  
## <a name="Obsolete"></a> Geçersiz öznitelik  
 `Obsolete` Özniteliği bir program varlık, artık kullanılması olarak işaretler. Artık kullanılmıyor olarak işaretlendiğinden bir varlığın her kullanımdan sonra bir uyarı veya öznitelik nasıl yapılandırıldığına bağlı olarak, bir hata oluşturur. Örneğin:  
  
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
  
 Bu örnekte `Obsolete` öznitelik sınıfına uygulanan `A` ve yönteme `B.OldMethod`. Öznitelik oluşturucusunda ikinci bağımsız değişkeni için uyguladığı `B.OldMethod` ayarlanır `true`, sınıfını kullanarak ise bu yöntem bir derleyici hatasına neden olur `A` bir uyarı yalnızca üretim olur. Çağırma `B.NewMethod`, ancak hiçbir uyarı veya hata üretir.  
  
 Uyarı veya hata bir parçası olarak öznitelik yapıcısına ilk bağımsız değişken olarak sağlanan dizesi görüntülenir. Örneğin, önceki tanımları ile kullandığınızda, aşağıdaki kod iki uyarıları ve bir hata oluşturur:  
  
```vb  
' Generates 2 warnings:  
' Dim a As New A  
' Generate no errors or warnings:  
  
Dim b As New B  
b.NewMethod()  
  
' Generates an error, terminating compilation:  
' b.OldMethod()  
```  
  
 Sınıf için iki uyarı `A` üretilir: sınıf başvurusu bildirimi için diğeri için sınıf oluşturucu.  
  
 `Obsolete` Öznitelik bağımsız değişkeni olmadan kullanılabilir, ancak öğe neden dahil olmak üzere bir açıklama kullanılmıyor ve ne kullanmanız önerilir.  
  
 `Obsolete` Özniteliği tek kullanımlık bir özniteliktir ve öznitelikleri izin veren herhangi bir varlık için uygulanabilir. `Obsolete` için bir diğer addır <xref:System.ObsoleteAttribute>.  
  
## <a name="Conditional"></a> Conditional özniteliği  
 `Conditional` Özniteliği bir yönteminin yürütülmesi bir ön işleme tanımlayıcısı bağımlı yapar. `Conditional` Özniteliği için bir diğer ad, <xref:System.Diagnostics.ConditionalAttribute>ve bir yöntem veya bir öznitelik sınıfı için uygulanabilir.  
  
 Bu örnekte, `Conditional` etkinleştirmek veya program özel tanılama bilgilerinin görüntülenmesini devre dışı bırakmak için bir yönteme uygulanır:  
  
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
  
 Varsa `TRACE_ON` tanımlayıcı tanımlı değil, hiçbir İzleme çıktısı görüntülenir.  
  
 `Conditional` Özniteliği ile kullanılan genellikle `DEBUG` izleme ve hata ayıklama derlemeleri ancak içinde olmayan sürüm yapıları, günlük özellikleri etkinleştirmek için tanımlayıcı şöyle:  
  
```vb  
<Conditional("DEBUG")>   
Shared Sub DebugMethod()  
  
End Sub  
```  
  
 Koşullu olarak işaretlenmiş bir yöntem çağrıldığında, varlığı veya yokluğu belirtilen ön işleme sembolünün çağrı dahil mi, yoksa atlanmış mı olduğunu belirler. Simge tanımlanmışsa çağrısı bulunur; Aksi takdirde, çağrı atlanır. Kullanarak `Conditional` bir olmamasına içinde yöntemleri kapsayan daha zarif ve hataya daha az seçenek `#if…#endif` blokları, şöyle:  
  
```vb  
#If DEBUG Then  
    Sub ConditionalMethod()  
    End Sub  
#End If  
```  
  
 Bir koşullu metot bir class veya struct bildiriminde bir yöntem olmalı ve bir dönüş değeri olmamalıdır.  
  
### <a name="using-multiple-identifiers"></a>Birden çok tanımlayıcılarla  
 Bir yöntemin birden fazla varsa `Conditional` öznitelikleri, yönteme bir çağrı ise dahil en az bir koşullu simgeleri tanımlanır (diğer bir deyişle, simgeler mantıksal veya işlecini kullanarak birbirine bağlıdır). Bu örnekte, ya da varlığını `A` veya `B` bir yöntem çağrısında neden olur:  
  
```vb  
<Conditional("A"), Conditional("B")>   
Shared Sub DoIfAorB()  
  
End Sub  
```  
  
 Mantıksal ve işlecini kullanarak simgeleri bağlama etkiyi elde etmek için seri koşullu yöntemler tanımlayabilirsiniz. Örneğin, ikinci yöntem aşağıdaki yalnızca her iki yürütecek `A` ve `B` tanımlanır:  
  
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
  
### <a name="using-conditional-with-attribute-classes"></a>Koşullu öznitelik sınıfları ile kullanma  
 `Conditional` Özniteliği bir öznitelik sınıf tanımına da uygulanabilir. Bu örnekte, özel öznitelik `Documentation` yalnızca hata ayıklama tanımlanmışsa meta verilere bilgi ekleyeceksiniz.  
  
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
  
## <a name="CallerInfo"></a> Arayan bilgileri öznitelikleri  
 Arayan Bilgisi özniteliklerini kullanarak bir yöntemin arayanı hakkında bilgi edinebilirsiniz. Kaynak kodu dosyasının yolu, satır numarası kaynak kodu ve arayanın üye adını alabilirsiniz.  
  
 Üye arayan bilgileri elde etmek için isteğe bağlı parametrelere uygulanan öznitelikler kullanın. İsteğe bağlı her parametre varsayılan bir değer belirtir. Aşağıdaki tabloda tanımlanan arayan bilgisi öznitelikleri listelenmektedir <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> ad alanı:  
  
|Öznitelik|Açıklama|Tür|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Kaynak dosyasının arayanı içeren tam yolu. Derleme zamanında yolu budur.|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Yöntemin çağrıldığı kaynak dosyadaki satır numarası.|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Yöntem adı veya çağıranın özelliğinin adı. Daha fazla bilgi için [arayan bilgileri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).|`String`|  
  
 Arayan bilgisi öznitelikleri hakkında daha fazla bilgi için bkz: [arayan bilgileri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).  
  
## <a name="VB"></a> Visual Basic öznitelikleri  
 Aşağıdaki tabloda, Visual Basic özel özniteliklerini listeler.  
  
|Öznitelik|Amaç|  
|---------------|-------------|  
|<xref:Microsoft.VisualBasic.ComClassAttribute>|Derleyiciye, sınıfı bir COM nesnesi olarak açılmamalıdır gösterir.|  
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute>|Modül üyelerinin yalnızca modül için gerekli nitelik kullanılarak erişilecektir izin verir.|  
|<xref:Microsoft.VisualBasic.VBFixedStringAttribute>|Bir sabit uzunluklu dize boyutu kullanmak için bir yapı ile giriş ve çıkış dosyasını belirtir. işlevleri.|  
|<xref:Microsoft.VisualBasic.VBFixedArrayAttribute>|Sabit bir dizinin boyutu kullanmak için bir yapı ile giriş ve çıkış dosyasını belirtir. işlevleri.|  
  
### <a name="comclassattribute"></a>COMClassAttribute  
 Kullanım `COMClassAttribute` Visual Basic'den COM bileşenleri oluşturma işlemini basitleştirmek için. COM nesneleri, .NET Framework derlemeleri ve olmadan önemli ölçüde farklı `COMClassAttribute`, çeşitli Visual Basic'den COM nesnesi oluşturmak için adımları izlemeniz gerekir. İşaretlenmiş sınıflar için `COMClassAttribute`, derleyici bu adımların birçoğunun otomatik olarak gerçekleştirir.  
  
### <a name="hidemodulenameattribute"></a>HideModuleNameAttribute  
 Kullanım `HideModuleNameAttribute` modülü üyeleri yalnızca modül için gerekli nitelik kullanılarak erişilecek izin vermek için.  
  
### <a name="vbfixedstringattribute"></a>VBFixedStringAttribute  
 Kullanım `VBFixedStringAttribute` sabit uzunluklu bir dize oluşturmak için Visual Basic zorlamak için. Varsayılan olarak, değişken uzunluğu dizelerdir ve bu öznitelik dosyaları dizelere depolarken kullanışlıdır. Aşağıdaki kod bunu göstermektedir:  
  
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
 Kullanım `VBFixedArrayAttribute` sabit boyutludur diziler bildirmek için. Visual Basic dizeleri gibi varsayılan olarak, değişken uzunluğu dizilerdir. Bu öznitelik serileştirilmesi ya da veri dosyalara yazma kullanışlıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Visual Basic programlama kılavuzu](../../../../visual-basic/programming-guide/index.md)
- [Öznitelikler](../../../../standard/attributes/index.md)
- [Yansıma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [(Visual Basic) yansıma kullanarak özniteliklere erişme](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
