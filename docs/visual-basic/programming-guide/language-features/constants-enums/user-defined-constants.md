---
title: Kullanıcı Tanımlı Sabitler (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic], circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants [Visual Basic]
- scope [Visual Basic], constants
- constants [Visual Basic], user-defined
- circular references between constants [Visual Basic]
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
ms.openlocfilehash: dc940105bbeb5e54819b8df5d5b3c831c7a6e145
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527321"
---
# <a name="user-defined-constants-visual-basic"></a>Kullanıcı Tanımlı Sabitler (Visual Basic)
Bir sayı veya dize değişmez yerini alır, anlamlı bir ad bir sabittir. Sabitler adından da anlaşılacağı gibi bir uygulamanın yürütülmesini sabit kalması değerlerini depolar. Denetimleri veya birlikte çalıştığınız bileşenleri tarafından tanımlanan sabitleri kullanabilir veya kendi oluşturabilirsiniz. Kendiniz oluşturduğunuz sabitleri olarak açıklanmıştır *kullanıcı tanımlı*.  
  
 Bir sabit ile bildirme `Const` deyimi, bir değişken adı oluşturmak için yaptığınız aynı yönergeleri kullanarak. Varsa `Option Strict` olduğu `On`, sabit türün açıkça belirtmesi gerekir.  
  
## <a name="const-statement-usage"></a>Const deyimi kullanımı  
 A `Const` deyimi matematiksel bir temsil veya tarih/saat miktarı:  
  
 [!code-vb[VbEnumsTask#10](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_1.vb)]  
  
 Ayrıca tanımlayabilirsiniz `String` sabitleri:  
  
 [!code-vb[VbEnumsTask#13](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_2.vb)]  
  
 Eşittir işareti sağ tarafında ifade ( `=` ) genellikle bir sayı veya dize ancak (işlev çağrıları bu ifade içeremez olsa da) bir sayı veya dize sonucu olan bir ifade olabilir. Önceden tanımlanmış sabitleri açısından sabitleri bile tanımlayabilirsiniz:  
  
 [!code-vb[VbEnumsTask#15](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_3.vb)]  
  
## <a name="scope-of-user-defined-constants"></a>Kullanıcı tanımlı sabitler kapsamı  
 A `Const` deyiminin kapsamı değil, aynı konumda bildirilen bir değişken ile aynı. Kapsam aşağıdaki yollardan birini belirtebilirsiniz:  
  
-   Yalnızca bir yordam içinde var olan bir sabit oluşturmak için bu yordam içinde bildirin.  
  
-   Bir sınıf içindeki tüm yordamlara, ancak bu modül dışında herhangi bir kod için kullanılabilir bir sabit oluşturmak için sınıf bildirimleri bölümünde bildirin.  
  
-   Bir derlemenin tüm üyeleri, ancak derlemenin dışından istemciler için kullanılabilir bir sabit değer oluşturmak için kullanarak bildirin `Friend` sınıf bildirimleri bölümünde anahtar sözcüğü.  
  
-   Uygulamanın tamamında kullanılabilir bir sabit oluşturmak için kullanarak bildirin `Public` bildirimlerinde anahtar sözcük bölümünde sınıfı.  
  
 Daha fazla bilgi için [nasıl yapılır: Bir sabit bildirme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).  
  
### <a name="avoiding-circular-references"></a>Döngüsel başvurular kaçınma  
 Sabitler, diğer sabitleri açısından tanımlanabilir, yanlışlıkla oluşturmak mümkün olmasıdır bir *döngüsü*, ya da iki veya daha fazla sabitler arasında döngüsel başvuru. Diğer, aşağıdaki örnekte olduğu gibi bakımından tanımlanmış her biri iki veya daha fazla genel sabitleri sahip bir döngü gerçekleşir:  
  
 [!code-vb[VbEnumsTask#16](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_4.vb)]  
[!code-vb[VbEnumsTask#17](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_5.vb)]  
  
 Bir döngü meydana gelirse, Visual Basic derleyici hatası oluşturur.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Const Deyimi](../../../../visual-basic/language-reference/statements/const-statement.md)
- [Sabit ve Değişmez Değerli Veri Türleri](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [Sabitler ve Sabit Listeleri](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)
- [Sabitler ve Sabit Listeleri](../../../../visual-basic/language-reference/constants-and-enumerations.md)
- [Sabit Listelerine Genel Bakış](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [Sabitlere Genel Bakış](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Nasıl yapılır: Bir numaralandırma bildirme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Sabit Listeleri ve Ad Niteliği](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Option Strict Deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
