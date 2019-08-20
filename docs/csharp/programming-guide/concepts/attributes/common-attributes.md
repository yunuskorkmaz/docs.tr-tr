---
title: Ortak öznitelikler (C#)
ms.date: 07/20/2015
ms.assetid: 785a0526-6c0e-4599-8c61-ccdc88dd9965
ms.openlocfilehash: 7988dad410c6e51869ec9d7e40d94e874443a5f8
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595466"
---
# <a name="common-attributes-c"></a>Ortak öznitelikler (C#)
Bu konuda, C# programlarda en yaygın olarak kullanılan öznitelikler açıklanmaktadır.  
  
- [Genel öznitelikler](#Global)  
  
- [Kullanımdan kaldırılmış öznitelik](#Obsolete)  
  
- [Koşullu öznitelik](#Conditional)  
  
- [Arayan bilgileri öznitelikleri](#CallerInfo)  
  
## <a name="Global"></a>Genel öznitelikler  
 Çoğu öznitelik sınıflar veya yöntemler gibi belirli dil öğelerine uygulanır; Ancak, bazı öznitelikler geneldir, tüm derleme veya modül için geçerlidir. Örneğin, <xref:System.Reflection.AssemblyVersionAttribute> özniteliği aşağıdaki gibi bir derlemeye sürüm bilgisi eklemek için kullanılabilir:  
  
```csharp  
[assembly: AssemblyVersion("1.0.0.0")]  
```  
  
 Genel öznitelikler, herhangi bir üst düzey `using` yönergelerden sonra ve herhangi bir tür, modül veya ad alanı bildirimlerinden sonra kaynak kodunda görünür. Genel öznitelikler birden çok kaynak dosyasında görünebilir, ancak dosyaların tek bir derleme geçişinde derlenmesi gerekir. C# Projelerde, genel öznitelikler AssemblyInfo.cs dosyasına konur.  
  
 Derleme öznitelikleri, bir derleme hakkında bilgi sağlayan değerlerdir. Bunlar aşağıdaki kategorilere ayrılır:  
  
- Bütünleştirilmiş kod kimliği öznitelikleri  
  
- Bilgilendirici öznitelikler  
  
- Bütünleştirilmiş kod bildirim öznitelikleri  
  
### <a name="assembly-identity-attributes"></a>Bütünleştirilmiş kod kimliği öznitelikleri  
 Üç öznitelik (varsa, güçlü bir ad varsa) bir derlemenin kimliğini belirleme: ad, sürüm ve kültür. Bu öznitelikler, derlemenin tam adını oluşturur ve kodda başvuru yaptığınızda gereklidir. Öznitelikleri kullanarak bir derlemenin sürümünü ve kültürünü ayarlayabilirsiniz. Bununla birlikte, ad değeri derleyici tarafından, derleme [bilgileri Iletişim kutusunda](/visualstudio/ide/reference/assembly-information-dialog-box)VISUAL Studio IDE veya derleme oluşturulduğunda derleme Bağlayıcısı (al. exe) tarafından ayarlanır. <xref:System.Reflection.AssemblyFlagsAttribute> Özniteliği, derlemenin birden çok kopyasının birlikte kullanılıp kullanılamayacağını belirtir.  
  
 Aşağıdaki tabloda kimlik öznitelikleri gösterilmektedir.  
  
|Öznitelik|Amaç|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|Bir derlemenin kimliğini tam olarak açıklar.|  
|<xref:System.Reflection.AssemblyVersionAttribute>|Bir derlemenin sürümünü belirtir.|  
|<xref:System.Reflection.AssemblyCultureAttribute>|Derlemenin desteklediği kültürü belirtir.|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|Bir derlemenin aynı bilgisayarda, aynı işlemde veya aynı uygulama etki alanında yan yana yürütmeyi destekleyip desteklemediğini belirtir.|  
  
### <a name="informational-attributes"></a>Bilgilendirici öznitelikler  
 Bir derlemeye ek şirket veya ürün bilgileri sağlamak için bilgilendirici öznitelikleri kullanabilirsiniz. Aşağıdaki tabloda, <xref:System.Reflection?displayProperty=nameWithType> ad alanında tanımlanan bilgilendirici öznitelikler gösterilmektedir.  
  
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
 Derleme bildiriminde bilgi sağlamak için bütünleştirilmiş kod bildirim özniteliklerini kullanabilirsiniz. Buna Başlık, açıklama, varsayılan diğer ad ve yapılandırma dahildir. Aşağıdaki tabloda, <xref:System.Reflection?displayProperty=nameWithType> ad alanında tanımlanan derleme bildirimi öznitelikleri gösterilmektedir.  
  
|Öznitelik|Amaç|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|Bir derleme bildirimi için derleme başlığını belirten özel bir özniteliği tanımlar.|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|Bir derleme bildirimi için derleme açıklamasını belirten özel bir özniteliği tanımlar.|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|Derleme bildirimi için bir derleme yapılandırması (perakende veya hata ayıklama) belirten özel bir öznitelik tanımlar.|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|Bir derleme bildirimi için kolay bir varsayılan diğer ad tanımlar|  
  
## <a name="Obsolete"></a>Kullanımdan kaldırılmış öznitelik  
 Özniteliği `Obsolete` , bir program varlığını artık kullanım için önerilmeyen bir şekilde işaretler. Kullanımdan kalktı olarak işaretlenen bir varlığın her kullanımı, özniteliğin nasıl yapılandırıldığına bağlı olarak bir uyarı veya hata oluşturur. Örneğin:  
  
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
  
 Bu örnekte, `Obsolete` özniteliği sınıfa `A` ve yöntemine `B.OldMethod`uygulanır. Öğesine `B.OldMethod` uygulanan öznitelik oluşturucusunun ikinci bağımsız değişkeni olarak `true`ayarlandığından, bu yöntem bir derleyici hatasına neden olur, ancak sınıf `A` kullanımı yalnızca bir uyarı oluşturur. Ancak `B.NewMethod`çağırma, hiçbir uyarı veya hata üretir.  
  
 Öznitelik oluşturucusuna ilk bağımsız değişken olarak girilen dize, uyarının veya hatanın bir parçası olarak görüntülenir. Örneğin, önceki tanımlarla birlikte kullandığınızda, aşağıdaki kod iki uyarı ve bir hata oluşturur:  
  
```csharp  
// Generates 2 warnings:  
// A a = new A();  
  
// Generate no errors or warnings:  
B b = new B();  
b.NewMethod();  
  
// Generates an error, terminating compilation:  
// b.OldMethod();  
```  
  
 Sınıf `A` için iki uyarı oluşturulur: biri sınıf başvurusunun bildirimi ve diğeri sınıf oluşturucusu içindir.  
  
 `Obsolete` Öznitelik bağımsız değişkenler olmadan kullanılabilir, ancak öğenin neden kullanımdan kalkdığına ve bunun yerine ne tür bir açıklama dahil edilmesi önerilir.  
  
 `Obsolete` Özniteliği tek kullanım özniteliğidir ve özniteliklere izin veren herhangi bir varlığa uygulanabilir. `Obsolete`, için <xref:System.ObsoleteAttribute>bir diğer addır.  
  
## <a name="Conditional"></a>Koşullu öznitelik  
 `Conditional` Özniteliği bir işlem ön işleme tanımlayıcısına bağımlı bir yöntemin yürütülmesini sağlar. `Conditional` Özniteliği için<xref:System.Diagnostics.ConditionalAttribute>bir diğer addır ve bir yönteme veya öznitelik sınıfına uygulanabilir.  
  
 Bu örnekte, `Conditional` programa özgü tanılama bilgilerinin görüntülenmesini etkinleştirmek veya devre dışı bırakmak için bir yönteme uygulanır:  
  
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
  
 `TRACE_ON` Tanımlayıcı tanımlanmamışsa, hiçbir izleme çıkışı gösterilmez.  
  
 Öznitelik, genellikle hata ayıklama derlemeleri için `DEBUG` izleme ve günlüğe kaydetme özelliklerini etkinleştirmek için tanımlayıcı ile birlikte kullanılır, ancak bunun gibi sürüm yapılarında desteklenmez: `Conditional`  
  
```csharp  
[Conditional("DEBUG")]  
static void DebugMethod()  
{  
}  
```  
  
 Koşullu olarak işaretlenen bir yöntem çağrıldığında, belirtilen ön işleme simgesinin varlığı veya yokluğu, çağrının eklenip eklenmeyeceğini veya atlanmadığını belirler. Sembol tanımlanmışsa, çağrı dahil edilir; Aksi takdirde, çağrı atlanır. Kullanılarak `Conditional` , blokların içindeki yöntemlerin içine yerleştirilmesi `#if…#endif` için aşağıdaki gibi bir temizleyici, daha zarif ve daha az hataya açık bir alternatiftir:  
  
```csharp  
#if DEBUG  
    void ConditionalMethod()  
    {  
    }  
#endif  
```  
  
 Koşullu Yöntem bir sınıf veya yapı bildiriminde bir yöntem olmalıdır ve dönüş değeri içermemelidir.  
  
### <a name="using-multiple-identifiers"></a>Birden çok tanımlayıcı kullanma  
 Bir yöntemin birden çok `Conditional` özniteliği varsa, koşullu simgelerden en az biri tanımlanmışsa yöntemine bir çağrı dahil edilir (başka bir deyişle, semboller or işleci kullanılarak mantıksal olarak birbirlerine bağlanır). Bu örnekte, ya da `A` `B` birinin varlığı bir yöntem çağrısına neden olur:  
  
```csharp  
[Conditional("A"), Conditional("B")]  
static void DoIfAorB()  
{  
    // ...  
}  
```  
  
 VE işlecini kullanarak sembolleri mantıksal olarak bağlama etkisini elde etmek için, seri koşullu yöntemleri tanımlayabilirsiniz. Örneğin, aşağıdaki ikinci yöntem yalnızca `A` ve `B` tanımlanırsa yürütülür:  
  
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
  
### <a name="using-conditional-with-attribute-classes"></a>Öznitelik sınıfları ile koşullu kullanma  
 Öznitelik `Conditional` , öznitelik sınıfı tanımına da uygulanabilir. Bu örnekte, özel öznitelik `Documentation` yalnızca hata ayıklama tanımlanmışsa meta verilere bilgi ekler.  
  
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
  
## <a name="CallerInfo"></a>Arayan bilgileri öznitelikleri  
 Arayan Bilgisi özniteliklerini kullanarak bir yöntemin arayanı hakkında bilgi edinebilirsiniz. Kaynak kodun dosya yolunu, kaynak kodundaki satır numarasını ve arayanın üye adını elde edebilirsiniz.  
  
 Üye çağıran bilgilerini almak için, isteğe bağlı parametrelere uygulanan öznitelikleri kullanırsınız. Her isteğe bağlı parametre varsayılan bir değer belirtir. Aşağıdaki tabloda, <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> ad alanında tanımlanan arayan bilgileri öznitelikleri listelenmektedir:  
  
|Öznitelik|Açıklama|Tür|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Kaynak dosyasının arayanı içeren tam yolu. Bu, derleme zamanının yoludur.|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Yöntemin çağrıldığı kaynak dosyadaki satır numarası.|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Çağıranın Yöntem adı veya özellik adı. Daha fazla bilgi için bkz. [arayan bilgileriC#()](../caller-information.md).|`String`|  
  
 Arayan bilgileri öznitelikleri hakkında daha fazla bilgi için bkz. [arayan bilgileri (C#)](../caller-information.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection>
- <xref:System.Attribute>
- [C# Programlama Kılavuzu](../../index.md)
- [Öznitelikler](../../../../standard/attributes/index.md)
- [Yansıma (C#)](../reflection.md)
- [Yansıma (C#) kullanarak özniteliklere erişme](./accessing-attributes-by-using-reflection.md)
