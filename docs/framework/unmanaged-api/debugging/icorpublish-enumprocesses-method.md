---
title: ICorPublish::EnumProcesses Yöntemi
ms.date: 03/30/2017
api_name:
- ICorPublish.EnumProcesses
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::EnumProcesses
helpviewer_keywords:
- ICorPublish::EnumProcesses method [.NET Framework debugging]
- EnumProcesses method [.NET Framework debugging]
ms.assetid: 4ae765f0-93b2-4b6f-aea1-7b0cf44e04a7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 77bae0de732fc8847650b9ce03f8228111a76334
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466524"
---
# <a name="icorpublishenumprocesses-method"></a><span data-ttu-id="19f21-102">ICorPublish::EnumProcesses Yöntemi</span><span class="sxs-lookup"><span data-stu-id="19f21-102">ICorPublish::EnumProcesses Method</span></span>
<span data-ttu-id="19f21-103">Bu bilgisayar üzerinde çalışan yönetilen işlemler için bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="19f21-103">Gets an enumerator for the managed processes running on this computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19f21-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="19f21-104">Syntax</span></span>  
  
```  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19f21-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="19f21-105">Parameters</span></span>  
 `Type`  
 <span data-ttu-id="19f21-106">Değerini [COR_PUB_ENUMPROCESS](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md) alınacak işlem türünü belirten sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="19f21-106">A value of the [COR_PUB_ENUMPROCESS](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md) enumeration that specifies the type of process to be retrieved.</span></span> <span data-ttu-id="19f21-107">Geçerli sürümde, yalnızca COR_PUB_MANAGEDONLY geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="19f21-107">In the current version, only COR_PUB_MANAGEDONLY is valid.</span></span>  
  
 `ppIEnum`  
 <span data-ttu-id="19f21-108">Adresine bir işaretçi bir [Icorpublishprocessenum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) Numaralandırıcı işlemlerin örneği.</span><span class="sxs-lookup"><span data-stu-id="19f21-108">A pointer to the address of an [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance that is the enumerator of the processes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19f21-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="19f21-109">Remarks</span></span>  
 <span data-ttu-id="19f21-110">Numaralandırıcının toplama işlemlerinin ne zaman çalışan işlemler üzerinde bir anlık görüntü alır `EnumProcesses` yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="19f21-110">The enumerator's collection of processes is based on a snapshot of the processes that are running when the `EnumProcesses` method is called.</span></span> <span data-ttu-id="19f21-111">Numaralandırıcı önce sonlandırma veya sonrasında herhangi bir işlem içermez `EnumProcesses` çağrılır.</span><span class="sxs-lookup"><span data-stu-id="19f21-111">The enumerator will not include any processes that terminate before or start after `EnumProcesses` is called.</span></span>  
  
 <span data-ttu-id="19f21-112">`EnumProcesses` Yöntemi çağrılabilir birden çok kez bu [Icorpublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md) işlemlerinin yeni ve güncel bir koleksiyon oluşturmak için örneği.</span><span class="sxs-lookup"><span data-stu-id="19f21-112">The `EnumProcesses` method may be called more than once on this [ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md) instance to create a new up-to-date collection of processes.</span></span> <span data-ttu-id="19f21-113">Mevcut koleksiyonlar sonraki çağrılar tarafından etkilenmez `EnumProcesses` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="19f21-113">Existing collections will not be affected by subsequent calls of the `EnumProcesses` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19f21-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="19f21-114">Requirements</span></span>  
 <span data-ttu-id="19f21-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19f21-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19f21-116">**Üst bilgi:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="19f21-116">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="19f21-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="19f21-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19f21-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19f21-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19f21-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19f21-119">See also</span></span>
- [<span data-ttu-id="19f21-120">ICorPublish Arabirimi</span><span class="sxs-lookup"><span data-stu-id="19f21-120">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)
