---
title: 'Nasıl yapılır: Belirsiz Sayıda Parametre İsteyen Bir Yordamı Aşırı Yükleme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], indefinite number of parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
ms.openlocfilehash: 026dd59db135e8b195ae014aaff5e3a6a7846fc7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651498"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a>Nasıl yapılır: Belirsiz Sayıda Parametre İsteyen Bir Yordamı Aşırı Yükleme (Visual Basic)
Bir yordam varsa bir [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametresi, tek boyutlu bir dizi parametre dizisi için ayırdığınız aşırı yüklenmiş bir sürümünü tanımlayamazsınız. Daha fazla bilgi için bkz: "Örtük aşırı yüklemeler için bir ParamArray parametre" [aşırı yükleme yordamları konuları](./considerations-in-overloading-procedures.md).  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a>Değişken sayıda parametre isteyen bir yordamı aşırı yükleme için  
  
1.  Yordam ve kod mantığı avantajları gelen çağırma sürümlerden birden fazla aşırı onaylaması bir `ParamArray` parametresi. "Aşırı ve ParamArrays" bölümüne bakın [yordamları aşırı yüklemeye ilişkin düşünceler](./considerations-in-overloading-procedures.md).  
  
2.  Sağlanan değerlerin hangi numaraları yordamı parametre listesi değişken bölümünde kabul etmelidir saptayın. Bu değer durumunun içerebilir ve tek tek boyutlu dizi durumunun içerebilir.  
  
3.  Sağlanan değerleri kabul edilebilir her sayısı için yazma bir `Sub` veya `Function` karşılık gelen parametre listesi tanımlar bildirimi deyimi. Ya da kullanmayın `Optional` veya `ParamArray` Bu aşırı yüklenmiş sürümünde anahtar sözcüğü.  
  
4.  Her bildiriminde önünde `Sub` veya `Function` anahtar sözcüğüyle [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) anahtar sözcüğü.  
  
5.  Her bildirim bildirim ait parametre listesine karşılık gelen değer çağıran kodu sağlıyor yükleyen yürütülecek yordamı kodu yazın.  
  
6.  Her bir yordam ile sonlandırmak `End Sub` veya `End Function` uygun şekilde deyimi.  
  
## <a name="example"></a>Örnek  
 İle tanımlanmış bir yordam aşağıdaki örnekte bir [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametre ve eşdeğer bir aşırı yüklenmiş yordamlar dizisi.  
  
 [!code-vb[VbVbcnProcedures#69](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#70](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_2.vb)]  
  
 Tek boyutlu bir dizi parametre dizisi için gereken bir parametre listesi ile bu tür bir yordamı aşırı yükleme yapılamıyor. Ancak, diğer örtük aşırı imzalarını kullanabilirsiniz. Aşağıdaki bildirimler bu gösterilmektedir.  
  
 [!code-vb[VbVbcnProcedures#71](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_3.vb)]  
  
 Çağrıyı yapan kod için bir veya daha fazla değer sağlanan olup olmadığını sınamak aşırı yüklü sürümlerini koddaki yok `ParamArray` parametresi veya ise, kaç tane. Visual Basic çağırma bağımsız değişken listesi eşleşen sürüm denetimi geçirir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Çünkü bir yordama bir `ParamArray` parametre kümesi aşırı yüklenmiş sürümleri için eşdeğer ve bu örtük aşırı yüklemeleri birine karşılık gelen bir parametre listesi ile bu tür bir yordamı tekrar yükleyemez. Daha fazla bilgi için bkz: [aşırı yükleme yordamları konuları](./considerations-in-overloading-procedures.md).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Süresiz olarak büyük olabilen bir dizi ile ilgilenir olduğunda, uygulamanızın iç bazı kapasite taşmasını riski yoktur. Bir parametre dizisi kabul ederseniz, çağrıyı yapan kod kendisine geçirilen dizi uzunluğu, test ve uygulamanız için çok büyük ise uygun adımları gerçekleştirin gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamlar](./index.md)  
 [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)  
 [İsteğe Bağlı Parametreler](./optional-parameters.md)  
 [Parametre Dizileri](./parameter-arrays.md)  
 [Yordam Aşırı Yüklemesi](./procedure-overloading.md)  
 [Yordam Sorunlarını Giderme](./troubleshooting-procedures.md)  
 [Nasıl yapılır: Bir Yordamın Birden Fazla Sürümünü Tanımlama](./how-to-define-multiple-versions-of-a-procedure.md)  
 [Nasıl yapılır: Aşırı Yüklenmiş Bir Yordamı Çağırma](./how-to-call-an-overloaded-procedure.md)  
 [Nasıl yapılır: İsteğe Bağlı Parametreler İsteyen Bir Yordamı Aşırı Yükleme](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [Aşırı Yükleme Çözümü](./overload-resolution.md)
