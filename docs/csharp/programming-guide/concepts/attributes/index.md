---
title: Öznitelikler (C#)
ms.date: 07/20/2015
ms.assetid: f148f13f-a0d5-4f22-9c87-4b73d5dde270
ms.openlocfilehash: a7e64c29ab8ca56a47ec6554ebc316f4922d3aca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="attributes-c"></a>Öznitelikler (C#)
Öznitelikler meta verileri veya tanımlayıcı bilgileri (derleme, türleri, yöntemler, özellikler ve benzeri) kodu ile ilişkilendirme için güçlü bir yöntem sağlar. Öznitelik bir program varlıkla ilişkilendirilen sonra öznitelik çalışma zamanında adlı bir yöntemi kullanarak sorgulanabilir *yansıma*. Daha fazla bilgi için bkz: [yansıma (C#)](../../../../csharp/programming-guide/concepts/reflection.md).  
  
 Öznitelikler, aşağıdaki özelliklere sahiptir:  
  
-   Öznitelikleri programınıza meta veri ekleyin. *Meta veri* bir programda tanımlanan türleri hakkındaki bilgilerdir. Tüm .NET derlemelerini belirlenen türleri ve derlemede tanımlanan tür üyeleri açıklayan meta veriler içeriyor. Gerekli ek bilgileri belirtmek için özel öznitelikler ekleyebilirsiniz. Daha fazla bilgi için bkz: [özel öznitelikler oluşturma (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md).  
  
-   Tüm derlemeler, modüller veya daha küçük program öğeleri sınıfları ve özellikleri gibi bir veya daha fazla öznitelik uygulayabilirsiniz.  
  
-   Öznitelikler, yöntemleri ve özellikleri aynı şekilde bağımsız değişkenleri kabul edebilir.  
  
-   Programınızı kendi meta verileri veya diğer programları meta yansıma kullanarak inceleyebilirsiniz. Daha fazla bilgi için bkz: [yansıma (C#) kullanarak erişme özniteliklerle](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).  
  
## <a name="using-attributes"></a>Öznitelikleri kullanma  
 Belirli bir özniteliği, geçerli olduğu bildirimleri türlerini kısıtlayacak ancak öznitelikleri pek çok bildiriminde, yerleştirilebilir. C# ' ta, bir öznitelik köşeli parantez ([]) içine özniteliğinin adı girerek geçerli olduğu varlık bildiriminin üstüne belirtin.  
  
 Bu örnekte, <xref:System.SerializableAttribute> özniteliği bir sınıf için belirli bir karakteristik uygulamak için kullanılır:  
  
```csharp  
[System.Serializable]  
public class SampleClass  
{  
    // Objects of this type can be serialized.  
}  
```  
  
 Öznitelik bir yöntemle <xref:System.Runtime.InteropServices.DllImportAttribute> şöyle bildirilmiş:  
  
```csharp  
using System.Runtime.InteropServices;  
```  
  
```csharp  
[System.Runtime.InteropServices.DllImport("user32.dll")]  
extern static void SampleMethod();  
```  
  
 Birden fazla öznitelik bir bildiriminde yerleştirilebilir:  
  
```csharp  
using System.Runtime.InteropServices;  
```  
  
```csharp  
void MethodA([In][Out] ref double x) { }  
void MethodB([Out][In] ref double x) { }  
void MethodC([In, Out] ref double x) { }  
```  
  
 Bazı öznitelikler, belirli bir varlık için birden çok kez belirtilebilir. Multiuse bir öznitelik örneğidir <xref:System.Diagnostics.ConditionalAttribute>:  
  
```csharp  
[Conditional("DEBUG"), Conditional("TEST1")]  
void TraceMethod()  
{  
    // ...  
}  
```  
  
> [!NOTE]
>  Kurala göre .NET Framework'teki diğer öğelerini bunları ayırt etmek için "özniteliği" word tüm öznitelik adları bitemez. Ancak, öznitelikler kodda kullanırken özniteliği soneki belirtmek gerekmez. Örneğin, `[DllImport]` eşdeğerdir `[DllImportAttribute]`, ancak `DllImportAttribute` .NET Framework'teki özniteliğin gerçek adıdır.  
  
### <a name="attribute-parameters"></a>Öznitelik parametreleri  
 Konumsal, adlandırılmamış veya adlandırılmış parametreleri birçok özniteliklere sahiptir. Konumsal parametreleri belirli bir sırada belirtilmeli ve atlanmış olamaz; adlandırılmış parametreler isteğe bağlıdır ve herhangi bir sırada belirtilebilir. Konumsal parametreler ilk belirtildi. Örneğin, bu üç özniteliğin eşdeğerdir:  
  
```csharp  
[DllImport("user32.dll")]  
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]  
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]  
```  
  
 İlk parametre, DLL adı konumsal ve her zaman ilk gelir; diğer olarak adlandırılır. Bu durumda, kullanıcılar atlanabilir şekilde her ikisi de false, parametreleri varsayılan adı. Varsayılan parametre değerleri hakkında bilgi için tek tek özniteliğin belgelerine bakın.  
  
### <a name="attribute-targets"></a>Öznitelik Hedefleri  
 *Hedef* bir öznitelik geçerli olduğu varlık özniteliğidir. Örneğin, bir öznitelik, bir sınıf, belirli bir yöntemi veya tüm derleme için geçerli olabilir. Varsayılan olarak, bir öznitelik yakalanması öğesine uygulanır. Ancak bir öznitelik bir yöntem veya onun parametresi veya dönüş değeri uygulanıp uygulanmayacağını, aynı zamanda açıkça, örneğin, tanımlayabilirsiniz.  
  
 Açıkça bir öznitelik hedefini belirlemek için aşağıdaki sözdizimini kullanın:  
  
```csharp  
[target : attribute-list]  
```  
  
 Olası listesi `target` değerleri aşağıdaki tabloda gösterilmiştir.  
  
|Hedef değer|Uygulandığı öğe:|  
|------------------|----------------|  
|`assembly`|Tüm derleme|  
|`module`|Geçerli derleme Modülü|  
|`field`|Bir sınıf veya yapı alanında|  
|`event`|Olay|  
|`method`|Yöntem veya `get` ve `set` özellik erişimcisi|  
|`param`|Yöntem parametreleri veya `set` özellik erişimcisi parametreleri|  
|`property`|Özellik|  
|`return`|Yöntemi, özelliği dizin oluşturucu, değeri döndürür veya `get` özelliği erişimcisi|  
|`type`|Yapısı, sınıf, arabirim, numaralandırma veya temsilci|  
  
 Aşağıdaki örnek, derlemeler ve modüller öznitelikleri uygulanacak gösterilmiştir. Daha fazla bilgi için bkz: [ortak öznitelikler (C#)](../../../../csharp/programming-guide/concepts/attributes/common-attributes.md).  
  
```csharp  
using System;  
using System.Reflection;  
[assembly: AssemblyTitleAttribute("Production assembly 4")]  
[module: CLSCompliant(true)]  
```  
  
 Aşağıdaki örnekte, yöntem, yöntem parametreleri, öznitelikleri uygulamak gösterilmiştir ve yöntemi dönüş değerleri C# '.  
  
```csharp  
// default: applies to method  
[SomeAttr]  
int Method1() { return 0; }  
  
// applies to method  
[method: SomeAttr]  
int Method2() { return 0; }  
  
// applies to return value  
[return: SomeAttr]  
int Method3() { return 0; }  
```  
  
> [!NOTE]
>  Hedefler, bağımsız olarak `SomeAttr` geçerli olması için tanımlanan `return` hedef sahip belirtilmesi bile `SomeAttr` yalnızca dönüş değerleri uygulamak için tanımlanmış. Diğer bir deyişle, derleyici kullanmaz `AttributeUsage` bilgileri belirsiz öznitelik hedefleri çözümlemek için. Daha fazla bilgi için bkz: [AttributeUsage (C#)](../../../../csharp/programming-guide/concepts/attributes/attributeusage.md).  
  
## <a name="common-uses-for-attributes"></a>Öznitelikler için ortak kullanımlar  
 Aşağıdaki öznitelikler'ın yaygın kullanımları bazılarını kod içerir:  
  
-   Yöntemlerini kullanarak işaretleme `WebMethod` yöntemi SOAP protokolü üzerinden aranabilir olması gerektiğini belirtmek için Web Hizmetleri içinde öznitelik. Daha fazla bilgi için bkz. <xref:System.Web.Services.WebMethodAttribute>.  
  
-   Yerel kod ile birlikte çalışırken yöntem parametreleri sıralamakta nasıl açıklayan. Daha fazla bilgi için bkz. <xref:System.Runtime.InteropServices.MarshalAsAttribute>.  
  
-   Sınıfları, yöntemleri ve arabirimleri COM özelliklerini açıklayan.  
  
-   Yönetilmeyen çağırma kullanarak kod <xref:System.Runtime.InteropServices.DllImportAttribute> sınıfı.  
  
-   Başlık, sürüm, açıklama veya ticari marka bakımından derlemenizi açıklayan.  
  
-   Kalıcılığını serileştirmek için bir sınıf hangi üyelerinin açıklayan.  
  
-   Sınıf üyeleri ve XML serileştirme için XML düğümler arasında eşleme açıklayan.  
  
-   Yöntemleri için güvenlik gereksinimleri açıklanır.  
  
-   Güvenlik uygulamak için kullanılan özellikleri belirleme.  
  
-   Böylece kodu hata ayıklamak kolay tam zamanında (JIT) derleyici tarafından iyileştirmeleri denetleme.  
  
-   Arayan bir yöntemi hakkında bilgi edinme.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Daha fazla bilgi için bkz.:  
  
-   [Özel öznitelikler (C#) oluşturma](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)  
  
-   [Yansıma (C#) kullanarak özniteliklere erişme](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
  
-   [Nasıl yapılır: öznitelikleri (C#) kullanarak C/C++ birleşimi oluşturma](../../../../csharp/programming-guide/concepts/attributes/how-to-create-a-c-cpp-union-by-using-attributes.md)  
  
-   [Ortak öznitelikler (C#)](../../../../csharp/programming-guide/concepts/attributes/common-attributes.md)  
  
-   [Arayan bilgileri (C#)](../../../../csharp/programming-guide/concepts/caller-information.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../../csharp/programming-guide/index.md)  
 [Yansıma (C#)](../../../../csharp/programming-guide/concepts/reflection.md)  
 [Öznitelikler](../../../../../docs/standard/attributes/index.md)
