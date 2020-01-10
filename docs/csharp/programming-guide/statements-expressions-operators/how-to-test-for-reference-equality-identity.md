---
title: Başvuru eşitlik için test etme (kimlik)- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- object identity [C#]
- reference equality [C#]
ms.assetid: 91307fda-267b-4fd2-a338-2aada39ee791
ms.openlocfilehash: 77ce2ef0ccf47d619134c120101ba2aa04f485e6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75699060"
---
# <a name="how-to-test-for-reference-equality-identity-c-programming-guide"></a>Başvuru eşitlik için test etme (kimlik) (C# Programlama Kılavuzu)
Türlerinizin başvuru eşitlik karşılaştırmalarını desteklemek için herhangi bir özel mantık uygulamanız gerekmez. Bu işlevsellik, statik <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> yöntemi tarafından tüm türler için sağlanır.  
  
 Aşağıdaki örnek, iki değişkenin *başvuru eşitliği*olup olmadığını nasıl belirleyeceğini gösterir. Bu, bellekteki aynı nesneye başvurdukları anlamına gelir.  
  
 Örnek ayrıca, neden <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> her zaman değer türleri için `false` döndürdüğünü ve neden dize eşitliğini belirlemede <xref:System.Object.ReferenceEquals%2A> kullanmamalısınız olduğunu gösterir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideObjects#90](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#90)]  
  
 <xref:System.Object?displayProperty=nameWithType> Universal temel sınıfındaki `Equals` uygulanması de bir başvuru eşitlik denetimi gerçekleştirir, ancak bunu kullanmak en iyisidir çünkü yöntemi geçersiz kılmak için bir sınıf olması durumunda sonuçlar beklediğiniz gibi olmayabilir. Aynı değer, `==` ve `!=` işleçleri için de geçerlidir. Başvuru türleri üzerinde çalışırken, `==` ve `!=` varsayılan davranışı bir başvuru eşitlik denetimi gerçekleştirdir. Ancak, türetilmiş sınıflar bir değer eşitlik denetimi gerçekleştirmek için işlecini aşırı yükleyebilir. Hata olasılığını en aza indirmek için, iki nesnenin başvuru eşitlik içerip içermediğini belirleyebilmek gerektiğinde <xref:System.Object.ReferenceEquals%2A> her zaman en iyi şekilde kullanılır.  
  
 Aynı derleme içindeki sabit dizeler her zaman çalışma zamanı tarafından dağıtılır. Diğer bir deyişle, her benzersiz sabit değer dizesinin yalnızca bir örneği korunur. Ancak çalışma zamanı, çalışma zamanında oluşturulan dizelerin birbirine bağlı olduğunu veya farklı derlemelerdeki iki eşit Sabit dizenin birbirine bağlı olduğunu garanti etmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Eşitlik Karşılaştırmaları](./equality-comparisons.md)
