---
title: Boolean Veri Türü
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
ms.openlocfilehash: 851c524a83c5f24b77a151634a96798249c5905e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374427"
---
# <a name="boolean-data-type-visual-basic"></a>Boole Veri Türü (Visual Basic)

Yalnızca veya olabilecek değerleri barındırır `True` `False` . Anahtar sözcükler `True` ve `False` iki değişken için karşılık gelir `Boolean` .  
  
## <a name="remarks"></a>Açıklamalar  

 True/false, Yes/No veya on/off gibi iki durumlu değerler içeren [Boolean veri türü (Visual Basic)](boolean-data-type.md) kullanın.  
  
 Varsayılan değeri `Boolean` `False` .  
  
 `Boolean`değerler sayı olarak depolanmaz ve depolanan değerlerin sayılara eşit olması amaçlanmamıştır. Ve için eşdeğer sayısal değerleri temel alan hiçbir kodu asla yazmamanız `True` gerekir `False` . Mümkün olduğunda, `Boolean` değişkenlerin kullanımını tasarlandıkları mantıksal değerlerle kısıtlamalısınız.  
  
## <a name="type-conversions"></a>Tür Dönüştürmeleri  

 Visual Basic sayısal veri türü değerlerini öğesine dönüştürdüğünde `Boolean` 0 olur `False` ve diğer tüm değerler olur `True` . Visual Basic `Boolean` değerleri sayısal türlere dönüştürdüğünde `False` 0 olur ve `True` -1 olur.  
  
 `Boolean`Değerler ve sayısal veri türleri arasında dönüştürme yaptığınızda, .NET Framework dönüştürme yöntemlerinin Visual Basic dönüştürme anahtar sözcükleriyle her zaman aynı sonuçları üretmeyeceğini aklınızda bulundurun. Bunun nedeni Visual Basic dönüştürmenin önceki sürümlerle uyumlu davranışları korumasından kaynaklanır. Daha fazla bilgi için bkz. [sorun giderme veri türlerinde](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)"Boole türü doğru şekilde sayısal türe dönüştürülmüyor".  
  
## <a name="programming-tips"></a>Programlama İpuçları  
  
- **Negatif sayılar.** `Boolean`sayısal bir tür değil ve negatif bir değeri temsil edemez. Herhangi bir durumda, `Boolean` sayısal değerleri tutmak için kullanmamalısınız.  
  
- **Tür karakterleri.** `Boolean`değişmez değer türü karakteri veya tanımlayıcı türü karakteri yok.  
  
- **Çerçeve türü.** .NET Framework karşılık gelen tür <xref:System.Boolean?displayProperty=nameWithType> yapısıdır.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnekte, basit bir `runningVB` `Boolean` Evet/Hayır ayarı depolayan bir değişkendir.  
  
```vb  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Boolean?displayProperty=nameWithType>
- [Veri türleri](index.md)
- [Tür Dönüştürme İşlevleri](../functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../keywords/conversion-summary.md)
- [Veri Türlerinin Etkili Kullanımı](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Veri Türü Sorunlarını Giderme](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [CType İşlevi](../functions/ctype-function.md)
