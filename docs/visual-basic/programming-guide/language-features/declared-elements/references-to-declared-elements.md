---
title: Bildirilmiş Öğelere Başvurular
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic]
- references [Visual Basic], declared elements
- qualified names [Visual Basic]
ms.assetid: d6301709-f4cc-4b7a-b8ba-80898f14ab46
ms.openlocfilehash: 23bff2eb098982f67ecb1b709e59096d5259a644
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405189"
---
# <a name="references-to-declared-elements-visual-basic"></a>Bildirilmiş Öğelere Başvurular (Visual Basic)
Kodunuz, belirtilen bir öğeye başvurduğunda, Visual Basic derleyici, bu adın uygun bildirimine başvurinizdeki adla eşleşir. Aynı ada sahip birden fazla öğe bildirilirse, adını *niteleyerek* bu öğelerin ne şekilde başvurulduğunu kontrol edebilirsiniz.  
  
 Derleyici, bir ad başvurusunu en *dar kapsamlı*bir ad bildirimine eşleştirmeye çalışır. Bu, başvuru yapan kod ile başladığı ve kapsayan öğelerin birbirini izleyen düzeylerinde dışa doğru çalışacağı anlamına gelir.  
  
 Aşağıdaki örnek, aynı ada sahip iki değişkene yapılan başvuruları gösterir. Örnek, her adı, `totalCount` modüldeki farklı kapsam düzeylerinde olan iki değişken bildirir `container` . Yordam, `showCount` `totalCount` nitelik olmadan görüntülendiğinde, Visual Basic derleyici, en dar kapsama sahip bildirime başvuruyu çözer, yani içinde yerel bildirim `showCount` . `totalCount`Kapsayıcı modül ile nitelediğinde `container` , derleyici daha geniş kapsamlı bir bildirime başvuruyu çözer.  
  
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
  
## <a name="qualifying-an-element-name"></a>Öğe adını nitelendirme  
 Bu arama işlemini geçersiz kılmak ve daha geniş bir kapsamda belirtilen bir ad belirtmek istiyorsanız, adı daha geniş kapsamın kapsayan öğesiyle *nitelemeniz* gerekir. Bazı durumlarda, kapsayan öğesini de nitelemeniz gerekebilir.  
  
 Bir adın nitelemesini, kaynak deyiminizde, hedef öğenin nerede tanımlandığını tanımlayan bilgilerle daha önce anlamına gelir. Bu bilgilere bir *nitelik dizesi*adı verilir. Bir veya daha fazla ad alanı ve bir modül, sınıf ya da yapı içerebilir.  
  
 Nitelik dizesi, hedef öğeyi içeren modülü, sınıfı veya yapıyı kesin olarak belirtmelidir. Kapsayıcı, genellikle bir ad alanı olan başka bir kapsayan öğede bulunabilir. Nitelik dizesinde içerilen birkaç öğe eklemeniz gerekebilir.  
  
#### <a name="to-access-a-declared-element-by-qualifying-its-name"></a>Adı niteleyerek, belirtilen bir öğeye erişmek için  
  
1. Öğenin tanımlandığı konumu saptayın. Bu, bir ad alanı ya da bir ad uzayı hiyerarşisi içerebilir. En düşük düzey ad alanı içinde, öğe bir modül, sınıf veya yapıda bulunmalıdır.  
  
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
  
2. Hedef öğenin konumuna göre bir nitelik yolu belirleme. En üst düzey ad alanıyla başlayın, en düşük düzey ad alanına ilerleyin ve hedef öğeyi içeren modül, sınıf ya da yapıyla sonlandırın. Yoldaki her öğe, takip eden öğesi içermelidir.  
  
     `outerSpace`→ `innerSpace` → `holdsTotals` →`totals`  
  
3. Hedef öğe için nitelik dizesini hazırlayın. `.`Yoldaki her öğeden sonra bir nokta () koyun. Uygulamanızın, nitelik dizinizdeki her öğeye erişimi olmalıdır.  
  
    ```vb  
    outerSpace.innerSpace.holdsTotals.totals.  
    ```  
  
