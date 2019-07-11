---
title: ICorDebugMergedAssemblyRecord::GetPublicKey yöntemi
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7540a87b007656ad3363576f835a89846d287ed1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752735"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="8cd9e-102">ICorDebugMergedAssemblyRecord::GetPublicKey yöntemi</span><span class="sxs-lookup"><span data-stu-id="8cd9e-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="8cd9e-103">Derlemenin ortak anahtarı alır.</span><span class="sxs-lookup"><span data-stu-id="8cd9e-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cd9e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8cd9e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,   
   [out] ULONG32 *pcbPublicKey,   
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8cd9e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8cd9e-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="8cd9e-106">[in] En fazla bayt sayısını `pbPublicKey` dizisi.</span><span class="sxs-lookup"><span data-stu-id="8cd9e-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="8cd9e-107">[out] Gerçek yazılan bayt sayısı için bir işaretçi `pbPublicKey` dizisi.</span><span class="sxs-lookup"><span data-stu-id="8cd9e-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="8cd9e-108">[out] Derlemenin ortak anahtarı içeren bir bayt dizisine bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8cd9e-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8cd9e-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8cd9e-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8cd9e-110">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8cd9e-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8cd9e-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8cd9e-111">Requirements</span></span>  
 <span data-ttu-id="8cd9e-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8cd9e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cd9e-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8cd9e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8cd9e-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8cd9e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8cd9e-115">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cd9e-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cd9e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8cd9e-116">See also</span></span>

- [<span data-ttu-id="8cd9e-117">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8cd9e-117">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="8cd9e-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8cd9e-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
