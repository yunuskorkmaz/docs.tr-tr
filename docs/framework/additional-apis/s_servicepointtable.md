---
title: ServicePointManager. s_ServicePointTable alanı
description: .NET 'teki ServicePointManager. s_ServicePointTable alanı hakkında bilgi edinin. Bu karma tablo alanı AppDomain 'de etkin HTTP bağlantıları (ServicePoints) içerir.
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
ms.openlocfilehash: 9462ae10125dd37706f786a1f2cef78e62fbabcc
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989548"
---
# <a name="servicepointmanagers_servicepointtable-field"></a><span data-ttu-id="47cd2-104">ServicePointManager. s \_ servicepointtable alanı</span><span class="sxs-lookup"><span data-stu-id="47cd2-104">ServicePointManager.s\_ServicePointTable Field</span></span>

<span data-ttu-id="47cd2-105">`ServicePointManager.s_ServicePointTable`<xref:System.Collections.Hashtable>, içindeki ETKIN HTTP bağlantılarının listesini içeren bir <xref:System.Net.ServicePoint> ' dır <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="47cd2-105">`ServicePointManager.s_ServicePointTable` is a <xref:System.Collections.Hashtable> that contains the list of active HTTP connections (<xref:System.Net.ServicePoint>s) in the <xref:System.AppDomain>.</span></span>

## <a name="syntax"></a><span data-ttu-id="47cd2-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="47cd2-106">Syntax</span></span>
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> <span data-ttu-id="47cd2-107">`ServicePointManager.s_ServicePointTable`Alan özeldir ve doğrudan kodunuzda kullanılması amaçlıyordu.</span><span class="sxs-lookup"><span data-stu-id="47cd2-107">The `ServicePointManager.s_ServicePointTable` field is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="47cd2-108">Microsoft, herhangi bir koşulda bu alanın bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="47cd2-108">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="47cd2-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="47cd2-109">Requirements</span></span>

<span data-ttu-id="47cd2-110">**Ad alanı:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="47cd2-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="47cd2-111">**Bütünleştirilmiş kod:** Sistem (System.dll)</span><span class="sxs-lookup"><span data-stu-id="47cd2-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="47cd2-112">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="47cd2-112">**.NET Framework versions:** Available since 2.0.</span></span>
