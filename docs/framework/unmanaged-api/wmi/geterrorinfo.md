---
title: Geterrorınfo işlevi (yönetilmeyen API Başvurusu)
description: Geterrorınfo işlevi önceki işlev çağrısında hata bilgilerini alır.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b27dae07697943c696dc3419f2414701feb1220
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577679"
---
# <a name="geterrorinfo-function"></a><span data-ttu-id="7efa1-103">Geterrorınfo işlevi</span><span class="sxs-lookup"><span data-stu-id="7efa1-103">GetErrorInfo function</span></span>
<span data-ttu-id="7efa1-104">Önceki işlev çağrısında hata bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="7efa1-104">Retrieves error information from the previous function call.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="7efa1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7efa1-105">Syntax</span></span>  
  
```  
IErrorInfo* GetErrorInfo(); 
```  

## <a name="return-value"></a><span data-ttu-id="7efa1-106">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="7efa1-106">Return value</span></span>

<span data-ttu-id="7efa1-107">Bir işaretçi bir [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) işlev çağrısı başarılı olursa, nesne veya `null` başarısız olması durumunda.</span><span class="sxs-lookup"><span data-stu-id="7efa1-107">An pointer to an [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) object if the function call succeeds, or `null` if it fails.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="7efa1-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7efa1-108">Remarks</span></span>

<span data-ttu-id="7efa1-109">Bu işlev bir çağrı sarılır [IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7efa1-109">This function wraps a call to the [IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7efa1-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7efa1-110">Requirements</span></span>  
 <span data-ttu-id="7efa1-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7efa1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7efa1-112">**Üst bilgi:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="7efa1-112">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="7efa1-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7efa1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7efa1-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7efa1-114">See also</span></span>
- [<span data-ttu-id="7efa1-115">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7efa1-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
