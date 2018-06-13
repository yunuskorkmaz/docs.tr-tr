---
title: Visual Basic'de Ad Alanları
ms.date: 07/20/2015
f1_keywords:
- vb.global
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- name collisions
- Global keyword [Visual Basic]
- namespace pollution
- names [Visual Basic], avoiding conflicts
- naming conflicts [Visual Basic], namespaces
- namespaces [Visual Basic], assemblies
- Visual Basic code, namespaces
- fully qualified names [Visual Basic]
- naming conventions [Visual Basic], naming conflicts
- namespaces
ms.assetid: cffac744-ab8c-4f1f-ba50-732c22ab4b88
ms.openlocfilehash: c1302bf4b424c7c03fb6c2d8132b086c4d30fd87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655564"
---
# <a name="namespaces-in-visual-basic"></a>Visual Basic'de Ad Alanları
Ad alanları, bir derlemede tanımlanan nesneleri düzenleyin. Derlemeleri sırayla diğer ad içeren birden çok ad alanları içerebilir. Ad alanları, Karışıklığı önlemek ve nesneleri oluşan büyük gruplar gibi sınıf kitaplıkları kullanırken başvuruları basitleştirin.  
  
 Örneğin, [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] tanımlar <xref:System.Windows.Forms.ListBox> sınıfını <xref:System.Windows.Forms?displayProperty=nameWithType> ad alanı. Aşağıdaki kod parçası, bu sınıf için tam olarak nitelenmiş adını kullanarak bir değişken bildirme gösterilmektedir:  
  
 [!code-vb[VbVbalrApplication#6](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_1.vb)]  
  
## <a name="avoiding-name-collisions"></a>Ad çakışmaları önleme  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] ad alanları olarak da adlandırılan bir sorun adres *ad alanı kirliliği*, başka bir kitaplıktaki benzer adlarının kullanımını da bir sınıf kitaplığı Geliştirici hampered içinde. Var olan bileşenleri ile bu çakışmaları adlandırılan *ad çakışması*.  
  
 Adlı yeni bir sınıf oluşturursanız, örneğin, `ListBox`, projenizin niteliğe olmadan içinde kullanın. Ancak, kullanmak istiyorsanız, [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.Windows.Forms.ListBox> sınıfı aynı projede başvuru benzersiz hale getirmek için tam bir başvuru kullanmanız gerekir. Visual Basic başvurusu benzersiz değilse, adı belirsiz olduğunu bildiren bir hata oluşturur. Aşağıdaki kod örneği, bu nesnelerin bildirme gösterilmiştir:  
  
 [!code-vb[VbVbalrApplication#7](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_2.vb)]  
  
 Her iki içeren adlı bir nesne iki ad alanı hiyerarşileri aşağıda gösterilmiştir `ListBox`.  
  
 ![Namespace hiyerarşi](../../../visual-basic/programming-guide/program-structure/media/vanamespacehierarchy.gif "vaNamespaceHierarchy")  
  
 Varsayılan olarak, Visual Basic ile oluşturduğunuz her yürütülebilir dosyayı projenize aynı ada sahip bir ad alanı içerir. Örneğin, bir nesne adlı bir projede tanımlarsanız `ListBoxProject`, yürütülebilir dosya ListBoxProject.exe adlı bir ad alanı içeren `ListBoxProject`.  
  
 Birden çok derleme aynı ad alanını kullanabilirsiniz. Visual Basic bunları adları tek bir dizi değerlendirir. Örneğin, sınıfları adlı bir ad alanı için tanımlayabilirsiniz `SomeNameSpace` adlı bir bütünleştirilmiş `Assemb1`ve aynı ad alanından adlı bir derleme için ek sınıflarını tanımla `Assemb2`.  
  
## <a name="fully-qualified-names"></a>Tam olarak nitelenmiş adlar  
 Nesne tanımlandığı ad alanı adı ile önek nesne başvuruları tam adlardır. Sınıfının bir başvurusunu oluşturursanız, diğer projelerinde tanımlanmış nesneleri kullanabilirsiniz (seçerek **Başvuru Ekle** gelen **proje** menüsü) ve sonra kodunuzda nesne için tam ad kullanın. Aşağıdaki kod parçası, başka bir projenin ad alanından bir nesne için tam ad kullanmayı gösterir:  
  
 [!code-vb[VbVbalrApplication#8](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_3.vb)]  
  
 Tam olarak nitelenmiş adlar önlemek adlandırma bunlar derleyici hangi nesne kullanıldığını belirlemek olası hale çakışıyor. Ancak, adları kendilerini uzun ve sıkıcı elde edebilirsiniz. Bu sorunu almak için kullanabileceğiniz `Imports` tanımlamak için deyimi bir *diğer*— bir tam ad yerine kullanabileceğiniz bir kısaltılmış adı. Örneğin, aşağıdaki kod örneği iki tam olarak nitelenmiş adlar için diğer adlar oluşturur ve bu diğer adlar iki nesneleri tanımlamak için kullanılır.  
  
 [!code-vb[VbVbalrApplication#9](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_4.vb)]  
  
 [!code-vb[VbVbalrApplication#10](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_5.vb)]  
  
 Kullanırsanız `Imports` deyimi bir diğer ad olmadan nitelik, ad alanının sağlandığından, projeye benzersiz oldukları tüm adlar kullanabilirsiniz. Projeniz içeriyorsa `Imports` deyimleri aynı ada sahip öğe içeren ad alanları için gereken tam olarak nitelemek bu adı kullandığınızda. Örneğin, aşağıdaki iki projeniz bulunan varsayalım `Imports` deyimleri:  
  
 [!code-vb[VbVbalrApplication#11](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_6.vb)]  
  
 Kullanmayı denerseniz, `Class1` tam niteleme olmadan, Visual Basic, bildiren bir hata adı üretir `Class1` belirsiz.  
  
## <a name="namespace-level-statements"></a>Namespace düzeyi deyimleri  
 Ad alanı içinde modüller, arabirimleri, sınıflar, temsilciler, numaralandırmalar, yapılar ve diğer ad alanları gibi öğeleri tanımlayabilirsiniz. Özellikler, yordamlar, değişkenler ve ad alanı düzeyinde olayları gibi öğeleri tanımlayamazsınız. Bu öğeler, modüller, yapıları ve sınıfları gibi kapsayıcılarına içinde bildirilmelidir.  
  
## <a name="global-keyword-in-fully-qualified-names"></a>Tam olarak nitelenmiş adlar genel anahtar sözcüğü  
 Ad alanları iç içe geçmiş hiyerarşisini tanımladıysanız, bu hiyerarşi içinde kod erişmesi engellenebilir <xref:System?displayProperty=nameWithType> ad alanı .NET Framework'ün. Aşağıdaki örnek bir hiyerarşide gösterilmektedir `SpecialSpace.System` ad alanı erişimi için <xref:System?displayProperty=nameWithType>.  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As System.Int32  
                Dim n As System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 Sonuç olarak, Visual Basic derleyici başarıyla başvurusu çözümlenemiyor <xref:System.Int32?displayProperty=nameWithType>, çünkü `SpecialSpace.System` tanımlamaz `Int32`. Kullanabileceğiniz `Global` .NET Framework sınıf kitaplığı en dıştaki düzeyinde niteliğe zinciri başlatmak için anahtar sözcüğü. Bu sayede belirtmek <xref:System?displayProperty=nameWithType> ad alanı veya diğer ad alanı Sınıf Kitaplığı'nda. Aşağıdaki örnek bunu göstermektedir.  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As Global.System.Int32  
                Dim n As Global.System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 Kullanabileceğiniz `Global` erişim gibi diğer kök düzeyinde ad alanları için <xref:Microsoft.VisualBasic?displayProperty=nameWithType>ve projenizi ile ilişkili herhangi bir ad alanı.  
  
## <a name="global-keyword-in-namespace-statements"></a>Namespace deyimlerinde genel anahtar sözcüğü  
 Aynı zamanda `Global` in anahtar sözcüğü bir [Namespace deyimi](../../../visual-basic/language-reference/statements/namespace-statement.md). Bu, bir ad alanı, projenin kök ad alanı dışında tanımlamanıza olanak sağlar.  
  
 Tüm ad alanlarını projenizdeki projesinin kök ad alanı esas alır.  Visual Studio Proje adına projenizdeki tüm kodları için varsayılan kök ad alanı olarak atar. Örneğin, projenizin adlı `ConsoleApplication1`, programlama öğeleri ad alanına ait `ConsoleApplication1`. Bildirirseniz `Namespace Magnetosphere`, başvurular `Magnetosphere` projede erişecek `ConsoleApplication1.Magnetosphere`.  
  
 Aşağıdaki örneklerde `Global` projesinin kök ad alanı dışında bir ad alanı bildirmek için anahtar sözcüğü.  
  
 [!code-vb[VbVbalrApplication#22](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_7.vb)]  
  
 Bir ad alanı bildirimi `Global` başka bir ad alanında iç içe olamaz.  
  
 Kullanabileceğiniz [uygulama sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) görüntülemek ve değiştirmek için **kök Namespace** projenin.  Yeni projeler için **kök Namespace** proje adının varsayılan değeri. Neden `Global` en üst düzey ad olacak şekilde, temizleyebilirsiniz **kök Namespace** giriş kutusu boş olmasını sağlayın. Temizleme **kök Namespace** gereksinimini ortadan kaldırır `Global` ad alanı bildirimleri anahtar sözcük.  
  
 Varsa bir `Namespace` ifade, bir ad alanı .NET Framework ayrıca bir ad bildirir, .NET Framework ad kullanılamaz hale varsa `Global` anahtar sözcüğü bir tam ad kullanılmaz. Kullanmadan, .NET Framework ad alanına erişimi etkinleştirmek için `Global` anahtar sözcüğü, içerebilir `Global` anahtar sözcük `Namespace` deyimi.  
  
 Aşağıdaki örnek sahip `Global` anahtar sözcük `System.Text` ad alanı bildirimi.  
  
 Varsa `Global` anahtar sözcük ad alanı bildirimi mevcut değildi <xref:System.Text.StringBuilder> belirtmeden erişilemedi `Global.System.Text.StringBuilder`. Adlı bir proje için `ConsoleApplication1`, başvurular `System.Text` erişir `ConsoleApplication1.System.Text` varsa `Global` anahtar sözcüğü olmayan kullanıldı.  
  
 [!code-vb[VbVbalrApplication#21](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_8.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ListBox>  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
 [Derlemeler ve Genel Derleme Önbelleği](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Nasıl yapılır: Komut Satırını Kullanarak Bütünleştirilmiş Kodlar Oluşturma ve Kullanma](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)  
 [References ve Imports Deyimi](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [Imports Deyimi (.NET Ad Alanı ve Türü)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [Office Çözümlerinde Kod Yazma](https://msdn.microsoft.com/library/bb608596)
