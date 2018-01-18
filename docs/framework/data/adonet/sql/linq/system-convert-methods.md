---
title: "System.Convert'i yöntemleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ca6c5b6-ea5d-4ab0-b675-f082135b342c
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 0d0dc8889c9d71063dabd89b0434b088b4368080
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="systemconvert-methods"></a><span data-ttu-id="b5732-102">System.Convert'i yöntemleri</span><span class="sxs-lookup"><span data-stu-id="b5732-102">System.Convert Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="b5732-103">Aşağıdaki desteklemiyor <xref:System.Convert> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="b5732-103"> does not support the following <xref:System.Convert> methods.</span></span>  
  
-   <span data-ttu-id="b5732-104">Sürümleriyle bir <xref:System.IFormatProvider> parametresi.</span><span class="sxs-lookup"><span data-stu-id="b5732-104">Versions with an <xref:System.IFormatProvider> parameter.</span></span>  
  
-   <span data-ttu-id="b5732-105">Karakter dizileri veya bayt dizileri yöntemleri:</span><span class="sxs-lookup"><span data-stu-id="b5732-105">Methods that involve char arrays or byte arrays:</span></span>  
  
    -   <xref:System.Convert.FromBase64CharArray%2A>  
  
    -   <xref:System.Convert.ToBase64CharArray%2A>  
  
    -   <xref:System.Convert.FromBase64String%2A>  
  
    -   <xref:System.Convert.ToBase64String%2A>  
  
-   <span data-ttu-id="b5732-106">Aşağıdaki yöntemleri:</span><span class="sxs-lookup"><span data-stu-id="b5732-106">The following methods:</span></span>  
  
    -   <span data-ttu-id="b5732-107">`public static <Type2> To<Type2>(<Type1> value);`Burada</span><span class="sxs-lookup"><span data-stu-id="b5732-107">`public static <Type2> To<Type2>(<Type1> value);` where</span></span>  
  
         <span data-ttu-id="b5732-108">`Type1`ve `Type2` her biri olan `sbyte`, `uint`, `ulong`, veya `ushort`.</span><span class="sxs-lookup"><span data-stu-id="b5732-108">`Type1` and `Type2` are each one of `sbyte`, `uint`, `ulong`, or `ushort`.</span></span>  
  
    -   <span data-ttu-id="b5732-109">C# ' TA:</span><span class="sxs-lookup"><span data-stu-id="b5732-109">C#:</span></span>  
  
         `int To<int type>(string value, int fromBase),`  
  
         `ToString(... value, int toBase)`  
  
    -   <span data-ttu-id="b5732-110">Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="b5732-110">Visual Basic:</span></span>  
  
         `Function To(Of [Numeric])(value as String, fromBase As Integer)`  
  
         `As [Numeric], ToString( value As …, toBase As Integer)`  
  
    -   <xref:System.Convert.IsDBNull%2A>  
  
    -   <xref:System.Convert.GetTypeCode%2A>  
  
    -   <xref:System.Convert.ChangeType%2A>  
  
## <a name="see-also"></a><span data-ttu-id="b5732-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b5732-111">See Also</span></span>  
 [<span data-ttu-id="b5732-112">Veri Türleri ve İşlevleri</span><span class="sxs-lookup"><span data-stu-id="b5732-112">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
