---
title: ICorDebugMergedAssemblyRecord::GetPublicKey yöntemi
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 610e46d5cb550a266c5558c49239d1818c1e85de
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107282"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="a5d89-102">ICorDebugMergedAssemblyRecord::GetPublicKey yöntemi</span><span class="sxs-lookup"><span data-stu-id="a5d89-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="a5d89-103">Derlemenin ortak anahtarı alır.</span><span class="sxs-lookup"><span data-stu-id="a5d89-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5d89-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a5d89-104">Syntax</span></span>  
  
```  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,   
   [out] ULONG32 *pcbPublicKey,   
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5d89-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a5d89-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="a5d89-106">[in] En fazla bayt sayısını `pbPublicKey` dizisi.</span><span class="sxs-lookup"><span data-stu-id="a5d89-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="a5d89-107">[out] Gerçek yazılan bayt sayısı için bir işaretçi `pbPublicKey` dizisi.</span><span class="sxs-lookup"><span data-stu-id="a5d89-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="a5d89-108">[out] Derlemenin ortak anahtarı içeren bir bayt dizisine bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a5d89-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5d89-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a5d89-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5d89-110">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a5d89-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5d89-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a5d89-111">Requirements</span></span>  
 <span data-ttu-id="a5d89-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5d89-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5d89-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a5d89-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a5d89-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5d89-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5d89-115">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5d89-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5d89-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5d89-116">See also</span></span>

- [<span data-ttu-id="a5d89-117">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a5d89-117">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="a5d89-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a5d89-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
