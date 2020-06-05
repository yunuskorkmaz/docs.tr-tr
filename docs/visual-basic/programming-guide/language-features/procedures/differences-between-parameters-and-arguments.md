---
title: Parametreler ve Bağımsız Değişkenler Arasındaki Farklar
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
ms.openlocfilehash: dd0a62b6567f3e74763b7f2e9b96803c193c7976
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403362"
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a>Parametreler ve Bağımsız Değişkenler Arasındaki Farklar (Visual Basic)
Çoğu durumda, bir yordamın çağrıldığı koşullara ilişkin bazı bilgileri olması gerekir. Yinelenen veya paylaşılan görevler gerçekleştiren bir yordam, her çağrı için farklı bilgiler kullanır. Bu bilgiler, çağırdığınızda yordama geçirdiğiniz değişkenlerin, sabitlerin ve ifadelerden oluşur.  
  
 Bu bilgileri yordamla iletmek için, yordam bir *parametreyi*tanımlar ve çağıran kod bu parametreye bir *bağımsız değişken* geçirir. Parametresini bir park alanı ve bağımsız değişkeni olarak bir otomobil olarak düşünebilirsiniz. Farklı otomobil bir park alanını farklı zamanlarda park edebilir gibi, çağıran kod, yordamı her çağırdığında aynı parametreye farklı bir bağımsız değişken geçirebilir.  
  
## <a name="parameters"></a>Parametreler  
 Bir *parametre* , bu işlemi çağırdığınızda yordamın geçirilmesini beklediği bir değeri temsil eder. Yordamın bildirimi, parametrelerini tanımlar.  
  
 Bir `Function` veya `Sub` yordamı tanımladığınızda, yordam adından hemen sonra parantez içinde bir *parametre listesi* belirtirsiniz. Her parametre için bir ad, veri türü ve bir geçirme mekanizması ([ByVal](../../../language-reference/modifiers/byval.md) veya [ByRef](../../../language-reference/modifiers/byref.md)) belirtirsiniz. Ayrıca, bir parametresinin isteğe bağlı olduğunu belirtebilirsiniz. Bu, çağıran kodun bunun için bir değer geçmesi gerekmediği anlamına gelir.  
  
 Her parametrenin adı, yordamda *yerel bir değişken* işlevi görür. Parametre adını başka herhangi bir değişken kullandığınız şekilde kullanırsınız.  
  
## <a name="arguments"></a>Arguments  
 Bir *bağımsız değişken* , yordamı çağırdığınızda bir yordam parametresine geçirdiğiniz değeri temsil eder. Çağıran kod, yordamı çağırdığında bağımsız değişkenleri sağlar.  
  
 Bir `Function` veya `Sub` yordamını çağırdığınızda, yordam adının hemen ardından parantez içine bir *bağımsız değişken listesi* dahil edersiniz. Her bağımsız değişken, listedeki aynı konumdaki parametreye karşılık gelir.  
  
 Parametre tanımının aksine bağımsız değişkenlerin adları yoktur. Her bağımsız değişken sıfır veya daha fazla değişken, sabit ve değişmez değer içerebilen bir ifadedir. Değerlendirilen ifadenin veri türü genellikle karşılık gelen parametre için tanımlanan veri türüyle eşleşir ve herhangi bir durumda parametre türüne dönüştürülebilir olmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Alt Yordamlar](./sub-procedures.md)
- [İşlev Yordamları](./function-procedures.md)
- [Özellik Yordamları](./property-procedures.md)
- [İşleç Yordamları](./operator-procedures.md)
- [Nasıl yapılır: Bir Yordamın Parametresini Tanımlama](./how-to-define-a-parameter-for-a-procedure.md)
- [Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme](./how-to-pass-arguments-to-a-procedure.md)
- [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](./passing-arguments-by-value-and-by-reference.md)
- [Özyinelemeli Yordamlar](./recursive-procedures.md)
- [Yordam Aşırı Yüklemesi](./procedure-overloading.md)
