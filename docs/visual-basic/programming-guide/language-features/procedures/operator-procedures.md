---
title: İşleç Yordamları (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8fba5180da6498d280fa4192937c39d3e33168e8
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="operator-procedures-visual-basic"></a>İşleç Yordamları (Visual Basic)
Bir dizi standart işleci davranışını tanımlamak Visual Basic deyimi bir işleç yordamı olduğu (gibi `*`, `<>`, veya `And`) bir sınıf veya yapı tanımladığınız. Bu da adlandırılır *İşleç aşırı yüklemesi*.  
  
## <a name="when-to-define-operator-procedures"></a>İşleç yordamları tanımlamak ne zaman  
 Bir sınıf veya yapı tanımlandığında, bu sınıf veya yapı türünde olmasını değişkenleri bildirebilirsiniz. Bazen bir ifadenin bir parçası olarak bir işlem katılmayı gibi bir değişken gerekiyor. Bunu yapmak için bir işlecinin işleneni olmalıdır.  
  
 Visual Basic işleçleri üzerinde yalnızca kendi temel veri türlerini tanımlar. Bir işleç davranışını tanımlamak ya da işlenen her ikisi de sınıf veya yapı türünü.  
  
 Daha fazla bilgi için bkz: [Operator deyimi](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
## <a name="types-of-operator-procedure"></a>İşleç yordamı türleri  
 Bir işleç yordamı şu türlerden biri olabilir:  
  
-   Bağımsız değişken sınıf veya yapı türünü olduğu birli işleç tanımı.  
  
-   Sınıf veya yapı türünü olduğu en az bir bağımsız değişken ikili işleç tanımı.  
  
-   Bağımsız değişken sınıf veya yapı türünü olduğu bir dönüşüm işleci tanımı.  
  
-   Sınıf veya yapı türü döndüren bir dönüşüm işleci tanımı.  
  
 Dönüştürme işleçleri her zaman birli ve her zaman kullanmanız `CType` olduğunu tanımlama işleci olarak.  
  
## <a name="declaration-syntax"></a>Bildirim Sözdizimi  
 Bir işleç yordamı bildirme söz dizimi aşağıdaki gibidir:  
  
 `Public Shared`   `[Widening | Narrowing]`   `Operator`  *işlecin* `(` *operand1*`[,`*operand2* `]) As` *veri türü*   
  
 `' Statements of the operator procedure.`  
  
 `End Operator`  
  
 Kullandığınız `Widening` veya `Narrowing` anahtar sözcüğü yalnızca bir tür dönüştürme işleci. İşleç simgesi her zaman olduğu [CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md) için tür dönüştürme işleci.  
  
 İkili işleç tanımlamak için iki işlenen bildirme ve bir tür dönüştürme işleci dahil olmak üzere bir birli işleç tanımlamak için bir işlenen bildirin. Tüm işlenenleri bildirilmelidir `ByVal`.  
  
 Her işlenen parametrelerini bildirme aynı şekilde bildirme [alt yordamlar](./sub-procedures.md).  
  
### <a name="data-type"></a>Veri Türü  
 Bir sınıf veya yapı tanımladığınız bir işleci tanımlama olduğundan, işlenen en az biri bu sınıf veya yapı, veri türü olmalıdır. Tür dönüştürme işleci için işlenen veya dönüş türü sınıf veya yapı, veri türü olmalıdır.  
  
 Daha fazla ayrıntı için bkz: [Operator deyimi](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
## <a name="calling-syntax"></a>Arama sözdizimi  
 Bir işleç yordamı örtük olarak bir ifadede işleç simgesi kullanarak çağırır. Önceden tanımlı işleçler için yaptığınız gibi işlenen sağlayın.  
  
 Bir işleç yordamı için örtük bir arama söz dizimi aşağıdaki gibidir:  
  
 `Dim testStruct As`  *structurename*  
  
 `Dim testNewStruct As`  *structurename*`= testStruct`*işlecin*   `10`  
  
### <a name="illustration-of-declaration-and-call"></a>Bildirim ve çağrı çizimi  
 Aşağıdaki yapısını imzalı 128-bit tamsayı değeri bağlı sırası yüksek ve düşük düzey parçaları olarak depolar. Tanımladığı `+` iki eklemek için işleci `veryLong` değerleri ve bir kaynaklanan oluşturmak `veryLong` değeri.  
  
 [!code-vb[VbVbcnProcedures#23](./codesnippet/VisualBasic/operator-procedures_1.vb)]  
  
 Aşağıdaki örnek tipik bir çağrı gösterilmektedir `+` tanımlanan işleci `veryLong`.  
  
 [!code-vb[VbVbcnProcedures#24](./codesnippet/VisualBasic/operator-procedures_2.vb)]  
  
 Daha fazla bilgi ve örnekler için bkz: [İşleç aşırı yüklemesi Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamlar](./index.md)  
 [Alt Yordamlar](./sub-procedures.md)  
 [İşlev Yordamları](./function-procedures.md)  
 [Özellik Yordamları](./property-procedures.md)  
 [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)  
 [Operator Deyimi](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Nasıl yapılır: İşleç Tanımlama](./how-to-define-an-operator.md)  
 [Nasıl yapılır: Dönüştürme İşleci Tanımlama](./how-to-define-a-conversion-operator.md)  
 [Nasıl yapılır: Bir İşleç Yordamı Çağırma](./how-to-call-an-operator-procedure.md)  
 [Nasıl yapılır: İşleçleri Tanımlayan Bir Sınıf Kullanma](./how-to-use-a-class-that-defines-operators.md)
