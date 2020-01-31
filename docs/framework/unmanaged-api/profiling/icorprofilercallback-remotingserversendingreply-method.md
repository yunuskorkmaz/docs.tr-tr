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
ms.openlocfilehash: f77901623ef4df7b43276c18a910cf62fcc4451d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865980"
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a><span data-ttu-id="e1ab2-102">ICorProfilerCallback::RemotingServerSendingReply Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e1ab2-102">ICorProfilerCallback::RemotingServerSendingReply Method</span></span>
<span data-ttu-id="e1ab2-103">Profil oluşturucuya işlemin uzak yöntem çağırma isteğini işlemeyi tamamladığını ve yanıtı bir kanaldan iletmek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="e1ab2-103">Notifies the profiler that the process has finished processing a remote method invocation request and is about to transmit the reply through a channel.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1ab2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e1ab2-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1ab2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e1ab2-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="e1ab2-106">'ndaki Şu koşullarda [ICorProfilerCallback:: RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) içinde belirtilen değere karşılık gelen bir GUID işaretçisi:</span><span class="sxs-lookup"><span data-stu-id="e1ab2-106">[in] A pointer to a GUID that will correspond with the value provided in [ICorProfilerCallback::RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="e1ab2-107">Uzaktan iletişim GUID tanımlama bilgileri etkin.</span><span class="sxs-lookup"><span data-stu-id="e1ab2-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="e1ab2-108">Kanal, iletiyi iletmede başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="e1ab2-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="e1ab2-109">GUID tanımlama bilgileri, istemci tarafı işleminde etkindir.</span><span class="sxs-lookup"><span data-stu-id="e1ab2-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="e1ab2-110">Bu, uzaktan iletişim çağrılarının ve mantıksal çağrı yığınının oluşturulmasına kolay bir şekilde eşleştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e1ab2-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="e1ab2-111">'ndaki Çağrı zaman uyumsuz ise `true` bir değer; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="e1ab2-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1ab2-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e1ab2-112">Requirements</span></span>  
 <span data-ttu-id="e1ab2-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1ab2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1ab2-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e1ab2-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e1ab2-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e1ab2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1ab2-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1ab2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1ab2-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1ab2-117">See also</span></span>

- [<span data-ttu-id="e1ab2-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e1ab2-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
