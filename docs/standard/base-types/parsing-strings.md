---
title: ".NET dizeleri ayrıştırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9c2193dd1b1f3c0478efb5fc9c2b80250ef1878f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="parsing-strings-in-net"></a><span data-ttu-id="05218-102">.NET dizeleri ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="05218-102">Parsing Strings in .NET</span></span>
<span data-ttu-id="05218-103">Ayrıştırma işlemi bir .NET taban türü, temel türü içine temsil eden bir dize dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="05218-103">A parsing operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="05218-104">Örneğin, bir ayrıştırma işlemi, bir dizeyi bir kayan noktalı sayı veya tarih ve saat değerine dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="05218-104">For example, a parsing operation is used to convert a string to a floating-point number or to a date and time value.</span></span> <span data-ttu-id="05218-105">Ayrıştırma işlemi gerçekleştirmek için en yaygın olarak kullanılan yöntemidir `Parse` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="05218-105">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="05218-106">Ayrıştırma (bir taban türü dize gösterimine dönüştürülmesi içerir) biçimlendirme tersine çevirme işlemi olduğundan, aynı kuralları ve kuralları birçoğu uygulayın.</span><span class="sxs-lookup"><span data-stu-id="05218-106">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="05218-107">Arabirimini uygulayan bir nesneye yalnızca biçimlendirme olarak kullanan <xref:System.IFormatProvider> arabirimini uygulayan bir nesne de kullandığı ayrıştırma kültüre duyarlı biçimlendirme bilgi sağlamak için <xref:System.IFormatProvider> bir dize gösterimi yorumlama belirlemek için arabirimi .</span><span class="sxs-lookup"><span data-stu-id="05218-107">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="05218-108">Daha fazla bilgi için bkz: [biçimlendirme türleri](../../../docs/standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="05218-108">For more information, see [Formatting Types](../../../docs/standard/base-types/formatting-types.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="05218-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="05218-109">In This Section</span></span>  
 [<span data-ttu-id="05218-110">Sayısal Dizeleri Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="05218-110">Parsing Numeric Strings</span></span>](../../../docs/standard/base-types/parsing-numeric.md)  
 <span data-ttu-id="05218-111">Dizeleri .NET sayısal türlerine dönüştürmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="05218-111">Describes how to convert strings into .NET numeric types.</span></span>  
  
 [<span data-ttu-id="05218-112">Tarih ve Saat Dizelerini Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="05218-112">Parsing Date and Time Strings</span></span>](../../../docs/standard/base-types/parsing-datetime.md)  
 <span data-ttu-id="05218-113">Dizeleri .NET dönüştürülmesi açıklanmaktadır **DateTime** türleri.</span><span class="sxs-lookup"><span data-stu-id="05218-113">Describes how to convert strings into .NET **DateTime** types.</span></span>  
  
 [<span data-ttu-id="05218-114">Diğer Dizeleri Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="05218-114">Parsing Other Strings</span></span>](../../../docs/standard/base-types/parsing-other.md)  
 <span data-ttu-id="05218-115">Dizelere dönüştürme açıklar **Char**, **Boolean**, ve **Enum** türleri.</span><span class="sxs-lookup"><span data-stu-id="05218-115">Describes how to convert strings into **Char**, **Boolean**, and **Enum** types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="05218-116">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="05218-116">Related Sections</span></span>  
 [<span data-ttu-id="05218-117">Biçimlendirme Türleri</span><span class="sxs-lookup"><span data-stu-id="05218-117">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="05218-118">Biçim belirticiler ve biçim sağlayıcıları gibi temel biçimlendirme kavramlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="05218-118">Describes basic formatting concepts like format specifiers and format providers.</span></span>  
  
 [<span data-ttu-id="05218-119">.NET içinde Tür Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="05218-119">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="05218-120">Türleri dönüştürme açıklar.</span><span class="sxs-lookup"><span data-stu-id="05218-120">Describes how to convert types.</span></span>  
  
 [<span data-ttu-id="05218-121">Temel Türler</span><span class="sxs-lookup"><span data-stu-id="05218-121">Base Types</span></span>](../../../docs/standard/base-types/index.md)  
 <span data-ttu-id="05218-122">.NET temel türlerinde gerçekleştirdiğiniz ortak işlemleri açıklanır.</span><span class="sxs-lookup"><span data-stu-id="05218-122">Describes common operations that you can perform on .NET base types.</span></span>
