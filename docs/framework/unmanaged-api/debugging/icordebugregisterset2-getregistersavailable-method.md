---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugRegisterSet2:: GetRegistersAvailable yöntemi'
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
ms.openlocfilehash: 3839647e69efd63aefd1aa154c457f292e684336
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790730"
---
# <a name="icordebugregisterset2getregistersavailable-method"></a><span data-ttu-id="c94e5-103">ICorDebugRegisterSet2::GetRegistersAvailable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c94e5-103">ICorDebugRegisterSet2::GetRegistersAvailable Method</span></span>

<span data-ttu-id="c94e5-104">Kullanılabilir yazmaçların bit eşlemini sağlayan bir bayt dizisini alır.</span><span class="sxs-lookup"><span data-stu-id="c94e5-104">Gets an array of bytes that provides a bitmap of the available registers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c94e5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c94e5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c94e5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c94e5-106">Parameters</span></span>  

 `numChunks`  
 <span data-ttu-id="c94e5-107">'ndaki `availableRegChunks` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="c94e5-107">[in] The size of the `availableRegChunks` array.</span></span>  
  
 `availableRegChunks`  
 <span data-ttu-id="c94e5-108">dışı Her bitin bir kayda karşılık gelen bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="c94e5-108">[out] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="c94e5-109">Bir yazmaç varsa, kaydın karşılık gelen biti ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c94e5-109">If a register is available, the register's corresponding bit is set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c94e5-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c94e5-110">Remarks</span></span>  

 <span data-ttu-id="c94e5-111">CorDebugRegister sabit listesinin değerleri, farklı mikro işlemcilerin kayıtlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c94e5-111">The values of the CorDebugRegister enumeration specify the registers of different microprocessors.</span></span> <span data-ttu-id="c94e5-112">Her bir değerin üst beş biti, `availableRegChunks` bayt dizisinin dizinidir.</span><span class="sxs-lookup"><span data-stu-id="c94e5-112">The upper five bits of each value are the index into the `availableRegChunks` array of bytes.</span></span> <span data-ttu-id="c94e5-113">Her bir değerin alt üç biti, dizinlenmiş bayt içindeki bit konumunu belirler.</span><span class="sxs-lookup"><span data-stu-id="c94e5-113">The lower three bits of each value identify the bit position within the indexed byte.</span></span> <span data-ttu-id="c94e5-114">Belirli bir `CorDebugRegister` kaydı belirten bir değer verildiğinde, maskede kaydın konumu aşağıdaki şekilde belirlenir:</span><span class="sxs-lookup"><span data-stu-id="c94e5-114">Given a `CorDebugRegister` value that specifies a particular register, the register's position in the mask is determined as follows:</span></span>  
  
1. <span data-ttu-id="c94e5-115">Dizideki doğru bayta erişmek için gereken dizini ayıklayın `availableRegChunks` :</span><span class="sxs-lookup"><span data-stu-id="c94e5-115">Extract the index needed to access the correct byte in the `availableRegChunks` array:</span></span>  
  
     <span data-ttu-id="c94e5-116">`CorDebugRegister` değer >> 3</span><span class="sxs-lookup"><span data-stu-id="c94e5-116">`CorDebugRegister` value >> 3</span></span>  
  
2. <span data-ttu-id="c94e5-117">Dizin oluşturulan bayt içindeki bit konumunu ayıklayın; burada bit sıfır en az önemli bir bittir:</span><span class="sxs-lookup"><span data-stu-id="c94e5-117">Extract the bit position within the indexed byte, where bit zero is the least significant bit:</span></span>  
  
     <span data-ttu-id="c94e5-118">`CorDebugRegister` değer & 7</span><span class="sxs-lookup"><span data-stu-id="c94e5-118">`CorDebugRegister` value & 7</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c94e5-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c94e5-119">Requirements</span></span>  

 <span data-ttu-id="c94e5-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c94e5-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c94e5-121">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c94e5-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c94e5-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c94e5-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c94e5-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c94e5-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c94e5-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c94e5-124">See also</span></span>

- [<span data-ttu-id="c94e5-125">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c94e5-125">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
- [<span data-ttu-id="c94e5-126">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c94e5-126">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
