---
title: ICorDebugRegisterSet2::GetRegistersAvailable Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegistersAvailable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegistersAvailable
helpviewer_keywords:
- GetRegistersAvailable method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegistersAvailable method [.NET Framework debugging]
ms.assetid: f3ed344b-0d3a-44e8-8000-2a97e0805a2c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0ee807ae17e4d53d3f6f3963f5a91df0a2dddd0c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59099878"
---
# <a name="icordebugregisterset2getregistersavailable-method"></a><span data-ttu-id="cf63e-102">ICorDebugRegisterSet2::GetRegistersAvailable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cf63e-102">ICorDebugRegisterSet2::GetRegistersAvailable Method</span></span>
<span data-ttu-id="cf63e-103">Bir bit eşlem kullanılabilir kayıtlara sağlayan bayt dizisini alır.</span><span class="sxs-lookup"><span data-stu-id="cf63e-103">Gets an array of bytes that provides a bitmap of the available registers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf63e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf63e-104">Syntax</span></span>  
  
```  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf63e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cf63e-105">Parameters</span></span>  
 `numChunks`  
 <span data-ttu-id="cf63e-106">[in] Boyutu `availableRegChunks` dizisi.</span><span class="sxs-lookup"><span data-stu-id="cf63e-106">[in] The size of the `availableRegChunks` array.</span></span>  
  
 `availableRegChunks`  
 <span data-ttu-id="cf63e-107">[out] Bir bayt dizisi, bir kasaya her bitini karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="cf63e-107">[out] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="cf63e-108">Bir kayıt varsa, kasanın karşılık gelen bit ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="cf63e-108">If a register is available, the register's corresponding bit is set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf63e-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cf63e-109">Remarks</span></span>  
 <span data-ttu-id="cf63e-110">CorDebugRegister sabit listesi değerlerini farklı mikro kasalar belirtin.</span><span class="sxs-lookup"><span data-stu-id="cf63e-110">The values of the CorDebugRegister enumeration specify the registers of different microprocessors.</span></span> <span data-ttu-id="cf63e-111">Her bir değerin üst beş biti dizine olan `availableRegChunks` bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="cf63e-111">The upper five bits of each value are the index into the `availableRegChunks` array of bytes.</span></span> <span data-ttu-id="cf63e-112">Her bir değerin alt üç bit dizinli bayt içindeki bit konumu belirleyin.</span><span class="sxs-lookup"><span data-stu-id="cf63e-112">The lower three bits of each value identify the bit position within the indexed byte.</span></span> <span data-ttu-id="cf63e-113">Verilen bir `CorDebugRegister` belirli bir kaydı, maske kasanın konumu belirten bir değer şu şekilde belirlenir:</span><span class="sxs-lookup"><span data-stu-id="cf63e-113">Given a `CorDebugRegister` value that specifies a particular register, the register's position in the mask is determined as follows:</span></span>  
  
1.  <span data-ttu-id="cf63e-114">Doğru bayt erişmesi gereken dizin ayıklamak `availableRegChunks` dizisi:</span><span class="sxs-lookup"><span data-stu-id="cf63e-114">Extract the index needed to access the correct byte in the `availableRegChunks` array:</span></span>  
  
     `CorDebugRegister` <span data-ttu-id="cf63e-115">Değer >> 3</span><span class="sxs-lookup"><span data-stu-id="cf63e-115">value >> 3</span></span>  
  
2.  <span data-ttu-id="cf63e-116">Bit sıfır en az önemli bite olduğu dizinli bayt içindeki bit konumu ayıklayın:</span><span class="sxs-lookup"><span data-stu-id="cf63e-116">Extract the bit position within the indexed byte, where bit zero is the least significant bit:</span></span>  
  
     `CorDebugRegister` <span data-ttu-id="cf63e-117">Değer & 7</span><span class="sxs-lookup"><span data-stu-id="cf63e-117">value & 7</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf63e-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cf63e-118">Requirements</span></span>  
 <span data-ttu-id="cf63e-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf63e-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf63e-120">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cf63e-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cf63e-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cf63e-121">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="cf63e-122">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="cf63e-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cf63e-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf63e-123">See also</span></span>

- [<span data-ttu-id="cf63e-124">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf63e-124">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [<span data-ttu-id="cf63e-125">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf63e-125">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
