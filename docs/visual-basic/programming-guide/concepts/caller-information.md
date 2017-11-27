---
title: Arayan bilgileri (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 15d556eb-4d0c-4497-98a3-7f60abb7d6a1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dfd9339e990b2a2a7c57acde3c91295a7154fdc0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="caller-information-visual-basic"></a>Arayan bilgileri (Visual Basic)
Arayan Bilgisi özniteliklerini kullanarak bir yöntemin arayanı hakkında bilgi edinebilirsiniz. Kaynak kodunun dosya yolunu, kaynak kodundaki satır numarasını ve arayanın üye adını alabilirsiniz. Bu bilgiler, tanılama araçlarının izlenmesine, oluşturulmasına ve bu araçlarda hata ayıklanmasına yardımcı olur.  
  
 Bu bilgileri elde etmek için her biri varsayılan değere sahip isteğe bağlı parametrelere uygulanan öznitelikler kullanabilirsiniz. Aşağıdaki tabloda tanımlanan arayan bilgileri öznitelikleri listeler <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> ad alanı:  
  
|Öznitelik|Açıklama|Tür|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Kaynak dosyasının arayanı içeren tam yolu. Bu, derleme zamanındaki dosya yoludur.|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Yöntemin çağrıldığı kaynak dosyadaki satır numarası.|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Arayanın yöntemi veya özellik adı. Bkz: [üye adlarının](#MEMBERNAMES) bu konuda daha sonra.|`String`|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, Arayanın Bilgisi özniteliklerinin nasıl kullanılacağı gösterilmiştir. Her çağrıda `TraceMessage` isteğe bağlı bağımsız değişkenleri olarak yöntemi, arayan bilgileri değiştirdi.  
  
```vb  
Private Sub DoProcessing()  
    TraceMessage("Something happened.")  
End Sub  
  
Public Sub TraceMessage(message As String,  
        <System.Runtime.CompilerServices.CallerMemberName> Optional memberName As String = Nothing,  
        <System.Runtime.CompilerServices.CallerFilePath> Optional sourcefilePath As String = Nothing,  
        <System.Runtime.CompilerServices.CallerLineNumber()> Optional sourceLineNumber As Integer = 0)  
  
    System.Diagnostics.Trace.WriteLine("message: " & message)  
    System.Diagnostics.Trace.WriteLine("member name: " & memberName)  
    System.Diagnostics.Trace.WriteLine("source file path: " & sourcefilePath)  
    System.Diagnostics.Trace.WriteLine("source line number: " & sourceLineNumber)  
End Sub  
  
' Sample output:  
'   message: Something happened.  
'   member name: DoProcessing  
'   source file path: C:\Users\username\Documents\Visual Studio 2012\Projects\CallerInfoVB\CallerInfoVB\Form1.vb  
'   source line number: 15  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Her isteğe bağlı parametre için açık bir varsayılan değer belirtmeniz gerekir. İsteğe bağlı olarak belirtilmeyen parametrelere Arayan Bilgisi özniteliklerini uygulayamazsınız.  
  
 Arayan Bilgisi öznitelikleri, bir parametreyi isteğe bağlı hale getirmez. Bunun yerine, bağımsız değişken atlandığında geçirilen varsayılan değeri etkilerler.  
  
 Arayan Bilgisi değerleri, derleme zamanında Ara Dile (IL) değişmez değerler olarak verilir. Sonuçlarını aksine <xref:System.Exception.StackTrace%2A> özellik için özel durumlar, sonuçları gizleme tarafından etkilenmez.  
  
 Arayan bilgisini denetlemek veya gizlemek için isteğe bağlı bağımsız değişkenleri açıkça sağlayabilirsiniz.  
  
###  <a name="MEMBERNAMES"></a>Üye adlarının  
 Kullanabileceğiniz `CallerMemberName` özniteliği üye adı olarak belirtmekten kaçının bir `String` çağrılan yöntemin bağımsız değişkeni. Bu yöntemi kullanarak, bir sorunu önlemenize, **yeniden adlandırma yeniden düzenleme** değiştirmez `String` değerleri. Bu, özellikle aşağıdaki görevler için yararlı olur:  
  
-   İzleme ve tanılama yordamlarını kullanma.  
  
-   Uygulama <xref:System.ComponentModel.INotifyPropertyChanged> veri bağlama sırasında arabirim. Bu arabirim, bir nesnenin özelliğinin bağlama denetimine özelliğin değiştirildiğini bildirmesini ve böylece denetimin güncelleştirilmiş bilgileri görüntüleyebilmesini sağlar. Olmadan `CallerMemberName` öznitelik, bir hazır değer özellik adını belirtmeniz gerekir.  
  
 Aşağıdaki grafikte üye kullandığınızda, döndürülen adları gösterir `CallerMemberName` özniteliği.  
  
|Çağrının oluştuğu yer|Üye adı sonucu|  
|-------------------------|------------------------|  
|Yöntem, özellik veya olay|Yöntemin, özelliğin veya aramanın kaynaklandığı olayın adı.|  
|Oluşturucu|".ctor" dizesi|  
|Statik oluşturucu|".cctor" dizesi|  
|Yok edici|"Finalize" dizesi|  
|Kullanıcı tanımlı işleçler veya dönüştürmeler|Üye için oluşturulan "op_Addition" gibi bir ad.|  
|Öznitelik oluşturucu|Özniteliğin uygulandığı üyenin adı. Öznitelik bir üye içerisindeki herhangi bir öğeyse (parametre, dönüş değeri veya genel tür parametresi gibi), bu sonuç bu öğeyle ilişkili öğenin adıdır.|  
|İçeren üye yok (örneğin, derleme düzeyi veya türlere uygulanan öznitelikler)|İsteğe bağlı parametrenin varsayılan değeri.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Öznitelikler (Visual Basic)](../../../visual-basic/language-reference/attributes.md)  
 [Ortak öznitelikler (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md)  
 [İsteğe bağlı parametreler](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)  
 [Programlama Kavramları (Visual Basic)](../../../visual-basic/programming-guide/concepts/index.md)
