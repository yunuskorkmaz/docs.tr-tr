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
ms.openlocfilehash: cfa0950ca2ef4e969258c147b762fa95e52a82e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705828"
---
# <a name="icordebuggenericvalue-interface"></a><span data-ttu-id="f408e-102">ICorDebugGenericValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f408e-102">ICorDebugGenericValue Interface</span></span>

<span data-ttu-id="f408e-103">Tüm değerler için geçerli olan "ICorDebugValue" öğesinin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f408e-103">A subclass of "ICorDebugValue" that applies to all values.</span></span> <span data-ttu-id="f408e-104">Bu arabirim, değer için Alma ve Ayarlama yöntemlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="f408e-104">This interface provides Get and Set methods for the value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f408e-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f408e-105">Methods</span></span>  
  
|<span data-ttu-id="f408e-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f408e-106">Method</span></span>|<span data-ttu-id="f408e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f408e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f408e-108">GetValue Metodu</span><span class="sxs-lookup"><span data-stu-id="f408e-108">GetValue Method</span></span>](icordebuggenericvalue-getvalue-method.md)|<span data-ttu-id="f408e-109">Değeri belirtilen arabelleğe kopyalar.</span><span class="sxs-lookup"><span data-stu-id="f408e-109">Copies the value into the specified buffer.</span></span>|  
|[<span data-ttu-id="f408e-110">SetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f408e-110">SetValue Method</span></span>](icordebuggenericvalue-setvalue-method.md)|<span data-ttu-id="f408e-111">Belirtilen arabellekteki yeni bir değer kopyalar.</span><span class="sxs-lookup"><span data-stu-id="f408e-111">Copies a new value from the specified buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f408e-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f408e-112">Remarks</span></span>  

 <span data-ttu-id="f408e-113">`ICorDebugGenericValue` , Uzaktan erişilemeyen için bir alt arabirimdir.</span><span class="sxs-lookup"><span data-stu-id="f408e-113">`ICorDebugGenericValue` is a sub-interface because it is non-remotable.</span></span>  
  
 <span data-ttu-id="f408e-114">Başvuru türleri için, değer başvurunun içeriği yerine başvurudur.</span><span class="sxs-lookup"><span data-stu-id="f408e-114">For reference types, the value is the reference rather than the contents of the reference.</span></span>  
  
 <span data-ttu-id="f408e-115">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="f408e-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f408e-116">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="f408e-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f408e-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f408e-117">Requirements</span></span>  

 <span data-ttu-id="f408e-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f408e-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f408e-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f408e-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f408e-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f408e-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f408e-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f408e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f408e-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f408e-122">See also</span></span>

- [<span data-ttu-id="f408e-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f408e-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
