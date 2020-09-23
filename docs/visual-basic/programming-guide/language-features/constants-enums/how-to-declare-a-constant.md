---
title: 'Nasıl yapılır: Bir Sabit Bildirme'
ms.date: 07/20/2015
f1_keywords:
- vb.constant
helpviewer_keywords:
- Integer data type [Visual Basic], declaring constants
- Single data type [Visual Basic], declaring constants
- Const statement [Visual Basic], declaring constants
- procedures [Visual Basic], declaration
- data types [Visual Basic], constants
- Long data type [Visual Basic], declaring constants
- Visual Basic code, declaring variables and constants
- Double data type [Visual Basic], declaring constants
- Boolean data type [Visual Basic], declaring constants
- modules, declaring constants
- Byte data type [Visual Basic], declaring constants
- constants [Visual Basic], declaring
- Date data type [Visual Basic], declaring constants
- String data type [Visual Basic], declaring constants
- declaring constants [Visual Basic], const keyword
- Currency data type [Visual Basic], declaring constants and variants
- module-level constants and variables
- Object data type [Visual Basic], declaring constants
ms.assetid: f901b4fa-481f-4621-822e-427060577ad1
ms.openlocfilehash: 138dd58dac9d1983e35e61f8b98a77810fc6e38b
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058852"
---
# <a name="how-to-declare-a-constant-visual-basic"></a>Nasıl yapılır: Bir Sabit Bildirme (Visual Basic)

`Const`Bir sabiti bildirmek ve değerini ayarlamak için ifadesini kullanın. Bir sabiti bildirerek, bir değere anlamlı bir ad atarsınız. Sabit bir kez bildirildiğinde, değiştirilemez veya yeni bir değer atanamaz.  
  
 Bir yordamın içinde veya bir modülün, sınıfın veya yapının Bildirimler bölümünde bir sabit değer bildirirsiniz. Sınıf veya yapı düzeyi sabitleri varsayılan olarak olur `Private` , ancak `Public` `Friend` `Protected` `Protected Friend` uygun kod erişimi düzeyi için,, veya olarak da belirtilebilir.  
  
 Sabit, geçerli bir sembolik ada sahip olmalıdır (kurallar, değişken adları oluşturanlarla aynıdır) ve sayısal veya dize sabitleri ve işleçlerden oluşan bir ifade (ancak işlev çağrısı yoktur).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a>Bir sabit bildirmek için  
  
- Aşağıdaki örneklerde olduğu gibi, bir erişim belirticisi, `Const` anahtar sözcüğü ve bir ifadesi içeren bir bildirim yazın:  
  
     [!code-vb[VbEnumsTask#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#8)]  
  
     [Option Infer](../../../language-reference/statements/option-infer-statement.md) `Off` ve [Option Strict](../../../language-reference/statements/option-strict-statement.md) olduğunda `On` , bir veri türü belirterek ( `Boolean` ,,,,,,, `Byte` `Char` `DateTime` `Decimal` `Double` `Integer` `Long` ,,, `Short` `Single` veya `String` ) bir sabit değer belirtmeniz gerekir.  
  
     `Option Infer`Veya olduğunda `On` `Option Strict` `Off` , yan tümcesiyle bir veri türü belirtmeden bir sabit bildirebilirsiniz `As` . Derleyici, ifadenin türünden sabit türünü belirler. Daha fazla bilgi için bkz. [sabit ve değişmez değerli veri türleri](constant-and-literal-data-types.md).  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a>Açıkça belirtilen bir veri türüne sahip bir sabit bildirmek için  
  
- `As`Aşağıdaki örneklerde olduğu gibi anahtar sözcüğünü ve açık bir veri türünü içeren bir bildirim yazın:  
  
     [!code-vb[VbEnumsTask#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#9)]  
  
     Her satırda yalnızca tek bir sabit değer bildirirseniz kodunuz daha okunabilir olsa da, tek bir satırda birden çok sabit bildirebilirsiniz. Tek bir satırda birden çok sabit bildirirseniz, tümünün aynı erişim düzeyine sahip olmaları gerekir (,,, `Public` `Private` `Friend` `Protected` veya `Protected Friend` ).  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a>Birden çok sabiti tek bir satırda bildirmek için  
  
- Aşağıdaki örnekte olduğu gibi, bildirimleri virgülle ve boşlukla ayırın:  
  
    ```vb  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Const Deyimi](../../../language-reference/statements/const-statement.md)
- [Sabit ve Değişmez Değerli Veri Türleri](constant-and-literal-data-types.md)
- [Sabitlere Genel Bakış](constants-overview.md)
- [Nasıl yapılır: Bir Sabit Bildirme](how-to-declare-a-constant.md)
- [Kullanıcı Tanımlı Sabitler](user-defined-constants.md)
- [Sabit ve Değişmez Değerli Veri Türleri](constant-and-literal-data-types.md)
- [Nasıl yapılır: İlgili Sabit Değerleri Birlikte Gruplandırma](how-to-group-related-constant-values-together.md)
- [Sabit Listelerine Genel Bakış](enumerations-overview.md)
- [Nasıl yapılır: Bir Sabit Listesi Bildirme](how-to-declare-enumerations.md)
- [Nasıl yapılır: Bir Sabit Listesi Üyesine Başvurma](how-to-refer-to-an-enumeration-member.md)
- [Sabit Listeleri ve Ad Niteliği](enumerations-and-name-qualification.md)
- [Nasıl yapılır: Sabit Listesi Yoluyla Yineleme](how-to-iterate-through-an-enumeration.md)
- [Nasıl yapılır: Bir Numaralandırma Değeriyle İlişkili Dizeyi Belirleme](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Sabit Listesi Ne Zaman Kullanılır?](when-to-use-an-enumeration.md)

- [Sabit Listelerine Genel Bakış](enumerations-overview.md)
- [Sabitlere Genel Bakış](constants-overview.md)
- [Nasıl yapılır: numaralandırma bildirme](how-to-declare-enumerations.md)
- [Sabit Listeleri ve Ad Niteliği](enumerations-and-name-qualification.md)
- [Option Strict Deyimi](../../../language-reference/statements/option-strict-statement.md)
- [Sabitler ve numaralandırmalar](../../../language-reference/constants-and-enumerations.md)
