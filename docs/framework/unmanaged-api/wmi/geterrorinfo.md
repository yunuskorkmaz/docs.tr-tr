---
title: GetErrorInfo işlevi (yönetilmeyen API Başvurusu)
description: GetErrorInfo işlevi, önceki işlev çağrısından hata bilgilerini alır.
ms.date: 11/06/2017
api_name:
- GetErrorInfo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetErrorInfo
helpviewer_keywords:
- GetErrorInfo function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 9a80c0b5522113e704336cda29362a0406077931
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553681"
---
# <a name="geterrorinfo-function"></a><span data-ttu-id="55920-103">GetErrorInfo işlevi</span><span class="sxs-lookup"><span data-stu-id="55920-103">GetErrorInfo function</span></span>
<span data-ttu-id="55920-104">Önceki işlev çağrısından hata bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="55920-104">Retrieves error information from the previous function call.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="55920-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="55920-105">Syntax</span></span>  
  
```cpp  
IErrorInfo* GetErrorInfo();
```  

## <a name="return-value"></a><span data-ttu-id="55920-106">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="55920-106">Return value</span></span>

<span data-ttu-id="55920-107">İşlev çağrısı başarılı olursa veya başarısız olursa bir [IErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) nesnesine yönelik bir işaretçi `null` .</span><span class="sxs-lookup"><span data-stu-id="55920-107">An pointer to an [IErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) object if the function call succeeds, or `null` if it fails.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="55920-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="55920-108">Remarks</span></span>

<span data-ttu-id="55920-109">Bu işlev, [ICommandText Threadingınfo:: GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="55920-109">This function wraps a call to the [IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="55920-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="55920-110">Requirements</span></span>  
 <span data-ttu-id="55920-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55920-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55920-112">**Üst bilgi:** WMINet_Utils. def</span><span class="sxs-lookup"><span data-stu-id="55920-112">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="55920-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="55920-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55920-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55920-114">See also</span></span>

- [<span data-ttu-id="55920-115">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="55920-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
