---
title: ServicePointManager.s_ServicePointTable Alanı
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
ms.openlocfilehash: 6a56ecd6fc85005f5987c3c2ad0d1680ca63c398
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155825"
---
# <a name="servicepointmanagers_servicepointtable-field"></a><span data-ttu-id="b761d-102">ServicePointManager.s\_ServicePointTable Alanı</span><span class="sxs-lookup"><span data-stu-id="b761d-102">ServicePointManager.s\_ServicePointTable Field</span></span>

<span data-ttu-id="b761d-103">`ServicePointManager.s_ServicePointTable`etkin <xref:System.Collections.Hashtable> HTTP bağlantılarının (lar)<xref:System.Net.ServicePoint>listesini içeren bir <xref:System.AppDomain>bağlantıdır.</span><span class="sxs-lookup"><span data-stu-id="b761d-103">`ServicePointManager.s_ServicePointTable` is a <xref:System.Collections.Hashtable> that contains the list of active HTTP connections (<xref:System.Net.ServicePoint>s) in the <xref:System.AppDomain>.</span></span>

## <a name="syntax"></a><span data-ttu-id="b761d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b761d-104">Syntax</span></span>
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> <span data-ttu-id="b761d-105">Alan `ServicePointManager.s_ServicePointTable` özeldir ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="b761d-105">The `ServicePointManager.s_ServicePointTable` field is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="b761d-106">Microsoft, hiçbir koşulda bir üretim uygulamasında bu alanın kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="b761d-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="b761d-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b761d-107">Requirements</span></span>

<span data-ttu-id="b761d-108">**Ad alanı:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="b761d-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="b761d-109">**Montaj:** Sistem (System.dll'de)</span><span class="sxs-lookup"><span data-stu-id="b761d-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="b761d-110">**.NET Framework sürümleri:** 2.0'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="b761d-110">**.NET Framework versions:** Available since 2.0.</span></span>
