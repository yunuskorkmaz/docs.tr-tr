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
ms.openlocfilehash: 2661603ba33dd0bc28ac1a192794a4534225b641
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071644"
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a>Nasıl yapılır: Bir Yordamın Birden Fazla Sürümünü Tanımlama (Visual Basic)

Aynı adı ancak her sürüm için farklı bir parametre listesini kullanarak, onu *aşırı* yükleyerek birden çok sürümde bir yordam tanımlayabilirsiniz. Aşırı yükleme amacı, bir yordamın adına göre ayrım yapmadan daha yakından ilgili birkaç sürümünü tanımlamaktır.  
  
 Daha fazla bilgi için bkz. [yordam aşırı yüklemesi](./procedure-overloading.md).  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a>Bir yordamın birden fazla sürümünü tanımlamak için  
  
1. Tanımlamak istediğiniz `Sub` `Function` yordamın her sürümü için bir veya bildirim bildirimi yazın. Her bildirimde aynı yordam adını kullanın.  
  
2. `Sub` `Function` Her bildirimdeki veya anahtar sözcüğünün önüne [aşırı yüklemeler](../../../language-reference/modifiers/overloads.md) anahtar sözcüğünü ekleyin. Bildirim içinde isteğe bağlı olarak atlayabilirsiniz `Overloads` , ancak bu bildirimi herhangi bir bildirime eklerseniz, her bildirime dahil etmeniz gerekir.  
  
3. Her bildirim ifadesinin ardından, çağıran kodun bu sürümün parametre listesiyle eşleşen bağımsız değişkenler sağladığı belirli bir durumu işlemek için yordam kodu yazın. Çağıran kodun sağladığı parametreleri test etmek zorunda değilsiniz. Visual Basic, denetimi prosedürünün eşleşen sürümüne geçirir.  
  
4. Yordamın her sürümünü, `End Sub` veya `End Function` ifadesiyle uygun şekilde sonlandırın.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, bir `Sub` müşterinin bakiyesine karşı bir işlem gönderme yordamını tanımlar. Bu `Overloads` anahtar sözcüğünü kullanarak müşteriyi adı ve diğer hesap numarasına göre kabul eden bir, yordamın iki sürümünü tanımlar.  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
 Çağıran kod, bir veya olarak müşteri kimliğini alabilir `String` `Integer` ve ardından aynı çağırma ifadesini her iki durumda da kullanabilir.  
  
 Yordamın bu sürümlerini çağırma hakkında daha fazla bilgi için `post` bkz. [nasıl yapılır: daha fazla yüklenmiş bir yordamı çağırma](./how-to-call-an-overloaded-procedure.md).  
  
## <a name="compile-the-code"></a>Kodu derle  

 Aşırı yüklenmiş sürümlerden her birinin aynı yordam adına, ancak farklı bir parametre listesine sahip olduğundan emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Yordam Sorunlarını Giderme](./troubleshooting-procedures.md)
- [Nasıl yapılır: İsteğe Bağlı Parametreler İsteyen Bir Yordamı Aşırı Yükleme](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Nasıl yapılır: Belirsiz Sayıda Parametre İsteyen Bir Yordamı Aşırı Yükleme](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Yordamları Aşırı Yüklemeye İlişkin Düşünceler](./considerations-in-overloading-procedures.md)
- [Aşırı yükleme çözümlemesi](./overload-resolution.md)
