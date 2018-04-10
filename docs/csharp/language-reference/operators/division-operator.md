---
title: / İşleci (C# Başvurusu)
ms.date: 04/04/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /_CSharpKeyword
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5b17d122e3e3f75012e084903b6f8975fb53d46c
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="-operator-c-reference"></a>/ İşleci (C# Başvurusu)
Bölme işleci (`/`), ilk işlenen ikinci işlenen tarafından böler. Tüm sayısal türler bölme işleçlerini önceden.
  
## <a name="remarks"></a>Açıklamalar  
 Kullanıcı tanımlı türler aşırı yükleme `/` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)). Bir aşırı yüklemesini `/` işleci örtük olarak overloads [/ = işleci](division-assignment-operator.md).  
  
 İki tamsayının böldüğünüzde sonucu her zaman bir tamsayıdır. Örneğin, 7 sonucunu / 3: 2. Floored bölme olarak karıştırılmamalıdır budur `/` sıfıra doğru yuvarlar işleci: -7 / 3 -2.  
  
 Bir sayının bir rasyonel sayı olarak almak için kullanın `float`, `double`, veya `decimal` türleri. Arasında dönüştürme için birçok yolu vardır [yerleşik sayısal türleri](../../../csharp/language-reference/keywords/reference-tables-for-types.md).  
  
 Kalan belirlemek için [kalan işleci](../../../csharp/language-reference/operators/remainder-operator.md) `%`.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# İşleçleri](../../../csharp/language-reference/operators/index.md)
