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
ms.openlocfilehash: 62c2774701b0bb4bc322d689fec43e312bc776a3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662912"
---
# <a name="icorprofilercallbackremotingclientsendingmessage-method"></a><span data-ttu-id="fca91-102">ICorProfilerCallback::RemotingClientSendingMessage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fca91-102">ICorProfilerCallback::RemotingClientSendingMessage Method</span></span>
<span data-ttu-id="fca91-103">Profil Oluşturucu, istemci sunucuya istek göndermeden bildirir.</span><span class="sxs-lookup"><span data-stu-id="fca91-103">Notifies the profiler that the client is sending a request to the server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fca91-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fca91-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fca91-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fca91-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="fca91-106">[in] Karşılık gelen bir değer olarak sağlanan değer ile [Icorprofilercallback::remotingserverreceivingmessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md) Bu koşullar altında:</span><span class="sxs-lookup"><span data-stu-id="fca91-106">[in] A value that corresponds with the value provided in [ICorProfilerCallback::RemotingServerReceivingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="fca91-107">Uzaktan iletişim GUID tanımlama bilgilerinin etkin olur.</span><span class="sxs-lookup"><span data-stu-id="fca91-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="fca91-108">Kanal ileti iletilirken başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="fca91-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="fca91-109">GUID tanımlama bilgileri sunucu tarafı işlemini üzerinde etkindir.</span><span class="sxs-lookup"><span data-stu-id="fca91-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="fca91-110">Bu, uzak hizmet çağrıları ve bir mantıksal çağrı yığını oluşturulmasını kolay eşlemeye izin verir.</span><span class="sxs-lookup"><span data-stu-id="fca91-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="fca91-111">[in] Bir değer `true` çağrısı ise, zaman uyumsuz; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="fca91-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fca91-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fca91-112">Requirements</span></span>  
 <span data-ttu-id="fca91-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fca91-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fca91-114">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fca91-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fca91-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fca91-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fca91-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fca91-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fca91-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fca91-117">See also</span></span>

- [<span data-ttu-id="fca91-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fca91-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
