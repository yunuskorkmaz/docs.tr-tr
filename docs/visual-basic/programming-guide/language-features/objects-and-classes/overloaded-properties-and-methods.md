---
title: "Aşırı Yüklenmiş Özellikler ve Yöntemler (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- properties [Visual Basic], overloading
- methods [Visual Basic], overloading
- shadowing
- names [Visual Basic], multiple procedures with same
- procedures [Visual Basic], mulltiples with same name
- classes [Visual Basic], properties
- classes [Visual Basic], methods
- method overloading
- Overloads keyword [Visual Basic], overloaded members
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8a872540716941ccd0dbb8b058508b89ce26a988
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="overloaded-properties-and-methods-visual-basic"></a>Aşırı Yüklenmiş Özellikler ve Yöntemler (Visual Basic)
Aşırı yükleme birden fazla yordam, örnek oluşturucusu ya da bir sınıf aynı adlı ancak farklı bağımsız değişken türleri ile özelliğinde oluşturulmasını olur.  
  
## <a name="overloading-usage"></a>Kullanım aşırı yüklemesi  
 Nesne modeli, farklı veri türlerinde çalışmayabilir yordamlar için aynı adları uygulamadığınız belirleyen aşırı özellikle yararlıdır. Örneğin, birkaç farklı veri türlerini görüntülemek için bir sınıf olabilir `Display` şuna yordamları:  
  
 [!code-vb[VbVbalrOOP#64](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_1.vb)]  
  
 Aşırı yükleme olmadan aynı şeyi sonraki gösterildiği gibi yaparlar olsa bile her bir yordam için farklı adlar oluşturmanız gerekecek:  
  
 [!code-vb[VbVbalrOOP#65](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_2.vb)]  
  
 Aşırı yükleme, kullanılabilir veri türleri seçimine sağladığından özelliklerinin veya yöntemlerin kullanılacağını kolaylaştırır. Örneğin, aşırı yüklenmiş `Display` ele alınan yöntemi daha önce çağrılabilir herhangi bir kod aşağıdaki satırları ile:  
  
 [!code-vb[VbVbalrOOP#66](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_3.vb)]  
  
 Çalışma zamanında [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] parametrelerinin veri türleri üzerinde doğru yordamı dayalı aramalar belirtin.  
  
## <a name="overloading-rules"></a>Kuralları aşırı yüklemesi  
 İki veya daha fazla özelliklerinin veya yöntemlerin aynı ada sahip ekleyerek aşırı yüklenmiş bir üyesi için bir sınıf oluşturun. Aşırı yüklenmiş türetilmiş üyeler dışında aşırı yüklenmiş her üyesinin farklı parametre listeleri sahip olması gerekir ve aşağıdaki öğeleri farklılaştırıcı bir özellik olarak bir özellik veya yordam aşırı yüklemesi kullanılamaz:  
  
-   Değiştiriciler, gibi `ByVal` veya `ByRef`, üye veya üye parametreleri için geçerli.  
  
-   Parametrelerinin adları  
  
-   Dönüş türleri yordamları  
  
 `Overloads` Aşırı yüklendiğinde anahtar sözcüğü isteğe bağlı, ancak varsa aşırı üyeyi kullanan `Overloads` anahtar sözcüğü ve ardından diğer tüm aşırı yüklenmiş üyeler aynı ada sahip de belirtmelisiniz bu anahtar sözcük.  
  
 Türetilen sınıflar devralınan üyeleri aynı parametreleri ve parametre türleri olarak da bilinen bir işlem sahip üyeleriyle aşırı yükleme *ad ve imza tarafından gölgeleme*. Varsa `Overloads` anahtar sözcük ad ve imza tarafından Gölgeleme, üye uyarlamasını türetilen sınıfın temel sınıf uygulamasında yerine kullanılacak ve bu üye için diğer aşırı yüklemeler için örnekleri kullanılabilir olduğunda kullanılır türetilmiş sınıf.  
  
 Varsa `Overloads` anahtar sözcüğü, aynı parametreleri ve parametre türleri sahip bir üye devralınan bir üyesiyle aşırı yüklendiğinde atlanırsa, ardından aşırı yüklemesi adlı *adıyla gölgeleme*. Ada göre gölgeleme üyesi devralınan uyarlamasını değiştirir ve, tüm diğer aşırı yüklemeler türetilmiş sınıf ve kendi decedents örnekleri için kullanılamaz hale getirir.  
  
 `Overloads` Ve `Shadows` değiştiricileri hem kullanılamaz aynı özellik veya yöntem.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, ya da kabul aşırı yüklenmiş yöntemler oluşturur bir `String` veya `Decimal` dolar tutar ve return vergi içeren bir dize gösterimi.  
  
##### <a name="to-use-this-example-to-create-an-overloaded-method"></a>Aşırı yüklenmiş yöntemin oluşturmak için bu örneği kullanmak için  
  
1.  Yeni bir proje açın ve adlı bir sınıf ekleyin `TaxClass`.  
  
2.  Aşağıdaki kodu ekleyin `TaxClass` sınıfı.  
  
     [!code-vb[VbVbalrOOP#67](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_4.vb)]  
  
3.  Aşağıdaki yordam formunuza ekleyin.  
  
     [!code-vb[VbVbalrOOP#68](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_5.vb)]  
  
4.  Arama ve form düğme ekleme `ShowTax` yordamdan `Button1_Click` düğmesinin olayı.  
  
5.  Projeyi çalıştırın ve aşırı yüklenmiş sınamak için formu düğmeyi tıklatın `ShowTax` yordamı.  
  
 Çalışma zamanında derleyici kullanılmasını parametrelerini eşleşen uygun aşırı yüklenmiş işlevi seçer. Düğmeye tıkladığınızda, aşırı yüklenmiş yöntemin önce çağrılır bir `Price` bir dize ve "Fiyat bir dizedir. ileti, parametre Vergi is $5,12" görüntülenir. `TaxAmount`ile adlı bir `Decimal` ikinci kez ve iletiyi değer, "Fiyat bir ondalık sayı. Vergi is $5,12" görüntülenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nesneler ve sınıflar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Visual Basic'de gölgeleme](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [Sub deyimi](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Devralma temelleri](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [Gölgeleri](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)  
 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)  
 [Aşırı yüklemeler](../../../../visual-basic/language-reference/modifiers/overloads.md)  
 [Gölgeleri](../../../../visual-basic/language-reference/modifiers/shadows.md)
