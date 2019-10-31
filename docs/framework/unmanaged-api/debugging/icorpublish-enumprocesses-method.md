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
ms.openlocfilehash: 5f0dd814ad5adfa1b0dd7199530a3f993634a548
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121792"
---
# <a name="icorpublishenumprocesses-method"></a><span data-ttu-id="2b760-102">ICorPublish::EnumProcesses Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2b760-102">ICorPublish::EnumProcesses Method</span></span>
<span data-ttu-id="2b760-103">Bu bilgisayarda çalışan yönetilen işlemlere yönelik bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="2b760-103">Gets an enumerator for the managed processes running on this computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b760-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2b760-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b760-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2b760-105">Parameters</span></span>  
 `Type`  
 <span data-ttu-id="2b760-106">Alınacak işlemin türünü belirten [COR_PUB_ENUMPROCESS](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="2b760-106">A value of the [COR_PUB_ENUMPROCESS](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md) enumeration that specifies the type of process to be retrieved.</span></span> <span data-ttu-id="2b760-107">Geçerli sürümde yalnızca COR_PUB_MANAGEDONLY geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="2b760-107">In the current version, only COR_PUB_MANAGEDONLY is valid.</span></span>  
  
 `ppIEnum`  
 <span data-ttu-id="2b760-108">İşlemlerin numaralandırıcısı olan [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) örneğinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2b760-108">A pointer to the address of an [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance that is the enumerator of the processes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b760-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2b760-109">Remarks</span></span>  
 <span data-ttu-id="2b760-110">Numaralandırıcının işlem koleksiyonu, `EnumProcesses` yöntemi çağrıldığında çalışan işlemlerin anlık görüntüsünü temel alır.</span><span class="sxs-lookup"><span data-stu-id="2b760-110">The enumerator's collection of processes is based on a snapshot of the processes that are running when the `EnumProcesses` method is called.</span></span> <span data-ttu-id="2b760-111">Numaralandırıcı, `EnumProcesses` çağrıldıktan sonra, önce veya başlamadan sonra sona erecek herhangi bir işlem içermez.</span><span class="sxs-lookup"><span data-stu-id="2b760-111">The enumerator will not include any processes that terminate before or start after `EnumProcesses` is called.</span></span>  
  
 <span data-ttu-id="2b760-112">`EnumProcesses` yöntemi bu [ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md) örneğinde birden çok kez çağrılabilir ve bu işlemlerin yeni bir güncellik koleksiyonu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2b760-112">The `EnumProcesses` method may be called more than once on this [ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md) instance to create a new up-to-date collection of processes.</span></span> <span data-ttu-id="2b760-113">Mevcut koleksiyonlar `EnumProcesses` yönteminin sonraki çağrılarından etkilenmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="2b760-113">Existing collections will not be affected by subsequent calls of the `EnumProcesses` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b760-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2b760-114">Requirements</span></span>  
 <span data-ttu-id="2b760-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b760-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b760-116">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="2b760-116">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="2b760-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2b760-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b760-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b760-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b760-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b760-119">See also</span></span>

- [<span data-ttu-id="2b760-120">ICorPublish Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2b760-120">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)
