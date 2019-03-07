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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 655b2af2efcaba82af46e92ae94abf3a4adc349c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500414"
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a><span data-ttu-id="9bbc8-102">ICorProfilerCallback::RemotingServerSendingReply Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9bbc8-102">ICorProfilerCallback::RemotingServerSendingReply Method</span></span>
<span data-ttu-id="9bbc8-103">Profil Oluşturucu işlemi bir uzak yöntem çağırma isteği işlemeyi tamamladıktan ve yanıt bir kanal üzerinden iletilmek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="9bbc8-103">Notifies the profiler that the process has finished processing a remote method invocation request and is about to transmit the reply through a channel.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bbc8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9bbc8-104">Syntax</span></span>  
  
```  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9bbc8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9bbc8-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="9bbc8-106">[in] Sağlanan değerle karşılık gelecek bir GUID işaretçisi [Icorprofilercallback::remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) Bu koşullar altında:</span><span class="sxs-lookup"><span data-stu-id="9bbc8-106">[in] A pointer to a GUID that will correspond with the value provided in [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="9bbc8-107">Uzaktan iletişim GUID tanımlama bilgilerinin etkin olur.</span><span class="sxs-lookup"><span data-stu-id="9bbc8-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="9bbc8-108">Kanal ileti iletilirken başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="9bbc8-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="9bbc8-109">GUID tanımlama bilgileri istemci tarafı işlemini üzerinde etkindir.</span><span class="sxs-lookup"><span data-stu-id="9bbc8-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="9bbc8-110">Bu, uzak hizmet çağrıları ve bir mantıksal çağrı yığını oluşturulmasını kolay eşlemeye izin verir.</span><span class="sxs-lookup"><span data-stu-id="9bbc8-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="9bbc8-111">[in] Bir değer `true` çağrısı ise, zaman uyumsuz; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="9bbc8-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bbc8-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9bbc8-112">Requirements</span></span>  
 <span data-ttu-id="9bbc8-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bbc8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bbc8-114">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9bbc8-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9bbc8-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9bbc8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9bbc8-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bbc8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bbc8-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9bbc8-117">See also</span></span>
- [<span data-ttu-id="9bbc8-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9bbc8-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
