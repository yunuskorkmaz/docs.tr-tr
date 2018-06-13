---
title: ICorDebugMutableDataTarget::WriteVirtual yöntemi
ms.date: 03/30/2017
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 184ae290b3a7d86a3c0351d4cfb072bce37337d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417420"
---
# <a name="icordebugmutabledatatargetwritevirtual-method"></a><span data-ttu-id="5d071-102">ICorDebugMutableDataTarget::WriteVirtual yöntemi</span><span class="sxs-lookup"><span data-stu-id="5d071-102">ICorDebugMutableDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="5d071-103">Bellek, hedef işlem adres alanı yazar.</span><span class="sxs-lookup"><span data-stu-id="5d071-103">Writes memory into the target process address space.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d071-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d071-104">Syntax</span></span>  
  
```  
HRESULT WriteVirtual(  
   [in] CORDB_ADDRESS address,  
   [in, size_is(bytesRequested)] const BYTE * pBuffer,  
   [in] ULONG32 bytesRequested);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5d071-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5d071-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="5d071-106">[in] İçeriğini yazılacak adresinde `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="5d071-106">[in] The address at which to write the contents of `pBuffer`.</span></span>  
  
 `pBuffer`  
 <span data-ttu-id="5d071-107">[in] Yazılacak baytları içeren bir bayt dizisine bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5d071-107">[in] A pointer to a byte array that contains the bytes to be written.</span></span>  
  
 `address`  
 <span data-ttu-id="5d071-108">[in] Bayt sayısı `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="5d071-108">[in] The number of bytes in `pBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5d071-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5d071-109">Return Value</span></span>  
 <span data-ttu-id="5d071-110">`S_OK` Başarı veya diğer `HRESULT` hatasında.</span><span class="sxs-lookup"><span data-stu-id="5d071-110">`S_OK` on success, or any other `HRESULT` on failure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d071-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5d071-111">Remarks</span></span>  
 <span data-ttu-id="5d071-112">Tüm bayt yazılamaz yöntem çağrısının hedef adres alanındaki tüm bayt değiştirmeden başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="5d071-112">If any bytes cannot be written, the method call fails without changing any bytes in the target address space.</span></span> <span data-ttu-id="5d071-113">(Aksi halde, hedef daha yapar tutarsız bir durumda güvenilir hata ayıklama.)</span><span class="sxs-lookup"><span data-stu-id="5d071-113">(Otherwise, the target would be in an inconsistent state that makes further debugging unreliable.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d071-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5d071-114">Requirements</span></span>  
 <span data-ttu-id="5d071-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d071-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d071-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5d071-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5d071-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d071-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d071-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d071-118">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d071-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5d071-119">See Also</span></span>  
 [<span data-ttu-id="5d071-120">ICorDebugMutableDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5d071-120">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [<span data-ttu-id="5d071-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5d071-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
