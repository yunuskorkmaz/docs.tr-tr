---
title: .NET 'te dizeleri ayrıştırma
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
ms.openlocfilehash: 5e297c8f689fdabc268ee6e269a7969155befe7b
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769294"
---
# <a name="parsing-strings-in-net"></a><span data-ttu-id="a4895-105">.NET 'te dizeleri ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="a4895-105">Parsing Strings in .NET</span></span>
<span data-ttu-id="a4895-106">Bir ayrıştırma işlemi, .NET temel türünü temsil eden bir dizeyi bu temel türe dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="a4895-106">A parsing operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="a4895-107">Örneğin, bir dizeyi bir kayan noktalı sayıya veya tarih ve saat değerine dönüştürmek için bir ayrıştırma işlemi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4895-107">For example, a parsing operation is used to convert a string to a floating-point number or to a date and time value.</span></span> <span data-ttu-id="a4895-108">Bir ayrıştırma işlemi gerçekleştirmek için en yaygın olarak kullanılan yöntem `Parse` yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="a4895-108">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="a4895-109">Ayrıştırma, biçimlendirme işlemi (bir temel türü dize gösterimine dönüştürmeyi içerir) olduğundan, aynı kuralların ve kuralların birçoğu da geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a4895-109">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="a4895-110">Biçimlendirme <xref:System.IFormatProvider> , kültüre duyarlı biçimlendirme bilgilerini sağlamak için arabirimini uygulayan bir nesne kullandığından, ayrıştırma aynı zamanda <xref:System.IFormatProvider> bir dize gösterimini nasıl yorumlayacağını belirleme arabirimini uygulayan bir nesne kullanır.</span><span class="sxs-lookup"><span data-stu-id="a4895-110">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="a4895-111">Daha fazla bilgi için bkz. [Biçimlendirme Türleri](formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="a4895-111">For more information, see [Formatting Types](formatting-types.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a4895-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="a4895-112">In This Section</span></span>  
 [<span data-ttu-id="a4895-113">Sayısal Dizeleri Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="a4895-113">Parsing Numeric Strings</span></span>](parsing-numeric.md)  
 <span data-ttu-id="a4895-114">Dizelerin .NET sayısal türlerine nasıl dönüştürüleceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="a4895-114">Describes how to convert strings into .NET numeric types.</span></span>  
  
 [<span data-ttu-id="a4895-115">Tarih ve Saat Dizelerini Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="a4895-115">Parsing Date and Time Strings</span></span>](parsing-datetime.md)  
 <span data-ttu-id="a4895-116">Dizelerin .NET **DateTime** türlerine nasıl dönüştürüleceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="a4895-116">Describes how to convert strings into .NET **DateTime** types.</span></span>  
  
 [<span data-ttu-id="a4895-117">Diğer Dizeleri Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="a4895-117">Parsing Other Strings</span></span>](parsing-other.md)  
 <span data-ttu-id="a4895-118">Dizelerin **char**, **Boolean**ve **enum** türlerine nasıl dönüştürüleceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="a4895-118">Describes how to convert strings into **Char**, **Boolean**, and **Enum** types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a4895-119">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="a4895-119">Related Sections</span></span>  
 [<span data-ttu-id="a4895-120">Biçimlendirme Türleri</span><span class="sxs-lookup"><span data-stu-id="a4895-120">Formatting Types</span></span>](formatting-types.md)  
 <span data-ttu-id="a4895-121">Biçim belirticileri ve biçim sağlayıcıları gibi temel biçimlendirme kavramlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="a4895-121">Describes basic formatting concepts like format specifiers and format providers.</span></span>  
  
 [<span data-ttu-id="a4895-122">.NET 'te tür dönüştürme</span><span class="sxs-lookup"><span data-stu-id="a4895-122">Type Conversion in .NET</span></span>](type-conversion.md)  
 <span data-ttu-id="a4895-123">Türlerin nasıl dönüştürüleceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="a4895-123">Describes how to convert types.</span></span>
