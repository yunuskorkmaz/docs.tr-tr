---
title: "Nasıl yapılır: Bir Yapıyı Bildirme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8203327e189d095c9f7ceeb3b68ea24efe9ba882
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-a-structure-visual-basic"></a>Nasıl yapılır: Bir Yapıyı Bildirme (Visual Basic)
Yapı bildirimleri ile başlayan [Structure deyimi](../../../../visual-basic/language-reference/statements/structure-statement.md), ve onunla bitiş `End` `Structure` deyimi. Bu iki ifade arasında en az bir bildirmelisiniz *öğesi*. Öğeleri herhangi bir veri türü olabilir, ancak en az bir paylaşılmayan bir değişken ya da paylaşılmayan, de olay olması gerekir.  
  
 Yapı bildirimleri yapısı öğelerinde başlatılamıyor. Bir yapı türüne sahip olması için bir değişken bildirirken, değerler öğelerine değişken üzerinden erişerek atayın.  
  
 Yapılar ve sınıflar arasındaki farklar tartışma için bkz [yapılar ve sınıflar](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).  
  
 Tanıtım amacıyla, bir çalışanın adı, dahili telefon numarası ve maaş izlemek istediğiniz bir durum düşünün. Bir yapısı, tek bir değişkende bunu yapmanızı sağlar.  
  
### <a name="to-declare-a-structure"></a>Bir yapıyı bildirme  
  
1.  Başlangıç ve bitiş deyimleri yapısı için oluşturun.  
  
     Bir yapı kullanarak erişim düzeyini belirleyebileceğiniz [ortak](../../../../visual-basic/language-reference/modifiers/public.md), [korumalı](../../../../visual-basic/language-reference/modifiers/protected.md), [arkadaş](../../../../visual-basic/language-reference/modifiers/friend.md), veya [özel](../../../../visual-basic/language-reference/modifiers/private.md) anahtar sözcüğü veya sağlar, Varsayılan olarak `Public`.  
  
    ```  
    Private Structure employee  
    End Structure  
    ```  
  
2.  Öğeleri yapısı gövdesini ekleyin.  
  
     Bir yapı en az bir öğe olmalıdır. Her öğe bildirme ve bir erişim düzeyini belirtin. Kullanırsanız [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) erişilebilirlik hiçbir anahtar, varsayılan olarak `Public`.  
  
    ```  
    Private Structure employee  
        Public givenName As String  
        Public familyName As String  
        Public phoneExtension As Long  
        Private salary As Decimal  
        Public Sub giveRaise(raise As Double)  
            salary *= raise  
        End Sub  
        Public Event salaryReviewTime()  
    End Structure  
    ```  
  
     `salary` Önceki örnekte alandır `Private`, yani bile içeren sınıfından yapısı dışında erişilemez. Ancak, `giveRaise` yordam `Public`, bu nedenle, gelen dışında yapısı çağrılabilir. Benzer şekilde, yükseltebilirsiniz `salaryReviewTime` olayından yapısı dışında.  
  
     Değişkenlerinin yanı sıra `Sub` yordamları ve olaylar, sabitleri, ayrıca tanımlayabilirsiniz `Function` yordamları ve yapı özellikleri. En çok bir özellik olarak belirleyebilirsiniz *varsayılan özellik*, sağlanan en az bir değişken alır. Bir olay işleyebilir bir [paylaşılan](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub` yordamı. Daha fazla bilgi için bkz: [nasıl yapılır: bildirme ve Visual Basic'te bir varsayılan özellik çağrı](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Başlangıç veri türleri](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Bileşik veri türleri](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Değer türleri ve başvuru türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Yapıları](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Veri türleri sorunlarını giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Yapı değişkenleri](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)  
 [Yapılar ve diğer programlama öğeleri](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 [Yapılar ve sınıflar](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [Kullanıcı tanımlı veri türü](../../../../visual-basic/language-reference/data-types/user-defined-data-type.md)
