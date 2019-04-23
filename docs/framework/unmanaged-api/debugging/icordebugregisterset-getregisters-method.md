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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b417685361126951470571e2440cc842ab1c94fb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59153913"
---
# <a name="icordebugregistersetgetregisters-method"></a><span data-ttu-id="461e7-102">ICorDebugRegisterSet::GetRegisters Metodu</span><span class="sxs-lookup"><span data-stu-id="461e7-102">ICorDebugRegisterSet::GetRegisters Method</span></span>
<span data-ttu-id="461e7-103">Her kaydın değerini alır (şu anda kod yürüttüğünü bilgisayarda) bit maskesi kullanılarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="461e7-103">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="461e7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="461e7-104">Syntax</span></span>  
  
```  
HRESULT GetRegisters (  
    [in] ULONG64       mask,   
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="461e7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="461e7-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="461e7-106">[in] Hangi kayıt alınması için değerler belirten bir bit maskesi.</span><span class="sxs-lookup"><span data-stu-id="461e7-106">[in] A bit mask that specifies which register values are to be retrieved.</span></span> <span data-ttu-id="461e7-107">Her bit bir kasaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="461e7-107">Each bit corresponds to a register.</span></span> <span data-ttu-id="461e7-108">Bir bit olarak ayarlanırsa kasanın değeri alınır; Aksi takdirde, kaydın değeri alınamadı.</span><span class="sxs-lookup"><span data-stu-id="461e7-108">If a bit is set to one, the register's value is retrieved; otherwise, the register's value is not retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="461e7-109">[in] YAZMAÇ değerlerini alınacak sayısı.</span><span class="sxs-lookup"><span data-stu-id="461e7-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="461e7-110">[out] Bir dizi `CORDB_REGISTER` nesneleri, her biri bir kayıt değeri alır.</span><span class="sxs-lookup"><span data-stu-id="461e7-110">[out] An array of `CORDB_REGISTER` objects, each of which receives a value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="461e7-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="461e7-111">Remarks</span></span>  
 <span data-ttu-id="461e7-112">Dizinin boyutu bir bit maskesi için bitler sayısına eşit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="461e7-112">The size of the array should be equal to the number of bits set to one in the bit mask.</span></span> <span data-ttu-id="461e7-113">`regCount` Parametresi, YAZMAÇ değerlerini alacak arabellek öğelerin sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="461e7-113">The `regCount` parameter specifies the number of elements in the buffer that will receive the register values.</span></span> <span data-ttu-id="461e7-114">Varsa `regCount` değeri numarası maskesi tarafından belirtilen kayıtları için çok küçük, daha yüksek numaralı kayıtları kümesinden kesilecek.</span><span class="sxs-lookup"><span data-stu-id="461e7-114">If the `regCount` value is too small for the number of registers indicated by the mask, the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="461e7-115">Varsa `regCount` değer çok büyük olduğu kullanılmayan `regBuffer` öğeleri değiştirilmemiş olacaktır.</span><span class="sxs-lookup"><span data-stu-id="461e7-115">If the `regCount` value is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="461e7-116">Bit maskesi kullanılamıyor, bir kayıt belirtiyorsa `GetRegisters` konusu kasaya belirsiz bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="461e7-116">If the bit mask specifies a register that is unavailable, `GetRegisters` returns an indeterminate value for that register.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="461e7-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="461e7-117">Requirements</span></span>  
 <span data-ttu-id="461e7-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="461e7-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="461e7-119">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="461e7-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="461e7-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="461e7-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="461e7-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="461e7-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="461e7-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="461e7-122">See also</span></span>

- [<span data-ttu-id="461e7-123">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="461e7-123">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="461e7-124">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="461e7-124">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
