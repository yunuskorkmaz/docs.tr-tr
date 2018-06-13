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
ms.openlocfilehash: e409e2a80886fd5f7f4cdbeaa9b4e3325f8a967b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33272445"
---
# <a name="-operator-c-reference"></a>!= İşleci (C# Başvurusu)
Eşitsizlik işleci (`!=`) işlenenleri true tersi durumda, eşitse, false değerini döndürür. Eşitsizlik işleçleri dize ve nesne dahil olmak üzere tüm türleri için önceden tanımlanmıştır. Kullanıcı tanımlı türler aşırı yükleme `!=` işleci.  
  
## <a name="remarks"></a>Açıklamalar  
 İçin önceden tanımlanmış değer türleri, eşitsizlik işleci (`!=`) işlenenleri Aksi durumda farklı, false değerleri, true değerini döndürür. Başvuru türleri dışında `string`, `!=` iki işlenenleri farklı nesnelere atıfta, true değerini döndürür. İçin `string` türü, `!=` dize değerlerini karşılaştırır.  
  
 Kullanıcı tanımlı bir değer türleri aşırı yükleme `!=` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)). Bu nedenle ancak varsayılan olarak kullanıcı tanımlı başvuru türleri için `!=` hem önceden tanımlanmış ve kullanıcı tanımlı referans türleri için yukarıda açıklandığı gibi davranır. Varsa `!=` aşırı yüklendi [ == ](../../../csharp/language-reference/operators/equality-comparison-operator.md) da aşırı yüklenmiş gerekir. Tam sayı türleri üzerinde işlemler genellikle numaralandırma üzerinde izin verilir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#33](../../../csharp/language-reference/operators/codesnippet/CSharp/not-equal-operator_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# İşleçleri](../../../csharp/language-reference/operators/index.md)
