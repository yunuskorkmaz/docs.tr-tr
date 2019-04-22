---
title: Visual Basic'de Değişken Bildirimi
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], declaring
- member variables [Visual Basic], declarations
- Dim statement [Visual Basic], variable declaration
- declaring variables [Visual Basic]
- variables [Visual Basic], scope
- variables [Visual Basic], data types
- data types [Visual Basic], variable declarations
- lifetime [Visual Basic], variables
- variables [Visual Basic], lifetime
- access levels [Visual Basic], variables
- scope [Visual Basic], declaration statements
- variables [Visual Basic], access level
- local variables [Visual Basic], declarations
- scope [Visual Basic], variables
ms.assetid: d8f10226-92b1-480f-9f53-df377b2d7e15
ms.openlocfilehash: 699737ffbe0b136af8862931fadacec26772b928
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833288"
---
# <a name="variable-declaration-in-visual-basic"></a>Visual Basic'de Değişken Bildirimi
Adı ve Özellikler belirtmek için bir değişken bildirir. Değişkenler için bildirimi deyim [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md). Konumuna ve içeriği değişkenin özelliklerini belirler.  
  
 Değişken adlandırma kuralları ve hususlar için bu konudaki [bildirilen öğe adları](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="declaration-levels"></a>Bildirim düzeyleri  
  
### <a name="local-and-member-variables"></a>Yerel ve üye değişkenleri  
 A *yerel değişken* bir yordam içinde bildirilen biridir. A *üye değişkeni* üyesi olan bir Visual Basic türü; bir sınıf, yapı veya modül içine, ancak bu sınıf, yapı veya modül iç herhangi bir yordam içinde değil Modül düzeyinde bildirilmiş.  
  
### <a name="shared-and-instance-variables"></a>Paylaşılan ve örnek değişkenleri  
 Bir sınıf veya yapı olup olmadığına paylaşıldığından üzerinde bir üye değişkeni kategorisine bağlıdır. İle bildirilirse [paylaşılan](../../../../visual-basic/language-reference/modifiers/shared.md) olduğu anahtar sözcüğü, bir *paylaşılan değişken*, ve sınıf veya yapının tüm örnekleri arasında paylaşılan tek bir kopyası bulunmaktadır.  
  
 Aksi durumda olduğu bir *örnek değişkeni*, ve her sınıfın veya yapının örneği için ayrı bir kopyası oluşturulur. Belirli bir kopyasını bir örnek değişkeni, sınıfın veya yapının içinde oluşturulduğu örneği kullanılabilir. Herhangi bir örneğine sınıfın veya yapının örneği değişkeninde bir kopyasını bağımsızdır.  
  
## <a name="declaring-data-type"></a>Verisi türünü bildirme  
 [Olarak](../../../../visual-basic/language-reference/statements/as-clause.md) yan tümcesi bildirim deyiminde veri türü veya nesne türü bildirme değişkenin tanımlamanıza izin verir. Bir değişken için aşağıdaki türlerinden herhangi birini belirtebilirsiniz:  
  
-   Basit bir veri türü, gibi `Boolean`, `Long`, veya `Decimal`  
  
-   Bir dizi ya da yapı gibi bir bileşik veri türü  
  
-   Bir nesne türü veya uygulamanızdaki veya başka bir uygulamada tanımlanmış sınıf  
  
-   A [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] gibi sınıf <xref:System.Windows.Forms.Label> veya <xref:System.Windows.Forms.TextBox>  
  
-   Bir arabirim türü, gibi <xref:System.IComparable> veya <xref:System.IDisposable>  
  
 Veri türü yinelemek zorunda kalmadan birkaç bir ifade değişkenleri bildirebilirsiniz. Değişkenleri aşağıdaki deyimlerinde `i`, `j`, ve `k` türü olarak bildirilmiş `Integer`, `l` ve `m` olarak `Long`, ve `x` ve `y` olarak`Single`:  
  
```  
Dim i, j, k As Integer  
' All three variables in the preceding statement are declared as Integer.  
Dim l, m As Long, x, y As Single  
' In the preceding statement, l and m are Long, x and y are Single.  
```  
  
 Veri türleri hakkında daha fazla bilgi için bkz. [veri türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md). Nesneleri hakkında daha fazla bilgi için bkz. [nesneler ve sınıflar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) ve [bileşenler ile programlama](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).  
  
## <a name="local-type-inference"></a>Yerel Tür Arabirimi  
 *Anlam çıkarma* olmadan bildirilen yerel değişkenlerin veri türlerini belirlemek için kullanılan bir `As` yan tümcesi. Derleyici, başlatma ifadesinin türünden değişkeninin türü çıkarır. Bu, açıkça bir türü bildirmeden değişkenler bildirmek sağlar. Aşağıdaki örnekte, her ikisi de `num1` ve `num2` tamsayı olarak kesin olarak belirlenmiştir.  
  
 [!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]  
  
 Yerel tür çıkarımı kullanmak istiyorsanız `Option Infer` ayarlanmalıdır `On`. Daha fazla bilgi için [yerel tür çıkarımı](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) ve [Option Infer deyimi](../../../../visual-basic/language-reference/statements/option-infer-statement.md).  
  
## <a name="characteristics-of-declared-variables"></a>Bildirilen değişkenlerin özellikleri  
 *Ömrü* değişkenini süre sırasında hangi BT kullanım için kullanılabilir. (Bir yordam veya sınıf gibi) bildirir öğesi varolmaya devam eder sürece genel olarak, bir değişken mevcut. Değişken, kapsayıcı öğe ömründen uzun varolan devam gerekmez, bildiriminde özel bir şey yapmanız gerekmez. Değişken, kapsayıcı öğe artık var olmaya devam yapması gerekiyorsa, dahil edebileceğiniz `Static` veya `Shared` anahtar sözcüğü, `Dim` deyimi. Daha fazla bilgi için [Visual Basic'de ömür](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
 *Kapsam* değişkeninin adını nitelemeden başvurduğu tüm kod kümesidir. Bir değişkenin kapsamı burada bildirildiği tarafından belirlenir. Kodu belirli bir bölgede yer alan adlarıyla nitelemeniz gerek kalmadan bu bölgede tanımlanan değişkenleri kullanabilirsiniz. Daha fazla bilgi için [Visual Basic'de kapsam](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).  
  
 Bir değişkenin *erişim düzeyi* erişim iznine sahip kod kapsamını olduğu. Bu erişim değiştiricisi tarafından belirlenir (gibi [genel](../../../../visual-basic/language-reference/modifiers/public.md) veya [özel](../../../../visual-basic/language-reference/modifiers/private.md)) kullandığınız `Dim` deyimi. Daha fazla bilgi için [erişim düzeyini Visual Basic'te](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Yeni değişken oluşturma](../../../../visual-basic/programming-guide/language-features/variables/how-to-create-a-new-variable.md)
- [Nasıl yapılır: İçine ve dışına bir değişken veri taşıma](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)
- [Veri Türleri](../../../../visual-basic/language-reference/data-types/index.md)
- [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)
- [Static](../../../../visual-basic/language-reference/modifiers/static.md)
- [Bildirilen Öğe Özellikleri](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [Yerel Çıkarım](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Infer Deyimi](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
