---
title: CStr İşlevinin Dönüş Değerleri
ms.date: 07/20/2015
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
ms.openlocfilehash: 4a40777c7290ec6d8c0d032f2edca5d889e20f04
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349997"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a><span data-ttu-id="646c6-102">CStr İşlevinin Dönüş Değerleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="646c6-102">Return Values for the CStr Function (Visual Basic)</span></span>
<span data-ttu-id="646c6-103">Aşağıdaki tabloda, `expression`farklı veri türleri için `CStr` için dönüş değerleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="646c6-103">The following table describes the return values for `CStr` for different data types of `expression`.</span></span>  
  
|<span data-ttu-id="646c6-104">`expression` tür</span><span class="sxs-lookup"><span data-stu-id="646c6-104">If `expression` type is</span></span>|<span data-ttu-id="646c6-105">`CStr` döndürür</span><span class="sxs-lookup"><span data-stu-id="646c6-105">`CStr` returns</span></span>|  
|-----------------------------|--------------------|  
|[<span data-ttu-id="646c6-106">Boolean Veri Türü</span><span class="sxs-lookup"><span data-stu-id="646c6-106">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="646c6-107">"True" veya "false" içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="646c6-107">A string containing "True" or "False".</span></span>|  
|[<span data-ttu-id="646c6-108">Date Veri Türü</span><span class="sxs-lookup"><span data-stu-id="646c6-108">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="646c6-109">Sisteminizin kısa tarih biçiminde bir `Date` değeri (Tarih ve saat) içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="646c6-109">A string containing a `Date` value (date and time) in the short date format of your system.</span></span>|  
|[<span data-ttu-id="646c6-110">Sayısal Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="646c6-110">Numeric Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|<span data-ttu-id="646c6-111">Sayıyı temsil eden bir dize.</span><span class="sxs-lookup"><span data-stu-id="646c6-111">A string representing the number.</span></span>|  
  
## <a name="cstr-and-date"></a><span data-ttu-id="646c6-112">CStr ve Tarih</span><span class="sxs-lookup"><span data-stu-id="646c6-112">CStr and Date</span></span>  
 <span data-ttu-id="646c6-113">`Date` türü her zaman hem tarih hem de saat bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="646c6-113">The `Date` type always contains both date and time information.</span></span> <span data-ttu-id="646c6-114">Tür dönüştürme amaçları doğrultusunda Visual Basic, 1/1/0001 (yıl 1 ' den 1 ' de) tarih için nötr bir *değer* ve 00:00:00 (gece yarısı) zaman için nötr bir değer olacak şekilde değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="646c6-114">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="646c6-115">`CStr`, sonuçta elde edilen dizedeki nötr değerler içermez.</span><span class="sxs-lookup"><span data-stu-id="646c6-115">`CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="646c6-116">Örneğin, `#January 1, 0001 9:30:00#` bir dizeye dönüştürürseniz, sonuç "9:30:00" olur. tarih bilgileri bastırılır.</span><span class="sxs-lookup"><span data-stu-id="646c6-116">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="646c6-117">Ancak, tarih bilgileri özgün `Date` değerinde hala vardır ve <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>gibi işlevlerle kurtarılabilir.</span><span class="sxs-lookup"><span data-stu-id="646c6-117">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="646c6-118">`CStr` işlevi, uygulamanın geçerli kültür ayarlarına bağlı olarak dönüşümünü gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="646c6-118">The `CStr` function performs its conversion based on the current culture settings for the application.</span></span> <span data-ttu-id="646c6-119">Belirli bir kültürdeki bir sayının dize gösterimini almak için, sayının `ToString(IFormatProvider)` yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="646c6-119">To get the string representation of a number in a particular culture, use the number's `ToString(IFormatProvider)` method.</span></span> <span data-ttu-id="646c6-120">Örneğin, `Double` türündeki bir değeri bir `String`dönüştürrken <xref:System.Double.ToString%2A?displayProperty=nameWithType> kullanın.</span><span class="sxs-lookup"><span data-stu-id="646c6-120">For example, use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="646c6-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="646c6-121">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>
- [<span data-ttu-id="646c6-122">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="646c6-122">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="646c6-123">Boolean Veri Türü</span><span class="sxs-lookup"><span data-stu-id="646c6-123">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [<span data-ttu-id="646c6-124">Date Veri Türü</span><span class="sxs-lookup"><span data-stu-id="646c6-124">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)
