---
title: Ortak öznitelikler (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 11fe4894-1bf9-4525-a36b-cddcd3a5d22b
ms.openlocfilehash: 5a91b0aa48a22db4ea7fb56a9c632ff0cb44dce5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644166"
---
# <a name="common-attributes-visual-basic"></a>Ortak öznitelikler (Visual Basic)
Bu konuda, Visual Basic programlarında en yaygın olarak kullanılan öznitelikler açıklanmaktadır.  
  
-   [Genel Öznitelikler](#Global)  
  
-   [Artık kullanılmayan özniteliği](#Obsolete)  
  
-   [Koşul özniteliği](#Conditional)  
  
-   [Arayan bilgileri öznitelikleri](#CallerInfo)  
  
-   [Visual Basic öznitelikleri](#VB)  
  
##  <a name="Global"></a> Genel Öznitelikler  
 Çoğu öznitelik sınıfları veya yöntemleri gibi belirli bir dil öğeleri uygulanır; Ancak, bazı öznitelikler genel — tüm derleme veya modülü için geçerlidir. Örneğin, <xref:System.Reflection.AssemblyVersionAttribute> özniteliği, böyle bir bütünleştirilmiş sürüm bilgilerini eklemek için kullanılabilir:  
  
```vb  
<Assembly: AssemblyVersion("1.0.0.0")>  
```  
  
 Genel Öznitelikler görünen kaynak kodunda herhangi sonra en üst düzey `Imports` deyimleri ve herhangi bir tür, modül veya ad alanı bildirimleri öncesinde. Genel Öznitelikler birden çok kaynak dosyalarında görünebilir, ancak dosyaları tek bir derleme geçişinde derlenmiş olmalıdır. Visual Basic projeleri için genel özniteliklerle (Visual Studio'da bir proje oluşturduğunuzda dosyası otomatik olarak oluşturulur) AssemblyInfo.vb dosyasında genellikle yerleştirin.  
  
 Derleme özniteliklerinin bir derleme hakkında bilgi sağlayan değerlerdir. Bunlar aşağıdaki kategorilere ayrılır:  
  
-   Derleme kimlik öznitelikleri  
  
-   Bilgilendirme öznitelikleri  
  
-   Derleme bildirimi öznitelikleri  
  
### <a name="assembly-identity-attributes"></a>Derleme kimlik öznitelikleri  
 Üç özniteliklerle (tanımlayıcı ad, eğer varsa) bir derleme kimliğini belirlemek: ad, sürüm ve kültür. Bu öznitelikler derlemenin tam adını formunu ve kodda başvurduğunuzda gereklidir. Bir derlemenin sürüm ve öznitelikleri kullanarak kültür ayarlayabilirsiniz. Ancak, ad değeri Visual Studio IDE içinde derleyici tarafından ayarlanır [derleme bilgileri iletişim kutusu](/visualstudio/ide/reference/assembly-information-dialog-box), ya da derleme bağlayıcı (derleme oluşturulduğunda Al.exe) derleme bildirimi içeren dosyayı alarak. <xref:System.Reflection.AssemblyFlagsAttribute> Özniteliği, derleme birden çok kopyasını bir arada var olabilen olup olmadığını belirtir.  
  
 Aşağıdaki tabloda kimlik öznitelikleri gösterir.  
  
|Öznitelik|Amaç|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|Tam olarak bir derleme kimliğini açıklar.|  
|<xref:System.Reflection.AssemblyVersionAttribute>|Bir derlemeyi sürümünü belirtir.|  
|<xref:System.Reflection.AssemblyCultureAttribute>|Hangi derleme destekler kültür belirtir.|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|Bir derlemeyi aynı bilgisayardaki aynı işlemde ya da aynı uygulama etki alanında yan yana yürütme destekleyip desteklemediğini belirtir.|  
  
### <a name="informational-attributes"></a>Bilgilendirme öznitelikleri  
 Bilgilendirme öznitelikleri, ek şirket veya bir derleme için ürün bilgi sağlamak için kullanabilirsiniz. Aşağıdaki tabloda tanımlanan bilgilendirme öznitelikleri gösterir <xref:System.Reflection?displayProperty=nameWithType> ad alanı.  
  
|Öznitelik|Amaç|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute>|Derleme bildirimi ürün adını belirtir özel bir öznitelik tanımlar.|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|Derleme bildirimi için bir ticari marka belirtir özel bir öznitelik tanımlar.|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|Derleme bildirimi için bilgilendirici bir sürümünü belirten özel bir öznitelik tanımlar.|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|Derleme bildirimi için bir şirket adı belirtir özel bir öznitelik tanımlar.|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|Derleme bildirimi için telif hakkı belirtir özel bir öznitelik tanımlar.|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|Derleyicinin Win32 dosya sürümü kaynak için belirli bir sürüm numarasını kullanmasını söyler.|  
|<xref:System.CLSCompliantAttribute>|Derleme ortak dil belirtimi (CLS) ile uyumlu olup olmadığını belirtir.|  
  
### <a name="assembly-manifest-attributes"></a>Derleme bildirimi öznitelikleri  
 Derleme bildirimi özniteliklerinin derleme bildirimi bilgi sağlamak için kullanabilirsiniz. Bu başlık, açıklama, varsayılan diğer ad ve yapılandırmayı içerir. Derleme bildirimi öznitelikleri tanımlanan aşağıdaki tabloda gösterilmektedir <xref:System.Reflection?displayProperty=nameWithType> ad alanı.  
  
|Öznitelik|Amaç|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|Derleme bildirimi için bir derleme başlık belirtir özel bir öznitelik tanımlar.|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|Derleme bildirimi derleme açıklamasını belirtir özel bir öznitelik tanımlar.|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|Bir derleme yapılandırmasını (örneğin, tekil veya hata ayıklama) belirten özel bir öznitelik için bir derleme bildirimi tanımlar.|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|Derleme bildirimi için bir kolay varsayılan diğer adı tanımlar|  
  
##  <a name="Obsolete"></a> Artık kullanılmayan özniteliği  
 `Obsolete` Özniteliği bir program varlık artık kullanım için önerilen biri olarak işaretler. Artık kullanılmayan olarak işaretlenmiş bir varlığın her kullanın, daha sonra bir uyarı veya öznitelik nasıl yapılandırıldığına bağlı olarak bir hata oluşturur. Örneğin:  
  
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
  
 Bu örnekte `Obsolete` özniteliği sınıfına uygulanan `A` ve yöntemine `B.OldMethod`. Öznitelik oluşturucunun ikinci bağımsız değişkeni uygulanan çünkü `B.OldMethod` ayarlanır `true`, bu yöntem, sınıfını kullanarak ancak derleyici hatası neden olur `A` bir uyarı yalnızca ürettiği olur. Çağırma `B.NewMethod`, ancak hiçbir uyarı veya hata üretir.  
  
 Öznitelik oluşturucunun ilk bağımsız değişkeni olarak sağlanan dize uyarı veya hata bir parçası olarak görüntülenir. Örneğin, önceki tanımları ile kullandığınızda, aşağıdaki kod iki uyarılar ve bir hata oluşturur:  
  
```vb  
' Generates 2 warnings:  
' Dim a As New A  
' Generate no errors or warnings:  
  
Dim b As New B  
b.NewMethod()  
  
' Generates an error, terminating compilation:  
' b.OldMethod()  
```  
  
 Sınıfı için iki uyarıları `A` oluşturulur: sınıf başvurusu bildirimi için diğeri için sınıf oluşturucu.  
  
 `Obsolete` Öznitelik bağımsız değişkenler olmadan kullanılabilir, ancak neden bir açıklaması da dahil olmak üzere öğe kullanılmıyor ve ne kullanmanız önerilir.  
  
 `Obsolete` Özniteliği bir tek kullanımlık özniteliği ve öznitelikleri veren herhangi bir varlık için uygulanabilir. `Obsolete` bir diğer adı için <xref:System.ObsoleteAttribute>.  
  
##  <a name="Conditional"></a> Koşul özniteliği  
 `Conditional` Özniteliği bir yönteminin yürütülmesi üzerinde önişlem tanımlayıcısını bağımlı yapar. `Conditional` Özniteliktir için diğer ad <xref:System.Diagnostics.ConditionalAttribute>ve bir yöntem veya öznitelik sınıfı için uygulanabilir.  
  
 Bu örnekte, `Conditional` etkinleştirmek veya programa özgü tanı bilgilerini görüntülemeyi devre dışı bırakmak için bir yönteme uygulanır:  
  
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
  
 Varsa `TRACE_ON` tanımlayıcısı tanımlı değil, izleme çıktısı görüntülenir.  
  
 `Conditional` Özniteliği ile kullanılan genellikle `DEBUG` izleme ve hata ayıklama derlemeleri ancak içinde değil yayın derlemeler, günlük özellikleri etkinleştirmek için tanımlayıcı şöyle:  
  
```vb  
<Conditional("DEBUG")>   
Shared Sub DebugMethod()  
  
End Sub  
```  
  
 Koşullu olarak işaretli bir yöntem çağrıldığında, varlığının veya yokluğunun belirtilen önişlem simgenin çağrı dahil atlanmış verilip verilmediğini belirler. Simgenin tanımlanmışsa, çağrı bulunur; Aksi halde çağrı atlanır. Kullanarak `Conditional` bir temizleyici olan yöntemleri içinde kapsayan daha zarif ve hataya daha az alternatif `#if…#endif` blokları, şuna benzer:  
  
```vb  
#If DEBUG Then  
    Sub ConditionalMethod()  
    End Sub  
#End If  
```  
  
 Koşullu bir yöntem sınıfta veya yapı bildiriminde bir yöntem olmalıdır ve bir dönüş değeri olmamalıdır.  
  
### <a name="using-multiple-identifiers"></a>Birden çok tanımlayıcıları kullanma  
 Bir yöntemin birden çok varsa `Conditional` öznitelikleri yöntemine bir çağrı dahil en az bir koşullu simgelerin tanımlanmışsa (diğer bir deyişle, simgeler mantıksal veya işlecini kullanarak birbirine bağlıdır). Bu örnekte, ya da varlığını `A` veya `B` bir yöntem çağrısı neden olur:  
  
```vb  
<Conditional("A"), Conditional("B")>   
Shared Sub DoIfAorB()  
  
End Sub  
```  
  
 Mantıksal ve işlecini kullanarak simgeleri bağlama etkisini elde etmek için seri koşullu yöntemler tanımlayabilirsiniz. Örneğin, aşağıdaki ikinci yöntem yalnızca her iki yürütecek `A` ve `B` tanımlanır:  
  
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
 `Conditional` Özniteliği için öznitelik sınıf tanımını da uygulanabilir. Bu örnekte, özel öznitelik `Documentation` hata ayıklama tanımlanmışsa, yalnızca bilgi meta verileri ekler.  
  
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
  
##  <a name="CallerInfo"></a> Arayan bilgileri öznitelikleri  
 Arayan Bilgisi özniteliklerini kullanarak bir yöntemin arayanı hakkında bilgi edinebilirsiniz. Kaynak kodu dosya yolu, kaynak kodu ve arayan üye adı satır numarasını edinebilirsiniz.  
  
 Üye arayan bilgileri almak için isteğe bağlı parametreler uygulanan öznitelikleri kullanın. Her isteğe bağlı bir parametre varsayılan bir değer belirtir. Aşağıdaki tabloda tanımlanan arayan bilgileri öznitelikleri listeler <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> ad alanı:  
  
|Öznitelik|Açıklama|Tür|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Kaynak dosyasının arayanı içeren tam yolu. Derleme zamanında yolu budur.|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Satır numarası kaynak dosyasındaki yöntemi adı verilir.|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Yöntem adı veya çağıranın özellik adı. Daha fazla bilgi için bkz: [arayan bilgileri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).|`String`|  
  
 Arayan bilgileri öznitelikleri hakkında daha fazla bilgi için bkz: [arayan bilgileri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).  
  
##  <a name="VB"></a> Visual Basic öznitelikleri  
 Aşağıdaki tabloda Visual Basic'e özel öznitelikleri listeler.  
  
|Öznitelik|Amaç|  
|---------------|-------------|  
|<xref:Microsoft.VisualBasic.ComClassAttribute>|Derleyiciye sınıfı bir COM nesnesi olarak açık olduğunu gösterir.|  
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute>|Modül üyelerinin modülü için gerekli nitelik kullanarak erişilmesine olanak tanır.|  
|<xref:Microsoft.VisualBasic.VBFixedStringAttribute>|Giriş ve çıkış dosyası ile kullanmak için bir yapı sabit uzunlukta bir dize boyutunu belirtir işlevleri.|  
|<xref:Microsoft.VisualBasic.VBFixedArrayAttribute>|Giriş ve çıkış dosyası ile kullanmak için bir yapı sabit bir dizi boyutunu belirtir işlevleri.|  
  
### <a name="comclassattribute"></a>COMClassAttribute  
 Kullanım `COMClassAttribute` Visual Basic'den COM bileşenleri oluşturma işlemini basitleştirmek için. COM nesneleri .NET Framework derlemeleri olmadan ve önemli ölçüde farklı `COMClassAttribute`, çeşitli Visual Basic'den COM nesnesi oluşturmak için adımları izlemeniz gerekir. Sınıflar ile işaretlenen için `COMClassAttribute`, derleyici bu adımların otomatik olarak gerçekleştirir.  
  
### <a name="hidemodulenameattribute"></a>HideModuleNameAttribute  
 Kullanım `HideModuleNameAttribute` modülü üyeleri yalnızca modülü için gerekli nitelik kullanarak erişilmesine izin vermek için.  
  
### <a name="vbfixedstringattribute"></a>VBFixedStringAttribute  
 Kullanım `VBFixedStringAttribute` sabit uzunlukta bir dize oluşturmak için Visual Basic zorlamak için. Varsayılan olarak değişken uzunlukta dizelerdir ve bu öznitelik dosyaları dizelere depolarken kullanışlıdır. Aşağıdaki kod bu gösterir:  
  
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
 Kullanım `VBFixedArrayAttribute` sabit boyutludur diziler bildirme. Visual Basic dizeleri gibi varsayılan değişken uzunlukta diziler değildir. Bu öznitelik serileştirmek veya veri dosyaları yazılıyor yararlıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [Visual Basic programlama kılavuzu](../../../../visual-basic/programming-guide/index.md)  
 [Öznitelikler](../../../../standard/attributes/index.md)  
 [Yansıma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [(Visual Basic) yansıma kullanarak özniteliklere erişme](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
