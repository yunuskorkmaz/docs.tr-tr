---
title: Aşırı yüklenmiş Özellikler ve Yöntemler
ms.date: 07/20/2015
helpviewer_keywords:
- properties [Visual Basic], overloading
- methods [Visual Basic], overloading
- shadowing
- names [Visual Basic], multiple procedures with same
- procedures [Visual Basic], multiples with same name
- classes [Visual Basic], properties
- classes [Visual Basic], methods
- method overloading
- Overloads keyword [Visual Basic], overloaded members
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
ms.openlocfilehash: a5017d371f8a01436020443b2e3466c78fc35d21
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346096"
---
# <a name="overloaded-properties-and-methods-visual-basic"></a>Aşırı yüklenmiş Özellikler ve Yöntemler (Visual Basic)

Aşırı yükleme, aynı ada ancak farklı bağımsız değişken türlerine sahip bir sınıfta birden fazla yordamın, örnek oluşturucunun veya özelliğin oluşturulması.

## <a name="overloading-usage"></a>Kullanımı aşırı yükleme

Aşırı yükleme özellikle, nesne modeliniz farklı veri türlerinde çalışan yordamlar için özdeş adlar kullanmayı belirlemesi durumunda yararlıdır. Örneğin, çeşitli farklı veri türlerini görüntüleyebilen bir sınıf şuna benzer `Display` yordamlarına sahip olabilir:

[!code-vb[VbVbalrOOP#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#64)]

Aşırı yükleme olmadan, her bir yordam için, daha sonra gösterildiği gibi, aynı şeyi gerçekleştirseler bile ayrı adlar oluşturmanız gerekir:

[!code-vb[VbVbalrOOP#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#65)]

Aşırı yükleme özelliği, kullanılabilecek bir veri türleri seçimi sağladığından özellikleri veya yöntemleri kullanmayı kolaylaştırır. Örneğin, daha önce açıklanan aşırı yüklenmiş `Display` yöntemi aşağıdaki kod satırlarıyla çağrılabilir:

[!code-vb[VbVbalrOOP#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#66)]

Çalışma zamanında, Visual Basic belirttiğiniz parametrelerin veri türlerine göre doğru yordamı çağırır.

## <a name="overloading-rules"></a>Kuralları aşırı yükleme

 Aynı ada sahip iki veya daha fazla özellik ya da yöntem ekleyerek bir sınıf için aşırı yüklenmiş bir üye oluşturursunuz. Aşırı yüklenmiş türetilmiş Üyeler hariç olmak üzere, her aşırı yüklenmiş üye farklı parametre listelerine sahip olmalıdır ve bir özellik veya yordamı aşırı yüklerken bir ayrım özelliği olarak aşağıdaki öğeler kullanılamaz:

- Bir üyeye veya üyenin parametrelerine uygulanan `ByVal` veya `ByRef`gibi değiştiriciler.

- Parametrelerin adları

- Yordamların dönüş türleri

Aşırı yükleme sırasında `Overloads` anahtar sözcüğü isteğe bağlıdır, ancak herhangi bir aşırı yüklenmiş üye `Overloads` anahtar sözcüğünü kullanıyorsa, aynı ada sahip diğer tüm aşırı yüklenmiş Üyeler de bu anahtar sözcüğü belirtmelidir.

Türetilmiş sınıflar, *ad ve imza ile gölgeleme*olarak bilinen bir işlem olan aynı parametrelere ve parametre türlerine sahip üyelere sahip devralınan üyeleri aşırı yükleyebilir. Ad ve imza ile gölgeleme sırasında `Overloads` anahtar sözcüğü kullanılırsa, türetilmiş sınıfın üyenin uygulanması temel sınıftaki uygulama yerine kullanılır ve bu üyenin diğer tüm aşırı yüklemeleri türetilmiş sınıfın örnekleri tarafından kullanılabilir.

Aynı parametrelere ve parametre türlerine sahip bir üyeyle devralınan bir üyenin aşırı yüklemesi sırasında `Overloads` anahtar sözcüğü atlanırsa aşırı yükleme, *ada göre gölgeleme*olarak adlandırılır. Ada göre gölgeleme bir üyenin devralınmış uygulamasını değiştirir ve diğer tüm aşırı yüklemeleri türetilmiş sınıfın örneklerine ve onun decedents kullanılamaz hale getirir.

`Overloads` ve `Shadows` değiştiricileri her ikisi de aynı özellik veya yöntemle kullanılamaz.

### <a name="example"></a>Örnek

Aşağıdaki örnek, bir dolar tutarının `String` veya `Decimal` gösterimini kabul eden aşırı yüklenmiş yöntemler oluşturur ve satış vergisini içeren bir dize döndürür.

#### <a name="to-use-this-example-to-create-an-overloaded-method"></a>Daha fazla yüklenmiş bir yöntem oluşturmak için bu örneği kullanın

1. Yeni bir proje açın ve `TaxClass`adlı bir sınıf ekleyin.

2. Aşağıdaki kodu `TaxClass` sınıfına ekleyin.

    [!code-vb[VbVbalrOOP#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#67)]

3. Formunuza aşağıdaki yordamı ekleyin.

    [!code-vb[VbVbalrOOP#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#68)]

4. Formunuza bir düğme ekleyin ve düğmenin `Button1_Click` olayından `ShowTax` yordamını çağırın.

5. Projeyi çalıştırın ve aşırı yüklenmiş `ShowTax` yordamını sınamak için formdaki düğmeye tıklayın.

Çalışma zamanında, derleyici kullanılan parametrelerle eşleşen uygun aşırı yüklenmiş işlevi seçer. Düğmeye tıkladığınızda, önce aşırı yüklenmiş yöntemi bir dize ve ileti olan bir `Price` parametresiyle ilk olarak çağrılır, "Price bir dizedir. Vergi $5,12 "görüntülenir. `TaxAmount` ikinci kez bir `Decimal` değeriyle çağrılır, "Price bir Decimal olur. Vergi $5,12 "görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Nesneler ve Sınıflar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Visual Basic gölgeleme](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Sub Deyimi](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Devralma Temelleri](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)
- [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)
- [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
