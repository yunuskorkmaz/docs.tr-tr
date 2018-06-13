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
ms.openlocfilehash: 98563c175f12ad1ff25e1f578270fe1099175487
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453782"
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a><span data-ttu-id="16b81-102">ICorProfilerCallback::RemotingServerSendingReply Yöntemi</span><span class="sxs-lookup"><span data-stu-id="16b81-102">ICorProfilerCallback::RemotingServerSendingReply Method</span></span>
<span data-ttu-id="16b81-103">Profil Oluşturucu işlemi bir uzak yöntem çağırma isteği işlemi tamamladı ve yanıt bir kanal üzerinden iletilmek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="16b81-103">Notifies the profiler that the process has finished processing a remote method invocation request and is about to transmit the reply through a channel.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16b81-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16b81-104">Syntax</span></span>  
  
```  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="16b81-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="16b81-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="16b81-106">[in] Sağlanan değerle karşılık gelecek bir GUID gösteren bir işaretçi [Icorprofilercallback::remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) Bu koşullar altında:</span><span class="sxs-lookup"><span data-stu-id="16b81-106">[in] A pointer to a GUID that will correspond with the value provided in [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="16b81-107">Remoting GUID tanımlama bilgilerini etkindir.</span><span class="sxs-lookup"><span data-stu-id="16b81-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="16b81-108">Kanal ileti iletilirken başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="16b81-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="16b81-109">GUID tanımlama bilgileri için istemci tarafı işlemi üzerinde etkindir.</span><span class="sxs-lookup"><span data-stu-id="16b81-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="16b81-110">Bu, uzak çağrıları ve bir mantıksal çağrı yığını oluşturulmasını kolay eşlemeye izin verir.</span><span class="sxs-lookup"><span data-stu-id="16b81-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="16b81-111">[in] Bir değer `true` çağrısı, zaman uyumsuz Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="16b81-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16b81-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="16b81-112">Requirements</span></span>  
 <span data-ttu-id="16b81-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16b81-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16b81-114">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="16b81-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="16b81-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16b81-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16b81-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16b81-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16b81-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="16b81-117">See Also</span></span>  
 [<span data-ttu-id="16b81-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="16b81-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
