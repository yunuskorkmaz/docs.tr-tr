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
ms.openlocfilehash: 4729a8d3ac2c6f7ec51a032a07ebfd1c2838cb9a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782903"
---
# <a name="icorprofilercallbackremotingclientsendingmessage-method"></a><span data-ttu-id="40372-102">ICorProfilerCallback::RemotingClientSendingMessage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="40372-102">ICorProfilerCallback::RemotingClientSendingMessage Method</span></span>
<span data-ttu-id="40372-103">Profil Oluşturucu, istemci sunucuya istek göndermeden bildirir.</span><span class="sxs-lookup"><span data-stu-id="40372-103">Notifies the profiler that the client is sending a request to the server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40372-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="40372-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40372-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="40372-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="40372-106">[in] Karşılık gelen bir değer olarak sağlanan değer ile [Icorprofilercallback::remotingserverreceivingmessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md) Bu koşullar altında:</span><span class="sxs-lookup"><span data-stu-id="40372-106">[in] A value that corresponds with the value provided in [ICorProfilerCallback::RemotingServerReceivingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="40372-107">Uzaktan iletişim GUID tanımlama bilgilerinin etkin olur.</span><span class="sxs-lookup"><span data-stu-id="40372-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="40372-108">Kanal ileti iletilirken başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="40372-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="40372-109">GUID tanımlama bilgileri sunucu tarafı işlemini üzerinde etkindir.</span><span class="sxs-lookup"><span data-stu-id="40372-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="40372-110">Bu, uzak hizmet çağrıları ve bir mantıksal çağrı yığını oluşturulmasını kolay eşlemeye izin verir.</span><span class="sxs-lookup"><span data-stu-id="40372-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="40372-111">[in] Bir değer `true` çağrısı ise, zaman uyumsuz; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="40372-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40372-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="40372-112">Requirements</span></span>  
 <span data-ttu-id="40372-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40372-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40372-114">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="40372-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="40372-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="40372-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40372-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40372-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40372-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40372-117">See also</span></span>

- [<span data-ttu-id="40372-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="40372-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
