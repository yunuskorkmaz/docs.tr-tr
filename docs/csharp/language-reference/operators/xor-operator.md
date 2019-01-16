---
title: ^ işleci - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ^_CSharpKeyword
helpviewer_keywords:
- ^ operator [C#]
- bitwise exclusive OR operator [C#]
ms.assetid: b09bc815-570f-4db6-a637-5b4ed99d014a
ms.openlocfilehash: 152be2d81d1bf340b839d74f169d63d7260f7ca5
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333713"
---
# <a name="-operator-c-reference"></a>^ işleci (C# Başvurusu)

İkili `^` işleçleri tamsayı türleri için önceden tanımlanmış ve `bool`. İntegral türleri için `^` hesaplar. bit düzeyinde dışlamalı OR işlenenleri. İçin `bool` işlenenini `^` mantıksal özel hesaplar- veya kendi işlenenler; diğer bir deyişle, sonuç `true` işlenenleri tam olarak biri olan ve yalnızca, `true`.

## <a name="remarks"></a>Açıklamalar

Kullanıcı tanımlı türler aşırı yükleme `^` işleci (bkz [işleci](../keywords/operator.md)). Tamsayı türlerinde işlemler genellikle numaralandırma üzerinde izin verilir.

## <a name="example"></a>Örnek

[!code-csharp[csRefOperators#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#30)]

Hesaplama `0xf8 ^ 0x3f` önceki örnekte bir bit düzeyinde gerçekleştirir hariç veya F8 ve 3F onaltılık değerlerine karşılık gelen aşağıdaki iki ikili değerleri:

`1111 1000`

`0011 1111`

Özel veya sonucu `1100 0111`, onaltılık C7 olduğu.

## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C#işleçleri](index.md)
