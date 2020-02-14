---
title: ServicePointManager. s_ServicePointTable alanı
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ServicePointManager.s_ServicePointTable
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 24459679-291c-401a-9def-e42b29466fcf
ms.openlocfilehash: 272a0c113fd70d804c763ba0e7e6e9a4a4ee04ce
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214916"
---
# <a name="servicepointmanagers_servicepointtable-field"></a><span data-ttu-id="de8df-102">ServicePointManager. s\_ServicePointTable alanı</span><span class="sxs-lookup"><span data-stu-id="de8df-102">ServicePointManager.s\_ServicePointTable Field</span></span>

<span data-ttu-id="de8df-103">`ServicePointManager.s_ServicePointTable`, <xref:System.AppDomain>içindeki etkin HTTP bağlantılarının (<xref:System.Net.ServicePoint>s) listesini içeren bir <xref:System.Collections.Hashtable>.</span><span class="sxs-lookup"><span data-stu-id="de8df-103">`ServicePointManager.s_ServicePointTable` is a <xref:System.Collections.Hashtable> that contains the list of active HTTP connections (<xref:System.Net.ServicePoint>s) in the <xref:System.AppDomain>.</span></span>

## <a name="syntax"></a><span data-ttu-id="de8df-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="de8df-104">Syntax</span></span>
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> <span data-ttu-id="de8df-105">`ServicePointManager.s_ServicePointTable` alanı özeldir ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="de8df-105">The `ServicePointManager.s_ServicePointTable` field is private and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="de8df-106">Microsoft, herhangi bir koşulda bu alanın bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="de8df-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="de8df-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="de8df-107">Requirements</span></span>

<span data-ttu-id="de8df-108">**Ad alanı:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="de8df-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="de8df-109">**Bütünleştirilmiş kod:** Sistem (System. dll içinde)</span><span class="sxs-lookup"><span data-stu-id="de8df-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="de8df-110">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="de8df-110">**.NET Framework versions:** Available since 2.0.</span></span>
