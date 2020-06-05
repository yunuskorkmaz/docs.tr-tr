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
ms.openlocfilehash: 1672f12773ece012c580253b6dafbf9d0ac8f07c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84389158"
---
# <a name="overloaded-properties-and-methods-visual-basic"></a>Aşırı yüklenmiş Özellikler ve Yöntemler (Visual Basic)

Aşırı yükleme, aynı ada ancak farklı bağımsız değişken türlerine sahip bir sınıfta birden fazla yordamın, örnek oluşturucunun veya özelliğin oluşturulması.

## <a name="overloading-usage"></a>Kullanımı aşırı yükleme

Aşırı yükleme özellikle, nesne modeliniz farklı veri türlerinde çalışan yordamlar için özdeş adlar kullanmayı belirlemesi durumunda yararlıdır. Örneğin, çeşitli farklı veri türlerini görüntüleyebilen bir sınıf `Display` Şuna benzer yordamlar içerebilir:

[!code-vb[VbVbalrOOP#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#64)]

Aşırı yükleme olmadan, her bir yordam için, daha sonra gösterildiği gibi, aynı şeyi gerçekleştirseler bile ayrı adlar oluşturmanız gerekir:

[!code-vb[VbVbalrOOP#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#65)]

Aşırı yükleme özelliği, kullanılabilecek bir veri türleri seçimi sağladığından özellikleri veya yöntemleri kullanmayı kolaylaştırır. Örneğin, `Display` daha önce açıklanan aşırı yüklenmiş yöntem aşağıdaki kod satırlarıyla çağrılabilir:

[!code-vb[VbVbalrOOP#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#66)]

Çalışma zamanında, Visual Basic belirttiğiniz parametrelerin veri türlerine göre doğru yordamı çağırır.

## <a name="overloading-rules"></a>Kuralları aşırı yükleme

 Aynı ada sahip iki veya daha fazla özellik ya da yöntem ekleyerek bir sınıf için aşırı yüklenmiş bir üye oluşturursunuz. Aşırı yüklenmiş türetilmiş Üyeler hariç olmak üzere, her aşırı yüklenmiş üye farklı parametre listelerine sahip olmalıdır ve bir özellik veya yordamı aşırı yüklerken bir ayrım özelliği olarak aşağıdaki öğeler kullanılamaz:

- `ByVal` `ByRef` Bir üyeye veya üyenin parametrelerine uygulanan veya gibi değiştiriciler.

- Parametrelerin adları

- Yordamların dönüş türleri

`Overloads`Anahtar sözcüğü aşırı yükleme sırasında isteğe bağlıdır, ancak herhangi bir aşırı yüklenmiş üye `Overloads` anahtar sözcüğünü kullanıyorsa, aynı ada sahip diğer tüm aşırı yüklenmiş Üyeler de bu anahtar sözcüğü belirtmelidir.

Türetilmiş sınıflar, *ad ve imza ile gölgeleme*olarak bilinen bir işlem olan aynı parametrelere ve parametre türlerine sahip üyelere sahip devralınan üyeleri aşırı yükleyebilir. `Overloads`Anahtar sözcüğü ad ve imza ile gölgelendirmesi sırasında kullanılıyorsa, türetilmiş sınıfın üyenin uygulanması, temel sınıftaki uygulama yerine kullanılır ve bu üyeye ait diğer tüm aşırı yüklemeler türetilmiş sınıfın örnekleri tarafından kullanılabilir.

`Overloads`Aynı parametrelere ve parametre türlerine sahip bir üyeye sahip devralınmış bir üyeyi aşırı yüklerken anahtar sözcük atlanırsa, aşırı yükleme *ada göre gölgeleme*olarak adlandırılır. Ada göre gölgeleme bir üyenin devralınmış uygulamasını değiştirir ve diğer tüm aşırı yüklemeleri türetilmiş sınıfın örneklerine ve onun decedents kullanılamaz hale getirir.

`Overloads`Ve `Shadows` değiştiricileri aynı özellik veya yöntemle birlikte kullanılamaz.

### <a name="example"></a>Örnek

Aşağıdaki örnek, bir dolar tutarının bir ya da gösterimini kabul eden aşırı yüklenmiş yöntemler oluşturur `String` `Decimal` ve satış vergisini içeren bir dize döndürür.

#### <a name="to-use-this-example-to-create-an-overloaded-method"></a>Daha fazla yüklenmiş bir yöntem oluşturmak için bu örneği kullanın

1. Yeni bir proje açın ve adlı bir sınıf ekleyin `TaxClass` .

2. Sınıfına aşağıdaki kodu ekleyin `TaxClass` .

    [!code-vb[VbVbalrOOP#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#67)]

3. Formunuza aşağıdaki yordamı ekleyin.

    [!code-vb[VbVbalrOOP#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#68)]

4. Formunuza bir düğme ekleyin ve `ShowTax` `Button1_Click` düğmenin olayından yordamı çağırın.

5. Projeyi çalıştırın ve daha fazla yordamı test etmek için formdaki düğmeye tıklayın `ShowTax` .

Çalışma zamanında, derleyici kullanılan parametrelerle eşleşen uygun aşırı yüklenmiş işlevi seçer. Düğmeye tıkladığınızda, önce aşırı yüklenmiş yöntem dize ve ileti olan bir parametre ile ilk olarak çağrılır `Price` , "Price bir dizedir. Vergi $5,12 "görüntülenir. `TaxAmount``Decimal`ikinci kez bir değerle çağrılır, "Price bir Decimal olur. Vergi $5,12 "görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Nesneler ve sınıflar](index.md)
- [Visual Basic'de Gölgeleme](../declared-elements/shadowing.md)
- [Sub Deyimi](../../../language-reference/statements/sub-statement.md)
- [Devralma Temelleri](inheritance-basics.md)
- [Shadows](../../../language-reference/modifiers/shadows.md)
- [ByVal](../../../language-reference/modifiers/byval.md)
- [ByRef](../../../language-reference/modifiers/byref.md)
- [Aşırı Yüklemeler](../../../language-reference/modifiers/overloads.md)
- [Shadows](../../../language-reference/modifiers/shadows.md)
