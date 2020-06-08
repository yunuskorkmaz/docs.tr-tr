---
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
ms.openlocfilehash: 0a21924008bcbfa0894218f57aee559a564f8003
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499980"
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a><span data-ttu-id="b43cb-102">ICorProfilerCallback::RemotingClientReceivingReply Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b43cb-102">ICorProfilerCallback::RemotingClientReceivingReply Method</span></span>
<span data-ttu-id="b43cb-103">Profil oluşturucuya, uzaktan iletişim çağrısının sunucu tarafı bölümünün tamamlandığını ve istemcinin artık yanıtı aldığını ve yanıt işlemesini bildirir.</span><span class="sxs-lookup"><span data-stu-id="b43cb-103">Notifies the profiler that the server-side portion of a remoting call has completed and the client is now receiving and about to process the reply.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b43cb-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b43cb-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);
```  
  
## <a name="parameters"></a><span data-ttu-id="b43cb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b43cb-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="b43cb-106">'ndaki Şu koşullarda [ICorProfilerCallback:: RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md) içinde belirtilen değere karşılık gelen bir değer:</span><span class="sxs-lookup"><span data-stu-id="b43cb-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="b43cb-107">Uzaktan iletişim GUID tanımlama bilgileri etkin.</span><span class="sxs-lookup"><span data-stu-id="b43cb-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="b43cb-108">Kanal, iletiyi iletmede başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="b43cb-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="b43cb-109">GUID tanımlama bilgileri, sunucu tarafı işleminde etkindir.</span><span class="sxs-lookup"><span data-stu-id="b43cb-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="b43cb-110">Bu, uzaktan iletişim çağrılarının kolayca eşleştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b43cb-110">This allows easy pairing of remoting calls.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="b43cb-111">'ndaki `true`Çağrının zaman uyumsuz olduğu bir değer; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="b43cb-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b43cb-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b43cb-112">Requirements</span></span>  
 <span data-ttu-id="b43cb-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b43cb-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b43cb-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b43cb-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b43cb-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b43cb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b43cb-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b43cb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b43cb-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b43cb-117">See also</span></span>

- [<span data-ttu-id="b43cb-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b43cb-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
