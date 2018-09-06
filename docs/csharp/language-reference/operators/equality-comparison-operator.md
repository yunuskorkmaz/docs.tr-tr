---
title: == İşleci (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- ==_CSharpKeyword
helpviewer_keywords:
- == operator [C#]
- equality operator [C#]
ms.assetid: 34c6b597-caa2-4855-a7cd-38ecdd11bd07
ms.openlocfilehash: d9d7dcf3b38939e681fb51d6c674151cee78b3d0
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43779178"
---
# <a name="-operator-c-reference"></a>== İşleci (C# Başvurusu)
Önceden değer türleri eşitlik işlecini (`==`) işlenenleri değerlerini eşitse true değerini döndürür `false` Aksi takdirde. İçin başvuru türleri dışındaki [dize](../../../csharp/language-reference/keywords/string.md), `==` döndürür `true` iki işlenenleri aynı nesneye başvuruyorsa. İçin `string` türü `==` dizelerin değerlerini karşılaştırır.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanıcı tanımlı değer türleri aşırı yükleme `==` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)). Bu nedenle ancak varsayılan olarak kullanıcı tarafından tanımlanan başvuru türleri için `==` hem önceden tanımlanmış ve kullanıcı tarafından tanımlanan başvuru türleri için yukarıda açıklandığı gibi davranır. Varsa `==` aşırı yüklendi [! =](../../../csharp/language-reference/operators/not-equal-operator.md) da aşırı yüklenmiş gerekir. Tamsayı türlerinde işlemler genellikle numaralandırma üzerinde izin verilir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#36](../../../csharp/language-reference/operators/codesnippet/CSharp/equality-comparison-operator_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# İşleçleri](../../../csharp/language-reference/operators/index.md)
