---
title: Aşırı Yükleme Çözümü (Visual Basic Başvurusu)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- overload resolution
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedure overloading [Visual Basic], overload resolution
- signatures [Visual Basic], procedure
- overloads [Visual Basic], resolution
ms.assetid: 766115d1-4352-45fb-859f-6063e0de0ec0
ms.openlocfilehash: c55b1c001ae1c74b0c34d716b9fa3f90dade3e28
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966235"
---
# <a name="overload-resolution-visual-basic"></a>Aşırı Yükleme Çözümü (Visual Basic Başvurusu)
Visual Basic Derleyicisi aşırı yüklenmiş sürümlerinde tanımlanan bir yordam çağrısı karşılaştığında derleyici çağırmak için aşırı yüklemeleri, karar vermeniz gerekir. Bunu aşağıdaki adımları uygulayarak yapar:  
  
1.  **Erişilebilirlik.** Bu, çağrıyı yapan kod bunu çağırma engelleyen erişim düzeyine sahip hiçbir aşırı yüklemeyle ortadan kaldırır.  
  
2.  **Parametre sayısı.** Bu, çağrıyı sağlanan daha farklı bir dizi parametre tanımlar hiçbir aşırı yüklemeyle ortadan kaldırır.  
  
3.  **Parametre veri türleri.** Derleyici, örnek yöntemler tercih üzerinde genişletme yöntemleri sağlar. Herhangi bir örnek yöntemi yalnızca yordam çağrısı eşleştirilecek dönüştürmeleri genişletme gerektiren bulunursa, tüm uzantı yöntemleri bırakılır ve derleyici yalnızca örnek yöntemi adayları ile devam eder. Bu tür bir örnek yöntem bulunursa, örneği ve genişletme yöntemleri ile devam eder.  
  
     Bu adımda, çağırma bağımsız değişkenlerinin veri türleri için aşırı yüklemesi'içinde tanımlanan parametre türleri olarak değiştirilemez hiçbir aşırı yüklemeyle ortadan kaldırır.  
  
4.  **Daraltma dönüştürmeleri.** Bu çağırma bağımsız değişken türleri için tanımlanan parametre türleri bir daraltma dönüşümü gerektirir hiçbir aşırı yüklemeyle ortadan kaldırır. Bu tür denetimi olup geçiş geçerlidir ([Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) olan `On` veya `Off`.  
  
5.  **En az genişletme.** Derleyici çiftler halinde kalan aşırı göz önünde bulundurur. Her bir çifti için tanımlanan parametrelerin veri türlerini karşılaştırır. Tüm aşırı yüklemeler türlerinde diğer karşılık gelen türlerine genişletmek, derleyici ikinci ortadan kaldırır. Diğer bir deyişle, en az genişletme miktarını gerektiren aşırı korur.  
  
6.  **Tek aday.** Aşırı yüklemeler tek kadar çiftler halinde aşırı kalır ve aşırı yükleyen çağrısı çözümler considering devam eder. Derleyici, tek bir aday için aşırı azaltılamaz, bir hata oluşturur.  
  
 Aşağıdaki çizimde, bir dizi çağırmak için aşırı yüklenmiş sürümleri belirleyen işlemi gösterilmektedir.  
  
 ![Aşırı yükleme çözünürlüğü işlemi Akış Diyagramı](./media/overloadres.gif "OverloadRes")  
Aşırı yüklenmiş sürümleri arasında çözümleme  
  
 Aşağıdaki örnekte, bu aşırı yükleme çözünürlüğü işlemi gösterilmektedir.  
  
 [!code-vb[VbVbcnProcedures#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbcnProcedures#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#63)]  
  
 İlk çağrıda nedeniyle derleyici ilk aşırı yükleme ortadan ilk bağımsız değişken türünü (`Short`) daraltır karşılık gelen parametre türüne (`Byte`). Çünkü ikinci aşırı yükleme her bağımsız değişken türü, daha sonra üçüncü aşırı yükleme ortadan kaldırır (`Short` ve `Single`) üçüncü aşırı yükleme türüne karşılık gelen widens (`Integer` ve `Single`). İsteğe bağlı olarak derleyici arama için kullanır, böylece daha az genişletme, ikinci aşırı yükleme gerektirir.  
  
 İkinci çağrıda, derleyici aşırı daraltma göndermemeniz hiçbirini ortadan olamaz. Daha az bir bağımsız değişken türlerini genişletme ile ikinci aşırı yükleme çağırabilirsiniz çünkü aynı nedenle, ilk çağrıda olduğu gibi üçüncü aşırı yükleme kaldırır. Ancak, derleyici ilk ve ikinci aşırı yükler arasında çözümlenemiyor. Her diğer karşılık gelen türe widens bir tanımlanan parametre türüne sahip (`Byte` için `Short`, ancak `Single` için `Double`). Derleyici, bu nedenle bir aşırı yükleme çözünürlüğü hata oluşturur.  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a>İsteğe bağlı olarak aşırı yüklendi ve ParamArray bağımsız değişkenleri  
 Son parametre bildirilen dışında aynı imzaya bir yordamın iki aşırı yükleme varsa [isteğe bağlı](../../../../visual-basic/language-reference/modifiers/optional.md) birinde ve [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) diğerinde derleyici bir çağrı bu yordamı çözümler aşağıdaki gibidir:  
  
|Son bağımsız değişken olarak çağrı yaparsa|Son bağımsız değişken olarak bildirme aşırı yükleme çağrısı derleyici çözümler|  
|---|---|  
|Herhangi bir değer (atlanmış bağımsız değişkeni)|`Optional`|  
|Tek bir değer|`Optional`|  
|İki veya daha fazla virgülle ayrılmış bir liste değerleri|`ParamArray`|  
|(Boş bir dizi dahil) herhangi bir uzunlukta bir dizi|`ParamArray`|  
  
## <a name="see-also"></a>Ayrıca bkz.
- [İsteğe Bağlı Parametreler](./optional-parameters.md)
- [Parametre Dizileri](./parameter-arrays.md)
- [Yordam Aşırı Yüklemesi](./procedure-overloading.md)
- [Yordam Sorunlarını Giderme](./troubleshooting-procedures.md)
- [Nasıl yapılır: Bir yordamın birden fazla sürümünü tanımlama](./how-to-define-multiple-versions-of-a-procedure.md)
- [Nasıl yapılır: Aşırı yüklenmiş bir yordamı çağırma](./how-to-call-an-overloaded-procedure.md)
- [Nasıl yapılır: İsteğe bağlı parametreler isteyen bir yordamı aşırı yükleme](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Nasıl yapılır: Belirsiz sayıda parametre isteyen bir yordamı aşırı yükleme](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Yordamları Aşırı Yüklemeye İlişkin Düşünceler](./considerations-in-overloading-procedures.md)
- [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [Genişletme Yöntemleri](./extension-methods.md)
