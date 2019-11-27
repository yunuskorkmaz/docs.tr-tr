---
title: Boole Veri Türü
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
ms.openlocfilehash: 5d05514207c5d07e81aab897f40f728570f6bd87
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347843"
---
# <a name="boolean-data-type-visual-basic"></a>Boole Veri Türü (Visual Basic)

Yalnızca `True` veya `False`olabilecek değerleri tutar. `True` ve `False` anahtar sözcükleri `Boolean` değişkenlerinin iki durumuna karşılık gelir.  
  
## <a name="remarks"></a>Açıklamalar  

 True/false, Yes/No veya on/off gibi iki durumlu değerler içeren [Boolean veri türü (Visual Basic)](../../../visual-basic/language-reference/data-types/boolean-data-type.md) kullanın.  
  
 `Boolean` varsayılan değeri `False`.  
  
 `Boolean` değerler sayı olarak depolanmaz ve depolanan değerlerin sayılara eşit olması amaçlanmamıştır. `True` ve `False`için eşdeğer sayısal değerleri temel alan hiçbir kodu asla yazmamanız gerekir. Mümkün olduğunda, `Boolean` değişkenlerinin kullanımını, tasarlandıkları mantıksal değerlerle kısıtlamalısınız.  
  
## <a name="type-conversions"></a>Tür Dönüştürmeleri  

 Visual Basic sayısal veri türü değerlerini `Boolean`dönüştürdüğünde 0 `False` ve diğer tüm değerler `True`olur. Visual Basic `Boolean` değerlerini sayısal türlere dönüştürdüğünde, `False` 0 olur ve `True` 1 olur.  
  
 `Boolean` değerleri ve sayısal veri türleri arasında dönüştürme yaptığınızda, .NET Framework dönüştürme yöntemlerinin Visual Basic dönüştürme anahtar sözcükleriyle her zaman aynı sonuçları üretmeyeceğini göz önünde bulundurun. Bunun nedeni Visual Basic dönüştürmenin önceki sürümlerle uyumlu davranışları korumasından kaynaklanır. Daha fazla bilgi için bkz. [sorun giderme veri türlerinde](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)"Boole türü doğru şekilde sayısal türe dönüştürülmüyor".  
  
## <a name="programming-tips"></a>Programlama İpuçları  
  
- **Negatif sayılar.** `Boolean` sayısal bir tür değil ve negatif bir değeri temsil edemez. Herhangi bir durumda, sayısal değerleri tutmak için `Boolean` kullanmamalısınız.  
  
- **Tür karakterleri.** `Boolean` değişmez değer türü karakteri veya tanımlayıcı türü karakteri yok.  
  
- **Çerçeve türü.** .NET Framework karşılık gelen tür <xref:System.Boolean?displayProperty=nameWithType> yapısıdır.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnekte `runningVB`, basit bir Evet/Hayır ayarı depolayan bir `Boolean` değişkenidir.  
  
```vb  
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
