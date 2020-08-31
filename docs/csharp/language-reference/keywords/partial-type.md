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
# <a name="partial-type-c-reference"></a><span data-ttu-id="a1ab7-103">Kısmi tür (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a1ab7-103">partial type (C# Reference)</span></span>

<span data-ttu-id="a1ab7-104">Kısmi tür tanımları bir sınıf, yapı veya arabirimin tanımının birden fazla dosyaya bölünmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="a1ab7-104">Partial type definitions allow for the definition of a class, struct, or interface to be split into multiple files.</span></span>

<span data-ttu-id="a1ab7-105">*File1.cs*içinde:</span><span class="sxs-lookup"><span data-stu-id="a1ab7-105">In *File1.cs*:</span></span>

[!code-csharp[csrefKeywordsContextual#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#3)]  

<span data-ttu-id="a1ab7-106">*File2.cs* 'de bildirimi:</span><span class="sxs-lookup"><span data-stu-id="a1ab7-106">In *File2.cs* the declaration:</span></span>

[!code-csharp[csrefKeywordsContextual#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#4)]  

## <a name="remarks"></a><span data-ttu-id="a1ab7-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a1ab7-107">Remarks</span></span>

<span data-ttu-id="a1ab7-108">Bir sınıf, yapı veya arabirim türünün birkaç dosya üzerinde bölünmesi, büyük projelerle çalışırken veya [Windows Form Tasarımcısı](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)tarafından sağlandığı gibi otomatik olarak oluşturulan kodla yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="a1ab7-108">Splitting a class, struct or interface type over several files can be useful when you are working with large projects, or with automatically generated code such as that provided by the [Windows Forms Designer](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span></span> <span data-ttu-id="a1ab7-109">Kısmi bir tür, kısmi bir [Yöntem](partial-method.md)içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a1ab7-109">A partial type may contain a [partial method](partial-method.md).</span></span> <span data-ttu-id="a1ab7-110">Daha fazla bilgi için bkz. [kısmi sınıflar ve Yöntemler](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="a1ab7-110">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a1ab7-111">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="a1ab7-111">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="a1ab7-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1ab7-112">See also</span></span>

- [<span data-ttu-id="a1ab7-113">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="a1ab7-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a1ab7-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a1ab7-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a1ab7-115">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="a1ab7-115">Modifiers</span></span>](index.md)
- [<span data-ttu-id="a1ab7-116">Genel Türlere Giriş</span><span class="sxs-lookup"><span data-stu-id="a1ab7-116">Introduction to Generics</span></span>](../../programming-guide/generics/index.md)
