---
title: Boole Veri Türü (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.FALSE
- vb.TRUE
- vb.Boolean
helpviewer_keywords:
- Boolean data type
- Boolean values [Visual Basic], False keyword
- False keyword [Visual Basic]
- True keyword [Visual Basic]
- Boolean values [Visual Basic], True keyword
ms.assetid: 4858e630-4813-4216-a55e-f4d0feb884e4
ms.openlocfilehash: 5e90d1dc5eb0beb3afd8fc69da32f89943e94c48
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54741918"
---
# <a name="boolean-data-type-visual-basic"></a>Boole Veri Türü (Visual Basic)
Yalnızca ayrı tutma değerleri `True` veya `False`. Anahtar sözcükler `True` ve `False` iki durum için karşılık gelen `Boolean` değişkenleri.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım [Boole veri türü (Visual Basic)](../../../visual-basic/language-reference/data-types/boolean-data-type.md) Evet/Hayır veya açık/kapalı true/false gibi iki durumlu değerler içerecek şekilde.  
  
 Varsayılan değer olan `Boolean` olduğu `False`.  
  
 `Boolean` Değer sayı olarak depolanmaz ve depolanan değerler sayıya eşdeğer olması amaçlanmamıştır. Hiçbir zaman eşdeğer sayısal değerler için dayanan kod yazmanız gerekir `True` ve `False`. Mümkün olduğunda, kullanımını sınırlamanız gerekir `Boolean` kendisi için tasarlanan mantıksal değerleri değişkenlere.  
  
## <a name="type-conversions"></a>Tür Dönüştürmeleri  
 Visual Basic sayısal veri türü değerleri için ne zaman dönüştürür `Boolean`, 0 olur `False` ve diğer tüm değerler `True`. Visual Basic zaman dönüştürür `Boolean` değerleri sayısal türlere `False` 0 olur ve `True` -1 olur.  
  
 Arasında dönüştürürken `Boolean` değerlerini ve sayısal veri türlerini tutmak .NET Framework dönüştürme yöntemleri Visual Basic dönüştürme anahtar sözcükleri'dekiyle aynı sonucu her zaman oluşturmamasını unutmayın. Visual Basic dönüştürme davranışını önceki sürümleriyle uyumlu korur olmasıdır. Daha fazla bilgi için "Boole türü mu değil dönüştürmek için sayısal türü doğru" bölümüne bakın [veri türleri sorunlarını giderme](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## <a name="programming-tips"></a>Programlama İpuçları  
  
-   **Negatif sayılar.** `Boolean` bir sayısal tür değil ve negatif bir değeri temsil edemeyen. Her iki durumda da kullanmamalısınız `Boolean` sayısal değerleri tutmak için.  
  
-   **Tür karakterleri.** `Boolean` değişmez değer türü karakteri ya da tanımlayıcı türü karakteri var.  
  
-   **Çerçeve türü.** .NET Framework içinde karşılık gelen türü <xref:System.Boolean?displayProperty=nameWithType> yapısı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `runningVB` olduğu bir `Boolean` Evet/Hayır basit depolayan değişken.  
  
```  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Boolean?displayProperty=nameWithType>
- [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Veri Türü Sorunlarını Giderme](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [CType İşlevi](../../../visual-basic/language-reference/functions/ctype-function.md)
