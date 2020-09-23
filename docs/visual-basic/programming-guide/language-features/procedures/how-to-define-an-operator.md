---
title: 'Nasıl yapılır: Bir İşleci Tanımlama'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- operator procedures [Visual Basic], about operator procedures
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: d4b0e253-092a-4e6e-9fe2-01f562140a29
ms.openlocfilehash: 5acbd0439ddbb956b80d56e23d11cd5e152f37ff
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91087407"
---
# <a name="how-to-define-an-operator-visual-basic"></a>Nasıl yapılır: Bir İşleci Tanımlama (Visual Basic)

Bir sınıf veya yapı tanımladıysanız, `*` `<>` işlenenleri bir `And` veya her ikisi de sınıfınızın veya yapınızın türü olduğunda standart işlecin (örneğin,, veya) davranışını tanımlayabilirsiniz.  
  
 Standart işleci sınıf veya yapı içinde operatör yordamı olarak tanımlayın. Tüm operatör yordamları olmalıdır `Public` `Shared` .  
  
 Bir sınıf veya yapı üzerinde işleç tanımlamak, işleci *aşırı yükleme* olarak da adlandırılır.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `+` adlı bir yapının işlecini tanımlar `height` . Yapı, fit ve inç cinsinden ölçülen yükseklikleri kullanır. Bir *inç* 2,54 santimetre, bir *Foot* ise 12 inç 'tir. Normalleştirilmiş değerler (inç < 12,0) sağlamak için, Oluşturucu *Modül* 12 aritmetik işlemini gerçekleştirir. `+`İşleci, Normalleştirilmemiş değerler oluşturmak için oluşturucuyu kullanır.  
  
 [!code-vb[VbVbcnProcedures#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#25)]  
  
 Yapıyı aşağıdaki kodla test edebilirsiniz `height` .  
  
 [!code-vb[VbVbcnProcedures#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#26)]  

## <a name="see-also"></a>Ayrıca bkz.

- [İşleç Yordamları](./operator-procedures.md)
- [Nasıl yapılır: Dönüştürme İşleci Tanımlama](./how-to-define-a-conversion-operator.md)
- [Nasıl yapılır: Bir İşleç Yordamı Çağırma](./how-to-call-an-operator-procedure.md)
- [Nasıl yapılır: İşleçleri Tanımlayan Bir Sınıf Kullanma](./how-to-use-a-class-that-defines-operators.md)
- [Operator Deyimi](../../../language-reference/statements/operator-statement.md)
- [Structure Yapısı](../../../language-reference/statements/structure-statement.md)
- [Nasıl yapılır: Yapıyı Bildirme](../data-types/how-to-declare-a-structure.md)
- [Mod İşleci](../../../language-reference/operators/mod-operator.md)
