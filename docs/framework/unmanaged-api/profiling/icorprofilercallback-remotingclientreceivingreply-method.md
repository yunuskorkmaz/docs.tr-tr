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
ms.openlocfilehash: 04956fb5519c66141f4bd7330367f6c78b4e7bc4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453964"
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a><span data-ttu-id="1c4ca-102">ICorProfilerCallback::RemotingClientReceivingReply Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1c4ca-102">ICorProfilerCallback::RemotingClientReceivingReply Method</span></span>
<span data-ttu-id="1c4ca-103">Uzaktan iletişim çağrısı sunucu tarafı kısmı tamamlandı ve istemci şimdi alma profil oluşturucu bildirir ve yanıtı işlemek üzere.</span><span class="sxs-lookup"><span data-stu-id="1c4ca-103">Notifies the profiler that the server-side portion of a remoting call has completed and the client is now receiving and about to process the reply.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c4ca-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1c4ca-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="1c4ca-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1c4ca-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="1c4ca-106">[in] Karşılık gelecek bir değerle sağlanan [Icorprofilercallback::remotingserversendingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md) Bu koşullar altında:</span><span class="sxs-lookup"><span data-stu-id="1c4ca-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="1c4ca-107">Remoting GUID tanımlama bilgilerini etkindir.</span><span class="sxs-lookup"><span data-stu-id="1c4ca-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="1c4ca-108">Kanal ileti iletilirken başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="1c4ca-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="1c4ca-109">GUID tanımlama bilgileri sunucu tarafı işlemini üzerinde etkindir.</span><span class="sxs-lookup"><span data-stu-id="1c4ca-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="1c4ca-110">Bu, kolay remoting çağrıları eşlemeye izin verir.</span><span class="sxs-lookup"><span data-stu-id="1c4ca-110">This allows easy pairing of remoting calls.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="1c4ca-111">[in] Bir değer `true` çağrısı, zaman uyumsuz Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="1c4ca-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c4ca-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1c4ca-112">Requirements</span></span>  
 <span data-ttu-id="1c4ca-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c4ca-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c4ca-114">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1c4ca-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1c4ca-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c4ca-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c4ca-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c4ca-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c4ca-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1c4ca-117">See Also</span></span>  
 [<span data-ttu-id="1c4ca-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1c4ca-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
