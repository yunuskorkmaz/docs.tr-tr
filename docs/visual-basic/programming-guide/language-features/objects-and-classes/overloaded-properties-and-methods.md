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
ms.openlocfilehash: 472cd0dbfc0544477d8e368b553a454b977d633c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498615"
---
# <a name="overloaded-properties-and-methods-visual-basic"></a>Aşırı yüklenmiş özellikler ve yöntemler (Visual Basic)

Aşırı yükleme birden fazla yordam, örnek oluşturucusu veya bir sınıf ile aynı ada ancak farklı bağımsız değişken türleri özelliğinde oluşturulmasını var.  
  
## <a name="overloading-usage"></a>Kullanım aşırı yükleme

 Aynı adları için farklı veri türleri üzerinde çalışması yordamları kullanmak istemiyorsunuz, nesne modeli belirler. aşırı yükleme özellikle yararlı olur. Örneğin, birçok farklı veri türlerini görüntülemek için bir sınıf olabilir `Display` şuna yordamları:  
  
 [!code-vb[VbVbalrOOP#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#64)]
  
 Bunlar aşağıda gösterildiği aynı şeyi yapmak olsa da aşırı yüklemeden, her bir yordam için farklı adlar oluşturmanız gerekir:  
  
 [!code-vb[VbVbalrOOP#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#65)]
  
 Aşırı yükleme özelliklerinin veya yöntemlerin bir seçenek kullanılabilir veri türleri sağladığından kullanmayı kolaylaştırır. Örneğin, aşırı yüklenmiş `Display` yöntemi daha önce çağrılabilir herhangi aşağıdaki kod satırlarını:  
  
 [!code-vb[VbVbalrOOP#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#66)]
  
 Çalışma zamanında, Visual Basic belirttiğiniz parametrelerin veri türlerine göre doğru yordamını çağırır.  
  
## <a name="overloading-rules"></a>Kuralları aşırı yükleme

 Bir sınıf için aşırı yüklenmiş bir üye, iki veya daha fazla özelliklerinin veya yöntemlerin aynı ada sahip ekleyerek oluşturun. Türetilmiş aşırı yüklenmiş üyelerin dışında aşırı yüklenmiş üyelerin farklı parametre listeleri olmalıdır ve bir özellik veya yordamı aşırı yüklerken ayırt edici bir özellik olarak aşağıdaki öğeleri kullanılamaz:  
  
-   Değiştiriciler, gibi `ByVal` veya `ByRef`, üye veya üyenin parametreleri geçerlidir.  
  
-   Parametre adları  
  
-   Yordamları dönüş türleri  
  
 `Overloads` Aşırı yüklerken anahtar sözcüğü isteğe bağlı, ancak varsa aşırı üyeyi kullanan `Overloads` anahtar sözcüğü ve ardından aynı ada sahip diğer tüm aşırı yüklenmiş üyeler de belirtmelisiniz bu anahtar sözcük.  
  
 Türetilen sınıfların aynı parametreleri ve parametre türleri olarak da bilinen bir işlem olan üyelere sahip devralınan üyeleri aşırı yükleme *ada ve imzaya göre gölgeleme*. Varsa `Overloads` ada ve imzaya göre Gölgeleme, üyeyi türetilen sınıfın uygulaması temel sınıf uygulaması yerine kullanılır ve bu üye için diğer aşırı yüklemeler için örnekleri kullanılabilir olduğunda anahtar sözcüğü kullanılır türetilmiş sınıf.  
  
 Varsa `Overloads` anahtar sözcüğü devralınan bir üyeyi aynı parametreleri ve parametre türlerine sahip bir üye ile aşırı yüklerken atlanırsa, ardından aşırı yükleme olarak adlandırılır *adıyla gölgeleme*. Üye'nın devralınmış uygulaması adıyla gölgeleme değiştirir ve, diğer tüm aşırı yüklemeler türetilmiş sınıf ve onun decedents örneklerine kullanılamaz hale getirir.  
  
 `Overloads` Ve `Shadows` değiştiriciler hem de kullanılamaz aynı özellik veya yöntem.  
  
### <a name="example"></a>Örnek

 Aşağıdaki örnek, ya da kabul eden aşırı yüklenmiş yöntemler oluşturur. bir `String` veya `Decimal` dolar tutarını ve dönüş vergi içeren bir dize gösterimi.  
  
#### <a name="to-use-this-example-to-create-an-overloaded-method"></a>Aşırı yüklenmiş bir yöntem oluşturmak için bu örneği kullanmak için
  
1.  Adlı bir sınıf ekleyin ve yeni bir proje açmayı `TaxClass`.  
  
2.  Aşağıdaki kodu ekleyin `TaxClass` sınıfı.  
  
     [!code-vb[VbVbalrOOP#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#67)]
  
3.  Aşağıdaki yordam formunuza ekleyin.  
  
     [!code-vb[VbVbalrOOP#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#68)]
  
4.  Çağrı ve form için bir düğme ekleyin `ShowTax` yordamdan `Button1_Click` düğmesinin olayı.  
  
5.  Projeyi çalıştırın ve Aşırı yüklenen test etmek için form üzerindeki düğmeye tıklayın `ShowTax` yordamı.  
  
 Çalışma zamanında derleyici kullanılmakta parametrelerle eşleşen Aşırı yüklenen işlevin uygun seçer. Düğmeye tıkladığınızda, aşırı yüklenmiş yöntem ile ilk çağrılır bir `Price` parametresine bir dize ve iletinin "Fiyat bir dizedir. Vergi is $5,12" görüntülenir. `TaxAmount` ile adlı bir `Decimal` ikinci kez ve ileti değeri, "Fiyat bir ondalık. Vergi is $5,12" görüntülenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nesneler ve Sınıflar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Visual Basic'de gölgeleme](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Sub Deyimi](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Devralma Temelleri](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)
- [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)
- [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
