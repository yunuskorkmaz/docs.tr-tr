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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab801ec7899403f568d953535fcd430a862a2fd8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798587"
---
# <a name="geterrorinfo-function"></a><span data-ttu-id="b78ce-103">GetErrorInfo işlevi</span><span class="sxs-lookup"><span data-stu-id="b78ce-103">GetErrorInfo function</span></span>
<span data-ttu-id="b78ce-104">Önceki işlev çağrısından hata bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="b78ce-104">Retrieves error information from the previous function call.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="b78ce-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b78ce-105">Syntax</span></span>  
  
```cpp  
IErrorInfo* GetErrorInfo(); 
```  

## <a name="return-value"></a><span data-ttu-id="b78ce-106">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="b78ce-106">Return value</span></span>

<span data-ttu-id="b78ce-107">İşlev çağrısı başarılı olursa veya `null` başarısız olursa bir [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b78ce-107">An pointer to an [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) object if the function call succeeds, or `null` if it fails.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="b78ce-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b78ce-108">Remarks</span></span>

<span data-ttu-id="b78ce-109">Bu işlev, [ICommandText Threadingınfo:: GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="b78ce-109">This function wraps a call to the [IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b78ce-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b78ce-110">Requirements</span></span>  
 <span data-ttu-id="b78ce-111">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b78ce-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b78ce-112">**Üst bilgi** WMINet_Utils. def</span><span class="sxs-lookup"><span data-stu-id="b78ce-112">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="b78ce-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b78ce-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b78ce-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b78ce-114">See also</span></span>

- [<span data-ttu-id="b78ce-115">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b78ce-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
