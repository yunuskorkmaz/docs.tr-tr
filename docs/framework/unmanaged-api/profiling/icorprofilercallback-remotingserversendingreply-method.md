---
description: ': ICorProfilerCallback:: RemotingServerSendingReply yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 236a707fcbc051a3d00c408f71f3b4f9f452c220
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788884"
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a><span data-ttu-id="a05ed-103">ICorProfilerCallback::RemotingServerSendingReply Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a05ed-103">ICorProfilerCallback::RemotingServerSendingReply Method</span></span>

<span data-ttu-id="a05ed-104">Profil oluşturucuya işlemin uzak yöntem çağırma isteğini işlemeyi tamamladığını ve yanıtı bir kanaldan iletmek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="a05ed-104">Notifies the profiler that the process has finished processing a remote method invocation request and is about to transmit the reply through a channel.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a05ed-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a05ed-105">Syntax</span></span>  
  
```cpp  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a05ed-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a05ed-106">Parameters</span></span>  

 `pCookie`  
 <span data-ttu-id="a05ed-107">'ndaki Şu koşullarda [ICorProfilerCallback:: RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) içinde belirtilen değere karşılık gelen bir GUID işaretçisi:</span><span class="sxs-lookup"><span data-stu-id="a05ed-107">[in] A pointer to a GUID that will correspond with the value provided in [ICorProfilerCallback::RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="a05ed-108">Uzaktan iletişim GUID tanımlama bilgileri etkin.</span><span class="sxs-lookup"><span data-stu-id="a05ed-108">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="a05ed-109">Kanal, iletiyi iletmede başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="a05ed-109">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="a05ed-110">GUID tanımlama bilgileri, istemci tarafı işleminde etkindir.</span><span class="sxs-lookup"><span data-stu-id="a05ed-110">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="a05ed-111">Bu, uzaktan iletişim çağrılarının ve mantıksal çağrı yığınının oluşturulmasına kolay bir şekilde eşleştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a05ed-111">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="a05ed-112">'ndaki `true` Çağrının zaman uyumsuz olduğu bir değer; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="a05ed-112">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a05ed-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a05ed-113">Requirements</span></span>  

 <span data-ttu-id="a05ed-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a05ed-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a05ed-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a05ed-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a05ed-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a05ed-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a05ed-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a05ed-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a05ed-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a05ed-118">See also</span></span>

- [<span data-ttu-id="a05ed-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a05ed-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
