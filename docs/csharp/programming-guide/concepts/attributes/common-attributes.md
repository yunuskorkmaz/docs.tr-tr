---
title: Ortak Öznitelikler (C#)
ms.date: 07/20/2015
ms.assetid: 785a0526-6c0e-4599-8c61-ccdc88dd9965
ms.openlocfilehash: 7988dad410c6e51869ec9d7e40d94e874443a5f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399758"
---
# <a name="common-attributes-c"></a>Ortak Öznitelikler (C#)
Bu konu, C# programlarında en sık kullanılan öznitelikleri açıklar.  
  
- [Genel Özellikler](#Global)  
  
- [Eski Öznitelik](#Obsolete)  
  
- [Koşullu Öznitelik](#Conditional)  
  
- [Arayan Bilgi Öznitelikleri](#CallerInfo)  
  
## <a name="Global"></a>Genel Özellikler  
 Özniteliklerin çoğu sınıflar veya yöntemler gibi belirli dil öğelerine uygulanır; ancak, bazı öznitelikler geneldir— tüm derleme veya modül için geçerlidir. Örneğin, <xref:System.Reflection.AssemblyVersionAttribute> öznitelik sürüm bilgilerini aşağıdaki gibi bir derlemeye yerleştirmek için kullanılabilir:  
  
```csharp  
[assembly: AssemblyVersion("1.0.0.0")]  
```  
  
 Genel öznitelikler kaynak kodunda herhangi `using` bir üst düzey yönergeden sonra ve herhangi bir tür, modül veya ad alanı bildirimlerinden önce görünür. Genel öznitelikler birden çok kaynak dosyada görünebilir, ancak dosyaların tek bir derleme geçişinde derlenmiş olması gerekir. C# projelerinde, genel öznitelikler AssemblyInfo.cs dosyasına konur.  
  
 Derleme öznitelikleri, derleme hakkında bilgi sağlayan değerlerdir. Aşağıdaki kategorilere ayrılırlar:  
  
- Montaj kimlik öznitelikleri  
  
- Bilgilendirme özellikleri  
  
- Derleme bildirim öznitelikleri  
  
### <a name="assembly-identity-attributes"></a>Montaj Kimlik Öznitelikleri  
 Üç öznitelik (varsa güçlü bir adla) bir derlemenin kimliğini belirler: ad, sürüm ve kültür. Bu öznitelikler derlemenin tam adını oluşturur ve kodda başvuru yaptığınızda gereklidir. Öznitelikleri kullanarak derlemenin sürümünü ve kültürünü ayarlayabilirsiniz. Ancak, ad değeri derleyici tarafından ayarlanır, Assembly Information [Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box)Visual Studio IDE , veya Derleme Bağlayıcı (Al.exe) derleme bildirimi içeren dosyaya dayalı oluşturulur. Öznitelik, <xref:System.Reflection.AssemblyFlagsAttribute> derlemenin birden çok kopyasının bir arada bulunup bulunamayacağını belirtir.  
  
 Aşağıdaki tablo kimlik özniteliklerini gösterir.  
  
|Öznitelik|Amaç|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|Bir derlemenin kimliğini tam olarak açıklar.|  
|<xref:System.Reflection.AssemblyVersionAttribute>|Derlemenin sürümünü belirtir.|  
|<xref:System.Reflection.AssemblyCultureAttribute>|Derlemenin hangi kültürü desteklediğini belirtir.|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|Derlemenin aynı bilgisayarda, aynı işlemde veya aynı uygulama etki alanında yan yana yürütmeyi destekleyip desteklemediğini belirtir.|  
  
### <a name="informational-attributes"></a>Bilgi Özellikleri  
 Bir derleme için ek şirket veya ürün bilgileri sağlamak için bilgi özniteliklerini kullanabilirsiniz. Aşağıdaki tabloda <xref:System.Reflection?displayProperty=nameWithType> ad alanında tanımlanan bilgi öznitelikleri gösterilmektedir.  
  
|Öznitelik|Amaç|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute>|Derleme bildirimi için bir ürün adı belirten özel bir öznitelik tanımlar.|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|Derleme bildirimi için bir ticari marka belirten özel bir öznitelik tanımlar.|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|Derleme bildirimi için bir bilgi sürümü belirten özel bir öznitelik tanımlar.|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|Bir derleme bildirimi için şirket adını belirten özel bir öznitelik tanımlar.|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|Derleme bildiriminin telif hakkını belirten özel bir öznitelik tanımlar.|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|Derleyiciye Win32 dosya sürümü kaynağı için belirli bir sürüm numarası kullanmasını bildirir.|  
|<xref:System.CLSCompliantAttribute>|Derlemenin Ortak Dil Belirtimi (CLS) ile uyumlu olup olmadığını gösterir.|  
  
### <a name="assembly-manifest-attributes"></a>Derleme Bildirimi Öznitelikleri  
 Derleme bildiriminde bilgi sağlamak için derleme bildirimi özniteliklerini kullanabilirsiniz. Bu başlık, açıklama, varsayılan takma ad ve yapılandırma içerir. Aşağıdaki tablo, ad alanında tanımlanan <xref:System.Reflection?displayProperty=nameWithType> derleme bildirimi özniteliklerini gösterir.  
  
|Öznitelik|Amaç|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|Derleme bildirimi için derleme başlığı belirten özel bir öznitelik tanımlar.|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|Derleme bildirimi için derleme açıklaması belirten özel bir öznitelik tanımlar.|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|Derleme bildirimi için derleme yapılandırması (perakende veya hata ayıklama gibi) belirten özel bir öznitelik tanımlar.|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|Derleme bildirimi için uygun bir varsayılan takma ad tanımlar|  
  
## <a name="Obsolete"></a>Eski Öznitelik  
 Öznitelik artık `Obsolete` kullanım için önerilen biri olarak bir program varlık işaretler. Eski işaretlenmiş bir varlığın her kullanımı, özniteliğin nasıl yapılandırıldığına bağlı olarak daha sonra bir uyarı veya hata oluşturur. Örnek:  
  
```csharp  
[System.Obsolete("use class B")]  
class A  
{  
    public void Method() { }  
}  
class B  
{  
    [System.Obsolete("use NewMethod", true)]  
    public void OldMethod() { }  
    public void NewMethod() { }  
}  
```  
  
 Bu örnekte `Obsolete` öznitelik sınıfa `A` ve `B.OldMethod`yönteme uygulanır. Öznitelik oluşturucu uygulanan ikinci bağımsız `B.OldMethod` değişken için `true`ayarlanmış olduğundan, bu yöntem derleyici hatasına neden olurken, sınıf `A` kullanarak sadece bir uyarı üretecektir. Ancak `B.NewMethod`arama, hiçbir uyarı veya hata üretir.  
  
 Oluşturucuatörü atfetmek için ilk bağımsız değişken olarak sağlanan dize uyarı veya hatanın bir parçası olarak görüntülenir. Örneğin, önceki tanımlarla kullandığınızda, aşağıdaki kod iki uyarı ve bir hata oluşturur:  
  
```csharp  
// Generates 2 warnings:  
// A a = new A();  
  
// Generate no errors or warnings:  
B b = new B();  
b.NewMethod();  
  
// Generates an error, terminating compilation:  
// b.OldMethod();  
```  
  
 Sınıf `A` için iki uyarı oluşturulur: biri sınıf başvuru bildirimi için, diğeri sınıf oluşturucusu için.  
  
 Öznitelik `Obsolete` bağımsız değişkenler olmadan kullanılabilir, ancak öğenin neden eski olduğu ve bunun yerine ne kullanılacağı bir açıklama da dahil olmak üzere önerilir.  
  
 Öznitelik `Obsolete` tek kullanımlık bir özniteliktir ve özniteliklere izin veren herhangi bir varlığa uygulanabilir. `Obsolete`<xref:System.ObsoleteAttribute>için bir takma addır.  
  
## <a name="Conditional"></a>Koşullu Öznitelik  
 Öznitelik, `Conditional` bir yöntemin yürütülmesini bir ön işleme tanımlayıcısı bağımlı hale getirir. Öznitelik, `Conditional` <xref:System.Diagnostics.ConditionalAttribute>bir diğer adıdır ve bir yönteme veya öznitelik sınıfına uygulanabilir.  
  
 Bu örnekte, `Conditional` programa özgü tanılama bilgilerinin görüntülenmesini etkinleştirmek veya devre dışı etmek için bir yöntem uygulanır:  
  
```csharp  
#define TRACE_ON  
using System;  
using System.Diagnostics;  
  
public class Trace  
{  
    [Conditional("TRACE_ON")]  
    public static void Msg(string msg)  
    {  
        Console.WriteLine(msg);  
    }  
}  
  
public class ProgramClass  
{  
    static void Main()  
    {  
        Trace.Msg("Now in Main...");  
        Console.WriteLine("Done.");  
    }  
}  
```  
  
 `TRACE_ON` Tanımlayıcı tanımlanmamışsa, hiçbir izleme çıktısı görüntülenmez.  
  
 Öznitelik `Conditional` genellikle hata ayıklama yapılar için izleme ve günlük özelliklerini etkinleştirmek için tanımlayıcı ile `DEBUG` kullanılır, ancak sürüm yapılarda değil, aşağıdaki gibi:  
  
```csharp  
[Conditional("DEBUG")]  
static void DebugMethod()  
{  
}  
```  
  
 Koşullu olarak işaretlenmiş bir yöntem çağrıldığında, belirtilen ön işleme sembolünün varlığı veya yokluğu çağrının dahil edilip edilmeyeceğini veya atlanıp atlanmayacağını belirler. Sembol tanımlanırsa, çağrı dahil edilir; aksi takdirde, arama atlanır. Kullanma, `Conditional` daha temiz, daha zarif ve daha az hata `#if…#endif` yatkın bir alternatif blokların içinde yöntemleri çevreleyen, bu gibi:  
  
```csharp  
#if DEBUG  
    void ConditionalMethod()  
    {  
    }  
#endif  
```  
  
 Koşullu yöntem, bir sınıf veya yapı bildiriminde bir yöntem olmalı ve iade değerine sahip olmamalıdır.  
  
### <a name="using-multiple-identifiers"></a>Birden Çok Tanımlayıcı Kullanma  
 Bir yöntemin `Conditional` birden çok özniteliği varsa, koşullu sembollerden en az biri tanımlanırsa (diğer bir deyişle, semboller OR işleci kullanılarak mantıksal olarak birbirine bağlanır). Bu örnekte, ya `A` da `B` bir yöntem arama neden olur:  
  
```csharp  
[Conditional("A"), Conditional("B")]  
static void DoIfAorB()  
{  
    // ...  
}  
```  
  
 AND işleci kullanarak sembolleri mantıksal olarak bağlama efektini elde etmek için seri koşullu yöntemler tanımlayabilirsiniz. Örneğin, aşağıdaki ikinci yöntem yalnızca her `A` `B` ikisi de ve tanımlanmışsa yürütülecektir:  
  
```csharp
[Conditional("A")]  
static void DoIfA()  
{  
    DoIfAandB();  
}  
  
[Conditional("B")]  
static void DoIfAandB()  
{  
    // Code to execute when both A and B are defined...  
}  
```  
  
### <a name="using-conditional-with-attribute-classes"></a>Öznitelik Sınıfları ile Koşullu Kullanma  
 Öznitelik, `Conditional` öznitelik sınıfı tanımına da uygulanabilir. Bu örnekte, özel `Documentation` öznitelik yalnızca HATA Ayıklama tanımlanırsa meta verilere bilgi ekler.  
  
```csharp  
[Conditional("DEBUG")]  
public class Documentation : System.Attribute  
{  
    string text;  
  
    public Documentation(string text)  
    {  
        this.text = text;  
    }  
}  
  
class SampleClass  
{  
    // This attribute will only be included if DEBUG is defined.  
    [Documentation("This method displays an integer.")]  
    static void DoWork(int i)  
    {  
        System.Console.WriteLine(i.ToString());  
    }  
}  
```  
  
## <a name="CallerInfo"></a>Arayan Bilgi Öznitelikleri  
 Arayan Bilgisi özniteliklerini kullanarak bir yöntemin arayanı hakkında bilgi edinebilirsiniz. Kaynak kodun dosya yolunu, kaynak kodundaki satır numarasını ve arayanın üye adını alabilirsiniz.  
  
 Üye arayan bilgilerini elde etmek için isteğe bağlı parametrelere uygulanan öznitelikleri kullanırsınız. Her isteğe bağlı parametre varsayılan değer belirtir. Aşağıdaki <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> tabloda, ad alanında tanımlanan Arayan Bilgileri öznitelikleri listelenir:  
  
|Öznitelik|Açıklama|Tür|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Kaynak dosyasının arayanı içeren tam yolu. Bu derleme zamanda yoldur.|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Yöntemin çağrıldığı kaynak dosyadaki satır numarası.|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Arayanın yöntem adı veya özellik adı. Daha fazla bilgi için [Bkz. Arayan Bilgileri (C#)](../caller-information.md).|`String`|  
  
 Arayan Bilgileri öznitelikleri hakkında daha fazla bilgi [için, Bkz. Arayan Bilgileri (C#)](../caller-information.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection>
- <xref:System.Attribute>
- [C# Programlama Kılavuzu](../../index.md)
- [Öznitelikler](../../../../standard/attributes/index.md)
- [Yansıma (C#)](../reflection.md)
- [Yansıma (C#) kullanarak Özniteliklere Erişim](./accessing-attributes-by-using-reflection.md)
