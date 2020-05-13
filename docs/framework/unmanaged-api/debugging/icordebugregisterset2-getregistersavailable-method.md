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
ms.openlocfilehash: 2149c985519b95f89af2c50d05753ae7259babe4
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378217"
---
# <a name="icordebugregisterset2getregistersavailable-method"></a><span data-ttu-id="c5cb4-102">ICorDebugRegisterSet2::GetRegistersAvailable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c5cb4-102">ICorDebugRegisterSet2::GetRegistersAvailable Method</span></span>
<span data-ttu-id="c5cb4-103">Kullanılabilir yazmaçların bit eşlemini sağlayan bir bayt dizisini alır.</span><span class="sxs-lookup"><span data-stu-id="c5cb4-103">Gets an array of bytes that provides a bitmap of the available registers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5cb4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5cb4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5cb4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c5cb4-105">Parameters</span></span>  
 `numChunks`  
 <span data-ttu-id="c5cb4-106">'ndaki `availableRegChunks`Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="c5cb4-106">[in] The size of the `availableRegChunks` array.</span></span>  
  
 `availableRegChunks`  
 <span data-ttu-id="c5cb4-107">dışı Her bitin bir kayda karşılık gelen bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="c5cb4-107">[out] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="c5cb4-108">Bir yazmaç varsa, kaydın karşılık gelen biti ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c5cb4-108">If a register is available, the register's corresponding bit is set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5cb4-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c5cb4-109">Remarks</span></span>  
 <span data-ttu-id="c5cb4-110">CorDebugRegister sabit listesinin değerleri, farklı mikro işlemcilerin kayıtlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5cb4-110">The values of the CorDebugRegister enumeration specify the registers of different microprocessors.</span></span> <span data-ttu-id="c5cb4-111">Her bir değerin üst beş biti, `availableRegChunks` bayt dizisinin dizinidir.</span><span class="sxs-lookup"><span data-stu-id="c5cb4-111">The upper five bits of each value are the index into the `availableRegChunks` array of bytes.</span></span> <span data-ttu-id="c5cb4-112">Her bir değerin alt üç biti, dizinlenmiş bayt içindeki bit konumunu belirler.</span><span class="sxs-lookup"><span data-stu-id="c5cb4-112">The lower three bits of each value identify the bit position within the indexed byte.</span></span> <span data-ttu-id="c5cb4-113">Belirli bir `CorDebugRegister` kaydı belirten bir değer verildiğinde, maskede kaydın konumu aşağıdaki şekilde belirlenir:</span><span class="sxs-lookup"><span data-stu-id="c5cb4-113">Given a `CorDebugRegister` value that specifies a particular register, the register's position in the mask is determined as follows:</span></span>  
  
1. <span data-ttu-id="c5cb4-114">Dizideki doğru bayta erişmek için gereken dizini ayıklayın `availableRegChunks` :</span><span class="sxs-lookup"><span data-stu-id="c5cb4-114">Extract the index needed to access the correct byte in the `availableRegChunks` array:</span></span>  
  
     <span data-ttu-id="c5cb4-115">`CorDebugRegister`değer >> 3</span><span class="sxs-lookup"><span data-stu-id="c5cb4-115">`CorDebugRegister` value >> 3</span></span>  
  
2. <span data-ttu-id="c5cb4-116">Dizin oluşturulan bayt içindeki bit konumunu ayıklayın; burada bit sıfır en az önemli bir bittir:</span><span class="sxs-lookup"><span data-stu-id="c5cb4-116">Extract the bit position within the indexed byte, where bit zero is the least significant bit:</span></span>  
  
     <span data-ttu-id="c5cb4-117">`CorDebugRegister`değer & 7</span><span class="sxs-lookup"><span data-stu-id="c5cb4-117">`CorDebugRegister` value & 7</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5cb4-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c5cb4-118">Requirements</span></span>  
 <span data-ttu-id="c5cb4-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5cb4-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5cb4-120">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c5cb4-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c5cb4-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c5cb4-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5cb4-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5cb4-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5cb4-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5cb4-123">See also</span></span>

- [<span data-ttu-id="c5cb4-124">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c5cb4-124">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
- [<span data-ttu-id="c5cb4-125">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c5cb4-125">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
