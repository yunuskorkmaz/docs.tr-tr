---
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
ms.openlocfilehash: 7c5359ddf2c021f77ad1ea0a8579316c3c773fd5
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209792"
---
# <a name="icordebuggenericvalue-interface"></a><span data-ttu-id="1d401-102">ICorDebugGenericValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1d401-102">ICorDebugGenericValue Interface</span></span>

<span data-ttu-id="1d401-103">Tüm değerler için geçerli olan "ICorDebugValue" öğesinin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1d401-103">A subclass of "ICorDebugValue" that applies to all values.</span></span> <span data-ttu-id="1d401-104">Bu arabirim, değer için Alma ve Ayarlama yöntemlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="1d401-104">This interface provides Get and Set methods for the value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1d401-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1d401-105">Methods</span></span>  
  
|<span data-ttu-id="1d401-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1d401-106">Method</span></span>|<span data-ttu-id="1d401-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d401-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1d401-108">GetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1d401-108">GetValue Method</span></span>](icordebuggenericvalue-getvalue-method.md)|<span data-ttu-id="1d401-109">Değeri belirtilen arabelleğe kopyalar.</span><span class="sxs-lookup"><span data-stu-id="1d401-109">Copies the value into the specified buffer.</span></span>|  
|[<span data-ttu-id="1d401-110">SetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1d401-110">SetValue Method</span></span>](icordebuggenericvalue-setvalue-method.md)|<span data-ttu-id="1d401-111">Belirtilen arabellekteki yeni bir değer kopyalar.</span><span class="sxs-lookup"><span data-stu-id="1d401-111">Copies a new value from the specified buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d401-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1d401-112">Remarks</span></span>  
 <span data-ttu-id="1d401-113">`ICorDebugGenericValue`, Uzaktan erişilemeyen için bir alt arabirimdir.</span><span class="sxs-lookup"><span data-stu-id="1d401-113">`ICorDebugGenericValue` is a sub-interface because it is non-remotable.</span></span>  
  
 <span data-ttu-id="1d401-114">Başvuru türleri için, değer başvurunun içeriği yerine başvurudur.</span><span class="sxs-lookup"><span data-stu-id="1d401-114">For reference types, the value is the reference rather than the contents of the reference.</span></span>  
  
 <span data-ttu-id="1d401-115">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="1d401-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1d401-116">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="1d401-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d401-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1d401-117">Requirements</span></span>  
 <span data-ttu-id="1d401-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d401-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d401-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1d401-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1d401-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1d401-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d401-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d401-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d401-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d401-122">See also</span></span>

- [<span data-ttu-id="1d401-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1d401-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
