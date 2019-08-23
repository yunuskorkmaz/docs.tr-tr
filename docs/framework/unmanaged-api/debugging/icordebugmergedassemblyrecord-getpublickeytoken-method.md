---
title: 'Icordebugmergedassemblyrecord:: GetPublicKeyToken yöntemi'
ms.date: 03/30/2017
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 626aa53740839df0b47a876b3e82814a63ffd82d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936862"
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a><span data-ttu-id="d35ac-102">Icordebugmergedassemblyrecord:: GetPublicKeyToken yöntemi</span><span class="sxs-lookup"><span data-stu-id="d35ac-102">ICorDebugMergedAssemblyRecord::GetPublicKeyToken Method</span></span>
<span data-ttu-id="d35ac-103">Derlemenin ortak anahtar belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="d35ac-103">Gets the assembly's public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d35ac-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d35ac-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKeyToken(  
   [in] ULONG32 cbPublicKeyToken,   
   [out] ULONG32 *pcbPublicKeyToken,   
   [out, size_is(cbPublicKeyToken), length_is(*pcbPublicKeyToken)] BYTE pbPublicKeyToken[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d35ac-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d35ac-105">Parameters</span></span>  
 `cbPublicKeyToken`  
 <span data-ttu-id="d35ac-106">'ndaki `pbPublicKeyToken` Dizideki en fazla bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="d35ac-106">[in] The maximum number of bytes in the `pbPublicKeyToken` array.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="d35ac-107">dışı `pbPublicKeyToken` Diziye yazılan gerçek bayt sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d35ac-107">[out] A pointer to the actual number of bytes written to the `pbPublicKeyToken` array.</span></span>  
  
 `pbPublicKeyToken`  
 <span data-ttu-id="d35ac-108">dışı Derlemenin ortak anahtar belirtecini içeren bir bayt dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d35ac-108">[out] A pointer to a byte array that contains the assembly's public key token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d35ac-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d35ac-109">Remarks</span></span>  
 <span data-ttu-id="d35ac-110">Bir derlemenin ortak anahtar belirteci, ortak anahtarının SHA1 karmasının son sekiz bayttır.</span><span class="sxs-lookup"><span data-stu-id="d35ac-110">An assembly's public key token is the last eight bytes of a SHA1 hash of its public key.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d35ac-111">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d35ac-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d35ac-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d35ac-112">Requirements</span></span>  
 <span data-ttu-id="d35ac-113">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d35ac-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d35ac-114">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d35ac-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d35ac-115">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d35ac-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d35ac-116">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d35ac-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d35ac-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d35ac-117">See also</span></span>

- [<span data-ttu-id="d35ac-118">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d35ac-118">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="d35ac-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d35ac-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
