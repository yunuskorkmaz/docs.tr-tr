---
title: Bildirilmiş Öğelere Başvurular (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic]
- references [Visual Basic], declared elements
- qualified names [Visual Basic]
ms.assetid: d6301709-f4cc-4b7a-b8ba-80898f14ab46
ms.openlocfilehash: 0fca02ab2dcb507c1129f18f31a25c7809fc9710
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61917962"
---
# <a name="references-to-declared-elements-visual-basic"></a>Bildirilmiş Öğelere Başvurular (Visual Basic)
Kodunuz için bildirilen bir öğe başvurduğunda, Visual Basic Derleyicisi, adı uygun bildirimi, başvuru adı eşleşir. Aynı ada sahip birden fazla öğe bildirilmişse, bu öğeleri tarafından başvurulan olan denetleyebilirsiniz *uygun* adı.  
  
 Derleme adı başvuru adı bildirimi ile eşleştirmeyi dener *kapsamdan*. Başka bir deyişle, başvuru yapan koda ile başlar ve dışa doğru öğeleri içeren art arda gelen düzeyleri ile çalışır.  
  
 Aşağıdaki örnek, aynı ada sahip iki değişken başvuruları gösterir. Örnekte iki değişkenler bildirilmektedir, her adlı `totalCount`, kapsamın modülünde farklı düzeylerde `container`. Zaman yordamı `showCount` görüntüler `totalCount` niteleme olmadan Visual Basic Derleyicisi dar kapsamlı özelliği içindeki yerel bildirim bildirimi başvuruyu çözümler `showCount`. Ne zaman niteleyen `totalCount` içeren modülü ile `container`, derleyici daha geniş kapsamlı bildirimi başvuruyu çözümler.  
  
```vb  
' Assume these two modules are both in the same assembly.  
Module container  
    Public totalCount As Integer = 1  
    Public Sub showCount()  
        Dim totalCount As Integer = 6000  
        ' The following statement displays the local totalCount (6000).  
        MsgBox("Unqualified totalCount is " & CStr(totalCount))  
        ' The following statement displays the module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
Module callingModule  
    Public Sub displayCount()  
        container.showCount()  
        ' The following statement displays the containing module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
```  
  
## <a name="qualifying-an-element-name"></a>Bir öğe adı niteleme  
 Bu arama işlemi geçersiz kılabilir ve gerekir daha geniş bir kapsamda bildirilen bir ad belirtmek istiyorsanız *uygun* adı ile daha geniş kapsam kapsayıcı öğe. Bazı durumlarda, kapsayıcı öğe nitelemek olabilir.  
  
 Uygun. hedef öğenin tanımlandığı tanımlayan bilgiler ile kaynak deyiminde önceki adı anlamına gelir. Bu bilgiler adlı bir *nitelik dize*. Bir içerebilir veya daha fazla ad alanları ve bir modül, sınıf veya yapı.  
  
 Nitelik dize adlı modül, sınıf veya yapının hedef öğe içeren belirtmeniz gerekir. Kapsayıcı başka bir kapsayıcı öğe içinde genellikle bir ad alanı sırayla bulunabilir. Nitelik dizesine birkaç içeren öğeleri dahil etmek gerekebilir.  
  
#### <a name="to-access-a-declared-element-by-qualifying-its-name"></a>Bildirilen öğe adını nitelendirme tarafından erişmek için  
  
1. Öğe tanımlanmış konumu belirlenemiyor. Bu, bir ad veya hatta ad alanları hiyerarşisi içerebilir. En düşük düzey ad alanı içinde bir modül, sınıf veya yapı öğe bulunmalıdır.  
  
    ```vb  
    ' Assume the following hierarchy exists outside your code.  
    Namespace outerSpace  
        Namespace innerSpace  
            Module holdsTotals  
                Public Structure totals  
                    Public thisTotal As Integer  
                    Public Shared grandTotal As Long  
                End Structure  
            End Module  
        End Namespace  
    End Namespace  
    ```  
  
2. Hedef öğenin konumuna göre bir nitelenmiş yola belirleyin. En üst düzey ad alanı ile devam etmek için en düşük düzey ad alanı ve modül, sınıf veya hedef öğe içeren yapı ile bitmelidir. Yolun her öğeyi takip eden öğe içermelidir.  
  
     `outerSpace` → `innerSpace` → `holdsTotals` → `totals`  
  
