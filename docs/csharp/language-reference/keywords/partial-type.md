---
description: Kısmi tür-C# başvurusu
title: Kısmi tür-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
ms.openlocfilehash: 8ae98805eea7231e3a15cb74e636313e796796a2
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89117993"
---
# <a name="partial-type-c-reference"></a>Kısmi tür (C# Başvurusu)

Kısmi tür tanımları bir sınıf, yapı veya arabirimin tanımının birden fazla dosyaya bölünmesine izin verir.

*File1.cs*içinde:

[!code-csharp[csrefKeywordsContextual#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#3)]  

*File2.cs* 'de bildirimi:

[!code-csharp[csrefKeywordsContextual#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#4)]  

## <a name="remarks"></a>Açıklamalar

Bir sınıf, yapı veya arabirim türünün birkaç dosya üzerinde bölünmesi, büyük projelerle çalışırken veya [Windows Form Tasarımcısı](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)tarafından sağlandığı gibi otomatik olarak oluşturulan kodla yararlı olabilir. Kısmi bir tür, kısmi bir [Yöntem](partial-method.md)içerebilir. Daha fazla bilgi için bkz. [kısmi sınıflar ve Yöntemler](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [Değiştiriciler](index.md)
- [Genel Türlere Giriş](../../programming-guide/generics/index.md)
