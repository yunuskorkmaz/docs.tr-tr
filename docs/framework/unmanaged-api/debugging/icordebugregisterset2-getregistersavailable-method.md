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
ms.openlocfilehash: cb56ea817d4045c19793a6290d68ae8b6236f14a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712329"
---
# <a name="icordebugregisterset2getregistersavailable-method"></a><span data-ttu-id="b56cf-102">ICorDebugRegisterSet2::GetRegistersAvailable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b56cf-102">ICorDebugRegisterSet2::GetRegistersAvailable Method</span></span>

<span data-ttu-id="b56cf-103">Kullanılabilir yazmaçların bit eşlemini sağlayan bir bayt dizisini alır.</span><span class="sxs-lookup"><span data-stu-id="b56cf-103">Gets an array of bytes that provides a bitmap of the available registers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b56cf-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b56cf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b56cf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b56cf-105">Parameters</span></span>  

 `numChunks`  
 <span data-ttu-id="b56cf-106">'ndaki `availableRegChunks` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="b56cf-106">[in] The size of the `availableRegChunks` array.</span></span>  
  
 `availableRegChunks`  
 <span data-ttu-id="b56cf-107">dışı Her bitin bir kayda karşılık gelen bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="b56cf-107">[out] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="b56cf-108">Bir yazmaç varsa, kaydın karşılık gelen biti ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="b56cf-108">If a register is available, the register's corresponding bit is set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b56cf-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b56cf-109">Remarks</span></span>  

 <span data-ttu-id="b56cf-110">CorDebugRegister sabit listesinin değerleri, farklı mikro işlemcilerin kayıtlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b56cf-110">The values of the CorDebugRegister enumeration specify the registers of different microprocessors.</span></span> <span data-ttu-id="b56cf-111">Her bir değerin üst beş biti, `availableRegChunks` bayt dizisinin dizinidir.</span><span class="sxs-lookup"><span data-stu-id="b56cf-111">The upper five bits of each value are the index into the `availableRegChunks` array of bytes.</span></span> <span data-ttu-id="b56cf-112">Her bir değerin alt üç biti, dizinlenmiş bayt içindeki bit konumunu belirler.</span><span class="sxs-lookup"><span data-stu-id="b56cf-112">The lower three bits of each value identify the bit position within the indexed byte.</span></span> <span data-ttu-id="b56cf-113">Belirli bir `CorDebugRegister` kaydı belirten bir değer verildiğinde, maskede kaydın konumu aşağıdaki şekilde belirlenir:</span><span class="sxs-lookup"><span data-stu-id="b56cf-113">Given a `CorDebugRegister` value that specifies a particular register, the register's position in the mask is determined as follows:</span></span>  
  
1. <span data-ttu-id="b56cf-114">Dizideki doğru bayta erişmek için gereken dizini ayıklayın `availableRegChunks` :</span><span class="sxs-lookup"><span data-stu-id="b56cf-114">Extract the index needed to access the correct byte in the `availableRegChunks` array:</span></span>  
  
     <span data-ttu-id="b56cf-115">`CorDebugRegister` değer >> 3</span><span class="sxs-lookup"><span data-stu-id="b56cf-115">`CorDebugRegister` value >> 3</span></span>  
  
2. <span data-ttu-id="b56cf-116">Dizin oluşturulan bayt içindeki bit konumunu ayıklayın; burada bit sıfır en az önemli bir bittir:</span><span class="sxs-lookup"><span data-stu-id="b56cf-116">Extract the bit position within the indexed byte, where bit zero is the least significant bit:</span></span>  
  
     <span data-ttu-id="b56cf-117">`CorDebugRegister` değer & 7</span><span class="sxs-lookup"><span data-stu-id="b56cf-117">`CorDebugRegister` value & 7</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b56cf-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b56cf-118">Requirements</span></span>  

 <span data-ttu-id="b56cf-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b56cf-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b56cf-120">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b56cf-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b56cf-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b56cf-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b56cf-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b56cf-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b56cf-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b56cf-123">See also</span></span>

- [<span data-ttu-id="b56cf-124">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b56cf-124">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
- [<span data-ttu-id="b56cf-125">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b56cf-125">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
