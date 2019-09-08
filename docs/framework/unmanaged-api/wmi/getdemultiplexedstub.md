---
title: GetDemultiplexedStub işlevi (yönetilmeyen API Başvurusu)
description: GetDemultiplexedStub işlevi, bir istemcinin Windows yönetiminden zaman uyumsuz çağrılar almasına yardımcı olmak için bir nesne iletici havuzu oluşturur.
ms.date: 11/06/2017
api_name:
- GetDemultiplexedStub
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetDemultiplexedStub
helpviewer_keywords:
- GetDemultiplexedStub function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a2d3885a4a9e54950909053ba18de5b1891e7edf
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798602"
---
# <a name="getdemultiplexedstub-function"></a><span data-ttu-id="d1084-103">GetDemultiplexedStub işlevi</span><span class="sxs-lookup"><span data-stu-id="d1084-103">GetDemultiplexedStub function</span></span>
<span data-ttu-id="d1084-104">Bir istemciye Windows yönetiminden zaman uyumsuz çağrılar alma konusunda yardımcı olmak için bir nesne iletici havuzu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d1084-104">Creates an object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="d1084-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d1084-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject, 
   [in] boolean      isLocal, 
   [out] IUnknown**  ppObject
); 
```  

## <a name="parameters"></a><span data-ttu-id="d1084-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d1084-106">Parameters</span></span>

`pObject`  
<span data-ttu-id="d1084-107">'ndaki İstemcinin işlem içi [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink)uygulamasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d1084-107">[in] A pointer to the client's in-process implementation of [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).</span></span>

`isLocal`  
<span data-ttu-id="d1084-108">'ndaki Olayın yerel (`true`) olup olmadığını belirten bayrak; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="d1084-108">[in] A flag that indicates whether the event is local (`true`); otherwise, `false`.</span></span>

`ppObject`  
<span data-ttu-id="d1084-109">dışı Windows yönetiminden zaman uyumsuz çağrılar alırken bir istemciye yardımcı olmak için bir nesne ileticisi Havuzu.</span><span class="sxs-lookup"><span data-stu-id="d1084-109">[out] A object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>

## <a name="return-value"></a><span data-ttu-id="d1084-110">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="d1084-110">Return value</span></span>

<span data-ttu-id="d1084-111">İşlev başarılı olursa, dönüş değeri (0) `S_OK` olur.</span><span class="sxs-lookup"><span data-stu-id="d1084-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="d1084-112">İşlev başarısız olursa, dönüş değeri sıfır olmayan bir hata kodudur.</span><span class="sxs-lookup"><span data-stu-id="d1084-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="d1084-113">Genişletilmiş hata bilgilerini almak için [GetErrorInfo](geterrorinfo.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="d1084-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
    
## <a name="requirements"></a><span data-ttu-id="d1084-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d1084-114">Requirements</span></span>  
 <span data-ttu-id="d1084-115">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1084-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1084-116">**Üst bilgi** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="d1084-116">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="d1084-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d1084-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1084-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1084-118">See also</span></span>

- [<span data-ttu-id="d1084-119">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d1084-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
