---
title: "Boole Veri Türü (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bdc106f1ec874c1a2165df069d5f3485fe5b2e43
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="boolean-data-type-visual-basic"></a>Boole Veri Türü (Visual Basic)
Yalnızca ayrı tutma değerleri `True` veya `False`. Anahtar sözcükler `True` ve `False` için iki durumlarını karşılık `Boolean` değişkenleri.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım [Boole veri türü (Visual Basic)](../../../visual-basic/language-reference/data-types/boolean-data-type.md) true/false gibi iki durumlu değerler içermesini Evet/Hayır, veya açık/kapalı.  
  
 Varsayılan değer olan `Boolean` olan `False`.  
  
 `Boolean`değerleri sayı olarak depolanmaz ve depolanan değerlerin sayıya eşit olması amaçlanmamıştır. Hiçbir zaman eşdeğer sayısal değerler için güvenen kod yazmanız gerekir `True` ve `False`. Mümkün olduğunda, kullanımını kısıtlamalısınız `Boolean` , bunlar tasarlanan mantıksal değerleri değişkenleri.  
  
## <a name="type-conversions"></a>Tür Dönüştürmeleri  
 Visual Basic sayısal veri türü değerleri için ne zaman dönüştürür `Boolean`, 0 olur `False` ve diğer tüm değerler duruma `True`. Visual Basic zaman dönüştürür `Boolean` sayısal türler değerlere `False` 0 olur ve `True` -1 olur.  
  
 Arasında dönüştürürken `Boolean` değerleri ve sayısal veri türleri tutmak .NET Framework dönüştürme yöntemleri her zaman aynı sonucu olarak Visual Basic dönüşüm anahtar sözcükleri vermez unutmayın. Visual Basic dönüştürme davranış önceki sürümleriyle uyumlu koruyacağından budur. Daha fazla bilgi için "Boole türü mu değil dönüştürmek için sayısal türü doğru şekilde" bölümüne bakın [veri türleri sorunlarını giderme](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## <a name="programming-tips"></a>Programlama İpuçları  
  
-   **Negatif sayılar.** `Boolean`sayısal bir tür değil ve negatif bir değeri temsil edilemez. Her iki durumda da kullanılamaz `Boolean` sayısal değerleri tutmak için.  
  
-   **Karakterleri yazın.** `Boolean`değişmez değer türü karakteri ya da tanımlayıcı türü karakteri içeriyor.  
  
-   **Framework türü.** .NET Framework'teki karşılık gelen tür <xref:System.Boolean?displayProperty=nameWithType> yapısı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `runningVB` olan bir `Boolean` Evet/Hayır ayarı basit depolar değişkeni.  
  
```  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Boolean?displayProperty=nameWithType>  
 [Veri türleri](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Tür dönüşüm işlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Dönüştürme özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Veri türlerinin etkili kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [Veri türleri sorunlarını giderme](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [CType işlevi](../../../visual-basic/language-reference/functions/ctype-function.md)
