---
description: 'Daha fazla bilgi edinin: System. Convert yöntemleri'
title: System.Convert Yöntemleri
ms.date: 03/30/2017
ms.assetid: 3ca6c5b6-ea5d-4ab0-b675-f082135b342c
ms.openlocfilehash: a323f8d0c3c4a8d1248409d2ec27565acdc58222
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681415"
---
# <a name="systemconvert-methods"></a><span data-ttu-id="92081-103">System.Convert Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="92081-103">System.Convert Methods</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="92081-104">Aşağıdaki <xref:System.Convert> yöntemleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="92081-104">does not support the following <xref:System.Convert> methods.</span></span>

- <span data-ttu-id="92081-105">Bir parametre içeren sürümler <xref:System.IFormatProvider> .</span><span class="sxs-lookup"><span data-stu-id="92081-105">Versions with an <xref:System.IFormatProvider> parameter.</span></span>

- <span data-ttu-id="92081-106">Char dizilerini veya bayt dizilerini içeren Yöntemler:</span><span class="sxs-lookup"><span data-stu-id="92081-106">Methods that involve char arrays or byte arrays:</span></span>

  - <xref:System.Convert.FromBase64CharArray%2A>

  - <xref:System.Convert.ToBase64CharArray%2A>

  - <xref:System.Convert.FromBase64String%2A>

  - <xref:System.Convert.ToBase64String%2A>

- <span data-ttu-id="92081-107">Aşağıdaki Yöntemler:</span><span class="sxs-lookup"><span data-stu-id="92081-107">The following methods:</span></span>

  - <span data-ttu-id="92081-108">`public static <Type2> To<Type2>(<Type1> value);` olmadığı</span><span class="sxs-lookup"><span data-stu-id="92081-108">`public static <Type2> To<Type2>(<Type1> value);` where</span></span>

    <span data-ttu-id="92081-109">`Type1``Type2`her biri,, `sbyte` `uint` `ulong` veya `ushort` .</span><span class="sxs-lookup"><span data-stu-id="92081-109">`Type1` and `Type2` are each one of `sbyte`, `uint`, `ulong`, or `ushort`.</span></span>

  - <span data-ttu-id="92081-110">C#:</span><span class="sxs-lookup"><span data-stu-id="92081-110">C#:</span></span>

    `int To<int type>(string value, int fromBase),`

    `ToString(... value, int toBase)`

  - <span data-ttu-id="92081-111">Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="92081-111">Visual Basic:</span></span>

    `Function To(Of [Numeric])(value as String, fromBase As Integer)`

    `As [Numeric], ToString( value As …, toBase As Integer)`

  - <xref:System.Convert.IsDBNull%2A>

  - <xref:System.Convert.GetTypeCode%2A>

  - <xref:System.Convert.ChangeType%2A>

## <a name="see-also"></a><span data-ttu-id="92081-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92081-112">See also</span></span>

- [<span data-ttu-id="92081-113">Veri Türleri ve İşlevleri</span><span class="sxs-lookup"><span data-stu-id="92081-113">Data Types and Functions</span></span>](data-types-and-functions.md)
