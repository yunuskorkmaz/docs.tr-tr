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
ms.openlocfilehash: 5f25777402fa31e72cbbf36f58a6c4cc65542979
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45560103"
---
# <a name="geterrorinfo-function"></a><span data-ttu-id="b1fab-103">Geterrorınfo işlevi</span><span class="sxs-lookup"><span data-stu-id="b1fab-103">GetErrorInfo function</span></span>
<span data-ttu-id="b1fab-104">Önceki işlev çağrısında hata bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="b1fab-104">Retrieves error information from the previous function call.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="b1fab-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b1fab-105">Syntax</span></span>  
  
```  
IErrorInfo* GetErrorInfo(); 
```  

## <a name="return-value"></a><span data-ttu-id="b1fab-106">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="b1fab-106">Return value</span></span>

<span data-ttu-id="b1fab-107">Bir işaretçi bir [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) işlev çağrısı başarılı olursa, nesne veya `null` başarısız olması durumunda.</span><span class="sxs-lookup"><span data-stu-id="b1fab-107">An pointer to an [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) object if the function call succeeds, or `null` if it fails.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="b1fab-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b1fab-108">Remarks</span></span>

<span data-ttu-id="b1fab-109">Bu işlev bir çağrı sarılır [IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b1fab-109">This function wraps a call to the [IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b1fab-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b1fab-110">Requirements</span></span>  
 <span data-ttu-id="b1fab-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1fab-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1fab-112">**Başlık:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="b1fab-112">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="b1fab-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b1fab-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1fab-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1fab-114">See also</span></span>  
[<span data-ttu-id="b1fab-115">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b1fab-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
