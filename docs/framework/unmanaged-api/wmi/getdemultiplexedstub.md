---
title: "GetDemultiplexedStub işlevi (yönetilmeyen API Başvurusu)"
description: "GetDemultiplexedStub işlevi bir istemci zaman uyumsuz çağrılar Windows Yönetimi'nden alma yardımcı olması için bir nesne iletici havuz oluşturur."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetDemultiplexedStub
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetDemultiplexedStub
helpviewer_keywords: GetDemultiplexedStub function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a81101acbf65546ea068e6b5a0e8d9045aaadc71
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2017
---
# <a name="getdemultiplexedstub-function"></a><span data-ttu-id="ac349-103">GetDemultiplexedStub işlevi</span><span class="sxs-lookup"><span data-stu-id="ac349-103">GetDemultiplexedStub function</span></span>
<span data-ttu-id="ac349-104">Windows Yönetimi'nden zaman uyumsuz çağrılar alırken bir istemci yardımcı olması için bir nesne iletici havuz oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ac349-104">Creates an object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="ac349-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ac349-105">Syntax</span></span>  
  
```  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject, 
   [in] boolean      isLocal, 
   [out] IUnknown**  ppObject
); 
```  

## <a name="parameters"></a><span data-ttu-id="ac349-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ac349-106">Parameters</span></span>

`pObject`  
<span data-ttu-id="ac349-107">[in] İstemcinin işlemdeki uygulaması için bir işaretçi [IWbemObjectSink](https://msdn.microsoft.com/en-us/library/aa391787(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="ac349-107">[in] A pointer to the client's in-process implementation of [IWbemObjectSink](https://msdn.microsoft.com/en-us/library/aa391787(v=vs.85).aspx).</span></span>

`isLocal`  
<span data-ttu-id="ac349-108">[in] Olay yerel olup olmadığını belirten bir bayrak (`true`); Aksi halde, `false`.</span><span class="sxs-lookup"><span data-stu-id="ac349-108">[in] A flag that indicates whether the event is local (`true`); otherwise, `false`.</span></span>

`ppObject`  
<span data-ttu-id="ac349-109">[out] Windows Yönetimi'nden zaman uyumsuz çağrılar alırken bir istemci yardımcı olması için bir nesne iletici havuzu.</span><span class="sxs-lookup"><span data-stu-id="ac349-109">[out] A object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>

## <a name="return-value"></a><span data-ttu-id="ac349-110">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="ac349-110">Return value</span></span>

<span data-ttu-id="ac349-111">İşlev başarılı olursa, dönüş değeri olan `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="ac349-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="ac349-112">İşlev başarısız olursa, dönüş değeri sıfır olmayan bir hata kodudur.</span><span class="sxs-lookup"><span data-stu-id="ac349-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="ac349-113">Genişletilmiş hata bilgilerini için arama [Geterrorınfo](geterrorinfo.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="ac349-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
    
## <a name="requirements"></a><span data-ttu-id="ac349-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ac349-114">Requirements</span></span>  
 <span data-ttu-id="ac349-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac349-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac349-116">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="ac349-116">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="ac349-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ac349-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac349-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac349-118">See also</span></span>  
[<span data-ttu-id="ac349-119">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ac349-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
