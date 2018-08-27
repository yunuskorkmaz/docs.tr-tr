---
title: ^ İşleci (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- ^_CSharpKeyword
helpviewer_keywords:
- ^ operator [C#]
- bitwise exclusive OR operator [C#]
ms.assetid: b09bc815-570f-4db6-a637-5b4ed99d014a
ms.openlocfilehash: b1333f9d06e2804029550e6364a225558e096431
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925304"
---
# <a name="-operator-c-reference"></a>^ İşleci (C# Başvurusu)
İkili `^` işleçleri tamsayı türleri için önceden tanımlanmış ve `bool`. İntegral türleri için `^` hesaplar. bit düzeyinde dışlamalı OR işlenenleri. İçin `bool` işlenenini `^` mantıksal özel hesaplar- veya kendi işlenenler; diğer bir deyişle, sonuç `true` işlenenleri tam olarak biri olan ve yalnızca, `true`.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanıcı tanımlı türler aşırı yükleme `^` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)). Tamsayı türlerinde işlemler genellikle numaralandırma üzerinde izin verilir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#30](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-operator_1.cs)]  
  
 Hesaplama `0xf8 ^ 0x3f` önceki örnekte bir bit düzeyinde gerçekleştirir hariç veya F8 ve 3F onaltılık değerlerine karşılık gelen aşağıdaki iki ikili değerleri:  
  
 `1111 1000`  
  
 `0011 1111`  
  
 Özel veya sonucu `1100 0111`, onaltılık C7 olduğu.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# İşleçleri](../../../csharp/language-reference/operators/index.md)
