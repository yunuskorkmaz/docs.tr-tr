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
ms.openlocfilehash: f7a943627e2087e6b8c78ced9fc32824843d44fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175141"
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a><span data-ttu-id="36c8c-102">ICorProfilerCallback::RemotingClientReceivingReply Yöntemi</span><span class="sxs-lookup"><span data-stu-id="36c8c-102">ICorProfilerCallback::RemotingClientReceivingReply Method</span></span>
<span data-ttu-id="36c8c-103">Profiloluşturucuya, remoting çağrısının sunucu tarafındaki bölümünün tamamlandığını ve istemcinin şimdi yanıtı aldığını ve işlemek üzere olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="36c8c-103">Notifies the profiler that the server-side portion of a remoting call has completed and the client is now receiving and about to process the reply.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36c8c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="36c8c-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);
```  
  
## <a name="parameters"></a><span data-ttu-id="36c8c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="36c8c-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="36c8c-106">[içinde] Bu koşullar altında ICorProfilerCallback sağlanan değer ile karşılık gelecek bir [değer::RemotingServerSendingReply:](icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="36c8c-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="36c8c-107">GUID tanımlama bilgilerini remoting etkindir.</span><span class="sxs-lookup"><span data-stu-id="36c8c-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="36c8c-108">Kanal iletiyi iletmede başarılı dır.</span><span class="sxs-lookup"><span data-stu-id="36c8c-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="36c8c-109">GUID tanımlama bilgileri sunucu tarafında etkindir.</span><span class="sxs-lookup"><span data-stu-id="36c8c-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="36c8c-110">Bu, remoting çağrılarının kolay eşleşmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="36c8c-110">This allows easy pairing of remoting calls.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="36c8c-111">[içinde] Arama nın `true` eşzamanlı olması durumunda ki değer; aksi `false`takdirde, .</span><span class="sxs-lookup"><span data-stu-id="36c8c-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36c8c-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="36c8c-112">Requirements</span></span>  
 <span data-ttu-id="36c8c-113">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36c8c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36c8c-114">**Üstbilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="36c8c-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="36c8c-115">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36c8c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36c8c-116">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36c8c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36c8c-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36c8c-117">See also</span></span>

- [<span data-ttu-id="36c8c-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="36c8c-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
