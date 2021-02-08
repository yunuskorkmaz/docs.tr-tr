---
description: ': ICorProfilerCallback:: RemotingClientSendingMessage yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 3d075b3f3c3ffe63c9d4401bdc182037593b5b19
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788936"
---
# <a name="icorprofilercallbackremotingclientsendingmessage-method"></a><span data-ttu-id="c097d-103">ICorProfilerCallback::RemotingClientSendingMessage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c097d-103">ICorProfilerCallback::RemotingClientSendingMessage Method</span></span>

<span data-ttu-id="c097d-104">Profil oluşturucuyu istemcinin sunucuya bir istek gönderdiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="c097d-104">Notifies the profiler that the client is sending a request to the server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c097d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c097d-105">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c097d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c097d-106">Parameters</span></span>  

 `pCookie`  
 <span data-ttu-id="c097d-107">'ndaki Şu koşullarda [ICorProfilerCallback:: RemotingServerReceivingMessage](icorprofilercallback-remotingserverreceivingmessage-method.md) içinde belirtilen değere karşılık gelen bir değer:</span><span class="sxs-lookup"><span data-stu-id="c097d-107">[in] A value that corresponds with the value provided in [ICorProfilerCallback::RemotingServerReceivingMessage](icorprofilercallback-remotingserverreceivingmessage-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="c097d-108">Uzaktan iletişim GUID tanımlama bilgileri etkin.</span><span class="sxs-lookup"><span data-stu-id="c097d-108">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="c097d-109">Kanal, iletiyi iletmede başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="c097d-109">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="c097d-110">GUID tanımlama bilgileri, sunucu tarafı işleminde etkindir.</span><span class="sxs-lookup"><span data-stu-id="c097d-110">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="c097d-111">Bu, uzaktan iletişim çağrılarının ve mantıksal çağrı yığınının oluşturulmasına kolay bir şekilde eşleştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c097d-111">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="c097d-112">'ndaki `true` Çağrının zaman uyumsuz olduğu bir değer; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="c097d-112">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c097d-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c097d-113">Requirements</span></span>  

 <span data-ttu-id="c097d-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c097d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c097d-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c097d-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c097d-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c097d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c097d-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c097d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c097d-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c097d-118">See also</span></span>

- [<span data-ttu-id="c097d-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c097d-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
