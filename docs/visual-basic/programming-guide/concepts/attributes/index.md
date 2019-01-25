---
title: Öznitelikler genel bakış (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 1449f69b-c063-41de-8d89-f0bbdcf96ac6
ms.openlocfilehash: 282788f9aa5a1ac8c4ede95f04b45c26b9f56588
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559304"
---
# <a name="attributes-overview-visual-basic"></a>Öznitelikler genel bakış (Visual Basic)
Öznitelikler (derlemeler, türler, yöntemler, özellikler ve benzeri) koduyla ilişkili bir meta veriler ya da tanımlayıcı bilgileri, güçlü bir yöntem sağlar. Öznitelik, bir program varlıkla ilişkilendirilen sonra öznitelik çalışma zamanında olarak adlandırılan tekniği kullanarak sorgulanabilir *yansıma*. Daha fazla bilgi için [yansıma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).  
  
 Öznitelik, aşağıdaki özelliklere sahiptir:  
  
-   Öznitelik meta verileri programınıza ekleyin. *Meta veri* bir programda tanımlanan türleri hakkındaki bilgilerdir. Tüm .NET derlemeleri derlemede tanımlanan tür üyeleri ve türleri açıklayan meta veriler belirtilen bir kümesini içerir. Gerekli ek bilgileri belirtmek için özel öznitelikler ekleyebilirsiniz. Daha fazla bilgi için bkz: [özel öznitelikler oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md).  
  
-   Tüm derlemeler, modüller veya daha küçük program öğelerini sınıfları ve özellikleri gibi bir veya daha fazla öznitelikleri uygulayabilirsiniz.  
  
-   Öznitelikleri yöntemleri ve özellikleri aynı şekilde bağımsız değişkenleri kabul edebilir.  
  
-   Programınızı kendi meta veriler ya da diğer programları meta verilerde yansıma kullanarak inceleyebilirsiniz. Daha fazla bilgi için [erişme öznitelikleri kullanarak yansıma (Visual Basic) tarafından](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).  
  
## <a name="using-attributes"></a>Öznitelikleri kullanma  
 Belirli bir öznitelik bildirimleri, geçerli olduğu türlerini kısıtlamak ancak öznitelikleri pek çok bildiriminde yerleştirilebilir. Visual Basic'te, bir öznitelik açılı ayraç içine alınır (\< >). Bu, aynı satırda uygulandığı öğenin hemen önce yer almalıdır.  
  
 Bu örnekte, <xref:System.SerializableAttribute> özniteliği, belirli bir özellik için bir sınıf uygulamak için kullanılır:  
  
```vb  
<System.Serializable()> Public Class SampleClass  
    ' Objects of this type can be serialized.  
End Class  
```  
  
 Özniteliğine sahip metot <xref:System.Runtime.InteropServices.DllImportAttribute> şu şekilde bildirilir:  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
<System.Runtime.InteropServices.DllImport("user32.dll")>   
Sub SampleMethod()  
End Sub  
```  
  
 Birden fazla özniteliği bir bildiriminde yerleştirilebilir:  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
Sub MethodA(<[In](), Out()> ByVal x As Double)  
End Sub  
Sub MethodB(<Out(), [In]()> ByVal x As Double)  
End Sub  
```  
  
 Bazı öznitelikleri kereden fazla belirli bir varlık için belirtilebilir. Multiuse bir öznitelik örneğidir <xref:System.Diagnostics.ConditionalAttribute>:  
  
```vb  
<Conditional("DEBUG"), Conditional("TEST1")>   
Sub TraceMethod()  
End Sub  
```  
  
> [!NOTE]
>  Kural gereği, tüm öznitelik adları word .NET Framework'teki diğer öğelerden bunları ayırt etmek için "özniteliği" ile biter. Ancak, öznitelikler kodda kullanıldığında özniteliği soneki belirtmek gerekmez. Örneğin, `[DllImport]` eşdeğerdir `[DllImportAttribute]`, ancak `DllImportAttribute` .NET Framework'teki özniteliğin gerçek adıdır.  
  
### <a name="attribute-parameters"></a>Öznitelik parametreleri  
 Konumsal, adlandırılmamış veya adlandırılmış parametreleri fazla öznitelik var. Konumsal parametreleri belirli bir sırayla belirtilmelidir ve atlanamaz. adlandırılmış parametreler isteğe bağlıdır ve herhangi bir sırada belirtilebilir. Konumsal parametreler ilk belirtilir. Örneğin, bu üç özniteliğin eşdeğerdir:  
  
```vb  
<DllImport("user32.dll")>  
<DllImport("user32.dll", SetLastError:=False, ExactSpelling:=False)>  
<DllImport("user32.dll", ExactSpelling:=False, SetLastError:=False)>  
```  
  
 İlk parametre, DLL adı konumsal ve her zaman ilk gelir; diğerleri olarak adlandırılır. Bu durumda, döngülerinden çıkarılabilir şekilde her ikisi de false olarak parametreleri varsayılan adı. Varsayılan parametre değerleri hakkında bilgi için tek bir özniteliğin belgelerine bakın.  
  
### <a name="attribute-targets"></a>Öznitelik Hedefleri  
 *Hedef* özniteliği öznitelik uygulandığı varlıktır. Örneğin, bir öznitelik, bir sınıf, belirli bir yöntemi veya tüm derleme geçerli olabilir. Varsayılan olarak, kendisinden öğe için bir özniteliğini uygular. Ancak, bir yöntem veya, parametre veya dönüş değeri bir öznitelik uygulanmış olup olmadığını açıkça, örneğin, belirleyebilirsiniz.  
  
 Bir öznitelik hedefi açıkça tanımlamak için aşağıdaki sözdizimini kullanın:  
  
```vb  
<target : attribute-list>  
```  
  
 Olası listesini `target` değerleri aşağıdaki tabloda gösterilmiştir.  
  
|Hedef değer|Uygulandığı öğe:|  
|------------------|----------------|  
|`assembly`|Tüm derleme|  
|`module`|(Visual Basic modülünden farklıdır) geçerli derleme Modülü|  
  
 Aşağıdaki örnek, derlemeler ve modüller için öznitelik uygulayın gösterilmektedir. Daha fazla bilgi için [ortak öznitelikler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md).  
  
```vb  
Imports System.Reflection  
<Assembly: AssemblyTitleAttribute("Production assembly 4"),   
Module: CLSCompliant(True)>   
```  
  
## <a name="common-uses-for-attributes"></a>Öznitelikler için yaygın kullanımları  
 Aşağıdaki liste, kod öznitelikleri'nın yaygın kullanımları birkaçını içerir:  
  
-   Yöntemlerini kullanarak işaretleme `WebMethod` Web Hizmetleri yöntemi SOAP protokolü üzerinden çağrılabilmelidir belirtmek için özniteliği. Daha fazla bilgi için bkz. <xref:System.Web.Services.WebMethodAttribute>.  
  
-   Yerel kod ile birlikte çalışırken yöntem parametreleri'ı sıralama nasıl açıklayan. Daha fazla bilgi için bkz. <xref:System.Runtime.InteropServices.MarshalAsAttribute>.  
  
-   Sınıfları, yöntemleri ve arabirimleri için COM özelliklerini açıklayan.  
  
-   Yönetilmeyen çağırma kod kullanarak <xref:System.Runtime.InteropServices.DllImportAttribute> sınıfı.  
  
-   Başlık, sürüm, açıklama veya ticari marka açısından derlemenizi açıklayan.  
  
-   Kalıcılık için seri hale getirmek için bir sınıfın hangi üyelerinin açıklayan.  
  
-   Sınıf üyeleri için XML serileştirme XML düğümler arasındaki eşlemeyle ilgili bilgi açıklayan.  
  
-   Güvenlik gereksinimleri yöntemleri için açıklama.  
  
-   Güvenliği zorlamak için kullanılan özellikleri belirleme.  
  
-   Kod hatalarını ayıklamak kolay kalır. böylece en iyi duruma getirme just-in-time (JIT) derleyici tarafından denetleniyor.  
  
-   Bir yöntemin arayanı hakkında bilgi edinme.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Daha fazla bilgi için bkz.:  
  
-   [Özel öznitelikler (Visual Basic) oluşturma](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
  
-   [(Visual Basic) yansıma kullanarak özniteliklere erişme](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
  
-   [Nasıl yapılır: Öznitelikler (Visual Basic) kullanarak bir C/C++ birleşimi oluşturma](../../../../visual-basic/programming-guide/concepts/attributes/how-to-create-a-c-cpp-union-by-using-attributes.md)  
  
-   [Ortak öznitelikler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md)  
  
-   [Arayan bilgileri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md)  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Visual Basic programlama kılavuzu](../../../../visual-basic/programming-guide/index.md)
- [Yansıma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [Öznitelikler](../../../../standard/attributes/index.md)
