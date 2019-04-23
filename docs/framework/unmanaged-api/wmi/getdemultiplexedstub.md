---
title: GetDemultiplexedStub işlevi (yönetilmeyen API Başvurusu)
description: Bir istemcinin Windows Yönetimi'nden zaman uyumsuz bir çağrı alma yardımcı olmak için nesne ileticisi havuzu GetDemultiplexedStub işlevi oluşturur.
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
ms.openlocfilehash: 872164e2f48f1ef234b729b28aa9b1af1589c0fc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59180953"
---
# <a name="getdemultiplexedstub-function"></a><span data-ttu-id="ec0d8-103">GetDemultiplexedStub işlevi</span><span class="sxs-lookup"><span data-stu-id="ec0d8-103">GetDemultiplexedStub function</span></span>
<span data-ttu-id="ec0d8-104">Bir istemcinin Windows Yönetimi'nden zaman uyumsuz bir çağrı alma yardımcı olmak için nesne ileticisi havuzu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ec0d8-104">Creates an object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="ec0d8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ec0d8-105">Syntax</span></span>  
  
```  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject, 
   [in] boolean      isLocal, 
   [out] IUnknown**  ppObject
); 
```  

## <a name="parameters"></a><span data-ttu-id="ec0d8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ec0d8-106">Parameters</span></span>

`pObject`  
<span data-ttu-id="ec0d8-107">[in] İstemci işlem içi uygulaması için bir işaretçi [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).</span><span class="sxs-lookup"><span data-stu-id="ec0d8-107">[in] A pointer to the client's in-process implementation of [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).</span></span>

`isLocal`  
<span data-ttu-id="ec0d8-108">[in] Olay yerel olup olmadığını belirten bir bayrak (`true`); Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="ec0d8-108">[in] A flag that indicates whether the event is local (`true`); otherwise, `false`.</span></span>

`ppObject`  
<span data-ttu-id="ec0d8-109">[out] Bir istemcinin Windows Yönetimi'nden zaman uyumsuz bir çağrı alma yardımcı olmak için bir nesne ileticisi havuzu.</span><span class="sxs-lookup"><span data-stu-id="ec0d8-109">[out] A object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>

## <a name="return-value"></a><span data-ttu-id="ec0d8-110">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="ec0d8-110">Return value</span></span>

<span data-ttu-id="ec0d8-111">İşlev başarılı olursa, dönüş değeri olduğu `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="ec0d8-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="ec0d8-112">İşlev başarısız olursa, dönüş değeri sıfır olmayan hata kodudur.</span><span class="sxs-lookup"><span data-stu-id="ec0d8-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="ec0d8-113">Genişletilmiş hata bilgilerini almak için arama [Geterrorınfo](geterrorinfo.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="ec0d8-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
    
## <a name="requirements"></a><span data-ttu-id="ec0d8-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ec0d8-114">Requirements</span></span>  
 <span data-ttu-id="ec0d8-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec0d8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec0d8-116">**Üst bilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="ec0d8-116">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="ec0d8-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ec0d8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec0d8-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec0d8-118">See also</span></span>

- [<span data-ttu-id="ec0d8-119">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ec0d8-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
