---
title: ICorDebugMutableDataTarget::WriteVirtual yöntemi
ms.date: 03/30/2017
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d0a6a58a1a270cb67b75cf34ac5df8d45ccf307c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764571"
---
# <a name="icordebugmutabledatatargetwritevirtual-method"></a><span data-ttu-id="5c783-102">ICorDebugMutableDataTarget::WriteVirtual yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c783-102">ICorDebugMutableDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="5c783-103">Bellek, hedef işlemin adres alanına yazar.</span><span class="sxs-lookup"><span data-stu-id="5c783-103">Writes memory into the target process address space.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c783-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5c783-104">Syntax</span></span>  
  
```cpp  
HRESULT WriteVirtual(  
   [in] CORDB_ADDRESS address,  
   [in, size_is(bytesRequested)] const BYTE * pBuffer,  
   [in] ULONG32 bytesRequested);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c783-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5c783-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="5c783-106">[in] İçeriğini yazılacağı adresindeki `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="5c783-106">[in] The address at which to write the contents of `pBuffer`.</span></span>  
  
 `pBuffer`  
 <span data-ttu-id="5c783-107">[in] Yazılacak baytları içeren bir bayt dizisine bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5c783-107">[in] A pointer to a byte array that contains the bytes to be written.</span></span>  
  
 `address`  
 <span data-ttu-id="5c783-108">[in] Bayt sayısı `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="5c783-108">[in] The number of bytes in `pBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c783-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5c783-109">Return Value</span></span>  
 <span data-ttu-id="5c783-110">`S_OK` Başarı veya diğer `HRESULT` başarısız.</span><span class="sxs-lookup"><span data-stu-id="5c783-110">`S_OK` on success, or any other `HRESULT` on failure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c783-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5c783-111">Remarks</span></span>  
 <span data-ttu-id="5c783-112">Herhangi bir bayt yazılamaz yöntem çağrısında hedef adres alanındaki tüm bayt değiştirmeden başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="5c783-112">If any bytes cannot be written, the method call fails without changing any bytes in the target address space.</span></span> <span data-ttu-id="5c783-113">(Aksi takdirde, hedef daha yapar tutarsız bir durumda güvenilir hata ayıklama.)</span><span class="sxs-lookup"><span data-stu-id="5c783-113">(Otherwise, the target would be in an inconsistent state that makes further debugging unreliable.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c783-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5c783-114">Requirements</span></span>  
 <span data-ttu-id="5c783-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c783-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c783-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5c783-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c783-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c783-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c783-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c783-118">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c783-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c783-119">See also</span></span>

- [<span data-ttu-id="5c783-120">ICorDebugMutableDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5c783-120">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="5c783-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5c783-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
