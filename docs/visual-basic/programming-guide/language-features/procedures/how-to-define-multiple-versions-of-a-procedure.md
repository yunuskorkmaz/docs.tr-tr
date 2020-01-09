---
title: 'Nasıl yapılır: Bir Yordamın Birden Fazla Sürümünü Tanımlama'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
ms.openlocfilehash: e8ed9a6356b7177b2c029a9280d0790a93676653
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347594"
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a>Nasıl yapılır: Bir Yordamın Birden Fazla Sürümünü Tanımlama (Visual Basic)
Aynı adı ancak her sürüm için farklı bir parametre listesini kullanarak, onu *aşırı* yükleyerek birden çok sürümde bir yordam tanımlayabilirsiniz. Aşırı yükleme amacı, bir yordamın adına göre ayrım yapmadan daha yakından ilgili birkaç sürümünü tanımlamaktır.  
  
 Daha fazla bilgi için bkz. [yordam aşırı yüklemesi](./procedure-overloading.md).  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a>Bir yordamın birden fazla sürümünü tanımlamak için  
  
1. Tanımlamak istediğiniz yordamın her sürümü için bir `Sub` veya `Function` bildirim bildirimi yazın. Her bildirimde aynı yordam adını kullanın.  
  
2. Her bildirimdeki `Sub` veya `Function` anahtar sözcüğünün önüne [aşırı yüklemeler](../../../../visual-basic/language-reference/modifiers/overloads.md) anahtar sözcüğünü ekleyin. İsteğe bağlı olarak bildirimlerinizde `Overloads` atlayabilirsiniz, ancak bu bildirimi herhangi bir bildirime eklerseniz, her bildirime dahil etmeniz gerekir.  
  
3. Her bildirim ifadesinin ardından, çağıran kodun bu sürümün parametre listesiyle eşleşen bağımsız değişkenler sağladığı belirli bir durumu işlemek için yordam kodu yazın. Çağıran kodun sağladığı parametreleri test etmek zorunda değilsiniz. Visual Basic, denetimi prosedürünün eşleşen sürümüne geçirir.  
  
4. Yordamın her sürümünü, `End Sub` veya `End Function` ifadesiyle uygun şekilde sonlandırın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir müşterinin bakiyesine karşı bir işlem göndermek için bir `Sub` yordamı tanımlar. Yordamın, müşteriyi adı ve diğer hesap numarasına göre kabul eden iki sürümü tanımlamak için `Overloads` anahtar sözcüğünü kullanır.  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
 Çağıran kod, müşteri kimliğini bir `String` veya `Integer`olarak edinebilir ve sonra aynı çağırma ifadesini her iki durumda da kullanabilir.  
  
 `post` yordamının bu sürümlerini çağırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: çağrı aşırı yüklenmiş bir yordam](./how-to-call-an-overloaded-procedure.md).  
  
## <a name="compile-the-code"></a>Kod derleme  
 Aşırı yüklenmiş sürümlerden her birinin aynı yordam adına, ancak farklı bir parametre listesine sahip olduğundan emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Yordam Sorunlarını Giderme](./troubleshooting-procedures.md)
- [Nasıl yapılır: İsteğe Bağlı Parametreler İsteyen Bir Yordamı Aşırı Yükleme](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Nasıl yapılır: Belirsiz Sayıda Parametre İsteyen Bir Yordamı Aşırı Yükleme](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Yordamları Aşırı Yüklemeye İlişkin Düşünceler](./considerations-in-overloading-procedures.md)
- [Aşırı Yükleme Çözümü](./overload-resolution.md)
