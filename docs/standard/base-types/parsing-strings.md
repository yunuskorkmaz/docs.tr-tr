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
ms.openlocfilehash: ab446a8f868cabdeff73d1b72e1399b7c2beb1e1
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277420"
---
# <a name="parsing-strings-in-net"></a><span data-ttu-id="56acd-102">.NET 'te dizeleri ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="56acd-102">Parsing Strings in .NET</span></span>
<span data-ttu-id="56acd-103">Bir ayrıştırma işlemi, .NET temel türünü temsil eden bir dizeyi bu temel türe dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="56acd-103">A parsing operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="56acd-104">Örneğin, bir dizeyi bir kayan noktalı sayıya veya tarih ve saat değerine dönüştürmek için bir ayrıştırma işlemi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="56acd-104">For example, a parsing operation is used to convert a string to a floating-point number or to a date and time value.</span></span> <span data-ttu-id="56acd-105">Bir ayrıştırma işlemi gerçekleştirmek için en yaygın olarak kullanılan yöntem `Parse` yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="56acd-105">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="56acd-106">Ayrıştırma, biçimlendirme işlemi (bir temel türü dize gösterimine dönüştürmeyi içerir) olduğundan, aynı kuralların ve kuralların birçoğu da geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="56acd-106">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="56acd-107">Biçimlendirme <xref:System.IFormatProvider> , kültüre duyarlı biçimlendirme bilgilerini sağlamak için arabirimini uygulayan bir nesne kullandığından, ayrıştırma aynı zamanda <xref:System.IFormatProvider> bir dize gösterimini nasıl yorumlayacağını belirleme arabirimini uygulayan bir nesne kullanır.</span><span class="sxs-lookup"><span data-stu-id="56acd-107">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="56acd-108">Daha fazla bilgi için bkz. [Biçimlendirme Türleri](formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="56acd-108">For more information, see [Formatting Types](formatting-types.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="56acd-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="56acd-109">In This Section</span></span>  
 [<span data-ttu-id="56acd-110">Sayısal Dizeleri Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="56acd-110">Parsing Numeric Strings</span></span>](parsing-numeric.md)  
 <span data-ttu-id="56acd-111">Dizelerin .NET sayısal türlerine nasıl dönüştürüleceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="56acd-111">Describes how to convert strings into .NET numeric types.</span></span>  
  
 [<span data-ttu-id="56acd-112">Tarih ve Saat Dizelerini Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="56acd-112">Parsing Date and Time Strings</span></span>](parsing-datetime.md)  
 <span data-ttu-id="56acd-113">Dizelerin .NET **DateTime** türlerine nasıl dönüştürüleceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="56acd-113">Describes how to convert strings into .NET **DateTime** types.</span></span>  
  
 [<span data-ttu-id="56acd-114">Diğer Dizeleri Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="56acd-114">Parsing Other Strings</span></span>](parsing-other.md)  
 <span data-ttu-id="56acd-115">Dizelerin **char**, **Boolean**ve **enum** türlerine nasıl dönüştürüleceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="56acd-115">Describes how to convert strings into **Char**, **Boolean**, and **Enum** types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="56acd-116">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="56acd-116">Related Sections</span></span>  
 [<span data-ttu-id="56acd-117">Biçimlendirme Türleri</span><span class="sxs-lookup"><span data-stu-id="56acd-117">Formatting Types</span></span>](formatting-types.md)  
 <span data-ttu-id="56acd-118">Biçim belirticileri ve biçim sağlayıcıları gibi temel biçimlendirme kavramlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="56acd-118">Describes basic formatting concepts like format specifiers and format providers.</span></span>  
  
 [<span data-ttu-id="56acd-119">.NET 'te tür dönüştürme</span><span class="sxs-lookup"><span data-stu-id="56acd-119">Type Conversion in .NET</span></span>](type-conversion.md)  
 <span data-ttu-id="56acd-120">Türlerin nasıl dönüştürüleceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="56acd-120">Describes how to convert types.</span></span>
