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
ms.openlocfilehash: bf59d4e418223fd177bc5e19b173674b78e1f2ba
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499928"
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a><span data-ttu-id="fe389-102">ICorProfilerCallback::RemotingServerSendingReply Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe389-102">ICorProfilerCallback::RemotingServerSendingReply Method</span></span>
<span data-ttu-id="fe389-103">Profil oluşturucuya işlemin uzak yöntem çağırma isteğini işlemeyi tamamladığını ve yanıtı bir kanaldan iletmek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="fe389-103">Notifies the profiler that the process has finished processing a remote method invocation request and is about to transmit the reply through a channel.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe389-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="fe389-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe389-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fe389-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="fe389-106">'ndaki Şu koşullarda [ICorProfilerCallback:: RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) içinde belirtilen değere karşılık gelen bir GUID işaretçisi:</span><span class="sxs-lookup"><span data-stu-id="fe389-106">[in] A pointer to a GUID that will correspond with the value provided in [ICorProfilerCallback::RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="fe389-107">Uzaktan iletişim GUID tanımlama bilgileri etkin.</span><span class="sxs-lookup"><span data-stu-id="fe389-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="fe389-108">Kanal, iletiyi iletmede başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="fe389-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="fe389-109">GUID tanımlama bilgileri, istemci tarafı işleminde etkindir.</span><span class="sxs-lookup"><span data-stu-id="fe389-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="fe389-110">Bu, uzaktan iletişim çağrılarının ve mantıksal çağrı yığınının oluşturulmasına kolay bir şekilde eşleştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe389-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="fe389-111">'ndaki `true`Çağrının zaman uyumsuz olduğu bir değer; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="fe389-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe389-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fe389-112">Requirements</span></span>  
 <span data-ttu-id="fe389-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe389-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe389-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="fe389-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fe389-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fe389-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe389-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe389-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe389-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe389-117">See also</span></span>

- [<span data-ttu-id="fe389-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe389-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
