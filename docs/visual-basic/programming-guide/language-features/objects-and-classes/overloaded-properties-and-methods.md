---
title: Aşırı yüklenmiş özellikler ve yöntemler (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: c0aa7c4a13e049045743044a98020a1aab2cf1a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="overloaded-properties-and-methods-visual-basic"></a>Aşırı yüklenmiş özellikler ve yöntemler (Visual Basic)

Aşırı yükleme birden fazla yordam, örnek oluşturucusu ya da bir sınıf aynı adlı ancak farklı bağımsız değişken türleri ile özelliğinde oluşturulmasını olur.  
  
## <a name="overloading-usage"></a>Kullanım aşırı yüklemesi

 Nesne modeli, farklı veri türlerinde çalışmayabilir yordamlar için aynı adları uygulamadığınız belirleyen aşırı özellikle yararlıdır. Örneğin, birkaç farklı veri türlerini görüntülemek için bir sınıf olabilir `Display` şuna yordamları:  
  
 [!code-vb[VbVbalrOOP#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#64)]
  
 Aşırı yükleme olmadan aynı şeyi sonraki gösterildiği gibi yaparlar olsa bile her bir yordam için farklı adlar oluşturmanız gerekecek:  
  
 [!code-vb[VbVbalrOOP#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#65)]
  
 Aşırı yükleme, kullanılabilir veri türleri seçimine sağladığından özelliklerinin veya yöntemlerin kullanılacağını kolaylaştırır. Örneğin, aşırı yüklenmiş `Display` ele alınan yöntemi daha önce çağrılabilir herhangi bir kod aşağıdaki satırları ile:  
  
 [!code-vb[VbVbalrOOP#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#66)]
  
 Çalışma zamanında, Visual Basic belirttiğiniz parametreleri veri türlerine göre doğru yordamı çağırır.  
  
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
  
#### <a name="to-use-this-example-to-create-an-overloaded-method"></a>Aşırı yüklenmiş yöntemin oluşturmak için bu örneği kullanmak için
  
1.  Yeni bir proje açın ve adlı bir sınıf ekleyin `TaxClass`.  
  
2.  Aşağıdaki kodu ekleyin `TaxClass` sınıfı.  
  
     [!code-vb[VbVbalrOOP#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#67)]
  
3.  Aşağıdaki yordam formunuza ekleyin.  
  
     [!code-vb[VbVbalrOOP#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#68)]
  
4.  Arama ve form düğme ekleme `ShowTax` yordamdan `Button1_Click` düğmesinin olayı.  
  
5.  Projeyi çalıştırın ve aşırı yüklenmiş sınamak için formu düğmeyi tıklatın `ShowTax` yordamı.  
  
 Çalışma zamanında derleyici kullanılmasını parametrelerini eşleşen uygun aşırı yüklenmiş işlevi seçer. Düğmeye tıkladığınızda, aşırı yüklenmiş yöntemin önce çağrılır bir `Price` bir dize ve "Fiyat bir dizedir. ileti, parametre Vergi is $5,12" görüntülenir. `TaxAmount` ile adlı bir `Decimal` ikinci kez ve iletiyi değer, "Fiyat bir ondalık sayı. Vergi is $5,12" görüntülenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

 [Nesneler ve Sınıflar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Visual Basic'de gölgeleme](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [Sub Deyimi](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Devralma Temelleri](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)  
 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)  
 [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)  
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
