---
title: "Aşırı Yükleme Çözümü (Visual Basic Başvurusu)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- overload resolution
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedure overloading [Visual Basic], overload resolution
- signatures [Visual Basic], procedure
- overloads [Visual Basic], resolution
ms.assetid: 766115d1-4352-45fb-859f-6063e0de0ec0
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7eb71b69496e27b664fe297e9e5f105b360ce01d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="overload-resolution-visual-basic"></a>Aşırı Yükleme Çözümü (Visual Basic Başvurusu)
Zaman [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] derleyici birden fazla aşırı yüklenmiş sürümlerde tanımlı bir yordam çağrısına karşılaştığında, derleyici, çağırmak için aşırı karar vermeniz gerekir. Bunu aşağıdaki adımları gerçekleştirerek yapar:  
  
1.  **Erişilebilirlik.** Bu, çağrıyı yapan kod çağırma sonucu engelleyen bir erişim düzeyi ile hiçbir aşırı ortadan kaldırır.  
  
2.  **Parametre sayısı.** Bu, farklı sayıda parametreleri çağrısında sağlanan daha tanımlar hiçbir aşırı ortadan kaldırır.  
  
3.  **Parametre veri türleri.** Derleyici örneği yöntemleri tercih genişletme yöntemleri sağlar. Herhangi bir örnek yöntemi yalnızca yordam çağrısı eşleşecek şekilde dönüşümleri gerektiren bulunursa, tüm genişletme yöntemleri bırakılan ve derleyici yalnızca örnek yöntem aday ile devam eder. Bu tür bir örnek yöntemi bulunursa, örneği ve genişletme yöntemleri ile devam eder.  
  
     Bu adımda, kendisi için arama bağımsız değişkenlerinin veri türlerini aşırı tanımlanan parametre türleri dönüştürülemez hiçbir aşırı ortadan kaldırır.  
  
4.  **Daraltma dönüşümleri.** Bu arama bağımsız değişken türleri daraltma dönüştürme tanımlanan parametre türleri için gerektiren hiçbir aşırı ortadan kaldırır. Bu tür denetlemesi olup geçiş geçerlidir ([Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) olan `On` veya `Off`.  
  
5.  **En az genişletme.** Derleyici çiftleri içinde kalan aşırı göz önünde bulundurur. Her çifti için tanımlanan parametrelerin veri türlerini karşılaştırır. Karşılık gelen türlerine diğer tüm aşırı türlerinde genişletmek, derleyici ikinci ortadan kaldırır. Diğer bir deyişle, en az genişletme miktarını gerektirir aşırı korur.  
  
6.  **Tek adayı.** Aşırı çiftler halinde tek kadar kalır aşırı yükleme ve bu aşırı çağrısı çözümler considering devam eder. Derleyici tek bir aday için aşırı indiremezsiniz bir hata oluşturur.  
  
 Aşağıdaki çizimde çağırmak için aşırı yüklü sürümlerini kümesinin belirleyen işlemi gösterilmektedir.  
  
 ![Aşırı çözümleme işlemi Akış Diyagramı](./media/overloadres.gif "OverloadRes")  
Aşırı yüklenmiş sürümleri arasında çözme  
  
 Aşağıdaki örnek, bu aşırı çözümleme işlemi gösterilmektedir.  
  
 [!code-vb[VbVbcnProcedures#62](./codesnippet/VisualBasic/overload-resolution_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#63](./codesnippet/VisualBasic/overload-resolution_2.vb)]  
  
 İlk çağrıda derleyici ilk aşırı çünkü ortadan kaldıran ilk bağımsız değişken türü (`Short`) daraltır karşılık gelen parametrenin türünü (`Byte`). Tür bağımsız değişkeni, her olduğundan ikinci aşırı sonra üçüncü aşırı ortadan (`Short` ve `Single`) üçüncü aşırı içinde karşılık gelen türüne widens (`Integer` ve `Single`). Böylece isteğe bağlı olarak derleyici çağrısı kullanır ikinci aşırı daha az genişletme gerektirir.  
  
 İkinci çağrıda derleyici daraltma temel alarak aşırı hiçbirini ortadan olamaz. Daha az bağımsız değişken türleri genişletme ile ikinci aşırı çağırabilirsiniz olduğundan, üçüncü aşırı ilk çağrıda olduğu gibi aynı nedenden dolayı ortadan kaldırır. Ancak, derleyici arasında birinci ve ikinci aşırı yüklemeleri çözümlenemiyor. Her karşılık gelen türü diğer widens bir tanımlanan parametre türüne sahip (`Byte` için `Short`, ancak `Single` için `Double`). Derleyici, bu nedenle bir aşırı yüklemesini çözümleme hatası oluşturur.  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a>İsteğe bağlı aşırı ve ParamArray bağımsız değişkenleri  
 Bir yordamın iki aşırı son parametre bildirilmiş dışında aynı imzaları varsa [isteğe bağlı](../../../../visual-basic/language-reference/modifiers/optional.md) birinde ve [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) diğer, bu yordamı yapılan bir çağrı derleyici çözümler aşağıdaki gibidir:  
  
|Çağrı son bağımsız değişken olarak sağlarsa|Son bağımsız değişken olarak bildirme aşırı çağrısı derleyici çözümler|  
|---|---|  
|Herhangi bir değer (atlanmış bağımsız değişkeni)|`Optional`|  
|tek bir değer|`Optional`|  
|Virgülle ayrılmış bir liste iki veya daha fazla değer|`ParamArray`|  
|(Boş bir dizi dahil) herhangi bir uzunlukta bir dizi|`ParamArray`|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İsteğe bağlı parametreler](./optional-parameters.md)  
 [Parametre dizileri](./parameter-arrays.md)  
 [Yordam aşırı yüklemesi](./procedure-overloading.md)  
 [Sorun giderme yordamları](./troubleshooting-procedures.md)  
 [Nasıl yapılır: bir yordamın birden fazla sürümünü tanımlama](./how-to-define-multiple-versions-of-a-procedure.md)  
 [Nasıl yapılır: aşırı yüklenmiş bir yordamı çağırma](./how-to-call-an-overloaded-procedure.md)  
 [Nasıl yapılır: isteğe bağlı parametreler isteyen bir yordamı aşırı yükleme](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [Nasıl yapılır: belirsiz sayıda parametre isteyen bir yordamı aşırı yükleme](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [Yordamları aşırı yüklemeye ilişkin düşünceler](./considerations-in-overloading-procedures.md)  
 [Aşırı yüklemeler](../../../../visual-basic/language-reference/modifiers/overloads.md)  
 [Genişletme yöntemleri](./extension-methods.md)
