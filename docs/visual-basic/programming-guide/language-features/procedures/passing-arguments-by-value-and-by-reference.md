---
title: "Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- passing arguments [Visual Basic], by value or by reference
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
- argument passing [Visual Basic], by value or by reference
ms.assetid: fd8a9de6-7178-44d5-a9bf-458d4ad907c2
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 752c0c8e90cafe457cbd5d684bc984a1ea4632ac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="passing-arguments-by-value-and-by-reference-visual-basic"></a>Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme (Visual Basic)
İçinde [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], bir yordama bağımsız değişken geçirebilirsiniz *değeriyle* veya *başvuruya göre*. Bu olarak bilinir *mekanizması geçirme*, yordamı çağıran kodu değişkeninde temel programlama öğesi değişiklik olup olmadığını belirler. Yordam bildirimi belirterek her parametre için geçirme mekanizması belirler [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) veya [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) anahtar sözcüğü.  
  
## <a name="distinctions"></a>Farklılıklar  
 Bağımsız değişken bir yordama geçirilirken birbiriyle etkileşimde birkaç farklı farklılıklar farkında olması:  
  
-   Temel programlama öğesi değiştirilebilir veya değiştirilemez olup  
  
-   Bağımsız değişkenin kendisine değiştirilebilir veya değiştirilemez olup  
  
-   Bağımsız değişken değeri tarafından geçirilen olup olmadığını ya da başvuru  
  
-   Bağımsız değişken veri türü bir değer türü veya bir başvuru türü olup  
  
 Daha fazla bilgi için bkz: [arasındaki farklar değiştirilebilir ve değiştirilemez bağımsız değişkenler](./differences-between-modifiable-and-nonmodifiable-arguments.md) ve [farklar arasında geçirme bir bağımsız değişken değer ve başvuru tarafından](./differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
## <a name="choice-of-passing-mechanism"></a>Seçim mekanizması geçirme  
 Her değişken için dikkatle geçirme mekanizması seçmeniz gerekir.  
  
-   **Koruma**. Seçerken iki iletme mekanizmaları en önemli değişkenlerini değiştirmek için arama Etkilenme ölçüttür. Bağımsız değişken geçirme avantajı `ByRef` yordamı çağıran kodu bağımsız aracılığıyla bir değer döndürmesi emin olan. Bağımsız değişken geçirme avantajı `ByVal` yordamı tarafından değiştirilen bir değişken koruduğu emin olan.  
  
-   **Performans**. Geçirme mekanizması kodunuzu performansını etkileyebilir olsa da, genellikle anlamsız bir farktır. Bunun tek istisnası geçirilen değer türüdür `ByVal`. Bu durumda, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] bağımsız değişkeni, tüm veri içeriğini kopyalar. Bu nedenle, bir yapı gibi büyük değer türü için bunu geçirileceğini daha etkili olabilir `ByRef`.  
  
     Referans türleri için yalnızca verileri işaretçisine kopyalanan (dört 32-bit platformlarda 64 bit platformlarda sekiz bayt) bayttır. Bu nedenle, tür bağımsız değişkenler geçirebilirsiniz `String` veya `Object` performans zarar olmadan değeriyle.  
  
## <a name="determination-of-the-passing-mechanism"></a>Geçirme mekanizması olarak belirleme  
 Yordam bildirim her parametre için geçirme mekanizması belirtir. Çağrıyı yapan kod geçersiz kılınamaz bir `ByVal` mekanizması.  
  
 Bir parametre ile bildirilirse `ByRef`, çağrıyı yapan kod mekanizmasına zorlayabilirsiniz `ByVal` çağrısında parantez içinde bağımsız değişken adı kapsayan tarafından. Daha fazla bilgi için bkz: [nasıl yapılır: bağımsız değişkeni değere göre bayraklarıdır için zorlama](./how-to-force-an-argument-to-be-passed-by-value.md).  
  
 Varsayılan olarak [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] bağımsız değişkenleri değere göre geçirmektir.  
  
## <a name="when-to-pass-an-argument-by-value"></a>Bir bağımsız değişken değeri tarafından geçirmek ne zaman  
  
-   Bağımsız değişken temel arama code öğesi değiştirilemez bir öğeyse, karşılık gelen bir parametre bildirme [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). Kod değiştirilemez öğesinin değeri değiştirebilirsiniz.  
  
-   Temel öğesi değiştirilebilir, ancak değerini değiştirmek için yordamı istemiyorsanız, parametre bildirme `ByVal`. Yalnızca çağıran kodu değeri tarafından geçirilen değiştirilebilir bir öğenin değerini değiştirebilirsiniz.  
  
## <a name="when-to-pass-an-argument-by-reference"></a>Başvuruya göre bağımsız değişken geçirmek ne zaman  
  
-   Yordamı çağıran kodu temel alınan öğe değiştirmek için orijinal gereksinimi varsa, karşılık gelen bir parametre bildirme [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).  
  
-   Çağrıyı yapan kod temel alınan öğe değiştirme yordamı doğru kodunun yürütülmesini bağımlı olması durumunda, parametre bildirme `ByRef`. Değere göre başarılı olursa ya da çağıran kodu geçersiz kılmaları `ByRef` parantez içinde bağımsız değişken kapsayan tarafından mekanizması geçirme yordam çağrısı beklenmeyen sonuçlara neden.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, bağımsız değişkenleri değere göre geçirilecek ne zaman ve ne zaman başvuruya göre geçirme gösterilmektedir. Yordam `Calculate` her ikisi de sahip bir `ByVal` ve `ByRef` parametresi. Bir faiz oranını verilen `rate`ve para toplamını `debt`, yordamın için yeni bir değeri hesaplamak için bir görevdir `debt` diğer bir deyişle orijinal değerine faiz oranını uygulamanın sonucu `debt`. Çünkü `debt` olan bir `ByRef` parametresi, yeni toplam karşılık gelen çağrıyı yapan kod bağımsız değişkenin değeri olarak yansıtılır `debt`. Parametre `rate` olan bir `ByVal` parametresi çünkü `Calculate` değerini değiştirmemelisiniz.  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbcnProcedures#74](./codesnippet/VisualBasic/passing-arguments-by-value-and-by-reference_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamları](./index.md)  
 [Parametreler ve bağımsız değişkenler](./procedure-parameters-and-arguments.md)  
 [Nasıl yapılır: bir yordama bağımsız değişkenler geçirme](./how-to-pass-arguments-to-a-procedure.md)  
 [Nasıl yapılır: bir yordam bağımsız değişkeninin değerini değiştirme](./how-to-change-the-value-of-a-procedure-argument.md)  
 [Nasıl yapılır: bir yordam bağımsız değişkenini değer değişikliklerine karşı koruma](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [Nasıl yapılır: bağımsız değişkeni değere göre geçirilecek şekilde zorlama](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [Bağımsız değişkenleri konuma göre ve ada göre geçirme](./passing-arguments-by-position-and-by-name.md)  
 [Değer türleri ve başvuru türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
