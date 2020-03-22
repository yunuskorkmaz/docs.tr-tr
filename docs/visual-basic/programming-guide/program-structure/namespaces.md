---
title: Ad Alanları
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400675"
---
# <a name="namespaces-in-visual-basic"></a>Visual Basic'de Ad Alanları
Ad alanları bir derlemede tanımlanan nesneleri düzenler. Derlemeler, sırayla diğer ad alanları içerebilir birden çok ad alanı içerebilir. Ad alanları, sınıf kitaplıkları gibi büyük nesne grupları kullanırken belirsizliği önler ve başvuruları basitleştirir.  
  
 Örneğin, .NET Framework <xref:System.Windows.Forms.ListBox> <xref:System.Windows.Forms?displayProperty=nameWithType> ad alanındaki sınıfı tanımlar. Aşağıdaki kod parçası, bu sınıf için tam nitelikli adı kullanarak bir değişkenin nasıl bildirilir:  
  
 [!code-vb[VbVbalrApplication#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#6)]  
  
## <a name="avoiding-name-collisions"></a>Ad Çarpışmalarından Kaçınma  
 .NET Framework ad alanları, sınıf kitaplığı geliştiricisinin başka bir kitaplıkta benzer adların kullanılmasıyla engellendiği bazen *ad alanı kirliliği*olarak adlandırılan bir sorunu giderır. Varolan bileşenlerle bu çakışmalar bazen *ad çakışmaları*olarak adlandırılır.  
  
 Örneğin, adlı `ListBox`yeni bir sınıf oluşturursanız, bu sınıfı projenizde niteliksiz kullanabilirsiniz. Ancak, .NET Framework <xref:System.Windows.Forms.ListBox> sınıfını aynı projede kullanmak istiyorsanız, başvuruyu benzersiz kılmak için tam nitelikli bir başvuru kullanmanız gerekir. Başvuru benzersiz değilse, Visual Basic adı belirsiz olduğunu belirten bir hata üretir. Aşağıdaki kod örneği, bu nesnelerin nasıl bildirilen gösteriş gösterir:  
  
 [!code-vb[VbVbalrApplication#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#7)]  
  
 Aşağıdaki resimde, her ikisi de adlandırılmış `ListBox`bir nesne içeren iki ad alanı hiyerarşisi gösterilmektedir:  
  
 ![İki ad alanı hiyerarşisi gösteren ekran görüntüsü.](./media/namespaces/visual-basic-namespace-hierarchy.gif)  
  
 Varsayılan olarak, Visual Basic ile oluşturduğunuz her yürütülebilir dosya, projenizle aynı ada sahip bir ad alanı içerir. Örneğin, adlı `ListBoxProject`bir proje içinde bir nesne tanımlarsanız, yürütülebilir dosya ListBoxProject.exe adlı `ListBoxProject`bir ad alanı içerir.  
  
 Birden çok derleme aynı ad alanını kullanabilir. Visual Basic bunları tek bir ad kümesi olarak ele adatır. Örneğin, adlı `SomeNameSpace` `Assemb1`bir derlemede adı geçen bir ad alanı için sınıfları tanımlayabilir ve `Assemb2`aynı ad alanı için ek sınıflar tanımlayabilirsiniz.  
  
## <a name="fully-qualified-names"></a>Tam Nitelikli İsimler  
 Tam nitelikli adlar, nesnenin tanımlandığı ad alanının adı ile önceden belirlenmiş nesne başvurularıdır. Sınıfa bir başvuru oluşturursanız **(Proje** menüsünden **Referans Ekle'yi** seçerek) ve ardından kodunuzdaki nesne için tam nitelikli adı kullanırsanız, diğer projelerde tanımlanan nesneleri kullanabilirsiniz. Aşağıdaki kod parçası, başka bir projenin ad alanından bir nesne için tam nitelikli adın nasıl kullanılacağını gösterir:  
  
 [!code-vb[VbVbalrApplication#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#8)]  
  
 Tam nitelikli adlar, derleyicinin hangi nesnenin kullanıldığını belirlemesini mümkün kıldığı için çakışmaları engeller. Ancak, isimleri kendilerini uzun ve hantal alabilirsiniz. Bunu aşmak `Imports` için, tam nitelikli bir ad yerine kullanabileceğiniz kısaltılmış bir ad olan bir takma *ad*tanımlamak için deyimi kullanabilirsiniz. Örneğin, aşağıdaki kod örneği iki tam nitelikli ad için takma adlar oluşturur ve bu diğer adları iki nesne tanımlamak için kullanır.  
  
 [!code-vb[VbVbalrApplication#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#9)]  
  
 [!code-vb[VbVbalrApplication#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#10)]  
  
 İfadeyi `Imports` takma ad olmadan kullanırsanız, projeye özgü olmaları koşuluyla, bu ad alanındaki tüm adları nitelik siz de kullanabilirsiniz. Projeniz aynı `Imports` ada sahip öğeler içeren ad alanları için deyimler içeriyorsa, bu adı kullandığınızda tam olarak nitelemeniz gerekir. Örneğin, projenizin aşağıdaki iki `Imports` deyim içerdiğini varsayalım:  
  
 [!code-vb[VbVbalrApplication#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#11)]  
  
 Tam olarak nitelemeden kullanmaya `Class1` çalışırsanız, Visual Basic adının `Class1` belirsiz olduğunu belirten bir hata üretir.  
  
## <a name="namespace-level-statements"></a>Ad Alanı Düzey İfadeleri  
 Ad alanı içinde, modüller, arabirimler, sınıflar, temsilciler, sayısallamalar, yapılar ve diğer ad alanları gibi öğeleri tanımlayabilirsiniz. Ad alanı düzeyinde özellikler, yordamlar, değişkenler ve olaylar gibi öğeleri tanımlayamazsınız. Bu öğeler modüller, yapılar veya sınıflar gibi kapsayıcılar içinde bildirilmelidir.  
  
## <a name="global-keyword-in-fully-qualified-names"></a>Tam Nitelikli Adlarda Genel Anahtar Kelime  
 Ad alanları iç içe bir hiyerarşi tanımladıysanız, bu hiyerarşiiçindeki kodun .NET <xref:System?displayProperty=nameWithType> Framework ad alanına erişmeleri engellenebilir. Aşağıdaki örnekte, ad alanının `SpecialSpace.System` . <xref:System?displayProperty=nameWithType>  
  
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
  
 Sonuç olarak, Visual Basic derleyicisi başvuruyu <xref:System.Int32?displayProperty=nameWithType>başarıyla çözemiyor , çünkü `SpecialSpace.System` tanımlamaz. `Int32` .NET Framework `Global` sınıf kitaplığı en dış düzeyinde yeterlilik zincirini başlatmak için anahtar kelimeyi kullanabilirsiniz. Bu, sınıf kitaplığındaki <xref:System?displayProperty=nameWithType> ad alanını veya başka bir ad alanını belirtmenizi sağlar. Aşağıdaki örnek bunu göstermektedir.  
  
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
  
 Diğer kök `Global` düzeyindeki <xref:Microsoft.VisualBasic?displayProperty=nameWithType>ad alanlarına ve projenizle ilişkili ad alanına erişmek için kullanabilirsiniz.  
  
## <a name="global-keyword-in-namespace-statements"></a>Ad Alanı İfadelerinde Genel Anahtar Kelime  
 `Global` Anahtar sözcüğü Ad Alanı [Bildirimi'nde](../../../visual-basic/language-reference/statements/namespace-statement.md)de kullanabilirsiniz. Bu, projenizin kök ad alanından bir ad alanı tanımlamanıza olanak tanır.  
  
 Projenizdeki tüm ad alanları, projenin kök ad alanını temel adatır.  Visual Studio projenizdeki tüm kodlar için varsayılan kök ad alanı olarak proje adınızı atar. Örneğin, projeniz adlandırılmışsa, `ConsoleApplication1`programlama öğeleri ad `ConsoleApplication1`alanına aittir. Beyan `Namespace Magnetosphere`ederseniz, `Magnetosphere` projedeki başvurulara `ConsoleApplication1.Magnetosphere`erişecektir.  
  
 Aşağıdaki örnekler, `Global` projenin kök ad alanı dışında bir ad alanı bildirmek için anahtar sözcüğü kullanır.  
  
 [!code-vb[VbVbalrApplication#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#22)]  
  
 Ad alanı bildiriminde, `Global` başka bir ad alanında iç içe geçemez.  
  
 Projenin **Kök Ad Alanını** görüntülemek ve değiştirmek için Uygulama [Sayfasını, Proje Tasarımcısını (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) kullanabilirsiniz.  Yeni projeler için **Kök Ad Alanı** varsayılan olarak proje adına verilir. Üst `Global` düzey ad alanı olması **için,** kutuboş olacak şekilde Kök Ad Alanı girişini temizleyebilirsiniz. **Kök Ad Alanı'nın** temizlenmesi, `Global` ad alanı bildirimlerinde anahtar kelime gereksinimini ortadan kaldırır.  
  
 Bir `Namespace` deyim .NET Framework'de de ad alanı olan bir ad bildirirse, `Global` anahtar kelime tam nitelikli bir adda kullanılmazsa .NET Framework ad alanı kullanılamaz hale gelir. Anahtar kelimeyi `Global` kullanmadan bu .NET Framework ad alanına erişimi `Global` etkinleştirmek `Namespace` için, ekstredeki anahtar kelimeyi ekleyebilirsiniz.  
  
 Aşağıdaki örnekte `Global` `System.Text` ad alanı bildiriminde anahtar sözcük vardır.  
  
 `Global` Anahtar sözcük ad alanı bildiriminde yoksa, <xref:System.Text.StringBuilder> belirtmeden `Global.System.Text.StringBuilder`erişilemedi. Adlı `ConsoleApplication1`bir proje `System.Text` için, `ConsoleApplication1.System.Text` `Global` anahtar kelime kullanılmamışsa başvurular erişilir.  
  
 [!code-vb[VbVbalrApplication#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#21)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms?displayProperty=nameWithType>
- [.NET’te bütünleştirilmiş kodlar](../../../standard/assembly/index.md)
- [References ve Imports Deyimi](references-and-the-imports-statement.md)
- [Imports Deyimi (.NET Ad Alanı ve Türü)](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Office Çözümlerinde Kod Yazma](/visualstudio/vsto/writing-code-in-office-solutions)
