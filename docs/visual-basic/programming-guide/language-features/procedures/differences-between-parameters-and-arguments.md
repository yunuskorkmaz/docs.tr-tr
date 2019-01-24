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
ms.openlocfilehash: ec7c92975bc056fd740033b602b15cd1611c44d1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694041"
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a>Parametreler ve Bağımsız Değişkenler Arasındaki Farklar (Visual Basic)
Çoğu durumda, bir yordam içinde bunu çağrıldıktan koşullar hakkında bazı bilgiler olması gerekir. Yinelenen veya paylaşılan görevleri gerçekleştiren bir yordam her çağrı için farklı bilgileri kullanır. Bu bilgiler, değişkenleri, sabitleri ve onu çağırdığınızda yordama geçirdiğiniz ifadeleri oluşur.  
  
 Bu yordamı bilgiler iletmek için yordamı tanımlar. bir *parametre*, ve çağıran kod geçirir bir *bağımsız değişken* parametreye. Parametre olarak park boşluk ve bağımsız değişken bir otomobilin olarak düşünebilirsiniz. Yalnızca farklı otomobil park boşluk farklı zamanlarda park gibi çağıran kodun BT'nin yordam çağrıları her zaman aynı parametresi için farklı bir bağımsız değişken geçirebilirsiniz.  
  
## <a name="parameters"></a>Parametreler  
 A *parametre* yordamı çağırdığınızda, geçirmeniz bekliyor. bir değeri temsil eder. Yordam bildirimi parametrelerini tanımlar.  
  
 Tanımladığınızda bir `Function` veya `Sub` yordamı, belirttiğiniz bir *parametre listesi* yordam adına hemen arkasından parantez içinde. Her parametre için bir ad, bir veri türü ve geçirme mekanizma belirtin ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) veya [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)). Ayrıca, bir parametrenin isteğe bağlı olduğunu gösterebilir. Başka bir deyişle, çağırma kodunun kendisi için bir değer geçirmek yok.  
  
 Her parametre adı olarak hizmet veren bir *yerel değişken* yordamda. Parametre adı herhangi bir değişken aynı şekilde kullanırsınız.  
  
## <a name="arguments"></a>Arguments  
 Bir *bağımsız değişken* yordamı çağırdığınızda bir yordam parametresi için geçirdiğiniz değer temsil eder. Yordamı çağırdığında, çağıran kodun bağımsız değişkenleri sağlar.  
  
 Çağırdığınızda bir `Function` veya `Sub` yordamı, eklediğiniz bir *bağımsız değişken listesi* yordam adına hemen arkasından parantez içinde. Her bağımsız değişken listesinde aynı konumda parametresine karşılık gelir.  
  
 Parametre tanımında aksine, bağımsız değişken adları yok. Her bağımsız değişkeni sıfır veya daha fazla değişkenler, sabitler ve sabit değerleri içeren bir ifade ' dir. Değerlendirilmiş ifadeyi veri türüne karşılık gelen parametre için tanımlanan veri türü genellikle eşleşmesi gerekir ve her durumda parametre türüne dönüştürülebilir olmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Yordamlar](./index.md)
- [Alt Yordamlar](./sub-procedures.md)
- [İşlev Yordamları](./function-procedures.md)
- [Özellik Yordamları](./property-procedures.md)
- [İşleç Yordamları](./operator-procedures.md)
- [Nasıl yapılır: Bir yordamın parametresini tanımlama](./how-to-define-a-parameter-for-a-procedure.md)
- [Nasıl yapılır: Bir yordama bağımsız değişkenler geçirme](./how-to-pass-arguments-to-a-procedure.md)
- [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](./passing-arguments-by-value-and-by-reference.md)
- [Özyinelemeli Yordamlar](./recursive-procedures.md)
- [Yordam Aşırı Yüklemesi](./procedure-overloading.md)
