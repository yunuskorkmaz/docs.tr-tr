---
title: ICorDebugRegisterSet::GetRegisters Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetRegisters method [.NET Framework debugging]
ms.assetid: fdf91864-48ea-4aa6-b70c-361b7a3184c7
topic_type:
- apiref
ms.openlocfilehash: 112d530c765fc74ab4ea767cb3168977d1b45f47
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138357"
---
# <a name="icordebugregistersetgetregisters-method"></a><span data-ttu-id="6299b-102">ICorDebugRegisterSet::GetRegisters Metodu</span><span class="sxs-lookup"><span data-stu-id="6299b-102">ICorDebugRegisterSet::GetRegisters Method</span></span>
<span data-ttu-id="6299b-103">Bit maskesi tarafından belirtilen her kaydın (Şu anda kod yürüten bilgisayardaki) değerini alır.</span><span class="sxs-lookup"><span data-stu-id="6299b-103">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6299b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6299b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG64       mask,   
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6299b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6299b-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="6299b-106">'ndaki Hangi yazmaç değerlerinin alınacağını belirten bir bit maskesi.</span><span class="sxs-lookup"><span data-stu-id="6299b-106">[in] A bit mask that specifies which register values are to be retrieved.</span></span> <span data-ttu-id="6299b-107">Her bit bir kayda karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="6299b-107">Each bit corresponds to a register.</span></span> <span data-ttu-id="6299b-108">Bir bit olarak ayarlandıysa, kaydın değeri alınır; Aksi takdirde, kaydın değeri alınmadı.</span><span class="sxs-lookup"><span data-stu-id="6299b-108">If a bit is set to one, the register's value is retrieved; otherwise, the register's value is not retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="6299b-109">'ndaki Alınacak kayıt değerlerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="6299b-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="6299b-110">dışı Her biri bir yazmaç değeri alan `CORDB_REGISTER` nesnelerden oluşan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="6299b-110">[out] An array of `CORDB_REGISTER` objects, each of which receives a value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6299b-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6299b-111">Remarks</span></span>  
 <span data-ttu-id="6299b-112">Dizinin boyutu, bit maskesinde bir tane olarak ayarlanan bit sayısına eşit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6299b-112">The size of the array should be equal to the number of bits set to one in the bit mask.</span></span> <span data-ttu-id="6299b-113">`regCount` parametresi, kayıt değerlerini alacak arabellekteki öğelerin sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6299b-113">The `regCount` parameter specifies the number of elements in the buffer that will receive the register values.</span></span> <span data-ttu-id="6299b-114">`regCount` değeri maskenin gösterdiği kayıt sayısı için çok küçük ise, daha yüksek numaralandırılmış Yazmaçları kümeden kesilecek.</span><span class="sxs-lookup"><span data-stu-id="6299b-114">If the `regCount` value is too small for the number of registers indicated by the mask, the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="6299b-115">`regCount` değeri çok büyükse, kullanılmamış `regBuffer` öğeleri değiştirilmemiş olur.</span><span class="sxs-lookup"><span data-stu-id="6299b-115">If the `regCount` value is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="6299b-116">Bit maskesi kullanılamayan bir kaydı belirtirse `GetRegisters`, bu kayıt için belirsiz bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="6299b-116">If the bit mask specifies a register that is unavailable, `GetRegisters` returns an indeterminate value for that register.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6299b-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6299b-117">Requirements</span></span>  
 <span data-ttu-id="6299b-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6299b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6299b-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6299b-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6299b-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6299b-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6299b-121">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6299b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6299b-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6299b-122">See also</span></span>

- [<span data-ttu-id="6299b-123">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6299b-123">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="6299b-124">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6299b-124">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
