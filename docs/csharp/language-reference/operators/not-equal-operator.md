---
title: '!= İşleci (C# Başvurusu)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '!=_CSharpKeyword'
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b69d0b12734e690f0ba0209ccbbc7627ff92fe8a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# işleçleri](../../../csharp/language-reference/operators/index.md)
