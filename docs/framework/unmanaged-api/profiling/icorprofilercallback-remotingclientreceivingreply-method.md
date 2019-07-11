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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ff18d52091ca75152c20667d1ec1b024f44d6129
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782913"
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a><span data-ttu-id="9681d-102">ICorProfilerCallback::RemotingClientReceivingReply Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9681d-102">ICorProfilerCallback::RemotingClientReceivingReply Method</span></span>
<span data-ttu-id="9681d-103">Uzaktan iletişim çağrısı sunucu tarafı kısmı tamamlandı ve istemci artık alma profil oluşturucu bildirir ve yanıt işlenecek.</span><span class="sxs-lookup"><span data-stu-id="9681d-103">Notifies the profiler that the server-side portion of a remoting call has completed and the client is now receiving and about to process the reply.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9681d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9681d-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);   
```  
  
## <a name="parameters"></a><span data-ttu-id="9681d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9681d-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="9681d-106">[in] Sağlanan değer karşılık gelecek bir değerle [Icorprofilercallback::remotingserversendingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md) Bu koşullar altında:</span><span class="sxs-lookup"><span data-stu-id="9681d-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="9681d-107">Uzaktan iletişim GUID tanımlama bilgilerinin etkin olur.</span><span class="sxs-lookup"><span data-stu-id="9681d-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="9681d-108">Kanal ileti iletilirken başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="9681d-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="9681d-109">GUID tanımlama bilgileri sunucu tarafı işlemini üzerinde etkindir.</span><span class="sxs-lookup"><span data-stu-id="9681d-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="9681d-110">Bu, uzak hizmet çağrıları kolay eşlemeye izin verir.</span><span class="sxs-lookup"><span data-stu-id="9681d-110">This allows easy pairing of remoting calls.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="9681d-111">[in] Bir değer `true` çağrısı ise, zaman uyumsuz; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="9681d-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9681d-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9681d-112">Requirements</span></span>  
 <span data-ttu-id="9681d-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9681d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9681d-114">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9681d-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9681d-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9681d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9681d-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9681d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9681d-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9681d-117">See also</span></span>

- [<span data-ttu-id="9681d-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9681d-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
