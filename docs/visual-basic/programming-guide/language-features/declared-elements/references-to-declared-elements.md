---
title: "Bildirilmiş Öğelere Başvurular (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declared elements [Visual Basic]
- references [Visual Basic], declared elements
- qualified names [Visual Basic]
ms.assetid: d6301709-f4cc-4b7a-b8ba-80898f14ab46
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9b3847164b4e577a9265a746b9329218b4af928b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="references-to-declared-elements-visual-basic"></a>Bildirilmiş Öğelere Başvurular (Visual Basic)
Kodunuz için bildirilen bir öğe, başvurduğunda [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] derleyici adının uygun bildirimi, başvuru adı ile eşleşir. Aynı ada sahip birden fazla öğe bildirilirse, bu öğeler tarafından başvurulacak olduğu denetleyebilirsiniz *belirleme* adı.  
  
 Derleme adı bildirimiyle adı referansı eşleştirmeyi dener *dar kapsamı*. Bunun anlamı başvuru yapma kodu ile başlar ve dışa öğeleri içeren art arda gelen düzeyleri ile çalışır.  
  
 Aşağıdaki örnek, aynı ada sahip iki değişken başvuruları gösterir. Bu örnek iki değişken bildirir, her adlı `totalCount`, modüldeki kapsamının farklı düzeylerde `container`. Zaman yordamı `showCount` görüntüler `totalCount` nitelik olmadan [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] derleyici çözümler dar kapsamı, yani yerel bildirimi içinde bildirimiyle referansı `showCount`. Ne zaman niteleyen `totalCount` içeren modülü ile `container`, daha geniş kapsamlı bildirimi referansı derleyici giderir.  
  
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
 Bu arama işlemi geçersiz kılmak ve bir ad gerekir daha geniş bir kapsamda bildirilen belirtmek istiyorsanız *nitelemek* içeren bir öğesiyle daha geniş kapsam adı. Bazı durumlarda, kapsayan öğe nitelemek olabilir.  
  
 Uygun hedef öğe tanımlandığı tanımlayan bilgiler ile kaynak deyiminde önceki adı anlamına gelir. Bu bilgileri olarak adlandırılan bir *niteliğe dize*. Bir içerebilir veya daha fazla ad alanları ve bir modül sınıf veya yapı.  
  
 Niteliğe dize belirsizliğe modülü, sınıf veya yapı hedef öğe içeren belirtmeniz gerekir. Kapsayıcı sırayla başka bir kapsayıcı öğe, genellikle bir ad alanı bulunabilir. Niteliğe dizesine birkaç içeren öğe eklemek gerekebilir.  
  
#### <a name="to-access-a-declared-element-by-qualifying-its-name"></a>Bildirilen öğe adını niteleme tarafından erişmek için  
  
1.  Öğe tanımlanmış konum belirleyin. Bu, bir ad alanı veya hatta ad alanları hiyerarşisi içerebilir. En düşük düzeyde ad alanı içinde bir modül, sınıf veya yapı öğesi bulunmalıdır.  
  
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
  
2.  Hedef öğenin konum temelinde bir nitelenmiş yola belirler. En üst düzey ad alanıyla başlatmak, düşük düzeyli ad alanına devam ve modülü, sınıf ya da hedef öğe içeren yapısı ile bitmelidir. Her bir öğe yolu, kendisini izleyen öğesi içermelidir.  
  
     `outerSpace` → `innerSpace` → `holdsTotals` → `totals`  
  
3.  Niteliğe dize hedef öğe için hazırlayın. Bir süre yerleştirin (`.`) yolundaki her öğesinden sonra. Uygulamanızı her öğenin niteliğe dizenizi erişiminiz olmalıdır.  
  
    ```vb  
    outerSpace.innerSpace.holdsTotals.totals.  
    ```  
  
4.  İfade veya normal şekilde hedef öğesine başvuran atama ifadesi yazın.  
  
    ```vb  
    grandTotal = 9000  
    ```  
  
5.  Hedef öğe adı niteliğe dizesiyle koyun. Adı hemen dönem izlemelidir (`.`) modülü, sınıf veya öğeyi içeren yapısını izler.  
  
    ```vb  
    ' Assume the following module is part of your code.  
    Module accessGrandTotal  
        Public Sub setGrandTotal()  
            outerSpace.innerSpace.holdsTotals.totals.grandTotal = 9000  
        End Sub  
    End Module  
    ```  
  
6.  Derleyici niteliğe dize olduğu hedef öğe başvurusu eşleştirebilirsiniz açık ve anlaşılır bir bildirimi bulmak için kullanır.  
  
 Uygulamanız aynı ada sahip birden fazla programlama öğesi erişimi varsa bir adı başvurusu nitelemek olabilir. Örneğin, <xref:System.Windows.Forms> ve <xref:System.Web.UI.WebControls> her iki ad alanları içeren bir `Label` sınıfı (<xref:System.Windows.Forms.Label?displayProperty=nameWithType> ve <xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType>). Uygulamanız her ikisi de kullanıyorsa ya da kendi tanımladığı `Label` sınıfı, farklı ayırdetmek `Label` nesneleri. İçe veya ad alanı diğer adı içinde değişken bildirimi içerir. Aşağıdaki örnek, içeri aktarma diğer ad kullanır.  
  
```vb  
' The following statement must precede all your declarations.  
Imports win = System.Windows.Forms, web = System.Web.UI.WebControls  
' The following statement references the Windows.Forms.Label class.  
Dim winLabel As New win.Label()  
```  
  
## <a name="members-of-other-containing-elements"></a>Diğer içeren öğelerini üyeleri  
 Başka bir sınıf veya yapı paylaşılmayan üyesi kullandığınızda, değişken veya sınıf veya yapı örneğine işaret ifade üye adıyla nitelemeniz gerekir. Aşağıdaki örnekte, `demoClass` adlı bir sınıf örneği `class1`.  
  
