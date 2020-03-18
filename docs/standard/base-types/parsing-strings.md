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
ms.openlocfilehash: e4bf14981e538d95aebac3b0f36d38b61747989f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73084309"
---
# <a name="parsing-strings-in-net"></a><span data-ttu-id="ecdc2-102">.NET'te Dizeleri Ayrışdırma</span><span class="sxs-lookup"><span data-stu-id="ecdc2-102">Parsing Strings in .NET</span></span>
<span data-ttu-id="ecdc2-103">Ayrıştma işlemi, .NET taban türünü temsil eden bir dizeyi bu taban türüne dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="ecdc2-103">A parsing operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="ecdc2-104">Örneğin, bir ayrıştırma işlemi, bir dizeyi kayan nokta numarasına veya tarih ve saat değerine dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ecdc2-104">For example, a parsing operation is used to convert a string to a floating-point number or to a date and time value.</span></span> <span data-ttu-id="ecdc2-105">Ayrıştırma işlemini gerçekleştirmek için en sık `Parse` kullanılan yöntem yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="ecdc2-105">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="ecdc2-106">Ayrıştırma biçimlendirmenin ters işlemi olduğundan (bir taban türünü dize gösterimine dönüştürmeyi içerir), aynı kural ve kuralların çoğu geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ecdc2-106">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="ecdc2-107">Biçimlendirme, kültüre duyarlı biçimlendirme <xref:System.IFormatProvider> bilgileri sağlamak için arabirimi uygulayan bir nesne kullandığı gibi, <xref:System.IFormatProvider> ayrıştırma da dize gösterimini nasıl yorumlayacaklarını belirlemek için arabirimi uygulayan bir nesne kullanır.</span><span class="sxs-lookup"><span data-stu-id="ecdc2-107">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="ecdc2-108">Daha fazla bilgi için bkz. [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="ecdc2-108">For more information, see [Formatting Types](../../../docs/standard/base-types/formatting-types.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ecdc2-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ecdc2-109">In This Section</span></span>  
 [<span data-ttu-id="ecdc2-110">Sayısal Dizeleri Ayrıştma</span><span class="sxs-lookup"><span data-stu-id="ecdc2-110">Parsing Numeric Strings</span></span>](../../../docs/standard/base-types/parsing-numeric.md)  
 <span data-ttu-id="ecdc2-111">Dizeleri .NET sayısal türlerine nasıl dönüştüreceklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ecdc2-111">Describes how to convert strings into .NET numeric types.</span></span>  
  
 [<span data-ttu-id="ecdc2-112">Tarih ve Saat Dizelerini Ayrışdırma</span><span class="sxs-lookup"><span data-stu-id="ecdc2-112">Parsing Date and Time Strings</span></span>](../../../docs/standard/base-types/parsing-datetime.md)  
 <span data-ttu-id="ecdc2-113">Dizeleri .NET **DateTime** türlerine nasıl dönüştüreceklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ecdc2-113">Describes how to convert strings into .NET **DateTime** types.</span></span>  
  
 [<span data-ttu-id="ecdc2-114">Diğer Dizeleri Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="ecdc2-114">Parsing Other Strings</span></span>](../../../docs/standard/base-types/parsing-other.md)  
 <span data-ttu-id="ecdc2-115">Dizeleri **Char,** **Boolean**ve **Enum** türlerine nasıl dönüştüreceklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ecdc2-115">Describes how to convert strings into **Char**, **Boolean**, and **Enum** types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ecdc2-116">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="ecdc2-116">Related Sections</span></span>  
 [<span data-ttu-id="ecdc2-117">Biçimlendirme Türleri</span><span class="sxs-lookup"><span data-stu-id="ecdc2-117">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="ecdc2-118">Biçim belirteciler ve biçim sağlayıcıları gibi temel biçimlendirme kavramlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ecdc2-118">Describes basic formatting concepts like format specifiers and format providers.</span></span>  
  
 [<span data-ttu-id="ecdc2-119">.NET içinde Tür Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="ecdc2-119">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="ecdc2-120">Türlerin nasıl dönüştürülür şekilde dönüştürülür açıklanır.</span><span class="sxs-lookup"><span data-stu-id="ecdc2-120">Describes how to convert types.</span></span>  
  
 [<span data-ttu-id="ecdc2-121">Temel Türler</span><span class="sxs-lookup"><span data-stu-id="ecdc2-121">Base Types</span></span>](../../../docs/standard/base-types/index.md)  
 <span data-ttu-id="ecdc2-122">.NET taban türlerinde gerçekleştirebileceğiniz yaygın işlemleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="ecdc2-122">Describes common operations that you can perform on .NET base types.</span></span>
