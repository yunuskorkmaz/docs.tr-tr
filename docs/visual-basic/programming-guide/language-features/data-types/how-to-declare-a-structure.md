---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: yapı bildirme (Visual Basic)'
title: 'Nasıl yapılır: Yapıyı Bildirme'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: 7560f22db70fd5804ca309720d32477bcb9a3782
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100436935"
---
# <a name="how-to-declare-a-structure-visual-basic"></a>Nasıl yapılır: Bir Yapıyı Bildirme (Visual Basic)

Yapı [ifadesiyle](../../../language-reference/statements/structure-statement.md)bir yapı bildirimi başlar ve bunu `End Structure` ifadesiyle sonlandırın. Bu iki deyim arasında en az bir *öğe* bildirmeniz gerekir. Öğeleri herhangi bir veri türünde olabilir, ancak en az bir veya paylaşılmayan olmayan bir değişken ya da paylaşılmayan olmayan bir olay olmalıdır.  
  
 Yapı bildiriminde yapı öğelerinden hiçbirini başlatamıyor. Bir yapı türünde olması için bir değişken bildirdiğinizde, değişkenine değerleri değişken aracılığıyla erişerek atayabilirsiniz.  
  
 Yapılar ve sınıflar arasındaki farklılıklarla ilgili bir tartışma için bkz. [yapılar ve sınıflar](structures-and-classes.md).  
  
 Tanıtım amacıyla, bir çalışanın adını, telefon uzantısını ve maaşını izlemek istediğiniz bir durum düşünün. Bir yapı bunu tek bir değişkende yapmanıza olanak sağlar.  
  
### <a name="to-declare-a-structure"></a>Bir yapıyı bildirmek için  
  
1. Yapı için başlangıç ve bitiş deyimlerini oluşturun.  
  
     [Ortak](../../../language-reference/modifiers/public.md), [korumalı](../../../language-reference/modifiers/protected.md), [arkadaş](../../../language-reference/modifiers/friend.md)veya [özel](../../../language-reference/modifiers/private.md) anahtar sözcüğünü kullanarak bir yapının erişim düzeyini belirtebilir veya buna varsayılan olarak izin verebilirsiniz `Public` .  
  
    ```vb  
    Private Structure employee  
    End Structure  
    ```  
  
2. Yapının gövdesine öğe ekleyin.  
  
     Bir yapının en az bir öğesi olmalıdır. Her öğeyi bildirmeniz ve bunun için bir erişim düzeyi belirtmeniz gerekir. [Dim ifadesini](../../../language-reference/statements/dim-statement.md) herhangi bir anahtar sözcük olmadan kullanırsanız, erişilebilirlik varsayılan olarak olur `Public` .  
  
    ```vb  
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
  
     `salary`Yukarıdaki örnekteki alan, `Private` kapsayan sınıftan bile yapının dışından erişilemediği anlamına gelir. Ancak yordam, `giveRaise` `Public` Yapı dışından çağrılabilir. Benzer şekilde, `salaryReviewTime` olayı yapının dışından yükseltebilirsiniz.  
  
     Değişkenlere, `Sub` yordamlara ve olaylara ek olarak, `Function` bir yapıda sabitler, yordamlar ve özellikler de tanımlayabilirsiniz. En az bir bağımsız değişken alması şartıyla, en az bir özelliği *varsayılan özellik* olarak belirleyebilirsiniz. Bir olayı, paylaşılan bir yordamla işleyebilirsiniz [](../../../language-reference/modifiers/shared.md) `Sub` . Daha fazla bilgi için bkz. [nasıl yapılır: Visual Basic ' de varsayılan bir özellik bildirme ve çağırma](../procedures/how-to-declare-and-call-a-default-property.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri türleri](index.md)
- [Başlangıç Veri Türleri](elementary-data-types.md)
- [Bileşik Veri Türleri](composite-data-types.md)
- [Değer türleri ve başvuru türleri](value-types-and-reference-types.md)
- [Yapılar](structures.md)
- [Veri Türü Sorunlarını Giderme](troubleshooting-data-types.md)
- [Yapı Değişkenleri](structure-variables.md)
- [Yapılar ve Diğer Programlama Öğeleri](structures-and-other-programming-elements.md)
- [Yapılar ve Sınıflar](structures-and-classes.md)
- [Kullanıcı Tanımlı Veri Türü](../../../language-reference/data-types/user-defined-data-type.md)
