---
title: Dizeleri türlere Dönüştür
description: .NET ' te dize ayrıştırmayı anlayın. Ayrıştırma, .NET temel türünü temsil eden bir dizeyi bu temel türe dönüştürür. Ayrıştırma, biçimlendirme için ters işlemdir.
ms.date: 03/30/2017
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
ms.openlocfilehash: a5c38c29a45a9ce6f8aed7205c5bd44bebb023c2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683737"
---
# <a name="parse-strings-in-net"></a><span data-ttu-id="b92eb-105">.NET 'teki dizeleri ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="b92eb-105">Parse strings in .NET</span></span>

<span data-ttu-id="b92eb-106">Bir *ayrıştırma* işlemi, .net temel türünü temsil eden bir dizeyi bu temel türe dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="b92eb-106">A *parsing* operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="b92eb-107">Örneğin, bir dizeyi bir kayan noktalı sayıya veya bir tarih ve saat değerine dönüştürmek için bir ayrıştırma işlemi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b92eb-107">For example, a parsing operation is used to convert a string to a floating-point number or to a date-and-time value.</span></span> <span data-ttu-id="b92eb-108">Bir ayrıştırma işlemi gerçekleştirmek için en yaygın olarak kullanılan yöntem `Parse` yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="b92eb-108">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="b92eb-109">Ayrıştırma, biçimlendirme işlemi (bir temel türü dize gösterimine dönüştürmeyi içerir) olduğundan, aynı kuralların ve kuralların birçoğu da geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b92eb-109">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="b92eb-110">Biçimlendirme <xref:System.IFormatProvider> , kültüre duyarlı biçimlendirme bilgilerini sağlamak için arabirimini uygulayan bir nesne kullandığından, ayrıştırma aynı zamanda <xref:System.IFormatProvider> bir dize gösterimini nasıl yorumlayacağını belirleme arabirimini uygulayan bir nesne kullanır.</span><span class="sxs-lookup"><span data-stu-id="b92eb-110">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="b92eb-111">Daha fazla bilgi için bkz. [Biçim türleri](formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="b92eb-111">For more information, see [Format types](formatting-types.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="b92eb-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b92eb-112">In This Section</span></span>

 <span data-ttu-id="b92eb-113">[Sayısal dizeleri ayrıştırma](parsing-numeric.md)</span><span class="sxs-lookup"><span data-stu-id="b92eb-113">[Parsing Numeric Strings](parsing-numeric.md)</span></span>\
 <span data-ttu-id="b92eb-114">Dizelerin .NET sayısal türlerine nasıl dönüştürüleceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b92eb-114">Describes how to convert strings into .NET numeric types.</span></span>

 <span data-ttu-id="b92eb-115">[Tarih ve saat dizelerini ayrıştırma](parsing-datetime.md)</span><span class="sxs-lookup"><span data-stu-id="b92eb-115">[Parsing Date and Time Strings](parsing-datetime.md)</span></span>\
 <span data-ttu-id="b92eb-116">Dizelerin .NET **DateTime** türlerine nasıl dönüştürüleceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b92eb-116">Describes how to convert strings into .NET **DateTime** types.</span></span>

 <span data-ttu-id="b92eb-117">[Diğer dizeleri ayrıştırma](parsing-other.md)</span><span class="sxs-lookup"><span data-stu-id="b92eb-117">[Parsing Other Strings](parsing-other.md)</span></span>\
 <span data-ttu-id="b92eb-118">Dizelerin **char**, **Boolean** ve **enum** türlerine nasıl dönüştürüleceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b92eb-118">Describes how to convert strings into **Char**, **Boolean**, and **Enum** types.</span></span>

## <a name="related-sections"></a><span data-ttu-id="b92eb-119">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="b92eb-119">Related Sections</span></span>

 <span data-ttu-id="b92eb-120">[Biçimlendirme türleri](formatting-types.md)</span><span class="sxs-lookup"><span data-stu-id="b92eb-120">[Formatting Types](formatting-types.md)</span></span>\
 <span data-ttu-id="b92eb-121">Biçim belirticileri ve biçim sağlayıcıları gibi temel biçimlendirme kavramlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="b92eb-121">Describes basic formatting concepts like format specifiers and format providers.</span></span>

 <span data-ttu-id="b92eb-122">[.NET 'te tür dönüştürme](type-conversion.md)</span><span class="sxs-lookup"><span data-stu-id="b92eb-122">[Type Conversion in .NET](type-conversion.md)</span></span>\
 <span data-ttu-id="b92eb-123">Türlerin nasıl dönüştürüleceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b92eb-123">Describes how to convert types.</span></span>
