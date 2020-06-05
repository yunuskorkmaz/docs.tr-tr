---
title: DirectCast İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.directCast
- directCast
helpviewer_keywords:
- DirectCast keyword [Visual Basic]
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
ms.openlocfilehash: 96cb2082d59373deb34d6894270205b7c1045850
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371524"
---
# <a name="directcast-operator-visual-basic"></a>DirectCast İşleci (Visual Basic)
Devralma veya uygulamaya göre bir tür dönüştürme işlemi sunar.  
  
## <a name="remarks"></a>Açıklamalar  
 `DirectCast`dönüştürme için Visual Basic çalışma zamanı yardımcı yordamlarını kullanmaz, bu nedenle `CType` veri türüne dönüştürme işleminden daha iyi bir performans sağlayabilir `Object` .  
  
 `DirectCast` [CType Işlevini](../functions/ctype-function.md) ve [TryCast İşleci](trycast-operator.md) anahtar sözcüğünü kullanma yöntemine benzer şekilde anahtar sözcüğünü kullanırsınız. İlk bağımsız değişken olarak bir ifade ve ikinci bağımsız değişken olarak dönüştürülecek bir tür sağlarsınız. `DirectCast`iki bağımsız değişkenin veri türleri arasında devralma veya uygulama ilişkisi gerektirir. Bu, bir türün diğerini devralması ya da uygulamanız gereken anlamına gelir.  
  
## <a name="errors-and-failures"></a>Hatalar ve hatalar  
 `DirectCast`devralma veya uygulama ilişkisi olmadığını algılarsa bir derleyici hatası oluşturur. Ancak bir derleyici hatasının olmaması, başarılı bir dönüştürmeyi garanti etmez. İstenen dönüştürme daraltılamaz, çalışma zamanında başarısız olabilir. Bu durumda, çalışma zamanı bir hata oluşturur <xref:System.InvalidCastException> .  
  
## <a name="conversion-keywords"></a>Dönüşüm Anahtar Sözcükleri  
 Tür dönüştürme anahtar sözcüklerini karşılaştırma aşağıdaki gibidir.  
  
|Sözcükle|Veri türleri|Bağımsız değişken ilişkisi|Çalışma zamanı hatası|  
|---|---|---|---|  
|[CType İşlevi](../functions/ctype-function.md)|Tüm veri türleri|İki veri türü arasında genişletme veya daraltma dönüştürmesi tanımlanmalıdır|Oluşturur<xref:System.InvalidCastException>|  
|`DirectCast`|Tüm veri türleri|Bir tür, diğer türden devralması veya uygulamamalıdır|Oluşturur<xref:System.InvalidCastException>|  
|[TryCast İşleci](trycast-operator.md)|Yalnızca başvuru türleri|Bir tür, diğer türden devralması veya uygulamamalıdır|[Hiçbir şey](../nothing.md) döndürmez|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek `DirectCast` , çalışma zamanında başarısız olan diğeri ve başarılı olan iki kullanımı gösterir.  
  
 [!code-vb[VbVbalrKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#1)]  
  
 Önceki örnekte, çalışma zamanı türü ' `q` dir `Double` . `CType`' `Double` e dönüştürülebileceğinden başarılı oldu `Integer` . Ancak, `DirectCast` `Double` `Integer` bir dönüştürme var olsa da, çalışma zamanı türünün ile devralma ilişkisi olmadığından, ilki çalışma zamanında başarısız olur. İkinciden `DirectCast` <xref:System.Windows.Forms.Form> Devralındığı için, türünden türüne dönüştürdüğü için ikinci başarılı olur <xref:System.Windows.Forms.Control> <xref:System.Windows.Forms.Form> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Convert.ChangeType%2A?displayProperty=nameWithType>
- [Genişletme ve Daraltma Dönüşümleri](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Örtük ve Açık Dönüştürmeler](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
