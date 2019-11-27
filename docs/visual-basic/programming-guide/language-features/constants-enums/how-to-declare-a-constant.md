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
ms.openlocfilehash: 5054d4a4fc02d8bd22efceb01770fc54167d8cb3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347467"
---
# <a name="how-to-declare-a-constant-visual-basic"></a>Nasıl yapılır: Bir Sabit Bildirme (Visual Basic)
Bir sabiti bildirmek ve değerini ayarlamak için `Const` ifadesini kullanın. Bir sabiti bildirerek, bir değere anlamlı bir ad atarsınız. Sabit bir kez bildirildiğinde, değiştirilemez veya yeni bir değer atanamaz.  
  
 Bir yordamın içinde veya bir modülün, sınıfın veya yapının Bildirimler bölümünde bir sabit değer bildirirsiniz. Sınıf veya yapı düzeyi sabitleri varsayılan olarak `Private`, ancak uygun kod erişimi düzeyi için `Public`, `Friend`, `Protected`veya `Protected Friend` olarak da belirtilebilir.  
  
 Sabit, geçerli bir sembolik ada sahip olmalıdır (kurallar, değişken adları oluşturanlarla aynıdır) ve sayısal veya dize sabitleri ve işleçlerden oluşan bir ifade (ancak işlev çağrısı yoktur).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a>Bir sabit bildirmek için  
  
- Aşağıdaki örneklerde olduğu gibi, bir erişim belirticisi, `Const` anahtar sözcüğü ve bir ifade içeren bir bildirim yazın:  
  
     [!code-vb[VbEnumsTask#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#8)]  
  
     [Seçenek çıkarımı](../../../../visual-basic/language-reference/statements/option-infer-statement.md) `Off` ve [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) `On`, bir veri türü (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`veya `String`) belirterek bir sabiti açıkça bildirmeniz gerekir.  
  
     `Option Infer` `On` veya `Option Strict` `Off`olduğunda, bir `As` yan tümcesiyle veri türü belirtmeden bir sabit bildirebilirsiniz. Derleyici, ifadenin türünden sabit türünü belirler. Daha fazla bilgi için bkz. [sabit ve değişmez değerli veri türleri](constant-and-literal-data-types.md).  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a>Açıkça belirtilen bir veri türüne sahip bir sabit bildirmek için  
  
- Aşağıdaki örneklerde olduğu gibi `As` anahtar sözcüğünü ve açık bir veri türünü içeren bir bildirim yazın:  
  
     [!code-vb[VbEnumsTask#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#9)]  
  
     Her satırda yalnızca tek bir sabit değer bildirirseniz kodunuz daha okunabilir olsa da, tek bir satırda birden çok sabit bildirebilirsiniz. Tek bir satırda birden çok sabit bildirirseniz, tümünün aynı erişim düzeyine sahip olmaları gerekir (`Public`, `Private`, `Friend`, `Protected`veya `Protected Friend`).  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a>Birden çok sabiti tek bir satırda bildirmek için  
  
- Aşağıdaki örnekte olduğu gibi, bildirimleri virgülle ve boşlukla ayırın:  
  
    ```vb  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Const Deyimi](../../../../visual-basic/language-reference/statements/const-statement.md)
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
- [Nasıl yapılır: Bir Sabit Listesi Değeriyle İlişkili Dizeyi Belirleme](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Sabit Listesi Ne Zaman Kullanılır?](when-to-use-an-enumeration.md)

- [Sabit Listelerine Genel Bakış](enumerations-overview.md)
- [Sabitlere Genel Bakış](constants-overview.md)
- [Nasıl yapılır: numaralandırma bildirme](how-to-declare-enumerations.md)
- [Sabit Listeleri ve Ad Niteliği](enumerations-and-name-qualification.md)
- [Option Strict Deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Sabitler ve Sabit Listeleri](../../../../visual-basic/language-reference/constants-and-enumerations.md)
