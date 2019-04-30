---
title: . NET'te dizeleri ayrıştırma
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a6e0e7e69affd93320ec3f3d73e6254befaf6ae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766005"
---
# <a name="parsing-strings-in-net"></a><span data-ttu-id="207f2-102">. NET'te dizeleri ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="207f2-102">Parsing Strings in .NET</span></span>
<span data-ttu-id="207f2-103">Bir ayrıştırma işlemi, temel türü .NET taban türünü temsil eden bir dizeye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="207f2-103">A parsing operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="207f2-104">Örneğin, bir ayrıştırma işlemi, bir dizeyi bir kayan noktalı sayı veya tarih ve saat değerini dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="207f2-104">For example, a parsing operation is used to convert a string to a floating-point number or to a date and time value.</span></span> <span data-ttu-id="207f2-105">Bir ayrıştırma işlemi gerçekleştirmek için en yaygın kullanılan yöntemdir `Parse` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="207f2-105">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="207f2-106">Ayrıştırma (Bu bir taban türü dize gösterimine dönüştürme içerir) biçimlendirme tersine çevirme işlemi olduğundan, çoğu aynı kuralları ve kuralları geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="207f2-106">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="207f2-107">Yalnızca biçimlendirme olarak uygulayan bir nesne kullanır <xref:System.IFormatProvider> arabirimi uygulayan bir nesne de kullandığı ayrıştırma kültüre duyarlı biçimlendirme bilgilerini sağlamak üzere <xref:System.IFormatProvider> dize gösterimini yorumlama belirlemek için arabirimi .</span><span class="sxs-lookup"><span data-stu-id="207f2-107">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="207f2-108">Daha fazla bilgi için [biçimlendirme türleri](../../../docs/standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="207f2-108">For more information, see [Formatting Types](../../../docs/standard/base-types/formatting-types.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="207f2-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="207f2-109">In This Section</span></span>  
 [<span data-ttu-id="207f2-110">Sayısal Dizeleri Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="207f2-110">Parsing Numeric Strings</span></span>](../../../docs/standard/base-types/parsing-numeric.md)  
 <span data-ttu-id="207f2-111">Dizeleri .NET sayısal türlerine dönüştüren açıklar.</span><span class="sxs-lookup"><span data-stu-id="207f2-111">Describes how to convert strings into .NET numeric types.</span></span>  
  
 [<span data-ttu-id="207f2-112">Tarih ve Saat Dizelerini Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="207f2-112">Parsing Date and Time Strings</span></span>](../../../docs/standard/base-types/parsing-datetime.md)  
 <span data-ttu-id="207f2-113">.NET Framework'e dizeleri dönüştürüleceğini açıklar **DateTime** türleri.</span><span class="sxs-lookup"><span data-stu-id="207f2-113">Describes how to convert strings into .NET **DateTime** types.</span></span>  
  
 [<span data-ttu-id="207f2-114">Diğer Dizeleri Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="207f2-114">Parsing Other Strings</span></span>](../../../docs/standard/base-types/parsing-other.md)  
 <span data-ttu-id="207f2-115">Dizelere dönüştürülebileceği açıklar **Char**, **Boole**, ve **Enum** türleri.</span><span class="sxs-lookup"><span data-stu-id="207f2-115">Describes how to convert strings into **Char**, **Boolean**, and **Enum** types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="207f2-116">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="207f2-116">Related Sections</span></span>  
 [<span data-ttu-id="207f2-117">Biçimlendirme Türleri</span><span class="sxs-lookup"><span data-stu-id="207f2-117">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="207f2-118">Biçim belirticileri ve biçim sağlayıcıları gibi biçimlendirme temel kavramları açıklar.</span><span class="sxs-lookup"><span data-stu-id="207f2-118">Describes basic formatting concepts like format specifiers and format providers.</span></span>  
  
 [<span data-ttu-id="207f2-119">.NET içinde Tür Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="207f2-119">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="207f2-120">Türleri dönüştürme işlemini açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="207f2-120">Describes how to convert types.</span></span>  
  
 [<span data-ttu-id="207f2-121">Temel Türler</span><span class="sxs-lookup"><span data-stu-id="207f2-121">Base Types</span></span>](../../../docs/standard/base-types/index.md)  
 <span data-ttu-id="207f2-122">.NET temel türleri üzerinde gerçekleştirebileceğiniz sık kullanılan işlemleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="207f2-122">Describes common operations that you can perform on .NET base types.</span></span>
