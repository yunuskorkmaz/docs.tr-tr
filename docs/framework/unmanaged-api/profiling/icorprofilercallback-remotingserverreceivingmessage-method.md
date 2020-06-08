---
title: ICorProfilerCallback::RemotingServerReceivingMessage Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerReceivingMessage
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage
helpviewer_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage method [.NET Framework profiling]
- RemotingServerReceivingMessage method [.NET Framework profiling]
ms.assetid: 5604d21f-e6b7-490e-b469-42122a7568e1
topic_type:
- apiref
ms.openlocfilehash: 157e6bc6cb9603fa9558ad6d39f0b086849fc7b0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499902"
---
# <a name="icorprofilercallbackremotingserverreceivingmessage-method"></a><span data-ttu-id="dc721-102">ICorProfilerCallback::RemotingServerReceivingMessage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dc721-102">ICorProfilerCallback::RemotingServerReceivingMessage Method</span></span>
<span data-ttu-id="dc721-103">Profil oluşturucuya işlemin bir uzak yöntem çağırma veya etkinleştirme isteği aldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="dc721-103">Notifies the profiler that the process has received a remote method invocation or activation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc721-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="dc721-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc721-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dc721-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="dc721-106">'ndaki Şu koşullarda [ICorProfilerCallback:: RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md) içinde belirtilen değere karşılık gelen bir değer:</span><span class="sxs-lookup"><span data-stu-id="dc721-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="dc721-107">Uzaktan iletişim GUID tanımlama bilgileri etkin.</span><span class="sxs-lookup"><span data-stu-id="dc721-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="dc721-108">Kanal, iletiyi iletmede başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="dc721-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="dc721-109">GUID tanımlama bilgileri, istemci tarafı işleminde etkindir.</span><span class="sxs-lookup"><span data-stu-id="dc721-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="dc721-110">Bu, uzaktan iletişim çağrılarının ve mantıksal çağrı yığınının oluşturulmasına kolay bir şekilde eşleştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc721-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="dc721-111">'ndaki `true`Çağrının zaman uyumsuz olduğu bir değer; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="dc721-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc721-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dc721-112">Remarks</span></span>  
 <span data-ttu-id="dc721-113">İleti isteği zaman uyumsuz ise, istek herhangi bir rastgele iş parçacığı tarafından hizmet verebilir.</span><span class="sxs-lookup"><span data-stu-id="dc721-113">If the message request is asynchronous, the request can be serviced by any arbitrary thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc721-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dc721-114">Requirements</span></span>  
 <span data-ttu-id="dc721-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc721-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc721-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="dc721-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dc721-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="dc721-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc721-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc721-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc721-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc721-119">See also</span></span>

- [<span data-ttu-id="dc721-120">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dc721-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
