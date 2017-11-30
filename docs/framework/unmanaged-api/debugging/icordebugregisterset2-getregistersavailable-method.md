---
title: ICorDebugRegisterSet2::GetRegistersAvailable Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet2.GetRegistersAvailable
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet2::GetRegistersAvailable
helpviewer_keywords:
- GetRegistersAvailable method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegistersAvailable method [.NET Framework debugging]
ms.assetid: f3ed344b-0d3a-44e8-8000-2a97e0805a2c
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1f91b30b2ab50fc74049365d5c290bbaae1e20b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugregisterset2getregistersavailable-method"></a><span data-ttu-id="266c3-102">ICorDebugRegisterSet2::GetRegistersAvailable Metodu</span><span class="sxs-lookup"><span data-stu-id="266c3-102">ICorDebugRegisterSet2::GetRegistersAvailable Method</span></span>
<span data-ttu-id="266c3-103">Bir bit eşlem kullanılabilir yazmaçlar sağlayan bir bayt dizisi alır.</span><span class="sxs-lookup"><span data-stu-id="266c3-103">Gets an array of bytes that provides a bitmap of the available registers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="266c3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="266c3-104">Syntax</span></span>  
  
```  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="266c3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="266c3-105">Parameters</span></span>  
 `numChunks`  
 <span data-ttu-id="266c3-106">[in] Boyutunu `availableRegChunks` dizi.</span><span class="sxs-lookup"><span data-stu-id="266c3-106">[in] The size of the `availableRegChunks` array.</span></span>  
  
 `availableRegChunks`  
 <span data-ttu-id="266c3-107">[out] Bir bayt dizisi, bir kasaya her biti karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="266c3-107">[out] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="266c3-108">Bir kayıt varsa, kasanın karşılık gelen bit ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="266c3-108">If a register is available, the register's corresponding bit is set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="266c3-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="266c3-109">Remarks</span></span>  
 <span data-ttu-id="266c3-110">CorDebugRegister numaralandırması değerlerini farklı mikro yazmaçlar belirtin.</span><span class="sxs-lookup"><span data-stu-id="266c3-110">The values of the CorDebugRegister enumeration specify the registers of different microprocessors.</span></span> <span data-ttu-id="266c3-111">Üst beş her değerin dizine bittir `availableRegChunks` bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="266c3-111">The upper five bits of each value are the index into the `availableRegChunks` array of bytes.</span></span> <span data-ttu-id="266c3-112">Her bir değerin alt üç BITS dizinli bayt bit konumlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="266c3-112">The lower three bits of each value identify the bit position within the indexed byte.</span></span> <span data-ttu-id="266c3-113">Verilen bir `CorDebugRegister` maske kasanın konumda belirli bir kayıt belirten değeri şu şekilde belirlenir:</span><span class="sxs-lookup"><span data-stu-id="266c3-113">Given a `CorDebugRegister` value that specifies a particular register, the register's position in the mask is determined as follows:</span></span>  
  
1.  <span data-ttu-id="266c3-114">Doğru bayt erişmesi gereken dizin ayıklamak `availableRegChunks` dizi:</span><span class="sxs-lookup"><span data-stu-id="266c3-114">Extract the index needed to access the correct byte in the `availableRegChunks` array:</span></span>  
  
     <span data-ttu-id="266c3-115">`CorDebugRegister`Değer >> 3</span><span class="sxs-lookup"><span data-stu-id="266c3-115">`CorDebugRegister` value >> 3</span></span>  
  
2.  <span data-ttu-id="266c3-116">Bit sıfır en az önemli bit olduğu dizinli bayt bit konumlarını ayıklayın:</span><span class="sxs-lookup"><span data-stu-id="266c3-116">Extract the bit position within the indexed byte, where bit zero is the least significant bit:</span></span>  
  
     <span data-ttu-id="266c3-117">`CorDebugRegister`Değer & 7</span><span class="sxs-lookup"><span data-stu-id="266c3-117">`CorDebugRegister` value & 7</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="266c3-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="266c3-118">Requirements</span></span>  
 <span data-ttu-id="266c3-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="266c3-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="266c3-120">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="266c3-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="266c3-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="266c3-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="266c3-122">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="266c3-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="266c3-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="266c3-123">See Also</span></span>  
 [<span data-ttu-id="266c3-124">Icordebugregisterset2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="266c3-124">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 [<span data-ttu-id="266c3-125">Icordebugregisterset arabirimi</span><span class="sxs-lookup"><span data-stu-id="266c3-125">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
