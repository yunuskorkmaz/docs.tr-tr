---
title: kısmi tip - C# Referans
ms.date: 07/20/2015
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
ms.openlocfilehash: 551145b9cdf5fa24f3ae365665e8ff06cf5e9307
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715217"
---
# <a name="partial-type-c-reference"></a>kısmi tip (C# Reference)

Kısmi tür tanımları, bir sınıfın, yapının veya arabirimin tanımının birden çok dosyaya bölünmesine olanak tanır.

*File1.cs:*

[!code-csharp[csrefKeywordsContextual#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#3)]  

File2.cs *File2.cs* bildirgede:

[!code-csharp[csrefKeywordsContextual#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#4)]  

## <a name="remarks"></a>Açıklamalar

Bir sınıf, yapı veya arabirim türünü birkaç dosya üzerinde bölmek, büyük projelerle çalışırken veya Windows Forms [Designer](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)tarafından sağlanan gibi otomatik olarak oluşturulan kodla yararlı olabilir. Kısmi bir tür [kısmi](partial-method.md)bir yöntem içerebilir. Daha fazla bilgi için Kısmi [Sınıflar ve Yöntemler'e](../../programming-guide/classes-and-structs/partial-classes-and-methods.md)bakın.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [Değiştiriciler](index.md)
- [Genel Türlere Giriş](../../programming-guide/generics/index.md)
