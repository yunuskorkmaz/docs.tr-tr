---
title: "Nasıl yapılır: Bir Sabit Bildirme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 554f659e060087228fb43efd8b9d06103e21e980
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-a-constant-visual-basic"></a>Nasıl yapılır: Bir Sabit Bildirme (Visual Basic)
Kullandığınız `Const` bildirimini bir sabit bildirme ve değerini ayarlayın. Bir sabit bildirme tarafından anlamlı bir ad bir değere atayın. Bir sabit bildirildiğinde, değiştirilen veya yeni bir değer atanmış.  
  
 Bir sabit bir yordam içinde veya bir modül, sınıf veya yapı bildirimleri bölümünde bildirin. Sınıf veya yapı düzeyi sabitleri `Private` varsayılan olarak, aynı zamanda olarak bildirilmesi ancak `Public`, `Friend`, `Protected`, veya `Protected Friend` uygun düzeyde bir kod erişim için.  
  
 Sabiti (kuralları değişken adları oluşturmak için aynıdır) geçerli bir simgesel ad ve sayısal veya dize sabitleri ve işleçler (ancak hiçbir işlev çağrıları) oluşan bir ifade olması gerekir.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a>Bir sabit bildirme  
  
-   Bir erişim belirteci içeren bir bildirim yazma `Const` anahtar sözcüğü ve aşağıdaki örneklerde olduğu gibi bir ifade:  
  
     [!code-vb[VbEnumsTask#8](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_1.vb)]  
  
     Zaman [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) olan `Off` ve [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) olan `On`, bir veri türü belirterek bir sabiti açıkça bildirmelidir (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, veya `String`).  
  
     Zaman `Option Infer` olan `On` veya `Option Strict` olan `Off`, bir veri türüyle belirtmeden bir sabit bildirebilir bir `As` yan tümcesi. Derleyici ifade türünden sabiti türünü belirler. Daha fazla bilgi için bkz: [sabit ve değişmez değer veri türleri](constant-and-literal-data-types.md).  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a>Bir açıkça belirtilen veri türüne sahip bir sabit bildirme  
  
-   İçeren bir bildirim yazma `As` anahtar sözcüğü ve açık bir veri türü, aşağıdaki örneklerde olduğu gibi:  
  
     [!code-vb[VbEnumsTask#9](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_2.vb)]  
  
     Kodunuzun her satır için tek bir sabit bildirirseniz daha okunabilir olmasına rağmen tek bir satıra birden çok sabitleri bildirebilirsiniz. Tek bir satıra birden çok sabitleri bildirirseniz tüm aynı erişim düzeyini olmaları gerekir (`Public`, `Private`, `Friend`, `Protected`, veya `Protected Friend`).  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a>Tek bir satıra birden çok sabitleri bildirmek için  
  
-   Bildirimleri virgül ve boşluk aşağıdaki örnekteki gibi ayırır:  
  
    ```  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Const deyimi](../../../../visual-basic/language-reference/statements/const-statement.md)  
 [Sabit ve değişmez değerli veri türleri](constant-and-literal-data-types.md)  
 [Sabitlere genel bakış](constants-overview.md) [nasıl yapılır: bir sabit bildirme](how-to-declare-a-constant.md) [kullanıcı tanımlı sabitler](user-defined-constants.md) [sabit ve değişmez değerli veri türleri](constant-and-literal-data-types.md) [nasıl yapılır: Grup Sabit değerleri birlikte ilgili](how-to-group-related-constant-values-together.md) [numaralandırmalara genel bakış](enumerations-overview.md) [nasıl yapılır: numaralandırmaları bildirme](how-to-declare-enumerations.md) [nasıl yapılır: bir numaralandırma üyesine başvurma](how-to-refer-to-an-enumeration-member.md) [Numaralandırmalar ve ad niteliği](enumerations-and-name-qualification.md) [nasıl yapılır: bir numaralandırma yineleme](how-to-iterate-through-an-enumeration.md) [nasıl yapılır: bir numaralandırma değeriyle ilişkili dizeyi belirleme](how-to-determine-the-string-associated-with-an-enumeration-value.md) [Bir numaralandırmanın ne zaman kullanılacağı](when-to-use-an-enumeration.md)

 [Numaralandırmalara genel bakış](enumerations-overview.md)  
 [Sabitlere genel bakış](constants-overview.md)  
 [Nasıl yapılır: bir numaralandırma bildirme](how-to-declare-enumerations.md)  
 [Numaralandırmalar ve ad niteliği](enumerations-and-name-qualification.md)  
 [Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Sabitler ve numaralandırmalar](../../../../visual-basic/language-reference/constants-and-enumerations.md)
