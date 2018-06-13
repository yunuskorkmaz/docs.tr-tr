---
title: Parametreler ve Bağımsız Değişkenler Arasındaki Farklar (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- parameters [Visual Basic], and arguments
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], and parameters
- procedure parameters
- parameters [Visual Basic], definition
ms.assetid: c237c056-74f4-4749-9f2c-15864f139a31
ms.openlocfilehash: a5075c218371b754ac883b97475ab941811966b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650692"
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a>Parametreler ve Bağımsız Değişkenler Arasındaki Farklar (Visual Basic)
Çoğu durumda, bir yordam, onu çağrıldı koşullar hakkında bazı bilgileri olması gerekir. Yinelenen veya paylaşılan görevleri gerçekleştiren bir yordam her çağrı için farklı bilgileri kullanır. Bu bilgiler değişkenlerinin, sabitleri ve onu çağırdığınızda, yordama geçirdiğiniz ifadeler oluşur.  
  
 Bu bilgileri yordam için iletişim kurmak için yordamı tanımlayan bir *parametresi*, ve çağrıyı yapan kod geçirir bir *bağımsız değişkeni* parametreye. Park alanı parametre ve bağımsız değişken bir otomobil olarak düşünebilirsiniz. Yalnızca farklı otomobiller bir park alanında farklı zamanlarda park olarak çağıran kodu, BT'nin yordam çağrıları her zaman aynı parametresi için farklı bir bağımsız değişken geçirebilirsiniz.  
  
## <a name="parameters"></a>Parametreler  
 A *parametresi* yordamı, çağırdığınızda geçirmeniz bekliyor bir değeri temsil eder. Yordam bildirimi parametrelerini tanımlar.  
  
 Tanımladığınızda bir `Function` veya `Sub` yordamı, belirttiğiniz bir *parametre listesi* yordam adı hemen ardından parantez içinde. Her parametre için bir ad, bir veri türü ve geçirme mekanizması belirtin ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) veya [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)). Ayrıca, bir parametrenin isteğe bağlı olduğunu gösterebilir. Bu, çağrıyı yapan kod için bir değer geçirmek yok anlamına gelir.  
  
 Her parametre adı görevi gören bir *yerel değişken* yordamda. Parametre adı başka bir değişken aynı şekilde kullanın.  
  
## <a name="arguments"></a>Arguments  
 Bir *bağımsız değişkeni* yordam çağrısı yükleyen bir yordam parametresini geçirdiğiniz değerini temsil eder. Yordam çağrıları, çağrıyı yapan kod bağımsız değişkenler sağlar.  
  
 Çağırdığınızda bir `Function` veya `Sub` yordamı, eklediğiniz bir *bağımsız değişken listesi* yordam adı hemen ardından parantez içinde. Her değişken parametre aynı konumda yer alan listesindeki karşılık gelir.  
  
 Parametre tanımına aksine, bağımsız değişken adları yok. Her bir bağımsız değişkeni sıfır veya daha fazla değişkenlerinin, sabitleri ve değişmez değerleri içeren bir ifade değil. Değerlendirilmiş ifadeyi veri türüne karşılık gelen bir parametre için tanımlanan veri türü genellikle eşleşmelidir ve her durumda parametre türüne dönüştürülebilir olmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamlar](./index.md)  
 [Alt Yordamlar](./sub-procedures.md)  
 [İşlev Yordamları](./function-procedures.md)  
 [Özellik Yordamları](./property-procedures.md)  
 [İşleç Yordamları](./operator-procedures.md)  
 [Nasıl yapılır: Bir Yordamın Parametresini Tanımlama](./how-to-define-a-parameter-for-a-procedure.md)  
 [Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme](./how-to-pass-arguments-to-a-procedure.md)  
 [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](./passing-arguments-by-value-and-by-reference.md)  
 [Özyinelemeli Yordamlar](./recursive-procedures.md)  
 [Yordam Aşırı Yüklemesi](./procedure-overloading.md)
