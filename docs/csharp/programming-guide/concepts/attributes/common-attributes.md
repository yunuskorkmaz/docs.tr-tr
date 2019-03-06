---
title: Ortak öznitelikler (C#)
ms.date: 07/20/2015
ms.assetid: 785a0526-6c0e-4599-8c61-ccdc88dd9965
ms.openlocfilehash: d5d56fff82fb552f42f72c18b8c3b907c5bc113c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374810"
---
# <a name="common-attributes-c"></a>Ortak öznitelikler (C#)
Bu konuda, C# programlarında en çok kullanılan öznitelikler açıklanmaktadır.  
  
-   [Genel Öznitelikler](#Global)  
  
-   [Geçersiz öznitelik](#Obsolete)  
  
-   [Conditional özniteliği](#Conditional)  
  
-   [Arayan bilgileri öznitelikleri](#CallerInfo)  
  
## <a name="Global"></a> Genel Öznitelikler  
 Çoğu öznitelik sınıfları veya yöntemleri gibi belirli dil öğelerini uygulanır; Ancak, bazı öznitelikler genel — bir tüm derleme veya modül için geçerlidir. Örneğin, <xref:System.Reflection.AssemblyVersionAttribute> özniteliği, böyle bir derleme içinde sürüm bilgileri ekleme için kullanılabilir:  
  
```csharp  
[assembly: AssemblyVersion("1.0.0.0")]  
```  
  
 Genel Öznitelikler görünen kaynak kodunda herhangi sonra en üst düzey `using` yönergeleri ve herhangi bir tür, modül veya ad alanı bildirimleri önce. Genel Öznitelikler birden çok kaynak dosyalarında görünebilir, ancak dosyalar tek bir derleme pass derlenmelidir. C# projelerinde, genel öznitelikler AssemblyInfo.cs dosyasında yerleştirilir.  
  
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
  
 Bu örnekte `Obsolete` öznitelik sınıfına uygulanan `A` ve yönteme `B.OldMethod`. Öznitelik oluşturucusunda ikinci bağımsız değişkeni için uyguladığı `B.OldMethod` ayarlanır `true`, sınıfını kullanarak ise bu yöntem bir derleyici hatasına neden olur `A` bir uyarı yalnızca üretim olur. Çağırma `B.NewMethod`, ancak hiçbir uyarı veya hata üretir.  
  
 Uyarı veya hata bir parçası olarak öznitelik yapıcısına ilk bağımsız değişken olarak sağlanan dizesi görüntülenir. Örneğin, önceki tanımları ile kullandığınızda, aşağıdaki kod iki uyarıları ve bir hata oluşturur:  
  
```csharp  
// Generates 2 warnings:  
// A a = new A();  
  
// Generate no errors or warnings:  
B b = new B();  
b.NewMethod();  
  
// Generates an error, terminating compilation:  
// b.OldMethod();  
```  
  
 Sınıf için iki uyarı `A` üretilir: sınıf başvurusu bildirimi için diğeri için sınıf oluşturucu.  
  
 `Obsolete` Öznitelik bağımsız değişkeni olmadan kullanılabilir, ancak öğe neden dahil olmak üzere bir açıklama kullanılmıyor ve ne kullanmanız önerilir.  
  
 `Obsolete` Özniteliği tek kullanımlık bir özniteliktir ve öznitelikleri izin veren herhangi bir varlık için uygulanabilir. `Obsolete` için bir diğer addır <xref:System.ObsoleteAttribute>.  
  
## <a name="Conditional"></a> Conditional özniteliği  
 `Conditional` Özniteliği bir yönteminin yürütülmesi bir ön işleme tanımlayıcısı bağımlı yapar. `Conditional` Özniteliği için bir diğer ad, <xref:System.Diagnostics.ConditionalAttribute>ve bir yöntem veya bir öznitelik sınıfı için uygulanabilir.  
  
 Bu örnekte, `Conditional` etkinleştirmek veya program özel tanılama bilgilerinin görüntülenmesini devre dışı bırakmak için bir yönteme uygulanır:  
  
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
  
 Varsa `TRACE_ON` tanımlayıcı tanımlı değil, hiçbir İzleme çıktısı görüntülenir.  
  
 `Conditional` Özniteliği ile kullanılan genellikle `DEBUG` izleme ve hata ayıklama derlemeleri ancak içinde olmayan sürüm yapıları, günlük özellikleri etkinleştirmek için tanımlayıcı şöyle:  
  
```csharp  
[Conditional("DEBUG")]  
static void DebugMethod()  
{  
}  
```  
  
 Koşullu olarak işaretlenmiş bir yöntem çağrıldığında, varlığı veya yokluğu belirtilen ön işleme sembolünün çağrı dahil mi, yoksa atlanmış mı olduğunu belirler. Simge tanımlanmışsa çağrısı bulunur; Aksi takdirde, çağrı atlanır. Kullanarak `Conditional` bir olmamasına içinde yöntemleri kapsayan daha zarif ve hataya daha az seçenek `#if…#endif` blokları, şöyle:  
  
```csharp  
#if DEBUG  
    void ConditionalMethod()  
    {  
    }  
#endif  
```  
  
 Bir koşullu metot bir class veya struct bildiriminde bir yöntem olmalı ve bir dönüş değeri olmamalıdır.  
  
### <a name="using-multiple-identifiers"></a>Birden çok tanımlayıcılarla  
 Bir yöntemin birden fazla varsa `Conditional` öznitelikleri, yönteme bir çağrı ise dahil en az bir koşullu simgeleri tanımlanır (diğer bir deyişle, simgeler mantıksal veya işlecini kullanarak birbirine bağlıdır). Bu örnekte, ya da varlığını `A` veya `B` bir yöntem çağrısında neden olur:  
  
```csharp  
[Conditional("A"), Conditional("B")]  
static void DoIfAorB()  
{  
    // ...  
}  
```  
  
 Mantıksal ve işlecini kullanarak simgeleri bağlama etkiyi elde etmek için seri koşullu yöntemler tanımlayabilirsiniz. Örneğin, ikinci yöntem aşağıdaki yalnızca her iki yürütecek `A` ve `B` tanımlanır:  
  
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
  
### <a name="using-conditional-with-attribute-classes"></a>Koşullu öznitelik sınıfları ile kullanma  
 `Conditional` Özniteliği bir öznitelik sınıf tanımına da uygulanabilir. Bu örnekte, özel öznitelik `Documentation` yalnızca hata ayıklama tanımlanmışsa meta verilere bilgi ekleyeceksiniz.  
  
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
  
## <a name="CallerInfo"></a> Arayan bilgileri öznitelikleri  
 Arayan Bilgisi özniteliklerini kullanarak bir yöntemin arayanı hakkında bilgi edinebilirsiniz. Kaynak kodu dosyasının yolu, satır numarası kaynak kodu ve arayanın üye adını alabilirsiniz.  
  
 Üye arayan bilgileri elde etmek için isteğe bağlı parametrelere uygulanan öznitelikler kullanın. İsteğe bağlı her parametre varsayılan bir değer belirtir. Aşağıdaki tabloda tanımlanan arayan bilgisi öznitelikleri listelenmektedir <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> ad alanı:  
  
|Öznitelik|Açıklama|Tür|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Kaynak dosyasının arayanı içeren tam yolu. Derleme zamanında yolu budur.|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Yöntemin çağrıldığı kaynak dosyadaki satır numarası.|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Yöntem adı veya çağıranın özelliğinin adı. Daha fazla bilgi için [arayan bilgileri (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).|`String`|  
  
 Arayan bilgisi öznitelikleri hakkında daha fazla bilgi için bkz: [arayan bilgileri (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection>
- <xref:System.Attribute>
- [C# Programlama Kılavuzu](../../../../csharp/programming-guide/index.md)
- [Öznitelikler](../../../../../docs/standard/attributes/index.md)
- [Yansıma (C#)](../../../../csharp/programming-guide/concepts/reflection.md)
- [Yansıma (C#) kullanarak özniteliklere erişme](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
