---
title: System.Convert Yöntemleri
ms.date: 03/30/2017
ms.assetid: 3ca6c5b6-ea5d-4ab0-b675-f082135b342c
ms.openlocfilehash: d0aa0b11223e23b874471962d727d8e16e152ceb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781052"
---
# <a name="systemconvert-methods"></a><span data-ttu-id="f4045-102">System.Convert Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="f4045-102">System.Convert Methods</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="f4045-103">Aşağıdaki <xref:System.Convert> yöntemleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f4045-103">does not support the following <xref:System.Convert> methods.</span></span>

- <span data-ttu-id="f4045-104">Bir <xref:System.IFormatProvider> parametre içeren sürümler.</span><span class="sxs-lookup"><span data-stu-id="f4045-104">Versions with an <xref:System.IFormatProvider> parameter.</span></span>

- <span data-ttu-id="f4045-105">Char dizilerini veya bayt dizilerini içeren Yöntemler:</span><span class="sxs-lookup"><span data-stu-id="f4045-105">Methods that involve char arrays or byte arrays:</span></span>

  - <xref:System.Convert.FromBase64CharArray%2A>

  - <xref:System.Convert.ToBase64CharArray%2A>

  - <xref:System.Convert.FromBase64String%2A>

  - <xref:System.Convert.ToBase64String%2A>

- <span data-ttu-id="f4045-106">Aşağıdaki Yöntemler:</span><span class="sxs-lookup"><span data-stu-id="f4045-106">The following methods:</span></span>

  - <span data-ttu-id="f4045-107">`public static <Type2> To<Type2>(<Type1> value);`olmadığı</span><span class="sxs-lookup"><span data-stu-id="f4045-107">`public static <Type2> To<Type2>(<Type1> value);` where</span></span>

    <span data-ttu-id="f4045-108">`Type1``Type2` her biri`uint` ,,`ushort`veya. `sbyte` `ulong`</span><span class="sxs-lookup"><span data-stu-id="f4045-108">`Type1` and `Type2` are each one of `sbyte`, `uint`, `ulong`, or `ushort`.</span></span>

  - <span data-ttu-id="f4045-109">C#:</span><span class="sxs-lookup"><span data-stu-id="f4045-109">C#:</span></span>

    `int To<int type>(string value, int fromBase),`

    `ToString(... value, int toBase)`

  - <span data-ttu-id="f4045-110">Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="f4045-110">Visual Basic:</span></span>

    `Function To(Of [Numeric])(value as String, fromBase As Integer)`

    `As [Numeric], ToString( value As …, toBase As Integer)`

  - <xref:System.Convert.IsDBNull%2A>

  - <xref:System.Convert.GetTypeCode%2A>

  - <xref:System.Convert.ChangeType%2A>

## <a name="see-also"></a><span data-ttu-id="f4045-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4045-111">See also</span></span>

- [<span data-ttu-id="f4045-112">Veri Türleri ve İşlevleri</span><span class="sxs-lookup"><span data-stu-id="f4045-112">Data Types and Functions</span></span>](data-types-and-functions.md)