4. Hedef öğeye başvuran ifade veya atama deyimini normal şekilde yazın.  
  
    ```vb  
    grandTotal = 9000  
    ```  
  
5. Hedef öğe adından önce nitelik dizesiyle önce. Ad, `.` öğeyi içeren modülün, sınıfın veya yapının takip eden period 'ı () hemen izlemelidir.  
  
    ```vb  
    ' Assume the following module is part of your code.  
    Module accessGrandTotal  
        Public Sub setGrandTotal()  
            outerSpace.innerSpace.holdsTotals.totals.grandTotal = 9000  
        End Sub  
    End Module  
    ```  
  
6. Derleyici, hedef öğe başvurusuyla eşleşlebileceği açık, belirsiz bir bildirim bulmak için nitelik dizesini kullanır.  
  
 Ayrıca, uygulamanızın aynı ada sahip birden fazla programlama öğesine erişimi varsa, bir ad başvurusunu nitelemeniz gerekebilir. Örneğin, <xref:System.Windows.Forms> ve <xref:System.Web.UI.WebControls> ad alanları her ikisi de bir `Label` Sınıf ( <xref:System.Windows.Forms.Label?displayProperty=nameWithType> ve <xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType> ) içerir. Uygulamanız her ikisini de kullanıyorsa veya kendi sınıfını tanımlıyorsa, `Label` farklı nesneleri ayırt etmeniz gerekir `Label` . Ad alanını veya içeri aktarma diğer adını değişken bildirimine ekleyin. Aşağıdaki örnek, içeri aktarma diğer adını kullanır.  
  
```vb  
' The following statement must precede all your declarations.  
Imports win = System.Windows.Forms, web = System.Web.UI.WebControls  
' The following statement references the Windows.Forms.Label class.  
Dim winLabel As New win.Label()  
```  
  
## <a name="members-of-other-containing-elements"></a>Diğer öğeleri Içeren Üyeler  
 Başka bir sınıfın veya yapının paylaşılmayan bir üyesini kullandığınızda, önce üye adını bir sınıf veya yapının örneğine işaret eden bir değişkenle veya ifadeyle nitelemeniz gerekir. Aşağıdaki örnekte, `demoClass` adlı bir sınıfının örneğidir `class1` .  
  
```vb  
Dim demoClass As class1 = New class1()  
demoClass.someSub[(argumentlist)]  
```  
  
 [Paylaşılmayan](../../../language-reference/modifiers/shared.md)bir üyeyi nitelemek için sınıf adının kendisini kullanamazsınız. Önce bir nesne değişkeninde (Bu örnekte) bir örnek oluşturmanız `demoClass` ve ardından değişken adına göre başvurmalısınız.  
  
 Bir sınıf veya yapının `Shared` üyesi varsa, bu üyeyi sınıf veya yapı adıyla veya bir örneğe işaret eden bir değişken ya da ifadeyle niteleyebilirsiniz.  
  
 Bir modül ayrı örneklere sahip değildir ve tüm üyeleri `Shared` Varsayılan olarak ' dir. Bu nedenle bir modül üyesini modül adıyla niteleyebilirsiniz.  
  
 Aşağıdaki örnek, modül üye yordamlarına nitelikli başvuruları gösterir. Örnek, `Sub` hem adında hem de `perform` bir projedeki farklı modüllerde iki yordam bildirir. Her biri kendi modülünde nitelenmeden belirlenebilir, ancak başka herhangi bir yerden başvuruluyorsa nitelenmelidir. İçindeki son başvuru uygun olmadığından `module3` `perform` , derleyici bu başvuruyu çözemez.  
  
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
  
## <a name="references-to-projects"></a>Projelere başvurular  
 Başka bir projede tanımlanmış [ortak](../../../language-reference/modifiers/public.md) öğeleri kullanmak için, önce bu projenin derlemesine veya tür kitaplığına bir *başvuru* ayarlamanız gerekir. Bir başvuru ayarlamak için **Proje** menüsünde **Başvuru Ekle** ' ye tıklayın veya [-Reference (Visual Basic)](../../../reference/command-line-compiler/reference.md) komut satırı derleyici seçeneğini kullanın.  
  
 Örneğin, .NET Framework XML nesne modelini kullanabilirsiniz. Ad alanına bir başvuru ayarlarsanız, <xref:System.Xml> sınıfının herhangi birini (gibi) bildirebilir ve kullanabilirsiniz <xref:System.Xml.XmlDocument> . Aşağıdaki örnek kullanılmıştır <xref:System.Xml.XmlDocument> .  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As System.Xml.XmlDocument  
