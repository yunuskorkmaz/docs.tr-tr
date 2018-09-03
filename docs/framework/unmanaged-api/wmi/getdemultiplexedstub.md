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
ms.openlocfilehash: 4311a77c9159428bf7beacc99d4479acb28b91b6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43482362"
---
# <a name="getdemultiplexedstub-function"></a><span data-ttu-id="f47d6-103">GetDemultiplexedStub işlevi</span><span class="sxs-lookup"><span data-stu-id="f47d6-103">GetDemultiplexedStub function</span></span>
<span data-ttu-id="f47d6-104">Bir istemcinin Windows Yönetimi'nden zaman uyumsuz bir çağrı alma yardımcı olmak için nesne ileticisi havuzu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f47d6-104">Creates an object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="f47d6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f47d6-105">Syntax</span></span>  
  
```  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject, 
   [in] boolean      isLocal, 
   [out] IUnknown**  ppObject
); 
```  

## <a name="parameters"></a><span data-ttu-id="f47d6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f47d6-106">Parameters</span></span>

`pObject`  
<span data-ttu-id="f47d6-107">[in] İstemci işlem içi uygulaması için bir işaretçi [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).</span><span class="sxs-lookup"><span data-stu-id="f47d6-107">[in] A pointer to the client's in-process implementation of [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).</span></span>

`isLocal`  
<span data-ttu-id="f47d6-108">[in] Olay yerel olup olmadığını belirten bir bayrak (`true`); Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="f47d6-108">[in] A flag that indicates whether the event is local (`true`); otherwise, `false`.</span></span>

`ppObject`  
<span data-ttu-id="f47d6-109">[out] Bir istemcinin Windows Yönetimi'nden zaman uyumsuz bir çağrı alma yardımcı olmak için bir nesne ileticisi havuzu.</span><span class="sxs-lookup"><span data-stu-id="f47d6-109">[out] A object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>

## <a name="return-value"></a><span data-ttu-id="f47d6-110">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="f47d6-110">Return value</span></span>

<span data-ttu-id="f47d6-111">İşlev başarılı olursa, dönüş değeri olduğu `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="f47d6-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="f47d6-112">İşlev başarısız olursa, dönüş değeri sıfır olmayan hata kodudur.</span><span class="sxs-lookup"><span data-stu-id="f47d6-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="f47d6-113">Genişletilmiş hata bilgilerini almak için arama [Geterrorınfo](geterrorinfo.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="f47d6-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
    
## <a name="requirements"></a><span data-ttu-id="f47d6-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f47d6-114">Requirements</span></span>  
 <span data-ttu-id="f47d6-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f47d6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f47d6-116">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f47d6-116">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f47d6-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f47d6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f47d6-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f47d6-118">See also</span></span>  
[<span data-ttu-id="f47d6-119">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f47d6-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
