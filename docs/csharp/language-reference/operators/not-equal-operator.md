---
title: '!= İşleci (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '!=_CSharpKeyword'
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
ms.openlocfilehash: e974ffb1b25944e24fca23864dc7e932ec1876d5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43415387"
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
