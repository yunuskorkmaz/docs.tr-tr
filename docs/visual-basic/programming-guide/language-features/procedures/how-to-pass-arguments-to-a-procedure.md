---
title: 'Nasıl yapılır: Bağımsız değişkenleri geçirmek yordamına (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- arguments [Visual Basic], passing to procedures
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], calling
- argument passing [Visual Basic], procedures
ms.assetid: 08723588-3890-4ddc-8249-79e049e0f241
ms.openlocfilehash: 012ad8e6229958575030ee820a3b0b79cc50facc
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59333918"
---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a>Nasıl yapılır: Bağımsız değişkenleri geçirmek yordamına (Visual Basic)
Bir yordamı çağırdığınızda, parantez içinde bir bağımsız değişken listesiyle yordam adı izleyin. Yordamı tanımlar için gerekli her parametre karşılık gelen bir bağımsız değişken sağlayın ve isteğe bağlı bağımsız değişkenler sağlayabilirsiniz `Optional` parametreleri. Sağladığınız değil, bir `Optional` çağrı parametresi, sağladığınız sonraki herhangi bir bağımsız değişken, bunun yerine bağımsız değişken listesinde işaretlemek için virgül içermesi gerekir.  
  
 Bir veri türünde bir bağımsız değişken, karşılık gelen parametresinin farklı geçirileceğini düşünüyorsanız `Byte` için `String`, tür denetimi anahtarı ayarlayabilirsiniz ([Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) için `Off`. Varsa `Option Strict` olduğu `On`, kullanmanız gerekir veya açık dönüşüm anahtar sözcükleri dönüştürme işlemleri genişletme. Daha fazla bilgi için [Widening ve daraltma dönüşümleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) ve [tür dönüştürme işlevleri](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 Daha fazla bilgi için [parametreler ve bağımsız değişkenler](./procedure-parameters-and-arguments.md).  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a>Bir yordam için bir veya daha fazla bağımsız değişkenleri geçirmek için  
  
1. Arama deyiminde parantezler yordamın adıyla izleyin.  
  
2. Parantez içinde bir bağımsız değişken listesi yerleştirin. Yordamı tanımlar her gerekli parametre için bir bağımsız değişken içerir ve bağımsız değişkenlerin virgülle ayırın.  
  
3. Her değişken için karşılık gelen parametre veri öğesine dönüştürülebilir bir türün yordamı türü olarak değerlendirilen bir geçerli ifade tanımlar olduğundan emin olun.  
  
4. Bir parametre olarak tanımlanmışsa [isteğe bağlı](../../../../visual-basic/language-reference/modifiers/optional.md), bağımsız değişken listesinde içerebilir veya atlayın. Atlarsanız, yordam Bu parametre için tanımlanan varsayılan değeri kullanır.  
  
5. Bir bağımsız değişken atlarsanız bir `Optional` parametresi ve başka bir parametre sonra parametre listesinde, bir atlanmış bağımsız değişkeni yerine, bağımsız değişken listesinde fazladan bir virgül tarafından işaretleyebilirsiniz.  
  
     Aşağıdaki örnek, Visual Basic çağırır <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> işlevi.  
  
     [!code-vb[VbVbcnProcedures#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#34)]  
  
     Yukarıdaki örnekte, görüntülenecek iletiyi dize gerekli ilk bağımsız değişkeni sağlar. Bu ileti kutusunda gösterilecek düğmeler belirten isteğe bağlı ikinci parametresi için bağımsız değişken atlar. Çağrısı bir değer sağlamaz çünkü `MsgBox` varsayılan değeri kullandığını `MsgBoxStyle.OKOnly`, yalnızca görüntüleyen bir **Tamam** düğmesi.  
  
     İkinci bağımsız değişken listesinde virgülden belirtilmemişse ikinci bağımsız değişkenin bir yerde işaretler ve son dizeyse, isteğe bağlı üçüncü parametresi için geçirilen `MsgBox`, başlık çubuğunda görüntülenecek metni olduğu.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Alt Yordamlar](./sub-procedures.md)
- [İşlev Yordamları](./function-procedures.md)
- [Özellik Yordamları](./property-procedures.md)
- [İşleç Yordamları](./operator-procedures.md)
- [Nasıl yapılır: Bir Yordamın Parametresini Tanımlama](./how-to-define-a-parameter-for-a-procedure.md)
- [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](./passing-arguments-by-value-and-by-reference.md)
- [Özyinelemeli Yordamlar](./recursive-procedures.md)
- [Yordam Aşırı Yüklemesi](./procedure-overloading.md)
- [Nesneler ve Sınıflar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Nesne odaklı programlama (Visual Basic)](../../concepts/object-oriented-programming.md)