```vb  
Dim demoClass As class1 = New class1()  
demoClass.someSub[(argumentlist)]  
```  
  
 Değil üyesi nitelemek için sınıf adı kullanamazsınız [paylaşılan](../../../../visual-basic/language-reference/modifiers/shared.md). Önce bir nesne değişkeni örneğini oluşturmanız gerekir (Bu durumda `demoClass`) ve değişken adıyla başvuru.  
  
 Bir sınıf veya yapı varsa bir `Shared` üye, bu üye sınıf veya yapı adı veya bir değişkeni veya bir örneğine işaret ifade ile uygun.  
  
 Bir modül ayrı bir örneğe sahip değil ve tüm üyeleri olan `Shared` varsayılan olarak. Bu nedenle, modül adına sahip bir modül üye nitelemek.  
  
 Aşağıdaki örnek, tam modül üye yordam başvurularını gösterir. İki örnek bildirir `Sub` yordamları, her ikisi de adlı `perform`, farklı bir proje modüllerde. Her biri kendi modülü içinde niteliğe olmadan belirtildi ancak başka bir yerde gelen başvurulan tam olması gerekir. Son başvuru olduğundan `module3` uygun değil `perform`, derleyici, başvurusu çözümlenemiyor.  
  
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
 Kullanmak için [ortak](../../../../visual-basic/language-reference/modifiers/public.md) öğesi, başka bir projede tanımlandı ilk ayarlamalısınız bir *başvuru* projenin derleme veya tür kitaplığı. Bir başvuru ayarlamak için tıklatın **Başvuru Ekle** üzerinde **proje** menüsü veya kullanım [/Reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) komut satırı derleyici seçeneği.  
  
 Örneğin, XML nesne modelini kullanabilirsiniz [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Bir başvuru ayarlayın, <xref:System.Xml> ad alanı, bildirme ve onun sınıflarından herhangi biriyle gibi kullanma <xref:System.Xml.XmlDocument>. Aşağıdaki örnek kullanır <xref:System.Xml.XmlDocument>.  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As System.Xml.XmlDocument  
```  
  
## <a name="importing-containing-elements"></a>Öğeleri içeren içeri aktarma  
 Kullanabileceğiniz [Imports deyimi (.NET Namespace ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) için *alma* modüller veya kullanmak istediğiniz sınıfları içeren ad alanları. Bu, tam olarak nitelikli kendi adlar olmadan içeri aktarılan ad alanında tanımlanan öğe başvurmak sağlar. Aşağıdaki örnek almak için önceki örnekte yeniden yazar <xref:System.Xml> ad alanı.  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As XmlDocument  
```  
  
 Ayrıca, `Imports` deyimi tanımlayabilirsiniz bir *diğer alma* içeri aktarılan her ad alanı için. Bu, kaynak kodu daha kısa ve daha kolay okunabilir hale getirebilirsiniz. Aşağıdaki örnek kullanmak için önceki örnekte yeniden yazar `xD` için diğer ad olarak <xref:System.Xml> ad alanı.  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports xD = System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As xD.XmlDocument  
```  
  
 `Imports` Deyimi yapmaz başka proje öğelerinden uygulamanız için kullanılabilir. Diğer bir deyişle, bir başvuru ayarlama yer almaz. Bir ad alanı yalnızca içeri aktarma, bu ad alanında tanımlı adları nitelemeniz gereksinimini ortadan kaldırır.  
  
 Aynı zamanda `Imports` modülleri, sınıflar, yapılar ve numaralandırmalar almak için deyimi. Daha sonra içeri aktarılan bu öğeler niteliğe olmadan üyeleri kullanabilirsiniz. Bununla birlikte, her zaman sınıfları ve yapıları değişkeni ya da bir sınıf veya yapı örneğine değerlendirir ifade ile paylaşılmayan üyeleri nitelemeniz gerekir.  
  
## <a name="naming-guidelines"></a>Adlandırma yönergeleri  
 Aynı ada sahip iki veya daha fazla programlama öğeleri tanımlarken bir *ad belirsizliği* derleyici bu adı için bir başvuru çözümlemeye çalışırken neden olabilir. Kapsamında birden çok tek bir tanım ise veya tanım kapsamları dahilinde olması durumunda irresolvable başvurudur. Örneğin, "Tam başvuru örnek" üzerinde bu yardım sayfasına bakın.  
  
 Tüm öğeleri benzersiz adlar sağlayarak ad belirsizliği önleyebilirsiniz. Daha sonra bir ad alanı, modül veya sınıf adıyla nitelemek gerek kalmadan herhangi bir öğeye başvuru yapabilirsiniz. Ayrıca, yanlışlıkla yanlış öğesine başvuran olasılığını de azaltın.  
  
## <a name="shadowing"></a>Gölgeleme  
 İki programlama öğeleri aynı adı paylaşan, bunlardan birini gizleyebilirsiniz, veya *gölge*, diğerinde. Gölgeli bir öğe için başvuru kullanılabilir değil; Bunun yerine, kodunuzu kullandığında gölgeli öğe adı [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] derleyici onu gölgeleme öğesine giderir. Örnekleri içeren daha ayrıntılı bir açıklaması için bkz: [Visual Basic'de gölgeleme](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bildirilen öğe adları](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Bildirilen öğe özellikleri](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [Proje ve çözüm özelliklerini yönetme](/visualstudio/ide/managing-project-and-solution-properties)  
 [Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [Imports deyimi (.NET Namespace ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [New işleci](../../../../visual-basic/language-reference/operators/new-operator.md)  
 [Ortak](../../../../visual-basic/language-reference/modifiers/public.md)
