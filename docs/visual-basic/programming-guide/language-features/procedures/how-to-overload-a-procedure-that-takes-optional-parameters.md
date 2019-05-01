---
title: 'Nasıl yapılır: (Visual Basic) isteğe bağlı parametreler isteyen bir yordamı aşırı yükleme'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], optional parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: 825f9d56-4cde-43fd-993a-b9171717e2eb
ms.openlocfilehash: 58c52a7d73efbd96d772dd85d6bf2c9084fb1241
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61863655"
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a>Nasıl yapılır: (Visual Basic) isteğe bağlı parametreler isteyen bir yordamı aşırı yükleme
Bir veya daha fazla yordam varsa, [isteğe bağlı](../../../../visual-basic/language-reference/modifiers/optional.md) parametreleri, herhangi bir örtük bunun aşırı yüklerinden eşleşen aşırı yüklenmiş bir sürümünü tanımlayamaz. "Daha fazla bilgi için örtük aşırı yüklemeleri için isteğe bağlı parametreleri" bölümüne bakın [aşırı yükleme yordamları Hususlarına](./considerations-in-overloading-procedures.md).  
  
## <a name="one-optional-parameter"></a>Bir isteğe bağlı parametre  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a>İsteğe bağlı bir parametre isteyen bir yordamı aşırı yükleme için  
  
1. Yazma bir `Sub` veya `Function` parametre listesinde isteğe bağlı parametre içeren bildirim deyimindeki. Kullanmayın `Optional` anahtar sözcüğü Bu aşırı yüklenmiş bir sürüm.  
  
2. Önünde `Sub` veya `Function` anahtar sözcüğü ile [aşırı](../../../../visual-basic/language-reference/modifiers/overloads.md) anahtar sözcüğü.  
  
3. Çağıran kod sağlayan isteğe bağlı bağımsız değişken olduğunda yürütülecek yordamı kod yazın.  
  
4. Yordama sonlandırmak `End Sub` veya `End Function` uygun şekilde deyimi.  
  
5. İsteğe bağlı parametresi parametre listesinde içermez dışında ilk bildirimi için aynı olan ikinci bir bildirim deyiminin yazın.  
  
6. Çağıran kod, isteğe bağlı bağımsız değişken sağlamıyor yürütülecek yordamı kod yazın. Yordama sonlandırmak `End Sub` veya `End Function` uygun şekilde deyimi.  
  
     Aşağıdaki örnek, iki aşırı yüklenmiş yordamlar ve son olarak geçersiz ve geçerli aşırı yüklü sürümlerini örnekleri bir denk kümesi bir isteğe bağlı parametresi tanımlı bir yordam gösterir.  
  
     [!code-vb[VbVbcnProcedures#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#59)]  
  
     [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
     [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
## <a name="multiple-optional-parameters"></a>Birden fazla isteğe bağlı parametreler  
 Birden fazla isteğe bağlı parametre içeren bir yordam için normalde ikiden fazla aşırı yüklenmiş sürümleri gerekir. Örneğin, iki isteğe bağlı parametre vardır ve çağıran kod sağlayın veya her biri birbirinden atlarsanız, belirtilen bağımsız değişkenleri her bir olası kombinasyonu için dört aşırı yüklenmiş sürümleri gerekir.  
  
 İsteğe bağlı parametrelerin sayısı arttıkça, aşırı yükleme karmaşıklığı artırır. N isteğe bağlı parametreler için sağlanan bağımsız değişkenler bazı birleşimlerini kabul edilebilir olmayan sürece 2 gereksinim ^ N aşırı yüklü sürümler. Yordamı doğasına bağlı olarak, mantıksal netliğini tüm aşırı yüklenmiş sürümleri tanımlama için fazladan çaba yaslar bulabilirsiniz.  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a>Birden fazla isteğe bağlı parametre isteyen bir yordamı aşırı yükleme için  
  
1. Sağlanan isteğe bağlı bağımsız değişkenlere hangi birleşimleri yordamın mantığı için kabul edilebilir olduğunu belirleyin. İsteğe bağlı bir parametre başka bağlıysa kabul edilemez bir birleşimi ortaya çıkabilir. Örneğin, bir parametre bir eşin adını kabul eder ve başka bir eşin yaş kabul eder, yaş sağlama ancak ad atlama bağımsız değişkenlerin bir birleşimi kabul edilebilir değil.  
  
2. Sağlanan isteğe bağlı bağımsız değişkenler için her kabul edilebilir birleşim yazma bir `Sub` veya `Function` bildirim deyimindeki, karşılık gelen parametre listesi tanımlar. Kullanmayın `Optional` anahtar sözcüğü.  
  
3. Her bildiriminde önünde `Sub` veya `Function` anahtar sözcüğü ile [aşırı](../../../../visual-basic/language-reference/modifiers/overloads.md) anahtar sözcüğü.  
  
4. Her bildirimi çağıran kod sağlayan bu bildirimin parametre listesine karşılık gelen bir bağımsız değişken listesi, yürütülecek yordamı kod yazın.  
  
5. Her bir yordam sonlandırmak `End Sub` veya `End Function` uygun şekilde deyimi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [İsteğe Bağlı Parametreler](./optional-parameters.md)
- [Parametre Dizileri](./parameter-arrays.md)
- [Yordam Aşırı Yüklemesi](./procedure-overloading.md)
- [Yordam Sorunlarını Giderme](./troubleshooting-procedures.md)
- [Nasıl yapılır: Bir yordamın birden fazla sürümünü tanımlama](./how-to-define-multiple-versions-of-a-procedure.md)
- [Nasıl yapılır: Aşırı yüklenmiş bir yordamı çağırma](./how-to-call-an-overloaded-procedure.md)
- [Nasıl yapılır: Belirsiz sayıda parametre isteyen bir yordamı aşırı yükleme](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Aşırı Yükleme Çözümü](./overload-resolution.md)
