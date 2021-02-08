---
description: ': ICorProfilerCallback:: RemotingClientReceivingReply yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerCallback::RemotingClientReceivingReply Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientReceivingReply
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientReceivingReply
helpviewer_keywords:
- ICorProfilerCallback::RemotingClientReceivingReply method [.NET Framework profiling]
- RemotingClientReceivingReply method [.NET Framework profiling]
ms.assetid: 15cfc300-8231-4ecb-9a04-19851c3eb484
topic_type:
- apiref
ms.openlocfilehash: 4c1d42baa9f4381b66c9be75afa239899ae81b81
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788949"
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a><span data-ttu-id="142a1-103">ICorProfilerCallback::RemotingClientReceivingReply Yöntemi</span><span class="sxs-lookup"><span data-stu-id="142a1-103">ICorProfilerCallback::RemotingClientReceivingReply Method</span></span>

<span data-ttu-id="142a1-104">Profil oluşturucuya, uzaktan iletişim çağrısının sunucu tarafı bölümünün tamamlandığını ve istemcinin artık yanıtı aldığını ve yanıt işlemesini bildirir.</span><span class="sxs-lookup"><span data-stu-id="142a1-104">Notifies the profiler that the server-side portion of a remoting call has completed and the client is now receiving and about to process the reply.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="142a1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="142a1-105">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);
```  
  
## <a name="parameters"></a><span data-ttu-id="142a1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="142a1-106">Parameters</span></span>  

 `pCookie`  
 <span data-ttu-id="142a1-107">'ndaki Şu koşullarda [ICorProfilerCallback:: RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md) içinde belirtilen değere karşılık gelen bir değer:</span><span class="sxs-lookup"><span data-stu-id="142a1-107">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="142a1-108">Uzaktan iletişim GUID tanımlama bilgileri etkin.</span><span class="sxs-lookup"><span data-stu-id="142a1-108">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="142a1-109">Kanal, iletiyi iletmede başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="142a1-109">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="142a1-110">GUID tanımlama bilgileri, sunucu tarafı işleminde etkindir.</span><span class="sxs-lookup"><span data-stu-id="142a1-110">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="142a1-111">Bu, uzaktan iletişim çağrılarının kolayca eşleştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="142a1-111">This allows easy pairing of remoting calls.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="142a1-112">'ndaki `true` Çağrının zaman uyumsuz olduğu bir değer; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="142a1-112">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="142a1-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="142a1-113">Requirements</span></span>  

 <span data-ttu-id="142a1-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="142a1-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="142a1-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="142a1-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="142a1-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="142a1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="142a1-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="142a1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="142a1-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="142a1-118">See also</span></span>

- [<span data-ttu-id="142a1-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="142a1-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
