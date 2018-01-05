---
title: "Geterrorınfo işlevi (yönetilmeyen API Başvurusu)"
description: "Geterrorınfo işlevi önceki işlev çağrısında hata bilgilerini alır."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetErrorInfo
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetErrorInfo
helpviewer_keywords: GetErrorInfo function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d4b4acde080c61fbfd5cec319c1986b8c86352c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="geterrorinfo-function"></a><span data-ttu-id="b2bf9-103">Geterrorınfo işlevi</span><span class="sxs-lookup"><span data-stu-id="b2bf9-103">GetErrorInfo function</span></span>
<span data-ttu-id="b2bf9-104">Önceki işlev çağrısında hata bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-104">Retrieves error information from the previous function call.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="b2bf9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b2bf9-105">Syntax</span></span>  
  
```  
IErrorInfo* GetErrorInfo(); 
```  

## <a name="return-value"></a><span data-ttu-id="b2bf9-106">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="b2bf9-106">Return value</span></span>

<span data-ttu-id="b2bf9-107">Bir işaretçi bir [IErrorInfo](https://msdn.microsoft.com/library/windows/desktop/ms221233(v=vs.85).aspx) işlev çağrısı başarılı olursa, nesne veya `null` başarısız olursa.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-107">An pointer to an [IErrorInfo](https://msdn.microsoft.com/library/windows/desktop/ms221233(v=vs.85).aspx) object if the function call succeeds, or `null` if it fails.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="b2bf9-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b2bf9-108">Remarks</span></span>

<span data-ttu-id="b2bf9-109">Bu işlev çağrısı sarmalar [IComThreadingInfo::GetErrorInfo](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-109">This function wraps a call to the [IComThreadingInfo::GetErrorInfo](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b2bf9-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2bf9-110">Requirements</span></span>  
 <span data-ttu-id="b2bf9-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2bf9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2bf9-112">**Başlık:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="b2bf9-112">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="b2bf9-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b2bf9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2bf9-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-114">See also</span></span>  
[<span data-ttu-id="b2bf9-115">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b2bf9-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
