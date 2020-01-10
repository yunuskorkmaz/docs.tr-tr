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
# <a name="partial-type-c-reference"></a><span data-ttu-id="1d29b-102">Kısmi tür (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="1d29b-102">partial type (C# Reference)</span></span>

<span data-ttu-id="1d29b-103">Kısmi tür tanımları bir sınıf, yapı veya arabirimin tanımının birden fazla dosyaya bölünmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="1d29b-103">Partial type definitions allow for the definition of a class, struct, or interface to be split into multiple files.</span></span>

<span data-ttu-id="1d29b-104">*File1.cs*içinde:</span><span class="sxs-lookup"><span data-stu-id="1d29b-104">In *File1.cs*:</span></span>

[!code-csharp[csrefKeywordsContextual#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#3)]  

<span data-ttu-id="1d29b-105">*File2.cs* 'de bildirimi:</span><span class="sxs-lookup"><span data-stu-id="1d29b-105">In *File2.cs* the declaration:</span></span>

[!code-csharp[csrefKeywordsContextual#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#4)]  

## <a name="remarks"></a><span data-ttu-id="1d29b-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1d29b-106">Remarks</span></span>

<span data-ttu-id="1d29b-107">Bir sınıf, yapı veya arabirim türünün birkaç dosya üzerinde bölünmesi, büyük projelerle çalışırken veya [Windows Form Tasarımcısı](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)tarafından sağlandığı gibi otomatik olarak oluşturulan kodla yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="1d29b-107">Splitting a class, struct or interface type over several files can be useful when you are working with large projects, or with automatically generated code such as that provided by the [Windows Forms Designer](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span></span> <span data-ttu-id="1d29b-108">Kısmi bir tür, kısmi bir [Yöntem](partial-method.md)içerebilir.</span><span class="sxs-lookup"><span data-stu-id="1d29b-108">A partial type may contain a [partial method](partial-method.md).</span></span> <span data-ttu-id="1d29b-109">Daha fazla bilgi için bkz. [kısmi sınıflar ve Yöntemler](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="1d29b-109">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1d29b-110">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="1d29b-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="1d29b-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d29b-111">See also</span></span>

- [<span data-ttu-id="1d29b-112">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="1d29b-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1d29b-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1d29b-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1d29b-114">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="1d29b-114">Modifiers</span></span>](index.md)
- [<span data-ttu-id="1d29b-115">Genel Türlere Giriş</span><span class="sxs-lookup"><span data-stu-id="1d29b-115">Introduction to Generics</span></span>](../../programming-guide/generics/index.md)
