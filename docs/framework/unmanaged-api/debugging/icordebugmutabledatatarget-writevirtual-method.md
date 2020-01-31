---
title: 'Icordebugmutabledatatarget:: WriteVirtual yöntemi'
ms.date: 03/30/2017
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
ms.openlocfilehash: 2b4bd1dc97f37f5a514ab54f9e4d778fe3b91736
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792827"
---
# <a name="icordebugmutabledatatargetwritevirtual-method"></a><span data-ttu-id="86e80-102">Icordebugmutabledatatarget:: WriteVirtual yöntemi</span><span class="sxs-lookup"><span data-stu-id="86e80-102">ICorDebugMutableDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="86e80-103">Belleği hedef işlem adres alanına yazar.</span><span class="sxs-lookup"><span data-stu-id="86e80-103">Writes memory into the target process address space.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86e80-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86e80-104">Syntax</span></span>  
  
```cpp  
HRESULT WriteVirtual(  
   [in] CORDB_ADDRESS address,  
   [in, size_is(bytesRequested)] const BYTE * pBuffer,  
   [in] ULONG32 bytesRequested);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86e80-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="86e80-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="86e80-106">'ndaki `pBuffer`içeriğinin yazılacağı adres.</span><span class="sxs-lookup"><span data-stu-id="86e80-106">[in] The address at which to write the contents of `pBuffer`.</span></span>  
  
 `pBuffer`  
 <span data-ttu-id="86e80-107">'ndaki Yazılacak baytları içeren bir bayt dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="86e80-107">[in] A pointer to a byte array that contains the bytes to be written.</span></span>  
  
 `address`  
 <span data-ttu-id="86e80-108">'ndaki `pBuffer`bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="86e80-108">[in] The number of bytes in `pBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="86e80-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="86e80-109">Return Value</span></span>  
 <span data-ttu-id="86e80-110">başarılı veya hata durumunda başka bir `HRESULT` `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="86e80-110">`S_OK` on success, or any other `HRESULT` on failure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86e80-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="86e80-111">Remarks</span></span>  
 <span data-ttu-id="86e80-112">Herhangi bir bayt yazılamaz ise, yöntem çağrısı, hedef adres alanındaki herhangi bir bayt değiştirilmeden başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="86e80-112">If any bytes cannot be written, the method call fails without changing any bytes in the target address space.</span></span> <span data-ttu-id="86e80-113">(Aksi halde, hedef, güvenli olmayan bir şekilde hata ayıklama olanağı sunan tutarsız bir durumda olabilir.)</span><span class="sxs-lookup"><span data-stu-id="86e80-113">(Otherwise, the target would be in an inconsistent state that makes further debugging unreliable.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86e80-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="86e80-114">Requirements</span></span>  
 <span data-ttu-id="86e80-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86e80-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86e80-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="86e80-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86e80-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="86e80-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86e80-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86e80-118">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86e80-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86e80-119">See also</span></span>

- [<span data-ttu-id="86e80-120">ICorDebugMutableDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="86e80-120">ICorDebugMutableDataTarget Interface</span></span>](icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="86e80-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="86e80-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
