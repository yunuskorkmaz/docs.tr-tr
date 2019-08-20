---
title: 'Nasıl yapılır: Başvuru eşitlik için test (kimlik)- C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- object identity [C#]
- reference equality [C#]
ms.assetid: 91307fda-267b-4fd2-a338-2aada39ee791
ms.openlocfilehash: 2b4b7b7bdd03077a78aa2a6375764fa86a885ef5
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588632"
---
# <a name="how-to-test-for-reference-equality-identity-c-programming-guide"></a>Nasıl yapılır: Başvuru eşitlik için test (kimlik) (C# Programlama Kılavuzu)
Türlerinizin başvuru eşitlik karşılaştırmalarını desteklemek için herhangi bir özel mantık uygulamanız gerekmez. Bu işlev, statik <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> yönteme göre tüm türler için sağlanır.  
  
 Aşağıdaki örnek, iki değişkenin *başvuru eşitliği*olup olmadığını nasıl belirleyeceğini gösterir. Bu, bellekteki aynı nesneye başvurdukları anlamına gelir.  
  
 Örnek ayrıca neden <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> her zaman değer türleri `false` için döndüğünü ve <xref:System.Object.ReferenceEquals%2A> neden dize eşitliğini belirlemede kullanmamalısınız gerektiğini gösterir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideObjects#90](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#90)]  
  
 Evrensel temel sınıftaki `Equals` uygulamasının uygulanması de bir başvuru eşitlik denetimi gerçekleştirir, ancak bunu kullanmak en iyisidir çünkü yöntemi geçersiz kılmak için bir sınıf olduğunda, sonuçlar beklediğiniz gibi olmayabilir. <xref:System.Object?displayProperty=nameWithType> Aynı, `==` ve `!=` işleçleri için de geçerlidir. Başvuru türleri üzerinde çalıştıklarında, varsayılan davranışı `==` ve `!=` başvuru eşitlik denetimi gerçekleştirmek için kullanılır. Ancak, türetilmiş sınıflar bir değer eşitlik denetimi gerçekleştirmek için işlecini aşırı yükleyebilir. Hata olasılığını en aza indirmek için, iki nesnenin başvuru eşitlik içerip içermediğini <xref:System.Object.ReferenceEquals%2A> belirlemekte her zaman en iyi şekilde kullanılır.  
  
 Aynı derleme içindeki sabit dizeler her zaman çalışma zamanı tarafından dağıtılır. Diğer bir deyişle, her benzersiz sabit değer dizesinin yalnızca bir örneği korunur. Ancak çalışma zamanı, çalışma zamanında oluşturulan dizelerin birbirine bağlı olduğunu veya farklı derlemelerdeki iki eşit Sabit dizenin birbirine bağlı olduğunu garanti etmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Eşitlik Karşılaştırmaları](./equality-comparisons.md)
