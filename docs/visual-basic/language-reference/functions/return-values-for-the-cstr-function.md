---
description: 'Hakkında daha fazla bilgi edinin: CStr Işlevi için dönüş değerleri (Visual Basic)'
title: CStr için Dönüş Değerleri İşlevi
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
ms.openlocfilehash: ce45059db8ff8e926954014a09379ee54f1caf30
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731164"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a><span data-ttu-id="9866f-103">CStr İşlevinin Dönüş Değerleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9866f-103">Return Values for the CStr Function (Visual Basic)</span></span>

<span data-ttu-id="9866f-104">Aşağıdaki tabloda, `CStr` farklı veri türleri için dönüş değerleri açıklanmaktadır `expression` .</span><span class="sxs-lookup"><span data-stu-id="9866f-104">The following table describes the return values for `CStr` for different data types of `expression`.</span></span>  
  
|<span data-ttu-id="9866f-105">Eğer `expression` tür ise</span><span class="sxs-lookup"><span data-stu-id="9866f-105">If `expression` type is</span></span>|<span data-ttu-id="9866f-106">`CStr` döndürdüğü</span><span class="sxs-lookup"><span data-stu-id="9866f-106">`CStr` returns</span></span>|  
|-----------------------------|--------------------|  
|[<span data-ttu-id="9866f-107">Boolean Veri Türü</span><span class="sxs-lookup"><span data-stu-id="9866f-107">Boolean Data Type</span></span>](../data-types/boolean-data-type.md)|<span data-ttu-id="9866f-108">"True" veya "false" içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="9866f-108">A string containing "True" or "False".</span></span>|  
|[<span data-ttu-id="9866f-109">Date Veri Türü</span><span class="sxs-lookup"><span data-stu-id="9866f-109">Date Data Type</span></span>](../data-types/date-data-type.md)|<span data-ttu-id="9866f-110">`Date`Sisteminizin kısa tarih biçiminde bir değer (Tarih ve saat) içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="9866f-110">A string containing a `Date` value (date and time) in the short date format of your system.</span></span>|  
|[<span data-ttu-id="9866f-111">Sayısal Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="9866f-111">Numeric Data Types</span></span>](../../programming-guide/language-features/data-types/numeric-data-types.md)|<span data-ttu-id="9866f-112">Sayıyı temsil eden bir dize.</span><span class="sxs-lookup"><span data-stu-id="9866f-112">A string representing the number.</span></span>|  
  
## <a name="cstr-and-date"></a><span data-ttu-id="9866f-113">CStr ve Tarih</span><span class="sxs-lookup"><span data-stu-id="9866f-113">CStr and Date</span></span>  

 <span data-ttu-id="9866f-114">`Date`Tür her zaman hem tarih hem de saat bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="9866f-114">The `Date` type always contains both date and time information.</span></span> <span data-ttu-id="9866f-115">Tür dönüştürme amaçları doğrultusunda Visual Basic, 1/1/0001 (yıl 1 ' den 1 ' de) tarih için nötr bir *değer* ve 00:00:00 (gece yarısı) zaman için nötr bir değer olacak şekilde değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="9866f-115">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="9866f-116">`CStr` Sonuç dizesinde nötr değerler içermez.</span><span class="sxs-lookup"><span data-stu-id="9866f-116">`CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="9866f-117">Örneğin, `#January 1, 0001 9:30:00#` bir dizeye dönüştürürseniz, sonuç "9:30:00 har" olur; tarih bilgileri bastırılır.</span><span class="sxs-lookup"><span data-stu-id="9866f-117">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="9866f-118">Ancak, tarih bilgileri özgün değerde hala bulunur `Date` ve gibi işlevlerle kurtarılabilir <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> .</span><span class="sxs-lookup"><span data-stu-id="9866f-118">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9866f-119">`CStr`İşlevi, uygulamanın geçerli kültür ayarlarına bağlı olarak dönüşümünü gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="9866f-119">The `CStr` function performs its conversion based on the current culture settings for the application.</span></span> <span data-ttu-id="9866f-120">Belirli bir kültürdeki bir sayının dize gösterimini almak için, sayının `ToString(IFormatProvider)` metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="9866f-120">To get the string representation of a number in a particular culture, use the number's `ToString(IFormatProvider)` method.</span></span> <span data-ttu-id="9866f-121">Örneğin, türünde bir <xref:System.Double.ToString%2A?displayProperty=nameWithType> değer bir değeri olarak dönüştürülürken kullanın `Double` `String` .</span><span class="sxs-lookup"><span data-stu-id="9866f-121">For example, use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9866f-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9866f-122">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>
- [<span data-ttu-id="9866f-123">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="9866f-123">Type Conversion Functions</span></span>](type-conversion-functions.md)
- [<span data-ttu-id="9866f-124">Boolean Veri Türü</span><span class="sxs-lookup"><span data-stu-id="9866f-124">Boolean Data Type</span></span>](../data-types/boolean-data-type.md)
- [<span data-ttu-id="9866f-125">Date Veri Türü</span><span class="sxs-lookup"><span data-stu-id="9866f-125">Date Data Type</span></span>](../data-types/date-data-type.md)
