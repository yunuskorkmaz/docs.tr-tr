---
title: '\= İşleci'
ms.date: 07/20/2015
f1_keywords:
- '\='
- vb.\=
helpviewer_keywords:
- '\= operator [Visual Basic]'
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator \= [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 6f39915d-e398-4045-afcc-da6885e57b9c
ms.openlocfilehash: 6e749e13c0427354db9e361538d4bef10b6c6b04
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873406"
---
# <a name="-operator"></a>\\= İşleci

Bir değişkenin veya özelliğin değerini bir ifadenin değerine böler ve tamsayı sonucunu değişkene veya özelliğe atar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
variableorproperty \= expression  
```  
  
## <a name="parts"></a>Bölümler  

 `variableorproperty`  
 Gereklidir. Herhangi bir sayısal değişken veya özellik.  
  
 `expression`  
 Gereklidir. Herhangi bir sayısal ifade.  
  
## <a name="remarks"></a>Açıklamalar  

 İşlecinin sol tarafındaki öğesi `\=` basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir. Değişken veya özellik [ReadOnly](../modifiers/readonly.md)olamaz.  
  
 `\=`İşleci, bir değişkenin veya özelliğin değerini solundaki değer ile sola böler ve tamsayı sonucunu sol tarafındaki değişkene veya özelliğe atar  
  
 Tamsayı bölme hakkında daha fazla bilgi için bkz. [\ işleç (Visual Basic)](integer-division-operator.md).  
  
## <a name="overloading"></a>Aşırı Yükleme  

 `\`İşleç *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. İşleci aşırı yüklemek `\` işlecin davranışını etkiler `\=` . Kodunuzun `\=` bir sınıf veya yapı üzerinde kullanması durumunda `\` , yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `\=` bir `Integer` değişkeni ikinci olarak bölmek ve tamsayı sonucunu ilk değişkene atamak için işlecini kullanır.  
  
 [!code-vb[VbVbalrOperators#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#19)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\ İşleci (Visual Basic)](integer-division-operator.md)
- [/= İşleci (Visual Basic)](floating-point-division-assignment-operator.md)
- [Atama Işleçleri](assignment-operators.md)
- [Aritmetik Işleçler](arithmetic-operators.md)
- [Visual Basic'de İşleç Önceliği](operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](operators-listed-by-functionality.md)
- [Deyimler](../../programming-guide/language-features/statements.md)
