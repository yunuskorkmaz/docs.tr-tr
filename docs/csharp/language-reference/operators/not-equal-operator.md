---
title: '! = İşleci - C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '!=_CSharpKeyword'
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
ms.openlocfilehash: 15f1b5930117e608644a58343fb855562f36b21c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237824"
---
# <a name="-operator-c-reference"></a>!= İşleci (C# Başvurusu)
Eşitsizlik işleci (`!=`), işlenenlerinin true, eşitse false değerini döndürür. Eşitsizlik işleçleri, string ve object dahil olmak üzere tüm türleri için önceden tanımlanmıştır. Kullanıcı tanımlı türler aşırı yükleme `!=` işleci.  
  
## <a name="remarks"></a>Açıklamalar  
 Önceden değer türleri, eşitsizlik işleci (`!=`) işlenenleri değerlerini, aksi takdirde farklı, false ise true değerini döndürür. İçin başvuru türleri dışındaki `string`, `!=` iki işlenenleri farklı nesnelere başvuruda bulunuyorsa true değerini döndürür. İçin `string` türü `!=` dizelerin değerlerini karşılaştırır.  
  
 Kullanıcı tanımlı değer türleri aşırı yükleme `!=` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)). Bu nedenle ancak varsayılan olarak kullanıcı tarafından tanımlanan başvuru türleri için `!=` hem önceden tanımlanmış ve kullanıcı tarafından tanımlanan başvuru türleri için yukarıda açıklandığı gibi davranır. Varsa `!=` aşırı yüklendi [ == ](../../../csharp/language-reference/operators/equality-comparison-operator.md) da aşırı yüklenmiş gerekir. Tamsayı türlerinde işlemler genellikle numaralandırma üzerinde izin verilir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#33](../../../csharp/language-reference/operators/codesnippet/CSharp/not-equal-operator_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# İşleçleri](../../../csharp/language-reference/operators/index.md)
