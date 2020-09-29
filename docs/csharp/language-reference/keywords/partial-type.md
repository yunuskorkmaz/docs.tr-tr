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
ms.openlocfilehash: 4e73b34390143a2ac9b839e1da79b7894232c4b4
ms.sourcegitcommit: b4a46f6d7ebf44c0035627d00924164bcae2db30
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91437882"
---
# <a name="partial-type-c-reference"></a>Kısmi tür (C# Başvurusu)

Kısmi tür tanımları bir sınıf, yapı, arabirim veya kaydın tanımının birden çok dosyaya bölünmesine izin verir.

*File1.cs*içinde:

[!code-csharp[csrefKeywordsContextual#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#3)]  

*File2.cs* 'de bildirimi:

[!code-csharp[csrefKeywordsContextual#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#4)]  

## <a name="remarks"></a>Açıklamalar

Bir sınıf, yapı veya arabirim türünün birkaç dosya üzerinde bölünmesi, büyük projelerle çalışırken veya [Windows Form Tasarımcısı](/dotnet/desktop/winforms/controls/developing-windows-forms-controls-at-design-time)tarafından sağlandığı gibi otomatik olarak oluşturulan kodla yararlı olabilir. Kısmi bir tür, kısmi bir [Yöntem](partial-method.md)içerebilir. Daha fazla bilgi için bkz. [kısmi sınıflar ve Yöntemler](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [Değiştiriciler](index.md)
- [Genel Türlere Giriş](../../programming-guide/generics/index.md)
