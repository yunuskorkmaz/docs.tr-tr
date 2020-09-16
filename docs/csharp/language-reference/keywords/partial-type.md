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
ms.openlocfilehash: 0445ac33473c7e2d1916705893b22ba21bb981ff
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90536852"
---
# <a name="partial-type-c-reference"></a><span data-ttu-id="9224a-103">Kısmi tür (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="9224a-103">partial type (C# Reference)</span></span>

<span data-ttu-id="9224a-104">Kısmi tür tanımları bir sınıf, yapı veya arabirimin tanımının birden fazla dosyaya bölünmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="9224a-104">Partial type definitions allow for the definition of a class, struct, or interface to be split into multiple files.</span></span>

<span data-ttu-id="9224a-105">*File1.cs*içinde:</span><span class="sxs-lookup"><span data-stu-id="9224a-105">In *File1.cs*:</span></span>

[!code-csharp[csrefKeywordsContextual#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#3)]  

<span data-ttu-id="9224a-106">*File2.cs* 'de bildirimi:</span><span class="sxs-lookup"><span data-stu-id="9224a-106">In *File2.cs* the declaration:</span></span>

[!code-csharp[csrefKeywordsContextual#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#4)]  

## <a name="remarks"></a><span data-ttu-id="9224a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9224a-107">Remarks</span></span>

<span data-ttu-id="9224a-108">Bir sınıf, yapı veya arabirim türünün birkaç dosya üzerinde bölünmesi, büyük projelerle çalışırken veya [Windows Form Tasarımcısı](/dotnet/desktop/winforms/controls/developing-windows-forms-controls-at-design-time)tarafından sağlandığı gibi otomatik olarak oluşturulan kodla yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="9224a-108">Splitting a class, struct or interface type over several files can be useful when you are working with large projects, or with automatically generated code such as that provided by the [Windows Forms Designer](/dotnet/desktop/winforms/controls/developing-windows-forms-controls-at-design-time).</span></span> <span data-ttu-id="9224a-109">Kısmi bir tür, kısmi bir [Yöntem](partial-method.md)içerebilir.</span><span class="sxs-lookup"><span data-stu-id="9224a-109">A partial type may contain a [partial method](partial-method.md).</span></span> <span data-ttu-id="9224a-110">Daha fazla bilgi için bkz. [kısmi sınıflar ve Yöntemler](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="9224a-110">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9224a-111">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="9224a-111">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="9224a-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9224a-112">See also</span></span>

- [<span data-ttu-id="9224a-113">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="9224a-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9224a-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9224a-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9224a-115">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="9224a-115">Modifiers</span></span>](index.md)
- [<span data-ttu-id="9224a-116">Genel Türlere Giriş</span><span class="sxs-lookup"><span data-stu-id="9224a-116">Introduction to Generics</span></span>](../../programming-guide/generics/index.md)
