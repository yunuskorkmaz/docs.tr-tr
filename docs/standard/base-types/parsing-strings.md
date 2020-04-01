---
title: .NET'te Dizeleri Ayrışdırma
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
ms.openlocfilehash: 717022e5d2e292c1624e6155bd7571e4daa997b9
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523811"
---
# <a name="parsing-strings-in-net"></a><span data-ttu-id="b4e67-102">.NET'te Dizeleri Ayrışdırma</span><span class="sxs-lookup"><span data-stu-id="b4e67-102">Parsing Strings in .NET</span></span>
<span data-ttu-id="b4e67-103">Ayrıştma işlemi, .NET taban türünü temsil eden bir dizeyi bu taban türüne dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="b4e67-103">A parsing operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="b4e67-104">Örneğin, bir ayrıştırma işlemi, bir dizeyi kayan nokta numarasına veya tarih ve saat değerine dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b4e67-104">For example, a parsing operation is used to convert a string to a floating-point number or to a date and time value.</span></span> <span data-ttu-id="b4e67-105">Ayrıştırma işlemini gerçekleştirmek için en sık `Parse` kullanılan yöntem yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="b4e67-105">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="b4e67-106">Ayrıştırma biçimlendirmenin ters işlemi olduğundan (bir taban türünü dize gösterimine dönüştürmeyi içerir), aynı kural ve kuralların çoğu geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b4e67-106">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="b4e67-107">Biçimlendirme, kültüre duyarlı biçimlendirme <xref:System.IFormatProvider> bilgileri sağlamak için arabirimi uygulayan bir nesne kullandığı gibi, <xref:System.IFormatProvider> ayrıştırma da dize gösterimini nasıl yorumlayacaklarını belirlemek için arabirimi uygulayan bir nesne kullanır.</span><span class="sxs-lookup"><span data-stu-id="b4e67-107">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="b4e67-108">Daha fazla bilgi için bkz. [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="b4e67-108">For more information, see [Formatting Types](../../../docs/standard/base-types/formatting-types.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b4e67-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b4e67-109">In This Section</span></span>  
 [<span data-ttu-id="b4e67-110">Sayısal Dizeleri Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="b4e67-110">Parsing Numeric Strings</span></span>](../../../docs/standard/base-types/parsing-numeric.md)  
 <span data-ttu-id="b4e67-111">Dizeleri .NET sayısal türlerine nasıl dönüştüreceklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b4e67-111">Describes how to convert strings into .NET numeric types.</span></span>  
  
 [<span data-ttu-id="b4e67-112">Tarih ve Saat Dizelerini Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="b4e67-112">Parsing Date and Time Strings</span></span>](../../../docs/standard/base-types/parsing-datetime.md)  
 <span data-ttu-id="b4e67-113">Dizeleri .NET **DateTime** türlerine nasıl dönüştüreceklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b4e67-113">Describes how to convert strings into .NET **DateTime** types.</span></span>  
  
 [<span data-ttu-id="b4e67-114">Diğer Dizeleri Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="b4e67-114">Parsing Other Strings</span></span>](../../../docs/standard/base-types/parsing-other.md)  
 <span data-ttu-id="b4e67-115">Dizeleri **Char,** **Boolean**ve **Enum** türlerine nasıl dönüştüreceklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b4e67-115">Describes how to convert strings into **Char**, **Boolean**, and **Enum** types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b4e67-116">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="b4e67-116">Related Sections</span></span>  
 [<span data-ttu-id="b4e67-117">Biçimlendirme Türleri</span><span class="sxs-lookup"><span data-stu-id="b4e67-117">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="b4e67-118">Biçim belirteciler ve biçim sağlayıcıları gibi temel biçimlendirme kavramlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="b4e67-118">Describes basic formatting concepts like format specifiers and format providers.</span></span>  
  
 [<span data-ttu-id="b4e67-119">.NET içinde Tür Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="b4e67-119">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="b4e67-120">Türlerin nasıl dönüştürülür şekilde dönüştürülür açıklanır.</span><span class="sxs-lookup"><span data-stu-id="b4e67-120">Describes how to convert types.</span></span>
