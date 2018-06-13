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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 14717b67db03b941d33b5df61c64b5df078adaa2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451434"
---
# <a name="icorprofilercallbackremotingclientsendingmessage-method"></a><span data-ttu-id="6ee5c-102">ICorProfilerCallback::RemotingClientSendingMessage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6ee5c-102">ICorProfilerCallback::RemotingClientSendingMessage Method</span></span>
<span data-ttu-id="6ee5c-103">Profil Oluşturucu istemci sunucuya istek gönderilirken bildirir.</span><span class="sxs-lookup"><span data-stu-id="6ee5c-103">Notifies the profiler that the client is sending a request to the server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ee5c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6ee5c-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6ee5c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6ee5c-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="6ee5c-106">[in] Karşılık gelen bir değer olarak sağlanan değerle birlikte [Icorprofilercallback::remotingserverreceivingmessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md) Bu koşullar altında:</span><span class="sxs-lookup"><span data-stu-id="6ee5c-106">[in] A value that corresponds with the value provided in [ICorProfilerCallback::RemotingServerReceivingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="6ee5c-107">Remoting GUID tanımlama bilgilerini etkindir.</span><span class="sxs-lookup"><span data-stu-id="6ee5c-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="6ee5c-108">Kanal ileti iletilirken başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="6ee5c-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="6ee5c-109">GUID tanımlama bilgileri sunucu tarafı işlemini üzerinde etkindir.</span><span class="sxs-lookup"><span data-stu-id="6ee5c-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="6ee5c-110">Bu, uzak çağrıları ve bir mantıksal çağrı yığını oluşturulmasını kolay eşlemeye izin verir.</span><span class="sxs-lookup"><span data-stu-id="6ee5c-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="6ee5c-111">[in] Bir değer `true` çağrısı, zaman uyumsuz Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="6ee5c-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ee5c-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6ee5c-112">Requirements</span></span>  
 <span data-ttu-id="6ee5c-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ee5c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ee5c-114">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6ee5c-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6ee5c-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6ee5c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6ee5c-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ee5c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ee5c-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6ee5c-117">See Also</span></span>  
 [<span data-ttu-id="6ee5c-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6ee5c-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
