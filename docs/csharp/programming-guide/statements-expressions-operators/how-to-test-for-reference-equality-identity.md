---
title: Başvuru eşitlik için test etme (kimlik)-C# Programlama Kılavuzu
description: Başvuru eşitliği (kimlik) için test yapmayı öğrenin. Bir kod örneğine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
helpviewer_keywords:
- object identity [C#]
- reference equality [C#]
ms.assetid: 91307fda-267b-4fd2-a338-2aada39ee791
ms.openlocfilehash: 1d1a0e5d80ac8d2a689e75acbc6099b92e16f23f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151447"
---
# <a name="how-to-test-for-reference-equality-identity-c-programming-guide"></a>Başvuru eşitlik için test etme (kimlik) (C# Programlama Kılavuzu)

Türlerinizin başvuru eşitlik karşılaştırmalarını desteklemek için herhangi bir özel mantık uygulamanız gerekmez. Bu işlev, statik yönteme göre tüm türler için sağlanır <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> .  
  
 Aşağıdaki örnek, iki değişkenin *başvuru eşitliği*olup olmadığını nasıl belirleyeceğini gösterir. Bu, bellekteki aynı nesneye başvurdukları anlamına gelir.  
  
 Örnek ayrıca neden <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> her zaman `false` değer türleri için döndüğünü ve neden  <xref:System.Object.ReferenceEquals%2A> dize eşitliğini belirlemede kullanmamalısınız gerektiğini gösterir.  
  
## <a name="example"></a>Örnek  

 [!code-csharp[csProgGuideObjects#90](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#90)]  
  
 `Equals` <xref:System.Object?displayProperty=nameWithType> Evrensel temel sınıftaki uygulamasının uygulanması de bir başvuru eşitlik denetimi gerçekleştirir, ancak bunu kullanmak en iyisidir çünkü yöntemi geçersiz kılmak için bir sınıf olduğunda, sonuçlar beklediğiniz gibi olmayabilir. Aynı, ve işleçleri için de `==` geçerlidir `!=` . Başvuru türleri üzerinde çalıştıklarında, varsayılan davranışı `==` ve `!=` başvuru eşitlik denetimi gerçekleştirmek için kullanılır. Ancak, türetilmiş sınıflar bir değer eşitlik denetimi gerçekleştirmek için işlecini aşırı yükleyebilir. Hata olasılığını en aza indirmek için, <xref:System.Object.ReferenceEquals%2A> iki nesnenin başvuru eşitlik içerip içermediğini belirlemekte her zaman en iyi şekilde kullanılır.  
  
 Aynı derleme içindeki sabit dizeler her zaman çalışma zamanı tarafından dağıtılır. Diğer bir deyişle, her benzersiz sabit değer dizesinin yalnızca bir örneği korunur. Ancak çalışma zamanı, çalışma zamanında oluşturulan dizelerin birbirine bağlı olduğunu veya farklı derlemelerdeki iki eşit Sabit dizenin birbirine bağlı olduğunu garanti etmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Eşitlik karşılaştırmaları](./equality-comparisons.md)
