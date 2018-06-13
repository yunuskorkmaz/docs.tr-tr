---
title: 'Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme (Visual Basic)'
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
ms.openlocfilehash: f393f17f87c5920fb9bfa2a2097c09d48bebdc16
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650598"
---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a>Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme (Visual Basic)
Bir yordam çağrısı için bağımsız değişken listesi parantez içinde yordam adıyla izleyin. Yordam tanımlar her gerekli parametre için karşılık gelen bir bağımsız değişken sağlayın ve isteğe bağlı olarak bağımsız değişkenleri sağlayın `Optional` parametreleri. Sağladığınız değil, bir `Optional` çağrısında parametre, sonraki tüm bağımsız değişkenleri sağlamış olursunuz, onun yerine bağımsız değişken listesinde işaretlemek için virgül içermelidir.  
  
 Bir veri türünde bir bağımsız değişken gibi kendi karşılık gelen bir parametre farklı geçirmek istiyorsanız, `Byte` için `String`, tür denetlemesi anahtarı ayarlayabilirsiniz ([Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) için `Off`. Varsa `Option Strict` olan `On`, ya da kullanmalıdır dönüşümleri veya açık dönüşüm anahtar sözcükleri genişletme. Daha fazla bilgi için bkz: [Widening ve daraltma dönüşümleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) ve [tür dönüştürme işlevleri](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 Daha fazla bilgi için bkz: [parametreler ve bağımsız değişkenler](./procedure-parameters-and-arguments.md).  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a>Bir yordama bağımsız değişkenlerden biri veya daha fazla geçirmek için  
  
1.  Arama deyiminde parantez yordamı adıyla izleyin.  
  
2.  Parantez içinde bir bağımsız değişken listesi yerleştirin. Bağımsız değişkenler virgülle ayırın ve yordam tanımlar her gerekli parametre için bir bağımsız değişken içerir.  
  
3.  Her değişken için karşılık gelen bir parametre türü yordamı bir veri türüne dönüştürülebilir değerlendiren geçerli bir ifade tanımlar olduğundan emin olun.  
  
4.  Bir parametre olarak tanımlanmışsa [isteğe bağlı](../../../../visual-basic/language-reference/modifiers/optional.md), bağımsız değişken listesinde içerebilir veya onu atlayın. Yordam atlarsanız, bu parametre için tanımlanan varsayılan değeri kullanır.  
  
5.  Bir bağımsız değişken atlarsanız bir `Optional` parametre ve başka bir parametre sonra parametre listesinde, bağımsız değişken listesinde fazladan bir virgül tarafından belirtilmemiş bağımsız değişkeni yerine işaretleyebilirsiniz.  
  
     Aşağıdaki örnek Visual Basic çağırır <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> işlevi.  
  
     [!code-vb[VbVbcnProcedures#34](./codesnippet/VisualBasic/how-to-pass-arguments-to-a-procedure_1.vb)]  
  
     Önceki örnekte görüntülenecek ileti dizesi gerekli ilk bağımsız sağlar. İleti kutusu görüntülenecek düğmeleri belirten isteğe bağlı ikinci parametre için bir bağımsız değişken atlar. Çağrısı bir değer sağlamaz çünkü `MsgBox` varsayılan değeri kullanır `MsgBoxStyle.OKOnly`, yalnızca görüntüleyen bir **Tamam** düğmesi.  
  
     Bağımsız değişken listesinde ikinci virgülle belirtilmemişse ikinci bağımsız değişkeni yerine işaretler ve son dize için isteğe bağlı üçüncü parametresi, geçirilen `MsgBox`, başlık çubuğunda görüntülenecek metni olduğu.  
  
## <a name="see-also"></a>Ayrıca bkz.

 [Alt Yordamlar](./sub-procedures.md)  
 [İşlev Yordamları](./function-procedures.md)  
 [Özellik Yordamları](./property-procedures.md)  
 [İşleç Yordamları](./operator-procedures.md)  
 [Nasıl yapılır: Bir Yordamın Parametresini Tanımlama](./how-to-define-a-parameter-for-a-procedure.md)  
 [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](./passing-arguments-by-value-and-by-reference.md)  
 [Özyinelemeli Yordamlar](./recursive-procedures.md)  
 [Yordam Aşırı Yüklemesi](./procedure-overloading.md)  
 [Nesneler ve Sınıflar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Nesne odaklı programlama (Visual Basic)](../../concepts/object-oriented-programming.md)  
