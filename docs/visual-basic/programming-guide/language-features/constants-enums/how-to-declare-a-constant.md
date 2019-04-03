---
title: 'Nasıl yapılır: (Visual Basic) bir sabit bildirme'
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
ms.openlocfilehash: 95bfa3da5499c518dad0c235b539784fee2bb522
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843415"
---
# <a name="how-to-declare-a-constant-visual-basic"></a>Nasıl yapılır: (Visual Basic) bir sabit bildirme
Kullandığınız `Const` deyimini bir sabit bildirme ve değerini ayarlayın. Bir sabit bildirme tarafından bir değer anlamlı bir ad atayın. Bir sabit bildirildiğinde, değiştiren veya yeni bir değer atanır.  
  
 Size, bir yordam içinde veya bir modül, sınıf veya yapı bildirimleri bölümünde bir sabit bildirme. Sınıf veya yapı düzeyi sabitleri `Private` , varsayılan olarak da bildirilmeleri ancak `Public`, `Friend`, `Protected`, veya `Protected Friend` uygun düzeyde kod erişim için.  
  
 Sabit (kuralları değişken adları oluşturmak için aynıdır) geçerli bir simgesel ad ve sayısal veya dize sabitleri ve işleçler (ancak hiçbir işlev çağrıları) oluşan bir ifade olması gerekir.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a>Bir sabit bildirme  
  
-   Bir erişim belirticisi içeren bir bildirimi yazma `Const` anahtar sözcüğü ve aşağıdaki örneklerde gösterildiği gibi bir ifade:  
  
     [!code-vb[VbEnumsTask#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#8)]  
  
     Zaman [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) olduğu `Off` ve [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) olduğu `On`, bir veri türü belirterek bir sabiti açıkça bildirmelidir (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, veya `String`).  
  
     Zaman `Option Infer` olduğu `On` veya `Option Strict` olduğu `Off`, bir veri türüyle belirtmeden bir sabit bildirebilirsiniz bir `As` yan tümcesi. Derleyici sabiti ifadesinin türünden türünü belirler. Daha fazla bilgi için [sabit ve değişmez değer veri türleri](constant-and-literal-data-types.md).  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a>Açıkça belirtilen veri türü olan bir sabit bildirme  
  
-   İçeren bir bildirimi yazma `As` anahtar sözcüğü ve açık bir veri türü, aşağıdaki örneklerde olduğu gibi:  
  
     [!code-vb[VbEnumsTask#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#9)]  
  
     Kodunuzu daha okunabilir her satırda yalnızca tek bir sabit bildirirseniz olmasına rağmen tek bir satırda birden çok sabitleri bildirebilirsiniz. Birden çok sabitleri tek bir satıra bildirirseniz, tümü aynı erişim düzeyini olmaları gerekir (`Public`, `Private`, `Friend`, `Protected`, veya `Protected Friend`).  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a>Birden çok sabitleri tek bir satıra bildirmek için  
  
-   Bir virgül ve aşağıdaki örnekte olduğu gibi bir boşluk ile bildirimleri ayırın:  
  
    ```  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Const Deyimi](../../../../visual-basic/language-reference/statements/const-statement.md)
- [Sabit ve Değişmez Değerli Veri Türleri](constant-and-literal-data-types.md)
- [Sabitlere Genel Bakış](constants-overview.md)
- [Nasıl yapılır: Bir sabit bildirme](how-to-declare-a-constant.md)
- [Kullanıcı Tanımlı Sabitler](user-defined-constants.md)
- [Sabit ve Değişmez Değerli Veri Türleri](constant-and-literal-data-types.md)
- [Nasıl yapılır: İlgili sabit değerleri birlikte gruplandırma](how-to-group-related-constant-values-together.md)
- [Sabit Listelerine Genel Bakış](enumerations-overview.md)
- [Nasıl yapılır: Sabit listesi bildirme](how-to-declare-enumerations.md)
- [Nasıl yapılır: Bir numaralandırma üyesine başvurma](how-to-refer-to-an-enumeration-member.md)
- [Sabit Listeleri ve Ad Niteliği](enumerations-and-name-qualification.md)
- [Nasıl yapılır: Bir sabit listesi yoluyla yineleme](how-to-iterate-through-an-enumeration.md)
- [Nasıl yapılır: Bir numaralandırma değeriyle ilişkili dizeyi belirleme](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Sabit Listesi Ne Zaman Kullanılır?](when-to-use-an-enumeration.md)

- [Sabit Listelerine Genel Bakış](enumerations-overview.md)
- [Sabitlere Genel Bakış](constants-overview.md)
- [Nasıl yapılır: Bir numaralandırma bildirme](how-to-declare-enumerations.md)
- [Sabit Listeleri ve Ad Niteliği](enumerations-and-name-qualification.md)
- [Option Strict Deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Sabitler ve Sabit Listeleri](../../../../visual-basic/language-reference/constants-and-enumerations.md)