3. Nitelik dize hedef öğe için hazırlayın. Bir nokta koyun (`.`) sonra her öğenin yolu. Uygulamanızı her öğe nitelik dizenizi erişiminiz olmalıdır.  
  
    ```vb  
    outerSpace.innerSpace.holdsTotals.totals.  
    ```  
  
4. İfade veya normal bir şekilde hedef öğeye başvuran atama ifadesi yazın.  
  
    ```vb  
    grandTotal = 9000  
    ```  
  
5. Hedef öğe adı nitelik dizesiyle koyun. Ad, dönem hemen izlemelidir (`.`) modülü, sınıf veya öğeyi içeren yapı izler.  
  
    ```vb  
    ' Assume the following module is part of your code.  
    Module accessGrandTotal  
        Public Sub setGrandTotal()  
            outerSpace.innerSpace.holdsTotals.totals.grandTotal = 9000  
        End Sub  
    End Module  
    ```  
  
6. Derleyici nitelik dizesi için hedef öğe başvurusu eşleşebilir açık ve anlaşılır bir bildirimi bulmak için kullanır.  
  
 Uygulamanız aynı ada sahip birden fazla programlama öğesine erişimi varsa ad başvuru nitelemek olabilir. Örneğin, <xref:System.Windows.Forms> ve <xref:System.Web.UI.WebControls> her iki ad alanları içeren bir `Label` sınıfı (<xref:System.Windows.Forms.Label?displayProperty=nameWithType> ve <xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType>). Uygulamanız hem de kullanıyorsa veya kendi tanımlıyorsa `Label` sınıfı, farklı ayırdetmek `Label` nesneleri. Değişken bildiriminde içe veya ad alanı diğer adı içerir. Aşağıdaki örnek, içeri aktarma diğer ad kullanır.  
  
```vb  
' The following statement must precede all your declarations.  
Imports win = System.Windows.Forms, web = System.Web.UI.WebControls  
' The following statement references the Windows.Forms.Label class.  
Dim winLabel As New win.Label()  
```  
  
## <a name="members-of-other-containing-elements"></a>Diğer içeren öğeleri üyeleri  
 Paylaşılmayan başka bir sınıf veya yapı üyesi kullandığınızda, önce bir değişkenin veya ifadenin sınıfın veya yapının örneğine işaret eden üye adıyla nitelemeniz gerekir. Aşağıdaki örnekte, `demoClass` adlı bir sınıfın bir örneği `class1`.  
  
```vb  
Dim demoClass As class1 = New class1()  
demoClass.someSub[(argumentlist)]  
```  
  
 Sınıf adı olmayan bir üye nitelemek için kullanamazsınız [paylaşılan](../../../../visual-basic/language-reference/modifiers/shared.md). Öncelikle bir nesne değişkeninin örneği oluşturmanız gerekir (Bu durumda `demoClass`) ve değişken adıyla başvurun.  
  
 Bir sınıf veya yapı varsa bir `Shared` üye bu üyenin sınıf veya yapı adı veya bir değişkeni veya bir örneğine işaret eden ifade uygun.  
  
 Ayrı bir örneğinin bir modül yok ve tüm üyeleri `Shared` varsayılan olarak. Bu nedenle, modül ada sahip bir modül üye nitelendirin.  
  
 Aşağıdaki örnek, tam modülü üye yordamlarına yönelik başvuruları gösterir. İki örnek bildirir `Sub` yordamları, hem adlandırılmış `perform`, bir projede farklı modül içinde. Her biri kendi modül içinde nitelik olmadan belirtilebilir ancak başka bir yerde gelen başvurulan nitelenmiş olmalıdır. En son başvurusunun çünkü `module3` uygun değil `perform`, derleyici bu başvurusu çözümlenemiyor.  
  
```vb  
' Assume these three modules are all in the same assembly.  
Module module1  
    Public Sub perform()  
        MsgBox("module1.perform() now returning")  
    End Sub  
End Module  
Module module2  
    Public Sub perform()  
        MsgBox("module2.perform() now returning")  
    End Sub  
    Public Sub doSomething()  
        ' The following statement calls perform in module2, the active module.  
        perform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
    End Sub  
End Module  
Module module3  
    Public Sub callPerform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
        ' The following statement makes an unresolvable name reference  
        ' and therefore generates a COMPILER ERROR.  
        perform() ' INVALID statement  
    End Sub  
End Module  
```  
  
