---
title: İşleç Yordamları (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
ms.assetid: 8c513d38-246b-4fb7-8b75-29e1364e555b
ms.openlocfilehash: cafc742474d6f7b46fbfb73374a59a350812a2a5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64639096"
---
# <a name="operator-procedures-visual-basic"></a>İşleç Yordamları (Visual Basic)
Bir işleç yordamı standart işlecinin davranışını tanımlayan Visual Basic deyimleri bir dizisidir (gibi `*`, `<>`, veya `And`) bir sınıf veya yapı tanımladığınız üzerinde. Bu da adlandırılır *İşleç aşırı yüklemesi*.  
  
## <a name="when-to-define-operator-procedures"></a>İşleç yordamları tanımlamak ne zaman  
 Bir sınıf veya yapı tanımlandığında, bu sınıfın veya yapının türünde olmasını değişkenleri bildirebilirsiniz. Bazen bir ifadenin bir parçası olarak bir işlem katılmak bu tür bir değişken gerekiyor. Bunu yapmak için bir işlecinin bir işleneni olmalıdır.  
  
 Visual Basic, yalnızca temel veri türleri üzerinde işleçler tanımlar. Bir operatörün davranışını tanımlayabilirsiniz veya iki işlenenleri sınıf veya yapının türüdür.  
  
 Daha fazla bilgi için [Operator deyimi](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
## <a name="types-of-operator-procedure"></a>İşleç yordamı türleri  
 Bir işleç yordamı şu türlerden biri olabilir:  
  
- Bağımsız değişkeni, sınıfın veya yapının türünü olduğu birli işleç tanımı.  
  
- Sınıf veya yapı türünde olduğu en az bir bağımsız değişken ikili bir işleç tanımını.  
  
- Bağımsız değişkeni, sınıfın veya yapının türünü olduğu bir dönüştürme operatörünün tanımı.  
  
- Sınıf veya yapı türü döndüren bir dönüştürme operatörünün tanımı.  
  
 Dönüştürme işleçleri her zaman birli ve her zaman `CType` olduğunu tanımlama işleci olarak.  
  
## <a name="declaration-syntax"></a>Bildirim Sözdizimi  
 Bir işleç yordamı bildirmek için sözdizimi aşağıdaki gibidir:  
  
 `Public Shared`   `[Widening | Narrowing]`   `Operator`  *işlecin* `(` *işlenen1*`[,`*işlenen2* `]) As` *veri türü*  
  
 `' Statements of the operator procedure.`  
  
 `End Operator`  
  
 Kullandığınız `Widening` veya `Narrowing` yalnızca bir tür dönüştürme işleci anahtar sözcüğü. Her zaman işlecin olduğu [CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md) için tür dönüştürme işleci.  
  
 İkili işleç tanımlamak için iki işlenenden bildirme ve bir tür dönüştürme işleci dahil olmak üzere bir birli işleç tanımlamak için tek bir işlenen bildirin. Tüm işlenenler bildirilmelidir `ByVal`.  
  
 Her işlenen bildirmek için parametreleri aynı şekilde bildirmek [alt yordamlar](./sub-procedures.md).  
  
### <a name="data-type"></a>Veri Türü  
 Bir sınıf veya yapı sizin tanımladığınız bir işleci tanımlama için en az bir işlenen, sınıfın veya yapının veri türünde olmalıdır. Tür dönüştürme işleci için işlenen ya da dönüş türü, sınıfın veya yapının veri türünde olmalıdır.  
  
 Daha fazla ayrıntı için [Operator deyimi](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
## <a name="calling-syntax"></a>Arama söz dizimi  
 Bir işleç yordamı örtük olarak bir ifadede operatör sembolünü kullanarak çağırın. Önceden tanımlı operatörler için yaptığınız gibi işlenenler sağladığınız.  
  
 Bir işleç yordamı örtük çağrıyla sözdizimi aşağıdaki gibidir:  
  
 `Dim testStruct As`  *structurename*  
  
 `Dim testNewStruct As`  *structurename*`= testStruct`*işlecin*  `10`  
  
### <a name="illustration-of-declaration-and-call"></a>Bildirim ve çağrı gösterimi  
 Aşağıdaki yapıya bağlı yüksek ve düşük düzey parçaları olarak 128-bit imzalı bir tamsayı değeri depolar. Tanımladığı `+` işleci iki eklemek için `veryLong` değerleri ve bir sonuç üretmek `veryLong` değeri.  
  
 [!code-vb[VbVbcnProcedures#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#23)]  
  
 Aşağıdaki örnek, tipik bir çağrı gösterir `+` tanımlanan işleci `veryLong`.  
  
 [!code-vb[VbVbcnProcedures#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#24)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Alt Yordamlar](./sub-procedures.md)
- [İşlev Yordamları](./function-procedures.md)
- [Özellik Yordamları](./property-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Operator Deyimi](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Nasıl yapılır: Bir işleci tanımlama](./how-to-define-an-operator.md)
- [Nasıl yapılır: Bir dönüşüm işleci tanımlama](./how-to-define-a-conversion-operator.md)
- [Nasıl yapılır: Bir işleç yordamı çağırma](./how-to-call-an-operator-procedure.md)
- [Nasıl yapılır: İşleçleri tanımlayan bir sınıf kullanma](./how-to-use-a-class-that-defines-operators.md)
