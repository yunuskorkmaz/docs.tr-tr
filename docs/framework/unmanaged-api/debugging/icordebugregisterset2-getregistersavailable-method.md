---
title: ICorDebugRegisterSet2::GetRegistersAvailable Metodu
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
ms.openlocfilehash: d3a9cdb49c1a44dbc68cd4b7ccf4d4781ce5c539
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421898"
---
# <a name="icordebugregisterset2getregistersavailable-method"></a><span data-ttu-id="915a2-102">ICorDebugRegisterSet2::GetRegistersAvailable Metodu</span><span class="sxs-lookup"><span data-stu-id="915a2-102">ICorDebugRegisterSet2::GetRegistersAvailable Method</span></span>
<span data-ttu-id="915a2-103">Bir bit eşlem kullanılabilir yazmaçlar sağlayan bir bayt dizisi alır.</span><span class="sxs-lookup"><span data-stu-id="915a2-103">Gets an array of bytes that provides a bitmap of the available registers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="915a2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="915a2-104">Syntax</span></span>  
  
```  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="915a2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="915a2-105">Parameters</span></span>  
 `numChunks`  
 <span data-ttu-id="915a2-106">[in] Boyutunu `availableRegChunks` dizi.</span><span class="sxs-lookup"><span data-stu-id="915a2-106">[in] The size of the `availableRegChunks` array.</span></span>  
  
 `availableRegChunks`  
 <span data-ttu-id="915a2-107">[out] Bir bayt dizisi, bir kasaya her biti karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="915a2-107">[out] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="915a2-108">Bir kayıt varsa, kasanın karşılık gelen bit ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="915a2-108">If a register is available, the register's corresponding bit is set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="915a2-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="915a2-109">Remarks</span></span>  
 <span data-ttu-id="915a2-110">CorDebugRegister numaralandırması değerlerini farklı mikro yazmaçlar belirtin.</span><span class="sxs-lookup"><span data-stu-id="915a2-110">The values of the CorDebugRegister enumeration specify the registers of different microprocessors.</span></span> <span data-ttu-id="915a2-111">Üst beş her değerin dizine bittir `availableRegChunks` bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="915a2-111">The upper five bits of each value are the index into the `availableRegChunks` array of bytes.</span></span> <span data-ttu-id="915a2-112">Her bir değerin alt üç BITS dizinli bayt bit konumlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="915a2-112">The lower three bits of each value identify the bit position within the indexed byte.</span></span> <span data-ttu-id="915a2-113">Verilen bir `CorDebugRegister` maske kasanın konumda belirli bir kayıt belirten değeri şu şekilde belirlenir:</span><span class="sxs-lookup"><span data-stu-id="915a2-113">Given a `CorDebugRegister` value that specifies a particular register, the register's position in the mask is determined as follows:</span></span>  
  
1.  <span data-ttu-id="915a2-114">Doğru bayt erişmesi gereken dizin ayıklamak `availableRegChunks` dizi:</span><span class="sxs-lookup"><span data-stu-id="915a2-114">Extract the index needed to access the correct byte in the `availableRegChunks` array:</span></span>  
  
     <span data-ttu-id="915a2-115">`CorDebugRegister` Değer >> 3</span><span class="sxs-lookup"><span data-stu-id="915a2-115">`CorDebugRegister` value >> 3</span></span>  
  
2.  <span data-ttu-id="915a2-116">Bit sıfır en az önemli bit olduğu dizinli bayt bit konumlarını ayıklayın:</span><span class="sxs-lookup"><span data-stu-id="915a2-116">Extract the bit position within the indexed byte, where bit zero is the least significant bit:</span></span>  
  
     <span data-ttu-id="915a2-117">`CorDebugRegister` Değer & 7</span><span class="sxs-lookup"><span data-stu-id="915a2-117">`CorDebugRegister` value & 7</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="915a2-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="915a2-118">Requirements</span></span>  
 <span data-ttu-id="915a2-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="915a2-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="915a2-120">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="915a2-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="915a2-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="915a2-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="915a2-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="915a2-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="915a2-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="915a2-123">See Also</span></span>  
 [<span data-ttu-id="915a2-124">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="915a2-124">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 [<span data-ttu-id="915a2-125">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="915a2-125">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
