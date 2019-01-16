---
title: '* Operator - C# başvurusu'
ms.custom: seodec18
ms.date: 04/04/2018
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
ms.openlocfilehash: f4490c4632d9344eb879ea55c20787b838781d91
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333739"
---
# <a name="-operator-c-reference"></a>* işleci (C# Başvurusu)

Çarpma işleci (`*`), işlenenlerinin çarpımını hesaplar. Tüm sayısal türler, çarpma işleçleri önceden tanımlanmış.

`*` Okuma ve yazma için bir işaretçi sağlar başvuru işleci de görür.

## <a name="remarks"></a>Açıklamalar

`*` İşleci işaretçi türleri bildirme ve işaretçi başvuru kaldırma için de kullanılır. Bu işleci yalnızca güvenli bağlamlarda kullanımı tarafından gösterilen kullanılabilir [güvenli olmayan](../keywords/unsafe.md) anahtar sözcüğü ve gerektiren [/ unsafe](../compiler-options/unsafe-compiler-option.md) derleyici seçeneği.  Başvuru işleci yöneltme işleci de denir.

Kullanıcı tanımlı türler ikili aşırı yükleme `*` işleci (bkz [işleci](../keywords/operator.md)). İkili İşleç aşırı karşılık gelen atama işleci, varsa, aynı zamanda örtük olarak aşırı yüklenmiş olur.

## <a name="example"></a>Örnek

[!code-csharp-interactive[csRefOperators#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#50)]

## <a name="example"></a>Örnek

[!code-csharp[csRefOperators#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#51)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [Güvenli Olmayan Kod ve İşaretçiler](../../programming-guide/unsafe-code-pointers/index.md)
- [C# İşleçleri](index.md)