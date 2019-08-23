---
title: CStr İşlevinin Dönüş Değerleri (Visual Basic)
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
ms.openlocfilehash: cd525ea5a295411e509f3bc37285675d15a8c4f4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930043"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a><span data-ttu-id="8d127-102">CStr İşlevinin Dönüş Değerleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d127-102">Return Values for the CStr Function (Visual Basic)</span></span>
<span data-ttu-id="8d127-103">Aşağıdaki tabloda, farklı veri `CStr` `expression`türleri için dönüş değerleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8d127-103">The following table describes the return values for `CStr` for different data types of `expression`.</span></span>  
  
|<span data-ttu-id="8d127-104">Eğer `expression` tür ise</span><span class="sxs-lookup"><span data-stu-id="8d127-104">If `expression` type is</span></span>|<span data-ttu-id="8d127-105">`CStr`döndürdüğü</span><span class="sxs-lookup"><span data-stu-id="8d127-105">`CStr` returns</span></span>|  
|-----------------------------|--------------------|  
|[<span data-ttu-id="8d127-106">Boolean Veri Türü</span><span class="sxs-lookup"><span data-stu-id="8d127-106">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="8d127-107">"True" veya "false" içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="8d127-107">A string containing "True" or "False".</span></span>|  
|[<span data-ttu-id="8d127-108">Date Veri Türü</span><span class="sxs-lookup"><span data-stu-id="8d127-108">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="8d127-109">Sisteminizin kısa tarih biçiminde `Date` bir değer (Tarih ve saat) içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="8d127-109">A string containing a `Date` value (date and time) in the short date format of your system.</span></span>|  
|[<span data-ttu-id="8d127-110">Sayısal Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="8d127-110">Numeric Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|<span data-ttu-id="8d127-111">Sayıyı temsil eden bir dize.</span><span class="sxs-lookup"><span data-stu-id="8d127-111">A string representing the number.</span></span>|  
  
## <a name="cstr-and-date"></a><span data-ttu-id="8d127-112">CStr ve Tarih</span><span class="sxs-lookup"><span data-stu-id="8d127-112">CStr and Date</span></span>  
 <span data-ttu-id="8d127-113">`Date` Tür her zaman hem tarih hem de saat bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="8d127-113">The `Date` type always contains both date and time information.</span></span> <span data-ttu-id="8d127-114">Tür dönüştürme amaçları doğrultusunda Visual Basic, 1/1/0001 (yıl 1 ' den 1 ' de) tarih için nötr bir *değer* ve 00:00:00 (gece yarısı) zaman için nötr bir değer olacak şekilde değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="8d127-114">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="8d127-115">`CStr`Sonuç dizesinde nötr değerler içermez.</span><span class="sxs-lookup"><span data-stu-id="8d127-115">`CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="8d127-116">Örneğin, bir dizeye dönüştürürseniz `#January 1, 0001 9:30:00#` , sonuç "9:30:00 har" olur; tarih bilgileri bastırılır.</span><span class="sxs-lookup"><span data-stu-id="8d127-116">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="8d127-117">Ancak, tarih bilgileri özgün `Date` değerde hala bulunur ve gibi işlevlerle <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>kurtarılabilir.</span><span class="sxs-lookup"><span data-stu-id="8d127-117">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8d127-118">`CStr` İşlevi, uygulamanın geçerli kültür ayarlarına bağlı olarak dönüşümünü gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="8d127-118">The `CStr` function performs its conversion based on the current culture settings for the application.</span></span> <span data-ttu-id="8d127-119">Belirli bir kültürdeki bir sayının dize gösterimini almak için, sayının `ToString(IFormatProvider)` metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="8d127-119">To get the string representation of a number in a particular culture, use the number's `ToString(IFormatProvider)` method.</span></span> <span data-ttu-id="8d127-120">Örneğin, türünde `Double` bir <xref:System.Double.ToString%2A?displayProperty=nameWithType> değer bir `String`değeri olarak dönüştürülürken kullanın.</span><span class="sxs-lookup"><span data-stu-id="8d127-120">For example, use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d127-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d127-121">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>
- [<span data-ttu-id="8d127-122">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="8d127-122">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="8d127-123">Boolean Veri Türü</span><span class="sxs-lookup"><span data-stu-id="8d127-123">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [<span data-ttu-id="8d127-124">Date Veri Türü</span><span class="sxs-lookup"><span data-stu-id="8d127-124">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)
