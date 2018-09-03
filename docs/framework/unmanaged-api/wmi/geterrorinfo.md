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
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43482242"
---
# <a name="geterrorinfo-function"></a><span data-ttu-id="b0a15-103">Geterrorınfo işlevi</span><span class="sxs-lookup"><span data-stu-id="b0a15-103">GetErrorInfo function</span></span>
<span data-ttu-id="b0a15-104">Önceki işlev çağrısında hata bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="b0a15-104">Retrieves error information from the previous function call.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="b0a15-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b0a15-105">Syntax</span></span>  
  
```  
IErrorInfo* GetErrorInfo(); 
```  

## <a name="return-value"></a><span data-ttu-id="b0a15-106">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="b0a15-106">Return value</span></span>

<span data-ttu-id="b0a15-107">Bir işaretçi bir [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) işlev çağrısı başarılı olursa, nesne veya `null` başarısız olması durumunda.</span><span class="sxs-lookup"><span data-stu-id="b0a15-107">An pointer to an [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) object if the function call succeeds, or `null` if it fails.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="b0a15-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b0a15-108">Remarks</span></span>

<span data-ttu-id="b0a15-109">Bu işlev bir çağrı sarılır [IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b0a15-109">This function wraps a call to the [IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b0a15-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b0a15-110">Requirements</span></span>  
 <span data-ttu-id="b0a15-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0a15-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0a15-112">**Başlık:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="b0a15-112">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="b0a15-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b0a15-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0a15-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0a15-114">See also</span></span>  
[<span data-ttu-id="b0a15-115">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b0a15-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
