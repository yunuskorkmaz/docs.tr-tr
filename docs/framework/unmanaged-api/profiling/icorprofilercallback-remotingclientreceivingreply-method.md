---
title: "ICorProfilerCallback::RemotingClientReceivingReply Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RemotingClientReceivingReply
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RemotingClientReceivingReply
helpviewer_keywords:
- ICorProfilerCallback::RemotingClientReceivingReply method [.NET Framework profiling]
- RemotingClientReceivingReply method [.NET Framework profiling]
ms.assetid: 15cfc300-8231-4ecb-9a04-19851c3eb484
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 831ce047f38f7f4a5c7a8b84efea423c482a418d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a><span data-ttu-id="7a0a8-102">ICorProfilerCallback::RemotingClientReceivingReply Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7a0a8-102">ICorProfilerCallback::RemotingClientReceivingReply Method</span></span>
<span data-ttu-id="7a0a8-103">Uzaktan iletişim çağrısı sunucu tarafı kısmı tamamlandı ve istemci şimdi alma profil oluşturucu bildirir ve yanıtı işlemek üzere.</span><span class="sxs-lookup"><span data-stu-id="7a0a8-103">Notifies the profiler that the server-side portion of a remoting call has completed and the client is now receiving and about to process the reply.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a0a8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7a0a8-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="7a0a8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7a0a8-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="7a0a8-106">[in] Karşılık gelecek bir değerle sağlanan [Icorprofilercallback::remotingserversendingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md) Bu koşullar altında:</span><span class="sxs-lookup"><span data-stu-id="7a0a8-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="7a0a8-107">Remoting GUID tanımlama bilgilerini etkindir.</span><span class="sxs-lookup"><span data-stu-id="7a0a8-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="7a0a8-108">Kanal ileti iletilirken başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="7a0a8-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="7a0a8-109">GUID tanımlama bilgileri sunucu tarafı işlemini üzerinde etkindir.</span><span class="sxs-lookup"><span data-stu-id="7a0a8-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="7a0a8-110">Bu, kolay remoting çağrıları eşlemeye izin verir.</span><span class="sxs-lookup"><span data-stu-id="7a0a8-110">This allows easy pairing of remoting calls.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="7a0a8-111">[in] Bir değer `true` çağrısı, zaman uyumsuz Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="7a0a8-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a0a8-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7a0a8-112">Requirements</span></span>  
 <span data-ttu-id="7a0a8-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a0a8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a0a8-114">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7a0a8-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7a0a8-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a0a8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a0a8-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a0a8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a0a8-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7a0a8-117">See Also</span></span>  
 [<span data-ttu-id="7a0a8-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7a0a8-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
