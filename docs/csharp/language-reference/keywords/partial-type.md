---
title: Kısmi türü (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
ms.openlocfilehash: 365d00d2c53d3efe1cd4330bdd3ec48740a49c53
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43674037"
---
# <a name="partial-type-c-reference"></a><span data-ttu-id="e5ec3-102">Kısmi türü (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e5ec3-102">partial type (C# Reference)</span></span>

<span data-ttu-id="e5ec3-103">Kısmi tür tanımlarını bir sınıf, yapı veya arabirim tanımı için birden fazla dosyaya bölünmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="e5ec3-103">Partial type definitions allow for the definition of a class, struct, or interface to be split into multiple files.</span></span>

<span data-ttu-id="e5ec3-104">İçinde *File1.cs*:</span><span class="sxs-lookup"><span data-stu-id="e5ec3-104">In *File1.cs*:</span></span>

[!code-csharp[csrefKeywordsContextual#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#3)]  

<span data-ttu-id="e5ec3-105">İçinde *File2.cs* bildirimi:</span><span class="sxs-lookup"><span data-stu-id="e5ec3-105">In *File2.cs* the declaration:</span></span>

[!code-csharp[csrefKeywordsContextual#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#4)]  

## <a name="remarks"></a><span data-ttu-id="e5ec3-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e5ec3-106">Remarks</span></span>

<span data-ttu-id="e5ec3-107">Büyük projeler veya sağladığı gibi otomatik olarak oluşturulan kod ile çalışırken, bir sınıf bölme, yapı veya arabirim türü çeşitli dosyalar üzerinde yararlı olabilir [Windows Form Tasarımcısı](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="e5ec3-107">Splitting a class, struct or interface type over several files can be useful when you are working with large projects, or with automatically generated code such as that provided by the [Windows Forms Designer](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span></span> <span data-ttu-id="e5ec3-108">Kısmi bir tür içerebilir bir [kısmi yöntem](partial-method.md).</span><span class="sxs-lookup"><span data-stu-id="e5ec3-108">A partial type may contain a [partial method](partial-method.md).</span></span> <span data-ttu-id="e5ec3-109">Daha fazla bilgi için [kısmi sınıflar ve yöntemler](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="e5ec3-109">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e5ec3-110">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="e5ec3-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="e5ec3-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5ec3-111">See also</span></span>

- [<span data-ttu-id="e5ec3-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="e5ec3-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e5ec3-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e5ec3-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e5ec3-114">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="e5ec3-114">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="e5ec3-115">Genel Türlere Giriş</span><span class="sxs-lookup"><span data-stu-id="e5ec3-115">Introduction to Generics</span></span>](../../programming-guide/generics/introduction-to-generics.md)