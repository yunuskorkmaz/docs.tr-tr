---
title: ICorProfilerCallback::RemotingClientSendingMessage Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientSendingMessage
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientSendingMessage
helpviewer_keywords:
- RemotingClientSendingMessage method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientSendingMessage method [.NET Framework profiling]
ms.assetid: 54d9a5a5-3877-49c1-a503-ce7c7943bc2a
topic_type:
- apiref
ms.openlocfilehash: ae9cb089ad6c0b0422063d3db413b97eb6ff1405
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445791"
---
# <a name="icorprofilercallbackremotingclientsendingmessage-method"></a><span data-ttu-id="1d94c-102">ICorProfilerCallback::RemotingClientSendingMessage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1d94c-102">ICorProfilerCallback::RemotingClientSendingMessage Method</span></span>
<span data-ttu-id="1d94c-103">Profil oluşturucuyu istemcinin sunucuya bir istek gönderdiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="1d94c-103">Notifies the profiler that the client is sending a request to the server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d94c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1d94c-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d94c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1d94c-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="1d94c-106">'ndaki Şu koşullarda [ICorProfilerCallback:: RemotingServerReceivingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md) içinde belirtilen değere karşılık gelen bir değer:</span><span class="sxs-lookup"><span data-stu-id="1d94c-106">[in] A value that corresponds with the value provided in [ICorProfilerCallback::RemotingServerReceivingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="1d94c-107">Uzaktan iletişim GUID tanımlama bilgileri etkin.</span><span class="sxs-lookup"><span data-stu-id="1d94c-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="1d94c-108">Kanal, iletiyi iletmede başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="1d94c-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="1d94c-109">GUID tanımlama bilgileri, sunucu tarafı işleminde etkindir.</span><span class="sxs-lookup"><span data-stu-id="1d94c-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="1d94c-110">Bu, uzaktan iletişim çağrılarının ve mantıksal çağrı yığınının oluşturulmasına kolay bir şekilde eşleştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="1d94c-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="1d94c-111">'ndaki Çağrı zaman uyumsuz ise `true` bir değer; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="1d94c-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d94c-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1d94c-112">Requirements</span></span>  
 <span data-ttu-id="1d94c-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d94c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d94c-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1d94c-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1d94c-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1d94c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d94c-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d94c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d94c-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d94c-117">See also</span></span>

- [<span data-ttu-id="1d94c-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1d94c-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
