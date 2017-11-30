---
title: "Nasıl yapılır: Bir Yordam Bağımsız Değişkenini Değer Değişikliklerine Karşı Koruma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: d2b7c766-ce16-4d2c-8d79-3fc0e7ba2227
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7975cbbc38c39223a4af5c87ac6bb090be548f2d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a>Nasıl yapılır: Bir Yordam Bağımsız Değişkenini Değer Değişikliklerine Karşı Koruma (Visual Basic)
Bir yordam parametre olarak bildirirse [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] yordamı kod çağıran kodu değişkeninde temel programlama öğesi için doğrudan bir başvuru sağlar. Bu, yordamı çağıran kodu değişkeninde alttaki değerini değiştirmek için izin verir. Bazı durumlarda, bu tür bir değişiklik karşı korumak çağıran kodu isteyebilirsiniz.  
  
 Her zaman bir bağımsız değişken değişikliği karşılık gelen bir parametre bildirerek Koruyabileceğiniz [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) yordamda. Bazı durumlarda ancak diğer belirtilen bir bağımsız değişkeni değiştirmek istiyorsanız, bildirebilir `ByRef` ve her çağrıda geçirme mekanizması belirlemek çağıran kodu izin verin. Karşılık gelen bağımsız değişkeni değere göre geçirilecek parantez içinde kapsayan ya da bu başvuruya göre geçirmek için parantez içinde kapsayan değil bunu yapar. Daha fazla bilgi için bkz: [nasıl yapılır: bağımsız değişkeni değere göre bayraklarıdır için zorlama](./how-to-force-an-argument-to-be-passed-by-value.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir dizi değişkeni alabilir ve çalışan iki yordam üzerinde öğeleri gösterir. `increase` Yordamı yalnızca ekler her öğe için. `replace` Yordamı atar yeni bir dizi parametre `a()` ve her öğe için ekler. Ancak, yeniden atama çağıran kodu temel alınan dizi değişkeni etkilemez.  
  
 [!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#38](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_3.vb)]  
  
 İlk `MsgBox` çağrısı görüntüler "increase(n) sonra: 11, 21, 31, 41". Çünkü dizi `n` bir başvuru türü `replace` geçirme mekanizması olmamasına rağmen bu grubun üyeleri değiştirebilirsiniz `ByVal`.  
  
 İkinci `MsgBox` çağrısı görüntüler "replace(n) sonra: 11, 21, 31, 41". Çünkü `n` geçirilen `ByVal`, `replace` değişkeni değiştirilemiyor `n` yeni bir dizi atayarak çağıran kodu. Zaman `replace` yeni dizi örneği oluşturur `k` ve yerel bir değişkene atar `a`, başvuru kaybederse `n` çağıran kodu tarafından geçirilen. Üyeleri değiştiğinde `a`, yalnızca yerel dizi `k` etkilenir. Bu nedenle, `replace` dizi değerlerini artırmaz `n` çağıran kodu.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Varsayılan olarak [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] bağımsız değişkenleri değere göre geçirmektir. Ancak, ya da dahil etmek için uygulama programlama iyi [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) veya [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) bildirilen her parametre olan anahtar sözcük. Bu, kodunuzu okumak kolaylaştırır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamları](./index.md)  
 [Parametreler ve bağımsız değişkenler](./procedure-parameters-and-arguments.md)  
 [Nasıl yapılır: bir yordama bağımsız değişkenler geçirme](./how-to-pass-arguments-to-a-procedure.md)  
 [Bağımsız değişkenleri değere ve başvuruya göre geçirme](./passing-arguments-by-value-and-by-reference.md)  
 [Değiştirilebilir ve değiştirilemez bağımsız değişkenler arasındaki farklar](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [Değere ve başvuruya göre bağımsız değişken geçirme arasındaki farklar](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [Nasıl yapılır: bir yordam bağımsız değişkeninin değerini değiştirme](./how-to-change-the-value-of-a-procedure-argument.md)  
 [Nasıl yapılır: bağımsız değişkeni değere göre geçirilecek şekilde zorlama](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [Bağımsız değişkenleri konuma göre ve ada göre geçirme](./passing-arguments-by-position-and-by-name.md)  
 [Değer türleri ve başvuru türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
