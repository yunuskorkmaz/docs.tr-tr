---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugGenericValue arabirimi'
title: ICorDebugGenericValue Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue
helpviewer_keywords:
- ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: bc14f408-b359-4c8c-ade2-888ccdf7261b
topic_type:
- apiref
ms.openlocfilehash: 7c81855849d7b72bc509d20072b96bb64f5d395a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692043"
---
# <a name="icordebuggenericvalue-interface"></a><span data-ttu-id="7d3e3-103">ICorDebugGenericValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7d3e3-103">ICorDebugGenericValue Interface</span></span>

<span data-ttu-id="7d3e3-104">Tüm değerler için geçerli olan "ICorDebugValue" öğesinin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7d3e3-104">A subclass of "ICorDebugValue" that applies to all values.</span></span> <span data-ttu-id="7d3e3-105">Bu arabirim, değer için Alma ve Ayarlama yöntemlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="7d3e3-105">This interface provides Get and Set methods for the value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7d3e3-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7d3e3-106">Methods</span></span>  
  
|<span data-ttu-id="7d3e3-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7d3e3-107">Method</span></span>|<span data-ttu-id="7d3e3-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d3e3-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7d3e3-109">GetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d3e3-109">GetValue Method</span></span>](icordebuggenericvalue-getvalue-method.md)|<span data-ttu-id="7d3e3-110">Değeri belirtilen arabelleğe kopyalar.</span><span class="sxs-lookup"><span data-stu-id="7d3e3-110">Copies the value into the specified buffer.</span></span>|  
|[<span data-ttu-id="7d3e3-111">SetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d3e3-111">SetValue Method</span></span>](icordebuggenericvalue-setvalue-method.md)|<span data-ttu-id="7d3e3-112">Belirtilen arabellekteki yeni bir değer kopyalar.</span><span class="sxs-lookup"><span data-stu-id="7d3e3-112">Copies a new value from the specified buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d3e3-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7d3e3-113">Remarks</span></span>  

 <span data-ttu-id="7d3e3-114">`ICorDebugGenericValue` , Uzaktan erişilemeyen için bir alt arabirimdir.</span><span class="sxs-lookup"><span data-stu-id="7d3e3-114">`ICorDebugGenericValue` is a sub-interface because it is non-remotable.</span></span>  
  
 <span data-ttu-id="7d3e3-115">Başvuru türleri için, değer başvurunun içeriği yerine başvurudur.</span><span class="sxs-lookup"><span data-stu-id="7d3e3-115">For reference types, the value is the reference rather than the contents of the reference.</span></span>  
  
 <span data-ttu-id="7d3e3-116">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="7d3e3-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7d3e3-117">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="7d3e3-117">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d3e3-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7d3e3-118">Requirements</span></span>  

 <span data-ttu-id="7d3e3-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d3e3-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d3e3-120">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7d3e3-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d3e3-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7d3e3-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d3e3-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d3e3-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d3e3-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d3e3-123">See also</span></span>

- [<span data-ttu-id="7d3e3-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7d3e3-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
