---
title: "Kullanıcı Tanımlı Sabitler (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- constants [Visual Basic], circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants [Visual Basic]
- scope [Visual Basic], constants
- constants [Visual Basic], user-defined
- circular references between constants [Visual Basic]
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ce839c3e843a52b31e40c13cb765f8eaf9959ea4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="user-defined-constants-visual-basic"></a>Kullanıcı Tanımlı Sabitler (Visual Basic)
Bir sabit bir sayı veya değişmez dize yerini alır anlamlı bir addır. Adından da anlaşılacağı gibi bir uygulama yürütme sabit kalır değerleri sabitleri depolar. Denetimleri veya birlikte çalıştığınız bileşenleri tarafından tanımlanan sabitleri kullanabilir veya kendi oluşturabilirsiniz. Kendi başınıza oluşturduğunuz sabitleri olarak açıklanmıştır *kullanıcı tanımlı*.  
  
 İle bir sabit bildirme `Const` deyimi, bir değişken adı oluşturmak için yaptığınız aynı yönergeleri kullanarak. Varsa `Option Strict` olan `On`, açıkça sabit türü belirtmesi gerekir.  
  
## <a name="const-statement-usage"></a>Const deyimi kullanımı  
 A `Const` deyimi bir matematik temsil veya tarih/saat miktarı:  
  
 [!code-vb[VbEnumsTask#10](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_1.vb)]  
  
 Ayrıca tanımlayabilirsiniz `String` sabitleri:  
  
 [!code-vb[VbEnumsTask#13](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_2.vb)]  
  
 Sağ tarafındaki ifade eşittir işaretinden ( `=` ) genellikle bir sayı veya değişmez değer dize olur, ancak (işlevlere çağrıları ifade içeremez rağmen), bir sayı veya dize sonuçları bir ifade olabilir. Önceden tanımlanmış sabitleri bakımından sabitleri bile tanımlayabilirsiniz:  
  
 [!code-vb[VbEnumsTask#15](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_3.vb)]  
  
## <a name="scope-of-user-defined-constants"></a>Kullanıcı tanımlı sabitler kapsamı  
 A `Const` deyiminin kapsamı aynı konumda bildirilen bir değişken değil. Kapsam aşağıdaki yollardan birini belirtebilirsiniz:  
  
-   Yalnızca bir yordam içinde mevcut bir sabit oluşturmak için bu yordam içinde bildirin.  
  
-   Bir sınıftaki tüm yordamlar ancak bu modül dışında herhangi bir kod için kullanılabilir bir sabit oluşturmak için sınıf bildirimleri bölümünde bildirin.  
  
-   Bir derlemeyi tüm üyeleri ancak derlemenin dış istemciler için kullanılabilir bir sabit oluşturmak için kullanarak bildirme `Friend` sınıf bildirimleri bölümünde anahtar sözcüğü.  
  
-   Uygulama genelinde kullanılabilir bir sabit oluşturmak için kullanarak bildirme `Public` anahtar sözcüğü bildirimlerden bölümünde sınıfı.  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: bir sabit bildirme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).  
  
### <a name="avoiding-circular-references"></a>Döngüsel başvuru önleme  
 Sabitler diğer sabitleri bakımından tanımlanmış olması nedeniyle yanlışlıkla oluşturmak mümkün bir *döngüsü*, ya da iki veya daha fazla sabitler arasında döngüsel başvuru. Diğer, aşağıdaki örnekte olduğu gibi bakımından tanımlanmış her biri iki veya daha fazla ortak sabitleri sahip olduğunda bir döngü oluşur:  
  
 [!code-vb[VbEnumsTask#16](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_4.vb)]  
[!code-vb[VbEnumsTask#17](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_5.vb)]  
  
 Bir döngü ortaya çıkarsa, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] derleyici hatası oluşturur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Const deyimi](../../../../visual-basic/language-reference/statements/const-statement.md)  
 [Sabit ve değişmez değerli veri türleri](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [Sabitler ve numaralandırmalar](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)  
 [Sabitler ve numaralandırmalar](../../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [Numaralandırmalara genel bakış](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [Sabitlere genel bakış](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [Nasıl yapılır: bir numaralandırma bildirme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [Numaralandırmalar ve ad niteliği](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
