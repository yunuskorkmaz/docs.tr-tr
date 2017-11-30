---
title: "CStr İşlevinin Dönüş Değerleri (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- times [Visual Basic], CStr Function return values
- type conversion [Visual Basic]
- dates [Visual Basic], CStr Function return values
- CStr function
- strings [Visual Basic], return value
- Date data type [Visual Basic], converting
- dates [Visual Basic]
- String data type [Visual Basic], converting
ms.assetid: 3aa744e7-1419-45d5-85e3-e5abc2953673
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b498c9b1b7916467c96ed2c645c7131192a5e8b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a><span data-ttu-id="44ff1-102">CStr İşlevinin Dönüş Değerleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44ff1-102">Return Values for the CStr Function (Visual Basic)</span></span>
<span data-ttu-id="44ff1-103">Dönüş değerleri aşağıdaki tabloda açıklanmaktadır `CStr` farklı veri türleri için `expression`.</span><span class="sxs-lookup"><span data-stu-id="44ff1-103">The following table describes the return values for `CStr` for different data types of `expression`.</span></span>  
  
|<span data-ttu-id="44ff1-104">Varsa `expression` türü</span><span class="sxs-lookup"><span data-stu-id="44ff1-104">If `expression` type is</span></span>|<span data-ttu-id="44ff1-105">`CStr`döndürür</span><span class="sxs-lookup"><span data-stu-id="44ff1-105">`CStr` returns</span></span>|  
|-----------------------------|--------------------|  
|[<span data-ttu-id="44ff1-106">Boole veri türü</span><span class="sxs-lookup"><span data-stu-id="44ff1-106">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="44ff1-107">"True" içeren bir dize veya "False".</span><span class="sxs-lookup"><span data-stu-id="44ff1-107">A string containing "True" or "False".</span></span>|  
|[<span data-ttu-id="44ff1-108">Tarih veri türü</span><span class="sxs-lookup"><span data-stu-id="44ff1-108">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="44ff1-109">Bir dizeyi içeren bir `Date` sisteminizin kısa tarih biçiminde (tarih ve saat) değeri.</span><span class="sxs-lookup"><span data-stu-id="44ff1-109">A string containing a `Date` value (date and time) in the short date format of your system.</span></span>|  
|[<span data-ttu-id="44ff1-110">Sayısal veri türleri</span><span class="sxs-lookup"><span data-stu-id="44ff1-110">Numeric Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|<span data-ttu-id="44ff1-111">Sayısını temsil eden bir dize.</span><span class="sxs-lookup"><span data-stu-id="44ff1-111">A string representing the number.</span></span>|  
  
## <a name="cstr-and-date"></a><span data-ttu-id="44ff1-112">CStr ve tarihi</span><span class="sxs-lookup"><span data-stu-id="44ff1-112">CStr and Date</span></span>  
 <span data-ttu-id="44ff1-113">`Date` Türü her zaman tarih ve saat bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="44ff1-113">The `Date` type always contains both date and time information.</span></span> <span data-ttu-id="44ff1-114">Tür dönüşümü amaçları doğrultusunda, Visual Basic 1/1/0001 (Ocak 1 yılının 1) olarak göz önünde bulundurur bir *nötr değeri* tarihini ve 00:00:00 (gece yarısı) süresi dilden bağımsız bir değer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="44ff1-114">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="44ff1-115">`CStr`dilden bağımsız değerleri sonuç dizesinde içermez.</span><span class="sxs-lookup"><span data-stu-id="44ff1-115">`CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="44ff1-116">Örneğin, dönüştürmek, `#January 1, 0001 9:30:00#` bir dizeye sonucu "9:30:00 AM"; tarih bilgisini engellenir.</span><span class="sxs-lookup"><span data-stu-id="44ff1-116">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="44ff1-117">Ancak, tarih bilgisini özgün hala mevcut olduğu `Date` değer ve işlevleriyle gibi kurtarılabilir <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.</span><span class="sxs-lookup"><span data-stu-id="44ff1-117">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="44ff1-118">`CStr` İşlevi uygulama için geçerli kültür ayarları göre kendi dönüştürme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="44ff1-118">The `CStr` function performs its conversion based on the current culture settings for the application.</span></span> <span data-ttu-id="44ff1-119">Bir sayı dize gösterimini içinde belirli bir kültür almak için sayının kullanmak `ToString(IFormatProvider)` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="44ff1-119">To get the string representation of a number in a particular culture, use the number's `ToString(IFormatProvider)` method.</span></span> <span data-ttu-id="44ff1-120">Örneğin, <xref:System.Double.ToString%2A?displayProperty=nameWithType> türünde bir değer dönüştürülürken `Double` için bir `String`.</span><span class="sxs-lookup"><span data-stu-id="44ff1-120">For example, use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44ff1-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="44ff1-121">See Also</span></span>  
 <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>  
 [<span data-ttu-id="44ff1-122">Tür dönüşüm işlevleri</span><span class="sxs-lookup"><span data-stu-id="44ff1-122">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="44ff1-123">Boole veri türü</span><span class="sxs-lookup"><span data-stu-id="44ff1-123">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)  
 [<span data-ttu-id="44ff1-124">Tarih veri türü</span><span class="sxs-lookup"><span data-stu-id="44ff1-124">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)
