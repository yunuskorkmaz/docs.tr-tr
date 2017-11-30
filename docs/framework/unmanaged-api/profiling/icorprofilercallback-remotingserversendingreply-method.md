---
title: "ICorProfilerCallback::RemotingServerSendingReply Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RemotingServerSendingReply
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RemotingServerSendingReply
helpviewer_keywords:
- RemotingServerSendingReply method [.NET Framework profiling]
- ICorProfilerCallback::RemotingServerSendingReply method [.NET Framework profiling]
ms.assetid: dfe84a19-2e03-4be2-8b25-f02bad38e4a9
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b99b2de235634b715a6f5ba9fee9ee49ab34063a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a><span data-ttu-id="c7a25-102">ICorProfilerCallback::RemotingServerSendingReply Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c7a25-102">ICorProfilerCallback::RemotingServerSendingReply Method</span></span>
<span data-ttu-id="c7a25-103">Profil Oluşturucu işlemi bir uzak yöntem çağırma isteği işlemi tamamladı ve yanıt bir kanal üzerinden iletilmek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="c7a25-103">Notifies the profiler that the process has finished processing a remote method invocation request and is about to transmit the reply through a channel.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7a25-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7a25-104">Syntax</span></span>  
  
```  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c7a25-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c7a25-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="c7a25-106">[in] Sağlanan değerle karşılık gelecek bir GUID gösteren bir işaretçi [Icorprofilercallback::remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) Bu koşullar altında:</span><span class="sxs-lookup"><span data-stu-id="c7a25-106">[in] A pointer to a GUID that will correspond with the value provided in [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="c7a25-107">Remoting GUID tanımlama bilgilerini etkindir.</span><span class="sxs-lookup"><span data-stu-id="c7a25-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="c7a25-108">Kanal ileti iletilirken başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="c7a25-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="c7a25-109">GUID tanımlama bilgileri için istemci tarafı işlemi üzerinde etkindir.</span><span class="sxs-lookup"><span data-stu-id="c7a25-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="c7a25-110">Bu, uzak çağrıları ve bir mantıksal çağrı yığını oluşturulmasını kolay eşlemeye izin verir.</span><span class="sxs-lookup"><span data-stu-id="c7a25-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="c7a25-111">[in] Bir değer `true` çağrısı, zaman uyumsuz Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="c7a25-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7a25-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c7a25-112">Requirements</span></span>  
 <span data-ttu-id="c7a25-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7a25-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7a25-114">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c7a25-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c7a25-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7a25-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7a25-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7a25-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7a25-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c7a25-117">See Also</span></span>  
 [<span data-ttu-id="c7a25-118">Icorprofilercallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7a25-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
