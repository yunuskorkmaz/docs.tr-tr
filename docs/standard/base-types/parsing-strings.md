---
title: .NET 'te dizeleri ayrıştırma
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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084309"
---
# <a name="parsing-strings-in-net"></a><span data-ttu-id="35b34-102">.NET 'te dizeleri ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="35b34-102">Parsing Strings in .NET</span></span>
<span data-ttu-id="35b34-103">Bir ayrıştırma işlemi, .NET temel türünü temsil eden bir dizeyi bu temel türe dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="35b34-103">A parsing operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="35b34-104">Örneğin, bir dizeyi bir kayan noktalı sayıya veya tarih ve saat değerine dönüştürmek için bir ayrıştırma işlemi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="35b34-104">For example, a parsing operation is used to convert a string to a floating-point number or to a date and time value.</span></span> <span data-ttu-id="35b34-105">Bir ayrıştırma işlemi gerçekleştirmek için en yaygın olarak kullanılan yöntem `Parse` yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="35b34-105">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="35b34-106">Ayrıştırma, biçimlendirme işlemi (bir temel türü dize gösterimine dönüştürmeyi içerir) olduğundan, aynı kuralların ve kuralların birçoğu da geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="35b34-106">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="35b34-107">Biçimlendirme, kültüre duyarlı biçimlendirme bilgilerini sağlamak için <xref:System.IFormatProvider> arabirimini uygulayan bir nesne kullandığından, ayrıştırma Ayrıca bir dize gösterimini nasıl yorumlayacağını anlamak için <xref:System.IFormatProvider> arabirimini uygulayan bir nesne kullanır.</span><span class="sxs-lookup"><span data-stu-id="35b34-107">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="35b34-108">Daha fazla bilgi için bkz. [biçimlendirme türleri](../../../docs/standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="35b34-108">For more information, see [Formatting Types](../../../docs/standard/base-types/formatting-types.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="35b34-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="35b34-109">In This Section</span></span>  
 [<span data-ttu-id="35b34-110">Sayısal Dizeleri Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="35b34-110">Parsing Numeric Strings</span></span>](../../../docs/standard/base-types/parsing-numeric.md)  
 <span data-ttu-id="35b34-111">Dizelerin .NET sayısal türlerine nasıl dönüştürüleceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="35b34-111">Describes how to convert strings into .NET numeric types.</span></span>  
  
 [<span data-ttu-id="35b34-112">Tarih ve Saat Dizelerini Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="35b34-112">Parsing Date and Time Strings</span></span>](../../../docs/standard/base-types/parsing-datetime.md)  
 <span data-ttu-id="35b34-113">Dizelerin .NET **DateTime** türlerine nasıl dönüştürüleceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="35b34-113">Describes how to convert strings into .NET **DateTime** types.</span></span>  
  
 [<span data-ttu-id="35b34-114">Diğer Dizeleri Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="35b34-114">Parsing Other Strings</span></span>](../../../docs/standard/base-types/parsing-other.md)  
 <span data-ttu-id="35b34-115">Dizelerin **char**, **Boolean**ve **enum** türlerine nasıl dönüştürüleceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="35b34-115">Describes how to convert strings into **Char**, **Boolean**, and **Enum** types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="35b34-116">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="35b34-116">Related Sections</span></span>  
 [<span data-ttu-id="35b34-117">Biçimlendirme Türleri</span><span class="sxs-lookup"><span data-stu-id="35b34-117">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="35b34-118">Biçim belirticileri ve biçim sağlayıcıları gibi temel biçimlendirme kavramlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="35b34-118">Describes basic formatting concepts like format specifiers and format providers.</span></span>  
  
 [<span data-ttu-id="35b34-119">.NET içinde Tür Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="35b34-119">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="35b34-120">Türlerin nasıl dönüştürüleceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="35b34-120">Describes how to convert types.</span></span>  
  
 [<span data-ttu-id="35b34-121">Temel Türler</span><span class="sxs-lookup"><span data-stu-id="35b34-121">Base Types</span></span>](../../../docs/standard/base-types/index.md)  
 <span data-ttu-id="35b34-122">.NET temel türlerinde gerçekleştirebileceğiniz yaygın işlemleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="35b34-122">Describes common operations that you can perform on .NET base types.</span></span>
