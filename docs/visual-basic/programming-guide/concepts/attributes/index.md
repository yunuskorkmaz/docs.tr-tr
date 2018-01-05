---
title: "Öznitelikler genel bakış (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1449f69b-c063-41de-8d89-f0bbdcf96ac6
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2b78eb3e5ac52ec89e810fde682249c689ba304a
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="attributes-overview-visual-basic"></a>Öznitelikler genel bakış (Visual Basic)
Öznitelikler meta verileri veya tanımlayıcı bilgileri (derleme, türleri, yöntemler, özellikler ve benzeri) kodu ile ilişkilendirme için güçlü bir yöntem sağlar. Öznitelik bir program varlıkla ilişkilendirilen sonra öznitelik çalışma zamanında adlı bir yöntemi kullanarak sorgulanabilir *yansıma*. Daha fazla bilgi için bkz: [yansıma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).  
  
 Öznitelikler, aşağıdaki özelliklere sahiptir:  
  
-   Öznitelikleri programınıza meta veri ekleyin. *Meta veri* bir programda tanımlanan türleri hakkındaki bilgilerdir. Tüm .NET derlemelerini belirlenen türleri ve derlemede tanımlanan tür üyeleri açıklayan meta veriler içeriyor. Gerekli ek bilgileri belirtmek için özel öznitelikler ekleyebilirsiniz. Daha fazla bilgi için bkz: [özel öznitelikler oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md).  
  
-   Tüm derlemeler, modüller veya daha küçük program öğeleri sınıfları ve özellikleri gibi bir veya daha fazla öznitelik uygulayabilirsiniz.  
  
-   Öznitelikler, yöntemleri ve özellikleri aynı şekilde bağımsız değişkenleri kabul edebilir.  
  
-   Programınızı kendi meta verileri veya diğer programları meta yansıma kullanarak inceleyebilirsiniz. Daha fazla bilgi için bkz: [erişme öznitelikleri kullanarak yansıma (Visual Basic) tarafından](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).  
  
## <a name="using-attributes"></a>Öznitelikleri kullanma  
 Belirli bir özniteliği, geçerli olduğu bildirimleri türlerini kısıtlayacak ancak öznitelikleri pek çok bildiriminde, yerleştirilebilir. Visual Basic'te bir öznitelik açılı ayraç (\< >). Bu, aynı satırda uygulandığı öğe hemen önce görünmelidir.  
  
 Bu örnekte, <xref:System.SerializableAttribute> özniteliği bir sınıf için belirli bir karakteristik uygulamak için kullanılır:  
  
```vb  
<System.Serializable()> Public Class SampleClass  
    ' Objects of this type can be serialized.  
End Class  
```  
  
 Öznitelik bir yöntemle <xref:System.Runtime.InteropServices.DllImportAttribute> şöyle bildirilmiş:  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
<System.Runtime.InteropServices.DllImport("user32.dll")>   
Sub SampleMethod()  
End Sub  
```  
  
 Birden fazla öznitelik bir bildiriminde yerleştirilebilir:  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
Sub MethodA(<[In](), Out()> ByVal x As Double)  
End Sub  
Sub MethodB(<Out(), [In]()> ByVal x As Double)  
End Sub  
```  
  
 Bazı öznitelikler, belirli bir varlık için birden çok kez belirtilebilir. Multiuse bir öznitelik örneğidir <xref:System.Diagnostics.ConditionalAttribute>:  
  
```vb  
<Conditional("DEBUG"), Conditional("TEST1")>   
Sub TraceMethod()  
End Sub  
```  
  
> [!NOTE]
>  Kurala göre .NET Framework'teki diğer öğelerini bunları ayırt etmek için "özniteliği" word tüm öznitelik adları bitemez. Ancak, öznitelikler kodda kullanırken özniteliği soneki belirtmek gerekmez. Örneğin, `[DllImport]` eşdeğerdir `[DllImportAttribute]`, ancak `DllImportAttribute` .NET Framework'teki özniteliğin gerçek adıdır.  
  
### <a name="attribute-parameters"></a>Öznitelik parametreleri  
 Konumsal, adlandırılmamış veya adlandırılmış parametreleri birçok özniteliklere sahiptir. Konumsal parametreleri belirli bir sırada belirtilmeli ve atlanmış olamaz; adlandırılmış parametreler isteğe bağlıdır ve herhangi bir sırada belirtilebilir. Konumsal parametreler ilk belirtildi. Örneğin, bu üç özniteliğin eşdeğerdir:  
  
```vb  
<DllImport("user32.dll")>  
<DllImport("user32.dll", SetLastError:=False, ExactSpelling:=False)>  
<DllImport("user32.dll", ExactSpelling:=False, SetLastError:=False)>  
```  
  
 İlk parametre, DLL adı konumsal ve her zaman ilk gelir; diğer olarak adlandırılır. Bu durumda, kullanıcılar atlanabilir şekilde her ikisi de false, parametreleri varsayılan adı. Varsayılan parametre değerleri hakkında bilgi için tek tek özniteliğin belgelerine bakın.  
  
### <a name="attribute-targets"></a>Öznitelik Hedefleri  
 *Hedef* bir öznitelik geçerli olduğu varlık özniteliğidir. Örneğin, bir öznitelik, bir sınıf, belirli bir yöntemi veya tüm derleme için geçerli olabilir. Varsayılan olarak, bir öznitelik yakalanması öğesine uygulanır. Ancak bir öznitelik bir yöntem veya onun parametresi veya dönüş değeri uygulanıp uygulanmayacağını, aynı zamanda açıkça, örneğin, tanımlayabilirsiniz.  
  
 Açıkça bir öznitelik hedefini belirlemek için aşağıdaki sözdizimini kullanın:  
  
```vb  
<target : attribute-list>  
```  
  
 Olası listesi `target` değerleri aşağıdaki tabloda gösterilmiştir.  
  
|Hedef değer|Uygulandığı öğe:|  
|------------------|----------------|  
|`assembly`|Tüm derleme|  
|`module`|(Visual Basic modülünden farklı) geçerli derleme Modülü|  
  
 Aşağıdaki örnek, derlemeler ve modüller öznitelikleri uygulanacak gösterilmiştir. Daha fazla bilgi için bkz: [ortak öznitelikler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md).  
  
```vb  
Imports System.Reflection  
<Assembly: AssemblyTitleAttribute("Production assembly 4"),   
Module: CLSCompliant(True)>   
```  
  
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
  
-   [Özel öznitelikler (Visual Basic) oluşturma](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
  
-   [(Visual Basic) yansıma kullanarak özniteliklere erişme](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
  
-   [Nasıl yapılır: öznitelikleri (Visual Basic) kullanarak C/C++ birleşimi oluşturma](../../../../visual-basic/programming-guide/concepts/attributes/how-to-create-a-c-cpp-union-by-using-attributes.md)  
  
-   [Ortak öznitelikler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md)  
  
-   [Arayan bilgileri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic programlama kılavuzu](../../../../visual-basic/programming-guide/index.md)  
 [Yansıma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [Öznitelikler](../../../../standard/attributes/index.md)
