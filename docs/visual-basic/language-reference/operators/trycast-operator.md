---
title: TryCast İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords:
- TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
ms.openlocfilehash: dc4807781f9e1aaf894016952911bd7b32c42948
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875316"
---
# <a name="trycast-operator-visual-basic"></a>TryCast İşleci (Visual Basic)

Özel durum oluşturmayan bir tür dönüştürme işlemi sunar.  
  
## <a name="remarks"></a>Açıklamalar  

 Denenen bir dönüştürme başarısız olursa `CType` ve `DirectCast` her ikisi de bir <xref:System.InvalidCastException> hata oluşturur. Bu, uygulamanızın performansını olumsuz etkileyebilir. `TryCast`[hiçbir şey](../nothing.md)döndürmez, bu nedenle olası bir özel durumu işlemek zorunda kalmak yerine yalnızca döndürülen sonucu test etmeniz gerekir `Nothing` .  
  
 `TryCast`Anahtar sözcüğünü [CType Işlevini](../functions/ctype-function.md) ve [DirectCast İşleci](directcast-operator.md) anahtar sözcüğünü kullandığınız şekilde kullanırsınız. İlk bağımsız değişken olarak bir ifade ve ikinci bağımsız değişken olarak dönüştürülecek bir tür sağlarsınız. `TryCast` Yalnızca sınıflar ve arabirimler gibi başvuru türlerinde çalışır. İki tür arasında devralma veya uygulama ilişkisi gerektirir. Bu, bir türün diğerini devralması ya da uygulamanız gereken anlamına gelir.  
  
## <a name="errors-and-failures"></a>Hatalar ve hatalar  

 `TryCast` devralma veya uygulama ilişkisi olmadığını algılarsa bir derleyici hatası oluşturur. Ancak bir derleyici hatasının olmaması, başarılı bir dönüştürmeyi garanti etmez. İstenen dönüştürme daraltılamaz, çalışma zamanında başarısız olabilir. Bu durumda `TryCast` [hiçbir şey](../nothing.md)döndürmez.  
  
## <a name="conversion-keywords"></a>Dönüşüm Anahtar Sözcükleri  

 Tür dönüştürme anahtar sözcüklerini karşılaştırma aşağıdaki gibidir.  
  
|Sözcükle|Veri türleri|Bağımsız değişken ilişkisi|Çalışma zamanı hatası|  
|---|---|---|---|  
|[CType İşlevi](../functions/ctype-function.md)|Tüm veri türleri|İki veri türü arasında genişletme veya daraltma dönüştürmesi tanımlanmalıdır|Oluşturur <xref:System.InvalidCastException>|  
|[DirectCast İşleci](directcast-operator.md)|Tüm veri türleri|Bir tür, diğer türden devralması veya uygulamamalıdır|Oluşturur <xref:System.InvalidCastException>|  
|`TryCast`|Yalnızca başvuru türleri|Bir tür, diğer türden devralması veya uygulamamalıdır|[Hiçbir şey](../nothing.md) döndürmez|  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek nasıl kullanılacağını göstermektedir `TryCast` .  
  
 [!code-vb[VbVbalrKeywords#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Genişletme ve Daraltma Dönüşümleri](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Örtük ve Açık Dönüştürmeler](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
