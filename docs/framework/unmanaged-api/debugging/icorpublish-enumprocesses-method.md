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
ms.openlocfilehash: 297f672097dd6561a971608f368369c623532907
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716921"
---
# <a name="icorpublishenumprocesses-method"></a><span data-ttu-id="60a90-102">ICorPublish::EnumProcesses Yöntemi</span><span class="sxs-lookup"><span data-stu-id="60a90-102">ICorPublish::EnumProcesses Method</span></span>

<span data-ttu-id="60a90-103">Bu bilgisayarda çalışan yönetilen işlemlere yönelik bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="60a90-103">Gets an enumerator for the managed processes running on this computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60a90-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="60a90-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60a90-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="60a90-105">Parameters</span></span>  

 `Type`  
 <span data-ttu-id="60a90-106">Alınacak işlemin türünü belirten [COR_PUB_ENUMPROCESS](cor-pub-enumprocess-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="60a90-106">A value of the [COR_PUB_ENUMPROCESS](cor-pub-enumprocess-enumeration.md) enumeration that specifies the type of process to be retrieved.</span></span> <span data-ttu-id="60a90-107">Geçerli sürümde yalnızca COR_PUB_MANAGEDONLY geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="60a90-107">In the current version, only COR_PUB_MANAGEDONLY is valid.</span></span>  
  
 `ppIEnum`  
 <span data-ttu-id="60a90-108">İşlemlerin numaralandırıcısı olan [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) örneğinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="60a90-108">A pointer to the address of an [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) instance that is the enumerator of the processes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60a90-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="60a90-109">Remarks</span></span>  

 <span data-ttu-id="60a90-110">Numaralandırıcının işlem koleksiyonu, yöntemi çağrıldığında çalışan işlemlerin anlık görüntüsünü temel alır `EnumProcesses` .</span><span class="sxs-lookup"><span data-stu-id="60a90-110">The enumerator's collection of processes is based on a snapshot of the processes that are running when the `EnumProcesses` method is called.</span></span> <span data-ttu-id="60a90-111">Numaralandırıcı çağrılmadan önce ya da başlamadan önce sonlanacak herhangi bir işlem içermez `EnumProcesses` .</span><span class="sxs-lookup"><span data-stu-id="60a90-111">The enumerator will not include any processes that terminate before or start after `EnumProcesses` is called.</span></span>  
  
 <span data-ttu-id="60a90-112">`EnumProcesses`Yöntemi bu [ICorPublish](icorpublish-interface.md) örneğinde birden çok kez çağrılabilir ve bu işlem, yeni bir güncel koleksiyon oluşturur.</span><span class="sxs-lookup"><span data-stu-id="60a90-112">The `EnumProcesses` method may be called more than once on this [ICorPublish](icorpublish-interface.md) instance to create a new up-to-date collection of processes.</span></span> <span data-ttu-id="60a90-113">Mevcut koleksiyonlar, yönteminin sonraki çağrılarından etkilenmeyecektir `EnumProcesses` .</span><span class="sxs-lookup"><span data-stu-id="60a90-113">Existing collections will not be affected by subsequent calls of the `EnumProcesses` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60a90-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="60a90-114">Requirements</span></span>  

 <span data-ttu-id="60a90-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60a90-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60a90-116">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="60a90-116">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="60a90-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="60a90-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60a90-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60a90-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60a90-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60a90-119">See also</span></span>

- [<span data-ttu-id="60a90-120">ICorPublish Arabirimi</span><span class="sxs-lookup"><span data-stu-id="60a90-120">ICorPublish Interface</span></span>](icorpublish-interface.md)
