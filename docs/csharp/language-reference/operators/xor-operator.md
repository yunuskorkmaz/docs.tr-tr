---
title: ^ İşleci (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- ^_CSharpKeyword
helpviewer_keywords:
- ^ operator [C#]
- bitwise exclusive OR operator [C#]
ms.assetid: b09bc815-570f-4db6-a637-5b4ed99d014a
ms.openlocfilehash: 5cc3cd2cfc932646e5b2dd6ec034555b07582379
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33271256"
---
# <a name="-operator-c-reference"></a>^ İşleci (C# Başvurusu)
İkili `^` işleçleri tam sayı türleri için önceden tanımlanmış ve `bool`. Tam sayı türleri için `^` bitwise hesaplar işlenenleri hariç veya. İçin `bool` işlenenler, `^` mantıksal özel hesaplar- veya kendi işlenenleri; diğer bir deyişle, sonuç `true` işlenenleri tam olarak birine varsa ve yalnızca ise `true`.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanıcı tanımlı türler aşırı yükleme `^` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)). Tam sayı türleri üzerinde işlemler genellikle numaralandırma üzerinde izin verilir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#30](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-operator_1.cs)]  
  
 Hesaplaması `0xf8 ^ 0x3f` önceki örnekte bit gerçekleştirir hariç veya onaltılık değerler F8 ve 3F karşılık gelen aşağıdaki iki ikili değerleri:  
  
 `1111 1000`  
  
 `0011 1111`  
  
 Dışlayan OR sonucu `1100 0111`, onaltılık C7 değil.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# İşleçleri](../../../csharp/language-reference/operators/index.md)
