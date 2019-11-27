---
title: DirectCast İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.directCast
- directCast
helpviewer_keywords:
- DirectCast keyword [Visual Basic]
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
ms.openlocfilehash: 8ea29b80cf27bbb2c21a8cebbfaa0a294e05f11d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331315"
---
# <a name="directcast-operator-visual-basic"></a>DirectCast İşleci (Visual Basic)
Devralma veya uygulamaya göre bir tür dönüştürme işlemi sunar.  
  
## <a name="remarks"></a>Açıklamalar  
 `DirectCast`, dönüştürme için Visual Basic çalışma zamanı yardımcı yordamlarını kullanmaz, bu nedenle `Object`veri türüne dönüştürme sırasında `CType` kıyasla biraz daha iyi bir performans sağlayabilir.  
  
 [CType işlevini](../../../visual-basic/language-reference/functions/ctype-function.md) ve [TryCast İşleci](../../../visual-basic/language-reference/operators/trycast-operator.md) anahtar sözcüğünü kullanma yöntemine benzer şekilde `DirectCast` anahtar sözcüğünü kullanırsınız. İlk bağımsız değişken olarak bir ifade ve ikinci bağımsız değişken olarak dönüştürülecek bir tür sağlarsınız. `DirectCast` iki bağımsız değişkenin veri türleri arasında devralma veya uygulama ilişkisi gerektirir. Bu, bir türün diğerini devralması ya da uygulamanız gereken anlamına gelir.  
  
## <a name="errors-and-failures"></a>Hatalar ve hatalar  
 `DirectCast`, devralma veya uygulama ilişkisi olmadığını algılarsa bir derleyici hatası oluşturur. Ancak bir derleyici hatasının olmaması, başarılı bir dönüştürmeyi garanti etmez. İstenen dönüştürme daraltılamaz, çalışma zamanında başarısız olabilir. Bu durumda, çalışma zamanı bir <xref:System.InvalidCastException> hatası oluşturur.  
  
## <a name="conversion-keywords"></a>Dönüşüm Anahtar Sözcükleri  
 Tür dönüştürme anahtar sözcüklerini karşılaştırma aşağıdaki gibidir.  
  
|Anahtar sözcüğü|Veri türleri|Bağımsız değişken ilişkisi|Çalışma zamanı hatası|  
|---|---|---|---|  
|[CType İşlevi](../../../visual-basic/language-reference/functions/ctype-function.md)|Tüm veri türleri|İki veri türü arasında genişletme veya daraltma dönüştürmesi tanımlanmalıdır|<xref:System.InvalidCastException> oluşturur|  
|`DirectCast`|Tüm veri türleri|Bir tür, diğer türden devralması veya uygulamamalıdır|<xref:System.InvalidCastException> oluşturur|  
|[TryCast İşleci](../../../visual-basic/language-reference/operators/trycast-operator.md)|Yalnızca başvuru türleri|Bir tür, diğer türden devralması veya uygulamamalıdır|[Hiçbir şey](../../../visual-basic/language-reference/nothing.md) döndürmez|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, çalışma zamanında başarısız olan ve başarılı bir şekilde `DirectCast`iki kullanımını gösterir.  
  
 [!code-vb[VbVbalrKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#1)]  
  
 Yukarıdaki örnekte, `q` çalışma zamanı türü `Double`. `Double` `Integer`dönüştürülebildiğinden `CType` başarılı olur. Ancak, bir dönüştürme var olsa da, `Double` çalışma zamanı türünün `Integer`devralma ilişkisi olmadığından ilk `DirectCast` çalışma zamanında başarısız olur. İkinci `DirectCast`, <xref:System.Windows.Forms.Form> türünden <xref:System.Windows.Forms.Form> devraldığı <xref:System.Windows.Forms.Control>türüne dönüştürülemediğinden başarılı olur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Convert.ChangeType%2A?displayProperty=nameWithType>
- [Genişletme ve Daraltma Dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Örtük ve Açık Dönüştürmeler](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
