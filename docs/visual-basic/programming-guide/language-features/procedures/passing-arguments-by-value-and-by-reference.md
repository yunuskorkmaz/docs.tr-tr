---
title: Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme
ms.date: 07/20/2015
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- passing arguments [Visual Basic], by value or by reference
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
- argument passing [Visual Basic], by value or by reference
ms.assetid: fd8a9de6-7178-44d5-a9bf-458d4ad907c2
ms.openlocfilehash: b7430b209f53a0a924ec587a0097178baf0075e3
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91059229"
---
# <a name="passing-arguments-by-value-and-by-reference-visual-basic"></a>Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme (Visual Basic)

Visual Basic, bir yordama *değere* veya *başvuruya*göre bir bağımsız değişken geçirebilirsiniz. Bu, *geçirme mekanizması*olarak bilinir ve yordamın çağıran koddaki bağımsız değişkenin temelindeki programlama öğesini değiştirip değiştiremeyeceğini belirler. Yordam bildirimi, [ByVal](../../../language-reference/modifiers/byval.md) veya [ByRef](../../../language-reference/modifiers/byref.md) anahtar sözcüğü belirtilerek her bir parametre için geçen geçiş mekanizmasını belirler.  
  
## <a name="distinctions"></a>Farklar  

 Bir yordama bir bağımsız değişken geçirirken, birbirleriyle etkileşime geçen birkaç farklı ayrımın farkında olun:  
  
- Temeldeki programlama öğesinin değiştirilebilir mi yoksa değiştirilemez mi olduğunu belirtir  
  
- Bağımsız değişkenin değiştirilebilir olup olmadığı  
  
- Bağımsız değişkenin değere göre mi yoksa başvuruya göre mi geçtiğini belirtir  
  
- Bağımsız değişken veri türünün bir değer türü veya bir başvuru türü olup olmadığı  
  
 Daha fazla bilgi için bkz. [değiştirilebilir ve değiştirilemeyen bağımsız değişkenler](./differences-between-modifiable-and-nonmodifiable-arguments.md) Ile [bir bağımsız değişkeni değere ve başvuruya göre geçirme arasındaki](./differences-between-passing-an-argument-by-value-and-by-reference.md)farklılıklar.  
  
## <a name="choice-of-passing-mechanism"></a>Geçirme mekanizması seçimi  

 Geçirilen mekanizmayı her bağımsız değişken için dikkatle seçmeniz gerekir.  
  
- **Koruma**. İki geçiş mekanizması arasında seçim yaparken en önemli ölçüt, değiştirilecek çağrı değişkenlerinin açıklanmesidir. Bağımsız değişken geçirmenin avantajı, `ByRef` yordamın bu bağımsız değişken aracılığıyla çağırma koduna bir değer döndüremesidir. Bağımsız değişken geçirmenin avantajı, `ByVal` bir değişkenin yordam tarafından değiştirilmesini koruabilmesidir.  
  
- **Performans**. Geçirme mekanizması kodunuzun performansını etkileyebilse de, fark genellikle önemsizdir. Bu bir özel durum geçildi değer türüdür `ByVal` . Bu durumda Visual Basic bağımsız değişkenin tüm veri içeriğini kopyalar. Bu nedenle, yapı gibi büyük bir değer türü için, daha verimli olabilir `ByRef` .  
  
     Başvuru türleri için, yalnızca verilerin işaretçisi kopyalanır (32-bit platformlarda dört bayt, 64 bit platformlarda sekiz bayt). Bu nedenle, bu tür bağımsız değişkenleri, `String` performansı çok fazla `Object` performans olmadan veya değere göre geçirebilirsiniz.  
  
## <a name="determination-of-the-passing-mechanism"></a>Geçen mekanizmanın belirlenmesi  

 Yordam bildirimi her parametre için geçen mekanizmayı belirtir. Çağıran kod bir `ByVal` mekanizmayı geçersiz kılamaz.  
  
 Bir parametre ile bildirilirse `ByRef` , çağıran kod, `ByVal` bağımsız değişken adını çağrıda parantez içine alarak mekanizmayı zorlayabilir. Daha fazla bilgi için bkz. [nasıl yapılır: bağımsız değişkeni değere göre geçirilmesine zorlama](./how-to-force-an-argument-to-be-passed-by-value.md).  
  
 Visual Basic varsayılan değeri, bağımsız değişkenleri değere göre geçirmektir.  
  
## <a name="when-to-pass-an-argument-by-value"></a>Bir bağımsız değişkenin değere göre ne zaman geçirileceğini  
  
- Bağımsız değişkeni temel alan çağıran kod öğesi değiştirilemeyen bir öğe ise, karşılık gelen [ByVal](../../../language-reference/modifiers/byval.md)parametresini bildirin. Değiştirilemeyen bir öğenin değerini değiştirmek için kod yok.  
  
- Temeldeki öğe değiştirilebilir, ancak yordamın değerini değiştirebilmesini istemiyorsanız, parametresini bildirin `ByVal` . Yalnızca çağıran kod, değere göre geçirilen değiştirilebilir öğenin değerini değiştirebilir.  
  
## <a name="when-to-pass-an-argument-by-reference"></a>Bir bağımsız değişkenin başvuruya göre ne zaman geçirileceğini  
  
- Yordamın, çağıran koddaki temel alınan öğeyi değiştirmesi gerekirse, karşılık gelen [ByRef](../../../language-reference/modifiers/byref.md)parametresini bildirin.  
  
- Kodun doğru yürütülmesi, çağıran koddaki temeldeki öğeyi değiştirme yordamına bağımlıysa, parametresini bildirin `ByRef` . Bunu değere göre geçirirseniz veya çağırma kodu `ByRef` bağımsız değişkeni parantez içine alarak geçen mekanizmayı geçersiz kılıyorsa, yordam çağrısı beklenmedik sonuçlar üretebilir.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Description  

 Aşağıdaki örnek, bağımsız değişkenlerin değere göre ne zaman geçirileceğini ve başvuruya göre ne zaman geçirileceğini gösterir. Yordamda `Calculate` hem a `ByVal` hem de `ByRef` parametresi vardır. Bir faiz oranı, `rate` ve toplam para miktarı verildiğinde, `debt` yordamın görevi, `debt` Bu değerin özgün değerine uygulanan faiz oranını uygulamanın sonucu olan yeni bir değer hesaplayacaktır `debt` . `debt`Bir parametre olduğundan `ByRef` , yeni toplam, öğesine karşılık gelen çağıran koddaki bağımsız değişkenin değerine yansıtılır `debt` . Parametresi `rate` , `ByVal` `Calculate` değerini değiştirmemelidir.  
  
### <a name="code"></a>Kod  

 [!code-vb[VbVbcnProcedures#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class2.vb#74)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme](./how-to-pass-arguments-to-a-procedure.md)
- [Nasıl yapılır: Bir Yordam Bağımsız Değişkeninin Değerini Değiştirme](./how-to-change-the-value-of-a-procedure-argument.md)
- [Nasıl yapılır: Bir Yordam Bağımsız Değişkenini Değer Değişikliklerine Karşı Koruma](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Nasıl yapılır: Bağımsız Değişkeni Değere Göre Geçirilecek Şekilde Zorlama](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme](./passing-arguments-by-position-and-by-name.md)
- [Değer Türleri ve Başvuru Türleri](../data-types/value-types-and-reference-types.md)
