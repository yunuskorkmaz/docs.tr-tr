---
title: Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- passing arguments [Visual Basic], by value or by reference
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
- argument passing [Visual Basic], by value or by reference
ms.assetid: fd8a9de6-7178-44d5-a9bf-458d4ad907c2
ms.openlocfilehash: c2c778afea90a90b2b5f83300c2d174db39f3c15
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978481"
---
# <a name="passing-arguments-by-value-and-by-reference-visual-basic"></a>Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme (Visual Basic)
Visual Basic'te bir yordama bağımsız değişken geçirebilirsiniz *değeriyle* veya *başvuruya göre*. Bu olarak bilinir *mekanizması geçirme*, yordamı çağıran koddaki bağımsız temel programlama öğesine değiştirip değiştiremeyeceğini belirler. Yordam bildirimi belirterek her parametre geçirme mekanizması belirler [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) veya [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) anahtar sözcüğü.  
  
## <a name="distinctions"></a>Farklılıklar  
 Bağımsız değişken bir yordama geçirilirken birbiriyle etkileşim birkaç farklı farklılıklar dikkat:  
  
-   Temel programlama öğesine değiştirilebilir veya değiştirilemez olup  
  
-   Bağımsız değişkenin kendisine değiştirilebilir veya değiştirilemez olup  
  
-   Değere göre geçirilen bağımsız değişken olup olmadığını ya da başvuru  
  
-   Bağımsız değişken veri türü bir değer türü veya bir başvuru türü olup  
  
 Daha fazla bilgi için [arasındaki farklar değiştirilebilir ve değiştirilemez bağımsız değişkenler](./differences-between-modifiable-and-nonmodifiable-arguments.md) ve [farklar arasında geçen bir bağımsız değişken değer ve başvuru tarafından](./differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
## <a name="choice-of-passing-mechanism"></a>Seçim mekanizması geçirme  
 Her bağımsız değişkeni için dikkatli bir şekilde geçirme mekanizması seçmeniz gerekir.  
  
-   **Koruma**. Arasında iki geçirme mekanizması seçme içinde en önemli değiştirmek için değişkenleri çağırma açığa ölçüttür. Bağımsız değişken geçirme avantajı `ByRef` yordamı bir değer bu bağımsız değişkeni aracılığıyla çağıran koda geri dönebilirsiniz. Bağımsız değişken geçirme avantajı `ByVal` olduğundan, bir değişken yordamı tarafından değiştirilen korur.  
  
-   **Performans**. Geçirme mekanizması kodunuzun performansını etkileyebilir olsa da, genellikle anlamsız bir farktır. Bunun tek istisnası, geçirilen bir değer türüdür `ByVal`. Bu durumda, Visual Basic bağımsız değişkeni, tüm veri içeriğini kopyalar. Bu nedenle, bir yapı gibi büyük bir değer türü için onu geçirilmesinin daha etkili olabilir `ByRef`.  
  
     Başvuru türleri için yalnızca veri kopyalanan (dört bayt 32-bit platformlarda 64-bit platformlarda sekiz bayt) işaretçisidir. Bu nedenle, türünde bağımsız değişkenler geçirebilirsiniz `String` veya `Object` performans zarar olmadan değere göre.  
  
## <a name="determination-of-the-passing-mechanism"></a>Geçirme mekanizması olarak belirleme  
 Yordam bildirimi her parametre geçirme mekanizması belirtir. Çağıran kod geçersiz kılamaz bir `ByVal` mekanizması.  
  
 Bir parametre ile bildirilirse `ByRef`, çağıran kodun mekanizmasına zorlayabilirsiniz `ByVal` parantez içinde çağrısında bağımsız değişken adını kapsayan tarafından. Daha fazla bilgi için [nasıl yapılır: Bağımsız değişkeni değere göre geçirilecek şekilde zorlama](./how-to-force-an-argument-to-be-passed-by-value.md).  
  
 Visual Basic'te bağımsız değişkenleri değere göre geçirilecek varsayılandır.  
  
## <a name="when-to-pass-an-argument-by-value"></a>Ne zaman bir bağımsız değişken değere göre geçirin.  
  
-   Bağımsız değişken arka plandaki çağıran kod öğesi değiştirilemez bir öğeyse, karşılık gelen parametre bildirmek [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). Kod, değiştirilemez öğenin değerini değiştirebilirsiniz.  
  
-   Temel alınan öğe değiştirilebilir, ancak değeri değiştirebilmesi için yordamı istemiyorsanız, parametre bildirmek `ByVal`. Yalnızca çağıran kod, değer olarak geçilemez değiştirilebilir bir öğenin değerini değiştirebilirsiniz.  
  
## <a name="when-to-pass-an-argument-by-reference"></a>Ne zaman başvuruya göre bağımsız değişken geçirin  
  
-   Yordamı çağıran koddaki temel alınan öğeyi değiştirmek için orijinal gereksinimi varsa, karşılık gelen parametre bildirmek [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).  
  
-   Temel alınan öğeyi çağıran koddaki yordamı doğru kod yürütmeyi bağlıdır, parametre bildirmek `ByRef`. Değere göre geçirirseniz veya çağırma kodunun kılıyorsa `ByRef` mekanizması bağımsız değişken parantez içine alarak geçirme yordam çağrısı beklenmeyen sonuçlara neden.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, bağımsız değişkenleri değere göre geçirilecek zaman ve ne zaman geçirileceğini başvuruya göre gösterir. Yordam `Calculate` hem de bir `ByVal` ve `ByRef` parametresi. Faiz oranını verilen `rate`ve para ödülleriyle toplamını `debt`, yordamın için yeni bir değer hesaplamak için görevdir `debt` faiz oranını özgün değeri olarak diğer bir deyişle sonucu `debt`. Çünkü `debt` olduğu bir `ByRef` parametresini yeni toplam karşılık gelen çağıran koddaki bağımsız değişkenin değeri yansıtılır `debt`. Parametre `rate` olduğu bir `ByVal` parametresi çünkü `Calculate` değerini değiştirmemesi gerekir.  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbcnProcedures#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class2.vb#74)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Yordamlar](./index.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Nasıl yapılır: Bir yordama bağımsız değişkenler geçirme](./how-to-pass-arguments-to-a-procedure.md)
- [Nasıl yapılır: Bir yordam bağımsız değişkeninin değerini değiştirme](./how-to-change-the-value-of-a-procedure-argument.md)
- [Nasıl yapılır: Bir yordam bağımsız değişkenini değer değişikliklerine karşı koruma](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Nasıl yapılır: Bağımsız değişkeni değere göre geçirilecek şekilde zorlama](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme](./passing-arguments-by-position-and-by-name.md)
- [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
