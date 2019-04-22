---
title: Namespace deyimi (Visual Basic)
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
ms.openlocfilehash: 7f6b976af7933b3895f6992488d2d1532a8fc2f7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58820938"
---
# <a name="namespace-statement"></a>Namespace Deyimi
Bir ad alanının adını bildirir ve bu ad alanı içinde derlenecek bildirimi takip eden kaynak koda neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Namespace [Global.] { name | name.name }  
    [ componenttypes ]  
End Namespace  
```  
  
## <a name="parts"></a>Bölümler  
 Global  
 İsteğe bağlı. Bir ad alanı, projenin kök ad dışında tanımlamanızı sağlar. Bkz: [Visual Basic'de ad alanları](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 `name`  
 Gerekli. Ad alanını tanımlayan benzersiz bir ad. Geçerli bir Visual Basic tanımlayıcısı olmalıdır. Daha fazla bilgi için [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 `componenttypes`  
 İsteğe bağlı. Ad alanı oluşturan öğeler. Bunlar, içerir, ancak numaralandırmalar, yapılar, arabirimler, sınıflar, modülleri, temsilciler ve diğer ad alanları için sınırlı değildir.  
  
 `End Namespace`  
 Sonlandıran bir `Namespace` blok.  
  
## <a name="remarks"></a>Açıklamalar  
 Ad alanları, bir kuruluş sistemi olarak kullanılır. Bunlar, sınıflandırmak ve diğer programları ve uygulamalar için sunulan programlama öğeleri sunmak için bir yol sağlar. Bir ad alanı değil Not bir *türü* bir sınıf veya yapı olan anlamında — veri türü bir ad alanı için bir programlama öğesi bildiremezsiniz.  
  
 Tüm programlama öğesine, sonra bildirilen bir `Namespace` deyimi, ad alanına ait. Visual Basic eder ya da karşılaşana kadar öğeleri son bildirilen ad alanına derlemek bir `End Namespace` deyimi veya başka bir `Namespace` deyimi.  
  
 Bir ad alanı zaten, hatta projenizin dışında tanımlanmışsa, programlama öğeleri ekleyebilirsiniz. Bunu yapmak için kullandığınız bir `Namespace` öğeleri bu ad alanına derlemek için Visual Basic yönlendirmek için deyimi.  
  
 Kullanabileceğiniz bir `Namespace` dosya veya ad alanı düzeyinde yalnızca deyimi. Başka bir deyişle *bildirim içeriğinin* bir ad alanı, bir kaynak dosyası veya başka bir ad olmalıdır ve bir sınıf, yapı, modül, arabirimi veya yordamı olamaz. Daha fazla bilgi için [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 İçindeki başka bir ad alanını bildirebilirsiniz. Bildirmek, ancak diğer kod en içteki ad alanında bildirilen öğeler eriştiğinde, iç içe geçme hiyerarşideki tüm ad alanı adları içeren bir nitelik dize kullanması gerektiğini unutmayın. iç içe geçme düzeyi için katı sınırı yoktur.  
  
## <a name="access-level"></a>Erişim düzeyi  
 Ad alanları, sahip oldukları gibi kabul edilir bir `Public` erişim düzeyi. Bir ad alanı, aynı projede herhangi bir kod projesi başvuran diğer projeler ve projeden oluşturulan herhangi bir derleme erişilebilir.  
  
 Ad alanı düzeyinde bir ad alanı, ancak diğer herhangi bir öğe içinde değil anlamına gelir, bildirilmiş programlama öğeleri olabilir `Public` veya `Friend` erişim. Belirtilmezse, bir öğe gibi erişim düzeyini kullanır `Friend` varsayılan olarak. Ad alanı düzeyinde bildirebilirsiniz öğelerini, sınıflar, yapılar, modüller, arabirimleri, sabit listeleri ve temsilciler içerir. Daha fazla bilgi için [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
## <a name="root-namespace"></a>Kök Namespace  
 Projenizdeki tüm ad alanı adlarını temel alan bir *kök ad alanı*. Visual Studio proje adınız, projenizdeki tüm kodlar için varsayılan kök ad alanı olarak atar. Örneğin, projeniz `Payroll`, ad alanına programlama öğelerine ait `Payroll`. Bildirirseniz `Namespace funding`, söz konusu ad alanının tam adı `Payroll.funding`.  
  
 Mevcut bir ad alanında belirtmek istiyorsanız bir `Namespace` ifadesi gibi genel listeye sınıfı örnekte, kök ad alanı null bir değere ayarlayabilirsiniz. Bunu yapmak için tıklatın **proje özellikleri** gelen **proje** menüsünü ve ardından **kök ad alanı** giriş kutusu boş olmasını sağlayın. Bu genel listeye sınıfı örnekte yapmadınız, Visual Basic Derleyicisi götürecek `System.Collections.Generic` proje içinde yeni bir ad alanı olarak `Payroll`, tam adıyla `Payroll.System.Collections.Generic`.  
  
 Alternatif olarak, `Global` projenizin dışında tanımlı ad alanlarının öğelerine başvurmak için anahtar sözcüğü. Bunun yapılması, kök ad alanı olarak proje adınız korumak olanak tanır. Bu, istemeden programlama öğeleriniz olanlar var olan ad alanları ile birlikte birleştirme olasılığını azaltır. Daha fazla bilgi için "Genel anahtar sözcüğü, tam olarak nitelenmiş adlar" bölümüne bakın [Visual Basic'de ad alanları](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 `Global` Anahtar sözcüğü bir Namespace deyimi içinde de kullanılabilir. Bu, bir ad alanı, projenin kök ad dışında tanımlamanıza olanak sağlar. Daha fazla bilgi için bkz. "Genel anahtar sözcüğü, arama Namespace ifadeler" bölümünde [Visual Basic'de ad alanları](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 **Sorun giderme.** Kök ad ad alanı adları beklenmeyen bitiştirmelerini neden olabilir. Projenizin dışında tanımlı ad alanlarına başvuru yaptığınızda, Visual Basic Derleyicisi bunları kök ad alanındaki iç içe geçmiş ad alanları olarak construe. Böyle bir durumda, derleyici dış ad alanlarında zaten tanımlanmış olan tüm türleri kabul etmiyor. Bunu önlemek için kök ad alanınız "Kök Namespace" açıklandığı gibi null bir değere ayarlayın veya kullanın `Global` dış ad alanlarının erişim öğelerine anahtar sözcüğü.  
  
## <a name="attributes-and-modifiers"></a>Öznitelikler ve değiştiriciler  
 Bir ad alanına öznitelikleri uygulanamıyor. Bir öznitelik için ad alanları gibi kaynak sınıflandırıcılar anlamlı değil derleme meta bilgileri katkıda bulunur.  
  
 Bir ad alanına herhangi bir erişim veya yordam değiştiricileri ya da diğer değiştiricilere uygulanamıyor. Bu değiştiriciler, bir tür olduğundan, anlamlı değildir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir diğerinde iç içe iki ad bildirir.  
  
 [!code-vb[VbVbalrStatements#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#43)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tek bir satırda birden çok iç içe geçmiş ad alanları bildirir ve önceki örneğe eşdeğerdir.  
  
 [!code-vb[VbVbalrStatements#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#41)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, önceki örneklerde tanımlanan sınıfı erişir.  
  
 [!code-vb[VbVbalrStatements#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#42)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yeni bir genel liste sınıf çatısında önizlememiz tanımlar ve bu gruba ekler <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanı.  
  
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
- [Visual Basic'de ad alanları](../../../visual-basic/programming-guide/program-structure/namespaces.md)
