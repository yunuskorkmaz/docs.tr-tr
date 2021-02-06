---
description: ': Icordebugmutabledatatarget:: WriteVirtual yöntemi hakkında daha fazla bilgi edinin'
title: 'Icordebugmutabledatatarget:: WriteVirtual yöntemi'
ms.date: 03/30/2017
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
ms.openlocfilehash: 3f3400456b7af51f4b24d7e14e35d641f03a8bfd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637826"
---
# <a name="icordebugmutabledatatargetwritevirtual-method"></a><span data-ttu-id="e08b6-103">Icordebugmutabledatatarget:: WriteVirtual yöntemi</span><span class="sxs-lookup"><span data-stu-id="e08b6-103">ICorDebugMutableDataTarget::WriteVirtual Method</span></span>

<span data-ttu-id="e08b6-104">Belleği hedef işlem adres alanına yazar.</span><span class="sxs-lookup"><span data-stu-id="e08b6-104">Writes memory into the target process address space.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e08b6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e08b6-105">Syntax</span></span>  
  
```cpp  
HRESULT WriteVirtual(  
   [in] CORDB_ADDRESS address,  
   [in, size_is(bytesRequested)] const BYTE * pBuffer,  
   [in] ULONG32 bytesRequested);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e08b6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e08b6-106">Parameters</span></span>  

 `address`  
 <span data-ttu-id="e08b6-107">'ndaki İçeriğin yazılacağı adres `pBuffer` .</span><span class="sxs-lookup"><span data-stu-id="e08b6-107">[in] The address at which to write the contents of `pBuffer`.</span></span>  
  
 `pBuffer`  
 <span data-ttu-id="e08b6-108">'ndaki Yazılacak baytları içeren bir bayt dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e08b6-108">[in] A pointer to a byte array that contains the bytes to be written.</span></span>  
  
 `address`  
 <span data-ttu-id="e08b6-109">'ndaki İçindeki bayt sayısı `pBuffer` .</span><span class="sxs-lookup"><span data-stu-id="e08b6-109">[in] The number of bytes in `pBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e08b6-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e08b6-110">Return Value</span></span>  

 <span data-ttu-id="e08b6-111">`S_OK` başarılı veya `HRESULT` başarısız olduğunda.</span><span class="sxs-lookup"><span data-stu-id="e08b6-111">`S_OK` on success, or any other `HRESULT` on failure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e08b6-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e08b6-112">Remarks</span></span>  

 <span data-ttu-id="e08b6-113">Herhangi bir bayt yazılamaz ise, yöntem çağrısı, hedef adres alanındaki herhangi bir bayt değiştirilmeden başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="e08b6-113">If any bytes cannot be written, the method call fails without changing any bytes in the target address space.</span></span> <span data-ttu-id="e08b6-114">(Aksi halde, hedef, güvenli olmayan bir şekilde hata ayıklama olanağı sunan tutarsız bir durumda olabilir.)</span><span class="sxs-lookup"><span data-stu-id="e08b6-114">(Otherwise, the target would be in an inconsistent state that makes further debugging unreliable.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e08b6-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e08b6-115">Requirements</span></span>  

 <span data-ttu-id="e08b6-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e08b6-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e08b6-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e08b6-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e08b6-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e08b6-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e08b6-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e08b6-119">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e08b6-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e08b6-120">See also</span></span>

- [<span data-ttu-id="e08b6-121">ICorDebugMutableDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e08b6-121">ICorDebugMutableDataTarget Interface</span></span>](icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="e08b6-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e08b6-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
