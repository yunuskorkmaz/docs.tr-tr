---
title: '{1&gt;Ad Alanları&lt;1}'
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
ms.openlocfilehash: ec892167f30a7ded739dc188ab4096cb3a5d154c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347323"
---
# <a name="namespaces-in-visual-basic"></a>Visual Basic'de Ad Alanları
Ad alanları bir derlemede tanımlanan nesneleri düzenler. Derlemeler birden çok ad alanı içerebilir ve bu da diğer ad alanlarını içerebilir. Ad alanları, sınıf kitaplıkları gibi büyük nesne gruplarını kullanırken belirsizlik ve başvuruları basitleştirir.  
  
 Örneğin .NET Framework, <xref:System.Windows.Forms?displayProperty=nameWithType> ad alanındaki <xref:System.Windows.Forms.ListBox> sınıfını tanımlar. Aşağıdaki kod parçası, bu sınıf için tam nitelikli adı kullanarak bir değişkenin nasıl bildirilemeyeceğini göstermektedir:  
  
 [!code-vb[VbVbalrApplication#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#6)]  
  
## <a name="avoiding-name-collisions"></a>Ad çakışmalarını önleme  
 .NET Framework ad alanları, bazen bir sınıf kitaplığı geliştiricisinin başka bir kitaplıktaki benzer adların kullanımıyla birlikte olduğu *ad alanı kirliliğine*de denilen bir sorunu ele alırlar. Var olan bileşenlerle ilgili bu çakışmalar bazen *ad çarpışmaları*olarak adlandırılır.  
  
 Örneğin, `ListBox`adlı yeni bir sınıf oluşturursanız, bunu proje içinde nitelik olmadan kullanabilirsiniz. Ancak, .NET Framework <xref:System.Windows.Forms.ListBox> sınıfını aynı projede kullanmak istiyorsanız, başvuruyu benzersiz hale getirmek için tam olarak nitelenmiş bir başvuru kullanmanız gerekir. Başvuru benzersiz değilse, Visual Basic adın belirsiz olduğunu belirten bir hata üretir. Aşağıdaki kod örneği, bu nesnelerin nasıl bildirileceğini göstermektedir:  
  
 [!code-vb[VbVbalrApplication#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#7)]  
  
 Aşağıdaki çizimde, her ikisi de `ListBox`adlı bir nesne içeren iki ad alanı hiyerarşisi gösterilmektedir:  
  
 ![İki ad alanı hiyerarşisi gösteren ekran görüntüsü.](./media/namespaces/visual-basic-namespace-hierarchy.gif)  
  
 Varsayılan olarak, Visual Basic ile oluşturduğunuz her çalıştırılabilir dosya, projenizle aynı ada sahip bir ad alanı içerir. Örneğin, `ListBoxProject`adlı bir proje içinde bir nesne tanımlarsanız, ListBoxProject. exe yürütülebilir dosyası `ListBoxProject`adlı bir ad alanı içerir.  
  
 Birden çok derleme aynı ad alanını kullanabilir. Visual Basic, bunları tek bir ad kümesi olarak değerlendirir. Örneğin, `Assemb1`adlı bir derlemede `SomeNameSpace` adlı bir ad alanı için sınıflar tanımlayabilir ve `Assemb2`adlı bir derlemeden aynı ad alanı için ek sınıflar tanımlayabilirsiniz.  
  
## <a name="fully-qualified-names"></a>Tam nitelikli adlar  
 Tam nitelikli adlar, nesnenin tanımlandığı ad alanının adı önekli nesne başvurulardır. Sınıfa bir başvuru oluşturursanız ( **Proje** menüsünden **Başvuru Ekle** ' yi seçerek) diğer projelerde tanımlı nesneleri kullanabilirsiniz ve sonra kodunuzda nesne için tam adı kullanın. Aşağıdaki kod parçası, başka bir projenin ad alanından bir nesne için tam olarak nitelenmiş adın nasıl kullanılacağını gösterir:  
  
 [!code-vb[VbVbalrApplication#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#8)]  
  
 Tam nitelikli adlar, derleyicinin hangi nesnenin kullanılmakta olduğunu belirlemesini olanaklı kıdığından, adlandırma çakışmalarını önler. Ancak, adları uzun ve çok daha fazla alabilir. Bu sorunu gidermek için `Imports` ifadesini kullanarak bir *diğer*ad tanımlayabilirsiniz — tam adı yerine kullanabileceğiniz kısaltılmış bir addır. Örneğin, aşağıdaki kod örneği iki tam ad için diğer adlar oluşturur ve iki nesneyi tanımlamak için bu diğer adları kullanır.  
  
 [!code-vb[VbVbalrApplication#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#9)]  
  
 [!code-vb[VbVbalrApplication#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#10)]  
  
 `Imports` ifadesini bir diğer ad olmadan kullanırsanız, bu ad alanındaki tüm adları, proje için benzersiz olmaları kaydıyla, nitelendirme olmadan kullanabilirsiniz. Projeniz aynı ada sahip öğeleri içeren ad alanları için `Imports` deyimleri içeriyorsa, bu adı kullandığınızda bu adı tam olarak nitelemeniz gerekir. Örneğin, projenizin aşağıdaki iki `Imports` deyimi içerdiğini varsayalım:  
  
 [!code-vb[VbVbalrApplication#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#11)]  
  
 Tam olarak nitelemeden `Class1` kullanmaya çalışırsanız Visual Basic, `Class1` adının belirsiz olduğunu belirten bir hata üretir.  
  
## <a name="namespace-level-statements"></a>Ad alanı düzeyi deyimleri  
 Bir ad alanı içinde modüller, arabirimler, sınıflar, temsilciler, numaralandırmalar, yapılar ve diğer ad alanları gibi öğeleri tanımlayabilirsiniz. Ad alanı düzeyinde özellikler, yordamlar, değişkenler ve olaylar gibi öğeleri tanımlayamazsınız. Bu öğeler modüller, yapılar veya sınıflar gibi kapsayıcılar içinde bildirilmelidir.  
  
## <a name="global-keyword-in-fully-qualified-names"></a>Tam adlarda genel anahtar sözcük  
 İç içe geçmiş bir ad alanı hiyerarşisi tanımladıysanız, bu hiyerarşinin içindeki kodun, .NET Framework <xref:System?displayProperty=nameWithType> ad alanına erişimi engellenmiş olabilir. Aşağıdaki örnek, `SpecialSpace.System` ad alanının <xref:System?displayProperty=nameWithType>erişimi engellediği bir hiyerarşiyi gösterir.  
  
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
  
 Sonuç olarak, `SpecialSpace.System` `Int32`tanımlamayan için Visual Basic Derleyicisi <xref:System.Int32?displayProperty=nameWithType>başvurusunu başarıyla çözümleyemiyor. `Global` anahtar sözcüğünü kullanarak, nitelendirme zincirini .NET Framework sınıf kitaplığının en dıştaki düzeyinde başlatabilirsiniz. Bu, sınıf kitaplığındaki <xref:System?displayProperty=nameWithType> ad alanını veya başka bir ad alanını belirtmenize olanak tanır. Aşağıdaki örnek bunu göstermektedir.  
  
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
  
 <xref:Microsoft.VisualBasic?displayProperty=nameWithType>gibi diğer kök düzeyi ad alanlarına ve projenizle ilişkili herhangi bir ad alanına erişmek için `Global` kullanabilirsiniz.  
  
## <a name="global-keyword-in-namespace-statements"></a>Namespace deyimlerde Global anahtar sözcüğü  
 Bir [Namespace deyimindeki](../../../visual-basic/language-reference/statements/namespace-statement.md)`Global` anahtar sözcüğünü de kullanabilirsiniz. Bu, projenizin kök ad alanından bir ad alanı tanımlamanızı sağlar.  
  
 Projenizdeki tüm ad alanları, projenin kök ad alanını temel alır.  Visual Studio, projenizdeki tüm kodlar için proje adınızı varsayılan kök ad alanı olarak atar. Örneğin, projeniz `ConsoleApplication1`olarak adlandırılmışsa, programlama öğeleri ad alanı `ConsoleApplication1`aittir. `Namespace Magnetosphere`bildirirseniz, projedeki `Magnetosphere` başvurular `ConsoleApplication1.Magnetosphere`erişir.  
  
 Aşağıdaki örneklerde, proje için kök ad alanından bir ad alanını bildirmek üzere `Global` anahtar sözcüğü kullanılır.  
  
 [!code-vb[VbVbalrApplication#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#22)]  
  
 Bir ad alanı bildiriminde, `Global` başka bir ad alanında iç içe geçirilemez.  
  
 Projenin **kök ad alanını** görüntülemek ve değiştirmek Için [uygulama sayfasını, Proje tasarımcısı 'nı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) kullanabilirsiniz.  Yeni projeler için, **kök ad alanı** varsayılan olarak proje adı olur. `Global` en üst düzey ad alanı olmasını sağlamak için, **kök ad alanı** girişini temizleyerek kutunun boş olmasını sağlayabilirsiniz. **Kök ad alanını** Temizleme, ad alanı bildirimlerinde `Global` anahtar kelimesinin gereksinimini ortadan kaldırır.  
  
 `Namespace` bir ifade .NET Framework bir ad alanı olan bir ad bildirirse, `Global` anahtar sözcüğü tam bir ad içinde kullanılmıyorsa .NET Framework ad alanı kullanılamaz hale gelir. `Global` anahtar sözcüğünü kullanmadan bu .NET Framework ad alanına erişimi etkinleştirmek için `Namespace` ifadesine `Global` anahtar sözcüğünü ekleyebilirsiniz.  
  
 Aşağıdaki örnekte, `System.Text` ad alanı bildiriminde `Global` anahtar sözcüğü vardır.  
  
 `Global` anahtar sözcüğü ad alanı bildiriminde yoksa, <xref:System.Text.StringBuilder> `Global.System.Text.StringBuilder`belirtilmeden erişilemez. `ConsoleApplication1`adlı bir proje için, `Global` anahtar sözcüğü kullanılmazsa `System.Text` başvuruları `ConsoleApplication1.System.Text` erişir.  
  
 [!code-vb[VbVbalrApplication#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#21)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms?displayProperty=nameWithType>
- [.NET’te bütünleştirilmiş kodlar](../../../standard/assembly/index.md)
- [References ve Imports Deyimi](references-and-the-imports-statement.md)
- [Imports Deyimi (.NET Ad Alanı ve Türü)](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Office Çözümlerinde Kod Yazma](/visualstudio/vsto/writing-code-in-office-solutions)
