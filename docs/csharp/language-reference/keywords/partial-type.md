---
title: Kısmi tür- C# başvuru
ms.date: 07/20/2015
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
ms.openlocfilehash: 551145b9cdf5fa24f3ae365665e8ff06cf5e9307
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715217"
---
# <a name="partial-type-c-reference"></a>Kısmi tür (C# başvuru)

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

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [Değiştiriciler](index.md)
- [Genel Türlere Giriş](../../programming-guide/generics/index.md)
