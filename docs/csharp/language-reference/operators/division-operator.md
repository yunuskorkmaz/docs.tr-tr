---
title: / İşleci - C# başvurusu
ms.custom: seodec18
ms.date: 04/04/2018
f1_keywords:
- /_CSharpKeyword
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
ms.openlocfilehash: c77d9264baac05f2212db37fe50490516359e96e
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242327"
---
# <a name="-operator-c-reference"></a>/ İşleci (C# Başvurusu)
Bölme işleci (`/`) ilk işlenenin ikinci işleneni olarak böler. Tüm sayısal türlerin bölme işleçlerini önceden tanımlanmış.
  
## <a name="remarks"></a>Açıklamalar  
 Kullanıcı tanımlı türler aşırı yükleme `/` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)). Bir aşırı yüklemesini `/` işleci örtük aşırı [/ = işleci](division-assignment-operator.md).  
  
 İki tamsayının ayırdığınızda, sonucu her zaman bir tamsayıdır. Örneğin, 7 sonucunu / 3, 2. Floored bölme olarak karıştırılmamalıdır budur `/` işleci, sıfıra doğru yuvarlar: -7 / 3 -2.  
  
 Bir sayının rasyonel sayı olarak almak için kullanın `float`, `double`, veya `decimal` türleri. Arasında dönüştürmek için birçok yolu vardır [yerleşik sayısal türleri](../../../csharp/language-reference/keywords/reference-tables-for-types.md).  
  
 Kalan belirlemek için [kalan işleci](../../../csharp/language-reference/operators/remainder-operator.md) `%`.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# İşleçleri](../../../csharp/language-reference/operators/index.md)
