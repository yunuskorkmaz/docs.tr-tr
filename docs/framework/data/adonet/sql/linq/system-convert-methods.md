---
title: System.Convert Yöntemleri
ms.date: 03/30/2017
ms.assetid: 3ca6c5b6-ea5d-4ab0-b675-f082135b342c
ms.openlocfilehash: 9836820f2c084a80fcc0a4856f20597716344dfd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59480657"
---
# <a name="systemconvert-methods"></a><span data-ttu-id="473de-102">System.Convert Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="473de-102">System.Convert Methods</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="473de-103">şunları desteklemez <xref:System.Convert> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="473de-103">does not support the following <xref:System.Convert> methods.</span></span>

- <span data-ttu-id="473de-104">Sürümleriyle bir <xref:System.IFormatProvider> parametresi.</span><span class="sxs-lookup"><span data-stu-id="473de-104">Versions with an <xref:System.IFormatProvider> parameter.</span></span>

- <span data-ttu-id="473de-105">Karakter dizileri veya bayt dizileri içeren yöntemler:</span><span class="sxs-lookup"><span data-stu-id="473de-105">Methods that involve char arrays or byte arrays:</span></span>

  - <xref:System.Convert.FromBase64CharArray%2A>

  - <xref:System.Convert.ToBase64CharArray%2A>

  - <xref:System.Convert.FromBase64String%2A>

  - <xref:System.Convert.ToBase64String%2A>

- <span data-ttu-id="473de-106">Aşağıdaki yöntemleri:</span><span class="sxs-lookup"><span data-stu-id="473de-106">The following methods:</span></span>

  - <span data-ttu-id="473de-107">`public static <Type2> To<Type2>(<Type1> value);` Burada</span><span class="sxs-lookup"><span data-stu-id="473de-107">`public static <Type2> To<Type2>(<Type1> value);` where</span></span>

    <span data-ttu-id="473de-108">`Type1` ve `Type2` her biri için olan `sbyte`, `uint`, `ulong`, veya `ushort`.</span><span class="sxs-lookup"><span data-stu-id="473de-108">`Type1` and `Type2` are each one of `sbyte`, `uint`, `ulong`, or `ushort`.</span></span>

  - <span data-ttu-id="473de-109">C#:</span><span class="sxs-lookup"><span data-stu-id="473de-109">C#:</span></span>

    `int To<int type>(string value, int fromBase),`

    `ToString(... value, int toBase)`

  - <span data-ttu-id="473de-110">Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="473de-110">Visual Basic:</span></span>

    `Function To(Of [Numeric])(value as String, fromBase As Integer)`

    `As [Numeric], ToString( value As …, toBase As Integer)`

  - <xref:System.Convert.IsDBNull%2A>

  - <xref:System.Convert.GetTypeCode%2A>

  - <xref:System.Convert.ChangeType%2A>

## <a name="see-also"></a><span data-ttu-id="473de-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="473de-111">See also</span></span>

- [<span data-ttu-id="473de-112">Veri Türleri ve İşlevleri</span><span class="sxs-lookup"><span data-stu-id="473de-112">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
