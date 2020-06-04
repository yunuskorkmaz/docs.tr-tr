---
title: 'Nasıl yapılır: Aşırı Yüklenmiş Bir Yordamı Çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
ms.openlocfilehash: de101309fa1edaaddc3defc5759d9293fbef684c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388549"
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a>Nasıl yapılır: Aşırı Yüklenmiş Bir Yordamı Çağırma (Visual Basic)
Bir yordamı aşırı yükleme avantajı, çağrının esnekliğine sahiptir. Çağıran kod, yordama geçmesi için gereken bilgileri elde edebilir ve ardından tek bir yordam adı çağırarak, hangi bağımsız değişken geçirdiğine bakılmaksızın onu çağırabilir.  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a>Birden fazla sürümü tanımlanmış bir yordamı çağırmak için  
  
1. Çağıran kodda, yordama geçirilecek verileri saptayın.  
  
2. Yordam çağrısını, verileri bağımsız değişken listesinde sunarak normal şekilde yazın. Bağımsız değişkenlerin, yordam için tanımlanan sürümlerden birindeki parametre listesiyle eşleştiğinden emin olun.  
  
3. Hangi yordamın hangi sürüme çağrılacağını belirlemelisiniz. Visual Basic, denetimi bağımsız değişken listenizden eşleşen sürüme geçirir.  
  
     Aşağıdaki örnek, `post` [nasıl yapılır: bir yordamın birden fazla sürümünü tanımlama konusunda](./how-to-define-multiple-versions-of-a-procedure.md)belirtilen yordamı çağırır. Müşteri kimliğini edinir, bir veya bir olduğunu belirler `String` `Integer` ve her iki durumda da aynı yordamı çağırır.  
  
     [!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]  
  
     [!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Yordam Aşırı Yüklemesi](./procedure-overloading.md)
- [Yordam Sorunlarını Giderme](./troubleshooting-procedures.md)
- [Nasıl yapılır: Bir Yordamın Birden Fazla Sürümünü Tanımlama](./how-to-define-multiple-versions-of-a-procedure.md)
- [Nasıl yapılır: İsteğe Bağlı Parametreler İsteyen Bir Yordamı Aşırı Yükleme](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Nasıl yapılır: Belirsiz Sayıda Parametre İsteyen Bir Yordamı Aşırı Yükleme](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Yordamları Aşırı Yüklemeye İlişkin Düşünceler](./considerations-in-overloading-procedures.md)
- [Aşırı yükleme çözümlemesi](./overload-resolution.md)
- [Aşırı Yüklemeler](../../../language-reference/modifiers/overloads.md)