```  
  
## <a name="importing-containing-elements"></a>Içerilen öğeleri içeri aktarma  
 Kullanmak istediğiniz modülleri veya sınıfları içeren ad alanlarını *içeri aktarmak* Için [Imports Ifadesini (.net ad alanı ve türü)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) kullanabilirsiniz. Bu, adlarını tamamen nitelemeden içeri aktarılan bir ad alanında tanımlanan öğelere başvurmanızı sağlar. Aşağıdaki örnek, ad alanını içeri aktarmak için önceki örneği yeniden yazar <xref:System.Xml> .  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As XmlDocument  
```  
  
 Ayrıca, ifade, `Imports` içeri aktarılan her ad alanı için bir *içeri aktarma diğer adı* tanımlayabilir. Bu, kaynak kodu daha kısa ve daha kolay okunabilir hale getirir. Aşağıdaki örnek, `xD` ad alanı için bir diğer ad olarak kullanmak üzere önceki örneği yeniden yazar <xref:System.Xml> .  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports xD = System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As xD.XmlDocument  
```  
  
 Bu `Imports` ifade, uygulamanız için kullanılabilir olan diğer projelerden öğe yapmaz. Diğer bir deyişle, bir başvuru ayarlamanın yerini almaz. Bir ad alanını içeri aktarmak, bu ad alanında tanımlanan adları nitelendirmek için gereken gereksinimi ortadan kaldırır.  
  
 Ayrıca, `Imports` modülleri, sınıfları, yapıları ve numaralandırmalar içeri aktarmak için ifadesini de kullanabilirsiniz. Daha sonra, bu içeri aktarılan öğelerin üyelerini nitelik olmadan kullanabilirsiniz. Ancak, sınıfların ve yapıların paylaşılmayan üyelerini her zaman, sınıf veya yapının bir örneğini değerlendiren bir değişkenle veya ifadeyle nitelemeniz gerekir.  
  
## <a name="naming-guidelines"></a>Adlandırma Kuralları  
 Aynı ada sahip iki veya daha fazla programlama öğesi tanımladığınızda, derleyici bu ada bir başvuruyu çözmeyi denediğinde bir *ad belirsizliğe* neden olabilir. Kapsam içinde birden fazla tanım varsa veya kapsam içinde bir tanım yoksa, başvuru ırıolarak çözülebilir. Bir örnek için, bu Yardım sayfasında "nitelikli başvuru örneği" başlığına bakın.  
  
 Tüm öğelerinizi benzersiz adlara vererek ad belirsizliğe engel olabilirsiniz. Daha sonra, adını bir ad alanı, modül veya sınıf ile nitelendirmek zorunda kalmadan herhangi bir öğeye başvuru yapabilirsiniz. Yanlışlıkla yanlış öğeye başvurma olasılığını da azaltabilirsiniz.  
  
## <a name="shadowing"></a>Gölge Kullanım  
 İki programlama öğesi aynı adı paylaşıyorsa, bunlardan biri diğer birini gizleyebilir veya *gölgelendirebilir*. Gölgelendirilmiş bir öğe başvuru için kullanılamaz; Bunun yerine, kodunuz gölgeli öğe adını kullandığında, Visual Basic derleyici onu gölgeleme öğesine çözer. Örneklerle ilgili daha ayrıntılı bir açıklama için bkz. [gölgeleme Visual Basic](shadowing.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bildirilen Öğe Adları](declared-element-names.md)
- [Bildirilen Öğe Özellikleri](declared-element-characteristics.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
- [Değişkenler](../variables/index.md)
- [Imports Deyimi (.NET Ad Alanı ve Türü)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [New Işleci](../../../language-reference/operators/new-operator.md)
- [Geneldir](../../../language-reference/modifiers/public.md)
