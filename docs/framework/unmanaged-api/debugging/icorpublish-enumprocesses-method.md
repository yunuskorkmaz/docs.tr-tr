---
description: ': ICorPublish:: EnumProcesses yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 2451f179301eff4caca966568f966d145e269f51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722002"
---
# <a name="icorpublishenumprocesses-method"></a><span data-ttu-id="3ba2f-103">ICorPublish::EnumProcesses Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3ba2f-103">ICorPublish::EnumProcesses Method</span></span>

<span data-ttu-id="3ba2f-104">Bu bilgisayarda çalışan yönetilen işlemlere yönelik bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="3ba2f-104">Gets an enumerator for the managed processes running on this computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ba2f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3ba2f-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ba2f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3ba2f-106">Parameters</span></span>  

 `Type`  
 <span data-ttu-id="3ba2f-107">Alınacak işlemin türünü belirten [COR_PUB_ENUMPROCESS](cor-pub-enumprocess-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="3ba2f-107">A value of the [COR_PUB_ENUMPROCESS](cor-pub-enumprocess-enumeration.md) enumeration that specifies the type of process to be retrieved.</span></span> <span data-ttu-id="3ba2f-108">Geçerli sürümde yalnızca COR_PUB_MANAGEDONLY geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3ba2f-108">In the current version, only COR_PUB_MANAGEDONLY is valid.</span></span>  
  
 `ppIEnum`  
 <span data-ttu-id="3ba2f-109">İşlemlerin numaralandırıcısı olan [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) örneğinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3ba2f-109">A pointer to the address of an [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) instance that is the enumerator of the processes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ba2f-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3ba2f-110">Remarks</span></span>  

 <span data-ttu-id="3ba2f-111">Numaralandırıcının işlem koleksiyonu, yöntemi çağrıldığında çalışan işlemlerin anlık görüntüsünü temel alır `EnumProcesses` .</span><span class="sxs-lookup"><span data-stu-id="3ba2f-111">The enumerator's collection of processes is based on a snapshot of the processes that are running when the `EnumProcesses` method is called.</span></span> <span data-ttu-id="3ba2f-112">Numaralandırıcı çağrılmadan önce ya da başlamadan önce sonlanacak herhangi bir işlem içermez `EnumProcesses` .</span><span class="sxs-lookup"><span data-stu-id="3ba2f-112">The enumerator will not include any processes that terminate before or start after `EnumProcesses` is called.</span></span>  
  
 <span data-ttu-id="3ba2f-113">`EnumProcesses`Yöntemi bu [ICorPublish](icorpublish-interface.md) örneğinde birden çok kez çağrılabilir ve bu işlem, yeni bir güncel koleksiyon oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3ba2f-113">The `EnumProcesses` method may be called more than once on this [ICorPublish](icorpublish-interface.md) instance to create a new up-to-date collection of processes.</span></span> <span data-ttu-id="3ba2f-114">Mevcut koleksiyonlar, yönteminin sonraki çağrılarından etkilenmeyecektir `EnumProcesses` .</span><span class="sxs-lookup"><span data-stu-id="3ba2f-114">Existing collections will not be affected by subsequent calls of the `EnumProcesses` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ba2f-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3ba2f-115">Requirements</span></span>  

 <span data-ttu-id="3ba2f-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ba2f-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ba2f-117">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="3ba2f-117">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="3ba2f-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3ba2f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ba2f-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ba2f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ba2f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3ba2f-120">See also</span></span>

- [<span data-ttu-id="3ba2f-121">ICorPublish Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3ba2f-121">ICorPublish Interface</span></span>](icorpublish-interface.md)
