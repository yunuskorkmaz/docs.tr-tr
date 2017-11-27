---
title: "Parametreler ve Bağımsız Değişkenler Arasındaki Farklar (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b6613c64a24ef18239422b69f8b5320eadc95b92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Yordamları](./index.md)  
 [Alt yordamlar](./sub-procedures.md)  
 [İşlev yordamları](./function-procedures.md)  
 [Özellik yordamları](./property-procedures.md)  
 [İşleç yordamları](./operator-procedures.md)  
 [Nasıl yapılır: bir yordamın parametresini tanımlama](./how-to-define-a-parameter-for-a-procedure.md)  
 [Nasıl yapılır: bir yordama bağımsız değişkenler geçirme](./how-to-pass-arguments-to-a-procedure.md)  
 [Bağımsız değişkenleri değere ve başvuruya göre geçirme](./passing-arguments-by-value-and-by-reference.md)  
 [Özyinelemeli yordamlar](./recursive-procedures.md)  
 [Yordam aşırı yüklemesi](./procedure-overloading.md)
