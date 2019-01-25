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
ms.openlocfilehash: 6bf9f8241459f566eb0724596640fd6036ae799a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659624"
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a><span data-ttu-id="a2de5-102">ICorProfilerCallback::RemotingServerSendingReply Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a2de5-102">ICorProfilerCallback::RemotingServerSendingReply Method</span></span>
<span data-ttu-id="a2de5-103">Profil Oluşturucu işlemi bir uzak yöntem çağırma isteği işlemeyi tamamladıktan ve yanıt bir kanal üzerinden iletilmek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="a2de5-103">Notifies the profiler that the process has finished processing a remote method invocation request and is about to transmit the reply through a channel.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2de5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a2de5-104">Syntax</span></span>  
  
```  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a2de5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a2de5-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="a2de5-106">[in] Sağlanan değerle karşılık gelecek bir GUID işaretçisi [Icorprofilercallback::remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) Bu koşullar altında:</span><span class="sxs-lookup"><span data-stu-id="a2de5-106">[in] A pointer to a GUID that will correspond with the value provided in [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="a2de5-107">Uzaktan iletişim GUID tanımlama bilgilerinin etkin olur.</span><span class="sxs-lookup"><span data-stu-id="a2de5-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="a2de5-108">Kanal ileti iletilirken başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="a2de5-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="a2de5-109">GUID tanımlama bilgileri istemci tarafı işlemini üzerinde etkindir.</span><span class="sxs-lookup"><span data-stu-id="a2de5-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="a2de5-110">Bu, uzak hizmet çağrıları ve bir mantıksal çağrı yığını oluşturulmasını kolay eşlemeye izin verir.</span><span class="sxs-lookup"><span data-stu-id="a2de5-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="a2de5-111">[in] Bir değer `true` çağrısı ise, zaman uyumsuz; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="a2de5-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2de5-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a2de5-112">Requirements</span></span>  
 <span data-ttu-id="a2de5-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2de5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2de5-114">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a2de5-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a2de5-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2de5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2de5-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2de5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2de5-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2de5-117">See also</span></span>
- [<span data-ttu-id="a2de5-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a2de5-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
