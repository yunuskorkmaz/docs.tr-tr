---
title: "ICorProfilerCallback::RemotingServerReceivingMessage Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RemotingServerReceivingMessage
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RemotingServerReceivingMessage
helpviewer_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage method [.NET Framework profiling]
- RemotingServerReceivingMessage method [.NET Framework profiling]
ms.assetid: 5604d21f-e6b7-490e-b469-42122a7568e1
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e4542f5362d83bc5c0419b9f1ff389c9a21aad29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackremotingserverreceivingmessage-method"></a><span data-ttu-id="fb73e-102">ICorProfilerCallback::RemotingServerReceivingMessage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fb73e-102">ICorProfilerCallback::RemotingServerReceivingMessage Method</span></span>
<span data-ttu-id="fb73e-103">Profil Oluşturucu işlemi bir uzak yöntem çağırma veya etkinleştirme isteği aldı bildirir.</span><span class="sxs-lookup"><span data-stu-id="fb73e-103">Notifies the profiler that the process has received a remote method invocation or activation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb73e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fb73e-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fb73e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fb73e-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="fb73e-106">[in] Karşılık gelecek bir değerle sağlanan [Icorprofilercallback::remotingclientsendingmessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md) Bu koşullar altında:</span><span class="sxs-lookup"><span data-stu-id="fb73e-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="fb73e-107">Remoting GUID tanımlama bilgilerini etkindir.</span><span class="sxs-lookup"><span data-stu-id="fb73e-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="fb73e-108">Kanal ileti iletilirken başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="fb73e-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="fb73e-109">GUID tanımlama bilgileri için istemci tarafı işlemi üzerinde etkindir.</span><span class="sxs-lookup"><span data-stu-id="fb73e-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="fb73e-110">Bu, uzak çağrıları ve bir mantıksal çağrı yığını oluşturulmasını kolay eşlemeye izin verir.</span><span class="sxs-lookup"><span data-stu-id="fb73e-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="fb73e-111">[in] Bir değer `true` çağrısı, zaman uyumsuz Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="fb73e-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb73e-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fb73e-112">Remarks</span></span>  
 <span data-ttu-id="fb73e-113">İleti isteği zaman uyumsuz ise, istek rasgele bir iş parçacığı tarafından hizmet verebilir.</span><span class="sxs-lookup"><span data-stu-id="fb73e-113">If the message request is asynchronous, the request can be serviced by any arbitrary thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb73e-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fb73e-114">Requirements</span></span>  
 <span data-ttu-id="fb73e-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb73e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb73e-116">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fb73e-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fb73e-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb73e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb73e-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb73e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb73e-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fb73e-119">See Also</span></span>  
 [<span data-ttu-id="fb73e-120">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fb73e-120">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
