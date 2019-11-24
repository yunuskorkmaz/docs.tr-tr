---
title: ICorProfilerCallback::RemotingServerSendingReply Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerSendingReply
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerSendingReply
helpviewer_keywords:
- RemotingServerSendingReply method [.NET Framework profiling]
- ICorProfilerCallback::RemotingServerSendingReply method [.NET Framework profiling]
ms.assetid: dfe84a19-2e03-4be2-8b25-f02bad38e4a9
topic_type:
- apiref
ms.openlocfilehash: 1aa5a0d20ee87fe4362016ed0d7fa29ef786460e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430722"
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a><span data-ttu-id="3df4a-102">ICorProfilerCallback::RemotingServerSendingReply Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3df4a-102">ICorProfilerCallback::RemotingServerSendingReply Method</span></span>
<span data-ttu-id="3df4a-103">Notifies the profiler that the process has finished processing a remote method invocation request and is about to transmit the reply through a channel.</span><span class="sxs-lookup"><span data-stu-id="3df4a-103">Notifies the profiler that the process has finished processing a remote method invocation request and is about to transmit the reply through a channel.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3df4a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3df4a-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3df4a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3df4a-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="3df4a-106">[in] A pointer to a GUID that will correspond with the value provided in [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) under these conditions:</span><span class="sxs-lookup"><span data-stu-id="3df4a-106">[in] A pointer to a GUID that will correspond with the value provided in [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="3df4a-107">Remoting GUID cookies are active.</span><span class="sxs-lookup"><span data-stu-id="3df4a-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="3df4a-108">The channel succeeds in transmitting the message.</span><span class="sxs-lookup"><span data-stu-id="3df4a-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="3df4a-109">GUID cookies are active on the client-side process.</span><span class="sxs-lookup"><span data-stu-id="3df4a-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="3df4a-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span><span class="sxs-lookup"><span data-stu-id="3df4a-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="3df4a-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span><span class="sxs-lookup"><span data-stu-id="3df4a-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3df4a-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3df4a-112">Requirements</span></span>  
 <span data-ttu-id="3df4a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3df4a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3df4a-114">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3df4a-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3df4a-115">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3df4a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3df4a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3df4a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3df4a-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3df4a-117">See also</span></span>

- [<span data-ttu-id="3df4a-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3df4a-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
