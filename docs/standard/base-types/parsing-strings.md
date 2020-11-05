---
title: Dizeleri türlere Dönüştür
description: .NET ' te dize ayrıştırmayı anlayın. Ayrıştırma, .NET temel türünü temsil eden bir dizeyi bu temel türe dönüştürür. Ayrıştırma, biçimlendirme için ters işlemdir.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
ms.openlocfilehash: 3d23fa9c7ecc3593f03f70dbd5ea7bda841e8f4f
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400859"
---
# <a name="parse-strings-in-net"></a><span data-ttu-id="57969-105">.NET 'teki dizeleri ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="57969-105">Parse strings in .NET</span></span>

<span data-ttu-id="57969-106">Bir *ayrıştırma* işlemi, .net temel türünü temsil eden bir dizeyi bu temel türe dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="57969-106">A *parsing* operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="57969-107">Örneğin, bir dizeyi bir kayan noktalı sayıya veya bir tarih ve saat değerine dönüştürmek için bir ayrıştırma işlemi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="57969-107">For example, a parsing operation is used to convert a string to a floating-point number or to a date-and-time value.</span></span> <span data-ttu-id="57969-108">Bir ayrıştırma işlemi gerçekleştirmek için en yaygın olarak kullanılan yöntem `Parse` yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="57969-108">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="57969-109">Ayrıştırma, biçimlendirme işlemi (bir temel türü dize gösterimine dönüştürmeyi içerir) olduğundan, aynı kuralların ve kuralların birçoğu da geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="57969-109">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="57969-110">Biçimlendirme <xref:System.IFormatProvider> , kültüre duyarlı biçimlendirme bilgilerini sağlamak için arabirimini uygulayan bir nesne kullandığından, ayrıştırma aynı zamanda <xref:System.IFormatProvider> bir dize gösterimini nasıl yorumlayacağını belirleme arabirimini uygulayan bir nesne kullanır.</span><span class="sxs-lookup"><span data-stu-id="57969-110">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="57969-111">Daha fazla bilgi için bkz. [Biçim türleri](formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="57969-111">For more information, see [Format types](formatting-types.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="57969-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="57969-112">In This Section</span></span>
 <span data-ttu-id="57969-113">[Sayısal dizeleri ayrıştırma](parsing-numeric.md)</span><span class="sxs-lookup"><span data-stu-id="57969-113">[Parsing Numeric Strings](parsing-numeric.md)</span></span>\
 <span data-ttu-id="57969-114">Dizelerin .NET sayısal türlerine nasıl dönüştürüleceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="57969-114">Describes how to convert strings into .NET numeric types.</span></span>

 <span data-ttu-id="57969-115">[Tarih ve saat dizelerini ayrıştırma](parsing-datetime.md)</span><span class="sxs-lookup"><span data-stu-id="57969-115">[Parsing Date and Time Strings](parsing-datetime.md)</span></span>\
 <span data-ttu-id="57969-116">Dizelerin .NET **DateTime** türlerine nasıl dönüştürüleceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="57969-116">Describes how to convert strings into .NET **DateTime** types.</span></span>

 <span data-ttu-id="57969-117">[Diğer dizeleri ayrıştırma](parsing-other.md)</span><span class="sxs-lookup"><span data-stu-id="57969-117">[Parsing Other Strings](parsing-other.md)</span></span>\
 <span data-ttu-id="57969-118">Dizelerin **char** , **Boolean** ve **enum** türlerine nasıl dönüştürüleceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="57969-118">Describes how to convert strings into **Char** , **Boolean** , and **Enum** types.</span></span>

## <a name="related-sections"></a><span data-ttu-id="57969-119">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="57969-119">Related Sections</span></span>
 <span data-ttu-id="57969-120">[Biçimlendirme türleri](formatting-types.md)</span><span class="sxs-lookup"><span data-stu-id="57969-120">[Formatting Types](formatting-types.md)</span></span>\
 <span data-ttu-id="57969-121">Biçim belirticileri ve biçim sağlayıcıları gibi temel biçimlendirme kavramlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="57969-121">Describes basic formatting concepts like format specifiers and format providers.</span></span>

 <span data-ttu-id="57969-122">[.NET 'te tür dönüştürme](type-conversion.md)</span><span class="sxs-lookup"><span data-stu-id="57969-122">[Type Conversion in .NET](type-conversion.md)</span></span>\
 <span data-ttu-id="57969-123">Türlerin nasıl dönüştürüleceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="57969-123">Describes how to convert types.</span></span>
