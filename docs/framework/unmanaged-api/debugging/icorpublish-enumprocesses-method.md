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
ms.openlocfilehash: 2779138a0999e34ad6424d76ddfebbcfdf611d58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422903"
---
# <a name="icorpublishenumprocesses-method"></a><span data-ttu-id="2991a-102">ICorPublish::EnumProcesses Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2991a-102">ICorPublish::EnumProcesses Method</span></span>
<span data-ttu-id="2991a-103">Bu bilgisayarda çalışan yönetilen işlemler için bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="2991a-103">Gets an enumerator for the managed processes running on this computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2991a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2991a-104">Syntax</span></span>  
  
```  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2991a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2991a-105">Parameters</span></span>  
 `Type`  
 <span data-ttu-id="2991a-106">Değerini [COR_PUB_ENUMPROCESS](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md) alınacak işlemi türünü belirtir numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="2991a-106">A value of the [COR_PUB_ENUMPROCESS](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md) enumeration that specifies the type of process to be retrieved.</span></span> <span data-ttu-id="2991a-107">Geçerli sürümde, yalnızca COR_PUB_MANAGEDONLY geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="2991a-107">In the current version, only COR_PUB_MANAGEDONLY is valid.</span></span>  
  
 `ppIEnum`  
 <span data-ttu-id="2991a-108">Adresine bir işaretçi bir [Icorpublishprocessenum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) işlemlerin Numaralandırıcı olan örneği.</span><span class="sxs-lookup"><span data-stu-id="2991a-108">A pointer to the address of an [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance that is the enumerator of the processes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2991a-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2991a-109">Remarks</span></span>  
 <span data-ttu-id="2991a-110">Numaralandırıcının koleksiyonu işlemlerinin ne zaman çalışan işlemler üzerinde bir anlık görüntü tabanlı `EnumProcesses` yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2991a-110">The enumerator's collection of processes is based on a snapshot of the processes that are running when the `EnumProcesses` method is called.</span></span> <span data-ttu-id="2991a-111">Numaralayıcı önce sonlandırma veya sonrasında herhangi bir işlem içermeyecek `EnumProcesses` olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="2991a-111">The enumerator will not include any processes that terminate before or start after `EnumProcesses` is called.</span></span>  
  
 <span data-ttu-id="2991a-112">`EnumProcesses` Yöntemi çağrılabilir birden çok kez bu [Icorpublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md) işlemleri yeni güncel bir koleksiyonunu oluşturmak için örnek.</span><span class="sxs-lookup"><span data-stu-id="2991a-112">The `EnumProcesses` method may be called more than once on this [ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md) instance to create a new up-to-date collection of processes.</span></span> <span data-ttu-id="2991a-113">Var olan koleksiyonları sonraki çağrılar tarafından etkilenmez `EnumProcesses` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2991a-113">Existing collections will not be affected by subsequent calls of the `EnumProcesses` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2991a-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2991a-114">Requirements</span></span>  
 <span data-ttu-id="2991a-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2991a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2991a-116">**Başlık:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="2991a-116">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="2991a-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2991a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2991a-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2991a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2991a-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2991a-119">See Also</span></span>  
 [<span data-ttu-id="2991a-120">ICorPublish Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2991a-120">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)
