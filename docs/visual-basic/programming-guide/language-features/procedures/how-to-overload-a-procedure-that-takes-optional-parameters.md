---
title: 'Nasıl yapılır: İsteğe Bağlı Parametreler İsteyen Bir Yordamı Aşırı Yükleme'
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
ms.openlocfilehash: 78ca6b2b95dfd5a7f208e5251f08dfccc5514946
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071527"
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a>Nasıl yapılır: İsteğe Bağlı Parametreler İsteyen Bir Yordamı Aşırı Yükleme (Visual Basic)

Bir yordamda bir veya daha fazla [Isteğe bağlı](../../../language-reference/modifiers/optional.md) parametre varsa, örtük aşırı yüklemelerinin hiçbiriyle eşleşen aşırı yüklenmiş bir sürüm tanımlayamazsınız. Daha fazla bilgi için bkz. Opsiyonel [yükleme yordamlarına göz](./considerations-in-overloading-procedures.md)atın.  
  
## <a name="one-optional-parameter"></a>Bir Isteğe bağlı parametre  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a>İsteğe bağlı bir parametre alan bir yordamı aşırı yüklemek için  
  
1. `Sub` `Function` Parametre listesinde isteğe bağlı parametreyi içeren bir veya bildirim bildirimi yazın. `Optional`Bu aşırı yüklenmiş sürümde anahtar sözcüğünü kullanmayın.  
  
2. `Sub` `Function` [Aşırı yüklemeler](../../../language-reference/modifiers/overloads.md) anahtar sözcüğüyle veya anahtar kelimeden önce.  
  
3. Çağıran kod isteğe bağlı bağımsız değişkeni sağladığı zaman yürütülmesi gereken yordam kodunu yazın.  
  
4. Yordamı `End Sub` veya `End Function` ifadesiyle uygun şekilde sonlandırın.  
  
5. Parametre listesinde isteğe bağlı parametreyi içermediği hariç birinci bildirimle özdeş ikinci bir bildirim bildirimi yazın.  
  
6. Çağıran kod isteğe bağlı bağımsız değişkeni sağlamadığınızda yürütülmesi gereken yordam kodunu yazın. Yordamı `End Sub` veya `End Function` ifadesiyle uygun şekilde sonlandırın.  
  
     Aşağıdaki örnek, isteğe bağlı bir parametre ile tanımlanan, iki aşırı yüklenmiş yordamın eşdeğer bir kümesini ve son olarak hem geçersiz hem de geçerli aşırı yüklenmiş sürümlerin örneklerini gösterir.  
  
     [!code-vb[VbVbcnProcedures#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#59)]  
  
     [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
     [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
## <a name="multiple-optional-parameters"></a>Birden çok Isteğe bağlı parametre  

 Birden fazla isteğe bağlı parametreye sahip bir yordam için normalde ikiden fazla aşırı yüklenmiş sürüm gerekir. Örneğin, isteğe bağlı iki parametre varsa ve çağıran kod, birbirinden bağımsız olarak her birini belirtebilir veya atlayabilir, sağlanan bağımsız değişkenlerin her bir birleşimi için bir tane olmak üzere dört aşırı yüklü sürüme ihtiyacınız vardır.  
  
 İsteğe bağlı parametrelerin sayısı arttıkça aşırı yüklemenin karmaşıklığı artar. Sağlanan bağımsız değişkenlerin bazı birleşimleri kabul edilemez değilse, N isteğe bağlı parametre için 2 ^ N aşırı yüklenmiş sürüme ihtiyacınız vardır. Yordamın doğasına bağlı olarak, tüm aşırı yüklenmiş sürümlerin tanımlanmasıyla ilgili ekstra çabaların açıklık netliği olduğunu fark edebilirsiniz.  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a>Birden fazla isteğe bağlı parametre alan bir yordamı aşırı yüklemek için  
  
1. Sağlanan isteğe bağlı bağımsız değişkenlerin hangi birleşimlerinin yordamın mantığı için kabul edilebilir olduğunu belirleme. İsteğe bağlı bir parametre diğerine bağımlıysa, kabul edilemez bir bileşim meydana gelebilir. Örneğin, bir parametre kişinin adını kabul ediyorsa ve başka birinin yaşını kabul ediyorsa, yaşı sağlayan bağımsız değişkenlerin bir birleşimi ve adı yok edilemez.  
  
2. Sağlanan isteğe bağlı bağımsız değişkenlerin her bir kabul edilebilir kombinasyonu için `Sub` , `Function` karşılık gelen parametre listesini tanımlayan bir veya bildirim bildirimi yazın. `Optional`Anahtar sözcüğünü kullanmayın.  
  
3. Her bildirimde, `Sub` veya `Function` anahtar sözcüğünün önüne [aşırı yüklemeler](../../../language-reference/modifiers/overloads.md) anahtar sözcüğünü ekleyin.  
  
4. Her bildirime göre, çağıran kod bu bildirimin parametre listesine karşılık gelen bir bağımsız değişken listesi sağladığı zaman yürütülmesi gereken yordam kodunu yazın.  
  
5. Her yordamı `End Sub` veya `End Function` ifadesiyle uygun şekilde sonlandırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [İsteğe Bağlı Parametreler](./optional-parameters.md)
- [Parametre Dizileri](./parameter-arrays.md)
- [Yordam Aşırı Yüklemesi](./procedure-overloading.md)
- [Yordam Sorunlarını Giderme](./troubleshooting-procedures.md)
- [Nasıl yapılır: Bir Yordamın Birden Fazla Sürümünü Tanımlama](./how-to-define-multiple-versions-of-a-procedure.md)
- [Nasıl yapılır: Aşırı Yüklenmiş Bir Yordamı Çağırma](./how-to-call-an-overloaded-procedure.md)
- [Nasıl yapılır: Belirsiz Sayıda Parametre İsteyen Bir Yordamı Aşırı Yükleme](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Aşırı yükleme çözümlemesi](./overload-resolution.md)
