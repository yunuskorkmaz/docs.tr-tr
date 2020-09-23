---
title: Ad alanları
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
ms.openlocfilehash: f4521fa10c3bb9e8e121e3c228a23061becd1741
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072203"
---
# <a name="namespaces-in-visual-basic"></a>Visual Basic'de Ad Alanları

Ad alanları bir derlemede tanımlanan nesneleri düzenler. Derlemeler birden çok ad alanı içerebilir ve bu da diğer ad alanlarını içerebilir. Ad alanları, sınıf kitaplıkları gibi büyük nesne gruplarını kullanırken belirsizlik ve başvuruları basitleştirir.  
  
 Örneğin, .NET Framework <xref:System.Windows.Forms.ListBox> <xref:System.Windows.Forms?displayProperty=nameWithType> ad alanındaki sınıfını tanımlar. Aşağıdaki kod parçası, bu sınıf için tam nitelikli adı kullanarak bir değişkenin nasıl bildirilemeyeceğini göstermektedir:  
  
 [!code-vb[VbVbalrApplication#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#6)]  
  
## <a name="avoiding-name-collisions"></a>Ad çakışmalarını önleme  

 .NET Framework ad alanları, bazen bir sınıf kitaplığı geliştiricisinin başka bir kitaplıktaki benzer adların kullanımıyla birlikte olduğu *ad alanı kirliliğine*de denilen bir sorunu ele alırlar. Var olan bileşenlerle ilgili bu çakışmalar bazen *ad çarpışmaları*olarak adlandırılır.  
  
 Örneğin, adlı yeni bir sınıf oluşturursanız `ListBox` , bunu proje içinde nitelik olmadan kullanabilirsiniz. Ancak .NET Framework <xref:System.Windows.Forms.ListBox> sınıfını aynı projede kullanmak istiyorsanız, başvuruyu benzersiz hale getirmek için tam olarak nitelenmiş bir başvuru kullanmanız gerekir. Başvuru benzersiz değilse, Visual Basic adın belirsiz olduğunu belirten bir hata üretir. Aşağıdaki kod örneği, bu nesnelerin nasıl bildirileceğini göstermektedir:  
  
 [!code-vb[VbVbalrApplication#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#7)]  
  
 Aşağıdaki çizimde adında bir nesne içeren iki ad alanı hiyerarşisi gösterilmektedir `ListBox` :  
  
 ![İki ad alanı hiyerarşisi gösteren ekran görüntüsü.](./media/namespaces/visual-basic-namespace-hierarchy.gif)  
  
 Varsayılan olarak, Visual Basic ile oluşturduğunuz her çalıştırılabilir dosya, projenizle aynı ada sahip bir ad alanı içerir. Örneğin, adlı bir proje içinde bir nesne tanımlarsanız `ListBoxProject` , çalıştırılabilir dosya ListBoxProject.exe adlı bir ad alanı içerir `ListBoxProject` .  
  
 Birden çok derleme aynı ad alanını kullanabilir. Visual Basic, bunları tek bir ad kümesi olarak değerlendirir. Örneğin, adlı bir derlemede adlı bir ad alanı için sınıflar tanımlayabilir `SomeNameSpace` `Assemb1` ve adlı bir derlemeden aynı ad alanı için ek sınıflar tanımlayabilirsiniz `Assemb2` .  
  
## <a name="fully-qualified-names"></a>Tam nitelikli adlar  

 Tam nitelikli adlar, nesnenin tanımlandığı ad alanının adı önekli nesne başvurulardır. Sınıfa bir başvuru oluşturursanız ( **Proje** menüsünden **Başvuru Ekle** ' yi seçerek) diğer projelerde tanımlı nesneleri kullanabilirsiniz ve sonra kodunuzda nesne için tam adı kullanın. Aşağıdaki kod parçası, başka bir projenin ad alanından bir nesne için tam olarak nitelenmiş adın nasıl kullanılacağını gösterir:  
  
 [!code-vb[VbVbalrApplication#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#8)]  
  
 Tam nitelikli adlar, derleyicinin hangi nesnenin kullanılmakta olduğunu belirlemesini olanaklı kıdığından, adlandırma çakışmalarını önler. Ancak, adları uzun ve çok daha fazla alabilir. Bu sorunu gidermek için, bir `Imports` *diğer*ad tanımlamak için ifadesini kullanabilirsiniz — bir tam adı yerine kullanabileceğiniz kısaltılmış bir addır. Örneğin, aşağıdaki kod örneği iki tam ad için diğer adlar oluşturur ve iki nesneyi tanımlamak için bu diğer adları kullanır.  
  
 [!code-vb[VbVbalrApplication#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#9)]  
  
 [!code-vb[VbVbalrApplication#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#10)]  
  
 `Imports`İfadesini bir diğer ad olmadan kullanırsanız, bu ad alanındaki tüm adları, proje için benzersiz olmaları şartıyla, nitelendirme olmadan kullanabilirsiniz. Projeniz `Imports` aynı ada sahip öğeleri içeren ad alanları için deyimler içeriyorsa, bu adı kullandığınızda bu adı tam olarak nitelemeniz gerekir. Örneğin, projenizin aşağıdaki iki deyimi içerdiğini varsayalım `Imports` :  
  
 [!code-vb[VbVbalrApplication#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#11)]  
  
 `Class1`Tam nitelikli olmadan kullanmaya çalışırsanız, Visual Basic adın belirsiz olduğunu belirten bir hata üretir `Class1` .  
  
## <a name="namespace-level-statements"></a>Ad alanı düzeyi deyimleri  

 Bir ad alanı içinde modüller, arabirimler, sınıflar, temsilciler, numaralandırmalar, yapılar ve diğer ad alanları gibi öğeleri tanımlayabilirsiniz. Ad alanı düzeyinde özellikler, yordamlar, değişkenler ve olaylar gibi öğeleri tanımlayamazsınız. Bu öğeler modüller, yapılar veya sınıflar gibi kapsayıcılar içinde bildirilmelidir.  
  
## <a name="global-keyword-in-fully-qualified-names"></a>Tam adlarda genel anahtar sözcük  

 İç içe geçmiş bir ad alanı hiyerarşisi tanımladıysanız, bu hiyerarşinin içindeki kodun <xref:System?displayProperty=nameWithType> .NET Framework ad alanına erişmesi engellenebilir. Aşağıdaki örnekte, `SpecialSpace.System` ad alanının erişimini engellediği bir hiyerarşi gösterilmektedir <xref:System?displayProperty=nameWithType> .  
  
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
  
 Sonuç olarak, Visual Basic derleyici öğesine başvurusunu başarıyla çözümleyemiyor <xref:System.Int32?displayProperty=nameWithType> , çünkü `SpecialSpace.System` tanımlamaz `Int32` . `Global`Anahtar sözcüğünü, .NET Framework sınıf kitaplığının en dıştaki düzeyinde nitelik zinciri başlatmak için kullanabilirsiniz. Bu, <xref:System?displayProperty=nameWithType> sınıf kitaplığında ad alanı veya diğer ad alanı belirtmenize olanak tanır. Aşağıdaki örnek bunu göstermektedir.  
  
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
  
 Gibi `Global` diğer kök düzeyi ad alanlarına <xref:Microsoft.VisualBasic?displayProperty=nameWithType> ve projenizle ilişkili herhangi bir ad alanına erişmek için öğesini kullanabilirsiniz.  
  
## <a name="global-keyword-in-namespace-statements"></a>Namespace deyimlerde Global anahtar sözcüğü  

 `Global`Bir [Namespace deyimindeki](../../language-reference/statements/namespace-statement.md)anahtar sözcüğünü de kullanabilirsiniz. Bu, projenizin kök ad alanından bir ad alanı tanımlamanızı sağlar.  
  
 Projenizdeki tüm ad alanları, projenin kök ad alanını temel alır.  Visual Studio, projenizdeki tüm kodlar için proje adınızı varsayılan kök ad alanı olarak atar. Örneğin, projeniz adlandırılmışsa `ConsoleApplication1` , programlama öğeleri ad alanına aittir `ConsoleApplication1` . Bildirirseniz `Namespace Magnetosphere` , `Magnetosphere` projedeki başvuruları erişir `ConsoleApplication1.Magnetosphere` .  
  
 Aşağıdaki örneklerde, `Global` projenin kök ad alanından dışarı bir ad alanı bildirmek için anahtar sözcüğü kullanılır.  
  
 [!code-vb[VbVbalrApplication#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#22)]  
  
 Bir ad alanı bildiriminde, `Global` başka bir ad alanında iç içe geçirilemez.  
  
 Projenin **kök ad alanını** görüntülemek ve değiştirmek Için [uygulama sayfasını, Proje tasarımcısı 'nı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) kullanabilirsiniz.  Yeni projeler için, **kök ad alanı** varsayılan olarak proje adı olur. `Global`En üst düzey ad alanı olmasını sağlamak için, **kök ad alanı** girişini temizleyerek kutunun boş olması gerekir. **Kök ad alanını** Temizleme, `Global` ad alanı bildirimlerinde anahtar kelimesinin gereksinimini ortadan kaldırır.  
  
 Bir `Namespace` deyimde .NET Framework bir ad alanı olan bir ad bildirirse, `Global` anahtar sözcüğü tam bir ad içinde kullanılmıyorsa, .NET Framework ad alanı kullanılamaz hale gelir. Anahtar sözcüğünü kullanmadan bu .NET Framework ad alanına erişimi etkinleştirmek için `Global` , `Global` anahtar sözcüğünü `Namespace` deyime ekleyebilirsiniz.  
  
 Aşağıdaki örnek, `Global` `System.Text` ad alanı bildiriminde anahtar kelimedir.  
  
 `Global`Anahtar sözcüğü ad alanı bildiriminde yoksa, <xref:System.Text.StringBuilder> belirtilmeden erişilemez `Global.System.Text.StringBuilder` . Adlı bir proje için `ConsoleApplication1` , `System.Text` `ConsoleApplication1.System.Text` `Global` anahtar sözcüğü kullanılsaydı başvurular erişim sağlar.  
  
 [!code-vb[VbVbalrApplication#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#21)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms?displayProperty=nameWithType>
- [.NET’te bütünleştirilmiş kodlar](../../../standard/assembly/index.md)
- [References ve Imports Deyimi](references-and-the-imports-statement.md)
- [Imports Deyimi (.NET Ad Alanı ve Türü)](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Office Çözümlerinde Kod Yazma](/visualstudio/vsto/writing-code-in-office-solutions)
