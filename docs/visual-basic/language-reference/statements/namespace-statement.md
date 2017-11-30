---
title: Namespace Deyimi
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Namespace
helpviewer_keywords:
- namespaces [Visual Basic], root
- Namespace statement [Visual Basic]
- namespaces [Visual Basic], nested
- declaring namespaces [Visual Basic], syntax
- namespaces [Visual Basic], declaring
- root namespaces
- declarations [Visual Basic], namespaces
ms.assetid: a31fbd95-9ace-4c3d-bbb1-51222a2272b2
caps.latest.revision: "39"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9863286a8eda2559ab678c77a81cc7d6063c3e3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="namespace-statement"></a>Namespace Deyimi
Bir ad alanı bildirir ve ad alanında derlenmesi için bildirimini izleyen kaynak kodunu neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Namespace [Global.] { name | name.name }  
    [ componenttypes ]  
End Namespace  
```  
  
## <a name="parts"></a>Bölümler  
 Global  
 İsteğe bağlı. Kök ad alanı projenizin dışında bir ad alanı tanımlamanızı sağlar. Bkz: [Visual Basic'de ad alanları](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 `name`  
 Gerekli. Ad alanını tanımlayan benzersiz bir ad. Geçerli bir Visual Basic tanımlayıcı olması gerekir. Daha fazla bilgi için bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 `componenttypes`  
 İsteğe bağlı. Ad alanı olun öğeleri. Bunlar arasında ancak numaralandırmalar, yapıları, arabirimleri, sınıflar, modüller, temsilciler ve diğer ad alanları için sınırlı değildir.  
  
 `End Namespace`  
 Sonlandırır bir `Namespace` bloğu.  
  
## <a name="remarks"></a>Açıklamalar  
 Ad alanları, bir kuruluş sistemi olarak kullanılır. Bunlar, sınıflandırmak ve diğer programları ve uygulamaları sunulan programlama öğeleri sunmak için bir yol sağlar. Bir ad değil Not bir *türü* bir sınıf veya yapı herkese açık — bir ad alanı veri türüne sahip bir programlama öğesi bildiremezsiniz.  
  
 Sonra tüm programlama öğeleri bildirilen bir `Namespace` deyimi bu ad alanına ait. Visual Basic devam eder ya da bulduğu kadar öğeleri son bildirilen ad alanına derlemek bir `End Namespace` deyimi veya başka bir `Namespace` deyimi.  
  
 Bir ad alanı zaten, hatta projenizi dışında tanımlanmışsa, programlama öğeleri ekleyebilirsiniz. Bunu yapmak için kullandığınız bir `Namespace` öğeleri bu ad alanına derlemek için Visual Basic yönlendirmek için deyimi.  
  
 Kullanabileceğiniz bir `Namespace` dosya veya ad alanı düzeyinde yalnızca deyimi. Yani *bildirimi bağlam* için bir ad alanı kaynak dosyası veya başka bir ad olmalıdır ve bir sınıf, yapı, modülü, arabirimi veya yordamı olamaz. Daha fazla bilgi için bkz: [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 İçinde başka bir ad alanı bildirebilir. Declare, ancak başka bir kod en içteki ad alanında bildirilen öğeler eriştiğinde, iç içe geçmiş hiyerarşideki tüm ad alanı adlarını içeren bir niteliği dize kullanması gerektiğini unutmayın iç içe geçme düzeyleri katı bir sınır yoktur.  
  
## <a name="access-level"></a>Erişim düzeyi  
 Ad alanları sanki sahip oldukları kabul edilir bir `Public` erişim düzeyi. Bir ad alanı, aynı proje başka bir yerindeki kod projesine başvuru diğer projeler ve projesinden derleme erişilebilir.  
  
 Bir ad alanı, ancak diğer herhangi bir öğe içinde değil anlamı ad alanı düzeyinde bildirilen programlama öğeleri olabilir `Public` veya `Friend` erişim. Belirtilmezse, bu tür erişim düzeyi bir öğeyi kullanan `Friend` varsayılan olarak. Ad alanı düzeyinde bildirebilir öğeler, sınıflar, yapılar, modüller, arabirimler, numaralandırmalar ve temsilciler içerir. Daha fazla bilgi için bkz: [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
## <a name="root-namespace"></a>Kök Namespace  
 Projenizdeki tüm ad alanı adlarını temel alan bir *kök ad alanı*. Visual Studio Proje adına projenizdeki tüm kodları için varsayılan kök ad alanı olarak atar. Örneğin, projenizin adlı `Payroll`, programlama öğeleri ad alanına ait `Payroll`. Bildirirseniz `Namespace funding`, bu ad alanının tam adı `Payroll.funding`.  
  
 Varolan bir ad alanında belirtmek istiyorsanız bir `Namespace` deyimi, gibi genel liste sınıfı örnekte, kök ad alanı null bir değere ayarlayabilirsiniz. Bunu yapmak için tıklatın **proje özelliklerini** gelen **proje** menüsüne ve ardından Temizle **kök ad alanı** giriş kutusu boş olmasını sağlayın. Bu genel liste sınıfı örnekte yapmadınız, Visual Basic derleyici götürecek `System.Collections.Generic` proje içindeki yeni bir ad alanı olarak `Payroll`, tam adıyla `Payroll.System.Collections.Generic`.  
  
 Alternatif olarak, kullanabileceğiniz `Global` anahtar projeniz dışında tanımlanan ad alanları öğelerine bakın. Bunun yapılması, kök ad alanı olarak projenizin adına korumak olanak tanır. Bu, istemeden programlama öğelerinizi olanlar var olan ad alanları ile birlikte birleştirme olasılığını azaltır. Daha fazla bilgi için "Genel anahtar sözcüğü içinde tam olarak nitelenmiş adlar" bölümüne bakın [Visual Basic'de ad alanları](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 `Global` Anahtar sözcüğü bir Namespace deyimi içinde de kullanılabilir. Bu, bir ad alanı, projenin kök ad alanı dışında tanımlamanıza olanak sağlar. Daha fazla bilgi için "Genel anahtar sözcüğü içinde arama Namespace deyimleri" bölümüne bakın [Visual Basic'de ad alanları](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 **Sorun giderme.** Kök ad alanı için ad alanı adlarının beklenmeyen birleştirmeler yol açabilir. Projenizi dışında tanımlanan ad alanları için başvuru yaparsanız, Visual Basic derleyici bunları kök ad alanı iç içe geçmiş ad alanları olarak construe. Böyle bir durumda, dış ad alanları ile önceden tanımlanmış herhangi bir türünün derleyici tanımıyor. Bu durumu önlemek için kök ad alanı "Kök Namespace" açıklandığı gibi null bir değere ayarlayın veya kullanmak `Global` erişim öğeleri dış ad alanları için anahtar sözcüğü.  
  
## <a name="attributes-and-modifiers"></a>Öznitelikler ve değiştiricileri  
 Bir ad alanına öznitelikleri uygulanamıyor. Öznitelik, kaynak sınıflandırıcı ad alanları gibi anlamlı olmayan derlemenin meta verilerini, bilgileri katkıda bulunur.  
  
 Bir ad alanına herhangi bir erişim veya yordam değiştiricileri veya diğer değiştiricileri uygulayamazsınız. Bir tür olduğundan, bu değiştiricileri anlamlı değildir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, iki ad alanı, bir diğer iç içe geçmiş bildirir.  
  
 [!code-vb[VbVbalrStatements#43](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_1.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tek bir satıra birden çok iç içe geçmiş ad bildirir ve önceki örneğe eşdeğerdir.  
  
 [!code-vb[VbVbalrStatements#41](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_2.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, önceki örneklerde tanımlanmış sınıf erişir.  
  
 [!code-vb[VbVbalrStatements#42](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_3.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yeni bir genel liste sınıf çatıyı tanımlar ve ona ekler <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanı.  
  
```vb  
Namespace System.Collections.Generic  
    Class specialSortedList(Of T)  
        Inherits List(Of T)  
        ' Insert code to define the special generic list class.  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Imports deyimi (.NET Namespace ve türü)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [Bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Visual Basic'de ad alanları](../../../visual-basic/programming-guide/program-structure/namespaces.md)