## <a name="references-to-projects"></a>Proje başvuruları  
 Kullanılacak [genel](../../../../visual-basic/language-reference/modifiers/public.md) başka bir projede tanımlanan öğeleri, ilk ayarlamalısınız bir *başvuru* projenin derleme veya tür kitaplığına. Bir başvuru ayarlamak için tıklayın **Başvuru Ekle** üzerinde **proje** menü veya kullanım [/Reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) derleyici komut satırı seçeneği.  
  
 Örneğin, XML nesne modeli kullanabilirsiniz [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Bir başvuru ayarlamanız <xref:System.Xml> ad alanı, bildirme ve herhangi bir alt sınıfı gibi kullanma <xref:System.Xml.XmlDocument>. Aşağıdaki örnekte <xref:System.Xml.XmlDocument>.  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As System.Xml.XmlDocument  
```  
  
## <a name="importing-containing-elements"></a>Öğeleri içeren içeri aktarma  
 Kullanabileceğiniz [Imports deyimi (.NET Namespace ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) için *alma* modüller veya kullanmak istediğiniz sınıfları içeren ad alanları. Bu, tam adlarını niteleme olmadan bir içeri aktarılan ad alanında tanımlanan öğeler başvurmak sağlar. Aşağıdaki örnek, içeri aktarmak için önceki örnekte yeniden yazar <xref:System.Xml> ad alanı.  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As XmlDocument  
```  
  
 Ayrıca, `Imports` deyimi tanımlayabilirsiniz bir *diğer içeri aktarma* için her bir içeri aktarılan ad alanı. Bu, kaynak kodu daha kısa ve okunması kolay hale getirebilirsiniz. Aşağıdaki örnek, önceki örneğin yeniden yazar `xD` için bir diğer ad olarak <xref:System.Xml> ad alanı.  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports xD = System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As xD.XmlDocument  
```  
  
 `Imports` Deyimi yapmaz öğeleri diğer projelerden uygulamanız için kullanılabilir. Diğer bir deyişle, bir başvuru ayarlama yer almaz. Yalnızca bir ad alanı alma, o ad alanında tanımlanan adlar nitelemek için gereksinimini ortadan kaldırır.  
  
 Ayrıca `Imports` modülleri, sınıflar, yapılar ve sabit listeleri içeri aktarma deyimi. Daha sonra içeri aktarılan tür öğeleri nitelik olmadan üyeleri de kullanabilirsiniz. Ancak, sınıfları ve yapıları bir değişken veya sınıf veya yapının örneği için değerlendirilen bir ifade ile paylaşılmayan üyelerinin her zaman nitelemeniz gerekir.  
  
## <a name="naming-guidelines"></a>Adlandırma Kuralları  
 Aynı ada sahip iki veya daha fazla programlama öğeleri tanımlarken bir *ad belirsizliği* derleyici bir başvuru adı çözümlemeye çalışırken neden olabilir. Kapsam içinde birden çok bir tanım ise veya hiçbir tanımı kapsamları dahilinde olması durumunda, çözümlenemeyen başvurudur. Örneğin, "Tam başvuru örnek" Bu Yardım sayfasında bakın.  
  
 Tüm öğeleri benzersiz adlar sağlayarak ad belirsizliği önleyebilirsiniz. Daha sonra bir ad alanı, modül veya sınıfı adıyla nitelemeniz gerek kalmadan herhangi bir öğeye başvuru yapabilirsiniz. Ayrıca, yanlışlıkla yanlış öğesine başvuran olasılığını de azaltır.  
  
## <a name="shadowing"></a>Gölge Kullanım  
 Bunlardan biri, iki programlama öğeleri aynı adı paylaşan, gizleyebilirsiniz, veya *gölge*, diğerinde. Gölgeli öğe için başvuru kullanılabilir değil; Bunun yerine, kodunuzu gölgeli öğe adı kullandığında, Visual Basic Derleyicisi, gölgelendirme öğesine çözümler. Örnekleri içeren daha ayrıntılı bir açıklaması için bkz: [Visual Basic'de gölgeleme](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bildirilen Öğe Adları](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Bildirilen Öğe Özellikleri](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
- [Değişkenler](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Imports Deyimi (.NET Ad Alanı ve Türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [New İşleci](../../../../visual-basic/language-reference/operators/new-operator.md)
- [Public](../../../../visual-basic/language-reference/modifiers/public.md)
