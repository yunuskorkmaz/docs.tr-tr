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
# <a name="partial-type-c-reference"></a><span data-ttu-id="3fc92-102">kısmi tip (C# Reference)</span><span class="sxs-lookup"><span data-stu-id="3fc92-102">partial type (C# Reference)</span></span>

<span data-ttu-id="3fc92-103">Kısmi tür tanımları, bir sınıfın, yapının veya arabirimin tanımının birden çok dosyaya bölünmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3fc92-103">Partial type definitions allow for the definition of a class, struct, or interface to be split into multiple files.</span></span>

<span data-ttu-id="3fc92-104">*File1.cs:*</span><span class="sxs-lookup"><span data-stu-id="3fc92-104">In *File1.cs*:</span></span>

[!code-csharp[csrefKeywordsContextual#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#3)]  

<span data-ttu-id="3fc92-105">File2.cs *File2.cs* bildirgede:</span><span class="sxs-lookup"><span data-stu-id="3fc92-105">In *File2.cs* the declaration:</span></span>

[!code-csharp[csrefKeywordsContextual#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#4)]  

## <a name="remarks"></a><span data-ttu-id="3fc92-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3fc92-106">Remarks</span></span>

<span data-ttu-id="3fc92-107">Bir sınıf, yapı veya arabirim türünü birkaç dosya üzerinde bölmek, büyük projelerle çalışırken veya Windows Forms [Designer](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)tarafından sağlanan gibi otomatik olarak oluşturulan kodla yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="3fc92-107">Splitting a class, struct or interface type over several files can be useful when you are working with large projects, or with automatically generated code such as that provided by the [Windows Forms Designer](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span></span> <span data-ttu-id="3fc92-108">Kısmi bir tür [kısmi](partial-method.md)bir yöntem içerebilir.</span><span class="sxs-lookup"><span data-stu-id="3fc92-108">A partial type may contain a [partial method](partial-method.md).</span></span> <span data-ttu-id="3fc92-109">Daha fazla bilgi için Kısmi [Sınıflar ve Yöntemler'e](../../programming-guide/classes-and-structs/partial-classes-and-methods.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="3fc92-109">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3fc92-110">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="3fc92-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="3fc92-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3fc92-111">See also</span></span>

- [<span data-ttu-id="3fc92-112">C# Referans</span><span class="sxs-lookup"><span data-stu-id="3fc92-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3fc92-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3fc92-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3fc92-114">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="3fc92-114">Modifiers</span></span>](index.md)
- [<span data-ttu-id="3fc92-115">Genel Türlere Giriş</span><span class="sxs-lookup"><span data-stu-id="3fc92-115">Introduction to Generics</span></span>](../../programming-guide/generics/index.md)
