---
title: Namespace Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.Namespace
helpviewer_keywords:
- namespaces [Visual Basic], root
- Namespace statement [Visual Basic]
- namespaces [Visual Basic], nested
- declaring namespaces [Visual Basic], syntax
- namespaces [Visual Basic], declaring
- root namespaces
- declarations [Visual Basic], namespaces
ms.assetid: a31fbd95-9ace-4c3d-bbb1-51222a2272b2
ms.openlocfilehash: 19207a42890640bd82ec547e53eb6d833668e4b5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74329653"
---
# <a name="namespace-statement"></a>Namespace Deyimi
Bir ad alanının adını bildirir ve bildirimi takip eden kaynak kodunun bu ad alanı içinde derlenmesini sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Namespace [Global.] { name | name.name }  
    [ componenttypes ]  
End Namespace  
```  
  
## <a name="parts"></a>Bölümler  
 Global  
 İsteğe bağlı. Projenizin kök ad alanından bir ad alanı tanımlamanızı sağlar. Bkz. [Visual Basic ad alanları](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 `name`  
 Gerekli. Ad alanını tanımlayan benzersiz bir ad. Geçerli bir Visual Basic tanımlayıcısı olmalıdır. Daha fazla bilgi için bkz. [bildirilmemiş öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 `componenttypes`  
 İsteğe bağlı. Ad alanını oluşturan öğeler. Bunlar arasında, numaralandırmalar, yapılar, arabirimler, sınıflar, modüller, temsilciler ve diğer ad alanları bunlarla sınırlı değildir.  
  
 `End Namespace`  
 Bir `Namespace` bloğunu sonlandırır.  
  
## <a name="remarks"></a>Açıklamalar  
 Ad alanları bir kuruluş sistemi olarak kullanılır. Diğer programlar ve uygulamalar tarafından sunulan programlama öğelerini sınıflandırmak ve sunmak için bir yol sağlar. Bir ad alanı, bir sınıf veya yapının olduğu anlamda bir *tür* değildir; bir ad alanı veri türüne sahip olacak bir programlama öğesi bildiremezsiniz.  
  
 Bir `Namespace` deyimden sonra belirtilen tüm programlama öğeleri bu ad alanına ait. Visual Basic, bir `End Namespace` ifadesiyle veya başka bir `Namespace` ifadesiyle karşılaşana kadar öğeleri en son tanımlanan ad alanına derlemeye devam eder.  
  
 Bir ad alanı zaten tanımlanmışsa, projeniz dışında bile buna programlama öğeleri ekleyebilirsiniz. Bunu yapmak için, Visual Basic öğeleri bu ad alanına derlemek üzere yönlendirmek üzere bir `Namespace` ifadesini kullanın.  
  
 `Namespace` bir ifadesini yalnızca dosya veya ad alanı düzeyinde kullanabilirsiniz. Diğer bir deyişle, bir ad alanı için *Bildirim bağlamı* bir kaynak dosyası veya başka bir ad alanı olmalıdır ve bir sınıf, yapı, modül, arabirim veya yordam olamaz. Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Bir ad alanını başka bir ad alanı içinde bildirebilirsiniz. Bildirebileceğiniz iç içe geçme düzeylerine yönelik kesin bir sınır yoktur, ancak başka bir kod, iç içe geçmiş hiyerarşisinde belirtilen tüm ad alanı adlarını içeren bir nitelik dizesi kullanması gerektiğini unutmayın.  
  
## <a name="access-level"></a>Erişim düzeyi  
 Ad alanları `Public` erişim düzeyine sahip gibi davranır. Bir ad alanına, aynı projede yer alan koddan, projeye başvuran diğer projelerden ve projeden oluşturulan herhangi bir derlemeden erişilebilir.  
  
 Ad alanı düzeyinde tanımlanan, bir ad alanında anlamı olan ancak başka bir öğe içinde olmayan programlama öğeleri, `Public` veya `Friend` erişim içerebilir. Belirtilmemişse, böyle bir öğenin erişim düzeyi varsayılan olarak `Friend` kullanır. Ad alanı düzeyinde bildirebileceğiniz öğeler sınıflar, yapılar, modüller, arabirimler, numaralandırmalar ve temsilciler içerir. Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
## <a name="root-namespace"></a>Kök ad alanı  
 Projenizdeki tüm ad alanı adları bir *kök ad alanını*temel alır. Visual Studio, projenizdeki tüm kodlar için proje adınızı varsayılan kök ad alanı olarak atar. Örneğin, projeniz `Payroll`olarak adlandırılmışsa, programlama öğeleri ad alanı `Payroll`aittir. `Namespace funding`bildirirseniz, bu ad alanının tam adı `Payroll.funding`.  
  
 Genel liste sınıfı örneğinde olduğu gibi `Namespace` bildiriminde var olan bir ad alanı belirtmek istiyorsanız, kök ad alanınızı null bir değer olarak ayarlayabilirsiniz. Bunu yapmak için **Proje** menüsünden **Proje özellikleri** ' ne tıklayın ve ardından kutunun boş olması için **kök ad alanı** girişini temizleyin. Bunu genel liste sınıfı örneğinde yapmadıysanız, Visual Basic derleyici, `Payroll.System.Collections.Generic`tam adıyla proje `Payroll`içinde yeni bir ad alanı olarak `System.Collections.Generic` alır.  
  
 Alternatif olarak, `Global` anahtar sözcüğünü, projenizin dışında tanımlanan ad alanları öğelerine başvurmak için de kullanabilirsiniz. Bunun yapılması, proje adınızı kök ad alanı olarak korumanızı sağlar. Bu, programlama öğelerinizi, varolan ad uzaylarınızla birlikte yanlışlıkla birleştirme olasılığını azaltır. Daha fazla bilgi için [Visual Basic ad alanları](../../../visual-basic/programming-guide/program-structure/namespaces.md)Içindeki "tam adlarda genel anahtar sözcük" bölümüne bakın.  
  
 `Global` anahtar sözcüğü, bir Namespace ifadesinde de kullanılabilir. Bu, projenizin kök ad alanından bir ad alanı tanımlamanızı sağlar. Daha fazla bilgi için [Visual Basic ad alanları](../../../visual-basic/programming-guide/program-structure/namespaces.md)Içindeki "ad alanı deyimlerine genel anahtar sözcüğü" bölümüne bakın.  
  
 **Sorunu.** Kök ad alanı, ad alanı adlarının beklenmedik birleştirmeleri oluşmasına neden olabilir. Projenizin dışında tanımlanan ad alanlarına başvuru yaparsanız, Visual Basic derleyici bunları kök ad alanında iç içe geçmiş ad alanları olarak construe. Böyle bir durumda, derleyici dış ad alanlarında zaten tanımlanmış olan herhangi bir türü tanımaz. Bunu önlemek için, kök ad alanınızı "kök ad alanı" içinde açıklandığı şekilde null bir değer olarak ayarlayın veya dış ad alanlarının öğelerine erişmek için `Global` anahtar sözcüğünü kullanın.  
  
## <a name="attributes-and-modifiers"></a>Öznitelikler ve değiştiriciler  
 Bir ad alanına öznitelikler uygulayamazsınız. Bir öznitelik, verileri, ad alanları gibi kaynak sınıflandırıcılar için anlamlı olmayan derlemenin meta verilerine katkıda bulunur.  
  
 Herhangi bir erişim veya yordam değiştiricisi ya da başka bir değiştirici, bir ad alanına uygulayamazsınız. Bir tür olmadığından, bu değiştiriciler anlamlı değildir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, diğeri diğeri olan iki ad alanını bildirir.  
  
 [!code-vb[VbVbalrStatements#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#43)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, birden çok iç içe ad alanını tek bir satırda bildirir ve bu, önceki örneğe eşdeğerdir.  
  
 [!code-vb[VbVbalrStatements#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#41)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, önceki örneklerde tanımlanan sınıfa erişir.  
  
 [!code-vb[VbVbalrStatements#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#42)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, yeni bir genel liste sınıfının iskelet 'sini tanımlar ve <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanına ekler.  
  
```vb  
Namespace System.Collections.Generic  
    Class specialSortedList(Of T)  
        Inherits List(Of T)  
        ' Insert code to define the special generic list class.  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Imports Deyimi (.NET Ad Alanı ve Türü)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Bildirilen Öğe Adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Visual Basic ad alanları](../../../visual-basic/programming-guide/program-structure/namespaces.md)
