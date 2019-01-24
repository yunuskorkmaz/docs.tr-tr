---
title: 'Nasıl yapılır: Bir yordam (Visual Basic) birden fazla sürümünü tanımlama'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
ms.openlocfilehash: a3f4657b22fe0a9186e339d00cd9341e55405244
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528881"
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a>Nasıl yapılır: Bir yordam (Visual Basic) birden fazla sürümünü tanımlama
Bir yordam tarafından birden çok sürümü tanımlayabilirsiniz *aşırı yükleme* , her sürüm için aynı ada ancak farklı parametre listesini kullanarak. Aşırı yükleme amacı, ada göre ayırmak zorunda kalmadan bir yordamın birden fazla yakından ilgili sürümünü tanımlamaktır.  
  
 Daha fazla bilgi için [yordam aşırı yüklemesi](./procedure-overloading.md).  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a>Bir yordamın birden fazla sürümünü tanımlama  
  
1.  Yazma bir `Sub` veya `Function` bildirim deyimindeki tanımlamak istediğiniz yordamı her sürümü için. Her bildiriminde aynı yordam adı kullanın.  
  
2.  Önünde `Sub` veya `Function` anahtar sözcüğü ile her bildirimindeki [aşırı](../../../../visual-basic/language-reference/modifiers/overloads.md) anahtar sözcüğü. İsteğe bağlı olarak atlayabilirsiniz `Overloads` bildirimleri hiçbirinde dahil, ancak bildirimlerinde, her bildiriminde eklemeniz gerekir.  
  
3.  Her bildirim deyimindeki burada çağıran kod söz konusu sürüme ait parametre listesi ile eşleşen bağımsız değişkenleri sağlayan özel durumu işlemek için yordamı kod yazın. Test etmek hangi parametrelerini çağıran kod tarafından sağlanan yok. Visual Basic için yordamı'nın eşleşen sürümünün denetim geçer.  
  
4.  Yordamı her bir sürümü sonlandırmak `End Sub` veya `End Function` uygun şekilde deyimi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte tanımlayan bir `Sub` Müşteri'nin Dengeleme karşı bir işlem göndermeniz için yordamı. Kullandığı `Overloads` iki yordamı müşterinin adı ve diğer hesap numarası tarafından kabul eden bir sürümünü tanımlamak için anahtar sözcüğü.  
  
 [!code-vb[VbVbcnProcedures#72](./codesnippet/VisualBasic/how-to-define-multiple-versions-of-a-procedure_1.vb)]  
  
 Çağıran kod olarak ya da Müşteri Kimliği edinebilirsiniz bir `String` veya `Integer`ve sonra her iki durumda da aynı çağıran deyimini kullanın.  
  
 Bu sürümleri çağırma hakkında bilgi için `post` yordamı bkz [nasıl yapılır: Aşırı yüklenmiş bir yordamı çağırma](./how-to-call-an-overloaded-procedure.md).  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Her aşırı yüklü sürümü farklı parametre listesi ancak aynı yordam adı olduğundan emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Yordamlar](./index.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Yordam Sorunlarını Giderme](./troubleshooting-procedures.md)
- [Nasıl yapılır: İsteğe bağlı parametreler isteyen bir yordamı aşırı yükleme](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Nasıl yapılır: Belirsiz sayıda parametre isteyen bir yordamı aşırı yükleme](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Yordamları Aşırı Yüklemeye İlişkin Düşünceler](./considerations-in-overloading-procedures.md)
- [Aşırı Yükleme Çözümü](./overload-resolution.md)
