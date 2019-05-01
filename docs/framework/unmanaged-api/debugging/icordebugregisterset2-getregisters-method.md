---
title: ICorDebugRegisterSet2::GetRegisters Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegisters method [.NET Framework debugging]
ms.assetid: dbc498a8-ba3f-42f2-bdd9-b623c77a1019
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2dc1064656f3493db78d858cf1e86db0cb83d6c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782869"
---
# <a name="icordebugregisterset2getregisters-method"></a><span data-ttu-id="a1ee9-102">ICorDebugRegisterSet2::GetRegisters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1ee9-102">ICorDebugRegisterSet2::GetRegisters Method</span></span>
<span data-ttu-id="a1ee9-103">Her kaydın değerini alır (üzerinde kod şu anda Yürütülüyor platform için) belirli bir bit maskesi kullanılarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="a1ee9-103">Gets the value of each register (for the platform on which code is currently executing) that is specified by the given bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1ee9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a1ee9-104">Syntax</span></span>  
  
```  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1ee9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a1ee9-105">Parameters</span></span>  
 `maskCount`  
 <span data-ttu-id="a1ee9-106">[in] Bayt cinsinden boyutu, `mask` dizisi.</span><span class="sxs-lookup"><span data-stu-id="a1ee9-106">[in] The size, in bytes, of the `mask` array.</span></span>  
  
 `mask`  
 <span data-ttu-id="a1ee9-107">[in] Bir bayt dizisi, bir kasaya her bitini karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="a1ee9-107">[in] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="a1ee9-108">1 bit ise karşılık gelen kasanın değer alınır.</span><span class="sxs-lookup"><span data-stu-id="a1ee9-108">If the bit is 1, the corresponding register's value will be retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="a1ee9-109">[in] YAZMAÇ değerlerini alınacak sayısı.</span><span class="sxs-lookup"><span data-stu-id="a1ee9-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="a1ee9-110">[out] Bir dizi `CORDB_REGISTER` nesneleri, her biri bir kayıt değeri alır.</span><span class="sxs-lookup"><span data-stu-id="a1ee9-110">[out] An array of `CORDB_REGISTER` objects, each of which receives the value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1ee9-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a1ee9-111">Remarks</span></span>  
 <span data-ttu-id="a1ee9-112">`GetRegisters` Yöntemi maskesi tarafından belirtilen kayıtlardaki değerler dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="a1ee9-112">The `GetRegisters` method returns an array of values from the registers that are specified by the mask.</span></span> <span data-ttu-id="a1ee9-113">Dizi maskesi biti ayarlanmamış yazmaçların değerleri içermiyor.</span><span class="sxs-lookup"><span data-stu-id="a1ee9-113">The array does not contain values of registers whose mask bit is not set.</span></span> <span data-ttu-id="a1ee9-114">Bu nedenle, boyutu `regBuffer` dizi maskesi 1 sayıya eşit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a1ee9-114">Thus, the size of the `regBuffer` array must be equal to the number of 1's in the mask.</span></span> <span data-ttu-id="a1ee9-115">Varsa değerini `regCount` sayı değerleri daha yüksek numaralı yazmaçların maskesi tarafından belirtilen yazmaçların kümesinden kesilecek için yeterli büyüklükte değil.</span><span class="sxs-lookup"><span data-stu-id="a1ee9-115">If the value of `regCount` is too small for the number of registers indicated by the mask, the values of the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="a1ee9-116">Varsa `regCount` çok büyük kullanılmayan `regBuffer` öğeleri değiştirilmemiş olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a1ee9-116">If `regCount` is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="a1ee9-117">Kullanılamayan bir kaydı maskesiyle belirtilirse, bu kasa için belirsiz bir değer döndürülür.</span><span class="sxs-lookup"><span data-stu-id="a1ee9-117">If an unavailable register is indicated by the mask, an indeterminate value will be returned for that register.</span></span>  
  
 <span data-ttu-id="a1ee9-118">`ICorDebugRegisterSet2::GetRegisters` Yöntemi 64'den fazla kayda sahip platformları için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a1ee9-118">The `ICorDebugRegisterSet2::GetRegisters` method is necessary for platforms which have more than 64 registers.</span></span> <span data-ttu-id="a1ee9-119">Örneğin, en fazla 64-bit bit maskesi erişebilmeleri IA64 128 genel amaçlı kaydeder ve 128 kayan nokta kayıtlarını vardır.</span><span class="sxs-lookup"><span data-stu-id="a1ee9-119">For example, IA64 has 128 general purpose registers and 128 floating-point registers, so you need more than 64-bits in the bit mask.</span></span>  
  
 <span data-ttu-id="a1ee9-120">X86 gibi platformlarda olduğu gibi 64'den fazla kayda sahip değilseniz `GetRegisters` yöntemi, bayt cinsinden aslında çevirir `mask` Bayt dizisine bir `ULONG64` ve [Icordebugregisterset:: GetRegisters](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md) gereken yöntemini `ULONG64` maskesi.</span><span class="sxs-lookup"><span data-stu-id="a1ee9-120">If you do not have more than 64 registers, as is the case on platforms such as x86, the `GetRegisters` method actually just translates the bytes in the `mask` byte array into a `ULONG64` and then calls the [ICorDebugRegisterSet::GetRegisters](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md) method, which takes the `ULONG64` mask.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1ee9-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a1ee9-121">Requirements</span></span>  
 <span data-ttu-id="a1ee9-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1ee9-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1ee9-123">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a1ee9-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a1ee9-124">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1ee9-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1ee9-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1ee9-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1ee9-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1ee9-126">See also</span></span>

- [<span data-ttu-id="a1ee9-127">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a1ee9-127">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [<span data-ttu-id="a1ee9-128">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a1ee9-128">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
