---
title: 'Nasıl yapılır: Bir Yordamın Birden Fazla Sürümünü Tanımlama (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
ms.openlocfilehash: a4d0c5bbb07dd5433ff62179fc10a6274bf19364
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649818"
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a>Nasıl yapılır: Bir Yordamın Birden Fazla Sürümünü Tanımlama (Visual Basic)
Birden çok sürümü tarafından bir yordam tanımlayabilirsiniz *aşırı yüklemesi* , aynı adlı ancak farklı parametre listesini her sürüm için kullanma. Aşırı yükleme amacı, ada göre ayırt zorunda kalmadan bir yordamın birden fazla yakından ilgili sürümünü tanımlamaktır.  
  
 Daha fazla bilgi için bkz: [yordam aşırı yüklemesi](./procedure-overloading.md).  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a>Bir yordamın birden fazla sürümünü tanımlamak için  
  
1.  Yazma bir `Sub` veya `Function` bildirimi deyimi tanımlamak istediğiniz yordamı her sürümü. Aynı yordamı adı her bildiriminde kullanın.  
  
2.  Öncesinde `Sub` veya `Function` anahtar sözcüğü ile her bildiriminde [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) anahtar sözcüğü. İsteğe bağlı olarak atlayabilirsiniz `Overloads` bildirimlerin hiçbirinde dahil, ancak bildirimlerden, her bildiriminde içermesi gerekir.  
  
3.  Her bildirim deyimi burada çağıran kodu bu sürüme ait parametre listesi eşleşen bağımsız değişken sağlayan özel durumu işlemek için bir yordam kod yazın. Test etmek için hangi parametreleri tarafından sağlanan çağıran kodu yok. Visual Basic denetim yordamınız eşleşen sürümüne geçirir.  
  
4.  Her bir sürümü yordamını sonlandırmak `End Sub` veya `End Function` uygun şekilde deyimi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek tanımlayan bir `Sub` Müşteri'nin Bakiye karşı bir işlem sonrası için yordamı. Kullandığı `Overloads` yordamın adı ve diğer müşteri hesap numarası tarafından kabul eden bir iki sürümünü tanımlamak üzere anahtar sözcük.  
  
 [!code-vb[VbVbcnProcedures#72](./codesnippet/VisualBasic/how-to-define-multiple-versions-of-a-procedure_1.vb)]  
  
 Çağrıyı yapan kod olarak ya da müşteri kimliği elde edebilirsiniz bir `String` veya bir `Integer`ve ardından her iki durumda da aynı arama deyimini kullanın.  
  
 Bu sürümleri çağrı hakkında bilgi için `post` yordamı, bkz: [nasıl yapılır: aşırı yüklenmiş bir yordamı çağırma](./how-to-call-an-overloaded-procedure.md).  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Aşırı yüklenmiş sürümlerinizi her farklı parametre listesi ancak aynı yordam adı olduğundan emin olun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamlar](./index.md)  
 [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)  
 [Yordam Sorunlarını Giderme](./troubleshooting-procedures.md)  
 [Nasıl yapılır: İsteğe Bağlı Parametreler İsteyen Bir Yordamı Aşırı Yükleme](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [Nasıl yapılır: Belirsiz Sayıda Parametre İsteyen Bir Yordamı Aşırı Yükleme](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [Yordamları Aşırı Yüklemeye İlişkin Düşünceler](./considerations-in-overloading-procedures.md)  
 [Aşırı Yükleme Çözümü](./overload-resolution.md)
