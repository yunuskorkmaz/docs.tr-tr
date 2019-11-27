---
title: TryCast İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords:
- TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
ms.openlocfilehash: 53306575cfc385039be3939fd87cf993b4509af4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348209"
---
# <a name="trycast-operator-visual-basic"></a>TryCast İşleci (Visual Basic)
Özel durum oluşturmayan bir tür dönüştürme işlemi sunar.  
  
## <a name="remarks"></a>Açıklamalar  
 Denenen bir dönüştürme başarısız olursa `CType` ve `DirectCast` her ikisi de <xref:System.InvalidCastException> hatası oluşturur. Bu, uygulamanızın performansını olumsuz etkileyebilir. `TryCast` [hiçbir şey](../../../visual-basic/language-reference/nothing.md)döndürmez, bu nedenle olası bir özel durumu işlemek zorunda kalmak yerine yalnızca `Nothing`karşı döndürülen sonucu test etmeniz gerekir.  
  
 `TryCast` anahtar sözcüğünü [CType işlevini](../../../visual-basic/language-reference/functions/ctype-function.md) ve [DirectCast İşleci](../../../visual-basic/language-reference/operators/directcast-operator.md) anahtar sözcüğünü kullandığınız şekilde kullanırsınız. İlk bağımsız değişken olarak bir ifade ve ikinci bağımsız değişken olarak dönüştürülecek bir tür sağlarsınız. `TryCast` yalnızca sınıflar ve arabirimler gibi başvuru türlerinde çalışır. İki tür arasında devralma veya uygulama ilişkisi gerektirir. Bu, bir türün diğerini devralması ya da uygulamanız gereken anlamına gelir.  
  
## <a name="errors-and-failures"></a>Hatalar ve hatalar  
 `TryCast`, devralma veya uygulama ilişkisi olmadığını algılarsa bir derleyici hatası oluşturur. Ancak bir derleyici hatasının olmaması, başarılı bir dönüştürmeyi garanti etmez. İstenen dönüştürme daraltılamaz, çalışma zamanında başarısız olabilir. Bu durumda `TryCast` [hiçbir şey](../../../visual-basic/language-reference/nothing.md)döndürmez.  
  
## <a name="conversion-keywords"></a>Dönüşüm Anahtar Sözcükleri  
 Tür dönüştürme anahtar sözcüklerini karşılaştırma aşağıdaki gibidir.  
  
|Anahtar sözcüğü|Veri türleri|Bağımsız değişken ilişkisi|Çalışma zamanı hatası|  
|---|---|---|---|  
|[CType İşlevi](../../../visual-basic/language-reference/functions/ctype-function.md)|Tüm veri türleri|İki veri türü arasında genişletme veya daraltma dönüştürmesi tanımlanmalıdır|<xref:System.InvalidCastException> oluşturur|  
|[DirectCast İşleci](../../../visual-basic/language-reference/operators/directcast-operator.md)|Tüm veri türleri|Bir tür, diğer türden devralması veya uygulamamalıdır|<xref:System.InvalidCastException> oluşturur|  
|`TryCast`|Yalnızca başvuru türleri|Bir tür, diğer türden devralması veya uygulamamalıdır|[Hiçbir şey](../../../visual-basic/language-reference/nothing.md) döndürmez|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek `TryCast`nasıl kullanacağınızı gösterir.  
  
 [!code-vb[VbVbalrKeywords#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Genişletme ve Daraltma Dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Örtük ve Açık Dönüştürmeler](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
