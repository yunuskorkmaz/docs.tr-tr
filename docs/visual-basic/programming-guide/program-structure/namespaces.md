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
ms.openlocfilehash: 6b320d21c33fa798ca2fd3ef5a04363d141f99f2
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45666765"
---
# <a name="namespaces-in-visual-basic"></a>Visual Basic'de Ad Alanları
Ad alanları, bir derlemede tanımlanan nesneler düzenleyin. Derlemeleri diğer ad alanlarında sırayla içerebilen birden çok ad alanları içerebilir. Ad alanları belirsizlik önlemek ve büyük nesne grupları gibi sınıf kitaplıkları kullanırken başvuruları basitleştirin.  
  
 Örneğin, [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] tanımlar <xref:System.Windows.Forms.ListBox> sınıfını <xref:System.Windows.Forms?displayProperty=nameWithType> ad alanı. Aşağıdaki kod parçası, bu sınıfın tam adını kullanarak bir değişken bildirmek gösterilmektedir:  
  
 [!code-vb[VbVbalrApplication#6](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_1.vb)]  
  
## <a name="avoiding-name-collisions"></a>Ad çakışmalarını önleme  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] ad alanları olarak da adlandırılan bir sorun gidermek *ad alanı kirliliği*, başka bir kitaplık benzer adlarında kullanımı, bir sınıf kitaplığı geliştiricisi belgelemenin içinde. Bu çakışmaları var olan bileşenleri ile adlandırılan *adı Çarpışmaları*.  
  
 Örneğin, adında yeni bir sınıf oluşturursanız `ListBox`, nitelik olmadan proje içinde kullanabilirsiniz. Ancak, kullanmak istiyorsanız [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.Windows.Forms.ListBox> sınıfı aynı projede benzersiz başvuru yapmak için tam nitelikli bir başvuru kullanmanız gerekir. Başvuru benzersiz değilse, Visual Basic adı belirsiz bildiren bir hata üretir. Aşağıdaki kod örneği, bu nesneleri bildirmek gösterilmektedir:  
  
 [!code-vb[VbVbalrApplication#7](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_2.vb)]  
  
 Her iki içeren adlı bir nesne iki ad alanı hiyerarşileri, aşağıdaki çizimde `ListBox`.  
  
 ![Namespace hiyerarşi](../../../visual-basic/programming-guide/program-structure/media/vanamespacehierarchy.gif "vaNamespaceHierarchy")  
  
 Varsayılan olarak, Visual Basic ile oluşturduğunuz her bir yürütülebilir dosya projeniz gibi aynı ada sahip bir ad alanı içerir. Örneğin, bir nesne adlı bir proje içinde tanımlarsanız `ListBoxProject`, yürütülebilir dosyayı ListBoxProject.exe adlı bir ad alanı içeren `ListBoxProject`.  
  
 Birden çok derleme, aynı ad alanını kullanabilirsiniz. Visual Basic, bunları tek bir ad kümesini değerlendirir. Örneğin, sınıflar adlandırılan bir ad alanı için tanımlayabileceğiniz `SomeNameSpace` adlı bir derlemede `Assemb1`ve aynı ad alanından adlı bir derleme için ek sınıfları tanımlama `Assemb2`.  
  
## <a name="fully-qualified-names"></a>Tam olarak nitelenmiş adlar  
 Tam nesne tanımlandığı ad alanı adı ile ön ekli nesne başvuruları adlarıdır. Sınıfa bir başvuru oluşturursanız, diğer projelerde tanımlanan nesneler kullanabilirsiniz (seçerek **Başvuru Ekle** gelen **proje** menüsü) ve kodunuzda nesnenin tam adını kullanın. Aşağıdaki kod parçası, başka bir projenin ad alanındaki nesnenin tam adı kullanma işlemini gösterir:  
  
 [!code-vb[VbVbalrApplication#8](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_3.vb)]  
  
 Tam olarak nitelenmiş adlar önlemek adlandırma bunlar derleyicinin nesnenin kullanıldığını belirlemek mümkün kılar çünkü çakışıyor. Ancak, adları, uzun ve çetrefilli elde edebilirsiniz. Bu sorunu aşmak için kullanabileceğiniz `Imports` deyimi tanımlamak için bir *diğer*— kısaltılmış adı yerine tam adını kullanabilirsiniz. Örneğin, aşağıdaki kod örneği, iki tam olarak nitelenmiş adlar için diğer ad oluşturur ve bu diğer adlar iki nesneleri tanımlamak için kullanır.  
  
 [!code-vb[VbVbalrApplication#9](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_4.vb)]  
  
 [!code-vb[VbVbalrApplication#10](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_5.vb)]  
  
 Kullanırsanız `Imports` deyimi bir diğer ad, projeye benzersiz oldukları içeren ad niteliği olmadan sağlanan tüm adlarını kullanabilirsiniz. Projeniz içeriyorsa `Imports` deyimleri aynı ada sahip öğeleri içeren ad alanları için tam olarak nitelemeniz gerekir adı kullandığınızda. Örneğin, projeniz aşağıdaki iki içeriyordu. varsayalım `Imports` ifadeleri:  
  
 [!code-vb[VbVbalrApplication#11](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_6.vb)]  
  
 Kullanmayı denerseniz `Class1` tam olarak niteleme olmadan, Visual Basic belirten bir hatayla adı üretir `Class1` belirsiz.  
  
## <a name="namespace-level-statements"></a>Namespace düzeyi deyimleri  
 Ad alanı içinde modüller, arabirimler, sınıflar, temsilciler, numaralandırmalar, yapılar ve diğer ad alanları gibi öğeleri tanımlayabilirsiniz. Özellikler, yordamlar, değişkenler ve ad alanı düzeyinde olaylar gibi öğeleri tanımlayamazsınız. Bu öğeleri modülleri, yapılar ve sınıflar gibi kapsayıcıları içinde bildirilmesi gerekir.  
  
## <a name="global-keyword-in-fully-qualified-names"></a>Global anahtar sözcüğü, tam olarak nitelenmiş adlar  
 İç içe geçmiş ad alanları hiyerarşisi tanımladıysanız, söz konusu hiyerarşi içinde kod erişimi engellenebilir <xref:System?displayProperty=nameWithType> ad alanı .NET Framework'ün. Bir hiyerarşide aşağıdaki örnekte `SpecialSpace.System` ad alanı blokları erişim <xref:System?displayProperty=nameWithType>.  
  
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
  
 Sonuç olarak, Visual Basic Derleyicisi başvuru başarıyla çözümlenemiyor <xref:System.Int32?displayProperty=nameWithType>, çünkü `SpecialSpace.System` tanımlamaz `Int32`. Kullanabileceğiniz `Global` .NET Framework sınıf kitaplığı, en dıştaki düzeyinde nitelik zinciri başlatmak için anahtar sözcüğü. Bu sayede belirtmek <xref:System?displayProperty=nameWithType> ad alanı veya Sınıf Kitaplığı'nda herhangi bir ad. Aşağıdaki örnek bunu göstermektedir.  
  
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
  
 Kullanabileceğiniz `Global` erişim gibi diğer kök düzeyinde ad alanları için <xref:Microsoft.VisualBasic?displayProperty=nameWithType>ve projenizle ilişkili herhangi bir ad alanı.  
  
## <a name="global-keyword-in-namespace-statements"></a>Global anahtar sözcüğü Namespace deyimlerinde  
 Ayrıca `Global` anahtar sözcüğü bir [Namespace deyimi](../../../visual-basic/language-reference/statements/namespace-statement.md). Bu, bir ad alanı, projenin kök ad dışında tanımlamanıza olanak sağlar.  
  
 Projenizdeki tüm ad alanlarını projenin kök ad alanını temel alır.  Visual Studio proje adınız, projenizdeki tüm kodlar için varsayılan kök ad alanı olarak atar. Örneğin, projeniz `ConsoleApplication1`, ad alanına programlama öğelerine ait `ConsoleApplication1`. Bildirirseniz `Namespace Magnetosphere`, başvurular `Magnetosphere` projede erişecek `ConsoleApplication1.Magnetosphere`.  
  
 Aşağıdaki örneklerde `Global` projenin kök ad alanı dışında bir ad alanı bildirmek için anahtar sözcüğü.  
  
 [!code-vb[VbVbalrApplication#22](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_7.vb)]  
  
 Bir ad alanı bildiriminde `Global` başka bir ad alanında iç içe olamaz.  
  
 Kullanabileceğiniz [uygulama sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) görüntülemek ve değiştirmek için **kök Namespace** proje.  Yeni projelerde **kök Namespace** varsayılan olarak projenin adı. Neden `Global` en üst düzey ad olacak şekilde temizleyebilir **kök Namespace** giriş kutusu boş olmasını sağlayın. Temizleme **kök Namespace** gereksinimini ortadan kaldırır `Global` anahtar sözcük ad alanı bildirimi.  
  
 Varsa bir `Namespace` ifade, bir ad alanı .NET Framework ayrıca bir ad bildirir, .NET Framework ad alanı kullanılamaz hale gelmesi durumunda `Global` anahtar sözcüğü, bir tam adı kullanılamıyor. Kullanmadan, .NET Framework ad alanına erişimi etkinleştirmek için `Global` anahtar sözcüğünü içerebilir `Global` anahtar sözcüğünü `Namespace` deyimi.  
  
 Aşağıdaki örnek sahip `Global` anahtar sözcüğünü `System.Text` ad alanı bildirimi.  
  
 Varsa `Global` anahtar sözcüğü ad alanı bildiriminde mevcut değildi <xref:System.Text.StringBuilder> belirtmeden erişilemedi `Global.System.Text.StringBuilder`. Adlı bir proje için `ConsoleApplication1`, başvurular `System.Text` eriştiğiniz `ConsoleApplication1.System.Text` varsa `Global` anahtar sözcüğü değil kullanıldı.  
  
 [!code-vb[VbVbalrApplication#21](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_8.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ListBox>  
- <xref:System.Windows.Forms?displayProperty=nameWithType>  
- [Derlemeler ve Genel Derleme Önbelleği](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
- [Nasıl yapılır: Komut Satırını Kullanarak Bütünleştirilmiş Kodlar Oluşturma ve Kullanma](../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)  
- [References ve Imports Deyimi](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
- [Imports Deyimi (.NET Ad Alanı ve Türü)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
- [Office Çözümlerinde Kod Yazma](/visualstudio/vsto/writing-code-in-office-solutions)
