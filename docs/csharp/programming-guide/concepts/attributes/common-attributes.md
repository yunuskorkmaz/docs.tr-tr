---
title: "Ortak öznitelikler (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 785a0526-6c0e-4599-8c61-ccdc88dd9965
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4e0a8912aa60e4c2918bb812963d83fae8d529f1
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2017
---
# <a name="common-attributes-c"></a>Ortak öznitelikler (C#)
Bu konuda, C# programlarında en yaygın olarak kullanılan öznitelikler açıklanmaktadır.  
  
-   [Genel Öznitelikler](#Global)  
  
-   [Artık kullanılmayan özniteliği](#Obsolete)  
  
-   [Koşul özniteliği](#Conditional)  
  
-   [Arayan bilgileri öznitelikleri](#CallerInfo)  
  
##  <a name="Global"></a>Genel Öznitelikler  
 Çoğu öznitelik sınıfları veya yöntemleri gibi belirli bir dil öğeleri uygulanır; Ancak, bazı öznitelikler genel — tüm derleme veya modülü için geçerlidir. Örneğin, <xref:System.Reflection.AssemblyVersionAttribute> özniteliği, böyle bir bütünleştirilmiş sürüm bilgilerini eklemek için kullanılabilir:  
  
```csharp  
[assembly: AssemblyVersion("1.0.0.0")]  
```  
  
 Genel Öznitelikler görünen kaynak kodunda herhangi sonra en üst düzey `using` yönergeleri ve herhangi bir tür, modül veya ad alanı bildirimleri öncesinde. Genel Öznitelikler birden çok kaynak dosyalarında görünebilir, ancak dosyaları tek bir derleme geçişinde derlenmiş olmalıdır. C# projelerinde, genel öznitelikler AssemblyInfo.cs dosyasında yerleştirilir.  
  
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
  
##  <a name="Obsolete"></a>Artık kullanılmayan özniteliği  
 `Obsolete` Özniteliği bir program varlık artık kullanım için önerilen biri olarak işaretler. Artık kullanılmayan olarak işaretlenmiş bir varlığın her kullanın, daha sonra bir uyarı veya öznitelik nasıl yapılandırıldığına bağlı olarak bir hata oluşturur. Örneğin:  
  
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
  
 Bu örnekte `Obsolete` özniteliği sınıfına uygulanan `A` ve yöntemine `B.OldMethod`. Öznitelik oluşturucunun ikinci bağımsız değişkeni uygulanan çünkü `B.OldMethod` ayarlanır `true`, bu yöntem, sınıfını kullanarak ancak derleyici hatası neden olur `A` bir uyarı yalnızca ürettiği olur. Çağırma `B.NewMethod`, ancak hiçbir uyarı veya hata üretir.  
  
 Öznitelik oluşturucunun ilk bağımsız değişkeni olarak sağlanan dize uyarı veya hata bir parçası olarak görüntülenir. Örneğin, önceki tanımları ile kullandığınızda, aşağıdaki kod iki uyarılar ve bir hata oluşturur:  
  
```csharp  
// Generates 2 warnings:  
// A a = new A();  
  
// Generate no errors or warnings:  
B b = new B();  
b.NewMethod();  
  
// Generates an error, terminating compilation:  
// b.OldMethod();  
```  
  
 Sınıfı için iki uyarıları `A` oluşturulur: sınıf başvurusu bildirimi için diğeri için sınıf oluşturucu.  
  
 `Obsolete` Öznitelik bağımsız değişkenler olmadan kullanılabilir, ancak neden bir açıklaması da dahil olmak üzere öğe kullanılmıyor ve ne kullanmanız önerilir.  
  
 `Obsolete` Özniteliği bir tek kullanımlık özniteliği ve öznitelikleri veren herhangi bir varlık için uygulanabilir. `Obsolete`bir diğer adı için <xref:System.ObsoleteAttribute>.  
  
##  <a name="Conditional"></a>Koşul özniteliği  
 `Conditional` Özniteliği bir yönteminin yürütülmesi üzerinde önişlem tanımlayıcısını bağımlı yapar. `Conditional` Özniteliktir için diğer ad <xref:System.Diagnostics.ConditionalAttribute>ve bir yöntem veya öznitelik sınıfı için uygulanabilir.  
  
 Bu örnekte, `Conditional` etkinleştirmek veya programa özgü tanı bilgilerini görüntülemeyi devre dışı bırakmak için bir yönteme uygulanır:  
  
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
  
 Varsa `TRACE_ON` tanımlayıcısı tanımlı değil, izleme çıktısı görüntülenir.  
  
 `Conditional` Özniteliği ile kullanılan genellikle `DEBUG` izleme ve hata ayıklama derlemeleri ancak içinde değil yayın derlemeler, günlük özellikleri etkinleştirmek için tanımlayıcı şöyle:  
  
```csharp  
[Conditional("DEBUG")]  
static void DebugMethod()  
{  
}  
```  
  
 Koşullu olarak işaretli bir yöntem çağrıldığında, varlığının veya yokluğunun belirtilen önişlem simgenin çağrı dahil atlanmış verilip verilmediğini belirler. Simgenin tanımlanmışsa, çağrı bulunur; Aksi halde çağrı atlanır. Kullanarak `Conditional` bir temizleyici olan yöntemleri içinde kapsayan daha zarif ve hataya daha az alternatif `#if…#endif` blokları, şuna benzer:  
  
```csharp  
#if DEBUG  
    void ConditionalMethod()  
    {  
    }  
#endif  
```  
  
 Koşullu bir yöntem sınıfta veya yapı bildiriminde bir yöntem olmalıdır ve bir dönüş değeri olmamalıdır.  
  
### <a name="using-multiple-identifiers"></a>Birden çok tanımlayıcıları kullanma  
 Bir yöntemin birden çok varsa `Conditional` öznitelikleri yöntemine bir çağrı dahil en az bir koşullu simgelerin tanımlanmışsa (diğer bir deyişle, simgeler mantıksal veya işlecini kullanarak birbirine bağlıdır). Bu örnekte, ya da varlığını `A` veya `B` bir yöntem çağrısı neden olur:  
  
```csharp  
[Conditional("A"), Conditional("B")]  
static void DoIfAorB()  
{  
    // ...  
}  
```  
  
 Mantıksal ve işlecini kullanarak simgeleri bağlama etkisini elde etmek için seri koşullu yöntemler tanımlayabilirsiniz. Örneğin, aşağıdaki ikinci yöntem yalnızca her iki yürütecek `A` ve `B` tanımlanır:  
  
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
 `Conditional` Özniteliği için öznitelik sınıf tanımını da uygulanabilir. Bu örnekte, özel öznitelik `Documentation` hata ayıklama tanımlanmışsa, yalnızca bilgi meta verileri ekler.  
  
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
  
##  <a name="CallerInfo"></a>Arayan bilgileri öznitelikleri  
 Arayan Bilgisi özniteliklerini kullanarak bir yöntemin arayanı hakkında bilgi edinebilirsiniz. Kaynak kodu dosya yolu, kaynak kodu ve arayan üye adı satır numarasını edinebilirsiniz.  
  
 Üye arayan bilgileri almak için isteğe bağlı parametreler uygulanan öznitelikleri kullanın. Her isteğe bağlı bir parametre varsayılan bir değer belirtir. Aşağıdaki tabloda tanımlanan arayan bilgileri öznitelikleri listeler <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> ad alanı:  
  
|Öznitelik|Açıklama|Tür|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Kaynak dosyasının arayanı içeren tam yolu. Derleme zamanında yolu budur.|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Satır numarası kaynak dosyasındaki yöntemi adı verilir.|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Yöntem adı veya çağıranın özellik adı. Daha fazla bilgi için bkz: [arayan bilgileri (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).|`String`|  
  
 Arayan bilgileri öznitelikleri hakkında daha fazla bilgi için bkz: [arayan bilgileri (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [C# programlama kılavuzu](../../../../csharp/programming-guide/index.md)  
 [Öznitelikleri](../../../../../docs/standard/attributes/index.md)  
 [Yansıma (C#)](../../../../csharp/programming-guide/concepts/reflection.md)  
 [Yansıma (C#) kullanarak özniteliklere erişme](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
